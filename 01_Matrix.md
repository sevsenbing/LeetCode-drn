# 01 Matrix
## 题目：
Given a matrix consists of 0 and 1, find the distance of the nearest 0 for each cell.

The distance between two adjacent cells is 1.
Example 1: 
Input:

0 0 0
0 1 0
0 0 0
Output:
0 0 0
0 1 0
0 0 0
Example 2: 
Input:

0 0 0
0 1 0
1 1 1
Output:
0 0 0
0 1 0
1 2 1
Note:
The number of elements of the given matrix will not exceed 10,000.
There are at least one 0 in the given matrix.
The cells are adjacent in only four directions: up, down, left and right.

## 分析：
这道题我一开始想的方法超笨，遍历数组，如果遇到‘1’，就从上下左右找是否有0，最后还要比较一下上下左右走到0的步数。结果果然超时了……错代码放一下……<br>
```ruby
class Solution {
public:
    vector<vector<int>> updateMatrix(vector<vector<int>>& matrix) {
        int n=matrix.size(),m=matrix[0].size(),i,j,ans[4]={1,1,1,1};
        for(i=0;i<n;i++){
            for(j=0;j<m;j++){
                if(matrix[i][j]==1){
                    int a=i,b=j;
                    while((a--)>=0&&matrix[a][b]>0){
                        if(matrix[a][b]!=0){ 
                            ans[0]++;
                            a--;
                        }
                    }
                    a=i;
                    while((a++)<=n-1&&matrix[a][b]>0){
                         if(matrix[a][b]!=0){ 
                            ans[1]++;
                            a++;
                         }
                    }
                    a=i;
                    while((b++)<=m-1&&matrix[a][b]>0){
                        if(matrix[a][b]!=0){
                            ans[2]++;
                            b++;
                        }
                    }
                    b=j;
                    while((b--)>=0&&matrix[a][b]>0){
                        if(matrix[a][b]!=0){
                            ans[3]++;
                            b--;
                        }
                    }
                    sort(ans,ans+4);
                    matrix[i][j]=ans[0];
                }
            }
        }
        return matrix;
    }
};
```
长又臭，在终端上测试倒是没问题，不过我自己都嫌弃这串代码……<br>
经历了想不明白怎么简化这段代码之后，上网看了一下大神们的做法，惊了，我果然还是太年轻……根本不用考虑0的事，只要min(ans[i][j],ans[i-1][j]+1)就可以了！<br>

## 代码：
```ruby
class Solution {
public:
    vector<vector<int>> updateMatrix(vector<vector<int>>& matrix) {
         int m=matrix.size(),n=matrix[0].size();
         vector<vector<int>>ans(m,vector<int>(n,INT_MAX-1));
         for (int i=0;i<m;i++){
             for (int j=0;j<n;j++){
                 if (matrix[i][j]==0)ans[i][j]=0;
                 else{
                     if(i>0) ans[i][j]=min(ans[i][j],ans[i-1][j]+1);
                     if(j>0) ans[i][j]=min(ans[i][j],ans[i][j-1]+1);
                 }
             }
         }
         for(int i=m-1;i>=0;i--){
             for(int j=n-1;j>=0;j--) {
                 if(ans[i][j]!=0&&ans[i][j]!=1){
                     if(i<m-1) ans[i][j]=min(ans[i][j],ans[i+1][j]+1);
                     if(j<n-1) ans[i][j]=min(ans[i][j],ans[i][j+1]+1);
                 }
             }
         }
         return ans;
     }
};
