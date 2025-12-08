---
classes: wide
title: comandi cisco per configurare un dhcp server
categories:
- Blog
tags:
- 
- 
permalink: /blog/cisco-dhcp

---

La configurazione di base segue questa logica: **escludere gli indirizzi statici, definire un pool di indirizzi dinamici e specificare i parametri di rete da inviare ai client**.

###  Configurazione Base del Server DHCP

In modalità configurazione globale (`configure terminal`).

1.  **Escludere Indirizzi Statici (Obbligatorio)**
    Impedisce al server di assegnare indirizzi riservati a server, gateway o altri dispositivi statici.

    
    ```cisco
    ! Per escludere un singolo indirizzo (es. il gateway .1)
    Router(config)# ip dhcp excluded-address 192.168.1.1

    ! Per escludere un intervallo (es. da .1 a .10)
    Router(config)# ip dhcp excluded-address 192.168.1.1 192.168.1.10
    ```

2.  **Creare un Pool DHCP (Obbligatorio)**
    Definisce il nome del pool e l'intervallo di rete da cui assegnare gli indirizzi.
    ```cisco
    Router(config)# ip dhcp pool NOME_POOL
    Router(dhcp-config)# network 192.168.1.0 255.255.255.0
    ```

3.  **Specificare i Parametri per i Client (Obbligatori/Raccomandati)**
    All'interno della configurazione del pool (`dhcp-config`), imposta i parametri che il server invierà ai client.
    ```cisco
    ! Il Gateway predefinito (Default Router)
    Router(dhcp-config)# default-router 192.168.1.1

    ! I Server DNS
    Router(dhcp-config)# dns-server 8.8.8.8 8.8.4.4

    ! Il Dominio DNS
    Router(dhcp-config)# domain-name tueazienda.local

    ! La Durata del Lease (affitto) in giorni, ore, minuti
    Router(dhcp-config)# lease 0 2 0 ! (2 ore)
    Router(dhcp-config)# lease infinite ! (per sempre)
    ```

###  Configurazioni Avanzate e Utili

| Scenario | Comandi di Configurazione |
| :--- | :--- |
| **Assegnare un IP Fisso (Reservation)** | `Router(dhcp-config)# host 192.168.1.50 255.255.255.0`<br>`Router(dhcp-config)# client-identifier 01aa.bbcc.ddee.ff`<br>`Router(dhcp-config)# client-name NOME_CLIENT` |
| **Impostare Opzioni Personalizzate** (es. Server NTP) | `Router(dhcp-config)# option 42 ip 192.168.1.200` |
| **Configurare Relay per Altre Reti** | `Router(config)# interface GigabitEthernet0/1`<br>`Router(config-if)# ip helper-address 192.168.2.1` |
| **Abilitare il Controllo dei Conflitti** | `Router(config)# ip dhcp ping packets 3`<br>`Router(config)# ip dhcp ping timeout 100` |

###  Verifica e Manutenzione

Per configurazioni più complesse (come più pool per VLAN diverse) o se hai un modello specific

| Comando | Cosa Mostra | Descrizione e Esempio |
| :--- | :--- | :--- |
| **`show ip dhcp pool`** | I dettagli di tutti i **pool DHCP** configurati. | Mostra il nome del pool, l'intervallo di indirizzi, quanti indirizzi sono stati assegnati (`In use`) e quanti sono esclusi, con una percentuale di utilizzo. |
| **`show ip dhcp server statistics`** |  Verifica che il servizio DHCP sia attivo| |
| **`show ip dhcp binding`** | Tutte le **assegnazioni attive** (lease). | Elenca gli indirizzi IP attualmente affittati ai client, con i relativi indirizzi MAC, la data di scadenza del lease e il tipo di assegnazione. È l'equivalente della "tabella dei lease". |
| **`show ip dhcp server statistics`** | Le **statistiche** di funzionamento del server. | Conta quante richieste DHCP di ogni tipo (DISCOVER, OFFER, REQUEST, ecc.) sono state ricevute ed elaborate. Fondamentale per il monitoraggio e la risoluzione dei problemi. |
| **`show ip dhcp conflict`** | I record di **conflitto di indirizzi IP**. | Se il server (tramite ping o gratuitous ARP) rileva che un indirizzo è già in uso, lo segna come conflitto e lo rimuove dal pool. Questo comando mostra tali record. |
| **`show ip dhcp import`** | I parametri **importati** da un server centrale. | Mostra le opzioni DHCP (come DNS e nome dominio) importate da un server esterno tramite il comando `import all`. |
| **`show running-config \| section dhcp`** | La **configurazione corrente** relativa al DHCP. | Comando universale. Filtra la configurazione in esecuzione mostrando solo le sezioni che contengono "dhcp", come i pool (`ip dhcp pool`) e gli indirizzi esclusi (`ip dhcp excluded-address`). |

