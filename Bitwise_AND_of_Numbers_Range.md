# Bitwise AND of Numbers Range
## 题目：
Given a range [m, n] where 0 <= m <= n <= 2147483647, return the bitwise AND of all numbers in this range, inclusive.

For example, given the range [5, 7], you should return 4.

## 分析：
最开始看这道题我一头雾水，因为没过多接触过这类问题。只好从二进制里找规律，5：101 6：110 7：111 最后得出的4：100；<br>
貌似这四个数字的共同点就是最左边都是1，那么是不是找出给出数字范围的左侧共同数就可以了<br>
那么只要不断游移，再判断是否相等，就一定可以找到左边相等的数了。<br>
最后返回的时候只需要左移【右移过的次数】。<br>

## 代码：
```ruby
class Solution {
public:
    int rangeBitwiseAnd(int m, int n) {
        int c=0;
        while(m!=n){
            m>>=1;
            n>>=1;
            c++;
        }
    return n<<c;
    }
};
```
话说在做题的时候一开始写的是
```ruby
m>>1;
n>>1;
```
超时了，去百度了一下回来，弄明白了两者的区别。
```ruby
m >> 1; // 是指把 m这个数右移一位，得到结果，当时不改变 m本身。
m >>= 1; // 是指把 m这个数右移一位，得到结果，并把结果赋值给 m 因此 m 的值被改变
```
居然又有一行代码就可以ac的方法，还用了递归，惊了。
```ruby
class Solution {
public:
    int rangeBitwiseAnd(int m, int n) {
        return (n > m) ? (rangeBitwiseAnd(m / 2, n / 2) << 1) : m;
    }
};
```
大概的思路是不相等就除以二，最后结果再乘二，其实仔细想想和左移右移思路相近，毕竟右移和左移可以看成是乘二和除二。<br>
