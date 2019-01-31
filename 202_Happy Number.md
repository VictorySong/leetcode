Happy Number
-------

[https://leetcode.com/problems/happy-number/](https://leetcode.com/problems/happy-number/)  

1. My Solution  
c++  
```c++
class Solution {
public:
    bool isHappy(int n) {
        if(n<0){
            return false;
        }
        int num=0;
        int residue=0;
        while((n%10)==0){
            n=n/10;
        }
        int pre=n;
        while(n>1){
            num=n;
            n=0;
            while(num>0){
                residue=num%10;
                n+=residue*residue;
                num=num/10;
            }
            while((n%10)==0){
                n=n/10;
            }
            if(n>pre && n>100)
                return false;
            pre=n;
        }
        return true;
    }
};
```
