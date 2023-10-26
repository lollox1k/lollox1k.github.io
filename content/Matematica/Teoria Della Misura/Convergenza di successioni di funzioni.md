# Convergenza di successioni di funzioni
## Convergenza puntuale q.o
Diciamo che si ha _convergenza quasi ovunque_ $f_n \to f$ q.o. Se si ha convergenza puntuale a meno di insiemi di misura nulla, ovvero $\forall x \in E$ con $\mu(E^c) =0$ si ha:
$$
\forall \epsilon > 0, \, \forall x \in E,\, \exists N \text{ t.c. } \quad |f_n(x)-f|< \epsilon \quad \forall n \geq N 
$$
## Convergenza in misura
Diamo che la successione $f_n \xrightarrow{\mu} f$ _converge in misura_ se:
$$
\lim_n \mu(|f_n-f|> \epsilon) = 0
$$
### Convergenza puntuale implica convergenza in misura

Definiamo gli insiemi:
$$
R_n := \{x \in \Omega \,\vert\, |f_n(x)-f(x)| > \epsilon \}
$$
quindi la definizione di convergenza in  misura può essere scritta come:
$$
\lim_n \mu(R_n) = 0
$$
Consideriamo il $\limsup$ di questa successione:
$$
R := \limsup_n R_n
$$
e dal [[Lemma di Fatou]] inverso
$$
\mu(\limsup_n R_n) \geq \limsup_n \mu(R_n)
$$

l'osservazione chiave è $E \cap R = \emptyset$, ovvero se un punto appartiene all'insieme dove abbiamo convergenza puntuale, non può essere nel limsup, infatti  $x \in R$ significa che per ogni $n$ esiste un $m\geq n$  tale che $|f_m(x)-f(x)| > \epsilon$, quindi $x \notin E$. Quindi $R \subseteq E^c$, e per monotonia della misura (assumiamo sia completa) $\mu(R) = 0$, quindi:
$$
0 \geq \limsup_n \mu(R_n) = \limsup_n \mu(|f_n-f|>\epsilon) \qquad \square
$$
> il limsup è infinitamente spesso i.o., ovvero avrò sempre degli m tali che ho l'evento $|f_m(x)-f(x)| > \epsilon$


### Il vicevera non vale:
**Controesempio**

Definiamo una successione che fa avanti e dietro:
$$
f_{nk}(x) = \mathbb{1}_{\left[\frac{k}{2^n}, \frac{k+1}{2^n}\right]}(x) \qquad 0 \leq k \leq n
$$
**Oss** possiamo estrerre una sottosuccessione che convergente anche quasi ovunque, basta prendere $f_n0$. Questa cosa è vera in generale. Convergenza in misura implica l'esistenza di una sottosuccessione estratta convergente quasi ovunque.

## Convergenza in Norma-p
Diciamo che $f_n \xrightarrow{\Vert \cdot \Vert^p} f$ se la differenza della norma $p$ tende a zero:
$$
\lim_n \Vert f_n -f \Vert_p = \left(\int |f_n-f|^pd\mu \right)^{\frac{1}{p}} = 0
$$
### Convergenza in norma implica convergenza in misura
Si sfrutta la monotonia delle  norme $p$:
$$
\Vert f_n-f\Vert_p \geq \Vert f_n-f \Vert_1 = \int_\Omega |f_n-f|d\mu 
$$
ora partizioniamo $\Omega$ con gli insieme di reso usati prima:
$$
R_n :=\{x \in \Omega\,|\, |f_n(x)-f(x)|> \epsilon\} \qquad \lim_n \mu(|f_n-f|> \epsilon) = \lim_n \mu(R_n)
$$
Quindi in questi insiemi possiamo minorare la funzione integranda con $\epsilon$, e per monotonia dell'integrale di Lebesgue:
$$
\int_\Omega |f_n-f|d\mu \geq \int_{\Omega \setminus R_n} |f_n-f|d\mu + \epsilon \mu(R_n) \geq \epsilon \mu(R_n) \quad \forall \epsilon > 0
$$
Passando al limite ottengo la tesi. $\square$


