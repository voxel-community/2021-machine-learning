# 03-crea-struttura-rete

| Capitolo precedente                                                                                                                                          | Capitolo successivo                                                                           |
| :--------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------: |
| [◀︎ 02-dataset-immagini](../02-dataset-immagini)  | [04-addestra-rete ▶︎](../04-addestra-rete) |

## Obiettivo

Creare la struttura della rete neurale.

È arrivato il momento di definire la struttura della nostra rete. Con struttura intendiamo il numero di strati (i ***layers***) di neuroni, la loro tipologia, e il numero di neuroni in ciascuno strato. 

In poche parole, più layer e neuroni mettiamo, più la rete diventerà "intelligente". 
Tuttavia, una rete molto grande avrà bisogno di più tempo e di dataset sempre più grandi per essere addestrata.

Per questo motivo è importante trovare una via di mezzo. 

Per imparare la differenza tra gattini e cagnolini ci basteranno 5 layer. In realtà vedremo che ogni tanto la rete potrebbe commette degli errori poiché non impara al meglio, ma per questo nostro esempio va più che bene! ✨

## Steps

### 1. Layer di input

In qualsiasi rete, il primo strato viene chiamato *layer di input*. Questo layer ha il compito di prendere le immagini dal nostro dataset. Il numero di neuroni di questo strato corrisponde alla dimensione delle immagini, che abbiamo impostato a 150x150x3 (tre canali per RGB).

- Crea il primo layer con questo comando:

```py
layer_input = layers.Input( shape=( 150, 150, 3 ) )
```

### 2. Layer interni adatti ad analizzare le immagini

I successivi tre strati si chiamano *convoluzioni*. In questi layer i neuroni sono organizzati in 3D nella forma di un parallelepipedo, e sono adatti ad analizzare immagini.

- Crea tre strati in sequenza:

```py
# primo layer
x = layers.Conv2D(16, 3, activation='relu')(layer_input)
x = layers.MaxPooling2D(2)(x)

# secondo layer
x = layers.Conv2D(32, 3, activation='relu')(x)
x = layers.MaxPooling2D(2)(x)

# terzo layer
x = layers.Conv2D(64, 3, activation='relu')(x)
x = layers.MaxPooling2D(2)(x)
```

Come quarto layer usiamo uno strato chiamato *fully-connected*, detto anche "layer denso". In questo layer i neuroni vengono compressi e appiattiti su sola dimensione, come in una specie di lista.

- Crea il quarto layer fully-connected con 512 neuroni:

```py
# quarto layer
x = layers.Flatten()(x)
x = layers.Dense(512, activation='relu')(x)
```

### 3. Layer di output

L'ultimo strato della nostra rete ha il compito di produrre l'output, ovvero il risultato. 

Nel nostro caso, il risultato deve essere un valore che rappresenta la presenza di gattini o di cagnolini. La soluzione più semplice è avere il layer che restituisce un singolo numero (ovvero un solo neurone), compreso tra 0 e 1: se il numero è vicino a 0 indichiamo i gattini 🐈, se è vicino a 1 abbiamo dei cagnolini 🐕.

- Crea il layer di output con un solo neurone:

```py
layer_output = layers.Dense(1, activation='sigmoid')(x)
```

### 4. Metti tutto insieme

Adesso che abbiamo definito la forma degli strati della rete, mettiamo tutto insieme per creare la rete completa, unendo il layer di input e il layer di output. 

Per farlo, bisogna creare un oggetto `Model` che contiene la rete neurale completa. A `Model` basta passare i nomi del layer di input e del layer di output. Ed è fatta!

- Crea la rete neurale chiamata `PuppiesKittens`:

```py
model = Model( layer_input, layer_output, name="PuppiesKittens" )
```

- Visualizza il contenuto della rete:

```py
model.summary()
```

Questo ultimo comando restituisce una descrizione dei layer della rete, ed include il numero totale di neuroni (`Total params`) contenuti nella rete. 

Dovresti avere una rete con circa 9.5 milioni di neuroni, mica male!



| Capitolo precedente                                                                                                                                          | Capitolo successivo                                                                           |
| :--------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------: |
| [◀︎ 02-dataset-immagini](../02-dataset-immagini)  | [04-addestra-rete ▶︎](../04-addestra-rete) |