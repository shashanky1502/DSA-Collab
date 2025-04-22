# 53. Maximum Subarray

Given an integer array nums, find the with the largest sum, and return its sum.


Example 1:

Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: The subarray [4,-1,2,1] has the largest sum 6.

```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int maxSum = INT_MIN;
        int sum = 0;
        for(int i=0;i<nums.size();i++){
            sum = max(nums[i],sum+nums[i]);
            maxSum = max(maxSum,sum);
        }
        return maxSum;
    }
};
```