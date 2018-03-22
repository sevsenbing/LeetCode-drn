# Best Time to Buy and Sell Stock with Transaction Fee
## 分析：
Your are given an array of integers prices, for which the i-th element is the price of a given stock on day i; and a non-negative integer fee representing a transaction fee.

You may complete as many transactions as you like, but you need to pay the transaction fee for each transaction. You may not buy more than 1 share of a stock at a time (ie. you must sell the stock share before you buy again.)

Return the maximum profit you can make.

Example 1:
Input: prices = [1, 3, 2, 8, 4, 9], fee = 2
Output: 8
Explanation: The maximum profit can be achieved by:
Buying at prices[0] = 1
Selling at prices[3] = 8
Buying at prices[4] = 4
Selling at prices[5] = 9
The total profit is ((8 - 1) - 2) + ((9 - 4) - 2) = 8.
Note:

0 < prices.length <= 50000.
0 < prices[i] < 50000.
0 <= fee < 50000.
## 分析：
由于第i天的情况只和i-1天有关，所以用两个变量就可以，不需要用数组。<br>
## 代码：
```ruby
class Solution {
public:
    int maxProfit(vector<int>& prices, int fee) {
        int ans=0,m=-prices[0],i;
        for(i=1;i<prices.size();i++){
            ans=max(ans,m+prices[i]-fee);
            m=max(m,ans-prices[i]);
        }
        return ans;  
    }
};
