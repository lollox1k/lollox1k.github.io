# Teorema di Weierstrass
Sia dato un problema di minimo $MIN(C,f)$, con l'insieme ammissibile $C$ compatto ed $f$ continua. Allora l'insieme della soluzioni $SOL(C,f)$ del problerma è non vuoto e compatto.

Come preliminare, ricordiamo che per L'[[Assioma di Dedekind]] ogni sottoinsieme non vuoto limitato inferiormente ammette un estremo inferiore. Se supponiamo di usare la retta estesa, allora non dobbiamo preoccuparci che sia limitato inferiormente: se siamo in questo caso, l'estremo inferiore è $-\infty$.

Inoltre uno spazio metrico è compatto se e solo se è sequenzialmente compatto (data ogni successione si può estrarre una convergente).

Per le proprietà di estremo inferiore (il massimo dei minoranti) posso sempre costruire una successione di punti in $C$ che converge all'estremo inferiore:
$$
\lim_{n\to\infty}f(x_n)=\inf_{x\in C}f(x)
$$
Per Dedekind, eisiste l'estremo inferiore, chiamiamolo $\overline f$.

## Dim
Facciamo vedere che è non vuoto. Poniamo $\overline f = inf_{x\in C} f(x)$, l'estremo inferiore di $f$. Esiste una successione di punti in $C$ tale che:
$$
\lim_{k\to\infty}f(x_k) = \overline f
$$
Siccome $C$ è compatto, è sequenzialmente compatto, quindi esiste una sottosuccessione convergente ad un punto $\overline x \in C$, e per continuità:
$$
\lim_{k\to\infty} f(x_k) = f(\overline x) = \overline f
$$
che è quindi soluzione ottima $\overline x \in SOL(C,f)$.
La compattezza segue banalmente dal fatto che un sottoinsieme chiuso di un compatto è compatto, infatti $SOL(C,f)\subseteq C$. $\square$ (la chiusura segue dalla [[Esistenza delle soluzioni ottime#Esistenza delle soluzioni ottime#Proposizione 1|Proposizione 1]]).
