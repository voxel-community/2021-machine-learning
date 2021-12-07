# 04-addestra-rete 

| Capitolo precedente                                                                                                                                          | Capitolo successivo                                                                           |
| :--------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------: |
| [◀︎ 03-crea-rete](../03-crea-rete)  | [05-cosa-ha-imparato ▶︎](../05-cosa-ha-imparato) |

## Obiettivo

Addestrare la rete neurale per imparare la differenza tra cani e gatti.

È tempo di far imparare qualcosa alla nostra rete! Abbiamo creato la sua struttura e l'abbiamo rempita di neuroni. Ma i suoi neuroni sono ancora "vuoti". Affinché i neuroni si attivino e si connettano insieme per imparare, è necessario ***addestrare*** la rete.

L'addestramento (***training***) consiste nel mostrare alla rete una immagine alla volta dicendole in qualche modo che "in questa immagine c'è un gattino" oppure "qui c'è un cagnolino". Le immagini le prenderemo dal nostro dataset che abbiamo già organizzato in due *generatori*.


## Steps

### 1. Imposta velocità e durata dell'addestramento

Il training di una rete comporta regolare diversi parametri. Ce ne sono due in particolare a cui devi prestare attenzione:
- a che velocità vuoi che la rete impari (learning rate),
- per quanto tempo (epoche),

1. Il ***learning rate*** rappresenta il ritmo con cui la rete impara cose nuove. 

      Se questo valore è troppo basso, la rete impiega tantissimo tempo ad apprendere. 
      Tuttavia, se il numero è troppo alto, la rete potrebbe confodersi e al primo errore perderebbe quello che ha imparato fino a quel momento.

2. Il numero di ***epoche*** rappresenta la durata dell'addestramento. Una epoca equivale ad aver visto tutte le immagini del dataset una volta sola. Eseguire più epoche, quindi, si traduce nel far vedere alla rete più volte le stesse immagini. Questo aiuta la rete a rafforzare quello che ha imparato. Tuttavia, **se il numero di epoche è eccessivo, la rete potrebbe "aver imparato a memoria" tutte le immagini, e non essere più in grado di riconoscere immagini nuove che non appartengono al training set**.

Anche in questo caso è dunque importante trovare una via di mezzo. Nel nostro caso useremo una velocità di apprendimento (***learning rate***) uguale a 0.001, e faremo durare l'addestramento per 8 epoche.

Copia il comando in un **nuovo blocco di codice**

```py
LRATE   = 0.001
EPOCH   = 8
```

### 2. Fai partire l'allenamento!

È tutto pronto per addestrare la nostra rete!

- Assegna il learning rate alla rete:

```py
from tensorflow.keras.optimizers import RMSprop

model.compile( loss='binary_crossentropy', optimizer=RMSprop( learning_rate=LRATE ), metrics=[ 'acc' ] )

```

- Fai partire l'addestramento:


```py
history = model.fit(
      train_generator,
      steps_per_epoch=100,
      epochs=EPOCH,
      validation_data=validation_generator,
      validation_steps=50,
      verbose=1)
```

Questo ultimo comando mostrerà piano piano l'avanzamento delle epoche dell'addestramento, il quale impiegherà circa un minuto

> Se vedi che ci mette troppo tempo assicurati di aver attivato la GPU su Colab come spiegato nel primo capitolo del tutorial.

Dovresti vedere un output del genere, dove le barrette rappresentano l'avanzamento di ogni epoca:

```
Epoch 1/8
100/100 [==============================] - 61s 591ms/step - loss: 0.7246 - acc: 0.5725 - val_loss: 0.6440 - val_acc: 0.6420
Epoch 2/8
 26/100 [======>.......................] - ETA: 37s - loss: 0.6602 - acc: 0.6673
```


| Capitolo precedente                                                                                                                                          | Capitolo successivo                                                                           |
| :--------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------: |
| [◀︎ 03-crea-rete](../03-crea-rete)  | [05-cosa-ha-imparato ▶︎](../05-cosa-ha-imparato) |
