# Fondamenti dell'analisi numerica
## Buona positura e numero di condizionamento di un problema

Si consierdi il seguente prolema astratto:
$$
F(x,d)=0
$$
Il problema è _ben posto_ se ammette un'unica soluzione che dipende con _continuità_ dai dati $d$.
Sia $D$ l’insieme dei dati ammissibili, ovvero, l’insieme dei valori di $d$ in corrispondenza dei quali il problema ammette soluzione unica. 
La dipendenza continua dai dati significa che piccole perturbazioni sui dati d debbano riflettersi in “piccole” variazioni nella soluzione x, ovvero perturbando il problema:
$$
F(x+\delta x, d + \delta d) = 0
$$
richiediamo che la conseguente perturbazione sulla soluzione $\delta x$ sia:
$$
\exists K_{0(d)}\quad \text{ tale che } \forall \delta d \,:\, d+\delta d \in D, \Vert \delta x \Vert \leq K \Vert \delta d\Vert
$$
**Osservazione** E' una richiesta di continuità di tipo Lipshitz, più forte della solita continuità $\epsilon-\delta$. Infatti vogliamo che le perturbazioni sulla soluzione siano dello stesso ordine di grandezza delle perturbazioni dei dati.

### Numero di condizionamento relativo
In base alla definizione di continuità Lipshitz, risulta sensato introdurre il _numero di condizionamento relativo_, quantificando la stabilità di un problema:
$$
K(d) := \sup \left\{ \frac{\Vert \delta x \Vert}{\Vert x\Vert} / \frac{\Vert \delta d \Vert}{\Vert d \Vert}, \quad \delta d \neq 0, \,\delta d + d \in D\right\}
$$
nel caso $x=0$ o $d=0$, è necessario introdurre un $K_{abs}$.

Quindi un problema si dice _mal condizionato_ se $K(d)$ è "grande" per quasi tutti i $d \in D$.

Se il problema ammette una sola soluzione, allora esiste un'applicazione "risolvente" tale che:
$$
x = G(d)\qquad F(G(d),d)=0
$$
Supponendo derivabile, possiamo espandere $G$ attorno a $d$, e scoprire che il numero di condizionamento dipende dal modulo dello Jacobbiano:
$$
 \delta x = G(d+\delta d) - G(d) \simeq  G'(d)\delta d + o(\Vert \delta d \Vert)
$$
quindi:
$$
K(d) = \Vert G'(d) \Vert \frac{\Vert d \Vert}{\Vert G(d)\Vert}
$$
### Sistemi di equazioni lineari
Un esempio importante è un generico sistema di equazioni lineari:
$$
Ax = b
$$
Se il problema è _ben posto_, ovvero la soluzione è unica, quindi la matrice è invertibile e la soluzione è:
$$
x = A^{-1}b \qquad G(d) = A^{-1}d
$$
che è anche lo Jacobbiano di se stessa, dunque il numero di condizionamento è:
$$
K(d) \simeq \Vert A^{-1} \Vert \frac{\Vert b \Vert}{\Vert A^{-1} b \Vert} = \Vert A^{-1} \Vert \frac{\Vert Ax \Vert}{\Vert x \Vert} \leq \Vert A^{-1} \Vert \Vert A \Vert =: K(A)
$$
dove abbiamo definito il numero di condizionamento $K(A)$ di una matrice invertibile $A$.

## Sorgenti di errori nei modelli computazionali

In generale esistono i seguenti tipi di errore:
1. _errori dovuti al modello_, controllabili curando la costruzione del modello matematico;
2. _errori nei dati_, riducibili aumentando l’accuratezza nelle misurazioni dei dati stessi;
3. _errori di troncamento_, dovuti al fatto che nel modello numerico le operazioni di passaggio al limite vengono approssimate con operazioni che richiedono un numero finito di passi;
4. _errori di arrotondamento_.
Sono questi ultimi punti, **3** e **4** gli **errori computazionali**. Un metodo numerico sarà dunque [[Consistenza di un metodo numerico| convergente]]  se _questo errore può essere arbitrariamente ridotto aumentando lo sforzo computazionale_. Ovviamente, seppur primario, la convergenza non è l’unico obiettivo di un metodo numerico, dovendosi coniugare all’accuratezza, all’affidabilità e all’efficienza.

- L’**accuratezza** esprime il fatto che gli _errori siano piccoli rispetto ad una tolleranza fissata_. Essa in genere si quantifica attraverso l’ordine di infinitesimo dell’errore $e_n$ rispetto al parametro caratteristico della discretizzazione.
- Un modello numerico si considera **affidabile** quando, se applicato ad un numero significativo di casi test di interesse pratico, l’errore totale da esso generato può essere tenuto al di sotto di una certa tolleranza con un margine di probabilità superiore ad una percentuale prestabilita.
- **Efficienza** significa infine che la complessità computazionale (tempo e memoria) necessaria per controllare tale errore sia la più bassa possibile.

