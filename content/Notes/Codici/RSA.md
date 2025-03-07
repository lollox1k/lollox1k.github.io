$p$ and $q$ big primes, modern RSA $1024/2048$ bit size of $n$
$$
c = p^e \mod(n)
$$
$$
p = c^d \mod(n)
$$
$$
n = pq \qquad \varphi(n) = (p-1)(q-1)
$$
Phi è la funzione di Eulero, indica quanti numeri primi precedono $n$. In generale è computazionalmente difficile calcolarla (servono tutti i primi fino ad $n$), ma nel caso di $n$ semiprimo (prodotto di due primi) assume una forma banale.
$$
de = 1 \mod(\varphi(n))  
$$
$d$ is the multiplicative inverse of $e$ modulus $n$. 
From Euler Theorem's:
$$
a^{\varphi(n)} = 1 \mod(n)
$$


