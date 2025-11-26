# Introduzione alla Ricerca Operativa

<details>
<summary><h2> Il metodo delle 5 fasi </h2></summary>

```mermaid
graph TD
    A[1. Identificazione del Problema] --> B(2. Raccolta Dati)
    B --> C{3. Modello Matematico}
    
    subgraph D[Risoluzione]
        C --> E[Definizione: variabili, vincoli, funzione obiettivo]
        E --> F[4. Soluzione - Algoritmi: Simplesso, Ford-Fulkerson, metodi su grafi]
    end
    
    F --> G{5. Verifica e Analisi}
    
    G -- Soluzione ottima e ammissibile? --> H(Attuazione / Implementazione)
    
    G -- Soluzione non accettabile? --> I[Ridefinizione di vincoli o obiettivo]
    I --> C
    
    G -- Modello non rappresentativo? --> J[Riesame del problema]
    J --> A

```
</details>

>### Attributi di una buona decisione
>- **efficace**: raggiunge lo scopo;
>- **efficiente**: raggiunge lo scopo consumando poche risorse;
>- **tempestiva**: coerente con l’orizzonte temporale del livello decisionale (strategico, tattico, operativo);
>- **robusta**: rimane buona (per lo meno ammissibile) anche in seguito a piccole variazioni nel valore dei dati;
>- **giustificabile**: può essere dimostrata razionale ad altri.
>

## Modello Matematico
$$
\begin{matrix}
\text{Funzione Obiettivo} & \min c^Tx
\\\
\text{Vincoli} & Ax \leq b
\\\
\end{matrix}
\quad \quad
\begin{matrix}
\text{Parametri} & b \in \mathbb{R}^m\\
& A \in \mathbb{R}^{m \times n}\\
& c \in \mathbb{R}^n
\\\
\\\
\text{Variabili} & x \in \mathbb{R}^n
\end{matrix}
$$

