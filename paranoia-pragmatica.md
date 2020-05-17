# Paranoia pragmatica

> Nessuno scrive codice perfetto

Data questa realtà deprimente, in che modo possiamo difenderci dagli errori presenti nel nostro codice e in quello degli altri? In questo capitolo vedremo alcune tecniche che ci permettono di scrivere codice difensivo.

### Progettare per contratto

Una delle tecniche difensive più note, che ci garantisce la correttezza dei nostri programmi, è _la tecnica di progettazione per contratto_, _**Design by Contract**_ \(DBC\). Con questa tecnica è possibile specificare i diritti e le responsabilità che deve avere ciascun modulo. Ogni metodo in un sistema software _fa qualcosa,_ ma prima di iniziare a fare quel _qualcosa_ il metodo ha delle aspettative sui parametri d'ingresso e sullo stato generale, così come il chiamante ha delle aspettative sui valori restituiti dal metodo e sullo stato generale. Ebbene, questo accordo tra le due parti si può _**contrattualizzare**_, ed è qui che entra in gioco il DBC.

### DBC

Nel Design by Contract possiamo descrivere queste aspettative nel seguente modo:

* **Precondizioni:** le condizioni necessarie affinché il metodo venga chiamato. E' responsabilità del chiamante passare i dati corretti.
* **Postcondizioni:** le condizioni garantite dal metodo dopo che è stato chiamato.
* **Invarianti di classe:** la classe garantisce che queste condizioni siano sempre vere nella prospettiva di un chiamante. Durante l'esecuzione del metodo della classe l'invarianza può non valere, ma quando la routine esce e il controllo ritorna al chiamante le invarianti di classe devono essere vere.

Vediamo il contratto di un metodo che inserisce un valore in una lista ordinata che non deve contenere duplicati.

```text
/**
 * @invariant forall Node n in elements() |
 *     n.prev() != null
 *         implies
 *             n.value().compareTo(n.prev().value()) > 0
 *
 */
 public class dbc_list {
     /**
      * @pre contains(aNode) == false
      * @post contains(aNode) == true
      /*
      public void insertNode(final Node aNode) { ... }
 }
```

Qui diciamo che i nodi in questa lista devono essere sempre in ordine crescente. Quando si inserisce un nuovo nodo, esso non può essere già presente e garantiamo che dopo l'esecuzione lo si troverà nella lista. Il contratto tra un metodo e ogni eventuale chiamante si può quindi leggere in questo modo:

> Se tutte le precondizioni di un metodo sono soddisfatte dal chiamante, il metodo garantirà che tutte le postcondizioni e le invarianti di classe saranno vere quando completerà il proprio lavoro.

Se una delle parti non rispetta i termini del contratto verrà sollevata un'eccezione. Attenzione: le precondizioni non devono essere utilizzate per svolgere compiti come la validazione dei dati di input dell'utente. I contratti non servono a questo, ma bensì per assicurarci che quello che non dovrebbe mai succedere, non succederà sicuramente.

### Asserzioni

Se il vostro linguaggio non supporta DBC potete sempre utilizzare le **asserzioni**. Tuttavia, le asserzioni sono meno potenti ed efficaci rispetto DBC. Tanto per cominciare, non c'è supporto per la propagazione delle asserzioni lungo una gerarchia di eredità. Questo significa che: se si aggira un metodo della classe base in cui sono state definite delle asserzioni, quest'ultime non verranno chiamate nelle classi figlie. Per ogni `return` presente nel metodo dovete richiamare le asserzioni per la "postcondizione", questo non solo viola il principio DRY, ma rende il codice anche brutto da leggere.

### Supporto per i linguaggi

I linguaggi che incorporano DBC controllano automaticamente le precondizioni e le postcondizioni in fase di compilazione. Nei linguaggi invece che non supportano DBC, come C, C++ e Java, è possibile installare preprocessori che verificano i contratti scritti sotto forma di commenti.

### Altri usi delle invarianti

Le invarianti di classe possono essere sfruttate anche in altri modi:

#### Invarianti di ciclo

Vengono utilizzate per fissare le condizioni di limite di un ciclo. Esse vengono applicate ad ogni iterazione di un ciclo.

#### Invarianti semantiche

Vengono utilizzate per esprimere requisiti inviolabili. Ad esempio, pensate al requisito in cui una stessa transazione non deve essere applicata due volte al conto di un utente con carta di debito. Se per qualsiasi motivo viene applicata una seconda volta, la condizione del mio contratto deve bloccarla e lanciare un'eccezione. Fate però attenzione a non confondere requisiti che costituiscono leggi immutabili e inviolabili con quelli che sono semplicemente direttive che potrebbero cambiare nel corso del tempo. Per questo parliamo di invarianti semantiche: devono essere fondamentali per il significato di una cosa e non soggette alle modifiche delle regole di business.

### I programmi morti non mentono

Gli errori nei programmi capitano a tutti. Quando ciò accade non limitatevi a dire "questo è impossibile che sia successo" ignorando il problema. I programmatori pragmatici, invece, si dicono che, se c'è un errore deve essere successo qualcosa di molto grave. Uno dei vantaggi del rilevare gli errori il più presto possibile è il crash precoce e, in molti casi, mandare in crash il programma è la cosa migliore che si possa fare. L'alternativa sarebbe continuare con l'esecuzione, magari scrivendo dati corrotti in qualche tabella del database. Chiaramente, a volte non è appropriato limitarsi ad uscire immediatamente da un programma in esecuzione: ci sono magari delle risorse impegnate che così non vengono liberate oppure è necessario scrivere prima dei messaggi di log. Il principio di base però resta sempre lo stesso: se succede un errore imprevisto nel vostro programma terminatelo il più presto possibile. Un programma "morto" normalmente fa meno danni di un programma "azzoppato".

### Programmazione assertiva

Spesso quando codifichiamo ci facciamo ingannare da noi stessi con frasi del tipo: "Questa cosa non potrà mai succedere...". Questo ci porta spesso ad ignorare le cose con una grave conseguenza nel lungo termine. Ogni volta che vi ritrovate a pensare "ma è ovvio che non può succedere", aggiungete del codice per verificarlo. Il modo più semplice per farlo è usare le asserzioni.

```text
void writeString(char *string) {
    assert(string != NULL);
}
```

La condizione inserita all'interno di un'asserzione non deve avere effetti collaterali. Ricordate anche che le asserzioni possono essere disattivate in fase di compilazione, perciò non mettete mai in una assert del codice che debba essere eseguito.

### Lasciate attive le asserzioni

Molti pensano che le asserzioni aggiungono del carico inutile al codice. Una volta che il codice è stato testato e consegnato non servono più e possono essere disattivate, così il codice girà più veloce.

Tuttavia questi presupposti sono falsi. In primo luogo si presuppone che i test trovino tutti gli errori. In realtà è altamente improbabile che scriviate dei test che coprano il 100% del vostro codice. In secondo luogo spesso ci si dimentica che l'ambiente di produzione è soggetto a più sollecitazioni rispetto all'ambiente di sviluppo. La nostra linea di difesa sta nel controllare ogni possibile errore: le asserzioni ci aiutano ad identificare gli errori peggiori, quelli che sono sfuggiti al nostro controllo. Pertanto non disattivate le asserzioni negli ambienti di produzione: se avete problemi di prestazioni disattivate solo le asserzioni che danno davvero fastidio.

### Quando usare le eccezioni

Le eccezioni dovrebbero essere usate raramente nel flusso normale di un programma; le eccezioni devono essere utilizzate per eventi imprevisti. Per esempio: se il codice deve aprire un file in sola lettura, ma quel file non esiste, deve essere sollevata un'eccezione? La risposta è "dipende". Se il file _**dovrebbe**_ essere lì, allora è giusto sollevare un'eccezione, poiché è successo qualcosa di imprevisto, ma se invece non avete idea se il file deve esistere o meno, non sembra _eccezionale_ che non ci sia. Il codice seguente apre il file `/etc/passwd`, il quale deve essere presente in tutti i sistemi Unix. Se non c'è allora è giusto che venga sollevata un'eccezione:

```text
public void openPasswd() throws FileNotFoundException {
    // Questo può lanciare FileNotFoundException
    stream = new FileInputStream("/etc/passwd");
}
```

Se invece dovete aprire in lettura un file specificato dall'utente, il codice potrebbe non dover lanciare un'eccezione.

```text
public boolean openUserFile(String name) {
    throws FileNotFoundException {
        File f = new File(name);
        if (!f.exists()) {
            return false;
        }
        stream = new FileInputStream(f);
        return true;
    }
}
```

Consiglio di non abusare con l'utilizzo delle eccezioni, perché riducono la leggibilità del codice portando ad un trasferimento del controllo immediato e non locale - come una sorta di _goto_ a cascata.

### Gli Error Handlers sono un'alternativa

Gli error handlers sono delle classi speciali che vengono richiamate quando si verifica un errore. Potete registrare un error handler affinché gestisca una categoria specifica di errori.

### Come equilibrare le risorse

Spesso ci capita di gestire delle risorse quando codifichiamo: memoria, thread, file e così via. L'uso delle risorse segue un andamento lineare: si assegna la risorsa, la si usa, la si libera. Tuttavia, nonostante il flusso sembri semplice, si nascondono delle insidie quando lavoriamo con le risorse. Per esempio: immaginate che dovete aprire un file, leggere le informazioni di un cliente, modificare un campo e scrivere il risultato nel file:

```text
void readCustomer(const char *fName, Customer *cRec) {
    cFile = fopen(fName, "r+");
    fread(cRec, sizeof(*cRec), 1, cFile);
}

void writeCustomer(Customer *cRec) {
    rewind(cFile);
    fwrite(cRec, sizeof(*cRec), 1, cFile);
    fclose(cFile);
}

void updateCustomer(const char *fName, double newBalance) {
    Customer cRec;
    readCustomer(fName, &cRec);
    cRec.balance = newBalance;
    writeCustomer(&cRec);
}
```

A prima vista sembra che tutto sia corretto, tuttavia c'è un problema: i metodi _readCustomer e writeCustomer_ sono strettamente accoppiati, entrambi condividono la variabile _cFile_. Ora immaginate che cambia la specifica e venga chiesto che il file deve essere aggiornato solo se il nuovo valore del saldo non è negativo:

```text
void updateCustomer(const char *fName, double newBalance) {
    Customer cRec;
    readCustomer(fName, &cRec);
    if (newBalance >= 0.0) {
        cRec.balance = newBalance;
        writeCustomer(&cRec);
    }
}
```

Il codice sopra riportato presenta un errore: quando il saldo è negativo il file viene aperto e mai più chiuso. Se questo codice andasse in produzione dopo qualche ora il server collasserebbe a causa del numero eccessivo di file aperti. Il consiglio **"finite quello che cominciate"** __ci dice che: _il metodo che assegna una risorsa deve anche liberarla_.

```text
void readCustomer(FILE *cFile, Customer *cRec) {
    fread(cRec, sizeof(*cRec), 1, cFile);
}

void writeCustomer(FILE *cFile, Customer *cRec) {
    rewind(cFile);
    fwrite(cRec, sizeof(*cRec), 1, cFile);
}

void updateCustomer(const char *fName, double newBalance) {
    FILE *cFile;
    Customer cRec;
    cFile = fopen(fName, "r+");
    readCustomer(cFile, &cRec);
    if (newBalance >= 0.0) {
        cRec.balance = newBalance;
        writeCustomer(cFile, &cRec);   
    }
    fclose(cFile);
}
```

Ora tutta la responsabilità per il file sta nel metodo _updateCustomer_. Il metodo si occupa sia dall'apertura che della chiusura del file.

### Oggetti e risorse

L'equilibrio tra allocazioni e de-allocazioni ricorda il rapporto fra costruttore e distruttore di classe. Se programmate in un linguaggio a oggetti troverete forse utile incapsulare le risorse in classi. Ogni volta che avete bisogno di una risorsa istanziate un oggetto di quella classe, mentre, quando non serve più, il distruttore dell'oggetto si occuperà di liberare la risorsa.

### Risorse ed eccezioni

I linguaggi che ammettono le eccezioni possono complicare la liberazione delle risorse: se viene lanciata un'eccezione bisogna ricordarsi anche di liberare la risorsa. Fortunatamente molti linguaggi hanno introdotto l'uso della clausola _finally_ nei blocchi _try-catch_. Quando un blocco _try-catch_ contiene la clausola _finally_ si ha la certezza che il codice in quella clausola venga sempre eseguito, anche se viene lanciata un'eccezione:

```text
public void doSomething() throws IOException {
    File tmpFile = new File(tmpFilename);
    FileWriter tmp = new FileWriter(tmpFile);
    try {
        // do something...
    } finally {
        tmpFile.delete();
    }
}
```

