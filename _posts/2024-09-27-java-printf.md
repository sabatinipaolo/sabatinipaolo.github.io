---
title: "Java printf"
categories:
  - Blog
tags:
  - java
  - printf
---
TLDR: anche java ha `printf` come in C

Nella quasi totalità dei sorgenti che trovate nei tutorial, esempi, stackoverflow e libri, troverete :

```java

    System.out.println("ciao mondo");

````

ma con piacevole sorpresa  nel proporci il file di esempio IntellijIdea scrive:

```java

    System.out.printf("ciao mondo");

````

E che novità è questa ? 
ChatGPT ci informa che poi non è tanto nuova ..

 ![ChatGPT ci informa che `printf()` è stato introdotto nel 2024]({{ site.url }}{{ site.baseurl }}/assets/images/java-printf/chatGpt.png)


riferimenti:

sutdent friendly : 

[www.w3schools.com](https://www.w3schools.com/java/ref_output_printf.asp)

professional: 

[java reference](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/io/PrintStream.html#printf(java.lang.String,java.lang.Object...))