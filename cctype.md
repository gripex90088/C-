### cctype

##### 	字符函数库，提供一组用于分析字符输入的工具

##### C++ Primer Plus  6.3, page 196

~~~C++
#include <iostream>

using namespace std;

int main()
{
	cout << "Enter text for analysis, and type @"
		"to termiunate input.\n";

	char ch;
	int whitespace = 0;
	int digits = 0;
	int chars = 0;
	int punct = 0;
	int others = 0;

	cin.get(ch); // get first character

	while (ch != '@') // test for sentinel
	{
		if (isalpha(ch))
			chars++;
		else if (isspace(ch))
			whitespace++;
		else if (isdigit(ch))
			digits++;
		else if (ispunct(ch))
			punct++;
		else
			others++;
		cin.get(ch);
	}

	cout << chars << " letters, "
		<< whitespace << " whitespace, "
		<< digits << " digits, "
		<< punct << " punctuations, "
		<< others << " others.\n";

	return 0;
}
~~~

