Esistono soluzioni di PDE come [[linear advection]] non differenziabili, basta considerare una condizione iniziale discontinua. Quindi non essendo derivabili, non possono soffisfare l'equazione differenziale, tuttavia in un certo senso sono soluzioni. Formalizziamo questo fatto grazie alle _funzioni test_, ovvero fuzioni smooth a supporto compatto. 

Intuitivamente, le funzioni test definiscono una _misura locale_ di una quantità tramite un integrale. 
Quindi sia $\psi \in C^{\infty}_{cpt}(\mathbb{R})$ ed $u \in C^1(\mathbb{R})$, integrando per parti otteniamo l'equivalenza
$$
\int u'\psi dx = \psi u|_{-\infty}^{+\infty} - \int u \psi'dx 
$$
il termine di bordo è nullo dato che la funzione test è a supporto compatto. Abbiamo _scaricato la derivata_ sulla funzione test (che è smooth). Siamo portati a definire una _derivata in senso debole_, anche per funzioni non derivabili.
### Definizione
Per prima cosa ci restringiamo alle funzioni _localmente integrabili_ (su un compatto) $L^1_{loc}(\Omega)$ con $\Omega \subseteq \mathbb{R}^n$. 
Definiamo la _derivata in senso debole_ $f$ di una funzione $u\in L^1_{loc}$ se vale per ogni funzione test $\psi$ l'equivalenza:
$$
\int_\Omega f\psi dx =  - \int_\Omega u \psi'dx 
$$
Si estende alla derivata n-esima integrando più volte per parti, questo fa oscillare il segno. 
Notazione: $D^\alpha f$ con $\alpha = \alpha_1,\dots\alpha_n$ interi non negativi, l'ordine $|\alpha| := a_1 + \dots a_n$.
$$
\int_\Omega (D^\alpha u) \psi d^nx = (-1)^{|\alpha|}\int_\Omega u (D^\alpha \psi) d^nx
$$
per tutte le funzioni test $\psi \in C^{\infty}_{cpt}(\Omega)$. 

### Oss
fortunatamente se la funzione è derivabile la derivata debole coincide con quella classica (soddisfa l'equivalenza banalmente perchè vale l'integrale per parti).

### Oss
è ben definitia? Ovvero _è unica_? Sì, basta far vedere che se l'integrale è nullo la funzione è nulla (come per $L^2$ è necessaria la relazione di equivalenza $q.o.$ ).



