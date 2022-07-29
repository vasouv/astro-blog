---
layout: "../../layouts/BlogPost.astro"
title: "Convert JSON array to List"
description: "Deserialize JSON array to Java List with Jackson"
publishDate: "20 Feb 2021"
categories: 
  - "jackson"
---

With Jackson we can convert a String that contains a JSON array to a List of objects.

```
new ObjectMapper().readValue(contents, new TypeReference<List<Claymore>>() {});
```
