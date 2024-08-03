# All of Statistics: *A concise Course in Statistical Inference* by *Larry Wasserman*

## Chapter 1: Probability

### 1.1 Introduction
Probability is a mathematical language for quantifying uncertainty.

### 1.2 Sample Spaces and Events

- $\Omega$: sample space
- points $\omega$ in $\Omega$: sample outcomes, realizations, or elements
- $A$: event, subset of $\Omega$
- $A^c$: complement of $A$ (not $A$)
- $A \cup B$: union ($A$ or $B$)
- $A \cap B$ or $AB$: intersection ($A$ and $B$)
- $A - B$: set difference ($\omega$ in $A$ but not in $B$)
- $A \subset B$: set inclusion
- $\emptyset$: null event (always false)
- $\Omega$: true event (always true)

> Examples: 
>
> If we toss a coin twice, then $\Omega = \{HH, HT, TH, TT\}$. The events that the first toss is head is $A = \{HH, HT\}$.
>
> There is usually no harm in taking the sample space to be larger than needed. 

### 1.3 Probability

#### Probability distribution

**Definition**: A function $\mathbb P$ that *assigns a real number* $\mathbb P (A)$ *to each event A is a* **probability distribution** *or a* **probability measure** *if it satisfies the following three axioms*:
1. Axiom 1: $\mathbb P (A) \ge 0$ for every $A$
2. Axiom 2: $\mathbb P (\Omega) = 1$
3. Axiom 3: *If* $A_1, A_2, ...$ *are disjoint then*
$$\mathbb P\left(\bigcup_{i=1}^\infty A_i\right) = \lim_{i=1}^\infty \mathbb P (A_i)$$

#### The two interpretations of $\mathbb P(A)$
1. **Frequencies**: $\mathbb P(A)$ is the long run proportion of times that $A$ is true in repetitions.
2. **Degrees of beliefs**: $\mathbb P(A)$ measures an observer's strength of belief that $A$ is true.

#### The two school of inference:
1. **Frequencies** -> **the frequentist**
2. **Degrees of beliefs** -> **the Bayesian school**

#### The many properties of $\mathbb P$ derived from the three Axioms.

$$\mathbb P(\emptyset) = 0$$
$$A \subset B \implies \mathbb P(A) \le \mathbb P(B)$$
$$0 \le \mathbb P(A) \le 1$$
$$\mathbb P(A^c) = 1 - \mathbb P(A)$$
$$A \bigcap B = \emptyset \implies \mathbb P(A \bigcup B) = \mathbb P(A) + \mathbb P(B)$$

#### Lemma 1.6

*For any events $A$ and $B$,*
$$ \mathbb P(A \bigcup B) = \mathbb P(A) + \mathbb P(B) - \mathbb P(AB)$$

#### Theorem 1.8: Continuity of Probabilities

*If $A_n \to A$ then*
$$ \mathbb P(A_n) \to \mathbb P(A)$$
*as $n \to \infty$*.

### 1.4 Probability on Finite Sample Spaces

#### Uniform probability distribution
If $\Omega$ is finite and if each outcome is equally likely, then
$$\mathbb P(A) = {|A| \over |\Omega|}$$
$|A|$ denotes the number  of elements in $A$.

#### $n$ choose $k$
- the number of distinct ways of choosing $k$ objects from $n$.
$${n \choose k} = { n! \over k!(n-k)!} $$

$${n \choose 0} = {n \choose n} $$
$${n \choose k} = {n \choose {n-k}}$$

### 1.5 Independent Events


### 1.6 Conditional Probability


### 1.7 Bayes' Theorem


