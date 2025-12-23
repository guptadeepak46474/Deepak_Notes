

## Minimum (Maximum) Path to Reach a Target

Generate problem statement for this pattern

**Statement**
```
Given a target find minimum (maximum) cost / path / sum to reach the target.
```

**Approach**
```
Choose minimum (maximum) path among all possible paths before the current state, then add value for the current state.
```
```
routes[i] = min(routes[i-1], routes[i-2], ... , routes[i-k]) + cost[i]
```


### Problems
746. Min Cost Climbing Stairs
```
  int take_one = cost[i] + dp(i+1, cost, memo);
  int take_two = i+1 < cost.size() ? cost[i+1] + dp(i+2, cost, memo) : 0;
  return memo[i] = min(take_one, take_two);
```    




## Distinct Ways



## Merging Intervals

This project implements **Federated Learning** using *PyTorch*.

## 5️⃣ Tables (For results & comparisons)

```md
| Method | Accuracy | Notes |
|------|---------|------|
| FedAvg | 82% | Baseline |
| Ours | 89% | Robust |