# Es di Formulazione

>[!NOTE]
>### Esonero E del 28 Novembre

ESERCIZIO D'ESAME: FORMULAZIONE L’azienda agricola L’orto stellato deve fornire ogni settimana alla Grande Distribuzione Organizzata (GDO) almeno 480 kg carote, 420 kg di zucchine e 260 kg di peperoni. Per ragioni commerciali, la GDO accetta dai suoi fornitori solo cassette da 10 kg che seguono specifici standard di composizione, stabiliti per contratto. Ogni riga della tabella di seguito specifica uno standard accettato:

    Standard 1: 4 kg Carote, 4 kg Zucchine, 2 kg Peperoni
    Standard 2: 5 kg Carote, 2 kg Zucchine, 3 kg Peperoni
    Standard 3: 3 kg Carote, 5 kg Zucchine, 2 kg Peperoni
    Standard 4: 6 kg Carote, 1 kg Zucchine, 3 kg Peperoni

All’orto stellato, la produzione di ogni cassetta costa 0.84 € cad. Scrivere la formulazione per il problema preso in esame in cui vengono minimizzati i costi dell’azienda. Indicare la tipologia di formulazione utilizzata, il significato di ogni variabile e di ogni vincolo inserito.





***
>[!NOTE]
>### Esame_Febbraio26_B 

ESERCIZIO D'ESAME: FORMULAZIONE (Problema di Miscelazione) Un'azienda deve produrre conglomerati bituminosi partendo da 4 componenti in magazzino.

    Inerte calcareo: Costo 28 €/ton, Resistenza 6, Flessibilità 5, Disponibilità 5000 ton
    Inerte basaltico: Costo 35 €/ton, Resistenza 9, Flessibilità 4, Disponibilità 4000 ton
    Fresato riciclato: Costo 18 €/ton, Resistenza 4, Flessibilità 6, Disponibilità 3500 ton
    Legante bituminoso: Costo 90 €/ton, Resistenza 3, Flessibilità 10, Disponibilità 2000 ton

Le miscele destinate alle 3 tipologie di traffico devono rispettare i seguenti vincoli:
```
Pista principale: 
- Servono 4000 tonnellate. 
- Deve avere indici di resistenza e flessibilità medi non inferiori rispettivamente a 7,5 e 5.

Taxiway: servono 3000 tonnellate.
- Deve avere indici di resistenza e flessibilità medi non inferiori rispettivamente a 6,5 e 5,5

Piazzale aeromobili: servono 2500 tonnellate. 
- Deve avere indici di resistenza e flessibilità medi non inferiori rispettivamente a 7,5 e 5.
```
Formulare un modello di Programmazione Lineare minimizzando il costo totale di produzione.

- $i \in \\{C, B, F, L\\}$ (Componenti: Calcareo, Basaltico, Fresato, Legante)
- $j \in \\{P, T, A\\}$ (Miscele: Pista, Taxiway, Piazzale Aeromobili)

Vincoli di Non Negatività:
- $$x_{ij} \ge 0 \quad \forall i \in \\{C,B,F,L\\}, \forall j \in \\{P,T,A\\}$$

$$\min Z = 28 \sum_{j} x_{Cj} + 35 \sum_{j} x_{Bj} + 18 \sum_{j} x_{Fj} + 90 \sum_{j} x_{Lj}$$

$$\min Z = 28(x_{CP} + x_{CT} + x_{CA}) + 35(x_{BP} + x_{BT} + x_{BA}) + 18(x_{FP} + x_{FT} + x_{FA}) + 90(x_{LP} + x_{LT} + x_{LA})$$

$$
\begin{gather}
\text{Vincoli di Domanda} \\
\begin{cases}
x_{CP} + x_{BP} + x_{FP} + x_{LP} = 4000\\
x_{CT} + x_{BT} + x_{FT} + x_{LT} = 3000\\
x_{CA} + x_{BA} + x_{FA} + x_{LA} = 2500
\end{cases}
\end{gather}
$$

$$
\begin{gather}
\text{Vincoli di Disponibilità} \\
\begin{cases}
x_{CP} + x_{CT} + x_{CA} \le 5000\\
x_{BP} + x_{BT} + x_{BA} \le 4000\\
x_{FP} + x_{FT} + x_{FA} \le 3500\\
x_{LP} + x_{LT} + x_{LA} \le 2000
\end{cases}
\end{gather}
$$

La formula generale per una caratteristica è: $\sum (\text{Coefficiente} \cdot x_{ij}) \ge \text{Indice Minimo} \cdot \text{Domanda}_j$

Vincoli di Resistenza (Minima):
- Pista ($\ge 7.5$ per 4000 ton):
   - $$6x_{CP} + 9x_{BP} + 4x_{FP} + 3x_{LP} \ge 7.5 \cdot 4000 \implies 6x_{CP} + 9x_{BP} + 4x_{FP} + 3x_{LP} \ge 30000$$

- Taxiway ($\ge 6.5$ per 3000 ton):
   - $$6x_{CT} + 9x_{BT} + 4x_{FT} + 3x_{LT} \ge 6.5 \cdot 3000 \implies 6x_{CT} + 9x_{BT} + 4x_{FT} + 3x_{LT} \ge 19500$$

- Piazzale ($\ge 7.5$ per 2500 ton):
   - $$6x_{CA} + 9x_{BA} + 4x_{FA} + 3x_{LA} \ge 7.5 \cdot 2500 \implies 6x_{CA} + 9x_{BA} + 4x_{FA} + 3x_{LA} \ge 18750$$

Vincoli di Flessibilità (Minima):
- Pista ($\ge 5$ per 4000 ton):
   - $$5x_{CP} + 4x_{BP} + 6x_{FP} + 10x_{LP} \ge 5 \cdot 4000 \implies 5x_{CP} + 4x_{BP} + 6x_{FP} + 10x_{LP} \ge 20000$$
- Taxiway ($\ge 5.5$ per 3000 ton):
   - $$5x_{CT} + 4x_{BT} + 6x_{FT} + 10x_{LT} \ge 5.5 \cdot 3000 \implies 5x_{CT} + 4x_{BT} + 6x_{FT} + 10x_{LT} \ge 16500$$
- Piazzale ($\ge 5$ per 2500 ton):
   - $$5x_{CA} + 4x_{BA} + 6x_{FA} + 10x_{LA} \ge 5 \cdot 2500 \implies 5x_{CA} + 4x_{BA} + 6x_{FA} + 10x_{LA} \ge 12500$$


***
>[!NOTE]
>### EsoneroA1_Giugno

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
240x_CA + 600x_CB + 1000x_CC \geq 10.000\\
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
