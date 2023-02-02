# Reinforcement Learning & q-Taxi

## Paradigma reale

Il concetto è simile all'addestramento di un cane.

Se si richiede ad un cane di fare qualcosa (es. riportare indietro un bastone) questo non risponderà        nel modo voluto.

Immaginiamo di simulare l'ambiente del parco e di lanciare un bastone.

Se il cane raccoglie il bastone e lo riporta indietro (comportamento desiderato)        esso viene premiato con un croccantino.

Immaginiamo di portare realmente il cane al parco e di lanciare un bastone;        esso raccoglierà il bastone e lo riporterà indietro con l'obiettivo di ricevere un altro croccantino (REWARD).

Questa è una tecnica di apprendimento positiva.

Immaginiamo di sgridare (PENALTY) il cane quando compie qualche gesto sgradevole;       il cane impererà cosa non dovrà fare.

Il cane si può denomianare AGENTE

il giardino (parco) è l'AMBIENTE

la situazione in cui ci si trova è lo STATO



Un esempio di stato è "il cane è difronte a me e io, con un certo tono di voce, gli dico qualcosa"



L'agente esegue un'AZIONE per transitare (TRANSIZIONE) da un certo stato ad un altro.

Un esempio di azione è "il cane si siede"



La transizione viene seguita da un reward o un penalty.



La POLICY (politica) è la strategia secondo la quale scegliere un'azione        ,in una certa situazione, che fornisca il miglior risultato.



## Reinforcement Learning

Il reinforcement learning si può definire come un concetto stante tra il supervised learning e l'unsupervised learning

Alcune attività possono trarre piccoli profitti da subito e altre tanti dopo molto sforzo.
L'obiettivo non è trarre il massimo numero di profitti ma di ottenere il massimo valore di profitto.
Quindi si vuole ottenere un valore massimale sul lungo periodo.
Di conseguenza, un reward non dipende da un singolo stato ma il valore totale sul lungo periodo dipende da una serie di stati.

Quindi, il reinforcement learning si può definire come la scienza dell'intraprendere ottime decisioni basandosi sull'esperienza.
Questo è possibile seguendo alcuni step
1) osservazione dell'ambiente
2) decidere cosa fare attuando delle strategie
3) agire secondo le strategie
4) ricevere un reward o un penalty
5) imparare dall'esperienza e rifinire la strategia
6) iterare fin quando la strategia ottimale non è definita

## q-Taxi

insegnare ad un taxi a prelevare i clienti dal luogo giusto e accompagnarli alla destinazione corretta

mediante il reinforcement learning.

Si vuole

a) lasciare il passeggero alla destinazione corretta

b) risparmiare tempo al passeggero evitando un numero eccessivi di "discese"

c) preoccuparsi per la sicurezza del passeggero e per le regole del traffico



L'autista è l'agente che vuole sviluppare la propria strategia imparando a controllare il taxi basandosi sull'esperienza acquisita.

L'agente dovrebbe ricevere un reward se rilascia il passeggero nel luogo giusto.

L'agente dovrebbe ricevere un penalty se rilascia il passeggero nel luogo sbagliato.

L'agente dovrebbe ricevere un leggeri penalty se non rilascia il passeggero nel luogo giusto in tempo;

in questo caso il penalty deve essere leggero perché non si vuole che l'autista compia gesti sbagliati (es. guidare in modo imprudente) pur di ottenere un reward.



Lo **state space** è l'insieme di tutte le possibili situazioni che il taxi può incontrare

![](/Users/anto/Documents/VmWareSharedDir/win7/taxi-QL/readme/im1.png)

Il taxi può raggiungere 4 destinazioni: R,G,Y,B.

Immaginiamo che lo *state space* sia un parcheggio; si può dividere lo spazio come una griglia quindi il taxi può trovarsi in una delle 25 celle. Ciscuna cella viene identificata per mezzo di coordinate.

La posizione attuale del taxi è (3,1). Il passeggero si trova in Y ovvero in (4,0).

N.B.: è possibile simulare più passeggeri con le relative destinazioni complicando lo scenario.

### Azioni

Il taxi può compiere 6 azioni diverse:

1) andare a sud
2) andare a nord
3) andare ad est
4) andare ad ovest
5) caricare il passeggero
6) scaricare il passeggero

Queste azioni costituiscono l'**action space** ovvero l'insieme di tutte le azioni che l'agente può svolgere in un certo stato.

Tuttavia, l'agente (autista) non può compiere ogni azione quando desidera; esso non potrà andare contro un muro infatti in tal caso riceverà un penalty.

## Implementazione (python3)

[OpenAI gym](https://www.gymlibrary.dev/) fornisce un'implementazione per lo scenario illustrato chiamato *Taxi-v2*.

Occorre installare il pacchetto gym in Python

~~~py
``` 
pip3 install gym
```
~~~

È possibile caricare l'ambiente e visulaizzarlo con

~~~py
```
import gym
env = gym.make("Taxi-v2").env
env.render
```
~~~
