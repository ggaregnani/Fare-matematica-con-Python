# La probabilità nei modelli di linguaggio

| **Tema**                    | Costruire un semplice modello predittivo (autoregressione) a partire dalle frequenze delle parole in un testo (contesto)                                                                                                                                                                                                   |
|:----------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Obiettivi**               | Analizzare dati e interpretarli sviluppando deduzioni e ragionamenti sugli stessi anche con l’ausilio di rappresentazioni grafiche.<br> Riconoscere che il machine learning è un tipo di programmazione utilizzato nell'IA che permette agli algoritmi di apprendere dai dati e fare previsioni (**CS3.4.09, Digcomp3.0**) |
| **Pre-requisiti**           | Distribuzione delle frequenze e probabilità                                                                                                                                                                                                                                                                                |

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

![biblioteca](../assets/biblioteca.png)

Per analizzare il testo bisogna, innanzitutto, contarne le parole. Ad esempio, consideriamo la frase:

"Ho deciso di salire le scale molto piano, l'ufficio si trovava al quinto piano senza ascensore!".

Nella frase appare due volte la parola piano con diversi significati. Definiamo:

1. *parola token* una singola occorrenza di una stringa all'interno del testo, in questo caso, abbiamo due parole token piano;
2. *parola tipo* la classe di tutte le parole token che hanno la stessa sequenza di caratteri, quindi la classe piano che rappresenta tutte le parole token piano anche con diversi significati.
  
Il processo di tokenizzazione non sempre fa coincidere le unità con le parole.
Vediamo come suddivide le parole una nota [piattaforma di AI generativa](https://platform.openai.com/tokenizer) e quali sono i token utilizzati.

Contando i token e calcolando la loro frequenza nel testo, possiamo stimare la probabilità di trovare una parola.

Sto però considerando il **contesto**?

### Gli n-grammi

Per valutare il contesto devo considerare la seguenza di n parole precedenti.
Definiamo questa sequenza **n-gramma**.

Considero ad esempio la frase "Lo studente svolge gli esercizi di matematica". I bigrammi sono:
(Lo, studente);(studente, svolge); (svolge, gli); (gli, esercizi); (esercizi, di);
(di, matematica).

In testi lunghi, possiamo contare quante volte ogni n-gramma 
si ripete per calcolare la sua probabilità, cioè la probabilità dell'evento 
intersezione di due parole $P(A \cap B)$.
Inoltre, possiamo calcolare quante volte la singola parola compare nel testo, la frequenza
della parola type $P(B)$.

### Probabilità condizionata
Possiamo ora calcolare la probabilità che un evento $A$ si verifichi sapendo 
che un altro evento $B$ è già avvenuto.

La probabilità condizionata si calcola infatti come:

$$
P(A \mid B) = \frac{P(A \cap B)}{P(B)}
$$

dove:
- $P(A \mid B)$ è la probabilità di $A$ dato $B$;
- $P(A \cap B)$ è la probabilità che avvengano **sia A che B**, evento intersezione;
- $P(B)$ è la probabilità che avvenga $B$.

Applichiamo questo concetto per calcolare la probabilità di una generica parola $w_n$ 
conoscendo le $n$ parole precedenti $w_{n−1}, w_{n−2}, \dots$:

$$
P(w_n∣w_{n−1},  w_{n−2}, \dots) 
$$

dove $n$ è l'ordine dell'n-gramma che scelgo. Più parole considero più ampio sarà il contesto
ma anche il costo computazionale.

Ma come fa un modello predittivo di linguaggio a generare un testo?

## L'autoregressione

In statistica, un modello si dice *autoregressivo*
quando usa i propri output precedenti come input per le previsioni future.

Immaginiamo di voler completare la frase: "Oggi Marco studia..."
La sequenza dell'algoritmo per prevedere la parola sono:
1. suddividere il testo in parole token;
2. contare la frequenza di ogni n-gramma e di ogni 
parola;
3. calcolare la probabilità condizionata; 
4. sulla base delle probabilità scegliere la parola successiva, ad esempio *matematica*. La frase diventa 
"Oggi Marco studia matematica ..." e il nuovo n-gramma finirà con matematica.

## Esercitazione

Cerchiamo di capire come considerare il contesto e
come funziona un modello autoregressivo partendo da un archivio 
dei contenuti di Wikipedia e messo a disposizione sulla piattaforma 
[Hugging Face](https://huggingface.co/datasets/Salesforce/wikitext) (Merity et al., 2016). 

Apriamo il notebook Esercitazione.ipynb:
1. Importiamo i dati di Wikipedia;
2. Individuiamo le *parole token*;
3. Calcoliamo la frequenza assoluta e relativa di una *parola tipo*;
4. Calcoliamo i bigrammi e la probabilità condizionata; 
5. Proviamo a inserire una frase e farla completare dal nostro modello.

### Riflessioni 

Quali sono i limiti legati al contesto e all'autoregressione di un modello 
di linguaggio naturale?

## Fonti

Linguistica computazionale, Alessandro Lenci, Serena Auriemma, Martina Miliani (Hoepli, 2025)