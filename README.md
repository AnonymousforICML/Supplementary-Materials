# Algorithm Comparison Documentation

## Non-gradient Tracking Algorithms

In our experiments, we have included non-gradient tracking algorithms for comparison purposes, specifically the DC-DOGD algorithm [1].

### DC-DOGD Algorithm

DC-DOGD (Distributed Compressed Distributed Online Gradient Descent) is an algorithm that leverages communication compression mechanisms and One-point Bandit Feedback. This algorithm was originally developed for static regret optimization scenarios.

**Key features of DC-DOGD:**
- Uses communication compression to reduce bandwidth requirements
- Employs One-point Bandit Feedback mechanism
- Originally evaluated using static regret as the performance metric

### Our Experimental Setting

In our experiments, we assess the performance of these algorithms using dynamic regret instead of static regret. This provides a more challenging evaluation framework as dynamic regret measures performance against the sequence of best actions in hindsight, rather than against a single fixed action.

## References

[1] Tu, Zhipeng, et al. "Distributed online convex optimization with compressed communication." Advances in Neural Information Processing Systems 35 (2022): 34492-34504.
