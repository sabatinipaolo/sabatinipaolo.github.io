---
classes: wide
title: "Esercitazione grep "
categories:
  - blog
tags:
  - bash
  - linux
  - esercitazione 
  - grep


permalink: /blog/ese-guidata-grep/
---
TLDR: esercitazione guidata per studiare il comando **`grep`** dalle basi fino a funzioni più avanzate come le espressioni regolari e le opzioni per modificare l'output.

### Obiettivi:
- Imparare a utilizzare **`grep`** per cercare stringhe di testo in file.
- Imparare le opzioni principali di **`grep`**.
- Eseguire ricerche avanzate usando le espressioni regolari.
  

--- 

### Parte 1: Ricerca base con `grep`

#### 1.1. Creazione di un file di esempio
Prima di iniziare, crea un file di testo con cui lavorare. 
```bash 
    nano file.txt
```
scrivi il seguente contenuto:
```
Ciao mondo
Grep è un comando utile
Puoi usarlo per cercare testo nei file
grep supporta anche espressioni regolari
viene usato moltissimo
grep è così utile che ha dato
origine a un terribile neologismo: grepping
in italiano suonerebbe ancora più terribile: greppare

```

verifica il contenuto con:
```bash
cat file.txt
```


#### 1.2. Uso base di `grep`
Il comando **`grep`** può essere usato per cercare una stringa specifica in un file.

Esercizio: Trova tutte le righe che contengono la parola **`grep`**.

```bash
grep "grep" file.txt
```

output:

```
grep supporta anche espressioni regolari
grep è così utile che ha dato 
origine a un terribile neologismo: to grepping
in italiano suonerebbe ancora più terribile: greppare
```

a differenza di `cat` grep ha filtrato le righe dove è presente la stringa`"grep"`.

Ora prova :
```bash
grep "ne" file.txt
```

output:
```
Puoi usarlo per cercare testo nei file
viene usato moltissimo
origine a un terribile neologismo: to grepping
in italiano suonerebbe ancora più terribile: greppare
```



#### 1.3. `grep` è case-sensitive
Di default, **`grep`** distingue tra lettere maiuscole e minuscole.

Esercizio: Prova a cercare la stringa **`Grep`** (con la G maiuscola).

```bash
grep "Grep" file.txt
```

output:

```
Grep è un comando utile
```

#### 1.4. Ignora le differenze tra maiuscole e minuscole
Usa l'opzione `-i` per fare una ricerca **_case-insensitive_**.

Esercizio: Cerca di nuovo la stringa **`grep`**, ignorando maiuscole e minuscole.

```bash
grep -i "grep" file.txt
```
ha differenza di prima ha incluso sia lighe con `grep` sia quelle con `Grep` (con la G maiuscola)

#### 1.5. effettua la ricerca con le parole intere
Usa l'opzione `-w` per ricercale le paorole intere.

Esercizio: Cerca la parola **`grep`**.

```bash
grep -w "grep" file.txt
```
output:
```
grep supporta anche espressioni regolari
grep è così utile che ha dato 
```

Esercizio: Cerca la parola **`grep`** in modo **_case-insensitive_**.

```bash
grep -wi "grep" file.txt
```
output:
```
Grep è un comando utile
grep supporta anche espressioni regolari
grep è così utile che ha dato 
```
---

### Parte 2: Opzioni utili di `grep`

#### 2.1. Mostra il numero di riga
Usa l'opzione `-n` per mostrare il numero di riga in cui si trova il testo cercato.

Esercizio: Trova la parola **`grep`** e visualizza il numero di riga.

```bash
grep -n "grep" file.txt
```

output:
```
4:grep supporta anche espressioni regolari
6:grep è così utile che ha dato 
7:origine a un terribile neologismo: to grepping
8:in italiano suonerebbe ancora più terribile: greppare

```



#### 2.2. Conta le occorrenze
Usa l'opzione `-c` per contare quante volte una parola appare in un file.

Esercizio: Conta quante volte appare la parola **`grep`**.

```bash
grep -c "grep" file.txt
```

output:
```
4
```

Esercizio: Conta quante volte appare la parola **`grep`** in modo case-insensitive.

```bash
grep -ci "grep" file.txt
```

Risultato atteso:

```
5
```

ricodi? c'era una riga con `Grep` (con la G maiuscola)



#### 2.5. Escludi righe con una parola specifica
Usa l'opzione `-v` per escludere le righe che contengono una parola specifica.

Esercizio: Escludi le righe che contengono la parola **`grep`**.

```bash
grep -v "grep" file.txt
```

output:
```
Ciao mondo
Grep è un comando utile
Puoi usarlo per cercare testo nei file
viene usato moltissimo

```
#### 2.6. Visualizza qualche riga prima della riga filtrata
Usa l'opzione **`-B  n`** per visualizzare **`n`** righe prima delle righe filtrate.

Esercizio: Visualizza 2 righe prima di quelle che contengono la parola **`viene`**.

```bash
grep -B 2  "viene" file.txt
```

output:
```
Grep è un comando utile
Puoi usarlo per cercare testo nei file
viene usato moltissimo
```
#### 2.7. Visualizza qualche riga dopo la riga filtrata
Usa l'opzione `-A `_n_` ` per visualizzare _n_righe dopo le righe filtrate.

Esercizio: Visualizza 1 riga dopo  quelle che contengono la parola **`viene`**.

```bash
grep -A 1  "viene" file.txt
```

output:
```
viene usato moltissimo
grep è così utile che ha dato 
origine a un terribile neologismo: to grepping

```
#### 2.8. Composizione delle opzioni -A e -B

Esercizio: Visualizza 1 riga prima e 2 righe dopo le righe che contengono la parola **`Puoi`**.
```bash
grep -B 1 -A2  "Puoi" file.txt
```


#### 2.9 Uso di grep con piping
`grep` è comunemente usato nella forma in piping con qualche comando.

Esercizio: Visualizza 1 riga prima e 2 righe dopo le righe che contengono la parola **`Puoi`**.
```bash
cat file.txt | grep -B 1 -A2  "Puoi" 
```
l'output del comando cat viene dato in input a grep. In questo caso abbiamo digitato solo dei caratteri in più.

Ma è utilissimo quando l'output di qualche comando mostra centinaia di righe:

lancia : 
```bash
ps -A
```
questo comando mostra i processi attivi sul sstema con il proprio PID.
ora lancia :

```bash
ps -A | grep ssh
```
nota che ha filtrato le righe dove è presente la stringa **`ssh`** e non c'è stato bisogno di usare le virgolette






---
### DI PIÙ:
### Parte 3: Espressioni regolari con `grep`

#### 3.1. Cerca una parola che inizia con una determinata lettera
Usa l'opzione `-E` per abilitare le espressioni regolari estese.

Esercizio: Trova le righe che contengono parole che iniziano con la lettera **`P`**.

```bash
grep -E "\bP\w+" file.txt
```

output:

```
Puoi usarlo per cercare testo nei file
```

#### 3.2. Trova tutte le righe che finiscono con una parola specifica
Usa il simbolo `$` per indicare la fine di una riga.

Esercizio: Trova tutte le righe che finiscono con la stringa **`le`**.

```bash
grep "le$" file.txt
```

output:

```
Grep è un comando utile
Puoi usarlo per cercare testo nei file
```

> **per studiare le espressioni regolari utili per la manipolazione di stringhe vedere questo bellisimo sito: [https://regex101.com/](https://regex101.com/)**
---


#### 3.3. Cerca più parole contemporaneamente
Usa l'opzione `-E` (o `egrep`) per abilitare le espressioni regolari estese e cerca più parole contemporaneamente.

Esercizio: Cerca le righe che contengono la parola **`viene`** o la parola **`file`**.

```bash
grep -E "file|viene" file.txt
```
output:
```
Puoi usarlo per cercare testo nei file
viene usato moltissimo
```
