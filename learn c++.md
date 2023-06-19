## 基础进阶

### const的作用
* 类型检查:
const常量与#define宏定义常量的区别：__const常量具有类型，编译器可以进行安全检查；#define宏定义没有数据类型，只是简单的字符串替换，不能进行安全检查。__

* 
### 指针

* 如果不想修改实参，就用值传递，如果想修改实参，就用地址传递

* 当数组名传入到函数作为参数时，被退化为指向首元素的指针

### 枚举类
* 限定作用域的枚举类
在enum后面加关键字class或者struct
```python
    enum class color
    {
    	RED,
    	GREEN,
    	BLUE
    };
```
* 解决枚举值重名的问题，保持代码的可读性
```python

//定义两种枚举
	enum class color_inner
	{
		RED,
		GREEN,
		BLUE
	};
 
	enum color_out
	{
		RED,
		GREEN,
		BLUE
	};
    //声明并赋值
    color_out backColor = RED; //正确
    color_inner forntColor = RED; //错误，默认使用了out中的RED，没有指定作用域
    color_out backColor = color_out::RED; //正确，out也可以显示指定作用域
    color_inner forntColor = color_inner::RED;  //正确，inner必须指定作用域
```
* 枚举类赋值
可以部分指定，未被初始化的枚举值的值默认将比其前面的枚举值大1
```python
	enum color
	{
		RED=2,  
		GREEN,  //默认值是3，比前一个多1
		BLUE=7  
	};
```
可以部分指定，未被初始化的枚举值的值默认将比其前面的枚举值大1
```python
	enum color
	{
		RED=2,  
		GREEN,  //默认值是3，比前一个多1
		BLUE=7  
	};
```
* 指定枚举类型
C++11中，还可以指定给枚举类型赋值的整数类型，在enum的名字后面加上冒号以及指定的类型，限定作用域枚举默认为32位整形，在某些情况下，甚至没必要用到32位，为了节省开销，甚至可以用8位整形unsigned char，将类型指定成后，枚举变量变成了8位整型，减少了内存使用。不限定作用域的枚举类型，其成员不存在默认类型，只需要知道潜在类型是足够大的，肯定能容纳枚举值就行。
需要注意的是，不能指定为float或者double等类型，因为枚举量必须是一个整数，float和double都不是整数。
```python
	enum color:unsigned long
	{
		RED=1,  
		GREEN=5, 
		BLUE=7  
	};
```