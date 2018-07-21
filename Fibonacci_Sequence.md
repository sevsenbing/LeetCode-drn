# Fibonacci sequence
## 题目+分析：
今天试了好多次打不开leetcode了，于是在网上找了一道题，菲波那切数列。我的思路就是相加相加，因为斐波那契数列本来就是第n个数等于前面所有数之和，但是要注意的是第一个数和第二个数。在网上看了一下别人的解题思路，原来这个就可以看做是递归树了，第一次接触觉得有点神奇。
## 代码：
```C
int Fibonacci(int n){
    if(n<=1) return n;
    else{
        int[]f=new int[n+1];
        f[0]=0;f[1]=1;
        for(int i=2;i<=n;i++)
            f[i]=f[i-1]+f[i-2];
        return f[n];
   }
}
