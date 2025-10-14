---
classes: wide
title: "URL : anatomia de per esempi"
categories:
  - blog
tags:
  - HTML
  - browser 
  - php
  - post 

permalink: /blog/url-by-example/
---

TLDR: nella maggior parte dei casi un URL è composto da protocollo nome dominio percorso risorsa.



## 1 URL di esempio:

#### `https://sabatinipaolo.github.io/1.html`

Ecco tutte le sue parti:

#### **1. Schema (o Protocollo)**
*   **`https://`**
*   **Cosa fa:** Definisce il **protocollo** che il browser (client) e il server devono usare per comunicare.
*   **Esempi comuni:**
    *   `https` : Protocollo sicuro (crittografato).
    *   `http` : Protocollo non sicuro, sicuro de che?.
    *   `ftp` : Per il trasferimento di file.
    *   `mailto` : Per aprire il client di posta.

#### **2. Host (o "Dominio") o nome DNS dell'host**
```
sabatinipaolo.github.io
```

*   **Cosa fa:** Specifica l'**indirizzo del server** che ospita la risorsa. È il "nome" del sito.
*   Può essere un nome di dominio (come sopra) o un indirizzo IP (come `10.20.20.25`).


#### **3. Path (Percorso)**
*   `/1.html`
*   **Cosa fa:** Specifica la posizione **specifica** della risorsa all'interno del server. Come il percorso di una cartella sul tuo computer.
*   Indica spesso la struttura delle cartelle del sito web.



## 2 URL di esempio:

#### `https://sabatinipaolo.github.io/`

Abbiamo protocollo, nome host 


#### **. Path (Percorso)**
*   `/`
*   stavolta il path non sembra specificare la risorsa  ma solo la web root `/` .

in questo caso il web server potrebbe rispondere facendo vedere l'elenco dei file presenti nella directory (non buono per siti production)

o più frequentemente invia, se presente, un file predefinito seguendo un certo ordine di priorità opportunamente configurato 

esempio apache sul mio computer è configurato così:
```bash
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
```


## 3 URL di esempio:

#### `http://10.20.20.25/~paolo/prova/1.html`

Abbiamo protocollo, nome host , un path più complicato..

#### ** Path (Percorso)**
   `/~paolo/prova/1.html`

    sul web-server c'è a partire dalla web root una directory `~paolo` ( in realtà abbiamo visto che corrisponde a `../publich_html/` ...)
    nella quale c'è una directory `prova/` dove si trova il file `1.html` 

    

## 4 URL di esempio:

#### `https://duckduckgo.com/index.php?q=panini`

Abbiamo protocollo, nome host , un path con `?q=panini`  

#### Query String (Parametri di Ricerca)**
*   `?q=panini`
*   **Cosa fa:** Fornisce **parametri aggiuntivi** per quella risorsa. Viene utilizzata per ricerche, filtri, o per **inviare dati al server**.
*   Inizia con `?`.
*   I parametri sono in coppie `nome=valore`.
*   Le coppie sono separate da `&`.

nel nostro caso il server utilizza il parametro di nome `q` e di valore `panini` per fare una ricerca della parola panini ...

## 6 URL di esempio:

#### `https://sabatinipaolo.github.io/seg/index.html#segnalino`

Abbiamo protocollo, nome host , un path con `#segnalino`.
#### Fragment (Frammento o Anchor)**
*   `#segnalino`
*   **Cosa fa:** Identifica una **parte specifica** all'interno della risorsa stessa.
*   Nel caso di una pagina HTML, il browser scorrerà automaticamente fino alla sezione con l'ID `segnalino`.
*   **Importante:** Il frammento **non** viene inviato al server. Viene gestito solo dal browser.
