Letter Combinations of a Phone Number
---------------------

[https://leetcode.com/problems/letter-combinations-of-a-phone-number/submissions/](https://leetcode.com/problems/letter-combinations-of-a-phone-number/submissions/)  

1. My Solution  
c++  
```c++
class Solution {
public:
    vector<string> letterCombinations(string digits) {
        vector<string> map={"","","abc","def","ghi","jkl","mno","pqrs","tuv","wxyz"};
        vector<int> stack_i;
        vector<int> stack;
        int length=digits.size(),i=0,tem;
        string str;
        vector<string> ans;
        //初始化
        while(i<length){
            tem=int(digits[i])-48;
            stack.push_back(tem);
            stack_i.push_back(0);
            str.push_back(map[tem][stack_i[i]]);
            i++;
        }
        int stack_end=length-1;
        i=stack_end;
        while(i>-1){
            tem=stack[i];            
            if(stack_i[i]<map[tem].size()){
                str[i]=map[tem][stack_i[i]];
                if(i==stack_end){
                    stack_i[i]++;
                    ans.push_back(str);
                }else{
                    for(i++;i<length;i++){
                        stack_i[i]=0;
                        str[i]=map[stack[i]][stack_i[i]];
                    }
                    i--;
                }
            }else{
                i--;
                if(i>-1)
                    stack_i[i]++;
            }

        }
        return ans;
    }
};
```
Runtime: 4 ms, faster than 3.19% of C++ online submissions for Letter Combinations of a Phone Number.  
Memory Usage: 4.7 MB, less than 0.95% of C++ online submissions for Letter Combinations of a Phone Number.  
c++  
```c++
class Solution {
public:
    vector<string> map={"","","abc","def","ghi","jkl","mno","pqrs","tuv","wxyz"};

    vector<string> letterCombinations(string digits) {
        if(digits.size()<1){
            return {};
        }else if(digits.size()==1){
            int num=int(digits.front())-48;
            vector<string> ans;
            int i=0;
            string a;
            while(i<map[num].size()){
                a=map[num][i];
                ans.push_back(a);
                i++;
            }
            return ans;
        }else{
            int num=int(digits.front())-48;
            vector<string> re=letterCombinations(digits.substr(1));
            vector<string> ans;
            int i=0,j=0;
            while(i<map[num].size()){
                j=0;
                string a;
                a=map[num][i];
                while(j<re.size()){
                    ans.push_back(a+re[j]);
                    j++;
                }
                i++;
            }
            return ans;
        }
    }
};
```
Runtime: 4 ms, faster than 3.23% of C++ online submissions for Letter Combinations of a Phone Number.  
Memory Usage: 4.9 MB, less than 0.95% of C++ online submissions for Letter Combinations of a Phone Number.  
