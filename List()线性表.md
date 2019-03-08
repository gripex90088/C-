### 线性表



```C++
/***
*线性表（List）
* 零个或多个数据元素的有限序列
*—————————————————————————————————————————————————————————————————————————————
* ADT 线性表（List）
* Data
*	线性表的数据对象集合为{a1，a2，...，an}，每个元素的类型均为DataType。
*	其中，除第一个元素a1外，每个元素有且只有一个直接前驱元素，除了最后一
*	个元素an外，每一个元素有且只有一个直接后继元素。数据元素之间的关系是
*	一对一的关系
* Opeartion
*	InitList（*L）：初始化操作，建立一个空的线性表L
*	ListEmpty（L）： 若线性表为空，返回true，否则返回false
*	ClearList（*L）：将线性表清空
*	GetElem（L，i，*e）：将线性表L中的第i个位置元素值返回给e
*	LocateElem（L，e）：在线性表中查找与给定值e相等的元素，如果查找成功，返回该元素在表中序号
*						表示成功；否则，返回0表示失败
*	ListInsert（*L，i，e）：在线性表L中的第i个位置插入新元素e
*	ListDelete（*L，i，*e）：删除线性比L中第i个位置的元素，并用e返回其值
*	ListLength（L）：返回线性表L的元素个数
* endADT
*——————————————————————————————————————————————————————————————————————————————
****/
```



```C++
/**
* 线性表的顺序存储
*/
#include <iostream>

const int MaxSize = 100;

template <class T>
class SeqList
{
public:
	SeqList() { length = 0; } // 无参数构造方法
	SeqList(T a[], int n); // 有参数构造方法
	~SeqList() {}; // 析构函数
	int Length() { return length; }; // 线性表长度
	T Get(int i); // 按位查找
	int Locate(T x); // 按值查找
	void Insert(int i, T x); // 插入
	T Delete(int i);// 删除
	void PrintList(); // 遍历打印
private:
	T data[MaxSize]; // 顺序表使用数组实现
	int length; // 存储顺序表的长度
};

template <typename T>
SeqList<T>::SeqList(T a[], int n)
{
	if (n > MaxSize) throw "Wrong parameter";
	for (int i = 0; i < n; i++)
		data[i] = a[i];
	length = n;
}

template <typename T>
T SeqList<T>::Get(int i)
{
	if (i < 1 && i > length) throw "wrong Location";
	else return data[i - 1];
}

template <typename T>
int SeqList<T>::Locate(T x)
{
	for (int i = 0; i < length; i++)
		if (data[i] == x) return i + 1;
	return 0;
}

template <typename T>
void SeqList<T>::Insert(int i, T x)
{
	if (length >= MaxSize) throw "Overflow";
	if (i<1 || i>length + 1) throw "Location";
	for (int j = length; j >= i; j--)
		data[j] = data[j - 1];
	data[i - 1] = x;
	length++;
}

template <typename T>
T SeqList<T>::Delete(int i)
{
	int x;
	std::cout << length << std::endl;
	if (length == 0) throw "Underflow";
	if (i < 1 || i > length) throw "Location";
	x = data[i - 1];
	for (int j = i; j < length; j++)
		data[j - 1] = data[j];
	length--;

	return x;
}

template <typename T>
void SeqList<T>::PrintList()
{
	using std::cout;
	using std::endl;

	for (int i = 0; i < length; i++)
	{
		cout << data[i];
	}
}

int main()
{
	using std::cout;
	using std::endl;
	
//	SeqList<int> p;

	int arr[5] = { 1,2,3,4,5 };
	SeqList<int> p(arr, 6);
	cout << p.Length() <<endl;
	p.PrintList();
	
	p.Delete(6);
	p.PrintList();

	return 0;
}
```







