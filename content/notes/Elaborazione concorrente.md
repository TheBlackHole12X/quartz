---
title: "Elaborazione concorrente"
---
## Generalità
### Elaborazione Sequenziale vs Elaborazione Concorrente

Per elaborazione sequenziale si intende l'esecuzione di un programma sequenziale le cui istruzioni vengano eseguite una dopo l'altra in un determinato ordine, quindi un'operazione deve essere completata prima che inizi una successiva operazione. 

Per elaborazione concorrente intendiamo invece le tecniche e strumenti che descrivono il comportamento di processi paralleli, ovvero più processi che vengono eseguiti contemporaneamente.

La vera elaborazione concorrente si verifica solo quando si è in presenza di architetture multiprocessore, perché, come sappiamo, nei sistemi monoprocessori il parallelismo avviene virtualmente grazie al multitasking.

Possiamo parlare infine di sistema concorrente, ovvero un sistema software che manda avanti l'esecuzione di più processi che possono **cooperare** ad un obiettivo comune o **competere** per utilizzare **risorse condivise**.