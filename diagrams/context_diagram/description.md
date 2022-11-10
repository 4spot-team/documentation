# Commento al Diagramma di Contesto

## Utente


### Registrazione Account

* L'utente registra un nuovo Account (RF2). Durante la registrazione fornisce
email, username, password, metodi di pagamento, metodo di accredito e altre
informazioni personali fra cui le preferenze per le categorie Evento.
* Il sistema risponde con l'esito della registrazione, che può fallire nel caso
in cui l'email non sia valida, l'Account creato esista già, la password non rispetti
i criteri stabiliti o i metodi di pagamento / accredito non siano validi


### Login

* L'Utente effettua il Login al Sistema fornendo email e password (RF3)
* Il Sistema risponde con l'esito dell'autenticazione, che fallisce nel caso
in cui le credenziali fornite non corrispondano a nessun Account


### Recupero Password

* L'Utente può richiedere il recupero della Password (RF26) specificando un
indirizzo email per il recupero (che deve essere associato all'Account)
* Il Sistema risponde con l'esito dell'operazione, che può essere negativo
nel caso in cui l'indirizzo di posta elettronica fornito non corrisponda
a nessun Account esistente. In caso contrario, invia una mail all'indirizzo
di cui sopra con un link per la modifica della password


### Modifica Area Profilo

* L'Utente può modificare le proprie informazioni personali o i metodi di
pagamento / accredito dalla propria Area Profilo (RF4).
* Il Sistema risponde con l'esito della modifica, che può non andare a buon fine
nel caso in cui i metodi di pagamento o il metodo di accredito non siano validi


### Visualizzazione Pagina

* L'Utente può richiedere di visualizzare una specifica Pagina (Home,
Mappa, Utente, Evento, ...)
* Il Sistema risponde con la visualizzazione della suddetta pagina

### Ricerca Evento/Utente

* L'Utente può (dalla pagina "Mappa") ricercare uno specifico Evento o Utente
* Il Sistema risponde con una lista di risultati filtrati dalla lista completa
di Eventi e Utenti tramite matching lessicografico con l'input fornito

### Pubblicazione/Cancellazione Evento

* L'Utente può pubblicare (RF9) o cancellare (RF13) un Evento
* Il  Sistema risponde con l'esito dell'operazione
* Nel caso di cancellazione di un Evento, il Sistema notifica tutti i suoi 
partecipanti

### Iscrizione/Disiscrizione a un Evento

* L'Utente può iscriversi (RF15) o disiscriversi (RF16) a/da un Evento.
* Il Sistema risponde con l'esito dell'operazione

### Acquisto Biglietti

* L'Utente può acquistare un biglietto (RF11) per un Evento (utilizzando
uno dei metodi di pagamento specificati nell'Area Profilo (RF4))
* Il Sistema risponde con l'esito dell'acquisto. In caso positivo, fornisce
all'Utente un QR Code per la partecipazione all'Evento
* Nel caso di Evento cancellato, il Sistema si occupa di rimborsare l'Utente
dell'acquisto del biglietto (il rimborso non viene effettuato in caso di
disiscrizione dall'Evento)

### Vendita Biglietti

* Il Sistema, per un determinato Evento a pagamento, invia all'Utente 
Organizzatore la somma delle vendite dei biglietti (utilizzando il metodo
di accredito specificato nell'Area Profilo)

### Following

* Un Utente A può decidere di seguire (RF19) un altro Utente B.
* Il Sistema risponde all'Utente A con l'esito dell'operazione e notifica
l'Utente B del nuovo follower.
* Nel caso in cui l'Utente B seguisse l'Utente A, i due Utenti diventerebbero
Amici e verrebbero entrambi notificati dal Sistema della nuova Amicizia

### Rating

* A seguito della partecipazione ad un Evento (riscontrabile tramite QR Code)
il Sistema notifica l'Utente partecipante con una richiesta di Rating (RF20)
per l'Evento in questione.
* L'Utente partecipante può effettuare il Rating dell'Evento

### Commenti

* Un Utente con i diritti di visibilità per un determinato Evento può commentare 
l'Evento in questione (RF21)

### Messaggi

* Un Utente può inviare un Messaggio (RF22) a un altro Utente o in una Chat
di Gruppo Evento.
* Nel caso in cui l'Utente riceva un Messaggio, questo viene notificato dal 
Sistema
* Un Utente Organizzatore può creare una Chat di Gruppo Evento con i partecipanti
a uno dei suoi Eventi attivi (non ancora avvenuti)

### Segnalazione

* Un Utente può decidere di segnalare (RF23) un Commento ad un Evento, un Evento
o un Messaggio. 
* Il Sistema, in seguito alla decisione del Gestore di Servizio, blocca 
l'Account dell'Utente segnalato (più volte) comunicandogli un recapito mail
del Gestore di Servizio (di cui sopra). L'Account dell'Utente rimarrà 
bloccato fino a nuova decisione del Gestore di Servizio, nel cui caso
il Sistema sbloccherà l'Account
* Un Utente A può decidere di bloccare o sbloccare la Chat privata con un altro
Utente B

### Cancellazione Account

* Un Utente può richiedere la cancellazione del suo Account


## Banca / PayPal

### Pagamenti

* Il Sistema può disporre un pagamento nei confronti di un Utente (per 
l'accredito di biglietti venduti o per il rimborso di un biglietto).
* La Banca risponde con l'esito dell'operazione
* La Banca notifica il Sistema nel caso di pagamenti ricevuti da parte di 
uno o più Utenti per l'acquisto di biglietti

## Database (MongoDB)

* Il Sistema può richiedere un accesso in Lettura (R) ai Dati Utente, ai
dati Evento, o ai dati Chat
* Il Database, a seguito di una query, risponde con i risultati richiesti
* Il Sistema può richiedere accesso in Scrittura (W) ai Dati Utente, Evento
o Chat
* Il Database riceve i nuovi dati e li sostituisce a quelli vecchi

## Google Maps API

* Il Sistema richiede i dati Mappa all'API
* L'API risponde con i dati richiesti

## Google Gmail API

* Il Sistema utilizza l'API per l'invio di mail

## QR Code API

* Il Sistema può richiedere la generazione di un QR Code all'API per la 
partecipazione ad un Evento
* L'API notifica il Sistema nel caso in cui un QR Code venga attivato (e quindi
un Utente ha effettivamente partecipato ad un Evento)

## Gestore di Servizio

### Visualizzazione Pagine

* Il Gestore di Servizio può richiedere la visualizzazione di una specifica
Pagina (RF30)
* Il Sistema risponde con la visualizzazione della Pagina richiesta

### Segnalazioni e Blocco Account

* Il Sistema notifica il Gestore di Servizio nel caso in cui un Utente
abbia ricevuto 10 segnalazioni (indipendentemente che siano associate
a un Commento, a un Messaggio o ad un Evento)
* Il Gestore di Servizio può richiedere al Sistema di bloccare/sbloccare
l'Account di un determinato Utente a seguito delle segnalazioni

