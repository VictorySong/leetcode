Longest Common Prefix
--------------------

[https://leetcode.com/problems/longest-common-prefix/](https://leetcode.com/problems/longest-common-prefix/)  

1. My Solution  
c++  
```c++
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        int i=0;
        int j=0;
        char s;
        if(strs.size()<1){
            return "";
        }
        while(j<strs[0].size()){
            i=0;
            s=strs[0][j];
            while(i<strs.size()){
                if(s== strs[i][j])
                    i++;
                else
                    return strs[0].substr(0,j);
            }
            j++;
        }
        return strs[0].substr(0,j);
    }
};
```
