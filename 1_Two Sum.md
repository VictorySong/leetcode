Two Sum
-------------------------------------

[https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)  

1. My solution  
c++  
```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int i,j,count;
        count=nums.size();
        for(i=0;i<count;i++){
            for(j=i+1;j<count;j++){
                if(target==(nums[i]+nums[j])){
                    vector<int> r(2,i);
                    r[1]=j;
                    return r;
                }
            }
        }
    }
};
```
javascript
```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    for(let i=0;i<nums.length;i++){
        for(let j=i+1;j<nums.length;j++){
            if(target==(nums[i]+nums[j])){
                return [i,j];
            }
        }
    }
};
```
