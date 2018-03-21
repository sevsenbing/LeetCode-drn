# Best Time to Buy and Sell Stock
## 题目：
Say you have an array for which the ith element is the price of a given stock on day i.

If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.

Example 1:
Input: [7, 1, 5, 3, 6, 4]
Output: 5

max. difference = 6-1 = 5 (not 7-1 = 6, as selling price needs to be larger than buying price)
Example 2:
Input: [7, 6, 4, 3, 1]
Output: 0

In this case, no transaction is done, i.e. max profit = 0.
## 分析：
这个是按照时间轴来的<br>
因此卖出一定要在买入之后。<br>
## 代码：
```ruby
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int min =INT_MAX, ans = 0;
        for(int i = 0 ; i < prices.size(); i++){
            min=prices[i]<min?prices[i]:min;
            ans=(prices[i]-min)>ans?prices[i]-min:ans;
        }
        return ans;
    }
};
```

# Best Time to Buy and Sell Stock II
## 题目：
Say you have an array for which the ith element is the price of a given stock on day i.
Design an algorithm to find the maximum profit. You may completeas many transactions as you like (ie, buy one and sell one share of the stock multiple times). However, you may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).
## 分析：
这道题在上一题的基础上可以无限买入和卖出，因此只要前一天的股票比这一天的便宜，便可卖出。<br>
## 代码：
```ruby
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int ans=0;
        for(int i=1;i<prices.size();i++) 
            ans=(prices[i]>prices[i-1])?prices[i]-prices[i-1]+ans:ans;
        return ans;
    }
};
