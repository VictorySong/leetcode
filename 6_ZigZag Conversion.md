ZigZag Conversion
------------------

[https://leetcode.com/problems/zigzag-conversion/](https://leetcode.com/problems/zigzag-conversion/)  

1. My Solution  
javascript  
```javascript
/**
 * @param {string} s
 * @param {number} numRows
 * @return {string}
 */
var convert = function(s, numRows) {
    if(numRows==1)
        return s;
    let arr=new Array(numRows);
    for(let i=0;i<numRows;i++)
        arr[i]="";
    let i=0;
    let j=0;
    let ud=true;
    while(i<s.length){
        arr[j]=arr[j]+s[i];
        if(ud){
            if(j==numRows-1){
                j--;
                ud=false;
            }else
                j++;
        }else{
            if(j==0){
                j++;
                ud=true;
            }else
                j--;
        }
        i++;
    }
    let str='';
    arr.forEach(data=>{
        str+=data;
    });
    return str;
};
```
