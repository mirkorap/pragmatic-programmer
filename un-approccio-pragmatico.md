# Un approccio pragmatico

Vi sono suggerimenti e trucchi che facilitano lo sviluppo software in tutti i suoi livelli. In questo capitolo vogliamo unire queste idee e questi processi per poter scrivere del codice migliore, più veloce e più robusto.

### I mali della duplicazione

Quando sviluppiamo non facciamo altro che trasferire la conoscenza documentata nelle specifiche in codice comprensibile dalla macchina. Purtroppo, però, questa conoscenza non è stabile e spesso cambia a seguito di una semplice riunione con il cliente. Questa instabilità ci porta a passare gran parte del nostro tempo in modalità "manutenzione", riorganizzando il nostro codice. Molti pensano che la manutenzione inizi quando l'applicazione viene pubblicata, in realtà lo sviluppatore è sempre in modalità manutenzione: ad ogni cambio o aggiunta di requisito siamo costretti a rivedere e riorganizzare il nostro codice. L'unico modo per rendere il codice più facile da comprendere e da manutenere è quello di seguire il **principio DRY** \(_Don't Repeat Yourself\)_. Ogni elemento di conoscenza in un sistema deve avere un'unica rappresentazione, ovvero la stessa cosa non deve essere espressa in due o più luoghi.

### Come nasce una duplicazione?

Tutti i casi di duplicazione possono ricadere in una di queste categorie:

* **Duplicazione imposta:** gli sviluppatori pensano di non avere scelta: l'ambiente sembra obbligarli alla duplicazione.
* **Duplicazione inavvertita:** gli sviluppatori non si rendono conto che stanno duplicando le informazioni.
* **Duplicazione per impazienza:** gli sviluppatori impigriscono e duplicano perché sembra più facile.
* **Duplicazione fra sviluppatori:** persone diverse in un team duplicano un pezzo d'informazione.

### Duplicazione imposta

A volte sembra che la duplicazione ci venga imposta, tuttavia ci sono alcuni trucchi che ci consentono di rispettare il principio DRY e allo stesso tempo ci rendono la vità più semplice.

**Più rappresentazioni della stessa informazione:** spesso abbiamo bisogno della stessa informazione rappresentata in forme diverse. Immaginate che state scrivendo un'applicazione in cui gli attributi di una classe rispecchiano lo schema di una tabella di un database. Invece di duplicare l'informazione in entrambe le parti, potete utilizzare qualche tool di migration che si occupa di generare lo schema delle tabelle a partire dalle informazioni di una classe model.

**Duplicazione nel codice:** un altro caso di duplicazione imposta si ha quando vengono utilizzati i commenti per descrivere parti di codice. In questo modo non facciamo altro che ripetere la stessa informazione sia sotto forma di commento che sotto forma di codice. Se un domani dovessimo fare una modifica a quella parte di codice, ci dovremmo ricordare di modificare anche il commento, perché altrimenti quest'ultimo diventerebbe obsoleto. Pertanto cerchiamo di ridurre al minimo indispensabile l'utilizzo dei commenti e di utilizzare invece il codice per spiegare quello che stiamo facendo.

### Duplicazione inavvertita

In alcuni casi la duplicazione nasce come risultato di errori di progettazione. Immaginate che avete due classi: `Employee` e `Company`, ed entrambe hanno la necessità di conservare l'informazione relativa all'indirizzo, ovvero: provincia, città, cap, via e civico. Invece di ripetere queste proprietà su entrambe le classi, potete creare una classe `Address` per la rappresentazione di queste informazioni, così da evitare la duplicazione dei dati.

### Duplicazione per impazienza

Spesso duplichiamo il codice per semplice pigrizia. Vi serve una funzionalità molto simile a quella sviluppata in un altro modulo? Sarete tentati di copiare l'originale e di fare qualche modifica. Se sentite questa tentazione, ricordate: "le scorciatoie creano lunghi ritardi". Risparmierete magari qualche secondo sul breve periodo, ma a lungo andare vi troverete ad affrontare problemi che vi faranno perdere molte ore.

### Duplicazione fra sviluppatori

Il tipo di duplicazione più difficile da identificare è quello che si verifica quando più sviluppatori lavorano a uno stesso progetto. Capita che intere funzionalità vengono duplicate inavvertitamente. Il modi migliori per affrontare il problema sono: avere un leader tecnico che abbia una visione generale del progetto e della sua struttura, avere una divisione chiara delle responsabilità all'interno del progetto e, soprattutto, favorire la comunicazione e lo scambio di informazioni tra gli sviluppatori attraverso chat di gruppo e richieste di revisione del codice \([pull-requests](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests)\).

### Ortogonalità

Il concetto di ortogonalità è fondamentale se volete produrre dei sistemi facili da progettare, collaudare ed estendere. In informatica questo termine prende il significato di **indipendenza / disaccoppiamento**. Due o più cose sono ortogonali se le variazioni nell'una non influenzano le altre.

### Benefici dell'ortogonalità

I sistemi non ortogonali sono più complessi da modificare ed estendere. In questi sistemi i componenti sono fortemente interdipendenti: una modifica ad un componente porterà degli effetti indesiderati sugli altri componenti. Quando i componenti sono ben isolati l'uno dall'altro, sappiamo di poterne modificare uno senza doverci preoccupare del resto. Se non si cambiano le interfacce esterne di quel componente, si può stare tranquilli che non si causeranno problemi che possano propagarsi a tutto il sistema. Con i sistemi ortogonali si ottengono due benefici: si aumenta la produttività e si riduce il rischio.

### Aumento di produttività

* Componenti piccoli e indipendenti sono più semplici da progettare e collaudare.
* Un approccio ortogonale promuove il riuso. Se i componenti hanno responsabilità specifiche e ben definite, essi possono essere combinati con altri componenti dando vita a nuove funzionalità.

### Riduzione del rischio

* Se un modulo ha qualcosa che non va è meno probabile che diffonda i problemi in giro per il resto del sistema.
* Un sistema ortogonale è più facile da testare.
* In un sistema ortogonale i cambiamenti sono localizzati e questo rende il sistema molto meno fragile.

### Team di progetto

Un sistema non ortogonale causa problemi anche all'interno del team stesso, perché una modifica effettuata da un team potrebbe influenzare l'area di competenza di un altro team. Per risolvere in parte il problema bisognerebbe iniziare a separare l'infrastruttura dall'applicazione. Un team si occuperà dei componenti infrastrutturali \(database, interfaccia di comunicazione e così via\), mentre un altro team si occuperà delle funzionalità dell'applicazione. In quest'ultimo team si potrebbero creare dei sotto-team a cui verrà assegnato il compito di sviluppare una determinata funzionalità del progetto.

### Toolkit e librerie

Quando introducete una libreria di terze parti chiedetevi sempre se impone al vostro codice cambiamenti che danneggiano l'ortogonalità del sistema. Mantenere questi dettagli isolati dal codice vi da il vantaggio di rendere più facile il passaggio ad altre librerie in futuro.

### Codifica

Ogni volta che si scrive codice si corre il rischio di ridurre l'ortogonalità dell'applicazione. Esistono varie tecniche per evitare ciò:

* **Mantenete disaccoppiato il codice:** scrivete codice "timido", ovvero moduli che rivelano solo lo stretto necessario agli altri moduli \(non rendete tutte le funzioni pubbliche\). Rispettate la [_Legge di Demetra_](https://it.wikipedia.org/wiki/Legge_di_Demetra). Se dovete cambiare lo stato di un oggetto fatelo fare all'oggetto stesso.
* **Evitate dati globali:** ogni volta che il vostro codice fa riferimento a dati globali si lega agli altri componenti che condividono quei dati.
* **Evitate funzioni simili:** fate aderire il vostro codice al principio DRY.
* **Cercate di essere critici** **rispetto al vostro codice:** abituatevi a controllare e riorganizzare costantemente il vostro codice. Questo processo viene chiamato _refactoring_.

### Test

Se i componenti sono ben isolati è più facile testare i singoli moduli \(_unit testing\)._ Un altro modo per valutare l'ortogonalità di un sistema è quando si effettua _bug fixing._ Quando risolvete un bug dovete modificare pochi moduli oppure la modifica vi costringe a rivedere tutto il sistema?

### Vivere con l'ortogonalità

L'ortogonalità è in stretto contatto con il principio DRY. Con DRY si punta a ridurre al minimo la duplicazione in un sistema, mentre con l'ortogonalità si riduce l'interdipendenza fra i componenti. Applicando entrambi vi troverete ad avere sistemi più facili da sviluppare, collaudare ed estendere.

### Reversibilità

I concetti espressi in precedenza hanno un obiettivo in comune: la produzione di software flessibile. Non sempre le decisioni migliori si prendono al primo tentativo. Oggi magari state utilizzando la libreria del produttore A, ma domani potrebbe uscire una libreria migliore da parte del produttore B. Oggi state utilizzando un database relazionale, ma domani scoprite che un database non relazionale si adatta meglio al vostro progetto. Questi dettagli potrebbero cambiare nel futuro, così come possono cambiare i requisiti e l'hardware su cui deve girare il vostro sistema. Avere un sistema con scarso incapsulamento, elevato accoppiamento e logica codificata in modo rigido vi renderà difficile apportare questo tipo di cambiamenti.

### Proiettili traccianti

A volte dobbiamo fare i conti con progetti totalmente nuovi, mai costruiti prima, di cui non abbiamo idea di come inziare. Magari dovete utilizzare degli algoritmi, tecniche, linguaggi o librerie che non vi sono molto familiari. Un approccio pragmatico a questo genere di situazioni è quello di utilizzare dei **"proiettili traccianti"**.

### Codice che brilla nel buio

I proiettili traccianti sono speciali proiettili che contengono una carica pirotecnica che consente al tiratore di capire in quale direzione va il proiettile. Il codice tracciante fa la stessa cosa, ovvero ci permette di avere rapidamente una base minima del sistema finale. In campo business ci si riferisce ad esso con il termine di **MVP** \(_Minimum Viable Product_\). Il codice tracciante non è "a perdere": lo si scrive per conservarlo. Contiene tutti gli elementi e la struttura base del sistema finale, solo che non è completo e non è del tutto funzionante. Man mano che si va avanti nello sviluppo si aggiungono pezzi e si avanza sempre di più verso l'obiettivo finale. Lo sviluppo tracciante è coerente con l'idea che un prodotto non è mai finito: ci saranno sempre cambiamenti da apportare e funzioni da aggiungere. E' un approccio incrementale.

### I vantaggi del codice tracciante

Ecco alcuni vantaggi nell'utilizzo dello sviluppo tracciante:

* **Gli utenti possono vedere presto qualcosa che funziona:** gli utenti sanno di guardare qualcosa di incompleto. Non saranno delusi dalla mancanza di molte funzionalità, anzi saranno entusiasti di vedere qualche progresso concreto verso il loro sistema finale.
* **Gli sviluppatori costruiscono una struttura in cui lavorare:** vi troverete una struttura di base in cui lavorare, dove aggiungere man mano le nuove funzionalità.
* **Avete qualcosa da mostrare:** la dirigenza ha la tendenza di volere subito qualcosa da mostrare al cliente. Con lo sviluppo tracciante avete sempre qualcosa da mostrare.
* **Avete una percezione migliore dell'andamento del lavoro:** una volta definita la base del sistema i casi d'uso successivi verranno implementati uno alla volta. In questa maniera si evitano periodi troppo lunghi di blocco in cui non viene rilasciato nulla.

### Codice tracciante contro prototipazione

Potete pensare che questa idea del codice tracciante non sia altro che la prototipazione, ma c'è una differenza. Con il prototipo si mira a esplorare aspetti specifici del sistema finale. Con un prototipo si butta via tutto quello che si è messo insieme per mettere alla prova un'idea e si ricodifica da zero sfruttando quel che si è imparato. Il codice tracciante, invece, vi permette di creare una bozza del sistema finale, così da avere sia qualcosa da poter mostrare ai vostri clienti e sia una base da dare agli altri sviluppatori su cui andare a inserire le successive funzionalità. In sintesi, la prototipazione genera codice "a perdere", utile per esplorare campi del sistema finale, mentre il codice tracciante è un codice _lean_, magro ma completo, che costituisce parte del sistema finale.

### Prototipi e Post-it

I prototipi del software, così come quelli realizzati in altri settori, vengono utilizzati per analizzare e mettere alla prova un'idea prima di produrla su larga scala. Non per forza i prototipi devono essere basati sul codice. Per esempio, l'utilizzo dei post-it sono un ottimo modo per prototipare il flusso di lavoro e la logica di un'applicazione. Un'interfaccia utente si può prototipare con un mock-up non funzionale disegnato con un programma di disegno a punti. I prototipi ignorano tutti i dettagli non importanti e si focalizzano solo sull'analisi di un'idea. Se però vi rendete conto che non potete rinunciare ai dettagli, magari uno sviluppo in stile proiettili traccianti in quel caso sarebbe più appropriato.

### Cose da prototipare

Possiamo prototipare tutto ciò che non è stato mai provato prima, che è sperimentale o di cui nutriamo dei forti dubbi. Potete prototipare:

* architettura
* nuove funzionalità in un sistema esistente
* strumenti o componenti di terze parti
* problemi di prestazioni
* il design dell'interfaccia utente

### Come usare i prototipi

Quando costruite un prototipo potete ignorare questi dettagli:

* **Correttezza:** potete usare dati fittizzi.
* **Completezza:** il prototipo può funzionare in maniera molto limitata, magari con un solo gruppo di dati di input.
* **Robustezza:** è probabile che la verifica degli errori sia incompleta o del tutto assente.
* **Stile:** il codice di un prototipo probabilmente non dovrà essere pulito e chiaro. Considerate sempre che tutto il codice che scriverete verrà buttato dopo aver messo alla prova la vostra idea.

### Prototipi di architettura

I prototipi vengono utilizzati anche per capire come il sistema deve stare insieme nel complesso, rimandando a più tardi i dettagli. Per fare questo spesso viene utilizzata una lavagna con i post-it. Ecco alcune aree in cui vengono utilizzati i prototipi per indagare sull'architettura di un sistema:

* Analizzare le responsabilità che devono avere i componenti
* Analizzare come i componenti devono collaborare tra di loro
* Analizzare le possibili fonti di duplicazione tra i componenti

### Stime

Dare le stime su un progetto è una delle cose più difficile e meno piacevoli che un programmatore deve fare. Le stime ci mettono paura, ma ci sono alcuni trucchi che possono renderle meno spaventose.

### Quanto accurato è abbastanza accurato?

La prima domanda che dovete porvi quando qualcuno vi chiede una stima è quale sia il contesto in cui verrà ricevuta la vostra risposta. Ha bisogno di una stima molto precisa oppure vuole un'indicazione di massima? Una delle cose interessanti sulle stime è che le unità di misura che usate fanno una differenza nell'interpretazione del risultato. Se dite che per fare una certa cosa impiegherete 130 giorni lavorativi, l'interlocutore si aspetterà che ci mettiate esattamente quei giorni per terminare quella cosa. Se invece dite che ci metterete circa 6 mesi, l'interlocutore si aspetterà che finiate il lavoro tra i 5 e i 7 mesi. Entrambi i valori rappresentano lo stesso risultato, ma l'unità di misura utilizzata cambia la percezione del tempo che impiegherete. Vi consiglio di formulare le vostre stime dei tempi in questo modo:

| **Durata** | Indicate la stima in |
| :--- | :--- |
| 1 - 15 giorni | giorni |
| 3 - 8 settimane | settimane |
| 8 - 30 settimane | mesi |
| Oltre 30 settimane | anni |

### Chiedete a qualcuno

La stima non è altro che una valutazione sui tempi che si impiegano nello sviluppare una funzionalità o nella risoluzione di un problema. Funzionalità e problemi potrebbero essere già stati affrontati da qualcun altro, magari da un vostro collega. Prima di impegnarvi nel dare una stima vedete se qualche vostro collega ha già dovuto affrontare una situazione simile. Le esperienze degli altri ci possono aiutare nel dare delle stime più precise.

### Capire la domanda

Prima di dare una stima assicuratevi di aver capito bene quello che vi è stato chiesto. Inoltre, nel dare i tempi di stima, puntualizzate il contesto in cui le state dando: "Ipotizzando che le APIs di terze parti ci forniscono queste informazioni in questa maniera dovrei metterci circa 2 settimane".

### Costruire un modello del sistema

Una volta compresa la domanda occorre costruire un modello di come dovrà funzionare il sistema. Il modello può essere costruito utilizzando una semplice lavagna, dei post-it oppure attraverso la costruzione di semplici diagrammi di flusso.

### Suddividere il modello in componenti

Una volta che avete un modello potete suddividerlo in componenti. Potete abbozzare, sotto forma di grafici, il ruolo di ciascun componente e come essi interaggiscono tra di loro. Vedrete che ciascun componente darà un contributo differente al modello complessivo del sistema. Il trucco è quello di spezzare la stima del sistema finale in **stime parziali**: una per ogni componente del sistema.

### Calcolare le risposte

Solo nei casi più semplici una stima darà una singola risposta. Nel dare una stima consiglio sempre di dare tre risposte:

* **Stima ottimistica \(O\):** tutto deve procedere come pianificato senza alcun intoppo.
* **Stima nominale \(N\):** questa è la stima che con più probabilità si verificherà.
* **Stima pessimistica \(P\):** tutto andrà storto, niente è andato come pianificato.

Da questi tre valori è possibile calcolare la durata prevista per un task:

$$
µ = (O + 4N + P) / 6
$$

Ma questa è solo una media basata su alcuni coefficienti e non può essere utilizzata come scadenza, è solo un **suggerimento**. Possiamo allora andare a calcolare la deviazione standard del task: ovvero la misura di quanto imprecisa è la nostra stima.

$$
σ = (P – O) / 6
$$

Per esempio, immaginate che dovete stimare **in giorni** quanto impiegherete ad implementare la funzionalità X. Per farlo date le seguenti stime:

* **Stima ottimistica \(O\):** 3 giorni
* **Stima nominale \(N\):** 5 giorni
* **Stima pessimistica \(P\):** 12 giorni

Quindi la durata prevista per il task sarà:

$$
µ = (3 + (4 * 5) + 12) / 6
$$

Vale a dire circa 6 giorni. Andiamo adesso a calcolare quanto la nostra stima è precisa:

$$
σ = (12 – 3) / 6
$$

Vale a dire 1.5 giorni. Questo significa che per completare la funzionalità X impiegheremo dai 4.5 ai 7.5 giorni. Il mio consiglio per avere una stima quanto più precisa è quello di applicare questo calcolo ad ogni piccola funzionalità da implementare all'interno del sistema, così da avere un'idea chiara del tempo che impiegherete per implementare ciascuna funzionalità.

**NB:** _questa parte sul calcolo delle tre tipologie di stime non è presente nel libro originale "The Pragmatic Programmer", ma bensì nel libro "The Clean Coder" di Robert C. Martin. Per approfondire l'argomento consiglio la lettura di questo articolo:_ [_https://codingjourneyman.com/2014/10/06/the-clean-coder-estimation_](https://codingjourneyman.com/2014/10/06/the-clean-coder-estimation/)\_\_

### Tenete traccia delle proprie stime

Tenete traccia delle stime fatte, così da vedere quanto erano azzeccate. Col passare del tempo questo vi permetterà di fare stime sempre più accurate. Quando una stima si rivela sbagliata scoprite perché la realtà è stata diversa dalle vostre congetture.

### Che cosa dire quando viene chiesta una stima?

Rispondete: "Mi faccio sentire io".

Quasi sempre otterrete risultati migliori se rallentate il processo e prendete tempo nel riesaminare i passi descritti in questa sezione.

