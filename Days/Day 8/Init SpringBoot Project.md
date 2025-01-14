## Dependencies
`pom.xml`
```xml
<project>
	<!-- [...] -->
	
	<dependencies>
		<!-- DATABASE -->
		<dependency>
		    <groupId>org.springframework.boot</groupId>
	        <artifactId>spring-boot-starter-data-jpa</artifactId>
	    </dependency>
	   	<dependency>
		    <groupId>mysql</groupId>
		    <artifactId>mysql-connector-java</artifactId>
		    <version>8.0.33</version>
		</dependency>

		<!-- [...] -->
	<dependencies>
	
	<!-- [...] -->
</project>
```

### Example
![[Pasted image 20250114170911.png]]

## Database Connection
`src/main/resources/application.properties`
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/jaita138-db-spring-1
spring.datasource.username=root
spring.datasource.password=code

spring.jpa.hibernate.ddl-auto=update
```
