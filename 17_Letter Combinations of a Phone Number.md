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
