E' possibile rappresentare lo stato del sistema, passando dall' [[Entropia termodinamica]], funzione delle variabili estensive $(U,V,N)$ passando ad una o più di quelle [[Variabili coniugate| coniugate]], sostanzialmente sfruttando la [[trasformata di Legendre]].


### Helmhotz free energy
We want to descrive the system using the variables $(\beta, V, N)$. If our system needs to have constant temperature, it must be allowed to exchange energy with the environment, and thus _is not isolated anymore_. A usefull idea is that we can think of our system beeing in contant with an infinite _thermal reservoir_ at fixed temperature, with which it can exchange energy, but not particles or volume.

Let $S^S(U_S)$ and $S^R(U_R)$ be the respective entropies. Since the system plus the reservoiur are isolated, the total energy is a constant $U_{tot} = U_S + U_R$.
To find the equilibrium energies we need to maximize the total entropy:
$$
S(U_S, U_R) = S^S(U_S) + S^R(U_R) = S^S(U_S) + S^R(U_{tot}-U_S)
$$

Since with our hypotesis $U_s << U_R$, we can Taylor expand the reservoir entropy:
$$
S^R(U_{tot}-U_S) \simeq S^R(U_{tot}) -\frac{\partial S^R(U_R)}{\partial U}U_S = S^R(U_{tot}) -\beta U_S
$$
thus the equilibrium entropy is
$$
S(\overline U_S, \overline U_R) = \sup_U \{S^S(U) -\beta U\}
$$
which is the same as minimizing
$$
\hat F(\beta) = \inf_U \{\beta U -S^S(U)\}
$$
The themordynamic potential defined as
$$
F(\beta, V, N) := T \hat F(\beta, V, N)
$$
is called **Helmhotz free energy**. (The $T$ factor is due from conventions).

Since it's basically a Legendre transform, which is involutive, it contains all the information contained in the entropy.

The infimum is obtained at $\frac{\partial S}{\partial U} = \beta$, so that we can invert and write $U(T)$ 
$$
F(T,V,N) = T \hat F\left(\frac 1T,V,N\right) = U(T,V,N) -S(U(T,V,N), V, N)
$$

which is the familiar 
$$
F = U - TS
$$

**Properties** It shares similar properties of the entropy:
- is _convex_ in the extensive variables ($N,V$)
- and _concave_ in $\beta$ 
**Proof** linear minus concave is a convex function inf of convex function is convex, concavity follows from the inf definition. $\square$


**Thermodynamic stability** 
Like the entropy the derivatives of $F$ are physical quantities of interest.
$$
\left(\frac{\partial F}{\partial V} \right)_{\beta,N} = -p
$$
from this follows a conforting fact:
$$
\left(\frac{\partial p}{\partial V} \right)_{\beta,N} = \left(\frac{\partial^2 F}{\partial V^2} \right)_{\beta,N} \leq 0
$$
since $F$ is convex w.r.t. $V$. If this quanty where $> 0$, we are in trouble...


### The Grand potential
We can go further, and use the set of variables $(\beta, V, \mu)$. Now we allow our system to also exchange particles with the reservoir. Again with the hypotesis $N_S << N_R$ we can approximate
$$
\hat F^R(\beta, N_{tot}-N_S) \simeq \hat F^R(\beta, N_{tot}) -\frac\mu T N_S, \quad \frac{\partial \hat F}{\partial N} = \frac \mu T
$$
to find the equilibrium number of particles we minize the free energy:
$$
\hat F (\beta, \overline  N_S, \overline N_R) = \inf_N \{ \hat F^S(\beta, N) -\frac\mu T N\}
$$
but using the definition of the free energy this is the same as
$$
\hat\Phi(\beta, V,\mu) := \inf_{U,N} \left\{ \beta U -\frac\mu T N -S(U,V,N) \right\}
$$
again we define the **Grand potential** as
$$
\Phi(T,V,\mu) := T \hat \Phi\left(\frac 1 T, V, \mu\right)
$$
as before 
$$
\Phi = U -\mu N -TS
$$
one cool fact: since $\Phi$ is linear in the only extensive variable left, $V$, it has the simple form of 
$$
\Phi = -pV
$$
an easy consequence of the [[Variabili coniugate|Euler relation]] $TS = U + pV -\mu N$.

