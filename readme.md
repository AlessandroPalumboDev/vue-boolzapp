
A questo link trovate il brief di progetto:
https://docs.google.com/document/d/1n7zAM-rjfdqDIzszFA1F6pSZDL4LADU4w8k1RAl8kzM/edit

Vi ricordo di procedere per milestone, e vi consiglio di creare una sorta di avanzamento lavori:
- repo
    - milestone 1
    - milestone 2
    - etc...
Non correte, fate una stima personale di tempo per ogni milestone e dosate le forze!

## Descrizione
- MILESTONE 1
    - Replica della grafica con la possibilità di avere messaggi scritti dall’utente (verdi) e dall’interlocutore (bianco) assegnando due classi CSS diverse
    - Visualizzazione dinamica della lista contatti: tramite la direttiva v-for, visualizzare nome e immagine di ogni contatto

- MILESTONE 2
    - Visualizzazione dinamica dei messaggi: tramite la direttiva v-for, visualizzare tutti i messaggi relativi al contatto attivo all’interno del pannello della conversazione
    - Click sul contatto mostra la conversazione del contatto cliccato

- MILESTONE 3
    - Aggiunta di un messaggio: l’utente scrive un testo nella parte bassa e digitando “enter” il testo viene aggiunto al thread sopra, come messaggio verde
    - Risposta dall’interlocutore: ad ogni inserimento di un messaggio, l’utente riceverà un “ok” come risposta, che apparirà dopo 1 secondo.

- MILESTONE 4
    - Ricerca utenti: scrivendo qualcosa nell’input a sinistra, vengono visualizzati solo i contatti il cui nome contiene le lettere inserite (es, Marco, Matteo Martina -> Scrivo “mar” rimangono solo Marco e Martina)

- MILESTONE 5 - opzionale
    - Cancella messaggio: cliccando sul messaggio appare un menu a tendina che permette di cancellare il messaggio selezionato
    - Visualizzazione ora e ultimo messaggio inviato/ricevuto nella lista dei contatti

## Consigli utili:
- Si possono trascurare le scrollbar verticali, sia nel pannello dei messaggi, che nella lista dei contatti
- I pulsanti e le icone possono non funzionare (a parte l’invio del messaggio)
- Per gestire le date, può essere utile la libreria Luxon

## Svolgimento
- MILESTONE 1
    - Recupero html e css dell'esercizio 'html-css-boolzapp', lo analizzo e modifico replicando la grafica usando vue.js
    - Ritorno array di partenza e contatore indice
    - Creo v-for per stampa di tutti i messaggi di un oggetto specificato dal contatore dell'indice dell'array principale
    - Assegno la classe specifica basandomi sulla chiave status
    - Cre un altro v-for per tutti gli oggetti e stampo solo nome e immagine

- MILESTONE 2
    - Aggiungo evento al click sugli elementi della lista delle chat che cambia il contatore indice 

- MILESTONE 3
    - Dichiaro una chiave di ritorno vuota per il nuovo messaggio
    - Aggiungo v-model al campio di input del messaggio collegato alla chiave vuota
    - Aggiungo evento al clikc che sfrutta la funzione di invio messaggio
    - Creo funzione di invio messaggio che:
        - (se il v-model è diverso da chiave vuota)
            - Pusha oggetto con v-model modificato, data e status: 'sent'
            - Svuota v-model
            - setTimeout di un secondo che pusha un altro oggetto con data, testo:'Ok' e status: 'received'
            - (provo a usare Luxon per la chiave della data)

- MILESTONE 4
    - Creo dato vuoto per il v-model del campo di imput di ricerca
    - Creo metodo che se il v-model viene riempito restituisce (usando .map()) un array di elementi con la chiave .name che contiene il v-model e modifica la chiave .visible a quelli che non lo contengono, altrimenti restituisce l'array di partenza. Tutto .toLowerCase()
    - Uso lo stesso metodo per il v-for della visualizzazione della lista delle chat
    - Aggiungo v-show alla lista che visualizza solo elementi con visible === true

