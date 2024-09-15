---
title: "Il prompt di Bash "
categories:
  - blog
tags:
  - bash
  - prompt

permalink: /blog/il-prompt-di-bash/
---
  

Quando apriamo un terminale, la shell potrebbe darci qualche riga di benvenuto e poi un _**"prompt"**_ (qualcosa che ci invita/esorta ad inserire dei comandi).
 

Quello di bash ha il seguente aspetto:

    	 
	giovanni@server:~$
    

**`giovanni`** è l'utente con cui si sta lavorando 
**`server`** è l'hostname della macchina su cui giovanni sta lavorando 

**`~`**  significa che giovanni sta attualmente lavorando nella sua **home directory**

`$` serve a ricordare che giovanni è un **utente semplice**, altrimenti al posto del dollaro avremmo **`#`** che significa stiamo lavorando con il **super utente** **`root`**

## di più : 

se la shell si presentasse in questo modo :

    giovanni@server:~/Documenti~$

significa che giovanni sta lavorando nella directory Documenti che si trova nella sua **home directory**. 

---
se la shell si presentasse in questo modo :

    giovanni@server:~/Documenti/informatica~$

significa che giovanni sta lavorando nella directory informatica  che si trova nella directory Documenti che si trova nella sua home directory .

---
se la shell si presentasse in questo modo :

    giovanni@server:/usr/bin$

significa che giovanni sta lavorando nella directory bin  che si trova nella dirctory bin che si trova nella **root directory** segnalato con  lo slash iniziale **/**. Osserva che non c'è la tilde iniziale.

----
se la shell si presentasse in questo modo :

    root@server:/usr/bin#

significa che stiamo lavorando con il superutente root  nella directory bin  che si trova nella directory bin che si trova nella **root directory** segnalato con  lo slash iniziale **/**. 

**Non confondere** la **root directory,** spesso abbreviato con "la root" e **l'utente root**. 








