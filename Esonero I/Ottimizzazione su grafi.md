# Ottimizzazione su grafi

>[!Note] Panoramica
>I problemi su grafi in RO sono PL *speciali* con struttura a rete: si risolvono con algoritmi dedicati più efficienti del simplesso. Tre famiglie:
> - **Cammino minimo** → Dijkstra (singola origine), Floyd-Warshall (tutte le coppie).
> - **Albero ricoprente minimo** → Prim(-Dijkstra), Kruskal.
> - **Flusso massimo** → Ford-Fulkerson (e taglio minimo).
>
> ⚠️ All'esame: per Dijkstra e Prim il prof chiede di **mostrare le tabelle iter per iter** (nodo, flag, costo, predecessore $pred$). Prepara più tabelle, non solo il risultato.

***

## Cammino minimo — Dijkstra (versione efficiente)

Problema **singola-origine, multipla-destinazione**: dato un **digrafo pesato**, trovare il cammino di costo minimo da un nodo origine $s$ a tutti gli altri.

>[!Important] Idea e dati per nodo
> Si costruisce a partire da $s$ un **albero dei cammini orientati di costo minimo**. Per ogni nodo si tengono:
> - **costo**: lunghezza del cammino minimo attualmente noto da $s$;
> - **pred**: predecessore sul cammino (per ricostruire il percorso);
> - **flag**: $0$ = provvisorio, $1$ = **fissato** (entrato definitivamente in $S$, l'insieme dei nodi "visitati").
> Ad ogni iterazione si fissa (flag $=1$) il nodo con **costo provvisorio minimo**; $S$ cresce man mano. L'ordine di fissaggio dei nodi è ciò che il prof vuole in tabella.

>[!CAUTION] Cammini minimi ≠ albero ricoprente minimo
> L'**albero dei cammini minimi** (Dijkstra) e l'**albero ricoprente minimo** (Prim) hanno in genere **pesi diversi**: il primo minimizza il costo *da $s$ a ogni nodo*, il secondo la *somma dei lati* per connettere tutti i nodi. Confrontare i due pesi è una domanda d'esame tipica.

>[!tip] Sensitività su un arco (cammino minimo)
> - Se aumento il peso di un arco **che NON è nell'albero dei cammini minimi** → soluzione **invariata**.
> - Se **diminuisco** il peso di un arco non in soluzione → potrebbe **entrare** nella soluzione ottima (va ricontrollato).
> - Se cambio il peso di un arco **che è** nell'albero → la soluzione può cambiare.

***

## Albero ricoprente minimo — Prim(-Dijkstra)

Dato un grafo **non orientato** e pesato, trovare un **albero ricoprente** (connette tutti i nodi, $n-1$ lati, nessun ciclo) di **peso minimo**. Prim è la variante "a regione crescente" simile a Dijkstra.

>[!Important] Come funziona Prim
> Partendo da un vertice scelto, ad ogni iterazione si aggiunge il **lato di peso minimo** che collega un nodo in $S$ a un nodo fuori da $S$; si fissa il flag del nuovo vertice e si registra il **pred** (il nodo da cui è arrivato il lato). Si aggiungono $n-1$ lati.
> $$\text{costo dell'albero} = \sum \text{pesi dei lati scelti}$$

>[!tip] Proprietà e sensitività
> - **Indipendenza dalla radice**: l'albero ricoprente ottimo ha lo **stesso peso** qualunque sia il vertice di partenza (può cambiare la *forma*, non il peso).
> - **Più alberi ottimi**: esistono se ci sono **lati con lo stesso peso** (scelte a pari merito). Il peso è comunque identico.
> - Togliere lati **non** nella soluzione ottima → **nessun cambiamento**.
> - **Diminuire** il peso di un lato può ridurre il peso totale (nuovo albero ottimo con quel lato).

***

## Flusso massimo — Ford-Fulkerson (e taglio minimo)

Rete di flusso con **sorgente** $s$ e **pozzo** $t$. Ogni arco ha una **capacità** massima e porta un **flusso**. Obiettivo: massimo flusso da $s$ a $t$.

>[!Important] Vincoli
> - **Capacità**: $0 \le f(\text{arco}) \le \text{capacità}$.
> - **Conservatività**: per ogni nodo intermedio, **ciò che entra = ciò che esce**. Anche $s$ e $t$ rispettano la conservatività se si somma il flusso che esce/entra con segno; il flusso della rete è il valore $F$ che transita.
> - Un flusso iniziale ammissibile ha tipicamente $F_0 = 0$.

>[!Note] Cammini aumentanti
> Si cerca un **cammino aumentante** (un percorso da $s$ a $t$ con archi non saturi) e si **aumenta** il flusso di $\Delta$. $\Delta$ è l'incremento portato da quella sequenza.
> - Notazione tipica nelle tabelle: la coppia $(A, B)$ indica il flusso $A$ sull'arco **proveniente** dal nodo $B$.
> - $F$ = flusso totale raggiunto, $\Delta$ = aumento dato da quella sequenza.
> - L'**ordine** dei cammini aumentanti può variare, ma **il valore ottimo è lo stesso**.

>[!Important] Taglio minimo = flusso massimo (teorema)
> Quando non esistono più cammini aumentanti, si individua un **taglio** $(S, \bar S)$:
> - $S$ = nodi "raggiungibili/pieni";
> - $\bar S$ = nodi che **non riesco a toccare**;
> - gli **archi del taglio** sono quelli diretti che partono da un nodo in $S$ e arrivano a uno in $\bar S$.
>
> La **somma delle capacità** (o flussi saturi) degli archi del taglio = valore del **flusso massimo**. Il taglio di capacità minima certifica l'ottimalità del flusso.

***

## Cammini minimi tutte le coppie — Floyd-Warshall

Calcola i cammini minimi **fra tutte le coppie** di nodi aggiornando progressivamente due matrici: quella dei **percorsi orientati minimi** e quella dei **predecessori**. Ad ogni *passo $k$* si considera il nodo $k$ come intermedio.

>[!CAUTION] Cicli negativi
> Floyd-Warshall **funziona anche con archi di peso negativo**, *ma* se esiste un **ciclo di peso totale negativo** allora i cammini non sono definiti (si può girare nel ciclo per ridurre a volontà).
> - **Test**: alla fine, se nella **diagonale** compare un valore **negativo**, c'è un ciclo negativo → arrestare l'algoritmo e mostrare il ciclo.
> - Un arco negativo può innescare subito un ciclo negativo (es. arco $(C,B)<0$ che crea il ciclo $B \to C \to B$).

***

## Riepilogo: quando usare cosa

| Problema | Grafo | Algoritmo | Output |
|---|---|---|---|
| Cammino min da $s$ a tutti | orientato pesato | **Dijkstra** | albero dei cammini minimi + ordine nodi |
| Cammino min tutte le coppie | orientato (pesi anche <0) | **Floyd-Warshall** | matrice distanze + predecessori |
| Albero ricoprente min | non orientato pesato | **Prim-Dijkstra** | $n-1$ lati di peso minimo |
| Flusso massimo | rete con capacità | **Ford-Fulkerson** | flusso max + taglio minimo |

>[!tip] Confronto Dijkstra vs Floyd
> - **Dijkstra**: una sola origine, pesi **non negativi**, più efficiente per una sorgente.
> - **Floyd-Warshall**: tutte le coppie, tollera pesi negativi **ma non cicli negativi**.
