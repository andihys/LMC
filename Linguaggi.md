# LINGUAGGI E GRAMMATICHE
Per poter ottenere una macchina di Turing universale e necessario dare definizione formale di linguaggio, per comprendere l’inadeguatezza al riconoscimento di definizioni non formali ne citiamo una come segue

Un linguaggio è un insieme di parole e di metodi di combinazione delle parole usate e comprese da una comunità di persone

E necessario dunque esprimere sintassi (notazioni BNF EBNF) e semantica del linguaggio secondo notazioni formali (funzioni matematiche/formule logiche)

Da questa suddivisione si deduce quindi che una macchina di Turing universale deve adempiere a queste due operazioni

### STRUTTURA DI UN LINGUAGGIO
Elementi che compongono un linguaggio

- *ALFABETO*: un alfabeto A è un insieme finito e non vuoto di simboli atomici. Esempio: A={a,b}
- *STRINGA*: un stringa è una sequenza di simboli, ossia un elemento del prodotto cartesiano A^n
- *LINGUAGGIO*: un linguaggio L definito su A è un insieme di stringhe su A
- *CHIUSURA DI UN ALFABETO*: l’insime infinito di stringhe composte per mezzo della combinazione di a (tutti i possibili prodotti cartesiani) A∗ = A0 ∪ A1 ∪ A2 ...
- *CHIUSURA POSITIVA DI UN ALFABETO*: la chiusura escludendo la stringa vuota A+ = A∗ − {ϵ}
  
### GRAMMATICHE FORMALI
la grammatica e una notazione formale con cui definire la sintassi di un linguaggio: espressa dalla quadrupla <VT,VN,P,S> dove:

- VT insieme finito di simboli terminali
- VN insieme finito di simboli non terminali (metasimboli)
- P insieme finito delle produzioni
- S simbolo non terminale speciale chiamato scopo della grammatica
Una stringa composta da simboli e metasimboli si dice forma di frase.

- DERIVAZIONE
date due forme di frase α,β si dice che β deriva direttamente da α se e vero che

                    a=ηAδ, β=ηγδ

ed esiste una produzione A→γ, in caso non esista una produzione ma una catena di produzioni si parla di derivazione (non diretta)

### LINGUAGGIO GENERATO DALLA GRAMMATICA
data una grammatica G si dice linguaggio LG generato dalla grammatica G l’insieme delle frasi derivabili dal simbolo iniziale della grammatica applicando le sue produzioni

                    LG = { s∈VT∗ : S⇒s }
                    
quando due grammatiche producono lo stesso linguaggio si dice che sono equivalenti, stabilire se due grammatiche sono equivalenti e un problema indecidibile, inoltre grammatiche diverse ma equivalenti potrebbero necessitare di riconoscitori diversi
