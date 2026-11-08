# Teoria della dualità

>[!Important] Duale simmetrico
>Data la coppia nella forma "min con $\ge$":
>$$
>(P)\quad \min c^T x \;:\; Ax \ge b,\ x \ge 0
>\qquad\Longleftrightarrow\qquad
>(D)\quad \max b^T y \;:\; A^T y \le c,\ y \ge 0
>$$
> Il primale minimizza e ha vincoli $\ge$; il duale massimizza e ha vincoli $\le$. Si possono usare anche le forme "min con $\le$" e "max con $\le$": la costruzione segue la regola sotto.

## Costruzione del duale (regola)

Ogni **vincolo** del primale genera una **variabile** del duale, ogni **variabile** del primale genera un **vincolo** del duale. La matrice $A$ passa a $A^T$; $b$ e $c$ si scambiano di ruolo; $\min \to \max$.

| Primale (problema di minimizzazione) | Duale (problema di massimizzazione) |
|---|---|
| variabile $x_j \ge 0$ | vincolo $\le$ |
| variabile $x_j$ libera | vincolo $=$ |
| variabile $x_j \le 0$ | vincolo $\ge$ |
| vincolo $\ge$ | variabile $y_i \ge 0$ |
| vincolo $=$ | variabile $y_i$ libera |
| vincolo $\le$ | variabile $y_i \le 0$ |

>[!tip] Trucco
> In un problema di **minimizzazione con $\min$**, più variabili positive e vincoli $\ge$ sono "naturali"; se trovi variabili con vincoli $\le$ in un $\min$, moltiplica il vincolo per $-1$ (o usa la tabella) per riportarlo alla forma standard.

***

## Teorema fondamentale della PL

>[!Important] Duale debole (disuguaglianza)
> Se $x$ è ammissibile per $P$ e $y$ è ammissibile per $D$, allora
> $$c^T x \;\ge\; b^T y.$$
> Quindi **ogni valore del primale (min) è maggiorante di ogni valore del duale (max)**. In particolare il primale non può essere illimitato *inferiormente* se il duale è ammissibile, e viceversa.

>[!Important] Duale forte
> Se il primale ammette una soluzione ottima di valore finito $z^*$, allora anche il duale ne ammette una, e i valori coincidono:
> $$z^* = w^* \quad\Longleftrightarrow\quad c^T x^* = b^T y^*.$$
> Serve a *certificare* l'ottimalità: se trovo $x^*$ e $y^*$ ammissibili con **stesso costo**, sono entrambi ottimi.

***

## Condizioni di complementarità (ortogonalità)

>[!Important] Teorema
> Date $x^*$ ammissibile per $P$ e $y^*$ ammissibile per $D$, la coppia è **ottima** se e solo se per ogni indice vale la complementarità:
> $$\big(c_j - y^{*T} A_j\big)\, x_j^* = 0 \quad \forall j, \qquad y_i^*\,\big(A_i x^* - b_i\big) = 0 \quad \forall i.$$
> Cioè: **lo scarto di un vincolo è complementare alla variabile duale associata**, e viceversa.

>[!Note] Come si usa
> - Se una variabile è **in base** ($x_j^* > 0$) ⇒ il vincolo duale associato è **saturo** ($\bar c_j = 0$): serve a ricavare le equazioni per $y$.
> - Se un vincolo del primale **non è saturo** (scarto $> 0$) ⇒ la variabile duale associata è $0$.
> - Se un costo ridotto $\bar c_j > 0$ ⇒ $x_j^* = 0$.
> Per dimostrar l'ottimalità: imposta il sistema dato dai vincoli saturi, trova $y^*$ **ammissibile per il duale**, e verifica la complementarità → entrambi ottimi.

>[!CAUTION] Attenzione a chi deve annullarsi
> Nel sistema di complementarità non tutte le $y_i$ si annullano: si annullano quelle i cui vincoli primari *non* sono saturi; le altre possono essere $\ne 0$ e si determinano dal sistema.

***

## Interpretazione economica del duale (prezzi ombra)

Il **duale** attribuisce un **prezzo implicito** (o *ombra*) a ogni vincolo/risorsa del primale. I valori $y_i^*$ sono il **prezzo unitario** della risorsa $i$.

>[!Note] Esempio "concimi" (primale = agricoltore, duale = produttore)
> - **Primale**: l'agricoltore *minimizza* il costo dei composti in commercio ($xc_G, xc_F, \dots$) comprando quantità che garantiscono almeno i nutrienti $N, P$ richiesti. Ogni vincolo è il contenuto di $N$ e di $P$.
> - **Duale**: il produttore *massimizza* il ricavo dalla vendita dei nutrienti $y_N, y_P$. I vincoli impongono che per **ogni** composto in commercio il valore dei nutrienti che contiene **non superi** il suo prezzo ("nessun composto conviene": se il produttore chiedesse troppo, comprerei il composto al mercato).
> Quindi $y^*$ sono i prezzi massimi sostenibile dei nutrienti, e l'uguaglianza forte dice che al minimo di spesa l'agricoltore paga esattamente il valore dei nutrienti.

>[!Important] Prezzi ombra e risorse
> $y_i^*$ = aumento ottimale del costo (o del valore) per una variazione **unitaria** di $b_i$: se il vincolo $i$ non è attivo ($y_i^* = 0$), quella risorsa è "a buon mercato" e più disponibilità non cambia la soluzione.

***

## Analisi di sensitività

Domanda tipica: *la soluzione ottima di base cambia se modifico un dato?*

>[!Note] Perturbazione del **costo** $c_j$ (variabile fuori base)
> Modifico $c_j$ di un incremento $\delta$. La base ottima **resta ottima** se il **costo ridotto** della variabile resta $\ge 0$, cioè se
> $$\bar c_j + \delta \ge 0 \quad\Longleftrightarrow\quad \delta \ge -\,\bar c_j.$$
> Se la perturbazione supera questa soglia, la variabile conviene entrare in base → nuova soluzione.
> *Esempio tipico*: conviene comprare una risorsa "scontata" del $50\%$? Si confronta lo sconto con il **costo ridotto** della variabile associata: se anche scontata il costo ridotto resta $\ge 0$, **non conviene** e la base non cambia.

>[!Note] Perturbazione del **termine noto** $b_i$
> Cambiando $b$, la matrice di base non cambia: basta ricalcolare $\bar b = A_B^{-1} b$. La base **resta ottima** se è ancora **ammissibile**, cioè se
> $$\bar b \ge 0.$$ 
> Se una componente diventa $<0$ l'ammissibilità (e quindi l'ottimalità) si perde → serve il **duale**/*dual simplex* per riottenere fattibilità.

>[!tip] Strategia d'esame
> Non risolvere tutto da capo: sfrutta **la base ottima già trovata**.
> - Sensitività sui **costi** → controlla i **costi ridotti**.
> - Sensitività su **$b$** → controlla l'**ammissibilità** ($\bar b \ge 0$).
> - Sensitività e verifica di ottimalità → **condizioni di complementarità**.

***

## Riepilogo

| Concetto | Enunciato breve |
|---|---|
| Duale simmetrico | $\min c^Tx: Ax\ge b, x\ge0 \iff \max b^Ty: A^Ty\le c, y\ge0$ |
| Duale debole | $c^Tx \ge b^Ty$ per ogni coppia ammissibile |
| Duale forte | ottimo finito primale ⇒ ottimo duale e valori uguali |
| Complementarità | $(c_j - y^TA_j)x_j=0$, $y_i(A_ix-b_i)=0$ |
| Prezzi ombra | $y_i^*$ = valore implicito della risorsa $i$ |
| Sensitività costi | base invariata se $\bar c_j + \delta \ge 0$ |
| Sensitività $b$ | base invariata se $\bar b = A_B^{-1}b \ge 0$ |
