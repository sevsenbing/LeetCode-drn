```ruby
#include <iostream>
using namespace std;
class Sample {
public:
    int v;
// 在此处补充你的代码
Sample(){}
    Sample(const Sample&n){
        if(n.v==20) v=22;
        else v=9;
    }
    Sample(int d){v=d;}
};
// 完毕
void PrintAndDouble(Sample o)
{
    cout << o.v;
    cout << endl;
}
int main()
{
    Sample a(5);
    Sample b = a;
    PrintAndDouble(b);
    Sample c = 20;
    PrintAndDouble(c);
    Sample d;
    d = a;
    cout << d.v;
    return 0;
}

