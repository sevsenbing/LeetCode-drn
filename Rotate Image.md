#  Rotate Image
## 问题：
You are given an n x n 2D matrix representing an image.

Rotate the image by 90 degrees (clockwise).

Note:

You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation.

Example 1:

Given input matrix = 
[
  [1,2,3],
  [4,5,6],
  [7,8,9]
],

rotate the input matrix in-place such that it becomes:
[
  [7,4,1],
  [8,5,2],
  [9,6,3]
]
Example 2:

Given input matrix =
[
  [ 5, 1, 9,11],
  [ 2, 4, 8,10],
  [13, 3, 6, 7],
  [15,14,12,16]
], 

rotate the input matrix in-place such that it becomes:
[
  [15,13, 2, 5],
  [14, 3, 4, 1],
  [12, 6, 8, 9],
  [16, 7,10,11]
]
## 分析：
这道题是我寒假历史遗留问题……现在看来用C++做很简单。<br>
利用temp不停地对调位置就可以了。<br>
## 代码
```ruby
class Solution {
public:
    void rotate(vector<vector<int>>& matrix) {
        int m=matrix.size();
        for(int i=0;i<m/2;i++){
            for (int j=i;j<m-1-i;j++){
                int temp=matrix[i][j];
                matrix[i][j]=matrix[m-1-j][i];
                matrix[m-1-j][i]=matrix[m-1-i][m-1-j];
                matrix[m-1-i][m-1-j]=matrix[j][m-1-i];
                matrix[j][m-1-i]=temp;
            }
        }
    }
};
