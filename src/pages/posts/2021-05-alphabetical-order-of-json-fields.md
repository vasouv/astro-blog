---
layout: "../../layouts/BlogPost.astro"
title: "Alphabetical order of JSON fields"
description: "Order JSON fields alphabetically with Jackson"
publishDate: "19 May 2021"
categories: 
  - "jackson"
---

Let's say we want to order alphabetically the fields of an object that is returned from a rest controller; especially useful when the JSON has lots of fields.

This can be very easily achieved with a single annotation placed on the class.

```
@JsonPropertyOrder(alphabetic = true)
public class Album {

    private String title;
    private int year;
    private Band band;

}
```

The **JsonPropertyOrder** annotation on the class orders the fields of the converted class in alphabetical order. The result can be seen below

```
{
    "band": {
        "bandName": "Blind Guardian",
        "bandMembers": 4
    },
    "title": "Nightfall in Middle Earth",
    "year": 1998
}
```

Clearly we can see that the fields are ordered alphabetically. The fields of embedded objects though (**band**) are not ordered since that class does not have the annotation.
