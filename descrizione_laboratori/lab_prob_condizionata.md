# La probabilità nei modelli di linguaggio


| **Tema**                 |                                                                                         |
|:-------------------------|:----------------------------------------------------------------------------------------|
| **Scopo (DigComp)**      | Comprendere come dati e addestramento influenzano l'affidabilità dell'IA (**CS1.2.08**) |
| **Pre-requisiti**        | Frequenza assoluta e relativa, probabilità                                              |
| **Durata**               | 1 ora                                                                                   |
| **Target**               | Studenti del triennio                                                                   |
| **Setting della classe** | Assegnare un computer ogni studente.                                                    |

## File necessari e condivisione
Si consiglia di utilizzare Colab e classroom creando un 
compito con il notebook [esercitazione](../lab_prob_condizionata/Esercitazione.ipynb) 
con una copia per ogni studente.
 

## Fasi della lezione

### Presentazione del caso studio (20 minuti)
Utilizzare il README del laboratorio condividendolo con
gli studenti o proiettandolo per introdurre il caso studio. 
Per prima cosa, dovranno contare le parole e quindi si forniranno agli strumenti alcuni
concetti come parola token, parola tipo, frequenza relativa e assoluta. Si può vedere con Tokenizer cosa succede in
alcuni modelli di linguaggio.

### Esercitazione parte 1 (20 minuti)
In questa fase gli studenti saranno guidata passo dopo passo tramite il 
notebook [esercitazione](../lab_prob_condizionata/Esercitazione.ipynb) 
a scoprire come costruire il contesto con un semplice bigramma. 
Il dataset a disposizione sono i contenuti di Wikipedia. In prima fase usare
il dataset test per avere tempi di lettura dei dati più sostenibili in classe.

Osservare che nella funzione predict viene utilizzata la distribuzione di probabilità e non 
la probabilità massima. Questo per evitare che continui a prevedere la stessa parola entrando in un loop.
Si potrebbe andare ad approfondire la distribuzione di probabilità

### Riflessioni e discussioni (10 minuti)

Alcune domande o spunti sui cui discutere e riflettere:
1. Come posso considerare il contesto? Prova a cercare in internet quante parole token utilizzano i modelli
di AI per considerare il contesto.
2. Cosa può essere il limite di un modello autoregressivo? Andando avanti può dimenticare l'inizio della frase?


