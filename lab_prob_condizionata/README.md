# La probabilità nei modelli di linguaggio

| **Tema**                 |                                                                    |
|:-------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------|
| **Scopo (DigComp)**      | Comprendere come dati e addestramento influenzano l'affidabilità dell'IA (**CS1.2.08**)                                                          |
| **Durata**               | 1 ora                                                                                                                                            |
| **Target**               | Studenti del triennio                                                                                                                            |
| **Setting della classe** | Dividere la classe in due gruppi, a un gruppo viene assegnato il modello A e ad un gruppo il modello B. Assegnare un computer ogni due studenti. |

## Come funziona un modello di linguaggio?

![studente](../assets/studente_IA.png)

Come studente avrai sicuramento utilizzato un modello di linguaggio per svolgere un tema, 
risolvere un compito
di matematica o preparare una presentazione in inglese.

**Ma come funziona un modello di linguaggio?** 

Proviamo a capire come funziona un semplice modello di 
linguaggio e, in particolare, ci poniamo due domande:
1. Come possiamo considerare il **contesto** di una frase per prevere la parola successiva?
2. Come possiamo continuare a prevere le **parole successive**?

## L'importanza del contesto
I *language model* LM sono modelli 
che predicono la parola successiva data una sequenza di parole. Devono quindi partire da una serie di 
parole per capire qual è la parola **più probabile** in quel contesto.

### La probabilità di una parola
Immaginiamo di avera a disposizione un gran numero di testi, ad esempio, un archivio 
dei contenuti di Wikipedia. Questo costituisce la nostra biblioteca dove poter calcolare la probabilità di una parola.

Per analizzare il testo bisogna, innanzitutto, contarne le parole. Ad esempio, consideriamo la frase:

"Ho deciso di salire le scale molto piano, l'ufficio si trovava al quinto piano senza ascensore!".

Nella frase appare due volte la parola piano con diversi significati. Definiamo:

1. *parola token* una singola occorrenza di una stringa all'interno del testo, in questo caso, abbiamo due parole token piano;
2. *parola tipo* la classe di tutte le parole token che hanno la stessa sequenza di caratteri, quindi la classe piano che rappresenta tutte le parole token piano anche con diversi significati.
   
Possiamo stimare la probabilità di trovare una parola quindi tramite la **frequenza 
relativa** di quella parola tipo.

Sto però considerando il **contesto**?

### Probabilità condizionata
La probabilità condizionata esprime la probabilità che un evento $A$ si verifichi sapendo 
che un altro evento $B$ è già avvenuto.

Si indica con:

$$
P(A \mid B) = \frac{P(A \cap B)}{P(B)}
$$

dove:
- $P(A \mid B)$ è la probabilità di $A$ dato $B$;
- $P(A \cap B)$ è la probabilità che avvengano **sia A che B**;
- $P(B)$ è la probabilità che avvenga $B$.

Nei modelli di linguaggio la probabilità di una parola $w_n$ dipende 
dalle parole precedenti $v_{n−1}, v_{n−2}, \dots$:

$$
P(v_n∣v_{n−1},  v_{n−2}, \dots) 
$$

cioè è una probabilità condizionata.

### Probabilità dell'evento intersezione

La **regola del prodotto** permette di calcolare la probabilità che due eventi
\(A\) e \(B\) si verifichino **insieme**.

Si esprime come:

$$
P(A \cap B) = P(A \mid B)  P(B)
$$

Se gli eventi \(A\) e \(B\) sono **indipendenti**, allora:

$$
P(A \mid B) = P(A)
$$

e la probabilità dell'evento intersezione diventa:

$$
P(A \cap B) = P(A)  P(B)
$$



