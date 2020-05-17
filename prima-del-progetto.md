# Prima del progetto

Prima che il progetto inizi è molto importante avere un'idea chiara di ciò che si deve fare. In questo capitolo vedremo una serie di operazioni che occorre effettuare per evitare che il progetto fallisca prima ancora di iniziare.

### La fossa dei requisiti

Una delle fasi preliminari di un progetto consiste nella raccolta dei requisiti. Raramente, però, i requisiti si trovano in superficie, normalmente sono sepolti sotto strati di presupposti e idee sbagliate.

### Scavare alla ricerca dei requisiti

Riconoscere un requisito può essere qualcosa di semplice, ma allo stesso tempo può diventare complesso. Diventa semplice se il requisito enuncia qualcosa che deve essere ottenuto. Buoni esempi di requisiti sono i seguenti:

* Il record di un dipendente può essere visto solo da un gruppo di persone indicate esplicitamente.
* L'editor evidenzierà le parole chiave che verranno selezionate in funzione del tipo di file che si sta modificando.

Un requisito diventa complesso quando mescola i requisiti con le norme aziendali. Se prendiamo il primo esempio e lo riformuliamo come segue: "Solo l'ufficio del personale può vedere il record di un dipendente" diventa subito un requisito complesso da capire, perché mescola il requisito con le norme aziendali. Questo potrebbe portare lo sviluppatore a codificare erroneamente la norma all'interno del sistema con il rischio che se un domani le norme cambieranno e oltre all'ufficio del personale anche il managment dovrà poter visualizzare quel record, lo sviluppatore dovrà rivedere tutto il sistema. Il mio consiglio è quello di documentare queste norme in forma separata dal requisito e di creare un semplice collegamento fra le due cose. Il requisito diventa così un enunciato generale e agli sviluppatori viene fornita l'informazione delle norme aziendali come esempio del tipo di cose che dovranno supportare nell'implementazione. Alla fine il vostro sviluppo deve risolvere il loro problema di business, non semplicemente soddisfare i requisiti così come li hanno formulati. E' importante scoprire il motivo di fondo per cui gli utenti fanno una particolare cosa, non solo il modo in cui oggi la fanno. Esiste una tecnica semplice per entrare dentro i requisiti degli utenti, ovvero lavorare a fianco di un utente, così da iniziare a pensare come un utente e non solo come uno sviluppatore.

### Documentare i requisiti

Un altro problema che emerge durante la raccolta dei requisiti è il come documentarli. Ivar Jacobson ha proposto il concetto di **casi d'uso** per catturare i requisiti. Essi permettono di descrivere un particolare uso del sistema - non in termini d'interfaccia utente, ma in modo più astratto. Esiste una metodologia, descritta da Alistair Cockburn, per rappresentare i casi d'uso. Ecco un esempio del suo modello:

**A. INFORMAZIONI CARATTERISTICHE**

* Obiettivo nel contesto
* Raggio d'azione
* Livello
* Precondizioni
* Condizione finale di successo
* Condizione finale di fallimento
* Attore primario
* Innesco

**B. SCENARIO PRINCIPALE DI SUCCESSO**

**C. ESTENSIONI**

**D. VARIAZIONI**

**E. INFORMAZIONI CORRELATE**

* Priorità
* Obiettivo di prestazioni
* Frequenza
* Caso d'uso sovraordinato
* Casi d'uso subordinati
* Canale all'attore primario
* Attori secondari
* Canale agli attori secondari

**E. PIANIFICAZIONE TEMPORALE**

**G. PROBLEMI APERTI**

Utilizzando un modello come questo potete essere sicuri di includere tutte le informazioni che vi servono in un caso d'uso. Ecco un esempio concreto applicando questo modello:

**CASO D'USO 5: ACQUISTO DI MERCI**

**A. INFORMAZIONI CARATTERISTICHE**

* **Obiettivo nel contesto**: ****l'acquirente emette un ordine alla nostra azienda e si aspetta che le merci vengano spedite e fatturate.
* **Raggio d'azione**: ****azienda
* **Livello**: ****riepilogo
* **Precondizioni**: conosciamo l'acquirente, il suo indirizzo ecc.
* **Condizione finale di successo**: l'acquirente ha le merci, noi abbiamo il denaro corrispondente
* **Condizione finale di fallimento**: noi non abbiamo spedito le merci, l'acquirente non ci ha spedito il denaro
* **Attore primario**: l'acquirente
* **Innesco**: arriva un ordine d'acquisto

**B. SCENARIO PRINCIPALE DI SUCCESSO**

* L'acquirente chiama ed effettua un ordine d'acquisto
* L'azienda registra i dati anagrafici dell'acquirente: indirizzo, merci ordinate...
* L'azienda fornisce all'acquirente informazioni sulle merci, i prezzi, le date di consegna...
* L'acquirente firma l'ordine
* L'azienda prepara le merci per evadere l'ordine e le spedisce all'acquirente
* L'azienda invia una fattura all'acquirente
* L'acquirente paga quanto fatturato

**C. ESTENSIONI**

* L'azienda ha esaurito uno dei prodotti ordinati: l'ordine viene rinegoziato
* L'acquirente paga direttamente con carta di credito \(vedi caso d'uso 44\)
* L'acquirente restituisce la merce: gestione delle merci rese \(vedi caso d'uso 105\)

**D. VARIAZIONI**

* L'acquirente può ordinare per telefono, fax o via web
* L'acquirente può pagare in contanti, bonifico o carta di credito

**E. INFORMAZIONI CORRELATE**

* **Priorità**: massima
* **Obiettivo di prestazioni**: 5 minuti per ordine
* **Frequenza**: 200 al giorno
* **Caso d'uso sovraordinato**: gestione della relazione con il cliente \(vedi caso d'uso 2\)
* **Casi d'uso subordinati**:
  * Creazione dell'ordine \(vedi caso d'uso 15\)
  * Gestione pagamento tramite carta di credito \(vedi caso d'uso 44\)
  * Gestione dei resi \(vedi caso d'uso 105\)
* **Canale attore primario**: telefono
* **Attori secondari**: società delle carte di credito, banca, spedizioniere

**F. PIANIFICAZIONE TEMPORALE**

* Data di consegna: release 1.0

**G. PROBLEMI APERTI**

* Che cosa succede se possiamo evadere l'ordine solo parzialmente?
* Che cosa succede se la carta di credito risulta scaduta?

### Diagrammi di casi d'uso

Molti vanno ad esprimere i casi d'uso mediante diagrammi di attività UML. Tuttavia questi diagrammi non potranno mai esprimere in maniera completa tutte le informazioni del caso d'uso. Il mio consiglio è quello di utilizzare i diagrammi solo per rappresentare il flusso di lavoro e non per esprimere il caso d'uso. Quest'ultimo deve essere espresso in maniera testuale.

### Specificazioni eccessive

Un pericolo serio nella produzione di un documento di requisiti è scendere troppo nello specifico. Questo non significa che potete essere vaghi: dovete specificare i requisiti in maniera astratta e indicare le pratiche di lavoro come norme. I requisiti non sono nè architettura e nè interfaccia utente: essi sono **esigenze**.

### Solo una cosina ancora...

Molti fallimenti di progetti sono attribuiti al progressivo aumento delle caratteristiche da inserire. Spesso i clienti ci chiedono di aggiungere nuove funzionalità in corso d'opera, dopo che i requisiti del progetto sono stati già stilati. Queste nuove funzionalità, che purtroppo spesso non vengono prese in considerazione dal management, non fanno altro che posticipare la data di consegna del progetto. Alla fine gli sviluppatori vengono sempre accusati di essere in ritardo nella consegna e imprecisi nell'aver dato le stime. In realtà sarebbe utile tenere traccia di tutte queste funzionalità che sono state aggiunte in corso d'opera: chi ha richiesto la modifica, chi l'ha approvata, quante richieste sono state già approvate e così via.

### Usate un glossario di progetto

Non appena si comincia a parlare di requisiti, utenti ed esperti del settore useranno certi termini che hanno per loro un significato specifico. Create e tenete sempre aggiornato un **glossario di progetto**: un luogo in cui sono definiti tutti i termini specifici utilizzati nel progetto. Questo è uno dei concetti che sta alla base del [Domain-Driven Design](https://it.wikipedia.org/wiki/Domain-driven_design) \(DDD\).

### Risolvere rompicapi impossibili

A volte, mentre codifichiamo, ci troviamo di fronte a problemi che ci sembrano irrisolvibili. Il segreto per risolvere problemi di questo tipo è di identificare i vincoli reali e di trovare una soluzione in base a quelli.

### Gradi di libertà

Per risolvere un problema "impossibile" dovete prima identificare i vincoli più restrittivi e poi sistemare dentro i vincoli restanti. Successivamente enumerate tutte le possibili strade che avete davanti. Non escludete nulla, non importa quanto sembri inutilizzabile e stupido. Ora scorrete la lista e spiegate perché non si può prendere una certa strada. Ne siete sicuri? Potete dimostrarlo? Così facendo la soluzione al problema vi si parerà di fronte agli occhi.

### Deve esserci un modo più facile!

A volte vi troverete a lavorare su un problema che sembra molto più difficile di quel che pensavate. Magari vi state disperando perché state mancando la scadenza. E' il momento di fare un passo indietro e porsi qualche domanda:

* Esiste un modo più facile?
* State tentando di risolvere il problema giusto o siete stati distratti da qualcos'altro?
* Perché questa cosa è un problema?
* Che cosa lo rende così difficile da risolvere?
* Deve essere fatto in questo modo?
* Deve proprio essere fatto?

Molte volte cercare di dare una risposta a queste domande produce una rivelazione sorprendente.

### Non finché non siete pronti

A volte capita che ci sediamo di fronte al computer per scrivere codice, ma ad un certo punto iniziano a sorgerci dei dubbi. Una vocina dentro di noi ci dice: "Aspetta, risolvi prima i tuoi dubbi e poi ritorna a scrivere". Quando accade ciò fermatevi: ascoltate la vocina interiore e prima di ritornare a scrivere codice risolvete i vostri dubbi.

### Sano giudizio o procrastinazione?

Quando si lavora ad un progetto i dubbi possono essere tanti. Uno fra questi è la "sindrome da foglio bianco". Dovete iniziare un nuovo progetto, ma non sapete proprio da dove cominciare. State procrastinando o state semplicemente aspettando che tutti i pezzi vadano al loro posto? Una tecnica per risolvere i vostri dubbi è quella di iniziare con un prototipo. Se mentre prototipate vi state rendendo conto che state sprecando tempo, allora vuol dire che stavate procrastinando il lavoro. Se così non fosse, man mano che proseguite con il prototipo, ad un certo punto vi verrà l'illuminazione e i dubbi all'improvviso scompariranno. Quello è il momento perfetto per iniziare con il nuovo progetto.

### La trappola delle specifiche

La specifica di un programma è il processo per cui si prende un requisito e lo si chiarisce al punto in cui può subentrare la competenza di un programmatore. Le specifiche comunicano agli sviluppatori i dettagli di come dovrà funzionare il sistema. Un problema che può insorgere quando si scrivono le specifiche è quello di non sapersi fermare. Spesso si cerca la perfezione inserendo ogni minuscolo dettaglio nelle specifiche. Tuttavia questo può essere controproducente. In primo luogo è ingenuo pensare che una specifica possa catturare ogni particolare di un sistema: le specifiche sono scritte e lette da esseri umani e questo porta sempre e comunque alla libera interpretazione. Inoltre è molto improbabile che il cliente sappia esattamente di cosa ha bisogno già all'inizio di un progetto. Potrà dire di capire i requisiti, ma potete stare certi che, non appena vedrà girare il sistema, vi chiederà di effettuare dei cambiamenti. In secondo luogo specifiche troppo dettagliate vincolerebbero eccessivamente il lavoro di programmazione. Se doveste seguire per filo e per segno le specifiche descritte, non avreste margine di manovra nell'implementazione di un sistema. Cercate invece di vedere specifiche e implementazione come aspetti diversi di uno stesso processo - un tentativo di catturare e codificare un requisito. Questo non significa che le specifiche sono inutili, anzi sono necessarie per chiarire i dubbi degli sviluppatori. Ricordate semplicemente che si raggiunge un punto in cui i benefici diminuiscono o diventano addirittura negativi nel momento in cui le specifiche diventano eccessivamente dettagliate.

### Cerchi e frecce

Le metodologie come: la programmazione strutturata, gli [strumenti CASE](https://it.wikipedia.org/wiki/Computer-aided_software_engineering), i diagrammi ER, i diagrammi UML e così via, hanno da sempre avuto un posto importante nella storia della programmazione. Tuttavia queste metodologie non devono essere abbracciate ciecamente, ma devono essere viste con occhio critico. La filosofia "Il diagramma è l'applicazione, il resto è solo codifica meccanica" è assolutamente falsa. I metodi formali hanno alcuni svantaggi:

* La maggior parte dei metodi formali cattura i requisiti con una combinazione di diagrammi e un po' di parole di supporto. Questi diagrammi rappresentano la compresione che i progettisti hanno dei requisiti. In molti casi però quei diagrammi non hanno alcun significato per gli utenti finali. Questo significa che devono essere i progettisti a spiegare agli utenti finali come essi hanno interpretato i requisiti. E' come se il ruolo venisse invertito.
* I metodi formali non sempre riescono a descrivere esattamente il funzionamento del sistema. Solo mentre codificate avete una chiara idea di cosa il sistema deve fare.

In sintesi, i metodi formali sono utili? Assolutamente sì, ma occorre usarli con giudizio. Non dovete mai diventare schiavi di una metodologia. Usate i metodi formali come un qualsiasi altro strumento della vostra cassetta degli attrezzi.

