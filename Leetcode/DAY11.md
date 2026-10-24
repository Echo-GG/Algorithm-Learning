## Final Prices With a Special Discount in a Shop
Given an array of integers temperatures represents the daily temperatures, return an array answer such that answer[i] is the number of days you have to wait after the ith day to get a warmer temperature. If there is no future day for which this is possible, keep answer[i] == 0 instead.

```C++
	
class Solution {
	public:
	vector<int> dailyTemperatures(vector<int>& temperatures) {
		stack<int> st;
		int n = temperatures.size();
		vector<int> res(n, 0);
		
		for (int i = 0; i < n; i++) {
			while (!st.empty() &&
			temperatures[i] > temperatures[st.top()]) {
				int j = st.top();
				st.pop();
				
				res[j] = i - j;
			}
			
			st.push(i);
		}
		
		return res;
	}
};
```
