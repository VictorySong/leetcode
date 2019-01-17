Median of Two Sorted Arrays
------------

[https://leetcode.com/problems/median-of-two-sorted-arrays/](https://leetcode.com/problems/median-of-two-sorted-arrays/)  

1. My solution  
javascript  
```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number}
 */
var findMedianSortedArrays = function(nums1, nums2) {
    let [m,n]=[nums1.length,nums2.length];
    if((m+n)&1){
        return findk((m+n-1)>>1);
    }else{
        return (findk((m+n-1)>>1)+findk((m+n)>>1))/2;
    }
    function findk(k){
        //对长度小的进行二分
        if(nums1.length>nums2.length){
            let tem=nums1;
            nums1=nums2;
            nums2=tem;
        }
        //处理空字符串
        if(nums1.length==0)
            return nums2[k];
        let [i1,j1]=[0,Math.min(nums1.length-1,k)];//如果不加Math.min 下边的循环中l2可能小于0 但是如果是求中位数,这个位置不加Math.min 也没关系 因为k>=nums1.length;
        let l1=(i1+j1)>>1;
        let l2=k-1-l1;
        //l1+l2+2=k+1;
        while(i1<j1 && (nums1[l1]>nums2[l2+1] || nums2[l2]>nums1[l1+1])){
            if(nums1[l1]>nums2[l2+1]){
                j1=l1;
                l1=(i1+j1)>>1;
                l2=k-1-l1;  //l2+l1+2=k+1;
            }else if(nums2[l2]>nums1[l1+1]){
                i1=l1+1; //为了防止i1=l1 j1=l1+1 时陷入死循环
                l1=(i1+j1)>>1;
                l2=k-1-l1;
            }
        }
        if(i1==j1){
            if(l1==0){
                //向左二分或者根本没有进行二分nums1.length==1;
                //此刻l2有可能等于-1 如输入[1] [1]
                if(nums1[l1]>=nums2[l2+1])
                    return nums2[l2+1];
                else if(l2>=0)
                    return Math.max(nums1[l1],nums2[l2]);
                else
                    return nums1[l1];
            }else{
                if(l1==k)
                    return nums1[l1];
                else
                    return Math.max(nums1[l1],nums2[l2]);  //这一个else其实可以省掉,但因考虑到和下边情况不同这个还没进行nums1[l1]>nums2[l2+1] || nums2[l2]>nums1[l1+1]的判断就不省了
            }
        }else{
            return Math.max(nums1[l1],nums2[l2]);
        }
    };  
}
```  
