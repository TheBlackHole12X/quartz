---
title: "{{Sincronizzazione tra processi}}"
---

# Sincronizzazione tra processi

## Errori nei programmi concorrenti
Nella programmazione concorrente possiamo riscontrare maggiori difficoltà rispetto alla programmazione sequenziale, essa infatti ci introduce la possibilità di commettere errori dipendenti dal tempo, più difficili da correggere dato che i normali debugger non hanno la capacità di controllare la correttezza temporale.

Effettuare il testing di un programma concorrente è diverso rispetto ad uno sequenziale:
- dal programma sequenziale riceviamo diversi risultati ma solo in funzione di dati di input diversi, usando casi di prova, il programmatore può verificare i comportamenti del programma mettendo a confronto gli output con i risultati previsti. Se viene accuratamente scelto l'insieme dei dati di prova, possiamo essere più certi sulla correttezza del nostro lavoro;
- nei programmi concorrenti possono verificarsi errori legati ai tempi di esecuzione e schedulazione nella CPU i quali non possono essere determinati ed eliminati tramite il testing, ma devono invece essere evitati tramite una programmazione accurata, localizzando nel codice le parti che possono causare eventuali errori.

Gli errori dipendenti dal tempo sono causati da un'errata sincronizzazione dei processi, essi costituiscono una categoria di errori che possono verificarsi in corrispondenza a determinate velocità relative dei processi e non si riproducono, perciò il sistema dev'essere necessariamente riavviato con le stesse condizioni iniziali.
Le caratteristiche degli errori dipendenti dal tempo sono:
- irriproducibili: possono verificarsi con alcune sequenze e non con altre;  
- indeterminati: esito ed effetti dipendono dalla sequenza;  
- latenti: possono presentarsi solo con sequenze rare;  
- difficili da verificare e testare: perché le tecniche di verifica e testing si basano sulla riproducibilità del comportamento.

Se una risorsa è allocata come dedicata non è necessaria la sincronizzazione mentre se una risorsa è condivisa è necessario assicurare che gli accessi avvengano in modo non divisibile, ovvero le operazioni che un processo deve effettuare sulla risorsa non vengono interrotte neanche dallo scheduler ma si può garantire l'accesso in mutua esclusione fin quando il processo stesso non la rilascia al termine del suo utilizzo in modo da rendere disponibile il risultato dell'elaborazione quando questo è significativo.

Per eseguire le istruzioni in modo concorrente bisogna soddisfare le condizioni di Bernstein.

## Mutua esclusione e sezione critica
Se consideriamo due processi in competizione per l’uso esclusivo di una risorsa comune, non possiamo prevedere il momento preciso nel quale uno dei processi utilizzerà la risorsa, ma dobbiamo garantire che quando ne entra in possesso lo faccia in maniera esclusiva. Ovvero la risorsa verrà utilizzata da un processo alla volta, la quale verrà rilasciata al termine delle operazioni.

**Mutua esclusione**  
Si ha mutua esclusione quando non più di un processo alla volta può accedere a una risorsa comune.

La regola di mutua esclusione impone che le operazioni con le quali i processi accedono alle variabili comuni non si sovrappongano nel tempo: inoltre nessun vincolo è imposto sull’ordine con il quale le operazioni sulle variabili vengono eseguite.

**Sezione critica**
La sequenza di istruzioni con la quale un processo accede e modifica un insieme di variabili condivise prende il nome di sezione critica.

Nel modello a memoria condivisa le risorse comuni condivise saranno le variabili globali che verranno utilizzate dai diversi processi per scambiarsi informazioni.

## Starvation e deadlock
Un’errata sincronizzazione può portare al fallimento delle elaborazioni, genera situazioni di incoerenza dei dati, e può portare a situazioni di blocco dei processi: 
- starvation (o blocco individuale): si verifica quando un processo rimane in attesa di un evento che non accadrà mai, e quindi non può portare a termine il proprio lavoro;
- deadlock (o blocco multiplo): si verifica quando due o più processi rimangono in attesa di eventi che non potranno mai verificarsi a causa di condizioni cicliche nel possesso e nella richiesta di risorse.  