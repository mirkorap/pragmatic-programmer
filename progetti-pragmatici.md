# Progetti pragmatici

Una volta che il progetto è avviato occorre "tenerlo in vita". E' facile perdere la rotta e far naufragare un progetto. In questa ultima parte vedremo come mantenere un progetto attivo usando un approccio pragmatico.

### Team pragmatici

Finora abbiamo esaminato le tecniche pragmatiche che possono aiutare un singolo individuo ad essere un programmatore migliore. Le stesse tecniche possono essere applicate anche all'interno di un team.

### Niente finestre rotte

La qualità del codice è un problema dell'intero team, non del singolo individuo. E' molto importante che tutti i membri del team abbraccino la filosofia del _niente finestre rotte_.

### Tenere sott'occhio l'ambiente complessivo

Durante lo sviluppo del progetto è facile perdere di vista i cambiamenti che avvengono. Questo avviene soprattutto quando si lavora in team. I requisiti potrebbero cambiare, nuove caratteristiche possono essere aggiunte, i tempi di sviluppo si allungano e così via... Tutti questi cambiamenti devono essere tenuti sempre sott'occhio, non facciamoci assorbire solo dallo sviluppo del progetto.

### Comunicate!

Un aspetto fondamentale all'interno di un team è la comunicazione. E' importante che i membri del team si parlino e siano tutti allineati sullo sviluppo del progetto. Il team deve essere coordinato, durante le riunioni con il managment deve prevalere la voce dell'intero team e non del singolo individuo. La documentazione e la terminologia utilizzata dal team deve essere uguale per tutti: **il team deve essere un'unica entità**.

### Non ripetetevi

La duplicazione è uno degli aspetti peggiori per la manutenzione di un progetto. E' facile cadere nella duplicazione di codice quando si lavora in team. Chiaramente per evitare la duplicazione la comunicazione all'interno del team è fondamentale, ma a volte serve qualcosa di più. Il mio consiglio è quello di nominare uno o più "bibliotecari di progetto", ovvero una persona che abbia una conoscenza approfondita dell'intero codice scritto. Un altro consiglio è quello di sfruttare il sistema delle _code reviews_, ovvero far revisionare il codice a tutti i membri del team prima di metterlo in produzione.

### Ortogonalità

Un altro aspetto importante all'interno di un team è la divisione delle responsabilità. Nei team tradizionali questa divisione può essere rigida e sbagliata: ci sono analisti di business, architetti, progettisti, programmatori, tester, technical writer e così via. Questo però non da al team una visione d'insieme. Un programmatore che non interagisce con l'utente finale, non potrà mai sapere quali sono le reali esigenze di business dell'utente. Il mio consiglio è quello di organizzare il team in base alle funzionalità del progetto e non ai ruoli aziendali. Se il progetto richiede una sezione relativa alla creazione degli ordini d'acquisto, si potrebbe organizzare un team che si occupa esclusivamente di quella parte. Se è necessario che il programma abbia una sezione dedicata all'invio di newsletter, si potrebbe creare un team che si occupa dello sviluppo di quella precisa sezione. In questa maniera si riduce la confusione all'interno del gruppo e si evita il passaggio di parola infinito per arrivare alla fonte di conoscenza. Questa impostazione però funziona solo con sviluppatori responsabili. Creare una serie di team autonomi può infatti portare al disastro. Un progetto ha sempre bisogno di due teste: una tecnica e l'altra amministrattiva. Quella tecnica, ovvero il capo di progetto, si occupa di organizzare e coordinare i team e tiene sott'occhio il quadro generale del progetto. La parte amministrativa, il project manager, si occupa di organizzare le risorse, controllare e comunicare lo stato di avanzamento dei lavori e stabilire le priorità in base alle esigenze di business.

### Automazione

All'interno di un progetto è importante anche avere la figura del **tool builder**, ovvero una persona che si occupa di mettere in funzione tutta quella serie di strumenti che automatizzano la macchina del progetto. Fate produrre loro makefile, script di shell, pipeline e cose simili.

### Automazione onnipresente

Automatizzare i processi è un aspetto importante tanto quanto la codifica. Automatizzate le operazioni che dovete eseguire continuamente, non affidate al caso il successo di una procedura.

### Tutto in automatico

Esistono tanti modi per automatizzare i processi: creare makefile, script di shell, file da far eseguire al cron e così via. Qualsiasi sia il modo utilizzato ricordatevi di non lasciare alle persone l'onere di eseguire procedure manuali, poiché gli esseri umani possono commettere degli errori, i computer no.

### Compilazione del progetto

La compilazione del progetto è un'attività che deve essere affidabile e ripetibile. Consiglio l'utilizzo di makefile o script shell per eseguire questo tipo di procedure.

### Test di regressione

Potete usare makefile anche per eseguire i test all'interno del vostro progetto. Potete eseguire facilmente i test per il singolo modulo, una directory o per l'intero progetto.

### Automazione delle build

Il processo di build è un'altra operazione che deve essere eseguita automaticamente. Normalmente una build di progetto comprenderà i passi seguenti:

* Estrae il codice sorgente dal repository
* Costruisce il progetto da zero prendendo il codice estratto. Ogni build è contrassegnata da un numero di release
* Esegue una serie di operazioni per rendere il prodotto distribuibile: compila i sorgenti, imposta i permessi ai file e così via
* Esegue test specifici

Per la maggior parte dei progetti questo livello di build può essere eseguito automaticamente ogni notte sul server di testing.

### Automazione delle attività amministrative

Come per il processo di build anche altri processi, che non per forza devono essere strettamente legati allo sviluppo di software, possono essere automatizzati. Per esempi: se dovete presentare sul sito web aziendale il numero di righe di codice scritte o il numero di progetti sviluppati, potete creare un semplice script che legge queste informazioni dai repository e li pubblica automaticamente sul web. Qualsiasi sia il motivo applicate il principio DRY anche per quegli aspetti più banali.

### Test senza pietà

Uno degli aspetti più trascurati all'interno di un progetto sono i test. Molti sviluppatori tendono a creare test "morbidi", sapendo nel subconscio dove il codice fallirà ed evitando i punti deboli. Altri programmatori evitano proprio la creazione di test. I programmatori pragmatici preferiscono invece trovare gli errori oggi piuttosto che farli trovare ai propri utenti. Il mio consiglio è quello di scrivere codice di test contemporaneamente alla scrittura del codice di produzione \(o addirittura prima secondo il [TDD](https://it.wikipedia.org/wiki/Test_driven_development)\). In effetti, un buon progetto può avere più codice di test che codice di produzione. All'inizio può sembrare un dispendio di costi ed energie, ma alla lunga gli sforzi saranno tutti ripagati.

### Che cosa sottoporre a test

Esistono vari tipi di test, ecco quelli più conosciuti e utilizzati:

* unit test
* integration test
* esaurimento delle risorse
* performance test
* usability test

### Unit test

Uno unit test è codice che mette alla prova un modulo \(o classe\). Questo tipo di test è il fondamento di tutte le altre forme di test. Se le parti non funzionano isolatamente, probabilmente non funzioneranno bene neanche insieme.

### Integration test

I test di integrazione \(_integration test_\) servono a verificare come lavorano insieme un gruppo di moduli. I test di integrazione sono in realtà un'estensione degli unit test.

### Esaurimento delle risorse

Ora sapete che il vostro codice funziona in condizioni ideali, ma come si comporterà nelle condizioni del _mondo reale_? Nel mondo reale i vostri programmi non hanno risorse illimitate. Fra i limiti che il vostro codice potrebbe incontrare vi sono:

* memoria
* spazio su disco
* ampiezza di banda della CPU
* tempo
* ampiezza di banda del disco
* ampiezza di banda della rete

Se il codice non ha più memoria sufficiente fallisce in modo elegante o crasha improvvisamente facendo perdere tutto il lavoro svolto?

### Performance test

A volte è necessario sottoporre a test le prestazioni del sistema: **i cosidetti performance test o stress test**. Quanti utenti può supportare la vostra applicazione? In quanto tempo riesce ad inviare 10.000 email?

### Usability test

Il prodotto che avete creato è privo di bug, ma è anche facile da utilizzare? I test di usabilità vengono eseguiti con utenti reali e in condizioni ambientali reali. Essi servono a capire se il vostro prodotto è effettivamente usabile e si adatta agli utenti e non viceversa.

### Come sottoporre a test

Abbiamo visto che **cosa** sottoporre a test, ma adesso vediamo **come** sottoporlo a test, prestando particolare attenzione a:

* test di regressione
* dati di test
* collaudo dei sistemi GUI
* test dei test
* test esaustivi

### Test di regressione

Un test di regressione confronta l'output del test corrente con i valori precedenti \(o valori noti\). Possiamo così assicurarci che gli errori risolti oggi non hanno avuto conseguenze negative su cose che fino a ieri funzionavano bene. Tutti i test finora citati possono essere eseguiti come test di regressione.

### Dati di test

Da dove prendiamo i dati per eseguire tutti questi test? Esistono solo due tipi di dati: dati del mondo reale e dati di sintesi. I dati reali rappresentano i tipici dati che l'utente inserisce. I dati di sintesi invece sono generati artificialmente prendendo valori random o facendo riferimento a vincoli statistici. I motivi per cui è consigliabile usare i dati statistici sono numerosi:

* Servono molti dati, più di quelli che potrebbe fornire il mondo reale. Potreste riuscire a usare i dati reali come base per generare molti dati di sintesi.
* Servono dati per mettere alla prova le condizioni limite. La data 29 Febbraio 1999 oppure valori numerici molto grandi, sono solo alcuni esempi di dati di sintesi utilizzati per testare le condizioni di limite.
* Servono dati con determinate proprietà statistiche. Volete vedere come si comporta il codice se una transazione fallisce.

### Mettere alla prova sistemi GUI

Per mettere alla prova sistemi in cui hanno molto spazio le interfacce utente è necessario utilizzare strumenti di test specializzati. Esistono degli strumenti che consentono di costruire degli script che simulano le azioni che un utente può compiere all'interno dell'interfaccia grafica. Questi strumenti sono molto potenti e riescono ad adattarsi anche a piccole differenze di layout, qualora quest'ultimo abbia subito dei cambiamenti. Uno dei molti vantaggi di scrivere codice disaccoppiato è la maggiore modularità dei test. Quando la business logic è disaccoppiata dall'interfaccia utente è possibile sottoporre a test la logica dell'applicazione senza la presenza della GUI. Una volta validata la logica dell'applicazione, diventa più facile identificare gli errori quando si introduce l'interfaccia utente.

### Test dei test

Un consiglio per verificare che i vostri test funzionino è quello di provocare deliberatamente un errore all'interno del vostro sistema. Se l'errore viene segnalato dai vostri test vuol dire che il vostro sistema d'allarme funziona correttamente.

### Test esaustivi

Una volta che ho creato i test, come faccio a sapere se ho sottoposto a test sufficientemente completi la base di codice? La risposta, purtroppo, è "non è possibile saperlo". Esistono sul mercato degli strumenti che tengono traccia di quali righe di codice sono state sottoposte a test e quali no. Non aspettatevi di vedere una copertura del 100% per il vostro codice, infatti è molto difficile riuscirci. Qualora ci riusciste, il dato comunque sia non ci fornisce una risposta alla nostra domanda. Quel che importante è il numero degli stati che sottoponete a test e non le righe di codice che avete coperto con i test. Per esempio: supponiamo che abbiate una funzione che fa un calcolo su due interi, ciascuno dei quali può essere un numero tra 0 e 999:

```text
int test(int a, int b) {
    return a / (a + b);
}
```

In teoria questa funzione di tre righe ha 1.000.000 di stati logici, 999.999 dei quali funzioneranno correttamente e uno no \(quando a + b è uguale a zero\). Sapere semplicemente che una riga è stata sottoposta a test o meno non dice molto - dovete identificare tutti i possibili stati del programma. In generale questo è un problema davvero difficile.

### Quando sottoporre a test

Non lasciate i test come ultima cosa da fare. I test vanno fatti prima: non appena esiste del codice di produzione bisogna sottoporlo a test.

### E' tutta scrittura

Un aspetto trascurato dagli sviluppatori è la documentazione. E' uno dei compiti che spesso viene lasciato per ultimo o addirittura si spera di non dover nemmeno fare. Tuttavia la documentazione è parte integrante del processo di sviluppo. Si può rendere più facile la scrittura della documentazione se essa viene scritta contestualmente alla scrittura del codice. Esistono due tipi di documentazione: interna ed esterna. Quella interna comprende commenti al codice sorgente, documenti di progettazione e test. Quella esterna comprende tutta quella serie di manuali che vengono forniti all'utente per spiegargli il funzionamento dell'applicazione.

### Commenti nel codice

I commenti nel codice devono dire _perché_ è stata fatta una certa cosa, il suo senso e il suo scopo. Il codice già mostra _come_ è stata fatta, perciò ogni commento di questo tipo è una violazione del principio DRY. Un esempio di buoni commenti sono quei tipi di commenti che ci dicono: i compromessi tecnici, le ragioni per cui sono state prese determinate decisioni, quali alternative sono state scartate e così via \(vedi [Clean Code - Commenti](https://mirkorap16.gitbook.io/clean-code/commenti) per maggiori informazioni\). Attenzione a non riempire il codice di commenti: **ciò che è ovvio non deve essere commentato**. Piuttosto usate dei nomi significativi per spiegare il codice.

### Documenti eseguibili

Uno dei problemi nello scrivere la documentazione è quello della violazione del principio DRY. Immaginate che avete delle Rest API e da queste API dovete scrivere la relativa documentazione che spiega il loro utilizzo. Se fate delle modifiche alle API dovete ricordarvi di aggiornare anche la documentazione. Questa ridondanza delle informazioni può portare a delle discrepanze nel momento in cui vi scordate di aggiornare la documentazione. Un consiglio è quello di affidarvi a tool o librerie che leggono il codice e lo utilizzano come modello per creare la relativa documentazione sul Web. Questo vi permette di aggiornare il codice senza dovervi ricordare di aggiornare anche la relativa documentazione.

### Technical writer

Finora abbiamo parlato della documentazione interna, ovvero quella scritta dagli stessi programmatori. Anche per la documentazione esterna, ovvero i manuali utente spesso scritti dai technical writer, bisogna adottare gli stessi principi pragmatici: il principio DRY, l'ortogonalità, il concetto di model-view e l'uso dell'automazione.

### O lo stampi o lo intrecci

Uno dei problemi maggiori della documentazione cartacea è che diventa obsoleta nel momento esatto in cui viene stampata. Per tale ragione consiglio di pubblicare la documentazione sul Web, cosicché sia accessibile e modificabile da tutti. Se la stessa documentazione deve essere presentata in formati diversi: pdf, sul web, sotto forma di slides e così via, consiglio di utilizzare un linguaggio comune di markup e da questo produrre i diversi formati necessari. Il principio DRY va sempre rispettato, anche per la creazione di una semplice documentazione.

### Grandi speranze

Un'applicazione principalmente ha successo non perché è scritta bene, ma perché  soddisfa le aspettative dei suoi utenti. Un progetto che rimane al di sotto delle loro aspettative è considerato un fallimento. Come facciamo a non deludere le aspettative?

### Comunicare le aspettative

Gli utenti inizialmente arrivano da voi con una certa idea che vogliono sviluppare. Magari è incompleta, imprecisa e tecnicamente impossibile, ma è fondamentale che gli venga comunicato. Una volta che avete compreso i loro bisogni, lavorate con i vostri utenti in modo che la loro comprensione di ciò che realizzerete sia precisa. Dobbiamo gestire le loro aspettative e lavorare con loro per arrivare a una comprensione comune di quello che sarà il prodotto finale. Questo va fatto costantemente per tutto il processo di sviluppo. Alcune tecniche che ci agevolano in questo processo le abbiamo già viste: i [_Proiettili traccianti_](https://mirkorap16.gitbook.io/pragmatic-programmer/un-approccio-pragmatico#proiettili-traccianti), i [_Prototipi_](https://mirkorap16.gitbook.io/pragmatic-programmer/un-approccio-pragmatico#prototipi-e-post-it) __e i [_Post-it_](https://mirkorap16.gitbook.io/pragmatic-programmer/un-approccio-pragmatico#prototipi-e-post-it) __sono solo alcune di queste tecniche.

### Il miglio extra

Condividendo con gli utenti le loro aspettative non ci saranno molte sorprese quando il prodotto verrà finalmente consegnato. Tuttavia noi dobbiamo andare oltre e stupire i nostri utenti, dando loro qualcosa di più di ciò che si aspettavano. Per farlo possiamo introdurre quel minimo di caratteristiche in più per far felici i nostri utenti, ovvero quelle caratteristiche a basso costo che possiamo aggiungere con facilità all'interno del sistema. Un esempio sono:

* aiuto a fumetti con tooltip
* scorciatoie da tastiera
* una guida di consultazione rapida
* analizzatori di file di log
* una schermata iniziale personalizzata per la loro organizzazione

### Orgoglio e pregiudizio

I programmatori pragmatici non sfuggono di fronte alle responsabilità, anzi sono felici di accettare le sfide e di rendere ben nota la loro competenza. Essi sono fieri del codice che scrivono e nutrono un forte rispetto nei confronti degli altri loro colleghi. Non sono gelosi del proprio codice e delle proprie competenze, anzi li condividono insieme agli altri. Il vostro nome deve essere riconosciuto come indicatore di professionalità. Chi vede il vostro nome sul codice deve immaginare di stare per vedere un codice solido, ben scritto, collaudato e documentato. Un codice scritto da un vero **pragmatic programmer**.

