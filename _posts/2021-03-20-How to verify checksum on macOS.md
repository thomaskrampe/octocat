---
layout: default
title:  "How to verify checksum on macOS"
date:   2021-03-20 08:16:00 +0100
categories: macOS 
---

# How to verify checksum on macOS

## What is a checksum

A checksum is a sequence of numbers and letters derived from a piece of stored or transmitted digital data for the purpose of detecting errors that may have been introduced during its transmission or storage. It is usually applied to an installation file after it is received from the download server. So if you know the checksum of an original file, you can use it to check whether your copy of the file is identical or not.
To verify the checksum on your Mac first you need to open Terminal app. The Terminal app is in the Utilities folder in Applications. To open it, either open your Applications folder, then open Utilities and double-click on Terminal, or press Command and Spacebar to launch Spotlight and type “Terminal” then double-click the search result or simply press Enter.

## Verifying SHA-1, SHA-256, SHA-512 checksum

Type the following command in your Terminal:

{% highlight bash %}
shasum -a [1/256/512] /full/path/to/your/file
{% endhighlight %}

### Using OpenSSL to verify SHA-1, SHA-256, SHA-512

Type the following command in your Terminal:

{% highlight bash %}
openssl [sha1/sha256/sha512] /full/path/to/your/file
{% endhighlight %}

Or you can type the command openssl sha512 followed by space and drag and drop the file to the Terminal.

Output should look like:

{% highlight bash %}
thomas@Toms-MBP ~ % shasum -a 512 /Users/thomas/Desktop/Purchase.pdf
a735f6d82fc7c6757211274b802e8f693bf0352d025197c9d9bcb689817cd81b143c89c4d75fc8e351ae70a6b57e53359449b1e9df4c2f233994717c71f23fde  /Users/thomas/Desktop/Purchase.pdf

thomas@Toms-MBP ~ % openssl sha512 /Users/thomas/Desktop/Purchase.pdf
SHA512(/Users/thomas/Desktop/Purchase.pdf)= a735f6d82fc7c6757211274b802e8f693bf0352d025197c9d9bcb689817cd81b143c89c4d75fc8e351ae70a6b57e53359449b1e9df4c2f233994717c71f23fde
{% endhighlight %}

## Verifying MD5 checksum

MD5 is no longer recommended as a checksum hash for security reasons, but some legacy programs may still use it.

Type the following command in your Terminal:

{% highlight bash %}
md5 /full/path/to/your/file
{% endhighlight %}

Or you can type the command md5 followed by space and drag and drop the file to the Terminal.

You can use [Diffchecker][1] to find any deferences between them.

### Using OpenSSL to verify MD5

Type the following command in your Terminal:

{% highlight bash %}
openssl md5 /full/path/to/your/file
{% endhighlight %}

Or you can type the command openssl md5 followed by space and drag and drop the file to the Terminal.

Output should look like:

{% highlight bash %}
thomas@Toms-MBP ~ % md5 /Users/thomas/Desktop/Purchase.pdf
MD5 (/Users/thomas/Desktop/Purchase.pdf) = 43298e4c3c8f654e3438dbf7c5fc07a8

thomas@Toms-MBP ~ % openssl md5 /Users/thomas/Desktop/Purchase.pdf
MD5(/Users/thomas/Desktop/Purchase.pdf)= 43298e4c3c8f654e3438dbf7c5fc07a8
thomas@Toms-MBP ~ %
{% endhighlight %}

[1]: https://www.diffchecker.com/
