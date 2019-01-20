Palindrome Number
--------------------------------------------------------------------------------

[https://leetcode.com/problems/palindrome-number/](https://leetcode.com/problems/palindrome-number/)  

1. My solution  
c++  
```c++
class Solution {
public:
    bool isPalindrome(int x) {
        if(x<0)
            return false;
        else if(x==0)
            return true;
        else{
            char a[100];
            int i=0;
            while(x>0){
                a[i]=x%10;
                x=x/10;
                i++;
            }
            i--;
            int b=(i+1)/2;
            for(int j=0;j<b;j++){
                if(a[j]!=a[i-j])
                    return false;
            }
            return true;
        }
    }
};
```
