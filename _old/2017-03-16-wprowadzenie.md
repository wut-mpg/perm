---
layout: task
title: Układy równań
category: lab
lab: 2
task: 1
brief: Rozwiązywanie układów równań liniowych
---

## Rozwiązywanie układów równań liniowych

Należy stworzyć macierz:

$$
\mathbf{A}=\left( \begin{matrix}
1 & 2 & 3 \\
4 & 10 & 6 \\
7 & 8 & -2
\end{matrix} \right)
$$

oraz wektor \\( \mathbf{b}=[1,5,8] \\), a następnie rozwiązać układ równań liniowych \\( \mathbf{A}\mathbf{x}=\mathbf{b}^\mathsf{T} \\).

## Metoda najmniejszych kwadratów

Używając macierzy \\( \mathbf{A} \\) należy stworzyć macierz \\( \mathbf{B} \\) o postaci:

$$
\mathbf{B}=\left( \begin{matrix}
1 & 2 & 3 \\
4 & 10 & 6 \\
7 & 8 & -2 \\
3 & 12 & -5
\end{matrix} \right)
$$

oraz wektor \\( \mathbf{c}=[1,5,8,6] \\). Rozwiązać równanie \\( \mathbf{B}\mathbf{x}=\mathbf{c}^\mathsf{T} \\) używając metody najmniejszych kwadratów.


