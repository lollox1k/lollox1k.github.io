# Wielandt algorithm

Viene anche detto algoritmo dell'iterazione inversa, è dovuto a Wielandt (1944), e sfrutta uno shift per adattare il [[Power method]] al calcolo di tutto lo spettro (autovettori compresi) e non solo l'autovalore dominante.

L'idea è partire da un'approssimazione $\mu$ dell'autovalore che vogliamo approssimare, ad esempio usando [[Gershgorin cicle theorem]], in maniera tale da rendere $\lambda -\mu$ l'autovalore di modulo minimo. Ma allora, sarà l'autovalore di modulo massimo della matrice inversa:
$$
(A-\mu I)^{-1}
$$
Si può applicare il metodo delle potenze per ottenere la coppia autovalore-autovettore.

Quando si implementa si evita di invertire la matrice, è preferibile effettuare la fattorizzazione $LU$ e risolvere due sistemi triangolari.

