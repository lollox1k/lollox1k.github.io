# Formula di Stirling
$$
\lim_{N\to\infty} \frac{N!}{N^Ne^{-N}\sqrt(2\pi N)} = 1
$$
### Dim 
$N! = \Gamma(N+1)$
$$
\Gamma(t) = \int_0^\infty z^{t-1} e^{-z}dz
$$
$$
\Gamma(N+1) = \int_0^\infty z^N e^{-z}dz = \int_0^\infty e^{-(-N\ln{z}+z)}dz
$$
Uso l'approssimazione di picco. Il massimo della funzione all'esponente si ha per $z = N$. La derivata seconda vale $N$
$$
\lim_{N\to \infty} \frac{N^Ne^{-N}\sqrt{2\pi N}}{\Gamma(N+1)} = 1
$$
$\square$


E' un'approssimazione asintotica della funzione gamma:
$$
\Gamma(t) \sim (t-1)^{(t-1)}e^{-(t-1)}\sqrt{2\pi (t-1)}
$$
ovviamente posso ignorare i $-1$.