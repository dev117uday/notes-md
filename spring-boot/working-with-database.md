# Working with Database

## Configuration for PostgreSQL

```java
app:
  datasource:
    main:
      driver-class-name: org.postgresql.Driver
      jdbc-url: jdbc:postgresql://localhost:5431/amigoscode
      username: amigoscode
      password: password
      pool-size: 30
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

## MovieRowMapper

```java
public class MovieRowMapper implements RowMapper<Movie> {

	@Override
	public Movie mapRow(ResultSet rs, int rowNum) throws SQLException {
		return new Movie(
			rs.getInt("id"), rs.getString("name"), List.of(),
			LocalDate.parse(rs.getString("release_date"))
		);
	}
}
```
