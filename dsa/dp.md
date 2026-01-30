# Dynamic Programming Notes

## Linear DP

### 121. Best Time to Buy and Sell Stock
Using concept of peak and valley we can solve this problem without dp also
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int minPrice = INT_MAX; // This tracks our lowest "valley" so far
        int maxProfit = 0;      // This tracks the max difference found
        for (int price : prices) {
            // Update the valley if we find a lower price
            if (price < minPrice) {
                minPrice = price;
            } 
            // If the current price is a "peak" relative to our current "valley",
            // check if the profit is greater than what we've seen before.
            else if (price - minPrice > maxProfit) {
                maxProfit = price - minPrice;
            }
        }
        return maxProfit;
    }
};
```
**Using Dp Approach**
The DP Strategy
We track two states for every single day:
1. `dp[i][0]` (No Stock): The max profit we can have on day `i` if we don't have a stock in hand (either we never bought, or we sold it).
2. `dp[i][1]` (Holding Stock): The max profit (technically negative balance) we can have on day `i` if we do have a stock in hand.

The Transitions:
- To end the day with No Stock, we either:
  - Did nothing (kept the state from yesterday).
  - Sold the stock we were holding yesterday (price is added to our balance).
- To end the day Holding Stock, we either:
  - Did nothing (kept holding).
  - Bought the stock today. Note: Since we are only allowed one transaction, buying a stock means our current profit balance becomes just `-prices[i]`. We do not add it to previous profits.
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int n = prices.size();
        if (n == 0) return 0;

        // dp[i][0] = Max profit at day i with 0 stock
        // dp[i][1] = Max profit at day i with 1 stock
        vector<vector<int>> dp(n, vector<int>(2));

        // Base Case: Day 0
        dp[0][0] = 0;              // We have 0 profit if we don't buy anything
        dp[0][1] = -prices[0];     // If we buy, our 'profit' is negative price

        for (int i = 1; i < n; i++) {
            // Choice 1: Rest (keep yesterday's 0-stock state)
            // Choice 2: Sell (take yesterday's held stock and add today's price)
            dp[i][0] = max(dp[i-1][0], dp[i-1][1] + prices[i]);

            // Choice 1: Rest (keep holding yesterday's stock)
            // Choice 2: Buy (start a new transaction, so balance is -prices[i])
            dp[i][1] = max(dp[i-1][1], -prices[i]);
        }

        // The answer is the max profit with 0 stock at the last day
        return dp[n-1][0];
    }
};
```
TC: O(n), SC: O(n)

### 122. Best Time to Buy and Sell Stock II
using peak valley concept we can also solve this problem
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int max_profit = 0, valley = prices[0], peak = prices[0];
        int i = 0;
        while(i < prices.size()-1) {
            while(i < prices.size()-1 && prices[i] >= prices[i+1])
                i++; // we reached valley
            valley = prices[i];
            while(i < prices.size()-1 && prices[i] <= prices[i+1])
                i++; // we reached peak
            peak = prices[i];
            max_profit += peak - valley;
        }
        return max_profit;
    }
};
```
The DP approach for LeetCode 122 (Infinite Transactions) is almost identical to the single-transaction version, with one critical difference in how we handle the "Buy" state.
The Key Difference
- In Problem 121 (One Transaction): When you buy a stock, you assume your previous profit was 0 (since you haven't traded yet).
  - Formula: `held = max(held, 0 - price)`
- In Problem 122 (Infinite Transactions): When you buy a stock, you use the profit you have already accumulated from previous trades.
  - Formula: `held = max(held, noStock - price)`
The Transitions
1. `dp[i][0]` (No Stock): Same as before. You either rest, or you sell.
   - `dp[i][0] = max(dp[i-1][0], dp[i-1][1] + prices[i])`
2. `dp[i][1]` (Holding): You either keep holding, or you buy new stock using your previous profits.
   - `dp[i][1] = max(dp[i-1][1], dp[i-1][0] - prices[i])`

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int n = prices.size();
        if (n == 0) return 0;

        // dp[i][0] -> Max profit on day i having 0 stock
        // dp[i][1] -> Max profit on day i having 1 stock
        vector<vector<int>> dp(n, vector<int>(2));

        // Base Case
        dp[0][0] = 0;
        dp[0][1] = -prices[0];

        for (int i = 1; i < n; i++) {
            // If we have No Stock: 
            // 1. We had No Stock yesterday (Rest)
            // 2. We had Stock yesterday and Sold it today (+ prices[i])
            dp[i][0] = max(dp[i-1][0], dp[i-1][1] + prices[i]);

            // If we are Holding Stock:
            // 1. We were Holding yesterday (Rest)
            // 2. We had No Stock yesterday and Bought today (- prices[i])
            // NOTICE: We add dp[i-1][0] here! In Prob 121, this was just 0.
            dp[i][1] = max(dp[i-1][1], dp[i-1][0] - prices[i]);
        }

        return dp[n-1][0];
    }
};
```
TC: O(n), SC: O(n)

## Knapsack

## Multi Dimension Dp

## Interval Dp

## Bit Dp

## Digit Dp

## Dp on Trees

## String Dp

## Probability Dp

## Classic Dp

## Dp + Alpha (Tricks/DS)

## Insertion Dp

## Graph Dp

## Memorization Dp

## Binary Lifting

## Math