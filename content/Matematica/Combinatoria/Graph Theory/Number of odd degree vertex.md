
**Theorem** the number of odd degree vertices is even.

**Proof** Assume the number is odd. We arrive at a contraddiction. 
The sum of all vertices degree is two times the number of edges [[Handshake Lemma]]:
$$
\sum_{v\in V}d(v) = 2m
$$
we can spli the sum into odd and even degree:
$$
2m = \sum_{odd} d(v) + \sum_{even} d(v)
$$
now suppose the number of odd verticies is odd. The sum of an odd number of odds is odd, infact:
$$
\sum_{i=1}^{2M+1} (2k_i+1) = 2\sum_{i=1}^{2M+1}k_i + (2M+1) = 2\Big[ \sum k + M \Big] + 1
$$
A sum of even numbers is even (trivial). We conclude that:
$$
2m = 2A+1 + 2B = 2(A+B) + 1
$$
for some positive integers $A,B$.  But we are saying that $even=odd$, absurd (the equation doesn't have positive integers solutions). $\square$

