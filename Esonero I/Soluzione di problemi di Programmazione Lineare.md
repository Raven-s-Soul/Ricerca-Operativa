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
