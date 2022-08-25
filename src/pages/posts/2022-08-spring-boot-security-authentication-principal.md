---
layout: "../../layouts/BlogPost.astro"
title: "Spring Boot Security - Authentication Principal"
description: "How to get the logged in user through the SecurityContext in Spring Boot"
publishDate: "25 Aug 2022"
categories: 
  - "spring boot"
---

```java
Authentication authentication = SecurityContextHolder.getContext().getAuthentication();
String currentPrincipalName = authentication.getName();
```