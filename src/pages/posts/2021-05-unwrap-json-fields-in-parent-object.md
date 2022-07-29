---
layout: "../../layouts/BlogPost.astro"
title: "Unwrap JSON fields in parent object"
description: "Unwrap nested JSON fields in the parent object with Jackson"
publishDate: "21 May 2021"
categories: 
  - "jackson"
---

In this post I'll be showing how we can unwrap the fields of a class in its parent.

By serializing into JSON the following Java class

```
public class Album {

    private String title;
    private int year;
    private Band band;

}
```

we will end up with this JSON

```
{
    "title": "This album rocks!",
    "year": 2021,
    "band": {
        "bandName": "The Incredible Magnificents",
        "bandMembers": 33
    }
}
```

In case we want to pull the band fields up a level inside the **Album** object, we can annotate the **Band** field as **@JsonUnwrapped**

```
@JsonUnwrapped
private Band band;
```

And by doing that, we get the contents of the band object inside the album one.

```
{
    "title": "This album is unwrapped!",
    "year": 2021,
    "bandName": "The Incredible Magnificents",
    "bandMembers": 33
}
```
