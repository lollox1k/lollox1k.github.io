Mi dice la differenza di potenziale necessaria tra due regioni per avere una certa concentrazione, ad una certa temperatura. Abbiamo in gioco le "forze" di diffusioni, puramente statistiche che vanno contro il gradiente di concentrazione (gli ioni vanno dalle zone più dense a quelle meno dense), e una forza reale in gioco, come ad esempio quella elettrica.

#### Derivazione dalla statistica di MB

La maniera più semplice (per un fisico) per ricavare l'equazione è partire dalla [[statistica maxwell-boltzmann]], il rapporto delle concentrazioni è uguale al rapporto del numero di particelle (assumendo stesso volume), quindi il numero di particelle medio è dato dal rapporto dei fattori di Boltzmann, dipende dalle energie di singola particella nelle due regioni:

$$
\frac{[X_A]}{[X_B]} = \frac{e^{-\beta E_A}}{e^{-\beta E_B}} 
$$
prendendo il logaritmo e ricordando $\beta = 1/k_B T$
$$
Tk_B \ln{\frac{[X_A]}{[X_B]}} = E_B - E_A
$$
ricordiamo che $E_A$ e $E_B$ sono le energie di singola particelle nelle due regioni (divise da una membrana permeabile ad esempio), la parte cinetica si semplifica, rimane solo la parte spaziale del potenziale, se pensiamo a ioni con forze elettrice: $E = qV$. Come al solito in chimica si ragiona per moli, dividendo per il numero di Avocadro $N_A$  abbiamo:
$$
TR\ln{\frac{[X_A]}{[X_B]}} = z\frac{e}{N_A}(V_B - V_A)
$$
Dove $z$ è la valenza dello iono (per $Na^+$ $z=1$).Introducendo la costante di Faraday $F = e/N_A$ otteniamo la forma solita dell'equazione di Nerst:
$$
V_B - V_A = \frac{TR}{zF} \ln{\frac{[X_A]}{[X_B]}}
$$
#### Derivazione tramide [[Diffusione Fick's Law]]
Imponiamo l'equilibrio tra le densità di corrente di drift e diffusione. Come densità abbiamo le concentrazioni

$$
-D \nabla [C] - q\mu \nabla V [C] = 0
$$
Dalla [[Einstein's relation]] sappiamo che $\mu = D k_B T$
