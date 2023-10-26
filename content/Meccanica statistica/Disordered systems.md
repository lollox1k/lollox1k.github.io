# Disordered systems

Models like [[Modello di Curie-Weiss|Curie-Weiss]] may be too simple to capture the complexity of real solids, for example the couplings may depend on time, be pair depandant (two different molecules) or may be subjected to _noise_.

The key idea is to _make the coupling $J_{ij}$ random variables_, and then to study the typical behaviour of the system average the free energy for all realization of the couplings.

We have two different kind of averages:
- _Annealed_ $f^A := \beta^{-1} \ln \mathbb{E} Z$
- _Quenced_ $f^Q := \beta^{-1} \mathbb{E} \ln Z$

which correspond to two different physical cases
_annealing_: slow cool down to make the system more homogeneous
_quenching_: abrupt cool down to improve solid resistance.

It follow from [[Jensen's inequality]] that the annealed free energy is a lower bound on the quenched.
$$
f^Q \geq f^A
$$
The computation of the annealed free energy is much simpler, since averaging a logarithm is hard. One trick (not rigourus!) is the _replica trick_, which uses the identity
$$
\ln Z = \lim_{n\to\infty} \frac{Z^n-1}{n}
$$
Then instad of computing the average of a logarithm, one computes the $n$-th momenths.
