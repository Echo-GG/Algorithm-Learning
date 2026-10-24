## Shuffle the Array

Given the array nums consisting of 2n elements in the form [x1,x2,...,xn,y1,y2,...,yn].

Return the array in the form [x1,y1,x2,y2,...,xn,yn].

```C++
class Solution {
	public:
	vector<int> shuffle(vector<int>& nums, int n) {
		
		vector<int> res(2 * n);
		for(int i=0;i<2*n;i++){
			res[i] = 0;
		}
		int idx = 0;
		int l1 = 0;
		int l2 = n;
		while(l1 < n && l2 < 2 * n && idx < 2 * n){
			res[idx++] = nums[l1];
			res[idx++] = nums[l2];
			
			l1 ++;
			l2 ++;
		}
		
		return res;
	}
};
```
