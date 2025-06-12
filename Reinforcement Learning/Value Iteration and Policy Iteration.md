# Value Iteration and Policy Iteration

## Value iteration algorithm
**Goal**: Compute the optimal value function $V^\*(s)$ and derive the optimal policy $\pi^\*(s)$ in a Markov Decision Process (MDP).

### Given:
- State space $S$
- Action space $A$
- Transition probability $P(s', r \mid s, a)$
- Reward function $r(s, a, s')$
- Discount factor $\gamma \in [0, 1)$

---

### Core Idea:
Use the **Bellman Optimality Equation** iteratively to approximate $V^*(s)$:

$$
V_{k+1}(s) = \max_a \sum_{s', r} P(s', r \mid s, a) \left[ r + \gamma V_k(s') \right]
$$

---

### Value Iteration Pseudocode

```pseudo
Initialize V(s) arbitrarily (e.g., V(s) = 0 for all s)
Repeat:
    Δ = 0
    For each state s ∈ S:
        v = V(s)
        V(s) = max_a ∑_{s', r} P(s', r | s, a) [r + γ * V(s')]
        Δ = max(Δ, |v - V(s)|)
    Until Δ < θ (a small threshold)
```

## Policy Iteration Pseudocode

**Goal**: Find the optimal policy $\pi^\*$ and its corresponding value function $V^{\pi^\*}$ for a Markov Decision Process (MDP).

---

### Given:
- State space $S$
- Action space $A$
- Transition probabilities $P(s', r \mid s, a)$
- Reward function $r(s, a, s')$
- Discount factor $\gamma \in [0, 1)$

---

###  Key Idea:

Alternate between two steps:

1. **Policy Evaluation** – compute $V^\pi$ for the current policy $\pi$
2. **Policy Improvement** – update $\pi$ by acting greedily with respect to $V^\pi$

---

###  Bellman Expectation Equations

#### Policy Evaluation:

Solve for $V^\pi(s)$:

$$
V^\pi(s) = \sum_{a} \pi(a \mid s) \sum_{s', r} P(s', r \mid s, a) \left[ r + \gamma V^\pi(s') \right]
$$

#### Policy Improvement:

Update the policy:

$$
\pi_{\text{new}}(s) = \arg\max_{a} \sum_{s', r} P(s', r \mid s, a) \left[ r + \gamma V^\pi(s') \right]
$$

---

###  Policy Iteration Pseudocode

```pseudo
Initialize arbitrary policy π(s)
Repeat:
    1. Policy Evaluation:
        - Compute V^π(s) for all s (e.g., iterative or matrix method)
    2. Policy Improvement:
        - For each state s:
            π_new(s) = argmax_a ∑_{s', r} P(s', r | s, a) [r + γ * V^π(s')]
    Until π_new == π (policy is stable)
```

## Major Differences: Value Iteration vs. Policy Iteration

| Aspect               | Value Iteration                                      | Policy Iteration                                      |
|----------------------|------------------------------------------------------|--------------------------------------------------------|
| **Approach**         | Iteratively updates value estimates directly         | Alternates between policy evaluation and improvement   |
| **Main Step**        | Bellman *optimality* update                          | Bellman *expectation* update followed by improvement   |
| **Policy Handling**  | Extract policy *after* convergence                   | Maintains and improves policy in each iteration        |
| **Efficiency**       | Faster per iteration, but may require more iterations | Slower per iteration (policy eval), fewer iterations  |
| **Convergence Type** | Approximates optimal value function $V^\*$           |    Converges to optimal policy $\pi^\*$ explicitly     |
| **Output**           | $V^\*$, then derive $\pi^\*$                         |       $\pi^\*$ and $V^{\pi^\*}$                        |
| **Use Case**         | When fast approximate solutions are acceptable       | When exact policy is required                         |
