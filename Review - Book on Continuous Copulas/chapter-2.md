# Chapter 2

- **Fréchet-Hoeffding bounds:** For any d-dimensional copula C, $W(u) \leq C(u) \leq M(u)$, where $u \in [0, 1]^d$.
    - For instance in case of $U \sim U(0, 1)$, where $(U, 1 - U) \sim W$ (countermonotone copula) and $(U, ..., U) \sim M$ (comonotone copula), it is really easy to see.
    
- **Sklar's Theorem:** (explains why copula determine dependence between the components of a random vector) For any d dimensional df H with univariate margins, there exists a d-dimensional copula C such that $H(x) = C(F_1(x_1), ..., F_d(x_d))$, $x \in \mathbb{R}^d$, and this uniquely defined copula is given by $C(u) = H(F^{-1}_1(u_1), ... ,F^{-1}_d(u_d))$.
    - $h(x) = c(F_1(x_1), ..., F_d(x_d)) \prod_{j=1}^d f_j(x_j)$
    - copulas are invariant to monotonous transformations

- **Survival Copula**: Survival function $\bar F = 1 - F$. Let C be a copula & $U \sim C$, then $1-U \sim \bar C$, where C is the survival copula defined by the relationship $\bar c(u) = c(1-u_1, ..., 1-u_d)$.

- **Measures of Association**: 
    - **Pearson's Linear Correlation:** covariance divided by product of square root of variances.
        - between -1 and 1 & equal to 1 only if variables are linear combination of each other
        - 0 when linearly independent & invariant under strictly increasing linear transformations
        - **Demerits of $\rho$:** 
            - doesn't exist at times for non-linear terms
            - margins & $\rho$ don't uniquely determine joint distribution, and thus $\rho$ cannot be expressed in terms of unique underlying copula
            - = 0 doesn't imply that they are independent
            - it is invariant ONLY under strictly increasing LINEAR transformations.
    - **Rank Correlation Measures:** by depending only on underlying copula, they overcome several limitations. (often called measures of concordance)
        - **Spearman's Rho:** = $Cor(F_1(X_1), F_2(X_2))$ = $12\int_{[0,1]^2} C(u)du - 3$ = $12\int_{[0,1]^2} u_1u_2dC(u) - 3$
            - **Estimation:** We first estimate the marginal dfs $F_1$ & $F_2$, which is done through a sample of bivariate ranks, where $R_{ij}$ is the rank of $X_{ij}$ among $X_{1j}, ..., X_{nj}$ and then compute correlations. Thus, $\rho_S$ = correlation of ranks.
        - **Kendall's Tau:** = $\mathbb{E}(sign((X_1-X_1^{'})(X_2-X_2^{'})))$, where $(X_1^{'}, X_2^{'})$ are independent copies of $(X_1, X_2)$.
            - = $\mathbb{P}((X_1-X_1^{'})(X_2-X_2^{'})>0) - \mathbb{P}((X_1-X_1^{'})(X_2-X_2^{'})<0)$ = prob(concordance) - prob(discordance)
            - = $4\int_{[0,1]^2} C(u)dC(u) - 1$
            - **Estimation:** using sample analogs, $\tau_n = \frac{4p_n}{n(n-1)} - 1$, where $p_n$ is the number of concordant pairs. 
        - They follow the property of being -1 and 1 at lower and upper Fréchet bounds respectively, always exist, and are invariant under strictly increasing transformations.

    - **Tail Dependence Coefficients:** are limits of conditional probabilities of quantile exceedances. For a bivariate random vector with continuous margins and copula C:
        - Here, $\lambda_l = \lim_{q \text{ tends to } 0}\frac{C(q,q)}{q}$
        - Here, $\lambda_u = \lim_{q \text{ tends to } 1}\frac{1-2q+C(q,q)}{1-q}$
    
- **Rosenblatt Transform & Conditional Sampling:** for conditional copulas. Transformation $R_C$ transforms a vector $\bold{u} \in (0,1)^d$ into a vector $\bold{u}' \in (0,1)^d$ such that: $u_1' = u_1, u_2' = C_{2|1}(u_2|u_1), ..., u_d' = C_{d|1,...,d-1}(u_d|u_1,...,u_{d-1})$.

- **Note:** towards the end of this chapter, there are some quasi-random random number generation methods that are used for variance reduction (i.e. _Latin hypercube sampling_), which might come in handy later.