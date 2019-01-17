Reverse Integer
------------

[https://leetcode.com/problems/reverse-integer/](https://leetcode.com/problems/reverse-integer/)  

1. My Solution  
javascript  
```javascript
/**
 * @param {number} x
 * @return {number}
 */
var reverse = function(x) {
    let num;
    let rev=0;
    if(x>0){
        num=x;
        while(num>0){
            rev*=10;
            rev+=num%10;
            num=Math.floor(num/10);
        }
    }else if(x<0){
        num=-x;
        while(num>0){
            rev*=10;
            rev+=num%10;
            num=Math.floor(num/10);
        }
        rev=-rev;
    }
    if(rev<-2147483648 || rev>2147483647)
        return 0;
    return rev;
};
```
