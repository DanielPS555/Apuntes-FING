**Definition: (Mínimo Local)** Let $f: \mathbb{R}^n \rightarrow \mathbb{R}$ be a real-valued function and $\mathbf{c} \in \mathbb{R}^n$. $f$ has a *local minimum* at $\mathbf{c}$ if $\exists \epsilon > 0$ such that $\forall \mathbf{x} \in B(\mathbf{c}, \epsilon), f(\mathbf{c}) \leq f(\mathbf{x})$.

**Definition (Mínimo Global):** Let $f: \mathbb{R}^n \rightarrow \mathbb{R}$ be a real-valued function and $\mathbf{c} \in \mathbb{R}^n$. $f$ has a *global minimum* at $\mathbf{c}$ if $\forall \mathbf{x} \in \mathbb{R}^n, f(\mathbf{c}) \leq f(\mathbf{x})$.

**Definition:** Let $f: \mathbb{R}^n \rightarrow \mathbb{R}$, $f$ is *differentiable* $\iff \exists df$ una T.L tal que:
$$f(a+h)=f(a)+df(h)+r(h)$$
$$\text{donde }\lim_{h \rightarrow 0}{\frac{r(h)}{||h||}}$$

**Definition:** Let $f: \mathbb{R}^n \rightarrow \mathbb{R}$ be a differentiable scalar-valued function. The *gradient* of $f$, denoted $\nabla f$, is the vector of partial derivatives of $f$ with respect to its variables:

$$
\nabla f = \left( \frac{\partial f}{\partial x_1}, \frac{\partial f}{\partial x_2}, \ldots, \frac{\partial f}{\partial x_n} \right)
$$

where $\frac{\partial f}{\partial x_i}$ represents the partial derivative of $f$ with respect to the variable $x_i$.

### Propiedades geométricas del gradiente
**Prop:**
$$\frac{\partial f}{\partial \vec{v}}(a) = <\nabla f(a),\vec{v} >$$