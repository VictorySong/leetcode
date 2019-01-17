Longest Substring Without Repeating Characters
---------------------

[https://leetcode.com/problems/longest-substring-without-repeating-characters/](https://leetcode.com/problems/longest-substring-without-repeating-characters/)  

1. My solution  
javascript  
```javascript
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    let first=0;
    let last=-1;
    let num=0;
    let num_max=0;
    while(last<s.length-1){
        last=last+1;
        let t=true;
        for(let i=first;i<last;i++){
            if(s[last]==s[i]){
                last=last-1;
                if(num_max<num)
                    num_max=num;
                num=num-(i+1-first);
                first=i+1;
                t=false;
                break;
            }
        }
        if(t){
            num=num+1;
        }
    }
    if(num_max<num){
        num_max=num;
    }
    return num_max;
};
```
c
```c
int lengthOfLongestSubstring(char* s) {
    int first=0;
    int last=-1;
    int num=0;
    int num_max=0;
    while(s[++last]!='\0'){
        bool t=true;
        for(int i=first;i<last;i++){
            if(s[i]==s[last]){
                if(num_max<num)
                    num_max=num;
                num=num-(i+1-first);
                first=i+1;
                t=false;
                last--;
                break;
            }
        }
        if(t)
            num++;
    }
    if(num_max<num)
        num_max=num;
    return num_max;
}
```
