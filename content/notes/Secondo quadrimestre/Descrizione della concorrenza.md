## Esecuzione parallela
Per eseguire un processo non sequenziale c'è la necessità di utilizzare:
- Un elaboratore non sequenziale;
- un linguaggio di programmazione non sequenziale.

L'elaboratore non sequenziale è una macchina che è in grado di eseguire più operazioni contemporaneamente. Distinguiamo tali macchine in sistemi multiprocessori o multielaboratori dove abbiamo il parallelismo fisico, e sistemi monoprocessori multiprogrammati con parallelismo virtuale.

I linguaggi non sequenziali sono i linguaggi di programazione che consentono la programmazione delle attività concorrenti. Tali linguaggi concorrenti, di alto livello, implementano nuove istruzioni come i costrutti **fork-join** e **cobegin-coend**.

### fork-join
Le istruzioni fork-join servono a descrivere l'esecuzione parallela tramite la scomposizione di due processi e la riunione in un unico processo:
- L'istruzione fork corrisponde alla biforcazione di un nodo in due rami, quindi la creazione di un processo figlio che inizia l'esecuzione in parallelo con il processo padre;
- L'istruzione join viene eseguita quando il processo figlio termina la sua esecuzione e si sincronizza con il processo padre.

### cobegin-coend
Le istruzioni cobegin-coend permettono di indicare un punto in cui più processi iniziano contemporaneamente l'esecuzione (**cobegin**) e il punto in cui terminano, unendosi al processo principale (**coend**).
I costrutti cobegin-coend sono più semplici da utilizzare e il codice ottenuto è più strutturato e comprensibile, dato che tramite il fork-join trasformiamo il codice in strutture simili ai vecchi linguaggi di programmazione che utilizzavano l'istruzione di salto (**goto**).