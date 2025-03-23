<h1 style="color: blue;">LINGUAGGI E MODELLI COMPUTAZIONALI</h1>

---

# **Indice**

- [INTRODUZIONE](#Introduzione)
- [TEORIA DELLA COMPUTABILITÀ](#teoria)
- [LINGUAGGI E GRAMMATICHE](#linguaggi)
- [CLASSIFICAZIONE DELLE GRAMMATICHE DI CHOMSKY](#chomsky)

---
<h1 id=Introduzione style="color: blue;">Introduzione</h1>


## 📚 Cos'è la Computazione?

La **computazione** è il processo di esecuzione di una sequenza di operazioni definite per risolvere un problema o calcolare un risultato. In termini più formali, si riferisce a **qualsiasi trasformazione di informazioni** secondo regole ben precise, eseguita da un sistema (umano, meccanico o digitale). La computazione è alla base dell'informatica, della matematica computazionale e delle scienze cognitive.

> **Esempio**: Calcolare la somma di due numeri, eseguire una ricerca su internet, o simulare un sistema fisico sono tutti atti di computazione.

---

## 🧠 Modelli di Computazione

Un **modello di computazione** è una rappresentazione astratta di un sistema che esegue calcoli. Serve a formalizzare cosa significa "calcolare" e quali problemi una macchina è in grado di risolvere. Ecco i principali:

### 1. 🧾 **Macchina di Turing**
- Introdotta da Alan Turing nel 1936.
- Modello teorico con un nastro infinito e una testina che legge/scrive simboli.
- È il modello di riferimento per la **computabilità**.
- Rappresenta qualsiasi algoritmo eseguibile da un computer classico.

### 2. 🧮 **Lambda Calcolo**
- Introdotto da Alonzo Church.
- Basato su funzioni e sostituzioni.
- Modello fondamentale per la **programmazione funzionale**.
- Equivalente alla Macchina di Turing in termini di potenza computazionale.

### 3. 🧰 **Macchina RAM (Random Access Machine)**
- Modello astratto di un computer reale con registri e accesso diretto alla memoria.
- Utile per analizzare la **complessità computazionale** degli algoritmi.

### 4. 🔁 **Automati Finiti**
- Modelli semplici per sistemi con numero finito di stati.
- Utilizzati per descrivere linguaggi regolari e sistemi reattivi.
- Fondamentali nella **teoria dei linguaggi formali**.

### 5. 🧊 **Modelli a Stati Quantistici (Quantum Computing)**
- Basati sui principi della meccanica quantistica (qubit, sovrapposizione, entanglement).
- Possono risolvere alcuni problemi più velocemente dei modelli classici.
- Esempio: **Algoritmo di Shor** per la fattorizzazione di numeri primi.

---

## 🧩 Confronto tra i Modelli

| Modello              | Potenza Computazionale | Dominio d'Uso                  |
|----------------------|------------------------|--------------------------------|
| Macchina di Turing   | Universale             | Fondamenti teorici             |
| Lambda Calcolo       | Universale             | Programmazione funzionale      |
| Macchina RAM         | Universale             | Analisi di algoritmi           |
| Automati Finiti      | Limitata               | Linguaggi regolari, parsing    |
| Modelli Quantistici  | Potenzialmente superiori | Calcolo quantistico           |

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

$$
f_P: X \to Y
$$

Con questo formalismo definito, si può traslare il problema della ricerca dei problemi risolubili su quello delle funzioni computabili. Riprendendo la tesi di Church-Turing:

### FUNZIONE COMPUTABILE

Una funzione f: A → B è computabile se esiste una MdT che:
- data sul nastro una rappresentazione di x ∈ A  
- dopo un numero finito di passi  
- produce sul nastro una rappresentazione di f(x) ∈ B

Date le definizioni, viene spontaneo chiedersi se tutte le funzioni siano computabili o se esistano invece funzioni **definibili ma non computabili**. Per far ciò occorre confrontare i due insiemi.

Si fa presto, dato che l’insieme delle funzioni dai naturali ai naturali:

$$
F = \{ f: \mathbb{N} \to \mathbb{N} \}
$$

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

Una **grammatica formale** è un modello matematico utilizzato per descrivere la **struttura sintattica** di un linguaggio, ovvero l'insieme delle regole che stabiliscono quali sequenze di simboli costituiscono frasi valide in quel linguaggio.

Una grammatica viene rappresentata tramite una **quadrupla**:

$$
G = (V_T, V_N, P, S)
$$

dove:

- **$V_T$ – Insieme dei simboli terminali**  
  È un insieme **finito** di simboli che compaiono **nelle frasi finali** generate dalla grammatica. Sono i simboli "concreti" del linguaggio, come lettere (`a`, `b`), numeri (`0`, `1`), operatori (`+`, `*`), parole chiave (`if`, `while`), ecc.

- **$V_N$ – Insieme dei simboli non terminali**  
  Sono simboli astratti, chiamati anche *metasimboli*, utilizzati come **variabili sintattiche** durante la generazione. Guidano la costruzione delle frasi e **non appaiono** nelle frasi finali. Esempi: `S`, `Expr`, `Term`, `Stmt`.

- **$P$ – Insieme delle produzioni**  
  È un insieme **finito di regole di riscrittura**, chiamate anche **produzioni**, che specificano come un simbolo non terminale può essere sostituito da una combinazione di terminali e/o altri non terminali.

  Ogni produzione ha la forma generale:

$$
A \rightarrow \gamma
$$

dove $A \in V_N$ e $\gamma \in (V_T \cup V_N)^*$

  Questo significa che un simbolo non terminale $A$ può essere riscritto con una stringa $\gamma$ composta da simboli terminali e/o non terminali.

- **$S$ – Simbolo iniziale**  
  È un **simbolo non terminale speciale**, da cui inizia il processo di generazione. Tutte le frasi del linguaggio devono essere **derivabili** a partire da $S$.

---

#### **Esempi di Produzioni**

Ecco alcune produzioni tipiche, espresse in notazione LaTeX:

$$
S \rightarrow aSb \mid ab
$$

$$
\text{Expr} \rightarrow \text{Expr} + \text{Term} \mid \text{Term}
$$

$$
\text{Term} \rightarrow \text{number}
$$

---

#### **Cosa implicano praticamente?**

Le grammatiche formali servono a:

- **Generare le frasi** valide di un linguaggio, partendo da $S$ e applicando iterativamente le produzioni di $P$.
- **Verificare la correttezza sintattica** di una stringa: ovvero decidere se appartiene o meno al linguaggio.
- **Costruire strumenti come compilatori, parser e interpreti**, fondamentali in ingegneria del software.
- **Studiare proprietà teoriche dei linguaggi**, come ambiguità, decidibilità o potere computazionale.

---

#### **Esempio pratico: linguaggio delle parentesi bilanciate**

Definiamo una grammatica semplice per generare stringhe con parentesi bilanciate:

- $V_T = \{ (, ), a \}$
- $V_N = \{ S \}$
- $S$ è il simbolo iniziale
- Produzioni:

$$
S \rightarrow (S) \mid SS \mid a
$$

Frasi generate da questa grammatica:
- `a`
- `(a)`
- `((a))`
- `(a)(a)`
- `((a)(a))`

Questa grammatica formalizza un linguaggio in cui **ogni apertura ha una chiusura**, come accade in **espressioni matematiche, codice sorgente, alberi sintattici**, ecc.


Le grammatiche formali sono quindi **strumenti essenziali** in ingegneria informatica per **modellare linguaggi**, **costruire interpreti** e **analizzare il comportamento dei programmi**.



- **DERIVAZIONE**  
  Date due forme di frase α, β si dice che **β deriva direttamente da α** se è vero che:

$$
\alpha = \eta A \delta, \quad \beta = \eta \gamma \delta
$$

ed esiste una produzione A → γ. In caso non esista una produzione ma una **catena di produzioni**, si parla di derivazione **non diretta**.

### LINGUAGGIO GENERATO DALLA GRAMMATICA

Data una grammatica G, si dice **linguaggio LG generato dalla grammatica G** l’insieme delle frasi derivabili dal simbolo iniziale della grammatica applicando le sue produzioni:

$$
L_G = \{ s \in V_T^* \mid S \Rightarrow s \}
$$

Quando due grammatiche producono lo stesso linguaggio, si dice che sono **equivalenti**.  
Stabilire se due grammatiche sono equivalenti è un **problema indecidibile**.  
Inoltre, **grammatiche diverse ma equivalenti** potrebbero necessitare di **riconoscitori diversi**.

---

<h1 id=chomsky style="color: blue;">Classificazione delle grammatiche di Chomsky</h1>


La classificazione delle grammatiche di Chomsky suddivide le grammatiche formali in **quattro categorie principali**, in base alla loro **potenza espressiva** e alla **capacità computazionale necessaria per riconoscerle**.

## **Tipologie di Grammatiche**

| **Grammatica** | **Automa Riconoscitore** | **Descrizione** |
|--------------|----------------------|----------------|
| **Tipo 0** – Grammatiche senza restrizioni | **Macchina di Turing** | La forma più generale di grammatica. Le produzioni possono essere di qualsiasi tipo e il linguaggio generato è **riconoscibile** da una **Macchina di Turing**. |
| **Tipo 1** – Grammatiche sensibili al contesto | **Macchina di Turing con spazio limitato** | Le produzioni sono della forma: <br> αAβ → αγβ, con γ ≥ A. <br> Ogni regola deve **preservare la lunghezza** della stringa o **aumentarla**. |
| **Tipo 2** – Grammatiche libere dal contesto | **Automa a pila (PDA)** | Le produzioni sono della forma: <br> A → γ, con A **non terminale** e γ **qualsiasi stringa** di terminali e non terminali. |
| **Tipo 3** – Grammatiche regolari | **Automa a stati finiti (ASF)** | Le produzioni sono della forma: <br> A → aB oppure A → a (con A e B non terminali e a terminale). <br> Possono essere **regolari destrose** o **sinistrose**. |

---
### **Grammatiche Tipo 0 – Grammatiche Senza Restrizioni**
Le grammatiche **tipo 0** sono le più generali nella gerarchia di Chomsky. Possono generare **qualsiasi linguaggio formalmente descrivibile** e sono equivalenti ai linguaggi **riconoscibili** da una **Macchina di Turing**.

#### **Definizione Formale**
Una grammatica **senza restrizioni** è definita dalla quadrupla:

$$
G = (V_T, V_N, P, S)
$$

dove le produzioni \( P \) sono della forma:

$$
\alpha \to \beta, \quad \text{con } \alpha, \beta \in (V_T \cup V_N)^*, \alpha \neq \epsilon
$$

cioè, qualsiasi stringa di simboli terminali e non terminali può essere trasformata in un’altra stringa, a patto che la parte sinistra della produzione non sia vuota.

#### **Esempio di Grammatica Tipo 0**
Sia la grammatica:

$$
S \to aSb \quad |\quad ab
$$

Questa grammatica genera il linguaggio:

$$
L = \{ a^n b^n \mid n \geq 1 \}
$$

che non può essere riconosciuto da un **automa a stati finiti** o da un **automa a pila**, ma solo da una **Macchina di Turing**.

#### **Applicazioni in Ingegneria**
Le grammatiche di Tipo 0 vengono studiate in informatica teorica e ingegneria perché corrispondono al **potere computazionale massimo**. Qualsiasi problema risolvibile da un computer può essere modellato con una grammatica Tipo 0, rendendole fondamentali per lo **studio della decidibilità e della complessità computazionale**.

---

### **Grammatiche Tipo 1 – Grammatiche Sensibili al Contesto**
Le grammatiche **sensibili al contesto** sono più restrittive delle Tipo 0 e generano i **linguaggi sensibili al contesto**, riconosciuti da una **Macchina di Turing con spazio limitato**.

#### **Definizione Formale**
Le produzioni di una grammatica di Tipo 1 devono rispettare la forma:

$$
\alpha A \beta \to \alpha \gamma \beta, \quad \text{con } |\gamma| \geq |A|
$$

dove $A$ è un simbolo non terminale e $\alpha, \beta, \gamma$ sono stringhe di terminali e non terminali.


#### **Esempio di Grammatica Tipo 1**
Esempio di grammatica sensibile al contesto che genera il linguaggio $L = \{ a^n b^n c^n \mid n \geq 1 \}$:

1. $$\( S \to aSBC \mid aBC \)$$
2. $$\( CB \to DB \), \( DB \to DC \), \( DC \to BC \)$$
3. $$\( aB \to ab \), \( bB \to bb \), \( bC \to bc \), \( cC \to cc \)$$

Questa grammatica garantisce che le quantità di ($a, b, c$) siano uguali, il che non è possibile con grammatiche più semplici.

#### **Applicazioni in Ingegneria**
I linguaggi sensibili al contesto sono importanti per descrivere **linguaggi naturali complessi** e **restrizioni grammaticali avanzate**. In ingegneria, vengono studiati in teoria dei compilatori per analizzare costrutti complessi nei linguaggi di programmazione.

---

### **Grammatiche Tipo 2 – Grammatiche Libere dal Contesto**
Le grammatiche **libere dal contesto** sono più semplici e potenti rispetto a quelle regolari. Generano i **linguaggi liberi dal contesto**, che possono essere riconosciuti da un **Automa a Pila (PDA)**.

#### **Definizione Formale**
Le produzioni devono essere della forma:

$$
A \to \gamma, \quad \text{con } A \in V_N, \gamma \in (V_T \cup V_N)^*
$$

Un singolo simbolo non terminale viene riscritto indipendentemente dal contesto in cui si trova.

#### **Esempio di Grammatica Tipo 2**
Esempio per il linguaggio delle **parentesi bilanciate**:

1. $$\( S \to SS \)$$
2. $$\( S \to (S) \)$$
3. $$\( S \to \epsilon \)$$

Questa grammatica genera stringhe come **"()", "(())", "()()"**, ecc.

#### **Applicazioni in Ingegneria**
Queste grammatiche sono fondamentali per la **teoria dei compilatori**, poiché molti linguaggi di programmazione sono **linguaggi liberi dal contesto**. Gli **analizzatori sintattici (parser)** si basano su grammatiche di Tipo 2.

---

### **Grammatiche Tipo 3 – Grammatiche Regolari**
Le grammatiche **regolari** sono le più restrittive e semplici. Generano i **linguaggi regolari**, riconoscibili da un **Automa a Stati Finiti (ASF)**.

#### **Definizione Formale**
Le produzioni devono essere nella forma:

$$
A \to aB \quad \text{(regolare destrorsa)} \quad \text{oppure} \quad A \to Ba \quad \text{(regolare sinistrorsa)}
$$

oppure semplicemente:

$$
A \to a
$$

#### **Esempio di Grammatica Tipo 3**
Per il linguaggio delle stringhe che terminano in **01**:

1. $$\( S \to 0S \mid 1A \)$$
2. $$\( A \to 0B \)$$
3. $$\( B \to 1 \)$$

Genera stringhe come **"01", "101", "00001"**, ecc.

#### **Applicazioni in Ingegneria**
Le grammatiche regolari sono utilizzate nei **sistemi di riconoscimento di pattern**, nei **linguaggi di markup**, nei **filtri di ricerca** e nei **sistemi di espressioni regolari**. Sono alla base della progettazione di **linguaggi di scripting** e di **scanner lessicali nei compilatori**.

---

### **Deduzioni sulle grammatiche di Chomsky**
La classificazione delle grammatiche di Chomsky è cruciale per comprendere **quali linguaggi possono essere processati da diversi modelli computazionali**. Ogni livello ha la sua importanza in ingegneria e informatica:

- **Tipo 3**: Espressioni regolari, scanner lessicali.
- **Tipo 2**: Parsing dei linguaggi di programmazione.
- **Tipo 1**: Linguaggi più complessi, compilatori avanzati.
- **Tipo 0**: Problemi computazionali generali, limiti della computabilità.

Questa gerarchia aiuta a capire **quali linguaggi possono essere riconosciuti in base alla loro complessità** e alla potenza degli automi necessari per riconoscerli.


