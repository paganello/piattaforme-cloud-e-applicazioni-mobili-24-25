# Tecnologie Cloud & Mobile: Big Data and Applications in the Cloud


## 5.0 - Python

Python è un linguaggio interpretato con tipizzazione dinamica che si distingue per la sua concisione e versatilità. La sua natura lo rende adatto a molteplici paradigmi di programmazione: orientato agli oggetti, procedurale e funzionale. Python offre tipi di collezioni incorporate ricche come tuple, dizionari e set, e risulta estremamente facile da interfacciare con linguaggi come C, ObjC, Java e Fortran.

Le caratteristiche più distintive di Python includono l'utilizzo dell'indentazione al posto delle parentesi graffe, vari tipi di sequenze (stringhe immutabili, liste mutabili e tuple immutabili), potenti funzionalità di slicing, un sistema di eccezioni simile a Java e un sistema di oggetti semplice ma efficace.

Per quanto riguarda la sintassi, Python utilizza "=" per l'assegnazione e "==" per il confronto. Gli operatori aritmetici (+, -, *, /, %) funzionano come previsto, mentre "+" ha un uso speciale per la concatenazione di stringhe e "%" per la formattazione. Il comando base di stampa è `print()`, e una caratteristica notevole è che i tipi di variabili non devono essere dichiarati, poiché Python li determina automaticamente.

L'ecosistema Python è arricchito da numerose librerie che ne estendono le funzionalità: numpy per operazioni di array rapide e algebra lineare, matplotlib per la creazione di grafici di alta qualità, pandas per l'elaborazione dei dati, sklearn per il machine learning e TensorFlow/keras per il deep learning.

## 5.1 - Hadoop

Hadoop è nato nel 2003-2004 grazie a Doug Cutting e Michael J. Cafarella come supporto per la distribuzione del progetto di motore di ricerca Nutch. La sua evoluzione è continuata prima presso Yahoo (dal 2006) e poi come progetto Apache.

Si tratta di un framework software open source progettato per l'archiviazione e l'elaborazione di dati su larga scala su cluster di hardware commodity. Gli obiettivi principali di Hadoop sono facilitare il salvataggio e l'elaborazione di grandi dataset, lavorare con dati strutturati e non strutturati con la stessa facilità, semplificare la programmazione in ambienti distribuiti, garantire alta affidabilità, scalabilità e tolleranza ai guasti, nonché spostare il calcolo piuttosto che i dati.

#### HDFS (Hadoop Distributed File System)

HDFS è un file system distribuito ispirato al Google File System. È scalabile, distribuito e portatile (ma non condiviso), scritto in Java specificamente per il framework Hadoop. Rappresenta l'archiviazione distribuita primaria utilizzata dalle applicazioni Hadoop e può funzionare sia come parte di un cluster Hadoop sia come file system distribuito standalone per uso generale.

In HDFS, ogni file è rappresentato come un insieme non contiguo di blocchi (solitamente da 128 Mbyte) che, a differenza dei file system tradizionali, contengono solo dati RAW senza metadati. L'affidabilità e la tolleranza ai guasti sono garantite dalla replica dei dati su più host, mentre Zookeeper viene utilizzato per il coordinamento distribuito.

#### MapReduce

Il framework MapReduce segue un'architettura master-slave:
- Il nodo master (JobTracker) gestisce il ciclo di vita dei job: permanenza in coda, interazione con il file system, suddivisione in task, esecuzione dei task falliti e notifica sul progresso e sulla fine del job.
- I nodi slave (TaskTracker) gestiscono l'esecuzione dei singoli task, occupandosi della configurazione, dell'avvio e della gestione dei tentativi in caso di fallimento, notificando al nodo master il progresso e comunicando il completamento o fallimento del task.

MapReduce è un modello di programmazione di alto livello per l'elaborazione di dati parallela su larga scala. Funziona su hardware commodity, è fault-tolerant e utilizza l'approccio divide et impera: suddivide un problema di grandi dimensioni in sotto-problemi più piccoli, eseguibili in parallelo dai worker, e combina i risultati intermedi per ottenere il risultato finale.

#### YARN (Yet Another Resource Negotiator)

YARN è il gestore di risorse del cluster Hadoop che migliora la gestione delle risorse e l'elaborazione dei dati nel framework.

<div align="center">
  <img src="./images/05-1.png" width="450">
</div>

#### Hadoop 3

Hadoop 3 introduce importanti miglioramenti:
- **HDFS Erasure coding**: migliora l'efficienza di archiviazione di HDFS, offrendo circa il doppio dell'efficienza rispetto alla replica 3x. Utilizza Reed-Solomon per la ricostruzione invece della replica, riducendo l'overhead dal 200% al 40%.
- **YARN**: supporta servizi di lunga durata, offre miglioramenti dello scheduler, isolamento e supporto Docker, nonché una nuova interfaccia utente.
- Supporto per JDK8 e isolamento del classpath.

## 5.2 - PySpark

Nell'era dei big data, la sfida è processare enormi volumi di dati con costi e tempi ragionevoli. Due approcci principali emergono: scale-up (aumentare la potenza del computer) e scale-out (utilizzare molti computer standard e distribuire dati e calcoli).

Spark e Hadoop rispondono alle sfide poste dai grossi volumi di dati, dalla complessità dei sistemi distribuiti, dalle applicazioni complesse (ELT, text mining, modelli predittivi) e dai dati non strutturati.

#### Spark

Apache Spark è un framework open-source per l'elaborazione di grandi volumi di dati (big data) con velocità e semplicità. Sviluppato all'UC Berkeley nel 2010 da Matei Zaharia, estende il modello MapReduce per supportare in modo efficace più tipi di operazioni, query interattive e stream processing.

Essendo che il trend di elaborazione di dati globale è in crescita, ci è sicuramente utile imparare nuovi sistemi per l'elaborazione parallela e distribuita.

<div align="center">
  <img src="./images/05-2.png" width="450">
</div>

#### Applicazione

Scritto in Scala e compatibile con Hadoop, Spark offre API per Java, Scala e Python. È caratterizzato da un modello di programmazione ad alto livello, semplice e funzionale, ed è particolarmente veloce grazie al caching in memoria e alle ottimizzazioni delle query. General purpose, è ideale per ETL, machine learning e dati non strutturati.

La differenza principale è che Hadoop ha come obbiettivo quello di eseguire algoritmi complessi e personalizzati su una grandi moli di dati, mentre Spark ha come obbiettivo l'elaborazione di questi dati.
Spark è per dataprocessing, non va bene per esegure elaborazione real-time.

<div align="center">
  <img src="./images/05-3.png" width="450">
</div>

Rispetto a Hadoop MapReduce, Spark supporta molte tipologie di task come interrogazioni SQL, applicazioni streaming, machine learning e graph operations. Offre pattern generalizzati (stesso framework per molti casi d'uso), valutazione lazy (riduce gli stati di attesa, migliora il pipelining) e programmazione funzionale (rende più facile scrivere e mantenere applicazioni complesse).

Utilizzare spark mi permette di utilizzari linguaggi e motodi gia pronti per operare sui dati, come le gia citate query SQL sui dati di Spark.

#### Lo Stack

Lo stack Spark è composto da:
- Spark Core
- Spark SQL (dati strutturati)
- Spark Streaming (real-time)
- MLlib (Machine Learning)
- GraphX (elaborazione di grafi)

Il tutto funziona su uno scheduler standalone o su Hadoop/YARN o Mesos.

#### Funzionamento di Spark

Implementa una approccio lazy evaluation e funcional programming, questo con lo scopo di ridurre i carichi e quindi i tempi, mantenedo un approccio a flusso piu facile da mantenere grazie ad una piu bassa complessità di scittura dei job.

La valutazione lazy in Spark presenta numerosi vantaggi. Permette di avere una "big picture" del processo, vedendo più alternative, e di non eseguire operazioni non necessarie. Ad esempio, quando si prendono solo le prime 5 righe di un dataset unito, Spark non calcola l'intera unione ma prepara solo i primi 5 elementi della collezione.

In Spark, il driver program comunica con il cluster manager per richiedere risorse e avviare gli executor. Gli executor eseguono i task inviati dal driver sulla base delle azioni e trasformazioni richieste dal job dell'utente. Al termine dell'esecuzione, vengono rilasciate le risorse.

<div align="center">
  <img src="./images/05-4.png" width="450">
</div>

### RDD (Resilient Distributed Datasets)

Un RDD è una collezione distribuita immutabile di oggetti che possono essere utilizzati in parallelo. È resilient (può essere ricreato), distributed (elaborato in tutto il cluster) e contiene dati provenienti da file o data warehouse. Gli elementi di un RDD sono partizionati su un insieme di macchine e, se una partizione viene persa, può sempre essere ricostruita.

### DataFrame e Dataset

I DataFrame e i Dataset superano i limiti degli RDD, che non possono essere ottimizzati da Spark, risultano lenti in Python e Java e possono facilmente portare a catene di trasformazioni inefficienti.

Le API DataFrame forniscono un livello di astrazione superiore, permettendo di manipolare dati attraverso un linguaggio per query (anche SQL). Le query su DataFrame sono ottimizzate da Spark, anche se non sono type-safe.

I Dataset, disponibili con Spark 2.*, sono concettualmente simili a un RDD ma utilizzano il framework Tungsten per l'encoding in-memory, offrendo migliori performance in termini di spazio e velocità.

### Trasformazioni e Azioni

Le trasformazioni in Spark creano un nuovo dataset da uno esistente. Sono lazy, cioè non elaborano immediatamente i risultati, ottimizzando i calcoli e consentendo il recupero delle partizioni di dati perse. Esempi di trasformazioni sono map, filter, groupBy, join, reduceBy e sort.

Le azioni indicano che qualcosa deve essere effettuato e vengono eseguite immediatamente da Spark, producendo un risultato. Esempi di azioni sono reduce, count, saveAsTextFile, first, collect e take.


## 5.3 - Spark SQL

Spark SQL è un modulo per l'elaborazione di dati relazionali in Spark. Offre un'interfaccia SQL-like (HIVE over Spark) ed è fino a 100 volte più veloce per dati in memoria e 5-10 volte più veloce per dati su disco.

### DataFrame e Dataset in Spark SQL

A differenza di un RDD, un DataFrame organizza i dati in colonne denominate, come una tabella in un database relazionale. Impone una struttura su una collezione distribuita di dati, consentendo un'astrazione di livello superiore.

Un Dataset è un'estensione dell'API DataFrame che fornisce un'interfaccia di programmazione orientata agli oggetti e type-safe (rilevazione degli errori in fase di compilazione).

Entrambi sono costruiti sul motore Spark SQL e utilizzano Catalyst per generare piani di query logici e fisici ottimizzati; entrambi possono essere convertiti in un RDD.

### Modello di dati

Spark SQL supporta un modello di dati nidificato che include sia tipi SQL primitivi (boolean, integer, double, decimal, string, data, timestamp) sia tipi complessi (struct, array, map e union), oltre a tipi definiti dall'utente.

### Utilizzo di Spark SQL

È possibile eseguire query SQL attraverso un SQLContext o HiveContext, utilizzando il metodo sql(), che restituisce un DataFrame. Si possono combinare metodi DataFrame e query SQL nello stesso codice. Per utilizzare SQL, è necessario creare un alias di tabella per un DataFrame utilizzando registerTempTable().