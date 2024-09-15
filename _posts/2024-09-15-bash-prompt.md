---
title: "Il prompt di Bash "
categories:
  - blog
tags:
  - bash
  - prompt

permalink: /blog/il-prompt-di-bash/
---
  

TLDR:


![il prompt di Bash]({{ site.url }}{{ site.baseurl }}/assets/images/bash-prompt/tltr-bash-prompt)


---

Quando apriamo un terminale, la shell potrebbe darci qualche riga di benvenuto e poi un _**"prompt"**_ (qualcosa che ci invita/esorta ad inserire dei comandi).
 

Quello di bash ha il seguente aspetto:
```console 

    giovanni@server:~$

 ```   

**`giovanni`** è l'utente con cui si sta lavorando 
**`server`** è l'hostname della macchina su cui giovanni sta lavorando 

**`~`**  significa che giovanni sta attualmente lavorando nella sua **home directory**

`$` serve a ricordare che giovanni è un **utente semplice**, altrimenti al posto del dollaro avremmo **`#`** che significa stiamo lavorando con il **super utente** **`root`**

## di più : 

se la shell si presentasse in questo modo :
```console 
    giovanni@server:~/Documenti~$
 ```
significa che giovanni sta lavorando nella directory Documenti che si trova nella sua **home directory**. 

---
se la shell si presentasse in questo modo :
```console 
    giovanni@server:~/Documenti/informatica~$
 ```
significa che giovanni sta lavorando nella directory informatica  che si trova nella directory Documenti che si trova nella sua home directory .

---
se la shell si presentasse in questo modo :
```console 
    giovanni@server:/usr/bin$
 ```
significa che giovanni sta lavorando nella directory bin  che si trova nella dirctory bin che si trova nella **root directory** segnalato con  lo slash iniziale **/**. Osserva che non c'è la tilde iniziale.

----
se la shell si presentasse in questo modo :
```console 
    root@server:/usr/bin#
 ```
significa che stiamo lavorando con il superutente root  nella directory bin  che si trova nella directory bin che si trova nella **root directory** segnalato con  lo slash iniziale **/**. 

**Non confondere** la **root directory,** spesso abbreviato con "la root" e **l'utente root**. 

## ancora di più :

l'aspetto del prompt può variare nel suo aspetto. Può essere configurato per ogni utente, per distribuzione, per shell installata ....

quello presentato qui è il prompt con l'aspetto più comune e famoso della shell bash.

È possibile personalizzare il prompt modificando la variabile di sistema PS1 seguendo alcune regole.
Per intenderci, questo è il valore di default di PS1 su un sistema Debian:
```console 
PS1=\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$
```










