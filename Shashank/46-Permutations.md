# 46. Permutations

Given an array nums of distinct integers, return all the possible.
You can return the answer in any order.
```
Example 1:

Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

```cpp
class Solution {
public:

    vector<vector<int>> res;
    void f(int ind,vector<int> nums){
        if(ind==nums.size())
        {
            res.push_back(nums);
            return;
        }

        for(int j=ind;j<nums.size();j++){
            swap(nums[ind],nums[j]);
            f(ind+1,nums);
            swap(nums[ind],nums[j]);
        }
    }
    vector<vector<int>> permute(vector<int>& nums) {
        f(0,nums);
        return res;
    }
};
```

### - Try placing every number at position 'ind' 

```
Fix one position at a time: Start from the first index and try placing every number at that position by swapping.

Recurse to the next position: After fixing a number at the current index, recursively move to the next index and repeat.

Store the result when done: When all positions are fixed (i.e., you've reached the end of the array), store that permutation.

Backtrack (undo swap): After each recursive call, swap the numbers back to restore the original state for the next possibility.
```
