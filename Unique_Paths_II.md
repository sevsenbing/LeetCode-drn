# Unique Paths II
## 问题：
Follow up for "Unique Paths":

Now consider if some obstacles are added to the grids. How many unique paths would there be?

An obstacle and empty space is marked as 1 and 0 respectively in the grid.

For example,
There is one obstacle in the middle of a 3x3 grid as illustrated below.

[
  [0,0,0],
  [0,1,0],
  [0,0,0]
]
The total number of unique paths is 2.

Note: m and n will be at most 100.
## 分析：
就像unique paths I 一样，仍然是走楼梯思路，不同的地方就是多了障碍物，一旦遇到障碍物，就此路不通了。也就是说，只要遇到障碍物，之前所有走过的路都归零。所以可以反向加，每个格子的方法个数取决于上面的格子和左边的格子，并且该格子若有障碍物，就要归零。这个方法需要注意的是，要把所有初始的最左和最上的格子先判断完，再遍历剩下的。</br>
## 代码：
```ruby
int uniquePathsWithObstacles(int** obstacleGrid, int obstacleGridRowSize, int obstacleGridColSize) {
    int a[obstacleGridRowSize][obstacleGridColSize];    
    a[0][0]=(obstacleGrid[0][0]==0)?1:0;    
    for(int i=1;i<obstacleGridRowSize;i++) a[i][0]=(a[i-1][0]!=0&&obstacleGrid[i][0]==0)?1:0;    
    for(int j=1;j<obstacleGridColSize;j++) a[0][j]=(a[0][j-1]!=0&&obstacleGrid[0][j]==0)?1:0; 
    for(int i=1;i<obstacleGridRowSize;i++){    
        for(int j=1;j<obstacleGridColSize;j++){    
            if(obstacleGrid[i][j]==0) a[i][j]=a[i-1][j]+a[i][j-1];
            else a[i][j]=0;    
        }    
    }    
    return a[obstacleGridRowSize - 1][obstacleGridColSize - 1];    
}
