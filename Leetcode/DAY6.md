## Find All Numbers Disappeared in an Array
Given an array nums of n integers where nums[i] is in the range [1, n], return an array of all the integers in the range [1, n] that do not appear in nums.


```C++
class Solution {
	public:
	vector<int> findDisappearedNumbers(vector<int>& nums) {
		int n = nums.size();
		vector<int> res;
		
		// for(int i=0;i<n;i++){
			//     int idx = abs(nums[i]) - 1;
			//     if(nums[idx] > 0){
				//         nums[idx] = -nums[idx];
				//     }
			// }
		
		// for(int i=0;i<n;i++){
			//     if(nums[i]>0){
				//         res.push_back(i+1);
				//     }
			// }
		
		
		
		vector<bool> seen(n+1,false);
		for(int i=0;i<n;i++){
			seen[nums[i]] = true;
		}
		
		for(int i=1;i<=n;i++){
			if(!seen[i]){
				res.push_back(i);
			}
		}
		
		// for(int i=1;i<=n;i++){
			//     bool flag = false;
			
			//     for(int j=0;j<n;j++){
				//         if(nums[j] == i){
					//             flag = true;
					//             break;
					//         }
				//     }
			//     if(!flag){
				//         res.push_back(i);
				//     }
			
			// }
		
		return res;
	}
};

```
