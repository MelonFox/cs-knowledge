- #c++11
## using 定义类成员函数指针
-
  ```c++
  class CA
  {
  public:
      void func(int a, int b)
      {
          cout << a << " " << b << endl;
      }
      void funcB(double a, int b)
      {
          cout << "funcB " << a << endl;
      }
  };
  
  //using代替typedef定义类成员函数别名，并使用模版
  template<typename T>
  using call = void(CA::*)(T, int);
  
  //入参是CA类的成员函数指针
  template<typename T>
  void testfunc(call<T> lpcall)
  {
      CA *pa = new CA();
      T a = 1;
      (pa->*lpcall)(a, 6);
  }
  
  //调用方法：入参是CA类的成员函数指针
  testfunc<double>(&CA::funcB);
  
  ```
-