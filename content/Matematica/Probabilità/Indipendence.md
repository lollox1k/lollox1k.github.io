# Indipendenza di sigma algebre
Sotto $\sigma$-algebre $\mathcal{G_1}, \mathcal{G}_2, \dots$ di $\mathcal{F}$ vengono dette *indipendenti* se, quando $G_i \in \mathcal{G}_i$ ($i\in \mathbb{N}$), con indici $i_1,\dots,i_n$ _distinti_, allora vale:
$$
\mathbb{P} (G_{i_1} \cap G_{i_2} \cap \dots \cap G_{i_n}) = \prod_{k=1}^n \mathbb{P}(G_{i_k}) 
$$
**Osservazione** Gli indici distinti sono fondamentali, altrimenti ottengo $\mathbb{P(G)} = \mathbb{P(G)^2}$ che è vero solo per eventi $0,1$.


Da questa seguono le altre defininizioni d'indipendenza:
## Indipendenza di variabili aleatorie
Le v.a. $X_1,X_2,\dots$ sono indipendenti se le loro $\sigma$-algebre generate sono indipendenti.

## Indipendenza di eventi
Stessa cosa ma per le sigma algebre generate dai singoli eventi, ovvero:
$$
\sigma(E) = \{\emptyset, \Omega, E, E^c\}
$$
**Osservazione** E' equivalente a dire che la funzione caratteristica di $E$ sia indipendente (genera la stessa $\sigma$-algebra).


## Indipendenza di sigma algebre tramite pi sistemi
Vale il seguente lemma, siano $\mathcal{I}, \mathcal{J}$ due [[Pi-system]] che generano due sotto $\sigma$-algebre di $\mathcal{G}, \mathcal{H}$ di $\mathcal{F}$. (Quindi devono contenere $\Omega$). Allora $\mathcal{G}$ e $\mathcal{H}$ sono indipendenti se e solo se $\mathcal{I}$ e $\mathcal{J}$ lo sono.

**Dim** 
Supponiamo che $\mathcal{I}$ e $\mathcal{J}$ siano indipendenti, allora fissando $I \in \mathcal{I}$ ottengo due misure su $\mathcal{H}$:
$$
H \mapsto \mathbb{P}(H \cap I)\qquad H \mapsto \mathbb{P}(H)\mathbb{P}(I)
$$
danno la stessa massa ad $\Omega$, ed ovviamente sono in accord sul $\pi$ sistema $\mathcal{J}$, quindi per il [[Lemma di Dynkin]], sono in accordo su tutta la sigma algebra $\mathcal{H}$.

Faccio lo stesso fissando $H \in \mathcal{H}$, concludo. $\square$

**Remark**
Posso estenderlo ad ogni insieme finito di sotto sigma algebre, ripeto $n$ volte il ragionamento.

