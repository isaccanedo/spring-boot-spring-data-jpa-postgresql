# Spring Boot + Spring data JPA + PostgreSQL example

O Spring Boot + Spring data JPA anterior será reutilizado, modificado para suportar o banco de dados PostgreSQL.

Tecnologias utilizadas:

- Spring Boot 2.1.2.RELEASE
- Spring 5.1.4.RELEASE
- Hibernate 5.3.7
- HikariCP 3.2.0
- Driver PostgreSQL 42.2.5
- Maven 3
- Java 8

Coloca um driver postgresql e define o url da fonte de dados em application.properties. Feito, o Spring Boot pode se conectar a um banco de dados PostgreSQL.

pom.xml
```
    <dependency>
        <groupId>org.postgresql</groupId>
        <artifactId>postgresql</artifactId>
    </dependency>
```

### 1. Maven

pom.xml
```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
         http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <artifactId>spring-boot-data-jpa</artifactId>
    <packaging>jar</packaging>
    <name>Spring Boot Spring Data JPA</name>
    <version>1.0</version>

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.1.2.RELEASE</version>
    </parent>

    <properties>
        <java.version>1.8</java.version>
        <downloadSources>true</downloadSources>
        <downloadJavadocs>true</downloadJavadocs>
    </properties>

    <dependencies>

        <!-- jpa, crud repository -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-jpa</artifactId>
        </dependency>

        <!-- PostgreSQL -->
        <dependency>
            <groupId>org.postgresql</groupId>
            <artifactId>postgresql</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>

    </dependencies>

    <build>
        <plugins>

            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>

            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
                <version>2.22.0</version>
            </plugin>

        </plugins>

    </build>
</project>
```


### 2. Configure PostgreSQL
```
2.1 Update the PostgreSQL settings in spring.datasource.*

application.properties

## default connection pool
spring.datasource.hikari.connectionTimeout=20000
spring.datasource.hikari.maximumPoolSize=5

## PostgreSQL
spring.datasource.url=jdbc:postgresql://localhost:5432/postgres
spring.datasource.username=postgres
spring.datasource.password=password

#drop n create table again, good for testing, comment this in production
spring.jpa.hibernate.ddl-auto=create
```
Done.

### Download Source Code
$ git clone https://github.com/isaccanedo/spring-boot-spring-data-jpa-postgresql.git
$ cd spring-data-jpa-postgresql
$ mvn spring-boot:run



