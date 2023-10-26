# L'ensemble canonico
Chiamato da Boltzmann "Holode", sono distribuzioni stazionarie con un parametro $\beta$:
$$
\mu(\Delta) := \frac{1}{Z(\beta,V)}e^{-\beta E(\Delta)}, \qquad Z(\beta,V) := \sum_{\Delta}e^{-\beta E(\Delta)}
$$
Boltzmann dimostrò la proporzionalità di $\beta$ con $T(\mu)^{-1}$ e l'ortodicità dell'ensemble.

# Ortodicità
Cominciamo con l'approssimazione:
$$
Z(\beta,V) = \iint e^{-\beta K(p)}e^{-\beta \Phi(q)}\frac{dpdq}{N!h^{3N}}
$$
i.e. passiamo al continuo. Le quantità medie sono quindi:
$$
K(\mu)= \int \left( \sum_i^N \frac{p_i^2}{2m}\right)e^{-\beta E(p,q)}dqdp
$$
$$
v = \frac{V}{N}
$$
$$
U(\mu) = \frac{-\partial}{\partial\beta}\log Z(\beta,V)
$$
$$
p = P(\mu) = \sum_Q \frac{N}{Z(\beta,V)} \int_{v>0} e^{-\beta E(p,q)} 2mv^2 \frac{s}{S}dpdq
$$
questo schifo può essere riscritto come:
$$
p = \beta^{-1}\frac{\partial}{\partial V}\log Z(\beta,V)
$$
dettagli del conto qui [[Forma microscopica della pressione]].

Il grosso del lavoro è fatto, definendo l'energia libera come la funzione:
$$
F := -\beta^{-1}\log Z(\beta,V)
$$
e tramite questa l'entropia:
$$
S := \frac{U-F}{T}
$$
dobbiamo varificare la relazione:
$$
du = Tds - pdV
$$
un conto diretto sulla temperatura, definita come proporzionale alll'energia cinetica media rivela che:
$$
T = \frac{1}{k_B \beta}, \qquad \frac{dT}{T} = -\frac{d\beta}{\beta}
$$
calcoliamo il differenziale dell'energia libera:
$$
dF = \left[\beta^{-2}\log Z(\beta,V) + \beta^{-1}U\right]d\beta -\left[\beta^{-1}\frac{\partial_V Z(\beta,V)}{Z(\beta,V)}\right]dV
$$
$$
dF = \left[\frac{F-U}{T}\right]dT-pdV = -SdT-pdV
$$
quindi
$$
dU = d(F+TS) = dF + TdS + SdT = -SdT-pdV + TdS - SdT = TdS - pdV
$$
$\square$

### Remarks
- Indipendente dal limite termodinamico $N,V \to \infty$.
- Definisce l'energia libera termodinamica microscopicamente!

