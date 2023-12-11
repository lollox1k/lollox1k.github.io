> [!theorem] Let $(X, \Vert\cdot\Vert_X)$ a normed space and $(X', \Vert\cdot \Vert_{X'})$ its dual.
> Let $U \subseteq X$, $u' : U \to \mathbb{R}$ a continuous linear functional. Then there exists an _extention_ $x' : X \to \mathbb{R}$ a continuous linear functional such that $x'(u)=u'(u)$ for all $u \in U$ and $\Vert x' \Vert_{X'} = \Vert u' \Vert_{U'}$.

# Applications
Let $(X, \Vert \cdot \Vert_X)$ be a normed space. 
1. For all $x \in X$, $x \neq 0$ there is a linear operator $x' \in X'$ with $\Vert x'\Vert_{X'}=1$ and $x'(x) = \Vert x \Vert_X$. Define a linear functional on the subspace $U = span\{x\}$ as $u'(\lambda x) := \lambda \Vert x \Vert_X$ using Hahn-Banach we know there exists a continuous linear functional $x' \in X'$, let's check:
$$
x'(x) = u(x) = \Vert x \Vert_X \qquad \Vert x' \Vert_{X'} = \Vert u' \Vert_{U'}=\sup\{ |u'(u)| \mid \Vert u\Vert_X = 1\}
$$
	since $|u'(u)| = |\lambda| \Vert x \Vert_X$ so if $u$ is a unit vector $\lambda = \frac{1}{\Vert x \Vert_X}$. 
2. $(X', \Vert \cdot \Vert_{X\to\mathbb{R}})$ _separates_ points of $X$: for any $x_1, x_2 \in X$ such that $x_1 \neq x_2$ we can always find two linear operators $l_1, l_2 \in X'$ so that $l_1(x_1) \neq l_2(x_2)$. 
	Just use the previous result on the (non-zero) vector $x := x_2-x_1$, define the functional $x' \in X'$ as above. Then $x'(x) = \Vert x \Vert_X \neq 0$. By linearity
	$$
	x'(x) = x'(x_2-x_1) = x'(x_2) - x'(x_1) \neq 0
  $$
  3. For all $x \in X$ we can compute its norm by "reversing" the operator norm:
  $$
  \Vert x \Vert_X = \sup\{ |x'(x)| \mid x' \in X', \Vert x' \Vert_{X'} = 1\}
  $$
  by the $\sup$ definition of the operator norm
  $$
  \Vert x'\Vert_{X'} \geq \frac {|x'(x)|}{\Vert x \Vert_X} 
 $$
 and we see that 
$$
\sup\{ |x'(x)| \mid x' \in X', \Vert x' \Vert_{X'} = 1\} \leq \Vert x \Vert_X
$$ for the other inequality, we use $1.$, so we know there exists a functional such that $x'(x) = \Vert x \Vert_X$  with $\Vert x' \Vert_{X'} = 1$, so that
$$
\Vert x \Vert_X \leq \sup_{\Vert x' \Vert_{X'}=1} |x'(x)|
$$
and we get the desired equality. Indeed the $\sup$ is a $\max$.