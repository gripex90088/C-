### 简单文件输入/输出

##### 	C++ Primer Plus Chapter 6, page 207

+ 写入到文本文件	C++ Primer Plus 6.8.2

-------------------------------------------------------------------------------------------------------------------------

**警告: ** 打开已有文件，以接受输出时，默认将它长度截短为零，因此原来的内容将丢失

```C++
#include <iostream>
#include <fstream>

using namespace std;
int main()
{
	char automobile[50];
	int year;
	double a_price;
	double d_price;

	ofstream outFile; // create object for output
	outFile.open("carinfo.txt"); // associate with a file

	cout << "Enter the make and model of automobile: ";
	cin.getline(automobile, 50);
	cout << "Enter the model year: ";
	cin >> year;
	cout << "Enter the original asking price: ";
	cin >> a_price;
	d_price = 0.913 * a_price;

	cout << fixed;
	cout.precision(2);
	cout.setf(ios_base::showpoint);
	cout << "make and model: " << automobile << endl;
	cout << "Year: " << year << endl;
	cout << "Was asking $" << a_price << endl;
	cout << "Now asing $" << d_price << endl;

	outFile << fixed;
	outFile.precision(2);
	outFile.setf(ios_base::showpoint);
	outFile << "Make and model: " << automobile << endl;
	outFile << "Year: " << year << endl;
	outFile << "Was asking $" << a_price << endl;
	outFile << "Now asking $" << d_price << endl;
	outFile.close();
	return 0;
}
```



+ 读取文本文件 	C++ Primer Plus 6.8.3

-----------------------------------------------------------------------------------------------

**警告:**Windows文本文件中的每行都已回车字符和换行符结尾；通常情况下，C++在读取文件时将两个字	符转换为换行符， 并在写入文件时执行相反的转换，有些文本编辑器，不会自动在最后一行末尾添加换行符，因此，请在输入最后的文本后按下回车键，然后保存文件

```C++
#include <iostream>
#include <fstream>
#include <cstdlib>

using namespace std;

const int SIZE = 60;

int main()
{
	char filename[SIZE];
	ifstream inFile; // object for handling file input
	cout << "Enter name of data file: ";
	cin.getline(filename, SIZE);
	inFile.open(filename); //  associate inFile with a file
	if (!inFile.is_open()) // failed to open file
	{
		cout << "Coule not open the file " << filename << endl;
		cout << "Program termination.\n";
		exit(EXIT_FAILURE);
	}
	
	double value;
	double sum = 0.0;
	int count = 0; // number of items read
	
	inFile >> value; // get first value
	while (inFile.good()) // with input good and not at EOF
	{
		++count; // one more item read
		sum += value; // calculate running total
		inFile >> value; // get next value
	}
	
	if (inFile.eof())
		cout << "End of file reached.\n";
	else if (inFile.fail())
		cout << "Input terminated by data mismatch.\n";
	else
		cout << "Input terminated for unknown reason.\n";
	
	if (count == 0)
		cout << "No data processed.\n";
	else 
	{
		cout << "Items read: " << count << endl;
		cout << "Sum: " << sum << endl;
		cout << "Average: " << sum / count << endl;
	}
	
	inFile.close(); // finished with the file
	return 0;
}
```

