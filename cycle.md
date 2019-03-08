### 循环



+ for

  ```c++
  /* 基于范围的for循环 (c++11) 遍历？*/
  
  double prices[5] = {4.99, 10.99, 6.87, 9.7, 8.55};
  
  for (double x : prices)
      cout << x << endl;
  
  cout << "华丽的分割线=========================;\n";
  
  // 修改
  for (double &x : prices)
      x = x * 0.80;
  
  for (double x : prices)
      cout << x << endl;
  ```

  



+ 延时循环

  ```c++
  void waiting1(void)
  {
  	long wait = 0;
  	while (wait < 10000 )
  		wait++;
  }
  
  void waiting2(void)
  {
  	int i = 0;
  	while (i < 1000)
  	{
  		cout << clock() << endl;
  		i++;
  	}
  		
  	cout << "Enter the delay time, in seconds: ";
  	float secs;
  	cin >> secs;
  	clock_t delay = secs * CLOCKS_PER_SEC; // convert to clock ticks
  	cout << "starting\a\n";
  	clock_t start = clock();
  	while (clock() - start < delay) // wait until time elapses
  		; // note the semicolon
  	cout << "done \a\n";
  }
  ```

  