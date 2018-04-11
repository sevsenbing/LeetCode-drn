# Kth Smallest Number in Multiplication Table
## 题目：
Nearly every one have used the Multiplication Table. But could you find out the k-th smallest number quickly from the multiplication table?

Given the height m and the length n of a m * n Multiplication Table, and a positive integer k, you need to return the k-th smallest number in this table.

Example 1:
Input: m = 3, n = 3, k = 5
Output: 
Explanation: 
The Multiplication Table:
1	2	3
2	4	6
3	6	9

The 5-th smallest number is 3 (1, 2, 2, 3, 3).
Example 2:
Input: m = 2, n = 3, k = 6
Output: 
Explanation: 
The Multiplication Table:
1	2	3
2	4	6

The 6-th smallest number is 6 (1, 2, 2, 3, 4, 6).
Note:
The m and n will be in the range [1, 30000].
The k will be in the range [1, m * n]
## 分析：
第i行第j列的数等于i*j，以此判断一个数x在n×m第几大<br>
第i行小于等于x的数有min（n，x/i）个，将m行的值加起来即可。<br> 
## 代码：
```ruby
class Solution {
public:
    int findKthNumber(int m, int n, int k) {
        if(m<n){
            int t=n;
            n=m;
            m=t;
        }
        int s=1,e=k;
        while(s!=e){
            int x=0;
            int b=(s+e)/2;
            for(int i=1;i<=n&&i<=b;i++){
                if(b/i<m) x+=(b/i);
                else x+=m;
            }
            if(x>=k) e=b;
            else s=b+1;
        }
        for(;s>0;s--){
            for(int i=1;i<=n;i++){
                if(s%i==0&&s/i<=m) return s;
            }   
        }
    }
};
