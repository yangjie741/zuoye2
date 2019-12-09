# 9.1
(a)list，因为可能需要在容器的中间位置插入元素

(b)deque，因为需要在头部进行元素的删除，deque效率更高

(c)vector，无具体的删除插入操作，未知数量，vector是个不错的选择。

# 9.25
相等：不发生删除操作

elem2为尾后迭代器：删除elem1到最后一个元素

皆为尾后迭代器：不发生删除操作

# 9.29
resize(100)会将其大小改为100个元素的大小，添加新元素并初始化，之后使用resize(10)会将之后的90个元素舍弃。

# 9.43

```

#include<iostream>
#include<fstream>
#include<sstream>
#include<string>
#include<vector>
#include<forward_list>
using namespace std;
 
void func(string &s, string &oldVal, string &newVal)
{
	int _size = oldVal.size();
	string::iterator it1 = s.begin();
	string::iterator it2 = newVal.begin();
	string::iterator it3 = newVal.end();
 
	 for (it1; it1 <= (s.end()-oldVal.size()+1); ++it1)
	{
		if((s.substr(it1-s.begin(),_size) == oldVal))
		{
			it1 = s.erase(it1,it1+_size);
			it1 = s.insert(it1, it2, it3);
			advance(it1,_size);
		}
	}
}
 
int main(int argc, char**argv)
{
	string s = "abcdefg";
	string oldval = "bc";
	string newval = "asas";
	func(s,oldval,newval);
	cout<<s<<endl;
	return 0;
}
```
```
#include<iostream>  
#include<fstream>  
#include<sstream>  
#include<string>  
#include<vector>  
#include<forward_list>  
using namespace std;  
 
void func(string &s, string &oldVal, string &newVal)  
{  
	int _size = oldVal.size(); 
	int _size1 = newVal.size();
	string::iterator it1 = s.begin();  
	string::iterator it2 = newVal.begin();  
	string::iterator it3 = newVal.end();  
 
	for (it1; it1 <= (s.end()-oldVal.size()+1); ++it1)  
	{   
		if((s.substr(it1-s.begin(),_size) == oldVal))
		{  
			it1 = s.erase(it1,it1+_size);
			s.insert(it1, it2,it3);
			//test code
			/*cout<<(it1-s.begin())<<endl;
			cout<<s<<endl;*/
			advance(it1,_size1-1);
		}  
	}  
}  
 
int main(int argc, char**argv)  
{  
	string s = "abcdefg";  
	string oldval = "bc";  
	string newval = "asas";  
	func(s,oldval,newval);  
	cout<<s<<endl;  
	system("pause");
	return 0;  
}
```

# 10.3
```
#include<iostream>
#include<string>
#include<vector>
#include<algorithm>
#include<numeric>
using namespace std;
 
int main(int argc, char**argv)
{
	int a[10] = {0,1,2,5,4,5,4,5,4,5};
	vector<int> vec(a,a+10);
	cout<<"元素之和为："<<accumulate(vec.begin(),vec.end(),0);
 
	return 0;
}
```

# 10.15
```
[a](int &b){cout<<a+b;}
```

# 10.34
```
#include<vector>  
#include<algorithm>  
#include<numeric>  
#include<functional>
#include<iterator>
using namespace std;
using namespace placeholders;
 
int main(int argc, char**argv)  
{  
	int a[5] = {1,2,3,4,5};
	vector<int> day1(a,a+5);
 
	for (auto it1 = day1.rbegin(); it1 != day1.rend() ; ++it1)
	{
		cout<<*it1<<" ";
	}
 
	return 0;  
}
```
# 10.42
```

#include<iostream>  
#include<fstream>
#include<string>  
#include<vector> 
#include<list>
#include<algorithm>  
#include<numeric>  
#include<functional>
#include<iterator>
using namespace std;
using namespace placeholders;
 
int main(int argc, char**argv)  
{ 
	string a[10] = {"sdc","sddc","sdec","sfdc","sdec","sdc","sdc","fsdc","sadc","fsdc"};
	list<string> list1(a,a+10);
	list1.sort();
	list1.unique();
	for (auto it1 = list1.begin(); it1 != list1.end(); ++it1)
	{
		cout<<*it1<<" ";
	}
 
	return 0;  
} 
```
# 11.12
```

#include<iostream>  
#include<string>  
#include<fstream>
#include<list>
#include<vector> 
#include<map>  
#include<set>
#include<cctype>//ctype无法打开，包含tolower()函数和ispunct函数
#include<algorithm>
#include<utility>
using namespace std;
 
int main(int argc, char**argv)  
{ 
	vector<pair<string,int>> vec1(12);
	ifstream in1("1.txt");
	string str;
	size_t i = 0;
	while (in1>>str)
	{
		vec1[i].first = str;
		++i;
	}
	ifstream in2("2.txt");
	int val;
	size_t j = 0;
	while (in2>>val)
	{
		vec1[j].second = val;
		++j;
	}
 
	vector<pair<string,int>>::iterator it1 = vec1.begin();
	cout<<"vector中元素为："<<endl;
	for (it1; it1 != vec1.end(); ++it1)
	{
		cout<<it1->first<<" "<<it1->second<<endl;
	}
 
	return 0;  
} 
```

# 11.17

back_inserter()需要使用push_back()，而set不能够使用push_back()

# 11.38

没有任何变化的，用这个无序容器是不影响操作的

# 13.12

析构函数执行三次：accum，item1，item2

# 13.18
```

#include<iostream>  
#include<string>  
#include<fstream>
#include<list>
#include<vector> 
#include<map>  
#include<set>
#include<cctype>
#include<algorithm>
#include<utility>
#include<memory>
using namespace std;
 
class Employee
{
public:
	Employee();
	Employee(string& s);
	Employee(const Employee&) =delete;
	Employee& operator= (const Employee&) =delete;
	int number(){return _number;}
private:
	string employee;
	int _number;
	static int O_number
};
 
int Employee::O_number = 0;
Employee::Employee()//默认构造函数
{
	_number = O_number++;
}
Employee::Employee(string& s)//接受一个string的构造函数
{
	employee = s;
	_number = O_number++;
}
 
void show(Employee a)
{
	cout<<a.number()<<endl;
}
int main(int argc, char**argv)  
{
	Employee a, b, c;
	show(a);//调用函数时需要拷贝一次
	show(b);
	show(c);
 
	return 0;
}
```

# 13.46

(a)：f()为函数的返回值，临时值，属于右值，&&

(b)：vi[0]为变量，属于左值，&

(c)：r1为变量，属于左值，&

(d)：右侧为表达式，属于右值，&&

# 13.49
```

String& String::operator=(String&& rhs) NOEXCEPT
{
	if (this != &rhs) {
		free();
		elements = rhs.elements;
		end = rhs.end;
		rhs.elements = rhs.end = nullptr;//将源对象置为可析构的状态
	}
	return *this;
}
String::String(String&& s) NOEXCEPT : elements(s.elements), end(s.end)
{
	s.elements = s.end = nullptr;//将源对象置为可析构的状态
}
```

# 13.58
```

#include <vector>
#include <iostream>
#include <algorithm>
 
using std::vector;
using std::sort;
 
class Foo {
public:
	Foo sorted()&&;
	Foo sorted() const&;
 
private:
	vector<int> data;
};
 
Foo Foo::sorted() &&
{
	sort(data.begin(), data.end());
	std::cout << "&&" << std::endl; // debug
	return *this;
}
 
Foo Foo::sorted() const &
{
	//    Foo ret(*this);
	//    sort(ret.data.begin(), ret.data.end());
	//    return ret;
 
	std::cout << "const &" << std::endl; // debug
 
	//    Foo ret(*this);
	//    ret.sorted();     //13.56
	//    return ret;
 
	return Foo(*this).sorted(); //13.57
}
 
int main()
{
	Foo().sorted(); // call "&&"
	Foo f;
	f.sorted(); // call "const &"
}
```

# 14.3
(a) "cobble" == "stone"     (b) svec1[0] ==svec2[0]     (c)svec1 ==svec2     (d) svec[0] == "stone"

(a)应用了C++内置版本的==，比较两个指针。(b) 应用了string版本的==。(c)应用了vector版本的==。(d)应用了string版本的==。

# 14.25
```
class Date
{
public:
	Date& operator=(const string &date);
	//其他成员
};
Date& Sales_data::operator=(const string &date)
{
	istringstream in(date);
	char ch1, cha2;
	in >> year >> ch1 >> month >> ch2 >> day;
	if (!in || ch1 != '-' || ch2 != '-')
		throw std::invalid_argument("Bad date");
	if (month < 1 || month >12 || day < 1 || day > 31)
		throw std::invalid_argument("Bad date");
	return *this;
}
```

# 14.38
```
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
using std::istream;
using std::cout;
using std::cin;
using std::endl;
using std::vector;
using std::string;
 
class StrLenIs
{
public:
	StrLenIs(int len) : len(len) { }
	bool operator()(const string &str) { return str.length() == len; }
 
private:
	int len;
};
 
void readStr(istream &is, vector<string> &vec)
{
	string word;
	while (is >> word)
	{
		vec.push_back(word);
	}
}
 
int main()
{
	vector<string> vec;
	readStr(cin, vec);
	const int minLen = 1;
	const int maxLen = 10;
	for (int i = minLen; i <= maxLen; ++i)
	{
		StrLenIs slenIs(i);
		cout << "len: " << i << ", cnt: " << count_if(vec.begin(), vec.end(), slenIs) << endl;
	}
 
	return 0;
}
```
# 14.52
对于ld=si+ld，由于LongDouble不能转换为SmallInt，因此Smallint的成员operator+和friend operator都不可行。
由于Smallint不能转换为LongDouble，LongDouble的成员operator+和非成员operator+也都不可行。

由于SmallInt可以转换为int， LongDouble了可以转换为float和double，所以内置的operator+(int, float)和operator+(int, double)都可行，会产生二义性。

对于ld=ld+si，类似上一个加法表达式，由于Smallint不能转换为double，LongDouble也不能转换为SmallInt，因此SmallInt的成员operator+和两个非成员operator+都不匹配。

LongDouble的成员operator+可行，且为精确匹配。
SmallInt可以转换为int，longDouble可以转换为float和double，因此内置的operator+(float, int)和operator(double, int)都可行。但它们都需要类型转换，因此LongDouble的成员operator+优先匹配。


# 15.12
需要，override是表示对其基类函数的覆盖，final是表示此函数不能再被其他的函数所覆盖

# 15.16
```

class limit_quote : public Disc_quote
{
public:
	limit_quote();//默认构造函数
	limit_quote(const string&book, double price, size_t qty,double disc):Disc_quote(book,price,qty,disc){}//构造函数,直接调用基类的构造函数
	double net_price(size_t n) const
	{
		if (n > quantity)
		{
			return quantity*(1-_discount)*price+(n-quantity)*price;
		} 
		else
		{
			return quantity*(1-_discount)*price;
		}
	}
};
```

# 15.30
Basket.h
```

class Basket  
{  
    static bool compare(const std::shared_ptr<Quote> rhs, const std::shared_ptr<Quote> lhs) {  
        return rhs->isbn() < lhs->isbn();  
    }  //自定义compare
    std::multiset<std::shared_ptr<Quote>, decltype(compare)*> items{ compare }; //头文件set
public:  
    void add_item(const std::shared_ptr<Quote> &sale) {  
        items.insert(sale);  
    }  
    void add_item(const Quote &q)  
    {  
        items.insert(std::shared_ptr<Quote>(q.clone()));  
    }  
    void add_item(Quote &&q)  
    {  
        items.insert(std::shared_ptr<Quote>(std::move(q).clone()));  
    }  
    double total_receipt(std::ostream &os)const;  
}; 
```
Basket.cpp
```

double Basket::total_receipt(std::ostream &os)const  
{  
    double sum = 0.0;                                        
    for (auto iter = items.cbegin(); iter != items.cend(); iter = items.upper_bound(*iter))  
    {  
        sum += print_total(os, **iter, items.count(*iter)); 
    }  
    os << "Total Sale: " << sum << std::endl;  
    return sum;  
}
```
