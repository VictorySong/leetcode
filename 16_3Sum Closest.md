3Sum Closest
--------------

[https://leetcode.com/problems/3sum-closest/](https://leetcode.com/problems/3sum-closest/)  

1. My Solution  
c++  
```c++
class Solution {
public:
    int threeSumClosest(vector<int>& nums, int target) {
        int ans;
        sort(nums.begin(),nums.end());
        int j=0,i=nums.size()-1,k,closest,diff,sum;
        if(i>=2){
            ans=nums[0]+nums[i-1]+nums[i];
            closest=target-ans;
            closest=closest<0?-closest:closest;
        }
        while(i>=2){
            j=0;
            k=i-1;
            while(j<k){
                sum=nums[j]+nums[k]+nums[i];
                diff=sum-target;
                if(diff<0){
                    j++;
                    diff=-diff;
                }else if(diff>0){
                    k--;
                }else{
                    return sum;
                }
                if(diff<closest){
                    closest=diff;
                    ans=sum;
                }
            }
            i--;
        }
        return ans;
    }
};
```
Runtime: 4 ms, faster than 100.00% of C++ online submissions for 3Sum Closest.  
Memory Usage: 774.1 KB, less than 91.16% of C++ online submissions for 3Sum Closest.
