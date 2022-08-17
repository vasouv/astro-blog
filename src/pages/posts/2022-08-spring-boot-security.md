---
layout: "../../layouts/BlogPost.astro"
title: "Spring Boot Security - Basic Authentication"
description: "Examples on how to implement Basic Authentication with Spring Security"
publishDate: "17 Aug 2022"
categories: 
  - "spring boot"
---

# Basic Authentication with Spring Security

In this series of posts I want to document how to use Spring Security to secure an API. This first part will describe a couple of simple use cases using Basic Authentication. Nowadays Basic Authentication is not secure at all and should be avoided, but at the very least it gives us some tools to work with and is good enough for simple projects.

## Project setup
To start with, we need a Spring Boot project with the Web dependency. Then we'll create three controllers like so:

```java
@RestController
class HomeController {

	@GetMapping("/")
	public String home() {
		return "Home Controller";
	}

}

@RestController
class UnsecuredController {

	@GetMapping("unsecured")
	public String unsecured() {
		return "Unsecured Controller";
	}

}

@RestController
class SecuredController {

	@GetMapping("secured")
	public String secured() {
		return "Secured Controller";
	}
}
```

Now if we run the project, we can hit all three controllers and get a response. The end result is to have the Home and Unsecured endpoints available for all users, and only the Secured endpoint accessible to the authenticated user.

## Default security configuration
To enable the default configuration with Spring Security to the project, we need to add the suitable dependency:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>
```

When we run the project we'll notice a couple of things; in the logs there is a line that displays a generated password. This is generated for the default user and can be used as is. Also, all endpoints are secured by default, since the default security configuration is applied on the whole application. So if we try to call any endpoint, we'll get an HTTP 401 response.

So in order to hit any endpoint with the default credentials, we can use Postman to make the call. In the **Authorization** tab, we select **Basic Auth** and then provide **user** for the username, and the generated password.

### Setting custom username and password
We can set our custom credentials in the properties file.
```
spring.security.user.name = vasouv
spring.security.user.password = vasouv
```
Now by entering our own credentials in Postman, we can access the endpoints again.