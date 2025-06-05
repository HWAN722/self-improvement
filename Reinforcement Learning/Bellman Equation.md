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
- $\gamma$: discount factor, $0 \leq \gamma \leq 1$  
- $V^\pi(s)$: value of state $s$ under policy $\pi$

$$
Q^\pi(s, a) = \sum_{s', r} P(s', r \mid s, a) \left[ r + \gamma \sum_{a'} \pi(a' \mid s') Q^\pi(s', a') \right]
$$
- $Q^\pi(s, a)$: value of taking action $a$ in state $s$ under policy $\pi$

## Relationship
$$
V^\pi(s) = \sum_{a} \pi(a|s) Q^\pi(s, a)
$$
