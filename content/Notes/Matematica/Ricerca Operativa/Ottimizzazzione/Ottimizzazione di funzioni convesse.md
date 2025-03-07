Una classe importantissima di problemi di ottimizzazione è quella dei _problemi
di ottimizzazione convessi_. Un problema $MIN(C, f)$ è detto convesso se $C \subseteq \mathbb{R}^n$ è un insieme convesso è la $f : C → \mathbb{R}^n$ è convessa su $C$.

Intuitivamente le cose sono più semplici se la funzione e l'insieme ammissibile (il dominio dove cerchiamo i punti ottimali) sono convessi/concavi.

### Teorema
Sia $f : K \subseteq \mathbb{R}^n \to \mathbb{R}$ con $f$ e $K$ rispettivamente funzione ed insieme convessi, i punti di minimo _locali_ sono anche _globali_.
In altre parole, non esistono minimi locali che non siano globali.

#### Dim 
Banale per assurdo, supponiamo $x_0$ punto di minimo locale di $f$, ovvero $\exists \epsilon > 0$ t.c. $\forall x \in B_\epsilon(x_0) \cap K$ vale $f(x_0) < f(x)$. Sia $x_G$ il punto di minimo globale, vale $f(x_G) < f(x_0)$. 
Consideriamo la combinazione convessa tra i due punti, segue dalla convessità di $f$:
$$
f(\alpha x_G + (1-\alpha)x_0) \leq \alpha f(x_G) + (1-\alpha)f(x_0)
$$
essendo $\alpha \geq 0$ possiamo maggiorare (strettamente) il termine di destra sostituendo $\alpha f(x_G)$ con $\alpha f(x_0)$:
$$
f(\alpha x_G + (1-\alpha)x_0) < \alpha f(x_0) + (1-\alpha)f(x_0) = f(x_0)
$$
ma scegliendo $\alpha < \epsilon$ siamo all'interno della palla di centro $x_0$ dove è un minimo locale, ed possiamo trovare punti dove la funzione vale meno di $f(x_0)$, contro l'ipotesi iniziale. $QED$ 

Naturalmente vale un risultato analogo per il caso "complementare" dei massimi di funzioni concave:
#### Corollario
Sia $f : K \subseteq \mathbb{R}^n \to \mathbb{R}$ con $f$ e $K$ rispettivamente funzione concava e insieme convessi, i punti di massimo _locali_ sono anche _globali_.

La _stretta convessità_ della funzione obiettivo di un problema di minimizzazione
convessa aggiunge un’ulteriore importante informazione: 
_il problema può avere al più una sola soluzione ottima._
### Teorema
Sia $f : K \subseteq \mathbb{R}^n \to \mathbb{R}$ con $K$ insieme convesso ed $f$ funzione strettamente convessa, allora l'insieme $SOL(C,f)$ del problema di minimo $MIN(C,f)$ o è vuoto o contiene un solo punto.
#### Dim 
Banale, per assurdo: considero due soluzioni ottime $x_1,x_2$, quindi col medesimo valore ottimale $f(x_1) = f(x_2)$; applicando la stretta convessità si ottiene che il punto medio è migliore, contro l'ipotesi:
$$
f\Big(\frac{x_1+x_2}{2}\Big) < \frac{1}{2}f(x_1) + \frac{1}{2}f(x_2) = f(x_1) = f(x_2) \qquad \square
$$
#### Corollario
Come prima segue un risultato analogo per la massimizzazione di funzioni concave.
