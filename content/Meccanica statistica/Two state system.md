# Two state system

Uno dei modelli più semplici da studiare della meccanica statistica, utile come controllo, per verificare l'equivalenza degli ensemble nel limite termodinamico. 

## L'hamiltoniana 
L'insieme degli stati è definito come $\Omega_N = \{-1,1\}^N$, l'hamiltoniana
$$
\mathcal{H}(\sigma) = h\sum_{i=1}^N \sigma_i
$$
l'energia è semplicemente:
$$
h \left( \# \text{ spin in su} - \# \text{ spin in giù} \right)
$$
avrà quindi valori in $\{-Nh + 2kh \; | \; k = 0,\dots N\}$.

Fissata un'energia $E$, corrispondono ad essa:
$$
\binom{N}{ \frac{E/h+ N}{2}}
$$
Possiamo calcolare l'entropia microcanonica, passando al logaritmo. Siccome siamo iteressati al limite termodinamico, usaimo la [[Formula di Stirling]]. Per semplcità assumiamo $h=1$.
Definisco l'energia per particella $E = eN$, e la quantità $\alpha = \frac{1+e}{2}$.
$$
S(E) = N(1-\alpha)\ln(1-\alpha) - N\alpha \ln \alpha - N + N\alpha -N(1-\alpha)\ln(N(1-\alpha)) +N(1-\alpha)
$$
passando all'entropia per particella $s(e) := \frac{S(E)}{N}$ 
$$
s(e) = -\frac{(1+e)}{2}\ln\frac{(1+e)}{2} - \frac{(1-e)}{2}\ln\frac{(1-e)}{2}
$$
