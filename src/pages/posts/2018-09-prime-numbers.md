---
layout: "../../layouts/BlogPost.astro"
title: "Prime Numbers"
description: "Prime numbers in Java"
publishDate: "10 Sep 2018"
categories: 
  - "java"
---

In order to find out if a given number is Prime, it must be divisible only by itself and 1. Also, the number must be equal or greater than 2.

```java
public boolean isPrime(int number) {

    if (number < 2) {
        throw new IllegalArgumentException("Number must be > 2");
    }

    for (int i = 2; i < number; i++) {
        if (number % i == 0) {
            return false;
        }
    }

    return true;
}
```

We'll check all number up to the given number, if the remainder of the number divided by the iterator is zero, then the number is not prime because it divides with another number.

To check the algorithm, these tests will assert correctly.

```java
@Test
public void testIsPrime() {
    assertTrue(primeNumber.isPrime(2));
    assertTrue(primeNumber.isPrime(5));
    assertTrue(primeNumber.isPrime(23));
    assertTrue(primeNumber.isPrime(127));
}

@Test
public void testIsNotPrime() {
    assertFalse(primeNumber.isPrime(10));
    assertFalse(primeNumber.isPrime(21));
    assertFalse(primeNumber.isPrime(159));
}

@Test(expected = IllegalArgumentException.class)
public void expectsExceptions() {
    primeNumber.isPrime(-5);
}
```