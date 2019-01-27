Container With Most Water
------------------------

[https://leetcode.com/problems/container-with-most-water/](https://leetcode.com/problems/container-with-most-water/)  

1. My Solution  
c++(<font color='red'>Time Limit Exceeded</font>)  
```c++
class Solution {
public:
    int maxArea(vector<int>& height) {
        int v_max=0;
        int v=0;
        for(int i=0;i<height.size();i++){
            for(int j=i+1;j<height.size();i++){
                v=(height[i]<height[j]?height[i]:height[j])*(j-i);
                if(v>v_max)
                    v_max=v;
            }
        }
        return v_max;
    }
};
```
I don't know why this solution which is also given by leetcode can't pass.  

2. Two Pointer Approach  
c++  
```c++
class Solution {
public:
    int maxArea(vector<int>& height) {
        int i=0;
        int j=height.size()-1;
        int v_max=0;
        int v=0;
        while(i!=j){
            if(height[i]<height[j]){
                v=height[i]*(j-i);
                v_max=(v>v_max?v:v_max);
                i++;
            }else{
                v=height[j]*(j-i);
                v_max=(v>v_max?v:v_max);
                j--;
            }
        }
        return v_max;
    }
};
```
