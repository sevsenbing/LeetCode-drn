# Arranging Coins
## 题目：
You have a total of n coins that you want to form in a staircase shape, where every k-th row must have exactly k coins.

Given n, find the total number of full staircase rows that can be formed.

n is a non-negative integer and fits within the range of a 32-bit signed integer.

Example 1:

n = 5

The coins can form the following rows:
¤
¤ ¤
¤ ¤

Because the 3rd row is incomplete, we return 2.
Example 2:

n = 8

The coins can form the following rows:
¤
¤ ¤
¤ ¤ ¤
¤ ¤

Because the 4th row is incomplete, we return 3.
## 分析：
粗暴的写，一行一行放，最后看最后一行还有没有硬币，从此判断返回什么。<br>
## 代码：
```ruby
class Solution {
public:
    int arrangeCoins(int n) {
        int ans=1;
        for(int m=n-1;m>=ans+1;m-=ans){
            ans++;
        }
        return n==0?0:ans;
    }
};
```
这题网上看又有一行可以写完的代码，惊了。<br>
```ruby
class Solution {
public:
    int arrangeCoins(int n) {
        return (int)((-1 + sqrt(1 + 8 * (long)n)) / 2);
    }
};
```
运用等差数列的性质。
