---
title: "{{Semafori}}"
---
## Premessa
I semafori possono essere utilizzati per gestire la mutua esclusione, garantendo che solo un processo o thread alla volta possa accedere alla risorsa condivisa. Inoltre, i semafori possono essere utilizzati per la sincronizzazione tra i processi o thread, permettendo di controllare l'ordine di esecuzione delle operazioni.

## Semafori di basso livello e spinlock()
Il primo meccanismo che analizziamo è quello che associa a ogni risorsa una variabile x o **flag**;
Il flag fa la funzione di **semaforo**:
- x = 1 semaforo verde, è possibile accedere alla risorsa;
- x = 0 semaforo rosso, la risorsa è occupata ed è necessario aspettare che si liberi;
La variabile x semaforo può assumere solamente il valore 0 oppure 1: l’implementazione di questi semafori può essere realizzata con variabili **booleane** che prendono il nome di **spinlock**.

### Allocazione di una risorsa: lock()
La **funzione** che permette di allocare una risorsa prende il nome di lock(). Possiamo indicare la sua sintassi nel seguente formato:
`lock(x);`
dove x è il **semaforo** associato alla risorsa che desideriamo utilizzare.
Questa funzione dovrà:
- **testare** il semaforo per verificarne il suo **colore**;  
- se è **verde**, modificarne il valore a **rosso**;  
- se è **rosso**, aspettare che diventi verde per poi metterlo a **rosso**
```
funzione lock(x)  
inizia  
ripeti 
finche x=1  
x = 0;
fine
```

### Rilascio di una risorsa: unlock()
La **funzione** che permette di rilasciare una risorsa prende il nome di unlock().  
Possiamo indicare la sua sintassi nel seguente formato:
`unlock(x);`
dove x è il **semaforo** associato alla risorsa che desideriamo utilizzare.
La primitiva unlock() deve semplicemente modificare il valore del semaforo da rosso a verde, quindi:
```
funzione unlock(x)  
inizia  
x = 1; 
fine
```
La **mutua esclusione** si ottiene facendo precedere la **lock**(x) a una sezione critica e facendola seguire da una **unlock**(x).
```
...  
lock(x);  
< sezione critica >  
unlock(x);  
...
```

## Semaforo di Dijkstra
Dijkstra ha proposto due funzioni che permettono la soluzione di qualsiasi problema di interazione fra processi, che sono:  
- la funzione **P**(S), che riceve in ingresso un numero intero S non negativo (**semaforo**), che viene utilizzata per accedere alla **risorsa**;  
- la funzione **V**(S), che riceve anch’essa in ingresso un numero intero S non negativo (**semaforo**), che viene utilizzata per rilasciare la **risorsa**.
