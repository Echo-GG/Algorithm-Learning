## How Many Numbers Are Smaller Than the Current Number

Given the array nums, for each nums[i] find out how many numbers in the array are smaller than it. That is,
for each nums[i] you have to count the number of valid j's such that j != i and nums[j] < nums[i].

```C++
class Solution {
	public:
	vector<int> smallerNumbersThanCurrent(vector<int>& nums) {
		int n = nums.size();
		vector<int> res;
		for(int i=0;i<n;i++){
			int count = 0;
			for(int j=0;j<n;j++){
				if(nums[j] < nums[i]){
					count++;
				}
			}
			res.push_back(count);
		}
		
		
		return res;
	}
};
```
