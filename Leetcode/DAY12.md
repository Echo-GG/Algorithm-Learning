## Largest Rectangle in Histogram
Given an array of integers heights representing the histogram's bar height where the width of each bar is 1, return the area of the largest rectangle in the histogram.

 
```C++
class Solution {
public:
    int largestRectangleArea(vector<int>& heights) {
        int n = heights.size();
        int area = 0;
        stack<int> st;

        for (int i = 0; i < n; i++) {
            while (!st.empty() && heights[st.top()] > heights[i]) {
                int h = heights[st.top()];
                st.pop();

                // 矩形实际覆盖的最右柱子
                int right = i - 1;

                // 矩形实际覆盖的最左柱子
                int left;
                if (st.empty()) {
                    left = 0;
                } else {
                    left = st.top() + 1;
                }

                // 直接计算实际覆盖的柱子数量
                int width = right - left + 1;

                area = max(area, h * width);
            }

            st.push(i);
        }

        // 处理栈中剩余的柱子
        while (!st.empty()) {
            int h = heights[st.top()];
            st.pop();

            int right = n - 1;

            int left;
            if (st.empty()) {
                left = 0;
            } else {
                left = st.top() + 1;
            }

            int width = right - left + 1;

            area = max(area, h * width);
        }

        return area;
    }
};
```
