# 01-classificatore-come-funziona

| Capitolo precedente                                                                                                                                          | Capitolo successivo                                                                           |
| :--------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------: |
| [◀︎ 00-setup](../00-setup)  | [02-dataset-immagini ▶︎](../02-dataset-immagini) |

## Obiettivo

Crea una rete neurale in grado di distinguere tra immagini di gattini e immagini di cagnolini.

Con questo esercizio programmeremo da zero una rete neurale che, data un'immagine, è in grado di dire se sono presenti cani oppure gatti.

Questa tipologia di rete si chiama ***classificatore***, nel senso che deve imparare a distinguere tra "classi" di oggetti. In questo caso abbiamo due classi: la classe gattino 🐱 e la classe cagnolino 🐶.

### Come funziona?

Una rete neurale è una struttura composta da strati (=layer) di "neuroni artificiali" connessi tra di loro.

Quando creiamo una rete, definiamo quanti neuroni deve avere e su quanti strati vanno disposti i neuroni. Appena creata, però, la rete non è in grado di fare nulla in quanto i suoi neuroni non hanno ancora alcun significato.

Per essere usata, una rete va prima ***addestrata***. L'addestramento di una rete dipende dal tipo di compito che vogliamo essa esegua. Nel nostro caso vogliamo un classificatore di immagini, quindi l'addestramento consisterà nel mostrare alla rete un gran numero di immagini indicandole ogni volta se è presente un cagnolino oppure un gattino.

<kbd>![net](../assets/01-net.gif)</kbd>
(image from [codeburst.io](https://codeburst.io/machine-learning-243cc92247a1))

Dopo un periodo di addestramento, avendo visto tanti esempi di cosa è un cagnolino e di cosa è un gattino, i neuroni della rete si saranno attivati in una configurazione particolare. Questa configurazione permette alla rete di apprendere i concetti astratti di *gatto* e *cane*.

Terminato l'addestramento, la rete sarà quindi in grado di analizzare immagini mai viste prima ed riconoscere se ci sono gattini o cagnolini. Proviamo!


| Capitolo precedente                                                                                                                                          | Capitolo successivo                                                                           |
| :--------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------: |
| [◀︎ 00-setup](../00-setup)  | [02-dataset-immagini ▶︎](../02-dataset-immagini) |