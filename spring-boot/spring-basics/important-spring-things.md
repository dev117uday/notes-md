---
description: just things
---

# Important Spring Things

## ApplicationRunner

* Automatically run method when Spring Boot starts

```java
import org.springframework.boot.ApplicationArguments;
import org.springframework.boot.ApplicationRunner;
import org.springframework.stereotype.Component;

import lombok.extern.slf4j.Slf4j;

@Component
@Slf4j
public class ConfigRunner implements ApplicationRunner {

    @Override
    public void run(ApplicationArguments args) throws Exception {
        log.info("XXXXXXXXXXX ============ XXXXXXXXXXXXXX");
    }
    
}
```

