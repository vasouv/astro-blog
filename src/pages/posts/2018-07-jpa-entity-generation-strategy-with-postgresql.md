---
layout: "../../layouts/BlogPost.astro"
title: "JPA entity generation strategy with PostgreSQL"
description: "JPA entity generation strategy with PostgreSQL"
publishDate: "12 Jul 2018"
categories: 
  - "jpa"
---

So far I've been using workarounds to my entities' ID property because I hadn't properly looked into it. I think I wasn't even auto-incrementing the ID and therefore made methods to retrieve the largest ID, increment by 1 and set to the persisting entity. Yeah, complete workaround to something trivial.

# PostgreSQL

For PostgreSQL I have the following table:

```
create table BOOKS (
  id serial primary key,
  title varchar(100) not null,
  author varchar(100) null
);
```

Inserting rows with

```insert into BOOKS(title,author) values ('LOTR','Tolkien');```

auto-increments the ID and I don't have to use workarounds anymore.

# IDENTITY

To use in a JPA entity, I must set the ID annotations to:

```
@Id
@GeneratedValue( strategy=GenerationType.IDENTITY )
private Long id;
```

# SEQUENCE

There's also the Sequence generation strategy. After we create the table, we must set the sequence:

```create sequence book\_seq;```

For use in a JPA entity:

```
@Id
@GeneratedValue( strategy=GenerationType.SEQUENCE, generator="book\_gen" )
@SequenceGenerator( name="book\_gen", sequenceName="book\_seq", allocationSize=50 )
private Long id;
```
