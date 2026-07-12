# Formulazione di tipici problemi di ottimizzazione

## Problemi di formulazione

### Miscelazione (Mixing)

>Cos'è: Hai degli ingredienti grezzi e devi miscelarli per ottenere un prodotto finale che rispetti certe percentuali (es. un mangime, un concime, una lega metallica) al costo minimo.
>
>La Variabile: xj​ = quantità (es. kg o litri) dell'ingrediente j da mettere nel mix.
>
>Esempio super semplice: Devi fare un concime mescolando le sostanze A e B.
>
>     Vincolo tipico: (Azoto in A ⋅ xA​) + (Azoto in B ⋅ xB​) ≥ Azoto minimo richiesto.
>
>La trappola: Attenzione se ti chiede "caratteristiche medie". In quel caso non usare le frazioni, ma moltiplica il denominatore e portalo a destra del vincolo.


Aggiungere gli errori in difetto e in eccesso esempio
```math
\begin{cases}
33 x + 70y + 80z + 100w + E1 - E2 = \text{Valore 1}\\
33 x + 30y + 20z + 50w + E3 - E4 = \text{Valore 2}\\
...
\end{cases}
```
$$
\begin{gather}
\text {Dove} \quad E1 \quad \text {e} \quad E3 \quad \text {sono errori in difetto} \\
\text {Dove} \quad E2 \quad \text {e} \quad E4 \quad \text {sono errori in eccesso}
\end{gather}
$$

***

### Allocazione di risorse (Produzione)

>Cos'è: Hai risorse limitate in magazzino (ore di lavoro, metallo, plastica) e devi decidere cosa fabbricare per massimizzare il profitto.
>
>La Variabile: xj​ = numero di unità del prodotto j da fabbricare.
>
>Esempio super semplice: Produci Vasi (x1​) e Piatti (x2​).
>
>     Vincolo tipico: (Ore per fare un vaso ⋅ x1​) + (Ore per fare un piatto ⋅ x2​) ≤ Ore totali dei tuoi operai.
>
>La trappola: Leggere bene se il testo dice che una macchina fa la cosa A "oppure" la cosa B. In quel caso la variabile diventa "ore dedicate a fare quella cosa" (es. xA1​,xA2​).

***

### Gestione delle scorte

>Cos'è: A differenza di Miscelazione o Allocazione (dove decidi cosa fare in un singolo istante), qui il tempo è il fattore critico. Devi pianificare la produzione su più periodi (es. mesi, settimane o stagioni) per soddisfare una domanda
>
>variabile, decidendo se produrre di più oggi e mettere in magazzino (pagando un costo di giacenza) oppure produrre solo il necessario mese per mese.
>
>Le Variabili (Servono due tipi di variabili): In questi problemi non ti basta sapere quanto produci, devi anche tracciare cosa rimane invenduto. Per ogni periodo t avrai:
>
>     xt​ = quantità prodotta nel periodo t.
>     mt​ = quantità di merce messa in magazzino alla fine del periodo t.
>
>La Trappola (L'Equazione di Bilancio): È il cuore assoluto del problema. Non puoi usare i classici vincoli ≤ o ≥. Per ogni periodo t, devi scrivere un'equazione di conservazione della massa che collega ieri, oggi e domani. La formula fissa è:
>
>Magazzino di oggi (mt​) = Magazzino di ieri (mt−1​) + Produzione di oggi (xt​) - Domanda di oggi
>
>La Funzione Obiettivo: Solitamente cerchi di minimizzare la somma dei costi di produzione e dei costi di mantenimento in magazzino per tutti i periodi studiati.

***


### Assegnazione

***

### Pianificazione di attività

***

### Il Problema del Trasporto

>Cos'è: Hai dei fornitori (origini) con una certa scorta, e dei clienti (destinazioni) con una certa domanda. Devi spedire la merce pagando il meno possibile.
>
>La Variabile: Qui serve il doppio indice! xij​ = quantità di merce spedita dall'origine i alla destinazione j.
>
>Esempio super semplice: Spedisci letti ospedalieri dal Fornitore 1 all'Ospedale A (x1A​).
>
>I Vincoli (sono sempre di due tipi fissi):
>
>     Tutta la roba che parte dal Fornitore 1 ≤ Scorta del Fornitore 1.
>     Tutta la roba che arriva all'Ospedale A = Domanda dell'Ospedale A.

***

### Taglio ottimo

>Cos'è: Hai dei nastri o fogli standard grandi (es. 5 metri) e devi tagliarli in pezzi più piccoli (es. 60 cm e 150 cm) per soddisfare i clienti, sprecando il minor numero di fogli possibili.
>
>La Variabile (ATTENZIONE!): NON è il numero di pezzi finali! La variabile xi​ indica il numero di fogli grandi tagliati seguendo la "Modalità di taglio" i.
>
>Esempio super semplice:
>
>     Modalità 1: Taglio un foglio da 5m per fare tre pezzi da 150cm (scarto 50cm).
>     Vincolo: (Pezzi da 150cm ottenuti dalla Modalità 1 ⋅ x1​) + (Pezzi ottenuti da altre modalità...) ≥ Pezzi ordinati dai clienti.
