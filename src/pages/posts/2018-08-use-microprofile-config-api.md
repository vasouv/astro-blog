---
layout: "../../layouts/BlogPost.astro"
title: "Using the Microprofile Config API"
description: "How to use the Microprofile Config API"
publishDate: "19 Aug 2018"
categories: 
  - "microprofile"
---

Sure we could use the Properties class to read a .properties file, with the Microprofile Config API though we can simply inject the property and it's handled automatically.

# Maven dependency

To use it with Maven, we can either add the Config API dependency or the entire Microprofile dependency. If we're using an application server that implements the Microprofile APIs (such as Payara 5+), we can set the scope to **provided**.

```xml
<dependency>
    <groupId>org.eclipse.microprofile.config</groupId>
    <artifactId>microprofile-config-api</artifactId>
    <version>1.3</version>
    <scope>provided</scope>
</dependency>
```

# Properties file

We must create a **microprofile-config.properties** file in ../**resources/META-INF/.** The contents can be as such:

```
apiKey = public key
username = username here
```

# Injection point

In any class that we want to use a property, we can do

```java
@Inject
@ConfigProperty(name = "privKey", defaultValue="sth default")
private String privateKey;
```

It reads the property with the specific name, and if there's no value set then the default is used.

There's also another way by injecting the whole **@Config** file and then getting what properties we want.
