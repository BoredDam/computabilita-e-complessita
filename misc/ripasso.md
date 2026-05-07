# Recap pre-esame

questo è un file di ripassone pre-prova in itinere. si omettono la sintassy fAnCy di LaTeX e le regole della stupenda grammatica italiana, per un guadagno in tempi di ripasso.

prendete il contenuto di questo file con le pinze, e pregate per me pls


## File 1

### URM

Le macchine URM sono delle macchine teoriche che permettono l'esecuzione di programmi URM, costituiti da istruzioni del tipo

```py
Z(n) # azzera n
S(n) # incrementa n
T(m,n) # copia m in n
J(m,n,q) # se m == n, vai all'istruzione q
```

un programma URM è costituito da una sequenza $I_1, I_2, \dots, I_s$ di istruzioni, con $s$ lunghezza del programma.

Le macchine URM operano su un array infinito di celle di memoria contenenti numeri naturali a precisione infinita. Indichiamo l'array di celle col simbolo x-freccia. 
Quando lo disegnamo, ne rappresentiamo una restrizione finita, che esclude le (potenzialemente) infinite celle di memoria successive.

### Configurazioni

Chiamiamo configurazione istantanea la coppia $(k, \vec{x})$, con $k$ contatore di programma e $\vec{x}$ stato dei registri.

Definiamo computazione la sequenza (finita o infinita) di configurazioni istantanee del programma $P$ sullo stato $\vec{x}$ a partire dallo stato iniziale $(1, \vec{x})$.

Una configurazione istantanea $(k_i, \vec{x})$ si dice finale quando $k_i > s$, e quindi non ha successori in $P(\vec{x})$.

### Terminazione e non terminazione

La freccia in basso indica che una determinata computazione termina. È possibile specificare anche il valore di terminazione. 

La freccia in alto indica la non terminazione. Una computazione che non termina diverge, aka è infinita. Il programma che calcola una funzione che non è definita su un valore specifico, divergerà se fornito in input quel valore.

### Funzione parziale

$f : A \to B$ è una funzione parziale se essa è definita su alcuni valori del dominio. Non sempre associa a tutti i valori di A un valore, ma quando lo fa, questi valori sono in B. Utilizziamo la stessa notazione uparrow e downarrow. Una funzione si dice totale se associa a tutti gli elementi di A un elemento in B.

### Calcolabilità di una funzione parziale

Una funzione parziale $g : \mathbb{N}^n\to\mathbb{N}$ si dice calcolabile se esiste un programma $P$ che calcola $f_P^{(n)}$ tale che g ed f sono equivalenti. (equivalenza di Kleene).

Le funzioni urm calcolabili fanno parte dell'insieme C^urm. Le funzioni n-arie URM calcolabili stanno in C^urm_n. 

### Correttezza dei programmi

Date delle specifice di input A e output B, un programma P si dice parzialmente corretto se, quando rispetta A e termina, e l'output rispetta B.

Per essere totalmente corretto, deve anche avere garanzia di terminazione. 

## File 2

### Predicati decidibili

Una predicato n-ario è una funzione con arietà n e esiti true o false. a ogni predicato M associamo una funzione caratteristica c_M che da come output 1 se true e 0 se false. Un predicato M si dice decidibile se la sua funzione caratteristica è calcolabile.


### Calcolabilità su altri domini

Fino ad ora abbiamo lavorato esclusivamente nell'insieme $\mathbb N$. Se esiste una codifica verso e da N, iniettiva, suriettiva, effettivamente calcolabile e cui inversa è effettivamente calcolabile, allora possiamo operare anche su quel dominio.

Possiamo ad esempio lavorare coi negativi associando agli N dispari i numeri negativi, agli N pari i numeri positivi.

### Creazione di funzioni calcolabili

Definito un set di funzioni di base notoriamente calcolabili (funzione costante 0, x + 1 e proiezione, tramite le istruzioni URM che conosciamo), possiamo definire un set di operazioni tra funzioni calcolabili, che, se implementabili sotto forma di programma URM, dimostrano la chiusura dell'insieme delle funzioni calcolabili rispetto a tali operazioni.

### Composizione di funzioni  

Con f k-aria e g_1 ... g_k n-arie, e x-freccia di dimensione n
$$
f(g_1(\vec{x}), \dots,g_k(\vec{x}))
$$

### Ricorsione primitiva

$$
h(\vec x, y+1) \begin{cases}
h(\vec{x}, 0) = f(\vec{x})\\
h(\vec{x}, y + 1) = g(\vec{x}, y, h(\vec{x}, y))
\end{cases}
$$

### Minimalizzazione

$$
\mu y ( f (\vec{x}, y) = 0) = \text{a ...}
$$

... il minimo valore di y per cui f(x-freccia, y) termina su 0, se esiste e se non esistono valori più piccoli di y se non termina.

> seppur questo sembra contorto come behaviour, basta pensare a questa come una ricerca lineare su degli input della funzione da 0 a infinito. se una computazione intermedia non termina o non esiste un valore che azzeri la funzione (come con una funzione costante 1), amen.

