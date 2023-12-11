# Definition
Vogliamo associare ad una funzione con codominio in $\mathbb{R^n}$ un numero reale, il suo integrale (definito).

Si procede costruttivamente, prima definendo l'integrale per una classe di funzioni, le [[Funzioni semplici]], e poi generalizzando con un passaggio al limite per una classe più ampia di funzioni. 

Si comincia ragionando solo su funzioni a valori non negativi $f : E \to [0,\infty]$ 
$$
\int_E f d\mu := sup\Big\{  \int_E \phi d\mu \quad \Big|\quad \phi \text{  semplice, } 0\leq \phi \leq f   \Big\} 
$$
Approssimiamo sempre più $f$ dal basso con funzioni semplici (per questo ci siamo limitati a funzioni non negative). 

In effetti esiste una definizione più esplicita, per ogni funzione misurabile esiste una successione monotona crescente di funzioni semplici che converge puntualmente q.o. alla funzione, quindi è proprio il sup cercato. [[Funzioni misurabili#Successione monotna di funzioni semplici| successione monotona di funzioni semplici]]. Si può vedere come definizione alternativa.


Estendiamo banalmente a funzioni generali separando le parti positive e negative, e facendo la differenza:
$$
\int f d\mu = \int f_+ d\mu - \int f_- d\mu
$$
Dove è chiaro cosa sono $f_+$ e $f_-$ 

#### Funzioni integrabili secondo Lebesgue
Diciamo che $f$ è integrabile secondo Lebesgue su $E$ se entrambi gli integrali della parte positiva e negativa sono finiti. 

Qui c'è una differenza con l'integrale di Riemann, funzioni oscillanti che integrale davano zero, magari qui otteniamo forme indeterminate come $\infty - \infty$. 

Per essere precisi, $f$ è Lebesgue integrabile se e solo se anche $|f|$ lo è, infatti:
$$
|f| = f_+ + f_-
$$

# Properties

> [!proposition]
>**Absolute continuity** Let $f \in L^1(E)$ . Then for all $\epsilon > 0$ there exists a $\delta > 0$ such that
>$$
>\left|\int_E f d\mu\right| < \epsilon
>$$
>whenever $\mu(E) < \delta$.
>> [!proof]-
>> Let $g$ be a simple function, then
>> $$
>> \left|\int_E g d\mu \right| \leq\int_E |g| d\mu \leq \max |g| \mu(E)
>> $$
>> just take $\delta < \frac \epsilon {\max |g|}$. By density and the triangle inequality the claim is true in $L^1(E)$. $\square$


