## Max Consecutive Ones

Given a binary array nums, return the maximum number of consecutive 1's in the array.

```C++
	
class Solution {
	public:
	int findMaxConsecutiveOnes(vector<int>& nums) {
		int n = nums.size();
		int start = 0;
		int count = 0;
		
		int temp = 0;
		while(start < n){
			count = 0;
			while(start < n && nums[start]==0){
				start ++;
			}
			while(start < n && nums[start]==1){
				count ++;
				start ++;
			}
			if(count > temp)
				temp = count;
		}
		
		count = temp;
		
		return count;
	}
};
```
