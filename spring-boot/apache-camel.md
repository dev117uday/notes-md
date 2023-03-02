---
description: https://camel.apache.org/
---

# Apache Camel

*   set in application.properties file :&#x20;

    ```
    camel.springboot.main-run-controller = true
    ```



### File Operation in Apache Camel

```java
@Override
    public void configure() throws Exception {
        log.info("---- starting ----");
        moveAllFile();
        //moveSpecificFile("file");
        //moveSpecificFileWithContent("hello");
        //processFile();
        //multiFileProcessor();
        log.info("---- end ----");
    }

    public void moveAllFile() {
        from("file:/home/uday/a").log("--- moved ---")
                .to("file:/home/uday/b");
    }

    public void moveSpecificFile(String fileName) {
        from("file:/home/uday/a")
                .filter(header(Exchange.FILE_NAME).startsWith(fileName))
                .to("file:/home/uday/b");
    }

    public void moveSpecificFileWithContent(String content) {
        from("file:/home/uday/a")
                .filter(body().startsWith(content))
                .to("file:/home/uday/b");
    }

    public void processFile() {
        from("file:/home/uday/a")
                .process(p -> {
                    String body = p.getIn().getBody(String.class);
                    StringBuilder sb = new StringBuilder();
                    Arrays.stream(body.split(" "))
                        .forEach(s -> sb.append(s).append(","));
                    p.getIn().setBody(sb);
                }).to("file:/home/uday/b");
    }

    public void multiFileProcessor() {
        from("file:/home/uday/a/").unmarshal().csv().split(body()
        .tokenize(",")).choice()
                .when(body().contains("closed"))
                    .to("file:/home/uday/b?fileName=closed.csv")
                .when(body().contains("pending"))
                    .to("file:/home/uday/b?fileName=pending.csv")
                .when(body().contains("waiting"))
                    .to("file:/home/uday/b?fileName=waiting.csv");
    }
```

#### More file operation

```java
from("direct://log-file-values")
        .log("${messageHistory} ${headers.CamelFileAbsolute}")
        .log("${file:name} ${file:name.ext} ${file:size}");

from("file:files/input")
        .routeId("Files-Input-Route")
        .transform().body(String.class)

        .choice()

        //.when(simple("${file:ext} ends with 'xml'"))
        .when(method(deciderBean))
        .log("XML FILE")

        .when(simple("${body} contains 'USD'"))
        .log("Contains USD")
        .otherwise()
        .log("No Condition met")
        .end()

        // ignore this intellj warning

        .to("direct://log-file-values")
        .to("file:files/output");
```

### Multicast

```java
// ## multicast

from("timer:multicast?period=10000")
        .multicast()
        .to("log:something-1", "log:something-2");
```

### Spilt&#x20;

```java

from("file:files/csv")
        .unmarshal().csv()
        .split(body())
        .to("log:split-files");

from("file:files/csv")
        .convertBodyTo(String.class)
        .split(body(), ",")
        .to("log:split-files");

from("file:files/csv")
        .convertBodyTo(String.class)
        .split(method(spliterComponent))
        .to("log:split-files");
    
---
                
@Autowired
    private SpliterComponent spliterComponent;
    
@Component
public class SpliterComponent {
    public List<String> spilt(String body) {
        return Arrays.stream(body.split(" ")).toList();
    }
}
```

### Aggregation

```java
from("file:files/agg-json")
    .unmarshal().json(JsonLibrary.Jackson, CurrencyExchange.class)
    .aggregate(simple("${body.to}"), (oldExchange, newExchange) -> {

        Object newBody = newExchange.getIn().getBody();
        ArrayList lst = null;

        if (oldExchange == null) {
            lst = new ArrayList<Object>();
            lst.add(newBody);
            newExchange.getIn().setBody(lst);
            return newExchange;
        } else {
            // ignore
            lst = oldExchange.getIn().getBody(ArrayList.class);
            lst.add(newBody);
            return oldExchange;
        }

    }).completionSize(3)
    .to("log:agg-json");
```

### Routing Slip

```java
String routingSlip = "direct:endpoint1,direct:endpoint2";

from("timer:routingSlip?period={{time-period}}")
        .transform().constant("my message")
        .routingSlip(simple(routingSlip));

from("direct:endpoint1").to("{{endpoint-for-logging}}");

from("direct:endpoint2").to("log:endpoint2");

from("direct:endpoint3").to("log:endpoint3");

from("timer:routingSlip?period=10000")
        .transform().constant("my message")
        .dynamicRouter(method(dynamicRouterBean));
        
----

@Component
@Slf4j
public class DynamicRouterBean  {

    public String decideTheNextEndpoint(
            @ExchangeProperties Map<String, String> properties,
            @Headers Map<String, String> headers,
            @Body String body
    ) {
        log.info("{} {} {}", properties, headers, body);
        return "direct:endpoint1";
    }

}
```

### Error Handling

```java
// to enable tracing
getContext().setTracing(true);

// not make sure no message is lost
errorHandler(deadLetterChannel("activemq:dead-letter-queue"));

// to tap message while in camel context
from("").wireTap("");
```

### Active MQ

```java
from("timer:active-mq-timer?period=2000")
        .transform().constant("my message for active-mq")
        .log("--- message sent to queue ---")
        .to("activemq:my-activemq-queue");

from("file:files/json")
        .to("activemq:my-activemq-queue");

from("file:files/xml")
        .to("activemq:my-activemq-xml-queue");
        
from("activemq:my-activemq-queue")
        .unmarshal().json(JsonLibrary.Jackson, CurrencyExchange.class)
        .bean(myCurrencyExchangeProcessor)
        .bean(myCurrencyExchangeTransformer)
        .to("log:received-from-active-mq");

from("activemq:my-activemq-xml-queue")
        .unmarshal()
        .jacksonXml(CurrencyExchange.class)
        .to("log:received-from-activemq-xml");
```

### Kafka

```java
from("file:files/json")
        .log("${body}")
        .to("kafka:mykafkatopic");
```

### Using Time

```java
// queue :- timer
// transformation
// database :- log

// from : starting route
// to   : the final destination

// processing : doesnt change the message
// transform : does change the message

from("timer:first-timer")

        // example 1
        //.transform()
        //.constant("My message at : "+ LocalDateTime.now())

        // example 2
        //.bean(getCurrentTimeBean)

        // example 3
        .log("${body}")
        .transform().constant("My message")
        .log("${body}")
        .bean(getCurrentTimeBean)
        .log("${body}")
        .bean(simpleLoggingProcessingComponent)
        .log("${body}")

        .to("log:first-timer");
        
----

public class SimpleLoggingProcessingComponent implements Processor {
    @Override
    public void process(Exchange exchange) throws Exception {
        log.info("SimpleLoggingProcessingComponent : {}", exchange.getMessage().getBody());
    }
}

-----


```

### Rest API

```java
restConfiguration().host("localhost:8081");

from("timer:rest-api-consumer?period=3000")
        .setHeader("from", () -> "usd")
        .setHeader("to", () -> "inr")
        .to("rest:get:/currency-exchange/from/{from}/to/{to}")
        .log("${body}");
```
