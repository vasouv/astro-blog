---
layout: "../../layouts/BlogPost.astro"
title: "JAX-RS List Type Erasure in Response"
description: "JAX-RS List type erasure in Response object"
publishDate: "11 Aug 2018"
categories: 
  - "jax-rs"
---

When returning a List of objects in a JAX-RS Response, the type is lost and it asks for a MessageBodyWriter.

To properly return a list of objects in a Response, we must wrap that collection in a GenericEntity.

```
@GET
public Response findAll() {
    List<SuggestedName> suggestedNames = em.createNamedQuery("SuggestedName.findAll").getResultList();
    GenericEntity<List<SuggestedName>> list = new GenericEntity<List<SuggestedName>>(suggestedNames) {};
    return Response.ok(list).build();
}
```

Of course we have the option to return a List of objects directly, this is needed only for a Response return type.
