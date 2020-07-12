[toc]
#### 注意边界
太多次越界了，很多时候CLion并不会报错~~难道是我漏看了exit code?~~
一提交运行直接崩了

### C++相关
#### 初始化列表的使用要小心
```c++
vector<int> ret(n + 1, 1); // 初始化为n+1个1
vector<int> ret{n + 1, 1}; // 初始化为n + 1, 1两个元素！
```

#### 普通数组也可以使用range for进行遍历

#### push_back vs emplace_back
[C++ difference between emplace_back and push_back function
](http://candcplusplus.com/c-difference-between-emplace_back-and-push_back-function)  
1. 如果对象的构造函数参数不止一个，push_back只能接受对象实例；emplace_back可以接受构造函数的参数！
push_back只能接受对象实例或者单参数版本的构造函数的参数（通过隐式类型转换，如果声明为explicit也不行
而emplace_back可以接受多个构造函数参数

2. 性能  
对于内置类型没区别，对于自定义类型，emplace_back性能更好  
如果传入的是对象实例则没区别，如果传入的是构造对象参数  
* push_back  
如果直接传入构造函数参数，则通过隐式类型转换创建临时对象
    1. 调用构造函数创建临时对象
    2. 在vector中创建一个临时对象的拷贝
    3. 销毁临时对象
* emplace_back
不会创建临时对象，而是直接在vector中创建对象。避免了创建不必要的临时对象


### JetBrians产品中关于GitHub的fork、pull request使用
[官方文档](https://www.jetbrains.com/help/idea/contribute-to-projects.html)  
需要先**VCS | Git | Rebase my GitHub fork**  
之后就可以看到upstream