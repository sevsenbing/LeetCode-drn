# Spiral Matrix
## 题目：
Given a matrix of m x n elements (m rows, n columns), return all elements of the matrix in spiral order.

For example,
Given the following matrix:

[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]
You should return [1,2,3,6,9,8,7,4,5].

## 分析：
螺旋走位，那就按顺序来就好了，先往右，再往下，再往左，再往上，循环往复，直至走到中心位置。<br>
需要处理的地方就是，由于是螺旋的，所以每次循环每个方向的长度肯定有变化，可以设置四个值来标记。<br>
从colBegin到colEnd遍历，rowBegin++。从rowBegin到rowEnd遍历，colEnd--。从colEnd到colBegin遍历，rowEnd--。从rowEnd到rowBegin遍历，colBegin++<br>
不过运行了36ms，估计是一个笨方法吧。

##代码：
```c
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* spiralOrder(int** matrix, int matrixRowSize, int matrixColSize) {
    int*ans = (int*)malloc(matrixRowSize*matrixColSize*sizeof(int)),k=0,i=0;
    int rowBegin=0, rowEnd=matrixRowSize-1;
    int colBegin=0, colEnd=matrixColSize-1;
    while((rowBegin<=rowEnd) && (colBegin<=colEnd)){
        for(i=colBegin; i<=colEnd; i++) ans[k++]=matrix[rowBegin][i];
        rowBegin++;
        for(i=rowBegin; i<=rowEnd; i++) ans[k++] = matrix[i][colEnd];
        colEnd--;
        if(rowBegin<=rowEnd){
            for(i=colEnd; i>=colBegin; i--) ans[k++] = matrix[rowEnd][i];
        }
        rowEnd--;
        if(colBegin<=colEnd){
            for(i=rowEnd; i>=rowBegin; i--) ans[k++] = matrix[i][colBegin];
        }
        colBegin++;
    }
    return ans;
}
```
