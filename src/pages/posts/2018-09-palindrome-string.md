---
layout: "../../layouts/BlogPost.astro"
title: "Palindrome String"
description: "Palindrome String in Java"
publishDate: "10 Sep 2018"
categories: 
  - "java"
---

Palindrome strings are the ones that are mirrored after the middle letter, or mirrored in half. For example **abba** is palindrome and so is **civic**, but **ghgf** isn't. A single character is always palindrome of itself and so is the **space**.

I'll show two ways to check if a String is palindrome, the first method is to iterate the String and check the letters, while the second splits the String in two separate Strings, reverses the second and checks.

# 1. Looping the String

```java
public boolean isPalindromeWithLoop(String input) {

    if (input.length() < 2) {
        return true;
    }

    int begin = 0;
    int end = length;

    while (begin < end) {
        if (input.charAt(begin) != input.charAt(end)) {
            return false;
        }
        begin++;
        end--;
    }

    return true;
}
```

We'll be iterating the String forwards and backwards checking the characters each time. The moment there is an inequality, the String is not palindrome and therefore returns false.

# 2. Using the String.substring() method

```java
public boolean isPalindromeWithSubString(String input) {

	if (input.length() < 2) {
		return true;
	}

	String firstHalf, secondHalf;

	if (input.length() % 2 == 0) {
		firstHalf = input.substring(0, input.length() / 2);
		secondHalf = input.substring(input.length() / 2);
	} else {
		firstHalf = input.substring(0, input.length() / 2);
		secondHalf = input.substring((input.length() / 2) + 1);
	}

	String secondReverse = new StringBuilder(secondHalf).reverse().toString();

	if (firstHalf.equals(secondReverse)) {
		return true;
	} else {
		return false;
	}
}
```

In this case, we must first check if the length of the String is odd or even, because if it's odd and the middle character ends up in one of the substrings, the equality will fail.

If it's even, we get two substrings exactly in half. If it's odd, we disregard the middle character by getting the second substring by one off to the right. Then we reverse the second substring and check it with the first.

# 3. Testing

To test whether these methods work or not, these assertions will show it.

```java
@Test
public void whenWord\_shouldBePalindromeWithLoop() {

  assertTrue(palindrome.isPalindromeWithLoop("anna"));
  assertTrue(palindrome.isPalindromeWithLoop("civic"));
  assertTrue(palindrome.isPalindromeWithLoop("kayak"));
  assertTrue(palindrome.isPalindromeWithLoop("B"));
  assertTrue(palindrome.isPalindromeWithLoop(""));
  assertTrue(palindrome.isPalindromeWithLoop("cc"));
  assertTrue(palindrome.isPalindromeWithLoop("12321"));

}
```