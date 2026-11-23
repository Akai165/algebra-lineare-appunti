## 1. Sistemi di Equazioni Lineari

### 1.1 Introduzione e Casi Notevoli in $\mathbb{R}^2$ e $\mathbb{R}^3$  

Un sistema di $2$ equazioni lineari a $2$ incognite ha la forma generale:  

$$\begin{cases} a_{11}x + a_{12}y = b_1 \\ a_{21}x + a_{22}y = b_2 \end{cases}$$

> [!example] I tre casi fondamentali in $\mathbb{R}^2$  
> 
> 1. **Soluzione unica (**$1$ **soluzione):**  
>     
>     $$> \begin{cases} x + y = 3 \\ x + 2y = 5 \end{cases} \xrightarrow{E_2 - E_1} y = 2 \implies x = 1 \implies P = (1, 2) >$$
> 2. **Infinite soluzioni (**$\infty$ **soluzioni):**  
>     
>     $$> \begin{cases} x + y = 3 \\ 2x + 2y = 6 \end{cases} \xrightarrow{E_2 - 2E_1} 0 = 0 >$$
>     
>     Le due equazioni descrivono la stessa retta; le soluzioni coincidono con tutti i punti della retta.
>     
> 3. **Nessuna soluzione (**$0$ **soluzioni / impossibile):**  
>     
>     $$> \begin{cases} x + y = 3 \\ 2x + 2y = 5 \end{cases} \xrightarrow{E_2 - 2E_1} 0 = -1 \quad (\text{impossibile}) >$$
>     
>     Le rette sono parallele e distinte: non esistono intersezioni comuni.
>     

> [!summary] Interpretazione Geometrica
> 
> - **In** $\mathbb{R}^2$**:** Ogni equazione lineare rappresenta una **retta**. L'insieme delle soluzioni è l'intersezione tra le rette (un punto, una retta intera, oppure l'insieme vuoto $\emptyset$).
>     
> - **In** $\mathbb{R}^3$**:** Un'equazione del tipo $a x + b y + c z = d$ rappresenta un **piano nello spazio 3-dimensionale**. Le soluzioni comuni di $3$ equazioni lineari a $3$ incognite corrispondono all'intersezione di $3$ piani:
>     
>     - Un singolo punto (soluzione unica);
>         
>     - Una retta (infinite soluzioni dipendenti da $1$ parametro);
>         
>     - Un piano (infinite soluzioni dipendenti da $2$ parametri);
>         
>     - Nessun punto in comune ($\emptyset$).
>         

### 1.2 Formulazione Generale

Un sistema di $n$ equazioni lineari in $m$ incognite si scrive:  

$$(E): \begin{cases} a_{11}x_1 + a_{12}x_2 + \dots + a_{1m}x_m = b_1 \\ a_{21}x_1 + a_{22}x_2 + \dots + a_{2m}x_m = b_2 \\ \quad \vdots \\ a_{n1}x_1 + a_{n2}x_2 + \dots + a_{nm}x_m = b_n \end{cases} \quad a_{ij}, b_i \in \mathbb{R}$$

> [!definition] Sistema Omogeneo Associato Il sistema $(E)$ è detto **omogeneo** se $b_1 = b_2 = \dots = b_n = 0$. In caso contrario, è detto **non omogeneo**, e ad esso si associa il **sistema omogeneo associato**:  
> 
> $$> (E_{\text{om}}): \begin{cases} > a_{11}x_1 + a_{12}x_2 + \dots + a_{1m}x_m = 0 \\ > a_{21}x_1 + a_{22}x_2 + \dots + a_{2m}x_m = 0 \\ > \quad \vdots \\ > a_{n1}x_1 + a_{n2}x_2 + \dots + a_{nm}x_m = 0 > \end{cases} >$$

> [!theorem] Teorema sulla Struttura delle Soluzioni
> 
> 1. Se $(c_1, \dots, c_m)$ e $(d_1, \dots, d_m)$ sono soluzioni del sistema completo $(E)$, allora la loro differenza: $$ > (c_1 - d_1, , c_2 - d_2, , \dots, , c_m - d_m) > $$ è soluzione del sistema omogeneo associato $(E_{\text{om}})$.
>     
> 2. Fissata una soluzione particolare $c = (c_1, \dots, c_m)$ di $(E)$, tutte le soluzioni di $(E)$ sono della forma: $$ > (c_1 + e_1, , c_2 + e_2, , \dots, , c_m + e_m) > $$ al variare di $e = (e_1, \dots, e_m)$ tra le soluzioni di $(E_{\text{om}})$.
>     

> [!note] Formula Mnemonica  
> 
> $$> \text{Soluzione Generale} = \text{Soluzione Particolare} + \text{Soluzione Omogenea} >$$

> [!tip] Corollario sull'Unicità Il vettore nullo $(0, \dots, 0)$ è sempre soluzione di $(E_{\text{om}})$. Di conseguenza:
> 
> - Se $(E)$ ammette soluzione, tale soluzione è **unica** se e solo se $(0, \dots, 0)$ è l'**unica soluzione** di $(E_{\text{om}})$.
>     
> - Geometricamente, $(E_{\text{om}})$ individua sottospazi (iperpiani) passanti per l'origine.
>     

### 1.3 Operazioni Elementari sulle Righe

Per risolvere o semplificare un sistema $(E)$, si eseguono tre tipi di operazioni che **non alterano l'insieme delle soluzioni**:

1. **Tipo A:** Moltiplicare un'equazione $E_i$ per uno scalare non nullo $\lambda \neq 0$:  
    
    $$E_i \mapsto \lambda E_i$$
2. **Tipo B:** Sostituire l'equazione $E_j$ con la somma di se stessa e di un multiplo di un'altra equazione $E_i$:  
    
    $$E_j \mapsto E_j + \lambda E_i \quad (j \neq i)$$
3. **Tipo C:** Scambiare tra loro due equazioni:  
    
    $$E_i \longleftrightarrow E_j$$

## 2. Metodo di Eliminazione di Gauss e RREF

Rappresentiamo i coefficienti del sistema tramite una matrice $n \times m$:  

$$A = \begin{pmatrix} a_{11} & a_{12} & \dots & a_{1m} \\ a_{21} & a_{22} & \dots & a_{2m} \\ \vdots & \vdots & \ddots & \vdots \\ a_{n1} & a_{n2} & \dots & a_{nm} \end{pmatrix} \in M_{n \times m}(\mathbb{R})$$

Le operazioni elementari sulle equazioni si traducono in **operazioni elementari sulle righe** ($R_i$).

### 2.1 Forma a Scalini per Righe (REF)

> [!definition] Matrice a Scalini e Pivot Una matrice è in **forma a scalini per righe** (Row Echelon Form) se:
> 
> 1. Tutte le righe interamente nulle $(0, \dots, 0)$ si trovano in fondo alla matrice.
>     
> 2. Il primo elemento diverso da zero di ogni riga non nulla (detto **pivot**) si trova strettamente a destra del pivot della riga precedente.
>     

```
Forma tipica a scalini:
[ *   *   *   *   * ]
[ 0   *   *   *   * ]
[ 0   0   0   *   * ]
[ 0   0   0   0   0 ]
```

### 2.2 Algoritmo di Gauss

1. Individuare la prima colonna non nulla da sinistra.
    
2. Tramite scambio di righe (operazione $C'$), posizionare un elemento non nullo in prima riga: questo sarà il **pivot**.
    
3. Tramite operazioni del tipo $R_j \mapsto R_j + \lambda R_1$ (operazione $B'$), annullare tutti gli elementi al di sotto del pivot.
    
4. Ignorare temporaneamente la prima riga e ripetere ricorsivamente i passi $1-3$ sulla sottomatrice rimanente fino al raggiungimento della forma a scalini.
    

### 2.3 Risoluzione dei Sistemi Non Omogenei

Per un sistema non omogeneo si costruisce la **matrice aumentata** (o completa) accostando la colonna dei termini noti:  

$$(A \mid b) = \begin{pmatrix} a_{11} & \dots & a_{1m} & b_1 \\ \vdots & \ddots & \vdots & \vdots \\ a_{n1} & \dots & a_{nm} & b_n \end{pmatrix}$$

> [!theorem] Criterio di Risolubilità (Classificazione delle Soluzioni) Portata la matrice aumentata $(A \mid b)$ in forma a scalini:
> 
> 1. **Incompatibile (**$0$ **soluzioni):** Se compare un pivot nell'**ultima colonna** (quella dei termini noti), si ottiene una riga del tipo $[0 \; 0 \; \dots \; 0 \mid c]$ con $c \neq 0$, ovvero l'equazione impossibile $0 = c$.
>     
> 2. **Soluzione Unica (**$1$ **soluzione):** Se non vi sono pivot nell'ultima colonna e **ogni colonna delle incognite contiene un pivot** (nessuna variabile libera).
>     
> 3. **Infinite Soluzioni (**$\infty^{m-r}$ **soluzioni):** Se non vi sono pivot nell'ultima colonna e sono presenti colonne non pivot tra le incognite. Le variabili corrispondenti alle colonne senza pivot sono **variabili libere** (parametri).
>     

> [!example] Esempio Guidato: Sistema con Infinite Soluzioni  
> 
> $$> \begin{cases} > x_1 + x_2 - 4x_3 = 1 \\ > 2x_1 + 3x_2 - 10x_3 = 2 \\ > 5x_1 - 3x_2 - 4x_3 = 5 > \end{cases} > \implies > \begin{pmatrix} > 1 & 1 & -4 & 1 \\ > 2 & 3 & -10 & 2 \\ > 5 & -3 & -4 & 5 > \end{pmatrix} >$$
> 
> Applicando le operazioni sulle righe:  
> 
> $$> \begin{pmatrix} > 1 & 1 & -4 & 1 \\ > 2 & 3 & -10 & 2 \\ > 5 & -3 & -4 & 5 > \end{pmatrix} > \xrightarrow{\substack{R_2 - 2R_1 \\ R_3 - 5R_1}} > \begin{pmatrix} > 1 & 1 & -4 & 1 \\ > 0 & 1 & -2 & 0 \\ > 0 & -8 & 16 & 0 > \end{pmatrix} > \xrightarrow{R_3 + 8R_2} > \begin{pmatrix} > 1 & 1 & -4 & 1 \\ > 0 & 1 & -2 & 0 \\ > 0 & 0 & 0 & 0 > \end{pmatrix} >$$
> 
> - I pivot sono nelle colonne $1$ e $2$.
>     
> - La colonna $3$ non contiene pivot $\implies x_3 = t$ è una **variabile libera**.
>     
> - Ricavando a ritroso:  
>     
>     $$> x_2 - 2t = 0 \implies x_2 = 2t >$$$$> x_1 + (2t) - 4t = 1 \implies x_1 = 1 + 2t >$$
> - Soluzione generale:  
>     
>     $$> \begin{pmatrix} x_1 \\ x_2 \\ x_3 \end{pmatrix} = \begin{pmatrix} 1 + 2t \\ 2t \\ t \end{pmatrix} = \underbrace{\begin{pmatrix} 1 \\ 0 \\ 0 \end{pmatrix}}_{\text{Particolare}} + t \underbrace{\begin{pmatrix} 2 \\ 2 \\ 1 \end{pmatrix}}_{\text{Omogenea}} >$$

### 2.4 Forma a Scalini Ridotta (RREF) e Algoritmo di Gauss-Jordan

> [!definition] Matrice in Forma a Scalini Ridotta (RREF) Una matrice a scalini è in **forma ridotta** se:
> 
> 1. Ogni pivot è uguale a $1$.
>     
> 2. Ogni pivot è l'**unico elemento non nullo** della propria colonna (gli elementi sopra e sotto il pivot sono tutti $0$).
>     

> [!tip] Algoritmo di Gauss-Jordan
> 
> 1. Portare la matrice in forma a scalini (Gauss).
>     
> 2. Normalizzare ogni riga non nulla dividendo per il rispettivo pivot: $R_i \mapsto \frac{1}{\lambda} R_i$.
>     
> 3. Procedendo dal basso verso l'alto (dall'ultimo pivot al primo), annullare tutti i coefficienti posti **sopra** i pivot tramite operazioni $R_j \mapsto R_j + \mu R_i$.
>     

## 3. Spazi Vettoriali e Sottospazi

### 3.1 Definizione Assiomatica di Spazio Vettoriale

Uno **spazio vettoriale** su $\mathbb{R}$ è un insieme non vuoto $V$ dotato di due operazioni:

- **Somma interna:** $+: V \times V \to V, \; (u, v) \mapsto u + v$  
    
- **Prodotto per scalare:** $\cdot: \mathbb{R} \times V \to V, \; (\lambda, v) \mapsto \lambda v$  
    

Tali operazioni soddisfano gli $8$ assiomi per ogni $u, v, w \in V$ e $\lambda, \mu \in \mathbb{R}$:

1. $(u + v) + w = u + (v + w)$ _(Associatività della somma)_
    
2. $u + v = v + u$ _(Commutatività della somma)_
    
3. Esiste $0 \in V$ tale che $v + 0 = v$ _(Elemento neutro della somma)_
    
4. Per ogni $v \in V$, esiste $-v \in V$ tale che $v + (-v) = 0$ _(Opposto)_
    
5. $\lambda(u + v) = \lambda u + \lambda v$ _(Distributività rispetto ai vettori)_
    
6. $(\lambda + \mu)v = \lambda v + \mu v$ _(Distributività rispetto agli scalari)_
    
7. $(\lambda \mu)v = \lambda(\mu v)$ _(Compatibilità dei prodotti)_
    
8. $1 \cdot v = v$ _(Elemento neutro del prodotto)_
    

> [!example] Esempi Notabili di Spazi Vettoriali
> 
> - **Spazio euclideo standard** $\mathbb{R}^n$**:** Vettori colonna di $n$ componenti reali.
>     
> - **Spazio delle matrici** $M_{n \times m}(\mathbb{R})$**:** Con somma e moltiplicazione per scalare componente per componente.
>     
> - **Spazio dei polinomi** $\mathbb{R}[x]$**:** Polinomi a coefficienti reali di grado arbitrario.
>     
> - **Polinomi di grado limitato** $\mathbb{R}[x]_{\le d}$**:** Polinomi di grado minore o uguale a $d$.
>     
> - **Spazi di funzioni** $\mathcal{F}(\mathbb{R}, \mathbb{R})$ **e** $C^0(\mathbb{R})$**:** Funzioni reali e funzioni continue.
>     

### 3.2 Sottospazi Vettoriali

> [!definition] Sottospazio Vettoriale Sia $V$ uno spazio vettoriale. Un sottoinsieme non vuoto $W \subseteq V$ è un **sottospazio vettoriale** di $V$ se è chiuso rispetto alle due operazioni:
> 
> 1. $\forall w_1, w_2 \in W \implies w_1 + w_2 \in W$  
>     
> 2. $\forall \lambda \in \mathbb{R}, \; \forall w \in W \implies \lambda w \in W$  
>     

> [!theorem] Proprietà dei Sottospazi Se $W \subseteq V$ è un sottospazio vettoriale, allora:
> 
> - $0_V \in W$ (poiché $0 \cdot v = 0$).
>     
> - Se $w \in W$, allora $-w = (-1)w \in W$.
>     
> - Un sottospazio è esso stesso uno spazio vettoriale su $\mathbb{R}$.
>     

> [!example] Esempi e Controesempi
> 
> - In $\mathbb{R}^n$, l'iperpiano $t_1 = 0$ è un sottospazio. Al contrario, $t_1 = a$ con $a \neq 0$ **non** è un sottospazio perché non contiene il vettore nullo $(0, \dots, 0)$.
>     
> - L'insieme $\{f \in \mathbb{R}[x] : \deg(f) \le d\}$ è un sottospazio.
>     
> - L'insieme $\{f \in \mathbb{R}[x] : \deg(f) = d\}$ ($d \ge 1$) **non** è un sottospazio (la somma di due polinomi di grado $d$ può avere grado inferiore).
>     
> - L'insieme delle soluzioni di un sistema lineare omogeneo ad $m$ incognite:  
>     
>     $$> W = \left\{ x \in \mathbb{R}^m : A x = 0 \right\} >$$
>     
>     è sempre un sottospazio vettoriale di $\mathbb{R}^m$.
>     

## 4. Combinazioni Lineari, Span e Indipendenza Lineare

### 4.1 Combinazione Lineare e Span

> [!definition] Combinazione Lineare e Span Siano $v_1, \dots, v_m \in V$.
> 
> - Una **combinazione lineare** di $v_1, \dots, v_m$ è un vettore della forma:  
>     
>     $$> v = \lambda_1 v_1 + \lambda_2 v_2 + \dots + \lambda_m v_m \quad (\lambda_i \in \mathbb{R}) >$$
> - Lo **Span** (sottospazio generato) è l'insieme di tutte le possibili combinazioni lineari:  
>     
>     $$> \operatorname{Span}(v_1, \dots, v_m) := \left\{ \sum_{i=1}^m \lambda_i v_i : \lambda_i \in \mathbb{R} \right\} >$$
>     
>     $\operatorname{Span}(v_1, \dots, v_m)$ è il più piccolo sottospazio vettoriale di $V$ che contiene i vettori $v_1, \dots, v_m$.
>     

### 4.2 Dipendenza e Indipendenza Lineare

> [!definition] Vettori Linearmente Indipendenti I vettori $v_1, \dots, v_m \in V$ sono detti **linearmente indipendenti** se l'equazione vettoriale:  
> 
> $$> \lambda_1 v_1 + \lambda_2 v_2 + \dots + \lambda_m v_m = 0 >$$
> 
> ammette esclusivamente la soluzione banale $\lambda_1 = \lambda_2 = \dots = \lambda_m = 0$.
> 
> Se invece esistono scalari $\lambda_1, \dots, \lambda_m$ **non tutti nulli** tali che $\sum_{i=1}^m \lambda_i v_i = 0$, i vettori si dicono **linearmente dipendenti**.

> [!theorem] Criterio di Dipendenza Lineare I vettori $v_1, \dots, v_m$ sono linearmente dipendenti se e solo se almeno uno di essi può essere scritto come combinazione lineare degli altri: $$ > \exists i \in {1, \dots, m} : v_i = \sum_{j \neq i} \mu_j v_j > $$

> [!proof] Dimostrazione $(\implies)$ Se sono dipendenti, esistono coefficienti non tutti nulli tali che $\sum_{k=1}^m \lambda_k v_k = 0$. Supponiamo $\lambda_i \neq 0$. Dividendo per $\lambda_i$: $$ > v_i = -\sum_{j \neq i} \frac{\lambda_j}{\lambda_i} v_j > $$ $(\impliedby)$ Se $v_i = \sum_{j \neq i} \mu_j v_j$, portando tutto a primo membro otteniamo:  
> 
> $$> \sum_{j \neq i} \mu_j v_j - v_i = 0 >$$
> 
> Il coefficiente di $v_i$ è $-1 \neq 0$, dunque i vettori sono linearmente dipendenti.

### 4.3 Rimozione di Vettori Ridondanti

> [!theorem] Proposizione Se $v_m$ è combinazione lineare di $v_1, \dots, v_{m-1}$, allora:  
> 
> $$> \operatorname{Span}(v_1, \dots, v_{m-1}, v_m) = \operatorname{Span}(v_1, \dots, v_{m-1}) >$$

> [!tip] Corollario Da ogni insieme di generatori $\{v_1, \dots, v_n\}$ è possibile estrarre un sottoinsieme $\{v_{i_1}, \dots, v_{i_r}\}$ ($r \le n$) di vettori linearmente indipendenti tale che: $$ > \operatorname{Span}(v_{i_1}, \dots, v_{i_r}) = \operatorname{Span}(v_1, \dots, v_n) > $$

## 5. Basi, Coordinate e Dimensione

### 5.1 Base di uno Spazio Vettoriale

> [!definition] Base Un insieme ordinato di vettori $\mathcal{B} = \{v_1, \dots, v_n\} \subset V$ è una **base** di $V$ se:
> 
> 1. I vettori $v_1, \dots, v_n$ sono **linearmente indipendenti**.
>     
> 2. I vettori $v_1, \dots, v_n$ sono **generatori** di $V$, ovvero $\operatorname{Span}(v_1, \dots, v_n) = V$.
>     

> [!example] Basi Canoniche (Standard)
> 
> - **In** $\mathbb{R}^n$**:**  
>     
>     $$> e_1 = \begin{pmatrix} 1 \\ 0 \\ \vdots \\ 0 \end{pmatrix}, \; e_2 = \begin{pmatrix} 0 \\ 1 \\ \vdots \\ 0 \end{pmatrix}, \; \dots, \; e_n = \begin{pmatrix} 0 \\ 0 \\ \vdots \\ 1 \end{pmatrix} >$$
> - **In** $\mathbb{R}[x]_{\le d}$**:** I monomi $\{1, x, x^2, \dots, x^d\}$.
>     
> - **In** $M_{2 \times 2}(\mathbb{R})$**:**  
>     
>     $$> \begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix}, \; \begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix}, \; \begin{pmatrix} 0 & 0 \\ 1 & 0 \end{pmatrix}, \; \begin{pmatrix} 0 & 0 \\ 0 & 1 \end{pmatrix} >$$

> [!theorem] Unicità delle Coordinate Sia $\mathcal{B} = \{v_1, \dots, v_n\}$ una base di $V$. Per ogni vettore $v \in V$ esiste **un'unica** sequenza di scalari $(\alpha_1, \dots, \alpha_n) \in \mathbb{R}^n$ tali che: $$ > v = \alpha_1 v_1 + \alpha_2 v_2 + \dots + \alpha_n v_n > $$ Gli scalari $\alpha_i$ sono detti **coordinate** di $v$ rispetto alla base $\mathcal{B}$.

### 5.2 Determinazione delle Equazioni Cartesiane da Generatori

Dato un sottospazio definito tramite lo Span di una base:  

$$W = \operatorname{Span}(v_1, \dots, v_r) \subseteq \mathbb{R}^n$$

Un vettore generico $b = (x_1, \dots, x_n)^T$ appartiene a $W$ se e solo se il sistema:  

$$\begin{pmatrix} v_1 & v_2 & \dots & v_r & \mid & x \end{pmatrix}$$

è compatibile. Applicando Gauss, le righe che si annullano nella matrice dei coefficienti impongono vincoli lineari sui termini noti: tali vincoli costituiscono le **equazioni cartesiane** di $W$.

> [!example] Esempio Trovare le equazioni cartesiane del sottospazio $W = \operatorname{Span}\left( \begin{pmatrix} 1 \\ 1 \\ 1 \end{pmatrix}, \begin{pmatrix} 1 \\ 3 \\ 1 \end{pmatrix} \right) \subset \mathbb{R}^3$:  
> 
> $$> \begin{pmatrix} > 1 & 1 & x_1 \\ > 1 & 3 & x_2 \\ > 1 & 1 & x_3 > \end{pmatrix} > \xrightarrow{\substack{R_2 - R_1 \\ R_3 - R_1}} > \begin{pmatrix} > 1 & 1 & x_1 \\ > 0 & 2 & x_2 - x_1 \\ > 0 & 0 & x_3 - x_1 > \end{pmatrix} >$$
> 
> Affinché il sistema sia compatibile (nessun pivot nell'ultima colonna), deve valere:  
> 
> $$> x_3 - x_1 = 0 \iff x_1 - x_3 = 0 >$$
> 
> Questa è l'equazione cartesiana cercata.

### 5.3 Teorema della Dimensione

> [!theorem] Lemma Fondamentale Sia $V$ uno spazio vettoriale generato da $n$ elementi. Allora ogni insieme di $r$ vettori con $r > n$ è **linearmente dipendente**.

> [!proof] Dimostrazione (Traccia) Siano $\{e_1, \dots, e_n\}$ una base di $V$ e siano $v_1, \dots, v_r \in V$ con $r > n$. Esprimendo ogni $v_j$ rispetto alla base: $$ > v_j = \sum_{i=1}^n a_{ij} e_i > $$ L'equazione di dipendenza lineare $\sum_{j=1}^r \lambda_j v_j = 0$ porta al sistema omogeneo: $$ > \sum_{j=1}^r a_{ij} \lambda_j = 0 \quad \text{per } i = 1, \dots, n > $$ Questo è un sistema lineare omogeneo di $n$ equazioni in $r$ incognite. Poiché $r > n$, il numero di colonne è strettamente maggiore del numero di righe; nella forma a scalini ci saranno al più $n$ pivot, garantendo l'esistenza di almeno $r - n \ge 1$ variabili libere. Il sistema ammette quindi infinite soluzioni non banali, e i vettori $v_1, \dots, v_r$ sono linearmente dipendenti.

> [!theorem] Definizione e Buona Posizione della Dimensione Tutte le basi di uno spazio vettoriale finitamente generato $V$ hanno la **stessa cardinalità**. Tale numero intero positivo $n$ è detto **dimensione** dello spazio vettoriale: $$ > \dim V = n > $$

> [!summary] Proprietà Cruciali Se $\dim V = n$:
> 
> 1. Più di $n$ vettori sono sempre linearmente dipendenti.
>     
> 2. Meno di $n$ vettori non possono mai generare $V$.
>     
> 3. Un insieme di $n$ vettori linearmente indipendenti è **automaticamente una base**.
>     
> 4. Un insieme di $n$ generatori di $V$ è **automaticamente una base**.
>     
> 5. **Teorema del Completamento della Base:** Se $\{v_1, \dots, v_m\}$ sono linearmente indipendenti e $m < n$, possono sempre essere completati a una base di $V$ aggiungendo $n - m$ vettori scelti tra i vettori di una base nota (es. la base standard).
>     

## 6. Operazioni tra Sottospazi e Formula di Grassmann

### 6.1 Intersezione e Somma di Sottospazi

Siano $V_1, V_2 \subseteq V$ due sottospazi vettoriali:

- **Intersezione:**  
    
    $$V_1 \cap V_2 = \{ v \in V : v \in V_1 \text{ e } v \in V_2 \}$$
    
    $V_1 \cap V_2$ è sempre un sottospazio vettoriale di $V$.
    
- **Somma:**  
    
    $$V_1 + V_2 = \{ v_1 + v_2 : v_1 \in V_1, \, v_2 \in V_2 \}$$
    
    $V_1 + V_2$ è il più piccolo sottospazio vettoriale che contiene sia $V_1$ sia $V_2$.
    

> [!warning] Attenzione: Somma vs Unione L'unione insiemistica $V_1 \cup V_2$ **non è** (in generale) un sottospazio vettoriale. Lo spazio somma rappresenta invece lo Span dell'unione:  
> 
> $$> V_1 + V_2 = \operatorname{Span}(V_1 \cup V_2) >$$

### 6.2 Formula di Grassmann

> [!theorem] Teorema di Grassmann Siano $V_1$ e $V_2$ due sottospazi vettoriali a dimensione finita di uno spazio $V$. Allora:
> 
> $$\dim(V_1 + V_2) = \dim V_1 + \dim V_2 - \dim(V_1 \cap V_2)$$

> [!proof] ### Dimostrazione Completa (Formula di Grassmann)
> Sia $r = \dim(V_1 \cap V_2)$, e sia $\{e_1, \dots, e_r\}$ una base dell'intersezione $V_1 \cap V_2$. Per il teorema del completamento della base:
> - Completiamo $\{e_1, \dots, e_r\}$ a una base di $V_1$:
    
    $$\mathcal{B}_{V_1} = \{e_1, \dots, e_r, \, v_{r+1}, \dots, v_n\} \implies \dim V_1 = n$$
    
- Completiamo $\{e_1, \dots, e_r\}$ a una base di $V_2$:
    
    $$\mathcal{B}_{V_2} = \{e_1, \dots, e_r, \, w_{r+1}, \dots, w_m\} \implies \dim V_2 = m$$
    

Mostriamo che l'insieme:

$$\mathcal{B} = \{e_1, \dots, e_r, \, v_{r+1}, \dots, v_n, \, w_{r+1}, \dots, w_m\}$$

è una base di $V_1 + V_2$. La cardinalità di $\mathcal{B}$ è:

$$r + (n - r) + (m - r) = n + m - r = \dim V_1 + \dim V_2 - \dim(V_1 \cap V_2)$$

**1. Generazione** Ogni $v \in V_1 + V_2$ si scrive come $v = v_1 + v_2$, con $v_1 \in V_1$ e $v_2 \in V_2$. Poiché $v_1 \in \operatorname{Span}(\mathcal{B}_{V_1})$ e $v_2 \in \operatorname{Span}(\mathcal{B}_{V_2})$, la loro somma è combinazione lineare degli elementi di $\mathcal{B}$.

**2. Indipendenza Lineare** Poniamo una combinazione lineare nulla:

$$\sum_{i=1}^r \lambda_i e_i + \sum_{j=r+1}^n \mu_j v_j + \sum_{k=r+1}^m \nu_k w_k = 0$$

Isolando i termini con $w$:

$$\underbrace{\sum_{i=1}^r \lambda_i e_i + \sum_{j=r+1}^n \mu_j v_j}_{\in V_1} = \underbrace{-\sum_{k=r+1}^m \nu_k w_k}_{\in V_2}$$

Il vettore $-\sum_{k=r+1}^m \nu_k w_k$ appartiene sia a $V_2$ che a $V_1$, dunque appartiene a $V_1 \cap V_2$. Essendo $\{e_1, \dots, e_r\}$ una base di $V_1 \cap V_2$, tale vettore deve potersi scrivere come combinazione lineare di $e_1, \dots, e_r$:

$$-\sum_{k=r+1}^m \nu_k w_k = \sum_{i=1}^r \alpha_i e_i \iff \sum_{i=1}^r \alpha_i e_i + \sum_{k=r+1}^m \nu_k w_k = 0$$

Poiché $\{e_1, \dots, e_r, \, w_{r+1}, \dots, w_m\}$ è una base di $V_2$, tutti i suoi vettori sono linearmente indipendenti, per cui:

$$\nu_{r+1} = \dots = \nu_m = 0 \quad (\text{e } \alpha_i = 0)$$

Sostituendo $\nu_k = 0$ nell'equazione originaria, otteniamo:

$$\sum_{i=1}^r \lambda_i e_i + \sum_{j=r+1}^n \mu_j v_j = 0$$

Poiché $\{e_1, \dots, e_r, \, v_{r+1}, \dots, v_n\}$ è una base di $V_1$, i suoi vettori sono anch'essi linearmente indipendenti:

$$\lambda_1 = \dots = \lambda_r = \mu_{r+1} = \dots = \mu_n = 0$$

Tutti i coefficienti sono nulli $\implies \mathcal{B}$ è linearmente indipendente, dunque è una base di $V_1 + V_2$.

## 7. Esercizi Tipici Svolti

### Esercizio 1: Dimensione e Base di Somma e Intersezione in $\mathbb{R}^4$  

In $\mathbb{R}^4$, siano dati i sottospazi:

$$V = \left\{ x \in \mathbb{R}^4 : \begin{cases} x_1 + 2x_2 + x_3 = 0 \\ -x_1 - x_2 + 3x_4 = 0 \end{cases} \right\}, \quad W = \operatorname{Span}\left( w_1 = \begin{pmatrix} 2 \\ 0 \\ 1 \\ 1 \end{pmatrix}, \, w_2 = \begin{pmatrix} 3 \\ -2 \\ 0 \\ 1 \end{pmatrix} \right)$$

#### 1. Base e Dimensione di $V$  

La matrice dei coefficienti associata a $V$ è:

$$\begin{pmatrix} 1 & 2 & 1 & 0 \\ -1 & -1 & 0 & 3 \end{pmatrix} \xrightarrow{R_2 + R_1} \begin{pmatrix} 1 & 2 & 1 & 0 \\ 0 & 1 & 1 & 3 \end{pmatrix}$$

I pivot si trovano nelle colonne $1$ e $2$; le variabili libere sono $x_3$ e $x_4$.

$$x_2 = -x_3 - 3x_4$$$$x_1 = -2x_2 - x_3 = -2(-x_3 - 3x_4) - x_3 = x_3 + 6x_4$$

Il vettore generico di $V$ è:

$$\begin{pmatrix} x_1 \\ x_2 \\ x_3 \\ x_4 \end{pmatrix} = x_3 \begin{pmatrix} 1 \\ -1 \\ 1 \\ 0 \end{pmatrix} + x_4 \begin{pmatrix} 6 \\ -3 \\ 0 \\ 1 \end{pmatrix} \implies \dim V = 2, \quad \mathcal{B}_V = \left\{ \begin{pmatrix} 1 \\ -1 \\ 1 \\ 0 \end{pmatrix}, \begin{pmatrix} 6 \\ -3 \\ 0 \\ 1 \end{pmatrix} \right\}$$

#### 2. Dimensione di $W$  

I due vettori $w_1, w_2$ non sono proporzionali $\implies \dim W = 2$.

#### 3. Dimensione e Base di $V + W$  

$V + W = \operatorname{Span}(v_1, v_2, w_1, w_2)$. Costruiamo la matrice per colonne e riduciamo con Gauss:

$$\begin{pmatrix} 1 & 6 & 2 & 3 \\ -1 & -3 & 0 & -2 \\ 1 & 0 & 1 & 0 \\ 0 & 1 & 1 & 1 \end{pmatrix} \xrightarrow{\text{Gauss}} \begin{pmatrix} 1 & 6 & 2 & 3 \\ 0 & 3 & 2 & 1 \\ 0 & 0 & 3 & -3 \\ 0 & 0 & 0 & 0 \end{pmatrix}$$

Otteniamo $3$ pivot $\implies \dim(V + W) = 3$. Una base di $V + W$ è formata dalle prime tre colonne: $\{v_1, v_2, w_1\}$.

#### 4. Dimensione e Base di $V \cap W$ tramite Grassmann

Applicando la formula di Grassmann:

$$\dim(V \cap W) = \dim V + \dim W - \dim(V + W) = 2 + 2 - 3 = 1$$

Per trovare una base esplicita, cerchiamo le combinazioni $\lambda_1 w_1 + \lambda_2 w_2 \in W$ che soddisfano le equazioni di $V$:

$$\lambda_1 \begin{pmatrix} 2 \\ 0 \\ 1 \\ 1 \end{pmatrix} + \lambda_2 \begin{pmatrix} 3 \\ -2 \\ 0 \\ 1 \end{pmatrix} = \begin{pmatrix} 2\lambda_1 + 3\lambda_2 \\ -2\lambda_2 \\ \lambda_1 \\ \lambda_1 + \lambda_2 \end{pmatrix}$$

Sostituendo nelle equazioni di $V$:

$$\begin{cases} (2\lambda_1 + 3\lambda_2) + 2(-2\lambda_2) + (\lambda_1) = 0 \implies 3\lambda_1 - \lambda_2 = 0 \quad (\text{ovvero } \lambda_1 = \lambda_2 \text{ dai conti}) \\ -(2\lambda_1 + 3\lambda_2) - (-2\lambda_2) + 3(\lambda_1 + \lambda_2) = 0 \implies \lambda_1 - \lambda_2 = 0 \end{cases}$$

Ponendo $\lambda_1 = \lambda_2 = 1$:

$$w_1 + w_2 = \begin{pmatrix} 5 \\ -2 \\ 1 \\ 2 \end{pmatrix} \implies \mathcal{B}_{V \cap W} = \left\{ \begin{pmatrix} 5 \\ -2 \\ 1 \\ 2 \end{pmatrix} \right\}$$

### Esercizio 2: Completamento a una Base di $\mathbb{R}^3$  

Dati i vettori:

$$u_1 = \begin{pmatrix} 1 \\ -1 \\ 1 \end{pmatrix}, \quad u_2 = \begin{pmatrix} -1 \\ 1 \\ -1 \end{pmatrix}, \quad u_3 = \begin{pmatrix} -1 \\ -1 \\ 1 \end{pmatrix}$$

1. **Verificare se formano una base:** Riduciamo la matrice formata dai tre vettori:
    
    $$\begin{pmatrix} 1 & -1 & -1 \\ -1 & 1 & -1 \\ 1 & -1 & 1 \end{pmatrix} \xrightarrow{\substack{R_2 + R_1 \\ R_3 - R_1}} \begin{pmatrix} 1 & -1 & -1 \\ 0 & 0 & -2 \\ 0 & 0 & 2 \end{pmatrix} \xrightarrow{R_3 + R_2} \begin{pmatrix} 1 & -1 & -1 \\ 0 & 0 & -2 \\ 0 & 0 & 0 \end{pmatrix}$$
    
    Ci sono solo $2$ pivot $\implies$ i vettori sono linearmente dipendenti e generano un sottospazio di dimensione $2$. I pivot cadono nelle colonne $1$ e $3$, quindi $u_1$ e $u_3$ sono linearmente indipendenti.
    
2. **Completamento a una base di** $\mathbb{R}^3$**:** Per completare $\{u_1, u_3\}$ a una base di $\mathbb{R}^3$, testiamo i vettori della base canonica $e_1, e_2, e_3$:
    
    $$\begin{pmatrix} u_1 & u_3 & e_2 \end{pmatrix} = \begin{pmatrix} 1 & -1 & 0 \\ -1 & -1 & 1 \\ 1 & 1 & 0 \end{pmatrix} \xrightarrow{\substack{R_2 + R_1 \\ R_3 - R_1}} \begin{pmatrix} 1 & -1 & 0 \\ 0 & -2 & 1 \\ 0 & 2 & 0 \end{pmatrix} \xrightarrow{R_3 + R_2} \begin{pmatrix} 1 & -1 & 0 \\ 0 & -2 & 1 \\ 0 & 0 & 1 \end{pmatrix}$$
    
    Abbiamo $3$ pivot. Dunque $\{u_1, u_3, e_2\}$ è una base di $\mathbb{R}^3$.