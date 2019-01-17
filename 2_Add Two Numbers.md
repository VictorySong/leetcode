Add Two Numbers
--------------------------------------------------------------

[https://leetcode.com/problems/add-two-numbers/](https://leetcode.com/problems/add-two-numbers/)  

1. My Solution  
javascript  
```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var addTwoNumbers = function(l1, l2) {
    let p1=l1;
    let p2=l2;
    let p3=null,p4=null;
    let tem=0
    while(p1 !=null || p2!=null){
        if(p1!=null && p2!=null){
            let n=p1.val+p2.val+tem;
            if(p3==null){
                p3=new ListNode(n%10);
                p4=p3;
            }else{
                p3.next=new ListNode(n%10);
                p3=p3.next;
            }
            tem=Math.floor(n/10);
            p1=p1.next;
            p2=p2.next;
        }else if(p1!=null){
            let n=p1.val+tem;
            if(p3==null){
                p3=new ListNode(n%10);
                p4=p3;
            }else{
                p3.next=new ListNode(n%10);
                p3=p3.next;
            }
            tem=Math.floor(n/10);
            p1=p1.next;
        }else if(p2!=null){
            let n=p2.val+tem;
            if(p3==null){
                p3=new ListNode(n%10);
                p4=p3;
            }else{
                p3.next=new ListNode(n%10);
                p3=p3.next;
            }
            tem=Math.floor(n/10);
            p2=p2.next;
        }
    }
    if(tem!=0){
        p3.next=new ListNode(tem);
    }
    return p4;
};
```  
c++
```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode *p1=l1,*p2=l2,*p3=NULL,*p4=NULL;
        int tem=0;
        while(p1!=NULL || p2!=NULL){
            int a;
            if(p1!=NULL && p2!=NULL){
                a=p1->val+p2->val+tem;
                if(p3==NULL){
                    p3=new ListNode((a%10));
                    p4=p3;
                }else{
                    p3->next=new ListNode((a%10));
                    p3=p3->next;
                }
                p1=p1->next;
                p2=p2->next;
            }else if(p1!=NULL){
                a=p1->val+tem;
                if(p3==NULL){
                    p3=new ListNode((a%10));
                    p4=p3;
                }else{
                    p3->next=new ListNode((a%10));
                    p3=p3->next;
                }
                p1=p1->next;
            }else if(p2!=NULL){
                a=p2->val+tem;
                if(p3==NULL){
                    p3=new ListNode((a%10));
                    p4=p3;
                }else{
                    p3->next=new ListNode((a%10));
                    p3=p3->next;
                }
                p2=p2->next;
            }
            tem=a/10;
        }
        if(tem!=0){
            p3->next=new ListNode(tem);
        }
        return p4;
    }
};
```  
