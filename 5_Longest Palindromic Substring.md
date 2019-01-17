Longest Palindromic Substring
------------------------------------------------------

[https://leetcode.com/problems/longest-palindromic-substring/](https://leetcode.com/problems/longest-palindromic-substring/)  

1. My solution  
javascript  
```javascript
/**
 * @param {string} s
 * @return {string}
 */
var longestPalindrome = function(s) {
    let arr=[];
    for(let i=0;i<s.length;i++){
        for(let j=s.length-1;j>i-1;j--){
            if(Palindromic(s.slice(i,j+1))){
                arr.push(s.slice(i,j+1));
                break;
            }
        }
    }
    let sub="";
    arr.forEach((val,index)=>{
        if(val.length>sub.length)
            sub=val;
    });
    return sub;
    function Palindromic(sub){
        if(sub.length==1)
            return true;
        for(let i=0;i<=(sub.length-2)>>1;i++){
            if(sub[i]!=sub[sub.length-1-i])
                return false;
        }
        return true;
    }
};
```
2. Longest Common Substring
```javascript
```
