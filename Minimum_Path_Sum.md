# Minimum Path Sum
## 题目：
Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.

Example 1:
[[1,3,1],
 [1,5,1],
 [4,2,1]]
Given the above grid map, return 7. Because the path 1→3→1→1→1 minimizes the sum.

## 分析：
这道题和之前两道UniquePaths思路很相近，上网了解了一下，这种思路是动态规划。<br>
说一下这道题，就是给出一个二维数组，我假设每个格子里数字是步数，就是找出步数最少的方法。<br>
这道题也可以走一步看一步，走到每一格的总步数取决于本格步数加上左格和上格总步数最少的步数。<br>
因此需要注意的问题仍是先把最左格和最上格的总步数提前算出来。<br>
运行了4ms，应该不是最好的方法……<br>

## 代码：
```c
int minPathSum(int** grid, int gridRowSize, int gridColSize) {
    if(gridRowSize==0||gridColSize==0) return 0;
    int a[gridRowSize][gridColSize];
    a[0][0]=grid[0][0];
    for(int i=1;i<gridRowSize;i++) a[i][0]=a[i-1][0]+grid[i][0];
    for(int i=1;i<gridColSize;i++) a[0][i]=a[0][i-1]+grid[0][i];
    for(int i=1;i<gridRowSize;i++){
        for(int j=1;j<gridColSize;j++){
            a[i][j]=grid[i][j]+((a[i-1][j]>a[i][j-1])?a[i][j-1]:a[i-1][j]);
        }
    }
    return a[gridRowSize-1][gridColSize-1];
}
```
