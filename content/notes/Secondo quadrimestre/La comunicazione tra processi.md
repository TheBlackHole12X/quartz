## Introduzione
I processi concorrenti interagiscono tra di loro condividendo risorse comuni. Possiamo individuare due modelli di interazione concorrente:
- Modello a memoria comune;
- Modello a scambio di messaggi.

### Modello a memoria comune
Il modello a memoria comune viene utilizzato nelle architetture che usano un' unica memoria comune a tutti i processi, come nel caso delle macchine monoprocessori con processi multitasking, inoltre, il sistema operativo associa ad ogni risorsa un gestore di risorse.

### Modello a scambio di messaggi
Nel caso di un ambiente locale in cui ogni processo ha accesso solo alle risorse allocate nella propria memoria locale, i processi utilizzano lo scambio di messaggi come strumento di comunicazione e sincronizzazione. Questo modello rappresenta un sistema in cui ogni processore ha una memoria privata e opera in un ambiente locale che non è accessibile ad altri processi.

Il modello a scambio di messaggi può essere classificato in vari modi:
- nel caso di comunicazione asincrona la comunicazione da parte del processo mittente avviene senza che questo rimanga in attesa di una risposta da parte del processo destinatario;  
- nel caso di comunicazione sincrona lo scambio di informazioni può avvenire solo se mittente e destinatario sono pronti a “parlarsi” e quindi è necessario che si sincronizzino, e questa interazione prende il nome di **rendez-vous**:
	- stretto: se si limita alla trasmissione di un messaggio dal mittente al destinatario;
	- esteso: se il destinatario, una volta ricevuto il messaggio, deve inviare una risposta al mittente.

Possiamo inoltre distinguere la comunicazione **asimmetrica** e **simmetrica**:
- asimmetrica nel caso in cui il mittente nomina il destinatario ma il destinatario non nomina il mittente;
- simetrica quando entrambi si nominano in modo esplicito.

#### Modello client-server
Le risorse del sistema sono accessibili da un singolo processo che prende il nome di processo servitore (**o server**),  e quando un processo deve utilizzarla (**processo cliente**) non può accedervi direttamente ma deve chiedere al processo server di effettuare lui stesso le operazioni desiderate sulla risorsa e di comunicargli successivamente l’esito delle elaborazioni.