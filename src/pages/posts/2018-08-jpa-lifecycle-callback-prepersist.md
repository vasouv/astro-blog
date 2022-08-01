---
layout: "../../layouts/BlogPost.astro"
title: "JPA entity lifecycle callbacks - @PrePersist"
description: "How to use the @PrePersist JPA lifecycle callback"
publishDate: "25 Aug 2018"
categories: 
  - "jpa"
---

There are certain actions that we need to perform on an entity, that aren't necessarily business based. For example, putting a timestamp when an entity is persisted or updated, logging something or calculating the total amount of an order.

We can use the **@PrePersist** annotation on an entity method. It will be called when the entity manager is going to persist the entity, but right before it happens.

Like so:

```
@PrePersist
private void setTotalAmount() {
    ....
}
```

Then we just need to call **em.persist()** and  the entity manager executes the callback.
