---
title: "linux command: head tail"
categories:
  - Blog
tags:
  - bash
  - linux 
  - head 
  - tail 

permalink: /blog/bash-head-tail/
---
TLDR: `head` `tail`: mostrano la parte iniziale / finale di un file a terminale.


lanciare il comando
```console 
wget {{ site.url }}{{ site.baseurl }}/assets/text/hack.txt 
```


lanciare il comando 
```console 
cat hack.txt 
```
ha mostrato tutto il contenuto del file appena scaricato.

```console 
cat -n hack.txt 
```
ha mostrato il contenuto del file numerando le righe.

## head
sintassi:

```console
head [options] [file]
````

ora provate :
```console 
head hack.txt 
```
mostra le prime 10 linee (default) del file. Osserva che per linea si intende ogni carattere compreso tra due _"a capo"_

prova il comando con varie opzioni :
```console 
head -n 3 hack.txt 
```

```console 
head -3 hack.txt 
```

per verificare che sono effettivamente le prime 3 linee, lancia il comando

```console 
head -3 hack.txt | cat -n
```

## tail 

sintassi:

```console
tail [options] [file]
````

per l'elenco completo delle opzioni lanciate `tail --help`.

non è molto diverso da head : la differenza che mostrera le ultime righe invece dell prime.



ora provate :
```console 
tail hack.txt 
```
mostra le ultimr 10 linee (default) del file.
prova il comando con varie opzioni :
```console 
tail -n 3 hack.txt 
```

```console 
tail -3 hack.txt 
```

per verificare che sono effettivamente le prime 3 linee, lancia il comando

```console 
cat -n hack.txt| tail -3
```


##di più

`tail` e `head` posso essere usati in _piping_  per mostrare parti centrali di un file.

prova:
```console 
head -40 hack.txt | tail -5
```

per dimostrarlo:
prova:
```console 
cat -n hack.txt | head -40 | tail -5
```


## ancora di più:

il comando `tail` ha un importante opzione `-f` che mostra le ultime righe in tempo reale, molto utile per monitorare i file di log che i vari servizi scrivono:

TO BE CONTINUED
