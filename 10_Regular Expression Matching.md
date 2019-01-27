Regular Expression Matching
--------------------------------------------------------------------------------

[https://leetcode.com/problems/regular-expression-matching/](https://leetcode.com/problems/regular-expression-matching/)  

1. My Solution  
c++  
wrong thingking process
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
The algorithm above is wrong. It can solve s='aaa' p='ab*a*c*a'(the letters between 'a*' and 'a' will not appear) by counting the number of a ,but not s='aaca' p='ab*a*c*a'. I can set an array for the letters between 'a*' and 'a'.  
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
                    j+=2;
                    int sub_first=j;
                    int sub_j=j;
                    while(p[j] && (p[j+1] && p[j+1]=='*')){
                        j+=2;
                    }
                    int sub_end=j;
                    while(s[i] && s[i]==a){
                        i++;
                        a_num++;
                    }
                    bool s_exist_sub=false;
                    while(sub_j!=sub_end){
                        if(s[i] && s[i]==p[sub_j]){
                            i++;
                            s_exist_sub=true;
                        }else{
                            sub_j+=2;
                        }
                    }
                    //此时sub_j==j
                    if(p[sub_j]==a){
                        if(!s_exist_sub){
                            while(p[j] && p[j]==a){
                                a_num--;
                                j++;
                            }
                            if(a_num<0){
                                return false;
                            }
                        }
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
The algorithm above solves s='aaca' p='ab*a*c*a' but fails in s='aaa' p='ab*a*c*a'  
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
                    j+=2;
                    int sub_first=j;
                    int sub_j=j;
                    while(p[j] && (p[j+1] && p[j+1]=='*')){
                        j+=2;
                    }
                    int sub_end=j;
                    while(s[i] && s[i]==a){
                        i++;
                        a_num++;
                    }
                    if(p[sub_end]==a){
                        bool s_exist_sub=false;
                        while(sub_j!=sub_end){
                            if(s[i] && s[i]==p[sub_j]){
                                i++;
                                s_exist_sub=true;
                            }else{
                                sub_j+=2;
                            }
                        }
                        //此时sub_j==j
                        if(!s_exist_sub){
                            while(p[j] && p[j]==a){
                                a_num--;
                                j++;
                            }
                            if(a_num<0){
                                return false;
                            }
                        }
                    }else{
                        j=sub_first;
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
The algorithm above fails in s='a' p='ab*'  
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
                    j+=2;
                    int sub_first=j;
                    int sub_j=j;
                    while(p[j] && (p[j+1] && p[j+1]=='*')){
                        j+=2;
                    }
                    int sub_end=j;
                    while(s[i] && s[i]==a){
                        i++;
                        a_num++;
                    }
                    if(p[sub_end] && p[sub_end]==a){
                        bool s_exist_sub=false;
                        while(sub_j!=sub_end){
                            if(s[i] && s[i]==p[sub_j]){
                                i++;
                                s_exist_sub=true;
                            }else{
                                sub_j+=2;
                            }
                        }
                        //此时sub_j==j
                        if(!s_exist_sub){
                            while(p[j] && p[j]==a){
                                a_num--;
                                j++;
                            }
                            if(a_num<0){
                                return false;
                            }
                        }
                    }else{
                        j=sub_first;
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
        else if(i==s.size()){
            while(p[j+1] && p[j+1]=='*'){
                j+=2;
            }
            if(p[j])
                return false;
            else
                return true;
        }else
            return false;
    }
};
```
I think the algorithm above can solve s='a' p='ab*' but not in leetcode site because the string "a" in the leetcode ends with '"'.
