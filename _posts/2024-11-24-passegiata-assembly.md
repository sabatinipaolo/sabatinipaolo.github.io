---
title: "Piccola passeggiata nel mondo dell'assembly, compilatori "
categories:
  - blog
tags:
  - assembly
  - emulatore cpu
  - godbolt  

permalink: /blog/passeggiata-assembly/
---

TLDR: grezziaasima introduzione all'assembly con emulatore cpu on line.

un programma eseguibile è una "_sbrodolata di numeri_", numeri che però la CPU  riconosce come istruzioni che lui è in grado di  eseguire.
L'insieme delle istruzioni che è in grado di eseguire una cpu prende il nome di "instruction set" 

È utile ricordare che : 

- Per essere eseguito un programma deve essere caricato in RAM 


Il simulatore online : si tratta di un simulatore di un piccolo sistema con una CPU a 8bit, e una memoria di 256 Byte (chi sa perché..) 
la CPU ha 4 registri ad uso generale chiamati A B C D , IP Instruction Pointer, SP stack Pointer  e dei flag Z zero, C carry, F Fault .

ecc. ecc. TODO: sviluppare...

Il simulatore è stato scritto da Marco Schweighauser, grazie alla licenza permissiva  con cui è stato rilasciato (licenza MIT) ho potuto fare un fork e fare delle piccolissime modifiche ... 

## diamoci dentro !

caricare i programmi copiando e incollando i numeri nell'area "Code",
eseguirli passo passo e osservare il suo comportamento..

### primo programma:
```
6 2 24 6 2 38 6 1 44 6 1 33
```

con un po' di "reverse engineering ":

 `6 _reg_ _dato_ `, copia (muove) il _dato_ dalla memoria nella cpu nel registro _reg_

 >   codifica di reg 0=A 1=B 2=C 3=D


quesito cosa fa il seguente programma?:

```
    6 3 28 6 1 1 6 2 3 
```


### secondo programma:
```
6 0 18 1 2 0 6 1 3 1 3 1 
```

con un po' di "reverse engineering ":

`1 _reg_dst_ , _reg_src_` , copia (muove )  il contenuto del reg_src in reg_dst

codifica di reg 0=A 1=B 2=C 3=D


### terzo programma :

```
6 0 8 13 0 5 31 3
```

`6 0 8` cosa fa?
`13 0 5` cosa fa ?
come sommo 8 al registro c ? 

e `31 3` ?

`31 _indirizzo_`   sposta l'esecuzione (salta ) del programma all'istruzione che si trova in indirizzo

### QUESITO: 

quesito cosa fa il seguente programma?:
```
    6 3 28 31 8 6 3 0 13 3 1 
```


###  MA NON SAREBBE MEGLIO PROGRAMMARE IN MODO PIÙ UMANO ?.. TIPO COSÌ:

```
MOV C , 24 
MOV C , 38
MOV B, 1
MOV B, 33   
```

È il primo programma ( `6 2 24 6 2 38 6 1 44 6 1 33` ) 

Il secondo programma ( `6 0 18 1 2 0 6 1 3 1 3 1` ) si scriverebbe così:

```
MOV A , 18
MOV C,  A
MOV B,  3
MOV D ,B
```

il terzo (6 0 8 13 0 5 31 3):

```
      MOV A,8 
ciclo:
      ADD A,5
      JMP ciclo
```


### QUESITO :
> cosa fa
>```
     6 3 28 31 8 6 3 0 13 3 1 
```
?



```
       MOV D,28
      JMP salto:
      MOV  D, 0 
salto:
       ADD D,1 
```


### QUESTO È ASSEMBLY !!!!!!
un modo per estendere ai più l'arte di programmare e detronizzare quei pochi che riuscivano ad imparare a memoria gli op-code delle istruzioni ...
Lo ha inventato : [https://hackaday.com/2018/08/21/kathleen-booth-assembling-early-computers-while-inventing-assembly/](https://hackaday.com/2018/08/21/kathleen-booth-assembling-early-computers-while-inventing-assembly/)





> non è possibile darli in "pasto alla cpu così" (la cpu capisce solo numeretti)  
PER  QUESTO SERVE UN TRADUTTORE E UN PASSAGGIO IN PIÙ 

sorgente --> assembla-tore  (assembl -er) ---> [linker (non in questo piccolo sistema) ---> caricare in memoria 


i programmi scritti in linguaggi tipo c/c++, alla fine devono produrre la sbrodolata di numeretti, che poi possiamo considerare assembly ...

questo sito è interessantissimo :

[https://godbolt.org/](https://godbolt.org/)

