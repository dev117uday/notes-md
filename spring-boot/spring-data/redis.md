---
description: working with Redis and Spring Boot
---

# Redis

### Redis with Spring Boot

```java
@Configuration
@EnableRedisRepositories
public class RedisConfig {

	// configuration for connection
	@Bean
	public JedisConnectionFactory connectionFactory() {
		RedisStandaloneConfiguration configuration = new RedisStandaloneConfiguration();
		// load from properties
		configuration.setHostName("localhost");
		configuration.setPort(6379);
		return new JedisConnectionFactory(configuration);
	}

	// configuration for using redis with java
	@Bean
	public RedisTemplate<String, Object> redisTemplate() {
		RedisTemplate<String, Object> template = new RedisTemplate<>();
		template.setConnectionFactory(connectionFactory());
		template.setKeySerializer(new StringRedisSerializer());
		template.setHashKeySerializer(new StringRedisSerializer());
		template.setHashKeySerializer(new JdkSerializationRedisSerializer());
		template.setValueSerializer(new JdkSerializationRedisSerializer());
		template.setEnableTransactionSupport(true);
		template.afterPropertiesSet();
		return template;
	}

}
```

### Making class compatible with redis

* Annotate class with : `@RedisHash("Product")`
* Implement with `Serializable` interface

### Using Redis as DocStore

* As `docstore` because it gives the ability with to search and operate on values
* To add obj to Redis with id as identifier

```java
redisTemplate.opsForHash().put(HASH_KEY, product.getId(), product);
```

* To get all values of obj

```java
redisTemplate.opsForHash().values(HASH_KEY);
```

* To get document by id

```java
redisTemplate.opsForHash().get(HASH_KEY, id);
```

* To delete obj with id

```java
redisTemplate.opsForHash().delete(HASH_KEY, id);
```

### Enable caching at controller level

* Annotate with `@EnableCaching`
* To enable caching at method level

```java
@Cacheable( key = "#{id}", value = "HASH_KEY", unless = "#result.{field}>{value}" )
```

* To remove obj from cache when delete from db

```java
@CacheEvict(key = "#{id}", value = "HASH_KEY")
```

* To update obj from cache when delete from db

```java
@CachePut(key = "#{id}", value = "HASH_KEY")
```

### RedisTemplate for Pub/Sub

```java
@Bean
public RedisTemplate<String,Object> template() {
	RedisTemplate<String, Object> template = new RedisTemplate<>();
	template.setConnectionFactory(connectionFactory());
	template.setValueSerializer(new GenericToStringSerializer<Object>(Object.class));
	return template;
}

@Bean
public ChannelTopic topic() {
	return new ChannelTopic("pubsub:dev117uday");
}

@Bean
public MessageListenerAdapter messageListenerAdapter() {
	return new MessageListenerAdapter(new Receiver());
}

@Bean
public RedisMessageListenerContainer redisMessageListenerContainer( ) {
	RedisMessageListenerContainer container = new RedisMessageListenerContainer();
	container.setConnectionFactory(connectionFactory());
	container.addMessageListener(messageListenerAdapter(), topic());
	return container;
}
```

### Redis Stream Publisher template

```java
Gson gson = new Gson();
var json = gson.toJson(new Users("1", "1", "1"));		
redisTemplate.convertAndSend(topic.getTopic(), json );
```

### Redis Stream Subscriber template

```java
public class RedisReceiver implements MessageListener {

	Logger logger = LoggerFactory.getLogger(RedisReceiver.class);

	@Override
	public void onMessage(Message message, byte[] pattern) {
		try {
			var messageString = getObject(message.getBody());
			Gson gson = new Gson();
			var user = gson.fromJson((String) messageString, Users.class);
			logger.info("Consumed event {}", user.toString());
		} catch (ClassNotFoundException | IOException e) {
			e.printStackTrace();
		}

	}

	private static Object getObject(byte[] byteArr) throws IOException, ClassNotFoundException {
		ByteArrayInputStream bis = new ByteArrayInputStream(byteArr);
		ObjectInput in = new ObjectInputStream(bis);
		return in.readObject();
	}

}
```
