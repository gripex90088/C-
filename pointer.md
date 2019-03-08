##### pointer 指针

***

+ 指针与整型

```c++
#include <iostream>
#include <cstring>

using namespace std;
int main()
{
 	int * fellow; 
    // * fellow = 123456;  // err
    // cout << *fellow << endl;
    /*
    一定要在使用解除引用运算符(*)之前，将指针初始化为一个适当，确定的地址
    	由于fellow没有初始化， 它可能时任何值，fellow的指向的可能不是123456所要存储的地方，将导致一些难以跟踪的bug
    */  
    int * pt;
    // 0xB8000000老式计算机系统中视频内存的组合段偏移地址
    // pt = 0xB8000000; // C99之前，C语言允许这样赋值，但是C++在类型一致方面更为严格
    pt = (int *)0xB8000000;
    cout << pt << endl;
    
    char flower[10] = "rose";
    cout << flower << "s are red\n"; // rose s are red
    
    char str[10] = "flower";
    char *p;
    p = str;
    strcpy_s(p, strlen(str)+1, str);
}

```



