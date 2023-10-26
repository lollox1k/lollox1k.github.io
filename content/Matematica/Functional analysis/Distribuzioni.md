# Definizione
Per definire la [[Weak deriative|derivata debole]], abbiamo integrato una funzione localmente integrabile $f \in L^1_{loc}(\Omega)$ con una funzione test $\psi \in C^{\infty}_{cpt}(\Omega)$. Possiamo interpetare questa procedura come una funzionale definito dalla $f$ che manda $C^{\infty}_{cpt} \to \mathbb{R}$
$$
\psi \mapsto \int_\Omega f \psi d^nx
$$
Una _distribuzione_ su $\Omega \subset \mathbb{R}^n$ è un funzionale generale, non necessariamente rappresentabile in forma integrale, es. _[[Delta di Dirac]]_ $\delta_x$ :
$$
\delta_x[\psi] = \psi(x)
$$
ovviamente non vogliamo tutti i funzionali, ma quelli _lineari_, per avere uno spazio vettoriale e _continui_.
Lo spazio delle distribuzioni è quindi il _duale delle funzioni test_, con somma e prodotto per scalare definiti nella maniera ovvia, Swartz indicava $C^{\infty}_{cpt}$ con il simbolo $\mathcal{D}$ , quindi il suo duale:
$$
\mathcal{D}'(\Omega)
$$
Siccome ogni funzione localmente integrabile definisce la relativa distribuzione mediante l'integrale, è evidente che vale l'inclusione:
$$
L^1_{loc}(\Omega) \subset \mathcal{D}'(\Omega)
$$
dove abbiamo commesso un abuso di notazione (le funzioni ed i rispettivi funzionali integrali). In generale _ad ogni funzione in L^p si può associare una distribuzione_ (integrale).

### Convergenza e continutà
Prima dobbiamo definire la convergenza nello spazio di partenza, le funzioni test. Siano $\psi \in C^{\infty}_{cpt}(\Omega)$ , $\{\psi_k\}_{k \in \mathbb{N} }\subset C^{\infty}_{cpt}(\Omega)$, diciamo che la successione converge  
$$
\psi_k \to \psi 
$$
se e solo se il supporto di tutte le $\psi_k$ è contenuto in un insieme compatto $K\subset \Omega$ e le funzioni e tutte le derivate parziali convergono uniformemente in $K$.

Definiamo quindi la continuità come al solito. La distribuzione $u$ è continua se data una successione tale che $\psi_k \to \psi$, vale:
$$
\lim_{k\to\infty}(u,\psi_k) = (u,\psi)
$$
abbiamo introdotto la notazione comune $(u,\psi) := u[\psi]$.

### Derivate distribuzionali
Definiamo in maniera praticamente uguale alle [[Weak deriative|derivate deboli]]l e derivate di una distribuzione:
$$
(D^\alpha u,\psi) := (-1)^{|\alpha|}(u,D^\alpha \psi)
$$
ben definito perchè è una mappa lineare e continua.
##### Osservazioni
Le derivate deboli non sempre esistono, mentre quelle distribuzionali esistono sempre, $\psi$ sono $C^\infty$!!!.
Data la somiglianza spesso i termini derivata debole e distribuzionale vengono usati come sinonimi, ma sono cose diverse! (spazi diversi), infatti la derivata debole (quando esiste) è rappresentata da una funzione localmente integrabile, cosa non sempre vera per le distibuzioni.



