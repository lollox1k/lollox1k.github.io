# Ottimalità vincolata
Diamo una condizione di ottimalità _necessaria_ per un problema di ottimizzazione vincolata, legata al [[Cono Tangente]].

## Teorema
Sia $f : \mathbb{R}^n \to \mathbb{R}$ una funzione differenziabile su $C\subseteq \mathbb{R}^n$ insieme chiuso. Allora se $\overline x \in C$ è un minimo locale, deve necessariamente valere:
$$
\nabla f(\overline x)^Td \geq 0, \qquad \forall d \in T_C(\overline x)
$$
### Dim
Siccome $d \in T_C(\overline x)$, per definizione esistono due successioni tali che:
$$
x^k \to \overline x, \qquad d^k \to d
$$
siccome per ipotesi $\overline x$ è un minimo locale, allora per tutti i $k \geq \overline k$ abbastanza grandi deve valere:
$$
f(\overline x) \leq f(x^k)= f(d^k\tau^k+\overline x)
$$
espando con Taylor attorno a $\overline x$
$$
f(\overline x) \leq f(\overline x)+ \tau^k\nabla f(\overline x)^Td^k + o(|d^k\tau^k|)
$$
divido per $\tau^k$ e passo al limite, ottenendo la tesi. $\square$
