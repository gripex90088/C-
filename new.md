##### new && delete

相关文档 :

 	1. C++ Primer Plus 第6版  4.7.4

***

+ **在C语言中可以使用malloc()来分配内存，C++还可以使用new运算符**

+ **new**分配的内存块通常与**常规变量声明**分配的内存块不同

|              | new                                                          | 常规声明                                                     |
| ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 内存分配规则 | 值存储与堆(heap)内存或称为自由存储区(free store)中           | 值存储于栈(stack)内存中                                      |
| 创建数组     | new[]运算符创建数组时，采用动态(dynamic)联编，在运行时为数组分配存储空间，长度也在运行时设置  <br />dynamic binding, set size at run time | c常规声明创建数组时，采用静态联编，即数组长度在编译时设置<br />static binding, size fixed at compile time |

+ **delete**

  使用new与delete时，应遵守以下规则

  1. 不要使用delete释放不是new分配的内存
  2. 不要使用delete释放同一个内存两次
  3. 如果使用new[]为数组分配内存，则应使用delete[]释放
  4. 如果使用new[]为一个实体分配内存，则应使用delete(没有方括号释放)内存
  5. 对空指针应用delete时安全的
  6. 一定要配对的使用delete，否则会引发内存泄露(memory leak)

```c++
/*
C++ new 通用格式
	typeName * pointer_name = new typeName;
	typeName * pointer_name = new typeName[];
*/

#include <iostream>
using namespace std;

void main()
{
    int * pointer = new int;  // allocate memory with new
    delete pointer;  // free memory with de
    lete when done
    
    int pointer_arr = new int[10]; // allocate memory with new
    pointer_arr[0] = 1;
    pointer_arr[1] = 2;
    cout << pointer_arr[0] << endl;
    cout << pointer_arr[1] << endl;
    delete[] pointer_arr; // free memory with delete when done
    /*
    	释放整个数组，而不是指针指向的元素
    */
}
```