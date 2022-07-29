---
layout: "../../layouts/BlogPost.astro"
title: "WildFly Maven Plugin"
description: "Use the WildFly Maven plugin to deploy a Java EE application to a WildFly server"
publishDate: "02 Feb 2020"
categories: 
  - "maven"
---

When we're developing Java EE applications, we can use the IDE to deploy the project to the application server. We can however use the Maven plugin to deploy, which can be useful if the IDE doesn't support Java EE or the application server etc. For example, IntelliJ Community Edition doesn't support Java EE or application servers.

In order to enable the plugin:
```xml
<plugin>
    <groupId>org.wildfly.plugins</groupId>
    <artifactId>wildfly-maven-plugin</artifactId>
    <version>2.0.1.Final</version>
    <configuration>
        <jbossHome>~/DEV/wildfly-19.0.0.Final</jbossHome>
    </configuration>
</plugin>
```

To deploy the project for the first time:

`mvn wildfly:deploy`

and to redeploy:

`mvn wildfly:redeploy`

To undeploy run:

`mvn wildfly:undeploy`

[source](https://github.com/hantsy/jakartaee8-starter/blob/master/docs/03run-wildfly-mvn.md)
