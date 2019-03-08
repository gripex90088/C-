### struct

***



```c++
#include <iostream>
#include <string>

struct article // structure delcaration
{
	string title; // Must inlcude string header file
    string content;
};

struct inflatable
{
    char name[20];
    float volume;
    double price;
} in1, in2; // 结构体变量 structure variable

article structure_declaration_fun()
{
    article article1
    {
        "This is the title of the article",
        "This is the content of the article"1
    }
    return article1;
}

void initialzation_struct(void)
{
    inflatable infl = {
        "米其林",
        15,
        20
    };
    
    inflatable inf2 {
       	"米其林2",
        15,
        30
    };
    
    // 结构体变量
    in1 = {
        "米其林111",
        15,
        30
    };
}

int main()
{
    article article;
    article1 = structure_declaration_fun(); // 可以使用赋值运算符，将结构体赋值给另一个同类型的结构体
   
    initialzation_struct(); //初始化结构体
    return 0;
}
```

