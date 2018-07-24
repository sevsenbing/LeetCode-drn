# Number of Islands
## 题目：
Given a 2d grid map of '1's (land) and '0's (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.
```
Example 1:

Input:
11110
11010
11000
00000

Output: 1
```
```
Example 2:

Input:
11000
11000
00100
00011

Output: 3
```
## 分析：
这道题上学期做过，不过用的是C语言和数组，写了七十多行，今天用C++做。建立一个数组来判断数组中的数字是否被访问过，然后找上下左右是1的数字，这样下去就可以找出一片相连的数组，这里用的是递归。找完一个后返回主函数ans+1，然后再找下一个，最后得出答案。
## 代码
```C++
class Solution {
public:
    int numIslands(vector<vector<char>>& grid) {
        if(grid.empty()||grid[0].empty()) return 0;
        int m = grid.size(),n=grid[0].size(),ans=0;
        vector<vector<bool> > visited(m, vector<bool>(n, false));
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(grid[i][j]=='1'&&!visited[i][j]){
                    Num(grid,visited,i,j);
                    ans++;
                }
            }
        }
        return ans;
    }
    void Num(vector<vector<char> >&grid, vector<vector<bool> > &visited,int x,int y) {
        if(x<0||x>=grid.size()) return;
        if(y<0||y>=grid[0].size()) return;
        if(grid[x][y]!='1'||visited[x][y]) return;
        visited[x][y]=true;
        Num(grid,visited,x-1,y);
        Num(grid,visited,x+1,y);
        Num(grid,visited,x,y-1);
        Num(grid,visited,x,y+1);
    }
};
