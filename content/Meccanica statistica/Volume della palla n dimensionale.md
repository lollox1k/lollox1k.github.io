# Volume della palla n dim
$$
Vol(B_r) = \frac{(2\pi)^{N/2}}{\Gamma(N/2+1)}R^N \qquad Sup(B_r)= \frac{(2\pi)^{N/2}}{\Gamma(N/2)}R^{N-1}
$$
### Dim 
Primo fatto: 
$$
V = C_NR^N \qquad S = C_N' R^{N-1}
$$
Dobbiamo trovare la costante $C_N$.

Derivando:
$$
C_N' = NC_N
$$
Trucco incredibile: _integrale gassiano n dim_:
$$
(2\pi)^{N/2} = \int_{-\infty}^\infty e^{-\sum_i^n x_i^2}
dx = \int_0^\infty e^{-\rho^2} C'_n \rho^{n-1}d\rho$$
$$
C_n' = \frac{(2\pi)^{N/2}}{\Gamma(N/2)}
$$
Per il volume quindi:
$$
C_n = \frac{C_n'}{N} = \frac{(2\pi)^{N/2}}{N\Gamma(N/2)} = \frac{(2\pi)^{N/2}}{\Gamma(N/2+1)}
$$
$\square$

