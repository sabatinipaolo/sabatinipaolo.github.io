---
title: "esercizio sui caratteri jolly "
categories:
  - blog
tags:
  - bash
  - shell
  - cli
  - caratteri jolly
  - asterisco

permalink: /blog/caratteri-jolly/
---
TLDR: esercizio su `ls` con caratteri jolly * , ?

Lanciare il comando :

```console
    $ touch sezione_{a,b,c,d}.{doc,jpeg}
```

il comando sfrutta la caratteristica dell'espansione dei nomi dei file di bash per creare in un solo colpo molti file.
per vedere l'effetto lancia il comando

```console
    $ ls -1 
```
qui abbiamo usato l'opzione `-1` in modo da stampare la lista dei file su una colonna.

Lancia quindi i comandi:
```console
    $ touch lezione_{inf,sis,tpsit}.pdf
    $ touch testo{1,2,3,4,5}.txt
    $ touch regione{lazio,liguria,puglia}.doc
    $ touch voti_{1,2,3,4,5}_anno.txt
    $ touch circ_{1,2,3,4,5,6,8}.pdf
```

----
### carattere 
----


```console 
    $ ls *pdf
```

elenca i file che terminano con `pdf`

----


```console 
    $ ls *doc
```

elenca i file che terminano con `doc`

----


```console 
    $ ls sezione*
```

elenca i file che iniziano  con `sezione`

----



```console 
    $ ls sezione*doc
```

elenca i file che iniziano con `sezione` e terminano con `doc`

----

to be continued