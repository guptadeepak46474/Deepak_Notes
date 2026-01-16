# Imp Coding Concepts

## 1. Find the largest rectangle consisting only of 1s in a binary matrix.

**The most commonly used method is:**
```
Convert each row into a histogram and apply “Largest Rectangle in Histogram” using a stack
```

**One-Line Interview Explanation**
```
“For each row, I treat it as the base of a histogram of consecutive 1s and compute the largest rectangle using a monotonic stack.”
```

Original heights: [2, 1, 1, 1, 2]
After sentinel:   [2, 1, 1, 1, 2, 0]
Indexes:           0  1  2  3  4  5

**Key Rules to Remember:**
- Stack stores indices
- Stack is monotonically increasing
- When a smaller height appears, we:
  - Pop
  - Calculate area using the popped height

```cpp
int largestRectangleArea(vector<int>& heights) {
    stack<int> st;
    int maxArea = 0;
    heights.push_back(0);  // sentinel

    for (int i = 0; i < heights.size(); i++) {
        while (!st.empty() && heights[st.top()] > heights[i]) {
            int h = heights[st.top()];
            st.pop();
            int w = st.empty() ? i : i - st.top() - 1;
            maxArea = max(maxArea, h * w);
        }
        st.push(i);
    }
    return maxArea;
}

int maximalRectangle(vector<vector<int>>& matrix) {
    if (matrix.empty()) return 0;

    int n = matrix[0].size();
    vector<int> heights(n, 0);
    int ans = 0;

    for (auto& row : matrix) {
        for (int j = 0; j < n; j++) {
            heights[j] = (row[j] == 1) ? heights[j] + 1 : 0;
        }
        ans = max(ans, largestRectangleArea(heights));
    }
    return ans;
}
```

## 2. 