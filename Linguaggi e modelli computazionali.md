<h1 style="color: blue;">LINGUAGGI E MODELLI COMPUTAZIONALI</h1>

---

# **Indice**

- [TEORIA DELLA COMPUTABILITÀ](#teoria)
- [LINGUAGGI E GRAMMATICHE](#linguaggi)

---

<h1 id=teoria style="color: blue;">Teoria della computabilità</h1>

**TESI DI CHURCH-TURING:**  
Se un problema è umanamente calcolabile, allora esisterà una macchina di Turing in grado di risolverlo (cioè di calcolarlo). Secondo questa tesi, non esiste attualmente una macchina che può risolvere una più vasta area di problemi.  
Da questo si deduce che se la MdT non può risolvere un dato problema, quel problema è irresolubile.  
Ma cosa succede se una MdT non è in grado di risolvere un problema? Essa stessa si blocca in un loop e non produce output. Di conseguenza, si può dare una definizione di **PROBLEMA RISOLUBILE** come segue:

### PROBLEMA RISOLUBILE

È un problema la cui soluzione può essere espressa da una MdT (o formalismo equivalente).  
Ma la MdT computa funzioni, non problemi. Occorre quindi definire formalmente il concetto di **funzione caratteristica di un problema** per colmare il divario.

Dato un problema P e detti:
- l’insieme X dei suoi dati di ingresso  
- l’insieme Y delle risposte corrette  

si dice funzione caratteristica del problema P:
      fP: X → Y

Con questo formalismo definito, si può traslare il problema della ricerca dei problemi risolubili su quello delle funzioni computabili. Riprendendo la tesi di Church-Turing:

### FUNZIONE COMPUTABILE

Una funzione f: A → B è computabile se esiste una MdT che:
- data sul nastro una rappresentazione di x ∈ A  
- dopo un numero finito di passi  
- produce sul nastro una rappresentazione di f(x) ∈ B

Date le definizioni, viene spontaneo chiedersi se tutte le funzioni siano computabili o se esistano invece funzioni **definibili ma non computabili**. Per far ciò occorre confrontare i due insiemi.

Si fa presto, dato che l’insieme delle funzioni dai naturali ai naturali:

      F = {f: N → N}

non è numerabile, a differenza di quello delle funzioni computabili, dato che la cardinalità dei simboli di ingresso, di uscita e di stati di una MdT è finita.

Di conseguenza, **la gran parte delle funzioni definibili non è computabile**. Tuttavia, questo non risulta essere un problema, dato che le funzioni interessanti per una macchina che deve riconoscere un linguaggio sono quelle definite su un insieme finito di simboli. Tuttavia, **neanche questo sottoinsieme è “fortunato”**.

### PROBLEMA DELL’HALT DELLA MACCHINA DI TURING

Stabilire se una data macchina di Turing T, con un generico ingresso X, si ferma oppure no.  
Tale problema, perfettamente definibile, è tuttavia **non computabile**.

Ma allora, **come deve essere un linguaggio affinché la MdT possa computarlo?**

Poiché un linguaggio è un insieme di frasi, ci interessa indagare in generale il problema della generabilità **vs.** decidibilità di un insieme.

### INSIEME NUMERABILE

Insieme per cui esiste una funzione f: N → I (mappa l’insieme dei naturali in elementi dell’insieme).  
Tuttavia non è sufficiente: la funzione deve essere **computabile**.

### INSIEME RICORSIVAMENTE NUMERABILE (SEMI-DECIDIBILE)

Un insieme si dice ricorsivamente numerabile se f: N → I può essere **computata da una macchina di Turing**.

In questo caso, l’automa esecutore è in grado di rispondere **affermativamente** quando una determinata frase appartiene al linguaggio, ma **non è in grado di stabilire** se una frase non vi appartiene (esempio dei numeri pari e dispari).

### INSIEME DECIDIBILE

Un insieme S è detto decidibile se **sia S che il complemento N − S sono semidecidibili**.

Questo, per un automa, significa essere in grado di elencare **sia gli elementi che fanno parte** sia quelli che **non fanno parte** di un determinato linguaggio.

E proprio qui sta la chiave del problema:  
I linguaggi di programmazione sono costruiti a partire da un **alfabeto finito**, ma sono caratterizzati dall’insieme (infinito) delle **frasi lecite**. Non basta che tale insieme possa essere generato: è indispensabile **poter decidere** se una frase è giusta o sbagliata **senza entrare in ciclo infinito**.

- In questo modo un **compilatore** è in grado di arrestarsi e segnalare errore se una frase non appartiene al linguaggio.

---

<h1 id=linguaggi style="color: blue;">Linguaggi e grammatiche</h1>

Per poter ottenere una **macchina di Turing universale**, è necessario dare definizione formale di linguaggio.  
Per comprendere l’inadeguatezza al riconoscimento di definizioni non formali, ne citiamo una come segue:

> "Un linguaggio è un insieme di parole e di metodi di combinazione delle parole usate e comprese da una comunità di persone."

È quindi necessario esprimere **sintassi** (notazioni BNF, EBNF) e **semantica** del linguaggio secondo notazioni formali (funzioni matematiche / formule logiche).  
Da questa suddivisione si deduce che una **macchina di Turing universale** deve adempiere a queste due operazioni.

### STRUTTURA DI UN LINGUAGGIO

Elementi che compongono un linguaggio:

- **ALFABETO**: un alfabeto A è un insieme finito e non vuoto di simboli atomici.  
  Esempio: A = {a, b}
- **STRINGA**: una stringa è una sequenza di simboli, ossia un elemento del prodotto cartesiano Aⁿ
- **LINGUAGGIO**: un linguaggio L definito su A è un insieme di stringhe su A
- **CHIUSURA DI UN ALFABETO**: l’insieme infinito di stringhe composte per mezzo della combinazione di A (tutti i possibili prodotti cartesiani)  
  A* = A⁰ ∪ A¹ ∪ A² ...
- **CHIUSURA POSITIVA DI UN ALFABETO**: la chiusura escludendo la stringa vuota  
  A⁺ = A* − {ε}

### GRAMMATICHE FORMALI

La grammatica è una notazione formale con cui definire la sintassi di un linguaggio: espressa dalla quadrupla `<VT, VN, P, S>`, dove:

- **VT**: insieme finito di simboli terminali  
- **VN**: insieme finito di simboli non terminali (metasimboli)  
- **P**: insieme finito delle produzioni  
- **S**: simbolo non terminale speciale, chiamato **scopo della grammatica**  

Una stringa composta da simboli e metasimboli si dice **forma di frase**.

- **DERIVAZIONE**  
  Date due forme di frase α, β si dice che **β deriva direttamente da α** se è vero che:

      α = ηAδ, β = ηγδ

ed esiste una produzione A → γ. In caso non esista una produzione ma una **catena di produzioni**, si parla di derivazione **non diretta**.

### LINGUAGGIO GENERATO DALLA GRAMMATICA

Data una grammatica G, si dice **linguaggio LG generato dalla grammatica G** l’insieme delle frasi derivabili dal simbolo iniziale della grammatica applicando le sue produzioni:

      LG = { s ∈ VT* : S ⇒ s }

Quando due grammatiche producono lo stesso linguaggio, si dice che sono **equivalenti**.  
Stabilire se due grammatiche sono equivalenti è un **problema indecidibile**.  
Inoltre, **grammatiche diverse ma equivalenti** potrebbero necessitare di **riconoscitori diversi**.





