- #c++11
- 定义于头文件<initializer_list>，c++11起支持，是一个模版类
  ```c++
  template< class T >
  class initializer_list;
  ```
- `std::initializer_list<T>`是一个访问`const T`类型对象数组的轻量代理对象，内部对象都是`const`型
- 复制一个`std::initializer_list<T>`不会复制其底层对象
-
## `std::initializer_list<T>`对象使用示例
### 构造函数
- 用**花括号初始化器列表**初始化一个对象，该对象构造函数接收一个`std::initializer_list<T>`参数
  ```c++
  template<typename T> 
  class CTest
  {
      CTest(std::initializer_list<T> args):vec(args) {};
      std::Vector<T> vec;
  }
  
  CTest<int> a = {1, 2, 3, 4};
  ```
-
### 操作符右值或函数调用参数
- 用**花括号初始化器列表**作为赋值操作符的右值或者作为函数的调用参数。^^可以实现函数的可变入参^^
  ```c++
  int DataAppend(DATASTORAGE &dtStorage, 
                 initializer_list<char*> args, 
                 initializer_list<LPDATAINFO> datainfos)
  {
      if (args.size() != datainfos.size())
      {
          return -1;
      }
      auto p = args.begin();
      auto q = datainfos.begin();
      for(p,q ; p != args.end(), q!=datainfos.end(); p++, q++)
      {
          dtStorage.AddData(*p, strlen(*p), *q);
      }
      return 0;
  }
  
   DataAppend(dtStorage, {lpReqOrder->OrderRef, 
                              lpReqOrder->ExchangeID, 
                              lpReqOrder->InstrumentID, 
                              lpReqOrder->CombPositionID, 
                              lpReqOrder->ExchangeAccountID},
                            {&ustOrder.DI_OrderRef, 
                              &ustOrder.DI_ExchangeID, 
                              &ustOrder.DI_InstrumentID, 
                              &ustOrder.DI_CombPositionID, 
                              &ustOrder.DI_ExchangeAccountID});
  ```
-
### 和auto，for循环配合
-
  ```c++
  for (auto n : s.v)
    std::cout << n << ' ';
  std::cout << '\n';
  
  std::cout << "Range-for over brace-init-list: \n";
  
  for (int x : {-1, -2, -3}) // auto 的规则令此带范围 for 工作
    std::cout << x << ' ';
  std::cout << '\n';
  
  auto al = {10, 11, 12};   // auto 的特殊规则
  
  std::cout << "The list bound to auto has size() = " << al.size() << '\n';
  ```
-
### 作为模版参数
-
  ```c++
  template <typename T>
  void templated_fn(T) {}
  
  // templated_fn({1, 2, 3}); // 编译错误！“ {1, 2, 3} ”不是表达式，
                               // 它无类型，故 T 无法推导
  templated_fn<std::initializer_list<int>>({1, 2, 3}); // OK
  templated_fn<std::vector<int>>({1, 2, 3});           // 也 OK
  ```