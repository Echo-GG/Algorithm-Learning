## Set Mismatch

You have a set of integers s, which originally contains all the numbers from 1 to n. Unfortunately, due to some error, one of the numbers in s got duplicated to another number in the set, which results in repetition of one number and loss of another number.

You are given an integer array nums representing the data status of this set after the error.

Find the number that occurs twice and the number that is missing and return them in the form of an array.


```C++
class Solution {
	public:
	vector<int> findErrorNums(vector<int>& nums) {
		int n = nums.size();
		vector<int> res;
		for(int i=0;i<n;i++){
			bool flag = false;
			for(int j=i+1;j<n;j++){
				if(nums[i]==nums[j]){
					res.push_back(nums[i]);
					flag = true;
					break;
				} 
			}
			if(flag)
			break;
		}
		
		int sum = (1+n)*n/2;
		int count = 0;
		for(int i=0;i<n;i++)
		count+=nums[i];
		int target = sum - count + res[0];
		res.push_back(target);
		return res;
		
	}
};

```
