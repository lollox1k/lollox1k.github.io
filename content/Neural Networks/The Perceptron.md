# The perceptron
Abbiamo visto come reti di neuroni [[McCulloch-Pitts neuron]] siano universali, ovvero riescono a rappresentare ogni funzione binaria $M : \{0,1\}^N \mapsto \{0,1\}^K$. Quindi data una funzione, riesco a trovare i parametri dei neuroni tali che la rete replichi perfettamente la funzione. 

Ci poniamo ora il problema dell'apprendimento, ovvero come trovare i pesi "migliori" data una conoscenza parziale della funzione $M$.

## Online learning
Supponiamo di avere una rete "Maestro" ed una "Studente", l'obbiettivo è passare la conoscenza perfetta di $M$ del maestro allo studente, che all'inizio ha pesi random.
![[Pasted image 20221011145159.png]]

La procedura detta **online training**:
1. Si sceglie random una domanda $x \in \Omega$
2. Si confrontano le risposte:
- Se $S(x) = M(x)$ ok
- Se $S(x) \neq M(x)$ si aggiornano i pesi dello studente con una _certa regola_

La questione ora è capire quale regola $\Delta U$ e $\Delta J$ usare:
$$
J' = J + \Delta J \qquad U' = U + \Delta U
$$

## The Perceptron learning rule
A _perceptron_ is defined as a MP neuron which learns according to the following rule for updating its parameters:
- $S(x)=1$ e $M(x)=0$: $\Delta U = 1$ e $\Delta J = -x$ 
- $S(x)=0$ e $M(x)=1$: $\Delta U = -1$ e $\Delta J = x$

La regola è molto semplice: se lo studente ha risposto $1$ invece che $0$, devo abbassare l'argomento della funzione theta, chiamato _local field_ $h$:
$$
h= \sum_{i=1}^N J_ix_i - U
$$
nel caso opposto, lo incremente.

### Teorema convergenza della regola
Se il task è linearmente separabile, allora la procedura _converge in un numero finito di passi_ ad una configurazione stazionaria dove $S(x) = M(x)$ $\forall x \in \Omega$.
