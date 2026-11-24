## 1. Cos'è il determinante e qual è la sua proprietà chiave

> **In parole semplici:** Il determinante è una "macchina" che prende una matrice quadrata e la trasforma in un singolo numero reale. Questo numero serve a dirci subito se i vettori (righe o colonne) della matrice sono indipendenti oppure se sono "ridondanti" (uno è multiplo o combinazione degli altri): se il determinante è zero, la matrice è "schiacciata" e i suoi vettori sono dipendenti.

**Negli appunti:**

- **Definizione di partenza:** Il determinante è una funzione $\det: M_{n\times n}(\mathbb{R}) \to \mathbb{R}$.
    
- **Proprietà fondamentale $(*)$:**
    
    $$\det(A) = 0 \iff \text{le righe di } A \text{ sono linearmente dipendenti} \iff \text{le colonne di } A \text{ sono linearmente dipendenti}$$
    
- **I primi due casi base:**
    
    1. Per $n = 1$, se $A = [a]$, allora $\det(A) := a$.
        
    2. Per $n = 2$, se $A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}$, allora $\det(A) := ad - bc$.
        

🔗 **Connessione logica:** _Abbiamo appena inventato una formula per il caso $2 \times 2$ ($ad - bc$), ma funziona davvero? Prima di andare avanti, dobbiamo verificare che questa formula rispetti la proprietà fondamentale $(_)$.*

## 2. Verifica della proprietà $(*)$ per matrici $2 \times 2$

> **In parole semplici:** Qui dimostriamo che per una matrice $2 \times 2$, fare $ad - bc = 0$ equivale esattamente a dire che una riga (o colonna) è multipla dell'altra. È una doppia implicazione ($\iff$), quindi va dimostrata in entrambi i versi.

**Negli appunti:**

- **Verso ($\Rightarrow$): Se $ad - bc = 0$, allora le righe sono dipendenti**.
    
    - _Caso $a = 0$:_ Dall'equazione $0 \cdot d - bc = 0$ segue che $b = 0$ oppure $c = 0$.
        
        - Se $a = b = 0$, la prima riga è $[0 \ \ 0]$, quindi le righe sono automaticamente dipendenti.
            
        - Se $a = c = 0$ ma $b \neq 0$, la seconda riga $[0 \ \ d]$ si può scrivere come $\frac{d}{b}[0 \ \ b]$, quindi è multipla della prima.
            
    - _Caso $a \neq 0$:_ Poniamo $\lambda := \frac{b}{a}$. Da $ad = bc$ ricaviamo $d = \frac{b}{a}c = \lambda c$. Di conseguenza, le due righe sono $[a \ \ b] = a[1 \ \ \lambda]$ e $[c \ \ d] = c[1 \ \ \lambda]$: sono entrambe multiple dello stesso vettore $[1 \ \ \lambda]$, quindi sono dipendenti. (Per le colonne il ragionamento è identico).
        
- **Verso ($\Leftarrow$): Se le righe sono dipendenti, allora $ad - bc = 0$**.
    
    - Se $a = c = 0$, il calcolo dà subito $ad - bc = 0$.
        
    - Se $a \neq 0$ e le righe sono dipendenti, la seconda riga è multipla della prima tramite $\lambda = \frac{c}{a}$, cioè $c = \lambda a$ e $d = \lambda b$. Sostituendo nella formula: $ad - bc = a(\lambda b) - b(\lambda a) = \lambda(ab - ab) = 0$.
        
    - Se $c \neq 0$, si usa lo stesso ragionamento (valido anche per le colonne).
        

🔗 **Connessione logica:** _Ora sappiamo che $ad - bc$ funziona dal punto di vista algebrico. Ma cosa rappresenta questo numero nello spazio? Scopriamo che ha un significato visivo molto preciso._

## 3. Interpretazione geometrica del determinante $2 \times 2$

> **In parole semplici:** Se disegni le due colonne della matrice come due frecce (vettori) che partono dall'origine, queste formano i lati di un parallelogramma. Il determinante non è altro che l'area di quel parallelogramma! Se le due frecce sono allineate (dipendenti), il parallelogramma si schiaccia in una linea e la sua area diventa $0$ (proprio come il determinante!).

**Negli appunti:**

- **Teorema:** Se $a, b, c, d \ge 0$ e $ad - bc \ge 0$, allora:
    
    $$\det \begin{bmatrix} a & b \\ c & d \end{bmatrix} = \text{area del parallelogramma definito dai vettori } \begin{bmatrix} a \\ c \end{bmatrix} \text{ e } \begin{bmatrix} b \\ d \end{bmatrix}$$
    
- **4 esempi visivi per capire l'idea:**
    
    1. $A = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix} \implies \det(A) = 1$: è il quadrato unitario di lato $1$.
        
    2. $A = \begin{bmatrix} 1 & 1 \\ 0 & 1 \end{bmatrix} \implies \det(A) = 1$: è un parallelogramma con stessa base e stessa altezza del quadrato precedente, quindi ha la stessa area.
        
    3. $A = \begin{bmatrix} 1 & 1 \\ 0 & 2 \end{bmatrix} \implies \det(A) = 2$: la base è $1$ e l'altezza è $2$, quindi l'area equivale a quella di un rettangolo $1 \times 2$.
        
    4. $A = \begin{bmatrix} 1 & 1 \\ 1 & 2 \end{bmatrix} \implies \det(A) = 2 - 1 = 1$: geometricamente, questo parallelogramma si ottiene togliendo dal parallelogramma dell'esempio 3 quello dell'esempio 2, quindi la sua area è $2 - 1 = 1$.
        
- **Osservazione chiave:** Lo stesso trucco "per sottrazione" usato nell'esempio 4 dimostra il teorema in tutti i casi in cui le prime coordinate sono uguali, cioè $a = b$ (con $c < d$).
    

🔗 **Connessione logica:** _L'esempio 4 ci ha regalato un'arma segreta: sappiamo già dimostrare il teorema quando $a = b$. La strategia per dimostrare il teorema in generale sarà quindi "truccare" una matrice qualsiasi per ricondurla al caso $a = b$._

## 4. Dimostrazione del Teorema dell'area

> **In parole semplici:** Sappiamo dalla geometria che se allunghi un lato di un parallelogramma di un fattore $\lambda$ senza cambiare l'angolo, anche l'area si moltiplica per $\lambda$. Negli appunti si fa vedere che succede la stessa identica cosa al determinante se moltiplichi una colonna per $\lambda$. Così possiamo "allungare o accorciare" la seconda colonna finché non ha la stessa prima coordinata della prima ($a = b$), ricadendo nel caso facile che abbiamo già dimostrato!

**Negli appunti:**

- **Casi banali ($a = 0$):** Poiché tutti i numeri sono $\ge 0$ e $ad - bc \ge 0$, se $a = 0$ deve essere per forza $bc = 0$, quindi $b = 0$ oppure $c = 0$. In entrambi i casi i due vettori sono dipendenti (uno è nullo o sono entrambi sull'asse verticale), quindi sia l'area che il determinante valgono $0$.
    
- **Caso generale ($a \neq 0$ e $b \neq 0$):** Se $b = a$ abbiamo già finito per l'osservazione precedente. Altrimenti, moltiplichiamo e dividiamo la seconda colonna per $\frac{a}{b}$ (ovvero scaliamo per $\lambda = \frac{b}{a}$):
    
    $$\det \begin{bmatrix} a & b \\ c & d \end{bmatrix} = \frac{b}{a} \cdot \det \begin{bmatrix} a & a \\ c & \frac{ad}{b} \end{bmatrix}$$
    
    (Verifica algebrica: $\frac{b}{a}\left(a \cdot \frac{ad}{b} - ac\right) = ad - bc$).
    
- **Collegamento con la geometria:** Dalla trigonometria sappiamo che l'area di un parallelogramma con lati $s, t$ e angolo $\theta$ è $\text{area}(P) = s \cdot t \cdot \sin(\theta)$. Se cambiamo il secondo vettore $(b, d) \rightsquigarrow (\lambda b, \lambda d)$ con $\lambda > 0$, il lato $t$ diventa $\lambda t$ e l'area diventa $\lambda \cdot \text{area}(P)$. Poiché con $\lambda = \frac{b}{a}$ sia l'area che il determinante scalano dello stesso fattore $\lambda$, abbiamo ricondotto il caso generale al caso già noto in cui le prime due componenti sono uguali ($a = b$).
    
- **Nota sul caso $b = 0$ (con $a \neq 0$):**
    
    - Se anche $c = 0$, la matrice è $\begin{bmatrix} a & 0 \\ 0 & d \end{bmatrix}$: è un rettangolo di lati $a$ e $d$, quindi $\det = \text{area} = ad$.
        
    - Se $d = 0$, la seconda colonna è nulla, quindi $\det = \text{area} = 0$.
        
    - Se $c, d \neq 0$, si moltiplica/divide la seconda colonna per $\frac{d}{c}$ per ricondursi al caso simmetrico $\begin{bmatrix} a & 0 \\ c & c \end{bmatrix}$, risolvibile come sopra.
        

🔗 **Connessione logica:** _Fino a qui abbiamo lavorato solo con matrici $1 \times 1$ e $2 \times 2$. Come facciamo a calcolare il determinante di matrici grandi ($3 \times 3$, $4 \times 4$, ..., $n \times n$)? Usiamo l'induzione: definiamo il determinante grande spezzandolo in tanti determinanti più piccoli._

## 5. Definizione generale del determinante (Sviluppo di Laplace)

> **In parole semplici:** Per calcolare il determinante di una matrice $n \times n$, scegli una riga (o una colonna) a tuo piacere. Per ogni numero di quella riga, lo moltiplichi per il determinante della "sottomatrice" che ottieni cancellando la sua riga e la sua colonna, ricordandoti di alternare i segni $+$ e $-$ come su una scacchiera. La cosa magica è che qualsiasi riga o colonna tu scelga, il risultato finale è sempre lo stesso!

**Negli appunti:**

- **Costruzione per induzione:** Supponiamo di saper già calcolare il determinante per matrici $(n-1) \times (n-1)$. Data una matrice $A = [a_{ij}]$, indichiamo con $A_{ij}$ la sottomatrice ottenuta cancellando la riga $i$ e la colonna $j$.
    
- **Fatto fondamentale:** Le somme ottenute fissando una riga $i$ qualsiasi oppure una colonna $j$ qualsiasi danno sempre lo stesso risultato:
    
    - Sviluppo secondo la riga $i$-esima: $\sum_{j} (-1)^{i+j} a_{ij} \det(A_{ij})$
        
    - Sviluppo secondo la colonna $j$-esima: $\sum_{i} (-1)^{i+j} a_{ij} \det(A_{ij})$
        
- **Definizione:** $\det(A)$ (spesso scritto anche $\vert{}A\vert{}$) è definito proprio come il valore comune di queste somme.
    
- **Promemoria dei segni $(-1)^{i+j}$:** Per non fare ogni volta la potenza di $-1$, basta seguire lo schema a scacchiera (partendo sempre con $+$ in alto a sinistra):
    
    $$\begin{bmatrix} + & - & + & - & \dots \\ - & + & - & + & \dots \\ + & - & + & - & \dots \\ - & + & - & + & \dots \end{bmatrix}$$
    

🔗 **Connessione logica:** _Mettiamo subito alla prova questa regola generale: prima controlliamo che per $n=2$ ridia il nostro vecchio $ad - bc$, e poi la usiamo per calcolare matrici $3 \times 3$._

## 6. Applicazioni ed esempi ($n = 2$ e $n = 3$)

> **In parole semplici:** Quando usi lo sviluppo di Laplace nella pratica, conviene sempre scegliere la riga o la colonna che contiene più zeri possibile: ogni zero annulla un intero pezzo di calcolo e ti risparmia un sacco di fatica!

**Negli appunti:**

- **Verifica su $n = 2$ con $A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}$:**
    
    - Sviluppo sulla 1ª riga: $a \cdot d + b(-c) = ad - bc$
        
    - Sviluppo sulla 2ª riga: $c(-b) + d \cdot a = ad - bc$
        
    - Sviluppo sulla 1ª colonna: $a \cdot d + c(-b) = ad - bc$
        
    - Sviluppo sulla 2ª colonna: $b(-c) + d \cdot a = ad - bc$ (Tutti e quattro i modi portano allo stesso risultato).
        
- **Esempio numerico per $n = 3$:**
    
    $$A = \begin{bmatrix} 1 & 0 & -1 \\ 2 & 1 & 0 \\ 1 & 0 & 2 \end{bmatrix}$$
    
    - _Sviluppo secondo la 1ª riga:_
        
        $$1 \cdot \begin{vmatrix} 1 & 0 \\ 0 & 2 \end{vmatrix} + 0 + (-1) \cdot \begin{vmatrix} 2 & 1 \\ 1 & 0 \end{vmatrix} = 1(2 - 0) - 1(0 - 1) = 2 - (-1) = 3$$
        
    - _Sviluppo secondo la 2ª colonna (ancora più veloce perché ha due zeri!):_
        
        $$0 + 1 \cdot \begin{vmatrix} 1 & -1 \\ 1 & 2 \end{vmatrix} + 0 = 1(2 - (-1)) = 2 + 1 = 3$$
        
- **Formula generale per $n = 3$:** Sviluppando una generica matrice $3 \times 3$ lungo la prima riga si ottiene:
    
    $$\det(A) = a_{11} \begin{vmatrix} a_{22} & a_{23} \\ a_{32} & a_{33} \end{vmatrix} - a_{12} \begin{vmatrix} a_{21} & a_{23} \\ a_{31} & a_{33} \end{vmatrix} + a_{13} \begin{vmatrix} a_{21} & a_{22} \\ a_{31} & a_{32} \end{vmatrix}$$
    
    $$= a_{11}a_{22}a_{33} - a_{11}a_{23}a_{32} - a_{12}a_{21}a_{33} + a_{12}a_{23}a_{31} + a_{13}a_{21}a_{32} - a_{13}a_{22}a_{31}$$
    
- **Osservazione finale:** Se guardi i 6 addendi finali, in ogni singolo prodotto compare **esattamente un elemento per ogni riga e per ogni colonna** (ad esempio in $a_{11}a_{22}a_{33}$ i primi indici sono $1, 2, 3$ e i secondi indici sono $1, 2, 3$). Questa struttura vale per qualsiasi dimensione $n$: cambiano solo i segni davanti ai vari prodotti.

## 7. Il determinante delle matrici triangolari

**Il punto di partenza:** Calcolare il determinante con lo sviluppo di Laplace su matrici grandi è lungo e pieno di conti. Esiste però un caso in cui il calcolo è immediato: le matrici triangolari.

**Cosa dicono gli appunti:**

- **Enunciato:** Sia $A = [a_{ij}]$ una matrice triangolare superiore (cioè con tutti zeri sotto la diagonale principale: $a_{ij} = 0$ per $i > j$). Allora il suo determinante è il prodotto degli elementi sulla diagonale:
    
    $$\det(A) = \prod_{i=1}^n a_{ii} = a_{11} \cdot a_{22} \cdots a_{nn} \text{[cite: 1]}$$
    
- **Dimostrazione (per induzione su $n$):**
    
    - _Caso base ($n = 1$):_ una matrice $1 \times 1$ ha un solo elemento $a_{11}$, quindi il risultato è banalmente vero.
        
    - _Passo induttivo:_ sviluppando il determinante lungo la prima colonna (che ha tutti zeri tranne $a_{11}$), si ottiene $\det(A) = a_{11} \det(A_{11})$. Poiché la sottomatrice $A_{11}$ è ancora triangolare superiore di taglia $n-1$, per ipotesi induttiva $\det(A_{11}) = a_{22} \cdots a_{nn}$, da cui $\det(A) = a_{11} a_{22} \cdots a_{nn}$.
        
- **Nota:** Un risultato identico vale anche per le matrici triangolari inferiori.
    

> **In parole povere:** Se una matrice ha tutti zeri sotto (o sopra) la diagonale, non serve fare nessun calcolo complicato: basta moltiplicare tra loro i numeri sulla diagonale principale.

## 8. Come l'algoritmo di Gauss modifica il determinante

**Connessione logica:** Sappiamo che l'algoritmo di eliminazione di Gauss permette di trasformare _qualsiasi_ matrice quadrata $n \times n$ in una matrice triangolare superiore. Quindi, se capiamo come le mosse di Gauss cambiano il determinante durante il percorso, possiamo usare Gauss per calcolare il determinante di qualunque matrice!

**Cosa dicono gli appunti:** Analizziamo l'effetto delle operazioni elementari sulle righe:

1. **Scambio di due righe ($R_i \leftrightarrow R_j$):** il determinante cambia segno, ovvero $\det(A) \rightsquigarrow -\det(A)$.
    
    - _Perché funziona (dimostrazione):_ Se scambiamo due righe **adiacenti** $i$ e $i+1$, le sottomatrici complementari si scambiano ($A_{ij} \leftrightarrow A_{i+1, j}$), ma nella formula di Laplace $\sum_j (-1)^{i+j} a_{ij} \det(A_{ij})$ l'esponente diventa $(i+1)+j$, facendo cambiare segno a tutti i termini. Scambiare due righe qualsiasi $i$ e $j$ (con $i > j$) equivale a fare $(i-j) + (i-j-1) = 2(i-j) - 1$ scambi di righe adiacenti: essendo un numero **dispari** di cambi di segno, il risultato finale è comunque un segno meno.
        
2. **Sostituzione di una riga con sé stessa più un multiplo di un'altra ($R_i \rightsquigarrow R_i + \lambda R_j$, con $j \neq i$):** il determinante **non cambia**.
    
    - _Verifica in 4 piccoli passi:_
        
        - **I)** Se $A$ ha due righe uguali, allora $\det(A) = 0$. Infatti, scambiandole la matrice resta identica, ma per la regola precedente il determinante deve cambiare segno ($\det(A) = -\det(A) \implies \det(A) = 0$).
            
        - **II)** Se si moltiplica una riga $R_i$ per uno scalare $\lambda \neq 0$, allora $\det(A) \rightsquigarrow \lambda \cdot \det(A)$. Basta sviluppare secondo quella riga: ogni elemento viene moltiplicato per $\lambda$, mentre i complementi algebrici $A_{ij}$ restano invariati[cite: 1].
            
        - **III)** Se una riga è multipla di un'altra ($R_i = \lambda R_j$), allora $\det(A) = 0$. Per il punto II, possiamo "portare fuori" $\lambda$ ottenendo una matrice $B$ con due righe identiche, che per il punto I ha determinante zero.
            
        - **IV)** _Linearità rispetto a una riga:_ se $C$ si ottiene sommando due vettori nella riga $i$-esima ($[a_{i1}+b_{i1}, \dots, a_{in}+b_{in}]$), allora $\det(C) = \det(A) + \det(B)$ (si verifica sviluppando lungo la riga $i$).
            
    - _Conclusione della verifica:_ Applicando il punto IV alla matrice $C$ (dove $R_i$ diventa $R_i + \lambda R_j$), abbiamo $\det(C) = \det(A) + \det(B)$, dove $B$ ha al posto di $R_i$ la riga $\lambda R_j$. Ma $B$ ha due righe proporzionali, quindi $\det(B) = 0$ per il punto III, e resta $\det(C) = \det(A)$.
        

- **Formula finale per Gauss:** Riducendo $A$ a scala con Gauss, il determinante subisce solo i cambi di segno dovuti agli scambi di riga:
    
    $$\det(\text{triangolare}) = (-1)^r \det(A) \text{[cite: 2]}$$
    
    dove $r$ è il numero totale di scambi di righe effettuati.
    

> **In parole povere:** Puoi ridurre una matrice a gradini con Gauss senza alterare il determinante, a patto di ricordarti due cose: ogni volta che scambi due righe devi cambiare segno al risultato finale, mentre sommare a una riga il multiplo di un'altra è "gratis" (non cambia nulla).

## 9. Esempi pratici e scelta del metodo migliore

**Connessione logica:** Ora mettiamo in pratica la formula appena dimostrata su due esempi concreti, per poi capire quando conviene usare Gauss e quando invece è meglio tornare allo sviluppo di Laplace.

**Cosa dicono gli appunti:**

- **Esempio 1 (matrice $3 \times 3$):**
    
    $$A = \begin{bmatrix} 1 & 2 & 3 \\ 2 & 4 & 1 \\ 3 & 1 & 2 \end{bmatrix} \rightsquigarrow \begin{bmatrix} 1 & 2 & 3 \\ 0 & 0 & -5 \\ 0 & -5 & -7 \end{bmatrix} \xrightarrow{\text{scambio } R_2 \leftrightarrow R_3} \begin{bmatrix} 1 & 2 & 3 \\ 0 & -5 & -7 \\ 0 & 0 & -5 \end{bmatrix} =: B \text{[cite: 2]}$$
    
    La matrice triangolare $B$ ha $\det(B) = 1 \cdot (-5) \cdot (-5) = 25$[cite: 2]. Dato che abbiamo fatto **1 scambio** di righe ($r=1$), si ha $\det(A) = -25$[cite: 2].
    
- **Esempio 2 (matrice $4 \times 4$):**
    
    $$A = \begin{bmatrix} 4 & 0 & 0 & 1 \\ 1 & 1 & 2 & 0 \\ 0 & 2 & 1 & 1 \\ 1 & 1 & 0 & 1 \end{bmatrix} \text{[cite: 2, 3]}$$
    
    Scambiando $R_1 \leftrightarrow R_4$ e riducendo per righe (con un ulteriore scambio $R_2 \leftrightarrow R_3$), si arriva a due righe identiche $[0 \quad 0 \quad 2 \quad -1]$ e quindi a una riga di tutti zeri:
    
    $$\rightsquigarrow \begin{bmatrix} 1 & 1 & 0 & 1 \\ 0 & 2 & 1 & 1 \\ 0 & 0 & 2 & -1 \\ 0 & 0 & 0 & 0 \end{bmatrix} \implies \det(A) = 0 \text{[cite: 3]}$$
    
- **Confronto tra metodi (Gauss vs Sviluppo di Laplace):**
    
    - Gauss è molto pratico quando la matrice è **grande e piena** (molti elementi $\neq 0$).
        
    - Lo sviluppo di Laplace è più pratico quando la matrice ha **molti zeri**.
        
- **Esempio 3 (matrice sparsa $4 \times 4$):**
    
    $$A = \begin{bmatrix} 1 & 0 & 0 & 4 \\ 0 & 2 & 0 & 1 \\ 3 & 0 & 1 & 2 \\ 1 & 0 & 0 & 5 \end{bmatrix} \text{[cite: 3]}$$
    
    La terza colonna ha un solo elemento non nullo ($a_{33} = 1$, in posizione pari $3+3=6$, quindi segno $+$). Sviluppando lungo la terza colonna e poi lungo la seconda riga della sottomatrice:
    
    $$\det(A) = 1 \cdot \begin{vmatrix} 1 & 0 & 4 \\ 0 & 2 & 1 \\ 1 & 0 & 5 \end{vmatrix} = 1 \cdot \begin{vmatrix} 2 & 1 \\ 0 & 5 \end{vmatrix} + 4 \cdot \begin{vmatrix} 0 & 2 \\ 1 & 0 \end{vmatrix} = (2 \cdot 5) - (4 \cdot 2) = 2 \text{[cite: 3]}$$
    

> **In parole povere:** Non esiste un metodo unico migliore in assoluto: se la matrice è "piena" di numeri diversi da zero vai di Gauss; se invece vedi righe o colonne piene di zeri, usa lo sviluppo di Laplace su quelle.

## 10. Matrice trasposta e dipendenza lineare

**Connessione logica:** Finora abbiamo lavorato solo sulle _righe_. Ma cosa succede se ragioniamo sulle _colonne_? La matrice trasposta fa da ponte perfetto tra righe e colonne.

**Cosa dicono gli appunti:**

- **Definizione:** Data $A = [a_{ij}] \in M_{n \times n}(\mathbb{R})$, la sua **matrice trasposta** è $A^t = [a_{ji}] \in M_{n \times n}(\mathbb{R})$ (ottenuta scambiando righe e colonne)[cite: 3].
    
- **Proprietà:** $\det(A) = \det(A^t)$, perché lo sviluppo di Laplace rispetto alla colonna $i$-esima di $A$ è identico allo sviluppo rispetto alla riga $i$-esima di $A^t$[cite: 3]. _(Questo significa che tutte le regole sulle righe viste finora valgono anche per le colonne!)_
    
- **Teorema fondamentale:**
    
    $$\det(A) = 0 \iff \text{le righe di } A \text{ sono linearmente dipendenti} \iff \text{le colonne di } A \text{ sono linearmente dipendenti} \text{[cite: 3]}$$
    
- **Dimostrazione:** Poiché le righe di $A$ sono le colonne di $A^t$ e $\det(A) = \det(A^t)$, basta dimostrarlo per le colonne[cite: 3]. Riduciamo $A$ con Gauss a una matrice a scalini (triangolare superiore) $B$:
    
    - ($\Rightarrow$) Se $\det(A) = 0$, allora $\det(B) = 0$, quindi $B$ ha almeno uno zero sulla diagonale. Di conseguenza una colonna di $B$ non ha il pivot, il che rende le colonne di $B$ (e quindi anche quelle di $A$, poiché le mosse di Gauss non alterano le relazioni di dipendenza tra colonne) linearmente dipendenti.
        
    - ($\Leftarrow$) Viceversa, se le colonne di $A$ sono dipendenti, lo sono anche quelle di $B$; quindi una colonna di $B$ non ha il pivot e ha $0$ sulla diagonale, portando a $\det(B) = 0 \implies \det(A) = 0$.
        
- **Corollario (Applicazioni lineari):** Sia $A: \mathbb{R}^n \to \mathbb{R}^n$ l'applicazione lineare $v \mapsto A \cdot v$. Allora:
    
    $$\ker(A) \neq \{0\} \iff \operatorname{Im}(A) \neq \mathbb{R}^n \iff \det(A) = 0 \text{[cite: 4]}$$
    

> **In parole povere:** Il determinante è un "rilevatore di ridondanza": se vale $0$, vuol dire che almeno una riga (o una colonna) è una combinazione delle altre, e la trasformazione lineare associata "schiaccia" lo spazio perdendo dimensioni.

## 11. Teorema di Binet, matrici inverse e cambio di base

**Connessione logica:** Dopo aver collegato il determinante alle applicazioni lineari, gli appunti introducono il comportamento del determinante rispetto al prodotto tra matrici, usandolo subito per caratterizzare le matrici invertibili.

**Cosa dicono gli appunti:**

- **Teorema (di Binet):** Se $A, B \in M_{n \times n}(\mathbb{R})$, allora:
    
    $$\det(A \cdot B) = \det(A) \cdot \det(B) \text{[cite: 4]}$$
    
    - _Verifica per $n = 2$:_ Date $A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}$ e $B = \begin{bmatrix} a' & b' \\ c' & d' \end{bmatrix}$, si calcola $\det(A)\det(B) = (ad-bc)(a'd'-b'c') = aa'dd' + bb'cc' - a'bcd' - ab'c'd$. Svolgendo il prodotto $AB$ e calcolandone il determinante si ottiene la stessa espressione dopo aver semplificato i termini opposti $aa'cb'$ e $bc'dd'$.
        
- **Corollario (Invertibilità):** Una matrice $A \in M_{n \times n}(\mathbb{R})$ è invertibile (esiste $A^{-1}$) se e solo se $\det(A) \neq 0$, e in tal caso:
    
    $$\det(A^{-1}) = \frac{1}{\det(A)} \text{[cite: 4]}$$
    
    - _Dimostrazione:_ $A^{-1}$ esiste $\iff$ l'applicazione $v \mapsto Av$ è un isomorfismo ($\ker(A) = \{0\}$ e $\operatorname{Im}(A) = \mathbb{R}^n$) $\iff \det(A) \neq 0$ per il corollario precedente[cite: 4]. Inoltre, sapendo che $A \cdot A^{-1} = I$ e che $\det(I) = 1$ (perché $I$ è triangolare con tutti $1$ sulla diagonale), per il teorema di Binet si ha $\det(A) \cdot \det(A^{-1}) = \det(A \cdot A^{-1}) = \det(I) = 1$, da cui $\det(A^{-1}) = \frac{1}{\det(A)}$[cite: 4].
        
- **Proposizione finale (incompleta a fine pagina):** Sia $\varphi: V \to V$ una mappa lineare, $\mathcal{B}$ e $\mathcal{B}'$ due basi di $V$, $A$ la matrice di $\varphi$ rispetto a $\mathcal{B}$ e $A'$ rispetto a $\mathcal{B}'$...[cite: 4] _(Nota: la conclusione che manca in fondo alla pagina è che $\det(A) = \det(A')$, perché matrici simili hanno lo stesso determinante: $A' = P^{-1}AP \implies \det(A') = \det(P)^{-1}\det(A)\det(P) = \det(A)$)._
    

> **In parole povere:** Il determinante "rispetta" la moltiplicazione tra matrici. Grazie a questa proprietà, capiamo al volo se una matrice è invertibile (basta che $\det(A) \neq 0$) e scopriamo che il determinante di un endomorfismo non dipende dalla base scelta.****

## 12: Determinante, Matrice Aggiunta e Formula di Cramer

### 1. Il determinante di un'applicazione lineare non dipende dalla base

- **Cosa dicono gli appunti:** Se $A$ e $A'$ sono matrici associate alla stessa applicazione lineare $\varphi$ rispetto a due basi diverse, allora $\det(A) = \det(A')$. Di conseguenza, $\det(A)$ dipende solo dall'applicazione $\varphi$ e non dalla base scelta.
    
- **Dimostrazione:** Sappiamo che esiste una matrice invertibile $P$ (di cambiamento di base) tale che $A' = P A P^{-1}$. Per il teorema di Binet (il determinante del prodotto è il prodotto dei determinanti):
    
    $$\det(A') = \det(P)\det(A)\det(P^{-1}) = \det(A)\det(P)\det(P^{-1}) = \det(A) \cdot 1 = \det(A) \text{[cite: 1]}$$
    
- **Conseguenza (Corollario):** Se $\varphi: V \to V$ è un'applicazione lineare e $A$ è la sua matrice rispetto a una qualsiasi base, valgono le seguenti equivalenze:
    
    $$\ker(\varphi) \neq \{0\} \iff \operatorname{Im}(\varphi) \neq V \iff \det(A) = 0 \text{[cite: 1]}$$
    

> 💡 **Spiegazione semplice:** Cambiare base è come guardare lo stesso oggetto da un'angolazione diversa: le coordinate cambiano, ma le proprietà intrinseche della trasformazione (come il fattore di scala dei volumi, cioè il determinante) restano identiche. Inoltre, se il determinante è zero, la trasformazione "schiaccia" lo spazio perdendo dimensioni (l'immagine non copre tutto $V$ e alcuni vettori non nulli finiscono nello zero, cioè nel nucleo).

### 2. La Matrice Aggiunta e la Formula di Cramer

- **Il collegamento logico:** Ora che sappiamo che $\det(A) \neq 0$ garantisce che l'applicazione sia invertibile, vogliamo trovare una formula esplicita per calcolare la matrice inversa $A^{-1}$. Per farlo, introduciamo uno strumento ad hoc: la matrice aggiunta.
    
- **Definizione (Matrice aggiunta):** Data una matrice quadrata $A = [a_{ij}] \in M_{n \times n}(\mathbb{R})$, la sua **matrice aggiunta** $\tilde{A} = [\tilde{a}_{ij}]$ ha come elementi:
    
    $$\tilde{a}_{ij} = (-1)^{i+j} \det(A_{ji}) \text{[cite: 1]}$$
    
    (Attenzione allo scambio degli indici: per il posto $(i, j)$ si calcola il determinante della sottomatrice ottenuta eliminando la riga $j$ e la colonna $i$! In pratica è la trasposta della matrice dei cofattori).
    
- **Formula di Cramer:** Moltiplicando $A$ per la sua aggiunta si ottiene sempre una matrice diagonale con il determinante sulla diagonale:
    
    $$A \cdot \tilde{A} = \det(A) \cdot I \text{[cite: 1]}$$
    
    (dove $I \in M_{n \times n}(\mathbb{R})$ è la matrice identità).
    
- **Corollario (Formula per l'inversa):** Se $\det(A) \neq 0$, possiamo dividere entrambi i membri per $\det(A)$ e ricavare subito l'inversa:
    
    $$A^{-1} = \frac{1}{\det(A)} \cdot \tilde{A} \text{[cite: 1]}$$
    

> 💡 **Spiegazione semplice:** La matrice aggiunta è una matrice "gemella" costruita apposta per incastrarsi con $A$. Quando le moltiplichi, ogni riga di $A$ si combina con la colonna corrispondente di $\tilde{A}$ ricostruendo esattamente lo sviluppo di Laplace del determinante, mentre si annulla con tutte le altre colonne. Dividendo tutto per $\det(A)$, ottieni esattamente la matrice inversa[cite: 1].

### 3. Esempi pratici di calcolo dell'inversa

- **Caso $n = 2$:** Data $A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}$, scambiando gli elementi sulla diagonale principale e cambiando segno agli altri due si ottiene $\tilde{A} = \begin{bmatrix} d & -b \\ -c & a \end{bmatrix}$[cite: 1]. Se $\det(A) = ad - bc \neq 0$, ritroviamo la celebre formula[cite: 1]:
    
    $$A^{-1} = \frac{1}{ad - bc} \begin{bmatrix} d & -b \\ -c & a \end{bmatrix} \text{[cite: 1]}$$
    
- **Caso $n = 3$:** Data $A = \begin{bmatrix} 1 & 0 & 3 \\ 0 & 2 & 0 \\ 4 & 0 & 1 \end{bmatrix}$, calcoliamo il determinante sviluppando lungo la seconda riga (che ha due zeri, quindi è comodissima)[cite: 1]:
    
    $$\det(A) = 2 \cdot \begin{vmatrix} 1 & 3 \\ 4 & 1 \end{vmatrix} = 2 \cdot (1 - 12) = -22 \neq 0 \implies \exists A^{-1} \text{[cite: 1]}$$
    
    Calcolando tutti i cofattori e trasponendo si trova $\tilde{A} = \begin{bmatrix} 2 & 0 & -6 \\ 0 & -11 & 0 \\ -8 & 0 & 2 \end{bmatrix}$, da cui:
    
    $$A^{-1} = -\frac{1}{22}\tilde{A} = \begin{bmatrix} -\frac{1}{11} & 0 & \frac{3}{11} \\ 0 & \frac{1}{2} & 0 \\ \frac{4}{11} & 0 & -\frac{1}{11} \end{bmatrix} \text{[cite: 2]}$$
    

### 4. Dimostrazione della Formula di Cramer e un'applicazione bonus

- **Perché funziona $A \cdot \tilde{A} = \det(A) \cdot I$?** Calcoliamo il prodotto riga per colonna:
    
    - **Sulla diagonale (riga $i$ di $A$ $\times$ colonna $i$ di $\tilde{A}$):** Ad esempio per $i=1$, otteniamo $(-1)^{1+1}a_{11}\det(A_{11}) + (-1)^{1+2}a_{12}\det(A_{12}) + \dots + (-1)^{1+n}a_{1n}\det(A_{1n})$. Questa è esattamente la formula dello sviluppo di Laplace lungo la riga $i$, quindi fa $\det(A)$.
        
    - **Fuori dalla diagonale (riga $i$ di $A$ $\times$ colonna $j \neq i$ di $\tilde{A}$):** Ad esempio per $i=1, j=2$, otteniamo $(-1)^{1+2}a_{11}\det(A_{21}) + (-1)^{2+2}a_{12}\det(A_{22}) + \dots + (-1)^{2+n}a_{1n}\det(A_{2n})$. Questo equivale al determinante di una matrice fittizia in cui abbiamo **copiato la prima riga al posto della seconda**. Avendo due righe identiche, il suo determinante è $0$.
        
- **Il collegamento logico (Seconda dimostrazione di un teorema noto):** Grazie alla formula di Cramer, possiamo ridimostrare in poche righe che **$\det(A) = 0 \iff$ le colonne di $A$ sono linearmente dipendenti**:
    
    - **($\Rightarrow$) Se $\det(A) = 0$:** Per Cramer abbiamo $A\tilde{A} = 0$. Scegliendo una colonna non nulla $C_i \neq 0$ di $\tilde{A}$ (se $\tilde{A}=0$ il caso è ancora più semplice), l'equazione $A C_i = 0$ esprime una combinazione lineare non banale delle colonne di $A$ uguale a zero: quindi sono dipendenti.
        
    - **($\Leftarrow$) Se le colonne di $A$ sono dipendenti:** L'immagine di $A$ è un sottospazio proprio di $\mathbb{R}^n$ ($\dim \operatorname{Im}(A) < n$). Poiché $\operatorname{Im}(A\tilde{A}) \subset \operatorname{Im}(A)$, anche $A\tilde{A}$ non può coprire tutto $\mathbb{R}^n$. Ma se per assurdo fosse $\det(A) \neq 0$, avremmo $A\tilde{A} = \det(A) \cdot I$, la cui immagine è tutto $\mathbb{R}^n$ — contraddizione!
        

## 13: Richiami sui Polinomi, Divisione e Radici

### 1. Polinomi e Divisione con Resto (Algoritmo di Euclide)

- **Il collegamento logico:** Quando in algebra lineare cerchiamo gli autovalori, dobbiamo studiare le radici del polinomio caratteristico. Per questo motivo gli appunti fanno un ripasso su come si dividono e si scompongono i polinomi.
    
- **Definizione:** Un polinomio $f \in \mathbb{R}[x]$ è un'espressione del tipo $f = a_n x^n + a_{n-1}x^{n-1} + \dots + a_0$ con $a_i \in \mathbb{R}$ e $a_n \neq 0$. Il numero $n := \deg(f)$ è il **grado** di $f$.
    
- **Teorema della divisione con resto:** Dati $f$ (di grado $n$) e $g = b_m x^m + \dots + b_0$ (di grado $m \le n$), esistono e sono **unici** due polinomi $q$ (quoziente) e $r$ (resto) tali che:
    
    $$f = q \cdot g + r \quad \text{con } \deg(r) < \deg(g) \text{[cite: 3]}$$
    
- **Come si calcolano (Algoritmo di Euclide):** Si elimina il termine di grado massimo di $f$ sottraendo un opportuno multiplo di $g$:
    
    $$f_1 := f - \frac{a_n}{b_m}x^{n-m} g \text{[cite: 3]}$$
    
    Così facendo il termine $a_n x^n$ si cancella e $\deg(f_1) \le n - 1$. Se $\deg(f_1) < m$, ci fermiamo perché $f_1 = r$; altrimenti ripetiamo il procedimento su $f_1$ finché il grado non scende sotto $m$.
    
- **Esempi:**
    
    1. $f = x^4 + 2$, $g = x^3 + 2$: calcoliamo $f_1 = f - x g = (x^4 + 2) - (x^4 + 2x) = 2 - 2x$. Siccome $\deg(f_1) = 1 < 3$, abbiamo finito: $q = x$ e $r = 2 - 2x$.
        
    2. $f = x^4 + 2$, $g = x^3 + 3x^2$: primo passo $f_1 = f - xg = -3x^3 + 2$ (grado $3$, non basta ancora). Secondo passo $f_2 = f_1 + 3g = (-3x^3 + 2) + (3x^3 + 9x^2) = 9x^2 + 2 =: r$. Risalendo a ritroso: $f = (x - 3)g + (9x^2 + 2)$.
        

> 💡 **Spiegazione semplice:** La divisione tra polinomi funziona esattamente come la divisione in colonna delle elementari, solo che al posto delle cifre guardi le potenze della $x$: a ogni giro abbassi il grado del polinomio di partenza finché non ti rimane un "avanzo" (il resto) troppo piccolo per essere ancora diviso.

### 2. Radici di un polinomio e Teorema di Ruffini

- **Il collegamento logico:** Cosa succede se dividiamo un polinomio $f$ per un binomio semplice di primo grado come $(x - a)$? Qui entra in gioco il concetto di radice.
    
- **Definizione:** Un numero $a \in \mathbb{R}$ si dice **radice** di $f$ se $f(a) = 0$.
    
- **Proposizione (Teorema di Ruffini):** Se $a$ è radice di $f$, allora $f$ è divisibile per $(x - a)$, cioè:
    
    $$f = (x - a)q \quad \text{con } \deg(q) = \deg(f) - 1 \text{[cite: 3]}$$
    
- **Dimostrazione:** Facciamo la divisione con resto di $f$ per $(x - a)$: otteniamo $f = (x - a)q + r$. Poiché $\deg(r) < \deg(x - a) = 1$, il resto $r$ deve avere grado zero, cioè è una semplice costante numerica. Valutando entrambi i lati in $x = a$, abbiamo:
    
    $$0 = f(a) = (a - a)q(a) + r = r \implies r = 0 \text{[cite: 3]}$$
    

> 💡 **Spiegazione semplice:** Quando dividi per $(x - a)$, il resto è sempre un numero fisso[cite: 3]. Se sostituisci $a$ al posto della $x$, il pezzo $(x - a)q$ sparisce perché fa zero, lasciando scoperto solo il resto $r$[cite: 3]. Quindi il resto coincide sempre con $f(a)$: se $a$ azzera il polinomio, il resto è zero e la divisione è esatta[cite: 3]!

### 3. Molteplicità delle radici e Fattorizzazione in $\mathbb{R}[x]$

- **Il collegamento logico:** Una volta estratto un fattore $(x - a)$, il quoziente $q$ potrebbe avere ancora $a$ come radice. Ripetendo l'estrazione arriviamo al concetto di molteplicità e alla scomposizione completa del polinomio.
    
- **Corollario e Definizione di Molteplicità:** Se $f(a) = 0$, possiamo continuare a dividere per $(x - a)$ finché non troviamo un quoziente $g$ che non si annulla più in $a$ ($g(a) \neq 0$):
    
    $$f = (x - a)^m g \quad \text{con } 1 \le m \le \deg(f) \text{ e } g(a) \neq 0 \text{[cite: 4]}$$
    
    Il numero di volte $m$ in cui $(x - a)$ divide $f$ si chiama **molteplicità** della radice $a$.
    
- **Osservazione (Altre radici):** Se $b \neq a$ è un'altra radice di $f$, allora $0 = f(b) = (b - a)^m g(b)$. Poiché $b - a \neq 0$, deve essere per forza $g(b) = 0$. Quindi possiamo estrarre anche $(x - b)^{m'}$ da $g$, scrivendo $f = (x - a)^m (x - b)^{m'} h$ (con $h(a) \neq 0$ e $h(b) \neq 0$). A questo punto o $h$ ha altre radici reali e continuiamo, oppure non ne ha più (come nel caso di $h = x^2 + 1$) e ci fermiamo.
    
- **Teorema Finale (Struttura dei polinomi reali):** Ogni polinomio $f \in \mathbb{R}[x]$ ha un numero finito di radici reali distinte $a_1, a_2, \dots, a_s \in \mathbb{R}$. Dette $m_1, \dots, m_s$ le rispettive molteplicità, vale:
    
    $$m_1 + m_2 + \dots + m_s \le \deg(f) \text{[cite: 4]}$$
    
    e il polinomio si fattorizza come:
    
    $$f = (x - a_1)^{m_1}(x - a_2)^{m_2}\cdots(x - a_s)^{m_s} \cdot g \text{[cite: 4]}$$
    
    dove $g \in \mathbb{R}[x]$ è un polinomio privo di radici reali.
    
- **Nota Bene:** Se $\deg(f) \ge 5$, non esistono formule risolutive esatte generali per trovare le radici (per il teorema di Abel-Ruffini), ma solo metodi _ad hoc_ (es. Ruffini per tentativi) o metodi numerici approssimati[cite: 4].
    

> 💡 **Spiegazione semplice:** Ogni polinomio reale si può "smontare" come un Lego: metti da parte tutti i blocchetti $(x - \text{radice})$ contati con il loro esponente (la molteplicità), e quello che ti resta in mano alla fine è un blocco $g$ che nei numeri reali non si può più spezzare[cite: 4]. Di conseguenza, un polinomio di grado $n$ non può mai avere più di $n$ radici reali (contate con la loro molteplicità)