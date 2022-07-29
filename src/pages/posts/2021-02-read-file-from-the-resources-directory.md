---
layout: "../../layouts/BlogPost.astro"
title: "Read file from the resources directory"
description: "Read file from the resources directory in Spring Boot"
publishDate: "20 Feb 2021"
categories: 
  - "spring-boot"
---

We want to read a file in the **src/main/resources** directory and return it as a String.

First the ResourceLoader is autowired

```
@Autowired
ResourceLoader resourceLoader;
```

And then we read the file

```
Resource resource = resourceLoader.getResource("classpath:claymore.json");
InputStream inputStream = resource.getInputStream();
String contents = new BufferedReader(new InputStreamReader(inputStream)).lines().collect(Collectors.joining("\n"));
```
