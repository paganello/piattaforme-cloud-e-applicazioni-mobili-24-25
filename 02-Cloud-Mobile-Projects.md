# Tecnologie Cloud & Mobile

## 2.0 - DevOps

### Il Problema

Nel panorama digitale odierno, software e applicazioni sono essenziali per quasi tutte le operazioni aziendali. Tuttavia, i modelli tradizionali di sviluppo software presentano sfide significative. Il software deve essere eseguito su server per diventare un servizio, ma la distribuzione è spesso troppo lenta. Esistono punti di attrito interni alle organizzazioni IT che causano ritardi, traducendosi in perdite finanziarie. I dipartimenti IT diventono frequentemente colli di bottiglia nella transizione "dal concetto al guadagno".

I problemi comuni nella distribuzione del software includono diagnosi dei bug troppo lente, problemi specifici degli ambienti, ritardi nello sviluppo, errori manuali, rilasci falliti e scarsa qualità della vita per il personale IT.

### Cos'è DevOps?

DevOps è la pratica in cui ingegneri operativi e sviluppatori collaborano durante l'intero ciclo di vita del servizio, dalla progettazione attraverso il processo di sviluppo fino al supporto in produzione. Rappresenta la fusione dei ruoli di Sviluppo e Operations.

#### Valori Fondamentali (CAMS)

Il modello DevOps si basa su quattro valori fondamentali, noti come CAMS: Cultura (persone, processi e strumenti), Automazione (infrastruttura come codice), Misurazione (misurare tutto) e Condivisione (collaborazione e feedback).

#### Pilastri del DevOps

DevOps si fonda su tre pilastri essenziali: automazione dell'infrastruttura, consegna continua e ingegneria dell'affidabilità. Questi elementi costituiscono la base per un'implementazione efficace delle pratiche DevOps.

#### Infrastruttura come Codice

Il processo di sviluppo nell'infrastruttura come codice segue un flusso logico che parte dalla scrittura del codice, passa attraverso la validazione e i test unitari, prosegue con la costruzione di un artefatto, il suo deployment in ambiente di test, i test di integrazione e infine il deployment dell'artefatto in produzione.

#### Best Practice

Le migliori pratiche nel DevOps includono build veloci che passino il "test del caffè" (meno di 5 minuti), commit di piccole dimensioni, mantenere sempre la build funzionante, utilizzare un flusso di sviluppo basato su trunk/master, evitare test instabili e assicurarsi che ogni build restituisca uno stato (log) e un artefatto.

#### Strumenti

L'ecosistema DevOps utilizza vari strumenti come sistemi di controllo versione (Git, GitHub, CodeCommit), sistemi CI (Jenkins, Bamboo), strumenti di build (make, maven), framework di test, repository per artefatti (Artifactory, Dockerhub) e strumenti di deployment.

#### CI/CD

Il Continuous Integration è la pratica di unire costantemente il lavoro di sviluppo con il ramo principale. Il Continuous Delivery riguarda la consegna continua di codice a un ambiente quando è pronto, sia esso staging o produzione. Il Continuous Deployment si riferisce al rilascio del codice in produzione non appena è pronto.

La consegna continua comprende tre fasi principali: integrazione (CI) che include build e test, deployment (CD) che comprende deploy e test di integrazione, e infine delivery che estende il processo fino alla produzione.

Un principio fondamentale nel DevOps è la responsabilità: che il codice passi i test, venga deployato e rimanga funzionante per gli utenti è responsabilità dello sviluppatore, non di qualcun altro.

## 2.1 - Git

### Scenari Problematici senza Controllo Versione

Senza un sistema di controllo versione, gli sviluppatori affrontano vari problemi. Nel primo scenario, un programma funzionante smette di funzionare dopo una modifica e non riprende a funzionare anche ripristinando lo stato precedente. Nel secondo scenario, modifiche indipendenti funzionano separatamente ma creano problemi quando vengono unite. Nel terzo scenario, più sviluppatori apportano miglioramenti alla stessa classe e devono trovare un modo per unire efficacemente le modifiche.

### Sistemi di Controllo Versione

I sistemi di controllo versione mantengono versioni multiple di tutti i file, richiedono commenti per ogni modifica, consentono il check-in e check-out dei file per tracciare chi sta lavorando su cosa e visualizzano le differenze tra versioni. Utilizzare un controllo versione formale garantisce una storia dei cambiamenti, la possibilità di tornare indietro, elimina la preoccupazione di compromettere funzionalità esistenti e facilita la fusione di modifiche da più collaboratori.

### Git e GitHub

Git è un sistema di controllo versione distribuito gratuito e open source progettato per gestire progetti di ogni dimensione con velocità ed efficienza. GitHub è un servizio di hosting di repository Git basato sul web, che offre tutte le funzionalità di controllo della revisione distribuita e gestione del codice sorgente di Git oltre ad aggiungere funzionalità proprie.

### Storia e Concetto di Git

Git è stato originariamente sviluppato per lo sviluppo del kernel Linux. Nel 2005, a seguito di restrizioni sul sistema Bitkeeper precedentemente utilizzato, Linus Torvalds decise di creare un proprio strumento. Git è fondamentalmente un file system versionato su cui è stato sviluppato il sistema di controllo versione. Dispone di oltre 130 comandi, utilizza un modello di repository distribuito che può essere usato anche centralmente ed è particolarmente veloce.

### Utilizzo Base di Git

L'utilizzo base di Git comprende modificare file, verificare le modifiche con comandi come `git status`, `git diff` e `git log`, indicare quali modifiche salvare con `git add`, confermare le modifiche con `git commit`, inviarle a GitHub con `git push` e scaricare modifiche dei collaboratori con `git pull`.

### Best Practice con Git

Le migliori pratiche nell'uso di Git includono eseguire commit frequenti e di piccole dimensioni, rimanere sincronizzati con i collaboratori, inserire nel repository solo i file sorgente e non quelli derivati, e utilizzare un file .gitignore per indicare i file da ignorare.

### Gli Stati Locali in Git

Git riconosce tre stati locali per i file: la directory di lavoro dove si modificano i file, l'area di staging dove si preparano le modifiche per il commit, e il repository locale dove le modifiche sono salvate dopo il commit.

### Collaborazione con GitHub

Per contribuire a un repository esistente, si segue un processo che include: visitare il repository, crearne un fork, clonare la propria versione, apportare modifiche localmente, eseguire `git add` e `git commit`, inviare le modifiche al proprio repository GitHub con `git push`, e infine aprire una pull request per proporre le modifiche al repository originale.

## Metodologia Agile

### Cos'è un Progetto

Un progetto è un'impresa, condotta individualmente o in collaborazione, che può coinvolgere ricerca o design, pianificata attentamente per raggiungere un particolare obiettivo.

### Approccio Tradizionale vs Agile

Nell'approccio tradizionale, circa l'80% del tempo viene dedicato all'esecuzione e solo il 20% alla pianificazione. L'approccio Agile, formalizzato nel Manifesto Agile del 2001, valorizza:
- Individui e interazioni più che processi e strumenti
- Software funzionante più che documentazione esaustiva
- Collaborazione col cliente più che negoziazione contrattuale
- Rispondere al cambiamento più che seguire un piano

### Principi Agile

I principi Agile includono la priorità alla soddisfazione del cliente attraverso rilasci precoci e continui, l'accoglienza dei requisiti che cambiano, la consegna frequente di software funzionante, la collaborazione quotidiana tra business e sviluppatori, la costruzione di progetti intorno a individui motivati, la comunicazione faccia a faccia, l'uso del software funzionante come misura principale di progresso, lo sviluppo sostenibile, l'attenzione continua all'eccellenza tecnica, la semplicità, i team auto-organizzati e la riflessione regolare sul miglioramento.

### Scrum

Scrum è un processo Agile utilizzato per gestire progetti complessi dal 1990. Fornisce funzionalità di business in 30 giorni, con il business che stabilisce le priorità e i team che si auto-organizzano per determinare il miglior modo di consegnare le funzionalità più importanti. È scalabile a progetti distribuiti, grandi e di lunga durata, estremamente semplice ma molto difficile da implementare correttamente.

### Framework Scrum

Il framework Scrum comprende la pianificazione dello sprint con la definizione di "Done", la revisione dello sprint con la demo, la retrospettiva dello sprint e la riunione giornaliera scrum.

### Team Scrum

Un team Scrum è composto da sette (più o meno due) membri, è multifunzionale con competenze in testing, coding e architettura, seleziona gli obiettivi dello sprint e specifica i risultati del lavoro, ha il diritto di fare tutto entro i confini delle linee guida del progetto per raggiungere l'obiettivo dello sprint, si organizza autonomamente e dimostra i risultati del lavoro al Product Owner.

I ruoli chiave in Scrum sono:
- **Scrum Master**: assicura che il team sia pienamente funzionale e produttivo, facilita la cooperazione tra tutti i ruoli e le funzioni, rimuove gli ostacoli, protegge il team da interferenze esterne durante lo Sprint e garantisce che il processo sia seguito.
- **Product Owner**: definisce le caratteristiche del prodotto, decide sulla data di rilascio e sul contenuto, è responsabile della redditività del prodotto (ROI), stabilisce le priorità delle funzionalità in base al valore di mercato, regola funzionalità e priorità a ogni iterazione e accetta o rifiuta i risultati del lavoro.

### Burndown Chart

Il Burndown Chart visualizza graficamente il lavoro rimanente rispetto al tempo, aiutando il team a monitorare il progresso dello sprint e a prevedere se tutti gli elementi pianificati saranno completati entro la fine dello sprint.

### Kanban

Kanban è un altro approccio Agile a livello di team che si concentra sulla visualizzazione del flusso di lavoro, la limitazione del lavoro in corso (WIP), la misurazione e gestione del flusso, l'esplicitazione delle politiche di processo e il miglioramento collaborativo utilizzando modelli e metodo scientifico.

### Comunicazione del Team

Una comunicazione efficace del team è essenziale per il successo dei progetti Agile. Gli strumenti come Trello consentono di implementare facilmente un sistema Kanban per visualizzare e gestire il lavoro del team.

## Design as a Service

### Service Design

Il design del servizio è un approccio che considera l'esperienza completa dell'utente con un servizio, cercando di creare soluzioni che siano utili, utilizzabili e desiderabili per i clienti, oltre che efficienti ed efficaci per le organizzazioni.

### Best Practice

Le migliori pratiche nel design del servizio includono:
- Rimanere focalizzati sul cliente
- Rimanere attenti e adottare rapidamente le tendenze
- Prendere decisioni di alta qualità con alta velocità

### Caso Studio: TEDx

Il dataset TEDx contiene informazioni su circa 6.300 registrazioni audio-video di TED Talks caricate sul sito ufficiale TED.com (aggiornato al 15/03/2024). Il dataset è stato ottenuto con uno scraper basato su Selenium Web Driver per scopi accademici e didattici. I dati e lo scraper sono stati estratti dal sito ufficiale TED ed è disponibile sotto licenza MIT.

Per definire i sistemi e le idee di servizio basati su questo dataset, si possono utilizzare strumenti come draw.io per la progettazione del sistema e Trello per l'organizzazione e il tracciamento delle attività del progetto.