# Riflettore di Householder

Sia dato un vettore $u \in \mathbb{C}^n$. Vogliamo costruire l'applicazione lineare che proietta rispetto al piano ortogonale al vettore direttore $u$. 

## La matrice di Householder
La matrice di Householder rispetto al vettore $u$ è
$$
U = \mathbb{I} -2\frac{uu^H}{\Vert u \Vert^2 }
$$
### Proprietà
Seguono direttamente dalla definizione:
1. E' involutiva $UU = \mathbb{I}$, ovvero $U^{-1}=U$;
2. E' Hermitiana;
3. E' unitaria;
4. Ha determinante $-1$.

## Proposizione
Dati due vettori $x,y \in \mathbb{C}^n$ con stessa norma, il riflettore rispetto al vettore $x-y$ ha manda $x$ in $y$: $Ux = y$.
**Dim** conti. $\square$

Posso quindi utilizzare per mandare $x$ in un vettore con tutti zeri tranne la prima componente, che dovrà necesariamente essere $e^{i\theta} \Vert x \Vert$.



## Proposizione
Dato $x = (x_1,x_2,...,x_m)^T$ , il riflettore elementare associato al vettore $u = x+\sigma e_1^{(m)}$  dove $\sigma = \Vert x \Vert e^{i\theta}$ con $\theta = \arg{x_1}$,  (dove con $\arg{z}$, per $z \in \mathbb{C}$, $z \neq 0$ si intende l’angolo tra la direzione positiva dell’asse x e il raggio dall’origine a $z$ nel piano $xy$, quindi $-\pi \leq \arg{z} \leq \pi$)  fa sì che:
$$
Ux = -\sigma e_1
$$

>Dato un vettore $v$ è possibile trovare un vettore $u$ tale che il riflettore di householder associato azzera tutte le componenti di $v$ tranne una

**Dimostrazione** Qualche conto. $\square$




