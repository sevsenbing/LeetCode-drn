# Unique Paths
## 问题：
A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).How many possible unique paths are there?

Note: m and n will be at most 100.
## 分析：
和之前学的走楼梯有点像，这个就是有的格子有两种走法，向右或者向下，有的格子只有一种，向右。最后把所有情况加一起就可以啦。</br>
## 代码：
```ruby
int uniquePaths(int m, int n) {
    int heng=(m>n)?m:n;
    int shu=(m<n)?m:n;
    int a[100];
    for(int i=0;i<heng;i++) a[i]=1;
    for(int j=1;j<shu;j++){
        a[j]=a[j]*2;
        for(int i=j+1;i<heng;i++) a[i]=a[i-1]+a[i];
    }
    return a[heng-1];
}  
