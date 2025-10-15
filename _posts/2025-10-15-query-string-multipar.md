---
classes: wide
title: "URL, Query string multipar "
categories:
  - blog
tags:
  - http
  - browser 
  - php
  - post 
  - query string

permalink: /blog/url-query-multipar/
---

TLDR: che succede in caso di querystring con parametri multipli `?p1=val1&p2=val2`? L'http li invia tutti sarà poi chi li riceve (lato server) che decide come elaborarli.
Es. il php assegna l'ultimo valore, Java Servlet il primo valore !!

MORALE : il semplice esperimento con un contesto non ci permette di dedurne una regola generale, cercare conferma in fonti "normative"...

---


[https://chat.deepseek.com/share/1rjodq15z9fmv2aav0](https://chat.deepseek.com/share/1rjodq15z9fmv2aav0)

[https://chat.deepseek.com/share/vh4nchlj7an03pc2t8](https://chat.deepseek.com/share/vh4nchlj7an03pc2t8)

 ![dimostrazione ]({{ site.url }}{{ site.baseurl }}/assets/images/querystring_multivalpar.png)

