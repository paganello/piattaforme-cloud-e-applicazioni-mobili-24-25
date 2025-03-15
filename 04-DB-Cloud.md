# Tecnologie Cloud & Mobile: Data in the Cloud

*Corso 21069 - Piattaforme Mobile & Cloud*  
*Docente: Mauro Pelucchi (mauro.pelucchi@gmail.com)*

## 4.0 - Introduzione ai Database nel Cloud

L'integrazione dei database nel paradigma cloud rappresenta uno dei più significativi cambiamenti nell'architettura dei sistemi informativi moderni. Prima di addentrarci nelle specifiche tecnologie, è importante chiarire la distinzione fondamentale tra database e DBMS (Database Management System): mentre il database è la collezione di dati strutturati, il DBMS è il software che gestisce l'accesso, l'organizzazione e la manipolazione di tali dati.

I database si dividono in due categorie principali:
- **Database relazionali**: sistemi tradizionali come Microsoft SQL Server, Oracle Database e MySQL
- **Database non relazionali (NoSQL)**: sistemi come MongoDB, Cassandra e Redis

La scelta tra questi due paradigmi dipende fortemente dai requisiti applicativi specifici e dalle caratteristiche di ciascun tipo di database.

## 4.1 - Database Relazionali nel Cloud

I database relazionali sono la scelta ottimale quando:
- È necessario applicare regole di schema rigorose e garantire la qualità dei dati
- Il database non richiede una capacità estrema di lettura/scrittura
- Si dispone di un dataset relazionale che non necessita di prestazioni estreme

In questi casi, un sistema di gestione di database relazionale (RDBMS) rappresenta spesso la soluzione più semplice da implementare.

AWS offre diverse opzioni per database relazionali nel cloud, principalmente:
- **Amazon Relational Database Service (Amazon RDS)**: Si sceglie la macchina, e amazon la esegue gestendola.
- **Amazon Aurora**: Si imposta un numero minimo e massimo di macchine, in base alla necessità di calcolo amazon ne accende di nuove o ne spegne altre, in modo da adattarti al carico. è comunque un sistema gestito, le macchine sono gestite da amazon.

La differenza fondamentale tra servizi gestiti e non gestiti nel cloud sta nella responsabilità della manutenzione. Nei servizi non gestiti, l'utente deve occuparsi di scalabilità, tolleranza ai guasti e disponibilità del sistema. Nei servizi gestiti, queste caratteristiche sono tipicamente integrate nel servizio stesso.

I database relazionali tradizionali presentano diverse sfide che il cloud può aiutare a superare:
- Manutenzione dei server e impronta energetica
- Installazione del software e patch di sicurezza
- Backup del database e alta disponibilità
- Limiti di scalabilità
- Sicurezza dei dati
- Installazione e aggiornamento del sistema operativo

Il passaggio da database on-premises ad Amazon RDS offre numerosi vantaggi in termini di gestione e manutenzione.

Amazon RDS è consigliato quando l'applicazione richiede:
- Transazioni complesse o query complesse
- Una velocità media-alta di query o scrittura (fino a 30.000 IOPS: 15.000 letture + 15.000 scritture)
- Non più di un singolo nodo di lavoro o shard
- Alta durabilità

Al contrario, è sconsigliato quando l'applicazione richiede:
- Tassi massivi di lettura/scrittura (ad esempio, 150.000 scritture/secondo)
- Sharding dovuto a elevate dimensioni dei dati o esigenze di throughput
- Richieste GET o PUT semplici e query che un database NoSQL può gestire
- Personalizzazione del RDBMS

## 4.2 - Database NoSQL e il Teorema CAP

I database NoSQL presentano caratteristiche distintive rispetto ai database relazionali tradizionali:
- Non utilizzano SQL (esempi: HBase, Cassandra, Redis)
- Sono generalmente progetti open source
- La maggior parte funziona su cluster
- Mentre i RDBMS utilizzano transazioni ACID per gestire la consistenza, i database NoSQL impiegano metodi alternativi
- Sono "schema free" o "schema less"
- NoSQL rappresenta più un movimento che una tecnologia specifica
- I RDBMS non scompariranno, ma ora esistono alternative valide

Il Teorema CAP (formulato da Eric Brewer dell'Università della California a Berkeley) afferma che, dei tre attributi dei sistemi di dati distribuiti - Consistenza dei dati, Disponibilità del sistema e tolleranza al Partizionamento della rete - solo due possono essere raggiunti contemporaneamente:

- **CA**: database relazionali tradizionali
- **AP**: le richieste vengono eseguite su ogni nodo anche se violano la consistenza (Cassandra, DynamoDB)
- **CP**: le richieste vengono eseguite solo sui nodi che garantiscono la consistenza (HBase, MongoDB, Google BigTable)

In pratica, il teorema CAP implica che se non è possibile limitare il numero di guasti, le richieste possono essere dirette a qualsiasi server, e si insiste nel servire ogni richiesta ricevuta, allora non è possibile garantire la consistenza.

## 4.3 - Tipologie di Database NoSQL

### Key-Value Stores
Nei key-value stores:
- I dati sono immagazzinati in elementi che contengono una chiave insieme ai dati effettivi
- L'implementazione è più semplice rispetto ad altri modelli
- Risultano meno efficienti se la maggior parte delle operazioni riguarda solo una parte di un elemento
- Ogni chiave è associata a un valore unico, senza duplicati
- Il valore è un oggetto binario chiamato "blob", la cui struttura interna è irrilevante per il database

Esempi di key-value stores includono Redis e DynamoDB.

### Document Stores
I document stores rappresentano un'evoluzione del modello key-value:
- Il valore è solitamente strutturato e interpretabile dal database
- È possibile interrogare i dati in modi più sofisticati rispetto all'uso della semplice chiave

A differenza dei database relazionali, che immagazzinano i dati in tabelle con campi fissi, i document stores archiviano i dati in documenti che possono contenere un numero illimitato di campi di lunghezza illimitata. Questo approccio è particolarmente efficiente quando si dispone di informazioni incomplete o eterogenee: se di una persona si conoscono solo nome e cognome, ma di un'altra anche indirizzo, data di nascita e codice fiscale, si evitano campi inutilizzati che occuperebbero spazio inutilmente.

MongoDB è un esempio principale di document store.

### Column Family Stores
I column family stores, come Google BigTable:
- Prendono il nome dalla loro struttura composta da colonne sparse e assenza di schema rigido
- Non vanno concettualizzati come tabelle, ma come mappe a due livelli
- Mentre molti database utilizzano le righe come unità di memorizzazione, i column family stores sono ottimizzati per scenari in cui è necessario accedere a poche colonne di molte righe

### Graph Databases
I graph databases:
- Immagazzinano i dati sotto forma di strutture a grafo
- Rendono più efficiente l'accesso ai dati da parte di applicazioni orientate agli oggetti
- Sono particolarmente adatti per rappresentare relazioni complesse tra entità

Neo4J è un esempio prominente di graph database.

## 4.4 - MongoDB e DocumentDB in Dettaglio

### Cos'è MongoDB
MongoDB è un database documentale NoSQL con le seguenti caratteristiche:
- Nato nel 2007 (inizialmente come 10gen)
- Prima versione per produzione disponibile nel 2010
- Attualmente alla versione 7
- Database NoSQL orientato ai documenti
- Database hash-based e schema-less
- Nessun linguaggio di definizione dei dati (DDL)
- Ogni documento è identificato da un identificativo (_id)
- Formato BSON (basato su JSON, dove B sta per Binary)
- Le applicazioni gestiscono lo schema dei dati
- Scritto in C++
- Supporta API (driver) per numerosi linguaggi di programmazione: JavaScript, Python, Ruby, Perl, Java, JavaScala, C#, C++, Haskell, Erlang
- Driver predefiniti per Hadoop, strumenti di Business Intelligence, ecc.
- Interfaccia REST
- Multi-piattaforma (Windows, Linux, macOS)
- Disponibile sul cloud (AWS, Azure, GCP) e come MongoDB Atlas

### Funzionalità di MongoDB
MongoDB offre diverse funzionalità chiave:
- Schema dinamico senza necessità di DDL
- Database basato su documenti
- Indici secondari
- Linguaggio di query tramite API
- Scritture atomiche e letture completamente consistenti (se il sistema è configurato in questo modo)
- Replica master-slave con failover automatizzato (replica sets)
- Scalabilità orizzontale integrata tramite partizionamento automatico dei dati basato su range (sharding)
- Non supporta join né transazioni complesse

### Vantaggi di MongoDB
I principali vantaggi di MongoDB includono:
- Query molto semplici
- Linguaggio di scripting potente
- Capacità di scale-out
- Integrazione rapida dei dati
- Non è adatto per transazioni complesse

### MongoDB e il Teorema CAP
Per quanto riguarda il teorema CAP, MongoDB offre:
- Consistenza: tutte le repliche contengono la stessa versione dei dati
- Disponibilità: il sistema rimane attivo in caso di guasti
- Tolleranza al partizionamento: punti di accesso multipli e il sistema rimane attivo in caso di split

### Struttura Gerarchica di MongoDB
- Un'istanza MongoDB può avere zero o più "database"
- Un database può avere zero o più "collezioni"
- Una collezione può avere zero o più "documenti"
- Un documento può avere uno o più "campi"
- Gli "indici" in MongoDB funzionano in modo simile ai loro equivalenti RDBMS

### Confronto tra RDBMS e MongoDB
MongoDB utilizza una terminologia differente rispetto ai database relazionali:
- Database → Database
- Tabella, vista → Collezione
- Riga → Documento
- Colonna → Campo
- Indice → Indice
- Join → Documento incorporato
- Chiave esterna → Riferimento
- Partizione → Shard

### Documenti in MongoDB
MongoDB, come quasi tutti i database NoSQL, memorizza i dati in formato JSON (più precisamente, in formato BSON). Un singolo documento ha la sua propria struttura JSON, e documenti diversi all'interno della stessa collezione possono avere strutture completamente differenti. Questa è l'essenza del paradigma "schema-free".

La dimensione massima di un documento BSON è 16 MB, limite che aiuta a garantire che un singolo documento non utilizzi una quantità eccessiva di RAM o, durante la trasmissione, una quantità eccessiva di larghezza di banda.

Un esempio di documento MongoDB:
```json
{
  "_id": ObjectId("4efa8d2b7d284dad101e4bc9"),
  "name": "Mauro Pelucchi",
  "address": {
    "street": "via Finazzi 47",
    "city": "Carvico"
  },
  "shipAddresses": [
    {"street": "via Finazzi 47", "city": "Carvico"},
    {"street": "via Cavour 23", "city": "Carvico", "note": "suonare a Gianpietro"},
    {"street": "Edificio U7 - Università degli Studi di Milano Bicocca", "city": "Milano"}
  ]
}
```

### MongoDB Atlas
MongoDB Atlas è il servizio di database cloud completamente gestito da MongoDB, che offre un'architettura di alto livello per la distribuzione, la gestione e la scalabilità di database MongoDB nel cloud.