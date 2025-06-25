# Monte Carlo Methods

## Monte Carlo Basic
Estimate the value function $$V(s)$$ or action-value function $$Q(s,a)$$ based on sampled episodes.

Requirement: Episodes must terminate (i.e., they must reach a terminal state eventually).

Types:
- First-visit MC: Averages returns only the first time a state (or state-action pair) is visited in an episode.
- Every-visit MC: Averages returns every time a state (or state-action pair) is visited.

### Pseudocode
```
Initialize:
    V(s) arbitrarily for all s ∈ S
    Returns(s) = [] for all s ∈ S

For each episode:
    Generate an episode following policy π: 
        Episode = [(s0, a0, r1), (s1, a1, r2), ..., (sT, aT, rT+1)]
    G = 0
    VisitedStates = set()

    For t = T down to 0:
        G = γ * G + r_{t+1}
        If state s_t not in VisitedStates:
            Add s_t to VisitedStates
            Append G to Returns(s_t)
            V(s_t) = average(Returns(s_t))

```
