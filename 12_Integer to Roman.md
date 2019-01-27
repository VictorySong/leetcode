Integer to Roman
----------------

[https://leetcode.com/problems/integer-to-roman/](https://leetcode.com/problems/integer-to-roman/)  

1. My Solution  
c++  
```c++
class Solution {
public:
    string intToRoman(int num) {
        string str;
        int tem=num/1000;
        num=num%1000;
        while(tem>0){
            str=str+"M";
            tem--;
        }
        while(num>=100){
            if(num>=900){
                str=str+"CM";
                num-=900;
            }else if(num>=500){
                str=str+"D";
                num-=500;
            }else if(num>=400){
                str=str+"CD";
                num-=400;
            }else{
                tem=num/100;
                num=num%100;
                while(tem>0){
                    str=str+"C";
                    tem--;
                }
            }
        }
        while(num>=10){
            if(num>=90){
                str=str+"XC";
                num-=90;
            }else if(num>=50){
                str=str+"L";
                num-=50;
            }else if(num>=40){
                str=str+"XL";
                num-=40;
            }else{
                tem=num/10;
                num=num%10;
                while(tem>0){
                    str=str+"X";
                    tem--;
                }
            }
        }
        while(num>0){
            if(num>=9){
                str=str+"IX";
                num-=9;
            }else if(num>=5){
                str=str+"V";
                num-=5;
            }else if(num>=4){
                str=str+"IV";
                num-=4;
            }else{
                while(num>0){
                    str=str+"I";
                    num--;
                }
            }
        }
        return str;
    }
};
```
