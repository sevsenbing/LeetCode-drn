# Happy Number
## 题目：
Write an algorithm to determine if a number is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.

Example: 19 is a happy number

12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1

## 分析：
这道题是要找出快乐数，快乐数就是各个位上的数字平方，得出的数相加，再平方，相加，平方，相加。<br>
我的做法是额外定义一个函数，把每个位平方的和算出来，主函数里用两个数分别等于n一个调用函数一次，一个两次，如果存在周期的话，这两个数肯定相等<br>

## 代码：
```ruby
int sum(int n){
    int sum=0;
    int temp;
    while (n>0){
       temp=n%10;
        sum=sum+temp*temp;
        n=n/10;
    }
    return sum;
}
bool isHappy(int n){
    int x=n,y=n;
    do{
        x=sum(x);
        y=sum(y);
        y=sum(y);
    }
    while(x!=y);
    if (x==1) return 1;
    else return 0;
}
