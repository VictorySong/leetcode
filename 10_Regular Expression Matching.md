Regular Expression Matching
--------------------------------------------------------------------------------

[https://leetcode.com/problems/regular-expression-matching/](https://leetcode.com/problems/regular-expression-matching/)  

1. My Solution  
c++  
```c++
class Solution {
public:
    bool isMatch(string s, string p) {
        int i,j;
        i=j=0;
        while(i<s.size() && j<p.size()){
            if(96<int(p[j]) && int(p[j])<123){
                if(p[j+1] && p[j+1]=='*'){
                    char a=p[j];
                    int a_num=0;
                    bool first=true;
                    int f_a_tag;
                    j+=2;
                    while(p[j] && (p[j]==a || p[j+1]=='*')){
                        if((p[j]!=a || p[j+1]!='*') && first){
                            f_a_tag=j;
                            first=false;
                        }
                        if(p[j+1]=='*'){
                            j+=2;
                        }else{
                            a_num++;
                            j++;
                        }
                    }
                    int a_num_1=a_num;
                    while(s[i] && s[i]==a){
                        i++;
                        a_num--;
                    }
                    if(a_num>0)
                        return false;
                    else
                        i-=a_num_1;
                    if(!first){
                        j=f_a_tag;
                    }
                }else{
                    if(s[i]==p[j]){
                        i++;
                        j++;
                    }else
                        return false;
                }
            }else if(p[j]=='.'){
                if(p[j+1] && p[j+1]=='*'){
                    j+=2;
                    while(p[j] && p[j]=='.'){
                        if(p[j+1]=='*')
                            j+=2;
                        else
                            j++;
                    }
                    if(p[j] && p[j]!='*'){
                        while(s[i] && s[i]!=p[j])
                            i++;
                        if(!s[i])
                            return false;
                    }else if(!p[j])
                        return true;
                    else
                        return false;
                }else{
                    i++;
                    j++;
                }
            }else{
                return false;
            }
        }
        if(i==s.size() && j==p.size())
            return true;
        else
            return false;
    }
};
```
