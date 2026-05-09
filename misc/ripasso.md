# Recap pre-prima itinere

questo è un file di ripassone pre-prova in itinere. si omettono la sintassy *✨fancy✨* di LaTeX e le regole della stupenda grammatica italiana, per un guadagno in tempi di ripasso.

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

Nelle funzioni parziali, $Dom(f) \subseteq A$.

### Calcolabilità di una funzione parziale

Una funzione parziale $g : \mathbb{N}^n\to\mathbb{N}$ si dice calcolabile se esiste un programma $P$ che calcola $f_P^{(n)}$ tale che g ed f sono equivalenti. (equivalenza di Kleene).

Le funzioni urm calcolabili fanno parte dell'insieme C^urm. Le funzioni n-arie URM calcolabili stanno in C^urm_n. 

### Correttezza dei programmi

Date delle specifice di input A e output B, un programma P si dice parzialmente corretto se, quando rispetta A e termina, l'output rispetta B.

Per essere totalmente corretto, deve anche avere garanzia di terminazione su ogni input. 

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

## File 3


### Ricorsione primitiva

$$
h(\vec x, y+1) \begin{cases}
h(\vec{x}, 0) = f(\vec{x})\\
h(\vec{x}, y + 1) = g(\vec{x}, y, h(\vec{x}, y))
\end{cases}
$$

A parità di $f$ e $g$, esiste sempre ed è unica una funzione primitiva ricorsiva così definita.

Tra i vari risultati, abbiamo che:
produttorie, sommatorie, minimalizzazioni (tutte limitate) sono decidibili. Definizioni per casi sono decidibili tramite sommatorie di funzioni calcolabili per la funzione caratteristica del predicato definito su ogni caso. Lo è la ricerca dell'n-esimo numero primo.

Ne consegue che è possibile codificare una qualsiasi sequenza di interi come espomenti di prodotti di numeri primi. In questo modo possiamo ricondurre ricorsioni non primitive in una forma primitiva.


## File 4


### Minimalizzazione

$$
\mu y ( f (\vec{x}, y) = 0) = \text{a ...}
$$

... il minimo valore di y per cui f(x-freccia, y) termina su 0, se esiste e se non esistono valori più piccoli di y se non termina.

> seppur questo sembra contorto come behaviour, basta pensare a questa come una ricerca lineare su degli input della funzione da 0 a infinito. se una computazione intermedia non termina o non esiste un valore che azzeri la funzione (come con una funzione costante 1), amen.


Inoltre, la minimalizzazione sulla funzione caratteristica di un predicato decidibile, è decidibile

```
minimalizzazione di y(!sign(M(X, y)) = 0)
```

### Funzioni ricorsive parziali

L'insieme definito per composizione, ricorsione primitiva e minimalizzazione sulle funzioni iniziali è noto come l'insieme delle **funzioni ricorsive parziali**, e coincide con l'insieme delle funzioni URM-calcolabili.

L'insieme che esclude le funzioni ottenute con la minimalizzazione, include solo funzioni totali, e si dice insieme delle funzioni **primitive ricorsive**.


### Funzione di Ackermann

$$
	\psi(x,y)=
	\begin{cases}
		\psi (0, y) = \begin{cases}
			1 & \text{se } y=0 \\
			2 & \text{se } y=1 \\
			y+2 & \text{se } y>1
		\end{cases}
		& \text{se } x=0 \\[14pt]
		\psi (x, 0) = 1 & \text{se } x\geq 1,\; y=0 \\[6pt]
		\psi(x+1,y+1) = \psi(x,\psi(x + 1,y)) 
		& \text{se } x\geq 1,\; y\geq 1
	\end{cases}
$$

La funzione di Ackermann cresce più velocemente di qualsiasi altra funzione primitiva ricorsiva, quindi non può essere "contenuta" da una di esse. Qui, il riassunto della dimostrazione della calcolabilità


#### 1. Una tripla $(x,y,z)$ significa “$\psi(x,y)=z$”

- La tripla è un modo compatto per registrare un risultato parziale della computazione.
- Ad esempio, $(2,3,5)$ va letta come: “il valore di $\psi(2,3)$ è $5$”.
- Quindi le triple sono come righe di una tabella dei valori di Ackermann.


#### 2. Un insieme suitable è un insieme finito di triple che rispetta le regole di Ackermann

- Non ogni insieme di triple va bene: deve essere coerente con le tre clausole della definizione.
- Se contiene una tripla non di base, deve contenere anche le triple precedenti che la giustificano.
- Quindi un insieme suitable è come una piccola “prova finita” del valore scritto nelle sue triple.


#### 3. Gli insiemi finiti di triple si possono codificare con numeri

- Ogni tripla $(x,y,z)$ viene trasformata in un numero tramite una codifica standard.
- Poi un insieme finito di triple viene codificato a sua volta con un solo numero.
- In questo modo possiamo cercare tra numeri invece che tra insiemi astratti.


#### 4. Si può decidere meccanicamente se un numero codifica un insieme suitable

- Dato un numero $v$, possiamo decodificarlo e vedere quali triple contiene.
- Poi controlliamo, una per una, se rispettano le condizioni di suitable.
- Siccome l’insieme codificato è finito, questo controllo termina sempre.


#### 5. Allora si può cercare il primo insieme suitable che contiene una tripla $(x,y,z)$

- Fissati $x$ e $y$, si scorrono i numeri $v=0,1,2,\dots$.
- Per ogni $v$, si controlla se codifica un insieme suitable.
- Appena si trova un insieme suitable che contiene una tripla della forma $(x,y,z)$, ci si ferma.


#### 6. Il corrispondente $z$ è il valore di $\psi(x,y)$

- La suitable-ness garantisce che le triple contenute nell’insieme siano corrette.
- Quindi se l’insieme contiene $(x,y,z)$, quel $z$ non è casuale: è proprio il valore imposto dalle regole di Ackermann.
- Perciò leggendo quel $z$ otteniamo il valore cercato.


#### Conclusione

La funzione di Ackermann è calcolabile perché possiamo fare questa procedura:

$$
\text{cerca un codice }v
\rightarrow
\text{verifica che sia suitable}
\rightarrow
\text{leggi il valore }z.
$$

Quindi non serve conoscere in anticipo una formula semplice per $\psi(x,y)$: basta sapere che esiste una **prova finita codificabile** del suo valore, e che possiamo cercarla meccanicamente.



## File 5

### Funzioni ricorsive parziali - $\mathcal{R}$

$\mathcal{R}$ è la più piccola famiglia di funzioni parziali contenente le funzioni iniziali e che è chiusa rispetto a sostituzione, ricorsione primitiva e minimalizzazione.

Chiamiamo $\mathcal{R}_0$ la famiglia delle funzioni mu-ricorsive, ossia le funzioni definite su sostituzione, ricorsione p. e minimalizzazione MA solo se questa produce funzioni totali.

### $\mathcal{R} = C_{URM}$

Per definizione di $\mathcal{R} \subseteq C_{urm}$, questo è contenuto o concide con C. Dimostrare il contrario sembra complesso, ma in realtà nemmeno troppo.

Vogliamo dimostrare che $C_{URM} \subseteq \mathcal{R}$, ossia che tutte le funzioni calcolabili possono essere espresse come funzione ricorsiva parziale.


Supponiamo $f(\vec x)$ sia una funzione URM-calcolabile e P un programma che la calcola. Si definiscono delle funzioni:
-  $c_p(\vec x, t)$ = codifica della configurazione istantanea della computazione p su input x dopo t passi, di cui
    - $\pi_1(c_p(\vec x, t))$ è il valore del contatore di programma
    - $\pi_2(c_p(\vec x, t))$ codifica i registri, a cui si accede tramite $(\pi_2(c_p(\vec x, t)))_i$

La funzione $c_p(\vec x, t)$ è primitiva ricorsiva, quindi la computazione può essere simulata per un  finito di passi. 

$$
f_p(\vec x) = \pi_2(c_p(\vec x, \mu t (\pi_1(c_p(\vec x, t)) = 0)))_1
$$

Inserendo una ricerca non limitata sul valore t, si simula l'intera computazione, quindi R contiene tutte le funzioni calcolabili.

### Macchina di Turing

Hardware: 
- Nastro infinito diviso in caselle in cui ognuna delle caselle può contenere un simbolo dell'alfabeto o blank
- testina di lettura scrittura
- unità di controllo specificata da un insieme finito di quadruple

Operazioni elementari:
- Cancellare e sostituire un simbolo in lettura con un altro simbolo dell'alfabeto
- Spostare la testina a destra di una posizione
- Spostare la testina a sinistra di una posizione
- Cambiare lo stato interno della macchina scegliendo da una lista finita di stati interni della macchina, in base alle specifiche della macchina stessa

### Quadruple d'azione

$$
q_i, s_j, \alpha, q_\ell
$$

$$
\text{simbolo letto}, \
\text{stato corrente}, \
\text{azione (L/R/nuovo simbolo)}, \
\text{nuovo stato}
$$


### Turing calcolabilità

Una funzione si dice Turing calcolabile se questa è calcolabile da una macchina di Turing

### Tesi di Church-Turing

La classe delle funzioni intuitivamente calcolabili coincide con la classe $C_{URM}$ delle funzioni calcolabili.

## File 6

### Enumerazione delle funzioni calcolabili

- Gli insiemi $\mathbb N^2$, $\mathbb N^3$ ed $\mathbb N^k$ sono EFFETTIVAMENTE enumerabili.

- L'insieme di tutte le istruzioni URM è EFFETTIVAMENTE enumerabile

- L'insieme di tutti i programmi URM è EFFETTIVAMENTE enumerabile

- A ogni programma URM è associabile un numero noto come numero di Godel

- $P_n$ è il programma con numero di Godel n

- $\phi_a^{n}$ è la funzione n-aria calcolata dal programma $P_a$
    - $W_a^{n}$ è il suo dominio
    - $E_a^{n}$ è il suo range

- Una funzione calcolabile si trova nella sequenza (con ripetizioni) $\phi_1^{n}, \phi_2^{n}, \dots$.

- Si può rendere la sequenza senza ripetizioni trovando l'indice l'indice minimo per cui nessuno tra gli indici precedenti codifica la stessa funzione

### Diagonalizzazione

La diagonalizzazione di Cantor è un modo utilizzato per costruire ad hoc delle funzioni non calcolabili. Si costruisce la funzione $\chi(i) \neq \chi_i(i)$, ossia diversa da tutti gli elementi della diagonale della matrice del tipo

$$
\begin{array}{c|ccccc}
	& 0 & 1 & 2 & 3 & \cdots \\ \hline
	\chi_0 & \chi_0(0) & \chi_0(1) & \chi_0(2) & \chi_0(3) & \cdots \\
	\chi_1 & \chi_1(0) & \chi_1(1) & \chi_1(2) & \chi_1(3) & \cdots \\
	\chi_2 & \chi_2(0) & \chi_2(1) & \chi_2(2) & \chi_2(3) & \cdots \\
	\vdots & \vdots & \vdots & \vdots & \vdots & \ddots
\end{array}
$$

### Esempi d'uso 
Un esempio di funzione totale, unaria e non calcolabile, è la funzione

$$
f(n) = \begin{cases}
\phi_n(n) + 1 & \text{se } \phi_n(n)\downarrow\\
0 & \text{se } \phi_n(n)\uparrow
\end{cases}
$$

Ne consegue che il problema $n \in W_n$ è indecidibile.