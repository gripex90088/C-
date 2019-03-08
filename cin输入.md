### cin

##### 		C++ Primer Plus chapter 5, page 171 

​	

+ 原始cin输入

  ```c++
  char ch;
  int count = 0;
  cout << "Enter characters: enter # to quit:\n";
  cin >> ch; // get a character
  while (ch != '#') // test the character
  {
      cout << ch; // echo the character
      ++count; // count the characeter
      cin >> ch; // get the next character
  }
  cout << endl << count << " characters read \n";
  ```

  

+ cin.get(char)

  ```c++
  char ch;
  int count = 0;
  cout << "Enter characters; enter # to quit:\n";
  cin.get(ch); // use the cin.get(ch) function
  /*
  	使用哪一个cin.get()
  	在第4章的程序清单4.5中，使用一下代码
  	char name[ArSize];
  	...
  	cout << "Enter your name:\n";
  	cin.get(name, ArSize).get();
  	最后一行相当于两个函数调用，
  	cin.get(name, ArSize);
  	cin.get()的一个版本接受两个参数: 数组名(字符串(char*类型)的地址) 和 ArSize(int类型整数) （name是第一个元素的地址，因此字符数组名的类型为char*）
  	cin.get();
  */
  while (ch != '#')
  {
      count << ch;
      ++count;
      cin.get(ch); // use it again
  }
  cout << endl << count << " characters read\n";
  ```



+ 文件尾条件

  ```c++
  char ch;
  int count = 0;
  cin.get(ch); // attempt to read a char
  while (cin.fail() == false) // test for EOF
  {
      cout << ch; // echo character
      ++count;
      cin.get(ch); // attempt to read another char
  }
  
  cout << endl << count << " characters read\n";
  ```

  





