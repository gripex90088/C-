### 共用体

***

+ **用途:** 

  1. 当数据项使用两种或多种格式（但不会同时使用）时，可节省空间

  ```c++
  union one4all
  {
  	int int_val;
  	long lang_val;
  	double double_val;
  };
  
  struct widget
  {
  	char brand[20];
      int type;
      union id // format depends on widget type
      {
  		long id_num; // type 1 widgets
          char id_char[20]; // other widgets
      } id_val;
  };
  
  // 匿名共用体
  struct anonymous_union
  {
      char bread[20];
      int type;
      union // anonymous union
      {
          // 由于共用体是匿名的，因此id_char 和 id_num被视为prize的两个成员，他们的地址相同，所以不需要中间标识符id_val,程序员负责确定当前哪个成员是活动的
          long id_num;
          char id_char[20];
      };
  };
  
  // 使用共用体one4all
  void use_one4all(void);
  void use_widget(void);
  void use_anonymous_union(void);
  
  void main()
  {
      use_one4all();  
      use_widget();
  }
  
  void use_anonymous_union(void)
  {
      anonymous_union one;
      if (one.type == 1)
      {
          cin >> one.id_num;
      } else {
          cin >> one.id_char;
      }
  }
  
  void use_widget(void)
  {
      widget prize;
      if (prize.type == 1)
      {
          cin >> prize.id_val.id_num;
      } else {
          //prize.id_val.id_char = "hello"; // 数组字符串不允许 = 赋值
          cin >> prize.id_val.id_char;
      }
  }
  
  void use_one4all(void)
  {
      // 使用one4all来存储int，long，double，条件是在不同的时间运行
      one4all pail;
      pail.int_val = 12;
      
      pail.double_val = 1.35; // store a double, int value is lost
  }
  ```

  