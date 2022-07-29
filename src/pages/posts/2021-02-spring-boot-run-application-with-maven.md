---
layout: "../../layouts/BlogPost.astro"
title: "Spring Boot Run Application with Maven"
description: "Run a Spring Boot application with profile using Maven. For Spring Boot 1.5 & 2.X"
publishDate: "03 Mar 2021"
categories: 
  - "spring-boot"
---

## Spring Boot 2.x

```
mvn spring-boot:run -Dspring-boot.run.profiles=dev
```

## Spring Boot 1.x

```
mvn spring-boot:run -Dspring.profiles.active=dev
```
