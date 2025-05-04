# Tecnologie Cloud & Mobile: Building Server-less Applications

Presentazione di Mauro Pelucchi (mauro.pelucchi@gmail.com) - Università degli Studi di Bergamo - Corso 21069 - Piattaforme cloud e mobile.

## 7.1 - Argomenti Trattati

Il documento introduce i seguenti argomenti principali relativi alle tecnologie cloud e mobile, con un focus sulla creazione di applicazioni serverless:
*   Function as a Service (FaaS)
*   API (Application Programming Interfaces)
*   AWS Lambda Function & AWS API Gateway
*   Cenni su Node.js come tecnologia abilitante per alcuni scenari serverless/backend.

## 7.2 - La Sfida della Delivery del Software

Le aziende moderne si trovano di fronte alla sfida di bilanciare la stabilità delle loro operazioni con la necessità di sviluppare e rilasciare rapidamente nuove funzionalità software. L'obiettivo ideale è quello di poter consegnare software con "tolleranza zero" per le interruzioni (zero tolerance for outages), garantendo al contempo che il processo sia:
*   **Rapido (Quickly):** Per rispondere velocemente alle esigenze del mercato.
*   **Sicuro (Securely):** Per proteggere dati e sistemi.
*   **Affidabile (Reliably):** Per garantire la continuità del servizio.

## 7.3 - Ciclo di Vita dello Sviluppo dei Sistemi (SDLC)

Viene presentato un modello standard del ciclo di vita dello sviluppo dei sistemi (Systems Development Lifecycle - SDLC). Questo ciclo articola il processo di creazione e manutenzione del software in fasi distinte:
1.  **Plan (Pianificazione):** Definizione degli obiettivi e dell'ambito.
2.  **Define (Definizione):** Analisi dettagliata dei requisiti.
3.  **Design (Progettazione):** Progettazione dell'architettura e delle componenti del sistema.
4.  **Develop (Sviluppo):** Scrittura del codice, installazione di componenti e programmi, formazione degli utenti, test delle performance e aggiustamenti.
5.  **Deploy (Distribuzione):** Rilascio del software nell'ambiente di produzione.
6.  **Maintain (Manutenzione):** Monitoraggio, correzione di bug e aggiornamenti post-rilascio.

## 7.4 - Metodologie SDLC: Waterfall vs Agile

Si confrontano due approcci principali alla gestione dell'SDLC:
*   **Waterfall:** Un modello sequenziale e lineare dove ogni fase deve essere completata prima di iniziare la successiva (Plan -> Define -> Design -> Develop -> Deploy -> Maintain). È rigido e poco adatto a cambiamenti in corso d'opera.
*   **Agile:** Un modello iterativo e incrementale. Il lavoro è organizzato in cicli brevi chiamati "Sprint", ognuno dei quali attraversa tutte le fasi (Plan, Define, Design, Develop, Deploy, Maintain a livello di sprint). Questo permette maggiore flessibilità e adattabilità ai requisiti che cambiano.

## 7.5 - Fasi Principali dello Sviluppo Software Moderno

Le fasi generali dell'SDLC vengono ulteriormente dettagliate in attività più specifiche, tipiche dei processi di sviluppo moderni, spesso automatizzate tramite pipeline CI/CD (Continuous Integration/Continuous Deployment):
*   **Code:** Scrittura del codice sorgente (es. file `.java`), check-in nel sistema di version control, peer review del nuovo codice.
*   **Build:** Compilazione del codice, esecuzione di test unitari, esecuzione di controlli di stile (style checkers), raccolta di metriche sul codice, creazione di artefatti distribuibili (es. immagini container).
*   **Test:** Esecuzione di test di integrazione con altri sistemi, test di carico (load tests), test dell'interfaccia utente (UI), test di penetrazione (penetration tests) per la sicurezza.
*   **Deploy:** Distribuzione del codice negli ambienti di produzione.
*   **Maintain:** Monitoraggio continuo del codice in produzione per rilevare rapidamente comportamenti anomali o errori.

## 7.6 - Function as a Service (FaaS)

Questa sezione introduce il concetto di FaaS come evoluzione dei modelli cloud.

**Contesto Cloud (IaaS, PaaS, SaaS):**
Si richiama la classica stratificazione dei servizi cloud:
*   **IaaS (Infrastructure as a Service):** Fornisce risorse computazionali di base (VM, storage, network). Tipicamente per Network Architects.
*   **PaaS (Platform as a Service):** Offre una piattaforma per sviluppare, eseguire e gestire applicazioni senza gestire l'infrastruttura sottostante. Per Application Developers.
*   **SaaS (Software as a Service):** Fornisce software pronto all'uso via web. Per End Users.
La visibilità e il controllo sull'infrastruttura diminuiscono salendo da IaaS a SaaS.

**Oltre IaaS/PaaS/SaaS:**
Ci si chiede se serva qualcos'altro. Emergono esigenze legate a sicurezza, scalabilità (up/down), gestione dei server e delle dipendenze, spesso affrontate con l'uso di **Containers**. I container e i relativi orchestratori (es. Kubernetes) si collocano sopra l'IaaS e a volte in parallelo/integrati col PaaS.

**Dalle Applicazioni Monolitiche alle Funzioni:**
L'idea alla base di FaaS è spingere ulteriormente la granularità delle applicazioni. Si passa da:
1.  **Applicazione Monolitica:** Un unico blocco di codice.
2.  **Microservizi:** Applicazione scomposta in servizi più piccoli e indipendenti.
3.  **Functions (FaaS):** Applicazione scomposta a livello di singole funzioni, spesso attivate da eventi.

**Definizione di FaaS:**
FaaS è la capacità di eseguire una funzione specifica nel cloud senza doversi preoccupare della gestione dei server sottostanti. È una forma di **serverless computing** in cui si esegue codice in un ambiente astratto, tipicamente in risposta a eventi. Lo sviluppatore si concentra solo sul codice ("Just code to develop and execute"). FaaS si posiziona come un livello di astrazione ancora superiore rispetto a PaaS e Container Orchestrators.

**Livelli di Astrazione (Riepilogo):**
L'evoluzione dell'astrazione procede da: Bare Metal -> Virtual machines -> Containers -> Functions (FaaS). Salendo, aumenta il focus sulla logica di business e diminuisce la preoccupazione (e il controllo) sull'infrastruttura. L'evoluzione architetturale va da Servizi monolitici (autonomi, loosely-coupled) a Microservizi (single purpose, stateless, scalabili, automatizzati) fino a Functions (single action, effimere).

## 7.7 - Serverless Computing

Il Serverless Computing rappresenta un paradigma in cui il cloud provider gestisce dinamicamente l'allocazione e il provisioning dei server.

**Confronto tra Modelli:**
*   **On-premises:** Alti costi iniziali, capacità fissa, deployment lenti, manutenzione onerosa.
*   **Virtual servers (IaaS):** Indipendenza hardware, scalabilità elastica, provisioning rapido, manutenzione ridotta.
*   **Containers:** Indipendenza piattaforma, alta utilizzazione risorse, deployment rapidi, isolamento.
*   **Serverless (FaaS):** Nessun OS da gestire, scaling flessibile automatico, pay-per-use, fault tolerance integrata, zero manutenzione infrastruttura.
Il livello di astrazione cresce, permettendo di focalizzarsi sempre più sulla **logica di business**.

**Costruire Applicazioni Serverless Moderne:**
Si basano su:
*   **Piccoli pezzi, debolmente accoppiati:** Funzioni/microservizi indipendenti.
*   **Data store specifici:** Uso del DB più adatto allo scopo (NoSQL, relazionale...).
*   **Servizi specializzati per integrazione:** Code, notifiche, orchestrazione.
*   **Automazione tramite codice:** Infrastructure as Code (IaC), CI/CD.
Questo porta a pattern serverless compute event-driven, data store serverless, servizi gestiti e framework di deployment.

**Caratteristiche Chiave (Serverless/FaaS):**
*   Focus sviluppatori sul codice, non sulle operation.
*   Architettura Reattiva (event-driven).
*   Poliglotta (linguaggi diversi per funzioni diverse: Node.js, Java, Python...).
*   Stateless (lo stato va gestito esternamente).
*   Task-focused (ogni funzione fa una cosa specifica).
*   Event-triggered (attivate da eventi).
*   Esposte come API REST, ricevono eventi JSON.
*   Utility billing (pagamento solo per l'uso effettivo).

**Vantaggi e Svantaggi (Good vs Bad):**
*   **Vantaggi:** Alta concorrenza, aggiornamenti facili, alta utilizzazione, scalabilità, pricing granulare, separazione app/infra, poliglotta, sicurezza parzialmente gestita dal provider, focus singolo.
*   **Svantaggi:** Paradigma diverso, possibile assenza di framework noti, latenza potenziale (cold start) e variabile, statelessness richiede design apposito, poco tempo per ottimizzazione runtime, limiti risorse provider, pricing a volte complesso.

**Architettura FaaS (Concetti Base):**
Un flusso tipico FaaS prevede: Edge (UI, API Gateway, sorgenti eventi) -> Event Queue -> Dispatcher -> Master/Worker (dove gira il codice della funzione).

**Esempio AWS Lambda (S3 Trigger):**
1.  Upload codice su Lambda.
2.  Configurazione trigger (es. upload file su S3).
3.  Lambda esegue il codice solo quando scatta il trigger.
4.  Pagamento per il tempo di calcolo.
*Caso d'uso:* Upload foto su S3 -> Lambda la ridimensiona per web/mobile.

**Piattaforme FaaS/Serverless:**
Vengono mostrati loghi di varie soluzioni: AWS Lambda, Azure Functions, Google Cloud Functions, Serverless Framework, Apache OpenWhisk, ecc.

## 7.8 - AWS Lambda Function

Questa sezione approfondisce AWS Lambda, l'implementazione FaaS di Amazon.

**Cos'è una Lambda?**
*   Servizio FaaS.
*   Pagamento per invocazione/tempo.
*   Auto-scaling "infinito".
*   Focus sul business logic.
*   Zero amministrazione server.
Una funzione Lambda è composta da: **Codice**, **Dipendenze** (librerie, binari) e **Configurazione** (memoria, timeout, trigger, ecc.).

**Come Funziona:**
Si basa su: Authoring (scrittura codice), Statelessness, Deployment, Monitoring & Logging.

**Casi d'Uso Comuni:**
Web Applications, Backends (mobile, IoT), Data Processing (real-time, batch), Chatbots, Amazon Alexa Skills, Autonomous IT (policy, gestione infra).

**Modelli di Invocazione (Push/Pull):**
*   **Push:** Servizi AWS (S3, API Gateway) invocano Lambda direttamente.
*   **Pull (Polling):** Lambda legge eventi da code/stream (SQS, Kinesis, DynamoDB Streams) e si auto-invoca.

**Modelli di Esecuzione:**
*   **Synchronous (push):** L'invoker attende la risposta (es. API Gateway -> Lambda -> risposta HTTP).
*   **Asynchronous (event):** L'invoker invia l'evento e non attende (es. S3 -> Lambda).
*   **Stream-based (poll):** Lambda processa record da stream (es. Kinesis -> Lambda).

**Anatomia di una Funzione Lambda (Node.js):**
Il codice tipicamente esporta una funzione **handler** che riceve tre argomenti:
*   `event`: Oggetto con i dati di input (trigger payload).
*   `context`: Oggetto con metadati sull'esecuzione (ID richiesta, tempo rimanente, ecc.).
*   `callback`: Funzione (legacy in Node.js) per restituire il risultato o un errore.

**Building Blocks Serverless su AWS:**
Le app serverless combinano vari servizi AWS:
*   **Compute:** Lambda
*   **Storage:** S3, DynamoDB
*   **Database:** DynamoDB
*   **API Proxy:** API Gateway
*   **Messaging/Queues:** SQS, SNS
*   **Analytics:** Kinesis
*   **Orchestration:** Step Functions
*   **Monitoring:** X-Ray, CloudWatch

## 7.9 - API (Application Programming Interface)

Le API sono strumenti fondamentali per l'interazione tra sistemi software.

**Definizione:** Un'API è uno strumento/interfaccia che permette a computer (o componenti software) di scambiarsi informazioni e richiedere l'esecuzione di funzionalità.

**Importanza delle API:**
*   Sono interfacce a livello di codice (per librerie, OS, servizi web).
*   **Valore Aziendale:** Possono essere un asset strategico; richiedono investimento per l'apprendimento da parte degli utenti.
*   **Stabilità:** Tendono a cambiare lentamente, con mantenimento di versioni precedenti (a differenza dei siti web).
*   **API Pubbliche:** Abilitano ecosistemi e integrazioni di terze parti.

**Caratteristiche di una "Good API":**
*   **Per l'utente:** Facile da usare, facile da imparare, soddisfa i requisiti.
*   **Per lo sviluppatore:** Facile da manutenere, facile da estendere.

**Design di API:**
*   Raccogliere i veri requisiti (non soluzioni preconcette).
*   Definire scenari d'uso.
*   Creare specifiche brevi.
*   Considerare: Interfacce (semplici, generali, prevedibili, robuste), Gestione Risorse (file, memoria), Gestione Errori (fail fast).

**Utilizzo di un'API:**
Un client invia una richiesta (es. HTTP) a un API provider, che processa la richiesta (eventualmente interagendo con storage/servizi) e restituisce una risposta. Spesso richiede autenticazione/autorizzazione (es. API key, contratti).

## 7.10 - Esempi di API

Vengono illustrati alcuni esempi concreti:

*   **Clarifai API:** Per riconoscimento immagini/video. Si invia un input (immagine/video) e si ricevono predizioni (tag, concetti). Offre piani tariffari diversi, incluso uno gratuito. Le risposte sono tipicamente in JSON.
*   **Geocoding API (Mapquest, Google):** Trasformano indirizzi fisici in coordinate geografiche (lat/lon) e viceversa. MapQuest fornisce un portale per sviluppatori con documentazione, chiavi API ed esempi (JS, Python) per usare i suoi servizi, incluso il geocoding.
*   **OpenAI API:** Fornisce accesso a modelli AI avanzati (GPT-4, ecc.) per text generation, NLP, computer vision. Esempi mostrano come usarla via codice (JS, Python) per generare testo da prompt o ottenere output strutturato (JSON).
*   **OpenAI API con LlamaIndex:** LlamaIndex è un framework per costruire agenti LLM-powered e applicazioni RAG (Retrieval-Augmented Generation) che interagiscono con dati esterni (documenti, API). Permette di creare assistenti più sofisticati usando i modelli OpenAI.
*   **Esempio Pratico (CV Consultant):** Viene mostrata un'applicazione web (GitHub: mauropelucchi/cv-consultant) costruita con Streamlit, OpenAI e LlamaIndex. L'app prende in input un CV (PDF), lo indicizza, e permette all'utente di interagire con un assistente AI (basato su GPT-4o e LlamaIndex) per ricevere consigli personalizzati su come migliorare il CV o generare contenuti derivati come una bio professionale.

## 7.11 - Node.js

Node.js è un ambiente di runtime per eseguire JavaScript lato server.

**Caratteristiche Principali:**
*   Permette di usare JavaScript per il backend.
*   Basato sul motore V8 di Chrome.
*   Leggero ed efficiente.
*   **Event-Driven, Non-Blocking I/O:** Modello a singolo thread (event loop) che gestisce molte connessioni concorrenti senza bloccarsi sulle operazioni di I/O. L'I/O viene delegato e una callback viene eseguita al completamento.
*   Altamente Scalabile: Ottimo per applicazioni I/O intensive e ad alta concorrenza.

**Evoluzione di JavaScript:**
DHTML (anni '90) -> jQuery/RIA (anni '00) -> Node.js/Framework Moderni (Angular, React, Vue - anni '10+).

**Synchronous vs Asynchronous:**
Concetto chiave in Node.js. L'approccio asincrono (con callback, Promises, async/await) evita di bloccare l'event loop, garantendo reattività.

**Modello Single Thread Asynchronous I/O:**
L'event loop gestisce le richieste. Le operazioni I/O lunghe vengono eseguite in background. Al completamento, l'evento e la callback associata vengono messi in coda per essere eseguiti dall'event loop.

**Non-Blocking I/O:**
Si usano eventi e callback per non attendere il completamento dell'I/O. Il codice continua l'esecuzione mentre l'I/O è in corso.

**Quando Usare Node.js:**
Ideale per applicazioni con poche operazioni CPU-intensive ma molte operazioni I/O: web server, API, chat, app real-time, microservizi, applicazioni ad alta concorrenza.

**Comandi Base:**
*   `node`: Avvia REPL.
*   `node script.js`: Esegue script.
*   `node -v`: Versione Node.
*   `npm`: Gestore pacchetti.
*   `npm -v`: Versione npm.

**Moduli Popolari:**
Express (web framework), socket.io (real-time), Mongoose (MongoDB ODM), Pug/Jade (template engine), restify (API REST framework).