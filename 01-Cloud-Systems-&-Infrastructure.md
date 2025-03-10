# Cloud Systems and Infrastructure

## 1.0 - Introduzione alle Tecnologie Cloud e Mobile

Il documento presenta un corso su "Tecnologie Cloud e Mobile" tenuto dal Professor Mauro Pelucchi. Il corso si concentra su quattro aree principali:
- Cloud computing
- AWS (Amazon Web Services)
- Micro-servizi
- Architetture server-less

## 1.1 - Cloud Computing

### Evoluzione dei Paradigmi di Computing

La storia dell'informatica ha visto diversi paradigmi di computing:

1. **Mainframe computing**: Modello "1 computer / molti utenti" - un singolo computer centrale serviva molti utenti simultaneamente. Spesso interfacce utente proprietarie e meno personalizzabili.

2. **Client-server computing**: Modello "molti computer / molti utenti" - distribuzione del carico su diversi server che servono numerosi client. Interfacce come pagine web e quindi piu duttili e con curva di apprendimento piu rapida.

3. **Cloud computing**: Evoluzione che incarna il concetto "The network is the computer" (coniato da John Gage di Sun Microsystems nel 1984), oggi aggiornato in "The cloud is the computer" - l'infrastruttura di rete diventa l'elemento centrale dell'elaborazione.

AWS fa da padrona del mondo cloud anche perche è stata colei che è arrivata per prima. AWS nasce nel 2008 dalla necessità di Amazon di efficentare i propri processi IT, hanno quindi esportato questa pratica istituendo AWS.

### Virtualizzazione: Fondamento del Cloud Computing

La virtualizzazione rappresenta il primo passo fondamentale verso il cloud computing. Essa ci permette di astrarre dalla singola macchina, permettendo la realizzazione di diverse istanze.
- **Definizione**: Processo attraverso cui si scompone un grande server fisico in più server virtuali indipendenti.
- **Caratteristiche**: Ogni server virtuale è dedicato a uno specifico componente isolato.
- **Approccio**: Astrazione di servizi IT dove poche grandi macchine fisiche ospitano numerose macchine virtuali indipendenti, ciascuna con il proprio sistema operativo e applicazioni.

### Caratteristiche Fondamentali del Cloud Computing

Il documento identifica 5 caratteristiche essenziali:
1. **Servizi su richiesta**: Disponibilità immediata in base alle necessità
2. **Accesso di rete**: Disponibilità attraverso la rete
3. **Pooling di risorse**: Aggregazione di risorse per servire più clienti
4. **Elasticità rapida**: Scalabilità veloce verso l'alto o verso il basso
5. **Misurazione dei servizi**: Monitoraggio e fatturazione precisi del consumo

Tuttavia il diver principale che muove le aziende verso il cloud è la semplicità di gestione che porta con se.

### Benefici e Sfide del Cloud Computing

**Benefici**:
- Pay per Use (pagamento in base all'uso)
- Scalabilità
- Gestione della complessità
- Servizi gestiti
- Innovazione continua
- Risorse potenzialmente infinite
- Riduzione del time-to-market

**Sfide**:
- Sicurezza (compliance) e Service Assurance: Non in termini di sicurezza informatica, ma in termini di geoposizionamento dei dati e di availability. Non ho la sicurezza che una data risorsa sia diponibile in una data regione.
- Trasparenza
- Aggiornamenti
- Integrazione con IT esistenti
- Portabilità: è complicato migrare da un cloud all'altro.
- Confronto dei costi

## 1.2 - Modelli di Servizio Cloud

### 1. SaaS (Software as a Service)
- Il cliente utilizza applicazioni su un'infrastruttura accessibile tramite vari dispositivi client
- Accesso tramite API, interfacce web o client dedicati
- Esempi: Gmail, Office 365

### 2. PaaS (Platform as a Service)
- Permette di sviluppare e distribuire applicazioni utilizzando linguaggi di programmazione supportati dal fornitore
- L'infrastruttura sottostante è gestita dal provider
- Esempi: Google App Engine, Heroku

### 3. IaaS (Infrastructure as a Service)
- Noleggio di capacità di CPU, storage, network e altre risorse
- Include sistemi operativi e applicazioni di base
- Il cliente ha controllo sui sistemi operativi, storage e applicazioni
- Esempi: AWS EC2, Microsoft Azure, OCI

Altri tipi di servizi (aaS):

- AaaS (Architecture as a Service)
- BaaS (Business as a Service)
- CaaS (Computing as a Service)
- CRMaaS (CRM as a Service)
- DaaS (Data as a Service)
- DBaaS (Database as a Service)
- E molti altri...

## 1.3 - Modelli di Deployment Cloud

### Tipologie di Cloud

1. **Private Cloud**:
   - Custom Private Cloud
   - Packaged Private Cloud
   - Vantaggi: sicurezza personalizzata, maggior controllo

2. **Hybrid Cloud**:
   - Exclusive Cloud
   - Community Cloud
   - Combinazione di elementi privati e pubblici

3. **Public Cloud**:
   - Vantaggi: costi ridotti, nessuna manutenzione, scalabilità quasi illimitata, affidabilità elevata, semplicità, flessibilità

## 1.4 - Considerazioni sui Costi del Cloud

### Modelli di Pricing


- **Base Cost estimation**: Evoluzione del modello tradizionale, divido per tipo di costo. Non risco ad applicarlo su un cloud pubblico.
- **Time Based**: Analizzo quanto tempo ogni progetto mi occupa le risorse in cloud.
- **Metodo personalizzato**: Istituisco dei tag sotto i quali inserisco i vari costi che sostengo. Cio mi permette di istituire una suddivisione con una cersta granularità dei costi.

Posso utilizzare gli stumenti messi a disposizione dalla piattaforma cloud stessa.

### Esempio di Modello di Costo Semplice

Facciamo ora un esempio di costi in cloud:
- Database Server (NoSQL): 24 ore al giorno, tipo m5.2xlarge = $3,500/anno
- ETL (Spark): 10 ore al giorno, tipo m5.4xlarge = $2,900/anno
- Presentation: 10 ore al giorno, tipo m5.4xlarge = $2,900/anno
- **Totale annuale**: $9,300 (solo costi EC2!)

### Strategie per Risparmiare

Per ottimizzare i costi nel cloud, il documento suggerisce di sfruttare i vantaggi intrinseci del cloud:

1. **Istanze SPOT**:
   - Permettono di utilizzare capacità inutilizzata nel cloud
   - Offrono sconti fino al 90% rispetto ai prezzi on-demand
   - Attenzione: potrebbero essere interrotte se il prezzo Spot supera il prezzo massimo o se la domanda aumenta/offerta diminuisce

2. **Istanze Riservate**:
   - Pagamento anticipato per le istanze che si desidera prenotare
   - Offrono uno sconto significativo sulla tariffa oraria

## 1.5 - Recap dei Concetti Chiave del Cloud Computing

- **Risorse IT on demand**: disponibilità immediata
- **Migliori benefici in un contesto affidabile**: stabilità e sicurezza
- **Insieme di risorse informatiche virtualizzate**: astrazione
- **Assegnamento rapido di risorse a run-time**: provisioning dinamico
- **Sistemi ad alta scalabilità architetturale**: crescita flessibile
- **Affidabilità**: servizio continuativo
- **Virtualizzazione**: separazione logica dal fisico
- **Provisioning**: allocazione automatizzata
- **Scalabilità**: adattamento alle esigenze

## 1.6 - AWS (Amazon Web Services)

Amazon Web Services è una piattaforma di servizi cloud sicura che offre potenza di elaborazione, storage di database, distribuzione di contenuti e altre funzionalità per aiutare le imprese a ricalibrare le proprie risorse e crescere.

### Struttura Geografica di AWS

1. **Region**:
   - Collezioni indipendenti di risorse AWS in una geografia definita
   - Permette flessibilità nel posizionamento di istanze e dati

2. **Availability Zones**:
   - Ogni Region ha più location isolate chiamate Availability Zones
   - Consente di posizionare risorse in location multiple per maggiore resilienza

### Principali Servizi AWS
- **S3** (Simple Storage Service)
- **EC2** (Elastic Compute Cloud)
- **EMR** (Elastic MapReduce)
- **Redshift** (data warehouse)
- **Lambda** (servizi serverless)
- **Rekognition** (ML vision)
- **SageMaker** (ML platform)
- **QuickSight** (business analytics)
- **Athena** (query service)

#### S3 (Simple Storage Service)
- **Caratteristiche**: storage altamente scalabile, accessibile via API, veloce, alta disponibilità, economico
- **Tipo**: Object Store (non file system)
- **Vantaggi**: nativamente supportato da Spark, Hive; è un servizio (non richiede cluster); capacità illimitata; basso costo; sicuro

#### EC2 (Elastic Compute Cloud)
- **Definizione**: Virtual Machines in cloud
- **Scala**: Da piccole istanze (T2.Nano: 1 vCPU, 512 MB RAM) a enormi (X1.32xlarge: 128 vCPU, 2000 GB RAM)
- **GPU**: Disponibili per deep learning
- **Prezzi**: Per secondo, con opzioni On-Demand e "Spot Instances"
- **Spot Instances**: Aste per capacità EC2 inutilizzata, generalmente molto più economiche

#### EMR (Elastic MapReduce)
- **Funzionalità**: Cluster Hadoop, Spark, HBase, Presto, Hive
- **Vantaggi**: Esegue automaticamente tutto lo scaling e il provisioning necessario del cluster

## 1.7 - Micro-servizi
I micro-servizi emergono come risposta a sfide di:
- Manutenibilità
- Monitoring
- Scalabilità
- Aggiornamenti
- Onboarding

### Definizione di Micro-servizi

Secondo James Lewis e Martin Fowler:
"Scomposizione funzionale del sistema in componenti gestibili e implementabili in modo indipendente". 
Scompongo i sistemi complessi e monolitici in componenti fanno cose completamente differenti e separate, il fatto che siano cose scomposte mi permette di implementare solo cio che mi serve veramente. cio mi permette anche di creare le componenti in linguaggi di programmazione differenti, che siano piu addatti a cio che la componente dovrà fare.


### Caratteristiche dei Micro-servizi

1. **Componentizzazione tramite servizi**: suddivisione in componenti indipendenti
2. **Prodotti, non progetti**: focus su prodotti completi
3. **Organizzazione attorno alle capacità di business**: allineamento con le esigenze aziendali
4. **Decentralizzazione**: distribuzione della responsabilità


## 1.8 - Docker

Soluzione al problema del "run anywhere" (esecuzione ovunque) utilizzando container Linux. Mi permette di creare ambienti isolati, permettendo che la coesistenza di piu ambienti (anche incompatibili) sulla stessa macchina e sullo stesso OS.

Il problema della differenza tra ambienti di sviluppo e produzione, può causare conflitti di dipendenze e versioni. Docker risolve questo problema incapsulando applicazioni e dipendenze in container isolati.

### Vantaggi di Docker

1. **Efficienza**: i container condividono il kernel OS, sono più leggeri delle VM
2. **Portabilità**: eliminazione della "matrix from hell" di compatibilità
3. **Flessibilità**: capacità di costruire, distribuire ed eseguire qualsiasi app ovunque
4. **Sicurezza**: isolamento tra container e host

### Docker: Immagini e Container

- **Immagine**: file inerte, immutabile, essenzialmente uno snapshot di un container
- **Container**: istanza in esecuzione di un'immagine Docker

### Gestione delle Immagini
- **Docker Hub**: repository pubblico di immagini
- **Immagini private**: create tramite Dockerfile
- **Registri privati**: per conservare immagini aziendali

### Workflow Docker

1. Scrivere un Dockerfile
2. Effettuare il build dell'immagine
3. Avviare il container

### Dockerfile

Il documento mostra un esempio di Dockerfile complesso per un'applicazione big data, illustrando i comandi principali:
- **FROM**: imposta l'immagine base
- **ENV**: imposta variabili d'ambiente
- **RUN**: esegue comandi nell'immagine
- **ADD**: aggiunge file dall'host/URL al container
- **VOLUME**: specifica directory esterne al file system
- **EXPOSE**: specifica le porte da aprire
- **CMD**: comando predefinito all'esecuzione

### Comandi Docker Base

- **docker ps**: mostra l'elenco dei container attivi
- **docker stop**: ferma un container
- **docker rm**: rimuove un container
- **docker run**: avvia un container

### Recap Docker

- Docker permette di costruire sistemi modulari e portabili
- Può essere distribuito ovunque: on premises o in cloud
- Necessita di orchestrazione dei container (Kubernetes)
- Google ha introdotto i container più di 10 anni fa

## 1.9 - Architetture Serverless

### Definizione

Il serverless computing (noto anche come Functions as a Service) è una nuova astrazione del cloud computing che semplifica la scrittura di servizi web robusti e di larga scala. I programmatori scrivono funzioni serverless che rispondono a eventi esterni.

- **Allocazione automatica**: la piattaforma alloca automaticamente hardware aggiuntivo e gestisce il bilanciamento del carico quando la domanda aumenta
- **Deallocazione automatica**: le risorse inattive vengono silenziosamente deallocate quando la domanda diminuisce
- **Gestione degli errori**: la piattaforma rileva i guasti e ripete automaticamente le richieste

### Function as a Service

- **Fatturazione granulare**: i fornitori cloud fatturano solo l'esecuzione effettiva
- **Modello di programmazione event-driven**: esecuzione in risposta a eventi
- **Gestione operativa**: la piattaforma gestisce la maggior parte dei problemi operativi
- **Nessun controllo sulle risorse**: l'infrastruttura è completamente astratta
- **Funzioni di breve durata**: esecuzioni tipicamente brevi
- **Auto-scaling e provisioning**: gestiti dalla piattaforma
- **Alta disponibilità implicita**: resilienza integrata
- **Tolleranza ai guasti implicita**: gestione automatica degli errori
- **Nessun server da gestire**: astrazione completa dell'infrastruttura

Tuttavia le serverless function introduciunonouna latenza che in sistemi real o semi-real time puo provocare la rottura del sistema.


### Caratteristiche delle Piattaforme Serverless

- **Costo**: generalmente più economico per workload intermittenti
- **Performance e limiti**: vincoli di esecuzione
- **Linguaggi di programmazione**: supporto per diversi linguaggi
- **Modello di programmazione**: tipicamente event-driven
- **Componibilità**: capacità di combinare funzioni
- **Deployment**: semplificato
- **Sicurezza e accounting**: gestione integrata
- **Monitoraggio e debugging**: strumenti specifici

### Time-to-live vs Scaling

Il documento presenta un grafico che mette in relazione il tempo di vita (asse x) e la facilità di scaling (asse y):
- **Server-aware compute** (bare metal, VM, IaaS): lungo tempo di vita e più lento a scalare
- **Serverless compute** (FaaS, MBaaS, PaaS, SaaS): ottimizzato per lavorare su più server e nascondere i dettagli del server

La parte finale del documento accenna brevemente al Service Design, ma non fornisce dettagli specifici su questo argomento.