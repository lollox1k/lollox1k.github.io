# Filtrazione 
Una filtrazione di uno spazio di probabilità $(\Omega, \mathcal{F},\mathbb{P})$ è una famiglia di sigma algebre totalmente ordinate per inclusione, indicizzate con un insieme di indici totalmente ordinato $I$.
$$
\mathbb{F} := (\mathcal{F_i})_{i \in I} \qquad \mathcal{F_i} \subseteq \mathcal{F_j} \quad i \leq j 
$$

# Filtrazione naturale di un processo stocastico
Sia $(\Omega, \mathcal{A}, \mathbb{P})$ una spazio di probabilità, ed $(I,\leq)$ un insieme di indici totalmente ordinato; sia $(S,\Sigma)$ uno spazio misurabile, sia $X : I \times \Omega \mapsto S$.  La **filtrazione naturale** $\mathcal{F}_i^X$ del processo stocastico $X$ al tempo $i$:
$$
\mathcal{F}^X_i := \sigma\{ X_j^{-1}(A) \,|\, j \leq i, A \in \Sigma\}
$$
> è la più piccola sigma algebra che contiene tutte le preimmagini dei misurabili per tempi $j$ "fino" ad $i$.

# Processo stocastico prevedibile
Un processo stocastico si dice **prevedibile** se $X_i \in \mathcal{F}_i$ $\forall i \in I$.

### Proposizione
$$
X_i \in \mathcal{F}_{i-1} \iff X_i = f(X_1,\dots, X_{i-1}) 
$$
ovvero se è una funzione (deterministica) misurabile delle precedenti
1. VEDI
https://math.stackexchange.com/questions/3131221/what-is-meant-by-a-filtration-contains-the-information-until-time-t
