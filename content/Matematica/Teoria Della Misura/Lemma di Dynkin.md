## Lemma di Dynkin
Anche chiamato delle classi monotone, mostra come
Sia $\mathcal{I}$ un $\pi$ sistema su $S$ _contenente $S$_. Allora:
$$
d(\mathcal{I}) = \sigma(\mathcal{I})
$$
dove con $d(\mathcal{I})$ si intende il $d$ sistema generato dal $\pi$ sistema $\mathcal{I}$.
**Dim**
Per l'osservazione precedente, basta dimostrare che $d(\mathcal{I})$ è un $\pi$-sistema. Infatti se è anche chiuso per intersezioni finite, è una $\sigma$ algebra, ed è la più piccola perchè $d(\mathcal{I}) \subseteq \sigma(\mathcal{I})$.
1. Sia $\mathcal{D}_1 := \{ B \in d(\mathcal{I}) \,:\, B\cap C \in d(\mathcal{I}), \, \forall C \in \mathcal{I}\}$ ovvero tutti gli insiemi del $\lambda$ sistema che intersecati con i membri del $\pi$ sistema rimangono nel $\lambda$ sistema. Siccome $\mathcal{I}$ è un $\pi$ sistema, $\mathcal{I} \subseteq \mathcal{D}_1$ .
Facciamo vedere come $\mathcal{D}_1 \subseteq d(\mathcal{I})$ erediti la struttra di $d$-sistema:
- $S \in \mathcal{D}_1$, infatti $S \in \mathcal{I}$ e $S \cap C = C$ $\forall C$, essendo l'identità.
- Siano $B_1,B_2 \in \mathcal{D}_1$ con $B_1 \subseteq B_2$, vale la chisura per differenza:
$$
(B_2 \setminus B_1) \cap C = (B_2 \cap C) \setminus (B_1 \cap C) \quad \forall C \in \mathcal{I} 
$$
ma $(B_1\cap C)$ e $(B_2 \cap C)$ sono dentro al $d$-sistema, quindi anche la loro differenza lo è (ovviamente continua a valere l'inclusione), quindi $B_2\setminus B_1 \in \mathcal{D}_1$.
- Sia $(B_n)_{n \geq 1} \subseteq \mathcal{D}_1$ e $B_n \uparrow B$ , allora per $C \in \mathcal{I}$:
$$
(B_n \cap C) \uparrow (B\cap C)
$$
in quanto il limite è l'unione, che fattorizza con le intersezioni. Quindi $(B_n \cap C) \in d(\mathcal{I})$ e $B \in \mathcal{D}_1$. 
Abbiamo dimostrato che $\mathcal{D}_1$ è un $d$-sistema che contiene $\mathcal{I}$, quindi $d(\mathcal{I}) \subseteq \mathcal{D}_1$, ma per costruzione $\mathcal{D}_1 \subseteq d(\mathcal{I})$, quindi è proprio lui.
2. Sia $\mathcal{D}_2 := \{B \in d(\mathcal{I})\, : \, B \cap A \in d(\mathcal{I}), \forall A \in d(\mathcal{I}) \}$, ovviamente vale $\mathcal{D}_2 \subseteq \mathcal{D}_1$, e per come è definito è un $\pi$ sistema. Vogliamo far vedere che $\mathcal{I} \subseteq \mathcal{D}_2$ e che eredita la struttra di $d$-sistema.
- $\mathcal{I}\subseteq \mathcal{D}_2$ significa che se prendo $i \in \mathcal{I}$ ed un generico $B \in d(\mathcal{I})$, allora $i \cap B$ rimane in $d(\mathcal{I})$, ma i $B \in d(\mathcal{I})$ che godono di questa proprietà sono proprio gli elementi di $\mathcal{D}_1$ e siccome $\mathcal{D_2} \subseteq \mathcal{D_1}$, vale anche nel nostro nuovo insieme.
Posso dimostrare che eredita l'essere un $d$-sistema come ho fatto per $\mathcal{D}_1$, segue che $\mathcal{D}_2 = d(\mathcal{I})$ che per costruzione è anche un $\pi$ sistema. Quindi è una sigma algebra, contiene $\mathcal{I}$, il fatto che sia la più piccola segue dalla banale inclusione $d(A) \subseteq \sigma(A)$. $\square$