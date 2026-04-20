# Distanza euclidea e machine learning

| **Tema**                 | Calcolo della distanza tra due punti per comprendere la matematica alla base degli algoritmi di machine learning                                                       |
|:-------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Scopo (DigComp3.0)**   | Riconoscere che il machine learning è un tipo di programmazione utilizzato nell'IA che permette agli algoritmi di apprendere dai dati e fare previsioni (**CS3.4.09**) |
| **Pre-requisiti**        | Tabella a doppia entrata, distanza tra due punti, moda                                                                                                                 |
| **Durata**               | 4 ore                                                                                                                                                                  |
| **Target**               | Classe seconda a terza scuola secondaria di secondo grado                                                                                                              |
| **Setting della classe** | Laboratorio di informatica con computer per ogni  studente.                                                                                                            | 


## File necessari e condivisione
Gli studenti lavorano singolarmente all'**analisi di caso**. 
Viene fornito ad ogni studente il testo dell'[esercitazione_parte1](../lab_distanza_ml/esercitazione_parte1.pdf)
Il testo è scritto in latex e i sorgenti sono disponibili nella cartella materiali.
Si consiglia di utilizzare Colab e classroom creando un 
compito con il notebook [esercitazione_parte2](../lab_distanza_ml/esercitazione_parte2.ipynb) 
con una copia per ogni studente.


## Fasi della lezione

### Introduzione al machine learning (10 minuti-15 minuti)
Prima di partire con il caso studio abbiamo chiesto agli studenti:
1. Perché usare l'IA?
2. Come funziona un semplice algoritmo di machine learning?

Per rispondere alla prima domanda si può ragionare su come l'IA ci permetta di "abbracciare la complessità 
e fare uso del migliore alleato che abbiamo: l'irragionevelo efficacia dei dati" 
(La scorciatoia, N. Cristianini) per poi spiegare
brevemente agli studenti come funziona un algoritmo di machine learning ML.

### Presentazione del caso studio (20 minuti-30 minuti)
Utilizzare il README del laboratorio condividendolo con
gli studenti o proiettandolo per spiegare l'algoritmo.

### Esercitazione parte 1 (50 minuti)
Consegnare agli studenti [esercitazione_parte1](../lab_distanza_ml/esercitazione_parte1.pdf) 
e si può chiedere di svolgere le prime fasi dell'esercizio con un foglio di calcolo oppure a mano:
1. calcolo delle distanze dei punti di test dai punti di training
2. ordinare i punti in base alla distanza
3. scegliere i 3 punti più vicini
4. calcolare la moda e assegnare la label al punto di test 
A questo punto, dopo un confronto sui risultati ottenuti, si può procedere al calcolo 
della matrice di confusione.

Chiedere agli studenti di provare a ripetere l'esercizio con k=5.
Cosa osservano? 
L'esercitazione è costruita in modo che la label di uno dei punti di test cambia al variare di k e
quindi anche la matrice di confusione e l'accuratezza del modello. 
Obiettivo è far capire come sia compito del data scientist trovar quel valore di k
che migliora le performance del modello. Si può chiedere agli studenti se ha senso aumentare k e che rischi 
ci sono a utilizzare un k troppo alto.

### Esercitazione parte 2 (100 minuti)

Il [esercitazione_parte2](../lab_distanza_ml/esercitazione_parte2.ipynb)  può essere eseguito passo passo con gli studenti. Dopo ale prime considerazioni
sul dataset, si chiede agli studenti di scegliere due colonne del dataset che secondo loro possono essere 
usati per costruire il modello di previsione dei gusti di George. Possono visualizzare i punti
con le coordinate da loro scelte nel piano cartesiano.
Non esiste una scelta giusta o sbagliata.
Dopo aver scelto i due parametri, suddividere bene la fase di training dal test. 
Lasciare agli studenti la possibilità di cambiare le colonne scelte e il valore di k.
I valori di accuratezze che ottengono saranno intorno al 0.68.

Si può chiedere, a seconda delle competenze informatiche, di implementare un ciclo for per la scelta del k.

Costruito il modello, si introduce un nuovo set di validazione per capire se il modello costruito riesce a
prevedere i gusti di George.
