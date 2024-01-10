Vogliamo mappare un'istanza di un problema di decisione ad un'istanza di un altro, $T(A) = B$, con le seguenti proprietà:
1. la conversione avvien in tempo polinomiale 
2. $I_A \iff I_B$ ovvero un'istanza è true se e solo se l'altra lo è

Se è possibile trovare questa rimappattura $T$ diciamo che i problemi sono:
$$
A \leq_p B 
$$
è un ordine parziale, "B è almeno difficile quanto A". 
Idea di Karp 1971. 

Come per gli ordine vale un'equivalenza associata:
se valgono $A\leq_p B$ e $B \leq_p A$ allora $A$ e $B$ sono equivalenti in un senso computazionale.