## **面向对象程序设计**
### **object-oriented**
[教程相关!!!](https://www.geeksforgeeks.org/copy-constructor-in-cpp/) 
***
### 头文件与输入输出


~~~
iostream
using namespace std;
cin>>..>>..;
cout<<..<<..<<endl;

int i = 4;
int j(4);
~~~

- C++中函数原型可以不包含参数的名字,只包含类型,但是在函数定义时必须给出参数名
```C++
int Area(int, int);
```

- C++的缺省参数
    - 缺省参数只能从右向左缺省
    - 调用时若一个参数缺省,则后面的参数都缺省

### **bind**
~~~
int &y = x;
y = k;
~~~
- 引用，y相当于x的别名
- int &&k = i;//**illegal**
- int* &p = ps;//**right**
- int& *p//**illegal**
### **string**
字符串**类**
~~~
string s;
string *ps;
~~~
可以进行赋值，加减等操作
- string s1,s2;
- s1 = s2;
- string *ps1,*ps2;
- ps1 = ps2;

### static
- 在global变量上加static，可以防止其他的.cpp文件访问
- 在函数中加static,实际上相当于全局变量


### new&delete
内存空间的申请和清除,在堆中的动态申请
~~~
new int;
new Stash;
new int[10];
delete p;
delete[] p;
~~~
~~~
int *psome = new int[10];
delete [] psome;
~~~
***

# class in C++
~~~
class Point{
public:
        void init(int x,int y);
        void move(int dx,int dy);
        void Print();

Privat:
        int x;
        int y;
}
~~~

## :: resolver

- **Class name::function name**
- **:: function name**   //function not in class
~~~
void S::f(){
    ::f();
    ::a++;
    a--;
}
~~~

## this

- class 中隐藏的参数类型
- 是结构的指针
- eg: Point* this


# Objects vs. Class

~~~
class Point{
private:
    float x;
    float y;
public:
    Point(int x,int y);//构造函数
    Point(int deep);//函数重载
    Point() {x = 31; y = 17;};
    ~Point{
        cout<<~;
        print();
    }
    void print();
    void move(int dx,int dy);
}
~~~
- 自动完成初始化
- 允许函数重名，但参数表不同
- 无参数的构造函数为默认构造函数（default constructor）

### constructor
~~~
class X{
    int i;
public:
    X();
};
~~~

- 构造函数完成初始化

### destructor
~~~
class Y{
    public:
    ~Y();
};
~~~
- 本地变量生存期结束被析构

**程序三部分**
- Point.h:类的声明（成员变量、成员函数）
- Point.cpp：类的定义（需要 include） **creater**
- main.cpp : **user**

**Declarations(声明)**
- extern varibles
- function prototypes(函数声明)
- class/struct decaration
- inline function(内联函数)

## Standard header file structure
~~~
ifndef
define

endif
~~~

## STL
- 标准模板库
- 容器
- map:any key type,any value type.sorted
- vector: like C carry ,but auto-extending
- list: doubly-linked list

## vector
- eg:vector<string> note
- note.push_back(s)
- note.size()

## Basic Vector Operations
- **constructors**:
  - vector<Elem> c;
  - vector<Elem> c1(c2);

- **simple methods**:
  - V.size()
  - V.empty()
  - ==,!=,<,><=,>=
  - V.swap(v2)

- **iterators**:
  - I.begin()  //first position
  - I.end()    //last position

- **element access**:
  - V.at(index)
  - V[index]
  - V.front()   //first element
  - V.back()    //last element

- **add/remove/find**:
  - V.push_back(e)
  - V.pop_back()
  - V.insert(pos,e)
  - V.erase(pos)//删除
  - V.clear()
  - V.find(first,last,item)
  - vector 的自动增长只能通过上述操作进行，直接对不存在的下标赋值不会报错，但size不会增长

  **List Class**
    - 双向链表
    - x.front()
    - x.back()
    - x.push_back(intem) x.push_front(item)
    - x.pop_back() x.pop_back()
    - x.remove(item)

  **Maps**
    - 键-值对
    - hash map
    ~~~
    - map<k,v> m;
    - map<k,v> m1(m2);
    - map<k,v> m(b,e);
    - m.insert(e)
    - m.insert(beg,end)
    - m.insert(iter,e)
    - m.count(k)//看k是否存在
    - m.find(k)//找到k的对应值
    - m.erase(k)//key
    - m.erase(p)//point
    - m.erase(b,e)
    ~~~
    ~~~
    map<string,float> price;
    price["apple"] = 0.75;
    ~~~

    **iterate**
    ~~~
    list<int> L;
    list<int>::iterator li;
    li = L.begin();
    /**
    L.erase(li);
    ++li;; **/      //WRONG
    li = L.erase(li);   //RIGHT
    ~~~

    ## initialization vs.assignment
    - 初始化列表

    ## function overload

    **默认参数**
    - 从右向左放置，中间不空
    - 多文件时，在声明的时候默认

    ## friends
    - 友元类：可以访问成员变量的非成员函数
    - 友元函数

    ## inline functions(内连函数)
    - put inline function's bodies in headerfile(包括类中的inline function)
    - definition inline functions are just decarations
    - 类中直接定义函数相当于 inline functions
    - 可以在类中定义(实际为声明)函数直接加上inline关键字,并且在下面写出函数的内容(有inline关键字)
    - 定义其实是声明
    - 要把整个inline函数放到头文件中(.h)而不是在.cpp中
    - 优点:减少函数调用的开销,缺点:可执行文件变大 (以空间换时间)
    - 编译器会有一些优化
    - 存取函数可以做成inline函数

    ## const
    - for const
  const默认为内部链接(inernal linkage),只有在被定义的文件中可见，在其他编译单元不可见. 定义const时必须赋值给他，除非进行了extern的声明. 编译器不为const分配内存空间（除非进行了extern声明）,保存在符号表中
    ~~~
    char * const q = "abc";//q is const 指针不能再指向其
    他的对象
    const char* p ="ABCD";//(*p)  is a const char 
    限制指针的行为 内存可变(通过其他的指针)
    ~~~
    ~~~
    string p1("Fred");
    const string *p = &p1;//(*p)不可变
    string const*p = &p1;//(*p)不可变
    string* const p = &p1;//p不能改变
    ~~~
    ~~~
    char *s = "Hello";//该字符串为const
    ~~~

  - const for array or struct
    - 只是分配了一块不可更改的空间，编译时并不知道具体的内容是什么
  ~~~
  const int i[] = { 1, 2, 3, 4};
  float f[i[3]]; // Illegal  
  struct S { int i, j;};
  const S s[] = { { 1, 2 }, { 3, 4 }};
  double d[s[1].j]; // Illegal
  ~~~

    ## const objects
   - const的对象
       内容无法被修改 
   - const的成员变量
        放在构造函数的**初始化列表**
   - 不可以把const的对象赋值给非const的指针,这样可能会使const的内容改变
   - 返回一个非const的对象可以作为左值使用,返回const object不可以作为左值

    ## const function
    - 在类中将成员函数修饰为const表明在该函数体内，不能修改对象的数据成员而且不能调用非const函数。
    - const实际上是对this指针的修饰,相当于一种重载
    - const的object只可以调用const的函数
    ~~~
    我们定义的类的成员函数中，常常有一些成员函数不改变类的数据成员，也就是说，这些函数是"只读"函数，而有一些函数要修改类数据成员的值。如果把不改变数据成员的函数都加上const关键字进行标识，显然，可提高程序的可读性。其实，它还能提高程序的可靠性，已定义成const的成员函数，一旦企图修改数据成员的值，则编译器按错误处理。
    ~~~ 
    成员函数的const关键字在声明和定义时都要有
    const可以实现函数重载 原因在于const实际上作用在隐藏的this上

   ## static
   - eg:类中的 staic in m_h 会被所有的对象共享，在全局数据区，注意:一定要在对应的.cpp 文件中定义一个对应的全局变量
   - 类中的静态变量
   - 类中的静态函数：只能访问静态变量，使静态变量的访问受限，避免全局变量 ,没有产生对象时就可以调用
      类名::static函数名
   - 消除全局变量 
  
  ## avoiding name clashes
  - namespace写在.h文件中
  ~~~
  namespace old1{
    void f();
    void g();
  }

  namespace old2{
    void f();
    void g();
  }
  eg: old2::f();
      using namespace old2;
      using namespace std;

  namespace short = ***;
  ~~~
  - namespace are open    可以在不同的头文件中写同一个namespace的内容

  ## inheritance(继承)
  - superclass
  - subclasses
  - 拿已有的类定义新的类，继承全部的内容
  ~~~
  类中：
  public
  private
  protected:自身和子类可以访问
  ~~~
  - **static**的成员函数不可以是**virtual**函数,同时**static**的成员函数也不可以是**const**的函数

  - 可以把一个指向子类的指针当作指向父类的指针看待,子类的指针指向的前半部分内容就是父类的内容
  - 要注意继承时的构造函数的书写:在初始化列表里调用父类的构造函数

  ## polymorphism(多态)
  - 可以把子类的对象交给父类的变量(指针,引用)
  - sizeof()在编译时计算
  - 没有任何变量的类在内存中有一个字节(占位)
  - 直接将子类的对象赋给父类的变量会发生**sliced off**（直接将多的内容切除）类型转换,这样的情况下vptr不进行赋值,只有构造函数时才会赋值vptr. 
  - 引用和指针有同样的多态特性
  - 析构函数需要是 **virtual** 
  ```C++
  Shape* p  = new Ellipse(100.0F,200.0F);
  delete p;
  /* 实际上发生两步:
  1. p->detor()  析构函数
  2. free 
  */
  ```

  - up-casting(造型)
  - 
    - 把子类的指针或引用赋给父类 
    - 把子类当作父类看待
    - 子类的内容没有发生任何变化
  - 调用时使用父类的不同子类 
  - 关键字：virtual
    - 子类出现新的不同版本
  - binding
    - 静态
    - 动态
  - 多态变量(* &)
   - 通过 .访问(静态)
          **->** 或 **引用** 访问通过被访问内容判断：访问变量和非virtual函数时为静态
  - 有virtual函数的类，第一项是vtable指向virtual函数(函数指针)
  - 类中构造函数调用虚函数，虚函数看起来不起作用；类中其他函数调用虚函数为动态绑定(this->)
  - vptr可以指向vtable中的内容，在类被创建时确定，子类对象向父类对象赋值时不会改变,不进行vptr的拷贝.
  - 子类的函数中调用父类的函数
  - 要将析构函数做成virtual函数
  ```C++
  void 
  Derived::func() {
    cout << "In Derived::func!";
    Base::func(); 
  }
  ```
  - 在父类的**virtual**函数中,返回父类的**指针**或**引用**,在子类的相同的**virtual**函数中,可以返回子类的**指针**或**引用**,但返回分别返回子类,父类本身,则不能进行这样的重载. 


  - **override**(覆盖)
    - 父类与子类之间
    - 函数的名称和参数表相同
    - 父类中函数为virtual类
    - 返回类型相同(如果是&或*可以返回父类类型的子类)
  - **namehide:**父类中有多个overload的函数，子类中有与其同名的，则其他的overload函数在子类中不再存在

  - 禁止制造对象的机制(**抽象类**)：类中有一个虚函数为**纯虚函数** eg： virtual void render() = 0;   抽象类
  - C++支持多继承,没有单根结构

  ## copy constructor (拷贝构造)
  - T::T(const T&)
  - 在函数传参数和返回值时可能发生隐式的拷贝构造
  - 如果类中含有指针变量，需要自己重写拷贝构造函数
  - 注意拷贝构造时存在**指针**的情况,要保证拷贝后指向的不是同一块空间
  - 不写时会有默认的拷贝构造函数   
  - 禁止使用拷贝构造:
    ```C++
    Person(const Person &rhs) = delete;
    ```

  ## 运算符重载
  - operator * (...)
  - 单目运算符作为成员，双目运算符作为非成员(利用友元访问其中的内容)
  - 当重载的运算符是友元函数可以显示指定形参,是成员函数不可以
  - a++调用 **operator++(int)**
  - ++a调用 **operator++()**
  ```C++
  const Integer& Integer :: operator++(){
    this->i += 1;
    return *this;   //++a
  }

  const Integer& Integer :: operator ++(int){
    Integer old (*this);
    ++(*this);  //调用了第一个重载函数
    return old;   //a++
  }
  ```

  - 赋值运算符重载
如果自己不写,编译器会提供一个(类比于拷贝构造).要完善对**动态申请**内容的拷贝.
```C++
template <class T>
T& T::operator=( const T& rhs) {
  if( this != &rts) {   //进行的是地址的比较不是值的比较
    // perform assignment
    //要先判断是否赋值的内容是否指向了相同的内容.
  }
  return *this;
}
//赋值运算后得到的结果可以做左值.
```

  ~~~
  bool Integer :: operator >(const Integer& rhs){
    return i>rhs.i;
  }
  ~~~
  - []的运算符重载，返回引用(&)便于做左值+
  ~~~
  T& operator = (const T&that){
    if(this!=&that){
      do
    } //避免两者指向同一区域造成的错误
    else return *this;
  }
  ~~~
  ~~~
  类型转换函数
  X::operator T()//T为要转化的类型
  ~~~

  - **operator->**
    可以使对象表现的和指针一样,但这个重载运算符的返回值一定是指针

  - **operator()**
    使类表现的像函数一样 
  - && 右值引用
  - std::move()//将任何类型的值转为右值并赋值过去
    - 优点：减少大量的复制

- **Value Classes**
![p](../pic/1.png "a")
**explicit关键字:**
如果对**PathName(const string&)** 加上 **explicit**那么代表这个构造函数只可以被**显式**的调用,则上面最后一行的赋值语句不可以正确进行.

- 类型转化函数
```C++
class Rational {
  public:
    ...
    operator double () const;
};
Rational r(1,3); double d = 1.3 * r;
```
一般形式
```C++
X::operator T()
将X类型的对象转化为T类型.
```
User-defined T->C   for (**C=T**)
- if C(T) is a valid constructor call for C
- if operator C() is defined by T
两种方法不能同时存在否则会发生冲突.

  ## templates(模板)
  - 泛型
  ```C++
  template <class T>
  可以用T来带指任意的类型
  void swap(T& a,T& b);
  ```
  ```C++
  template<class T>
  class vector{
    ...
  }
  函数的定义：
  template <class T>
  T& vector<T> :: operator[](int index){
      return content[index];
  }
  //注意<T>
  ```
- 模版不在参数表中
```C++
template <class T>
T f(int i) {
  T a;
  a = a+i;
  return a;
}
f<double>(c);   //这样做可以指定返回类型
```
- 模板函在要使用的时候直接进行调用即可

- 函数模版的匹配规则
  • Check first for unique function match(必须完全匹配,包括是否含关键字const)
  • Then check for unique function template match (模版匹配)
  • Then implicit conversions on regular functions (对常规函数进行隐式的类型转化)

- **Class templates:**

- 模版中含有多个类型
```C++
template<class Key,class Value>;//但是一般使用单个字母
``` 

- **Expression paraeters:**
```C++
template <class T,int bounds=100>
class FixedVector {
  public:
  /*   */
  private:
  T elements[bounds];
};

//在写其中的函数模板时
template <class T,int bounds>
T& FixedVector<T,bounds>::operator[](int i) {
  ...
}
//在使用时可以指定初始值也可以不指定
```

- 模版的继承
```C++
template <class A>
class Derived ::public Base {

};

template <class A>
class Derived::public List<A> {

};
```



- 模版中的**friend**和**static**存在一些可能出现的问题

![p](../1.png "课件")
![p](../2.png "课件")


- 文件结构
模版中的函数实际上都是**decarelation**,都要放在.h文件中而不是.cpp文件中,这一点和**inline**相同
而静态成员变量一定要在.cpp文件中放一个全局变量.




## 右值引用
```C++
int && a = 10;
```

## 移动构造
```C++
std::move()
```
[移动构造相关](https://zhuanlan.zhihu.com/p/365412262)
 
[教程相关!!!](https://www.geeksforgeeks.org/copy-constructor-in-cpp/) 

- copy constructor发生的时刻
1.当类的对象按值返回时。
2.当类的对象通过值作为参数传递（给函数）时。
3.当一个对象是基于同一类的另一个对象构造时。
4.当编译器生成一个临时对象时。

- copy constructor注意
默认的拷贝构造只是浅拷贝,当类中有指针等内容时一定要自己重写,否则会产生很多危险.
 
## 异常处理
  ```C++
  try{
    ...
    }catch(SomeType v) {
      // handler code 
    }
    catch(...){
      //...为万能捕捉器 
    }
  
  ```
  - 关键字：**throw**,可以throw任何内容,可以构造一个异常情况的类然后将其抛出
例:写一个VectorIndexError类来处理下标越界的异常

  - 异常声明
  这个声明保证了函数不会抛出VIE以外的异常
```C++
void func throw(VIE) {
   
}
```
```C++
void f() throw() {
  /*不会抛出任何异常,否则程序终止*/
} 

void f() {
  /*可能抛出任何异常*/
}
```

  - 构造函数可能发生异常,构造没有完成,而这时内存无法被正确回收
    - 两阶段构造
    - 在构造函数中放try块

  - 析构函数发生异常,空间回收无法进行,内存无法正确回收
  - 将互相依赖的内容都放到一个try块中,每一个步骤的成功执行依赖于上一步

## Smart Pointer





## 类型转换

- **static_cast**
  - 是一种显式类型转化,不是隐式类型转化
  ```C++
  const int g = 20;
  int *h = static_cast<int*>(&g);   //error
  ```
  - static_cast<type>(expression) is not safe 
    when it is used to cast object pointer 
    (complilers does not check this conversion)



- **dynamic_cast:**
  - checks whether a downcast of object pointer is safe
  - 会动态检查类型转化是否安全,不安全会返回NULL.


- **const_cast:**
  可以用来转化const类型的变量或指针.

- **reinterperet_cast:**
  It is used to convert **pointers** or **reference** into integer or backforth
  ```C++
  int a,b;
  int *pA = &b;
  a = reinterperet_cast<int>(pA); //corret
  pA = reinterperet_cast<int*>(a);  //corret

  a = reinterperet_cast<int>(b); //error

  ``` 


## Streams
- **Extrators**:(提取器)
  istream:overload the >> operator
  ```C++
  template<class T>
  istream& operator>>(istream& is, T& obj) {
    /*
    * specific code for read obj
    */
    return is;
  }
  ```
  
- **Inseters**:(插入器)
  ostream:overload the << operator
  ```C++
  template<class T>
  ostream& operator<<(ostream& os,const T& obj ) {
    /*
    * specific code for read obj
    */
    return os;
  }
  ```

- **manipulators**:
  you can define your own manipulators
  ```C++
  ostream& tab(ostream& out) {
    return out<< '\t';
  }

  cout<<"Hello" << tab << "World!" << endl;
  ```
