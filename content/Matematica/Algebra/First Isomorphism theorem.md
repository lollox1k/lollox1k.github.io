**Theorem** Let $\phi$ be a homomorphism from a universal algebra $A$ to $B$, let $R \subseteq Ker(\phi)$. Then the function $\overline \phi : [x] \mapsto f(x)$ (where $x$ is any memeber of the equivalence class $[x]$) is a homomorphism of $A/R$ to $B$.
Furthermore, $\overline\phi$ is an isomorphism iff $R=Ker(\phi)$ and $B=\phi(A)$ ($\phi$ is an epi-morphism).

![[Pasted image 20230929160546.png|400]]

**Proof** First note that the mapping $\overline \phi$ is well defined, if $xRy$ then $\phi(x)=\phi(y)$ since $R \subseteq Ker(\phi)$. Let's show that it's an homorphism:
$$
\overline\phi([x] \cdot [y]) = \overline\phi([xy]) = \phi(xy)=\phi(x)\phi(y)=\overline\phi([x])\overline\phi([y]) 
$$

It's also clear that $\overline\phi$ is sujective iff $\phi$ is. If $R = Ker(\phi)$, then $xRy$ iff $\phi(x)=\phi(y)$ (previously we only had left implies right). From this follows that $\overline\phi$ is also injective, so that it's a isomorphism:
$$
\overline\phi([x]) = \overline\phi([y]) \iff \phi(x)=\phi(y) \iff xRy\iff [x]=[y] \quad \square
$$



**Note** The same proof can be extended to an arbitrary $n$-ary operation on $A$, we used binary to simplify notation.