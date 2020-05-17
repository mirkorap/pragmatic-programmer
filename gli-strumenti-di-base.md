# Gli strumenti di base

I programmatori, come dei bravi artigiani, nella loro vita quotidiana fanno affidamento a tutta una serie di strumenti che gli consente di essere più produttivi durante il lavoro. In questo capitolo vedremo gli strumenti base che ogni sviluppatore dovrebbe imparare ad utilizzare.

### Il potere del puro testo

Il materiale di base che ogni artigiano del software utilizza non è il legno, ma bensì la conoscenza. Raccogliamo i requisiti come conoscenza e poi trasferiamo questa conoscenza nei nostri progetti attraverso il codice, in _puro testo_.

### Che cos'è il puro testo?

Il _puro testo_ \(_plain text_\) è costituito da caratteri stampabili in forma direttamente leggibile e comprensibile dagli esseri umani. Per esempio, il frammento seguente è costituito da caratteri stampabili, ma è senza senso:

```text
Field19=467abe
```

Il lettore non ha idea di quale sia il significato di `467abe`. Per renderlo **comprensibile** agli esseri umani possiamo scriverlo così:

```text
DrawingType=UMLActivityDrawing
```

Il testo puro tendenzialmente è a un livello più alto rispetto ad una codifica binaria. Esso consente di rendere i dati autodescrittivi e comprensibili all'essere umano.

### Svantaggi

L'uso del puro testo presenta due svantaggi:

* Può richiedere più spazio di un formato binario compresso.
* Può essere più costoso dal punto di vista computazionale interpretare ed elaborare un file di puro testo.

Con la tecnologia che oggi abbiamo a disposizione, difficilmente questi due svantaggi possono rappresentare un problema nella scrittura di un'applicazione, tuttavia è bene sottolineare questa differenza rispetto al formato binario.

### Il potere del testo

Quali sono quindi i benefici del puro testo?

* Garanzia contro l'obsolescenza
* Potenza
* Maggiore facilità di test

### Garanzia contro l'obsolescenza

Dati leggibili dagli esseri umani e dati che si autodescrivono sopravviveranno più a lungo rispetto a dei dati espressi in formato binario: anche dopo anni dalla commercializzazione dell'applicazione potrete leggere il codice che ci sta dietro e, senza avere una conoscenza di cosa faccia l'applicazione, riuscirete facilmente a comprenderne le funzionalità.

### Potenza

Al giorno d'oggi ogni strumento dell'universo informatico, dai sistemi di controllo del codice agli editor, opera con il puro testo. Questo non solo ci consente di scrivere in puro testo, ma anche di utilizzare altri strumenti che riescono a comprendere ciò che noi scriviamo.

### Maggiore facilità di test

Se usate il puro testo anche i dati saranno più semplici da collaudare e modificare a seguito dei risultati dei test.

### Giochi di shell

Un altro strumento indispensabile per un programmatore è la shell di comando. Attraverso la shell è possibile utilizzare tutta una serie di strumenti messi a disposizione dal vostro computer e di combinarli, usando il _pipe_, in modi del tutto originali. La nuova generazione di programmatori si potrebbe chiedere: "Perché devo utilizzare la shell se posso fare tutto tramite interfaccia grafica?". Le interfacce grafiche sono meravigliose, perché ci permettono di compiere delle operazioni in un'ambiente visuale. Tuttavia con una GUI non possiamo attingere a tutte le funzionalità del sistema, perché siamo sempre vincolati alle capacità previste da chi ha progettato la GUI. Con la shell invece non abbiamo limiti e possiamo compiere operazioni complesse in breve tempo e automatizzarle attraverso la scrittura di file di script. Acquisite familiarità con la shell del vostro sistema operativo e rimarrete sorpresi da quanto può rendervi più produttivi.

### Power editing

Lo strumento per eccellenza di ogni sviluppatore è l'editor. Utilizziamo gli editor quotidianamente per: il codice, la documentazione, la configurazione di sistemi e così via. Per questo motivo è molto importante che scegliamo con cura l'editor da utilizzare.

### Caratteristiche degli editor

Ecco alcune capacità di base che qualsiasi editor decente dovrebbe avere:

* **Configurabile:** tutti gli aspetti dell'editor devono essere configurabili secondo le nostre preferenze: tipi di caratteri, colori, attribuzioni di tasti rapidi e così via.
* **Estendibile:** un editor non deve diventare obsoleto solo perché arriva un nuovo linguaggio di programmazione. Deve essere possibile insegnargli le sfumature di qualsiasi nuovo linguaggio o di qualsiasi nuovo formato testuale \(XML, HTML e così via\).
* **Programmabile:** deve essere possibile programmare l'editor per fargli svolgere attività complesse.

Molti editor hanno caratteristiche specifiche per particolari linguaggi:

* Evidenziazione della sintassi
* Autocompletamento
* Rientri automatici
* Modelli di codice e/o di documenti
* Funzioni simili a quelli di un IDE \(compilazione, debug e così via\)

### Produttività

L'utilizzo di un editor che rispecchia le caratteristiche sopra descritte vi renderà subito più produttivi: invece di utilizzare il mouse per navigare tra le righe di codice o aprire file e cartelle, avrete la possibilità di eseguire tutte queste operazioni senza dover staccare le mani dalla tastiera grazie all'utilizzo dei tasti rapidi. Un'altra caratteristica utile è il rietro automatico: anziché dover rientrare manualmente \(con la barra spaziatrice o con la tabulazione\), l'editor rientra il testo automaticamente al momento opportuno \(es.: dopo l'apertura di una parentesi graffa\).

### Quali editor sono disponibili?

L'utilizzo dell'editor è una scelta molto personale, tuttavia ecco un elenco degli editor che a mio avviso potrebbero fare a caso vostro:

* [Visual Studio Code](https://code.visualstudio.com/)
* [Sublime Text](https://www.sublimetext.com/)
* [Notepad++](https://notepad-plus-plus.org/)
* [Coda](https://panic.com/coda/)
* [Emacs](https://www.gnu.org/software/emacs/)
* [Vi](http://ex-vi.sourceforge.net/)

### Controllo del codice sorgente

Una delle funzionalità più importanti in ambito di sviluppo, ma non solo, è quella che ci consente di ripristinare lo stato precedente di un file o di un intero progetto ad un minuto, ora, giorno o settimane fa. I sistemi di controllo del codice sorgente ci consentono di tenere traccia delle modifiche effettuate ai file e di ripristinare una precedente versione in maniera facile e veloce. Un sistema di controllo del codice sorgente \(SCCS, _source code control system_\) fa molto più di questo: esso ci permette di tenere traccia anche di chi ha modificato i file e quando l'ha fatto. Ci consentono anche di comparare le versioni differenti di uno stesso file, in modo tale da visualizzare le differenze tra le due versioni. Vengono usati spesso gli SCCS anche per gestire le diramazioni nell'albero di sviluppo. Per esempio, una volta rilasciato del software normalmente vorrete continuare a svilupparlo per la release successiva, ma al contempo dovrete risolvere i bugs della release corrente. Per farlo potete creare un ramo per la risoluzione di un determinato bug \(es.: _fix/login-with-facebook_\) e un'altro ramo per sviluppare la funzionalità da includere nella release successiva \(es.: _feat/show-order-status_\). Sistemato il bug, poi potete mergiarlo sia sul ramo principale della release corrente \(_master\)_ e sia sul ramo contenente le nuove funzionalità per la release successiva. Infine, potete utilizzare un sistema di controllo del codice sorgente anche per la collaborazione tra due o più sviluppatori: per farlo basta installare e configurare il tool per il controllo del codice sorgente all'interno di un server remoto, il quale farà da tramite tra le modifiche apportate nel vostro computer e quelle effettuate da parte dei vostri colleghi.

### Controllo del codice sorgente e build

Un altro beneficio nell'utilizzo dei SCCS è quello di avere build del progetto **automatiche** e **ripetibili**. Il meccanismo di build del progetto può estrarre l'ultimo sorgente dal repository in modo automatico ed eseguire i test automatici di regressione per essere sicuri che ciò che è stato codificato non abbia guastato nulla. La build è ripetibile perché potete sempre ricostruire il sorgente nello stato in cui era in una data ben precisa.

### Debug

Una delle attività principali che uno sviluppatore svolge, e forse la meno piacevole, è la risoluzione dei bug. I difetti nel software si manifestono in molti modi: da requisiti non compresi a errori di codifica. Nessuno scrive codice perfetto, perciò è un dato di fatto che il debug richieda una parte cospicua della giornata.

### Psicologia del debug

Il debug è solo _risoluzione di problemi, problem solving_, perciò affrontatelo come tale. Anche se l'errore non lo avete commesso voi, non sprecate energie nel trovare il colpevole, ma concentratevi a risolvere il problema.

### Una mentalità da debug

Prima di iniziare il debug è importante adottare la mentalità giusta. La prima regola del debug è: **Niente panico!** E' facile farsi prendere dal panico quando la scadenza incombe o c'è il cliente che vi mette pressione, ma è molto importante che fate un passo indietro e pensate: "Qual è la causa di questo errore?". Evitate di perdere tempo giustificandovi dicendo: "Come è potuto accadere?" o "E' impossibile che non funzioni". Inoltre quando trovate un bug cercate di capire l'origine del problema, non limitatevi a mettere una semplice pezza a quella specifica occorrenza.

### Da dove iniziare

Prima di iniziare a scovare manualmente l'errore assicuratevi di aver azionato tutti i sistemi di warning del vostro compilatore. Inutile cercare l'errore manualmente quando può dircelo in maniera automatica il nostro compilatore. Quando cercate di risolvere un problema dovete raccogliere tutti i dati necessari per capire e riprodurre l'errore. Se il problema è stato segnalato da terzi fategli delle domande o chiedetegli di mostrarvi la procedura che ha seguito e che lo ha portato ad ottenere quell'errore.

### Visualizzate i vostri dati

Il modo più semplice per capire che cosa fa un programma è quello di visualizzare, passo dopo passo, i dati su cui agisce e l'output che viene generato. Potete visualizzare queste informazioni attraverso un **debugger**, il quale vi consente di visualizzare i dati e tutte le relazioni esistenti.

### Tracing

I debugger in genere si concentrano sullo stato del programma al momento. A volte è necessario osservare lo stato del programma nel tempo. I **trace statements** sono dei messaggi diagnostici che fate comparire su schermo o inviate su file di log e che dicono cose come: "Sono arrivato qui" oppure "Il valore di x = 2". Il tracing è preziosissimo soprattutto nei sistemi in cui il tempo è un fattore importante: processi concorrenti, applicazioni basate su eventi.

### Fare la papera di gomma

Un'altra tecnica utile per trovare la causa di un problema è quella di spiegare il problema a qualcun altro \(o ad una paperella di gomma, qualora non potete disturbare i vostri colleghi\). Il semplice fatto di spiegare, passo per passo, che cosa dovrebbe fare il codice, spesso spinge il problema a saltar fuori. Nello spiegare il problema a un'altra persona dovete dire esplicitamente cose che potreste dare per scontato quando esaminate il codice da soli.

### Processo di eliminazione

Nella maggior parte dei progetti il codice che dovete controllare può essere una miscela di codice scritto da voi, da altri membri del vostro team e da produttori esterni di librerie. E' possibile che l'errore stia nella libreria di terze parti, ma non deve essere la prima cosa a cui pensare, perché è molto più probabile che l'errore sta nel vostro codice applicativo. Se avete cambiato solo una cosa e il sistema ha smesso di funzionare, quell'unica cosa è probabilmente la causa del problema. A volte la cosa che è cambiata è fuori dal vostro controllo, magari avete aggiornato una libreria di terzi oppure è cambiata la risposta restituita dalle APIs di un servizio esterno che interrogate. Qualunque sia il motivo dovete apportare delle modifiche al vostro codice affinché si adatti ai nuovi aggiornamenti. Tenete d'occhio le vostre scadenze quando prendete in considerazione la possibilità di un aggiornamento: magari è meglio aspettare dopo il prossimo rilascio del vostro software.

### L'elemento sorpresa

Quando vi imbattete in un errore sorprendente non perdete tempo giustificandovi con frasi del tipo "Questo pezzo di codice ha sempre funzionato". Se un errore non si è mai presentato per anni non vuol dire che quel codice era privo di bug, ma che semplicemente non si sono verificate le condizioni tali da far emergere quell'errore. Sistemate l'errore, riflettete se dovete migliorare e modificare i vostri unit test o se dovete migliorare la verifica dei parametri in quella routine. Se è stato necessario molto tempo per sistemare l'errore chiedetevi il perché: c'è qualcosa che potreste fare per rendere più facile la risoluzione di questo errore la prossima volta?

### Generatori di codice

Un generatore di codice, come suggerisce il nome, non è altro che del "codice che scrive altro codice". Esso è molto utile quando dobbiamo ottenere la stessa funzionalità in contesti diversi. Esistono due tipi di generatori di codice:

* **Generatori di codice passivi:** vengono eseguiti una volta per produrre un risultato. Da quel momento in poi il risultato è autonomo - divorzia dal codice generatore.
* **Generatori di codice attivi:** vengono usati ogni volta che sono richiesti i loro risultati. I risultati possono essere sempre riprodotti da zero eseguendo nuovamente il generatore.

### Generatori di codice passivi

Vengono utilizzati per far risparmiare tempo nella scrittura di codice. Una volta prodotto, il risultato è un file sorgente a pieno diritto, esso verrà modificato e compilato come un qualsiasi altro file.

I generatori di codice passivi hanno molti usi:

* **Creare nuovi file sorgente:** un generatore può produrre un file sorgente con all'interno una struttura standard. Questo è quello che fanno molti IDE quando, per esempio, creiamo una nuova classe e automaticamente viene aggiunto il nome del package, un blocco di commento contenente le informazioni di copyright e il metodo costruttore.
* **Eseguire conversioni una tantum fra linguaggi di programmazione:** un generatore può essere utilizzato per convertire un file di codice sorgente da un linguaggio di programmazione ad un altro.

### Generatori di codice attivi

Mentre quelli passivi sono semplicemente una comodità, i generatori di codice attivi sono una necessità se si vuole seguire il principio DRY. Per esempio, immaginate che dovete creare per ogni entità della vostra applicazione una corrispondente tabella nel vostro database. Nel momento in cui avete la necessità di aggiungere un campo nella vostra entità vi dovete ricordare di aggiungere anche la relativa colonna sulla tabella del database. Stesso discorso quando dovete eliminare un campo dall'entità. Una buona alternativa è quella di creare l'entità con i relativi campi e successivamente generare un file di migrazione, il quale conterrà le istruzioni per creare la corrispondente tabella nel database. Questo sistema è molto utilizzato dagli ORM \(_Object-relational mapping_\) e si basa proprio sul concetto di codice autogenerato.

### I generatori di codice non devono essere per forza complessi

Un generatore di codice non deve essere per forza complesso. Normalmente la parte più complessa è il parser, cioè l'analizzatore sintattico del file di input. Mantenete semplice il formato dell'input e il generatore di codice diventa semplice da sviluppare.

