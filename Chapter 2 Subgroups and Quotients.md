Negative results: under what conditions we cannot have expander families.
# 1. Coverings and Quotients 
> **Definition 2.1 Graph Homomorphism**
> 1) Graph $X$ with $V,E$, another graph $X'$ with $V',E'$. A graph homomorphism between $X$ and $X'$ is a pair of maps $\phi_{V}: V \rightarrow V'$ and $\phi_{E}: E \rightarrow E'$, where whenever $e \in E$ has endpoints $a,b \in V$ and $\phi_{E}(e)$ has endpoints $a',b'\in V'$, then $\phi_{V}(\{a,b\}) = \{a',b'\}$. 
> 2) Usually write $\phi$ for two homomorphisms. 
> 3) If both $\phi_{V}$ and $\phi_{E}$ are bijective, then $\phi$ is an isomorphism.
> 4) For vertex $v$ of graph X, let $E_{v}$ be the set of edges incident to $v$. $E_{v}$ is a set, we regard multiple edges as distinct elements. With homomorphism $\phi$, $E_{v}$ is mapped to $E_{\phi(v)}$.

>**Definition 2.2 Covering**
>Homomorphism $\phi : X \rightarrow Y$, and $v$ is a vertex of $X$. 
>1) $\phi$ is bijective at $v$, if the map from $E_{v}$ to $E_{\phi(v)}$ induced by $\phi$ is bijective. 
>2) $\phi$ is locally bijective, if $\phi$ is bijective at every vertex of $X$. 
>3) $\phi$ is a covering from $X$ to $Y$, if $\phi$ is locally bijective and $\phi$ maps the vertex set of $X$ surjectively onto the vertex set of $Y$. 
>4) We say $X$ covers $Y$ if such a covering $\phi$ exists. 

Example 
![[Screenshot 2024-09-12 at 18.57.50.png]]
Covering $\phi:$ $\phi(v_{1}) = \phi(v_{4}) = w_{1}$, $\phi(v_{2}) = \phi(v_{3}) = w_{2}$,  $\phi(v_{5}) = \phi(v_{6}) = w_{3}$.

> **Lemma 2.3 Properties of covering**
> 1) If $X$ covers $Y$, then $X$ is $d$-regular iff $Y$ is $d$-regular. 
> 2) If $X$ covers $Y$ and $X$ is connected, then $Y$ is connected. 

Proof:
1) Immediately follows from bijection between $E_{v}$ and $E_{\phi(v)}$.
2) Let $w_{1}, w_{2}$ be two vertices of $Y$. Since $\phi$ is a surjective map of vertex set from $X$ to $Y$, there exists $v_{1}, v_{2}$ of $X$ s.t. $\phi(v_{1}) = w_{1}, \phi(v_{2}) = w_{2}$. Since $X$ is connected, there is a walk from $v_{1}$ to $v_{2}$ using edges $e_{1}, e_{2}, \dots, e_{n}$. Then the edges $\phi(e_{1}), \dots, \phi(e_{n})$ is also a walk in $Y$ from $w_{1}$ to $w_{2}$ since $\phi$ is a homomorphism. 

>**Definition 2.4 Fibre**
>Covering $\phi: X \rightarrow Y$, $w$ is a vertex of $Y$. 
>Then the fibre of $\phi$ at $w$, $\phi^{-1}(w)$, is the set of all vertices $v$ of $X$ s.t. $\phi(v)=w$. 

Remark: 
i.e. the preimgae of $w$ in $X$. Note $\phi$ is surjective for vertices. 

>**Lemma 2.5 For connected graphs, all fibres have same size**
>Covering $\phi: X \rightarrow Y$. 
>If $Y$ is connected (equivalently, $X$ is connected), then $|\phi^{-1}(w_{1})| = |\phi^{-1}(w_{2})|$ for all vertices $w_{1}, w_{2}$ of $Y$. 

Proof:
- Induction on $dist(w_{1}, w_{2})$, which is finite since $Y$ is connected.
- We first show this is true for adjacent $w_{1}, w_{2}$. 
- Let $m$ be the number of edges between $w_{1}, w_{2}$. Clearly $m > 0$.
- The number of edges between a vertex in $\phi^{-1}(w_{1})$ and a vertex in  $\phi^{-1}(w_{2})$ is $m \cdot | \phi^{-1}(w_{1})|$. (Fix a vertex in  $\phi^{-1}(w_{1})$, then considering vertices in  $\phi^{-1}(w_{2})$)
- Reverse the roles of $w_{1}$ and $w_{2}$, the number is  $m \cdot |\phi^{-1}(w_{2})|$. (Fix a vertex in  $\phi^{-1}(w_{2})$, then considering vertices in  $\phi^{-1}(w_{1})$)
- Hence  $|\phi^{-1}(w_{1})| =  |\phi^{-1}(w_{2})|$.
- The fibre of a vertex that is $j$ distance away has the same size as the fibre of a vertex that is $j+1$ distance away, since we can always consider the last step in the walk connecting two vertices. Inductive steps done.

>**Lemma 2.6**
> If $X$ and $Y$ are finite graphs s.t $X$ covers $Y$, then $h(X) \le h(Y)$. 

Proof
- If $Y$ is not connected, then by contrapositive of Lemma 2.3, so as $X$. All 0, done. 
- Suppose $Y$ is connected. 
- Let $S$ be a set of vertices of $Y$ s.t. $h(Y) = \frac{|\partial S|}{|S|}$ and $|S| \le \frac{1}{2}|Y|$. 
- Let $$\phi^{-1}(S) = \{v \in V_{X} \, \vert \, \phi(v) \in S \} $$
- Let $w$ be an arbitrary vertex of $Y$, $a = |\phi^{-1}(w)|$. 
- By Lemma 2.5, $|\phi^{-1}(S)| =a|S|$, and $|X| = a|Y|$. 
- Thus $|\phi^{-1}(S)| =a|S| \le \frac{a}{2}|Y| = \frac{1}{2}|X|$, which makes a proper set to be considered for isoperimetric constant. 
- Also, $|\partial [\phi^{-1}(S)]| = a|\partial S|$. Every edge in $\partial S$ has exactly $a$ preimage in $X$ ($a$ vertices collapsed into one vertex in $Y$, somehow similar to Lemma 2.5).
- Hence $$h(X) \le \frac{|\partial[\phi^{-1}(S)] |}{|\phi^{-1}(S)| } = \frac{a|\partial S|}{a|S|} = h(Y)$$

>**Definition 2.7 Coset Graph**
>Group $G$, $\Gamma$ symmetric in $G$, $H \le G$. Define the coset graph $Cos(H\backslash  G, \Gamma)$ as:
>1) vertex set: $H\backslash G$, set of right cosets of $H$ in $G$
>2) multiplicity between $Hx$ and $Hy$: number of $\gamma$ in $\Gamma$, counted with multiplicity, s.t. $Hx = Hy\gamma$.

Remark:
1) $Cos(H\backslash G, \Gamma)$ is $|\Gamma|$-regular.
2) $G/H:$ left cosets; $G\backslash H:$ right cosets.
3) If $H \triangleleft G$, then $G/H = G\backslash H$, and we have quotient group $G/H$. The map $G \rightarrow G/H$ by $a \mapsto aH$ is the canonical homomorphism. 
4) If $H \triangleleft G$, then $Cos(H\backslash G, \Gamma) = Cay(G/H, \overline{\Gamma})$, where $\overline{\Gamma} = \{\gamma H \, \vert \, \gamma \in \Gamma \}$ is the image of $\Gamma$ under the canonical homomorphism. Proof is just checking edge set and vertex set.

>**Lemma 2.8**
>Group $G$, $H \le G$, $\Gamma$ symmetric in $G$. 
>1) $Cay(G, \Gamma)$ covers $Cos(H\backslash G, \Gamma)$.
>2) $h(Cay(G,\Gamma)) \le h(Cos(H\backslash  G, \Gamma))$

Proof
- For $g\in G, \gamma \in \Gamma$, denote by $e(g,\gamma)$ the edge in $Cay(G,\Gamma)$ between $g$ and $g\gamma$ induced by $\gamma$; denote by $e(Hg,\gamma)$ the edge in $Cos(H\backslash G, \Gamma)$ between $Hg$ and $Hg\gamma$ induced by $\gamma$. 
- $\phi: Cay(G,\Gamma) \rightarrow Cos(H\backslash G, \Gamma)$, by $g \mapsto Hg, \, e(g,\gamma) \mapsto e(Hg,\gamma)$. Suffice to show $\phi$ is a covering.
- Surjective: trivial. 
- Injective: The number of edges must be the same. (handwritten graph)
- (2) immediately follows from (1) and Lemma 2.6.

>**Definition 2.9 Sequence of Quotients**
>$\{G_{n} \}, \{Q_{n} \}$ are sequences of finite groups. We say $\{G_{n} \}$ admits $\{Q_{n} \}$ as a sequence of quotients, if for each $n$ there exists $H_{n} \triangleleft G_{n}$ s.t. $G_{n}/H_{n} \cong Q_{n}$. 

>**Definition 2.10 Yields an expander family**
> $\{G_{n} \}$ is a sequence of finite groups. We say $\{G_{n}\}$ yields an expander family, if for some positive integer $d$, there exists a sequence $\{\Gamma_{n}\}$ where for each $n$, $\Gamma_{n}$ is symmetric in $G_{n}$ with $|\Gamma_{n}|= d$, so the sequence $\{Cay(G_{n}, \Gamma_{n})\}$ is an expander family.

>**Proposition 2.11 Quotients Non-expansion Principle**
> $\{G_{n} \}$ is a sequence of finite groups. Suppose $\{G_{n}\}$ admits $\{Q_{n}\}$ as a sequence of quotients. If $\{Q_{n}\}$ does not yield an expander family, then $\{G_{n}\}$ does not yield an expander family. 

Proof 
- Suppose not true. There exists a positive integer $d$ s.t. for each $n$, there is a $\Gamma_{n}$ symmetric in $G_{n}$ s.t. $Cay(G_{n}, \Gamma_{n})$ is an expander family. 
- Let $\overline{\Gamma_{n}}$ be the image of $\Gamma_{n}$ under the canonical homomorphism. 
- Then $Cos(H_{n}\backslash G_{n}, \Gamma_{n} ) = Cay(G_{n} /H_{n} , \overline{\Gamma_{n}})$ has isoperimetric constants larger than $Cay(G_{n}, \Gamma_{n})$, hence $\{Cay(Q_{n},\overline{\Gamma_{n}})\}$ is an expander family. 

Remark: 
- We can develop this principle with left cosets only. I doubt this formulation in book is designed as a comparison with next section.
- Next target is to restate the result with eigenvalues. 

>**Definition 2.12 Pullback**
>Homomorphism $\phi: X \rightarrow Y$. Let $f \in L^{2}(Y)$. 
>Define $f^{*} \in L^{2}(X)$ by $f^{*} = f \circ \phi$. We say $f^{*}$ is the pullback of $f$ via $\phi$. 

>**Lemma 2.13**
>$X$ covers $Y$. Let $A, \tilde{A}$ be the adjacency operators of $Y, X$, respectively. Let $f \in L^{2}(Y)$. Then $$(Af)^{*}=\tilde{A}f^{*}$$

Proof 
- $v$ be an arbitrary vertex of $X$, and $E_{v}$ is the set of all edges incident to $v$. 
- If $e$ is an edge in $Y$ incident to $v$, let $e(v)$ denote the other vertex incident to $e$. 
- Similarly, use $\tilde{e}$ for edges in $X$.
- Then, we can reformulate adjacency operator as $$Af(v) = \sum_{e\in E(v)}f(e(v)) $$
- Then, interpreting definitions of pullback and adjacency operator in different order $$\begin{aligned} (Af)^{*}(v) &= (Af)(\phi(v)) = \sum_{e\in E_{\phi(v)}}f(e(\phi(v))) \\ (\tilde{A}f^{*})(v) &= \sum_{\tilde{e}\in E_{v}}f^{*}(\tilde{e}(v)) = \sum_{\tilde{e}\in E_{v}}f(\phi(\tilde{e}(v))) \end{aligned}$$
- Since $\phi$ is a covering, incidence is preserved, thus $e(\phi(v)) = \phi(\tilde{e}(v))$ i.e. vertices connected to $\phi(v)$ by $e$ in $Y$, is the same as the map of vertices connected to $v$ by $e$ in $X$.

>**Lemma 2.14**
>$X$ covers $Y$. Then every eigenvalue of $Y$ is an eigenvalue of $X$. 

Proof 
- Let $A, \tilde{A}$ be the adjacency operators of $Y, X$, respectively.
- Let $\mu$ be an eigenvalue of $A$ with corresponding eigenfunction $f$. Then$$ \tilde{A}f^{*} = (Af)^{*} = (\mu f)^{*} = \mu f^{*}$$

>**Proposition 2.15**
>$d$-regular graphs $X$ and $Y$, and $X$ covers $Y$. Then $\lambda_{1}(X) \ge \lambda_{1}(Y)$.

Proof
- $\lambda_{0} = d$ for both $X$ and $Y$. 
- Possibly $\lambda_{1}(X)$ is not an eigenvalue of $Y$.

Remark
1) Idea: the quality of a graph is no better than that of any graph it covers. The covered graph is generally smaller, and it is more difficult to maintain the quality when graph becomes larger. 
2) Another proof for Quotients Non-expansion Principle
   - Fact: $Cay(G_{n}, \Gamma_{n})$ covers $Cay(G_{n} /H_{n} , \overline{\Gamma_{n}}) = Cay(Q_{n}, \overline{\Gamma_{n}})$.
   - Assumption: $\{Q_{n}\}$ not expander. 
   - Then $\{d-\lambda_{1}(Q_{n})\} \rightarrow 0$ for any $d$. (for any possible $\Gamma_{n}$, same for below)
   - Then $\{d-\lambda_{1}(G_{n})\} \rightarrow 0$ for any $d$, since $\lambda_{1}(Q_{n}) \le \lambda_{1}(G_{n})$ for any $n$.
   - Then $\{G_{n}\}$ not expander. 



# 2. Subgroups and Schreier Generators 

> **Definition 2.16 Set of Transversals**
> 1) Finite group $G$, $H \le G$. Let $T \subset G$ s.t. $T$ contains exactly one element from each right coset of $H$ in $G$. Then $T$ is a set of transversals for $H$ in $G$.
> 2) Denote $\overline{x}$ the unique element of $T$ s.t. $Hx = H\overline{x}$. 

> **Lemma 2.17**
> Let $G$, $H$, and $T$ be defined as above. Then:
> 1) For all $x \in G$, there exists a unique $h \in H$ s.t. $x = h\overline{x}$.
> 2) For all $h \in H$, $a \in G$, we have $\overline{ha} = \overline{a}$.
> 3) For all $a, b \in G$, we have $\overline{\overline{a}b} = \overline{ab}$.
> 4) For all $t \in T$, we have $\overline{t} = t$.

Proof: 
1) $h = x(\overline{x})^{-1}$, and there is only one $\overline{x}$ corresponding $x$, hence $h$ is unique. 
2) $H\overline{ha} = Hha = Ha = H\overline{a}$, second equality by definition of right coset. 
3) $\overline{a} = h^{-1}a$ for some $h \in H$, thus $\overline{a} = h'a$ for some $h' \in H$, since $H \le G$. Then, $\overline{\overline{a}b} = \overline{h'ab} = \overline{ab}$, last equality by (2).
4) $\overline{t} = ht$ for some $h \in H$ (same as (3)), thus $\overline{t} \in Ht$. Since $t \in Ht$, $\overline{t} = t$ since $T$ contains only one element from each right coset of $H$.

Remark: 
1) Following (1), we can decompose $G$ with $H$ and $T$, s.t. every $g \in G$, $g = ht$ for some $h \in H$ and $t \in T$. Also, $t = \overline{g}$, $h = g(\overline{g})^{-1}$.
2) For $t, \, \gamma \in G$, we introduce the notation $$\widehat{(t,\gamma)} = t\gamma(\overline{t\gamma})^{-1} $$Following (1), exists a unique $h \in H$ s.t. $t\gamma = h\overline{t\gamma}$. Notice that $\widehat{(t,\gamma)} = t\gamma(\overline{t\gamma})^{-1}=h$, hence $\widehat{(t,\gamma)}$ is an element of $H$, and $t\gamma = \widehat{(t,\gamma)}\overline{t\gamma}$ is the unique expression of $t\gamma$ in the form of $h\overline{t\gamma}$. 
3) Rigorously speaking we need redefine concepts like function, bijection, "set" multiplication etc. since we are dealing with multiset. I omit these details. Anyway the guiding principle is to pretend it is still a set and count the multiplicity (essentially not that different).

>**Definition 2.18 Schreier Generators**
>Let $G$, $H$, $T$, be defined as in Def 2.16. $\Gamma \in G$, define $$\hat{\Gamma} = \{\widehat{(t,\gamma)} \, \vert \, (t,\gamma) \in T \times \Gamma \} $$
>1) $\hat{\Gamma}$ is the set of Schreier generators for $H$ in $G$ with respect to $\Gamma$. 
>2) $|\hat{\Gamma}| = [G:H] \cdot |\Gamma|$, where $[G:H]$ means the number of right cosets generated by $H$, and clearly $|T| = [G:H]$

> **Lemma 2.19**
> $G, H, T$ as Def 2.16. 
> 1) If $\Gamma \in G$, then $\hat{\Gamma} \in H$. 
> 2) If $\Gamma$ symmetric in $G$, then $\hat{\Gamma}$ symmetric in H. 

Proof: 
1) Let $t \in T, \gamma \in \Gamma, x=t\gamma$.
   - By Lemma 2.17, $x=h\overline{x}$ for a unique $h\in H$, so $\widehat{(t,\gamma)} = h$.
2) Define map $\phi: T \times \Gamma \rightarrow T \times \Gamma$, by $\phi(t,\gamma) = (\overline{t\gamma},\gamma^{-1})$. 
   - Last equality by Lemma 2.17, we have $$(\phi \circ \phi)(t,\gamma) = \phi(\overline{t\gamma},\gamma^{-1}) = (\overline{\overline{t\gamma}\gamma^{-1}},\gamma) = (t,\gamma) $$ Inverse of $\phi$ is just itself, bijective. 
   - Again by Lemma 2.17 $$ \left( \widehat{(t,\gamma)} \right)^{-1} = \overline{t\gamma}\gamma^{-1}t^{-1} = \overline{t\gamma}\gamma^{-1}(\overline{\overline{t\gamma}\gamma^{-1}})^{-1} = \widehat{\phi(t,\gamma)} $$ Because $\phi$ is bijective, $\left( \widehat{(t,\gamma)} \right)^{-1}$ has same multiplicity in $\hat{\Gamma}$ as $\widehat{(t,\gamma)}$. 

Remark: 
If $Cay(G, \Gamma)$ is an undirected graph, then $Cay(H, \hat{\Gamma})$ is also an undirected graph. Following Chapter 1, we can consider an undirected graph as two (overlapping) directed graph. 

Example:
![[Screenshot 2024-09-11 at 21.02.16.png]]
- $G = D_{3} = \{1, r, r^{2}, s, sr, sr^{2} \}$, $H = \{ 1, r, r^{2} \}$, $\Gamma = \{ s, sr \}$.
- Right cosets of $H$ in $G$ are $H$ and $Hs = \{s, sr, sr^{2} \}$. 
- Let $T = \{1,s\}$, and $T$ is indeed a set of transversals for $H$ in $G$. 
- By collapsing edges horizontally, we get from right to left (e.g. $sr$ collapsing to $r^{2}$). The collapsed edge (two directed edge) becomes two (directed) loops. 
- This collapsing can be described by a surjective map, $G \rightarrow H$, by $ht \mapsto h$.
- Denote by $e(g,\gamma)$ each directed edge in $Cay(G, \Gamma)$ from $g$ to $g\gamma$.

>**Lemma 2.20**
>Map \[set of directed edges in $Cay(G,\Gamma)$] $\rightarrow$ \[set of directed edges in $Cay(H, \hat{\Gamma})$], by $$e(ht,\gamma) \rightarrow e(h,\widehat{(t,\gamma)})$$ is bijective. 

Proof
- Surjective is trivial. 
- Injective: same as Lemma 2.8 (how about a formal proof?)

>**Lemma 2.21**
>$G, H, T$ as Def 2.16. $\Gamma$ symmetric in $G$. Then $$ h(Cay(G,\Gamma)) \le \frac{h(Cay(H,\hat{\Gamma}))}{[G:H]}$$

Remark:
The actual result used in Proposition 2.24 is $h(Cay(G,\Gamma)) \le h(Cay(H,\hat{\Gamma}))$, which is an obvious implication of Lemma 2.21.

Proof:
- Let $S \subset H$, s.t. $|S| \le \frac{1}{2}|H|$ and $\frac{|\partial S|}{|S|} = h(Cay(H,\hat{\Gamma}))$.
- Let $\tilde{S} = \{ht \, \vert \, h \in S, \, t \in T \}$, so $|\tilde{S}| = |S| \cdot |T|$, and $|T| = [G:H]$
- Then $$|\tilde{S}| = |S|\cdot|T| \le \frac{1}{2}|H|\cdot|T| = \frac{1}{2}|G|$$
- Note: $$\begin{aligned} g\gamma \in \tilde{S} &\Longleftrightarrow (ht)\gamma \in \tilde{S} \\ &\Longleftrightarrow ht\gamma(\overline{ht\gamma})^{-1} \in S \\ &\Longleftrightarrow ht\gamma(\overline{t\gamma})^{-1} \in S \\ &\Longleftrightarrow h\widehat{(t,\gamma)} \in S \end{aligned} $$First line: decomposition of $g$ in $G$. Second line: $g\gamma = h't'$ since $g\gamma \in G$, and $h' = (g\gamma)(\overline{g\gamma})^{-1}$, which lies in $S$ by definition of $\tilde{S}$. Third line: by (4) of Lemma 2.17. Last line: definition. 
- Then: $$\begin{aligned} |\partial\tilde{S}| &= |\{e(g,\gamma) \, : \, g\in \tilde{S}, \gamma \in \Gamma, g\gamma \notin \tilde{S} \}| \\ &= |\{ e(ht,\gamma) \, : \, h \in S, t\in T, \gamma \in \Gamma, ht\gamma \notin \tilde{S} \}| \\ &= |\{ e(h,\widehat{(t,\gamma)}) \, : \, h \in S, t\in T, \gamma \in \Gamma, ht\gamma\notin \tilde{S} \}| \\ &= |\{ e(h,\widehat{(t,\gamma)}) \, : \, h \in S, t\in T, \gamma \in \Gamma, h\widehat{(t,\gamma)} \notin S \} \\ &= |\partial S| \end{aligned}$$ First line is the definition of boundary set in $Cay(G,\Gamma)$, edges which has one endpoint not in $\tilde{S}$, second line decomposes g, third line by the bijection map between $e(ht,\gamma)$ and $e(h,\widehat{(t,\gamma)})$, fourth line by last point, last line is again definition of boundary in $Cay(H,\tilde{\Gamma})$.
- Thus, $$h(Cay(G,\Gamma)) \le \frac{|\partial \tilde{S}|}{|\tilde{S}| } = \frac{|\partial S|}{|S|\cdot[G:H]} = \frac{h(Cay(H,\tilde{\Gamma}))}{[G:H]} $$

> **Corollary 2.22 Schreier Subgroup Lemma** 
> If $\Gamma$ generates $G$, then $\hat{\Gamma}$ generates $H$. 

Proof: 
- $\Gamma$ generates $G$
- then $Cay(G,\Gamma)$ is connected (Prop 1.9)
- then $h(Cay(G,\Gamma)) >0$, (properties of isoperimetric constant)
- then $h(Cay(H,\hat{\Gamma})) >0$, (Lemma 2.21)
- then $Cay(H,\hat{\Gamma})$ is connected (properties of isoperimetric constant)
- then $\hat{\Gamma}$ generates $H$.

Remark: 
The converse is false. Counterexample

> **Definition 2.23 Bounded-index sequence of subgroups**
> $\{G_{n}\}$ and $\{H_{n} \}$ are sequences of finite groups. We say that $\{G_{n}\}$ admits $\{H_{n} \}$ as a bounded-index sequence of subgroups, if $H_{n} \le G_{n}$ for all $n$, and the sequence $\{[G_{n}:H_{n}] \}$ is bounded. 

> **Proposition 2.24 Subgroups Nonexpansion Principle**
> $\{G_{n} \}$ be a sequence of finite groups. Suppose that $\{G_{n}\}$ admits $\{H_{n} \}$ as a bounded-index sequence of subgroups. If $\{H_{n} \}$ does not yield an expander family, so does $\{G_{n}\}$.

Proof: 
- Suppose not true. Then, there exists a positive $d$ and $\Gamma_{n}$ symmetric in $G_{n}$ with $|\Gamma_{n}| = d$ for all n, s.t. $\{Cay(G_{n}, \Gamma_{n}) \}$ is an expander family, and $h(Cay(G_{n},\Gamma_{n})) \ge \epsilon$ for some $\epsilon >0$. 
- Since $\{[G_{n}:H_{n}] \}$ is bounded, exist $M$ s.t. $[G_{n}:H_{n}] \le M$ for all n. 
- Let $T_{n}$ be a set of transversals for $H_{n}$ in $G_{n}$ for each n.
- Let $$\Lambda_{n} = \widehat{\Gamma_{n}} \cup \{(M - [G_{n}:H_{n}])d \cdot e_{n} \}$$ where $\cdot$ means the set contains $(M - [G_{n}:H_{n}])d$ copies of identity $e_{n}$ of group $G_{n}$. So $\Lambda_{n}$ is essentially the set of Schreier generators and the union is just modifying multiplicity of $e_{n}$ s.t. $|\Lambda_{n}| = [G_{n}:H_{n}]\cdot |\Gamma_{n}| + (M-[G_{n}:H_{n}])d =M\cdot d$, since $|\Gamma_{n}| = d$.
- After modification: 
   - $Cay(H_{n},\Lambda_{n})$ has same vertex set as $Cay(H_{n},\widehat{\Gamma_{n}})$, and their edge sets are the same expect for additional loops in $Cay(H_{n},\Lambda_{n})$. So they have the same isoperimetric constant. 
   - $\{Cay(H_{n},\Lambda_{n})\}$ is now a sequence of $Md$-regular graphs, since $|\Lambda_{n}|$ has a fixed size. We don't have this for $|\widehat{\Gamma_{n}}|$, so $\{Cay(H_{n},\widehat{\Gamma_{n}})\}$ do not fulfil the precondition of expander family.
- Then by Lemma 2.21 $$h(Cay(H_{n},\Lambda_{n})) = h(Cay(H_{n},\widehat{\Gamma_{n}})) \ge h((Cay(G_{n},\Gamma_{n}))) \ge \epsilon$$ for all $n$. Thus $\{Cay(H_{n}, \Lambda_{n}) \}$ is an expander family

 >**Lemma 2.25**
 >$G, H, T$ as Def 2.16. $\Gamma$ symmetric in $G$. Then $$\lambda_{1}(Cay(G,\Gamma))\ge \frac{\lambda_{1}(Cay(H,\hat{\Gamma}))}{[G:H]}$$
 
 Proof
 - $A_{G}, A_{H}$ are adjacency operators of $Cay(G,\Gamma), Cay(H, \hat{\Gamma})$, respectively. 
 - $\lambda_{H}=\lambda_{1}(Cay(H,\hat{\Gamma}))$, $f\in L^{2}_{0}(H,\mathbb{R})$, and is an eigenfunction of $\lambda_{H}$. Such an eigenfunction must exist, since $f_{0}$ as a constant 1 function must be an orthogonal eigenfunction (corresponding to the "constant" part of an orthogonal eigen basis), thus every other orthogonal eigenfunction must fall in $f\in L^{2}_{0}(H,\mathbb{R})$, since the definition of this space only requires functions to be orthogonal with $f_{0}$. 
 - Define $\tilde{f} \in L^{2}(G)$ by $\tilde{f}(ht) = f(h)$ for all $h \in H, t\in T$. Due to the decomposition of every $g \in G$, $\tilde{f}$ is well-defined.
 - Note $\tilde{f} \in L^{2}_{0}(G,\mathbb{R})$, since $$\sum_{g\in G}\tilde{f}(g) = \sum_{t\in T}\sum{h \in H}\tilde{f}(ht) = \sum_{t\in T}\sum_{h \in H}f(h) = 0$$
 - By Rayleigh-Ritz $$\lambda_{1}(Cay(G,\Gamma)) \ge \frac{\langle  A_{G}\tilde{f} ,\tilde{f} \rangle}{\langle \tilde{f},\tilde{f} \rangle }$$
 - Denominator: $$ \begin{aligned} \langle  \tilde{f} , \tilde{f} \rangle &= \sum_{g\in G}\tilde{f}(g)^2 \\ &= \sum_{t\in T}\sum_{h\in H}\tilde{f}(ht)^{2} \\ &= \sum_{t\in T}\sum_{h\in H}f(h)^2 \\ &= \sum_{t\in T} \langle  f , f \rangle \\ &= [G:H]\langle  f , f \rangle \end{aligned}$$ All by definitions.
 - Consider $ht\gamma$ as an element of $G$, then $ht\gamma = h't'$, and $h' = (ht\gamma)(\overline{ht\gamma})^{-1}, \, \tilde{f}(h't')=f(h')$
 - Thus, $\tilde{f}(ht\gamma)=f(ht\gamma(\overline{ht\gamma})^{-1})=f(h\widehat{(t,\gamma)})$ (last equation same as proof of Lemma 2.21)
 - Numerator:   $$\begin{aligned} \langle A_{G} \tilde{f} , \tilde{f} \rangle &= \sum_{g\in G}A_{G}\tilde{f}(g)\cdot \tilde{f}(g) \\ &= \sum_{g\in G}\sum_{\gamma \in \Gamma}\tilde{f}(g\gamma)\cdot \tilde{f}(g) \\ &= \sum_{h\in H}\sum_{t\in T}\sum_{\gamma \in \Gamma}\tilde{f}(ht\gamma)\cdot \tilde{f}(ht) \\ &= \sum_{h\in H}\sum_{t\in T}\sum_{\gamma \in \Gamma}f(h\widehat{(t,\gamma)})\cdot f(h) \\ &= \sum_{h\in H}(A_{H}f)(h)\cdot \overline{f(h)} \\ &= \langle A_{H} f , f \rangle \\ &= \lambda_{H} \langle f , f \rangle \end{aligned} $$ Note $f$ is a real function, thus $f = \overline{f}$. Else by definition.
 - Hence $$\lambda_{1}(Cay(G,\Gamma)) \ge \frac{\lambda_{H}\langle f , f \rangle}{[G:H]\langle f , f \rangle} = \frac{\lambda_{1}(Cay(H,\hat{\Gamma}))}{[G:H]}$$

Remark: 
1) Another common presentation of Lemma 2.25 is with normalised adjacency operators. Normalised = largest eigenvalue is 1. In this way, the adjacency matrix is related to a random walk on X, with each entry being a transition probability.
2) Another proof for Subgroups Non-expansion Principle: 
   - (handwritten proof)
 
