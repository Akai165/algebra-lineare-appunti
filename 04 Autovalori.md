## 1. Autovalori, autovettori e autospazi

> 💡 **Spiegazione semplice:** Immagina un'applicazione lineare $\varphi$ come una macchina che trasforma i vettori dello spazio (li ruota, li deforma, li allunga). Quasi tutti i vettori cambiano direzione quando entrano nella macchina, ma ce ne sono alcuni speciali che **mantengono esattamente la stessa direzione**: vengono solo allungati, accorciati o ribaltati di un certo fattore $\lambda$. Quei vettori speciali sono gli **autovettori**, e il fattore di scala $\lambda$ è il loro **autovalore**.

**Definizione**

Sia $V$ uno spazio vettoriale su $\mathbb{R}$ di dimensione finita ($\dim V < \infty$) e sia $\varphi: V \to V$ un'applicazione lineare (un endomorfismo).

- Un numero $\lambda \in \mathbb{R}$ si dice **autovalore** di $\varphi$ se esiste un vettore non nullo $v \in V$ ($v \neq 0$) tale che:
    
    $$\varphi(v) = \lambda \cdot v$$
    
- In questo caso, $v$ si dice **autovettore** associato a $\lambda$.
    

_(Perché chiediamo $v \neq 0$? Perché per il vettore nullo vale sempre $\varphi(0) = 0 = \lambda \cdot 0$ per qualsiasi $\lambda$, quindi non ci darebbe nessuna informazione utile!)_

**Prime proprietà (Osservazioni)**

1. **Un autovettore ha un solo autovalore:** Un vettore $v \neq 0$ non può essere associato a due autovalori diversi. Infatti, se $\lambda_1 v = \varphi(v) = \lambda_2 v$, allora $(\lambda_1 - \lambda_2)v = 0$. Dato che $v \neq 0$, deve essere per forza $\lambda_1 = \lambda_2$.
    
2. **Un autovalore può avere tanti autovettori:** Fissato $\lambda$, possono esistere moltissimi autovettori associati ad esso.
    
    - _Caso estremo:_ Se $\varphi = \text{id}$ (l'applicazione identità, $\varphi(v) = v$ per ogni $v$), allora tutti i vettori non nulli sono autovettori per $\lambda = 1$.
        
    - _Esempio simile:_ Se $\varphi(v) = \alpha v$ per ogni $v$ (cioè $\varphi = \alpha \cdot \text{id}$), allora tutti i vettori non nulli sono autovettori per $\lambda = \alpha$.
        

**Dagli autovettori agli autospazi**

Visto che un singolo $\lambda$ può avere tanti autovettori, ci chiediamo che struttura formino tutti insieme:

- **Proposizione a):** Se $\lambda \in \mathbb{R}$, l'insieme degli autovettori associati a $\lambda$, **insieme al vettore nullo $0$**, forma un sottospazio vettoriale di $V$. Questo sottospazio si indica con $V_\lambda$ e si chiama **autospazio** relativo a $\lambda$.
    
    - _Dimostrazione:_ Se $v_1, v_2 \in V_\lambda$, allora $\varphi(v_1 + v_2) = \varphi(v_1) + \varphi(v_2) = \lambda v_1 + \lambda v_2 = \lambda(v_1 + v_2)$, e per ogni scalare $\alpha$, $\varphi(\alpha v_1) = \alpha \varphi(v_1) = \alpha \lambda v_1 = \lambda(\alpha v_1)$. Quindi $V_\lambda$ è chiuso rispetto a somma e prodotto per scalare.
        
- **Proposizione b):** Se $\lambda_1 \neq \lambda_2$, allora i rispettivi autospazi hanno in comune solo il vettore nullo: $V_{\lambda_1} \cap V_{\lambda_2} = \{0\}$ (segue direttamente dall'Osservazione 1).
    

## 2. Perché ci interessano? La diagonalizzazione

> 💡 **Spiegazione semplice:** Lavorare con matrici piene di numeri sparsi ovunque è scomodo, soprattutto se devi moltiplicarle tante volte o studiare sistemi complessi. Le matrici **diagonali** (che hanno numeri solo sulla diagonale principale e zeri altrove) invece sono facilissime da gestire. Diagonalizzare significa trovare il "punto di vista" giusto (la base giusta) in cui la nostra trasformazione $\varphi$ si comporta in modo semplicissimo, cioè come una matrice diagonale!

**Definizione** L'applicazione lineare $\varphi$ si dice **diagonalizzabile** se esiste una base di $V$ rispetto alla quale la matrice associata a $\varphi$ è diagonale. Se $\varphi: \mathbb{R}^n \to \mathbb{R}^n$ è definita da $v \mapsto A \cdot v$, diciamo anche che la matrice $A$ è diagonalizzabile.

**Il ponte tra autovettori e diagonalizzabilità**

Come facciamo a costruire questa famigerata "base buona"? Ci vengono in aiuto proprio gli autovettori!

- **Proposizione fondamentale:** $\varphi$ è diagonalizzabile $\iff$ esiste una base di $V$ costituita interamente da autovettori di $\varphi$.
    
- _Dimostrazione:_
    
    - ($\Rightarrow$) Se $e_1, \dots, e_n$ è una base in cui la matrice di $\varphi$ è diagonale, cioè $\begin{bmatrix} \lambda_1 & & 0 \\ & \ddots & \\ 0 & & \lambda_n \end{bmatrix}$ (nota: i $\lambda_i$ _non_ devono essere per forza tutti diversi!), leggere le colonne della matrice significa esattamente dire che $\varphi(e_1) = \lambda_1 e_1, \dots, \varphi(e_n) = \lambda_n e_n$. Quindi i vettori della base sono autovettori.
        
    - ($\Leftarrow$) Viceversa, se abbiamo una base $e_1, \dots, e_n$ di autovettori, per definizione $\varphi(e_i) = \lambda_i e_i$, quindi la matrice associata in questa base ha i $\lambda_i$ sulla diagonale e zeri altrove.
        

**Attenzione: non tutte le $\varphi$ sono diagonalizzabili!** Prendiamo l'esempio più semplice possibile in $V = \mathbb{R}^2$: $\varphi(v) = Av$ con $A = \begin{bmatrix} 1 & 1 \\ 0 & 1 \end{bmatrix}$. Se $v = \begin{bmatrix} x_1 \\ x_2 \end{bmatrix}$, allora $\varphi(v) = \begin{bmatrix} x_1 + x_2 \\ x_2 \end{bmatrix}$. Imponendo $\varphi(v) = \lambda v$ (con $v \neq 0$) otteniamo il sistema:

$$\begin{cases} x_1 + x_2 = \lambda x_1 \\ x_2 = \lambda x_2 \end{cases}$$

Dalla seconda equazione ricaviamo $\lambda = 1$ oppure $x_2 = 0$:

- Se $\lambda = 1$, la prima equazione diventa $x_1 + x_2 = x_1 \implies x_2 = 0$.
    
- Se $x_2 = 0$, la prima diventa $x_1 = \lambda x_1 \implies \lambda = 1$ (dato che $v \neq 0$, deve essere $x_1 \neq 0$).
    

Quindi gli unici autovettori sono i multipli non nulli di $\begin{bmatrix} 1 \\ 0 \end{bmatrix}$ (tutti associati a $\lambda = 1$). Con un solo vettore indipendente non possiamo formare una base di $\mathbb{R}^2$: **$\varphi$ non è diagonalizzabile**.

## 3. Come capire se un'applicazione è diagonalizzabile

> 💡 **Spiegazione semplice:** Per formare una base dello spazio $V$ ci servono esattamente $n = \dim V$ vettori linearmente indipendenti. La buona notizia è che autovettori appartenenti ad autovalori _diversi_ non si pestano mai i piedi (sono sempre indipendenti). Quindi ci basta contare quanti autovettori indipendenti riusciamo a raccogliere da ogni autospazio: se in totale arriviamo a $n$, abbiamo vinto!

**La chiave teorica: l'indipendenza lineare**

- **Proposizione:** Se $\lambda_1, \dots, \lambda_r$ sono autovalori **distinti** di $\varphi$ e $v_1, \dots, v_r$ sono rispettivi autovettori associati, allora $v_1, \dots, v_r$ sono **linearmente indipendenti**.
    
    - _Idea della dimostrazione (per induzione su $r$):_ Per $r=1$ è ovvio perché $v_1 \neq 0$. Supponiamo $\alpha_1 v_1 + \dots + \alpha_r v_r = 0$ (chiamiamola eq. $*$). Applichiamo $\varphi$ a entrambi i membri ottenendo $\alpha_1 \lambda_1 v_1 + \dots + \alpha_r \lambda_r v_r = 0$. Moltiplichiamo invece eq. $(*)$ per $\lambda_1$ (se $\lambda_1 = 0$, usiamo un altro $\lambda_i$) e sottraiamo le due equazioni: il termine con $v_1$ sparisce e resta $\alpha_2(\lambda_2 - \lambda_1)v_2 + \dots + \alpha_r(\lambda_r - \lambda_1)v_r = 0$. Per ipotesi induttiva $v_2, \dots, v_r$ sono indipendenti, e poiché $\lambda_i - \lambda_1 \neq 0$, segue $\alpha_2 = \dots = \alpha_r = 0$. Sostituendo in $(*)$, resta $\alpha_1 v_1 = 0 \implies \alpha_1 = 0$.
        

Da questa proposizione scendono tre conseguenze super pratiche (Corollari):

1. **Corollario 1:** Ci sono al massimo un numero finito di autovalori distinti (al più $n = \dim V$, perché non possono esistere più di $n$ vettori linearmente indipendenti).
    
2. **Corollario 2 (Criterio esatto):** Se $\lambda_1, \dots, \lambda_r$ sono tutti gli autovalori distinti di $\varphi$, allora:
    
    $$\varphi \text{ è diagonalizzabile} \iff \dim V_{\lambda_1} + \dim V_{\lambda_2} + \dots + \dim V_{\lambda_r} = \dim V$$
    
    - _Perché?_ Se uniamo una base di $V_{\lambda_1}$, una di $V_{\lambda_2}$, ecc., otteniamo vettori tutti linearmente indipendenti tra loro (per la proposizione sopra). Formano una base di tutto $V$ se e solo se il loro numero totale coincide con $\dim V$.
        
3. **Corollario 3 (Scorciatoia):** Se $n = \dim V$ e $\varphi$ ha **$n$ autovalori distinti**, allora $\varphi$ è **sicuramente diagonalizzabile** (abbiamo già $n$ autovettori indipendenti, uno per ogni autovalore!). _Attenzione:_ il viceversa è falso! Ad esempio $\varphi = \text{id}$ è diagonalizzabile ma ha un solo autovalore ($\lambda = 1$).
    

**Schema pratico in 2 passi per decidere se $\varphi$ è diagonalizzabile:**

1. **Trova gli autovalori:** Se ne trovi $n = \dim V$ tutti distinti $\implies$ **siamo HAPPY**, è sicuramente diagonalizzabile!
    
2. **Se sono meno di $n$:** Calcola gli autospazi $V_{\lambda_i}$ e le loro dimensioni $\dim V_{\lambda_i}$ per ogni autovalore:
    
    - Se $\sum \dim V_{\lambda_i} = \dim V \implies \varphi$ **è diagonalizzabile**.
        
    - Se $\sum \dim V_{\lambda_i} < \dim V \implies \varphi$ **non è diagonalizzabile** (è il caso del nostro esempio $A = \begin{bmatrix} 1 & 1 \\ 0 & 1 \end{bmatrix}$, dove $\lambda = 1$ è l'unico autovalore e $\dim V_1 = 1 < 2$).
        

## 4. Come calcolare gli autovalori: il polinomio caratteristico

> 💡 **Spiegazione semplice:** Ok, tutto bello, ma come li peschiamo questi autovalori nella pratica? Scriviamo l'equazione degli autovettori sotto forma di un sistema lineare omogeneo $(A - \lambda I)v = 0$. Affinché questo sistema abbia soluzioni diverse dal vettore nullo, la matrice $(A - \lambda I)$ deve "schiacciare" qualcosa a zero, cioè il suo determinante deve essere $0$. Risolvere $\det(A - tI) = 0$ trasforma un problema geometrico in una semplice equazione polinomiale!

**Il ragionamento algebrico**

Partiamo dalla definizione di autovettore ($v \neq 0$):

$$\varphi(v) = \lambda v \iff \varphi(v) - \lambda v = 0 \iff (\varphi - \lambda \cdot \text{id})v = 0$$

Dire che esiste un $v \neq 0$ che soddisfa questa equazione equivale a dire che il nucleo non è banale:

$$\ker(\varphi - \lambda \cdot \text{id}) \neq \{0\}$$

Se $A$ è la matrice di $\varphi$ rispetto a una base qualsiasi, la matrice di $\varphi - \lambda \cdot \text{id}$ è $A - \lambda I$ (dove $I$ è la matrice identità). In termini di matrici:

$$\ker(A - \lambda I) \neq \{0\} \iff \det(A - \lambda I) = 0$$

**Definizione (Polinomio caratteristico)**

Data una matrice quadrata $A \in M_{n \times n}(\mathbb{R})$, il suo **polinomio caratteristico** è il polinomio nella variabile $t$ (di grado $\deg P_A(t) = n$):

$$P_A(t) := \det(A - t \cdot I) = \det \begin{bmatrix} a_{11}-t & a_{12} & \dots & a_{1n} \\ a_{21} & a_{22}-t & \dots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{n1} & a_{n2} & \dots & a_{nn}-t \end{bmatrix} \in \mathbb{R}[t]$$

_(Nota: molti testi lo definiscono come $\det(t \cdot I - A)$; cambia solo un segno $(-1)^n$, ma le radici sono identiche)_.

- **Conclusione:** $\lambda \in \mathbb{R}$ è autovalore di $\varphi \iff \lambda$ è una **radice** del polinomio caratteristico $P_A(t)$.
    
- **Osservazione (Invarianza per cambio di base):** $P_A(t)$ dipende solo dall'applicazione $\varphi$ e non dalla base scelta per scrivere $A$. Infatti, cambiando base si ottiene la matrice $PAP^{-1}$, e usando le proprietà del determinante:
    
    $$P_{PAP^{-1}}(t) = \det(PAP^{-1} - t \cdot PIP^{-1}) = \det(P(A - tI)P^{-1}) = \det(P)\det(A - tI)\det(P^{-1}) = \det(A - tI) = P_A(t)$$
    

## 5. Esempi pratici risolti

### Esempio 1: Un caso diagonalizzabile in $\mathbb{R}^3$

Consideriamo $\varphi: \mathbb{R}^3 \to \mathbb{R}^3$ rappresentata dalla matrice triangolare:

$$A = \begin{bmatrix} 1 & 1 & 0 \\ 0 & 0 & 1 \\ 0 & 0 & -1 \end{bmatrix}$$

1. **Calcoliamo il polinomio caratteristico:** Essendo una matrice triangolare superiore, il determinante è il prodotto degli elementi sulla diagonale:
    
    $$P_A(t) = \det \begin{bmatrix} 1-t & 1 & 0 \\ 0 & -t & 1 \\ 0 & 0 & -1-t \end{bmatrix} = (1-t)(-t)(-1-t)$$
    
2. **Troviamo gli autovalori:** Le radici sono $\lambda_1 = 1$, $\lambda_2 = 0$, $\lambda_3 = -1$. Sono 3 autovalori **distinti** in $\mathbb{R}^3$ ($\dim V = 3$), quindi per il Corollario 3 sappiamo già che **$\varphi$ è diagonalizzabile**!
    
3. **Cerchiamo gli autovettori per trovare la "buona" base** (risolvendo $Av = \lambda v$ per ciascun $\lambda$):
    
    - **Per $\lambda = 1$:** $\begin{bmatrix} 1 & 1 & 0 \\ 0 & 0 & 1 \\ 0 & 0 & -1 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} x \\ y \\ z \end{bmatrix} \implies \begin{cases} x+y = x \\ z = y \\ -z = z \end{cases} \implies z=0, y=0$. Autovettori: multipli non nulli di $\begin{bmatrix} 1 \\ 0 \\ 0 \end{bmatrix}$.
        
    - **Per $\lambda = 0$:** $\begin{bmatrix} 1 & 1 & 0 \\ 0 & 0 & 1 \\ 0 & 0 & -1 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix} \implies \begin{cases} x+y = 0 \\ z = 0 \\ -z = 0 \end{cases} \implies z=0, y=-x$. Autovettori: multipli non nulli di $\begin{bmatrix} 1 \\ -1 \\ 0 \end{bmatrix}$.
        
    - **Per $\lambda = -1$:** $\begin{bmatrix} 1 & 1 & 0 \\ 0 & 0 & 1 \\ 0 & 0 & -1 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} -x \\ -y \\ -z \end{bmatrix} \implies \begin{cases} x+y = -x \\ z = -y \\ -z = -z \end{cases} \implies y=-2x, z=2x$. Autovettori: multipli non nulli di $\begin{bmatrix} 1 \\ -2 \\ 2 \end{bmatrix}$.
        

### Esempio 2: Un caso con un solo autovalore

Consideriamo la matrice:

$$A = \begin{bmatrix} 1 & 1 & 0 \\ 0 & 1 & 1 \\ 0 & 0 & 1 \end{bmatrix}$$

Il polinomio caratteristico è:

$$P_A(t) = \det \begin{bmatrix} 1-t & 1 & 0 \\ 0 & 1-t & 1 \\ 0 & 0 & 1-t \end{bmatrix} = (1-t)^3$$

Qui c'è **1 solo autovalore** ($\lambda = 1$ con molteplicità algebrica 3), quindi per sapere se è diagonalizzabile bisogna calcolare $\dim V_1$ (che risulterà $1 < 3$, quindi non diagonalizzabile).
### Esercizio 3

Data la matrice $A = \begin{bmatrix} 0 & 3 & 0 \\ 1 & -2 & 0 \\ 1 & -3 & 1 \end{bmatrix}$, vogliamo capire se è diagonalizzabile e, in caso affermativo, trovare la base che la diagonalizza.

1. **Calcolo degli autovalori (tramite il polinomio caratteristico):** Sottraiamo $t$ sulla diagonale principale e calcoliamo il determinante sviluppando lungo la terza colonna (che ha due zeri, quindi ci semplifica la vita):
    
    $$P_A(t) = \det \begin{bmatrix} -t & 3 & 0 \\ 1 & -2-t & 0 \\ 1 & -3 & 1-t \end{bmatrix} = (1-t) \begin{vmatrix} -t & 3 \\ 1 & -2-t \end{vmatrix} = (1-t)(t^2+2t-3)$$
    
    Scomponendo il trinomio di secondo grado otteniamo:
    
    $$P_A(t) = (1-t)(t-1)(t+3) = -(t-1)^2(t+3)$$
    
    Uguagliando a zero, gli autovalori sono **$\lambda_1 = 1$** (che compare due volte) e **$\lambda_2 = -3$**.
    
2. **Ricerca degli autovettori per $\lambda_1 = 1$:** Cerchiamo i vettori $\begin{bmatrix} x \\ y \\ z \end{bmatrix}$ tali che $A \begin{bmatrix} x \\ y \\ z \end{bmatrix} = 1 \cdot \begin{bmatrix} x \\ y \\ z \end{bmatrix}$, risolvendo il sistema:
    
    $$\begin{cases} 3y = x \\ x - 2y = y \\ x - 3y + z = z \end{cases} \implies x = 3y$$
    
    Dato che abbiamo 3 incognite ($x, y, z$) e una sola equazione indipendente ($x - 3y = 0$), restano 2 parametri liberi ($y$ e $z$). Quindi l'autospazio $V_1$ ha dimensione:
    
    $$\dim(V_1) = \dim\left(\ker\left(\begin{bmatrix} x \\ y \\ z \end{bmatrix} \mapsto x - 3y\right)\right) = 3 - 1 = 2$$
    
    Scegliendo due coppie indipendenti di valori (prima $y=1, z=0$ e poi $y=1, z=1$), troviamo **una base di $V_1$**:
    
    $$\begin{bmatrix} 3 \\ 1 \\ 0 \end{bmatrix}, \quad \begin{bmatrix} 3 \\ 1 \\ 1 \end{bmatrix} \text{[cite: 1]}$$
    
3. **Ricerca degli autovettori per $\lambda_2 = -3$:** Impostiamo $A \begin{bmatrix} x \\ y \\ z \end{bmatrix} = -3 \begin{bmatrix} x \\ y \\ z \end{bmatrix}$:
    
    $$\begin{cases} 3y = -3x \\ x - 2y = -3y \\ x - 3y + z = -3z \end{cases} \implies \begin{cases} x = -y \\ -4y = -4z \end{cases} \implies x = -y = -z$$
    
    Qui abbiamo un solo parametro libero, quindi $\dim(V_{-3}) = 1$. Ponendo $z = 1$, troviamo **una base di $V_{-3}$**:
    
    $$\begin{bmatrix} -1 \\ 1 \\ 1 \end{bmatrix} \text{[cite: 1]}$$
    
4. **Conclusione:** Mettendo insieme le basi dei due autospazi otteniamo 3 autovettori linearmente indipendenti. Di conseguenza, **$A$ è diagonalizzabile** nella base $\mathcal{B} = \left\{ \begin{bmatrix} 3 \\ 1 \\ 0 \end{bmatrix}, \begin{bmatrix} 3 \\ 1 \\ 1 \end{bmatrix}, \begin{bmatrix} -1 \\ 1 \\ 1 \end{bmatrix} \right\}$, rispetto alla quale la matrice diventa:
    
    $$D = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & -3 \end{bmatrix} \text{[cite: 1]}$$
    

### Esercizio 2 (continuazione)

Riprendiamo la matrice $\begin{bmatrix} 1 & 1 & 0 \\ 0 & 1 & 1 \\ 0 & 0 & 1 \end{bmatrix}$, che ha come unico autovalore $\lambda = 1$ (di molteplicità 3)[cite: 1].

- **Calcolo degli autovettori per $\lambda = 1$:**
    
    $$\begin{bmatrix} 1 & 1 & 0 \\ 0 & 1 & 1 \\ 0 & 0 & 1 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} x \\ y \\ z \end{bmatrix} \implies \begin{cases} x + y = x \\ y + z = y \\ z = z \end{cases} \implies y = 0, \; z = 0$$
    
- **Conclusione:** Gli unici autovettori sono i multipli di $\begin{bmatrix} 1 \\ 0 \\ 0 \end{bmatrix}$ (dimensione 1 invece di 3). Non avendo abbastanza autovettori per formare una base di $\mathbb{R}^3$, la matrice **NON È DIAGONALIZZABILE**[cite: 1].
    

## 6. Diagonalizzabilità con un parametro (Esercizio 4)

> **💡 In parole semplici:** Quando una matrice contiene un parametro $a$, i suoi autovalori cambiano a seconda del valore di $a$. La regola d'oro è: se gli autovalori sono tutti **diversi tra loro**, la matrice è _sempre_ diagonalizzabile. I guai (e i calcoli extra) arrivano solo per quei valori "critici" di $a$ che fanno coincidere due o più autovalori.

**Testo:** Per quali valori del parametro $a$ la matrice $A = \begin{bmatrix} 2a & 1 & 1 \\ 1 & a & 1 \\ -1 & 1 & a \end{bmatrix}$ è diagonalizzabile?

1. **Polinomio caratteristico e autovalori:**
    
    $$P_A(t) = \det \begin{bmatrix} 2a-t & 1 & 1 \\ 1 & a-t & 1 \\ -1 & 1 & a-t \end{bmatrix} = (2a-t)[(a-t)^2 - 1] - [a-t+1] + [1+a-t]$$
    
    I due termini tra parentesi quadre si elidono ($-(a-t+1) + (a-t+1) = 0$), lasciando:
    
    $$P_A(t) = (2a-t)[(a-t)^2 - 1] = (2a-t)(a-t-1)(a-t+1)$$
    
    Gli autovalori sono quindi: **$\lambda_1 = 2a$**, **$\lambda_2 = a+1$**, **$\lambda_3 = a-1$**.
    
2. **Analisi dei casi:**
    
    - **Se $a \neq \pm 1$:** I tre autovalori sono tutti distinti ($2a \neq a+1$ e $2a \neq a-1$), quindi **$A$ è diagonalizzabile**.
        
    - **Caso critico $a = 1$:** Gli autovalori diventano **$2, 2, 0$**. Verifichiamo quanti autovettori riusciamo a trovare:
        
        - _Per $\lambda = 2$:_
            
            $$\begin{bmatrix} 2 & 1 & 1 \\ 1 & 1 & 1 \\ -1 & 1 & 1 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} 2x \\ 2y \\ 2z \end{bmatrix} \implies \begin{cases} 2x + y + z = 2x \\ x + y + z = 2y \\ -x + y + z = 2z \end{cases} \implies \begin{cases} y = -z \\ x = 2y = -2z \end{cases}$$
            
            I vettori hanno forma $\mu \begin{bmatrix} 2 \\ 1 \\ -1 \end{bmatrix}$, quindi $\dim(V_2) = 1$.
            
        - _Per $\lambda = 0$:_
            
            $$\begin{cases} 2x + y + z = 0 \\ x + y + z = 0 \\ -x + y + z = 0 \end{cases} \implies \begin{cases} y = -z \\ x = 0 \end{cases} \implies \mu \begin{bmatrix} 0 \\ 1 \\ -1 \end{bmatrix} \implies \dim(V_0) = 1$$
            
        - _Conclusione per $a=1$:_ $\dim(V_2) + \dim(V_0) = 1 + 1 = 2 < 3$, quindi **non diagonalizzabile**.
            
    - **Caso critico $a = -1$:** Gli autovalori diventano **$-2, 0, -2$**.
        
        - _Per $\lambda = -2$:_
            
            $$\begin{cases} -2x + y + z = -2x \\ x - y + z = -2x \\ -x + y - z = -2z \end{cases} \implies \begin{cases} y = -z \\ x = -2y \end{cases} \implies \dim(V_{-2}) = 1$$
            
        - _Conclusione per $a=-1$:_ Esattamente come prima, $\dim(V_{-2}) = 1$ e $\dim(V_0) = 1$, quindi **non diagonalizzabile**.
            

## 7. Teoria: Molteplicità Algebrica vs Geometrica

> **💡 In parole semplici:** Questo teorema è una scorciatoia potentissima che ti evita metà dei conti negli esercizi!
> 
> - La **molteplicità algebrica** ($m_a$) è "quante volte" un autovalore compare come soluzione del polinomio caratteristico (l'esponente del suo fattore).
>     
> - La **molteplicità geometrica** ($m_g$) è "quanti autovettori indipendenti" produce quell'autovalore (la dimensione dell'autospazio $V_\lambda$).
>     
> 
> La legge dice che $m_g$ non può mai superare $m_a$ (al massimo la pareggia). Per essere diagonalizzabili, **ogni autovalore deve pareggiare il conto** ($m_g = m_a$). Appena ne becchi anche solo uno con $m_g < m_a$, puoi fermarti subito: la matrice non è diagonalizzabile!

### Definizioni e Proposizione

Sia $\lambda$ un autovalore di un endomorfismo $\varphi$ su uno spazio vettoriale $V$ con $\dim V = n$:

- **Molteplicità algebrica ($m_a(\lambda)$):** molteplicità di $\lambda$ come radice di $P_A(t)$.
    
- **Molteplicità geometrica ($m_g(\lambda)$):** $\dim V_\lambda$.
    

**Proposizione:** Per ogni autovalore $\lambda$, vale sempre:

$$1 \le \dim V_\lambda \le m_a(\lambda) \quad (\text{molt. geometrica} \le \text{molt. algebrica}) \text{[cite: 3]}$$

- **Idea della dimostrazione:** Poniamo $r = \dim V_\lambda$ e prendiamo una base $e_1, \dots, e_r$ di $V_\lambda$, completandola poi a una base di tutto $V$: $\{e_1, \dots, e_r, v_{r+1}, \dots, v_n\}$. Rispetto a questa base, la matrice di $\varphi$ assume una forma a blocchi:
    
    $$M = \left[\begin{array}{c\|c} \lambda I_r & * \\ \hline 0 & B \end{array}\right] \text{[cite: 3]}$$
    
    Calcolando il polinomio caratteristico (sviluppando lungo le prime $r$ colonne), si ottiene:
    
    $$P_A(t) = \det \left[\begin{array}{c\|c} (\lambda - t)I_r & * \\ \hline 0 & B - tI \end{array}\right] = (\lambda - t)^r \det(B - tI) = (\lambda - t)^r P_B(t) \text{[cite: 3]}$$
    
    Poiché $(\lambda - t)^r$ divide $P_A(t)$, la radice $\lambda$ ha molteplicità algebrica almeno $r$, cioè $m_a(\lambda) \ge r = \dim V_\lambda$[cite: 3].
    
- **Criterio definitivo di diagonalizzabilità:**
    
    $$\varphi \text{ è diagonalizzabile su } \mathbb{R} \iff \begin{cases} 1. \text{ Tutti gli autovalori di } \varphi \text{ sono reali (somma delle } m_a = n\text{)} \\ 2. \text{ Per ogni autovalore } \lambda, \; m_a(\lambda) = m_g(\lambda) \end{cases} \text{[cite: 3]}$$
    
    _Nota pratica:_ Nell'Esercizio 4, per $a=1$ bastava controllare $\lambda = 2$ (che aveva $m_a = 2$, ma $m_g = 1 < 2$) senza nemmeno calcolare $V_0$[cite: 3]!
    

## 8. Applicazioni del criterio (Esercizi 5, 6 e 7)

### Esercizio 5 (Utilizzo della scorciatoia)

**Testo:** Per quali valori di $k$ è diagonalizzabile $A = \begin{bmatrix} 3 & 1 & 0 \\ 1 & 3 & 0 \\ k & 0 & 2 \end{bmatrix}$?[cite: 3]

1. **Polinomio caratteristico:**
    
    $$P_A(\lambda) = \det \begin{bmatrix} 3-\lambda & 1 & 0 \\ 1 & 3-\lambda & 0 \\ k & 0 & 2-\lambda \end{bmatrix} = (2-\lambda)[(3-\lambda)^2 - 1] = (2-\lambda)(\lambda^2 - 6\lambda + 8) = (2-\lambda)^2(4-\lambda)$$
    
    Gli autovalori sono **$\lambda = 2$** (con $m_a = 2$) e **$\lambda = 4$** (con $m_a = 1$).
    
2. **Controllo su $\lambda = 2$ (l'unico con $m_a > 1$):**
    
    $$\begin{bmatrix} 3 & 1 & 0 \\ 1 & 3 & 0 \\ k & 0 & 2 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} 2x \\ 2y \\ 2z \end{bmatrix} \implies \begin{cases} 3x + y = 2x \\ x + 3y = 2y \\ kx + 2z = 2z \end{cases} \implies \begin{cases} x = -y \\ kx = 0 \end{cases} \text{[cite: 4]}$$
    
    - **Se $k \neq 0$:** Dalla seconda equazione ricaviamo $x = 0$, quindi anche $y = 0$. Resta libero solo $z$: gli autovettori sono multipli di $\begin{bmatrix} 0 \\ 0 \\ 1 \end{bmatrix}$, quindi $\dim(V_2) = 1 < 2 \implies$ **$A$ non è diagonalizzabile**.
        
    - **Se $k = 0$:** L'equazione $0 \cdot x = 0$ è sempre soddisfatta! Restano 2 parametri liberi ($y$ e $z$), quindi $\dim(V_2) = 2$ (una base è $\begin{bmatrix} 0 \\ 0 \\ 1 \end{bmatrix}, \begin{bmatrix} 1 \\ -1 \\ 1 \end{bmatrix}$). Poiché $\lambda = 4$ ha $m_a = 1$, ha automaticamente $m_g = 1$ (ha almeno un autovettore non nullo). Quindi per $k=0$ **$A$ è diagonalizzabile**.
        

### Esercizio 6 (Matrici simili e cambio di base)

> **💡 In parole semplici:** Due matrici rappresentano lo stesso endomorfismo in basi diverse se e solo se sono **simili**. Due matrici simili condividono tutte le proprietà profonde: stesso polinomio caratteristico, stessi autovalori e _stessa diagonalizzabilità_. Se una è diagonalizzabile e l'altra no, non potranno mai rappresentare la stessa trasformazione!

**Testo:** Sia $\varphi: \mathbb{R}^3 \to \mathbb{R}^3$ l'endomorfismo con matrice $A = \begin{bmatrix} 2 & 0 & 0 \\ 3 & 1 & 0 \\ 5 & 1 & 1 \end{bmatrix}$ rispetto alla base standard. È possibile che rispetto a un'altra base abbia matrice $B = \begin{bmatrix} 1 & 0 & 3 \\ 0 & 1 & 4 \\ 0 & 0 & 2 \end{bmatrix}$?

1. **Confronto dei polinomi caratteristici:** Essendo entrambe triangolari, il determinante è il prodotto degli elementi sulla diagonale:
    
    $$P_A(\lambda) = (2-\lambda)(1-\lambda)^2 \quad \text{e} \quad P_B(\lambda) = (1-\lambda)^2(2-\lambda)$$
    
    I polinomi sono identici! Non basta ancora per escludere che rappresentino lo stesso $\varphi$.
    
2. **Confronto delle molteplicità geometriche per $\lambda = 1$ (che ha $m_a = 2$):**
    
    - **Per $A$:**
        
        $$\begin{cases} 2x = x \\ 3x + y = y \\ 5x + y + z = z \end{cases} \implies x = 0, \; y = 0 \implies \dim(V_1) = 1 < 2$$
        
        Quindi $A$ (e perciò $\varphi$) **non è diagonalizzabile**[cite: 4].
        
    - **Per $B$:**
        
        $$\begin{cases} x + 3z = x \\ y + 4z = y \\ 2z = z \end{cases} \implies z = 0, \quad x, y \text{ arbitrari} \implies \dim(V_1) = 2$$
        
        Poiché anche $\lambda = 2$ ha un autovettore, $B$ **è diagonalizzabile**.
        
3. **Conclusione:** **No, non è possibile:** $B$ non può essere la matrice di $\varphi$ rispetto ad alcuna base, perché $B$ è diagonalizzabile mentre $\varphi$ non lo è.
    

### Esercizio 7 (Diagonalizzabilità su $\mathbb{R}$ e discriminante)

> **💡 In parole semplici:** Qui lavoriamo nei numeri reali ($\mathbb{R}$). Se il polinomio caratteristico di secondo grado ha il $\Delta < 0$, significa che gli autovalori sono numeri complessi (non reali): in questo caso, su $\mathbb{R}$, la matrice non è diagonalizzabile a prescindere.

**Testo:** Per quali valori di $a$ la matrice $A = \begin{bmatrix} 1 & -1 \\ 1 & a \end{bmatrix}$ è diagonalizzabile su $\mathbb{R}$?

1. **Polinomio caratteristico e discriminante ($\Delta$):**
    
    $$P_A(t) = \det \begin{bmatrix} 1-t & -1 \\ 1 & a-t \end{bmatrix} = (1-t)(a-t) + 1 = t^2 - (a+1)t + (a+1)$$
    
    Calcoliamo il discriminante $\Delta = b^2 - 4ac$:
    
    $$\Delta = (a+1)^2 - 4(a+1) = (a+1)(a+1-4) = (a+1)(a-3) \text{[cite: 5]}$$
    
2. **Studio del segno di $\Delta$:**
    
    - **$\Delta > 0 \iff a < -1 \text{ oppure } a > 3$:** $P_A(t)$ ha **due radici reali distinte** $\implies$ **$A$ è diagonalizzabile**.
        
    - **$\Delta < 0 \iff -1 < a < 3$:** Non esistono radici reali $\implies$ **$A$ non è diagonalizzabile su $\mathbb{R}$**.
        
    - **$\Delta = 0 \iff a = -1 \text{ oppure } a = 3$:** Abbiamo un solo autovalore reale con $m_a = 2$. Dobbiamo verificare se $m_g = 2$:
        
        - _Se $a = -1$:_ Sostituendo in $P_A(t) = t^2 = 0$, l'autovalore è **$\lambda = 0$**.
            
            $$\begin{bmatrix} 1 & -1 \\ 1 & -1 \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \end{bmatrix} \iff x = y \implies \dim(V_0) = 1 < 2 \implies \text{non diagonalizzabile} \text{[cite: 5]}$$
            
        - _Se $a = 3$:_ Sostituendo in $P_A(t) = t^2 - 4t + 4 = (t-2)^2 = 0$, l'autovalore è **$\lambda = 2$**.
            
            $$\begin{bmatrix} 1 & -1 \\ 1 & 3 \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} = \begin{bmatrix} 2x \\ 2y \end{bmatrix} \implies \begin{cases} x - y = 2x \\ x + 3y = 2y \end{cases} \iff x = -y \implies \dim(V_2) = 1 < 2 \implies \text{non diagonalizzabile} \text{[cite: 5]}$$
            

In definitiva, $A$ è diagonalizzabile su $\mathbb{R}$ esclusivamente per **$a < -1$** oppure **$a > 3$**

## . Esercizio di riepilogo: Diagonalizzazione su $\mathbb{R}$

> 💡 **In parole semplici:** Diagonalizzare una matrice significa trovare un "punto di vista" (una nuova base di vettori) in cui la trasformazione geometrica associata alla matrice diventa semplicissima: invece di mescolare le coordinate tra loro, si limita ad allungare o accorciare i vettori lungo gli assi della nuova base.

**Testo dell'esercizio:** Sia data la matrice:

$$A = \begin{bmatrix} 0 & 2 & 1 \\ 2 & 3 & 2 \\ 1 & 2 & 0 \end{bmatrix}$$

Trovare (se esistono) una matrice diagonale $D$ e una matrice invertibile $P$ tali che $A = P D P^{-1}$.

**Svolgimento e connessioni logiche:**

- **Condizione di partenza:** Le matrici $P$ e $D$ esistono se e solo se $A$ è **diagonalizzabile**. Dobbiamo quindi verificare se questa proprietà vale.
    
- **Passo 1 — Trovare gli autovalori:** Per capire se $A$ è diagonalizzabile, calcoliamo innanzitutto il suo polinomio caratteristico $P_A(t) = \det(A - tI)$:
    
    $$P_A(t) = \det \begin{bmatrix} -t & 2 & 1 \\ 2 & 3-t & 2 \\ 1 & 2 & -t \end{bmatrix} = -t[-t(3-t)-4] - 2[-2t-2] + 1[4-(3-t)] = -t^3 + 3t^2 + 9t + 5$$
    
    Notando che $t = -1$ è una radice (annulla il polinomio), possiamo scomporlo con Ruffini:
    
    $$P_A(t) = (t+1)(-t^2 + 4t + 5) = -(t+1)^2(t-5)$$
    
    Da questa fattorizzazione ricaviamo gli autovalori e le loro **molteplicità algebriche** (quante volte compaiono come radici):
    
    - $\lambda_1 = -1$ con molteplicità algebrica $2$.
        
    - $\lambda_2 = 5$ con molteplicità algebrica $1$.
        
- **Passo 2 — Trovare gli autovettori e verificare la diagonalizzabilità:** Poiché $\lambda_2 = 5$ ha molteplicità algebrica $1$, siamo già sicuri che il suo autospazio avrà dimensione $1$. Il vero test è su $\lambda_1 = -1$: per essere diagonalizzabile, il suo autospazio $V_{-1}$ deve avere dimensione $2$ (uguale alla molteplicità algebrica).
    
    - **Autovettori per $\lambda = -1$:** Risolviamo il sistema $(A + I)v = 0$:
        
        $$\begin{cases} x + 2y + z = 0 \\ 2x + 4y + 2z = 0 \\ x + 2y + z = 0 \end{cases} \iff x + 2y + z = 0$$
        
        Essendo una sola equazione in $3$ incognite, abbiamo $2$ parametri liberi ($\dim V_{-1} = 2$). **Conclusione: $A$ è diagonalizzabile!** Una base di $V_{-1}$ è data da:
        
        $$v_1 = \begin{bmatrix} 1 \\ 0 \\ -1 \end{bmatrix}, \quad v_2 = \begin{bmatrix} 1 \\ -1 \\ 1 \end{bmatrix}$$
        
    - **Autovettori per $\lambda = 5$:** Risolviamo il sistema $(A - 5I)v = 0$:
        
        $$\begin{cases} 2y + z = 5x \\ 2x + 3y + 2z = 5y \\ x + 2y = 5z \end{cases} \implies \begin{cases} x = z \\ y = 2z \end{cases}$$
        
        Una base di $V_5$ è quindi data dal vettore:
        
        $$v_3 = \begin{bmatrix} 1 \\ 2 \\ 1 \end{bmatrix}$$
        
- **Passo 3 — Costruire $D$ e $P$:** Mettendo insieme i vettori trovati otteniamo la base di autovettori $\mathcal{B} = \{v_1, v_2, v_3\}$.
    
    - Rispetto a questa base, l'applicazione lineare $v \mapsto Av$ è rappresentata dalla matrice diagonale $D$ (che ha gli autovalori sulla diagonale):
        
        $$D = \begin{bmatrix} -1 & 0 & 0 \\ 0 & -1 & 0 \\ 0 & 0 & 5 \end{bmatrix}$$
        
    - La matrice $P$ del cambiamento di base da $\{v_1, v_2, v_3\}$ alla base standard si ottiene semplicemente affiancando gli autovettori in colonna (nello stesso ordine degli autovalori in $D$):
        
        $$P = \begin{bmatrix} 1 & 1 & 1 \\ 0 & -1 & 2 \\ -1 & 1 & 1 \end{bmatrix}$$
        

## 9. I Numeri Complessi ($\mathbb{C}$)

> 💡 **In parole semplici:** Nei numeri reali ($\mathbb{R}$) un numero al quadrato non può mai essere negativo, il che ci blocca davanti a equazioni come $x^2 + 1 = 0$ (e quindi ci impedisce di trovare alcuni autovalori!). I numeri complessi nascono inventando un "mattoncino" nuovo, l'unità immaginaria $i$, definito proprio per avere $i^2 = -1$. Geometricamente, non sono più punti su una retta, ma punti su un intero piano.

**Definizione e struttura:** Un **numero complesso** è un'espressione della forma $z = a + bi$, dove $a, b \in \mathbb{R}$ e $i$ è un parametro formale con la proprietà fondamentale $i^2 = -1$. L'insieme dei numeri complessi si indica con $\mathbb{C}$.

- **Esempi:** $1 + 2i$, $3 - \sqrt{2}\,i$, $\pi - \sqrt[3]{\frac{2}{3}}\,i$.
    
- **Collegamento con i reali:** Ogni numero reale $a \in \mathbb{R}$ si può vedere come un numero complesso con parte immaginaria nulla ($a = a + 0 \cdot i$), quindi $\mathbb{R} \subset \mathbb{C}$.
    

**Operazioni e struttura di spazio vettoriale:** Se prendiamo due numeri complessi $z = a + bi$ e $z' = a' + b'i$:

1. **Somma:** $z + z' := (a + a') + (b + b')i$ (si sommano separatamente le parti reali e quelle immaginarie).
    
2. **Prodotto per uno scalare reale $\lambda \in \mathbb{R}$:** $\lambda z = \lambda(a + bi) := \lambda a + \lambda b i$.
    

- **Osservazione chiave (connessione con l'algebra lineare):** Con queste due operazioni, $\mathbb{C}$ ha la struttura di **spazio vettoriale su $\mathbb{R}$**. Una sua base è $\{1, i\}$, quindi $\dim_{\mathbb{R}} \mathbb{C} = 2$. Infatti, la mappa $a + bi \mapsto (a, b)$ definisce un isomorfismo tra $\mathbb{C}$ e il piano cartesiano $\mathbb{R}^2$.
    

**Il prodotto in $\mathbb{C}$:** A differenza di $\mathbb{R}^2$, in $\mathbb{C}$ possiamo anche moltiplicare due elementi tra loro usando le normali regole algebriche e ricordando che $i^2 = -1$:

$$z \cdot z' = (a + bi)(a' + b'i) = (aa' - bb') + (ab' + a'b)i$$

_(Nota: se $z = a \in \mathbb{R}$, questa formula si riduce al prodotto per scalare $az' = aa' + ab'i$)._

- **Esempi di calcolo:**
    
    - $i^2 = (0 + 1 \cdot i)(0 + 1 \cdot i) = -1$
        
    - $(1 + i)(1 - i) = 1 - i^2 = 2$
        
    - $(1 + i)^2 = 2i \implies (1 + i)^4 = (2i)^2 = -4$
        
    - $\left(-\frac{1}{2} + \frac{\sqrt{3}}{2}i\right)^2 = -\frac{1}{2} - \frac{\sqrt{3}}{2}i$, da cui elevando ancora: $\left(-\frac{1}{2} + \frac{\sqrt{3}}{2}i\right)^3 = \left(-\frac{1}{2} - \frac{\sqrt{3}}{2}i\right)\left(-\frac{1}{2} + \frac{\sqrt{3}}{2}i\right) = \frac{1}{4} + \frac{3}{4} = 1$
        
- **Conseguenza sulle equazioni di 2° grado:** Se il discriminante $\Delta \in \mathbb{R}$ è negativo ($\Delta < 0$), allora $(\sqrt{-\Delta}\,i)^2 = \Delta$. Di conseguenza, **ogni** polinomio di secondo grado $ax^2 + bx + c \in \mathbb{R}[x]$ ha sempre radici in $\mathbb{C}$.
    

## 10. Coniugato, Divisione e Teorema Fondamentale dell'Algebra

> 💡 **In parole semplici:** Il **coniugato** è lo "specchio" di un numero complesso rispetto all'asse reale (si cambia segno solo alla parte con la $i$). È uno strumento comodissimo perché moltiplicando un numero per il suo coniugato sparisce la $i$ e si ottiene un numero reale positivo: questo trucco ci permette di fare le divisioni tra numeri complessi e di dimostrare che le soluzioni complesse dei polinomi reali arrivano sempre in "coppie gemelle".

**Definizione di coniugato e proprietà:** Dato $z = a + bi \in \mathbb{C}$, il suo **coniugato** è $\bar{z} := a - bi$.

- **Osservazioni immediate:**
    
    - $z + \bar{z} = 2a \in \mathbb{R}$
        
    - $z \cdot \bar{z} = a^2 + b^2 \in \mathbb{R}$ (che è sempre $\ge 0$, ed è uguale a $0 \iff a = b = 0 \iff z = 0$)
        
    - $z = \bar{z} \iff z \in \mathbb{R}$
        
- **Come fare le divisioni in $\mathbb{C}$:** Proprio perché $z \cdot \bar{z} = a^2 + b^2$ è un numero reale (diverso da zero se $z \neq 0$), possiamo definire l'inverso di $z$ moltiplicando sopra e sotto per $\bar{z}$:
    
    $$\frac{1}{z} := \frac{\bar{z}}{a^2 + b^2}$$
    
    Da qui, il rapporto tra due numeri complessi $z'$ e $z$ diventa:
    
    $$\frac{z'}{z} = \frac{z'\bar{z}}{a^2 + b^2} = \frac{(aa' + bb') + (-ab' + a'b)i}{a^2 + b^2}$$
    
    Quindi in $\mathbb{C}$ si possono eseguire tutte e $4$ le operazioni fondamentali ($+, -, \times, \div$).
    
- **Compatibilità del coniugato con le operazioni:**
    
    $$\overline{(z + z')} = \bar{z} + \bar{z}' \quad \text{e} \quad \overline{(z \cdot z')} = \bar{z} \cdot \bar{z}'$$
    
    _(Verifica: $a+a' - (b+b')i = (a-bi) + (a'-b'i)$, e allo stesso modo $aa'-bb' - (ab'+a'b)i = (a-bi)(a'-b'i)$)._ In particolare, la mappa $z \mapsto \bar{z}$ è un'applicazione lineare su $\mathbb{C}$ visto come spazio vettoriale su $\mathbb{R}$.
    

**Dal grado 2 a qualsiasi grado: il Teorema Fondamentale dell'Algebra:** Abbiamo visto poco fa che ogni polinomio di grado $2$ ha radici in $\mathbb{C}$. Questo vale in realtà per qualsiasi grado!

- **Teorema (Fondamentale dell'Algebra):** Ogni polinomio non costante $f \in \mathbb{C}[x]$ a coefficienti complessi ammette almeno una radice in $\mathbb{C}$: esiste cioè $z_1 \in \mathbb{C}$ tale che $f(z_1) = 0$.
    
- **Corollario (Scomposizione completa):** Applicando la divisione con resto tra polinomi, possiamo scrivere $f = (x - z_1)f_1$, dove $f_1$ ha grado $\deg f - 1$. Ripetendo il ragionamento su $f_1, f_2, \dots$ fino a esaurire il grado, ogni polinomio $f \in \mathbb{C}[x]$ si fattorizza completamente in fattori di primo grado:
    
    $$f = c(x - z_1)^{m_1}(x - z_2)^{m_2}\cdots(x - z_r)^{m_r} \quad (\text{con } m_1, \dots, m_r > 0)$$
    
    In particolare, anche ogni polinomio a coefficienti reali $f \in \mathbb{R}[x]$ si scompone così, avendo in generale alcune radici reali e altre complesse.
    
- **Esempio:**
    
    $$x^3 - 1 = (x - 1)\left(x + \frac{1}{2} + \frac{\sqrt{3}}{2}i\right)\left(x + \frac{1}{2} - \frac{\sqrt{3}}{2}i\right)$$
    

**La regola delle radici coniugate (per polinomi reali):** Nell'esempio appena visto, $-\frac{1}{2} - \frac{\sqrt{3}}{2}i$ è esattamente il coniugato di $-\frac{1}{2} + \frac{\sqrt{3}}{2}i$. Non è un caso!

- **Proposizione:** Se $f \in \mathbb{R}[x]$ (ha coefficienti _reali_) e $z \in \mathbb{C}$ è una sua radice ($f(z) = 0$), allora anche il suo coniugato $\bar{z}$ è una radice ($f(\bar{z}) = 0$).
    
- **Dimostrazione:** Scrivendo $f(x) = a_n x^n + a_{n-1}x^{n-1} + \dots + a_0$ con $a_k \in \mathbb{R}$ (quindi $\bar{a}_k = a_k$), applichiamo il coniugato a entrambi i membri di $f(z) = 0$:
    
    $$0 = \bar{0} = \overline{f(z)} = \overline{a_n z^n + \dots + a_0} = a_n \bar{z}^n + a_{n-1}\bar{z}^{n-1} + \dots + a_0 = f(\bar{z})$$
    
    **Conclusione:** Le radici di un polinomio reale sono o reali, oppure si presentano sempre in **coppie di numeri complessi coniugati** (come accade per $ax^2 + bx + c$ con $\Delta < 0$, dove le radici sono $\frac{1}{2a}[-b \pm \sqrt{-\Delta}\,i]$).
    

## 11. Diagonalizzazione su $\mathbb{C}$

> 💡 **In parole semplici:** Una matrice con numeri reali a volte "non ce la fa" a essere diagonalizzata su $\mathbb{R}$ perché il suo polinomio caratteristico non ha abbastanza soluzioni reali (ad esempio nelle rotazioni, dove nessun vettore resta sulla stessa retta). Se però accettiamo vettori e autovalori complessi (passando da $\mathbb{R}^n$ a $\mathbb{C}^n$), il Teorema Fondamentale dell'Algebra ci garantisce che gli autovalori esistono _sempre_, sbloccando la diagonalizzazione!

**Teoria generale:** Tutta la teoria degli spazi vettoriali e delle applicazioni lineari funziona identicamente sostituendo $\mathbb{R}$ con $\mathbb{C}$. Una matrice reale $A \in M_{n\times n}(\mathbb{R})$ definisce naturalmente anche un'applicazione lineare $\mathbb{C}^n \to \mathbb{C}^n$ ($v \mapsto Av$), perché $\mathbb{R} \subset \mathbb{C}$. Poiché il polinomio caratteristico $P_A(t)$ ha **sempre** radici in $\mathbb{C}$, su $\mathbb{C}$ una matrice ha **sempre** autovalori e autovettori.

**Esempio 1 (Matrice di rotazione $2 \times 2$):**

$$A = \begin{bmatrix} 0 & -1 \\ 1 & 0 \end{bmatrix} \implies P_A(t) = \det \begin{bmatrix} -t & -1 \\ 1 & -t \end{bmatrix} = t^2 + 1$$

- **Su $\mathbb{R}$:** Non ci sono radici, quindi **nessun autovalore** (non è diagonalizzabile su $\mathbb{R}$).
    
- **Su $\mathbb{C}$:** $t^2 + 1 = (t + i)(t - i) \implies$ ha due autovalori distinti $\lambda_1 = i$ e $\lambda_2 = -i$, quindi **è diagonalizzabile su $\mathbb{C}$**!
    

**Esempio 2 (Matrice $3 \times 3$ non diagonalizzabile su $\mathbb{R}$, ma sì su $\mathbb{C}$):**

$$A = \begin{bmatrix} 2 & 0 & 0 \\ 1 & 2 & 1 \\ 0 & -1 & 2 \end{bmatrix} \implies P_A(t) = \det \begin{bmatrix} 2-t & 0 & 0 \\ 1 & 2-t & 1 \\ 0 & -1 & 2-t \end{bmatrix} = (2 - t)\big((2 - t)^2 + 1\big)$$

- **Su $\mathbb{R}$:** Il fattore $(2 - t)^2 + 1$ non ha radici reali. L'unico autovalore reale è $\lambda = 2$ (con molteplicità algebrica $1 < 3$), quindi **$A$ non è diagonalizzabile su $\mathbb{R}$**.
    
- **Su $\mathbb{C}$:** Scomponendo $(2-t)^2 + 1 = (2 + i - t)(2 - i - t)$, il polinomio caratteristico diventa:
    
    $$P_A(t) = (2 - t)(2 + i - t)(2 - i - t)$$
    
    Abbiamo quindi **tre autovalori distinti** ($2$, $2+i$, $2-i$), perciò **$A$ è diagonalizzabile su $\mathbb{C}$**!
    

**Calcolo degli autovettori su $\mathbb{C}$ (continuazione Esempio 2):**

- **Per $\lambda = 2$:**
    
    $$\begin{cases} 2x = 2x \\ x + 2y + z = 2y \\ -y + 2z = 2z \end{cases} \implies \begin{cases} y = 0 \\ x = -z \end{cases} \implies v_1 = \begin{bmatrix} 1 \\ 0 \\ -1 \end{bmatrix} \text{ (e suoi multipli)}$$
    
- **Per $\lambda = 2 + i$:**
    
    $$\begin{cases} 2x = (2+i)x \\ x + 2y + z = (2+i)y \\ -y + 2z = (2+i)z \end{cases} \implies \begin{cases} x = 0 \\ z = iy \end{cases} \implies v_2 = \begin{bmatrix} 0 \\ 1 \\ i \end{bmatrix} \text{ (e suoi multipli)}$$
    
- **Per $\lambda = 2 - i$:** In modo analogo (o prendendo il coniugato!), si ottiene $x = 0, z = -iy$:
    
    $$v_3 = \begin{bmatrix} 0 \\ 1 \\ -i \end{bmatrix} \text{ (e suoi multipli)}$$
    

In questa base $\{v_1, v_2, v_3\}$ di $\mathbb{C}^3$, la matrice $A$ diventa diagonale:

$$D = \begin{bmatrix} 2 & 0 & 0 \\ 0 & 2+i & 0 \\ 0 & 0 & 2-i \end{bmatrix}$$

## 12. Nuovo argomento: Il Prodotto Scalare nel piano

> 💡 **In parole semplici:** Finora abbiamo usato i vettori solo per fare somme, combinazioni lineari e trasformazioni, senza mai parlare di **lunghezze** o **angoli**. Il prodotto scalare è lo strumento che porta la geometria dentro l'algebra lineare: prende due vettori e restituisce un singolo numero reale che ci dice quanto i due vettori "puntano nella stessa direzione" (se fa $0$, sono perpendicolari!).

**Definizione geometrica:** Dati due vettori nel piano $v$ e $w$, il loro **prodotto scalare** è definito come:

$$v \cdot w := \Vert{}v\Vert{} \cdot \Vert{}w\Vert{} \cdot \cos\theta$$

dove $\Vert{}v\Vert{}$ indica la lunghezza (norma) del vettore $v$, e $\theta$ è l'angolo compreso tra $v$ e $w$.

**Proprietà immediate:**

- Il risultato è sempre un numero reale: $v \cdot w \in \mathbb{R}$.
    
- Moltiplicando un vettore per se stesso ($\theta = 0 \implies \cos 0 = 1$), si ottiene il quadrato della sua lunghezza: $v \cdot v = \Vert{}v\Vert{}^2$, da cui $\Vert{}v\Vert{} = \sqrt{v \cdot v} \ge 0$.
    
- **Condizione di ortogonalità:** Se i vettori sono perpendicolari ($\theta = \frac{\pi}{2} \implies \cos\frac{\pi}{2} = 0$), allora $v \cdot w = 0$.
    

**Formula algebrica in coordinate:** Se rispetto alla base standard $v$ ha coordinate $(a_1, a_2)$ e $w$ ha coordinate $(b_1, b_2)$, allora il prodotto scalare si calcola semplicemente moltiplicando le componenti corrispondenti e sommandole:

$$v \cdot w = a_1 b_1 + a_2 b_2$$

- **Dimostrazione (collegamento con la base standard):** Sia $\{e_1, e_2\}$ la base standard ortonormale del piano, con $e_1 = (1, 0)$ sull'asse orizzontale ed $e_2 = (0, 1)$ sull'asse verticale _(nota: negli appunti le coordinate di $e_1$ ed $e_2$ erano invertite per distrazione, ma nel grafico a lato sono disegnate correttamente)_. Proiettando $v$ sugli assi tramite gli angoli $\theta_1$ e $\theta_2$ che forma con $e_1$ ed $e_2$:
    
    $$v \cdot e_1 = \Vert{}v\Vert{} \cdot 1 \cdot \cos\theta_1 = a_1, \qquad v \cdot e_2 = \Vert{}v\Vert{} \cdot 1 \cdot \cos\theta_2 = a_2$$
    
    dove $v = a_1 e_1 + a_2 e_2$. Allo stesso modo, per $w = b_1 e_1 + b_2 e_2$, si ha $w \cdot e_1 = b_1$ e $w \cdot e_2 = b_2$. Sfruttando la linearità del prodotto scalare, otteniamo infine:
    
    $$v \cdot w = (a_1 e_1 + a_2 e_2) \cdot w = a_1(e_1 \cdot w) + a_2(e_2 \cdot w) = a_1 b_1 + a_2 b_2$$
## 13. Prodotto scalare e Norma (Pagina 72)

Per iniziare a parlare di geometria (angoli e lunghezze) negli spazi vettoriali come $\mathbb{R}^n$, abbiamo bisogno di uno strumento algebrico che prenda due vettori e ci restituisca un numero: il prodotto scalare.

**Definizione (Prodotto scalare standard):** Siano $v = \begin{bmatrix} a_1 \\ \vdots \\ a_n \end{bmatrix}$ e $w = \begin{bmatrix} b_1 \\ \vdots \\ b_n \end{bmatrix}$ due vettori in $\mathbb{R}^n$. Il loro **prodotto scalare** è:

$$\langle v, w \rangle := a_1 b_1 + \dots + a_n b_n \in \mathbb{R}$$

La funzione $\langle \cdot, \cdot \rangle : \mathbb{R}^n \times \mathbb{R}^n \to \mathbb{R}$ si chiama **prodotto scalare standard**.

**Proprietà fondamentali:**

1. **Simmetria:** $\langle v, w \rangle = \langle w, v \rangle \quad \forall v, w \in \mathbb{R}^n$.
    
2. **Bilinearità:** Per $v \in \mathbb{R}^n$ fisso, la funzione $w \mapsto \langle v, w \rangle \in \mathbb{R}$ è un'applicazione lineare $\mathbb{R}^n \to \mathbb{R}$. Allo stesso modo, per $w$ fisso, $v \mapsto \langle v, w \rangle$ è lineare.
    
3. **Positività (definita positiva):** $\forall v \in \mathbb{R}^n$, $\langle v, v \rangle \ge 0$, e $\langle v, v \rangle = 0 \iff v = 0$. _(Infatti, $\langle v, v \rangle = a_1^2 + a_2^2 + \dots + a_n^2$)._
    

**Definizione (Norma):** Se $v \in \mathbb{R}^n$, la sua **norma** è:

$$\Vert{}v\Vert{} := \sqrt{\langle v, v \rangle}$$

**Complemento (Prodotti scalari generici):** In generale, se $V$ è uno spazio vettoriale su $\mathbb{R}$, un prodotto scalare su $V$ si definisce come una qualunque funzione $V \times V \to \mathbb{R}$, $(v, w) \mapsto \langle v, w \rangle$ che soddisfa le proprietà 1), 2) e 3). Esistono molti prodotti scalari diversi: ad esempio, presi $\lambda_1 \ge 0, \dots, \lambda_n \ge 0$ (strettamente positivi affinché valga la proprietà 3) su $V = \mathbb{R}^n$, la formula $(v, w) \mapsto \lambda_1 a_1 b_1 + \dots + \lambda_n a_n b_n$ è un prodotto scalare. Il prodotto standard è il caso particolare in cui $\lambda_1 = \dots = \lambda_n = 1$, ed è quello con cui lavoreremo sempre.

> **In parole povere:** Il prodotto scalare è una "macchina" che moltiplica componente per componente due vettori e somma tutto. Se fai il prodotto scalare di un vettore con sé stesso e metti tutto sotto radice, ottieni la **norma**, che non è altro che la lunghezza del vettore (esattamente come il teorema di Pitagora!).

## 14. Ortogonalità e Sistemi Ortonormali (Pagine 72–73)

Una volta definita la lunghezza grazie al prodotto scalare, il passo successivo è generalizzare il concetto geometrico di perpendicolarità ("angolo di 90°") a spazi con qualsiasi numero di dimensioni.

**Definizione (Ortogonalità e Ortonormalità):**

- Due vettori $v, w \in \mathbb{R}^n$ sono **ortogonali** se $\langle v, w \rangle = 0$.
    
- Un insieme di vettori $v_1, \dots, v_r$ è un **sistema ortogonale** se $\langle v_i, v_j \rangle = 0$ per ogni $i \neq j$.
    
- Un insieme $v_1, \dots, v_r$ è un **sistema ortonormale (ON)** se è ortogonale e inoltre ogni vettore ha lunghezza 1, cioè $\langle v_i, v_i \rangle = 1$ per ogni $i$.
    

**Perché l'ortogonalità è così comoda? Perché garantisce subito l'indipendenza lineare!**

**Proposizione:** Un sistema ortogonale di vettori (non nulli) è **linearmente indipendente**.

- **Dimostrazione:** Sia $v_1, \dots, v_r$ un sistema ortogonale (negli appunti gli indici arrivano fino a $n$, per generalità li teniamo fino a $r$). Supponiamo di avere una combinazione lineare nulla:
    
    $$\alpha_1 v_1 + \alpha_2 v_2 + \dots + \alpha_r v_r = 0$$
    
    Applichiamo il prodotto scalare con $v_1$, cioè $\langle \cdot, v_1 \rangle$, a entrambi i membri. Per linearità otteniamo:
    
    $$\alpha_1 \underbrace{\langle v_1, v_1 \rangle}_{= \lambda \neq 0} + \alpha_2 \underbrace{\langle v_2, v_1 \rangle}_{= 0} + \dots + \alpha_r \underbrace{\langle v_r, v_1 \rangle}_{= 0} = 0$$
    
    Da cui $\alpha_1 \lambda = 0 \implies \alpha_1 = 0$. Ripetendo lo stesso trucco con $v_2, v_3, \dots, v_r$, si ottiene $\alpha_2 = \alpha_3 = \dots = \alpha_r = 0$.
    

**Esempio classico:** La base standard di $\mathbb{R}^n$, formata da $e_1 = \begin{bmatrix} 1 \\ 0 \\ \vdots \\ 0 \end{bmatrix}, e_2 = \begin{bmatrix} 0 \\ 1 \\ \vdots \\ 0 \end{bmatrix}, \dots, e_n = \begin{bmatrix} 0 \\ 0 \\ \vdots \\ 1 \end{bmatrix}$, è un sistema ortonormale.

> **In parole povere:** Due vettori sono **ortogonali** quando sono perpendicolari (prodotto scalare zero). Se sono anche lunghi 1, sono **ortonormali** (come gli assi cartesiani $x, y, z$). La magia è che dei vettori perpendicolari tra loro puntano in direzioni completamente diverse, quindi non possono mai essere combinazione l'uno dell'altro: sono automaticamente linearmente indipendenti!

## 15. Funzioni lineari e Sottospazio Ortogonale (Pagine 73–74)

C'è un legame fortissimo tra il prodotto scalare e le applicazioni lineari che vanno da $\mathbb{R}^n$ a $\mathbb{R}$. Questo legame ci permetterà di definire il "sottospazio ortogonale".

**Osservazione e Conclusione (Rappresentazione delle funzioni lineari):**

- Sappiamo che, fissato $v \in \mathbb{R}^n$, la funzione $\varphi_v : w \mapsto \langle v, w \rangle$ è lineare. Se $v = a_1 e_1 + \dots + a_n e_n$, allora $\langle v, e_i \rangle = a_i$ per $i = 1, \dots, n$.
    
- **Viceversa**, ogni funzione lineare $\varphi : \mathbb{R}^n \to \mathbb{R}$ è univocamente determinata dai valori che assume sulla base standard: $\varphi(e_1) =: a_1, \dots, \varphi(e_n) =: a_n$. Infatti, per un generico $w = b_1 e_1 + \dots + b_n e_n$, si ha:
    
    $$\varphi(w) = b_1 \varphi(e_1) + \dots + b_n \varphi(e_n) = a_1 b_1 + \dots + a_n b_n = \langle v, w \rangle$$
    
    dove $v = \begin{bmatrix} a_1 \\ \vdots \\ a_n \end{bmatrix}$.
    
- **Conclusione:** Per ogni funzione lineare $\varphi : \mathbb{R}^n \to \mathbb{R}$ esiste un vettore $v \in \mathbb{R}^n$ tale che $\varphi(w) = \langle v, w \rangle$ per ogni $w \in \mathbb{R}^n$, quindi $\varphi = \varphi_v$.
    

**Ora guardiamo il nucleo ($\text{Ker}$) di questa funzione $\varphi_v$: chi sono i vettori che vengono mandati in $0$?**

**Osservazione (Sottospazio ortogonale a un vettore):** Sia $v \in \mathbb{R}^n$ e consideriamo $\varphi_v : \mathbb{R}^n \to \mathbb{R}$. Il suo nucleo è:

$$\text{Ker}(\varphi_v) = \{ w \in \mathbb{R}^n : \langle v, w \rangle = 0 \}$$

- **Notazione e Terminologia:** Indichiamo $\text{Ker}(\varphi_v) =: \langle v \rangle^\perp$, che si chiama **sottospazio ortogonale a $v$**.
    
- Se $v = a_1 e_1 + \dots + a_n e_n$, allora:
    
    $$\langle v \rangle^\perp = \left\{ \begin{bmatrix} b_1 \\ \vdots \\ b_n \end{bmatrix} \in \mathbb{R}^n : a_1 b_1 + \dots + a_n b_n = 0 \right\}$$
    
    Quindi i vettori di $\langle v \rangle^\perp$ sono esattamente le soluzioni dell'equazione lineare omogenea $a_1 x_1 + \dots + a_n x_n = 0$.
    

**Generalizzazione a più vettori:** Se abbiamo più vettori $v_1, \dots, v_r \in \mathbb{R}^n$, il loro sottospazio ortogonale è l'intersezione dei singoli nuclei:

$$\langle v_1, \dots, v_r \rangle^\perp := \text{Ker}(\varphi_{v_1}) \cap \dots \cap \text{Ker}(\varphi_{v_r}) = \{ w \in \mathbb{R}^n : \langle v_1, w \rangle = \dots = \langle v_r, w \rangle = 0 \}$$

Questo equivale a dire che $w$ è ortogonale a tutto lo Span:

$$\langle v_1, \dots, v_r \rangle^\perp = \{ w \in \mathbb{R}^n : \langle v, w \rangle = 0 \quad \forall v \in \text{Span}(v_1, \dots, v_r) \}$$

_(Infatti, se $v = \alpha_1 v_1 + \dots + \alpha_r v_r$, per linearità $\langle v, w \rangle = \alpha_1 \langle v_1, w \rangle + \dots + \alpha_r \langle v_r, w \rangle = 0$)._

- **Ricetta pratica (Sistema omogeneo):** Se $v_1 = \begin{bmatrix} a_{11} \\ \vdots \\ a_{1n} \end{bmatrix}, \dots, v_r = \begin{bmatrix} a_{r1} \\ \vdots \\ a_{rn} \end{bmatrix}$, allora $\langle v_1, \dots, v_r \rangle^\perp$ coincide con le **soluzioni del sistema omogeneo** che ha questi vettori come righe:
    
    $$\begin{cases} a_{11}x_1 + a_{12}x_2 + \dots + a_{1n}x_n = 0 \\ \vdots \\ a_{r1}x_1 + a_{r2}x_2 + \dots + a_{rn}x_n = 0 \end{cases}$$
    

**Esempio svolto:** Siano $v = \begin{bmatrix} 1 \\ 1 \\ 1 \\ 0 \end{bmatrix}$ e $w = \begin{bmatrix} 0 \\ 1 \\ 1 \\ 1 \end{bmatrix} \in \mathbb{R}^4$. Troviamo una base di $\langle v, w \rangle^\perp$. Per la ricetta appena vista, dobbiamo risolvere il sistema:

$$\begin{cases} x_1 + x_2 + x_3 = 0 \\ x_2 + x_3 + x_4 = 0 \end{cases}$$

Riduciamo a gradini la matrice dei coefficienti (sottraendo la seconda riga dalla prima):

$$\begin{bmatrix} 1 & 1 & 1 & 0 \\ 0 & 1 & 1 & 1 \end{bmatrix} \leadsto \begin{bmatrix} 1 & 0 & 0 & -1 \\ 0 & 1 & 1 & 1 \end{bmatrix} \implies \begin{cases} x_1 = x_4 \\ x_2 = -x_3 - x_4 \end{cases}$$

Ponendo i parametri liberi $x_4 = s$ e $x_3 = t$, la soluzione generale è:

$$\begin{bmatrix} s \\ -s - t \\ t \\ s \end{bmatrix} = s \underbrace{\begin{bmatrix} 1 \\ -1 \\ 0 \\ 1 \end{bmatrix}}_{=: v_1} + t \underbrace{\begin{bmatrix} 0 \\ -1 \\ 1 \\ 0 \end{bmatrix}}_{=: v_2}$$

Quindi $\{v_1, v_2\}$ è una base di $\langle v, w \rangle^\perp$.

**Interpretazione geometrica:**

- In $\mathbb{R}^2$, se $v = \begin{bmatrix} a_1 \\ a_2 \end{bmatrix} \neq 0$, allora $\langle v \rangle^\perp$ è la **retta** passante per l'origine di equazione $a_1 x_1 + a_2 x_2 = 0$, perpendicolare al vettore $v$.
    
- In $\mathbb{R}^3$, se $v = \begin{bmatrix} a_1 \\ a_2 \\ a_3 \end{bmatrix} \neq 0$, allora $\langle v \rangle^\perp$ è il **piano** passante per l'origine di equazione $a_1 x_1 + a_2 x_2 + a_3 x_3 = 0$, perpendicolare a $v$.
    

> **In parole povere:** Il sottospazio ortogonale $V^\perp$ è l'insieme di **tutti i vettori perpendicolari** a un dato gruppo di vettori. Per trovarlo nella pratica basta mettere i vettori di partenza come righe di una matrice e risolvere il sistema omogeneo $Ax = 0$. Geometricamente, in 3D, se prendi un vettore che punta verso l'alto, il suo ortogonale è tutto il piano orizzontale su cui poggia!

## 16. Esistenza e completamento di Basi Ortonormali (Pagine 75–76)

Adesso che sappiamo cos'è un sottospazio ortogonale e come calcolarlo, ci chiediamo: ogni sottospazio possiede una base "perfetta" (cioè ortonormale)? La risposta è sì, e lo dimostriamo proprio usando il concetto di $\langle v \rangle^\perp$ appena introdotto!

**Teorema:** Ogni sottospazio $V \subset \mathbb{R}^n$ ammette una **base ortonormale (ON)**.

- **Dimostrazione (per induzione su $\dim V$):**
    
    - Se $\dim V = 0$ o $1$, il risultato è ovvio (basta dividere l'unico vettore non nullo per la sua norma).
        
    - Supponiamo $\dim V = m$ e che il teorema valga per tutti i sottospazi di dimensione $m - 1$.
        
    - Prendiamo un vettore $v \in V$ con $v \neq 0$ e consideriamo il suo ortogonale dentro $V$:
        
        $$\langle v \rangle^\perp := \{ w \in V : \langle v, w \rangle = 0 \}$$
        
        Questo insieme è il nucleo della funzione lineare $\varphi_v : V \to \mathbb{R}$ definita da $w \mapsto \langle v, w \rangle$. Poiché $v \neq 0$, la funzione non è identicamente nulla (infatti $\varphi_v(v) = \langle v, v \rangle > 0$), quindi $\text{Im}(\varphi_v) = \mathbb{R}$, che ha dimensione 1. Per il teorema della dimensione (nullità più rango), $\dim \langle v \rangle^\perp = m - 1$.
        
    - Per ipotesi induttiva, $\langle v \rangle^\perp$ ammette una base ortonormale $v_2, \dots, v_m$.
        
    - Normalizziamo $v$ definendo $v_1 := \frac{v}{\Vert{}v\Vert{}}$. Allora $\Vert{}v_1\Vert{} = 1$ e la lista $v_1, v_2, \dots, v_m$ è un sistema ortonormale (perché $v_1$ è ortogonale a tutti i $v_i \in \langle v \rangle^\perp$, e i $v_i$ sono ortogonali tra loro per ipotesi). Essendo un sistema ortogonale, è linearmente indipendente; avendo $m = \dim V$ vettori, è una base ON di $V$.
        

**Corollario 1 (Completamento a base ON):** Sia $v_1, \dots, v_r$ un sistema ortonormale in $\mathbb{R}^n$. Allora esistono dei vettori $v_{r+1}, \dots, v_n \in \mathbb{R}^n$ tali che $v_1, \dots, v_r, v_{r+1}, \dots, v_n$ sia una base ON di $\mathbb{R}^n$.

- **Dimostrazione:** Per il teorema precedente, il sottospazio $\langle v_1, \dots, v_r \rangle^\perp$ ammette una base ON $v_{r+1}, \dots, v_m$. Consideriamo l'applicazione lineare $\varphi : \mathbb{R}^n \to \mathbb{R}^r$ data da $v \mapsto \begin{bmatrix} \langle v_1, v \rangle \\ \vdots \\ \langle v_r, v \rangle \end{bmatrix}$. Poiché $v_1, \dots, v_r$ è ortonormale, le immagini $\varphi(v_1), \dots, \varphi(v_r)$ formano esattamente la base standard di $\mathbb{R}^r$, quindi $\text{Im}(\varphi) = \mathbb{R}^r$ (ha dimensione $r$). Allora $\dim \text{Ker}(\varphi) = n - \dim \text{Im}(\varphi) = n - r$. Ma $\text{Ker}(\varphi)$ è proprio $\langle v_1, \dots, v_r \rangle^\perp$, quindi il numero dei vettori della sua base deve essere $m - r = n - r$, cioè $m = n$. Mettendo insieme i due gruppi otteniamo una base ON di $\mathbb{R}^n$.
    

**Corollario 2 (Dimensione dell'ortogonale):** Dalla dimostrazione segue subito che:

$$\dim \langle v_1, \dots, v_r \rangle^\perp = n - r$$

**Corollario 3 (Decomposizione ortogonale di $\mathbb{R}^n$):** Se $V \subset \mathbb{R}^n$ è un sottospazio, definiamo $V^\perp := \{ w \in \mathbb{R}^n : \langle v, w \rangle = 0 \quad \forall v \in V \}$. Allora:

$$V \cap V^\perp = \{0\} \quad \text{e} \quad \text{Span}(V, V^\perp) = \mathbb{R}^n$$

In particolare, $\dim V + \dim V^\perp = n$ (ovvero $\mathbb{R}^n = V \oplus V^\perp$).

- **Dimostrazione:** Se $v \in V \cap V^\perp$, allora $v$ è ortogonale a sé stesso, quindi $\langle v, v \rangle = 0 \implies v = 0$. Per il resto, basta prendere una base ON $v_1, \dots, v_r$ di $V$: allora $V^\perp = \langle v_1, \dots, v_r \rangle^\perp$ e si applica direttamente il Corollario precedente.
    

> **In parole povere:** Qualsiasi sottospazio tu prenda, puoi sempre costruirci dentro una "griglia" di assi perpendicolari e lunghi 1 (base ortonormale). Inoltre, lo spazio intero $\mathbb{R}^n$ si spacca in due mondi perfettamente complementari: il sottospazio $V$ e il suo ortogonale $V^\perp$. L'unico punto che hanno in comune è l'origine, e la somma delle loro dimensioni fa sempre $n$.

## 17. A cosa serve una base ortonormale? (Pagina 76)

Fino ad ora abbiamo faticato per costruire queste basi ortonormali. Qui arriviamo al dunque: perché sono così utili nei calcoli? Perché **trovano le coordinate di un vettore senza dover risolvere alcun sistema lineare**!

**Proposizione (Formula delle coordinate):** Se $v_1, \dots, v_n$ è una base ON di $\mathbb{R}^n$, allora per ogni $v \in \mathbb{R}^n$:

$$v = \sum_{i=1}^n \langle v, v_i \rangle v_i$$

_(È la generalizzazione di ciò che abbiamo già visto per la base standard)._

- **Dimostrazione:** Poiché $v_1, \dots, v_n$ è una base, esistono unici scalari $\alpha_1, \dots, \alpha_n \in \mathbb{R}$ tali che $v = \alpha_1 v_1 + \dots + \alpha_n v_n$. Facciamo il prodotto scalare di $v$ con il generico vettore $v_i$ della base:
    
    $$\langle v, v_i \rangle = \langle \alpha_1 v_1 + \dots + \alpha_n v_n, v_i \rangle = \alpha_1 \langle v_1, v_i \rangle + \dots + \alpha_n \langle v_n, v_i \rangle = \alpha_i$$
    
    perché $\langle v_j, v_i \rangle = 0$ per $i \neq j$, mentre $\langle v_i, v_i \rangle = 1$ quando $i = j$. Quindi **il prodotto scalare dà direttamente le coordinate di un vettore rispetto a una base ON**.
    

**Esempi pratici:**

1. **Base standard:** In $\mathbb{R}^n$ con la base standard $e_1, \dots, e_n$, se $v = \begin{bmatrix} a_1 \\ \vdots \\ a_n \end{bmatrix}$, ogni coordinata è proprio $a_i = \langle v, e_i \rangle$.
    
2. **Base ruotata in $\mathbb{R}^2$:** Consideriamo i vettori $u_1 = \begin{bmatrix} \frac{1}{\sqrt{2}} \\ \frac{1}{\sqrt{2}} \end{bmatrix}$ e $u_2 = \begin{bmatrix} \frac{1}{\sqrt{2}} \\ -\frac{1}{\sqrt{2}} \end{bmatrix}$. Formano una base ON di $\mathbb{R}^2$ _(infatti $\langle u_1, u_2 \rangle = 0$ e $\langle u_1, u_1 \rangle = \langle u_2, u_2 \rangle = 1$)_. Vogliamo scrivere $e_1 = \begin{bmatrix} 1 \\ 0 \end{bmatrix}$ come combinazione lineare di $u_1$ e $u_2$. Invece di impostare un sistema, calcoliamo due prodotti scalari:
    
    - $\langle e_1, u_1 \rangle = 1 \cdot \frac{1}{\sqrt{2}} + 0 \cdot \frac{1}{\sqrt{2}} = \frac{1}{\sqrt{2}}$
        
    - $\langle e_1, u_2 \rangle = 1 \cdot \frac{1}{\sqrt{2}} + 0 \cdot \left(-\frac{1}{\sqrt{2}}\right) = \frac{1}{\sqrt{2}}$
        
    
    Quindi subito:
    
    $$\begin{bmatrix} 1 \\ 0 \end{bmatrix} = \frac{1}{\sqrt{2}} \begin{bmatrix} \frac{1}{\sqrt{2}} \\ \frac{1}{\sqrt{2}} \end{bmatrix} + \frac{1}{\sqrt{2}} \begin{bmatrix} \frac{1}{\sqrt{2}} \\ -\frac{1}{\sqrt{2}} \end{bmatrix}$$
    
    In maniera del tutto analoga, calcolando $\langle e_2, u_1 \rangle$ e $\langle e_2, u_2 \rangle$, si trova:
    
    $$\begin{bmatrix} 0 \\ 1 \end{bmatrix} = \frac{1}{\sqrt{2}} \begin{bmatrix} \frac{1}{\sqrt{2}} \\ \frac{1}{\sqrt{2}} \end{bmatrix} - \frac{1}{\sqrt{2}} \begin{bmatrix} \frac{1}{\sqrt{2}} \\ -\frac{1}{\sqrt{2}} \end{bmatrix}$$
    

> **In parole povere:** Di solito, per cambiare base e trovare le coordinate di un vettore devi risolvere un noioso sistema lineare. Se invece usi una **base ortonormale**, ti basta fare un semplice prodotto scalare tra il tuo vettore e ciascun vettore della base per ottenere subito i coefficienti giusti!

## 18. L'algoritmo di Gram-Schmidt (Pag. 77)

> 💡 **In parole semplici:** Immagina di avere una base di uno spazio vettoriale i cui vettori sono tutti "storti" tra loro e di lunghezze diverse. L'algoritmo di Gram-Schmidt è una ricetta passo-passo per "raddrizzarli" (renderli ortogonali, cioè perpendicolari tra loro) e normalizzarli (farli diventare tutti di lunghezza $1$), ottenendo così una **base ortonormale (ON)**.

**Obiettivo:** Come trovare esplicitamente una base ON in un sottospazio $V \subset \mathbb{R}^n$?

Procediamo costruendo la base un vettore alla volta, aumentando man mano la dimensione:

- **Caso $\dim V = 1$:** Se $V = \langle v \rangle$ (generato da un solo vettore non nullo $v$), basta dividere $v$ per la sua lunghezza (norma):
    
    $$\overline{v}_1 := \frac{v}{\Vert{}v\Vert{}}$$
    
    Questo singolo vettore forma già una base ON.
    
- **Caso $\dim V = 2$:** Partiamo da una base qualsiasi $v_1, v_2$ di $V$. Il primo vettore lo sistemiamo come sopra: $\overline{v}_1 = \frac{v_1}{\Vert{}v_1\Vert{}}$. Per il secondo, togliamo a $v_2$ la sua "ombra" (proiezione ortogonale) lungo $\overline{v}_1$, definendo:
    
    $$w_2 := v_2 - \langle v_2, \overline{v}_1 \rangle \overline{v}_1$$
    
    In questo modo $w_2$ risulta ortogonale a $\overline{v}_1$. Infatti, sfruttando la linearità del prodotto scalare e il fatto che $\langle \overline{v}_1, \overline{v}_1 \rangle = \Vert{}\overline{v}_1\Vert{}^2 = 1$:
    
    $$\langle w_2, \overline{v}_1 \rangle = \langle v_2, \overline{v}_1 \rangle - \langle v_2, \overline{v}_1 \rangle \underbrace{\langle \overline{v}_1, \overline{v}_1 \rangle}_{1} = 0$$
    
    Normalizzando $w_2$, cioè ponendo $\overline{v}_2 := \frac{w_2}{\Vert{}w_2\Vert{}}$, otteniamo che $\overline{v}_1, \overline{v}_2$ è una base ON.
    
- **Caso $\dim V = 3$:** Data una base $v_1, v_2, v_3$ di $V$, per prima cosa trasformiamo $v_1, v_2$ in una base ON $\overline{v}_1, \overline{v}_2$ del sottospazio $\langle v_1, v_2 \rangle$ (come abbiamo appena fatto per $\dim V = 2$). Poi prendiamo $v_3$ e gli sottraiamo le componenti lungo entrambi i vettori già sistemati:
    
    $$w_3 := v_3 - \langle v_3, \overline{v}_1 \rangle \overline{v}_1 - \langle v_3, \overline{v}_2 \rangle \overline{v}_2$$
    
    Verifichiamo che $w_3$ sia ortogonale sia a $\overline{v}_1$ sia a $\overline{v}_2$:
    
    $$\langle w_3, \overline{v}_1 \rangle = \langle v_3, \overline{v}_1 \rangle - \langle v_3, \overline{v}_1 \rangle \underbrace{\langle \overline{v}_1, \overline{v}_1 \rangle}_{1} - \langle v_3, \overline{v}_2 \rangle \underbrace{\langle \overline{v}_2, \overline{v}_1 \rangle}_{0} = 0$$
    
    $$\langle w_3, \overline{v}_2 \rangle = \langle v_3, \overline{v}_2 \rangle - \langle v_3, \overline{v}_1 \rangle \underbrace{\langle \overline{v}_1, \overline{v}_2 \rangle}_{0} - \langle v_3, \overline{v}_2 \rangle \underbrace{\langle \overline{v}_2, \overline{v}_2 \rangle}_{1} = 0$$
    
    Quindi, normalizzando con $\overline{v}_3 := \frac{w_3}{\Vert{}w_3\Vert{}}$, otteniamo la base ON $\overline{v}_1, \overline{v}_2, \overline{v}_3$.
    
- **Caso generale ($\dim V = n$):** Data una base $v_1, \dots, v_n$ di $V$, la modifichiamo passo dopo passo:
    
    - $v_1 \leadsto \overline{v}_1$ base ON di $\langle v_1 \rangle$
        
    - $v_1, v_2 \leadsto \overline{v}_1, \overline{v}_2$ base ON di $\langle v_1, v_2 \rangle$
        
    - $\dots$
        
    - $v_1, \dots, v_{n-1} \leadsto \overline{v}_1, \dots, \overline{v}_{n-1}$ base ON di $\langle v_1, \dots, v_{n-1} \rangle$
        
    
    All'$n$-esimo passo, definiamo:
    
    $$w_n := v_n - \langle v_n, \overline{v}_1 \rangle \overline{v}_1 - \langle v_n, \overline{v}_2 \rangle \overline{v}_2 - \dots - \langle v_n, \overline{v}_{n-1} \rangle \overline{v}_{n-1}$$
    
    Come nei casi precedenti, si verifica che $w_n$ è ortogonale a tutti i precedenti e che, ponendo $\overline{v}_n := \frac{w_n}{\Vert{}w_n\Vert{}}$, i vettori $\overline{v}_1, \dots, \overline{v}_n$ formano una base ON di $V$. Questo procedimento è proprio **l'algoritmo di Gram-Schmidt**.
    

## 19. Esempi pratici di Gram-Schmidt (Pag. 78)

> 💡 **In parole semplici:** Qui mettiamo le mani in pasta con i numeri! Vedrai tre cose molto utili: come funziona l'algoritmo nella pratica, il fatto che non dà sempre la base "più bella" possibile se si può trovare a occhio, e come completare una base ON di un piano per ottenere una base ON di tutto lo spazio $\mathbb{R}^3$.

**Esempio 1:** Sia $V = \operatorname{Span}\left(\begin{bmatrix} 1 \\ 1 \\ 0 \end{bmatrix}, \begin{bmatrix} 0 \\ 1 \\ 1 \end{bmatrix}\right) \subset \mathbb{R}^3$, dove chiamiamo i due vettori $v_1$ e $v_2$. Applichiamo Gram-Schmidt:

1. Calcoliamo $\Vert{}v_1\Vert{} = \sqrt{1^2+1^2+0^2} = \sqrt{2} \implies \overline{v}_1 := \begin{bmatrix} 1/\sqrt{2} \\ 1/\sqrt{2} \\ 0 \end{bmatrix}$.
    
2. Calcoliamo $\langle v_2, \overline{v}_1 \rangle = 0 \cdot \frac{1}{\sqrt{2}} + 1 \cdot \frac{1}{\sqrt{2}} + 1 \cdot 0 = \frac{1}{\sqrt{2}}$, quindi:
    
    $$w_2 := v_2 - \langle v_2, \overline{v}_1 \rangle \overline{v}_1 = \begin{bmatrix} 0 \\ 1 \\ 1 \end{bmatrix} - \frac{1}{\sqrt{2}} \begin{bmatrix} 1/\sqrt{2} \\ 1/\sqrt{2} \\ 0 \end{bmatrix} = \begin{bmatrix} 0 \\ 1 \\ 1 \end{bmatrix} - \begin{bmatrix} 1/2 \\ 1/2 \\ 0 \end{bmatrix} = \begin{bmatrix} -1/2 \\ 1/2 \\ 1 \end{bmatrix}$$
    
3. Normalizziamo $w_2$: la sua norma è $\Vert{}w_2\Vert{} = \sqrt{\frac{1}{4} + \frac{1}{4} + 1} = \sqrt{\frac{6}{4}} = \frac{\sqrt{3}}{\sqrt{2}}$, da cui:
    
    $$\overline{v}_2 := \frac{w_2}{\Vert{}w_2\Vert{}} = \begin{bmatrix} -1/\sqrt{6} \\ 1/\sqrt{6} \\ \sqrt{2}/\sqrt{3} \end{bmatrix}$$
    
    Quindi $\overline{v}_1, \overline{v}_2$ è una base ON di $V$.
    

**Esempio 2:** Sia $V = \operatorname{Span}\left(\begin{bmatrix} 1 \\ 1 \\ 0 \end{bmatrix}, \begin{bmatrix} 2 \\ 1 \\ 0 \end{bmatrix}\right) \subset \mathbb{R}^3$. Applicare Gram-Schmidt qui produce una base ON piuttosto "brutta" piena di radici annidate $(*)$:

$$\overline{v}_1 = \begin{bmatrix} 1/\sqrt{2} \\ 1/\sqrt{2} \\ 0 \end{bmatrix}, \qquad \overline{v}_2 = \frac{1}{\sqrt{28 - 18\sqrt{2}}} \begin{bmatrix} 2\sqrt{2}-3 \\ \sqrt{2}-3 \\ 0 \end{bmatrix}$$

Tuttavia, osservando i vettori, ci accorgiamo che $V$ è semplicemente il piano dei vettori con terza coordinata nulla:

$$V = \left\{ \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} \in \mathbb{R}^3 : x_3 = 0 \right\} \implies \begin{bmatrix} 1 \\ 0 \\ 0 \end{bmatrix}, \begin{bmatrix} 0 \\ 1 \\ 0 \end{bmatrix} \text{ è già una base ON!}$$

**Morale:** Gram-Schmidt produce _una_ base ON, non necessariamente la più semplice!

**Esempio 3 (e completamento a base di $\mathbb{R}^3$):** Sia $V = \operatorname{Span}(u_1, u_2) \subset \mathbb{R}^3$ con $u_1 = \begin{bmatrix} 1 \\ 1 \\ 0 \end{bmatrix}$ e $u_2 = \begin{bmatrix} 4 \\ 0 \\ -1 \end{bmatrix}$.

1. Come nell'esempio 1, $\Vert{}u_1\Vert{} = \sqrt{2}$ e $\overline{v}_1 := \begin{bmatrix} 1/\sqrt{2} \\ 1/\sqrt{2} \\ 0 \end{bmatrix}$.
    
2. Poi $\langle u_2, \overline{v}_1 \rangle = \frac{1}{\sqrt{2}} \langle u_2, u_1 \rangle = \frac{4}{\sqrt{2}}$, quindi:
    
    $$w_2 := \begin{bmatrix} 4 \\ 0 \\ -1 \end{bmatrix} - \frac{4}{\sqrt{2}} \cdot \frac{1}{\sqrt{2}} \begin{bmatrix} 1 \\ 1 \\ 0 \end{bmatrix} = \begin{bmatrix} 4 \\ 0 \\ -1 \end{bmatrix} - \begin{bmatrix} 2 \\ 2 \\ 0 \end{bmatrix} = \begin{bmatrix} 2 \\ -2 \\ -1 \end{bmatrix}$$
    
3. Poiché $\Vert{}w_2\Vert{} = \sqrt{2^2 + (-2)^2 + (-1)^2} = \sqrt{9} = 3$, otteniamo $\overline{v}_2 = \begin{bmatrix} 2/3 \\ -2/3 \\ -1/3 \end{bmatrix}$, che ha norma $1$, e $\overline{v}_1, \overline{v}_2$ è una base ON di $V$.
    

_Connessione logica:_ Ora che abbiamo una base ON di $V$, come la completiamo per ottenere una base ON di tutto $\mathbb{R}^3$? Basta trovare un vettore ortogonale a tutto $V$ (cioè nel complemento ortogonale $V^\perp$) e normalizzarlo!

- $V^\perp$ è il sottospazio delle soluzioni del sistema dato dall'ortogonalità con $u_1$ e $u_2$:
    
    $$\begin{cases} x_1 + x_2 = 0 \\ 4x_1 - x_3 = 0 \end{cases} \implies x_1 = -x_2 = \frac{x_3}{4}$$
    
- Scegliendo $x_3 = 4$, troviamo un vettore di base per $V^\perp$: $w = \begin{bmatrix} 1 \\ -1 \\ 4 \end{bmatrix}$.
    
- Normalizzandolo ($\Vert{}w\Vert{} = \sqrt{1+1+16} = \sqrt{18} = 3\sqrt{2}$), otteniamo $\overline{v}_3 := \begin{bmatrix} 1/(3\sqrt{2}) \\ -1/(3\sqrt{2}) \\ 4/(3\sqrt{2}) \end{bmatrix}$. Così $\overline{v}_1, \overline{v}_2, \overline{v}_3$ è una base ON di $\mathbb{R}^3$.
    

## 20. Il Teorema Spettrale e le sue applicazioni (Pag. 79 - inizio 80)

> 💡 **In parole semplici:** Perché ci importa così tanto saper costruire basi ortonormali? Perché entra in gioco uno dei teoremi più potenti dell'algebra lineare: il **Teorema Spettrale**. Ci dice che le **matrici simmetriche** sono "fantastiche": non solo sono sempre diagonalizzabili, ma puoi addirittura trovare una base di autovettori tutti ortogonali e di lunghezza $1$ (ortonormali)! Come bonus immediato, questo ci permette di calcolare la "radice quadrata" di una matrice.

**Definizione:** Una matrice quadrata $A \in M_{n \times n}(\mathbb{R})$ (con elementi $a_{ij}$) si dice **simmetrica** se $a_{ij} = a_{ji}$ per ogni $i, j$. In modo equivalente, $A = A^T$ (dove $A^T$ è la matrice trasposta).

**Lemma fondamentale:** Se $A \in M_{n \times n}(\mathbb{R})$ è simmetrica, allora per ogni coppia di vettori $v, w \in \mathbb{R}^n$ vale:

$$\langle Av, w \rangle = \langle v, Aw \rangle$$

rispetto al prodotto scalare standard (cioè puoi "spostare" $A$ da una parte all'altra del prodotto scalare senza cambiare il risultato).

- **Dimostrazione:** Scriviamo $A = [a_{ij}]$, $v = \begin{bmatrix} b_1 \\ \vdots \\ b_n \end{bmatrix}$ e $w = \begin{bmatrix} c_1 \\ \vdots \\ c_n \end{bmatrix}$. Il vettore $Av$ ha come $i$-esima componente $\sum_{j=1}^n a_{ij} b_j$. Facendo il prodotto scalare con $w$:
    
    $$\langle Av, w \rangle = \sum_{i,j=1}^n a_{ij} b_j c_i$$
    
    In modo analogo, scambiando i ruoli di $v$ e $w$, si ha $\langle v, Aw \rangle = \sum_{i,j=1}^n a_{ij} c_j b_i$. Poiché la matrice è simmetrica ($a_{ij} = a_{ji}$), rinominando gli indici $i \leftrightarrow j$ si vede subito che le due somme sono identiche.
    

**Teorema Spettrale (per matrici simmetriche reali):** Se $A \in M_{n \times n}(\mathbb{R})$ è simmetrica, allora **ogni autovalore di $A$ è reale**, ed **$A$ è diagonalizzabile in una base ON di autovettori** (in particolare, una matrice simmetrica è _sempre_ diagonalizzabile!).

**Un'applicazione: la radice quadrata di una matrice (Corollario):** Sia $A \in M_{n \times n}(\mathbb{R})$ una matrice simmetrica tale che ogni suo autovalore sia $\ge 0$. Allora esiste una matrice $\sqrt{A} \in M_{n \times n}(\mathbb{R})$ tale che $(\sqrt{A})^2 = A$.

- **Dimostrazione:**
    
    1. _Caso diagonale:_ Se $A = \operatorname{diag}(\lambda_1, \dots, \lambda_n)$, basta prendere $\sqrt{A} = \operatorname{diag}(\sqrt{\lambda_1}, \dots, \sqrt{\lambda_n})$, operazione lecita perché tutti i $\lambda_i \ge 0$.
        
    2. _Caso generale:_ Grazie al Teorema Spettrale, esiste una matrice invertibile $P$ tale che $D = P^{-1}AP$ sia diagonale (con gli autovalori sulla diagonale). Per il punto precedente esiste $\sqrt{D}$. Allora definiamo $\sqrt{A} := P \sqrt{D} P^{-1}$, che soddisfa:
        
        $$(\sqrt{A})^2 = (P \sqrt{D} P^{-1})(P \sqrt{D} P^{-1}) = P \sqrt{D} \sqrt{D} P^{-1} = P D P^{-1} = A$$
        
- **Osservazione:** $\sqrt{A}$ non esiste sempre! Ad esempio, se $n=1$ e $A = [a]$, $\sqrt{A}$ esiste nei reali solo se $a \ge 0$. Più in generale, se $A = B^2$, passando ai determinanti si ha $\det(A) = \det(B)^2 \ge 0$, quindi $\sqrt{A}$ non esiste mai se $\det(A) < 0$.
    

## 21. Dimostrazione del Teorema Spettrale (Pag. 80 - 81)

> 💡 **In parole semplici:** Come si dimostra il Teorema Spettrale? Il trucco è dividerlo in due tempi:
> 
> 1. **Prima parte:** Supponendo che gli autovalori siano già reali, usiamo la simmetria ($Lemma$) e l'induzione per "staccare" un autovettore alla volta e costruire la base ON.
>     
> 2. **Seconda parte:** Per dimostrare che gli autovalori sono davvero reali (e non numeri complessi), facciamo finta di lavorare nei numeri complessi $\mathbb{C}^n$ e usiamo le proprietà del coniugato per dimostrare che ogni autovalore $\lambda$ è uguale al suo coniugato $\overline{\lambda}$, il che significa che è un numero reale!
>     

### Parte 1: Costruzione della base ON di autovettori

**Proposizione:** Se $A \in M_{n \times n}(\mathbb{R})$ ha tutti gli autovalori reali e soddisfa $\langle Av, w \rangle = \langle v, Aw \rangle$ per ogni $v, w$, allora esiste una base ON di autovettori di $A$.

- **Dimostrazione (per induzione su $n$):**
    
    - _Passo base ($n=1$):_ Un solo vettore normalizzato $v$ è già una base ON.
        
    - _Passo induttivo ($n > 1$):_ Poiché gli autovalori sono reali, ne esiste almeno uno $\lambda \in \mathbb{R}$ con autovettore $v$ ($Av = \lambda v$). Normalizzandolo ($v \leadsto \frac{v}{\Vert{}v\Vert{}}$), possiamo supporre $\Vert{}v\Vert{} = 1$.
        
    - Consideriamo ora lo spazio ortogonale $V := \langle v \rangle^\perp$, che ha dimensione $n-1$. Osserviamo che $A$ manda $V$ in se stesso (cioè $\forall w \in V \implies Aw \in V$). Infatti:
        
        $$\langle v, Aw \rangle = \langle Av, w \rangle = \langle \lambda v, w \rangle = \lambda \underbrace{\langle v, w \rangle}_{0 \text{ perché } w \in \langle v \rangle^\perp} = 0$$
        
        Quindi $Aw \in \langle v \rangle^\perp = V$.
        
    - Poiché $\dim V = n-1$ e la restrizione di $A$ su $V$ soddisfa ancora le stesse ipotesi, per ipotesi induttiva esiste una base ON di autovettori $v_2, \dots, v_n$ per $A$ su $V$. Unendo $v_1 := v$ a questi vettori, otteniamo $v_1, v_2, \dots, v_n$, che è una base ON di autovettori su tutto $\mathbb{R}^n$.
        

### Parte 2: Perché gli autovalori sono reali? (Passaggio a $\mathbb{C}^n$)

Per dimostrare che ogni autovalore di una matrice simmetrica reale è reale, dobbiamo estendere temporaneamente i nostri strumenti ai vettori complessi $\mathbb{C}^n$.

- **Definizione (Prodotto scalare standard su $\mathbb{C}^n$):** Dati $v = \begin{bmatrix} a_1 \\ \vdots \\ a_n \end{bmatrix}, w = \begin{bmatrix} b_1 \\ \vdots \\ b_n \end{bmatrix} \in \mathbb{C}^n$, si definisce:
    
    $$\langle v, w \rangle := a_1 \overline{b_1} + a_2 \overline{b_2} + \dots + a_n \overline{b_n}$$
    
    dove $\overline{z} = a - bi$ è il **coniugato complesso** di $z = a + bi$.
    
- **Norma su $\mathbb{C}^n$:** $\Vert{}v\Vert{} = \sqrt{\langle v, v \rangle} = \sqrt{\vert{}a_1\vert{}^2 + \vert{}a_2\vert{}^2 + \dots + \vert{}a_n\vert{}^2}$ (nota: se $v, w \in \mathbb{R}^n$, questo coincide esattamente con il prodotto scalare standard su $\mathbb{R}^n$).
    
- **Proprietà principali:** Sono simili a quelle su $\mathbb{R}^n$, ma bisogna fare attenzione al coniugato:
    
    1. $\langle v, w \rangle = \overline{\langle w, v \rangle}$
        
    2. $\langle \lambda v, w \rangle = \lambda \langle v, w \rangle$, ma sul secondo argomento il coniugato "esce": $\langle v, \lambda w \rangle = \overline{\lambda} \langle v, w \rangle$ per ogni $\lambda \in \mathbb{C}$.
        

**Proposizione:** Sia $A \in M_{n \times n}(\mathbb{R})$ simmetrica, pensata come matrice in $M_{n \times n}(\mathbb{C})$. Allora $\langle Av, w \rangle = \langle v, Aw \rangle$ vale per ogni $v, w \in \mathbb{C}^n$.

- _Dimostrazione:_ Identica al caso reale, sfruttando il fatto che avendo elementi reali simmetrici vale $a_{ij} = a_{ji} = \overline{a_{ji}}$.
    

**Corollario (Realtà degli autovalori):** Se $A \in M_{n \times n}(\mathbb{R})$ è simmetrica, ogni suo autovalore è reale.

- **Dimostrazione:** Lavoriamo su $\mathbb{C}^n$. Sia $\lambda \in \mathbb{C}$ un autovalore di $A$ e $v \in \mathbb{C}^n$ ($v \neq 0$) un suo autovettore, cioè $Av = \lambda v$. Calcoliamo in due modi diversi $\langle Av, v \rangle$:
    
    $$\lambda \langle v, v \rangle = \langle \lambda v, v \rangle = \langle Av, v \rangle = \langle v, Av \rangle = \langle v, \lambda v \rangle = \overline{\lambda} \langle v, v \rangle$$
    
    Poiché $v \neq 0$, si ha $\langle v, v \rangle = \Vert{}v\Vert{}^2 \neq 0$, quindi possiamo semplificarlo da entrambi i lati ottenendo $\lambda = \overline{\lambda}$, il che dimostra che $\lambda \in \mathbb{R}$!
    

**Complemento (Forma complessa del Teorema Spettrale):** Se $A \in M_{n \times n}(\mathbb{C})$ è una matrice complessa tale che $a_{ij} = \overline{a_{ji}}$ per ogni $i, j$ (detta matrice **autoaggiunta** o **Hermitiana**), gli stessi identici argomenti dimostrano che gli autovalori di $A$ sono tutti reali ed $A$ è diagonalizzabile in una base ON di $\mathbb{C}^n$.

## 22. Esempio completo finale (Pag. 81)

> 💡 **In parole semplici:** Mettiamo insieme tutto il capitolo! Prendiamo una matrice $3 \times 3$ simmetrica, notiamo al volo che è diagonalizzabile e troviamo una sua **base ON di autovettori** combinando il calcolo degli autovalori con Gram-Schmidt.

Consideriamo la matrice:

$$A = \begin{bmatrix} -1 & 2 & -2 \\ 2 & -4 & 4 \\ -2 & 4 & -4 \end{bmatrix}$$

1. **Analisi preliminare e autovalore $\lambda = 0$:**
    
    - Vediamo subito che $A$ è simmetrica ($A = A^T$), quindi per il Teorema Spettrale è sicuramente diagonalizzabile in una base ON di autovettori.
        
    - Inoltre, le colonne di $A$ sono tutte multipli della prima (la 2ª è $-2$ volte la 1ª, la 3ª è $2$ volte la 1ª). Quindi $\operatorname{rango}(A) = 1 < 3$, il che implica $\ker(A) \neq \{0\}$ e perciò $\lambda_1 = 0$ è un autovalore con molteplicità geometrica $\dim \ker(A) = 3 - 1 = 2$.
        
2. **Ricerca del terzo autovalore e del suo autovettore:**
    
    - Poiché $\ker(A)$ ha dimensione $2$, c'è un solo altro autovalore $\lambda \neq 0$. Risolviamo $A \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \lambda \begin{bmatrix} x \\ y \\ z \end{bmatrix}$.
        
    - Confrontando le righe del sistema (la 2ª riga è $-2$ volte la 1ª, la 3ª è $2$ volte la 1ª), si vede subito che $\lambda y = -2\lambda x$ e $\lambda z = 2\lambda x$ (cioè $y = -2x$ e $z = 2x$).
        
    - Scegliendo $x = 1$, troviamo l'autovettore $w = \begin{bmatrix} 1 \\ -2 \\ 2 \end{bmatrix}$ _(nota: negli appunti c'è un piccolo segno invertito scrivendo $[1, 2, -2]^T$, ma il calcolo dell'autovalore subito sotto usa giustamente le componenti $1, -2, 2$: infatti $\lambda = -1(1) + 2(-2) - 2(2) = -1 - 4 - 4 = -9$, oppure con $w = \begin{bmatrix} -1 \\ 2 \\ -2 \end{bmatrix}$ si ha comunque $\lambda = -9$; negli appunti il conto $\lambda = -1\cdot 1 + 2\cdot 2 + 2\cdot 2 = 7$ corrisponde al vettore $\begin{bmatrix} 1 \\ 2 \\ -2 \end{bmatrix}$ con segno cambiato nell'ultima riga di $A$, ma il metodo è identico!)_.
        
    - Normalizziamo $w$: poiché $\Vert{}w\Vert{} = \sqrt{1^2 + 2^2 + (-2)^2} = 3$, il primo vettore della nostra base ON è $\frac{w}{\Vert{}w\Vert{}} = \begin{bmatrix} 1/3 \\ 2/3 \\ -2/3 \end{bmatrix}$.
        
3. **Base ON dell'autospazio $\ker(A)$ (relativo a $\lambda = 0$):**
    
    - Gli autovettori di $\ker(A)$ sono automaticamente ortogonali a $w$ (perché autovettori di autovalori distinti di una matrice simmetrica sono sempre ortogonali!), quindi ci basta trovare una base ON interna a $\ker(A) = \left\{ \begin{bmatrix} x \\ y \\ z \end{bmatrix} : -x + 2y - 2z = 0 \right\}$.
        
    - Scegliamo due vettori linearmente indipendenti che soddisfano l'equazione:
        
        $$v_1 = \begin{bmatrix} 0 \\ 1 \\ 1 \end{bmatrix}, \qquad v_2 = \begin{bmatrix} 2 \\ 1 \\ 0 \end{bmatrix}$$
        
        _(nota: negli appunti $v_2$ ha $-1$ nella seconda riga, ma per soddisfare $-x+2y-2z=0$ con $x=2, z=0$ serve $y=1$, come infatti risulta coerente con il prodotto scalare successivo)_.
        
    - Applichiamo **Gram-Schmidt** a $v_1, v_2$:
        
        - $\overline{v}_1 = \frac{v_1}{\Vert{}v_1\Vert{}} = \begin{bmatrix} 0 \\ 1/\sqrt{2} \\ 1/\sqrt{2} \end{bmatrix}$.
            
        - Calcoliamo $w_2 = v_2 - \langle v_2, \overline{v}_1 \rangle \overline{v}_1$: con $\langle \overline{v}_1, v_2 \rangle = \frac{1}{\sqrt{2}}$ (negli appunti usa $v_2 = [2, -1, 0]^T$ con $\langle \overline{v}_1, v_2 \rangle = -\frac{1}{\sqrt{2}}$), otteniamo:
            
            $$w_2 = \begin{bmatrix} 2 \\ -1 \\ 0 \end{bmatrix} + \frac{1}{\sqrt{2}} \cdot \frac{1}{\sqrt{2}} \begin{bmatrix} 0 \\ 1 \\ 1 \end{bmatrix} = \begin{bmatrix} 2 \\ -1/2 \\ 1/2 \end{bmatrix}$$
            
        - Infine normalizziamo: $\overline{v}_2 = \frac{w_2}{\Vert{}w_2\Vert{}}$ _(attenzione al piccolo refuso finale sul foglio: $\Vert{}w_2\Vert{} = \sqrt{4 + 1/4 + 1/4} = \sqrt{18/4} = \frac{3}{\sqrt{2}}$, quindi dividendo per la norma si ottiene $\overline{v}_2 = \frac{\sqrt{2}}{3} w_2$)_.