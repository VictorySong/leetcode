String to Integer (atoi)
--------------------------------------------------------------------------------

[https://leetcode.com/problems/string-to-integer-atoi/](https://leetcode.com/problems/string-to-integer-atoi/)  

1. My solution  
c++
```c++
class Solution {
public:
    int myAtoi(string str) {
        int i=0;
        while(str[i]==' '){
            i++;
        }
        unsigned long long a=0;
        if(str[i]=='-'){
            int j=i+1;
            bool overflow=false;
            while(47<int(str[j]) && int(str[j])<58){
                a*=10;
                a+=int(str[j])-48;
                j++;
                if(a>2147483648)
                    return 1<<31;
            }
            return -int(a);
        }else if(str[i]=='+'){
            int j=i+1;
            while(47<int(str[j]) && int(str[j])<58){
                a*=10;
                a+=int(str[j])-48;
                j++;
                if(a>=2147483648)
                    return 2147483647;
            }
            return int(a);
        }else if(47<int(str[i]) && int(str[i])<58){
            int j=i;
            while(47<int(str[j]) && int(str[j])<58){
                a*=10;
                a+=int(str[j])-48;
                j++;
                if(a>=2147483648)
                    return 2147483647;
            }
            return int(a);
        }else{
            return 0;
        }
    }
};
```
