---
layout: "../../layouts/BlogPost.astro"
title: "Hibernate Date & Time Mappings"
description: "Map Java 8 Date and Time classes to the database in Spring Boot with Hibernate"
publishDate: "01 Aug 2022"
categories: 
  - "spring boot"
---

| Type           | JDBC                    |
| -------------- | ----------------------- |
| LocalDate      | DATE                    |
| LocalTime      | TIME                    |
| LocalDateTime  | TIMESTAMP               |
| OffsetTime     | TIME_WITH_TIMEZONE      |
| OffsetDateTime | TIMESTAMP_WITH_TIMEZONE |
| Duration       | BIGINT                  |
| Instant        | TIMESTAMP               |
| ZonedDateTime  | TIMESTAMP               |

[source](https://thorben-janssen.com/hibernate-jpa-date-and-time/)