# 1. Definitions from Graph Theory 

> **Definition 1.1 Multiset**
> A collection of objects where objects may appear more than once.
> Multiplicity: number of times appear for that object 

Example 
S = {a, a, 4, a, -1, -1, x, 15}
Multiplicity of a is 3, of -1 is 2. Size of S, denoted as |S|, is 8.

> **Definition 1.2 Graph**
> 1) A graph is composed of a vertex set V and an edge multiset E. 
> 2) The vertex set V can be any set. 
> 3) The edge multiset E is a multiset whose elements are sets of the form {v, w} or {v} where v and w are distinct vertices. 
> 4) An edge of the form {v} is called a loop.
> 5) If {v, w} $\in$ E, then v and w are adjacent or neighbours, and edge {v, w} is incident to v and w. Similarly, {v} is adjacent to itself and {v} is incident to v.
> 6) Degree of vertex v, deg(v) = number of edges e $\in$ E s.t. v is incident to e.
> 7) For loops, we specify that one loop contribute 1 to deg(v)
> 8) Order of a graph X, |X| = number of vertices in the graph. 

Remark: 
When we specify loop as only contributing one to deg(v), we have cancelled Euler's Theorem, which states that in connected graphs: Eulerian <=> degree of each vertex is even. 

Example: 
![[Figure1.png]]

>**Definition 1.3**
>1) Multigraph: graph has multiple edges (i.e. two distinct edges connecting same pair of vetrices)
>2) Digraph: graphs in which edges have directions
>3) d-regular graph: every vertex has degree d 

> **Definition 1.4 Walk and Connectedness**
> 1) Walk: finite alternating sequence of vertices and edges, of the form below, where $v_{i}$ $\in$ V and $e_{i}$ $\in$ E, $v_{i}$ is adjacent to $v_{i+1}$ with edge $e_{i}$
>     $$w = (v_{0}, e_{0}, v_{1}, e_{1}, \dots, v_{n-1}, e_{n-1}, v_{n})$$
> 2) Connected: A graph X with vertex set V is connected if for every x, y ∈ V there exists a walk from x to y. Otherwise, disconnected. 

>**Definition 1.5 Bipartite Graph**
>A graph $X$ with vertex set $V$ is bipartite if there exist $V_{1}$, $V_{2}$ ⊂ V such that
>1) $V$ = $V_{1}$ $\cup$ $V_{2}$,
>2) $V_{1}$ $\cap$ $V_{2}$ = $\varnothing$,
>3) every edge of $X$ is incident to a vertex in $V_{1}$ and a vertex in $V_{2}$.
>In this case, $(V_{1}, V_{2})$ is a bipartition of $V$. 

Remark: 
Bipartite graph <=> vertices of X can be coloured with two colours s.t. no adjacent vertices have the same colour. 

Example 
![[Screenshot 2024-09-02 at 20.33.34.png]]
> **Definition 1.6 Distance**
> 1) Distance between x and y, dist(x, y) = minimal length of walk between x and y
> 2) Diameter of X, diam(X) = $\max_{x,y\in V} dist(x,y)$

Remark: 
1) If x and y are not connected, dist(x, y) is infinity. Same for diam(X) in disconnected graphs. 
2) dist defines a metric space on V



# 2. Cayley Graphs 
Properties of Cayley graphs are connected with properties of the group.

> **Definition 1.7 Symmetric multiset of a group**
> Let G be a group and $\Gamma$ be a multi-subset of G. We say that $\Gamma$ is symmetric if whenever $y$ is an element of $\Gamma$ with multiplicity n, then $y^{-1}$  is an element of $\Gamma$ of multiplicity n. 
> (handwrite the notation)

> **Definition 1.8 Cayley Graph**
> Group G and symmetric multiset $\Gamma$. The Cayley graph of G with respect to $\Gamma$, $Cay(G, \Gamma$), is defined as follows: 
> 1) Vertices: Elements of G. 
> 2) Edges: $x,\, y \in G$ are adjacent iff exists $\gamma$ ∈ $\Gamma$ such that $x = y\gamma$ . (In other words, $y^{-1}x = \gamma$.) 
> 3) Multiplicity of the edge: multiplicity of $y^{-1}x$ in $\Gamma$.

Remark: 
1) It's necessary for $\Gamma$ to be symmetric. Due to transitivity of adjacency, $x = y\gamma$ leads to $y = x\gamma'$ , thus $\gamma = \gamma'$ 
2) If we relax $\Gamma$ to any multiset, then we get a directed Cayley graph.

Example 
![[Screenshot 2024-09-02 at 21.53.58.png]]

> **Proposition 1.9**
> Group G and symmetric multiset $\Gamma$. Then:
> 1) $Cay(G, \Gamma$) is $|\Gamma|$-regular. 
> 2) $Cay(G, \Gamma$) is connected <=> $\Gamma$ generates G as a group.

Proof ideas: 
- for any g in G, g multiply each element of $\Gamma$ generates a different edge.
- $\Gamma$ generates G 
     <=> any g in G, $g = \gamma_{1}\dots\gamma_{k} = 1_{G}\gamma_{1}\dots\gamma_{k}$ 
     <=> exists a walk in X from $1_{G}$ to g
     <=> X is connected 
Remark:
If we count a loop twice in Definition 1.2, then 1) would fail. 



# 3. Adjacency Operator 

>**Definition 1.10 Complex Vector Space $L^{2}(S)$**
>Finite set S. Define $L^{2}(S)$ as 
>(vector space of functions, mapping from S to complex numbers) 
>$$ L^{2}(S) = \{f: S \rightarrow \mathbb{C}\}$$
>$f, g \in L^{2}(S)$, $\alpha \in \mathbb{C}$
>Sum: $(f+g)(x) = f(x) + g(x)$
>Scalar multiplication: $(\alpha f)(x) = \alpha f(x)$
>Standard inner product and therefore norm
>$$ \langle f,g \rangle_{2} = \sum_{x\in S}f(x)\overline{g(x)} \; \; \; \; ||f||_{2} = \sqrt{\langle f,f \rangle_{2}} = \sqrt{\sum_{x\in S}|f(x)|^{2}} $$

Remark:
For simplicity, we often write $L^{2}(V)$, in which V is the vertex set of graph X, as $L^{2}(X)$. When doing so, we are viewing an element (function) f of $L^{2}(S)$ as:
1) a function (original definition)
2) a picture, where we label f(v) for every vertex of X
3) a (vector) value, with a particular ordering for vertices $v_{1}, \dots, v_{n}$ , as $(f(v_{1}), \dots, f(v_{n}))^{T}$. Written in this way, inner product is the same as complex inner product of vectors.
We also consider $L^{2}(E)$, where E is an edge multiset of X

Remark: Standard Basis 
Consider a set $S = \{x_{1},x_{2},... ,x_{n}\}$. Let $\beta = \{\delta_{x_{1}},\delta_{x_{2}},\dots ,\delta_{x_{n}}\} \in L^{2}(S)$, where $\delta_{x_{i}}(x_{j}) = 1$ if $i = j$, and $\delta_{x_{i}}(x_{j}) = 0$ if $i \ne j$.
    If $f \in L^{2}(S)$, then
    $$f(x) = f(x_{1})\delta_{x_{1}}(x) + \dots + f(x_{n})\delta_{x_{n}}(x)$$
That is, $\beta$ spans $L^{2}(S)$, and $\beta$ is an orthonormal basis.

>**Definition 1.11 Adjacency Matrix**
>Graph $X$, vertices ordered as $v_{1}, v_{2}, ..., v_{n}$
>Adjacency matrix of X is denoted as $A$, where $A_{i,j}$ is the number of edges that are incident to both $v_{i}$ and $v_{j}$

>**Proposition 1.12 Facts about Adjacency Matrix**
>1) $A$ is symmetric.
>2) Suppose $A$ is $n \times n$, then A has n real eigenvalues (not necessarily different)
>3) For graph $X$, two adjacency matrices using different vertex ordering have same eigenvalues. (hence we can talk about eigenvalues of a graph without referring to a specific vertex ordering)

Proof 
1) By definition. 
2) Symmetric real matrix, then by spectrum theorem in linear algebra. 
3) For two adjacency matrices of different ordering, $A_{1}, A_{2}$, 
     - We can get from one to the other by permutations on rows and columns, and these permutations are the same, in the sense that if we exchange column i with column j, we also exchange row i with row j.
     - Say the permutation needed from $A_{1}$ to $A_{2}$ is $\pi$, with corresponding row permutation matrix $R_{\pi}$, column permutation matrix $C_{\pi}$, then:
         $A_{2} = R_{\pi}C_{\pi}A_{1}$ (first permuting columns, then permuting rows)
         $A_{2} = C_{\pi}A_{1}R^{-1}_{\pi}$ (left multiply is permutation $\pi$, right multiply is permutation $-\pi$, and $R_{-\pi}=R^{-1}_{\pi}$)
         $A_{2}=C_{\pi}A_{1}C^{T}_{\pi}$ ($R_{-\pi}=R^{-1}_{\pi} = C_{\pi}$, and $P^{-1}=P^{T}$ for both $P=C_{\pi}$ and $P=R_{\pi}$  )
         Note $C_{\pi}$ is orthogonal, hence $A_{1}$ and $A_{2}$ are similar, with same eigenvalues. 

> **Definition 1.13 Spectrum of Graph**
> Order the eigenvalues of graph X as:
> $$ \lambda_{n-1}(X)\le \lambda_{n-2}(X) \le \dots \le \lambda_{1}(X) \le \lambda_{0}(X) $$
> We call the multiset of eigenvalues of X the _spectrum_ of X. For distinct eigenvalues $\mu_{1}, \mu_{2}, \dots, \mu_{r}$ with multiplicities $m_{1}, m_{2}, \dots, m_{r}$, we write:
> $$Spec(X) = \left(\begin{array}{cccc} \mu_{1} & \mu_{2} & \dots & \mu_{r} \\
 m_{1} & m_{2} & \dots & m_{r} 
 \end{array} \right) $$

Remark
Spectrum conveys much information about the graph, especially $\lambda_{1}(X)$. However, in most applications where graphs are large, we do not have spectrum. Our main task henceforth is to develop techniques to estimate $\lambda_{1}$. 

>**Definition 1.14 Adjacency Operator**
>Graph X, vertex set V, adjacency matrix with ordering $v_{1}, v_{2}, \dots, v_{n}$. Consider $f \in L^{2}(X)$, then 
>$$ (Af)(v) = \sum_{w\in V}A_{v,w}f(w)$$
>Hence A is a linear operator, $L^{2}(X) \rightarrow L^{2}(X)$. This is known as adjacency operator of X. 

Remark
1) This operator is natural considering the close connection between square matrix and operator.
2) For Cayley graph $X=Cay(G, \Gamma)$, we have:
$$ (Af)(g) = \sum_{y \in \Gamma}f(gy)$$ for all $g \in G$ 
(since $A_{g,w} = 1 \iff w = gy$ for some $y \in \Gamma$ )



# 4. Eigenvalues of Regular Graphs

> **Definition 1.15 Symmetric about 0**
> X is a d-regular graph. Then its spectrum is symmetric about 0 if whenever λ is an eigenvalue of X of multiplicity k, then −λ is also an eigenvalue of X with multiplicity k.

> **Proposition 1.16 Facts about regular graph's eigenvalues**
> If X is a d-regular graph with n vertices, then
>1) d is an eigenvalue of X.  
>2) $|λ_{i}(X)|≤d$ for $i= 0, \dots, n−1$.  
>3) $λ_{1}(X) < λ_{0}(X)$ iff X is connected.  
>4) If X is bipartite, then the spectrum of X is symmetric about 0. 
>5) If −d is an eigenvalue of X , then X is bipartite.

Proof
1) Consider constant function $f_{0}(x)=1$ for all vertices 
     $(Af_{0})(x) = \sum_{y\in V}A_{x,y}f_{0}(y)=\sum_{y\in V}A_{x,y} = d$  (since X is d-regular)
2) For arbitrary eigenvalue $\lambda$ with eigenfunction f, pick $x \in V$ s.t. $|f(x)| = max_{y\in V}|f(y)|$. Then,
     $|\lambda||f(x)| = |(Af)(x)|$ (eigenvalue)
     $=|\sum_{y\in V}A_{x,y}f(y)|$ (definition)
     $\le \sum_{y\in V}|A_{x,y}||f(y)|$ (triangle inequality)
     $\le |f(x)| \sum_{y\in V}|A_{x,y}|$ (by design of x)
     $= d|f(x)|$ (d-regular)
3) By results from spectrum theorem, multiplicity of eigenvalue d is equal to the dimension of its associated eigenspace, i.e. 
     $E_{d}(A) = \{f\in L^{2}(V) | Af = d \cdot f\}$
    WTS:  $dim(E_{d}(A)) = 1 \iff$ X is connected  
    With this, $\lambda_{1}$ cannot be equal to $\lambda_{0} = d$ (note eigenvalue $\lambda$'s are labelled in descending order), hence $λ_{1}(X) < λ_{0}(X)$
    1) Suppose X is connected, and f is an arbitrarily chosen eigenfunction associated with d. We will show that f is constant on V, hence eigenspace of d is of dim 1. 
     - Pick $x\in V$ s.t. $|f(x)| = max_{y\in V}|f(y)|$
     - WLOG, f(x) > 0, since -f is also an eigenfunction of d
     - Then, $f(x) = \frac{(Af)(x)}{d} = \sum_{y\in V}\frac{A_{x,y}}{d}f(y)$ (def of adjacency operator)
     - WTS: f(y) = f(x) for any y adjacent to x
         Suppose not. Then, f(t) < f(x) for some t adjacent to x. Then, since f(x) is the maximum, we have: $f(x) = \sum_{y\in V}\frac{A_{x,y}}{d}f(y) < \sum_{y\in V}\frac{A_{x,y}}{d}f(x) = f(x)$ (at least one <), contradiction. 
    - Repeat the process for each y that is adjacent to x, eventually we reach every vertex of X since X is connected. Hence f is constant on X. 
     2) Suppose X is disconnected. 
     - WTS: $dim(E_{d}(A)) > 1$, we show by constructing two linearly independent eigenfunctions associated with d
     - Let $V_{1}$ be the set of all vertices w that there is a walk from v to w in X.
     - Let $V_{2} = V \setminus V_{1}$ 
     - Define the functions: 
     - $f_{1}(x) = 1$ if $x \in V_{1}$, $f_{1}(x) = 0$ if $x \in V_{2}$; 
     - $f_{2}(x) = 0$ if $x \in V_{1}$, $f_{2}(x) = 1$ if $x \in V_{2}$; 
     - Then it is easy to check two functions are linearly independent. 
4) Suppose $V = V_{1}$ $\cup$ $V_{2}$, is a bipartition, λ is an eigenvalue with multiplicity k. Then by spectrum theorem, there are orthogonal eigenfunctions $f_{1}, \dots, f_{k}$ . For $i = 1, \dots, k$ , define the functions $$g_{i}(x)= \left\{\begin{array}{ll} f_{i}(x) & x \in V_{1} \\ -f_{i}(x) & x \in V_{2}\end{array} \right.$$WTS: each $g_{i}$ is an eigenfunction with associated eigenvalue $-\lambda$. Hence $-\lambda$ is an eigenvalue with multiplicity $m \ge k$. Same argument, reversing the roles of $\lambda$ and $-\lambda$ shows that $k \ge m$, so $m = k$, done. 
     For arbitrary $x \in V_{1}$, since every $y$ adjacent to $x$ is in $V_{2}$, we have:
     $(Ag_{i})(x) \, \, \, = \sum_{y\in V_{2}}A_{x,y}g_{i}(y)$ (adjacency operator)
             $= -\sum_{y\in V}A_{x,y}f_{i}(y)$ (for $y\in V_{1}$, $A_{x,y}=0$ so don't matter)
             $= -(Af_{i})(x)$ (adjacency operator)
             $= -\lambda f_{i}(x)$ (eigenvalue)
             $= -\lambda g_{i}(x)$ (definition, since $x \in V_{1}$ )
     Similar for $x \in V_{2}$. Hence $-\lambda$ is an eigenvalue. 
5) Assume X is connected. 
     - Suppose $-d$ is an eigenvalue, and f be an associated eigenfunction. 
     - Pick $x \in V$ s.t. $|f(x)| = \max_{y\in V}|f(y)|$
     - WLOG, $f(x) > 0$, since $-f$ is also an eigenfunction. 
     - Following argument in part (3)(1), we can show that $f(y) = -f(x)$ for all $y$ adjacent to $x$. By connectivity, eventually we have:
     $$f(y) = \left\{\begin{array}{ll} f(x) & \textrm{if $dist(x,y)$ is even}\\ -f(x) & \textrm{if $dist(x,y)$ is odd}\end{array} \right.$$
     - This gives a bipartition of $V$ by the value of $f(y)$. 
    The case for disconnected X is omitted. 


> **Definition 1.17 Circulant Matrix**
> 1) A circulant matrix $C$ is of the form: 
> $$ C = \left( \begin{array}{ccccc}
c_{0} & c_{1} & c_{2} & \ldots &c_{n-1}\\
c_{n-1} & c_{0} & c_{1} & \ldots &c_{n-2} \\
c_{n-2} & c_{n-1} & c_{0} & \ldots &c_{n-3} \\
\vdots & \vdots &\vdots & \ddots &\vdots \\
c_{1} & c_{2} & c_{3} & \ldots &c_{0} 
\end{array} \right) $$
>  2) The eigenvalues of the circulant matrix C given above are:
>  $$ \chi_{a} = \sum^{n-1}_{j=0}c_{j}\xi^{aj}$$
>  where $\xi = \exp(2\pi i/n)$ and $a = 0,1,2,\dots,n-1$

(Proof omitted)

> **Lemma 1.18**
> Let $n \ge 2$ and $a$ be integers. Let $\xi = \exp(2\pi i/n)$. Then 
> $$ \sum^{n-1}_{j=0}(\xi^{a})^{j} = \left\{\begin{array}{ll} 0 & \textrm{if $n$ does not divide $a$} \\n & \textrm{otherwise} \end{array} \right.$$

Proof
- If n divides a, then $\xi^{a} = 1$, done. 
- If not, then sum of geometric series. 

Example: Eigenvalues for complete graph $K_{n}$
- Definition from graph theory: graph with $n$ vertices, where vertices $v$ and $w$ are adjacent, via an edge of multiplicity 1, iff $v \ne w$. 
- Reformulation with Cayley graph: $K_{n} = Cay(\mathbb{Z}_{n}, \{1,2,\dots,n\})$
- Its adjacency matrix: $$\left( \begin{array}{ccccc}
0 & 1 & 1 & \ldots &1\\
1 & 0 & 1 & \ldots &1 \\
1 & 1 & 0 & \ldots &1 \\
\vdots & \vdots &\vdots & \ddots &\vdots \\
1 & 1 & 1 & \ldots & 0 
\end{array} \right) $$
- This is circulant. Hence we know the formula for all its eigenvalues. 
     If $a=0$, then $\chi_{0}=n-1$ ($c_{i}=0$ except for $i=0$)
     If $0 < a \le n-1$, then a cannot divide n. Applying lemma 1.18, we have: $$\chi_{a} = \sum^{n-1}_{j=0}c_{j}\xi^{aj} = \sum^{n-1}_{j=0}\xi^{aj}-1 = 0-1 = -1$$
- Hence, $$Spec(K_{n}) = \left(\begin{array}{cc} -1 & n-1 \\ n-1 & 1 \end{array} \right)$$
- Formulation of circulant matrix provides a quick computation for eigenvalues of all complete graphs. However, most regular graphs do not have such nice property. 



# 5. The Laplacian 
In this section we consider Laplacian on graph, which measures the inflow and outflow of a vertex. 

> **Definition 1.19**
> Graph X, vertex set V, edge set E.
> 1) Orientation: Give each edge $e$ an arbitrary orientation: from endpoint $e^{-}$ (origin) to the other endpoint $e^{+}$ (extremity). For loops, $e^{-}=e^{+}$.
> 2) Analogue of gradient: $d: L^{2}(V) \rightarrow L^{2}(E)$, s.t.  for each $f \in L^{2}(V)$ $$(df)(e)=f(e^{+})-f(e^{-})$$
> 3) Analogue of divergence: $d^{*}: L^{2}(E) \rightarrow L^{2}(V)$, s.t. for each $f \in L^{2}(E)$ $$(d^{*}f)(v) = \sum_{\substack{e\in E \\ v=e^{+}}}f(e) - \sum_{\substack{e\in E \\ v=e^{-}}}f(e) $$
> 4) Laplacian operator: $\Delta = d^{*}d$ 

Remark: 
- $(df)(e)$ measures the change of $f$ along the edge $e$, $(d^{*}f)(v)$ measures the total inward flow at vertex $v$. 
- Laplacian operator is introduced to simplify proofs in later chapters. 

> **Lemma 1.20 Laplacian does not depend on the choice orientation**
> X be a $k$-regular graph, with vertex set $V$, edge multiset $E$, and adjacency operator $A$. Then, $\Delta = kI - A$

Proof 
Let $f \in L^{2}(V)$ and $x \in V$. Then $$\begin{aligned} (\Delta f)(x) &= (d^{*}(df))(x) = \sum_{\substack{e\in E \\ v=e^{+}}}(df)(e)-\sum_{\substack{e\in E \\ v=e^{-}}}(df)(e)\\ &= \left(\sum_{\substack{e\in E \\ x=e^{+}}}f(x) - \sum_{\substack{e\in E \\ x=e^{+} \\ y=e^{-}}}f(y)\right) - \left(\sum_{\substack{e\in E \\ x=e^{-} \\ y=e^{+}}}f(y) - \sum_{\substack{e\in E \\ x=e^{-}}}f(x)\right) \\ &= \sum_{\substack{e\in E \\ x=e^{+} \, or \, x=e^{-}}}f(x) - \sum_{\substack{e \in E \\ x=e^{+}and \,y=e^{-} \, or \, x=e^{-} and \, y=e^{+}}}f(y) \\ &= kf(x) - \sum_{y\in V}A_{x,y}f(y) \\ &= ((kI-A)f)(x)  \end{aligned}  $$
First two lines by definition, third line by rearrange summation. 

Remark:
- The proof relies on the definition that loops are counted only once. 
- Since $\Delta = kI - A$, we have a linear transformation $\Delta: L^{2}(V) \rightarrow L^{2}(V)$ 
- $\Delta (\alpha f) = \alpha \Delta f$ for $\alpha \in \mathbb{C}$ (obvious from proof above)

> **Proposition 1.21 Eigenvalues of $\Delta$**
> $X$ is a $k$-regular graph, vertex set $V$, edge multiset $E$, $n=|V|$
> 1) The eigenvalues of $\Delta$ are: $$ 0 = k-\lambda_{0}(X) \le k-\lambda_{1}(X) \le \dots \le k-\lambda_{n-1}(X)$$ In particular, the eigenvalues of $\Delta$ lie in $[0,2k]$.
> 2) $f \in L^{2}(V)$, $g \in L^{2}(E)$. Then $$\langle df,g \rangle_{2} = \langle f,d^{*}g \rangle_{2}$$ and $$\langle \Delta f,f \rangle_{2} = \sum_{e\in E}|f(e^{+})-f(e^{-})|^{2}$$

Proof
1) $Af = \lambda f$ iff $(kI-A)f = (k-\lambda)f$, so we get eigenvalues. Recall for $k$-regular graph, its eigenvalues are bounded by $k$, so we have bounds for $\Delta$.
2) $$\begin{aligned} \langle df,g \rangle_{2} &= \sum_{e\in E}(df)(e)\overline{g(e)} = \sum_{e\in E}[f(e^{+}-f(e^{-}))]\overline{g(e)} \\ &= \sum_{e\in E}f(e^{+})\overline{g(e)} - \sum_{e\in E}f(e^{-})\overline{g(e)} \\ &= \sum_{v\in V}f(v)\sum_{\substack{e\in E \\ v=e^{+}}}\overline{g(e)} - \sum_{v\in V}f(v)\sum_{\substack{e\in E \\ v=e^{-}}}\overline{g(e)} \\ &= \sum_{v\in V}f(v)\overline{(d^{*}g)(v)} \\ &= \langle f,d^{*}g \rangle_{2} \end{aligned}$$
First and last lines are by definition. Second line opens the bracket. For the third line, if there is some v s.t. v is not equal to any $e^{+}$, then that term would be zero. Same for the second bulk with $e^{-}$. So the equation is legitimate. 
3) $$\begin{aligned} \langle \Delta f,f \rangle_{2} &= \langle d^{*}df,f \rangle_{2} = \overline{\langle  f,d^{*}df \rangle_{2}} \\ &= \overline{\langle  df,df \rangle_{2}} = \langle  df,df \rangle_{2} = ||df||^{2}_{2} \\ &= \sum_{e\in E}|f(e^{+})-f(e^{-})|^{2} \end{aligned} $$
From first line to second line by result (2), rest by definition. 



# 6. The Isoperimetric Constant
We want to study the quality of graph as a communication network. 
Standard for a good communication network: Each vertex has lots of neighbours (quick transmission), and the total number of edges is relatively small (low cost).

>**Definition 1.22 Isoperimetric constant**
>1) Graph $X$ with vertex set $V$, $F \in V$. The $boundary$ of $F$, $\partial F$ , is the set of edges connecting $F$ to $V \setminus F$.
>2) The isoperimetric constant of $X$ is defined as $$h(X) = \min \left\{ \frac{|\partial F|}{\min \{ |F|, |V \setminus F| \}} \; \biggr\rvert \; F \subset V  \right\} $$

Remark: 
- Numerator is the number of neighbours and denominator is the size of the set. We ask the question: does the set have lots of neighbours relative to its size? 
- The outer minimum takes the worst scenario across the graph. 
- We only want to consider information flow from a smaller part of the graph to the rest. Hence, the denominator must be less than $n/2$ , so we put another minimum there. Alternatively, we can restrict $F$ with $|F| \le n/2$.
- In summary, isoperimetric constant measures neighbourhood situation. 

> **Properties of Isoperimetric constant**
> 1) Suppose that $X$ is a $d$-regular graph. Then $0\le h(X) \le d$.
> 2) $h(X) = 0$ iff $X$ is disconnected. 

Proof 
1) LHS: 
   - non-negative is obvious. 
   - Singleton takes 0.
2) RHS: 
   - $\frac{|\partial F|}{|F|} \le \frac{d|F|}{|F|}$, i.e. every vertex of $F$ has all its edges incident with some vertex in $V \setminus F$, and this is a $d$-regular graph. An upper bound. 
   - Take $F$ to be a single point, upper bound achieved. 
3) $h(X) = 0 \Leftrightarrow \exists F \in X \, s.t. \, \partial F = \varnothing$, hence $X$ must be disconnected. 

Example:
![[Screenshot 2024-09-05 at 22.25.01.png]]

Motivation: 
- $h(K_{n})$ grows as at polynomial n. However, $K_{n}$ has too many edges, which makes it expensive. 
- We restrict the number of edges by considering regular graphs only. Then, we want to construct arbitrarily large graph with large isoperimetric constants. 

> **Definition 1.23 Bounded away from zero**
> Sequence $\{a_{n}\}$ is bounded away from zero if there exists $\epsilon > 0$ s.t. $a_{n} \ge \epsilon$ for all $n$. 

> **Definition 1.24 $\textcolor{red}{\textrm{Expander Family}}$**
> $\{X_{n}\}$ is a sequence of $d$-regular graphs s.t. $|X_{n}| \rightarrow \infty$ as $n \rightarrow \infty$. We say $\{X_{n}\}$ is an $expander \, family$ if the sequence $\{h(X_{n})\}$ is bounded away from zero.

Remark: 
There are other definitions of expander family, but I postpone their introductions until they are necessary. 

Example: There do not exist expander families of degree 2 
- Fact: Any connected 2-regular graph must be isomorphic to $C_{n}$ for some $n$. 
- Suffice to show that $\{C_{n}\}$ is not an expander family.
- (book p28, omitted)



# 7. The Rayleigh-Ritz Theorem 
Bounds for the second eigenvalue $\lambda_{1}(X)$ 

> **Definition 1.25**
> $X$ finite set, $f_{0}$ function constant on 1 on all of $X$. Define $$L^{2}(X,\mathbb{R}) = \{f:X\rightarrow \mathbb{R}\}$$ and $$ \begin{aligned} L^{2}_{0}(X,\mathbb{R}) &= \{f \in L^{2}(X,\mathbb{R}) \; \vert \; \langle f,f_{0} \rangle_{2} = 0\} \\ &= \{f \in L^{2}(X,\mathbb{R}) \; \vert \; \sum_{x\in X}f(x)=0 \}  \end{aligned}  $$

Remark: 
$L^{2}(X,\mathbb{R}) \subset L^{2}(X)$. However, we can also directly define $L^{2}_{0}(X)$ on entire $X$ with  $\langle f,f_{0} \rangle_{2} = 0$, and we still have Proposition 1.26. 

>**Proposition 1.26 Rayleigh-Ritz**
>$X$ is a $d$-regular graph with vertex set $V$. Then $$\lambda_{1}(X) = \max_{f\in L^{2}_{0}(V,\mathbb{R})} \frac{\langle Af,f_{0} \rangle_{2}}{||f||^{2}_{2}} = \max_{\substack{f\in L^{2}_{0}(V,\mathbb{R}) \\ ||f||_{2} = 1}}\langle Af,f_{0} \rangle_{2} $$
>Equivalently, $$d-\lambda_{1}(X) = \min_{f\in L^{2}_{0}(V,\mathbb{R})} \frac{\langle \Delta f,f \rangle_{2}}{||f||^{2}_{2}} = \min_{\substack{f\in L^{2}_{0}(V,\mathbb{R}) \\ ||f||_{2} = 1}}\langle \Delta f,f \rangle_{2} $$

Proof
1) Equivalence: Note $A = dI - \Delta$. The results follows from addition of inner product and the fact that $\langle  df,f \rangle_{2}= d||f||^{2}_{2}$.
2) By Spectrum Theorem, we can expand $f_{0}$ to an orthonormal basis $\{f_{0},f_{1},\dots,f_{n-1}\}$ of $L^{2}(X,\mathbb{R})$, where each $f_{i}$ is an associated eigenfunction of eigenvalue $\lambda_{i} = \lambda_{i}(X)$. 
     Let $f \in L^{2}_{0}(X,\mathbb{R})$ with $||f||_{2}=1$. 
     Since we have a basis, $f = c_{0}f_{0}+c_{1}f_{1}+\dots+c_{n-1}f_{n-1}$ for some $c_{i} \in \mathbb{R}$.
     Also, $$ \begin{aligned} 0 &= \langle  f,f_{0} \rangle_{2} \\ &= c_{0}\langle  f_{0},f_{0} \rangle_{2} + c_{1}\langle  f_{1},f_{0} \rangle_{2} + \dots + c_{n-1}\langle  f_{n-1},f_{0} \rangle_{2} = c_{0}   \end{aligned}$$
     First line by definition, second line by  orthonormal basis. 
     So, $f = c_{1}f_{1}+\dots+c_{n-1}f_{n-1}$.
     Then $$\begin{aligned} \langle  Af,f \rangle_{2} &= \langle  A\sum^{n-1}_{i=1}c_{i}f_{i} ,\sum^{n-1}_{i=1}c_{i}f_{i} \rangle_{2} = \langle  \sum^{n-1}_{i=1}\lambda_{i}c_{i}f_{i} ,\sum^{n-1}_{j=1}c_{j}f_{j} \rangle_{2} \\ &= \sum_{i=1}^{n-1}\sum_{j=1}^{n-1}c_{i}c_{j}\lambda_{i} \langle  f_{i},f_{j} \rangle_{2} = \sum_{i=1}^{n-1}c_{i}^{2}\lambda_{i}  \\ &\le \lambda_{1}\sum_{i=1}^{n-1}c_{i}^{2} \\ &= \lambda_{1}||f||^{2}_{2} = \lambda_{1}   \end{aligned}$$First line by expression of $f$, second line by the orthonormal basis (only equal to 1 for same $f_{i}$, otherwise 0), from second to third line by the fact that $\lambda_{1}$ is the second largest and the expression there exclude $\lambda_{0}$ (hence $\lambda_{1}$ is the largest). Last line by definition of $f$. 
     Hence we find an upper bound. Suffice to show this upper bound can be achieved. 
     Note $f_{1} \in L^{2}_{0}(X,\mathbb{R})$ with $||f_{1}||_{2}=1$, and $\langle  Af_{1} ,f_{1}  \rangle_{2} = \langle  \lambda_{1} f_{1} ,f_{1} \rangle_{2} = \lambda_{1}$.
     Hence $\lambda_{1}$ is indeed the maximum. 

Remark:
- Fact: $\overline{\langle  Af,f \rangle_{2}} = \overline{\langle  f,Af \rangle_{2}} = \langle  Af,f \rangle_{2}$, since $A$ as a real symmetric matrix has self-adjoint corresponding operator. Hence $\langle  Af,f \rangle_{2}$ is real, and the proof above applies to $L^{2}_{0}(X)$ defined on entire $X$. That is, we have $$\lambda_{1}(X) = \max_{g\in L_{0}^{2}(X)} \frac{\langle  Ag,g \rangle_{2}}{||g||^{2}_{2}} = \max_{\substack{g\in L^{2}_{0}(X) \\ ||g||^{2}_{2}=1 }}\langle  Af,f \rangle_{2}$$
- By cleverly choosing $f$, we can have a good lower bound for $\lambda_{1}$. 

> **Proposition 1.27 Bounds for $h(X)$**
> $X$ is a $d$-regular graph with vertex set $V$, edge multiset $E$. Then $$\frac{d-\lambda_{1}(X)}{2} \le h(X) \le \sqrt{2d(d-\lambda_{1}(X))}$$ (Proof omitted)

Remark: 
This results connect the lower bound of $\lambda_{1}(X)$ with the bounds of $h(X)$, hence useful for expander family. Roughly speaking, the smaller $\lambda_{1}(X)$ is, the larger $h(X)$ is, and the better the communication network would be. 

> **Definition 1.28 Spectral gap**
> 1) If $X$ is a connected $d$-regular graph, then $d−\lambda_{1}(X)$ is called the spectral gap of $X$.
> 2) $\{X_{n}\}$ is a sequence of $d$-regular graphs s.t. $|X_{n}| \rightarrow \infty$ as $n \rightarrow \infty$. We say $\{X_{n}\}$ is an $expander \, family$ iff $\{d−\lambda_{1}(X)\}$ is bounded away from zero. 

Remark: 
The corollary follow naturally from Proposition 1.27. Because this corollary, in the search of expander family, we focus on graph spectra. 

Example: 
Let $\Gamma = \{\sigma, \sigma^{-1}, \tau \} \subset S_{n}$ where $\sigma = (1,2,\dots,n)$ and $\tau = (1,2)$. We will show that $(X_{n}) = (Cay(S_{n},\Gamma))$ is not an expander family. 
- Each $X_{n}$ is 3-regular, since there are only 3 elements in $\Gamma$ and decomposition of each element into $xy$ only yields one $y$ for fixed $x$. 
- Suffice to show $3-\lambda_{1}(X_{n}) \rightarrow 0$ as $n \rightarrow \infty$ 
- _Key: find a good $f$ and Raleigh-Ritz_
- Define $f \, : \, S_{n} \rightarrow \mathbb{C}$ by $f(\alpha) = \exp(\frac{2\pi i}{n}\cdot \alpha^{-1}(1))$
- We first show that $f \in L^{2}_{0}(S_{n})$, so $\lambda_{1}(X_{n}) \ge \langle  Af,f \rangle_{2} / \langle  f,f \rangle_{2}$
     - 



# 8. Powers and Products of Adjacency Matrices

> **Definition 1.29 Digraph**
> 1) Define directed graph $X$ to be a set $V$ (vertices) and a multiset $E$ (directed edges), where every element of $E$ is an ordered pair $(v,w)$, called the directed edge from $v$ to $w$ and visualised as an arrow from $v$ to $w$, of elements of $V$. 
> 2) Define the adjacency matrix of digraph $X$ to be the $n \times n$ matrix whose $ij$ entry equals the number of directed edges from $v_{i}$ to $v_{j}$ in $X$. 

>**Definition 1.30 $X_{1} \cdot X_{2}$**
>$X_{1}$ and $X_{2}$ are two finite graphs (not necessarily digraphs) with same vertex set $V$. Define $X_{1} \cdot X_{2}$ to be the digraph with vertex set $V$, where multiplicity of the directed edge from $v_{1}$ to $v_{2}$ equals the number of pairs $(e_{1}, e_{2})$ s.t. $e_{1}$ is a directed edge in $X_{1}$ which starts at $v_{1}$ , and $e_{2}$ is a directed edge in $X_{2}$ which points from the terminal point of $e_{1}$ to $v_{2}$.

Remark: 
Essentially, we are taking a walk with length 2, first step in $X_{1}$ and second step in $X_{2}$. 

Example:
From graph $X$ and graph $Y$, construct $X \cdot Y$

![[Screenshot 2024-09-06 at 09.30.32.png]]

![[Screenshot 2024-09-06 at 09.30.41.png]] 
![[Screenshot 2024-09-06 at 09.30.49.png]]
The adjacency matrix $$A_{X \cdot Y} = \left( \begin{array}{ccc}
0 & 0 & 0 \\
0 & 2 & 3 \\
0 & 0 & 1  
\end{array} \right) $$
> **Definition 1.31 $X^{n}$**
> $X$ is a finite graph with vertex set $V$. Define $X^{n}$ to be the graph with vertex set $V$, where the multiplicity of the edge from $v_{1}$ to $v_{2}$ equals to the number of walks of length $n$ from $v_{1}$ to $v_{2}$. That is, $$X^{n} = X \cdot X \dots X$$

Remark: 
Repeat $X \cdot X$ for $n$ times, with same interpretation. 

> **Proposition 1.32**
> 1) $A_{X_{1} \cdot X_{2}} = A_{1} \cdot A_{2}$ (when $X_{1}$ and $X_{2}$ has same ordering of vertices )
> 2) $A_{X^{n}} = A^{n}$ 

Proof: 
1) Denote entries of $A_{1}$ as $p_{ij}$, entries of $A_{2}$ as $q_{ij}$, then for an arbitrary entry of $A_{X_{1} \cdot X_{2}}$ denoted as $A_{ij}$, by matrix multiplication, we have: $$A_{ij} = \sum^{n}_{k=1}p_{ik}q_{kj}$$ which matches the definition of an edge in $X_{1} \cdot X_{2}$ exactly. 
2) Repeat (1).

> **Proposition 1.33**
> $X$ is a finite graph with eigenvalues $\lambda_{0}, \dots, \lambda_{n-1}$. Then the eigenvalues of $X^{j}$ are $\lambda_{0}^{j}, \dots, \lambda_{n-1}^{j}$. 

Proof:
By spectrum theorem, we have $PAP^{-1}$ as a matrix with diagonal entries $\lambda_{0}, \dots, \lambda_{n-1}$ (since $A$ is diagonalisable), where $P$ is unitary. Since $PA^{j}P^{-1} = PAP^{-1}PAP^{-1}\dots PAP^{-1}$, we have eigenvalues of $X^{j}$ as $\lambda_{0}^{j}, \dots, \lambda_{n-1}^{j}$. 

> **Definition 1.34 Directed Cayley graph**
> $G$ is a group, and $\Gamma$ is a multi-subset of $G$. The directed Cayley graph of $G$ with respect to $\Gamma$, $Cay(G, \Gamma)$, is defined as follow. Vertices are the elements of $G$. For all $x, y \in G$, the multiplicity of the directed edge from $x$ to $y$ in $Cay(G, \Gamma)$ equals the number of elements $\gamma$ in $\Gamma$, counted with multiplicity, s.t. $x\gamma=y$. 

Note: then definition on the book is inconsistent with next proposition. 

> **Proposition 1.35**
> $G$ is a group, $\Gamma_{1}, \Gamma_{2} \subset G$. $X_{1} = Cay(G, \Gamma_{1})$ and $X_{2} = Cay(G, \Gamma_{2})$. Let $$\Gamma_{1}\Gamma_{2}=\{\gamma_{1}\gamma_{2} \, \vert \, (\gamma_{1},\gamma_{2}) \in \Gamma_{1} \times \Gamma_{2}  \}$$ Then $X_{1} \cdot X_{2} = Cay(G, \Gamma_{1}\Gamma_{2})$.

Proof: just unfold the definition

 