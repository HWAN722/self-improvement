# Bellman Equation

## Formula
$$
V^\pi(s) = \sum_{a} \pi(a|s) \sum_{s', r} P(s', r \mid s, a) \left[ r + \gamma V^\pi(s') \right]
$$

- $s$: current state  
- $a$: action taken in state $s$  
- $s'$: next state after taking action $a$ in $s$  
- $r$: reward received for transition from $s$ to $s'$ via $a$  
- $\pi(a \mid s)$: probability of taking action $a$ in state $s$ under policy $\pi$  
- $P(s', r \mid s, a)$: transition probability of reaching $s'$ and receiving $r$ from $s$ using $a$  
- $\gamma$: discount factor, $0 \leq \gamma \leq 1$  , the smaller $\gamma$ is, the model is more short-sighted.
- $V^\pi(s)$: value of state $s$ under policy $\pi$

$$
Q^\pi(s, a) = \sum_{s', r} P(s', r \mid s, a) \left[ r + \gamma \sum_{a'} \pi(a' \mid s') Q^\pi(s', a') \right]
$$
- $Q^\pi(s, a)$: value of taking action $a$ in state $s$ under policy $\pi$

## Relationship
$$
V^\pi(s) = \sum_{a} \pi(a|s) Q^\pi(s, a)
$$

## Bellman Optimality Equation(BOE)
$$
V(s) = \max_{a} \sum_{s', r} P(s', r \mid s, a) \left[ r + \gamma V(s') \right]
$$

## Contraction Mapping Theorem
Let $(X, d)$ be a **complete metric space**, and let $T: X \rightarrow X$ be a **contraction mapping**, i.e., there exists a constant $0 \leq \alpha < 1$ such that for all $x, y \in X$:

$$
d(T(x), T(y)) \leq \alpha \cdot d(x, y)
$$

Then:

1. $T$ has a **unique fixed point** $x^* \in X$ such that $T(x^\*) = x^\*$  
2. For any starting point $x_0 \in X$, the sequence $x_{k+1} = T(x_k)$ **converges to** $x^*$  
3. The rate of convergence is **geometric**, determined by $\alpha$
