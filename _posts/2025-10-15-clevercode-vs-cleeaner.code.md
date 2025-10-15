---
classes: wide
title: "Clever Code vs Clear Code"
categories:
  - blog
tags:
  - perle saggezza
  - clean code 
  
permalink: /blog/clevercode/
---
## **"Clever Code" vs "Clear Code"**

Spesso i programmatori si complicano inutilmente la vita ..

Questo comportamento è così comune che ha un nome preciso nel gergo della programmazione:



### **CLEVER CODE** (quello dell'autore):
```
roba inutilmente complicata  //TODO: fare un esempio ...puntatori invece di un indice, cilo per stampare due variabili ...  

```

### **CLEAR CODE** (la soluzione semplice):
```cpp
la soluzione semplice //TODO: fareesempio
```

## Perché i programmatori cadono in questa trappola:

1. **Desiderio di astrazione**: "Posso evitare di ripetere queste due parole!"
2. **Sottovalutazione della manutenibilità**: "Tanto lo capisco io"
3. **Over-engineering**: "Se uso le macro, puntatori, lambda  sembro più esperto"
4. **Falsa sensazione di eleganza**: "Look how clever I am!"

## Le conseguenze di essere "too clever":

### **1. Il mantenitore del codice (spesso tu stesso dopo 6 mesi)**
```cpp
// ❓ Tra 6 mesi: "Cosa diavolo significa c_extr?"
// ⏳ Perde 10 minuti a cercare di capire la macro
// 😠 Maledice l'autore originale
```

### **2. Il debug diventa un incubo**
```
//TODO : fare esempio

```

### **3. Il nuovo team member**
```cpp
// 🆕 Nuovo sviluppatore: "Ma perché non usano semplicemente un indice?"
// 🤯 Perde fiducia nella codebase
// 📉 Riduzione della produttività del team
```

## La saggezza dei programmatori esperti:

> **"Write code for humans, not for computers"** - Scrivi codice per umani, non per computer

> **"Debugging is twice as hard as writing the code in the first place. Therefore, if you write the code as cleverly as possible, you are, by definition, not smart enough to debug it."** - Brian Kernighan

## Casi dove "clever" è giustificato (questo non è uno di quelli):

```cpp
// ✅ Esempio di clever code GIUSTIFICATO (metaprogrammazione template)
template<typename T>
constexpr auto type_name() {
    // Magia template complessa ma necessaria
    // per ottenere il nome del tipo a compile-time
}


```

## Come evitare questa trappola:

1. **KISS Principle**: Keep It Simple, Stupid
2. **YAGNI**: You Ain't Gonna Need It (non implementare funzionalità "nel caso servano")
3. **Code Reviews**: Qualcuno avrebbe fermato questa macro
4. **Readability First**: Se non è immediatamente chiaro, è sbagliato
