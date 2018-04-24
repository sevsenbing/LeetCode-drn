# Reach a Number
## 题目：
You are standing at position 0 on an infinite number line. There is a goal at position target.

On each move, you can either go left or right. During the n-th move (starting from 1), you take n steps.

Return the minimum number of steps required to reach the destination.

Example 1:
Input: target = 3
Output: 2
Explanation:
On the first move we step from 0 to 1.
On the second step we step from 1 to 3.
Example 2:
Input: target = 2
Output: 3
Explanation:
On the first move we step from 0 to 1.
On the second move we step  from 1 to -1.
On the third move we step from -1 to 2.
Note:
target will be a non-zero integer in the range [-10^9, 10^9].

## 分析：
这道题的意思是，从0开始可以随意左右走，第一下走一步，第二下走两步，第n下走n步。然后给一个N值，问最少多少步可以走到。<br>
可以先求出第n步，使得从1累加到n刚好大于等于target，反向利用求和公式，求解n，然后算出当前n的累加和sum。<br>
如果此时sum和target正好相等，直接返回n。否则计算差值，差值时偶数，直接返回n，奇数判断此时n的奇偶，n是奇数返回n+2，n是偶数返回n+1。<br>

## 代码：
```ruby
class Solution {
public:
    int reachNumber(int target) {
        long n=ceil((-1.0+sqrt(1+8.0*abs(target)))/2);
        long sum=n*(n+1)/2;
        if(sum==abs(target)) return n;
        long ans=sum-abs(target);
        if((ans&1)==0) return n;
        else return n+((n&1)?2:1);
    }
};
