```C++
用途: 代替#define(宏定义)
const int a = 10;
const int b = 20;
int array2[a + b];
```

```c++
C++ const  与 C const 的区别
{
	C :  const是一个只读变量，有自己的存储空间
	C++:可能分配存储空间，也可能不分
		C++ const分配存储空间的时间
		{
          a) 当const为全局，并且在其它文件中使用，分配存储空间
          b) 当使用&地址操作符获取const常量时，分配存储空间
		}
}

// C++ 修改局部const
int main()
{
    const int testA = 10;
    int *p = NULL;
    p = (int *)&testA;
    *p = 10; // 间接赋值
    cout << testA << endl;
    return 0;
}
```

