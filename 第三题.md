```ruby
例：
输入：
apple
apple
zz
ww
qq
o
ddd
ddd
输出：
apple 25.00%
ddd 25.00%
o 12.50%
qq 12.50%
ww 12.50%
zz 12.50%

#include <iostream>
#include <cstdio>
#include <cstring>
#include <algorithm>
using namespace std;

typedef struct node
{
    char name[30];      //记录关键字字符串
	int balance ;			//平衡因子
	int count ;			//出现次数
    struct node *lchild ;	//左孩子
	struct node *rchild ;	//右孩子
}treenode, *avl;

int n ;  				//所有树种出现的总次数

treenode *create(char *key) ;
int height( avl tree ) ;
avl insertt( char *key , avl tree ) ;
void InOrder( avl tree );
avl LL( avl tree ) ;
avl RR( avl tree ) ;
avl LR( avl tree ) ;
avl RL( avl tree ) ;

treenode *create(char *key)
{
    treenode *tree = new treenode;
	strcpy( tree->name , key);
	tree->balance = 0;
	tree->count = 1;
	tree->lchild = NULL;
	tree->rchild = NULL;
    return tree;
}

int height( avl tree ) //深度   
{
    if( tree == NULL ) //如果这个节点为空，那么返回的深度就是-1
    {
	    return -1 ;
    }
	return tree->balance ;
}

avl insertt( char *key , avl tree )
{
    if( tree == NULL )
    {
        avl node = create( key );
        tree = node ;
    }
    else if( strcmp ( tree->name , key ) ==0 )
    {
 	   tree->count ++ ;
	}
    else if( strcmp ( key , tree->name ) < 0 )   
    {
        tree->lchild = insertt( key , tree->lchild ) ;
        if( height( tree->lchild ) - height( tree->rchild ) == 2 )  
        {    
            if( strcmp ( key , tree->lchild->name ) < 0 ) 
            {
			    tree = LL( tree ) ;
			}
            else
			{                        
                tree = LR( tree ) ;
			}
        }
    }
    else if( strcmp ( key , tree->name ) > 0 )    
    {
        tree->rchild = insertt ( key , tree->rchild ) ;
        if ( height( tree->lchild ) - height( tree->rchild) == -2 )  //AVL树不平衡
        {
            if ( strcmp ( key , tree->rchild->name ) > 0 )  // 插入到右子树右边，做单旋转
            {
			    tree = RR ( tree ) ;
			}
            else                       //插入到右子树左边，做双旋转
            {
			    tree = RL ( tree ) ;
			}
        }
    }
    tree->balance = max ( height( tree->lchild) , height( tree->rchild) ) + 1 ;
    return tree ;
}
void InOrder( avl tree )
{
    if( tree != NULL )        //按照中序遍历模式计算输出就是字典序
    {
        InOrder ( tree->lchild ) ;
        printf ( "%s %.2f%%\n" , tree->name , ( (double ) ( tree->count ) / ( double ) n ) * 100 ) ;  //输出字符串和所占百分比
        InOrder ( tree->rchild ) ;
    }
}

avl LL( avl tree )   //LL型的不平衡结点进行左单旋转
{
    avl temp ;
    temp = tree->lchild ;
    tree->lchild = temp->rchild ;
    temp->rchild = tree ;
    tree->balance = max( height( tree->lchild ) , height(tree->rchild ) ) + 1 ;  //旋转后重新调整树的高度
    temp->balance = max( height( temp->lchild ) , tree->balance ) + 1 ;
    return temp ;
}

avl RR( avl tree )   //RR型的不平衡结点处进行右单旋转
{
    avl temp ;
    temp = tree->rchild ;
    tree->rchild = temp->lchild ;
    temp->lchild = tree ;
    tree->balance = max( height( tree->lchild ) , height( tree->rchild) ) + 1 ;
    temp->balance = max( height( temp->rchild ) , tree->balance ) + 1 ;
    return temp ;
}

avl LR( avl tree )//LR型的不平衡结点处进行左右双旋  
{
    tree->lchild = RR( tree->lchild ) ;  //对不平衡结点的左孩子右旋转
    tree =  LL( tree ) ;   //对不平衡结点处左旋转
	return tree ;
}

avl RL( avl tree )
{
    tree->rchild = LL( tree->rchild ) ;  //对不平衡结点的右孩子左旋转
    tree =  RR( tree ) ;   //对不平衡结点处右旋转
	return tree ;
}

int main()
{ 
    avl tree = NULL ;
    char name[ 30 ] ;
    scanf( "%d" , &n ) ;
	getchar();
    for( int i = 0 ; i < n ; i++ )
    {
        gets( name ) ;
        tree = insertt ( name , tree ) ;   //将输入的字符串插入到二叉树中
    }
    InOrder ( tree ) ;
    return 0 ;
}
```
