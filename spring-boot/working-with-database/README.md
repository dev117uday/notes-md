# Working with Database

## Configuration for PostgreSQL

```java
// FOR JDBC
app:
  datasource:
    main:
      driver-class-name: org.postgresql.Driver
      jdbc-url: jdbc:postgresql://[host]:[port]/[db name]
      username: [username]
      password: [password]
      pool-size: [pool size]
      
// FOR JPA
spring:
  datasource:
    url: jdbc:postgresql://[host]:[port]/[db name]
    username: username
    password: [password]

  jpa:
   hibernate.ddl-auto: update
   show-sql: true
   properties:
     hibernate:
       dialect: org.hibernate.dialect.PostgreSQLDialect
```

## Configuring HikariDataSource

```java
@Configuration
public class DataSouceConfig {

	@Bean
	@Primary
	// to get the required environment variable from configuration
	@ConfigurationProperties(prefix = "app.datasource.main")
	public HikariDataSource hikariDataSource() {
		return DataSourceBuilder.create()
		.type(HikariDataSource.class).build();
	}

	@Bean
	public JdbcTemplate jdbcTemplate(HikariDataSource hikariDataSource) {
		return new JdbcTemplate(hikariDataSource);
	}

}
```

## RowMapper\<T>&#x20;

```java
public class TRowMapper implements RowMapper<T> {

	@Override
	public T mapRow(ResultSet rs, int rowNum) throws SQLException {
		return new Movie(
			rs.getInt("id"), rs.getString("column_name"), List.of(),
			LocalDate.parse(rs.getString("column_name"))
		);
	}
}
```

### Miscellaneous&#x20;

#### For flyway migration

* If you are using Flyway for db migration, create a folder `db/migrations` inside resource folder
  * Name the migration `V[number]__[name of migration].sql`
