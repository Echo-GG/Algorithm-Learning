## Concatenation of Array

Given an integer array nums of length n, you want to create an array ans of length 2n where ans[i] == nums[i] and ans[i + n] == nums[i] for 0 <= i < n (0-indexed).

Specifically, ans is the concatenation of two nums arrays.

Return the array ans.

```C++
class Solution {
	public:
	vector<int> getConcatenation(vector<int>& nums) {
		int n = nums.size();
		vector<int> res(2*n);
		for(int i=0;i<2*n;i++){
			res[i] = 0;
		}
		for(int i=0;i<=n-1;i++){
			res[i] = nums[i];
		}
		for(int i=n;i<2*n;i++){
			res[i] = nums[i-n];
		}
		
		return res;
	}
};
```
