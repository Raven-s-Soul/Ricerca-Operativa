# Soluzione di problemi di Programmazione Lineare

## Fourier-Motzkin

Problema geometrico di PL è generalmente

$$
\begin{gather}
\min c^Tx
\\
\{ Ax \leq b \}
\end{gather}
$$

>[!Note]
> é non vuoto se la sua ombra verso gli assi ammette punti

$$
\begin{matrix}
n & \text {limite inferiore} \\
m & \text {limite superiore} \\
\end{matrix}
$$
$$
\begin{Bmatrix}
A_1 \geq n \\
A_2 \leq m \\
\end{Bmatrix}
$$
$$
\begin{matrix}
n \leq m & \text {poliedro non vuoto} \\
n = m & \text {poliedro si proietta in un punto} \\
n \geq m & \text {poliedro è vuoto} \\
\end{matrix}
 $$

> Passare da un $\mathbb{R}^n$ verso un $\mathbb{R}^{n-1}$, tramita eliminazione della variabile $x_n$ ci sono 2 implicazioni
> - (Univoca) Passare da n a n-1 tolgo 1 componente
> - (Non univoca) Passare da n-1 a n, il quale ho libertà basti che soddisfa la condizione

$$
\begin{align*}
x_1 + x_2 \geq a \\
x_2 \leq b \\
... \\
\end{align*}
$$


$$
\begin{matrix}
\text {1 tipo} \( x_2 \geq \) & x_2 \geq x_1 + d \quad ... \\
\text {2 tipo} \( x_2 \leq \) & x_2 \leq b \\
\text {3 tipo} \( \text{non compare } x_2 \) & x_1 \geq c
\end{matrix}
$$

Esempio di come procedere

$$
\begin{align*}
b \geq x_1 + d \\
x_1 \geq c
\end{align*}
$$

Implicazione 2 dice, se prendo la soluzione $x_1 = a_1$ esiste almeno un valore $a_2=a_2$ che risolve il poliedro di partenza

$$
\max ( x_1 + d ) \leq a_2 \leq ( b )
$$

Come capire se il poliedro proiettato in $(x_1)$ è vuoto oppure no? Scegliere il vincolo più forte.

$$
\begin{align*}
x_1 \leq -d + b \\
x_1 \geq c
\end{align*}
$$

Esiste il caso in cui:
- $x_1$ è in un solo punto
- $x_1$ in un range di punti
- $x_1$ illimitato in una direzione, tipo $x_1 \leq 0$ (inferiormente)
- $x_1$ sensa vincoli
- Basta non trovarsi in casi in cui è impossbile

infine possiamo scegliere un valore ammissibile per $x_1$ e altrettando dopo per $x_2$

> [!important]
> In un sistema di disequazione di $m$ disequazione in $n$ variabili:
> - 1 tipo -> k
> - 2 tipo -> h
> - 3 tipo -> m - k - h

Posso fondre il 1 tipo e il secondo tipo cosi a coppie: (k * h combinazioni)

$$
\begin{align*}
\text {tipo 1} \quad  \geq \quad \text {tipo 2}  
\end{align*}
$$

> k * h può essere più grande di m

> infine per scegliere una soluzione ammissibile pongo un valore valido per una variabile e trovo la proiezzione del altra variabile e tutti i punti possibili a cui posso scegliere al 2nd variabile.

### funzione obbiettivo

$$
\begin{gather}
\min c^Tx = ( c_1, c_2, ... ,c_n)(x_1,x_2, ... , x_n)^T \\
\text{Pongo per esempio} \quad c_n = 0 \quad \to \quad \text {allora} \\
\min c^Tx = ( c_1, c_2, ... ,c_n)(x_1,x_2, ... , x_n)^T = ( c_1, c_2, ... ,c_{n-1})(x_1,x_2, ... , x_{n-1})^T
\end{gather}
$$

>[!Note]
>Se tutti i costi diversi da 0?
>- Non posso proietttare per eliminazione

Metodo:
1. aggiungo nuova variabile $z$ da minimizzare
2. nuovo vincolo $z= c^Tx$
3. applico la proiezione per sostituzione (eliminare $z= c^Tx$)

Tutte le variabili hanno costo nullo tranne $z$, proiettare tutte le variabili $x_i$ una alla volta

$$
\begin{gather}
\min z \\
\begin{Bmatrix}
z \geq a \\
z \leq b \\
\end{Bmatrix}
\end{gather}
$$

- Se $a \geq b$ problema inammissibile
- se $a \leq b$ allora $z\* = a$, trovo tutti i valori di $x_i$

***

## Geometria della Programmazione Lineare

>[!Important] Semispazi e poliedro
> - **Semispazio**: $S^{\ge} = \{x \in \mathbb{R}^n : a^T x \ge b\}$, $S^{\le} = \{x \in \mathbb{R}^n : a^T x \le b\}$. Sia i semispazi sia gli iperspazi (gli insiemi $\{x : a^Tx = b\}$) sono **convessi**.
> - **Poliedro**: intersezione di un numero *finito* $m$ di semispazi, $P = \{x \in \mathbb{R}^n : Ax \le b\}$. Se è limitato si chiama **politopo**.
> - Un politopo generato dai vettori $v_1,\dots,v_r$ tramite combinazione convessa ($\sum k_i v_i$ con $k_i \ge 0$, $\sum k_i = 1$) è il **più piccolo politopo** contenente quei vettori.

>[!Note] Vertici, direzioni, combinazione convessa
> - **Vertice**: punto $x \in P$ che **non** è combinazione convessa di altri due punti di $P$. Formalmente non esistono $x_1, x_2 \in P$ con $x = \alpha x_1 + (1-\alpha) x_2$, $\alpha \in (0,1)$.
>   - Nota: $\alpha \in [0,1]$ include gli estremi, $\alpha \in (0,1)$ li esclude → per escludere il punto stesso si usa l'intervallo aperto.
> - **Direzione**: solo per poliedri **illimitati**. Un versore $d$ ($\|d\|=1$) è direzione di $P$ se $\forall x \in P,\ \forall \alpha \ge 0:\ x + \alpha d \in P$.
>   - Definizione algebrica equivalente: $d$ è direzione $\iff Ad \le 0$.
> - **Direzione estrema**: direzione non esprimibile come combinazione conica di altre due direzioni ($d \ne k_1 d_1 + k_2 d_2$).
>
> ⚠️ Attenzione al **segno della direzione**: cambiando il segno si punta verso l'esterno del poliedro e si perde l'ammissibilità.

>[!Important] Teorema di Weyl–Minkowski
> Se $P$ contiene almeno un vertice allora: i vertici e le direzioni estreme sono in **numero finito**; ogni punto di $P$ si scrive come **combinazione convessa dei vertici + combinazione conica delle direzioni estreme**:
> $$x = \sum_{i=1}^{k} \lambda_i x^i + \sum_{j=1}^{h} \mu_j d^j, \qquad \sum_i \lambda_i = 1,\ \lambda_i,\mu_j \ge 0$$
> È il risultato che giustifica la ricerca dell'ottimo **fra i vertici**.

### Problema di PL e casi
Forma standard geometrica $\min\{c^T x : x \in P\}$:
- $\exists x^* \in P$ con $c^T x^* \le c^T x\ \forall x \in P$ → **soluzione ottima** $x^*$, valore $z^* = c^T x^*$.
- $P = \emptyset$ → problema **inammissibile**.
- $\exists$ direzione $d$ con $c^T d < 0$ → **illimitato inferiormente** ($z^* = -\infty$): ha soluzioni ma nessuna ottima.

>[!Important] Condizione geometrica di illimitatezza
> Se esiste una direzione $d$ di $P$ con **costo negativo** ($c^T d < 0$), camminando lungo $d$ il costo cala indefinitamente → illimitato inferiormente.

***

## Soluzione di Base Ammissibile (SBA)

Si passa dalla forma $\le$ alla **forma standard** aggiungendo le variabili di *slack* $s$: $Ax \le b \Rightarrow Ax + s = b,\ x,s \ge 0$. Si suppone $\text{rk}(A) = m$.

>[!Important] Catena di teoremi (vertice ⇄ SBA)
> - Se $P = \{x : Ax = b,\ x \ge 0\}$ è **non vuoto**, esiste sempre **almeno un vertice**.
> - **Condizione geometrica di ottimalità**: se esiste una soluzione ottima, esiste un **vertice ottimo**.
> - **Teorema chiave**: $x \in P$ è **vertice** $\iff$ $x$ è una **SBA** (*Soluzione di Base Ammissibile*).
> - Se esiste una soluzione ottima, allora esiste una **SBA ottima** → si può cercare l'ottimo solo fra le SBA.

>[!Note] Quante SBA (e perché non si enumerano tutte)
> Una base sceglie $m$ colonne su $n$: il numero di basi è $\binom{n}{m} = \dfrac{n!}{m!(n-m)!}$, che **cresce in modo esponenziale**. Alcune sottomatrici $m\times m$ sono singolari e alcune SBA non sono ammissibili → per questo non si enumerano esplicitamente, ma si usa il **simplesso** (enumerazione *implicita*).

>[!tip] Forma canonica rispetto a una base $B$
> Partizionando $A = [A_B \mid A_N]$, $x = (x_B, x_N)$, si ricava $x_B = A_B^{-1}b - A_B^{-1}A_N x_N$ e la funzione obiettivo diventa
> $$\min\; \bar z + \bar c^T x_N, \qquad \bar z = c_B^T A_B^{-1} b, \qquad \bar c = c_N - c_B^T A_B^{-1} A_N$$
> Il vettore $\bar c$ sono i **costi ridotti delle variabili fuori base**: sono i costi delle variabili non in base dopo aver "assorbito" l'effetto delle variabili in base.

>[!Important] Condizioni algebriche di ottimalità
> Per la SBA $x_B = \bar b,\ x_N = 0$:
> - **sufficiente**: se tutti i costi ridotti fuori base sono **$\bar c \ge 0$** → la SBA è **ottima**.
> - **necessaria**: se la SBA è ottima **e non degenere** → $\bar c \ge 0$.
>
> ⚠️ **Caso degenere**: la condizione $\bar c \ge 0$ è sufficiente ma **non necessaria**. Se la SBA è degenere e ha costi ridotti non tutti positivi, **non si può affermare nulla** né sull'ottimalità né sull'illimitatezza.

>[!Important] Condizioni algebriche di illimitatezza
> Se $\bar b \ge 0$ e **esiste** una variabile fuori base $j$ con $\bar c_j < 0$ **e** $\bar A_j \le 0$ (tutte componenti non positive) → il problema è **illimitato inferiormente**. Se $\bar A_j$ ha anche componenti positive, l'illimitatezza non è dimostrabile.

***

## Algoritmo del Simplesso

Idea: se il problema non è illimitato, **una SBA è ottima**; si parte da una SBA e ci si sposta su una **SBA adiacente di costo non maggiore** fino all'ottimo. È un **algoritmo esatto** e termina in un numero finito di passi (se non degenere).

>[!Note] SBA adiacenti
> Due basi $B_1, B_2$ sono **adiacenti** se differiscono per **una sola colonna**: si fa **entrare** una variabile in base e **uscire** un'altra (pivot).

>[!Important] Test di ottimalità e illimitatezza (criterio di scelta)
> Data la forma canonica ($\bar b \ge 0$):
> 1. Se $\bar c \ge 0$ → **ottima**, stop ($x_B = \bar b,\ x_N = 0$).
> 2. Se $\exists j:\ \bar c_j < 0$ **e** $\bar A_j \le 0$ → **illimitato inferiormente**, stop.
> 3. Altrimenti ($\exists j:\ \bar c_j < 0$ con qualche $a_{ij} > 0$) → la SBA è ammissibile ma non ottima: si itera.

>[!Note] Cambio di base — regola dell'angolo minimo
> - **Entra** $x_j$ con $\bar c_j < 0$ (aumentarla riduce il costo).
> - **Esce** la variabile in base $x_{B[k]}$ dove $k = \arg\min\limits_{i:\ a_{ij} > 0} \dfrac{\bar b_i}{a_{ij}}$ (rapporto minimo, per restare nel poliedro). Le variabili in base devono restare $\ge 0$.
> - Si ottiene la nuova base $B = \{B[1],\dots,B[k-1], j, B[k+1],\dots,B[m]\}$.

### Le due fasi
- **Fase 1**: trovare una **base ammissibile iniziale**, o dimostrare che **non esiste** (problema inammissibile).
- **Fase 2**: semplice iterazione del simplesso fino all'ottimo o all'illimitatezza.

>[!Note] Fase 1 e problema artificiale
> Se nella matrice $A$ **non** si "nasconde" una sottomatrice identità da cui partire, si introduce il **problema artificiale** con variabili artificiali $\varphi$:
> $$\min \sum_{i=1}^{m} \varphi_i, \qquad A x + I\varphi = b,\ x, \varphi \ge 0$$
> Proprietà: il PA **non è mai inammissibile** (ammette la base artificiale), **non è illimitato** ($\sum \varphi_i \ge 0$), e le sue soluzioni sono in **corrispondenza biunivoca** con quelle del problema originale.
> - Se il PA ha ottimo di **costo nullo** ($\varphi^* = 0$) → il problema originale è **ammissibile**.
> - Se il PA ha ottimo di costo **$> 0$** → il problema originale è **inammissibile**.

>[!tip] Matrice CARRY (versione efficiente)
> Invece di ricalcolare $A_B^{-1}$ a ogni iterazione, si mantiene una matrice **(m+1)×(m+1)** "CARRY" che raccoglie $\bar b$, $-\bar y^T$, $\bar z$, $A_B^{-1}$. L'aggiornamento si fa con una **sola operazione di pivot** sull'elemento $a_{kj}$. È la forma compatta usata in pratica.

>[!Important] Pivot, Gauss e inversa
> Il cambio di base si esegue come **eliminazione di Gauss** / **operazione di pivot**: si moltiplica la riga $k$ per un fattore e la si somma alle altre per azzerare la colonna $j$. L'inversa di una matrice quadra si calcola con Gauss sulla matrice a blocchi $[A \mid I] \to [I \mid A^{-1}]$.
> - Solo le matrici **quadrate** hanno determinante e sono invertibili.
> - Se non si ottengono **scalini su tutte le colonne** → rango non massimo → **non invertibile** (non è una base valida).

### Problema della degenerazione e anti-ciclo
Un'**SBA degenere** è una base con **una o più componenti nulle** in $x_B$ (cioè $\bar b_i = 0$). In fase di angolo minimo si può avere rapporto $= 0$: si fa un **pivot degenere** e la **base cambia ma la SBA resta la stessa** → rischio di **ciclare** all'infinito. Se tutte le iterazioni sono non degeneri, la funzione obiettivo **decresce strettamente** e non si rivede mai la stessa base.

Esistono **regole anti-ciclo** deterministiche:
- **Perturbazione**: se $\bar b_k = 0$, si perturba temporaneamente ponendo $\bar b_k = \varepsilon > 0$ (base non degenere), poi si ricalcola $b$ corretto.
- **Regola di Bland (minimo indice)**: entra la variabile con costo ridotto negativo di **indice minimo**; tra le uscenti candidate a rapporto minimo esce quella di **indice $B[k]$ minimo**. Elimina ogni scelta arbitraria.

>[!tip] Interpretazione geometrica del simplesso
> Algebraicamente il cambio di base sposta da una SBA alla **adiacente**; geometricamente si cammina da un **vertice** del poliedro a un **vertice vicino** lungo uno spigolo, migliorando il costo. La **retta isocosto** si "appoggia" ai vertici man mano che l'ottimo migliora.
