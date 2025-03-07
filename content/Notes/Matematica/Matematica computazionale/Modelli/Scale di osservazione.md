#### Microscopic
- Focus su ogni singolo agente/particella del sistema fisico in esame
- indivudare gli stati microscopici
- sistemi di ODEs
- molto accurati
Esempio: Meccanica Newtoniana 
$$
\ddot{x}_i = \frac{1}{m_i}F_i
$$
- modelli dinamici discreti
- interazioni binarie
E nel limite $N\to \infty$? Non è più computazionalmente pratico usare questa modellizzazzione

### Mesoscopic Kinetic
- approccio statistico alla modellizzazione
- distribuzione di probabilità cinetica $f(t,x,v)$
- PDEs
Esempio: Equazione di Boltzmann, eq. mean-field, tipo Vlasov

### Macroscopic
- evoluzione temporale di quantità sintentiche relative al fenomeno fisico:
1. $\rho(t,x)$ densità di un gas
2. $u(t,x)$ velocità media
3. $E(t,x)$ energia del gas
- PDEs
- Meno accurati
- Sistemi dinamici continui

Esistono vari limi per passare da un modello all'altro, quando possibile: posso saltare da una scala più accurata ad una meno:
- limite micro-mesoscopico
- limite meso-macroscopico
- limite micro-macroscopico