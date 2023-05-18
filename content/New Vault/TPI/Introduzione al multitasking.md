Un processo é una sequenza di istruzioni che attivano fasi di elaborazioni della cpu,fasi di attesa per l esecuzione di operazioni su altre risorse del sistema che di fatto lasciano inattiva la cpu
nei sistemi operativi multitasking durante le fasi di attesa mandano in esecuzione altri programmi tra quelli caricati in memoria, cio riduce al minimo la non operativitá della cpu migliorando cosi l'efficienza del sistema e rendendo possibile un parallelismo tra i processi che in realta é virtuale dato che il processore é unico 
Possiamo fare una distinzione di parallalelismo in

- multitasking: esecuzione di programmi indipendenti sulla CPU e sul processore di I/O
- multiprocessing: multiprogrammazione estesa a elaboratori dotati di piu CPU e processori di I/O

Un processo é costituito da due parti: 

- Il codice
- I dati del programma

In particolare i dati del programma si suddividono in:
- Variabili globali
- Variabili locali
- Variabili temporanee
- Variabili allocate dinamicamente

L'insieme di tutti i dati di un processo prende anche il nome di conesto del processo e varia istante per istante.
Un processo puo stare in diversi stati 
Per stato di un processo intendiamo la situazione possibile in cui il processo in esecuzione puo trovarsi. In particolare gli stati di un processo sono:
- Nuovo (New)
- Esecuzione(running)
- Attesa (Waiting)
- Pronto (Ready to run)
- Fine (Terminated)
La descrizione di questi stati avviene mediante il modello diagramma di stato