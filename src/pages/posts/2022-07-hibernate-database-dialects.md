---
layout: "../../layouts/BlogPost.astro"
title: "Hibernate Database Dialects"
description: "Hibernate Dialects that can be set to configure a datasource in Spring Boot"
publishDate: "24 Jul 2022"
categories: 
  - "spring boot"
---

Hibernate dialects for a couple of databases, that can be set at `spring.jpa.properties.hibernate.dialect`

| Database      | Dialect |
| :----------- | :----------- |
| H2 | org.hibernate.dialect.H2 |
| MariaDBDialect | org.hibernate.dialect.MariaDBDialect |
| MySQL8Dialect | org.hibernate.dialect.MySQL8Dialect |
| PostgreSQL95Dialect | org.hibernate.dialect.PostgreSQL95Dialect |

Example configuration
```
spring.datasource.url=jdbc:mariadb://localhost:3306/diet-logs-rev
spring.datasource.driver-class-name=org.mariadb.jdbc.Driver
spring.datasource.username=root
spring.datasource.password=root
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MariaDBDialect
spring.jpa.hibernate.ddl-auto=update
```