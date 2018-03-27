# Coin Change
## 题目：
You are given coins of different denominations and a total amount of money amount. Write a function to compute the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

Example 1:
coins = [1, 2, 5], amount = 11
return 3 (11 = 5 + 5 + 1)

Example 2:
coins = [2], amount = 3
return -1.

Note:
You may assume that you have an infinite number of each kind of coin.

Credits:
Special thanks to @jianchao.li.fighter for adding this problem and creating all test cases.

## 分析：
这道题就是相当于给出一个钱数，然后如何找零<br>
从1开始，逐渐+1的迭代<br>
把“零钱”从小到大排序，然后申请一个数组，数组中的i对应通过硬币组合出来的数字，数组[i]就是存的硬币的最小值。<br>

## 代码：
```ruby
int coinChange(int * coins, int coinsSize, int amount) {
    int ji(const int*a,const int*b);
    int i,j,n=0,l;
    int *ying=(int*)malloc(sizeof(int)*(amount+1));
    ying[0]=0;
    qsort(coins,coinsSize,sizeof(int),ji);
    for(i=1;i<=amount;i++){
        ying[i]=amount+1;
        for(j=0;j<coinsSize&&coins[j]<=i;j++){
            if(coins[j]==i){
                ying[i]=1;
                break;
            }
            l=i-coins[j];
            ying[i]=(ying[l]!=-1&&ying[l]+1<ying[i])?ying[l]+1:ying[i];
        }
        ying[i]=(ying[i]==amount+1)?(-1):ying[i];
    }
    return ying[amount];
}
int ji(const int*a,const int*b){return *a-*b;}
