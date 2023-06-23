# TWO SUM

Question : Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target. You may assume that each input would have exactly one solution, and you may not use the same element twice. You can return the answer in any order.

### BRUTE FORCE - Using two loops

Algorithm: 
- Iterate two loops.
- If sum of two elements equals to target, return those two elements.
- If not found then return empty vector.

Time Complexity: O(N<sup>2</sup>), Space Complexity: O(1)
```cpp 
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int n = nums.size();
        for(int i = 0; i <n; i++){
            for(int j =i+1; j<n; j++){
                if(nums[j] + nums[i] == target ){
                    return {i,j};
                }
            }
        }
        return {};
    }
};
```

### OPTIMISED - Using Map.
Algorithm:
- Iterate the loop from left to right.
- Initialize an empty Map.
- Compute the Complement of number i.e. target - current element.
- Search in Map if this number exists.
- If yes then return the indices.
- If No then push the current element in Map. 
- If loop gets completed and no such pair is found, then return empty vector.
