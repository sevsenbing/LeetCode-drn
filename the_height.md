# 高度
## 题目：
编程序实现功能：在一个标高为0m的平面上，有四个高度为15m的圆塔，其塔心坐标分别为（2,2）、（-2,2）、（2,-2）、（-2,-2）<br>
塔的圆半径为1m。输入一个坐标点的值，则输出该点的高度（假定塔外高度为0m）<br>
## 分析：
其实这不是LeetCode上的题，今天有高中同学问了我，<br>
要用C语言做，就复习了一下，加上之前一直没用过math那一套函数里的pow函数。<br>
pow函数头文件：<math.h> 格式： pow(a,b) a是底数，b是指数。<br>
## 代码：
```ruby
#include<stdio.h>
#include<math.h>
int main(){
    float x,y;
    int h=0;
    scanf("%f%f",&x,&y);
    if(x>=0&&y>=0) if(pow(x-2,2)+pow(y-2,2)<=1) h=15;
    if(x>=0&&y<=0) if(pow(x-2,2)+pow(y+2,2)<=1) h=15;
    if(x<=0&&y>=0) if(pow(x+2,x)+pow(y-2,2)<=1) h=15;
    if(x<=0&&y<=0) if(pow(x+2,x)+pow(y+2,2)<=1) h=15;
    printf("%d\n",h);
    return 0;
}
