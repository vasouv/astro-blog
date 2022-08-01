---
layout: "../../layouts/BlogPost.astro"
title: "Maven Build Plugin"
description: "Maven Build Plugin"
publishDate: "14 Aug 2018"
categories: 
  - "maven"
---

Certain Maven archetypes may not have a Maven build plugin, or if running the project outside of an IDE (which already knows how to build and run Maven) we usually want to do **java -jar <file>.jar** to run the executable.

For that, we need a Maven build plugin to create the executable jar and set the Main class to run. In the pom file we need the following:

```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-jar-plugin</artifactId>
            <version>3.1.0</version>
            <configuration>
                <archive>
                    <manifest>
                        <mainClass>vs.App</mainClass>
                    </manifest>
                </archive>
            </configuration>
        </plugin>
    </plugins>
</build>
```
And that's it.
