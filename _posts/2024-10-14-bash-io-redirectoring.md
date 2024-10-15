---
title: "I/O redirection in linux"
categories:
  - Blog
tags:
  - bash
  - linux 
  - redirection 

permalink: /blog/bash-redirection/
---
TLDR: `>` `<`: redirigono l'output e l'input di un comando in un file e da un file.


lanciare il comando:
```console 
ls -l /etc/
```
a video mostra il contenuto della directory `/etc` (che per informazione è una directory dove linux memorizza varie configurazioni di sitema)

ora lanciate il comando:

```console 
ls -l /etc/ > risultato.txt 
```
a video il comando non mostra nulla, 

dove è finito l'output ?

```console 
ls -l risulta*
```
c'è ora un file creato da pochissimo, visualizziamone il contenuto con :
```console 
cat risultato.txt
```
l'output del comando dato all'inizio è ora memorizzato nel file `risultato.txt`.

>  l'operatore `>` serve per reindirizzare lo standard output di un comando in un file 

ora lancia i comandi:
```console 
ls -l > risultato.txt
```
Cosa conterrà il file risultato?
Scopriamolo con :
```console 
cat risultato.txt
```
il contenuto precedente viene sovrascritto.


ora proviamo:
```console 
date >> cheoresono.txt
```

poi lanciatelo più volte aspettando un secondo tra un comando e l'altro.

lanciate più volte :
```console 
date >> cheoresono.txt
```
e poi :

```console
    whoami >> cheoresono.txt
```

ora vediamo cosa contiene il file :
```console 
cat  cheoresono.txt
```

> l'operatore `>>` reindirizza l'output _appendendolo_ su un file.

### Input redirection 

sul sistema che state usando è installato un comando `scomponi`. Questo comando chiede in input una serie di numeri (maggiori di uno ) e ne stampa la sua scomposizione in fattori primi (se non sapete che cosa è chiedete alla prof.ssa di matematica ).

lanciatelo:
```console
scomponi
```

Per interrompere il programma bisogna premere <kbd>ctrl</kbd> + <kbd>d</kbd> 

Dopo aver preso confidenza con il comando `scomponi` 
lanciate il comando :

```console
nano numeridascomporre.txt
```

e scrivete nel file :
```console
24
68
89
128
503
31
16

```

salvate il file con <kbd>ctrl</kbd> + <kbd>s</kbd>

uscite da nano con <kbd>ctrl</kbd> + <kbd>x</kbd>

controllate che avete effettivamente salvato il file:
```console
cat numeridascomporre.txt
```

ora lanciate il comando:
```console
scomponi < numeridascomporre.txt
```

Il programma scomponi ora non si ferma a chiedere all'utente i numeri perchè li preleva dal file `numeridascomporre.txt`, quando incontra la fine del file ( eof ) termina.

Il reindirizzammento dell'input funziona anche con tutti i comandi interattivi, sia di sistema sia quelli creati dall'utente (come in questo caso è `scomponi`)


### componendo i reindirizzamenti 

lanciate il comando :
```console
scomponi < numeridascomporre.txt > numeriscomposti.txt 
```

ora il comando preleva l'input dal file `numeridascomporre.txt` e non stampa più nulla a video perchè lo stampa nel file `numeriscomposti.txt`-

lanciate:
```console
cat numeriscomposti.txt
```

### esercizio sfida:

crea un file `10000scomposti.txt` con la scomposizione dei numeri da 2 a 10000,

suggerimento : creare un file  con i numeri da 2 a 10000 e _darlo in pasto_ a `scomponi` con il reindirizzamnto dell'input. ( sai compilare un file c++  ? )

suggerimento2 : cercare un comando bash/linux che stampi i numeri da 2 a 10000 per creare il file da dare in input

suggerimento3 : evita la creazione del file da dare in input studiando da solo il _piping dei comandi bash_ (cerca sul web)


*svolgi nei tre modi suggeriti l'esercizio*

### esercizio sfida n.2 :
elimina dal file ottenuto nel punto precedente le righe :


```inserire un numero >1 da scomporre in fattori primi, [ ctrl ] + [ d ] per uscire 
```

suggerimento : studia (cercando sul web) il comando `grep` 


