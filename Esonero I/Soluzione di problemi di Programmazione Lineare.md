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
