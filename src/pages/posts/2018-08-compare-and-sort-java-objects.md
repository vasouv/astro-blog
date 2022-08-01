---
layout: "../../layouts/BlogPost.astro"
title: "Comparing and sorting objects"
description: "How to compare and sort objects in Java"
publishDate: "29 Aug 2018"
categories: 
  - "java"
---

The Collection classes that Java offers do not ensure sorting, unless they implement the **Sorted** interface. They do ensure the order elements are added in them, therefore if we add ordered elements, they will remain ordered.

A List with primitive types and String are known to Java and can be sorted automatically with **Collections.sort(...)**. But if we have an ArrayList with custom classes, we have to define how sorting happens.

There are two ways, either the class must implement the **Comparable<T>** interface and override the **compareTo(...)** method, or create a **Comparator** object and pass it in the **Collections.sort(...)** method whenever we want to sort.

# Implementing Comparable

```
public class Album implements Comparable<Album> {

    @Override
    public int compareTo(Album al2) {
        if (this.year > al2.year) {
            return 1;
        }
        if (this.year < al2.year) {
            return -1;
        }
        return 0;
    }

}
```

How compareTo() is implemented is up to us, here I compare according to the Album year. If we sort, the list is in ascending order.

# Passing Comparator object

The Comparator passed in Collections.sort(...) takes precedence to the compareTo() method in the POJO. Or, this way the POJO doesn't have to implement the Comparable interface in the first place.

```
Comparator<Album> comparator = new Comparator<Album>() {

    @Override
    public int compare(Album a1, Album a2) {
        if (a1.year < a2.year) {
            return 1;
        }
        if (a1.year > a2.year) {
            return -1;
        }
        return 0;
    }

};
```

Now we can call **Collections.sort( list, comparator )** and the list is sorted.

It's convenient that we can have both ways at once. With the compareTo method we can have the sorting we usually want (by year), and in cases we want to sort by price we implement a Comparator.
