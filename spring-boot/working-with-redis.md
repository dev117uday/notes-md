# Working with Redis

### Redis with Spring Boot

```java
@Configuration
@EnableRedisRepositories
public class RedisConfig {

	// configuration for connection
	@Bean
	public JedisConnectionFactory connectionFactory() {
		RedisStandaloneConfiguration configuration = new RedisStandaloneConfiguration();
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

* As docstore because it gives the ability with to search and operate on values
* To add obj to redis with id as identifier

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

\-- how to set timeout limit
