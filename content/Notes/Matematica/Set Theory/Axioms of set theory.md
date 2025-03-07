## The $\in$-relation
Set theory is built on the postulate that there is a fundamental binary relation denoted $\in$ . 

We don't define explicitly sets and the relation $\in$, we will have nine axioms concerning ∈ and sets, and it is only in terms of these nine axioms that ∈ and sets are defined at all.

We can define the common relations:
- $x \notin y \:= \lnot(x\in y)$
- $x \subseteq y := \forall a : (a \in x \implies a \in y)$
- $x=y := (x\subseteq y)\land (y \subseteq x)$
$x\subset y := (x\subseteq y) \land \lnot(x = y)$


# The axioms
The totality of all these nine axioms are called ZFC set theory, which is a shorthand for Zermelo-Fraenkel set theory with the axiom of Choice

1. **Axiom on the $\in$-relation**  _The expression $x \in y$ is a proposition if, and only if, both $x$ and $y$ are sets:
$$
\forall x : \forall y : (x\in y) \lor \lnot(x \in y)
$$
This prevents tue Russell's paradox, in fact from this definition the russell set is not a set.

2. **Axiom on the existence of an empty set** _There exists a set that contains no elements:_
$$
\exists y : \forall x \notin y 
$$
3. **Axiom on pair sets** _Let $x$ and $y$ be sets. Then there exists a set that contains as its elements precisley $x$ and $y$:_
$$
\forall x : \forall y : \exists m : \forall u : (u \in m \iff (u=x \lor u=y))
$$
The pair set $m$ is denoted by $\{x,y\}$.
From this follows the existence of the _singleton_ set $\{x\} := \{x,x\}$.

4. **Axiom on union sets** _Let $x$ be a set. Then there exists a setr whose elements are precisley the elements of the elements of $x$:_
$$
\forall x : \exists u : \forall y : (y \in u \iff \exists s : (y\in s \land s \in x))
$$
The set $u$ is denoted by $\cup x$.
We need this axioms to build sets with more than 2 elments.

We can now define the intersection and the relative complement of sets. _Let $x$ be a set. We define the intersection of $x$ by:_
$$
\cap x := \{a \in \cup x | \forall b \in x : a \in b\}
$$
We can also define the difference of two sets $u \subseteq m$:
$$
m\setminus u := \{x \in m | x \notin u \}
$$

5. **Axiom of replacement** _Let $R$ be a functional relation and $m$ a set. Then the image of $m$ under $R$, denoteb by $im_R(m)$ is a set._
A realtion $R$ is functional if:
$$
\forall x : \exists! y : R(x,y)
$$
Hence the name.
The _principle of restricted comprension_ (given a set $m$ and a predicate $P(x)$ then $\{y \in m | P(y)\}$ is a set) is a consequence of the replacement axioms. Without the costrain of the set $m$ is known as the _principle of universal comprension_, wich Russell proved to be inconsistent.

6. **Axiom ont the existence of power sets** _Let $m$ be a set. Then there exists a set, denoted by $P(m)$, whose elements are precisely the subsets of $m$:_
$$
\forall x : \exists y : \forall a : (a \in y \iff a \subseteq x)
$$

7. **Axiom of infinity** _There exists a set that contains the empty set and, together with every other element $y$, it also contains the set $\{y\}$ as an element:
$$
\exists x : \emptyset \in x \land \forall y : (y \in x \implies \{y\} \in x)
$$
Consider one of this sets $x$. It follows that:
$$
x = \{ \emptyset, \{\emptyset\}, \{\{\emptyset\}\}, \dots \}
$$
We can define:
$$
0 := \emptyset, \quad 1 := \{\emptyset\}, \quad 2 := \{\{\emptyset \} \}, \quad \dots
$$

Accordin to our axioms the set $\mathbb{N} := x$ is a set. We then can define $\mathbb{R} := P(\mathbb{N})$.

There is a modern variant, insted of $\{y\} \in x$ we impose $y\cup \{y\} \in x$.

8. **Axiom of choice** _Let $x$ be a set whose elements are non-empty and mutually disjoint. Then there exists a set $y$ which contains exactly one element of each element of $x$._
$$
\forall x : P(x) \implies \exists y : \forall a \in x : \exists | b \in a : a \in y,
$$
where
$$
P(x) \iff (\exists a : a \in x)\land (\forall a : \forall b : (a\in b \land b \in x)\implies \cap\{a,b\} = \emptyset)
$$
The axiom of choice is independent of the other 8 axioms, which means that one could have set theory with or without the axiom of choice. However, standard mathematics uses the axiom of choice and hence so will we. There is a number of theorems that can only be proved by using the axiom of choice. Amongst these we have:
- every vector space has a basis;
- there exists a complete system of representatives of an equivalence relation;

9. **Axiom of foundation** _. Every non-empty set $x$ contains an element $y$ that has none of its elements in common with $x$:_
$$
\forall x : (\exists a : a \in x) \implies \exists y \in x : \cap \{x,y\} = \emptyset
$$
An immediate consequence of this axiom is that there is no set that contains itself as an element.
