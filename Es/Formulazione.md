# Es di Formulazione

> EsoneroA1_Giugno

ESERCIZIO D'ESAME: FORMULAZIONE (Problema di Allocazione/Produzione) Un'azienda di caffè possiede tre macchinari per la tostatura. 
In un'ora di lavoro ogni macchina può produrre una quantità fissa di caffè, e precisamente:

    tostatrice A: 240 kg chiara oppure 190 kg media oppure 120 kg scura;
    tostatrice B: 600 kg chiara oppure 450 kg media oppure 300 kg scura;
    tostatrice C: 1000 kg chiara oppure 750 kg media oppure 600 kg scura.

Il mercato richiede almeno 100 quintali di tostatura chiara, 80 quintali di tostatura media, 60 quintali di tostatura scura. 
I costi orari delle tre macchine sono: 50 euro per la tostatrice A, 90 euro per la tostatrice B, 180 euro per la tostatrice C. 
Scrivere un modello di programmazione lineare per determinare la produzione giornaliera (2 turni da 9 ore ciascuno) di costo minimo

>Trappola 1: La parola "oppure" (Il trucco delle variabili)
>- Se il testo avesse detto "la macchina produce 240 kg chiara E 190 kg media", le tue variabili sarebbero state semplicemente le ore totali di accensione della macchina (xA​,xB​,xC​).
>- Ma il testo dice "oppure". Questo significa che la macchina, in una certa ora, può fare solo una tipologia.
>- Devi quindi "sdoppiare" le variabili per indicare quante ore una specifica macchina dedica a una specifica tostatura.
>- Definiamo xij​ = ore di lavoro della macchina j dedicate alla tostatura i. Avremo quindi ben 9 variabili!
>
>Trappola 2: Le unità di misura La produzione delle macchine è in kg, ma la richiesta del mercato è in quintali. Prima di scrivere i vincoli, devi convertire la domanda:
>
>     100 quintali = 10.000 kg
>     80 quintali = 8.000 kg
>     60 quintali = 6.000 kg
>
>Inoltre, il testo dice che la giornata è divisa in "2 turni da 9 ore ciascuno".
>- Significa che ogni macchina può lavorare al massimo 18 ore al giorno.

$$
\begin{gather}
\text{Variabili di Decisione} \\
\begin{cases}
x_CA + x_MA + x_SA = \text{Ore tostatrice A}\\
x_CB + x_MB + x_SB = \text{Ore tostatrice B}\\
x_CC + x_MC + x_SC = \text{Ore tostatrice C}\\
\end{cases}
\end{gather}
$$

$$
\begin{gather}
\text{Funzione Obiettivo} \\
\text{Min } 50(x_CA​ + x_MA​+x_SA​)+90(x_CB​+x_MB​+x_SB​)+180(x_CC​+x_MC​+x_SC​)
\end{gather}
$$

$$
\begin{gather}
\text{Vincoli di Domanda} \\
\begin{cases}
240x_CA + 600x_CB + 100x_CC \geq 10.000\\
190x_MA + 450x_MB + 750x_MC \geq 8.000\\
120x_SA + 300x_SB + 600x_SC \geq 6.000\\
\end{cases}
\end{gather}
$$

$$
\begin{gather}
\text{Vincoli di Capacità Operativa} \\
\begin{cases}
x_CA + x_MA + x_SA \leq 18\\
x_CB + x_MB + x_SB \leq 18\\
x_CC + x_MC + x_SC \leq 18\\
\end{cases}
\end{gather}
$$

$$
\begin{gather}
\text{Vincoli di Non Negatività:} \\
x_{ij}\geq 0 \implies \forall i \in \{C,M,S\} \quad \text e \quad j \in \{A,B,C\}
\end{gather}
$$
