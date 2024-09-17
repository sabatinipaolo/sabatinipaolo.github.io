---
title: "Come funziona una shell, comandi interni esterni"
categories:
  - blog
tags:
  - bash
  - shell
  - comandi esterni
  - comandi interni

permalink: /blog/come-funziona-la-shell/
---
TLDR:
la shell legge in input un comando che può essere interno o esterno, se interno lo esegue se esterno lo sottomentte al sistema 

---

grossolanamente una shell il funzionamento è descritto dallo pseudo codice seguente ;


```console 

   while ( true )
       stampa il prompt;  
       legge una stringa ;

       if ( stringa == "exit" )  chiudi shell 

       if ( stringa è un comando della shell )
          esegui comando 
          continue;

       else 
        // è un comando esterno 
          sottometti al sistema il comando stringa


 ```   



per conoscere se un comando è interno o esterno si usa il comando **`type`**

esempi:
```console
    giovanni@server:~$ type cd 
    cd è un comando interno di shell

```
```console
    giovanni@server:~$ type rm
    rm è /usr/bin/rm
  
```
qui il comando type ci comunica che **`rm`** non è un comando interno, ma è un programma installato nella directory /usr/bin 

```console
    giovanni@server:~$ type type
    type è un comando interno di shell

```
