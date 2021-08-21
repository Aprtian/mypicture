# javaSE进阶

## 1.抽象类

### 1.1抽象类概念理解和抽象方法

![image-20210316183652838](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/W9jaXVxPupA3Z4t.png)

**抽象类：**

> 1.什么是抽象类：类和类之间具有共同特征，将这些共同特征提取出来，形成的就是抽象类。类本身是不存在的，所以抽象类无法创建对象。
>
> 2.抽象类属于什么数据类型：抽象类属于引用数据类型。
>
> 3.抽象类怎么定义：
>
> ​		语法：
>
> ​					【修饰符列表】 abstract class 类名{
>
> ​								类体;
>
> }
>
> 4.抽象类是无法实例化的，无法创建对象的，所以抽象类是用来继承的。
>
> 5. final和abstract不能联名使用，这两个关键字是对立的。
>
> 6.抽象类的子类是可以是抽象类。也可以不是抽象类。
>
> 7.抽象类虽然无法实例化，但是抽象类有构造方法，这个构造方法是提供子类使用的。
>
> 8.抽象方法关联到一个概念：抽象方法。什么是抽象方法：抽象方法表示没有实现的方法，没有方法体的方法。
>
> 例如：public static void main();
>
> ​			抽象方法的特点是：1.没有方法体，以分号结尾。
>
> ​							2.前面修饰符没有abstract关键字。
>
> 9.抽象类中不一定有抽象方法，抽象方法必须出现在抽象类中。

``` java
public class AbstractTest{
    public static void main(String[] args)
    {}
}

abstract class Account{
    //构造方法
    public Account(){
         }
    //方法重载
    public Account(String[]){
   }     
}
class CreditAccount extends Account{
    public CreditAccount(){
        super();//抽象方法
    }
}
```

### 1.2非抽象类继承抽象类必须将抽象方法实现

> **1.抽象类中不一定有抽象方法，抽象方法必须出现在抽象类中。**
>
> **2.重要结论：一个非抽象的类继承抽象类，必须将抽象类中的抽象方法实现了。这是java语法上强行规定的，必须的，不然编译器会报错。**
>
> **这里的覆盖或者说重写，也可以叫做实现。**
>
> **面试题：java 语言中凡是没有方法体的方法都是抽象方法？**
>
> **解释：不对，是错误的。object类中就有很多方法都是没有方法体的，都是“；”结尾的，但是他们都不是抽象方法，例如：public native int hashCode();**
>
> **这个方法底层调用了c++写的动态链接程序。前面修饰符列表中没有：abstract,有一个native。表示java本地程序。**

``` java
//例题：
/**
这就是面向抽象编程。
调用的都是a.xxx
a的类型就是抽象编程，不要面向具体编程，降低程序的耦合度，提高程序的扩展里。
编程思想是符合oop原则的。
*/

public class AbstractTest{
    public static void main(String[] args){
        Animal a =new Bird();
    a.move;
}
}
abstract class Animal{
    public abstract void move();
}
//非抽象类继承抽象类
class Bird extends Animal{
    public void move()//这个是必须写的不然会报错
    {
        Systen.out.println("鸟儿在飞翔");//必须写的
    }
}
//如果是BIrd是抽象类的话，并未覆盖Animal中的抽像方法move()
abstract class Bird extends Animal{
    
}
```

## 2.接口

### 2.1接口的基础语法

>接口：
>
>1.接口是一种引用数据类型。
>
>2.接口是完全抽象的。（抽象是半抽象的。）或者可以说接口是特殊类。
>
>3.接口怎么去定义，语法是什么？
>
>【修饰符列表】 interface 接口名{}
>
>4.接口支持多继承，一个接口可以继承多个接口。
>
>5.接口只包含两部分内容，一部分是：常量。另一部分是：抽象方法。接口中没有其他内容了，只有以上两部分内容。
>
>6.接口中的所有方法都是public修饰的。（都是公开的）。
>
>7.接口中的方法定义时:public abstract修饰符可以省略。
>
>8.接口中的方法都是抽象方法，所以接口的方法不能有方法体。public static final可以省略。

### 2.2 类实现接口要实现所有方法

> 1.接口的基础语法：类和类之间叫做继承，类和接口之间叫做实现。（继承）
>
> 继承使用extends关键字完成。
>
> 实现使用implements关键字完成。
>
> **2.当一个非抽象的类实现接口的话，必须将接口中所有的抽象方法全部实现（覆盖，重写）。**public 不能丢掉。

### 2.3 接口和多态联合使用

![image-20210317222629154](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/image-20210317222629154.png)

![image-20210317222646882](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/image-20210317222646882.png)

### 2.4 一个类可以实现多个接口

> 一个类可以同时实现多个接口
>
> 接口和接口之间支持多继承，那么一个类可以同时实现多个接口吗？
>
> 		对于计算机来说，一个机箱上有多个接口，一个接口是接键盘的，
> 		一个接口是接鼠标的，一个接口是接电源的，一个接口是接显示器的.....
> 		重点（五颗星*****）：一个类可以同时实现多个接口。
> 																																														
> 	这种机制弥补了java中的哪个缺陷？
> 		java中类和类只支持单继承。实际上单继承是为了简单而出现的，现实世界中
> 		存在多继承，java中的接口弥补了单继承带来的缺陷。
> 																																														
> 	接口A和接口B虽然没有继承关系，但是写代码的时候，可以互转。
> 	编译器没意见。但是运行时可能出现：ClassCastException
> 																																														
> 	之前有一个结论：
> 		无论向上转型还是向下转型，两种类型之间必须要有继承关系，
> 		没有继承关系编译器会报错。（这句话不适用在接口方面。）
> 		最终实际上和之前还是一样，需要加：instanceof运算符进行判断。
> 		向下转型养成好习惯。转型之前先if+instanceof进行判断。

![image-20210317224117522](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/image-20210317224117522.png)

``` java
public class Test03{
	public static void main(String[] args){
		// 多态该怎么用呢？
		// 都是父类型引用指向子类型对象
		A a = new D();
		//a.m2(); // 编译报错。A接口中没有m2()方法。
		B b = new D();
		C c = new D();

		// 这个编译没问题，运行也没问题。
		// 调用其他接口中的方法，你需要转型（接口转型。）
		B b2 = (B)a;
		b2.m2();

		// 直接向下转型为D可以吗？可以
		D d = (D)a;
		d.m2();

		M m = new E();
		// 经过测试：接口和接口之间在进行强制类型转换的时候，没有继承关系，也可以强转。
		// 但是一定要注意，运行时可能会出现ClassCastException异常。
		// 编译没问题，运行有问题。
		//K k = (K)m;
		if(m instanceof K){
			K k = (K)m;
		}
	}
}

interface K{
}

interface M{
}

class E implements M{
}

// --------------------------------------------------------------------

interface X{
}
interface Y{
}
interface Z extends X,Y{ //接口和接口支持多继承。
}

//------------------------------------------------------------------

interface A{
	void m1();
}

interface B{
	void m2();
}

interface C{
	void m3();
}

// 实现多个接口，其实就类似于多继承。
class D implements A,B,C{
	// 实现A接口的m1()
	public void m1(){
		
	}
	// 实现B接口中的m2()
	public void m2(){
		System.out.println("m2 ....");
	}
	// 实现接口C中的m3()
	public void m3(){
	
	}
}
```

### 2.5 extends和implement同时出现

``` java
/*
	继承和实现都存在的话，代码应该怎么写？
		extends 关键字在前。
		implements 关键字在后。
*/
public class Test04{
	public static void main(String[] args){
		// 创建对象（表面看Animal类没起作用！）
		Flyable f = new Cat(); //多态。
		f.fly();

		// 同一个接口
		Flyable f2 = new Pig();
		// 调用同一个fly()方法，最后的执行效果不同。
		f2.fly();

		Flyable f3 = new Fish();
		f3.fly();
	}
}

// 动物类：父类
class Animal{
}

// 可飞翔的接口（是一对翅膀）
// 能插拔的就是接口。（没有接口你怎么插拔。）
// 内存条插到主板上，他们之间有接口。内存条可以更换。
// 接口通常提取的是行为动作。
interface Flyable{
	void fly();
}

// 动物类子类：猫类
// Flyable是一个接口，是一对翅膀的接口，通过接口插到猫身上，让猫变的可以飞翔。
class Cat extends Animal implements Flyable{
	public void fly(){
		System.out.println("飞猫起飞，翱翔太空的一只猫，很神奇，我想做一只猫！！");
	}
}

// 蛇类，如果你不想让它飞，可以不实现Flyable接口
// 没有实现这个接口表示你没有翅膀，没有给你插翅膀，你肯定不能飞。
class Snake extends Animal{
}

// 想飞就插翅膀这个接口。
class Pig extends Animal implements Flyable{
	public void fly(){
		System.out.println("我是一只会飞的猪！！！");
	}
}

// 鱼（默认实际上是存在继承的，默认继承Object。）
/*
class Fish extends Object implements Flyable{
}
*/
class Fish implements Flyable{ //没写extends，也是有的，默认继承Object。
	public void fly(){
		System.out.println("我是六眼飞鱼（流言蜚语）！！！");
	}
}
```

### 2.6接口在开发中的作用

``` java
//西餐厨师
// 实现菜单上的菜
// 厨师是接口的实现者。
public class AmericCooker implements FoodMenu{

	// 西红柿炒蛋
	public void shiZiChaoJiDan(){
		System.out.println("西餐师傅做的西红柿炒鸡蛋！");
	}

	// 鱼香肉丝
	public void yuXiangRouSi(){
		System.out.println("西餐师傅做的鱼香肉丝！");
	}
}

//中餐厨师
// 实现菜单上的菜
// 厨师是接口的实现者。
public class ChinaCooker implements FoodMenu{

	// 西红柿炒蛋
	public void shiZiChaoJiDan(){
		System.out.println("中餐师傅做的西红柿炒鸡蛋，东北口味！");
	}

	// 鱼香肉丝
	public void yuXiangRouSi(){
		System.out.println("中餐师傅做的鱼香肉丝，东北口味！");
	}
}

// 顾客
public class Customer{
	// 顾客手里有一个菜单
	// Customer has a FoodMenu!（这句话什么意思：顾客有一个菜单）
	// 记住：以后凡是能够使用 has a 来描述的，统一以属性的方式存在。
	// 实例变量，属性
	// 面向抽象编程，面向接口编程。降低程序的耦合度，提高程序的扩展力。
	private FoodMenu foodMenu; 
	
	// 如果以下这样写，就表示写死了（焊接了。没有可插拔了。）
	// 中餐厨师
	//ChinaCooker cc;

	// 西餐厨师
	//AmericCooker ac

	// 构造方法
	public Customer(){
	}
	public Customer(FoodMenu foodMenu){
		this.foodMenu = foodMenu;
	}

	// setter and getter
	public void setFoodMenu(FoodMenu foodMenu){
		this.foodMenu = foodMenu;
	}
	public FoodMenu getFoodMenu(){
		return foodMenu;
	}

	// 提供一个点菜的方法
	public void order(){
		// 先拿到菜单才能点菜
		// 调用get方法拿菜单。
		//FoodMenu fm = this.getFoodMenu();
		// 也可以不调用get方法，因为在本类中私有的属性是可以访问
		foodMenu.shiZiChaoJiDan();
		foodMenu.yuXiangRouSi();
	}
}

/*
	Cat is a Animal，但凡满足is a的表示都可以设置为继承。
	Customer has a FoodMenu，但凡是满足has a的表示都以属性的形式存在。
*/

/*
class Address{
	String city;
	String street;
	String zipcode;
}

class User{
	int id;

	// 和这个一样。
	// String是一个类。
	// name是变量名。
	// name是一个引用。
	String name;

	// Address是一个类名。
	// 这就是一个变量。
	// 实例变量。
	Address addr; // addr是一个引用。是一个变量。

	public static void main(String[] args){
		// 局部变量
		//Address addr;
		//addr = new Address();

		// 合并。
		Address addr = new Address();

		User u = new User();
		u.id = 100;
		u.name = "zhangsan";
		u.addr = new Address();

		System.out.println(u.addr.city); // null
		System.out.println(u.addr.street); // null
		System.out.println(u.addr.zipcode); // null
	}
}

//“自己”类
// MySelf has a Friend;
class MySelf{
	// 你这个对象，应该有一个朋友对象的电话号码。
	// 电话号码就是一个对象的内存地址。联系你朋友的时候，打电话。
	// f是一个引用。f默认值是null，是null表示，你没有朋友。
	Friend f;

	public MySelf(){
	
	}
	//通过构造方法能不能给你一个朋友对象。
	public MySelf(Friend f){
		this.f = f;
	}

	public static void main(String[] args){
		// 创建朋友对象
		Friend f = new Friend(); //朋友对象有了

		// 创建对象的同时交朋友。
		MySelf m2 = new MySelf(f);


		// 创建自己对象
		// 目前还没有交朋友。
		MySelf m = new MySelf(); //自己对象
		// 交朋友
		m.f = f; // 把朋友的地址给了你。
	}
}

// “朋友”类
class Friend{

}

*/

/*
	接口：菜单，抽象的
*/
public interface FoodMenu{

	// 西红柿炒蛋
	void shiZiChaoJiDan();

	// 鱼香肉丝
	void yuXiangRouSi();

}

public class Test{
	public static void main(String[] args){

		// 创建厨师对象
		//FoodMenu cooker1 = new ChinaCooker();
		FoodMenu cooker1 = new AmericCooker();

		// 创建顾客对象
		Customer customer = new Customer(cooker1);

		// 顾客点菜
		customer.order();
	}
}
```

## 3.类与类之间的关系

> is a（继承）、has a（关联）、like a（实现）
>
> 		is a：
> 			Cat is a Animal（猫是一个动物）
> 			凡是能够满足is a的表示“继承关系”
> 			A extends B
> 																																														
> 		has a：
> 			I has a Pen（我有一支笔）
> 			凡是能够满足has a关系的表示“关联关系”
> 			关联关系通常以“属性”的形式存在。
> 			A{
> 				B b;
> 			}
> 																																															
> 		like a:
> 			Cooker like a FoodMenu（厨师像一个菜单一样）
> 			凡是能够满足like a关系的表示“实现关系”
> 			实现关系通常是：类实现接口。
> 			A implements B

## 4. 访问控制权限

``` java
package com.bjpowernode;

public class Test01{

	public static void main(String[] args){
		User user = new User();

		// private修饰的元素只能在本类中用。
		//System.out.println(user.id);
		System.out.println(user.age);
		System.out.println(user.weight);
		System.out.println(user.name);
	}
}

package com.bjpowernode2; // 包变化了。

//import com.bjpowernode.*;
import com.bjpowernode.User;

public class Test02{
	public static void main(String[] args){

		User user = new User();

		// 错误：protected在这里不行。
		//System.out.println(user.age);

		// 可以：公开的，在哪都行。
		System.out.println(user.weight);

		// 错误：“默认”在这里也不行。
		//System.out.println(user.name);

	}
}

package com.bjpowernode;

public class User{
	//给一些属性
	// 私有的
	private int id;
	// 受保护的
	protected int age;
	// 公开的
	public int weight;
	// 默认的
	String name;

	// 方法
	public void m1(){}
	private void m2(){}
	void m3(){}
	protected void m4(){}

	// 静态方法也可以。
	public static void x(){}
	private static void y(){}
	static void z(){}
	protected static void k(){}
}

//错误: 此处不允许使用修饰符private
/*
private class MyClass1{
}
*/

//错误: 此处不允许使用修饰符protected
/*
protected class MyClass1{
}
*/

class MyClass1{

}

package com.bjpowernode3; // 包变化了。

// 导入
import com.bjpowernode.User;

// User在com.bjpowernode包下。
// Vip在com.bjpowernode3包下。
// User和Vip不在同一个包下。
// 但是Vip是User的子类。
public class Vip extends User{

	//实例方法
	public void shopping(){
		// this表示当前对象
		// protected可以
		System.out.println(this.age);
		// 错误：默认 不行。
		//System.out.println(this.name);
	}

}
```

## 5. object类

### 5.1 tostring方法

``` java
/*
	关于Object类中的toString()方法

		1、源代码长什么样？
			public String toString() {
				return this.getClass().getName() + "@" + Integer.toHexString(hashCode());
			}
			源代码上toString()方法的默认实现是：
				类名@对象的内存地址转换为十六进制的形式

		2、SUN公司设计toString()方法的目的是什么？
			toString()方法的作用是什么？
				toString()方法的设计目的是：通过调用这个方法可以将一个“java对象”转换成“字符串表示形式”

		3、其实SUN公司开发java语言的时候，建议所有的子类都去重写toString()方法。
		toString()方法应该是一个简洁的、详实的、易阅读的.
*/
public class Test01{
	public static void main(String[] args){
		MyTime t1 = new MyTime(1970, 1, 1);
		// 一个日期对象转换成字符串形式的话，我可能还是希望能看到具体的日期信息。
		String s1 = t1.toString();

		//MyTime类重写toString()方法之前
		//System.out.println(s1); // MyTime@28a418fc
		
		//MyTime类重写toString()方法之后
		System.out.println(s1); // 1970年1月1日

		
		//System.out.println(t1.toString()); //1970年1月1日

		// 注意：输出引用的时候，会自动调用该引用的toString()方法。
		System.out.println(t1);
	}
}
class MyTime{
	int year;
	int month;
	int day;

	public MyTime(){
	
	}

	public MyTime(int year, int month, int day){
		this.year = year;
		this.month = month;
		this.day = day;
	}

	// 重写toString()方法
	// 这个toString()方法怎么重写呢？
	// 越简洁越好，可读性越强越好。
	// 向简洁的、详实的、易阅读的方向发展
	public String toString(){
		//return this.year + "年" + this.month + "月" + this.day + "日";
		return this.year + "/" + this.month + "/" + this.day;
	}
}
```

### 5.2 equals方法

``` java
/*
	关于Object类中的equals方法
		1、equals方法的源代码
			public boolean equals(Object obj) {
				return (this == obj);
			}
			以上这个方法是Object类的默认实现。
				
		
		2、SUN公司设计equals方法的目的是什么？
			以后编程的过程当中，都要通过equals方法来判断两个对象是否相等。
			equals方法是判断两个对象是否相等的。
		
		3、我们需要研究一下Object类给的这个默认的equals方法够不够用！！！！
				在Object类中的equals方法当中，默认采用的是“==”判断两个java对象
				是否相等。而“==”判断的是两个java对象的内存地址，我们应该判断
				两个java对象的内容是否相等。所以老祖宗的equals方法不够用，
				需要子类重写equals。
		
		4、判断两个java对象是否相等，不能使用“==”，因为“==”比较的是两个
		对象的内存地址。
*/
public class Test02{
	public static void main(String[] args){

		// 判断两个基本数据类型的数据是否相等直接使用“==”就行。
		int a = 100;
		int b = 100;
		// 这个“==”是判断a中保存的100和b中保存的100是否相等。
		System.out.println(a == b); //true（相等） false(不相等)

		// 判断两个java对象是否相等，我们怎么办？能直接使用“==”吗？
		// 创建一个日期对象是：2008年8月8日。
		MyTime t1 = new MyTime(2008, 8, 8); //MyTime t1 = 0x1234;
		// 创建了一个新的日期对象，但表示的日期也是：2008年8月8日。
		MyTime t2 = new MyTime(2008, 8, 8); //MyTime t2 = 0x3698;
		
		//测试以下，比较两个对象是否相等，能不能使用“==”？？？
		// 这里的“==”判断的是：t1中保存的对象内存地址和t2中保存的对象内存地址是否相等。
		System.out.println(t1 == t2); // false
		
		// 重写Object equals方法之前（比较的是对象内存地址）
		/*
		boolean flag = t1.equals(t2);
		System.out.println(flag); //false
		*/
		

		// 重写Object equals方法之后（比较的是内容。）
		boolean flag = t1.equals(t2);
		System.out.println(flag); //true

		// 再创建一个新的日期
		MyTime t3 = new MyTime(2008, 8, 9);
		// 两个日期不相等，就是false。
		System.out.println(t1.equals(t3)); // false

		// 我们这个程序有bug吗？可以运行，但是效率怎么样？低（怎么改造。）
		MyTime t4 = null;
		System.out.println(t1.equals(t4)); //false
	}
}

class MyTime { //extends Object{
	int year;
	int month;
	int day;

	public MyTime(){
	
	}
	public MyTime(int year, int month, int day){
		this.year = year;
		this.month = month;
		this.day = day;
	}

	// 默认的equals方法
	/*
	public boolean equals(Object obj) {
		return (this == obj);
	}
	*/

	/*
	// 重写Object类的equals方法
	// 怎么重写？复制粘贴。相同的返回值类型、相同的方法名、相同的形式参数列表。
	// equals到底应该怎么重写？你自己定，你认为两个对象什么相等的时候表示相等，你就怎么重写。
	public boolean equals(Object obj) {
		// 当年相同，月相同，并且日也相同的时候，表示两个日期相同。两个对象相等。
		// 获取第一个日期的年月日
		int year1 = this.year;
		int month1 = this.month;
		int day1 = this.day;

		// 获取第二个日期的年月日
		//int year2 = obj.year;
		//int month2 = obj.month;
		//int day2 = obj.day;

		if(obj instanceof MyTime){
			MyTime t = (MyTime)obj;
			int year2 = t.year;
			int month2 = t.month;
			int day2 = t.day;
			if(year1 == year2 && month1 == month2 && day1 == day2){
				return true;
			}
		}
		// 程序能够执行到此处表示日期不相等。
		return false;
	}
	*/

	/*
	// 改良equals方法
	public boolean equals(Object obj) {
		// 如果obj是空，直接返回false
		if(obj == null){
			return false;
		}
		// 如果obj不是一个MyTime，没必要比较了 ，直接返回false
		if(!(obj instanceof MyTime)){
			return false;
		}
		// 如果this和obj保存的内存地址相同，没必要比较了，直接返回true。
		// 内存地址相同的时候指向的堆内存的对象肯定是同一个。
		if(this == obj){
			return true;
		}
		// 程序能够执行到此处说明什么？
		// 说明obj不是null，obj是MyTime类型。
		MyTime t = (MyTime)obj;
		if(this.year == t.year && this.month == t.month && this.day == t.day){
			return true;
		}

		// 程序能到这里返回false
		return false;
	}
	*/

	
	//再次改良。
	/*
	public boolean equals(Object obj) {
		// 如果obj是空，直接返回false
		if(obj == null){
			return false;
		}
		// 如果obj不是一个MyTime，没必要比较了 ，直接返回false
		if(!(obj instanceof MyTime)){
			return false;
		}
		// 如果this和obj保存的内存地址相同，没必要比较了，直接返回true。
		// 内存地址相同的时候指向的堆内存的对象肯定是同一个。
		if(this == obj){
			return true;
		}
		// 程序能够执行到此处说明什么？
		// 说明obj不是null，obj是MyTime类型。
		MyTime t = (MyTime)obj;
		return this.year == t.year && this.month == t.month && this.day == t.day ;
	}
	*/

	public boolean equals(Object obj) {
		if(obj == null || !(obj instanceof MyTime)){
			return false;
		}
		if(this == obj){
			return true;
		}
		MyTime t = (MyTime)obj;
		return this.year == t.year && this.month == t.month && this.day == t.day ;
	}

}

/*
class Person{
	private String idCard;
}
*/


```

### 5.3 string类重写了toString和equals

``` java

/*
	java语言当中的字符串String有没有重写toString方法，有没有重写equals方法。

	总结：
		1、String类已经重写了equals方法，比较两个字符串不能使用==，必须使用equals。
		equals是通用的。

		2、String类已经重写了toString方法。
	
	大结论：
		java中什么类型的数据可以使用“==”判断
			java中基本数据类型比较是否相等，使用==

		java中什么类型的数据需要使用equals判断
			java中所有的引用数据类型统一使用equals方法来判断是否相等。
		
		这是规矩。
*/
public class Test03{
	public static void main(String[] args){

		// 大部分情况下，采用这样的方式创建字符串对象
		String s1 = "hello";
		String s2 = "abc";

		// 实际上String也是一个类。不属于基本数据类型。
		// 既然String是一个类，那么一定存在构造方法。
		String s3 = new String("Test1");
		String s4 = new String("Test1");
		// new两次，两个对象内存地址，s3保存的内存地址和s4保存的内存地址不同。
		// == 判断的是内存地址。不是内容。
		System.out.println(s3 == s4); // false

		// 比较两个字符串能不能使用双等号？
		// 不能，必须调用equals方法。
		// String类已经重写equals方法了。
		System.out.println(s3.equals(s4)); // true

		// String类有没有重写toString方法呢？
		String x = new String("动力节点");
		// 如果String没有重写toString()方法，输出结果：java.lang.String@十六进制的地址
		// 经过测试：String类已经重写了toString()方法。
		System.out.println(x.toString()); //动力节点
		System.out.println(x); //动力节点
	}
}
```

### 5.4重写Object类的equals方法

``` java

// String对象比较的时候必须使用equals方法。
public class Test04{
	public static void main(String[] args){
		/*
		Student s1 = new Student(111, "北京大兴亦庄二小");
		Student s2 = new Student(111, "北京大兴亦庄二小");
		System.out.println(s1 == s2); // false
		System.out.println(s1.equals(s2)); // true
		*/

		Student s1 = new Student(111, new String("北京大兴亦庄二小"));
		Student s2 = new Student(111, new String("北京大兴亦庄二小"));
		System.out.println(s1 == s2); // false
		System.out.println(s1.equals(s2)); // true
	}
}

class Student{
	// 学号
	int no; //基本数据类型，比较时使用：==
	// 所在学校
	String school; //引用数据类型，比较时使用：equals方法。

	public Student(){}
	public Student(int no,String school){
		this.no = no;
		this.school = school;
	}

	// 重写toString方法
	public String toString(){
		return "学号" + no + "，所在学校名称" + school;
	}

	// 重写equals方法
	// 需求：当一个学生的学号相等，并且学校相同时，表示同一个学生。
	// 思考：这个equals该怎么重写呢？
	// equals方法的编写模式都是固定的。架子差不多。
	public boolean equals(Object obj){
		if(obj == null || !(obj instanceof Student)) return false;
		if(this == obj) return true;
		Student s = (Student)obj;
		return this.no == s.no && this.school.equals(s.school);

		//字符串用双等号比较可以吗？
		// 不可以
		//return this.no == s.no && this.school == s.school;
	}
}

```

### 5.5 equals深层次理解和equals深层次的剖析

``` java

// String对象比较的时候必须使用equals方法。
public class Test04{
	public static void main(String[] args){
		/*
		Student s1 = new Student(111, "北京大兴亦庄二小");
		Student s2 = new Student(111, "北京大兴亦庄二小");
		System.out.println(s1 == s2); // false
		System.out.println(s1.equals(s2)); // true
		*/

		Student s1 = new Student(111, new String("北京大兴亦庄二小"));
		Student s2 = new Student(111, new String("北京大兴亦庄二小"));
		System.out.println(s1 == s2); // false
		System.out.println(s1.equals(s2)); // true
	}
}

class Student{
	// 学号
	int no; //基本数据类型，比较时使用：==
	// 所在学校
	String school; //引用数据类型，比较时使用：equals方法。

	public Student(){}
	public Student(int no,String school){
		this.no = no;
		this.school = school;
	}

	// 重写toString方法
	public String toString(){
		return "学号" + no + "，所在学校名称" + school;
	}

	// 重写equals方法
	// 需求：当一个学生的学号相等，并且学校相同时，表示同一个学生。
	// 思考：这个equals该怎么重写呢？
	// equals方法的编写模式都是固定的。架子差不多。
	public boolean equals(Object obj){
		if(obj == null || !(obj instanceof Student)) return false;
		if(this == obj) return true;
		Student s = (Student)obj;
		return this.no == s.no && this.school.equals(s.school);

		//字符串用双等号比较可以吗？
		// 不可以
		//return this.no == s.no && this.school == s.school;
	}
}

```

### 5.6 object的finalize方法

``` java
/*
	关于Object类中的finalize()方法。（非重点  非重点  非重点  了解即可。）

		1、在Object类中的源代码：
			protected void finalize() throws Throwable { }

			GC：负责调用finalize()方法。

		2、finalize()方法只有一个方法体，里面没有代码，而且这个方法是protected修饰的。

		3、这个方法不需要程序员手动调用，JVM的垃圾回收器负责调用这个方法。
		不像equals toString，equals和toString()方法是需要你写代码调用的。
		finalize()只需要重写，重写完将来自动会有程序来调用。

		4、finalize()方法的执行时机：
			当一个java对象即将被垃圾回收器回收的时候，垃圾回收器负责调用
			finalize()方法。
		
		5、finalize()方法实际上是SUN公司为java程序员准备的一个时机，垃圾销毁时机。
		如果希望在对象销毁时机执行一段代码的话，这段代码要写到finalize()方法当中。

		6、静态代码块的作用是什么？
			static {
				....
			}
			静态代码块在类加载时刻执行，并且只执行一次。
			这是一个SUN准备的类加载时机。

			finalize()方法同样也是SUN为程序员准备的一个时机。
			这个时机是垃圾回收时机。

		7、提示：	
			java中的垃圾回收器不是轻易启动的，
			垃圾太少，或者时间没到，种种条件下，
			有可能启动，也有可能不启动。
*/
public class Test06{
	public static void main(String[] args){
		/*
		// 创建对象
		Person p = new Person();

		// 怎么把Person对象变成垃圾？
		p = null;
		*/

		// 多造点垃圾
		/*
		for(int i = 0; i < 100000000; i++){
			Person p = new Person();
			p = null;
		}
		*/
		
		for(int i = 0; i < 1000; i++){
			Person p = new Person();
			p = null;

			// 有一段代码可以建议垃圾回收器启动。
			if(i % 2 == 0){
				System.gc(); // 建议启动垃圾回收器。（只是建议，可能不启动，也可能启动。启动的概率高了一些。）
			}
		}		

	}
}

// 项目开发中有这样的业务需求：所有对象在JVM中被释放的时候，请记录一下释放时间！！！
// 记录对象被释放的时间点，这个负责记录的代码写到哪里？
// 写到finalize()方法中。
class Person{

	// 重写finalize()方法
	// Person类型的对象被垃圾回收器回收的时候，垃圾回收器负责调用：p.finalize();
	protected void finalize() throws Throwable {
		// this代表当前对象
		System.out.println(this + "即将被销毁！");
	}
}
```

### 5.7object的hashCode方法

``` java
/*
	hashCode方法：
		在Object中的hashCode方法是怎样的？
			public native int hashCode();

			这个方法不是抽象方法，带有native关键字，底层调用C++程序。
		
		hashCode()方法返回的是哈希码：
			实际上就是一个java对象的内存地址，经过哈希算法，得出的一个值。
			所以hashCode()方法的执行结果可以等同看做一个java对象的内存地址。
*/
public class Test07{
	public static void main(String[] args){
		Object o = new Object();
		int hashCodeValue = o.hashCode();

		// 对象内存地址经过哈希算法转换的一个数字。可以等同看做内存地址。
		System.out.println(hashCodeValue); //798154996

		MyClass mc = new MyClass();
		int hashCodeValue2 = mc.hashCode();
		System.out.println(hashCodeValue2); //1392838282

		MyClass mc2 = new MyClass();
		System.out.println(mc2.hashCode()); // 523429237
	}
}

class MyClass
{
}
```

## 6.内部类

## 6.1内部类概述和引出匿名内部类

``` java
/*
	匿名内部类：

		1、什么是内部类？
			内部类：在类的内部又定义了一个新的类。被称为内部类。

		2、内部类的分类：
			静态内部类：类似于静态变量
			实例内部类：类似于实例变量
			局部内部类：类似于局部变量

		3、使用内部类编写的代码，可读性很差。能不用尽量不用。

		4、匿名内部类是局部内部类的一种。
			因为这个类没有名字而得名，叫做匿名内部类。
		
		5、学习匿名内部类主要是让大家以后在阅读别人代码的时候，能够理解。
		并不代表以后都要这样写。因为匿名内部类有两个缺点：
			缺点1：太复杂，太乱，可读性差。
			缺点2：类没有名字，以后想重复使用，不能用。
		
		6、不理解算了，你只要记住这种写法就行。
*/

class Test01{

	// 静态变量
	static String country;
	// 该类在类的内部，所以称为内部类
	// 由于前面有static，所以称为“静态内部类”
	static class Inner1{
	}
	
	// 实例变量
	int age;
	// 该类在类的内部，所以称为内部类
	// 没有static叫做实例内部类。
	class Inner2{
	}
 
	// 方法
	public void doSome(){
		// 局部变量
		int i = 100;
		// 该类在类的内部，所以称为内部类
		// 局部内部类。
		class Inner3{
		}
	}

	public void doOther(){
		// doSome()方法中的局部内部类Inner3，在doOther()中不能用。
	}

	// main方法，入口
	public static void main(String[] args){
		// 调用MyMath中的mySum方法。
		MyMath mm = new MyMath();
		/*
		Compute c = new ComputeImpl();
		mm.mySum(c, 100, 200);
		*/
		
		//合并（这样写代码，表示这个类名是有的。类名是：ComputeImpl）
		//mm.mySum(new ComputeImpl(), 100, 200);
	
		// 使用匿名内部类，表示这个ComputeImpl这个类没名字了。
		// 这里表面看上去好像是接口可以直接new了，实际上并不是接口可以new了。
		// 后面的{} 代表了对接口的实现。
		// 不建议使用匿名内部类，为什么？
		// 因为一个类没有名字，没有办法重复使用。另外代码太乱，可读性太差。
		mm.mySum(new Compute(){
			public int sum(int a, int b){
				return a + b;
			}
		}, 200, 300);



	}

}

// 负责计算的接口
interface Compute{ 
	
	// 抽象方法
	int sum(int a, int b);
}

// 你自动会在这里编写一个Compute接口的实现类
/*
class ComputeImpl implements Compute{

	// 对方法的实现
	public int sum(int a, int b){
		return a + b;
	}
}
*/

// 数学类
class MyMath{
	// 数学求和方法
	public void mySum(Compute c, int x, int y){
		int retValue = c.sum(x, y);
		System.out.println(x + "+" + y + "=" + retValue);
	}	
}
```

## 7.数组

### 7.1 一维数组的概述和内部结构和对一维数组的访问

``` java
package com.bjpowernode.javase.array;
/*
Array
    1、Java语言中的数组是一种引用数据类型。不属于基本数据类型。数组的父类是Object。
    2、数组实际上是一个容器，可以同时容纳多个元素。（数组是一个数据的集合。）
    数组：字面意思是“一组数据”
    3、数组当中可以存储“基本数据类型”的数据，也可以存储“引用数据类型”的数据。
    4、数组因为是引用类型，所以数组对象是堆内存当中。（数组是存储在堆当中的）
    5、数组当中如果存储的是“java对象”的话，实际上存储的是对象的“引用（内存地址）”，数组中不能直接存储java对象。
    6、数组一旦创建，在java中规定，长度不可变。（数组长度不可变）
    7、数组的分类：一维数组、二维数组、三维数组、多维数组...（一维数组较多，二维数组偶尔使用！）
    8、所有的数组对象都有length属性(java自带的)，用来获取数组中元素的个数。
    9、java中的数组要求数组中元素的类型统一。比如int类型数组只能存储int类型，Person类型数组只能存储Person类型。
    例如：超市购物，购物袋中只能装苹果，不能同时装苹果和橘子。（数组中存储的元素类型统一）
    10、数组在内存方面存储的时候，数组中的元素内存地址(存储的每一个元素都是有规则的挨着排列的)是连续的。内存地址连续。
    这是数组存储元素的特点（特色）。数组实际上是一种简单的数据结构。
    11、所有的数组都是拿“第一个小方框的内存地址”作为整个数组对象的内存地址。
    （数组中首元素的内存地址作为整个数组对象的内存地址。）
    12、数组中每一个元素都是有下标的，下标从0开始，以1递增。最后一个元素的下标是：length - 1
    下标非常重要，因为我们对数组中元素进行“存取”的时候，都需要通过下标来进行。
    13、数组这种数据结构的优点和缺点是什么？
        优点：查询/查找/检索某个下标上的元素时效率极高。可以说是查询效率最高的一个数据结构。
            为什么检索效率高？
                第一：每一个元素的内存地址在空间存储上是连续的。
                第二：每一个元素类型相同，所以占用空间大小一样。
                第三：知道第一个元素内存地址，知道每一个元素占用空间的大小，又知道下标，所以
                通过一个数学表达式就可以计算出某个下标上元素的内存地址。直接通过内存地址定位
                元素，所以数组的检索效率是最高的。

                数组中存储100个元素，或者存储100万个元素，在元素查询/检索方面，效率是相同的，
                因为数组中元素查找的时候不会一个一个找，是通过数学表达式计算出来的。（算出一个
                内存地址，直接定位的。）
        缺点：
            第一：由于为了保证数组中每个元素的内存地址连续，所以在数组上随机删除或者增加元素的时候，
        效率较低，因为随机增删元素会涉及到后面元素统一向前或者向后位移的操作。
            第二：数组不能存储大数据量，为什么？
                因为很难在内存空间上找到一块特别大的连续的内存空间。

        注意：对于数组中最后一个元素的增删，是没有效率影响的。
    14、怎么声明/定义一个一维数组？
        语法格式：
            int[] array1;
            double[] array2;
            boolean[] array3;
            String[] array4;
            Object[] array5;
    15、怎么初始化一个一维数组呢？
        包括两种方式：静态初始化一维数组，动态初始化一维数组。
        静态初始化语法格式：
            int[] array = {100, 2100, 300, 55};
        动态初始化语法格式：
            int[] array = new int[5]; // 这里的5表示数组的元素个数。
                                        // 初始化一个5个长度的int类型数组，每个元素默认值0
            String[] names = new String[6]; // 初始化6个长度的String类型数组，每个元素默认值null。

 */
public class ArrayTest01 {
    public static void main(String[] args) {
        // 声明一个int类型的数组，使用静态初始化的方式
        int[] a = {1, 100, 10, 20, 55, 689};
        // 这是C++风格，不建议java中使用。
        //int a[] = {1, 100, 10, 20, 55, 689};

        // 所有的数组对象都有length属性
        System.out.println("数组中元素的个数" + a.length);

        // 数组中每一个元素都有下标
        // 通过下标对数组中的元素进行存和取。
        // 取（读）
        System.out.println("第一个元素 = " + a[0]);
        System.out.println("最后一个元素 = " + a[5]);
        System.out.println("最后一个元素 = " + a[a.length - 1]);

        // 存（改）
        // 把第一个元素修改为111
        a[0] = 111;
        // 把最后一个元素修改为0
        a[a.length - 1] = 0;

        System.out.println("第一个元素 = " + a[0]);
        System.out.println("最后一个元素 = " + a[5]);

        // 一维数组怎么遍历呢？
        for(int i = 0; i < a.length; i++){
            System.out.println(a[i]); // i是从0到5，是下标
        }

        // 下标为6表示第7个元素，第7个元素没有，下标越界了。会出现什么异常呢？
        //System.out.println(a[6]); //ArrayIndexOutOfBoundsException（比较著名的异常。）

        // 从最后一个元素遍历到第1个元素
        for (int i = a.length - 1; i >= 0; i--) {
            System.out.println("颠倒顺序输出-->" + a[i]);
        }
    }
}

```

### 7.2动态初始化一维数组

``` java
package com.bjpowernode.javase.array;

/*
关于每个类型的默认值还有印象吗？
    数据类型            默认值
    ----------------------------
    byte                0
    short               0
    int                 0
    long                0L
    float               0.0F
    double              0.0
    boolean             false
    char                \u0000
    引用数据类型          null

 什么时候采用静态初始化方式，什么时候使用动态初始化方式呢？
    当你创建数组的时候，确定数组中存储哪些具体的元素时，采用静态初始化方式。
    当你创建数组的时候，不确定将来数组中存储哪些数据，你可以采用动态初始化的方式，预先分配内存空间。
 */
public class ArrayTest02 {
    public static void main(String[] args) {
        // 声明/定义一个数组，采用动态初始化的方式创建
        int[] a = new int[4]; // 创建长度为4的int数组，数组中每个元素的默认值是0
        // 遍历数组
        for (int i = 0; i < a.length; i++) {
            System.out.println("数组中下标为" + i + "的元素是：" + a[i]);
        }

        // 后期赋值
        a[0] = 1;
        a[1] = 100;
        a[2] = 111;
        a[3] = 222; // 注意下标别越界。

        for (int i = 0; i < a.length; i++) {
            System.out.println("数组中下标为" + i + "的元素是：" + a[i]);
        }

        // 初始化一个Object类型的数组，采用动态初始化方式
        Object[] objs = new Object[3]; // 3个长度，动态初始化，所以每个元素默认值是null
        for (int i = 0; i < objs.length; i++) {
            System.out.println(objs[i]);
        }

        System.out.println("===============================");

        String[] strs = new String[3];
        for (int i = 0; i < strs.length; i++) {
            System.out.println(strs[i]);
        }

        // 采用静态初始化的方式
        String[] strs2 = {"abc", "def", "xyz"};
        for (int i = 0; i < strs2.length; i++) {
            System.out.println(strs2[i]);
        }

        // 存储Object，采用静态初始化呢？
        /*Object o1 = new Object();
        Object o2 = new Object();
        Object o3 = new Object();

        Object[] objects = {o1, o2, o3};*/

        Object[] objects = {new Object(), new Object(), new Object()};

        for (int i = 0; i < objects.length; i++) {
            /*Object o = objects[i];
            System.out.println(o);*/
            System.out.println(objects[i]);
        }
    }
}

```

### 7.3 方法的参数是数组

``` java
package com.bjpowernode.javase.array;

// 当一个方法上，参数的类型是一个数组的时候。

public class ArrayTest03 {
    // main方法的编写方式，还可以采用C++的语法格式哦！
    public static void main(String args[]) { 

        System.out.println("hello world!");

        // java的风格。
        int[] a1 = {1,23,3};
        for (int i = 0; i < a1.length ; i++) {
            System.out.println(a1[i]);
        }

        // C++的写法，不建议。
        int a2[] = {3,4,2};
        for (int i = 0; i < a2.length ; i++) {
            System.out.println(a2[i]);
        }

        System.out.println("===================================");
        // 调用方法时传一个数组
        int[] x = {1,2,3,4};
        printArray(x);

        // 创建String数组
        String[] stringArray = {"abc", "def", "hehe", "haha"};
        printArray(stringArray);

        String[] strArray = new String[10];
        printArray(strArray); // 10个null

        System.out.println("================================");
        printArray(new String[3]);
        System.out.println("***********************************");
        printArray(new int[4]);

    }

    public static void printArray(int[] array){
        for(int i = 0; i < array.length; i++){
            System.out.println(array[i]);
        }
    }

    public static void printArray(String[] args){
        for(int i = 0; i < args.length; i++){
            System.out.println("String数组中的元素：" + args[i]);
        }
    }

}

package com.bjpowernode.javase.array;

// 当一个方法的参数是一个数组的时候，我们还可以采用这种方式传。

public class ArrayTest04 {
    public static void main(String[] args) {
        // 静态初始化一维数组
        int[] a = {1,2,3};
        printArray(a);

        System.out.println("============================");
        // 没有这种语法。
        //printArray({1,2,3});
        // 如果直接传递一个静态数组的话，语法必须这样写。
        printArray(new int[]{1,2,3});

        // 动态初始化一维数组
        int[] a2 = new int[4];
        printArray(a2);

        System.out.println("=============================");
        printArray(new int[3]);
    }

    // 为什么要使用静态方法？方便呀，不需要new对象啊。
    public static void printArray(int[] array){
        for (int i = 0; i < array.length; i++) {
            System.out.println(array[i]);
        }
    }
}

```

### 7.4 main方法的String数组

``` java
package com.bjpowernode.javase.array;
/*
1、main方法上面的“String[] args”有什么用？
    分析以下：谁负责调用main方法（JVM）
    JVM调用main方法的时候，会自动传一个String数组过来。
 */
public class ArrayTest05 {
    // 这个方法程序员负责写出来，JVM负责调用。JVM调用的时候一定会传一个String数组过来。
    public static void main(String[] args) {
        // JVM默认传递过来的这个数组对象的长度？默认0
        // 通过测试得出：args不是null。
        System.out.println("JVM给传递过来的String数组参数，它这个数组的长度是？" + args.length);

        // 以下这一行代码表示的含义：数组对象创建了，但是数组中没有任何数据。
        //String[] strs = new String[0];
        //String[] strs = {}; // 静态初始化数组，里面没东西。
        //printLength(strs);

        // 这个数组什么时候里面会有值呢？
        // 其实这个数组是留给用户的，用户可以在控制台上输入参数，这个参数自动会被转换为“String[] args”
        // 例如这样运行程序：java ArrayTest05 abc def xyz
        // 那么这个时候JVM会自动将“abc def xyz”通过空格的方式进行分离，分离完成之后，自动放到“String[] args”数组当中。
        // 所以main方法上面的String[] args数组主要是用来接收用户输入参数的。
        // 把abc def xyz 转换成字符串数组：{"abc","def","xyz"}
        // 遍历数组
        for (int i = 0; i < args.length; i++) {
            System.out.println(args[i]);
        }

    }

    public static void printLength(String[] args){
        System.out.println(args.length); // 0
    }
}

```

### 7.5 main方法String参数的实例

``` java
package com.bjpowernode.javase.array;

/*
模拟一个系统，假设这个系统要使用，必须输入用户名和密码。
 */
public class ArrayTest06 {
    // 用户名和密码输入到String[] args数组当中。
    public static void main(String[] args) {
        if(args.length != 2){
            System.out.println("使用该系统时请输入程序参数，参数中包括用户名和密码信息，例如：zhangsan 123");
            return;
        }

        // 程序执行到此处说明用户确实提供了用户名和密码。
        // 接下来你应该判断用户名和密码是否正确。
        // 取出用户名
        String username = args[0];
        // 取出密码
        String password = args[1];

        // 假设用户名是admin，密码是123的时候表示登录成功。其它一律失败。
        // 判断两个字符串是否相等，需要使用equals方法。
        //if(username.equals("admin") && password.equals("123")){
        // 这样编写是不是可以避免空指针异常。
        // 采用以下编码风格，及时username和password都是null，也不会出现空指针异常。（这是老程序员给的一条编程经验。）
        if("admin".equals(username) && "123".equals(password)){
            System.out.println("登录成功，欢迎[" + username + "]回来");
            System.out.println("您可以继续使用该系统....");
        }else{
            System.out.println("验证失败，用户名不存在或者密码错误！");
        }
    }
}

```

### 7.6数组中存储引用数据类型

``` java
package com.bjpowernode.javase.array;

/**
 * 一维数组的深入，数组中存储的类型为：引用数据类型
 * 对于数组来说，实际上只能存储java对象的“内存地址”。数组中存储的每个元素是“引用”。
 */
public class ArrayTest07 {
    public static void main(String[] args) {

        // a是一个数组
        // a[0] 是数组中的一个元素。
        // a[1] 是数组中的一个元素。
        int[] a = {100, 200, 300};
        System.out.println(a[1]);
        //a[2] = 400;

        int[] array = {1,2,3};
        for (int i = 0; i < array.length; i++) {
            /*int temp = array[i];
            System.out.println(temp);*/
            System.out.println(array[i]);
        }

        // 创建一个Animal类型的数组
        Animal a1 = new Animal();
        Animal a2 = new Animal();
        Animal[] animals = {a1, a2};

        // 对Animal数组进行遍历
        for (int i = 0; i < animals.length; i++) {
            /*Animal a = animals[i];
            a.move();*/
            // 代码合并
            animals[i].move(); // 这个move()方法不是数组的。是数组当中Animal对象的move()方法。
        }

        // 动态初始化一个长度为2的Animal类型数组。
        Animal[] ans = new Animal[2];
        // 创建一个Animal对象，放到数组的第一个盒子中。
        ans[0] = new Animal();

        // Animal数组中只能存放Animal类型，不能存放Product类型。
        //ans[1] = new Product();

        // Animal数组中可以存放Cat类型的数据，因为Cat是一个Animal。
        // Cat是Animal的子类。
        ans[1] = new Cat();

        // 创建一个Animal类型的数组，数组当中存储Cat和Bird
        Cat c = new Cat();
        Bird b = new Bird();
        Animal[] anis = {c, b};

        //Animal[] anis = {new Cat(), new Bird()}; // 该数组中存储了两个对象的内存地址。
        for (int i = 0; i < anis.length; i++){
            // 这个取出来的可能是Cat，也可能是Bird，不过肯定是一个Animal
            // 如果调用的方法是父类中存在的方法不需要向下转型。直接使用父类型引用调用即可。
            //anis[i]
            //Animal an = anis[i];
            //an.move();

            //Animal中没有sing()方法。
            //anis[i].sing();

            // 调用子对象特有方法的话，需要向下转型！！！
            if(anis[i] instanceof Cat){
                Cat cat = (Cat)anis[i];
                cat.catchMouse();
            }else if(anis[i] instanceof Bird){
                Bird bird = (Bird)anis[i];
                bird.sing();
            }
        }

    }
}

class Animal{
    public void move(){
        System.out.println("Animal move...");
    }
}

// 商品类
class Product{

}

// Cat是子类
class Cat extends Animal {
    public void move(){
        System.out.println("猫在走猫步！");
    }
    // 特有方法
    public void catchMouse(){
        System.out.println("猫抓老鼠！");
    }
}

// Bird子类
class Bird extends Animal {
    public void move(){
        System.out.println("Bird Fly!!!");
    }
    // 特有的方法
    public void sing(){
        System.out.println("鸟儿在歌唱！！！");
    }
}
```

### 7.7 数组的扩容和拷贝

``` java
package com.bjpowernode.javase.array;

/**
 * 关于一维数组的扩容。
 * 在java开发中，数组长度一旦确定不可变，那么数组满了怎么办？
 *      数组满了，需要扩容。
 *      java中对数组的扩容是：
 *          先新建一个大容量的数组，然后将小容量数组中的数据一个一个拷贝到大数组当中。
 *
 * 结论：数组扩容效率较低。因为涉及到拷贝的问题。所以在以后的开发中请注意：尽可能少的进行数组的拷贝。
 * 可以在创建数组对象的时候预估计以下多长合适，最好预估准确，这样可以减少数组的扩容次数。提高效率。
 */
public class ArrayTest08 {
    public static void main(String[] args) {
        // java中的数组是怎么进行拷贝的呢？
        //System.arraycopy(5个参数);

        // 拷贝源（从这个数组中拷贝）
        int[] src = {1, 11, 22, 3, 4};

        // 拷贝目标（拷贝到这个目标数组上）
        int[] dest = new int[20]; // 动态初始化一个长度为20的数组，每一个元素默认值0

        // 调用JDK System类中的arraycopy方法，来完成数组的拷贝
        //System.arraycopy(src, 1, dest, 3, 2);

        // 遍历目标数组
        /*
        for (int i = 0; i < dest.length; i++) {
            System.out.println(dest[i]); // 0 0 0 11 22 ... 0
        }
         */

        System.arraycopy(src, 0, dest, 0, src.length);
        for (int i = 0; i < dest.length; i++) {
            System.out.println(dest[i]);
        }

        // 数组中如果存储的元素是引用，可以拷贝吗？当然可以。
        String[] strs = {"hello", "world!", "study", "java", "oracle", "mysql", "jdbc"};
        String[] newStrs = new String[20];
        System.arraycopy(strs, 0, newStrs, 0, strs.length);
        for (int i = 0; i < newStrs.length; i++) {
            System.out.println(newStrs[i]);
        }

        System.out.println("================================");
        Object[] objs = {new Object(), new Object(), new Object()};
        Object[] newObjs = new Object[5];
        // 思考一下：这里拷贝的时候是拷贝对象，还是拷贝对象的地址。（地址。）
        System.arraycopy(objs, 0, newObjs, 0, objs.length);
        for (int i = 0; i < newObjs.length; i++) {
            System.out.println(newObjs[i]);
        }
    }
}

```

### 7.8 对二维数组的理解和二维数组的length属性

``` java
package com.bjpowernode.javase.array;
/*
关于java中的二维数组
    1、二维数组其实是一个特殊的一维数组，特殊在这个一维数组当中的每一个元素是一个一维数组。
    2、三维数组是什么？
        三维数组是一个特殊的二维数组，特殊在这个二维数组中每一个元素是一个一维数组。
        实际的开发中使用最多的就是一维数组。二维数组也很少使用。三维数组几乎不用。
    3、二维数组静态初始化
        int[][] array = {{1,1,1},{2,3,4,5},{0,0,0,0},{2,3,4,5},{2,3,4,5},{2,3,4,5},{2,3,4,5}};
 */
public class ArrayTest09 {
    public static void main(String[] args) {
        // 一维数组
        int[] array = {100, 200, 300};
        System.out.println(array.length); // 3
        System.out.println("=======================");

        // 二维数组
        // 以下代码当中：里面的是4个一维数组。
        int[][] a = {
                {100, 200, 300},
                {30, 20, 40, 50, 60},
                {6, 7, 9, 1},
                {0}
        };
        System.out.println(a.length); // 4
        System.out.println(a[0].length); // 3
        System.out.println(a[1].length); // 5
        System.out.println(a[2].length); // 4
        System.out.println(a[3].length); // 1

        // 里面的是5个一维数组。
        int[][] a2 = {
                {100, 200, 300},
                {30, 20, 40, 50, 60},
                {6, 7, 9, 1},
                {0},
                {1,2,3,4,5}
        };

    }
}

```

### 7.9 二维数组的元素访问

``` java
package com.bjpowernode.javase.array;

/*
关于二维数组中元素的：读和改。

    a[二维数组中的一维数组的下标][一维数组的下标]

    a[0][0]：表示第1个一维数组中的第1个元素。

    a[3][100]：表示第4个一维数组中的第101个元素。

    注意：对于a[3][100]来说，其中 a[3] 是一个整体。[100]是前面a[3]执行结束的结果然后再下标100.
 */
public class ArrayTest10 {
    public static void main(String[] args) {
        // 二维数组
        int[][] a = {
                {34,4,65},
                {100,200,3900,111},
                {0}
        };

        // 请取出以上二位数中的第1个一维数组。
        int[] 我是第1个一维数组 = a[0];
        int 我是第1个一维数组中的第1个元素 = 我是第1个一维数组[0];
        System.out.println(我是第1个一维数组中的第1个元素);

        // 以下代码的由来是因为以上代码的合并导致的。
        System.out.println(a[0][0]);

        // 取出第2个一维数组当中第3个元素
        System.out.println("第二个一维数组中第三个元素：" + a[1][2]);

        // 取出第3个一维数组当中第1个元素
        System.out.println("第3个一维数组中第1个元素：" + a[2][0]);

        // 改
        a[2][0] = 11111;
        System.out.println(a[2][0]);

        // 注意别越界。
        //java.lang.ArrayIndexOutOfBoundsException
        //System.out.println(a[2][1]);
    }
}

```

### 7.10 遍历二位数组

```java
package com.bjpowernode.javase.array;

/*
二维数组的遍历
 */
public class ArrayTest11 {
    public static void main(String[] args) {

        // 二维数组
        String[][] array = {
                {"java", "oracle", "c++", "python", "c#"},
                {"张三", "李四", "王五"},
                {"lucy", "jack", "rose"}
        };

        // 遍历二维数组
        for(int i = 0; i < array.length; i++){ // 外层循环3次。（负责纵向。）
            String[] 一维数组 = array[i];
            // 负责遍历一维数组
            for(int j = 0; j < 一维数组.length; j++){
                System.out.print(一维数组[j] + " ");
            }
            // 输出换行符
            System.out.println();
        }

        // 合并代码
        for(int i = 0; i < array.length; i++){ // 外层循环3次。（负责纵向。）
            for(int j = 0; j < array[i].length; j++){
                System.out.print(array[i][j] + " ");
            }
            System.out.println();
        }
    }
}

```

### 7.11 方法参数是个二维数组

``` java
package com.bjpowernode.javase.array;

/*
二维数组的遍历
 */
public class ArrayTest11 {
    public static void main(String[] args) {

        // 二维数组
        String[][] array = {
                {"java", "oracle", "c++", "python", "c#"},
                {"张三", "李四", "王五"},
                {"lucy", "jack", "rose"}
        };

        // 遍历二维数组
        for(int i = 0; i < array.length; i++){ // 外层循环3次。（负责纵向。）
            String[] 一维数组 = array[i];
            // 负责遍历一维数组
            for(int j = 0; j < 一维数组.length; j++){
                System.out.print(一维数组[j] + " ");
            }
            // 输出换行符
            System.out.println();
        }

        // 合并代码
        for(int i = 0; i < array.length; i++){ // 外层循环3次。（负责纵向。）
            for(int j = 0; j < array[i].length; j++){
                System.out.print(array[i][j] + " ");
            }
            System.out.println();
        }
    }
}

```

### 7.12 数组模拟栈数据结构

``` java
package com.bjpowernode.javase.array.homework;
/*
	编写程序，使用一维数组，模拟栈数据结构。
	要求：
		1、这个栈可以存储java中的任何引用类型的数据。
		2、在栈中提供push方法模拟压栈。（栈满了，要有提示信息。）
		3、在栈中提供pop方法模拟弹栈。（栈空了，也有有提示信息。）
		4、编写测试程序，new栈对象，调用push pop方法来模拟压栈弹栈的动作。
		5、假设栈的默认初始化容量是10.（请注意无参数构造方法的编写方式。）
 */
public class MyStack {
    // 向栈当中存储元素，我们这里使用一维数组模拟。存到栈中，就表示存储到数组中。
    // 因为数组是我们学习java的第一个容器。
    // 为什么选择Object类型数组？因为这个栈可以存储java中的任何引用类型的数据
    // new Animal()对象可以放进去，new Person()对象也可以放进去。因为Animal和Person的超级父类就是Object。
    // 包括String也可以存储进去。因为String父类也是Object。
    private Object[] elements;

    // 栈帧，永远指向栈顶部元素
    // 那么这个默认初始值应该是多少。注意：最初的栈是空的，一个元素都没有。
    //private int index = 0; // 如果index采用0，表示栈帧指向了顶部元素的上方。
    //private int index = -1; // 如果index采用-1，表示栈帧指向了顶部元素。
    private int index;

    /**
     * 无参数构造方法。默认初始化栈容量10.
     */
    public MyStack() {
        // 一维数组动态初始化
        // 默认初始化容量是10.
        this.elements = new Object[10];
        // 给index初始化
        this.index = -1;
    }

    /**
     * 压栈的方法
     * @param obj 被压入的元素
     */
    public void push(Object obj){
        if(index >= elements.length - 1){
            System.out.println("压栈失败，栈已满！");
            return;
        }
        // 程序能够走到这里，说明栈没满
        // 向栈中加1个元素，栈帧向上移动一个位置。
        index++;
        elements[index] = obj;
        // 在声明一次：所有的System.out.println()方法执行时，如果输出引用的话，自动调用引用的toString()方法。
        System.out.println("压栈" + obj + "元素成功，栈帧指向" + index);
    }

    /**
     * 弹栈的方法，从数组中往外取元素。每取出一个元素，栈帧向下移动一位。
     * @return
     */
    public void pop(){
        if(index < 0){
            System.out.println("弹栈失败，栈已空！");
            return;
        }
        // 程序能够执行到此处说明栈没有空。
        System.out.print("弹栈" + elements[index] + "元素成功，");
        // 栈帧向下移动一位。
        index--;
        System.out.println("栈帧指向" + index);
    }

    // set和get也许用不上，但是你必须写上，这是规矩。你使用IDEA生成就行了。
    // 封装：第一步：属性私有化，第二步：对外提供set和get方法。
    public Object[] getElements() {
        return elements;
    }

    public void setElements(Object[] elements) {
        this.elements = elements;
    }

    public int getIndex() {
        return index;
    }

    public void setIndex(int index) {
        this.index = index;
    }
}

package com.bjpowernode.javase.array.homework;

public class MyStackTest {
    public static void main(String[] args) {

        // 创建一个栈对象，初始化容量是10个。
        MyStack stack = new MyStack();

        // 调用方法压栈
        stack.push(new Object());
        stack.push(new Object());
        stack.push(new Object());
        stack.push(new Object());
        stack.push(new Object());
        stack.push(new Object());
        stack.push(new Object());
        stack.push(new Object());
        stack.push(new Object());
        stack.push(new Object()); // 最后压入的。最先弹出来。（这个才符合栈的数据结构。）

        // 压这个元素失败了。
        stack.push(new Object());

        // 弹栈
        stack.pop();
        stack.pop();
        stack.pop();
        stack.pop();
        stack.pop();
        stack.pop();
        stack.pop();
        stack.pop();
        stack.pop();
        stack.pop();

        stack.pop();
    }
}

```

### 7.13酒店管理系统部分功能实现

``` java
package com.bjpowernode.javase.array.homework;

import java.util.Scanner;

/*
为某个酒店编写程序：酒店管理系统，模拟订房、退房、打印所有房间状态等功能。
	1、该系统的用户是：酒店前台。
	2、酒店使用一个二维数组来模拟。“Room[][] rooms;”
	3、酒店中的每一个房间应该是一个java对象：Room
	4、每一个房间Room应该有：房间编号、房间类型、房间是否空闲.
	5、系统应该对外提供的功能：
		可以预定房间：用户输入房间编号，订房。
		可以退房：用户输入房间编号，退房。
		可以查看所有房间的状态：用户输入某个指令应该可以查看所有房间状态。
 */
public class HotelMgtSystem {

    public static void main(String[] args) {
        // 创建酒店对象
        Hotel hotel = new Hotel();
        // 打印房间状态
        //hotel.print();

        /*
        首先输出一个欢迎页面
         */
        System.out.println("欢迎使用酒店管理系统，请认真阅读以下使用说明");
        System.out.println("功能编号对应的功能：[1]表示查看房间列表。[2]表示订房。[3]表示退房。[0]表示退出系统。");
        Scanner s = new Scanner(System.in);

        // 一直可以使用（死循环。）。
        while(true){
            System.out.print("请输入功能编号：");
            int i = s.nextInt();
            if(i == 1){
                // 查看房间列表
                hotel.print();
            }else if(i == 2){
                // 订房
                System.out.print("请输入订房编号：");
                int roomNo = s.nextInt(); //小姐姐输入房间编号
                hotel.order(roomNo);
            }else if(i == 3){
                // 退房
                System.out.print("请输入退房编号：");
                int roomNo = s.nextInt(); //小姐姐输入房间编号
                hotel.exit(roomNo);
            }else if(i == 0){
                // 退出系统
                System.out.println("再见，欢迎下次再来！");
                return;
            }else{
                // 出错了！
                System.out.println("输入功能编号有误，请重新输入！");
            }
        }

    }
}

package com.bjpowernode.javase.array.homework;

/*
酒店对象，酒店中有二维数组，二维数组模拟大厦。
 */
public class Hotel {
    /**
     * 二维数组，模拟大厦所有的房间
     */
    private Room[][] rooms;

    // 盖楼通过构造方法来盖楼。
    public Hotel(){
        // 一共有几层，每层的房间类型是什么，每个房间的编号是什么。
        // 我们可以先写死。一共三层、一层单人间、二层标准间、三层总统套房，每层有10个房间。
        /**
         * 房间编号
         * 1楼：101 102 103 104 105 106..
         * 2楼：201 202 203 204 205 206..
         * 3楼：301 302 303 304 305 306..
         * ...
         */
        // 动态初始化
        rooms = new Room[3][10]; // 3行10列。3层楼，每层10个房间。

        // 创建30个Room对象，放到数组当中。
        // 怎么放？ 二维数组遍历。
        for(int i = 0; i < rooms.length; i++){ // i是下标：0 1 2。i+1是楼层：1,2,3
            for(int j = 0; j < rooms[i].length; j++){
                if(i == 0){
                    // 一层
                    rooms[i][j] = new Room((i+1)*100+j+1, "单人间", true);
                }else if(i == 1){
                    // 二层
                    rooms[i][j] = new Room((i+1)*100+j+1, "标准间", true);
                }else if(i == 2){
                    // 三层
                    rooms[i][j] = new Room((i+1)*100+j+1, "总统套房", true);
                }
            }
        }
    }

    // 在酒店对象上提供一个打印房间列表的方法
    public void print(){
        // 打印所有房间状态,就是遍历二维数组
        for(int i = 0; i < rooms.length; i++){
            // 里面for循环负责输出一层。
            for(int j = 0; j < rooms[i].length; j++) {
                Room room = rooms[i][j];
                System.out.print(room);
            }
            // 换行
            System.out.println();
        }
    }

    /**
     * 订房方法。
     * @param roomNo 调用此方法时需要传递一个房间编号过来。这个房间编号是前台小姐姐输入的。
     */
    public void order(int roomNo){
        // 订房最主要的是将房间对象的status修改为false。
        // Room对象的status修改为false。
        // 假设房间编号207（下标是 rooms[1][6] ）
        // 通过房间编号演算出下标。获取房间对象。
        Room room = rooms[roomNo / 100 - 1][roomNo % 100 - 1];
        // 修改为占用。
        room.setStatus(false);
        System.out.println(roomNo + "已订房！");
    }

    /**
     * 退房
     * @param roomNo
     */
    public void exit(int roomNo){
        Room room = rooms[roomNo / 100 - 1][roomNo % 100 - 1];
        // 修改为空闲。
        room.setStatus(true);
        System.out.println(roomNo + "已退房！");
    }

}

package com.bjpowernode.javase.array.homework;

/**
 * 酒店的房间
 */
public class Room extends Object{
    /**
     * 房间编号
     * 1楼：101 102 103 104 105 106..
     * 2楼：201 202 203 204 205 206..
     * 3楼：301 302 303 304 305 306..
     * ...
     */
    private int no;
    /**
     * 房间类型：标准间 单人间 总统套房
     */
    private String type;
    /**
     * 房间状态。
     * true表示空闲，房间可以被预定。
     * false表示占用，房间不能被预定。
     */
    private boolean status;

    // 构造方法
    public Room() {
    }

    public Room(int no, String type, boolean status) {
        this.no = no;
        this.type = type;
        this.status = status;
    }

    // setter and getter
    public int getNo() {
        return no;
    }

    public void setNo(int no) {
        this.no = no;
    }

    public String getType() {
        return type;
    }

    public void setType(String type) {
        this.type = type;
    }

    // IDEA工具对于boolean类型的变量，生成的get方法的方法名是：isXxx()
    // 如果你不喜欢，可以修改为getXxx()
    /*public boolean isStatus() {
        return status;
    }*/
    public boolean getStatus() {
        return status;
    }

    public void setStatus(boolean status) {
        this.status = status;
    }

    // equals方法重写
    // equals是用来比较两个对象是否相同的。
    // 至于怎么比较，这个还是程序员自己定。
    // 你认为两个房间的编号相同，就表示同一个房间，那么你写代码比较房间编号就行。
    public boolean equals(Object obj) {
        if(obj == null || !(obj instanceof Room)) return false;
        if(this == obj) return true;
        Room room = (Room)obj;
        // 当前房间编号 等于 传过来的房间对象的房间编号。认为是同一个房间。
        return this.getNo() == room.getNo();
    }

    // toString方法重写
    // toString方法的目的就是将java对象转换成字符串形式。
    // 怎么转，转换成什么格式，程序员自己定。目的就是：简单、清晰明了。
    // 我不要看对象内存地址。我要看具体的信息。
    public String toString() {
        //return "[101,单人间,占用]";
        //return "[102,单人间,空闲]"; // 写死了。

        //动态（把一个变量塞到一个字符串当中，口诀：加一个双引号，双引号中间加两个加号，两个加号中间加变量名。）
        return "["+no+","+type+","+(status ? "空闲" : "占用")+"]";
    }

    // 编写一个临时程序测试以下
    // 一会可以删除这个main方法
    /*
    public static void main(String[] args) {
        //Room room = new Room(101, "单人间", true);
        Room room = new Room(101, "单人间", false);

        //System.out.println(room.toString());
        // room是一个引用
        // println(引用)，会自动调用引用的toString()方法。
        System.out.println(room);

        Room room1 = new Room(102, "单人间", false);
        System.out.println(room.equals(room1));
    }
     */
    // 多行注释：ctrl + shift + /
    // 查看一个类的属性和方法：ctrl + F12
}

```

### 7.14 Arrays工具类

``` java
package com.bjpowernode.javase.array;

import java.util.Arrays;

/**
 * 使用以下SUN公司提供的数组工具类：java.util.Arrays;
 */
public class ArraysTest01 {
    public static void main(String[] args) {

        int[] arr = {112,3,4,56,67,1};

        // 工具类当中的方法大部分都是静态的。
        Arrays.sort(arr);

        // 遍历输出
        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }
    }
}

package com.bjpowernode.javase.array;

import java.util.Arrays;

/**
 * 好消息：
 *  SUN公司已经为我们程序员写好了一个数组工具类。
 *  java.util.Arrays;
 */
public class ArraysTest02 {
    public static void main(String[] args) {
        // java.util.Arrays; 工具类中有哪些方法，我们开发的时候要参考API帮助文档
        // 不要死记硬背。
        int[] arr = {3,6,4,5,12,1,2,32,5,5};
        // 排序
        Arrays.sort(arr);
        // 输出
        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }
        // 二分法查找（建立在排序基础之上。）
        int index = Arrays.binarySearch(arr, 5);

        System.out.println(index == -1 ? "该元素不存在" : "该元素下标是：" + index);
    }
}

```

### 7.15 冒泡排序

```java
package com.bjpowernode.javase.array;

/*
冒泡排序算法
    1、每一次循环结束之后，都要找出最大的数据，放到参与比较的这堆数据的最右边。（冒出最大的那个气泡。）
    2、核心：
        拿着左边的数字和右边的数字比对，当左边 > 右边的时候，交换位置。

原始数据：
3, 2, 7, 6, 8
第1次循环：(最大的跑到最右边。)
2, 3, 7, 6, 8 （3和2比较，2 < 3，所以2和3交换位置）
2, 3, 7, 6, 8 （虽然不需要交换位置：但是3和7还是需要比较一次。）
2, 3, 6, 7, 8 （7和6交换位置）
2, 3, 6, 7, 8 （虽然不需要交换位置：但是3和7还是需要比较一次。）

经过第1次循环，此时剩下参与比较的数据：2, 3, 6, 7
第2次循环：
2, 3, 6, 7 (2和3比较，不需要交换位置)
2, 3, 6, 7 （3和6比较，不需要交换位置）
2, 3, 6, 7 (6和7比较，不需要交换位置)

经过第2次循环，此时剩下参与比较的数据：2, 3, 6
第3次循环：
2, 3, 6 (2和3比较，不需要交换位置)
2, 3, 6 （3和6比较，不需要交换位置）

经过第3次循环，此时剩下参与比较的数据：2, 3
第4次循环：
2, 3 (2和3比较，不需要交换位置)

 */
public class BubbleSort {
    public static void main(String[] args) {

        // 这是int类型的数组对象
        //int[] arr = {3, 2, 7, 6, 8};
        int[] arr = {9, 8, 10, 7, 6, 0, 11};

        // 经过冒泡排序算法对以上数组中元素进行排序
        // 冒泡排序算法的核心是什么？

        // 7条数据，循环6次。以下的代码可以循环6次。
        /*
        for(int i = 0; i < arr.length-1; i++){
            System.out.println(i);
        }
         */

        // 7条数据，循环6次。以下的代码可以循环6次。（冒泡排序的外层循环采用这种方式）
        //int count = 0;
        int count2 = 0;
        for(int i = arr.length-1; i > 0; i--){
            for(int j = 0; j < i; j++){
                // 不管是否需要交换位置，总之是要比较一次的。
                //count++;
                if(arr[j] > arr[j+1]){
                    // 交换位置。
                    // arr[j] 和 arr[j+1] 交换
                    int temp;
                    temp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                    count2++;
                }
            }
        }

        //System.out.println("比较次数：" + count);
        System.out.println("交换位置的次数：" + count2); //13
        // 输出结果
        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }
    }
}

```

### 7.16  选择排序

```java
package com.bjpowernode.javase.array;
/*
选择排序：
    每一次从这堆“参与比较的数据当中”找出最小值，
    拿着这个最小值和“参与比较的这堆最前面的元素”交换位置。

    选择排序比冒泡排序好在：每一次的交换位置都是有意义的。

    关键点：选择排序中的关键在于，你怎么找出一堆数据中最小的。
        3 2 6 1 5
        假设：
            第一个3是最小的。
            3和2比较，发现2更小，所以此时最小的是2.

            继续拿着2往下比对，2和6比较，2仍然是最小的。
            继续拿着2往下比对，2和1比对，发现1更小，所以此时最小的是1.
            继续拿着1往下比对，1和5比对，发现1还是小的，所以1就是最小的。

            拿着1和最左边的3交换位置。
       2 6 3 5
       假设：
        第一个2是最小的。
        ...

      6 3 5
        假设6是最小的：
        6和3比对，发现3更小，所以此时最小的是3.
        ...
 */
public class SelectSort {
    public static void main(String[] args) {

        //int[] arr = {3, 1, 6, 2, 5};
        int[] arr = {9, 8, 10, 7, 6, 0, 11};

        int count = 0;
        int count2 = 0;

        // 选择排序
        // 5条数据循环4次。（外层循环4次。）
        for(int i = 0; i < arr.length - 1; i++){
            // i的值是0 1 2 3
            // i正好是“参加比较的这堆数据中”最左边那个元素的下标。
            //System.out.println(i);
            // i是一个参与比较的这堆数据中的起点下标。
            // 假设起点i下标位置上的元素是最小的。
            int min = i;
            for(int j = i+1; j < arr.length; j++){
                count++;
                //System.out.println("===>" + j);
                if(arr[j] < arr[min]){
                    min = j; //最小值的元素下标是j
                }
            }

            // 当i和min相等时，表示最初猜测是对的。
            // 当i和min不相等时，表示最初猜测是错的，有比这个元素更小的元素，
            // 需要拿着这个更小的元素和最左边的元素交换位置。
            if(min != i){
                // 表示存在更小的数据
                // arr[min] 最小的数据
                // arr[i] 最前面的数据
                int temp;
                temp = arr[min];
                arr[min] = arr[i];
                arr[i] = temp;
                count2++;
            }
        }

        // 冒泡排序和选择排序实际上比较的次数没变。
        // 交换位置的次数减少了。
        System.out.println("比较次数" + count); // 21
        System.out.println("交换次数：" + count2); // 5

        // 排序之后遍历
        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }
    }
}

//1 2 3 4 5
//假设1是最小的，结果1确实是最小的，就不需要交换位置。

```

### 7.17 二分查找

``` java
package com.bjpowernode.javase.array;
/*
数组的元素查找
    数组元素查找有两种方式：
        第一种方式：一个一个挨着找，直到找到为止。
        第二种方式：二分法查找（算法），这个效率较高。
 */
public class ArraySearch {
    public static void main(String[] args) {
        // 这个例子演示一下第一种方式
        int[] arr = {4,5,5,87,8};

        // 需求：找出87的下标。如果没有返回-1
        // 一个一个挨着找。
        /*
        for(int i = 0; i < arr.length;i ++){
            if(arr[i] == 87){
                System.out.println("87元素的下标是：" + i);
                return;
            }
        }
        // 程序执行到此处，表示没有87
        System.out.println("87不存在该元素！");
        */

        // 最好以上的程序封装一个方法，思考：传什么参数？返回什么值？
        // 传什么：第一个参数是数组，第二个参数是被查找的元素。
        // 返回值：返回被查找的这个元素的下标。如果找不到返回-1.
        int index = arraySearch(arr, 5);
        System.out.println(index == -1 ? "该元素不存在" : "该元素下标是：" + index);
    }

    /**
     * 从数组中检索某个元素的下标（返回的是第一个元素的下标。）
     * @param arr 被检索的数组
     * @param ele 被检索的元素
     * @return 大于等于0的数表示元素的下标，-1表示该元素不存在
     */
    public static int arraySearch(int[] arr, int ele) {
        for (int i = 0; i < arr.length; i++) {
            if(ele == arr[i]){
                return i;
            }
        }
        return -1;
    }
}


//--------------------------------------------
package com.bjpowernode.javase.array;

/*
1、数组工具类：自己写的。不是SUN的。

2、关于查找算法中的：二分法查找。
    10(下标0) 11 12 13 14 15 16 17 18 19 20(下标10)   arr数组。

    通过二分法查找，找出18这个元素的下标：
        (0 + 10) / 2 --> 中间元素的下标： 5

    拿着中间这个元素和目标要查找的元素进行对比：
        中间元素是：arr[5] --> 15
        15 < 18(被查找的元素)
        被查找的元素18在目前中间元素15的右边。
        所以开始元素的下标从0变成 5 + 1.

    再重新计算一个中间元素的下标：
        开始下标是：5 + 1
        结束下标是：10
        (6 + 10) / 2 --> 8

    8下标对应的元素arr[8]是18
        找到的中间元素正好和被找的的元素18相等，表示找到了：下标为8

    二分法查找的终止条件：一直折半，直到中间的那个元素恰好是被查找的元素。

3、二分法查找算法是基于排序的基础之上。（没有排序的数据是无法查找的。）

 */
public class ArrayUtil {
    public static void main(String[] args) {

        int[] arr = {100,200,230,235,600,1000,2000,9999};

        // 找出arr这个数组中200所在的下标。
        // 调用方法
        int index = binarySearch(arr, 230);
        System.out.println(index == -1 ? "该元素不存在！" : "该元素下标" + index);
    }

    /**
     * 从数组中查找目标元素的下标。
     * @param arr 被查找的数组（这个必须是已经排序的。）
     * @param dest 目标元素
     * @return -1表示该元素不存在，其它表示返回该元素的下标。
     */
    public static int binarySearch(int[] arr, int dest) {
        // 开始下标
        int begin = 0;
        // 结束下标
        int end = arr.length - 1;
        // 开始元素的下标只要在结束元素下标的左边，就有机会继续循环。
        while(begin <= end) {
            // 中间元素下标
            int mid = (begin + end) / 2;
            if (arr[mid] == dest) {
                return mid;
            } else if (arr[mid] < dest) {
                // 目标在“中间”的右边
                // 开始元素下标需要发生变化（开始元素的下标需要重新赋值）
                begin = mid + 1; // 一直增
            } else {
                // arr[mid] > dest
                // 目标在“中间”的左边
                // 修改结束元素的下标
                end = mid - 1; // 一直减
            }
        }
        return -1;
    }

}

```

## 8. String

### 8.1 字符串的存储原理

``` java
package com.bjpowernode.javase.string;

/*
关于Java JDK中内置的一个类：java.lang.String
    1、String表示字符串类型，属于引用数据类型，不属于基本数据类型。
    2、在java中随便使用双引号括起来的都是String对象。例如："abc"，"def"，"hello world!"，这是3个String对象。
    3、java中规定，双引号括起来的字符串，是不可变的，也就是说"abc"自出生到最终死亡，不可变，不能变成"abcd"，也不能变成"ab"
    4、在JDK当中双引号括起来的字符串，例如："abc" "def"都是直接存储在“方法区”的“字符串常量池”当中的。
    为什么SUN公司把字符串存储在一个“字符串常量池”当中呢。因为字符串在实际的开发中使用太频繁。为了执行效率，
    所以把字符串放到了方法区的字符串常量池当中。
 */
public class StringTest01 {
    public static void main(String[] args) {
        // 这两行代码表示底层创建了3个字符串对象，都在字符串常量池当中。
        String s1 = "abcdef";
        String s2 = "abcdef" + "xy";

        // 分析：这是使用new的方式创建的字符串对象。这个代码中的"xy"是从哪里来的？
        // 凡是双引号括起来的都在字符串常量池中有一份。
        // new对象的时候一定在堆内存当中开辟空间。
        String s3 = new String("xy");

        // i变量中保存的是100这个值。
        int i = 100;
        // s变量中保存的是字符串对象的内存地址。
        // s引用中保存的不是"abc"，是0x1111
        // 而0x1111是"abc"字符串对象在“字符串常量池”当中的内存地址。
        String s = "abc";
    }
}

package com.bjpowernode.javase.string;

public class User {
    private int id;
    private String name;

    public User() {
    }

    public User(int id, String name) {
        this.id = id;
        this.name = name;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}

package com.bjpowernode.javase.string;

public class UserTest {
    public static void main(String[] args) {

        User user = new User(110, "张三");

    }
}

package com.bjpowernode.javase.string;

public class StringTest02 {
    public static void main(String[] args) {
        String s1 = "hello";
        // "hello"是存储在方法区的字符串常量池当中
        // 所以这个"hello"不会新建。（因为这个对象已经存在了！）
        String s2 = "hello";
        // 分析结果是true还是false？
        // == 双等号比较的是不是变量中保存的内存地址？是的。
        System.out.println(s1 == s2); // true

        String x = new String("xyz");
        String y = new String("xyz");
        // 分析结果是true还是false？
        // == 双等号比较的是不是变量中保存的内存地址？是的。
        System.out.println(x == y); //false

        // 通过这个案例的学习，我们知道了，字符串对象之间的比较不能使用“==”
        // "=="不保险。应该调用String类的equals方法。
        // String类已经重写了equals方法，以下的equals方法调用的是String重写之后的equals方法。
        System.out.println(x.equals(y)); // true

        String k = new String("testString");
        //String k = null;
        // "testString"这个字符串可以后面加"."呢？
        // 因为"testString"是一个String字符串对象。只要是对象都能调用方法。
        System.out.println("testString".equals(k)); // 建议使用这种方式，因为这个可以避免空指针异常。
        System.out.println(k.equals("testString")); // 存在空指针异常的风险。不建议这样写。
    }
}

```

### 8.2 面试题

``` java
package com.bjpowernode.javase.string;
/*
分析以下程序，一共创建了几个对象
 */
public class StringTest03 {
    public static void main(String[] args) {
        /*
        一共3个对象：
            方法区字符串常量池中有1个："hello"
            堆内存当中有两个String对象。
            一共3个。
         */
        String s1 = new String("hello");
        String s2 = new String("hello");
    }
}

```

### 8.3 String类的构造方法

``` java
package com.bjpowernode.javase.string;

/**
 * 关于String类中的构造方法。
 *  第一个：String s = new String("");
 *  第二个：String s = ""; 最常用
 *  第三个：String s = new String(char数组);
 *  第四个：String s = new String(char数组,起始下标,长度);
 *  第五个：String s = new String(byte数组);
 *  第六个：String s = new String(byte数组,起始下标,长度)
 */
public class StringTest04 {
    public static void main(String[] args) {

        // 创建字符串对象最常用的一种方式
        String s1 =  "hello world!";
        // s1这个变量中保存的是一个内存地址。
        // 按说以下应该输出一个地址。
        // 但是输出一个字符串，说明String类已经重写了toString()方法。
        System.out.println(s1);//hello world!
        System.out.println(s1.toString()); //hello world!

        // 这里只掌握常用的构造方法。
        byte[] bytes = {97, 98, 99}; // 97是a，98是b，99是c
        String s2 = new String(bytes);

        // 前面说过：输出一个引用的时候，会自动调用toString()方法，默认Object的话，会自动输出对象的内存地址。
        // 通过输出结果我们得出一个结论：String类已经重写了toString()方法。
        // 输出字符串对象的话，输出的不是对象的内存地址，而是字符串本身。
        System.out.println(s2.toString()); //abc
        System.out.println(s2); //abc

        // String(字节数组,数组元素下标的起始位置,长度)
        // 将byte数组中的一部分转换成字符串。
        String s3 = new String(bytes, 1, 2);
        System.out.println(s3); // bc

        // 将char数组全部转换成字符串
        char[] chars = {'我','是','中','国','人'};
        String s4 = new String(chars);
        System.out.println(s4);
        // 将char数组的一部分转换成字符串
        String s5 = new String(chars, 2, 3);
        System.out.println(s5);

        String s6 = new String("helloworld!");
        System.out.println(s6); //helloworld!
    }
}

```

### 8.4 String的方法

``` java
package com.bjpowernode.javase.string;

public class StringTest05 {
    public static void main(String[] args) {

        // String类当中常用方法。
        //1（掌握）.char charAt(int index)
        char c = "中国人".charAt(1); // "中国人"是一个字符串String对象。只要是对象就能“点.”
        System.out.println(c); // 国

        // 2（了解）.int compareTo(String anotherString)
        // 字符串之间比较大小不能直接使用 > < ，需要使用compareTo方法。
        int result = "abc".compareTo("abc");
        System.out.println(result); //0（等于0） 前后一致  10 - 10 = 0

        int result2 = "abcd".compareTo("abce");
        System.out.println(result2); //-1（小于0） 前小后大 8 - 9 = -1

        int result3 = "abce".compareTo("abcd");
        System.out.println(result3); // 1（大于0） 前大后小 9 - 8 = 1

        // 拿着字符串第一个字母和后面字符串的第一个字母比较。能分胜负就不再比较了。
        System.out.println("xyz".compareTo("yxz")); // -1

        // 3（掌握）.boolean contains(CharSequence s)
        // 判断前面的字符串中是否包含后面的子字符串。
        System.out.println("HelloWorld.java".contains(".java")); // true
        System.out.println("http://www.baidu.com".contains("https://")); // false

        // 4（掌握）. boolean endsWith(String suffix)
        // 判断当前字符串是否以某个子字符串结尾。
        System.out.println("test.txt".endsWith(".java")); // false
        System.out.println("test.txt".endsWith(".txt")); // true
        System.out.println("fdsajklfhdkjlsahfjkdsahjklfdss".endsWith("ss")); // true

        // 5（掌握）.boolean equals(Object anObject)
        // 比较两个字符串必须使用equals方法，不能使用“==”
        // equals方法有没有调用compareTo方法？ 老版本可以看一下。JDK13中并没有调用compareTo()方法。
        // equals只能看出相等不相等。
        // compareTo方法可以看出是否相等，并且同时还可以看出谁大谁小。
        System.out.println("abc".equals("abc")); // true

        // 6（掌握）.boolean equalsIgnoreCase(String anotherString)
        // 判断两个字符串是否相等，并且同时忽略大小写。
        System.out.println("ABc".equalsIgnoreCase("abC")); // true

        // 7（掌握）.byte[] getBytes()
        // 将字符串对象转换成字节数组
        byte[] bytes = "abcdef".getBytes();
        for(int i = 0; i < bytes.length; i++){
            System.out.println(bytes[i]);
        }

        // 8（掌握）.int indexOf(String str)
        // 判断某个子字符串在当前字符串中第一次出现处的索引（下标）。
        System.out.println("oraclejavac++.netc#phppythonjavaoraclec++".indexOf("java")); // 6

        // 9（掌握）.boolean isEmpty()
        // 判断某个字符串是否为“空字符串”。底层源代码调用的应该是字符串的length()方法。
        //String s = "";
        String s = "a";
        System.out.println(s.isEmpty());

        // 10（掌握）. int length()
        // 面试题：判断数组长度和判断字符串长度不一样
        // 判断数组长度是length属性，判断字符串长度是length()方法。
        System.out.println("abc".length()); // 3

        System.out.println("".length()); // 0

        // 11（掌握）.int lastIndexOf(String str)
        // 判断某个子字符串在当前字符串中最后一次出现的索引（下标）
        System.out.println("oraclejavac++javac#phpjavapython".lastIndexOf("java")); //22

        // 12（掌握）. String replace(CharSequence target, CharSequence replacement)
        // 替换。
        // String的父接口就是：CharSequence
        String newString = "http://www.baidu.com".replace("http://", "https://");
        System.out.println(newString); //https://www.baidu.com
        // 把以下字符串中的“=”替换成“:”
        String newString2 = "name=zhangsan&password=123&age=20".replace("=", ":");
        System.out.println(newString2); //name:zhangsan&password:123&age:20

        // 13（掌握）.String[] split(String regex)
        // 拆分字符串
        String[] ymd = "1980-10-11".split("-"); //"1980-10-11"以"-"分隔符进行拆分。
        for(int i = 0; i < ymd.length; i++){
            System.out.println(ymd[i]);
        }
        String param = "name=zhangsan&password=123&age=20";
        String[] params = param.split("&");
        for(int i = 0; i <params.length; i++){
            System.out.println(params[i]);
            // 可以继续向下拆分，可以通过“=”拆分。
        }

        // 14（掌握）、boolean startsWith(String prefix)
        // 判断某个字符串是否以某个子字符串开始。
        System.out.println("http://www.baidu.com".startsWith("http")); // true
        System.out.println("http://www.baidu.com".startsWith("https")); // false

        // 15（掌握）、 String substring(int beginIndex) 参数是起始下标。
        // 截取字符串
        System.out.println("http://www.baidu.com".substring(7)); //www.baidu.com

        // 16（掌握）、String substring(int beginIndex, int endIndex)
        // beginIndex起始位置（包括）
        // endIndex结束位置（不包括）
        System.out.println("http://www.baidu.com".substring(7, 10)); //www

        // 17(掌握)、char[] toCharArray()
        // 将字符串转换成char数组
        char[] chars = "我是中国人".toCharArray();
        for(int i = 0; i < chars.length; i++){
            System.out.println(chars[i]);
        }

        // 18（掌握）、String toLowerCase()
        // 转换为小写。
        System.out.println("ABCDefKXyz".toLowerCase());

        // 19（掌握）、String toUpperCase();
        System.out.println("ABCDefKXyz".toUpperCase());

        // 20（掌握）. String trim();
        // 去除字符串前后空白
        System.out.println("           hello      world             ".trim());

        // 21（掌握）. String中只有一个方法是静态的，不需要new对象
        // 这个方法叫做valueOf
        // 作用：将“非字符串”转换成“字符串”
        //String s1 = String.valueOf(true);
        //String s1 = String.valueOf(100);
        //String s1 = String.valueOf(3.14);

        // 这个静态的valueOf()方法，参数是一个对象的时候，会自动调用该对象的toString()方法吗？
        String s1 = String.valueOf(new Customer());
        //System.out.println(s1); // 没有重写toString()方法之前是对象内存地址 com.bjpowernode.javase.string.Customer@10f87f48
        System.out.println(s1); //我是一个VIP客户！！！！

        // 我们是不是可以研究一下println()方法的源代码了？
        System.out.println(100);
        System.out.println(3.14);
        System.out.println(true);

        Object obj = new Object();
        // 通过源代码可以看出：为什么输出一个引用的时候，会调用toString()方法!!!!
        //　本质上System.out.println()这个方法在输出任何数据的时候都是先转换成字符串，再输出。
        System.out.println(obj);

        System.out.println(new Customer());
    }
}

class Customer {
    // 重写toString()方法

    @Override
    public String toString() {
        return "我是一个VIP客户！！！！";
    }
}

```

### 8.5 StringBuffer进行字符串拼接 

``` java
package com.bjpowernode.javase.stringbuffer;

/**
 * 思考：我们在实际的开发中，如果需要进行字符串的频繁拼接，会有什么问题？
 *      因为java中的字符串是不可变的，每一次拼接都会产生新字符串。
 *      这样会占用大量的方法区内存。造成内存空间的浪费。
 *          String s = "abc";
 *          s += "hello";
 *          就以上两行代码，就导致在方法区字符串常量池当中创建了3个对象：
 *              "abc"
 *              "hello"
 *              "abchello"
 */
public class StringBufferTest01 {
    public static void main(String[] args) {
        String s = "";
        // 这样做会给java的方法区字符串常量池带来很大的压力。
        for(int i = 0; i < 100; i++){
            //s += i;
            s = s + i;
            System.out.println(s);
        }
    }
}

package com.bjpowernode.javase.stringbuffer;

/**
 * 如果以后需要进行大量字符串的拼接操作，建议使用JDK中自带的：
 *      java.lang.StringBuffer
 *      java.lang.StringBuilder
 *
 * 如何优化StringBuffer的性能？
 *      在创建StringBuffer的时候尽可能给定一个初始化容量。
 *      最好减少底层数组的扩容次数。预估计一下，给一个大一些初始化容量。
 *      关键点：给一个合适的初始化容量。可以提高程序的执行效率。
 */
public class StringBufferTest02 {
    public static void main(String[] args) {

        // 创建一个初始化容量为16个byte[] 数组。（字符串缓冲区对象）
        StringBuffer stringBuffer = new StringBuffer();

        // 拼接字符串，以后拼接字符串统一调用 append()方法。
        // append是追加的意思。
        stringBuffer.append("a");
        stringBuffer.append("b");
        stringBuffer.append("d");
        stringBuffer.append(3.14);
        stringBuffer.append(true);
        // append方法底层在进行追加的时候，如果byte数组满了，会自动扩容。
        stringBuffer.append(100L);

        System.out.println(stringBuffer.toString());

        // 指定初始化容量的StringBuffer对象（字符串缓冲区对象）
        StringBuffer sb = new StringBuffer(100);
        sb.append("hello");
        sb.append("world");
        sb.append("hello");
        sb.append("kitty");

        System.out.println(sb);
    }
}

```

### 8.6 StringBuilder和StringBuffer的区别

``` java
package com.bjpowernode.javase.stringbuffer;

/*
java.lang.StringBuilder
StringBuffer和StringBuilder的区别？
    StringBuffer中的方法都有：synchronized关键字修饰。表示StringBuffer在多线程环境下运行是安全的。
    StringBuilder中的方法都没有：synchronized关键字修饰，表示StringBuilder在多线程环境下运行是不安全的。

    StringBuffer是线程安全的。
    StringBuilder是非线程安全的。
    
 */
public class StringBuilderTest01 {
    public static void main(String[] args) {

        // 使用StringBuilder也是可以完成字符串的拼接。
        StringBuilder sb = new StringBuilder();
        sb.append(100);
        sb.append(true);
        sb.append("hello");
        sb.append("kitty");
        System.out.println(sb);
    }
}

package com.bjpowernode.javase.stringbuffer;
/*
1、面试题：String为什么是不可变的？
    我看过源代码，String类中有一个byte[]数组，这个byte[]数组采用了final修饰，
    因为数组一旦创建长度不可变。并且被final修饰的引用一旦指向某个对象之后，不
    可再指向其它对象，所以String是不可变的！
        "abc" 无法变成 "abcd"

2、StringBuilder/StringBuffer为什么是可变的呢？
    我看过源代码，StringBuffer/StringBuilder内部实际上是一个byte[]数组，
    这个byte[]数组没有被final修饰，StringBuffer/StringBuilder的初始化
    容量我记得应该是16，当存满之后会进行扩容，底层调用了数组拷贝的方法
    System.arraycopy()...是这样扩容的。所以StringBuilder/StringBuffer
    适合于使用字符串的频繁拼接操作。

 */
public class StringBufferTest04 {
    public static void main(String[] args) {

        // 字符串不可变是什么意思？
        // 是说双引号里面的字符串对象一旦创建不可变。
        String s = "abc"; //"abc"放到了字符串常量池当中。"abc"不可变。

        // s变量是可以指向其它对象的。
        // 字符串不可变不是说以上变量s不可变。说的是"abc"这个对象不可变。
        s = "xyz";//"xyz"放到了字符串常量池当中。"xyz"不可变。

    }
}

```

### 8.7 包装类存在的意义

```java
package com.bjpowernode.javase.integer;
/*
1、java中为8种基本数据类型又对应准备了8种包装类型。8种包装类属于引用数据类型，父类是Object。
2、思考：为什么要再提供8种包装类呢？
    因为8种基本数据类型不够用。
    所以SUN又提供对应的8种包装类型。
 */
public class IntegerTest01 {

    //入口
    public static void main(String[] args) {

        // 有没有这种需求：调用doSome()方法的时候需要传一个数字进去。
        // 但是数字属于基本数据类型，而doSome()方法参数的类型是Object。
        // 可见doSome()方法无法接收基本数据类型的数字。那怎么办呢？可以传一个数字对应的包装类进去。

        // 把100这个数字经过构造方法包装成对象。
        MyInt myInt = new MyInt(100);
        // doSome()方法虽然不能直接传100，但是可以传一个100对应的包装类型。
        doSome(myInt);
    }

    public static void doSome(Object obj){
        //System.out.println(obj);
        System.out.println(obj.toString());
    }
}

package com.bjpowernode.javase.integer;
// 这种包装类目前是我自己写的。实际开发中我们不需要自己写。
// 8种基本数据类型对应的8种包装类，SUN公司已经写好了。我们直接用。
public class MyInt {
    int value;

    public MyInt() {
    }

    public MyInt(int value) {
        this.value = value;
    }

    @Override
    public String toString() {
        return String.valueOf(value);
    }
}

```

### 8.8 八种包装类和拆箱和装箱的概念

``` java
package com.bjpowernode.javase.integer;

/*
1、8种基本数据类型对应的包装类型名是什么？
    基本数据类型              包装类型
    -------------------------------------
    byte                    java.lang.Byte（父类Number）
    short                   java.lang.Short（父类Number）
    int                     java.lang.Integer（父类Number）
    long                    java.lang.Long（父类Number）
    float                   java.lang.Float（父类Number）
    double                  java.lang.Double（父类Number）
    boolean                 java.lang.Boolean（父类Object）
    char                    java.lang.Character（父类Object）

2、以上八种包装类中，重点以java.lang.Integer为代表进行学习，其它的类型照葫芦画瓢就行。

3、八种包装类中其中6个都是数字对应的包装类，他们的父类都是Number，可以先研究一下Number中公共的方法：
    Number是一个抽象类，无法实例化对象。
    Number类中有这样的方法：
        byte byteValue() 以 byte 形式返回指定的数值。
        abstract  double doubleValue()以 double 形式返回指定的数值。
        abstract  float floatValue()以 float 形式返回指定的数值。
        abstract  int intValue()以 int 形式返回指定的数值。
        abstract  long longValue()以 long 形式返回指定的数值。
        short shortValue()以 short 形式返回指定的数值。
        这些方法其实所有的数字包装类的子类都有，这些方法是负责拆箱的。

 */
public class IntegerTest02 {
    public static void main(String[] args) {

        // 123这个基本数据类型，进行构造方法的包装达到了：基本数据类型向引用数据类型的转换。
        // 基本数据类型 -(转换为)->引用数据类型（装箱）
        Integer i = new Integer(123);

        // 将引用数据类型--(转换为)-> 基本数据类型
        float f = i.floatValue();
        System.out.println(f); //123.0

        // 将引用数据类型--(转换为)-> 基本数据类型（拆箱）
        int retValue = i.intValue();
        System.out.println(retValue); //123
    }
}

```

### 8.9 Integer的构造方法和Double的构造方法

``` java
package com.bjpowernode.javase.integer;

/*
关于Integer类的构造方法，有两个：
    Integer(int)
    Integer(String)
 */
public class IntegerTest03 {
    public static void main(String[] args) {

        // Java9之后不建议使用这个构造方法了。出现横线表示已过时。
        // 将数字100转换成Integer包装类型（int --> Integer）
        Integer x = new Integer(100);
        System.out.println(x);

        // 将String类型的数字，转换成Integer包装类型。（String --> Integer）
        Integer y = new Integer("123");
        System.out.println(y);

        // double -->Double
        Double d = new Double(1.23);
        System.out.println(d);

        // String --> Double
        Double e = new Double("3.14");
        System.out.println(e);
    }
}

```

### 8.10 通过常量获取最大值和最小值

``` java
package com.bjpowernode.javase.integer;

public class IntegerTest04 {
    public static void main(String[] args) {
        // 通过访问包装类的常量，来获取最大值和最小值
        System.out.println("int的最大值：" + Integer.MAX_VALUE);
        System.out.println("int的最小值：" + Integer.MIN_VALUE);
        System.out.println("byte的最大值：" + Byte.MAX_VALUE);
        System.out.println("byte的最小值：" + Byte.MIN_VALUE);
    }
}

```

### 8.11自动装箱和自动拆箱

``` java
package com.bjpowernode.javase.integer;

/**
 * 好消息：在java5之后，引入了一种新特性，自动装箱和自动拆箱
 *  自动装箱：基本数据类型自动转换成包装类。
 *  自动拆箱：包装类自动转换成基本数据类型。
 *
 * 有了自动拆箱之后，Number类中的方法就用不着了！
 *
 * 自动装箱和自动拆箱的好处？
 *      方便编程。
 */
public class IntegerTest05 {
    public static void main(String[] args) {

        // 900是基本数据类型
        // x是包装类型
        // 基本数据类型 --(自动转换)--> 包装类型：自动装箱
        Integer x = 900;
        System.out.println(x);

        // x是包装类型
        // y是基本数据类型
        // 包装类型 --(自动转换)--> 基本数据类型：自动拆箱
        int y = x;
        System.out.println(y);

        // z是一个引用，z是一个变量，z还是保存了一个对象的内存地址。
        Integer z = 1000; // 等同于：Integer z = new Integer(1000);
        // 分析为什么这个没有报错呢？
        // +两边要求是基本数据类型的数字，z是包装类，不属于基本数据类型，这里会进行自动拆箱。将z转换成基本数据类型
        // 在java5之前你这样写肯定编译器报错。
        System.out.println(z + 1);

        Integer a = 1000; // Integer a = new Integer(1000); a是个引用，保存内存地址指向对象。
        Integer b = 1000; // Integer b = new Integer(1000); b是个引用，保存内存地址指向对象。
        // == 比较的是对象的内存地址，a和b两个引用中保存的对象内存地址不同。
        // == 这个运算符不会触发自动拆箱机制。（只有+ - * /等运算的时候才会。）
        System.out.println(a == b); //false
    }
}

```

### 8.12 String为什么是不可以变的

``` java
package com.bjpowernode.javase.stringbuffer;
/*
1、面试题：String为什么是不可变的？
    我看过源代码，String类中有一个byte[]数组，这个byte[]数组采用了final修饰，
    因为数组一旦创建长度不可变。并且被final修饰的引用一旦指向某个对象之后，不
    可再指向其它对象，所以String是不可变的！
        "abc" 无法变成 "abcd"

2、StringBuilder/StringBuffer为什么是可变的呢？
    我看过源代码，StringBuffer/StringBuilder内部实际上是一个byte[]数组，
    这个byte[]数组没有被final修饰，StringBuffer/StringBuilder的初始化
    容量我记得应该是16，当存满之后会进行扩容，底层调用了数组拷贝的方法
    System.arraycopy()...是这样扩容的。所以StringBuilder/StringBuffer
    适合于使用字符串的频繁拼接操作。

 */
public class StringBufferTest04 {
    public static void main(String[] args) {

        // 字符串不可变是什么意思？
        // 是说双引号里面的字符串对象一旦创建不可变。
        String s = "abc"; //"abc"放到了字符串常量池当中。"abc"不可变。

        // s变量是可以指向其它对象的。
        // 字符串不可变不是说以上变量s不可变。说的是"abc"这个对象不可变。
        s = "xyz";//"xyz"放到了字符串常量池当中。"xyz"不可变。

    }
}

package com.bjpowernode.javase.integer;

/*
这个题目是Integer非常重要的面试题。
 */
public class IntegerTest06 {
    public static void main(String[] args) {

        Integer a = 128;
        Integer b = 128;
        System.out.println(a == b); //false

        /*
        java中为了提高程序的执行效率，将[-128到127]之间所有的包装对象提前创建好，
        放到了一个方法区的“整数型常量池”当中了，目的是只要用这个区间的数据不需要
        再new了，直接从整数型常量池当中取出来。

        原理：x变量中保存的对象的内存地址和y变量中保存的对象的内存地址是一样的。
         */
        Integer x = 127;
        Integer y = 127;
        // == 永远判断的都是两个对象的内存地址是否相同。
        System.out.println(x == y); //true
    }
}

```

### 8.13 Integer常用方法和NumberFormatException异常

``` java
package com.bjpowernode.javase.integer;

import jdk.swing.interop.SwingInterOpUtils;

/*
总结一下之前所学的经典异常？
    空指针异常：NullPointerException
    类型转换异常：ClassCastException
    数组下标越界异常：ArrayIndexOutOfBoundsException
    数字格式化异常：NumberFormatException

Integer类当中有哪些常用的方法呢？
 */
public class IntegerTest07 {
    public static void main(String[] args) {

        // 手动装箱
        Integer x = new Integer(1000);

        // 手动拆箱。
        int y = x.intValue();
        System.out.println(y);

        Integer a = new Integer("123");

        // 编译的时候没问题，一切符合java语法，运行时会不会出问题呢？
        // 不是一个“数字”可以包装成Integer吗？不能。运行时出现异常。
        // java.lang.NumberFormatException
        //Integer a = new Integer("中文");

        // 重点方法
        // static int parseInt(String s)
        // 静态方法，传参String，返回int
        //网页上文本框中输入的100实际上是"100"字符串。后台数据库中要求存储100数字，此时java程序需要将"100"转换成100数字。
        int retValue = Integer.parseInt("123"); // String -转换-> int
        //int retValue = Integer.parseInt("中文"); // NumberFormatException
        System.out.println(retValue + 100);

        // 照葫芦画瓢
        double retValue2 = Double.parseDouble("3.14");
        System.out.println(retValue2 + 1); //4.140000000000001（精度问题）

        float retValue3 = Float.parseFloat("1.0");
        System.out.println(retValue3 + 1); //2.0

        // -----------------------------------以下内容作为了解，不需要掌握---------------------------------------
        // static String toBinaryString(int i)
        // 静态的：将十进制转换成二进制字符串。
        String binaryString = Integer.toBinaryString(3);
        System.out.println(binaryString); //"11" 二进制字符串

        // static String toHexString(int i)
        // 静态的：将十进制转换成十六进制字符串。
        String hexString = Integer.toHexString(16);
        System.out.println(hexString); // "10"

        // 十六进制：1 2 3 4 5 6 7 8 9 a b c d e f 10 11 12 13 14 15 16 17 18 19 1a
        hexString = Integer.toHexString(17);
        System.out.println(hexString); // "11"

        //static String toOctalString(int i)
        // 静态的：将十进制转换成八进制字符串。
        String octalString = Integer.toOctalString(8);
        System.out.println(octalString); // "10"

        System.out.println(new Object()); //java.lang.Object@6e8cf4c6

        // valueOf方法作为了解
        //static Integer valueOf(int i)
        // 静态的：int-->Integer
        Integer i1 = Integer.valueOf(100);
        System.out.println(i1);

        // static Integer valueOf(String s)
        // 静态的：String-->Integer
        Integer i2 = Integer.valueOf("100");
        System.out.println(i2);
    }
}

```

![day26-String Integer int三种类型的互相转换](E:\java\JavaSE\JavaSE进阶每日复习笔记\day26-String Integer int三种类型的互相转换.png)

### 8.14 integer和int装换

```java
package com.bjpowernode.javase.integer;

/**
 * String int Integer之间互相转换
 */
public class IntegerTest08 {
    public static void main(String[] args) {

        // String --> int
        int i1 = Integer.parseInt("100"); // i1是100数字
        System.out.println(i1 + 1); // 101

        // int --> String
        String s2 = i1 + ""; // "100"字符串
        System.out.println(s2 + 1); // "1001"

        // int --> Integer
        // 自动装箱
        Integer x = 1000;

        // Integer --> int
        // 自动拆箱
        int y = x;

        // String --> Integer
        Integer k = Integer.valueOf("123");

        // Integer --> String
        String e = String.valueOf(k);
    }
}

```

## 9.  Java对日期的处理和统计方法执行时长和通过毫秒构造Date方法

```java
package com.bjpowernode.javase.date;

import java.text.SimpleDateFormat;
import java.util.Date;

/*
java中对日期的处理
    这个案例最主要掌握：
        知识点1：怎么获取系统当前时间
        知识点2：String ---> Date
        知识点3：Date ---> String
 */
public class DateTest01 {
    public static void main(String[] args) throws Exception {

        // 获取系统当前时间（精确到毫秒的系统当前时间）
        // 直接调用无参数构造方法就行。
        Date nowTime = new Date();

        // java.util.Date类的toString()方法已经被重写了。
        // 输出的应该不是一个对象的内存地址，应该是一个日期字符串。
        //System.out.println(nowTime); //Thu Mar 05 10:51:06 CST 2020

        // 日期可以格式化吗？
        // 将日期类型Date，按照指定的格式进行转换：Date --转换成具有一定格式的日期字符串-->String
        // SimpleDateFormat是java.text包下的。专门负责日期格式化的。
        /*
        yyyy 年(年是4位)
        MM 月（月是2位）
        dd 日
        HH 时
        mm 分
        ss 秒
        SSS 毫秒（毫秒3位，最高999。1000毫秒代表1秒）
        注意：在日期格式中，除了y M d H m s S这些字符不能随便写之外，剩下的符号格式自己随意组织。
         */
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss SSS");
        //SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy");
        //SimpleDateFormat sdf = new SimpleDateFormat("yy/MM/dd HH:mm:ss");

        String nowTimeStr = sdf.format(nowTime);
        System.out.println(nowTimeStr);

        // 假设现在有一个日期字符串String，怎么转换成Date类型？
        // String --> Date
        String time = "2008-08-08 08:08:08 888";
        //SimpleDateFormat sdf2 = new SimpleDateFormat("格式不能随便写，要和日期字符串格式相同");
        // 注意：字符串的日期格式和SimpleDateFormat对象指定的日期格式要一致。不然会出现异常：java.text.ParseException
        SimpleDateFormat sdf2 = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss SSS");
        Date dateTime = sdf2.parse(time);
        System.out.println(dateTime); //Fri Aug 08 08:08:08 CST 2008

    }
}

package com.bjpowernode.javase.date;
/*
获取自1970年1月1日 00:00:00 000到当前系统时间的总毫秒数。
1秒 = 1000毫秒

简单总结一下System类的相关属性和方法：
    System.out 【out是System类的静态变量。】
    System.out.println() 【println()方法不是System类的，是PrintStream类的方法。】
    System.gc() 建议启动垃圾回收器
    System.currentTimeMillis() 获取自1970年1月1日到系统当前时间的总毫秒数。
    System.exit(0) 退出JVM。
 */
public class DateTest02 {
    public static void main(String[] args) {
        // 获取自1970年1月1日 00:00:00 000到当前系统时间的总毫秒数。
        long nowTimeMillis = System.currentTimeMillis();
        System.out.println(nowTimeMillis); //1583377912981

        // 统计一个方法耗时
        // 在调用目标方法之前记录一个毫秒数
        long begin = System.currentTimeMillis();
        print();
        // 在执行完目标方法之后记录一个毫秒数
        long end = System.currentTimeMillis();
        System.out.println("耗费时长"+(end - begin)+"毫秒");
    }

    // 需求：统计一个方法执行所耗费的时长
    public static void print(){
        for(int i = 0; i < 1000000000; i++){
            System.out.println("i = " + i);
        }
    }
}

package com.bjpowernode.javase.date;

import java.text.SimpleDateFormat;
import java.util.Date;

/*
java中对日期的处理
    这个案例最主要掌握：
        知识点1：怎么获取系统当前时间
        知识点2：String ---> Date
        知识点3：Date ---> String
 */
public class DateTest01 {
    public static void main(String[] args) throws Exception {

        // 获取系统当前时间（精确到毫秒的系统当前时间）
        // 直接调用无参数构造方法就行。
        Date nowTime = new Date();

        // java.util.Date类的toString()方法已经被重写了。
        // 输出的应该不是一个对象的内存地址，应该是一个日期字符串。
        //System.out.println(nowTime); //Thu Mar 05 10:51:06 CST 2020

        // 日期可以格式化吗？
        // 将日期类型Date，按照指定的格式进行转换：Date --转换成具有一定格式的日期字符串-->String
        // SimpleDateFormat是java.text包下的。专门负责日期格式化的。
        /*
        yyyy 年(年是4位)
        MM 月（月是2位）
        dd 日
        HH 时
        mm 分
        ss 秒
        SSS 毫秒（毫秒3位，最高999。1000毫秒代表1秒）
        注意：在日期格式中，除了y M d H m s S这些字符不能随便写之外，剩下的符号格式自己随意组织。
         */
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss SSS");
        //SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy");
        //SimpleDateFormat sdf = new SimpleDateFormat("yy/MM/dd HH:mm:ss");

        String nowTimeStr = sdf.format(nowTime);
        System.out.println(nowTimeStr);

        // 假设现在有一个日期字符串String，怎么转换成Date类型？
        // String --> Date
        String time = "2008-08-08 08:08:08 888";
        //SimpleDateFormat sdf2 = new SimpleDateFormat("格式不能随便写，要和日期字符串格式相同");
        // 注意：字符串的日期格式和SimpleDateFormat对象指定的日期格式要一致。不然会出现异常：java.text.ParseException
        SimpleDateFormat sdf2 = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss SSS");
        Date dateTime = sdf2.parse(time);
        System.out.println(dateTime); //Fri Aug 08 08:08:08 CST 2008

    }
}

```

## 10.数字类

### 10.1 数字格式化和高精度BigDecimal

``` java
package com.bjpowernode.javase.number;

import java.text.DecimalFormat;

/*
关于数字的格式化。（了解）
 */
public class DecimalFormatTest01 {
    public static void main(String[] args) {
        // java.text.DecimalFormat专门负责数字格式化的。
        //DecimalFormat df = new DecimalFormat("数字格式");

        /*
        数字格式有哪些？
            # 代表任意数字
            , 代表千分位
            . 代表小数点
            0 代表不够时补0

            ###,###.##
                表示：加入千分位，保留2个小数。
         */
        DecimalFormat df = new DecimalFormat("###,###.##");
        //String s = df.format(1234.56);
        String s = df.format(1234.561232);
        System.out.println(s); // "1,234.56"

        DecimalFormat df2 = new DecimalFormat("###,###.0000"); //保留4个小数位，不够补上0
        String s2 = df2.format(1234.56);
        System.out.println(s2); // "1,234.5600"

    }
}


package com.bjpowernode.javase.number;

import java.math.BigDecimal;

/*
1、BigDecimal 属于大数据，精度极高。不属于基本数据类型，属于java对象（引用数据类型）
这是SUN提供的一个类。专门用在财务软件当中。

2、注意：财务软件中double是不够的。咱们之前有一个学生去用友面试，经理就问了这样一个问题：
    你处理过财务数据吗？用的哪一种类型？
        千万别说double，说java.math.BigDecimal
 */
public class BigDecimalTest01 {
    public static void main(String[] args) {

        // 这个100不是普通的100，是精度极高的100
        BigDecimal v1 = new BigDecimal(100);
        // 精度极高的200
        BigDecimal v2 = new BigDecimal(200);
        // 求和
        // v1 + v2; // 这样不行，v1和v2都是引用，不能直接使用+求和。
        BigDecimal v3 = v1.add(v2); // 调用方法求和。
        System.out.println(v3); //300

        BigDecimal v4 = v2.divide(v1);
        System.out.println(v4); // 2
    }
}

```

## 11.随机数

### 11.1 产生随机数

``` java
package com.bjpowernode.javase.random;

import java.util.Random;

/**
 * 随机数
 */
public class RandomTest01 {
    public static void main(String[] args) {
        // 创建随机数对象
        Random random = new Random();

        // 随机产生一个int类型取值范围内的数字。
        int num1 = random.nextInt();

        System.out.println(num1);

        // 产生[0~100]之间的随机数。不能产生101。
        // nextInt翻译为：下一个int类型的数据是101，表示只能取到100.
        int num2 = random.nextInt(101); //不包括101
        System.out.println(num2);
    }
}

```

### 11.2 生成五个不同的随机数

``` java
package com.bjpowernode.javase.random;

import java.util.Arrays;
import java.util.Random;

/*
编写程序，生成5个不重复的随机数[0-100]。重复的话重新生成。
最终生成的5个随机数放到数组中，要求数组中这5个随机数不重复。
 */
public class RandomTest02 {
    public static void main(String[] args) {

        // 创建Random对象
        Random random = new Random();

        // 准备一个长度为5的一维数组。
        int[] arr = new int[5]; // 默认值都是0
        for(int i = 0; i < arr.length; i++){
            arr[i] = -1;
        }

        // 循环，生成随机数
        int index = 0;
        while(index < arr.length){
            // 生成随机数
            //int num = random.nextInt(101);
            //int num = random.nextInt(6); // 只能生成[0-5]的随机数！
            int num = random.nextInt(4); // 只能生成[0-3]的随机数！永远都有重复的，永远都凑不够5个。
            System.out.println("生成的随机数：" + num);
            // 判断arr数组中有没有这个num
            // 如果没有这个num，就放进去。
            if(!contains(arr, num)){
                arr[index++] = num;
            }
        }

        // 遍历以上的数组
        for(int i = 0; i < arr.length; i++){
            System.out.println(arr[i]);
        }
    }

    /**
     * 单独编写一个方法，这个方法专门用来判断数组中是否包含某个元素
     * @param arr 数组
     * @param key 元素
     * @return true表示包含，false表示不包含。
     */
    public static boolean contains(int[] arr, int key){
        /*
        // 这个方案bug。（排序出问题了。）
        // 对数组进行升序
        //Arrays.sort(arr);
        // 进行二分法查找
        // 二分法查找的结果 >= 0说明，这个元素找到了，找到了表示存在！
        //return Arrays.binarySearch(arr, key) >= 0;
         */

        for(int i = 0; i < arr.length; i++){
            if(arr[i] == key){
                // 条件成立了表示包含，返回true
                return true;
            }
        }
        // 这个就表示不包含！
        return false;
    }

}

```

## 12. 枚举

### 12.1 为什么使用枚举

``` java
package com.bjpowernode.javase.enum2; // 标识符，关键字不能做标识符。enum是关键字。
/*
这个案例没有使用java中的枚举，分析以下程序，在设计方面有什么缺陷？
    以下代码可以编译，也可以运行。这些都没有问题。
    就是设计上你觉得有什么缺陷？

 */
public class EnumTest01 {
    public static void main(String[] args) {

        //System.out.println(10 / 0); //java.lang.ArithmeticException: / by zero
        /*
        int retValue = divide(10, 2);
        System.out.println(retValue == 1 ? "计算成功" : "计算失败"); // 1

        int retValue2 = divide(10, 0);
        System.out.println(retValue2 == 0 ? "计算失败" : "计算成功"); // 0
         */

        boolean success = divide(10, 0);
        System.out.println(success ? "计算成功" : "计算失败");
    }

    /**
     * 需求（这是设计者说的！）：以下程序，计算两个int类型数据的商，计算成功返回1，计算失败返回0
     * @param a int类型的数据
     * @param b int类型的数据
     * @return 返回1表示成功，返回0表示失败！
     */
    /*
    public static int divide(int a, int b){
        try {
            int c = a / b;
            // 程序执行到此处表示以上代码没有发生异常。表示执行成功！
            return 1;
        } catch (Exception e){
            // 程序执行到此处表示以上程序出现了异常！
            // 表示执行失败！
            return 0;
        }
    }
     */

    // 设计缺陷？在这个方法的返回值类型上。返回一个int不恰当。
    // 既然最后的结果只是成功和失败，最好使用布尔类型。因为布尔类型true和false正好可以表示两种不同的状态。
    /*
    public static int divide(int a, int b){
        try {
            int c = a / b;
            // 返回10已经偏离了需求，实际上已经出错了，但是编译器没有检查出来。
            // 我们一直想追求的是：所有的错误尽可能让编译器找出来，所有的错误越早发现越好！
            return 10;
        } catch (Exception e){
            return 0;
        }
    }
    */

    // 这种设计不错。
    public static boolean divide(int a, int b){
        try {
            int c = a / b;
            return true;
        } catch (Exception e){
            return false;
        }
    }

    /*
    思考：以上的这个方法设计没毛病，挺好，返回true和false表示两种情况，
    但是在以后的开发中，有可能遇到一个方法的执行结果可能包括三种情况，
    四种情况，五种情况不等，但是每一个都是可以数清楚的，一枚一枚都是可以
    列举出来的。这个布尔类型就无法满足需求了。此时需要使用java语言中的
    枚举类型。
     */

}

```

### 12.2 枚举的使用

```java
package com.bjpowernode.javase.enum2;

// 采用枚举的方式改造程序
/*
总结：
    1、枚举是一种引用数据类型
    2、枚举类型怎么定义，语法是？
        enum 枚举类型名{
            枚举值1,枚举值2
        }
    3、结果只有两种情况的，建议使用布尔类型。
    结果超过两种并且还是可以一枚一枚列举出来的，建议使用枚举类型。
        例如：颜色、四季、星期等都可以使用枚举类型。
 */
public class EnumTest02 {
    public static void main(String[] args) {
        Result r = divide(10, 2);
        System.out.println(r == Result.SUCCESS ? "计算成功" : "计算失败");
    }

    /**
     * 计算两个int类型数据的商。
     * @param a int数据
     * @param b int数据
     * @return Result.SUCCESS表示成功，Result.FAIL表示失败！
     */
    public static Result divide(int a, int b){
        try {
            int c = a / b;
            return Result.SUCCESS;
        } catch (Exception e){
            return Result.FAIL;
        }
    }
}

// 枚举：一枚一枚可以列举出来的，才建议使用枚举类型。
// 枚举编译之后也是生成class文件。
// 枚举也是一种引用数据类型。
// 枚举中的每一个值可以看做是常量。
enum Result{
    // SUCCESS 是枚举Result类型中的一个值
    // FAIL 是枚举Result类型中的一个值
    // 枚举中的每一个值，可以看做是“常量”
    SUCCESS, FAIL
}

package com.bjpowernode.javase.enum2;

/**
 * 颜色枚举类型
 */
public enum Color {
    /**
     * 颜色值
     */
    RED,BLUE,YELLOW,BLACK
}

/*
class MyClass {
    public static final String RED = "red";
    public static final String BLUE = "blue";
    public static final String YELLOW = "yellow";
    public static final String BLACK = "black";

    public static void main(String[] args) {
        String c = MyClass.RED;
        System.out.println(c);

        // RED
        System.out.println(Color.RED);
    }
}
*/

package com.bjpowernode.javase.enum2;

/**
 * 四季枚举类型
 */
public enum Season {
    /*
    春夏秋冬
     */
    SPRING, SUMMER, AUTUMN, WINTER
}

package com.bjpowernode.javase.enum2;

public class SwitchTest {
    public static void main(String[] args) {
        // switch语句支持枚举类型
        // switch也支持String、int
        // 低版本的JDK，只支持int
        // 高版本的JDK，支持int、String、枚举。
        // byte short char也可以，因为存在自动类型转换。
        switch (Season.SPRING) {
            // 必须省略Season.
            case SPRING:
                System.out.println("春天");
                break;
            case SUMMER:
                System.out.println("夏天");
                break;
            case AUTUMN:
                System.out.println("秋天");
                break;
            case WINTER:
                System.out.println("冬天");
                break;
        }

    }
}


```

## 13. 异常

### 13.1 异常概述

``` java
package com.bjpowernode.javase.exception;
/*
1、什么是异常，java提供异常处理机制有什么用？
    以下程序执行过程中发生了不正常的情况，而这种不正常的情况叫做：异常
    java语言是很完善的语言，提供了异常的处理方式，以下程序执行过程中出现了不正常情况，
    java把该异常信息打印输出到控制台，供程序员参考。程序员看到异常信息之后，可以对
    程序进行修改，让程序更加的健壮。

    什么是异常：程序执行过程中的不正常情况。
    异常的作用：增强程序的健壮性。

2、以下程序执行控制台出现了：
    Exception in thread "main" java.lang.ArithmeticException: / by zero
	    at com.bjpowernode.javase.exception.ExceptionTest01.main(ExceptionTest01.java:14)
	这个信息被我们称为：异常信息。这个信息是JVM打印的。
 */
public class ExceptionTest01 {
    public static void main(String[] args) {
        int a = 10;
        int b = 0;
        // 实际上JVM在执行到此处的时候，会new异常对象：new ArithmeticException("/ by zero");
        // 并且JVM将new的异常对象抛出，打印输出信息到控制台了。
        int c = a / b;
        System.out.println(a + "/" + b + "=" + c);

        // 此处运行也会创建一个：ArithmeticException类型的异常对象。
        //System.out.println(100 / 0);

        // 我观察到异常信息之后，对程序进行修改，更加健壮。
        /*
        int a = 10;
        int b = 2;
        if(b == 0) {
            System.out.println("除数不能为0");
            return;
        }
        // 程序执行到此处表示除数一定不是0
        int c = a / b;
        System.out.println(a + "/" + b + "=" + c);
         */
    }
}

```

### 13.2 Java中异常以类和对象的形式存在

``` java
package com.bjpowernode.javase.exception;

/*
java语言中异常是以什么形式存在的呢？
    1、异常在java中以类的形式存在，每一个异常类都可以创建异常对象。
    2、异常对应的现实生活中是怎样的？
        火灾(异常类)：
            2008年8月8日,小明家着火了（异常对象）
            2008年8月9日,小刚家着火了（异常对象）
            2008年9月8日,小红家着火了（异常对象）

        类是：模板。
        对象是：实际存在的个体。

        钱包丢了（异常类）：
            2008年1月8日，小明的钱包丢了（异常对象）
            2008年1月9日，小芳的钱包丢了（异常对象）
            ....
 */
public class ExceptionTest02 {
    public static void main(String[] args) {

        // 通过“异常类”实例化“异常对象”
        NumberFormatException nfe = new NumberFormatException("数字格式化异常！");

        // java.lang.NumberFormatException: 数字格式化异常！
        System.out.println(nfe);

        // 通过“异常类”创建“异常对象”
        NullPointerException npe = new NullPointerException("空指针异常发生了！");

        //java.lang.NullPointerException: 空指针异常发生了！
        System.out.println(npe);
    }
}

```

### 13.3 UML以及starUML和异常的继承结构和编译时异常和运行时异常区别和异常的处理方法和异常的两种处理方式

> 1.1、异常在java中以类和对象的形式存在。那么异常的继承结构是怎样的？
> 我们可以使用UML图来描述一下继承结构。
> 画UML图有很多工具，例如：Rational Rose（收费的）、starUML等....
> 	Object
> 	Object下有Throwable（可抛出的）
> 	Throwable下有两个分支：Error（不可处理，直接退出JVM）和Exception（可处理的）
> 	Exception下有两个分支：
> 		Exception的直接子类：编译时异常（要求程序员在编写程序阶段必须预先对这些异常进行处理，如果不处理编译器报错，因此得名编译时异常。）。
> 		RuntimeException：运行时异常。（在编写程序阶段程序员可以预先处理，也可以不管，都行。）
>
> 1.2、编译时异常和运行时异常，都是发生在运行阶段。编译阶段异常是不会发生的。
> 编译时异常因为什么而得名？
> 	因为编译时异常必须在编译(编写)阶段预先处理，如果不处理编译器报错，因此得名。
> 	所有异常都是在运行阶段发生的。因为只有程序运行阶段才可以new对象。
> 	因为异常的发生就是new异常对象。
>
> 1.3、编译时异常和运行时异常的区别？
>
> 	编译时异常一般发生的概率比较高。
> 		举个例子：
> 			你看到外面下雨了，倾盆大雨的。
> 			你出门之前会预料到：如果不打伞，我可能会生病（生病是一种异常）。
> 			而且这个异常发生的概率很高，所以我们出门之前要拿一把伞。
> 			“拿一把伞”就是对“生病异常”发生之前的一种处理方式。
> 																																					
> 			对于一些发生概率较高的异常，需要在运行之前对其进行预处理。
> 																																					
> 	运行时异常一般发生的概率比较低。
> 		举个例子：
> 			小明走在大街上，可能会被天上的飞机轮子砸到。
> 			被飞机轮子砸到也算一种异常。
> 			但是这种异常发生概率较低。
> 			在出门之前你没必要提前对这种发生概率较低的异常进行预处理。
> 			如果你预处理这种异常，你将活的很累。
> 																																					
> 	假设你在出门之前，你把能够发生的异常都预先处理，你这个人会更加
> 	的安全，但是你这个人活的很累。
> 																																					
> 	假设java中没有对异常进行划分，没有分为：编译时异常和运行时异常，
> 	所有的异常都需要在编写程序阶段对其进行预处理，将是怎样的效果呢？
> 		首先，如果这样的话，程序肯定是绝对的安全的。
> 		但是程序员编写程序太累，代码到处都是处理异常
> 		的代码。
>
> 1.4、编译时异常还有其他名字：
> 	受检异常：CheckedException
> 	受控异常
>
> 1.5、运行时异常还有其它名字：
> 	未受检异常：UnCheckedException
> 	非受控异常
>
> 1.6、再次强调：所有异常都是发生在运行阶段的。
>
> 1.7、Java语言中对异常的处理包括两种方式：
>
> 	第一种方式：在方法声明的位置上，使用throws关键字，抛给上一级。
> 		谁调用我，我就抛给谁。抛给上一级。
> 																																					
> 	第二种方式：使用try..catch语句进行异常的捕捉。
> 		这件事发生了，谁也不知道，因为我给抓住了。
> 																																					
> 	举个例子：
> 		我是某集团的一个销售员，因为我的失误，导致公司损失了1000元，
> 		“损失1000元”这可以看做是一个异常发生了。我有两种处理方式，
> 		第一种方式：我把这件事告诉我的领导【异常上抛】
> 		第二种方式：我自己掏腰包把这个钱补上。【异常的捕捉】
> 																																						
> 		张三 --> 李四 ---> 王五 --> CEO
> 																																					
> 	思考：
> 		异常发生之后，如果我选择了上抛，抛给了我的调用者，调用者需要
> 		对这个异常继续处理，那么调用者处理这个异常同样有两种处理方式。
>
> 1.8、注意：Java中异常发生之后如果一直上抛，最终抛给了main方法，main方法继续
> 向上抛，抛给了调用者JVM，JVM知道这个异常发生，只有一个结果。终止java程序的执行。

### 13.4  运行时异常编写程序是可以不写

``` java
package com.bjpowernode.javase.exception;

public class ExceptionTest03 {
    public static void main(String[] args) {
        /*
        程序执行到此处发生了ArithmeticException异常，
        底层new了一个ArithmeticException异常对象，
        然后抛出了，由于是main方法调用了100 / 0，
        所以这个异常ArithmeticException抛给了main方法，
        main方法没有处理，将这个异常自动抛给了JVM。
        JVM最终终止程序的执行。

        ArithmeticException 继承 RuntimeException，属于运行时异常。
        在编写程序阶段不需要对这种异常进行预先的处理。
         */
        System.out.println(100 / 0);

        // 这里的HelloWorld没有输出，没有执行。
        System.out.println("Hello World!");
    }
}

```

### 13.5 方法位置上使用throws

``` java
package com.bjpowernode.javase.exception;

/*
以下代码报错的原因是什么？
    因为doSome()方法声明位置上使用了：throws ClassNotFoundException
    而ClassNotFoundException是编译时异常。必须编写代码时处理，没有处理
    编译器报错。
 */
public class ExceptionTest04 {
    public static void main(String[] args) {
        // main方法中调用doSome()方法
        // 因为doSome()方法声明位置上有：throws ClassNotFoundException
        // 我们在调用doSome()方法的时候必须对这种异常进行预先的处理。
        // 如果不处理，编译器就报错。
        //编译器报错信息： Unhandled exception: java.lang.ClassNotFoundException
        //doSome();
    }

    /**
     * doSome方法在方法声明的位置上使用了：throws ClassNotFoundException
     * 这个代码表示doSome()方法在执行过程中，有可能会出现ClassNotFoundException异常。
     * 叫做类没找到异常。这个异常直接父类是：Exception，所以ClassNotFoundException属于编译时异常。
     * @throws ClassNotFoundException
     */
    public static void doSome() throws ClassNotFoundException{
        System.out.println("doSome!!!!");
    }

}

```

### 13.6 异常处理原理

``` java
package com.bjpowernode.javase.exception;

public class ExceptionTest05 {
    // 第一种处理方式：在方法声明的位置上继续使用：throws，来完成异常的继续上抛。抛给调用者。
    // 上抛类似于推卸责任。（继续把异常传递给调用者。）
    /*
    public static void main(String[] args) throws ClassNotFoundException {
        doSome();
    }
     */

    // 第二种处理方式：try..catch进行捕捉。
    // 捕捉等于把异常拦下了，异常真正的解决了。（调用者是不知道的。）
    public static void main(String[] args) {
        try {
            doSome();
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        }
    }

    public static void doSome() throws ClassNotFoundException{
        System.out.println("doSome!!!!");
    }

}

```

### 13.7 异常捕捉和上报的联合使用

``` java
package com.bjpowernode.javase.exception;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

/*
处理异常的第一种方式：
    在方法声明的位置上使用throws关键字抛出，谁调用我这个方法，我就抛给谁。抛给调用者来处理。
    这种处理异常的态度：上报。

处理异常的第二种方式：
    使用try..catch语句对异常进行捕捉。
    这个异常不会上报，自己把这个事儿处理了。
    异常抛到此处为止，不再上抛了。

注意：
    只要异常没有捕捉，采用上报的方式，此方法的后续代码不会执行。
    另外需要注意，try语句块中的某一行出现异常，该行后面的代码不会执行。
    try..catch捕捉异常之后，后续代码可以执行。

在以后的开发中，处理编译时异常，应该上报还是捕捉呢，怎么选？
    如果希望调用者来处理，选择throws上报。
    其它情况使用捕捉的方式。
 */
public class ExceptionTest06 {
    // 一般不建议在main方法上使用throws，因为这个异常如果真正的发生了，一定会抛给JVM。JVM只有终止。
    // 异常处理机制的作用就是增强程序的健壮性。怎么能做到，异常发生了也不影响程序的执行。所以
    // 一般main方法中的异常建议使用try..catch进行捕捉。main就不要继续上抛了。
    /*
    public static void main(String[] args) throws FileNotFoundException {
        System.out.println("main begin");
        m1();
        System.out.println("main over");
    }
     */
    public static void main(String[] args) {

        // 100 / 0这是算术异常，这个异常是运行时异常，你在编译阶段，可以处理，也可以不处理。编译器不管。
        //System.out.println(100 / 0); // 不处理编译器也不管
        // 你处理也可以。
        /*
        try {
            System.out.println(100 / 0);
        } catch(ArithmeticException e){
            System.out.println("算术异常了！！！！");
        }
         */

        System.out.println("main begin");
        try {
            // try尝试
            m1();
            // 以上代码出现异常，直接进入catch语句块中执行。
            System.out.println("hello world!");
        } catch (FileNotFoundException e){ // catch后面的好像一个方法的形参。
            // 这个分支中可以使用e引用，e引用保存的内存地址是那个new出来异常对象的内存地址。
            // catch是捕捉异常之后走的分支。
            // 在catch分支中干什么？处理异常。
            System.out.println("文件不存在，可能路径错误，也可能该文件被删除了！");
            System.out.println(e); //java.io.FileNotFoundException: D:\course\01-课\学习方法.txt (系统找不到指定的路径。)
        }

        // try..catch把异常抓住之后，这里的代码会继续执行。
        System.out.println("main over");
    }

    private static void m1() throws FileNotFoundException {
        System.out.println("m1 begin");
        m2();
        // 以上代码出异常，这里是无法执行的。
        System.out.println("m1 over");
    }

    // 抛别的不行，抛ClassCastException说明你还是没有对FileNotFoundException进行处理
    //private static void m2() throws ClassCastException{
    // 抛FileNotFoundException的父对象IOException，这样是可以的。因为IOException包括FileNotFoundException
    //private static void m2() throws IOException {
    // 这样也可以，因为Exception包括所有的异常。
    //private static void m2() throws Exception{
    // throws后面也可以写多个异常，可以使用逗号隔开。
    //private static void m2() throws ClassCastException, FileNotFoundException{
    private static void m2() throws FileNotFoundException {
        System.out.println("m2 begin");
        // 编译器报错原因是：m3()方法声明位置上有：throws FileNotFoundException
        // 我们在这里调用m3()没有对异常进行预处理，所以编译报错。
        // m3();

        m3();
        // 以上如果出现异常，这里是无法执行的！
        System.out.println("m2 over");
    }

    private static void m3() throws FileNotFoundException {
        // 调用SUN jdk中某个类的构造方法。
        // 这个类还没有接触过，后期IO流的时候就知道了。
        // 我们只是借助这个类学习一下异常处理机制。
        // 创建一个输入流对象，该流指向一个文件。
        /*
        编译报错的原因是什么？
            第一：这里调用了一个构造方法：FileInputStream(String name)
            第二：这个构造方法的声明位置上有：throws FileNotFoundException
            第三：通过类的继承结构看到：FileNotFoundException父类是IOException，IOException的父类是Exception，
            最终得知，FileNotFoundException是编译时异常。

            错误原因？编译时异常要求程序员编写程序阶段必须对它进行处理，不处理编译器就报错。
         */
        //new FileInputStream("D:\\course\\01-开课\\学习方法.txt");

        // 我们采用第一种处理方式：在方法声明的位置上使用throws继续上抛。
        // 一个方法体当中的代码出现异常之后，如果上报的话，此方法结束。
        new FileInputStream("D:\\course\\01-课\\学习方法.txt");

        System.out.println("如果以上代码出异常，这里会执行吗??????????????????不会！！！");
    }
}

```

### 13.8 异常执行和没执行地方和try catch和Java8特性和上报和捕捉

``` java
package com.bjpowernode.javase.exception;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

/*
深入try..catch
    1、catch后面的小括号中的类型可以是具体的异常类型，也可以是该异常类型的父类型。
    2、catch可以写多个。建议catch的时候，精确的一个一个处理。这样有利于程序的调试。
    3、catch写多个的时候，从上到下，必须遵守从小到大。
 */
public class ExceptionTest07 {
    /*
    public static void main(String[] args) throws Exception, FileNotFoundException, NullPointerException {

    }
     */

    /*public static void main(String[] args) throws Exception {

    }*/

    public static void main(String[] args) {

        //编译报错
        /*try {
            FileInputStream fis = new FileInputStream("D:\\course\\02-JavaSE\\document\\JavaSE进阶讲义\\JavaSE进阶-01-面向对象.pdf");
        } catch(NullPointerException e) {

        }*/

        /*try {
            FileInputStream fis = new FileInputStream("D:\\curse\\02-JavaSE\\document\\JavaSE进阶讲义\\JavaSE进阶-01-面向对象.pdf");
            System.out.println("以上出现异常，这里无法执行！");
        } catch(FileNotFoundException e) {
            System.out.println("文件不存在！");
        }

        System.out.println("hello world!");*/

        /*try {
            FileInputStream fis = new FileInputStream("D:\\curse\\02-JavaSE\\document\\JavaSE进阶讲义\\JavaSE进阶-01-面向对象.pdf");
        } catch(IOException e) { // 多态：IOException e = new FileNotFoundException();
            System.out.println("文件不存在！");
        }*/

        /*try {
            FileInputStream fis = new FileInputStream("D:\\curse\\02-JavaSE\\document\\JavaSE进阶讲义\\JavaSE进阶-01-面向对象.pdf");
        } catch(Exception e) { // 多态：Exception e = new FileNotFoundException();
            System.out.println("文件不存在！");
        }*/

        /*try {
            //创建输入流
            FileInputStream fis = new FileInputStream("D:\\curse\\02-JavaSE\\document\\JavaSE进阶讲义\\JavaSE进阶-01-面向对象.pdf");
            //读文件
            fis.read();
        } catch(Exception e) { //所有的异常都走这个分支。
            System.out.println("文件不存在！");
        }*/

        /*try {
            //创建输入流
            FileInputStream fis = new FileInputStream("D:\\curse\\02-JavaSE\\document\\JavaSE进阶讲义\\JavaSE进阶-01-面向对象.pdf");
            //读文件
            fis.read();
        } catch(FileNotFoundException e) {
            System.out.println("文件不存在！");
        } catch(IOException e){
            System.out.println("读文件报错了！");
        }*/

        // 编译报错。
        /*
        try {
            //创建输入流
            FileInputStream fis = new FileInputStream("D:\\curse\\02-JavaSE\\document\\JavaSE进阶讲义\\JavaSE进阶-01-面向对象.pdf");
            //读文件
            fis.read();
        } catch(IOException e){
            System.out.println("读文件报错了！");
        } catch(FileNotFoundException e) {
            System.out.println("文件不存在！");
        }
         */

        // JDK8的新特性！
        try {
            //创建输入流
            FileInputStream fis = new FileInputStream("D:\\curse\\02-JavaSE\\document\\JavaSE进阶讲义\\JavaSE进阶-01-面向对象.pdf");
            // 进行数学运算
            System.out.println(100 / 0); // 这个异常是运行时异常，编写程序时可以处理，也可以不处理。
        } catch(FileNotFoundException | ArithmeticException | NullPointerException e) {
            System.out.println("文件不存在？数学异常？空指针异常？都有可能！");
        }
    }
}
```

### 13.9 异常对象的常用方法

``` java
package com.bjpowernode.javase.exception;

import java.io.FileInputStream;
import java.io.FileNotFoundException;

/*
异常对象的两个方法：
    String msg = e.getMessage();
    e.printStackTrace(); // 一般都是使用这个。

我们以后查看异常的追踪信息，我们应该怎么看，可以快速的调试程序呢？
    异常信息追踪信息，从上往下一行一行看。
    但是需要注意的是：SUN写的代码就不用看了(看包名就知道是自己的还是SUN的。)。
    主要的问题是出现在自己编写的代码上。
 */
public class ExceptionTest09 {
    public static void main(String[] args) {
        try {
            m1();
        } catch (FileNotFoundException e) {
            // 获取异常的简单描述信息
            String msg = e.getMessage();
            System.out.println(msg); //C:\jetns-agent.jar (系统找不到指定的文件。)

            //打印异常堆栈追踪信息！！！
            //在实际的开发中，建议使用这个。养成好习惯！
            // 这行代码要写上，不然出问题你也不知道！
            //e.printStackTrace();
            /*
            java.io.FileNotFoundException: C:\jetns-agent.jar (系统找不到指定的文件。)
                at java.base/java.io.FileInputStream.open0(Native Method)
                at java.base/java.io.FileInputStream.open(FileInputStream.java:213)
                at java.base/java.io.FileInputStream.<init>(FileInputStream.java:155)
                at java.base/java.io.FileInputStream.<init>(FileInputStream.java:110)
                at com.bjpowernode.javase.exception.ExceptionTest09.m3(ExceptionTest09.java:31)
                at com.bjpowernode.javase.exception.ExceptionTest09.m2(ExceptionTest09.java:27)
                at com.bjpowernode.javase.exception.ExceptionTest09.m1(ExceptionTest09.java:23)
                at com.bjpowernode.javase.exception.ExceptionTest09.main(ExceptionTest09.java:14)
                因为31行出问题导致了27行
                27行出问题导致23行
                23行出问题导致14行。
                应该先查看31行的代码。31行是代码错误的根源。
             */
        }

        // 这里程序不耽误执行，很健壮。《服务器不会因为遇到异常而宕机。》
        System.out.println("Hello World!");
    }

    private static void m1() throws FileNotFoundException {
        m2();
    }

    private static void m2() throws FileNotFoundException {
        m3();
    }

    private static void m3() throws FileNotFoundException {
        new FileInputStream("C:\\jetns-agent.jar");
    }
}


```

### 13.10 finally子句的使用

``` java
package com.bjpowernode.javase.exception;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

/*
关于try..catch中的finally子句：
    1、在finally子句中的代码是最后执行的，并且是一定会执行的，即使try语句块中的代码出现了异常。
        finally子句必须和try一起出现，不能单独编写。

    2、finally语句通常使用在哪些情况下呢？
        通常在finally语句块中完成资源的释放/关闭。
        因为finally中的代码比较有保障。
        即使try语句块中的代码出现异常，finally中代码也会正常执行。
 */
public class ExceptionTest10 {
    public static void main(String[] args) {
        FileInputStream fis = null; // 声明位置放到try外面。这样在finally中才能用。
        try {
            // 创建输入流对象
            fis = new FileInputStream("D:\\course\\02-JavaSE\\document\\JavaSE进阶讲义\\JavaSE进阶-01-面向对象.pdf");
            // 开始读文件....

            String s = null;
            // 这里一定会出现空指针异常！
            s.toString();
            System.out.println("hello world!");

            // 流使用完需要关闭，因为流是占用资源的。
            // 即使以上程序出现异常，流也必须要关闭！
            // 放在这里有可能流关不了。
            //fis.close();
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch(IOException e){
            e.printStackTrace();
        } catch(NullPointerException e) {
            e.printStackTrace();
        } finally {
            System.out.println("hello 浩克！");
            // 流的关闭放在这里比较保险。
            // finally中的代码是一定会执行的。
            // 即使try中出现了异常！
            if (fis != null) { // 避免空指针异常！
                try {
                    // close()方法有异常，采用捕捉的方式。
                    fis.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }

        System.out.println("hello kitty!");

    }
}

package com.bjpowernode.javase.exception;
/*
finally语句：
    放在finally语句块中的代码是一定会执行的【再次强调！！！】
 */
public class ExceptionTest11 {
    public static void main(String[] args) {
        /*
        try和finally，没有catch可以吗？可以。
            try不能单独使用。
            try finally可以联合使用。
        以下代码的执行顺序：
            先执行try...
            再执行finally...
            最后执行 return （return语句只要执行方法必然结束。）
         */
        try {
            System.out.println("try...");
            return;
        } finally {
            // finally中的语句会执行。能执行到。
            System.out.println("finally...");
        }

        // 这里不能写语句，因为这个代码是无法执行到的。
        //System.out.println("Hello World!");
    }
}
```

### 13.11 退出JVMfinally不执行

``` java
package com.bjpowernode.javase.exception;

/*
finally
 */
public class ExceptionTest12 {
    public static void main(String[] args) {
        try {
            System.out.println("try...");
            // 退出JVM
            System.exit(0); // 退出JVM之后，finally语句中的代码就不执行了！
        } finally {
            System.out.println("finally...");
        }
    }
}

```

### 13.12 finally 面试题

``` java
package com.bjpowernode.javase.exception;
/*
finally面试题
 */
public class ExceptionTest13 {
    public static void main(String[] args) {
        int result = m();
        System.out.println(result); //100
    }

    /*
    java语法规则（有一些规则是不能破坏的，一旦这么说了，就必须这么做！）：
        java中有一条这样的规则：
            方法体中的代码必须遵循自上而下顺序依次逐行执行（亘古不变的语法！）
        java中海油一条语法规则：
            return语句一旦执行，整个方法必须结束（亘古不变的语法！）
     */
    public static int m(){
        int i = 100;
        try {
            // 这行代码出现在int i = 100;的下面，所以最终结果必须是返回100
            // return语句还必须保证是最后执行的。一旦执行，整个方法结束。
            return i;
        } finally {
            i++;
        }
    }
}

/*
反编译之后的效果
public static int m(){
    int i = 100;
    int j = i;
    i++;
    return j;
}
 */

```

### 13.13 final和finally和finalize的区别

``` java
package com.bjpowernode.javase.exception;

/*
final finally finalize有什么区别？
    final 关键字
        final修饰的类无法继承
        final修饰的方法无法覆盖
        final修饰的变量不能重新赋值。

    finally 关键字
        和try一起联合使用。
        finally语句块中的代码是必须执行的。

    finalize 标识符
        是一个Object类中的方法名。
        这个方法是由垃圾回收器GC负责调用的。
 */
public class ExceptionTest14 {
    public static void main(String[] args) {

        // final是一个关键字。表示最终的。不变的。
        final int i = 100;
        //i = 200;

        // finally也是一个关键字，和try联合使用，使用在异常处理机制中
        // 在fianlly语句块中的代码是一定会执行的。
        try {

        } finally {
            System.out.println("finally....");
        }

        // finalize()是Object类中的一个方法。作为方法名出现。
        // 所以finalize是标识符。
        // finalize()方法是JVM的GC垃圾回收器负责调用。
        Object obj;
    }
}

// final修饰的类无法继承
final class A {
    // 常量。
    public static final double MATH_PI = 3.1415926;
}

class B {
    // final修饰的方法无法覆盖
    public final void doSome(){

    }
}

```

### 13.14 Java中自定义异常

``` java
package com.bjpowernode.javase.exception;

public class ExceptionTest15 {
    public static void main(String[] args) {

        // 创建异常对象（只new了异常对象，并没有手动抛出）
        MyException e = new MyException("用户名不能为空！");

        // 打印异常堆栈信息
        e.printStackTrace();

        // 获取异常简单描述信息
        String msg = e.getMessage();
        System.out.println(msg);
    }
}

```

### 13.15 异常在实际开发中的作用

``` java
package com.bjpowernode.javase.exception;
/*
	编写程序，使用一维数组，模拟栈数据结构。
	要求：
		1、这个栈可以存储java中的任何引用类型的数据。
		2、在栈中提供push方法模拟压栈。（栈满了，要有提示信息。）
		3、在栈中提供pop方法模拟弹栈。（栈空了，也有有提示信息。）
		4、编写测试程序，new栈对象，调用push pop方法来模拟压栈弹栈的动作。
		5、假设栈的默认初始化容量是10.（请注意无参数构造方法的编写方式。）
 */
public class MyStack {
    // 向栈当中存储元素，我们这里使用一维数组模拟。存到栈中，就表示存储到数组中。
    // 因为数组是我们学习java的第一个容器。
    // 为什么选择Object类型数组？因为这个栈可以存储java中的任何引用类型的数据
    // new Animal()对象可以放进去，new Person()对象也可以放进去。因为Animal和Person的超级父类就是Object。
    // 包括String也可以存储进去。因为String父类也是Object。
    private Object[] elements;

    // 栈帧，永远指向栈顶部元素
    // 那么这个默认初始值应该是多少。注意：最初的栈是空的，一个元素都没有。
    //private int index = 0; // 如果index采用0，表示栈帧指向了顶部元素的上方。
    //private int index = -1; // 如果index采用-1，表示栈帧指向了顶部元素。
    private int index;

    /**
     * 无参数构造方法。默认初始化栈容量10.
     */
    public MyStack() {
        // 一维数组动态初始化
        // 默认初始化容量是10.
        this.elements = new Object[10];
        // 给index初始化
        this.index = -1;
    }

    /**
     * 压栈的方法
     * @param obj 被压入的元素
     */
    public void push(Object obj) throws MyStackOperationException {
        if(index >= elements.length - 1){
            // 改良之前
            //System.out.println("压栈失败，栈已满！");
            //return;

            // 创建异常对象
            //MyStackOperationException e = new MyStackOperationException("压栈失败，栈已满！");
            // 手动将异常抛出去！
            //throw e; //这里捕捉没有意义，自己new一个异常，自己捉，没有意义。栈已满这个信息你需要传递出去。

            // 合并（手动抛出异常！）
            throw new MyStackOperationException("压栈失败，栈已满！");
        }
        // 程序能够走到这里，说明栈没满
        // 向栈中加1个元素，栈帧向上移动一个位置。
        index++;
        elements[index] = obj;
        // 在声明一次：所有的System.out.println()方法执行时，如果输出引用的话，自动调用引用的toString()方法。
        System.out.println("压栈" + obj + "元素成功，栈帧指向" + index);
    }

    /**
     * 弹栈的方法，从数组中往外取元素。每取出一个元素，栈帧向下移动一位。
     * @return
     */
    public void pop() throws MyStackOperationException {
        if(index < 0){
            //System.out.println("弹栈失败，栈已空！");
            //return;
            throw new MyStackOperationException("弹栈失败，栈已空！");
        }
        // 程序能够执行到此处说明栈没有空。
        System.out.print("弹栈" + elements[index] + "元素成功，");
        // 栈帧向下移动一位。
        index--;
        System.out.println("栈帧指向" + index);
    }

    // set和get也许用不上，但是你必须写上，这是规矩。你使用IDEA生成就行了。
    // 封装：第一步：属性私有化，第二步：对外提供set和get方法。
    public Object[] getElements() {
        return elements;
    }

    public void setElements(Object[] elements) {
        this.elements = elements;
    }

    public int getIndex() {
        return index;
    }

    public void setIndex(int index) {
        this.index = index;
    }
}


package com.bjpowernode.javase.exception;

// 测试改良之后的MyStack
// 注意：最后这个例子，是异常最终要的案例。必须掌握。自定义异常在实际开发中的应用。
public class ExceptionTest16 {

    public static void main(String[] args) {

        // 创建栈对象
        MyStack stack = new MyStack();

        // 压栈
        try {
            stack.push(new Object());
            stack.push(new Object());
            stack.push(new Object());
            stack.push(new Object());
            stack.push(new Object());
            stack.push(new Object());
            stack.push(new Object());
            stack.push(new Object());
            stack.push(new Object());
            stack.push(new Object());
            // 这里栈满了
            stack.push(new Object());
        } catch (MyStackOperationException e) {
            // 输出异常的简单信息。
            System.out.println(e.getMessage());
        }

        // 弹栈
        try {
            stack.pop();
            stack.pop();
            stack.pop();
            stack.pop();
            stack.pop();
            stack.pop();
            stack.pop();
            stack.pop();
            stack.pop();
            stack.pop();
            // 弹栈失败
            stack.pop();
        } catch (MyStackOperationException e) {
            System.out.println(e.getMessage());
        }
    }
}

```

### 13.16 异常与方法覆盖

``` java
package com.bjpowernode.javase.exception;

/*
之前在讲解方法覆盖的时候，当时遗留了一个问题？
    重写之后的方法不能比重写之前的方法抛出更多（更宽泛）的异常，可以更少。
 */
class Animal {
    public void doSome(){

    }

    public void doOther() throws Exception{

    }
}

class Cat extends Animal {

    // 编译正常。
    public void doSome() throws RuntimeException{

    }

    // 编译报错。
    /*public void doSome() throws Exception{

    }*/

    // 编译正常。
    /*public void doOther() {

    }*/

    // 编译正常。
    /*public void doOther() throws Exception{

    }*/

    // 编译正常。
    public void doOther() throws NullPointerException{

    }
}

/*
总结异常中的关键字：
    异常捕捉：
        try
        catch
        finally

    throws 在方法声明位置上使用，表示上报异常信息给调用者。
    throw 手动抛出异常！
 */
```

### 13.17 作业题

``` java
package com.bjpowernode.javase.exception.homework;
/*
用户业务类，处理用户相关的业务：例如登录、注册等功能。
 */
public class UserService {

    /**
     * 用户注册
     * @param username 用户名
     * @param password 密码
     * @throws IllegalNameException 当用户名为null，或者用户名长度小于6，或者长度大于14，会出现该异常！
     */
    public void register(String username, String password) throws IllegalNameException {
        /*
        引用等于null的这个判断最好放到所有条件的最前面。
         */
        /*if(username == null || username.length() < 6 || username.length() > 14){
        }*/

        /*
        再分享一个经验：username == null 不如写成 null == username
        "abc".equals(username) 比 username.equals("abc") 好。
         */
        /*if(null == username || username.length() < 6 || username.length() > 14){
        }*/

        if(null == username || username.length() < 6 || username.length() > 14) {
            /*System.out.println("用户名不合法，长度必须在[6-14]之间");
            return;*/
            throw new IllegalNameException("用户名不合法，长度必须在[6-14]之间");
        }
        // 程序能够执行到此处说明，用户名合法
        System.out.println("注册成功，欢迎["+username+"]");
    }
}

package com.bjpowernode.javase.exception.homework;

/**
 * 自定义异常
 */
public class IllegalNameException extends Exception {
    public IllegalNameException(){

    }
    public IllegalNameException(String s){
        super(s);
    }
}

package com.bjpowernode.javase.exception.homework;

public class Test {
    public static void main(String[] args) {
        // 创建UserService对象
        UserService userService = new UserService();
        // 用户名和密码就不再从控制台接收了
        try {
            userService.register("jack", "123");
        } catch (IllegalNameException e) {
            //System.out.println(e.getMessage());
            e.printStackTrace();
        }
    }
}

武器作业题：
   package com.bjpowernode.day24.homework;

/**
 * 军队
 *
 * 类在强制类型转换过程中，如果是类转换成接口类型。
 * 那么类和接口之间不需要存在继承关系，也可以转换，
 * java语法中允许。
 */
public class Army {
    /**
     * 武器数组
     */
    private Weapon[] weapons;

    /**
     * 创建军队的构造方法。
     * @param count 武器数量
     */
    public Army(int count){
        // 动态初始化数组中每一个元素默认值是null。
        // 武器数组是有了，但是武器数组中没有放武器。
        weapons = new Weapon[count];
    }

    /**
     * 将武器加入数组
     * @param weapon
     */
    public void addWeapon(Weapon weapon) throws AddWeaponException {
        for(int i = 0; i < weapons.length; i++){
            //if(null == weapons[i]) {
            if(weapons[i] == null) {
                // 把武器添加到空的位置上。
                weapons[i] = weapon;
                System.out.println(weapon + "：武器添加成功");
                return;
            }
        }
        // 程序如果执行到此处说明，武器没有添加成功
        throw new AddWeaponException("武器数量已达到上限！");
    }

    /**
     * 所有可攻击的武器攻击。
     */
    public void attackAll(){
        // 遍历数组
        for(int i = 0; i < weapons.length; i ++){
            if(weapons[i] instanceof Shootable){
                // 调用子类中特有的方法，向下转型。
                Shootable shootable = (Shootable)weapons[i];
                shootable.shoot();
            }
        }
    }

    /**
     * 所有可移动的武器移动
     */
    public void moveAll(){
        // 遍历数组
        for(int i = 0; i < weapons.length; i ++){
            if(weapons[i] instanceof Moveable){
                // 调用子类中特有的方法，向下转型。
                Moveable moveable = (Moveable)weapons[i];
                moveable.move();
            }
        }
    }
}

package com.bjpowernode.day24.homework;

/**
 * 添加武器异常。
 */
public class AddWeaponException extends Exception {
    public AddWeaponException(){

    }
    public AddWeaponException(String s){
        super(s);
    }
}

package com.bjpowernode.day24.homework;

/**
 * 高射炮，是武器，但是不能移动，只能射击
 */
public class GaoShePao extends Weapon implements Shootable {

    @Override
    public void shoot() {
        System.out.println("高射炮开炮！！！");
    }
}

package com.bjpowernode.day24.homework;

/**
 * 可移动的接口
 */
public interface Moveable {

    /**
     * 移动行为
     */
    void move();
}

package com.bjpowernode.day24.homework;

/**
 * 可射击的
 */
public interface Shootable {
    /**
     * 射击行为
     */
    void shoot();
}

package com.bjpowernode.day24.homework;

/**
 * 坦克是一个武器，可移动，可攻击。
 */
public class Tank extends Weapon implements Moveable,Shootable{

    @Override
    public void move() {
        System.out.println("坦克移动");
    }

    @Override
    public void shoot() {
        System.out.println("坦克开炮");
    }
}

package com.bjpowernode.day24.homework;

public class Test {
    public static void main(String[] args) {
        // 构建一个军队
        Army army = new Army(4); // 军队只有4个武器。
        // 创建武器对象
        Fighter fighter = new Fighter();
        Fighter fighter2 = new Fighter();
        Tank tank = new Tank();
        WuZiFeiJi wuZiFeiJi = new WuZiFeiJi();
        GaoShePao gaoShePao = new GaoShePao();

        // 添加武器
        try {
            army.addWeapon(fighter);
            army.addWeapon(tank);
            army.addWeapon(wuZiFeiJi);
            army.addWeapon(gaoShePao);
            army.addWeapon(fighter2);
        } catch (AddWeaponException e) {
            System.out.println(e.getMessage());
        }

        // 让所有可移动的移动
        army.moveAll();

        // 让所有可攻击的攻击
        army.attackAll();

        // 这是new一个异常对象。没有手动抛异常，它就是一个普通的java类。
        // 就像User类一样。没有区别。
        /*AddWeaponException e = new AddWeaponException("武器数量已达到上限！");
        System.out.println(e.getMessage());*/
    }
}

package com.bjpowernode.day24.homework;

/**
 * 所有武器的父类
 */
public class Weapon {
}

package com.bjpowernode.day24.homework;

/**
 * 物资运输飞机，是武器，但是只能移动，不能攻击
 */
public class WuZiFeiJi extends Weapon implements Moveable {
    @Override
    public void move() {
        System.out.println("运输机起飞！");
    }
}

package com.bjpowernode.day24.homework;

/**
 * 战斗机，是武器，可以移动，可攻击
 */
public class Fighter extends Weapon implements Moveable, Shootable {

    @Override
    public void move() {
        System.out.println("战斗机起飞");
    }

    @Override
    public void shoot() {
        System.out.println("战斗机开炮！");
    }
}

```

## 14.集合

### 14.1集合的概述和存储内容和不同数据结构

>1、集合概述
>
>	1.1、什么是集合？有什么用？
>																																
>		数组其实就是一个集合。集合实际上就是一个容器。可以来容纳其它类型的数据。
>																																
>		集合为什么说在开发中使用较多？
>			集合是一个容器，是一个载体，可以一次容纳多个对象。
>			在实际开发中，假设连接数据库，数据库当中有10条记录，
>			那么假设把这10条记录查询出来，在java程序中会将10条
>			数据封装成10个java对象，然后将10个java对象放到某一个
>			集合当中，将集合传到前端，然后遍历集合，将一个数据一个
>			数据展现出来。
>																																
>	1.2、集合不能直接存储基本数据类型，另外集合也不能直接存储java对象，
>	集合当中存储的都是java对象的内存地址。（或者说集合中存储的是引用。）
>		list.add(100); //自动装箱Integer
>		注意：
>			集合在java中本身是一个容器，是一个对象。
>			集合中任何时候存储的都是“引用”。
>																																
>	1.3、在java中每一个不同的集合，底层会对应不同的数据结构。往不同的集合中
>	存储元素，等于将数据放到了不同的数据结构当中。什么是数据结构？数据存储的
>	结构就是数据结构。不同的数据结构，数据存储方式不同。例如：
>		数组、二叉树、链表、哈希表...
>		以上这些都是常见的数据结构。
>																																
>		你往集合c1中放数据，可能是放到数组上了。
>		你往集合c2中放数据，可能是放到二叉树上了。
>		.....
>		你使用不同的集合等同于使用了不同的数据结构。
>																																
>		你在java集合这一章节，你需要掌握的不是精通数据结构。java中已经将数据结构
>		实现了，已经写好了这些常用的集合类，你只需要掌握怎么用？在什么情况下选择
>		哪一种合适的集合去使用即可。
>																																
>		new ArrayList(); 创建一个集合对象，底层是数组。
>		new LinkedList(); 创建一个集合对象，底层是链表。
>		new TreeSet(); 创建一个集合对象，底层是二叉树。
>		.....
>																																
>	1.4、集合在java JDK中哪个包下？
>		java.util.*;
>			所有的集合类和集合接口都在java.util包下。
>																																
>	1.5、为了让大家掌握集合这块的内容，最好能将集合的继承结构图背会！！！
>		集合整个这个体系是怎样的一个结构，你需要有印象。
>																																
>	1.6、在java中集合分为两大类：
>		一类是单个方式存储元素：
>			单个方式存储元素，这一类集合中超级父接口：java.util.Collection;
>																																
>		一类是以键值对儿的方式存储元素
>			以键值对的方式存储元素，这一类集合中超级父接口：java.util.Map;
>
>2、总结重点：
>
>	第一个重点：把集合继承结构图背会。
>																																
>	第二个重点：把Collection接口中常用方法测试几遍。
>																																
>	第三个重点：把迭代器弄明白。
>																																
>	第四个重点：Collection接口中的remove方法和contains方法底层都会调用equals，
>					这个弄明白。

![day28-集合中存储的是对象的内存地址](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/day28-%E9%9B%86%E5%90%88%E4%B8%AD%E5%AD%98%E5%82%A8%E7%9A%84%E6%98%AF%E5%AF%B9%E8%B1%A1%E7%9A%84%E5%86%85%E5%AD%98%E5%9C%B0%E5%9D%80.png)

### 14.2 集合继承的结构图

![image-20210410140607589](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/image-20210410140607589.png)

![image-20210410141808992](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/image-20210410141808992.png)

**总结（所有的实现类）：**

n ArrayList：底层是数组。

n LinkedList：底层是双向链表。

n Vector：底层是数组，线程安全的，效率较低，使用较少。

n HashSet：底层是HashMap，放到HashSet集合中的元素等同于放到HashMap集合key部分了。

n TreeSet：底层是TreeMap，放到TreeSet集合中的元素等同于放到TreeMap集合key部分了。

n HashMap:底层是哈希表。

n Hashtable：底层也是哈希表，只不过线程安全的，效率较低，使用较少。

n Properties：是线程安全的，并且key和value只能存储字符串String。

n TreeMap：底层是二叉树。TreeMap集合的key可以自动按照大小顺序排序。

 

List集合存储元素的特点：

​     有序可重复

​     有序：存进去的顺序和取出的顺序相同，每一个元素都有下标。

​     可重复：存进去1，可以再存储一个1.

 

Set（Map）集合存储元素的特点：

​     无序不可重复

​     无序：存进去的顺序和取出的顺序不一定相同。另外Set集合中元素没有下标。

​     不可重复：存进去1，不能再存储1了。

 

SortedSet（SortedMap）集合存储元素特点：

​     首先是无序不可重复的，但是SortedSet集合中的元素是可排序的。

​     无序：存进去的顺序和取出的顺序不一定相同。另外Set集合中元素没有下标。

​     不可重复：存进去1，不能再存储1了。

​     可排序：可以按照大小顺序排列。

 

Map集合的key，就是一个Set集合。

往Set集合中放数据，实际上放到了Map集合的key部分。

### 14.3 Collection接口常用方法

```java
package com.bjpowernode.javase.collection;

import java.util.ArrayList;
import java.util.Collection;

/*
关于java.util.Collection接口中常用的方法。
    1、Collection中能存放什么元素？
        没有使用“泛型”之前，Collection中可以存储Object的所有子类型。
        使用了“泛型”之后，Collection中只能存储某个具体的类型。
        集合后期我们会学习“泛型”语法。目前先不用管。Collection中什么都能存，
        只要是Object的子类型就行。（集合中不能直接存储基本数据类型，也不能存
        java对象，只是存储java对象的内存地址。）
    2、Collection中的常用方法
        boolean add(Object e) 向集合中添加元素
        int size()  获取集合中元素的个数
        void clear() 清空集合
        boolean contains(Object o) 判断当前集合中是否包含元素o，包含返回true，不包含返回false
        boolean remove(Object o) 删除集合中的某个元素。
        boolean isEmpty()  判断该集合中元素的个数是否为0
        Object[] toArray()  调用这个方法可以把集合转换成数组。【作为了解，使用不多。】
 */
public class CollectionTest01 {
    public static void main(String[] args) {
        // 创建一个集合对象
        //Collection c = new Collection(); // 接口是抽象的，无法实例化。
        // 多态
        Collection c = new ArrayList();
        // 测试Collection接口中的常用方法
        c.add(1200); // 自动装箱(java5的新特性。),实际上是放进去了一个对象的内存地址。Integer x = new Integer(1200);
        c.add(3.14); // 自动装箱
        c.add(new Object());
        c.add(new Student());
        c.add(true); // 自动装箱

        // 获取集合中元素的个数
        System.out.println("集合中元素个数是：" + c.size()); // 5

        // 清空集合
        c.clear();
        System.out.println("集合中元素个数是：" + c.size()); // 0

        // 再向集合中添加元素
        c.add("hello"); // "hello"对象的内存地址放到了集合当中。
        c.add("world");
        c.add("浩克");
        c.add("绿巨人");
        c.add(1);

        // 判断集合中是否包含"绿巨人"
        boolean flag = c.contains("绿巨人");
        System.out.println(flag); // true
        boolean flag2 = c.contains("绿巨人2");
        System.out.println(flag2); // false
        System.out.println(c.contains(1)); // true

        System.out.println("集合中元素个数是：" + c.size()); // 5

        // 删除集合中某个元素
        c.remove(1);
        System.out.println("集合中元素个数是：" + c.size()); // 4

        // 判断集合是否为空（集合中是否存在元素）
        System.out.println(c.isEmpty()); // false
        // 清空
        c.clear();
        System.out.println(c.isEmpty()); // true（true表示集合中没有元素了！）

        c.add("abc");
        c.add("def");
        c.add(100);
        c.add("helloworld!");
        c.add(new Student());

        // 转换成数组（了解，使用不多。）
        Object[] objs = c.toArray();
        for(int i = 0; i < objs.length; i++){
            // 遍历数组
            Object o = objs[i];
            System.out.println(o);
        }
    }
}

class Student{

}

```

### 14.4 Collection集合迭代

```java
package com.bjpowernode.javase.collection;

import java.util.ArrayList;
import java.util.Collection;
import java.util.Iterator;

/**
 * 关于集合遍历/迭代专题。（重点：五颗星*****）
 *   // 创建集合对象
        Collection c = new ArrayList(); // 后面的集合无所谓，主要是看前面的Collection接口，怎么遍历/迭代。
        // 添加元素
        c.add("abc");
        c.add("def");
        c.add(100);
        c.add(new Object());
        // 对集合Collection进行遍历/迭代
        // 第一步：获取集合对象的迭代器对象Iterator
        Iterator it = c.iterator();
        // 第二步：通过以上获取的迭代器对象开始迭代/遍历集合。
        /*
            以下两个方法是迭代器对象Iterator中的方法：
                boolean hasNext()如果仍有元素可以迭代，则返回 true。
                Object next() 返回迭代的下一个元素。
      
        while(it.hasNext()){
            Object obj = it.next();
            System.out.println(obj);
        }
         /*boolean hasNext = it.hasNext();
        System.out.println(hasNext);
        if(hasNext) {
            // 不管你当初存进去什么，取出来统一都是Object。
            Object obj = it.next();
            System.out.println(obj);
        }

        hasNext = it.hasNext();
        System.out.println(hasNext);
        if(hasNext) {
            Object obj = it.next();
            System.out.println(obj);
        }
        Boolean hashNext = it.hashNext();//true可以迭代，false停止迭代
        Obeject obj = it.next();//然迭代器前进一位，拿到元素
 **/
public class CollectionTest02 {
    public static void main(String[] args) {
        // 注意：以下讲解的遍历方式/迭代方式，是所有Collection通用的一种方式。
        // 在Map集合中不能用。在所有的Collection以及子类中使用。
        // 创建集合对象
        Collection c = new ArrayList(); // 后面的集合无所谓，主要是看前面的Collection接口，怎么遍历/迭代。
        // 添加元素
        c.add("abc");
        c.add("def");
        c.add(100);
        c.add(new Object());
        // 对集合Collection进行遍历/迭代
        // 第一步：获取集合对象的迭代器对象Iterator
        Iterator it = c.iterator();
        // 第二步：通过以上获取的迭代器对象开始迭代/遍历集合。
        /*
            以下两个方法是迭代器对象Iterator中的方法：
                boolean hasNext()如果仍有元素可以迭代，则返回 true。
                Object next() 返回迭代的下一个元素。
         */
        while(it.hasNext()){
            Object obj = it.next();
            System.out.println(obj);
        }

        // 一直取，不判断，会出现异常：java.util.NoSuchElementException
        /*while(true){
            Object obj = it.next();
            System.out.println(obj);
        }*/

        /*boolean hasNext = it.hasNext();
        System.out.println(hasNext);
        if(hasNext) {
            // 不管你当初存进去什么，取出来统一都是Object。
            Object obj = it.next();
            System.out.println(obj);
        }

        hasNext = it.hasNext();
        System.out.println(hasNext);
        if(hasNext) {
            Object obj = it.next();
            System.out.println(obj);
        }

        hasNext = it.hasNext();
        System.out.println(hasNext);
        if(hasNext) {
            Object obj = it.next();
            System.out.println(obj);
        }

        hasNext = it.hasNext();
        System.out.println(hasNext);
        if(hasNext) {
            Object obj = it.next();
            System.out.println(obj);
        }

        hasNext = it.hasNext();
        System.out.println(hasNext);
        if(hasNext) {
            Object obj = it.next();
            System.out.println(obj);
        }*/
    }
}

```

![day28-迭代集合的原理](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/day28-%E8%BF%AD%E4%BB%A3%E9%9B%86%E5%90%88%E7%9A%84%E5%8E%9F%E7%90%86.png)

### 14.5 迭代器的执行原理和迭代器是通用的

``` java
package com.bjpowernode.javase.collection;

import java.util.ArrayList;
import java.util.Collection;
import java.util.Iterator;

/**
 * 关于集合遍历/迭代专题。（重点：五颗星*****）
 */
public class CollectionTest02 {
    public static void main(String[] args) {
        // 注意：以下讲解的遍历方式/迭代方式，是所有Collection通用的一种方式。
        // 在Map集合中不能用。在所有的Collection以及子类中使用。
        // 创建集合对象
        Collection c = new ArrayList(); // 后面的集合无所谓，主要是看前面的Collection接口，怎么遍历/迭代。
        // 添加元素
        c.add("abc");
        c.add("def");
        c.add(100);
        c.add(new Object());
        // 对集合Collection进行遍历/迭代
        // 第一步：获取集合对象的迭代器对象Iterator
        Iterator it = c.iterator();
        // 第二步：通过以上获取的迭代器对象开始迭代/遍历集合。
        /*
            以下两个方法是迭代器对象Iterator中的方法：
                boolean hasNext()如果仍有元素可以迭代，则返回 true。
                Object next() 返回迭代的下一个元素。
         */
        while(it.hasNext()){
            Object obj = it.next();
            System.out.println(obj);
        }

        // 一直取，不判断，会出现异常：java.util.NoSuchElementException
        /*while(true){
            Object obj = it.next();
            System.out.println(obj);
        }*/

        /*boolean hasNext = it.hasNext();
        System.out.println(hasNext);
        if(hasNext) {
            // 不管你当初存进去什么，取出来统一都是Object。
            Object obj = it.next();
            System.out.println(obj);
        }

        hasNext = it.hasNext();
        System.out.println(hasNext);
        if(hasNext) {
            Object obj = it.next();
            System.out.println(obj);
        }

        hasNext = it.hasNext();
        System.out.println(hasNext);
        if(hasNext) {
            Object obj = it.next();
            System.out.println(obj);
        }

        hasNext = it.hasNext();
        System.out.println(hasNext);
        if(hasNext) {
            Object obj = it.next();
            System.out.println(obj);
        }

        hasNext = it.hasNext();
        System.out.println(hasNext);
        if(hasNext) {
            Object obj = it.next();
            System.out.println(obj);
        }*/
    }
}

package com.bjpowernode.javase.collection;

import java.util.ArrayList;
import java.util.Collection;
import java.util.HashSet;
import java.util.Iterator;

/*
关于集合的迭代/遍历
 */
public class CollectionTest03 {
    public static void main(String[] args) {
        // 创建集合对象
        Collection c1  = new ArrayList(); // ArrayList集合：有序可重复
        // 添加元素
        c1.add(1);
        c1.add(2);
        c1.add(3);
        c1.add(4);
        c1.add(1);

        // 迭代集合
        Iterator it = c1.iterator();
        while(it.hasNext()){
            // 存进去是什么类型，取出来还是什么类型。
            Object obj = it.next();
            /*if(obj instanceof Integer){
                System.out.println("Integer类型");
            }*/
            // 只不过在输出的时候会转换成字符串。因为这里println会调用toString()方法。
            System.out.println(obj);
        }

        // HashSet集合：无序不可重复
        Collection c2 = new HashSet();
        // 无序：存进去和取出的顺序不一定相同。
        // 不可重复：存储100，不能再存储100.
        c2.add(100);
        c2.add(200);
        c2.add(300);
        c2.add(90);
        c2.add(400);
        c2.add(50);
        c2.add(60);
        c2.add(100);
        Iterator it2 = c2.iterator();
        while(it2.hasNext()){
            System.out.println(it2.next());
        }
    }
}

```

### 14.6 contains方法解析

``` java
package com.bjpowernode.javase.collection;

import java.util.ArrayList;
import java.util.Collection;

/*
深入Collection集合的contains方法：
    boolean contains(Object o)
        判断集合中是否包含某个对象o
        如果包含返回true， 如果不包含返回false。

    contains方法是用来判断集合中是否包含某个元素的方法，
    那么它在底层是怎么判断集合中是否包含某个元素的呢？
        调用了equals方法进行比对。
        equals方法返回true，就表示包含这个元素。
 */
public class CollectionTest04 {
    public static void main(String[] args) {
        // 创建集合对象
        Collection c = new ArrayList();

        // 向集合中存储元素
        String s1 = new String("abc"); // s1 = 0x1111
        c.add(s1); // 放进去了一个"abc"

        String s2 = new String("def"); // s2 = 0x2222
        c.add(s2);

        // 集合中元素的个数
        System.out.println("元素的个数是：" + c.size()); // 2

        // 新建的对象String
        String x = new String("abc"); // x = 0x5555
        // c集合中是否包含x？结果猜测一下是true还是false？
        System.out.println(c.contains(x)); //判断集合中是否存在"abc" true
    }
}

//源码分析(contains和remove)
package com.bjpowernode.javase.collection;

import java.util.ArrayList;
import java.util.Collection;

/*
测试contains方法
测试remove方法。
结论：存放在一个集合中的类型，一定要重写equals方法。
 */
public class CollectionTest05 {
    public static void main(String[] args) {
        // 创建集合对象
        Collection c = new ArrayList();
        // 创建用户对象
        User u1 = new User("jack");
        // 加入集合
        c.add(u1);

        // 判断集合中是否包含u2
        User u2 = new User("jack");

        // 没有重写equals之前：这个结果是false
        //System.out.println(c.contains(u2)); // false
        // 重写equals方法之后，比较的时候会比较name。
        System.out.println(c.contains(u2)); // true

        c.remove(u2);
        System.out.println(c.size()); // 0

        /*Integer x = new Integer(10000);
        c.add(x);

        Integer y = new Integer(10000);
        System.out.println(c.contains(y)); // true*/

        // 创建集合对象
        Collection cc = new ArrayList();
        // 创建字符串对象
        String s1 = new String("hello");
        // 加进去。
        cc.add(s1);

        // 创建了一个新的字符串对象
        String s2 = new String("hello");
        // 删除s2
        cc.remove(s2); // s1.equals(s2) java认为s1和s2是一样的。删除s2就是删除s1。
        // 集合中元素个数是？
        System.out.println(cc.size()); // 0
    }
}

class User{
    private String name;
    public User(){}
    public User(String name){
        this.name = name;
    }

    // 重写equals方法
    // 将来调用equals方法的时候，一定是调用这个重写的equals方法。
    // 这个equals方法的比较原理是：只要姓名一样就表示同一个用户。
    public boolean equals(Object o) {
        if(o == null || !(o instanceof User)) return false;
        if(o == this) return true;
        User u = (User)o;
        // 如果名字一样表示同一个人。（不再比较对象的内存地址了。比较内容。）
        return u.name.equals(this.name);
    }

}

```

### 14.7 集合中元素的删除

``` java
package com.bjpowernode.javase.collection;

import java.util.ArrayList;
import java.util.Collection;
import java.util.Iterator;

/*
关于集合元素的remove
    重点：当集合的结构发生改变时，迭代器必须重新获取，如果还是用以前老的迭代器，会出现
    异常：java.util.ConcurrentModificationException

    重点：在迭代集合元素的过程中，不能调用集合对象的remove方法，删除元素：
        c.remove(o); 迭代过程中不能这样。
        会出现：java.util.ConcurrentModificationException

    重点：在迭代元素的过程当中，一定要使用迭代器Iterator的remove方法，删除元素，
    不要使用集合自带的remove方法删除元素。

 */
public class CollectionTest06 {
    public static void main(String[] args) {
        // 创建集合
        Collection c = new ArrayList();

        // 注意：此时获取的迭代器，指向的是那是集合中没有元素状态下的迭代器。
        // 一定要注意：集合结构只要发生改变，迭代器必须重新获取。
        // 当集合结构发生了改变，迭代器没有重新获取时，调用next()方法时：java.util.ConcurrentModificationException
        Iterator it = c.iterator();

        // 添加元素
        c.add(1); // Integer类型
        c.add(2);
        c.add(3);

        // 获取迭代器
        //Iterator it = c.iterator();
        /*while(it.hasNext()){
            // 编写代码时next()方法返回值类型必须是Object。
            // Integer i = it.next();
            Object obj = it.next();
            System.out.println(obj);
        }*/

        Collection c2 = new ArrayList();
        c2.add("abc");
        c2.add("def");
        c2.add("xyz");

        Iterator it2 = c2.iterator();
        while(it2.hasNext()){
            Object o = it2.next();
            // 删除元素
            // 删除元素之后，集合的结构发生了变化，应该重新去获取迭代器
            // 但是，循环下一次的时候并没有重新获取迭代器，所以会出现异常：java.util.ConcurrentModificationException
            // 出异常根本原因是：集合中元素删除了，但是没有更新迭代器（迭代器不知道集合变化了）
            //c2.remove(o); // 直接通过集合去删除元素，没有通知迭代器。（导致迭代器的快照和原集合状态不同。）
            // 使用迭代器来删除可以吗？
            // 迭代器去删除时，会自动更新迭代器，并且更新集合（删除集合中的元素）。
            it2.remove(); // 删除的一定是迭代器指向的当前元素。
            System.out.println(o);
        }

        System.out.println(c2.size()); //0
    }
}

```

### 14.8 List接口特有方法

 ``` java
package com.bjpowernode.javase.collection;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.LinkedList;
import java.util.List;

/*
测试List接口中常用方法
    1、List集合存储元素特点：有序可重复
        有序：List集合中的元素有下标。
        从0开始，以1递增。
        可重复：存储一个1，还可以再存储1.
    2、List既然是Collection接口的子接口，那么肯定List接口有自己“特色”的方法：
        以下只列出List接口特有的常用的方法：
            void add(int index, Object element)
            Object set(int index, Object element)
            Object get(int index)
            int indexOf(Object o)
            int lastIndexOf(Object o)
            Object remove(int index)

        以上几个方法不需要死记硬背，可以自己编写代码测试一下，理解一下，
        以后开发的时候，还是要翻阅帮助文档。
 */
public class ListTest01 {
    public static void main(String[] args) {
        // 创建List类型的集合。
        //List myList = new LinkedList();
        //List myList = new Vector();
        List myList = new ArrayList();

        // 添加元素
        myList.add("A"); // 默认都是向集合末尾添加元素。
        myList.add("B");
        myList.add("C");
        myList.add("C");
        myList.add("D");

        //在列表的指定位置插入指定元素（第一个参数是下标）
        // 这个方法使用不多，因为对于ArrayList集合来说效率比较低。
        myList.add(1, "KING");

        // 迭代
        Iterator it = myList.iterator();
        while(it.hasNext()){
            Object elt = it.next();
            System.out.println(elt);
        }

        // 根据下标获取元素
        Object firstObj = myList.get(0);
        System.out.println(firstObj);

        // 因为有下标，所以List集合有自己比较特殊的遍历方式
        // 通过下标遍历。【List集合特有的方式，Set没有。】
        for(int i = 0; i < myList.size(); i++){
            Object obj = myList.get(i);
            System.out.println(obj);
        }

        // 获取指定对象第一次出现处的索引。
        System.out.println(myList.indexOf("C")); // 3

        // 获取指定对象最后一次出现处的索引。
        System.out.println(myList.lastIndexOf("C")); // 4

        // 删除指定下标位置的元素
        // 删除下标为0的元素
        myList.remove(0);
        System.out.println(myList.size()); // 5

        System.out.println("====================================");

        // 修改指定位置的元素
        myList.set(2, "Soft");

        // 遍历集合
        for(int i = 0; i < myList.size(); i++){
            Object obj = myList.get(i);
            System.out.println(obj);
        }
    }
}

/*
计算机英语：
    增删改查这几个单词要知道：
        增：add、save、new
        删：delete、drop、remove
        改：update、set、modify
        查：find、get、query、select
 */
 ```

### 14.9 ArrayList集合初始化容量及扩容

``` java
package com.bjpowernode.javase.collection;

import java.util.ArrayList;
import java.util.List;

/*
ArrayList集合：
    1、默认初始化容量10（底层先创建了一个长度为0的数组，当添加第一个元素的时候，初始化容量10。）
    2、集合底层是一个Object[]数组。
    3、构造方法：
        new ArrayList();
        new ArrayList(20);
    4、ArrayList集合的扩容：
        增长到原容量的1.5倍。
        ArrayList集合底层是数组，怎么优化？
            尽可能少的扩容。因为数组扩容效率比较低，建议在使用ArrayList集合
            的时候预估计元素的个数，给定一个初始化容量。
    5、数组优点：
        检索效率比较高。（每个元素占用空间大小相同，内存地址是连续的，知道首元素内存地址，
        然后知道下标，通过数学表达式计算出元素的内存地址，所以检索效率最高。）
    6、数组缺点：
        随机增删元素效率比较低。
        另外数组无法存储大数据量。（很难找到一块非常巨大的连续的内存空间。）
    7、向数组末尾添加元素，效率很高，不受影响。
    8、面试官经常问的一个问题？
        这么多的集合中，你用哪个集合最多？
            答：ArrayList集合。
            因为往数组末尾添加元素，效率不受影响。
            另外，我们检索/查找某个元素的操作比较多。

    7、ArrayList集合是非线程安全的。（不是线程安全的集合。）
 */
public class ArrayListTest01 {
    public static void main(String[] args) {

        // 默认初始化容量是10
        // 数组的长度是10
        List list1 = new ArrayList();
        // 集合的size()方法是获取当前集合中元素的个数。不是获取集合的容量。
        System.out.println(list1.size()); // 0

        // 指定初始化容量
        // 数组的长度是20
        List list2 = new ArrayList(20);
        // 集合的size()方法是获取当前集合中元素的个数。不是获取集合的容量。
        System.out.println(list2.size()); // 0

        list1.add(1);
        list1.add(2);
        list1.add(3);
        list1.add(4);
        list1.add(5);
        list1.add(6);
        list1.add(7);
        list1.add(8);
        list1.add(9);
        list1.add(10);

        System.out.println(list1.size());

        // 再加一个元素
        list1.add(11);
        System.out.println(list1.size()); // 11个元素。
        /*
        int newCapacity = ArraysSupport.newLength(oldCapacity,minCapacity - oldCapacity,oldCapacity >> 1);
         */
        // 100 二进制转换成10进制： 00000100右移一位 00000010 （2）  【4 / 2】
        // 原先是4、现在增长：2，增长之后是6，增长之后的容量是之前容量的：1.5倍。
        // 6是4的1.5倍
    }
}

```

### 14.10 二进制位运算

``` java
package com.bjpowernode.javase.collection;

/*
位运算符 >>
 */
public class BinaryTest {
    public static void main(String[] args) {

        // 5
        // >> 1 二进制右移1位。
        // >> 2 二进制右移2位。
        // 10的二进制位是：00001010  【10】
        // 10的二进制右移1位是：00000101  【5】
        System.out.println(10 >> 1); // 右移1位就是除以2

        // 二进制位左移1位
        // 10的二进制位是：00001010  【10】
        // 10的二进制左移1位：00010100 【20】
        System.out.println(10 << 1);
    }
}

```

### 14.11 ArrayList集合的另一个构造方法和数组末尾添加数据效率高

``` java
package com.bjpowernode.javase.collection;

import java.util.ArrayList;
import java.util.Collection;
import java.util.HashSet;
import java.util.List;

/*
集合ArrayList的构造方法
 */
public class ArrayListTest02 {
    public static void main(String[] args) {

        // 默认初始化容量10
        List myList1 = new ArrayList();

        // 指定初始化容量100
        List myList2 = new ArrayList(100);

        // 创建一个HashSet集合
        Collection c = new HashSet();
        // 添加元素到Set集合
        c.add(100);
        c.add(200);
        c.add(900);
        c.add(50);

        // 通过这个构造方法就可以将HashSet集合转换成List集合。
        List myList3 = new ArrayList(c);
        for(int i = 0; i < myList3.size(); i++){
            System.out.println(myList3.get(i));
        }
    }
}

```

### 14.12 单向链表数据结构

``` java
package com.bjpowernode.javase.danlink;

/*
链表类。(单向链表)
 */
public class Link<E> {
    public static void main(String[] args) {
        Link<String> link = new Link<>();
        link.add("abc");

        // 类型不匹配。
        //link.add(123);
    }

    // 头节点
    Node header;

    int size = 0;

    public int size(){
        return size;
    }

    // 向链表中添加元素的方法（向末尾添加）
    public void add(E data){
    //public void add(Object data){
        // 创建一个新的节点对象
        // 让之前单链表的末尾节点next指向新节点对象。
        // 有可能这个元素是第一个，也可能是第二个，也可能是第三个。
        if(header == null){
            // 说明还没有节点。
            // new一个新的节点对象，作为头节点对象。
            // 这个时候的头节点既是一个头节点，又是一个末尾节点。
            header = new Node(data, null);
        }else {
            // 说明头不是空！
            // 头节点已经存在了！
            // 找出当前末尾节点，让当前末尾节点的next是新节点。
            Node currentLastNode = findLast(header);
            currentLastNode.next = new Node(data, null);
        }
        size++;
    }

    /**
     * 专门查找末尾节点的方法。
     */
    private Node findLast(Node node) {
        if(node.next == null) {
            // 如果一个节点的next是null
            // 说明这个节点就是末尾节点。
            return node;
        }
        // 程序能够到这里说明：node不是末尾节点。
        return findLast(node.next); // 递归算法！
    }

    // 删除链表中某个数据的方法
    public void remove(Object obj){

    }

    // 修改链表中某个数据的方法
    public void modify(Object newObj){

    }

    // 查找链表中某个元素的方法。
    public int find(Object obj){
        return 1;
    }
}

```

### 14.13 链表的优缺点

``` java
package com.bjpowernode.javase.collection;

import java.util.ArrayList;
import java.util.LinkedList;
import java.util.List;

/*
链表的优点：
    由于链表上的元素在空间存储上内存地址不连续。
    所以随机增删元素的时候不会有大量元素位移，因此随机增删效率较高。
    在以后的开发中，如果遇到随机增删集合中元素的业务比较多时，建议
    使用LinkedList。

链表的缺点：
    不能通过数学表达式计算被查找元素的内存地址，每一次查找都是从头
    节点开始遍历，直到找到为止。所以LinkedList集合检索/查找的效率
    较低。

    ArrayList：把检索发挥到极致。（末尾添加元素效率还是很高的。）
    LinkedList：把随机增删发挥到极致。
    加元素都是往末尾添加，所以ArrayList用的比LinkedList多。
 */
public class LinkedListTest01 {
    public static void main(String[] args) {
        // LinkedList集合底层也是有下标的。
        // 注意：ArrayList之所以检索效率比较高，不是单纯因为下标的原因。是因为底层数组发挥的作用。
        // LinkedList集合照样有下标，但是检索/查找某个元素的时候效率比较低，因为只能从头节点开始一个一个遍历。
        List list = new LinkedList();
        list.add("a");
        list.add("b");
        list.add("c");

        for(int i = 0; i <list.size(); i++){
            Object obj = list.get(i);
            System.out.println(obj);
        }

        // LinkedList集合有初始化容量吗？没有。
        // 最初这个链表中没有任何元素。first和last引用都是null。
        // 不管是LinkedList还是ArrayList，以后写代码时不需要关心具体是哪个集合。
        // 因为我们要面向接口编程，调用的方法都是接口中的方法。
        //List list2 = new ArrayList(); // 这样写表示底层你用了数组。
        List list2 = new LinkedList(); // 这样写表示底层你用了双向链表。

        // 以下这些方法你面向的都是接口编程。
        list2.add("123");
        list2.add("456");
        list2.add("789");

        for(int i = 0; i < list2.size(); i++){
            System.out.println(list2.get(i));
        }

    }
}
```

### 14.14 LinkList源码分析

 ``` java
package com.bjpowernode.javase.collection;

import java.util.ArrayList;
import java.util.LinkedList;
import java.util.List;

/*
链表的优点：
    由于链表上的元素在空间存储上内存地址不连续。
    所以随机增删元素的时候不会有大量元素位移，因此随机增删效率较高。
    在以后的开发中，如果遇到随机增删集合中元素的业务比较多时，建议
    使用LinkedList。

链表的缺点：
    不能通过数学表达式计算被查找元素的内存地址，每一次查找都是从头
    节点开始遍历，直到找到为止。所以LinkedList集合检索/查找的效率
    较低。

    ArrayList：把检索发挥到极致。（末尾添加元素效率还是很高的。）
    LinkedList：把随机增删发挥到极致。
    加元素都是往末尾添加，所以ArrayList用的比LinkedList多。
 */
public class LinkedListTest01 {
    public static void main(String[] args) {
        // LinkedList集合底层也是有下标的。
        // 注意：ArrayList之所以检索效率比较高，不是单纯因为下标的原因。是因为底层数组发挥的作用。
        // LinkedList集合照样有下标，但是检索/查找某个元素的时候效率比较低，因为只能从头节点开始一个一个遍历。
        List list = new LinkedList();
        list.add("a");
        list.add("b");
        list.add("c");

        for(int i = 0; i <list.size(); i++){
            Object obj = list.get(i);
            System.out.println(obj);
        }

        // LinkedList集合有初始化容量吗？没有。
        // 最初这个链表中没有任何元素。first和last引用都是null。
        // 不管是LinkedList还是ArrayList，以后写代码时不需要关心具体是哪个集合。
        // 因为我们要面向接口编程，调用的方法都是接口中的方法。
        //List list2 = new ArrayList(); // 这样写表示底层你用了数组。
        List list2 = new LinkedList(); // 这样写表示底层你用了双向链表。

        // 以下这些方法你面向的都是接口编程。
        list2.add("123");
        list2.add("456");
        list2.add("789");

        for(int i = 0; i < list2.size(); i++){
            System.out.println(list2.get(i));
        }

    }
}

 ```

![day29-LinkedList内存图](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/day29-LinkedList%E5%86%85%E5%AD%98%E5%9B%BE.png)

![day29-链表（单向链表）](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/day29-%E9%93%BE%E8%A1%A8%EF%BC%88%E5%8D%95%E5%90%91%E9%93%BE%E8%A1%A8%EF%BC%89.png)

![day29-双向链表](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/day29-%E5%8F%8C%E5%90%91%E9%93%BE%E8%A1%A8.png)

### 14.5 Vector源码分析

``` java
package com.bjpowernode.javase.collection;

import java.util.*;

/*
Vector：
    1、底层也是一个数组。
    2、初始化容量：10
    3、怎么扩容的？
        扩容之后是原容量的2倍。
        10--> 20 --> 40 --> 80

    4、ArrayList集合扩容特点：
        ArrayList集合扩容是原容量1.5倍。

    5、Vector中所有的方法都是线程同步的，都带有synchronized关键字，
    是线程安全的。效率比较低，使用较少了。

    6、怎么将一个线程不安全的ArrayList集合转换成线程安全的呢？
        使用集合工具类：
            java.util.Collections;

            java.util.Collection 是集合接口。
            java.util.Collections 是集合工具类。
 */
public class VectorTest {
    public static void main(String[] args) {
        // 创建一个Vector集合
        List vector = new Vector();
        //Vector vector = new Vector();

        // 添加元素
        // 默认容量10个。
        vector.add(1);
        vector.add(2);
        vector.add(3);
        vector.add(4);
        vector.add(5);
        vector.add(6);
        vector.add(7);
        vector.add(8);
        vector.add(9);
        vector.add(10);

        // 满了之后扩容（扩容之后的容量是20.）
        vector.add(11);

        Iterator it = vector.iterator();
        while(it.hasNext()){
            Object obj = it.next();
            System.out.println(obj);
        }

        // 这个可能以后要使用！！！！
        List myList = new ArrayList(); // 非线程安全的。

        // 变成线程安全的
        Collections.synchronizedList(myList); // 这里没有办法看效果，因为多线程没学，你记住先！

        // myList集合就是线程安全的了。
        myList.add("111");
        myList.add("222");
        myList.add("333");
    }
}

```

### 14.6 泛型机制

``` java
package com.bjpowernode.javase.collection;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

/*
1、JDK5.0之后推出的新特性：泛型
2、泛型这种语法机制，只在程序编译阶段起作用，只是给编译器参考的。（运行阶段泛型没用！）
3、使用了泛型好处是什么？
    第一：集合中存储的元素类型统一了。
    第二：从集合中取出的元素类型是泛型指定的类型，不需要进行大量的“向下转型”！

4、泛型的缺点是什么？
    导致集合中存储的元素缺乏多样性！
    大多数业务中，集合中元素的类型还是统一的。所以这种泛型特性被大家所认可。
 */
public class GenericTest01 {
    public static void main(String[] args) {

        /*
        // 不使用泛型机制，分析程序存在缺点
        List myList = new ArrayList();

        // 准备对象
        Cat c = new Cat();
        Bird b = new Bird();

        // 将对象添加到集合当中
        myList.add(c);
        myList.add(b);

        // 遍历集合，取出每个Animal，让它move
        Iterator it = myList.iterator();
        while(it.hasNext()) {
            // 没有这个语法，通过迭代器取出的就是Object
            //Animal a = it.next();

            Object obj = it.next();
            //obj中没有move方法，无法调用，需要向下转型！
            if(obj instanceof Animal){
                Animal a = (Animal)obj;
                a.move();
            }
        }
         */

        // 使用JDK5之后的泛型机制
        // 使用泛型List<Animal>之后，表示List集合中只允许存储Animal类型的数据。
        // 用泛型来指定集合中存储的数据类型。
        List<Animal> myList = new ArrayList<Animal>();

        // 指定List集合中只能存储Animal，那么存储String就编译报错了。
        // 这样用了泛型之后，集合中元素的数据类型更加统一了。
        //myList.add("abc");

        Cat c = new Cat();
        Bird b = new Bird();

        myList.add(c);
        myList.add(b);

        // 获取迭代器
        // 这个表示迭代器迭代的是Animal类型。
        Iterator<Animal> it = myList.iterator();
        while(it.hasNext()){
            // 使用泛型之后，每一次迭代返回的数据都是Animal类型。
            //Animal a = it.next();
            // 这里不需要进行强制类型转换了。直接调用。
            //a.move();

            // 调用子类型特有的方法还是需要向下转换的！
            Animal a = it.next();
            if(a instanceof Cat) {
                Cat x = (Cat)a;
                x.catchMouse();
            }
            if(a instanceof Bird) {
                Bird y = (Bird)a;
                y.fly();
            }
        }
    }
}

class Animal {
    // 父类自带方法
    public void move(){
        System.out.println("动物在移动！");
    }
}

class Cat extends Animal {
    // 特有方法
    public void catchMouse(){
        System.out.println("猫抓老鼠！");
    }
}

class Bird extends Animal {
    // 特有方法
    public void fly(){
        System.out.println("鸟儿在飞翔！");
    }
}
```

### 14.7 类型自动推断

``` java
package com.bjpowernode.javase.collection;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

/*
JDK之后引入了：自动类型推断机制。（又称为钻石表达式）
 */
public class GenericTest02 {
    public static void main(String[] args) {

        // ArrayList<这里的类型会自动推断>()，前提是JDK8之后才允许。
        // 自动类型推断，钻石表达式！
        List<Animal> myList = new ArrayList<>();

        myList.add(new Animal());
        myList.add(new Cat());
        myList.add(new Bird());

        // 遍历
        Iterator<Animal> it = myList.iterator();
        while(it.hasNext()){
            Animal a = it.next();
            a.move();
        }

        List<String> strList = new ArrayList<>();

        // 类型不匹配。
        //strList.add(new Cat());
        strList.add("http://www.126.com");
        strList.add("http://www.baidu.com");
        strList.add("http://www.bjpowernode.com");

        // 类型不匹配。
        //strList.add(123);

        //System.out.println(strList.size());

        // 遍历
        Iterator<String> it2 = strList.iterator();
        while(it2.hasNext()){
            // 如果没有使用泛型
            /*
            Object obj = it2.next();
            if(obj instanceof String){
                String ss = (String)obj;
                ss.substring(7);
            }
             */
            // 直接通过迭代器获取了String类型的数据
            String s = it2.next();
            // 直接调用String类的substring方法截取字符串。
            String newString = s.substring(7);
            System.out.println(newString);
        }
    }
}
```

### 14.8 自动泛型

``` java
package com.bjpowernode.javase.collection;

/*
自定义泛型可以吗？可以
    自定义泛型的时候，<> 尖括号中的是一个标识符，随便写。
    java源代码中经常出现的是：
        <E>和<T>
    E是Element单词首字母。
    T是Type单词首字母。
 */
public class GenericTest03<标识符随便写> {

    public void doSome(标识符随便写 o){
        System.out.println(o);
    }

    public static void main(String[] args) {

        // new对象的时候指定了泛型是：String类型
        GenericTest03<String> gt = new GenericTest03<>();

        // 类型不匹配
        //gt.doSome(100);

        gt.doSome("abc");

        // =============================================================
        GenericTest03<Integer> gt2 = new GenericTest03<>();
        gt2.doSome(100);

        // 类型不匹配
        //gt2.doSome("abc");

        MyIterator<String> mi = new MyIterator<>();
        String s1 = mi.get();

        MyIterator<Animal> mi2 = new MyIterator<>();
        Animal a = mi2.get();

        // 不用泛型就是Object类型。
        /*GenericTest03 gt3 = new GenericTest03();
        gt3.doSome(new Object());*/
    }
}

class MyIterator<T> {
    public T get(){
        return null;
    }
}
```

### 14.9 foreach

``` java
package com.bjpowernode.javase.collection;

/*
JDK5.0之后推出了一个新特性：叫做增强for循环，或者叫做foreach
 */
public class ForEachTest01 {
    public static void main(String[] args) {

        // int类型数组
        int[] arr = {432,4,65,46,54,76,54};

        // 遍历数组（普通for循环）
        for(int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }

        // 增强for（foreach）
        // 以下是语法
        /*for(元素类型 变量名 : 数组或集合){
            System.out.println(变量名);
        }*/

        System.out.println("======================================");
        // foreach有一个缺点：没有下标。在需要使用下标的循环中，不建议使用增强for循环。
        for(int data : arr) {
            // data就是数组中的元素（数组中的每一个元素。）
            System.out.println(data);
        }
    }
}

package com.bjpowernode.javase.collection;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

/*
集合使用foreach
 */
public class ForEachTest02 {
    public static void main(String[] args) {
        // 创建List集合
        List<String> strList = new ArrayList<>();

        // 添加元素
        strList.add("hello");
        strList.add("world!");
        strList.add("kitty!");

        // 遍历，使用迭代器方式
        Iterator<String> it = strList.iterator();
        while(it.hasNext()){
            String s = it.next();
            System.out.println(s);
        }

        // 使用下标方式（只针对于有下标的集合）
        for(int i = 0; i < strList.size(); i++){
            System.out.println(strList.get(i));
        }

        // 使用foreach
        for(String s : strList){ // 因为泛型使用的是String类型，所以是：String s
            System.out.println(s);
        }

        List<Integer> list = new ArrayList<>();
        list.add(100);
        list.add(200);
        list.add(300);
        for(Integer i : list){ // i代表集合中的元素
            System.out.println(i);
        }
    }
}

```

### 14.10 HashSet集合特点

``` java
package com.bjpowernode.javase.collection;

import java.util.HashSet;
import java.util.Set;

/*
HashSet集合：
    无序不可重复。
 */
public class HashSetTest01 {
    public static void main(String[] args) {
        // 演示一下HashSet集合特点
        Set<String> strs = new HashSet<>();

        // 添加元素
        strs.add("hello3");
        strs.add("hello4");
        strs.add("hello1");
        strs.add("hello2");
        strs.add("hello3");
        strs.add("hello3");
        strs.add("hello3");
        strs.add("hello3");

        // 遍历
        /*
        hello1
        hello4
        hello2
        hello3
        1、存储时顺序和取出的顺序不同。
        2、不可重复。
        3、放到HashSet集合中的元素实际上是放到HashMap集合的key部分了。
         */
        for(String s : strs){
            System.out.println(s);
        }
    }
}

```

### 14.11 TreeSet集合特点

``` java
package com.bjpowernode.javase.collection;

import java.util.Set;
import java.util.TreeSet;

/*
TreeSet集合存储元素特点：
    1、无序不可重复的，但是存储的元素可以自动按照大小顺序排序！
    称为：可排序集合。

    2、无序：这里的无序指的是存进去的顺序和取出来的顺序不同。并且没有下标。
 */
public class TreeSetTest01 {
    public static void main(String[] args) {
        // 创建集合对象
        Set<String> strs = new TreeSet<>();
        // 添加元素
        strs.add("A");
        strs.add("B");
        strs.add("Z");
        strs.add("Y");
        strs.add("Z");
        strs.add("K");
        strs.add("M");
        // 遍历
        /*
            A
            B
            K
            M
            Y
            Z
        从小到大自动排序！
         */
        for(String s : strs){
            System.out.println(s);
        }
    }
}

```

### 14.12 Map接口常用方法

``` java
package com.bjpowernode.javase.collection;

import java.util.Collection;
import java.util.HashMap;
import java.util.Map;

/*
java.util.Map接口中常用的方法：
    1、Map和Collection没有继承关系。
    2、Map集合以key和value的方式存储数据：键值对
        key和value都是引用数据类型。
        key和value都是存储对象的内存地址。
        key起到主导的地位，value是key的一个附属品。
    3、Map接口中常用方法：
        V put(K key, V value) 向Map集合中添加键值对
        V get(Object key) 通过key获取value
        void clear()    清空Map集合
        boolean containsKey(Object key) 判断Map中是否包含某个key
        boolean containsValue(Object value) 判断Map中是否包含某个value
        boolean isEmpty()   判断Map集合中元素个数是否为0
        V remove(Object key) 通过key删除键值对
        int size() 获取Map集合中键值对的个数。
        Collection<V> values() 获取Map集合中所有的value，返回一个Collection

        Set<K> keySet() 获取Map集合所有的key（所有的键是一个set集合）

        Set<Map.Entry<K,V>> entrySet()
            将Map集合转换成Set集合
            假设现在有一个Map集合，如下所示：
                map1集合对象
                key             value
                ----------------------------
                1               zhangsan
                2               lisi
                3               wangwu
                4               zhaoliu

                Set set = map1.entrySet();
                set集合对象
                1=zhangsan 【注意：Map集合通过entrySet()方法转换成的这个Set集合，Set集合中元素的类型是 Map.Entry<K,V>】
                2=lisi     【Map.Entry和String一样，都是一种类型的名字，只不过：Map.Entry是静态内部类，是Map中的静态内部类】
                3=wangwu
                4=zhaoliu ---> 这个东西是个什么？Map.Entry
 */
public class MapTest01 {
    public static void main(String[] args) {
        // 创建Map集合对象
        Map<Integer, String> map = new HashMap<>();
        // 向Map集合中添加键值对
        map.put(1, "zhangsan"); // 1在这里进行了自动装箱。
        map.put(2, "lisi");
        map.put(3, "wangwu");
        map.put(4, "zhaoliu");
        // 通过key获取value
        String value = map.get(2);
        System.out.println(value);
        // 获取键值对的数量
        System.out.println("键值对的数量：" + map.size());
        // 通过key删除key-value
        map.remove(2);
        System.out.println("键值对的数量：" + map.size());
        // 判断是否包含某个key
        // contains方法底层调用的都是equals进行比对的，所以自定义的类型需要重写equals方法。
        System.out.println(map.containsKey(new Integer(4))); // true
        // 判断是否包含某个value
        System.out.println(map.containsValue(new String("wangwu"))); // true

        // 获取所有的value
        Collection<String> values = map.values();
        // foreach
        for(String s : values){
            System.out.println(s);
        }

        // 清空map集合
        map.clear();
        System.out.println("键值对的数量：" + map.size());
        // 判断是否为空
        System.out.println(map.isEmpty()); // true
    }
}


package com.bjpowernode.javase.collection;


import java.util.HashSet;
import java.util.Set;

public class MyClass {

    // 声明一个静态内部类
    private static class InnerClass {

        // 静态方法
        public static void m1(){
            System.out.println("静态内部类的m1方法执行");
        }

        // 实例方法
        public void m2(){
            System.out.println("静态内部类中的实例方法执行！");
        }

    }

    public static void main(String[] args) {

        // 类名叫做：MyClass.InnerClass
        MyClass.InnerClass.m1();

        // 创建静态内部类对象
        MyClass.InnerClass mi =  new MyClass.InnerClass();
        mi.m2();

        // 给一个Set集合
        // 该Set集合中存储的对象是：MyClass.InnerClass类型
        Set<MyClass.InnerClass> set = new HashSet<>();

        // 这个Set集合中存储的是字符串对象。
        Set<String> set2 = new HashSet<>();

        Set<MyMap.MyEntry<Integer, String>> set3 = new HashSet<>();
    }
}


class MyMap {
    public static class MyEntry<K,V> {

    }
}

```

### 14.13 遍历Map集合方法

``` java
package com.bjpowernode.javase.collection;

import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;
import java.util.Set;

/*
Map集合的遍历。【非常重要】
 */
public class MapTest02 {
    public static void main(String[] args) {

        // 第一种方式：获取所有的key，通过遍历key，来遍历value
        Map<Integer, String> map = new HashMap<>();
        map.put(1, "zhangsan");
        map.put(2, "lisi");
        map.put(3, "wangwu");
        map.put(4, "zhaoliu");
        // 遍历Map集合
        // 获取所有的key，所有的key是一个Set集合
        Set<Integer> keys = map.keySet();
        // 遍历key，通过key获取value
        // 迭代器可以
        /*Iterator<Integer> it = keys.iterator();
        while(it.hasNext()){
            // 取出其中一个key
            Integer key = it.next();
            // 通过key获取value
            String value = map.get(key);
            System.out.println(key + "=" + value);
        }*/
        // foreach也可以
        for(Integer key : keys){
            System.out.println(key + "=" + map.get(key));
        }

        // 第二种方式：Set<Map.Entry<K,V>> entrySet()
        // 以上这个方法是把Map集合直接全部转换成Set集合。
        // Set集合中元素的类型是：Map.Entry
        Set<Map.Entry<Integer,String>> set = map.entrySet();
        // 遍历Set集合，每一次取出一个Node
        // 迭代器
        /*Iterator<Map.Entry<Integer,String>> it2 = set.iterator();
        while(it2.hasNext()){
            Map.Entry<Integer,String> node = it2.next();
            Integer key = node.getKey();
            String value = node.getValue();
            System.out.println(key + "=" + value);
        }*/

        // foreach
        // 这种方式效率比较高，因为获取key和value都是直接从node对象中获取的属性值。
        // 这种方式比较适合于大数据量。
        for(Map.Entry<Integer,String> node : set){
            System.out.println(node.getKey() + "--->" + node.getValue());
        }
    }
}

```

### 14.14 哈希表数据结构同时重写hashCode和equals

``` java
package com.bjpowernode.javase.collection;

import java.util.HashMap;
import java.util.Map;
import java.util.Set;

/*
HashMap集合：
    1、HashMap集合底层是哈希表/散列表的数据结构。
    2、哈希表是一个怎样的数据结构呢？
        哈希表是一个数组和单向链表的结合体。
        数组：在查询方面效率很高，随机增删方面效率很低。
        单向链表：在随机增删方面效率较高，在查询方面效率很低。
        哈希表将以上的两种数据结构融合在一起，充分发挥它们各自的优点。
    3、HashMap集合底层的源代码：
        public class HashMap{
            // HashMap底层实际上就是一个数组。（一维数组）
            Node<K,V>[] table;
            // 静态的内部类HashMap.Node
            static class Node<K,V> {
                final int hash; // 哈希值（哈希值是key的hashCode()方法的执行结果。hash值通过哈希函数/算法，可以转换存储成数组的下标。）
                final K key; // 存储到Map集合中的那个key
                V value; // 存储到Map集合中的那个value
                Node<K,V> next; // 下一个节点的内存地址。
            }
        }
        哈希表/散列表：一维数组，这个数组中每一个元素是一个单向链表。（数组和链表的结合体。）
    4、最主要掌握的是：
        map.put(k,v)
        v = map.get(k)
        以上这两个方法的实现原理，是必须掌握的。
    5、HashMap集合的key部分特点：
        无序，不可重复。
        为什么无序？ 因为不一定挂到哪个单向链表上。
        不可重复是怎么保证的？ equals方法来保证HashMap集合的key不可重复。
        如果key重复了，value会覆盖。

        放在HashMap集合key部分的元素其实就是放到HashSet集合中了。
        所以HashSet集合中的元素也需要同时重写hashCode()+equals()方法。

    6、哈希表HashMap使用不当时无法发挥性能！
        假设将所有的hashCode()方法返回值固定为某个值，那么会导致底层哈希表变成了
        纯单向链表。这种情况我们成为：散列分布不均匀。
        什么是散列分布均匀？
            假设有100个元素，10个单向链表，那么每个单向链表上有10个节点，这是最好的，
            是散列分布均匀的。
        假设将所有的hashCode()方法返回值都设定为不一样的值，可以吗，有什么问题？
            不行，因为这样的话导致底层哈希表就成为一维数组了，没有链表的概念了。
            也是散列分布不均匀。
        散列分布均匀需要你重写hashCode()方法时有一定的技巧。
    7、重点：放在HashMap集合key部分的元素，以及放在HashSet集合中的元素，需要同时重写hashCode和equals方法。
    8、HashMap集合的默认初始化容量是16，默认加载因子是0.75
        这个默认加载因子是当HashMap集合底层数组的容量达到75%的时候，数组开始扩容。

        重点，记住：HashMap集合初始化容量必须是2的倍数，这也是官方推荐的，
        这是因为达到散列均匀，为了提高HashMap集合的存取效率，所必须的。
 */
public class HashMapTest01 {
    public static void main(String[] args) {
        // 测试HashMap集合key部分的元素特点
        // Integer是key，它的hashCode和equals都重写了。
        Map<Integer,String> map = new HashMap<>();
        map.put(1111, "zhangsan");
        map.put(6666, "lisi");
        map.put(7777, "wangwu");
        map.put(2222, "zhaoliu");
        map.put(2222, "king"); //key重复的时候value会自动覆盖。

        System.out.println(map.size()); // 4

        // 遍历Map集合
        Set<Map.Entry<Integer,String>> set = map.entrySet();
        for(Map.Entry<Integer,String> entry : set){
            // 验证结果：HashMap集合key部分元素：无序不可重复。
            System.out.println(entry.getKey() + "=" + entry.getValue());
        }
    }
}

```

![day30-Map集合转换成Set集合entrySet()方法](E:\java\JavaSE\JavaSE进阶每日复习笔记\day30-Map集合转换成Set集合entrySet()方法.png)

![day30-哈希表或者散列表数据结构](E:\java\JavaSE\JavaSE进阶每日复习笔记\day30-哈希表或者散列表数据结构.png)

### 14.15同时重写hashCode和equals和java对hashMap集合的改进

``` ava
package com.bjpowernode.javase.bean;

import java.util.Objects;

public class Student {
    private String name;

    public Student() {
    }

    public Student(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    // hashCode

    // equals（如果学生名字一样，表示同一个学生。）
    /*public boolean equals(Object obj){
        if(obj == null || !(obj instanceof Student)) return false;
        if(obj == this) return true;
        Student s = (Student)obj;
        return this.name.equals(s.name);
    }*/

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Student student = (Student) o;
        return Objects.equals(name, student.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name);
    }
}

package com.bjpowernode.javase.bean;

import java.util.HashSet;
import java.util.Set;

/*
1、向Map集合中存，以及从Map集合中取，都是先调用key的hashCode方法，然后再调用equals方法！
equals方法有可能调用，也有可能不调用。
    拿put(k,v)举例，什么时候equals不会调用？
        k.hashCode()方法返回哈希值，
        哈希值经过哈希算法转换成数组下标。
        数组下标位置上如果是null，equals不需要执行。
    拿get(k)举例，什么时候equals不会调用？
        k.hashCode()方法返回哈希值，
        哈希值经过哈希算法转换成数组下标。
        数组下标位置上如果是null，equals不需要执行。

2、注意：如果一个类的equals方法重写了，那么hashCode()方法必须重写。
并且equals方法返回如果是true，hashCode()方法返回的值必须一样。
    equals方法返回true表示两个对象相同，在同一个单向链表上比较。
    那么对于同一个单向链表上的节点来说，他们的哈希值都是相同的。
    所以hashCode()方法的返回值也应该相同。

3、hashCode()方法和equals()方法不用研究了，直接使用IDEA工具生成，但是这两个方法需要同时生成。

4、终极结论：
    放在HashMap集合key部分的，以及放在HashSet集合中的元素，需要同时重写hashCode方法和equals方法。

5、对于哈希表数据结构来说：
    如果o1和o2的hash值相同，一定是放到同一个单向链表上。
    当然如果o1和o2的hash值不同，但由于哈希算法执行结束之后转换的数组下标可能相同，此时会发生“哈希碰撞”。

 */
public class HashMapTest02 {
    public static void main(String[] args) {

        Student s1 = new Student("zhangsan");
        Student s2 = new Student("zhangsan");

        // 重写equals方法之前是false
        //System.out.println(s1.equals(s2)); // false

        // 重写equals方法之后是true
        System.out.println(s1.equals(s2)); //true （s1和s2表示相等）

        System.out.println("s1的hashCode=" + s1.hashCode()); //284720968 (重写hashCode之后-1432604525)
        System.out.println("s2的hashCode=" + s2.hashCode()); //122883338 (重写hashCode之后-1432604525)

        // s1.equals(s2)结果已经是true了，表示s1和s2是一样的，相同的，那么往HashSet集合中放的话，
        // 按说只能放进去1个。（HashSet集合特点：无序不可重复）
        Set<Student> students = new HashSet<>();
        students.add(s1);
        students.add(s2);
        System.out.println(students.size()); // 这个结果按说应该是1. 但是结果是2.显然不符合HashSet集合存储特点。怎么办？
    }
}

```

### 14.16HashMap和Hashtable的区别

``` java
package com.bjpowernode.javase.bean;

import java.util.HashMap;
import java.util.Map;

/*
HashMap集合key部分允许null吗？
    允许
    但是要注意：HashMap集合的key null值只能有一个。
    有可能面试的时候遇到这样的问题。
 */
public class HashMapTest03 {
    public static void main(String[] args) {

        Map map = new HashMap();

        // HashMap集合允许key为null
        map.put(null, null);
        System.out.println(map.size()); // 1

        // key重复的话value是覆盖！
        map.put(null, 100);
        System.out.println(map.size()); //1

        // 通过key获取value
        System.out.println(map.get(null)); // 100
    }
}


package com.bjpowernode.javase.bean;

import java.util.Hashtable;
import java.util.Map;

/*
Hashtable的key可以为null吗？
    Hashtable的key和value都是不能为null的。
    HashMap集合的key和value都是可以为null的。

Hashtable方法都带有synchronized：线程安全的。
线程安全有其它的方案，这个Hashtable对线程的处理
导致效率较低，使用较少了。

Hashtable和HashMap一样，底层都是哈希表数据结构。
Hashtable的初始化容量是11，默认加载因子是：0.75f
Hashtable的扩容是：原容量 * 2 + 1
 */
public class HashtableTest01 {
    public static void main(String[] args) {
        Map map = new Hashtable();

        //map.put(null, "123");
        map.put(100, null);

    }
}

```

### 14.17 properties类

``` java
package com.bjpowernode.javase.collection;

import java.util.Properties;

/*
目前只需要掌握Properties属性类对象的相关方法即可。
Properties是一个Map集合，继承Hashtable，Properties的key和value都是String类型。
Properties被称为属性类对象。
Properties是线程安全的。
 */
public class PropertiesTest01 {
    public static void main(String[] args) {

        // 创建一个Properties对象
        Properties pro = new Properties();

        // 需要掌握Properties的两个方法，一个存，一个取。
        pro.setProperty("url", "jdbc:mysql://localhost:3306/bjpowernode");
        pro.setProperty("driver","com.mysql.jdbc.Driver");
        pro.setProperty("username", "root");
        pro.setProperty("password", "123");

        // 通过key获取value
        String url = pro.getProperty("url");
        String driver = pro.getProperty("driver");
        String username = pro.getProperty("username");
        String password = pro.getProperty("password");

        System.out.println(url);
        System.out.println(driver);
        System.out.println(username);
        System.out.println(password);

    }
}

```

### 14.18 TreeSet对String是可排序的

``` java
package com.bjpowernode.javase.collection;

import java.util.TreeSet;

/*
1、TreeSet集合底层实际上是一个TreeMap
2、TreeMap集合底层是一个二叉树。
3、放到TreeSet集合中的元素，等同于放到TreeMap集合key部分了。
4、TreeSet集合中的元素：无序不可重复，但是可以按照元素的大小顺序自动排序。
称为：可排序集合。
 */
public class TreeSetTest02 {
    public static void main(String[] args) {
        // 创建一个TreeSet集合
        TreeSet<String> ts = new TreeSet<>();
        // 添加String
        ts.add("zhangsan");
        ts.add("lisi");
        ts.add("wangwu");
        ts.add("zhangsi");
        ts.add("wangliu");
        // 遍历
        for(String s : ts){
            // 按照字典顺序，升序！
            System.out.println(s);
        }

        TreeSet<Integer> ts2 = new TreeSet<>();
        ts2.add(100);
        ts2.add(200);
        ts2.add(900);
        ts2.add(800);
        ts2.add(600);
        ts2.add(10);
        for(Integer elt : ts2){
            // 升序！
            System.out.println(elt);
        }
    }
}

/*
数据库中有很多数据：
    userid  name     birth
    -------------------------------------
    1       zs          1980-11-11
    2       ls          1980-10-11
    3       ww          1981-11-11
    4       zl          1979-11-11

    编写程序从数据库当中取出数据，在页面展示用户信息的时候按照生日升序或者降序。
    这个时候可以使用TreeSet集合，因为TreeSet集合放进去，拿出来就是有顺序的。
 */

```

### 14.19 TreeSet无法对自定义类型排序

``` java
package com.bjpowernode.javase.collection;

import java.util.TreeSet;

/*
对自定义的类型来说，TreeSet可以排序吗？
    以下程序中对于Person类型来说，无法排序。因为没有指定Person对象之间的比较规则。
    谁大谁小并没有说明啊。

    以下程序运行的时候出现了这个异常：
        java.lang.ClassCastException:
            class com.bjpowernode.javase.collection.Person
            cannot be cast to class java.lang.Comparable
    出现这个异常的原因是：
        Person类没有实现java.lang.Comparable接口。
 */
public class TreeSetTest03 {
    public static void main(String[] args) {
        Person p1 = new Person(32);
        //System.out.println(p1);
        Person p2 = new Person(20);
        Person p3 = new Person(30);
        Person p4 = new Person(25);

        // 创建TreeSet集合
        TreeSet<Person> persons = new TreeSet<>();
        // 添加元素
        persons.add(p1);
        persons.add(p2);
        persons.add(p3);
        persons.add(p4);

        // 遍历
        for (Person p : persons){
            System.out.println(p);
        }
    }
}

class Person {
    int age;
    public Person(int age){
        this.age = age;
    }

    // 重写toString()方法
    public String toString(){
        return "Person[age="+age+"]";
    }
}

```

### 14.20 自定义类型实现Comparable接口

``` java
package com.bjpowernode.javase.collection;

import java.util.TreeSet;

public class TreeSetTest04 {
    public static void main(String[] args) {
        Customer c1 = new Customer(32);
        Customer c2 = new Customer(20);
        Customer c3 = new Customer(30);
        Customer c4 = new Customer(25);

        // 创建TreeSet集合
        TreeSet<Customer> customers = new TreeSet<>();
        // 添加元素
        customers.add(c1);
        customers.add(c2);
        customers.add(c3);
        customers.add(c4);

        // 遍历
        for (Customer c : customers){
            System.out.println(c);
        }
    }
}

// 放在TreeSet集合中的元素需要实现java.lang.Comparable接口。
// 并且实现compareTo方法。equals可以不写。
class Customer implements Comparable<Customer>{

    int age;
    public Customer(int age){
        this.age = age;
    }

    // 需要在这个方法中编写比较的逻辑，或者说比较的规则，按照什么进行比较！
    // k.compareTo(t.key)
    // 拿着参数k和集合中的每一个k进行比较，返回值可能是>0 <0 =0
    // 比较规则最终还是由程序员指定的：例如按照年龄升序。或者按照年龄降序。
    @Override
    public int compareTo(Customer c) { // c1.compareTo(c2);
        // this是c1
        // c是c2
        // c1和c2比较的时候，就是this和c比较。
        /*int age1 = this.age;
        int age2 = c.age;
        if(age1 == age2){
            return 0;
        } else if(age1 > age2) {
            return 1;
        } else {
            return -1;
        }*/
        //return this.age - c.age; // =0 >0 <0
        return c.age - this.age;
    }

    public String toString(){
        return "Customer[age="+age+"]";
    }
}


```

### 14.21 比较规则该怎么写

``` java
package com.bjpowernode.javase.collection;

import java.util.TreeSet;

/*
先按照年龄升序，如果年龄一样的再按照姓名升序。
 */
public class TreeSetTest05 {
    public static void main(String[] args) {
        TreeSet<Vip> vips = new TreeSet<>();
        vips.add(new Vip("zhangsi", 20));
        vips.add(new Vip("zhangsan", 20));
        vips.add(new Vip("king", 18));
        vips.add(new Vip("soft", 17));
        for(Vip vip : vips){
            System.out.println(vip);
        }
    }
}

class Vip implements Comparable<Vip>{
    String name;
    int age;

    public Vip(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public String toString() {
        return "Vip{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

    /*
    compareTo方法的返回值很重要：
        返回0表示相同，value会覆盖。
        返回>0，会继续在右子树上找。【10 - 9 = 1 ，1 > 0的说明左边这个数字比较大。所以在右子树上找。】
        返回<0，会继续在左子树上找。
     */
    @Override
    public int compareTo(Vip v) {
        // 写排序规则，按照什么进行比较。
        if(this.age == v.age){
            // 年龄相同时按照名字排序。
            // 姓名是String类型，可以直接比。调用compareTo来完成比较。
            return this.name.compareTo(v.name);
        } else {
            // 年龄不一样
            return this.age - v.age;
        }
    }
}


```

### 14.22 自平衡二叉树数据结构和实现比较器接口

``` java
package com.bjpowernode.javase.collection;

import java.util.Comparator;
import java.util.TreeSet;

/*
TreeSet集合中元素可排序的第二种方式：使用比较器的方式。
最终的结论：
    放到TreeSet或者TreeMap集合key部分的元素要想做到排序,包括两种方式：
        第一种：放在集合中的元素实现java.lang.Comparable接口。
        第二种：在构造TreeSet或者TreeMap集合的时候给它传一个比较器对象。
Comparable和Comparator怎么选择呢？
    当比较规则不会发生改变的时候，或者说当比较规则只有1个的时候，建议实现Comparable接口。
    如果比较规则有多个，并且需要多个比较规则之间频繁切换，建议使用Comparator接口。

    Comparator接口的设计符合OCP原则。
 */
public class TreeSetTest06 {
    public static void main(String[] args) {
        // 创建TreeSet集合的时候，需要使用这个比较器。
        // TreeSet<WuGui> wuGuis = new TreeSet<>();//这样不行，没有通过构造方法传递一个比较器进去。

        // 给构造方法传递一个比较器。
        //TreeSet<WuGui> wuGuis = new TreeSet<>(new WuGuiComparator());

        // 大家可以使用匿名内部类的方式（这个类没有名字。直接new接口。）
        TreeSet<WuGui> wuGuis = new TreeSet<>(new Comparator<WuGui>() {
            @Override
            public int compare(WuGui o1, WuGui o2) {
                return o1.age - o2.age;
            }
        });

        wuGuis.add(new WuGui(1000));
        wuGuis.add(new WuGui(800));
        wuGuis.add(new WuGui(810));

        for(WuGui wuGui : wuGuis){
            System.out.println(wuGui);
        }
    }
}

// 乌龟
class WuGui{

    int age;

    public WuGui(int age){
        this.age = age;
    }

    @Override
    public String toString() {
        return "小乌龟[" +
                "age=" + age +
                ']';
    }
}

// 单独在这里编写一个比较器
// 比较器实现java.util.Comparator接口。（Comparable是java.lang包下的。Comparator是java.util包下的。）
/*
class WuGuiComparator implements Comparator<WuGui> {

    @Override
    public int compare(WuGui o1, WuGui o2) {
        // 指定比较规则
        // 按照年龄排序
        return o1.age - o2.age;
    }
}
 */

```

![day30-自平衡二叉树](E:\java\JavaSE\JavaSE进阶每日复习笔记\day30-自平衡二叉树.png)

### 14.23 collection工具类

``` java
package com.bjpowernode.javase.collection;

import java.util.*;

/*
java.util.Collection 集合接口
java.util.Collections 集合工具类，方便集合的操作。
 */
public class CollectionsTest {
    public static void main(String[] args) {

        // ArrayList集合不是线程安全的。
        List<String> list = new ArrayList<>();

        // 变成线程安全的
        Collections.synchronizedList(list);

        // 排序
        list.add("abf");
        list.add("abx");
        list.add("abc");
        list.add("abe");

        Collections.sort(list);
        for(String s : list){
            System.out.println(s);
        }

        List<WuGui2> wuGuis = new ArrayList<>();
        wuGuis.add(new WuGui2(1000));
        wuGuis.add(new WuGui2(8000));
        wuGuis.add(new WuGui2(500));
        // 注意：对List集合中元素排序，需要保证List集合中的元素实现了：Comparable接口。
        Collections.sort(wuGuis);
        for(WuGui2 wg : wuGuis){
            System.out.println(wg);
        }

        // 对Set集合怎么排序呢？
        Set<String> set = new HashSet<>();
        set.add("king");
        set.add("kingsoft");
        set.add("king2");
        set.add("king1");
        // 将Set集合转换成List集合
        List<String> myList = new ArrayList<>(set);
        Collections.sort(myList);
        for(String s : myList) {
            System.out.println(s);
        }

        // 这种方式也可以排序。
        //Collections.sort(list集合, 比较器对象);
    }
}

class WuGui2 implements Comparable<WuGui2>{
    int age;
    public WuGui2(int age){
        this.age = age;
    }

    @Override
    public int compareTo(WuGui2 o) {
        return this.age - o.age;
    }

    @Override
    public String toString() {
        return "WuGui2{" +
                "age=" + age +
                '}';
    }
}



```

### 14.24 回顾List

```java
package com.bjpowernode.javase.review;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.LinkedList;

/*
    1.1、每个集合对象的创建（new）
	1.2、向集合中添加元素
	1.3、从集合中取出某个元素
	1.4、遍历集合
 */
public class ArrayListTest {
    public static void main(String[] args) {
        // 创建集合对象
        //ArrayList<String> list = new ArrayList<>();
        LinkedList<String> list = new LinkedList<>();
        // 添加元素
        list.add("zhangsan");
        list.add("lisi");
        list.add("wangwu");
        // 从集合中取出某个元素
        // List集合有下标
        String firstElt = list.get(0);
        System.out.println(firstElt);
        // 遍历（下标方式）
        for(int i = 0; i < list.size(); i++){
            String elt = list.get(i);
            System.out.println(elt);
        }
        // 遍历（迭代器方式，这个是通用的，所有Collection都能用）
        Iterator<String> it = list.iterator();
        while(it.hasNext()){
            System.out.println(it.next());
        }

        // while循环修改为for循环
        /*for(Iterator<String> it2 = list.iterator(); it2.hasNext(); ){
            System.out.println("====>" + it2.next());
        }*/

        // 遍历（foreach方式）
        for(String s : list){
            System.out.println(s);
        }
    }
}

```

### 14.25 回顾HashSet

``` java
package com.bjpowernode.javase.review;

import java.util.HashSet;
import java.util.Iterator;
import java.util.Objects;
import java.util.Set;

/*
    1.1、每个集合对象的创建（new）
	1.2、向集合中添加元素
	1.3、从集合中取出某个元素
	1.4、遍历集合
	1.5、测试HashSet集合的特点：无序不可重复。
 */
public class HashSetTest {
    public static void main(String[] args) {
        // 创建集合对象
        HashSet<String> set = new HashSet<>();

        // 添加元素
        set.add("abc");
        set.add("def");
        set.add("king");

        // set集合中的元素不能通过下标取了。没有下标
        // 遍历集合（迭代器）
        Iterator<String> it = set.iterator();
        while(it.hasNext()){
            System.out.println(it.next());
        }

        // 遍历集合（foreach）
        for(String s : set){
            System.out.println(s);
        }

        set.add("king");
        set.add("king");
        set.add("king");
        System.out.println(set.size()); //3 （后面3个king都没有加进去。）

        set.add("1");
        set.add("10");
        set.add("2");

        for(String s : set){
            System.out.println("--->" + s);
        }

        // 创建Set集合，存储Student数据
        Set<Student> students = new HashSet<>();

        Student s1 = new Student(111, "zhangsan");
        Student s2 = new Student(222, "lisi");
        Student s3 = new Student(111, "zhangsan");

        students.add(s1);
        students.add(s2);
        students.add(s3);

        System.out.println(students.size()); // 2

        // 遍历
        for(Student stu : students){
            System.out.println(stu);
        }

    }
}

class Student {
    int no;
    String name;

    public Student() {
    }

    public Student(int no, String name) {
        this.no = no;
        this.name = name;
    }

    @Override
    public String toString() {
        return "Student{" +
                "no=" + no +
                ", name='" + name + '\'' +
                '}';
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Student student = (Student) o;
        return no == student.no &&
                Objects.equals(name, student.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(no, name);
    }
}

```

### 14.26 回顾TreeSet

``` java
package com.bjpowernode.javase.review;

import java.util.Comparator;
import java.util.Iterator;
import java.util.TreeSet;

/*
    1.1、每个集合对象的创建（new）
	1.2、向集合中添加元素
	1.3、从集合中取出某个元素
	1.4、遍历集合
	1.5、测试TreeSet集合中的元素是可排序的。
	1.6、测试TreeSet集合中存储的类型是自定义的。
	1.7、测试实现Comparable接口的方式
	1.8、测试实现Comparator接口的方式（最好测试以下匿名内部类的方式）
 */
public class TreeSetTest {
    public static void main(String[] args) {
        // 集合的创建（可以测试以下TreeSet集合中存储String、Integer的。这些类都是SUN写好的。）
        //TreeSet<Integer> ts = new TreeSet<>();

        // 编写比较器可以改变规则。
        TreeSet<Integer> ts = new TreeSet<>(new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                return o2 - o1; // 自动拆箱
            }
        });

        // 添加元素
        ts.add(1);
        ts.add(100);
        ts.add(10);
        ts.add(10);
        ts.add(10);
        ts.add(10);
        ts.add(0);

        // 遍历（迭代器方式）
        Iterator<Integer> it = ts.iterator();
        while(it.hasNext()) {
            Integer i = it.next();
            System.out.println(i);
        }

        // 遍历（foreach）
        for(Integer x : ts){
            System.out.println(x);
        }

        // TreeSet集合中存储自定义类型
        TreeSet<A> atree = new TreeSet<>();

        atree.add(new A(100));
        atree.add(new A(200));
        atree.add(new A(500));
        atree.add(new A(300));
        atree.add(new A(400));
        atree.add(new A(1000));

        // 遍历
        for(A a : atree){
            System.out.println(a);
        }

        //TreeSet<B> btree = new TreeSet<>(new BComparator());
        // 匿名内部类方式。
        TreeSet<B> btree = new TreeSet<>(new Comparator<B>() {
            @Override
            public int compare(B o1, B o2) {
                return o1.i - o2.i;
            }
        });

        btree.add(new B(500));
        btree.add(new B(100));
        btree.add(new B(200));
        btree.add(new B(600));
        btree.add(new B(300));
        btree.add(new B(50));

        for(B b : btree){
            System.out.println(b);
        }
    }
}

// 第一种方式：实现Comparable接口
class A implements Comparable<A>{
    int i;

    public A(int i){
        this.i = i;
    }

    @Override
    public String toString() {
        return "A{" +
                "i=" + i +
                '}';
    }

    @Override
    public int compareTo(A o) {
        //return this.i - o.i;
        return o.i - this.i;
    }
}

class B {
    int i;
    public B(int i){
        this.i = i;
    }

    @Override
    public String toString() {
        return "B{" +
                "i=" + i +
                '}';
    }
}

// 比较器
class BComparator implements Comparator<B> {

    @Override
    public int compare(B o1, B o2) {
        return o1.i - o2.i;
    }
}
```

### 14.27 回顾HashMap

``` java
package com.bjpowernode.javase.review;

import java.util.HashMap;
import java.util.Map;
import java.util.Set;

/*
    1.1、每个集合对象的创建（new）
	1.2、向集合中添加元素
	1.3、从集合中取出某个元素
	1.4、遍历集合
 */
public class HashMapTest {
    public static void main(String[] args) {
        // 创建Map集合
        Map<Integer, String> map = new HashMap<>();
        // 添加元素
        map.put(1, "zhangsan");
        map.put(9, "lisi");
        map.put(10, "wangwu");
        map.put(2, "king");
        map.put(2, "simth"); // key重复value会覆盖。
        // 获取元素个数
        System.out.println(map.size());
        // 取key是2的元素
        System.out.println(map.get(2)); // smith
        // 遍历Map集合很重要，几种方式都要会。
        // 第一种方式：先获取所有的key，遍历key的时候，通过key获取value
        Set<Integer> keys = map.keySet();
        for(Integer key : keys){
            System.out.println(key + "=" + map.get(key));
        }

        // 第二种方式：是将Map集合转换成Set集合，Set集合中每一个元素是Node
        // 这个Node节点中有key和value
        Set<Map.Entry<Integer,String>> nodes = map.entrySet();
        for(Map.Entry<Integer,String> node : nodes){
            System.out.println(node.getKey() + "=" + node.getValue());
        }
    }
}

package com.bjpowernode.javase.review;

import java.util.Properties;

public class PropertiesTest {
    public static void main(String[] args) {
        // 创建对象
        Properties pro = new Properties();
        // 存
        pro.setProperty("username", "test");
        pro.setProperty("password", "test123");
        // 取
        String username = pro.getProperty("username");
        String password = pro.getProperty("password");
        System.out.println(username);
        System.out.println(password);

    }
}

```

## 15. IO流 -->流的分类-->流怎么学-->流的四大家族-->流的close和flash方法-->需要掌握的流

![day31-什么是IO](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/day31-%E4%BB%80%E4%B9%88%E6%98%AFIO.png)

``` java
day31课堂笔记

1、集合这块最主要掌握什么内容？
	1.1、每个集合对象的创建（new）
	1.2、向集合中添加元素
	1.3、从集合中取出某个元素
	1.4、遍历集合
	1.5、主要的集合类：
		ArrayList
		LinkedList
		HashSet (HashMap的key，存储在HashMap集合key的元素需要同时重写hashCode + equals)
		TreeSet
		HashMap
		Properties
		TreeMap

2、IO流，什么是IO？
	I : Input
	O : Output
	通过IO可以完成硬盘文件的读和写。

3、IO流的分类？

	有多种分类方式：

		一种方式是按照流的方向进行分类：
			以内存作为参照物，
				往内存中去，叫做输入(Input)。或者叫做读(Read)。
				从内存中出来，叫做输出(Output)。或者叫做写(Write)。

		另一种方式是按照读取数据方式不同进行分类：
			有的流是按照字节的方式读取数据，一次读取1个字节byte，等同于一次读取8个二进制位。
			这种流是万能的，什么类型的文件都可以读取。包括：文本文件，图片，声音文件，视频文件等....
				假设文件file1.txt，采用字节流的话是这样读的：
					a中国bc张三fe
					第一次读：一个字节，正好读到'a'
					第二次读：一个字节，正好读到'中'字符的一半。
					第三次读：一个字节，正好读到'中'字符的另外一半。

			有的流是按照字符的方式读取数据的，一次读取一个字符，这种流是为了方便读取
			普通文本文件而存在的，这种流不能读取：图片、声音、视频等文件。只能读取纯
			文本文件，连word文件都无法读取。
				假设文件file1.txt，采用字符流的话是这样读的：
					a中国bc张三fe
					第一次读：'a'字符（'a'字符在windows系统中占用1个字节。）
					第二次读：'中'字符（'中'字符在windows系统中占用2个字节。）
	
	综上所述：流的分类
		输入流、输出流
		字节流、字符流

4、Java中的IO流都已经写好了，我们程序员不需要关心,我们最主要还是掌握，
在java中已经提供了哪些流，每个流的特点是什么，每个流对象上的常用方法有
哪些？？？？
	java中所有的流都是在：java.io.*;下。

	java中主要还是研究：
		怎么new流对象。
		调用流对象的哪个方法是读，哪个方法是写。

5、java IO流这块有四大家族：
	四大家族的首领：
		java.io.InputStream  字节输入流
		java.io.OutputStream 字节输出流

		java.io.Reader		字符输入流
		java.io.Writer		字符输出流

		四大家族的首领都是抽象类。(abstract class)

		所有的流都实现了：
			java.io.Closeable接口，都是可关闭的，都有close()方法。
			流毕竟是一个管道，这个是内存和硬盘之间的通道，用完之后一定要关闭，
			不然会耗费(占用)很多资源。养成好习惯，用完流一定要关闭。

		所有的输出流都实现了：
			java.io.Flushable接口，都是可刷新的，都有flush()方法。
			养成一个好习惯，输出流在最终输出之后，一定要记得flush()
			刷新一下。这个刷新表示将通道/管道当中剩余未输出的数据
			强行输出完（清空管道！）刷新的作用就是清空管道。
			注意：如果没有flush()可能会导致丢失数据。


	注意：在java中只要“类名”以Stream结尾的都是字节流。以“Reader/Writer”结尾的都是字符流。

6、java.io包下需要掌握的流有16个：
	
	文件专属：
		java.io.FileInputStream（掌握）
		java.io.FileOutputStream（掌握）
		java.io.FileReader
		java.io.FileWriter

	转换流：（将字节流转换成字符流）
		java.io.InputStreamReader
		java.io.OutputStreamWriter

	缓冲流专属：
		java.io.BufferedReader
		java.io.BufferedWriter
		java.io.BufferedInputStream
		java.io.BufferedOutputStream

	数据流专属：
		java.io.DataInputStream
		java.io.DataOutputStream

	标准输出流：
		java.io.PrintWriter
		java.io.PrintStream（掌握）

	对象专属流：
		java.io.ObjectInputStream（掌握）
		java.io.ObjectOutputStream（掌握）

7、java.io.File类。
	File类的常用方法。

8、java io这块还剩下什么内容：
	第一：ObjectInputStream ObjectOutputStream的使用。
	第二：IO流+Properties集合的联合使用。
```

### 15.1 FileinputStream初步

``` java
package com.bjpowernode.java.io;

import java.io.BufferedReader;
import java.io.FileReader;

/*
BufferedReader:
    带有缓冲区的字符输入流。
    使用这个流的时候不需要自定义char数组，或者说不需要自定义byte数组。自带缓冲。
 */
public class BufferedReaderTest01 {
    public static void main(String[] args) throws Exception{

        FileReader reader = new FileReader("Copy02.java");
        // 当一个流的构造方法中需要一个流的时候，这个被传进来的流叫做：节点流。
        // 外部负责包装的这个流，叫做：包装流，还有一个名字叫做：处理流。
        // 像当前这个程序来说：FileReader就是一个节点流。BufferedReader就是包装流/处理流。
        BufferedReader br = new BufferedReader(reader);

        // 读一行
        /*String firstLine = br.readLine();
        System.out.println(firstLine);

        String secondLine = br.readLine();
        System.out.println(secondLine);

        String line3 = br.readLine();
        System.out.println(line3);*/

        // br.readLine()方法读取一个文本行，但不带换行符。
        String s = null;
        while((s = br.readLine()) != null){
            System.out.print(s);
        }

        // 关闭流
        // 对于包装流来说，只需要关闭最外层流就行，里面的节点流会自动关闭。（可以看源代码。）
        br.close();
    }
}

```

### 15.2 FileinputStream循环读

``` java
package com.bjpowernode.java.io;

import java.io.BufferedReader;
import java.io.FileInputStream;
import java.io.InputStream;
import java.io.InputStreamReader;

/*
    转换流：InputStreamReader
 */
public class BufferedReaderTest02 {
    public static void main(String[] args) throws Exception{

        /*// 字节流
        FileInputStream in = new FileInputStream("Copy02.java");

        // 通过转换流转换（InputStreamReader将字节流转换成字符流。）
        // in是节点流。reader是包装流。
        InputStreamReader reader = new InputStreamReader(in);

        // 这个构造方法只能传一个字符流。不能传字节流。
        // reader是节点流。br是包装流。
        BufferedReader br = new BufferedReader(reader);*/

        // 合并
        BufferedReader br = new BufferedReader(new InputStreamReader(new FileInputStream("Copy02.java")));

        String line = null;
        while((line = br.readLine()) != null){
            System.out.println(line);
        }

        // 关闭最外层
        br.close();
    }
}

```

### 15.3 IDEA中的当前路径往byte数组中读

``` java
package com.bjpowernode.java.io;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

/*
int read(byte[] b)
    一次最多读取 b.length 个字节。
    减少硬盘和内存的交互，提高程序的执行效率。
    往byte[]数组当中读。
 */
public class FileInputStreamTest03 {
    public static void main(String[] args) {
        FileInputStream fis = null;
        try {
            // 相对路径的话呢？相对路径一定是从当前所在的位置作为起点开始找！
            // IDEA默认的当前路径是哪里？工程Project的根就是IDEA的默认当前路径。
            //fis = new FileInputStream("tempfile3");
            //fis = new FileInputStream("chapter23/tempfile2");
            //fis = new FileInputStream("chapter23/src/tempfile3");
            fis = new FileInputStream("chapter23/src/com/bjpowernode/java/io/tempfile4");

            // 开始读，采用byte数组，一次读取多个字节。最多读取“数组.length”个字节。
            byte[] bytes = new byte[4]; // 准备一个4个长度的byte数组，一次最多读取4个字节。
            // 这个方法的返回值是：读取到的字节数量。（不是字节本身）
            int readCount = fis.read(bytes);
            System.out.println(readCount); // 第一次读到了4个字节。
            // 将字节数组全部转换成字符串
            //System.out.println(new String(bytes)); // abcd
            // 不应该全部都转换，应该是读取了多少个字节，转换多少个。
            System.out.println(new String(bytes,0, readCount));

            readCount = fis.read(bytes); // 第二次只能读取到2个字节。
            System.out.println(readCount); // 2
            // 将字节数组全部转换成字符串
            //System.out.println(new String(bytes)); // efcd
            // 不应该全部都转换，应该是读取了多少个字节，转换多少个。
            System.out.println(new String(bytes,0, readCount));

            readCount = fis.read(bytes); // 1个字节都没有读取到返回-1
            System.out.println(readCount); // -1

        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if (fis != null) {
                try {
                    fis.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}

```

### FileinputStream的最终程序

``` java
package com.bjpowernode.java.io;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

/*
最终版，需要掌握。
 */
public class FileInputStreamTest04 {
    public static void main(String[] args) {
        FileInputStream fis = null;
        try {
            fis = new FileInputStream("chapter23/src/tempfile3");
            // 准备一个byte数组
            byte[] bytes = new byte[4];
            /*while(true){
                int readCount = fis.read(bytes);
                if(readCount == -1){
                    break;
                }
                // 把byte数组转换成字符串，读到多少个转换多少个。
                System.out.print(new String(bytes, 0, readCount));
            }*/

            int readCount = 0;
            while((readCount = fis.read(bytes)) != -1) {
                System.out.print(new String(bytes, 0, readCount));
            }

        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if (fis != null) {
                try {
                    fis.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}

```

### 15.4 FileInputStream的其他常用方法和skip方法

``` java
package com.bjpowernode.java.io;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

/*
FileInputStream类的其它常用方法：
    int available()：返回流当中剩余的没有读到的字节数量
    long skip(long n)：跳过几个字节不读。
 */
public class FileInputStreamTest05 {
    public static void main(String[] args) {
        FileInputStream fis = null;
        try {
            fis = new FileInputStream("tempfile");
            System.out.println("总字节数量：" + fis.available());
            // 读1个字节
            //int readByte = fis.read();
            // 还剩下可以读的字节数量是：5
            //System.out.println("剩下多少个字节没有读：" + fis.available());
            // 这个方法有什么用？
            //byte[] bytes = new byte[fis.available()]; // 这种方式不太适合太大的文件，因为byte[]数组不能太大。
            // 不需要循环了。
            // 直接读一次就行了。
            //int readCount = fis.read(bytes); // 6
            //System.out.println(new String(bytes)); // abcdef

            // skip跳过几个字节不读取，这个方法也可能以后会用！
            fis.skip(3);
            System.out.println(fis.read()); //100

        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if (fis != null) {
                try {
                    fis.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}

```

### 15.5 FileOutputStream的使用

``` java
package com.bjpowernode.java.io;

import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;

/**
 * 文件字节输出流，负责写。
 * 从内存到硬盘。
 */
public class FileOutputStreamTest01 {
    public static void main(String[] args) {
        FileOutputStream fos = null;
        try {
            // myfile文件不存在的时候会自动新建！
            // 这种方式谨慎使用，这种方式会先将原文件清空，然后重新写入。
            //fos = new FileOutputStream("myfile");
            //fos = new FileOutputStream("chapter23/src/tempfile3");

            // 以追加的方式在文件末尾写入。不会清空原文件内容。
            fos = new FileOutputStream("chapter23/src/tempfile3", true);
            // 开始写。
            byte[] bytes = {97, 98, 99, 100};
            // 将byte数组全部写出！
            fos.write(bytes); // abcd
            // 将byte数组的一部分写出！
            fos.write(bytes, 0, 2); // 再写出ab

            // 字符串
            String s = "我是一个中国人，我骄傲！！！";
            // 将字符串转换成byte数组。
            byte[] bs = s.getBytes();
            // 写
            fos.write(bs);

            // 写完之后，最后一定要刷新
            fos.flush();
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if (fos != null) {
                try {
                    fos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}

```

### 15.6 文件复制

```java
package com.bjpowernode.java.io;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;

/*
使用FileInputStream + FileOutputStream完成文件的拷贝。
拷贝的过程应该是一边读，一边写。
使用以上的字节流拷贝文件的时候，文件类型随意，万能的。什么样的文件都能拷贝。
 */
public class Copy01 {
    public static void main(String[] args) {
        FileInputStream fis = null;
        FileOutputStream fos = null;
        try {
            // 创建一个输入流对象
            fis = new FileInputStream("D:\\course\\02-JavaSE\\video\\chapter01\\动力节点-JavaSE-杜聚宾-001-文件扩展名的显示.avi");
            // 创建一个输出流对象
            fos = new FileOutputStream("C:\\动力节点-JavaSE-杜聚宾-001-文件扩展名的显示.avi");

            // 最核心的：一边读，一边写
            byte[] bytes = new byte[1024 * 1024]; // 1MB（一次最多拷贝1MB。）
            int readCount = 0;
            while((readCount = fis.read(bytes)) != -1) {
                fos.write(bytes, 0, readCount);
            }

            // 刷新，输出流最后要刷新
            fos.flush();
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            // 分开try，不要一起try。
            // 一起try的时候，其中一个出现异常，可能会影响到另一个流的关闭。
            if (fos != null) {
                try {
                    fos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if (fis != null) {
                try {
                    fis.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}

```



### 15.7 FileReader的使用

``` java
package com.bjpowernode.java.io;

import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;

/*
FileReader：
    文件字符输入流，只能读取普通文本。
    读取文本内容时，比较方便，快捷。
 */
public class FileReaderTest {
    public static void main(String[] args) {
        FileReader reader = null;
        try {
            // 创建文件字符输入流
            reader = new FileReader("tempfile");

            //准备一个char数组
            char[] chars = new char[4];
            // 往char数组中读
            reader.read(chars); // 按照字符的方式读取：第一次e，第二次f，第三次 风....
            for(char c : chars) {
                System.out.println(c);
            }

            /*// 开始读
            char[] chars = new char[4]; // 一次读取4个字符
            int readCount = 0;
            while((readCount = reader.read(chars)) != -1) {
                System.out.print(new String(chars,0,readCount));
            }*/
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if (reader != null) {
                try {
                    reader.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}

```

### 15.8 FileWriter的使用

``` java
package com.bjpowernode.java.io;

import java.io.FileWriter;
import java.io.IOException;

/*
FileWriter:
    文件字符输出流。写。
    只能输出普通文本。
 */
public class FileWriterTest {
    public static void main(String[] args) {
        FileWriter out = null;
        try {
            // 创建文件字符输出流对象
            //out = new FileWriter("file");
            out = new FileWriter("file", true);

            // 开始写。
            char[] chars = {'我','是','中','国','人'};
            out.write(chars);
            out.write(chars, 2, 3);

            out.write("我是一名java软件工程师！");
            // 写出一个换行符。
            out.write("\n");
            out.write("hello world!");

            // 刷新
            out.flush();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if (out != null) {
                try {
                    out.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}

```

### 15.9 复制普通文本文件

``` java
package com.bjpowernode.java.io;

import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;

/*
使用FileReader FileWriter进行拷贝的话，只能拷贝“普通文本”文件。
 */
public class Copy02 {
    public static void main(String[] args) {
        FileReader in = null;
        FileWriter out = null;
        try {
            // 读
            in = new FileReader("chapter23/src/com/bjpowernode/java/io/Copy02.java");
            // 写
            out = new FileWriter("Copy02.java");

            // 一边读一边写：
            char[] chars = new char[1024 * 512]; // 1MB
            int readCount = 0;
            while((readCount = in.read(chars)) != -1){
                out.write(chars, 0, readCount);
            }

            // 刷新
            out.flush();
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if (in != null) {
                try {
                    in.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if (out != null) {
                try {
                    out.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }

    }
}

```

### 15.10 带有缓冲区的字符流

``` java
package com.bjpowernode.java.io;

import java.io.BufferedReader;
import java.io.FileReader;

/*
BufferedReader:
    带有缓冲区的字符输入流。
    使用这个流的时候不需要自定义char数组，或者说不需要自定义byte数组。自带缓冲。
 */
public class BufferedReaderTest01 {
    public static void main(String[] args) throws Exception{

        FileReader reader = new FileReader("Copy02.java");
        // 当一个流的构造方法中需要一个流的时候，这个被传进来的流叫做：节点流。
        // 外部负责包装的这个流，叫做：包装流，还有一个名字叫做：处理流。
        // 像当前这个程序来说：FileReader就是一个节点流。BufferedReader就是包装流/处理流。
        BufferedReader br = new BufferedReader(reader);

        // 读一行
        /*String firstLine = br.readLine();
        System.out.println(firstLine);

        String secondLine = br.readLine();
        System.out.println(secondLine);

        String line3 = br.readLine();
        System.out.println(line3);*/

        // br.readLine()方法读取一个文本行，但不带换行符。
        String s = null;
        while((s = br.readLine()) != null){
            System.out.print(s);
        }

        // 关闭流
        // 对于包装流来说，只需要关闭最外层流就行，里面的节点流会自动关闭。（可以看源代码。）
        br.close();
    }
}

```

### 15.11 字节流和包装流

``` java
package com.bjpowernode.java.io;

import java.io.BufferedReader;
import java.io.FileInputStream;
import java.io.InputStream;
import java.io.InputStreamReader;

/*
    转换流：InputStreamReader
 */
public class BufferedReaderTest02 {
    public static void main(String[] args) throws Exception{

        /*// 字节流
        FileInputStream in = new FileInputStream("Copy02.java");

        // 通过转换流转换（InputStreamReader将字节流转换成字符流。）
        // in是节点流。reader是包装流。
        InputStreamReader reader = new InputStreamReader(in);

        // 这个构造方法只能传一个字符流。不能传字节流。
        // reader是节点流。br是包装流。
        BufferedReader br = new BufferedReader(reader);*/

        // 合并
        BufferedReader br = new BufferedReader(new InputStreamReader(new FileInputStream("Copy02.java")));

        String line = null;
        while((line = br.readLine()) != null){
            System.out.println(line);
        }

        // 关闭最外层
        br.close();
    }
}

```

### 15.12 带有缓冲区的字符流

``` java
package com.bjpowernode.java.io;

import java.io.BufferedWriter;
import java.io.FileOutputStream;
import java.io.FileWriter;
import java.io.OutputStreamWriter;

/*
BufferedWriter：带有缓冲的字符输出流。
OutputStreamWriter：转换流
 */
public class BufferedWriterTest {
    public static void main(String[] args) throws Exception{
        // 带有缓冲区的字符输出流
        //BufferedWriter out = new BufferedWriter(new FileWriter("copy"));

        BufferedWriter out = new BufferedWriter(new OutputStreamWriter(new FileOutputStream("copy", true)));
        // 开始写。
        out.write("hello world!");
        out.write("\n");
        out.write("hello kitty!");
        // 刷新
        out.flush();
        // 关闭最外层
        out.close();
    }
}

```

### 15.13 数据流

``` java
package com.bjpowernode.java.io;

import java.io.DataInputStream;
import java.io.FileInputStream;

/*
DataInputStream:数据字节输入流。
DataOutputStream写的文件，只能使用DataInputStream去读。并且读的时候你需要提前知道写入的顺序。
读的顺序需要和写的顺序一致。才可以正常取出数据。

 */
public class DataInputStreamTest01 {
    public static void main(String[] args) throws Exception{
        DataInputStream dis = new DataInputStream(new FileInputStream("data"));
        // 开始读
        byte b = dis.readByte();
        short s = dis.readShort();
        int i = dis.readInt();
        long l = dis.readLong();
        float f = dis.readFloat();
        double d = dis.readDouble();
        boolean sex = dis.readBoolean();
        char c = dis.readChar();

        System.out.println(b);
        System.out.println(s);
        System.out.println(i + 1000);
        System.out.println(l);
        System.out.println(f);
        System.out.println(d);
        System.out.println(sex);
        System.out.println(c);

        dis.close();
    }
}

package com.bjpowernode.java.io;

import java.io.DataInputStream;
import java.io.FileInputStream;

/*
DataInputStream:数据字节输入流。
DataOutputStream写的文件，只能使用DataInputStream去读。并且读的时候你需要提前知道写入的顺序。
读的顺序需要和写的顺序一致。才可以正常取出数据。

 */
public class DataInputStreamTest01 {
    public static void main(String[] args) throws Exception{
        DataInputStream dis = new DataInputStream(new FileInputStream("data"));
        // 开始读
        byte b = dis.readByte();
        short s = dis.readShort();
        int i = dis.readInt();
        long l = dis.readLong();
        float f = dis.readFloat();
        double d = dis.readDouble();
        boolean sex = dis.readBoolean();
        char c = dis.readChar();

        System.out.println(b);
        System.out.println(s);
        System.out.println(i + 1000);
        System.out.println(l);
        System.out.println(f);
        System.out.println(d);
        System.out.println(sex);
        System.out.println(c);

        dis.close();
    }
}

```

### 15.14 标准输出流和File类的理解

``` java
package com.bjpowernode.java.io;

import java.io.FileOutputStream;
import java.io.PrintStream;

/*
java.io.PrintStream：标准的字节输出流。默认输出到控制台。
 */
public class PrintStreamTest {
    public static void main(String[] args) throws Exception{

        // 联合起来写
        System.out.println("hello world!");

        // 分开写
        PrintStream ps = System.out;
        ps.println("hello zhangsan");
        ps.println("hello lisi");
        ps.println("hello wangwu");

        // 标准输出流不需要手动close()关闭。
        // 可以改变标准输出流的输出方向吗？ 可以
        /*
        // 这些是之前System类使用过的方法和属性。
        System.gc();
        System.currentTimeMillis();
        PrintStream ps2 = System.out;
        System.exit(0);
        System.arraycopy(....);
         */

        // 标准输出流不再指向控制台，指向“log”文件。
        PrintStream printStream = new PrintStream(new FileOutputStream("log"));
        // 修改输出方向，将输出方向修改到"log"文件。
        System.setOut(printStream);
        // 再输出
        System.out.println("hello world");
        System.out.println("hello kitty");
        System.out.println("hello zhangsan");

    }
}

package com.bjpowernode.java.io;

import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.PrintStream;
import java.text.SimpleDateFormat;
import java.util.Date;

/*
日志工具
 */
public class Logger {
    /*
    记录日志的方法。
     */
    public static void log(String msg) {
        try {
            // 指向一个日志文件
            PrintStream out = new PrintStream(new FileOutputStream("log.txt", true));
            // 改变输出方向
            System.setOut(out);
            // 日期当前时间
            Date nowTime = new Date();
            SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss SSS");
            String strTime = sdf.format(nowTime);

            System.out.println(strTime + ": " + msg);
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        }
    }
}

package com.bjpowernode.java.io;

public class LogTest {
    public static void main(String[] args) {
        //测试工具类是否好用
        Logger.log("调用了System类的gc()方法，建议启动垃圾回收");
        Logger.log("调用了UserService的doSome()方法");
        Logger.log("用户尝试进行登录，验证失败");
        Logger.log("我非常喜欢这个记录日志的工具哦！");
    }
}

```

### 15.15 File类的常用方法

``` java
package com.bjpowernode.java.io;

import java.io.File;

/*
File
    1、File类和四大家族没有关系，所以File类不能完成文件的读和写。
    2、File对象代表什么？
        文件和目录路径名的抽象表示形式。
        C:\Drivers 这是一个File对象
        C:\Drivers\Lan\Realtek\Readme.txt 也是File对象。
        一个File对象有可能对应的是目录，也可能是文件。
        File只是一个路径名的抽象表示形式。
    3、需要掌握File类中常用的方法
 */
public class FileTest01 {
    public static void main(String[] args) throws Exception {
        // 创建一个File对象
        File f1 = new File("D:\\file");

        // 判断是否存在！
        System.out.println(f1.exists());

        // 如果D:\file不存在，则以文件的形式创建出来
        /*if(!f1.exists()) {
            // 以文件形式新建
            f1.createNewFile();
        }*/

        // 如果D:\file不存在，则以目录的形式创建出来
        /*if(!f1.exists()) {
            // 以目录的形式新建。
            f1.mkdir();
        }*/

        // 可以创建多重目录吗？
        File f2 = new File("D:/a/b/c/d/e/f");
        /*if(!f2.exists()) {
            // 多重目录的形式新建。
            f2.mkdirs();
        }*/

        File f3 = new File("D:\\course\\01-开课\\学习方法.txt");
        // 获取文件的父路径
        String parentPath = f3.getParent();
        System.out.println(parentPath); //D:\course\01-开课
        File parentFile = f3.getParentFile();
        System.out.println("获取绝对路径：" + parentFile.getAbsolutePath());

        File f4 = new File("copy");
        System.out.println("绝对路径：" + f4.getAbsolutePath()); // C:\Users\Administrator\IdeaProjects\javase\copy

    }
}

package com.bjpowernode.java.io;

import java.io.File;
import java.text.SimpleDateFormat;
import java.util.Date;

/*
File类的常用方法
 */
public class FileTest02 {
    public static void main(String[] args) {

        File f1 = new File("D:\\course\\01-开课\\开学典礼.ppt");
        // 获取文件名
        System.out.println("文件名：" + f1.getName());

        // 判断是否是一个目录
        System.out.println(f1.isDirectory()); // false

        // 判断是否是一个文件
        System.out.println(f1.isFile()); // true

        // 获取文件最后一次修改时间
        long haoMiao = f1.lastModified(); // 这个毫秒是从1970年到现在的总毫秒数。
        // 将总毫秒数转换成日期?????
        Date time = new Date(haoMiao);
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss SSS");
        String strTime = sdf.format(time);
        System.out.println(strTime);

        // 获取文件大小
        System.out.println(f1.length()); //216064字节。
    }
}

package com.bjpowernode.java.io;

import java.io.File;

/*
File中的listFiles方法。
 */
public class FileTest03 {
    public static void main(String[] args) {
        // File[] listFiles()
        // 获取当前目录下所有的子文件。
        File f = new File("D:\\course\\01-开课");
        File[] files = f.listFiles();
        // foreach
        for(File file : files){
            //System.out.println(file.getAbsolutePath());
            System.out.println(file.getName());
        }
    }
}

```

### 15.16 目录拷贝

``` java
package com.bjpowernode.java.io;

import java.io.*;

/*
拷贝目录
 */
public class CopyAll {
    public static void main(String[] args) {
        // 拷贝源
        File srcFile = new File("D:\\course\\02-JavaSE\\document");
        // 拷贝目标
        File destFile = new File("C:\\a\\b\\c");
        // 调用方法拷贝
        copyDir(srcFile, destFile);
    }

    /**
     * 拷贝目录
     * @param srcFile 拷贝源
     * @param destFile 拷贝目标
     */
    private static void copyDir(File srcFile, File destFile) {
        if(srcFile.isFile()) {
            // srcFile如果是一个文件的话，递归结束。
            // 是文件的时候需要拷贝。
            // ....一边读一边写。
            FileInputStream in = null;
            FileOutputStream out = null;
            try {
                // 读这个文件
                // D:\course\02-JavaSE\document\JavaSE进阶讲义\JavaSE进阶-01-面向对象.pdf
                in = new FileInputStream(srcFile);
                // 写到这个文件中
                // C:\course\02-JavaSE\document\JavaSE进阶讲义\JavaSE进阶-01-面向对象.pdf
                String path = (destFile.getAbsolutePath().endsWith("\\") ? destFile.getAbsolutePath() : destFile.getAbsolutePath() + "\\")  + srcFile.getAbsolutePath().substring(3);
                out = new FileOutputStream(path);
                // 一边读一边写
                byte[] bytes = new byte[1024 * 1024]; // 一次复制1MB
                int readCount = 0;
                while((readCount = in.read(bytes)) != -1){
                    out.write(bytes, 0, readCount);
                }
                out.flush();
            } catch (FileNotFoundException e) {
                e.printStackTrace();
            } catch (IOException e) {
                e.printStackTrace();
            } finally {
                if (out != null) {
                    try {
                        out.close();
                    } catch (IOException e) {
                        e.printStackTrace();
                    }
                }
                if (in != null) {
                    try {
                        in.close();
                    } catch (IOException e) {
                        e.printStackTrace();
                    }
                }
            }
            return;
        }
        // 获取源下面的子目录
        File[] files = srcFile.listFiles();
        for(File file : files){
            // 获取所有文件的（包括目录和文件）绝对路径
            //System.out.println(file.getAbsolutePath());
            if(file.isDirectory()){
                // 新建对应的目录
                //System.out.println(file.getAbsolutePath());
                //D:\course\02-JavaSE\document\JavaSE进阶讲义       源目录
                //C:\course\02-JavaSE\document\JavaSE进阶讲义       目标目录
                String srcDir = file.getAbsolutePath();
                String destDir = (destFile.getAbsolutePath().endsWith("\\") ? destFile.getAbsolutePath() : destFile.getAbsolutePath() + "\\")  + srcDir.substring(3);
                File newFile = new File(destDir);
                if(!newFile.exists()){
                    newFile.mkdirs();
                }
            }
            // 递归调用
            copyDir(file, destFile);
        }
    }
}

package com.bjpowernode.java.io;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;

/*
使用FileInputStream + FileOutputStream完成文件的拷贝。
拷贝的过程应该是一边读，一边写。
使用以上的字节流拷贝文件的时候，文件类型随意，万能的。什么样的文件都能拷贝。
 */
public class Copy01 {
    public static void main(String[] args) {
        FileInputStream fis = null;
        FileOutputStream fos = null;
        try {
            // 创建一个输入流对象
            fis = new FileInputStream("D:\\course\\02-JavaSE\\video\\chapter01\\动力节点-JavaSE-杜聚宾-001-文件扩展名的显示.avi");
            // 创建一个输出流对象
            fos = new FileOutputStream("C:\\动力节点-JavaSE-杜聚宾-001-文件扩展名的显示.avi");

            // 最核心的：一边读，一边写
            byte[] bytes = new byte[1024 * 1024]; // 1MB（一次最多拷贝1MB。）
            int readCount = 0;
            while((readCount = fis.read(bytes)) != -1) {
                fos.write(bytes, 0, readCount);
            }

            // 刷新，输出流最后要刷新
            fos.flush();
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            // 分开try，不要一起try。
            // 一起try的时候，其中一个出现异常，可能会影响到另一个流的关闭。
            if (fos != null) {
                try {
                    fos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if (fis != null) {
                try {
                    fis.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}


package com.bjpowernode.java.io;

import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;

/*
使用FileReader FileWriter进行拷贝的话，只能拷贝“普通文本”文件。
 */
public class Copy02 {
    public static void main(String[] args) {
        FileReader in = null;
        FileWriter out = null;
        try {
            // 读
            in = new FileReader("chapter23/src/com/bjpowernode/java/io/Copy02.java");
            // 写
            out = new FileWriter("Copy02.java");

            // 一边读一边写：
            char[] chars = new char[1024 * 512]; // 1MB
            int readCount = 0;
            while((readCount = in.read(chars)) != -1){
                out.write(chars, 0, readCount);
            }

            // 刷新
            out.flush();
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if (in != null) {
                try {
                    in.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if (out != null) {
                try {
                    out.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }

    }
}

```

### 15.17 序列化和反序列化

![day32-对象的序列化和反序列化](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/day32-%E5%AF%B9%E8%B1%A1%E7%9A%84%E5%BA%8F%E5%88%97%E5%8C%96%E5%92%8C%E5%8F%8D%E5%BA%8F%E5%88%97%E5%8C%96.png)

### 15.18 序列化的实现

``` java
package com.bjpowernode.java.bean;

import java.io.Serializable;

public class Student implements Serializable {

    // IDEA工具自动生成序列化版本号。
    //private static final long serialVersionUID = -7998917368642754840L;

    // Java虚拟机看到Serializable接口之后，会自动生成一个序列化版本号。
    // 这里没有手动写出来，java虚拟机会默认提供这个序列化版本号。
    // 建议将序列化版本号手动的写出来。不建议自动生成
    private static final long serialVersionUID = 1L; // java虚拟机识别一个类的时候先通过类名，如果类名一致，再通过序列化版本号。

    private int no;
    //private String name;

    // 过了很久，Student这个类源代码改动了。
    // 源代码改动之后，需要重新编译，编译之后生成了全新的字节码文件。
    // 并且class文件再次运行的时候，java虚拟机生成的序列化版本号也会发生相应的改变。
    private int age;
    private String email;
    private String address;

    public Student() {
    }

    public Student(int no, String name) {
        this.no = no;
        //this.name = name;
    }

    public int getNo() {
        return no;
    }

    public void setNo(int no) {
        this.no = no;
    }

    /*public String getName() {
        return name;
    }*/

    /*public void setName(String name) {
        this.name = name;
    }*/

    /*@Override
    public String toString() {
        return "Student{" +
                "no=" + no +
                ", name='" + name + '\'' +
                '}';
    }*/

    @Override
    public String toString() {
        return "Student{" +
                "no=" + no +
                ", age=" + age +
                ", email='" + email + '\'' +
                ", address='" + address + '\'' +
                '}';
    }
}

```

### 15.19 反序列化的实现

```java
package com.bjpowernode.java.io;

import java.io.FileInputStream;
import java.io.ObjectInputStream;

/*
反序列化
 */
public class ObjectInputStreamTest01 {
    public static void main(String[] args) throws Exception{
        ObjectInputStream ois = new ObjectInputStream(new FileInputStream("students"));
        // 开始反序列化，读
        Object obj = ois.readObject();
        // 反序列化回来是一个学生对象，所以会调用学生对象的toString方法。
        System.out.println(obj);
        ois.close();
    }
}

```

### 15.20 序列化多个对象

```java
package com.bjpowernode.java.io;

import com.bjpowernode.java.bean.User;

import java.io.FileInputStream;
import java.io.ObjectInputStream;
import java.util.List;

/*
反序列化集合
 */
public class ObjectInputStreamTest02 {
    public static void main(String[] args) throws Exception{
        ObjectInputStream ois = new ObjectInputStream(new FileInputStream("users"));
        //Object obj = ois.readObject();
        //System.out.println(obj instanceof List);
        List<User> userList = (List<User>)ois.readObject();
        for(User user : userList){
            System.out.println(user);
        }
        ois.close();
    }
}

package com.bjpowernode.java.bean;

import java.io.Serializable;

public class User implements Serializable {
    private int no;
    // transient关键字表示游离的，不参与序列化。
    private transient String name; // name不参与序列化操作！

    public User() {
    }

    public User(int no, String name) {
        this.no = no;
        this.name = name;
    }

    @Override
    public String toString() {
        return "User{" +
                "no=" + no +
                ", name='" + name + '\'' +
                '}';
    }

    public int getNo() {
        return no;
    }

    public void setNo(int no) {
        this.no = no;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}

package com.bjpowernode.java.io;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

/*
对第一个程序进行改进。循环方式。

分析这个程序的缺点：
    一次读取一个字节byte，这样内存和硬盘交互太频繁，基本上时间/资源都耗费
    在交互上面了。能不能一次读取多个字节呢？可以。
 */
public class FileInputStreamTest02 {
    public static void main(String[] args) {
        FileInputStream fis = null;
        try {
            fis = new FileInputStream("D:\\course\\JavaProjects\\02-JavaSE\\temp");

            /*while(true) {
                int readData = fis.read();
                if(readData == -1) {
                    break;
                }
                System.out.println(readData);
            }*/

            // 改造while循环
            int readData = 0;
            while((readData = fis.read()) != -1){
                System.out.println(readData);
            }

        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if (fis != null) {
                try {
                    fis.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}

```

### 15.21transient关键字

```java
package com.bjpowernode.java.bean;

import java.io.Serializable;

public class User implements Serializable {
    private int no;
    // transient关键字表示游离的，不参与序列化。
    private transient String name; // name不参与序列化操作！

    public User() {
    }

    public User(int no, String name) {
        this.no = no;
        this.name = name;
    }

    @Override
    public String toString() {
        return "User{" +
                "no=" + no +
                ", name='" + name + '\'' +
                '}';
    }

    public int getNo() {
        return no;
    }

    public void setNo(int no) {
        this.no = no;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}

```

### 15.22 关于序列化版本号

``` java
package com.bjpowernode.java.io;

import java.io.FileInputStream;
import java.io.ObjectInputStream;

/*
反序列化
 */
public class ObjectInputStreamTest01 {
    public static void main(String[] args) throws Exception{
        ObjectInputStream ois = new ObjectInputStream(new FileInputStream("students"));
        // 开始反序列化，读
        Object obj = ois.readObject();
        // 反序列化回来是一个学生对象，所以会调用学生对象的toString方法。
        System.out.println(obj);
        ois.close();
    }
}

package com.bjpowernode.java.io;

import com.bjpowernode.java.bean.Student;

import java.io.FileOutputStream;
import java.io.ObjectOutputStream;

/*
1、java.io.NotSerializableException:
    Student对象不支持序列化！！！！

2、参与序列化和反序列化的对象，必须实现Serializable接口。

3、注意：通过源代码发现，Serializable接口只是一个标志接口：
    public interface Serializable {
    }
    这个接口当中什么代码都没有。
    那么它起到一个什么作用呢？
        起到标识的作用，标志的作用，java虚拟机看到这个类实现了这个接口，可能会对这个类进行特殊待遇。
        Serializable这个标志接口是给java虚拟机参考的，java虚拟机看到这个接口之后，会为该类自动生成
        一个序列化版本号。

4、序列化版本号有什么用呢？
    java.io.InvalidClassException:
        com.bjpowernode.java.bean.Student;
        local class incompatible:
            stream classdesc serialVersionUID = -684255398724514298（十年后）,
            local class serialVersionUID = -3463447116624555755（十年前）

    java语言中是采用什么机制来区分类的？
        第一：首先通过类名进行比对，如果类名不一样，肯定不是同一个类。
        第二：如果类名一样，再怎么进行类的区别？靠序列化版本号进行区分。

    小鹏编写了一个类：com.bjpowernode.java.bean.Student implements Serializable
    胡浪编写了一个类：com.bjpowernode.java.bean.Student implements Serializable
    不同的人编写了同一个类，但“这两个类确实不是同一个类”。这个时候序列化版本就起上作用了。
    对于java虚拟机来说，java虚拟机是可以区分开这两个类的，因为这两个类都实现了Serializable接口，
    都有默认的序列化版本号，他们的序列化版本号不一样。所以区分开了。（这是自动生成序列化版本号的好处）

    请思考？
        这种自动生成序列化版本号有什么缺陷？
            这种自动生成的序列化版本号缺点是：一旦代码确定之后，不能进行后续的修改，
            因为只要修改，必然会重新编译，此时会生成全新的序列化版本号，这个时候java
            虚拟机会认为这是一个全新的类。（这样就不好了！）

    最终结论：
        凡是一个类实现了Serializable接口，建议给该类提供一个固定不变的序列化版本号。
        这样，以后这个类即使代码修改了，但是版本号不变，java虚拟机会认为是同一个类。

 */
public class ObjectOutputStreamTest01 {
    public static void main(String[] args) throws Exception{
        // 创建java对象
        Student s = new Student(1111, "zhangsan");
        // 序列化
        ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("students"));

        // 序列化对象
        oos.writeObject(s);

        // 刷新
        oos.flush();
        // 关闭
        oos.close();
    }
}

```

### 15.23 Idea生成序列化版本号

``` java
package com.bjpowernode.java.bean;

import java.io.Serializable;

public class Student implements Serializable {

    // IDEA工具自动生成序列化版本号。
    //private static final long serialVersionUID = -7998917368642754840L;

    // Java虚拟机看到Serializable接口之后，会自动生成一个序列化版本号。
    // 这里没有手动写出来，java虚拟机会默认提供这个序列化版本号。
    // 建议将序列化版本号手动的写出来。不建议自动生成
    private static final long serialVersionUID = 1L; // java虚拟机识别一个类的时候先通过类名，如果类名一致，再通过序列化版本号。

    private int no;
    //private String name;

    // 过了很久，Student这个类源代码改动了。
    // 源代码改动之后，需要重新编译，编译之后生成了全新的字节码文件。
    // 并且class文件再次运行的时候，java虚拟机生成的序列化版本号也会发生相应的改变。
    private int age;
    private String email;
    private String address;

    public Student() {
    }

    public Student(int no, String name) {
        this.no = no;
        //this.name = name;
    }

    public int getNo() {
        return no;
    }

    public void setNo(int no) {
        this.no = no;
    }

    /*public String getName() {
        return name;
    }*/

    /*public void setName(String name) {
        this.name = name;
    }*/

    /*@Override
    public String toString() {
        return "Student{" +
                "no=" + no +
                ", name='" + name + '\'' +
                '}';
    }*/

    @Override
    public String toString() {
        return "Student{" +
                "no=" + no +
                ", age=" + age +
                ", email='" + email + '\'' +
                ", address='" + address + '\'' +
                '}';
    }
}

```

### 15.24 IO和Properties联合使用

``` java
package com.bjpowernode.java.io;

import java.io.FileReader;
import java.util.Properties;

/*
IO+Properties的联合应用。
非常好的一个设计理念：
    以后经常改变的数据，可以单独写到一个文件中，使用程序动态读取。
    将来只需要修改这个文件的内容，java代码不需要改动，不需要重新
    编译，服务器也不需要重启。就可以拿到动态的信息。

    类似于以上机制的这种文件被称为配置文件。
    并且当配置文件中的内容格式是：
        key1=value
        key2=value
    的时候，我们把这种配置文件叫做属性配置文件。

    java规范中有要求：属性配置文件建议以.properties结尾，但这不是必须的。
    这种以.properties结尾的文件在java中被称为：属性配置文件。
    其中Properties是专门存放属性配置文件内容的一个类。
 */
public class IoPropertiesTest01 {
    public static void main(String[] args) throws Exception{
        /*
        Properties是一个Map集合，key和value都是String类型。
        想将userinfo文件中的数据加载到Properties对象当中。
         */
        // 新建一个输入流对象
        FileReader reader = new FileReader("chapter23/userinfo.properties");

        // 新建一个Map集合
        Properties pro = new Properties();

        // 调用Properties对象的load方法将文件中的数据加载到Map集合中。
        pro.load(reader); // 文件中的数据顺着管道加载到Map集合中，其中等号=左边做key，右边做value

        // 通过key来获取value呢？
        String username = pro.getProperty("username");
        System.out.println(username);

        String password = pro.getProperty("password");
        System.out.println(password);

        String data = pro.getProperty("data");
        System.out.println(data);

        String usernamex = pro.getProperty("usernamex");
        System.out.println(usernamex);
    }
}

```

## 16.线程

```java
4、多线程

	4.1、什么是进程？什么是线程？
		进程是一个应用程序（1个进程是一个软件）。
		线程是一个进程中的执行场景/执行单元。
		一个进程可以启动多个线程。
	
	4.2、对于java程序来说，当在DOS命令窗口中输入：
		java HelloWorld 回车之后。
		会先启动JVM，而JVM就是一个进程。
		JVM再启动一个主线程调用main方法。
		同时再启动一个垃圾回收线程负责看护，回收垃圾。
		最起码，现在的java程序中至少有两个线程并发，
		一个是垃圾回收线程，一个是执行main方法的主线程。
	
	4.3、进程和线程是什么关系？举个例子

		阿里巴巴：进程
			马云：阿里巴巴的一个线程
			童文红:阿里巴巴的一个线程
		
		京东：进程
			强东：京东的一个线程
			妹妹：京东的一个线程
		
		进程可以看做是现实生活当中的公司。
		线程可以看做是公司当中的某个员工。

		注意：
			进程A和进程B的内存独立不共享。（阿里巴巴和京东资源不会共享的！）
				魔兽游戏是一个进程
				酷狗音乐是一个进程
				这两个进程是独立的，不共享资源。

			线程A和线程B呢？
				在java语言中：
					线程A和线程B，堆内存和方法区内存共享。
					但是栈内存独立，一个线程一个栈。
			
				假设启动10个线程，会有10个栈空间，每个栈和每个栈之间，
				互不干扰，各自执行各自的，这就是多线程并发。
			
			火车站，可以看做是一个进程。
			火车站中的每一个售票窗口可以看做是一个线程。
			我在窗口1购票，你可以在窗口2购票，你不需要等我，我也不需要等你。
			所以多线程并发可以提高效率。

			java中之所以有多线程机制，目的就是为了提高程序的处理效率。

	4.4、思考一个问题：
		使用了多线程机制之后，main方法结束，是不是有可能程序也不会结束。
		main方法结束只是主线程结束了，主栈空了，其它的栈(线程)可能还在
		压栈弹栈。

	4.5、分析一个问题：对于单核的CPU来说，真的可以做到真正的多线程并发吗？

		对于多核的CPU电脑来说，真正的多线程并发是没问题的。
			4核CPU表示同一个时间点上，可以真正的有4个进程并发执行。

		什么是真正的多线程并发？
			t1线程执行t1的。
			t2线程执行t2的。
			t1不会影响t2，t2也不会影响t1。这叫做真正的多线程并发。

		单核的CPU表示只有一个大脑：
			不能够做到真正的多线程并发，但是可以做到给人一种“多线程并发”的感觉。
			对于单核的CPU来说，在某一个时间点上实际上只能处理一件事情，但是由于
			CPU的处理速度极快，多个线程之间频繁切换执行，跟人来的感觉是：多个事情
			同时在做！！！！！
				线程A：播放音乐
				线程B：运行魔兽游戏
				线程A和线程B频繁切换执行，人类会感觉音乐一直在播放，游戏一直在运行，
				给我们的感觉是同时并发的。
		
		电影院采用胶卷播放电影，一个胶卷一个胶卷播放速度达到一定程度之后，
		人类的眼睛产生了错觉，感觉是动画的。这说明人类的反应速度很慢，就像
		一根钢针扎到手上，到最终感觉到疼，这个过程是需要“很长的”时间的，在
		这个期间计算机可以进行亿万次的循环。所以计算机的执行速度很快。
	
5、java语言中，实现线程有两种方式，那两种方式呢？

	java支持多线程机制。并且java已经将多线程实现了，我们只需要继承就行了。

	第一种方式：编写一个类，直接继承java.lang.Thread，重写run方法。
		// 定义线程类
		public class MyThread extends Thread{
			public void run(){
			
			}
		}
		// 创建线程对象
		MyThread t = new MyThread();
		// 启动线程。
		t.start();
	
	第二种方式：编写一个类，实现java.lang.Runnable接口，实现run方法。
		// 定义一个可运行的类
		public class MyRunnable implements Runnable {
			public void run(){
			
			}
		}
		// 创建线程对象
		Thread t = new Thread(new MyRunnable());
		// 启动线程
		t.start();
	
	注意：第二种方式实现接口比较常用，因为一个类实现了接口，它还可以去继承
	其它的类，更灵活。

6、关于线程对象的生命周期？
	新建状态
	就绪状态
	运行状态
	阻塞状态
	死亡状态
        1、(这部分内容属于了解)关于线程的调度

	1.1、常见的线程调度模型有哪些？

		抢占式调度模型：
			那个线程的优先级比较高，抢到的CPU时间片的概率就高一些/多一些。
			java采用的就是抢占式调度模型。

		均分式调度模型：
			平均分配CPU时间片。每个线程占有的CPU时间片时间长度一样。
			平均分配，一切平等。
			有一些编程语言，线程调度模型采用的是这种方式。
	
	1.2、java中提供了哪些方法是和线程调度有关系的呢？

		实例方法：
			void setPriority(int newPriority) 设置线程的优先级
			int getPriority() 获取线程优先级
			最低优先级1
			默认优先级是5
			最高优先级10
			优先级比较高的获取CPU时间片可能会多一些。（但也不完全是，大概率是多的。）
		
		静态方法：
			static void yield()  让位方法
			暂停当前正在执行的线程对象，并执行其他线程
			yield()方法不是阻塞方法。让当前线程让位，让给其它线程使用。
			yield()方法的执行会让当前线程从“运行状态”回到“就绪状态”。
			注意：在回到就绪之后，有可能还会再次抢到。
		
		实例方法：
			void join()  
			合并线程
			class MyThread1 extends Thread {
				public void doSome(){
					MyThread2 t = new MyThread2();
					t.join(); // 当前线程进入阻塞，t线程执行，直到t线程结束。当前线程才可以继续。
				}
			}

			class MyThread2 extends Thread{
				
			}

2、关于多线程并发环境下，数据的安全问题。

	2.1、为什么这个是重点？
		以后在开发中，我们的项目都是运行在服务器当中，
		而服务器已经将线程的定义，线程对象的创建，线程
		的启动等，都已经实现完了。这些代码我们都不需要
		编写。

		最重要的是：你要知道，你编写的程序需要放到一个
		多线程的环境下运行，你更需要关注的是这些数据
		在多线程并发的环境下是否是安全的。（重点：*****）
	
	2.2、什么时候数据在多线程并发的环境下会存在安全问题呢？
		三个条件：
			条件1：多线程并发。
			条件2：有共享数据。
			条件3：共享数据有修改的行为。

		满足以上3个条件之后，就会存在线程安全问题。
	
	2.3、怎么解决线程安全问题呢？
		当多线程并发的环境下，有共享数据，并且这个数据还会被修改，此时就存在
		线程安全问题，怎么解决这个问题？
			线程排队执行。（不能并发）。
			用排队执行解决线程安全问题。
			这种机制被称为：线程同步机制。

			专业术语叫做：线程同步，实际上就是线程不能并发了，线程必须排队执行。
		
		怎么解决线程安全问题呀？
			使用“线程同步机制”。
		
		线程同步就是线程排队了，线程排队了就会牺牲一部分效率，没办法，数据安全
		第一位，只有数据安全了，我们才可以谈效率。数据不安全，没有效率的事儿。
	
	2.4、说到线程同步这块，涉及到这两个专业术语：

		异步编程模型：
			线程t1和线程t2，各自执行各自的，t1不管t2，t2不管t1，
			谁也不需要等谁，这种编程模型叫做：异步编程模型。
			其实就是：多线程并发（效率较高。）

			异步就是并发。

		同步编程模型：
			线程t1和线程t2，在线程t1执行的时候，必须等待t2线程执行
			结束，或者说在t2线程执行的时候，必须等待t1线程执行结束，
			两个线程之间发生了等待关系，这就是同步编程模型。
			效率较低。线程排队执行。

			同步就是排队。

3、Java中有三大变量？【重要的内容。】

	实例变量：在堆中。

	静态变量：在方法区。

	局部变量：在栈中。

	以上三大变量中：
		局部变量永远都不会存在线程安全问题。
		因为局部变量不共享。（一个线程一个栈。）
		局部变量在栈中。所以局部变量永远都不会共享。
	
	实例变量在堆中，堆只有1个。
	静态变量在方法区中，方法区只有1个。
	堆和方法区都是多线程共享的，所以可能存在线程安全问题。

	局部变量+常量：不会有线程安全问题。
	成员变量：可能会有线程安全问题。

4、如果使用局部变量的话：
	建议使用：StringBuilder。
	因为局部变量不存在线程安全问题。选择StringBuilder。
	StringBuffer效率比较低。

	ArrayList是非线程安全的。
	Vector是线程安全的。
	HashMap HashSet是非线程安全的。
	Hashtable是线程安全的。

5、总结：
	synchronized有三种写法：

		第一种：同步代码块
			灵活
			synchronized(线程共享对象){
				同步代码块;
			}

		第二种：在实例方法上使用synchronized
			表示共享对象一定是this
			并且同步代码块是整个方法体。
		
		第三种：在静态方法上使用synchronized
			表示找类锁。
			类锁永远只有1把。
			就算创建了100个对象，那类锁也只有一把。
		
		对象锁：1个对象1把锁，100个对象100把锁。
		类锁：100个对象，也可能只是1把类锁。

6、聊一聊，我们以后开发中应该怎么解决线程安全问题？

	是一上来就选择线程同步吗？synchronized
		不是，synchronized会让程序的执行效率降低，用户体验不好。
		系统的用户吞吐量降低。用户体验差。在不得已的情况下再选择
		线程同步机制。
	
	第一种方案：尽量使用局部变量代替“实例变量和静态变量”。

	第二种方案：如果必须是实例变量，那么可以考虑创建多个对象，这样
	实例变量的内存就不共享了。（一个线程对应1个对象，100个线程对应100个对象，
	对象不共享，就没有数据安全问题了。）

	第三种方案：如果不能使用局部变量，对象也不能创建多个，这个时候
	就只能选择synchronized了。线程同步机制。

7、线程这块还有那些内容呢？列举一下
	7.1、守护线程
	7.2、定时器
	7.3、实现线程的第三种方式：FutureTask方式，实现Callable接口。（JDK8新特性。）
	7.4、关于Object类中的wait和notify方法。（生产者和消费者模式！）
1、线程这块还有那些内容呢？列举一下

	1.1、守护线程

		java语言中线程分为两大类：
			一类是：用户线程
			一类是：守护线程（后台线程）
			其中具有代表性的就是：垃圾回收线程（守护线程）。

		守护线程的特点：
			一般守护线程是一个死循环，所有的用户线程只要结束，
			守护线程自动结束。
		
		注意：主线程main方法是一个用户线程。

		守护线程用在什么地方呢？
			每天00:00的时候系统数据自动备份。
			这个需要使用到定时器，并且我们可以将定时器设置为守护线程。
			一直在那里看着，没到00:00的时候就备份一次。所有的用户线程
			如果结束了，守护线程自动退出，没有必要进行数据备份了。

	1.2、定时器
		定时器的作用：
			间隔特定的时间，执行特定的程序。

			每周要进行银行账户的总账操作。
			每天要进行数据的备份操作。

			在实际的开发中，每隔多久执行一段特定的程序，这种需求是很常见的，
			那么在java中其实可以采用多种方式实现：
				
				可以使用sleep方法，睡眠，设置睡眠时间，没到这个时间点醒来，执行
				任务。这种方式是最原始的定时器。（比较low）

				在java的类库中已经写好了一个定时器：java.util.Timer，可以直接拿来用。
				不过，这种方式在目前的开发中也很少用，因为现在有很多高级框架都是支持
				定时任务的。

				在实际的开发中，目前使用较多的是Spring框架中提供的SpringTask框架，
				这个框架只要进行简单的配置，就可以完成定时器的任务。


	1.3、实现线程的第三种方式：实现Callable接口。（JDK8新特性。）
		这种方式实现的线程可以获取线程的返回值。
		之前讲解的那两种方式是无法获取线程返回值的，因为run方法返回void。

		思考：
			系统委派一个线程去执行一个任务，该线程执行完任务之后，可能
			会有一个执行结果，我们怎么能拿到这个执行结果呢？
				使用第三种方式：实现Callable接口方式。


	1.4、关于Object类中的wait和notify方法。（生产者和消费者模式！）

		第一：wait和notify方法不是线程对象的方法，是java中任何一个java对象
		都有的方法，因为这两个方式是Object类中自带的。
			wait方法和notify方法不是通过线程对象调用，
			不是这样的：t.wait()，也不是这样的：t.notify()..不对。
		
		第二：wait()方法作用？
			Object o = new Object();
			o.wait();

			表示：
				让正在o对象上活动的线程进入等待状态，无期限等待，
				直到被唤醒为止。
				o.wait();方法的调用，会让“当前线程（正在o对象上
				活动的线程）”进入等待状态。

		第三：notify()方法作用？
			Object o = new Object();
			o.notify();

			表示：
				唤醒正在o对象上等待的线程。
			
			还有一个notifyAll()方法：
				这个方法是唤醒o对象上处于等待的所有线程。


2、反射机制（比较简单，因为只要会查帮助文档，就可以了。）
	
	2.1、反射机制有什么用？
		通过java语言中的反射机制可以操作字节码文件。
		优点类似于黑客。（可以读和修改字节码文件。）
		通过反射机制可以操作代码片段。（class文件。）
	
	2.2、反射机制的相关类在哪个包下？
		java.lang.reflect.*;
	
	2.3、反射机制相关的重要的类有哪些？

		java.lang.Class：代表整个字节码，代表一个类型，代表整个类。

		java.lang.reflect.Method：代表字节码中的方法字节码。代表类中的方法。

		java.lang.reflect.Constructor：代表字节码中的构造方法字节码。代表类中的构造方法

		java.lang.reflect.Field：代表字节码中的属性字节码。代表类中的成员变量（静态变量+实例变量）。

		java.lang.Class：
			public class User{
				// Field
				int no;

				// Constructor
				public User(){
				
				}
				public User(int no){
					this.no = no;
				}

				// Method
				public void setNo(int no){
					this.no = no;
				}
				public int getNo(){
					return no;
				}
			}

3、关于JDK中自带的类加载器：（聊一聊，不需要掌握，知道当然最好！）
	3.1、什么是类加载器？
		专门负责加载类的命令/工具。
		ClassLoader
	
	3.2、JDK中自带了3个类加载器
		启动类加载器:rt.jar
		扩展类加载器:ext/*.jar
		应用类加载器:classpath
	
	3.3、假设有这样一段代码：
		String s = "abc";
		
		代码在开始执行之前，会将所需要类全部加载到JVM当中。
		通过类加载器加载，看到以上代码类加载器会找String.class
		文件，找到就加载，那么是怎么进行加载的呢？

			首先通过“启动类加载器”加载。
				注意：启动类加载器专门加载：C:\Program Files\Java\jdk1.8.0_101\jre\lib\rt.jar
				rt.jar中都是JDK最核心的类库。
			
			如果通过“启动类加载器”加载不到的时候，
			会通过"扩展类加载器"加载。
				注意：扩展类加载器专门加载：C:\Program Files\Java\jdk1.8.0_101\jre\lib\ext\*.jar

	
			如果“扩展类加载器”没有加载到，那么
			会通过“应用类加载器”加载。
				注意：应用类加载器专门加载：classpath中的类。
	
	3.4、java中为了保证类加载的安全，使用了双亲委派机制。
		优先从启动类加载器中加载，这个称为“父”
		“父”无法加载到，再从扩展类加载器中加载，
		这个称为“母”。双亲委派。如果都加载不到，
		才会考虑从应用类加载器中加载。直到加载
		到为止。
		
		day35课堂笔记

1、回顾反射机制

	1.1、什么是反射机制？反射机制有什么用？
		反射机制：可以操作字节码文件
		作用：可以让程序更加灵活。

	1.2、反射机制相关的类在哪个包下？
		java.lang.reflect.*;

	1.3、反射机制相关的主要的类？
		java.lang.Class
		java.lang.reflect.Method;
		java.lang.reflect.Constructor;
		java.lang.reflect.Field;

	1.4、在java中获取Class的三种方式？
		第一种：	 
			Class c = Class.forName("完整类名");
		第二种：
			Class c = 对象.getClass();
		第三种：
			Class c = int.class;
			Class c = String.class;

	1.5、获取了Class之后，可以调用无参数构造方法来实例化对象

		//c代表的就是日期Date类型
		Class c = Class.forName("java.util.Date");

		//实例化一个Date日期类型的对象
		Object obj = c.newInstance();

		一定要注意：
			newInstance()底层调用的是该类型的无参数构造方法。
			如果没有这个无参数构造方法会出现"实例化"异常。
	
	1.6、如果你只想让一个类的“静态代码块”执行的话，你可以怎么做？
		Class.forName("该类的类名");
		这样类就加载，类加载的时候，静态代码块执行！！！！
		在这里，对该方法的返回值不感兴趣，主要是为了使用“类加载”这个动作。
	
	1.7、关于路径问题？

		String path = Thread.currentThread().getContextClassLoader()
						  .getResource("写相对路径，但是这个相对路径从src出发开始找").getPath();	

		String path = Thread.currentThread().getContextClassLoader()
						  .getResource("abc").getPath();	//必须保证src下有abc文件。

		String path = Thread.currentThread().getContextClassLoader()
						  .getResource("a/db").getPath();	//必须保证src下有a目录，a目录下有db文件。
		
		String path = Thread.currentThread().getContextClassLoader()
						  .getResource("com/bjpowernode/test.properties").getPath();	
						  //必须保证src下有com目录，com目录下有bjpowernode目录。
						  //bjpowernode目录下有test.properties文件。

		这种方式是为了获取一个文件的绝对路径。（通用方式，不会受到环境移植的影响。）
		但是该文件要求放在类路径下，换句话说：也就是放到src下面。
		src下是类的根路径。

		直接以流的形式返回：
		InputStream in = Thread.currentThread().getContextClassLoader()
								.getResourceAsStream("com/bjpowernode/test.properties");

	1.8、IO + Properties，怎么快速绑定属性资源文件？

		//要求：第一这个文件必须在类路径下
		//第二这个文件必须是以.properties结尾。
		ResourceBundle bundle = ResourceBundle.getBundle("com/bjpowernode/test");
		String value = bundle.getString(key);
	

2、今日反射机制的重点内容
	2.1、通过反射机制访问对象的某个属性。
	2.2、通过反射机制调用对象的某个方法。
	2.3、通过反射机制调用某个构造方法实例化对象。
	2.4、通过反射机制获取父类以及父类型接口。

3、注解

	3.1、注解，或者叫做注释类型，英文单词是：Annotation
		疑问：注解到底是干啥的？？？？？？？？？

	3.2、注解Annotation是一种引用数据类型。编译之后也是生成xxx.class文件。

	3.3、怎么自定义注解呢？语法格式？

		 [修饰符列表] @interface 注解类型名{

		 }
	
	3.4、注解怎么使用，用在什么地方？

		第一：注解使用时的语法格式是：
			@注解类型名
		
		第二：注解可以出现在类上、属性上、方法上、变量上等....
		注解还可以出现在注解类型上。
	
	3.5、JDK内置了哪些注解呢？

		java.lang包下的注释类型：

			掌握：
			Deprecated 用 @Deprecated 注释的程序元素，
			不鼓励程序员使用这样的元素，通常是因为它很危险或存在更好的选择。 

			掌握：
			Override 表示一个方法声明打算重写超类中的另一个方法声明。 

			不用掌握：
			SuppressWarnings 指示应该在注释元素（以及包含在该注释元素中的
			所有程序元素）中取消显示指定的编译器警告。 
	
	3.6、元注解
		什么是元注解？
			用来标注“注解类型”的“注解”，称为元注解。

		常见的元注解有哪些？
			Target
			Retention
		
		关于Target注解：
			这是一个元注解，用来标注“注解类型”的“注解”
			这个Target注解用来标注“被标注的注解”可以出现在哪些位置上。

			@Target(ElementType.METHOD)：表示“被标注的注解”只能出现在方法上。
			@Target(value={CONSTRUCTOR, FIELD, LOCAL_VARIABLE, METHOD, PACKAGE, MODULE, PARAMETER, TYPE})
				表示该注解可以出现在：
					构造方法上
					字段上
					局部变量上
					方法上
					....
					类上...
		
		关于Retention注解：
			这是一个元注解，用来标注“注解类型”的“注解”
			这个Retention注解用来标注“被标注的注解”最终保存在哪里。

			@Retention(RetentionPolicy.SOURCE)：表示该注解只被保留在java源文件中。
			@Retention(RetentionPolicy.CLASS)：表示该注解被保存在class文件中。
			@Retention(RetentionPolicy.RUNTIME)：表示该注解被保存在class文件中，并且可以被反射机制所读取。
		
	3.7、Retention的源代码

			//元注解	
			public @interface Retention {
				//属性
				RetentionPolicy value();
			}
			
		RetentionPolicy的源代码：
			public enum RetentionPolicy {
				 SOURCE,
				 CLASS,
				 RUNTIME
			}

			//@Retention(value=RetentionPolicy.RUNTIME)
			@Retention(RetentionPolicy.RUNTIME)
			public @interface MyAnnotation{}



	3.8、Target的源代码
		

	3.9、注解在开发中有什么用呢？

		需求：
			假设有这样一个注解，叫做：@Id
			这个注解只能出现在类上面，当这个类上有这个注解的时候，
			要求这个类中必须有一个int类型的id属性。如果没有这个属性
			就报异常。如果有这个属性则正常执行！


4、JDK新特性
	后续。。。。。。。

```

### 16.1 进程和线程的关系

``` java
进程和线程是什么关系？举个例子

		阿里巴巴：进程
			马云：阿里巴巴的一个线程
			童文红:阿里巴巴的一个线程
		
		京东：进程
			强东：京东的一个线程
			妹妹：京东的一个线程
		
		进程可以看做是现实生活当中的公司。
		线程可以看做是公司当中的某个员工。

		注意：
			进程A和进程B的内存独立不共享。（阿里巴巴和京东资源不会共享的！）
				魔兽游戏是一个进程
				酷狗音乐是一个进程
				这两个进程是独立的，不共享资源。

			线程A和线程B呢？
				在java语言中：
					线程A和线程B，堆内存和方法区内存共享。
					但是栈内存独立，一个线程一个栈。
			
				假设启动10个线程，会有10个栈空间，每个栈和每个栈之间，
				互不干扰，各自执行各自的，这就是多线程并发。
			
			火车站，可以看做是一个进程。
			火车站中的每一个售票窗口可以看做是一个线程。
			我在窗口1购票，你可以在窗口2购票，你不需要等我，我也不需要等你。
			所以多线程并发可以提高效率。

			java中之所以有多线程机制，目的就是为了提高程序的处理效率。
思考一个问题：
		使用了多线程机制之后，main方法结束，是不是有可能程序也不会结束。
		main方法结束只是主线程结束了，主栈空了，其它的栈(线程)可能还在
		压栈弹栈。
```

### 16.2 堆适和方法区共享栈独立

![day32-一个线程一个栈](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/day32-%E4%B8%80%E4%B8%AA%E7%BA%BF%E7%A8%8B%E4%B8%80%E4%B8%AA%E6%A0%88.png)

### 16.3 多线程并发的理解

```java
分析一个问题：对于单核的CPU来说，真的可以做到真正的多线程并发吗？

		对于多核的CPU电脑来说，真正的多线程并发是没问题的。
			4核CPU表示同一个时间点上，可以真正的有4个进程并发执行。

		什么是真正的多线程并发？
			t1线程执行t1的。
			t2线程执行t2的。
			t1不会影响t2，t2也不会影响t1。这叫做真正的多线程并发。

		单核的CPU表示只有一个大脑：
			不能够做到真正的多线程并发，但是可以做到给人一种“多线程并发”的感觉。
			对于单核的CPU来说，在某一个时间点上实际上只能处理一件事情，但是由于
			CPU的处理速度极快，多个线程之间频繁切换执行，跟人来的感觉是：多个事情
			同时在做！！！！！
				线程A：播放音乐
				线程B：运行魔兽游戏
				线程A和线程B频繁切换执行，人类会感觉音乐一直在播放，游戏一直在运行，
				给我们的感觉是同时并发的。
		
		电影院采用胶卷播放电影，一个胶卷一个胶卷播放速度达到一定程度之后，
		人类的眼睛产生了错觉，感觉是动画的。这说明人类的反应速度很慢，就像
		一根钢针扎到手上，到最终感觉到疼，这个过程是需要“很长的”时间的，在
		这个期间计算机可以进行亿万次的循环。所以计算机的执行速度很快。
```

### 16.4 分析程序存在几个线程

```java
package com.bjpowernode.java.thread;

/*
大家分析以下程序，有几个线程，除垃圾回收线程之外。有几个线程？
    1个线程。（因为程序只有1个栈。）

main begin
m1 begin
m2 begin
m3 execute!
m2 over
m1 over
main over
    一个栈中，自上而下的顺序依次逐行执行！

 */
public class ThreadTest01 {
    public static void main(String[] args) {
        System.out.println("main begin");
        m1();
        System.out.println("main over");
    }

    private static void m1() {
        System.out.println("m1 begin");
        m2();
        System.out.println("m1 over");
    }

    private static void m2() {
        System.out.println("m2 begin");
        m3();
        System.out.println("m2 over");
    }

    private static void m3() {
        System.out.println("m3 execute!");
    }
}

```

### 16.5 实现线程的第一种方式

```java
package com.bjpowernode.java.thread;
/*
实现线程的第一种方式：
    编写一个类，直接继承java.lang.Thread，重写run方法。

    怎么创建线程对象？ new就行了。
    怎么启动线程呢？ 调用线程对象的start()方法。

注意：
    亘古不变的道理：
        方法体当中的代码永远都是自上而下的顺序依次逐行执行的。

以下程序的输出结果有这样的特点：
    有先有后。
    有多有少。
    这是咋回事？这里画一个问号？？？？？？？？？？？？？？？？？？？？？？？
 */
public class ThreadTest02 {
    public static void main(String[] args) {
        // 这里是main方法，这里的代码属于主线程，在主栈中运行。
        // 新建一个分支线程对象
        MyThread t = new MyThread();
        // 启动线程
        //t.run(); // 不会启动线程，不会分配新的分支栈。（这种方式就是单线程。）
        // start()方法的作用是：启动一个分支线程，在JVM中开辟一个新的栈空间，这段代码任务完成之后，瞬间就结束了。
        // 这段代码的任务只是为了开启一个新的栈空间，只要新的栈空间开出来，start()方法就结束了。线程就启动成功了。
        // 启动成功的线程会自动调用run方法，并且run方法在分支栈的栈底部（压栈）。
        // run方法在分支栈的栈底部，main方法在主栈的栈底部。run和main是平级的。
        t.start();
        // 这里的代码还是运行在主线程中。
        for(int i = 0; i < 1000; i++){
            System.out.println("主线程--->" + i);
        }
    }
}

class MyThread extends Thread {
    @Override
    public void run() {
        // 编写程序，这段程序运行在分支线程中（分支栈）。
        for(int i = 0; i < 1000; i++){
            System.out.println("分支线程--->" + i);
        }
    }
}

```

### 16.6 run和start的区别



![day32-线程的run](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/day32-%E7%BA%BF%E7%A8%8B%E7%9A%84run.png)

![day32-线程的start](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/day32-%E7%BA%BF%E7%A8%8B%E7%9A%84start.png)

```java
package com.bjpowernode.java.thread;
/*
实现线程的第一种方式：
    编写一个类，直接继承java.lang.Thread，重写run方法。

    怎么创建线程对象？ new就行了。
    怎么启动线程呢？ 调用线程对象的start()方法。

注意：
    亘古不变的道理：
        方法体当中的代码永远都是自上而下的顺序依次逐行执行的。

以下程序的输出结果有这样的特点：
    有先有后。
    有多有少。
    这是咋回事？这里画一个问号？？？？？？？？？？？？？？？？？？？？？？？
 */
public class ThreadTest02 {
    public static void main(String[] args) {
        // 这里是main方法，这里的代码属于主线程，在主栈中运行。
        // 新建一个分支线程对象
        MyThread t = new MyThread();
        // 启动线程
        //t.run(); // 不会启动线程，不会分配新的分支栈。（这种方式就是单线程。）
        // start()方法的作用是：启动一个分支线程，在JVM中开辟一个新的栈空间，这段代码任务完成之后，瞬间就结束了。
        // 这段代码的任务只是为了开启一个新的栈空间，只要新的栈空间开出来，start()方法就结束了。线程就启动成功了。
        // 启动成功的线程会自动调用run方法，并且run方法在分支栈的栈底部（压栈）。
        // run方法在分支栈的栈底部，main方法在主栈的栈底部。run和main是平级的。
        t.start();
        // 这里的代码还是运行在主线程中。
        for(int i = 0; i < 1000; i++){
            System.out.println("主线程--->" + i);
        }
    }
}

class MyThread extends Thread {
    @Override
    public void run() {
        // 编写程序，这段程序运行在分支线程中（分支栈）。
        for(int i = 0; i < 1000; i++){
            System.out.println("分支线程--->" + i);
        }
    }
}

```

### 16.7 实现线程的第二种方式

```java
package com.bjpowernode.java.thread;
/*
实现线程的第二种方式，编写一个类实现java.lang.Runnable接口。
 */
public class ThreadTest03 {
    public static void main(String[] args) {
        // 创建一个可运行的对象
        //MyRunnable r = new MyRunnable();
        // 将可运行的对象封装成一个线程对象
        //Thread t = new Thread(r);
        Thread t = new Thread(new MyRunnable()); // 合并代码
        // 启动线程
        t.start();

        for(int i = 0; i < 100; i++){
            System.out.println("主线程--->" + i);
        }
    }
}

// 这并不是一个线程类，是一个可运行的类。它还不是一个线程。
class MyRunnable implements Runnable {

    @Override
    public void run() {
        for(int i = 0; i < 100; i++){
            System.out.println("分支线程--->" + i);
        }
    }
}

```

### 16.8 采用匿名内部类的方式

```java
/**
采用匿名内部类可以吗？
 */
public class ThreadTest04 {
    public static void main(String[] args) {
        // 创建线程对象，采用匿名内部类方式。
        // 这是通过一个没有名字的类，new出来的对象。
        Thread t = new Thread(new Runnable(){
            @Override
            public void run() {
                for(int i = 0; i < 100; i++){
                    System.out.println("t线程---> " + i);
                }
            }
        });

        // 启动线程
        t.start();

        for(int i = 0; i < 100; i++){
            System.out.println("main线程---> " + i);
        }
    }
}

```

### 16.9 线程的生命周期

![image-20210527154645222](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/image-20210527154645222.png)

### 16.10 获取线程的名字

```java
/*
1、怎么获取当前线程对象？
    Thread t = Thread.currentThread();
    返回值t就是当前线程。

2、获取线程对象的名字
    String name = 线程对象.getName();

3、修改线程对象的名字
    线程对象.setName("线程名字");

4、当线程没有设置名字的时候，默认的名字有什么规律？（了解一下）
    Thread-0
    Thread-1
    Thread-2
    Thread-3
    .....
 */
public class ThreadTest05 {
    public void doSome(){
        // 这样就不行了
        //this.getName();
        //super.getName();
        // 但是这样可以
        String name = Thread.currentThread().getName();
        System.out.println("------->" + name);
    }

    public static void main(String[] args) {
        ThreadTest05 tt = new ThreadTest05();
        tt.doSome();

        //currentThread就是当前线程对象
        // 这个代码出现在main方法当中，所以当前线程就是主线程。
        Thread currentThread = Thread.currentThread();
        System.out.println(currentThread.getName()); //main

        // 创建线程对象
        MyThread2 t = new MyThread2();
        // 设置线程的名字
        t.setName("t1");
        // 获取线程的名字
        String tName = t.getName();
        System.out.println(tName); //Thread-0

        MyThread2 t2 = new MyThread2();
        t2.setName("t2");
        System.out.println(t2.getName()); //Thread-1\
        t2.start();

        // 启动线程
        t.start();
    }
}

class MyThread2 extends Thread {
    public void run(){
        for(int i = 0; i < 100; i++){
            // currentThread就是当前线程对象。当前线程是谁呢？
            // 当t1线程执行run方法，那么这个当前线程就是t1
            // 当t2线程执行run方法，那么这个当前线程就是t2
            Thread currentThread = Thread.currentThread();
            System.out.println(currentThread.getName() + "-->" + i);

            //System.out.println(super.getName() + "-->" + i);
            //System.out.println(this.getName() + "-->" + i);
        }
    }
}

```

### 16.11 获取当前线程对象

```java
package com.bjpowernode.java.thread;
/*
1、怎么获取当前线程对象？
    Thread t = Thread.currentThread();
    返回值t就是当前线程。

2、获取线程对象的名字
    String name = 线程对象.getName();

3、修改线程对象的名字
    线程对象.setName("线程名字");

4、当线程没有设置名字的时候，默认的名字有什么规律？（了解一下）
    Thread-0
    Thread-1
    Thread-2
    Thread-3
    .....
 */
public class ThreadTest05 {
    public void doSome(){
        // 这样就不行了
        //this.getName();
        //super.getName();
        // 但是这样可以
        String name = Thread.currentThread().getName();
        System.out.println("------->" + name);
    }

    public static void main(String[] args) {
        ThreadTest05 tt = new ThreadTest05();
        tt.doSome();

        //currentThread就是当前线程对象
        // 这个代码出现在main方法当中，所以当前线程就是主线程。
        Thread currentThread = Thread.currentThread();
        System.out.println(currentThread.getName()); //main

        // 创建线程对象
        MyThread2 t = new MyThread2();
        // 设置线程的名字
        t.setName("t1");
        // 获取线程的名字
        String tName = t.getName();
        System.out.println(tName); //Thread-0

        MyThread2 t2 = new MyThread2();
        t2.setName("t2");
        System.out.println(t2.getName()); //Thread-1\
        t2.start();

        // 启动线程
        t.start();
    }
}

class MyThread2 extends Thread {
    public void run(){
        for(int i = 0; i < 100; i++){
            // currentThread就是当前线程对象。当前线程是谁呢？
            // 当t1线程执行run方法，那么这个当前线程就是t1
            // 当t2线程执行run方法，那么这个当前线程就是t2
            Thread currentThread = Thread.currentThread();
            System.out.println(currentThread.getName() + "-->" + i);

            //System.out.println(super.getName() + "-->" + i);
            //System.out.println(this.getName() + "-->" + i);
        }
    }
}

```

### 16.12 线程的sleep方法

```java
package com.bjpowernode.java.thread;
/*
关于线程的sleep方法：
    static void sleep(long millis)
    1、静态方法：Thread.sleep(1000);
    2、参数是毫秒
    3、作用：让当前线程进入休眠，进入“阻塞状态”，放弃占有CPU时间片，让给其它线程使用。
        这行代码出现在A线程中，A线程就会进入休眠。
        这行代码出现在B线程中，B线程就会进入休眠。
    4、Thread.sleep()方法，可以做到这种效果：
        间隔特定的时间，去执行一段特定的代码，每隔多久执行一次。
 */
public class ThreadTest06 {
    public static void main(String[] args) {

        // 让当前线程进入休眠，睡眠5秒
        // 当前线程是主线程！！！
        /*try {
            Thread.sleep(1000 * 5);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }*/

        // 5秒之后执行这里的代码
        //System.out.println("hello world!");

        for(int i = 0; i < 10; i++){
            System.out.println(Thread.currentThread().getName() + "--->" + i);

            // 睡眠1秒
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}

```

### 16.13 sleep方法的面试题

```java
package com.bjpowernode.java.thread;
/*
关于Thread.sleep()方法的一个面试题：
 */
public class ThreadTest07 {
    public static void main(String[] args) {
        // 创建线程对象
        Thread t = new MyThread3();
        t.setName("t");
        t.start();

        // 调用sleep方法
        try {
            // 问题：这行代码会让线程t进入休眠状态吗？
            t.sleep(1000 * 5); // 在执行的时候还是会转换成：Thread.sleep(1000 * 5);
                                     // 这行代码的作用是：让当前线程进入休眠，也就是说main线程进入休眠。
                                     // 这样代码出现在main方法中，main线程睡眠。
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        // 5秒之后这里才会执行。
        System.out.println("hello World!");
    }
}

class MyThread3 extends Thread {
    public void run(){
        for(int i = 0; i < 10000; i++){
            System.out.println(Thread.currentThread().getName() + "--->" + i);
        }
    }
}

```

#### 16.14 终止线程的睡眠

```java
package com.bjpowernode.java.thread;
/*
sleep睡眠太久了，如果希望半道上醒来，你应该怎么办？也就是说怎么叫醒一个正在睡眠的线程？？
    注意：这个不是终断线程的执行，是终止线程的睡眠。
 */
public class ThreadTest08 {
    public static void main(String[] args) {
        Thread t = new Thread(new MyRunnable2());
        t.setName("t");
        t.start();

        // 希望5秒之后，t线程醒来（5秒之后主线程手里的活儿干完了。）
        try {
            Thread.sleep(1000 * 5);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        // 终断t线程的睡眠（这种终断睡眠的方式依靠了java的异常处理机制。）
        t.interrupt(); // 干扰，一盆冷水过去！
    }
}

class MyRunnable2 implements Runnable {

    // 重点：run()当中的异常不能throws，只能try catch
    // 因为run()方法在父类中没有抛出任何异常，子类不能比父类抛出更多的异常。
    @Override
    public void run() {
        System.out.println(Thread.currentThread().getName() + "---> begin");
        try {
            // 睡眠1年
            Thread.sleep(1000 * 60 * 60 * 24 * 365);
        } catch (InterruptedException e) {
            // 打印异常信息
            //e.printStackTrace();
        }
        //1年之后才会执行这里
        System.out.println(Thread.currentThread().getName() + "---> end");

        // 调用doOther
        //doOther();
    }

    // 其它方法可以throws
    /*public void doOther() throws Exception{

    }*/
}

```

### 16.15 强制终止线程的执行

``` java
package com.bjpowernode.java.thread;
/*
在java中怎么强行终止一个线程的执行。
    这种方式存在很大的缺点：容易丢失数据。因为这种方式是直接将线程杀死了，
    线程没有保存的数据将会丢失。不建议使用。
 */
public class ThreadTest09 {
    public static void main(String[] args) {
        Thread t = new Thread(new MyRunnable3());
        t.setName("t");
        t.start();

        // 模拟5秒
        try {
            Thread.sleep(1000 * 5);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        // 5秒之后强行终止t线程
        t.stop(); // 已过时（不建议使用。）
    }
}

class MyRunnable3 implements Runnable {

    @Override
    public void run() {
        for(int i = 0; i < 10; i++){
            System.out.println(Thread.currentThread().getName() + "--->" + i);
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}

```

### 16.16 合理的终止一个线程的执行

``` java
package com.bjpowernode.java.thread;
/*
怎么合理的终止一个线程的执行。这种方式是很常用的。
 */
public class ThreadTest10 {
    public static void main(String[] args) {
        MyRunable4 r = new MyRunable4();
        Thread t = new Thread(r);
        t.setName("t");
        t.start();

        // 模拟5秒
        try {
            Thread.sleep(5000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        // 终止线程
        // 你想要什么时候终止t的执行，那么你把标记修改为false，就结束了。
        r.run = false;
    }
}

class MyRunable4 implements Runnable {

    // 打一个布尔标记
    boolean run = true;

    @Override
    public void run() {
        for (int i = 0; i < 10; i++){
            if(run){
                System.out.println(Thread.currentThread().getName() + "--->" + i);
                try {
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }else{
                // return就结束了，你在结束之前还有什么没保存的。
                // 在这里可以保存呀。
                //save....

                //终止当前线程
                return;
            }
        }
    }
}

```

### 16.17 线程的调度概述

```java
1、(这部分内容属于了解)关于线程的调度

	1.1、常见的线程调度模型有哪些？

		抢占式调度模型：
			那个线程的优先级比较高，抢到的CPU时间片的概率就高一些/多一些。
			java采用的就是抢占式调度模型。

		均分式调度模型：
			平均分配CPU时间片。每个线程占有的CPU时间片时间长度一样。
			平均分配，一切平等。
			有一些编程语言，线程调度模型采用的是这种方式。
```

### 16.18 线程调度的方法

![image-20210527200702565](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/image-20210527200702565.png)

```java
1.2、java中提供了哪些方法是和线程调度有关系的呢？

		实例方法：
			void setPriority(int newPriority) 设置线程的优先级
			int getPriority() 获取线程优先级
			最低优先级1
			默认优先级是5
			最高优先级10
			优先级比较高的获取CPU时间片可能会多一些。（但也不完全是，大概率是多的。）
		
		静态方法：
			static void yield()  让位方法
			暂停当前正在执行的线程对象，并执行其他线程
			yield()方法不是阻塞方法。让当前线程让位，让给其它线程使用。
			yield()方法的执行会让当前线程从“运行状态”回到“就绪状态”。
			注意：在回到就绪之后，有可能还会再次抢到。
		
		实例方法：
			void join()  
			合并线程
			class MyThread1 extends Thread {
				public void doSome(){
					MyThread2 t = new MyThread2();
					t.join(); // 当前线程进入阻塞，t线程执行，直到t线程结束。当前线程才可以继续。
				}
			}

			class MyThread2 extends Thread{
				
			}
```

### 16.19 线程的优先级

```java
package com.bjpowernode.java.thread;

/*
了解：关于线程的优先级
 */
public class ThreadTest11 {
    public static void main(String[] args) {
        // 设置主线程的优先级为1
        Thread.currentThread().setPriority(1);

        /*System.out.println("最高优先级" + Thread.MAX_PRIORITY);
        System.out.println("最低优先级" + Thread.MIN_PRIORITY);
        System.out.println("默认优先级" + Thread.NORM_PRIORITY);*/

        // 获取当前线程对象，获取当前线程的优先级
        Thread currentThread = Thread.currentThread();
        // main线程的默认优先级是：5
        //System.out.println(currentThread.getName() + "线程的默认优先级是：" + currentThread.getPriority());

        Thread t = new Thread(new MyRunnable5());
        t.setPriority(10);
        t.setName("t");
        t.start();

        // 优先级较高的，只是抢到的CPU时间片相对多一些。
        // 大概率方向更偏向于优先级比较高的。
        for(int i = 0; i < 10000; i++){
            System.out.println(Thread.currentThread().getName() + "-->" + i);
        }


    }
}

class MyRunnable5 implements Runnable {

    @Override
    public void run() {
        // 获取线程优先级
        //System.out.println(Thread.currentThread().getName() + "线程的默认优先级：" + Thread.currentThread().getPriority());
        for(int i = 0; i < 10000; i++){
            System.out.println(Thread.currentThread().getName() + "-->" + i);
        }
    }
}

```

### 16.20 线程让位

```java
package com.bjpowernode.java.thread;

/*
让位，当前线程暂停，回到就绪状态，让给其它线程。
静态方法：Thread.yield();
 */
public class ThreadTest12 {
    public static void main(String[] args) {
        Thread t = new Thread(new MyRunnable6());
        t.setName("t");
        t.start();

        for(int i = 1; i <= 10000; i++) {
            System.out.println(Thread.currentThread().getName() + "--->" + i);
        }
    }
}

class MyRunnable6 implements Runnable {

    @Override
    public void run() {
        for(int i = 1; i <= 10000; i++) {
            //每100个让位一次。
            if(i % 100 == 0){
                Thread.yield(); // 当前线程暂停一下，让给主线程。
            }
            System.out.println(Thread.currentThread().getName() + "--->" + i);
        }
    }
}

```

### 16.21 线程合并

```java
package com.bjpowernode.java.thread;

/*
线程合并
 */
public class ThreadTest13 {
    public static void main(String[] args) {
        System.out.println("main begin");

        Thread t = new Thread(new MyRunnable7());
        t.setName("t");
        t.start();

        //合并线程
        try {
            t.join(); // t合并到当前线程中，当前线程受阻塞，t线程执行直到结束。
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        System.out.println("main over");
    }
}

class MyRunnable7 implements Runnable {

    @Override
    public void run() {
        for(int i = 0; i < 10000; i++){
            System.out.println(Thread.currentThread().getName() + "--->" + i);
        }
    }
}

```

### 16.22 线程安全是重点

```java
2、关于多线程并发环境下，数据的安全问题。

	2.1、为什么这个是重点？
		以后在开发中，我们的项目都是运行在服务器当中，
		而服务器已经将线程的定义，线程对象的创建，线程
		的启动等，都已经实现完了。这些代码我们都不需要
		编写。

		最重要的是：你要知道，你编写的程序需要放到一个
		多线程的环境下运行，你更需要关注的是这些数据
		在多线程并发的环境下是否是安全的。（重点：*****）
```

### 16.23 线程不安全的条件

![day33-多线程并发对同一个账户进行取款](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/day33-%E5%A4%9A%E7%BA%BF%E7%A8%8B%E5%B9%B6%E5%8F%91%E5%AF%B9%E5%90%8C%E4%B8%80%E4%B8%AA%E8%B4%A6%E6%88%B7%E8%BF%9B%E8%A1%8C%E5%8F%96%E6%AC%BE.png)

```java

	2.2、什么时候数据在多线程并发的环境下会存在安全问题呢？
		三个条件：
			条件1：多线程并发。
			条件2：有共享数据。
			条件3：共享数据有修改的行为。

		满足以上3个条件之后，就会存在线程安全问题。
```

### 16.24 怎么解决线程安全

```java
2.3、怎么解决线程安全问题呢？
		当多线程并发的环境下，有共享数据，并且这个数据还会被修改，此时就存在
		线程安全问题，怎么解决这个问题？
			线程排队执行。（不能并发）。
			用排队执行解决线程安全问题。
			这种机制被称为：线程同步机制。

			专业术语叫做：线程同步，实际上就是线程不能并发了，线程必须排队执行。
		
		怎么解决线程安全问题呀？
			使用“线程同步机制”。
		
		线程同步就是线程排队了，线程排队了就会牺牲一部分效率，没办法，数据安全
		第一位，只有数据安全了，我们才可以谈效率。数据不安全，没有效率的事儿。
```

### 16.25 同步和异步的理解

```java
2.4、说到线程同步这块，涉及到这两个专业术语：

		异步编程模型：
			线程t1和线程t2，各自执行各自的，t1不管t2，t2不管t1，
			谁也不需要等谁，这种编程模型叫做：异步编程模型。
			其实就是：多线程并发（效率较高。）

			异步就是并发。

		同步编程模型：
			线程t1和线程t2，在线程t1执行的时候，必须等待t2线程执行
			结束，或者说在t2线程执行的时候，必须等待t1线程执行结束，
			两个线程之间发生了等待关系，这就是同步编程模型。
			效率较低。线程排队执行。

			同步就是排队。
```

### 16.27 账户类的定义

```java
package com.bjpowernode.java.threadsafe;
/*
银行账户
    不使用线程同步机制，多线程对同一个账户进行取款，出现线程安全问题。
 */
public class Account {
    // 账号
    private String actno;
    // 余额
    private double balance;

    public Account() {
    }

    public Account(String actno, double balance) {
        this.actno = actno;
        this.balance = balance;
    }

    public String getActno() {
        return actno;
    }

    public void setActno(String actno) {
        this.actno = actno;
    }

    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }

    //取款的方法
    public void withdraw(double money){
        // t1和t2并发这个方法。。。。（t1和t2是两个栈。两个栈操作堆中同一个对象。）
        // 取款之前的余额
        double before = this.getBalance(); // 10000
        // 取款之后的余额
        double after = before - money;

        // 在这里模拟一下网络延迟，100%会出现问题
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        // 更新余额
        // 思考：t1执行到这里了，但还没有来得及执行这行代码，t2线程进来withdraw方法了。此时一定出问题。
        this.setBalance(after);
    }
}
```

### 16.28 模拟两个线程对同一个账户取款

``` java
package com.bjpowernode.java.threadsafe;
/*
银行账户
    不使用线程同步机制，多线程对同一个账户进行取款，出现线程安全问题。
 */
public class Account {
    // 账号
    private String actno;
    // 余额
    private double balance;

    public Account() {
    }

    public Account(String actno, double balance) {
        this.actno = actno;
        this.balance = balance;
    }

    public String getActno() {
        return actno;
    }

    public void setActno(String actno) {
        this.actno = actno;
    }

    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }

    //取款的方法
    public void withdraw(double money){
        // t1和t2并发这个方法。。。。（t1和t2是两个栈。两个栈操作堆中同一个对象。）
        // 取款之前的余额
        double before = this.getBalance(); // 10000
        // 取款之后的余额
        double after = before - money;

        // 在这里模拟一下网络延迟，100%会出现问题
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        // 更新余额
        // 思考：t1执行到这里了，但还没有来得及执行这行代码，t2线程进来withdraw方法了。此时一定出问题。
        this.setBalance(after);
    }
}

package com.bjpowernode.java.threadsafe;

public class AccountThread extends Thread {

    // 两个线程必须共享同一个账户对象。
    private Account act;

    // 通过构造方法传递过来账户对象
    public AccountThread(Account act) {
        this.act = act;
    }

    public void run(){
        // run方法的执行表示取款操作。
        // 假设取款5000
        double money = 5000;
        // 取款
        // 多线程并发执行这个方法。
        act.withdraw(money);

        System.out.println(Thread.currentThread().getName() + "对"+act.getActno()+"取款"+money+"成功，余额" + act.getBalance());
    }
}


package com.bjpowernode.java.threadsafe;

public class Test {
    public static void main(String[] args) {
        // 创建账户对象（只创建1个）
        Account act = new Account("act-001", 10000);
        // 创建两个线程
        Thread t1 = new AccountThread(act);
        Thread t2 = new AccountThread(act);
        // 设置name
        t1.setName("t1");
        t2.setName("t2");
        // 启动线程取款
        t1.start();
        t2.start();
    }
}

```

### 16.29 同步代码块synchronized

```java
package com.bjpowernode.java.threadsafe2;
/*
银行账户
    使用线程同步机制，解决线程安全问题。
 */
public class Account {
    // 账号
    private String actno;
    // 余额
    private double balance; //实例变量。

    //对象
    Object obj = new Object(); // 实例变量。（Account对象是多线程共享的，Account对象中的实例变量obj也是共享的。）

    public Account() {
    }

    public Account(String actno, double balance) {
        this.actno = actno;
        this.balance = balance;
    }

    public String getActno() {
        return actno;
    }

    public void setActno(String actno) {
        this.actno = actno;
    }

    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }

    //取款的方法
    public void withdraw(double money){

        //int i = 100;
        //i = 101;

        // 以下这几行代码必须是线程排队的，不能并发。
        // 一个线程把这里的代码全部执行结束之后，另一个线程才能进来。
        /*
        线程同步机制的语法是：
            synchronized(){
                // 线程同步代码块。
            }
            synchronized后面小括号中传的这个“数据”是相当关键的。
            这个数据必须是多线程共享的数据。才能达到多线程排队。

            ()中写什么？
                那要看你想让哪些线程同步。
                假设t1、t2、t3、t4、t5，有5个线程，
                你只希望t1 t2 t3排队，t4 t5不需要排队。怎么办？
                你一定要在()中写一个t1 t2 t3共享的对象。而这个
                对象对于t4 t5来说不是共享的。

            这里的共享对象是：账户对象。
            账户对象是共享的，那么this就是账户对象吧！！！
            不一定是this，这里只要是多线程共享的那个对象就行。

            在java语言中，任何一个对象都有“一把锁”，其实这把锁就是标记。（只是把它叫做锁。）
            100个对象，100把锁。1个对象1把锁。

            以下代码的执行原理？
                1、假设t1和t2线程并发，开始执行以下代码的时候，肯定有一个先一个后。
                2、假设t1先执行了，遇到了synchronized，这个时候自动找“后面共享对象”的对象锁，
                找到之后，并占有这把锁，然后执行同步代码块中的程序，在程序执行过程中一直都是
                占有这把锁的。直到同步代码块代码结束，这把锁才会释放。
                3、假设t1已经占有这把锁，此时t2也遇到synchronized关键字，也会去占有后面
                共享对象的这把锁，结果这把锁被t1占有，t2只能在同步代码块外面等待t1的结束，
                直到t1把同步代码块执行结束了，t1会归还这把锁，此时t2终于等到这把锁，然后
                t2占有这把锁之后，进入同步代码块执行程序。

                这样就达到了线程排队执行。
                这里需要注意的是：这个共享对象一定要选好了。这个共享对象一定是你需要排队
                执行的这些线程对象所共享的。
         */
        //Object obj2 = new Object();
        //synchronized (this){
        //synchronized (obj) {
        //synchronized ("abc") { // "abc"在字符串常量池当中。
        //synchronized (null) { // 报错：空指针。
        //synchronized (obj2) { // 这样编写就不安全了。因为obj2不是共享对象。
            double before = this.getBalance();
            double after = before - money;
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            this.setBalance(after);
        //}
    }
    
}

package com.bjpowernode.java.threadsafe2;

public class AccountThread extends Thread {

    // 两个线程必须共享同一个账户对象。
    private Account act;

    // 通过构造方法传递过来账户对象
    public AccountThread(Account act) {
        this.act = act;
    }

    public void run(){
        // run方法的执行表示取款操作。
        // 假设取款5000
        double money = 5000;
        // 取款
        // 多线程并发执行这个方法。
        //synchronized (this) { //这里的this是AccountThread对象，这个对象不共享！
        synchronized (act) { // 这种方式也可以，只不过扩大了同步的范围，效率更低了。
            act.withdraw(money);
        }

        System.out.println(Thread.currentThread().getName() + "对"+act.getActno()+"取款"+money+"成功，余额" + act.getBalance());
    }
}

package com.bjpowernode.java.threadsafe2;

public class Test {
    public static void main(String[] args) {
        // 创建账户对象（只创建1个）
        Account act = new Account("act-001", 10000);
        // 创建两个线程
        Thread t1 = new AccountThread(act);
        Thread t2 = new AccountThread(act);

        // 设置name
        t1.setName("t1");
        t2.setName("t2");
        // 启动线程取款
        t1.start();
        t2.start();
    }
}

```

### 16.30 对synchronized的理解

![image-20210821130523652](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/image-20210821130523652.png)

```java
package com.bjpowernode.java.threadsafe2;
/*
银行账户
    使用线程同步机制，解决线程安全问题。
 */
public class Account {
    // 账号
    private String actno;
    // 余额
    private double balance; //实例变量。

    //对象
    Object obj = new Object(); // 实例变量。（Account对象是多线程共享的，Account对象中的实例变量obj也是共享的。）

    public Account() {
    }

    public Account(String actno, double balance) {
        this.actno = actno;
        this.balance = balance;
    }

    public String getActno() {
        return actno;
    }

    public void setActno(String actno) {
        this.actno = actno;
    }

    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }

    //取款的方法
    public void withdraw(double money){

        //int i = 100;
        //i = 101;

        // 以下这几行代码必须是线程排队的，不能并发。
        // 一个线程把这里的代码全部执行结束之后，另一个线程才能进来。
        /*
        线程同步机制的语法是：
            synchronized(){
                // 线程同步代码块。
            }
            synchronized后面小括号中传的这个“数据”是相当关键的。
            这个数据必须是多线程共享的数据。才能达到多线程排队。

            ()中写什么？
                那要看你想让哪些线程同步。
                假设t1、t2、t3、t4、t5，有5个线程，
                你只希望t1 t2 t3排队，t4 t5不需要排队。怎么办？
                你一定要在()中写一个t1 t2 t3共享的对象。而这个
                对象对于t4 t5来说不是共享的。

            这里的共享对象是：账户对象。
            账户对象是共享的，那么this就是账户对象吧！！！
            不一定是this，这里只要是多线程共享的那个对象就行。

            在java语言中，任何一个对象都有“一把锁”，其实这把锁就是标记。（只是把它叫做锁。）
            100个对象，100把锁。1个对象1把锁。

            以下代码的执行原理？
                1、假设t1和t2线程并发，开始执行以下代码的时候，肯定有一个先一个后。
                2、假设t1先执行了，遇到了synchronized，这个时候自动找“后面共享对象”的对象锁，
                找到之后，并占有这把锁，然后执行同步代码块中的程序，在程序执行过程中一直都是
                占有这把锁的。直到同步代码块代码结束，这把锁才会释放。
                3、假设t1已经占有这把锁，此时t2也遇到synchronized关键字，也会去占有后面
                共享对象的这把锁，结果这把锁被t1占有，t2只能在同步代码块外面等待t1的结束，
                直到t1把同步代码块执行结束了，t1会归还这把锁，此时t2终于等到这把锁，然后
                t2占有这把锁之后，进入同步代码块执行程序。

                这样就达到了线程排队执行。
                这里需要注意的是：这个共享对象一定要选好了。这个共享对象一定是你需要排队
                执行的这些线程对象所共享的。
         */
        //Object obj2 = new Object();
        //synchronized (this){
        //synchronized (obj) {
        //synchronized ("abc") { // "abc"在字符串常量池当中。
        //synchronized (null) { // 报错：空指针。
        //synchronized (obj2) { // 这样编写就不安全了。因为obj2不是共享对象。
            double before = this.getBalance();
            double after = before - money;
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            this.setBalance(after);
        //}
    }
    
}

package com.bjpowernode.java.threadsafe2;

public class AccountThread extends Thread {

    // 两个线程必须共享同一个账户对象。
    private Account act;

    // 通过构造方法传递过来账户对象
    public AccountThread(Account act) {
        this.act = act;
    }

    public void run(){
        // run方法的执行表示取款操作。
        // 假设取款5000
        double money = 5000;
        // 取款
        // 多线程并发执行这个方法。
        //synchronized (this) { //这里的this是AccountThread对象，这个对象不共享！
        synchronized (act) { // 这种方式也可以，只不过扩大了同步的范围，效率更低了。
            act.withdraw(money);
        }

        System.out.println(Thread.currentThread().getName() + "对"+act.getActno()+"取款"+money+"成功，余额" + act.getBalance());
    }
}

package com.bjpowernode.java.threadsafe2;

public class Test {
    public static void main(String[] args) {
        // 创建账户对象（只创建1个）
        Account act = new Account("act-001", 10000);
        // 创建两个线程
        Thread t1 = new AccountThread(act);
        Thread t2 = new AccountThread(act);

        // 设置name
        t1.setName("t1");
        t2.setName("t2");
        // 启动线程取款
        t1.start();
        t2.start();
    }
}
```

### 16.31 哪些变量有线程安全问题

```java
3、Java中有三大变量？【重要的内容。】

	实例变量：在堆中。

	静态变量：在方法区。

	局部变量：在栈中。

	以上三大变量中：
		局部变量永远都不会存在线程安全问题。
		因为局部变量不共享。（一个线程一个栈。）
		局部变量在栈中。所以局部变量永远都不会共享。
	
	实例变量在堆中，堆只有1个。
	静态变量在方法区中，方法区只有1个。
	堆和方法区都是多线程共享的，所以可能存在线程安全问题。

	局部变量+常量：不会有线程安全问题。
	成员变量：可能会有线程安全问题。
```

### 16.32 扩大同步范围

```java
package com.bjpowernode.java.threadsafe2;
/*
银行账户
    使用线程同步机制，解决线程安全问题。
 */
public class Account {
    // 账号
    private String actno;
    // 余额
    private double balance; //实例变量。

    //对象
    Object obj = new Object(); // 实例变量。（Account对象是多线程共享的，Account对象中的实例变量obj也是共享的。）

    public Account() {
    }

    public Account(String actno, double balance) {
        this.actno = actno;
        this.balance = balance;
    }

    public String getActno() {
        return actno;
    }

    public void setActno(String actno) {
        this.actno = actno;
    }

    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }

    //取款的方法
    public void withdraw(double money){

        //int i = 100;
        //i = 101;

        // 以下这几行代码必须是线程排队的，不能并发。
        // 一个线程把这里的代码全部执行结束之后，另一个线程才能进来。
        /*
        线程同步机制的语法是：
            synchronized(){
                // 线程同步代码块。
            }
            synchronized后面小括号中传的这个“数据”是相当关键的。
            这个数据必须是多线程共享的数据。才能达到多线程排队。

            ()中写什么？
                那要看你想让哪些线程同步。
                假设t1、t2、t3、t4、t5，有5个线程，
                你只希望t1 t2 t3排队，t4 t5不需要排队。怎么办？
                你一定要在()中写一个t1 t2 t3共享的对象。而这个
                对象对于t4 t5来说不是共享的。

            这里的共享对象是：账户对象。
            账户对象是共享的，那么this就是账户对象吧！！！
            不一定是this，这里只要是多线程共享的那个对象就行。

            在java语言中，任何一个对象都有“一把锁”，其实这把锁就是标记。（只是把它叫做锁。）
            100个对象，100把锁。1个对象1把锁。

            以下代码的执行原理？
                1、假设t1和t2线程并发，开始执行以下代码的时候，肯定有一个先一个后。
                2、假设t1先执行了，遇到了synchronized，这个时候自动找“后面共享对象”的对象锁，
                找到之后，并占有这把锁，然后执行同步代码块中的程序，在程序执行过程中一直都是
                占有这把锁的。直到同步代码块代码结束，这把锁才会释放。
                3、假设t1已经占有这把锁，此时t2也遇到synchronized关键字，也会去占有后面
                共享对象的这把锁，结果这把锁被t1占有，t2只能在同步代码块外面等待t1的结束，
                直到t1把同步代码块执行结束了，t1会归还这把锁，此时t2终于等到这把锁，然后
                t2占有这把锁之后，进入同步代码块执行程序。

                这样就达到了线程排队执行。
                这里需要注意的是：这个共享对象一定要选好了。这个共享对象一定是你需要排队
                执行的这些线程对象所共享的。
         */
        //Object obj2 = new Object();
        //synchronized (this){
        //synchronized (obj) {
        //synchronized ("abc") { // "abc"在字符串常量池当中。
        //synchronized (null) { // 报错：空指针。
        //synchronized (obj2) { // 这样编写就不安全了。因为obj2不是共享对象。
            double before = this.getBalance();
            double after = before - money;
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            this.setBalance(after);
        //}
    }
    
}

package com.bjpowernode.java.threadsafe2;

public class AccountThread extends Thread {

    // 两个线程必须共享同一个账户对象。
    private Account act;

    // 通过构造方法传递过来账户对象
    public AccountThread(Account act) {
        this.act = act;
    }

    public void run(){
        // run方法的执行表示取款操作。
        // 假设取款5000
        double money = 5000;
        // 取款
        // 多线程并发执行这个方法。
        //synchronized (this) { //这里的this是AccountThread对象，这个对象不共享！
        synchronized (act) { // 这种方式也可以，只不过扩大了同步的范围，效率更低了。
            act.withdraw(money);
        }

        System.out.println(Thread.currentThread().getName() + "对"+act.getActno()+"取款"+money+"成功，余额" + act.getBalance());
    }
}

package com.bjpowernode.java.threadsafe2;

public class Test {
    public static void main(String[] args) {
        // 创建账户对象（只创建1个）
        Account act = new Account("act-001", 10000);
        // 创建两个线程
        Thread t1 = new AccountThread(act);
        Thread t2 = new AccountThread(act);

        // 设置name
        t1.setName("t1");
        t2.setName("t2");
        // 启动线程取款
        t1.start();
        t2.start();
    }
}
```

### 16.33 synchronized出现在实例方法上

```java
package com.bjpowernode.java.threadsafe3;

public class Account {
    // 账号
    private String actno;
    // 余额
    private double balance;

    public Account() {
    }

    public Account(String actno, double balance) {
        this.actno = actno;
        this.balance = balance;
    }

    public String getActno() {
        return actno;
    }

    public void setActno(String actno) {
        this.actno = actno;
    }

    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }

    //取款的方法
    /*
    在实例方法上可以使用synchronized吗？可以的。
        synchronized出现在实例方法上，一定锁的是this。
        没得挑。只能是this。不能是其他的对象了。
        所以这种方式不灵活。

        另外还有一个缺点：synchronized出现在实例方法上，
        表示整个方法体都需要同步，可能会无故扩大同步的
        范围，导致程序的执行效率降低。所以这种方式不常用。

        synchronized使用在实例方法上有什么优点？
            代码写的少了。节俭了。

        如果共享的对象就是this，并且需要同步的代码块是整个方法体，
        建议使用这种方式。
     */
    public synchronized void withdraw(double money){
        double before = this.getBalance(); // 10000
        double after = before - money;
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        this.setBalance(after);
    }
}
```

### 16.34 synchroized的三种写法

```java
synchronized有三种写法：

		第一种：同步代码块
			灵活
			synchronized(线程共享对象){
				同步代码块;
			}

		第二种：在实例方法上使用synchronized
			表示共享对象一定是this
			并且同步代码块是整个方法体。
		
		第三种：在静态方法上使用synchronized
			表示找类锁。
			类锁永远只有1把。
			就算创建了100个对象，那类锁也只有一把。
		
		对象锁：1个对象1把锁，100个对象100把锁。
		类锁：100个对象，也可能只是1把类锁。
```

### 16.35 synchoized面试题

```java
package com.bjpowernode.java.exam1;

// 面试题：doOther方法执行的时候需要等待doSome方法的结束吗？
    //不需要，因为doOther()方法没有synchronized
public class Exam01 {
    public static void main(String[] args) throws InterruptedException {
        MyClass mc = new MyClass();

        Thread t1 = new MyThread(mc);
        Thread t2 = new MyThread(mc);

        t1.setName("t1");
        t2.setName("t2");

        t1.start();
        Thread.sleep(1000); //这个睡眠的作用是：为了保证t1线程先执行。
        t2.start();
    }
}

class MyThread extends Thread {
    private MyClass mc;
    public MyThread(MyClass mc){
        this.mc = mc;
    }
    public void run(){
        if(Thread.currentThread().getName().equals("t1")){
            mc.doSome();
        }
        if(Thread.currentThread().getName().equals("t2")){
            mc.doOther();
        }
    }
}

class MyClass {
    public synchronized void doSome(){
        System.out.println("doSome begin");
        try {
            Thread.sleep(1000 * 10);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("doSome over");
    }
    public void doOther(){
        System.out.println("doOther begin");
        System.out.println("doOther over");
    }
}

package com.bjpowernode.java.exam2;

// 面试题：doOther方法执行的时候需要等待doSome方法的结束吗？
    //需要
public class Exam01 {
    public static void main(String[] args) throws InterruptedException {
        MyClass mc = new MyClass();

        Thread t1 = new MyThread(mc);
        Thread t2 = new MyThread(mc);

        t1.setName("t1");
        t2.setName("t2");

        t1.start();
        Thread.sleep(1000); //这个睡眠的作用是：为了保证t1线程先执行。
        t2.start();
    }
}

class MyThread extends Thread {
    private MyClass mc;
    public MyThread(MyClass mc){
        this.mc = mc;
    }
    public void run(){
        if(Thread.currentThread().getName().equals("t1")){
            mc.doSome();
        }
        if(Thread.currentThread().getName().equals("t2")){
            mc.doOther();
        }
    }
}

class MyClass {
    public synchronized void doSome(){
        System.out.println("doSome begin");
        try {
            Thread.sleep(1000 * 10);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("doSome over");
    }
    public synchronized void doOther(){
        System.out.println("doOther begin");
        System.out.println("doOther over");
    }
}

package com.bjpowernode.java.exam3;

// 面试题：doOther方法执行的时候需要等待doSome方法的结束吗？
    //不需要，因为MyClass对象是两个，两把锁。
public class Exam01 {
    public static void main(String[] args) throws InterruptedException {
        MyClass mc1 = new MyClass();
        MyClass mc2 = new MyClass();

        Thread t1 = new MyThread(mc1);
        Thread t2 = new MyThread(mc2);

        t1.setName("t1");
        t2.setName("t2");

        t1.start();
        Thread.sleep(1000); //这个睡眠的作用是：为了保证t1线程先执行。
        t2.start();
    }
}

class MyThread extends Thread {
    private MyClass mc;
    public MyThread(MyClass mc){
        this.mc = mc;
    }
    public void run(){
        if(Thread.currentThread().getName().equals("t1")){
            mc.doSome();
        }
        if(Thread.currentThread().getName().equals("t2")){
            mc.doOther();
        }
    }
}

class MyClass {
    public synchronized void doSome(){
        System.out.println("doSome begin");
        try {
            Thread.sleep(1000 * 10);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("doSome over");
    }
    public synchronized void doOther(){
        System.out.println("doOther begin");
        System.out.println("doOther over");
    }
}

package com.bjpowernode.java.exam4;

// 面试题：doOther方法执行的时候需要等待doSome方法的结束吗？
    //需要，因为静态方法是类锁，不管创建了几个对象，类锁只有1把。
public class Exam01 {
    public static void main(String[] args) throws InterruptedException {
        MyClass mc1 = new MyClass();
        MyClass mc2 = new MyClass();

        Thread t1 = new MyThread(mc1);
        Thread t2 = new MyThread(mc2);

        t1.setName("t1");
        t2.setName("t2");

        t1.start();
        Thread.sleep(1000); //这个睡眠的作用是：为了保证t1线程先执行。
        t2.start();
    }
}

class MyThread extends Thread {
    private MyClass mc;
    public MyThread(MyClass mc){
        this.mc = mc;
    }
    public void run(){
        if(Thread.currentThread().getName().equals("t1")){
            mc.doSome();
        }
        if(Thread.currentThread().getName().equals("t2")){
            mc.doOther();
        }
    }
}

class MyClass {
    // synchronized出现在静态方法上是找类锁。
    public synchronized static void doSome(){
        System.out.println("doSome begin");
        try {
            Thread.sleep(1000 * 10);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("doSome over");
    }
    public synchronized static void doOther(){
        System.out.println("doOther begin");
        System.out.println("doOther over");
    }
}

```

### 16.36 死锁概述

![day33-死锁](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/day33-%E6%AD%BB%E9%94%81.png)

```java
package com.bjpowernode.java.deadlock;
/*
死锁代码要会写。
一般面试官要求你会写。
只有会写的，才会在以后的开发中注意这个事儿。
因为死锁很难调试。
 */
public class DeadLock {
    public static void main(String[] args) {
        Object o1 = new Object();
        Object o2 = new Object();

        // t1和t2两个线程共享o1,o2
        Thread t1 = new MyThread1(o1,o2);
        Thread t2 = new MyThread2(o1,o2);

        t1.start();
        t2.start();
    }
}

class MyThread1 extends Thread{
    Object o1;
    Object o2;
    public MyThread1(Object o1,Object o2){
        this.o1 = o1;
        this.o2 = o2;
    }
    public void run(){
        synchronized (o1){
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            synchronized (o2){

            }
        }
    }
}

class MyThread2 extends Thread {
    Object o1;
    Object o2;
    public MyThread2(Object o1,Object o2){
        this.o1 = o1;
        this.o2 = o2;
    }
    public void run(){
        synchronized (o2){
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            synchronized (o1){

            }
        }
    }
}

```

### 16.37 开发中怎么解决线程安全问题

```java
6、聊一聊，我们以后开发中应该怎么解决线程安全问题？

	是一上来就选择线程同步吗？synchronized
		不是，synchronized会让程序的执行效率降低，用户体验不好。
		系统的用户吞吐量降低。用户体验差。在不得已的情况下再选择
		线程同步机制。
	
	第一种方案：尽量使用局部变量代替“实例变量和静态变量”。

	第二种方案：如果必须是实例变量，那么可以考虑创建多个对象，这样
	实例变量的内存就不共享了。（一个线程对应1个对象，100个线程对应100个对象，
	对象不共享，就没有数据安全问题了。）

	第三种方案：如果不能使用局部变量，对象也不能创建多个，这个时候
	就只能选择synchronized了。线程同步机制。

```

### 16.38 线程这块还有哪些内容

```java
7、线程这块还有那些内容呢？列举一下
	7.1、守护线程
	7.2、定时器
	7.3、实现线程的第三种方式：FutureTask方式，实现Callable接口。（JDK8新特性。）
	7.4、关于Object类中的wait和notify方法。（生产者和消费者模式！）

```

### 16.39 守护线程概述

```java
1、线程这块还有那些内容呢？列举一下

	1.1、守护线程

		java语言中线程分为两大类：
			一类是：用户线程
			一类是：守护线程（后台线程）
			其中具有代表性的就是：垃圾回收线程（守护线程）。

		守护线程的特点：
			一般守护线程是一个死循环，所有的用户线程只要结束，
			守护线程自动结束。
		
		注意：主线程main方法是一个用户线程。

		守护线程用在什么地方呢？
			每天00:00的时候系统数据自动备份。
			这个需要使用到定时器，并且我们可以将定时器设置为守护线程。
			一直在那里看着，没到00:00的时候就备份一次。所有的用户线程
			如果结束了，守护线程自动退出，没有必要进行数据备份了。
```

### 16.40 实现守护线程

```java
package com.bjpowernode.java.thread;
/*
守护线程
 */
public class ThreadTest14 {
    public static void main(String[] args) {
        Thread t = new BakDataThread();
        t.setName("备份数据的线程");

        // 启动线程之前，将线程设置为守护线程
        t.setDaemon(true);

        t.start();

        // 主线程：主线程是用户线程
        for(int i = 0; i < 10; i++){
            System.out.println(Thread.currentThread().getName() + "--->" + i);
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}

class BakDataThread extends Thread {
    public void run(){
        int i = 0;
        // 即使是死循环，但由于该线程是守护者，当用户线程结束，守护线程自动终止。
        while(true){
            System.out.println(Thread.currentThread().getName() + "--->" + (++i));
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}
```

### 16.41 定时器概述和实现定时器

```java
1.2、定时器
		定时器的作用：
			间隔特定的时间，执行特定的程序。

			每周要进行银行账户的总账操作。
			每天要进行数据的备份操作。

			在实际的开发中，每隔多久执行一段特定的程序，这种需求是很常见的，
			那么在java中其实可以采用多种方式实现：
				
				可以使用sleep方法，睡眠，设置睡眠时间，没到这个时间点醒来，执行
				任务。这种方式是最原始的定时器。（比较low）

				在java的类库中已经写好了一个定时器：java.util.Timer，可以直接拿来用。
				不过，这种方式在目前的开发中也很少用，因为现在有很多高级框架都是支持
				定时任务的。

				在实际的开发中，目前使用较多的是Spring框架中提供的SpringTask框架，
				这个框架只要进行简单的配置，就可以完成定时器的任务。
    package com.bjpowernode.java.thread;

import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.Timer;
import java.util.TimerTask;

/*
使用定时器指定定时任务。
 */
public class TimerTest {
    public static void main(String[] args) throws Exception {

        // 创建定时器对象
        Timer timer = new Timer();
        //Timer timer = new Timer(true); //守护线程的方式

        // 指定定时任务
        //timer.schedule(定时任务, 第一次执行时间, 间隔多久执行一次);
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        Date firstTime = sdf.parse("2020-03-14 09:34:30");
        //timer.schedule(new LogTimerTask() , firstTime, 1000 * 10);
        // 每年执行一次。
        //timer.schedule(new LogTimerTask() , firstTime, 1000 * 60 * 60 * 24 * 365);

        //匿名内部类方式
        timer.schedule(new TimerTask(){
            @Override
            public void run() {
                // code....
            }
        } , firstTime, 1000 * 10);

    }
}

// 编写一个定时任务类
// 假设这是一个记录日志的定时任务
class LogTimerTask extends TimerTask {

    @Override
    public void run() {
        // 编写你需要执行的任务就行了。
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        String strTime = sdf.format(new Date());
        System.out.println(strTime + ":成功完成了一次数据备份！");
    }
}

```

### 16.42 实现线程的第三种方式

```java
package com.bjpowernode.java.thread;

import java.util.concurrent.Callable;
import java.util.concurrent.FutureTask; // JUC包下的，属于java的并发包，老JDK中没有这个包。新特性。

/*
实现线程的第三种方式：
    实现Callable接口
    这种方式的优点：可以获取到线程的执行结果。
    这种方式的缺点：效率比较低，在获取t线程执行结果的时候，当前线程受阻塞，效率较低。
 */
public class ThreadTest15 {
    public static void main(String[] args) throws Exception {

        // 第一步：创建一个“未来任务类”对象。
        // 参数非常重要，需要给一个Callable接口实现类对象。
        FutureTask task = new FutureTask(new Callable() {
            @Override
            public Object call() throws Exception { // call()方法就相当于run方法。只不过这个有返回值
                // 线程执行一个任务，执行之后可能会有一个执行结果
                // 模拟执行
                System.out.println("call method begin");
                Thread.sleep(1000 * 10);
                System.out.println("call method end!");
                int a = 100;
                int b = 200;
                return a + b; //自动装箱(300结果变成Integer)
            }
        });

        // 创建线程对象
        Thread t = new Thread(task);

        // 启动线程
        t.start();

        // 这里是main方法，这是在主线程中。
        // 在主线程中，怎么获取t线程的返回结果？
        // get()方法的执行会导致“当前线程阻塞”
        Object obj = task.get();
        System.out.println("线程执行结果:" + obj);

        // main方法这里的程序要想执行必须等待get()方法的结束
        // 而get()方法可能需要很久。因为get()方法是为了拿另一个线程的执行结果
        // 另一个线程执行是需要时间的。
        System.out.println("hello world!");
    }
}

```

### 16.43 wait和notify概述

![day34-wait和notify方法的理解](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/day34-wait%E5%92%8Cnotify%E6%96%B9%E6%B3%95%E7%9A%84%E7%90%86%E8%A7%A3.png)

``` java
1.4、关于Object类中的wait和notify方法。（生产者和消费者模式！）

		第一：wait和notify方法不是线程对象的方法，是java中任何一个java对象
		都有的方法，因为这两个方式是Object类中自带的。
			wait方法和notify方法不是通过线程对象调用，
			不是这样的：t.wait()，也不是这样的：t.notify()..不对。
		
		第二：wait()方法作用？
			Object o = new Object();
			o.wait();

			表示：
				让正在o对象上活动的线程进入等待状态，无期限等待，
				直到被唤醒为止。
				o.wait();方法的调用，会让“当前线程（正在o对象上
				活动的线程）”进入等待状态。

		第三：notify()方法作用？
			Object o = new Object();
			o.notify();

			表示：
				唤醒正在o对象上等待的线程。
			
			还有一个notifyAll()方法：
				这个方法是唤醒o对象上处于等待的所有线程。


```

### 16.44 生产者和消费者模式

![day34-生产者和消费者模式](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/day34-%E7%94%9F%E4%BA%A7%E8%80%85%E5%92%8C%E6%B6%88%E8%B4%B9%E8%80%85%E6%A8%A1%E5%BC%8F.png)

```java
1.4、关于Object类中的wait和notify方法。（生产者和消费者模式！）

		第一：wait和notify方法不是线程对象的方法，是java中任何一个java对象
		都有的方法，因为这两个方式是Object类中自带的。
			wait方法和notify方法不是通过线程对象调用，
			不是这样的：t.wait()，也不是这样的：t.notify()..不对。
		
		第二：wait()方法作用？
			Object o = new Object();
			o.wait();

			表示：
				让正在o对象上活动的线程进入等待状态，无期限等待，
				直到被唤醒为止。
				o.wait();方法的调用，会让“当前线程（正在o对象上
				活动的线程）”进入等待状态。

		第三：notify()方法作用？
			Object o = new Object();
			o.notify();

			表示：
				唤醒正在o对象上等待的线程。
			
			还有一个notifyAll()方法：
				这个方法是唤醒o对象上处于等待的所有线程。
```

### 16.45 实现生产者和消费者模式

```java
package com.ggs.java.thread.SE;

/**
 * @author wzx
 * @create 2021-06-01-17:43
 */


import java.util.ArrayList;
import java.util.List;

/**
 1、使用 wait 方法和 notify 方法实现“生产者和消费者模式”

 2、什么是“生产者和消费者模式”？
 生产线程负责生产，消费线程负责消费。
 生产线程和消费线程要达到均衡。
 这是一种特殊的业务需求，在这种特殊的情况下需要使用wait方法和notify方法。

 3、wait 和 notify方法不是线程对象的方法，是普通java对象都有的方法。

 4、wait方法和 notify方法建立在线程同步的基础之上。因为多线程要同时操作一个仓库。有线程安全问题。

 5、wait方法作用：o.wait()让正在o对象上活动的线程t进入等待状态，并且释放掉t线程之前占有的o对象的锁。

 6、notify 方法作用：o.notify()让正在o对象上等待的线程唤醒，只是通知，不会释放o对象上之前占有的锁。

 7、模拟这样一个需求：
 仓库我们采用 List 集合。
 List 集合中假设只能存储1个元素。
 1个元素就表示仓库满了。
 如果 List 集合中元素个数是0，就表示仓库空了。
 保证 List 集合中永远都是最多存储1个元素。

 必须做到这种效果：生产1个消费1个。
 * @author wzx
 */
public class ThreadTest16 {
    public static void main(String[] args) {
        // 创建1个仓库对象，共享的。
        List list = new ArrayList();
        // 创建两个线程对象
        // 生产者线程
        Thread t1 = new Thread(new Producer(list));
        // 消费者线程
        Thread t2 = new Thread(new Consumer(list));

        t1.setName("生产者线程");
        t2.setName("消费者线程");

        t1.start();
        t2.start();
    }
}

/** 生产线程*/
class Producer implements Runnable {
    // 仓库
    private List list;

    public Producer(List list) {
        this.list = list;
    }
    @Override
    public void run() {
        // 一直生产（使用死循环来模拟一直生产）
        while(true){
            // 给仓库对象list加锁。
            synchronized (list){
                if(list.size() > 0){ // 大于0，说明仓库中已经有1个元素了。
                    try {
                        // 当前线程进入等待状态，并且释放Producer之前占有的list集合的锁。
                        list.wait();
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
                // 程序能够执行到这里说明仓库是空的，可以生产
                Object obj = new Object();
                list.add(obj);
                System.out.println(Thread.currentThread().getName() + "--->" + obj);
                // 唤醒消费者进行消费
                list.notifyAll();
            }
        }
    }
}

 /**消费线程*/
class Consumer implements Runnable {
    // 仓库
    private List list;

    public Consumer(List list) {
        this.list = list;
    }

    @Override
    public void run() {
        // 一直消费
        while(true){
            synchronized (list) {
                if(list.size() == 0){
                    try {
                        // 仓库已经空了。
                        // 消费者线程等待，释放掉list集合的锁
                        list.wait();
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
                // 程序能够执行到此处说明仓库中有数据，进行消费。
                Object obj = list.remove(0);
                System.out.println(Thread.currentThread().getName() + "--->" + obj);
                // 唤醒生产者生产。
                list.notifyAll();
            }
        }
    }
}

```

### 16.46 wait和notify代码分析

```java
package com.ggs.java.thread.SE;

/**
 * @author wzx
 * @create 2021-06-01-17:43
 */


import java.util.ArrayList;
import java.util.List;

/**
 1、使用 wait 方法和 notify 方法实现“生产者和消费者模式”

 2、什么是“生产者和消费者模式”？
 生产线程负责生产，消费线程负责消费。
 生产线程和消费线程要达到均衡。
 这是一种特殊的业务需求，在这种特殊的情况下需要使用wait方法和notify方法。

 3、wait 和 notify方法不是线程对象的方法，是普通java对象都有的方法。

 4、wait方法和 notify方法建立在线程同步的基础之上。因为多线程要同时操作一个仓库。有线程安全问题。

 5、wait方法作用：o.wait()让正在o对象上活动的线程t进入等待状态，并且释放掉t线程之前占有的o对象的锁。

 6、notify 方法作用：o.notify()让正在o对象上等待的线程唤醒，只是通知，不会释放o对象上之前占有的锁。

 7、模拟这样一个需求：
 仓库我们采用 List 集合。
 List 集合中假设只能存储1个元素。
 1个元素就表示仓库满了。
 如果 List 集合中元素个数是0，就表示仓库空了。
 保证 List 集合中永远都是最多存储1个元素。

 必须做到这种效果：生产1个消费1个。
 * @author wzx
 */
public class ThreadTest16 {
    public static void main(String[] args) {
        // 创建1个仓库对象，共享的。
        List list = new ArrayList();
        // 创建两个线程对象
        // 生产者线程
        Thread t1 = new Thread(new Producer(list));
        // 消费者线程
        Thread t2 = new Thread(new Consumer(list));

        t1.setName("生产者线程");
        t2.setName("消费者线程");

        t1.start();
        t2.start();
    }
}

/** 生产线程*/
class Producer implements Runnable {
    // 仓库
    private List list;

    public Producer(List list) {
        this.list = list;
    }
    @Override
    public void run() {
        // 一直生产（使用死循环来模拟一直生产）
        while(true){
            // 给仓库对象list加锁。
            synchronized (list){
                if(list.size() > 0){ // 大于0，说明仓库中已经有1个元素了。
                    try {
                        // 当前线程进入等待状态，并且释放Producer之前占有的list集合的锁。
                        list.wait();
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
                // 程序能够执行到这里说明仓库是空的，可以生产
                Object obj = new Object();
                list.add(obj);
                System.out.println(Thread.currentThread().getName() + "--->" + obj);
                // 唤醒消费者进行消费
                list.notifyAll();
            }
        }
    }
}

 /**消费线程*/
class Consumer implements Runnable {
    // 仓库
    private List list;

    public Consumer(List list) {
        this.list = list;
    }

    @Override
    public void run() {
        // 一直消费
        while(true){
            synchronized (list) {
                if(list.size() == 0){
                    try {
                        // 仓库已经空了。
                        // 消费者线程等待，释放掉list集合的锁
                        list.wait();
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
                // 程序能够执行到此处说明仓库中有数据，进行消费。
                Object obj = list.remove(0);
                System.out.println(Thread.currentThread().getName() + "--->" + obj);
                // 唤醒生产者生产。
                list.notifyAll();
            }
        }
    }
}

```

### 16.47 线程实现交替输出

```java
```

### 16.48 反射机制概述

```java
2、反射机制（比较简单，因为只要会查帮助文档，就可以了。）
	
	2.1、反射机制有什么用？
		通过java语言中的反射机制可以操作字节码文件。
		优点类似于黑客。（可以读和修改字节码文件。）
		通过反射机制可以操作代码片段。（class文件。）
	
	2.2、反射机制的相关类在哪个包下？
		java.lang.reflect.*;
	
	2.3、反射机制相关的重要的类有哪些？

		java.lang.Class：代表整个字节码，代表一个类型，代表整个类。

		java.lang.reflect.Method：代表字节码中的方法字节码。代表类中的方法。

		java.lang.reflect.Constructor：代表字节码中的构造方法字节码。代表类中的构造方法

		java.lang.reflect.Field：代表字节码中的属性字节码。代表类中的成员变量（静态变量+实例变量）。

		java.lang.Class：
			public class User{
				// Field
				int no;

				// Constructor
				public User(){
				
				}
				public User(int no){
					this.no = no;
				}

				// Method
				public void setNo(int no){
					this.no = no;
				}
				public int getNo(){
					return no;
				}
			}
```

### 16.49 获取class的三种方式

![day34-字节码内存图](https://gitee.com/luck365/studypicture/raw/master/img/javase%E8%BF%9B%E9%98%B6/day34-%E5%AD%97%E8%8A%82%E7%A0%81%E5%86%85%E5%AD%98%E5%9B%BE.png)

```java
package com.ggs.java.reflect;

/**
 * @author wzx
 * @create 2021-06-02-21:11
 */


import java.util.Date;

/**
要操作一个类的字节码，需要首先获取到这个类的字节码，怎么获取java.lang.Class实例？
    三种方式
        第一种：Class c = Class.forName("完整类名带包名");
        第二种：Class c = 对象.getClass();
        第三种：Class c = 任何类型.class;

 */
public class ReflectTest01 {
    public static void main(String[] args) {
        /*
        Class.forName()
            1、静态方法
            2、方法的参数是一个字符串。
            3、字符串需要的是一个完整类名。
            4、完整类名必须带有包名。java.lang包也不能省略。
         */
        Class c1 = null;
        Class c2 = null;
        try {
            // c1代表String.class文件，或者说c1代表String类型。
            c1 = Class.forName("java.lang.String");
            // c2代表Date类型
            c2 = Class.forName("java.util.Date");
            // c3代表Integer类型
            Class c3 = Class.forName("java.lang.Integer");
            // c4代表System类型
            Class c4 = Class.forName("java.lang.System");

        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        }

        // java中任何一个对象都有一个方法：getClass()
        String s = "abc";
        // x代表String.class字节码文件，x代表String类型。
        Class x = s.getClass();
        // true（==判断的是对象的内存地址。）
        System.out.println(c1 == x);

        Date time = new Date();
        Class y = time.getClass();
        // true (c2和y两个变量中保存的内存地址都是一样的，都指向方法区中的字节码文件。)
        System.out.println(c2 == y);

        // 第三种方式，java语言中任何一种类型，包括基本数据类型，它都有.class属性。
        // z代表String类型
        Class z = String.class;
        // k代表Date类型
        Class k = Date.class;
        // f代表int类型
        Class f = int.class;
        // e代表double类型
        Class e = double.class;
        // true
        System.out.println(x == z);

    }
}

```

### 16.50 通过反射实例化对象

```java
package com.bjpowernode.java.reflect;

import com.bjpowernode.java.bean.User;

/*
获取到Class，能干什么？
    通过Class的newInstance()方法来实例化对象。
    注意：newInstance()方法内部实际上调用了无参数构造方法，必须保证无参构造存在才可以。
 */
public class ReflectTest02 {
    public static void main(String[] args) {

        // 这是不使用反射机制，创建对象
        User user = new User();
        System.out.println(user);

        // 下面这段代码是以反射机制的方式创建对象。
        try {
            // 通过反射机制，获取Class，通过Class来实例化对象
            Class c = Class.forName("com.bjpowernode.java.bean.User"); // c代表User类型。

            // newInstance() 这个方法会调用User这个类的无参数构造方法，完成对象的创建。
            // 重点是：newInstance()调用的是无参构造，必须保证无参构造是存在的！
            Object obj = c.newInstance();

            System.out.println(obj); // com.bjpowernode.java.bean.User@10f87f48
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        } catch (IllegalAccessException e) {
            e.printStackTrace();
        } catch (InstantiationException e) {
            e.printStackTrace();
        }
    }
}

```

### 16.51 通过读属性文件实现化对象

```java
package com.bjpowernode.java.reflect;

import com.bjpowernode.java.bean.User;

import java.io.FileReader;
import java.util.Properties;

/*
验证反射机制的灵活性。
    java代码写一遍，再不改变java源代码的基础之上，可以做到不同对象的实例化。
    非常之灵活。（符合OCP开闭原则：对扩展开放，对修改关闭。）

后期你们要学习的是高级框架，而工作过程中，也都是使用高级框架，
包括： ssh ssm
    Spring SpringMVC MyBatis
    Spring Struts Hibernate
    ...
    这些高级框架底层实现原理：都采用了反射机制。所以反射机制还是重要的。
    学会了反射机制有利于你理解剖析框架底层的源代码。
 */
public class ReflectTest03 {
    public static void main(String[] args) throws Exception{

        // 这种方式代码就写死了。只能创建一个User类型的对象
        //User user = new User();

        // 以下代码是灵活的，代码不需要改动，可以修改配置文件，配置文件修改之后，可以创建出不同的实例对象。
        // 通过IO流读取classinfo.properties文件
        FileReader reader = new FileReader("chapter25/classinfo2.properties");
        // 创建属性类对象Map
        Properties pro = new Properties(); // key value都是String
        // 加载
        pro.load(reader);
        // 关闭流
        reader.close();

        // 通过key获取value
        String className = pro.getProperty("className");
        //System.out.println(className);

        // 通过反射机制实例化对象
        Class c = Class.forName(className);
        Object obj = c.newInstance();
        System.out.println(obj);
    }
}

```

### 16.52 只让静态代码块执行可以使用forName

```java
package com.bjpowernode.java.reflect;
/*
研究一下：Class.forName()发生了什么？
    记住，重点：
        如果你只是希望一个类的静态代码块执行，其它代码一律不执行，
        你可以使用：
            Class.forName("完整类名");
        这个方法的执行会导致类加载，类加载时，静态代码块执行。

提示：
    后面JDBC技术的时候我们还需要。
 */
public class ReflectTest04 {
    public static void main(String[] args) {
        try {
            // Class.forName()这个方法的执行会导致：类加载。
            Class.forName("com.bjpowernode.java.reflect.MyClass");
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        }
    }
}


```

### 16.53 获取类路径下文件的绝对路径

```java
package com.bjpowernode.java.reflect;

import java.io.FileReader;

/*
研究一下文件路径的问题。
怎么获取一个文件的绝对路径。以下讲解的这种方式是通用的。但前提是：文件需要在类路径下。才能用这种方式。
 */
public class AboutPath {
    public static void main(String[] args) throws Exception{
        // 这种方式的路径缺点是：移植性差，在IDEA中默认的当前路径是project的根。
        // 这个代码假设离开了IDEA，换到了其它位置，可能当前路径就不是project的根了，这时这个路径就无效了。
        //FileReader reader = new FileReader("chapter25/classinfo2.properties");

        // 接下来说一种比较通用的一种路径。即使代码换位置了，这样编写仍然是通用的。
        // 注意：使用以下通用方式的前提是：这个文件必须在类路径下。
        // 什么类路径下？方式在src下的都是类路径下。【记住它】
        // src是类的根路径。
        /*
        解释：
            Thread.currentThread() 当前线程对象
            getContextClassLoader() 是线程对象的方法，可以获取到当前线程的类加载器对象。
            getResource() 【获取资源】这是类加载器对象的方法，当前线程的类加载器默认从类的根路径下加载资源。
         */
        String path = Thread.currentThread().getContextClassLoader()
                .getResource("classinfo2.properties").getPath(); // 这种方式获取文件绝对路径是通用的。

        // 采用以上的代码可以拿到一个文件的绝对路径。
        // /C:/Users/Administrator/IdeaProjects/javase/out/production/chapter25/classinfo2.properties
        System.out.println(path);

        // 获取db.properties文件的绝对路径（从类的根路径下作为起点开始）
        String path2 = Thread.currentThread().getContextClassLoader()
                .getResource("com/bjpowernode/java/bean/db.properties").getPath();
        System.out.println(path2);

    }
}

```

### 16.54 以流的形式直接返回

```java
package com.bjpowernode.java.reflect;

import java.io.FileReader;
import java.io.InputStream;
import java.util.Properties;

public class IoPropertiesTest {
    public static void main(String[] args) throws Exception{

        // 获取一个文件的绝对路径了！！！！！
        /*String path = Thread.currentThread().getContextClassLoader()
                .getResource("classinfo2.properties").getPath();
        FileReader reader = new FileReader(path);*/

        // 直接以流的形式返回。
        InputStream reader = Thread.currentThread().getContextClassLoader()
                .getResourceAsStream("classinfo2.properties");

        Properties pro = new Properties();
        pro.load(reader);
        reader.close();
        // 通过key获取value
        String className = pro.getProperty("className");
        System.out.println(className);
    }
}

```

### 16.55 资源绑定器

```java
package com.bjpowernode.java.reflect;

import java.util.ResourceBundle;

/*
java.util包下提供了一个资源绑定器，便于获取属性配置文件中的内容。
使用以下这种方式的时候，属性配置文件xxx.properties必须放到类路径下。
 */
public class ResourceBundleTest {
    public static void main(String[] args) {

        // 资源绑定器，只能绑定xxx.properties文件。并且这个文件必须在类路径下。文件扩展名也必须是properties
        // 并且在写路径的时候，路径后面的扩展名不能写。
        //ResourceBundle bundle = ResourceBundle.getBundle("classinfo2");

        ResourceBundle bundle = ResourceBundle.getBundle("com/bjpowernode/java/bean/db");

        String className = bundle.getString("className");
        System.out.println(className);

    }
}

```

### 16.56 类加载器概述

``` java

3、关于JDK中自带的类加载器：（聊一聊，不需要掌握，知道当然最好！）
	3.1、什么是类加载器？
		专门负责加载类的命令/工具。
		ClassLoader
	
	3.2、JDK中自带了3个类加载器
		启动类加载器:rt.jar
		扩展类加载器:ext/**.jar*/
		应用类加载器:classpath
	
	3.3、假设有这样一段代码：
		String s = "abc";
		
		代码在开始执行之前，会将所需要类全部加载到JVM当中。
		通过类加载器加载，看到以上代码类加载器会找String.class
		文件，找到就加载，那么是怎么进行加载的呢？

			首先通过“启动类加载器”加载。
				注意：启动类加载器专门加载：C:\Program Files\Java\jdk1.8.0_101\jre\lib\rt.jar
				rt.jar中都是JDK最核心的类库。
			
			如果通过“启动类加载器”加载不到的时候，
			会通过"扩展类加载器"加载。
				注意：扩展类加载器专门加载：C:\Program Files\Java\jdk1.8.0_101\jre\lib\ext\*.jar

	
			如果“扩展类加载器”没有加载到，那么
			会通过“应用类加载器”加载。
				注意：应用类加载器专门加载：classpath中的类。
	
```

### 16.57 双亲委派机制

```java
3.4、java中为了保证类加载的安全，使用了双亲委派机制。
		优先从启动类加载器中加载，这个称为“父”
		“父”无法加载到，再从扩展类加载器中加载，
		这个称为“母”。双亲委派。如果都加载不到，
		才会考虑从应用类加载器中加载。直到加载
		到为止。
		
```

### 16.58 获取Filed

```java
1、回顾反射机制

	1.1、什么是反射机制？反射机制有什么用？
		反射机制：可以操作字节码文件
		作用：可以让程序更加灵活。

	1.2、反射机制相关的类在哪个包下？
		java.lang.reflect.*;

	1.3、反射机制相关的主要的类？
		java.lang.Class
		java.lang.reflect.Method;
		java.lang.reflect.Constructor;
		java.lang.reflect.Field;

	1.4、在java中获取Class的三种方式？
		第一种：	 
			Class c = Class.forName("完整类名");
		第二种：
			Class c = 对象.getClass();
		第三种：
			Class c = int.class;
			Class c = String.class;

	1.5、获取了Class之后，可以调用无参数构造方法来实例化对象

		//c代表的就是日期Date类型
		Class c = Class.forName("java.util.Date");

		//实例化一个Date日期类型的对象
		Object obj = c.newInstance();

		一定要注意：
			newInstance()底层调用的是该类型的无参数构造方法。
			如果没有这个无参数构造方法会出现"实例化"异常。
	
	1.6、如果你只想让一个类的“静态代码块”执行的话，你可以怎么做？
		Class.forName("该类的类名");
		这样类就加载，类加载的时候，静态代码块执行！！！！
		在这里，对该方法的返回值不感兴趣，主要是为了使用“类加载”这个动作。
	
	1.7、关于路径问题？

		String path = Thread.currentThread().getContextClassLoader()
						  .getResource("写相对路径，但是这个相对路径从src出发开始找").getPath();	

		String path = Thread.currentThread().getContextClassLoader()
						  .getResource("abc").getPath();	//必须保证src下有abc文件。

		String path = Thread.currentThread().getContextClassLoader()
						  .getResource("a/db").getPath();	//必须保证src下有a目录，a目录下有db文件。
		
		String path = Thread.currentThread().getContextClassLoader()
						  .getResource("com/bjpowernode/test.properties").getPath();	
						  //必须保证src下有com目录，com目录下有bjpowernode目录。
						  //bjpowernode目录下有test.properties文件。

		这种方式是为了获取一个文件的绝对路径。（通用方式，不会受到环境移植的影响。）
		但是该文件要求放在类路径下，换句话说：也就是放到src下面。
		src下是类的根路径。

		直接以流的形式返回：
		InputStream in = Thread.currentThread().getContextClassLoader()
								.getResourceAsStream("com/bjpowernode/test.properties");

	1.8、IO + Properties，怎么快速绑定属性资源文件？

		//要求：第一这个文件必须在类路径下
		//第二这个文件必须是以.properties结尾。
		ResourceBundle bundle = ResourceBundle.getBundle("com/bjpowernode/test");
		String value = bundle.getString(key);

package com.bjpowernode.java.reflect;

import java.lang.reflect.Field;
import java.lang.reflect.Modifier;

/*
反射Student类当中所有的Field（了解一下）
 */
public class ReflectTest05 {
    public static void main(String[] args) throws Exception{

        // 获取整个类
        Class studentClass = Class.forName("com.bjpowernode.java.bean.Student");

        //com.bjpowernode.java.bean.Student
        String className = studentClass.getName();
        System.out.println("完整类名：" + className);

        String simpleName = studentClass.getSimpleName();
        System.out.println("简类名：" + simpleName);

        // 获取类中所有的public修饰的Field
        Field[] fields = studentClass.getFields();
        System.out.println(fields.length); // 测试数组中只有1个元素
        // 取出这个Field
        Field f = fields[0];
        // 取出这个Field它的名字
        String fieldName = f.getName();
        System.out.println(fieldName);

        // 获取所有的Field
        Field[] fs = studentClass.getDeclaredFields();
        System.out.println(fs.length); // 4

        System.out.println("==================================");
        // 遍历
        for(Field field : fs){
            // 获取属性的修饰符列表
            int i = field.getModifiers(); // 返回的修饰符是一个数字，每个数字是修饰符的代号！！！
            System.out.println(i);
            // 可以将这个“代号”数字转换成“字符串”吗？
            String modifierString = Modifier.toString(i);
            System.out.println(modifierString);
            // 获取属性的类型
            Class fieldType = field.getType();
            //String fName = fieldType.getName();
            String fName = fieldType.getSimpleName();
            System.out.println(fName);
            // 获取属性的名字
            System.out.println(field.getName());
        }
    }
}

package com.bjpowernode.java.bean;

// 反射属性Field
public class Student {

    // Field翻译为字段，其实就是属性/成员
    // 4个Field，分别采用了不同的访问控制权限修饰符
    private String name; // Field对象
    protected int age; // Field对象
    boolean sex;
    public int no;
    public static final double MATH_PI = 3.1415926;
}

```

### 16.59 通过反射机制访问对象属性

```java
package com.bjpowernode.java.reflect;

//通过反射机制，反编译一个类的属性Field（了解一下）

import java.lang.reflect.Field;
import java.lang.reflect.Modifier;

public class ReflectTest06 {
    public static void main(String[] args) throws Exception{

        // 创建这个是为了拼接字符串。
        StringBuilder s = new StringBuilder();

        //Class studentClass = Class.forName("com.bjpowernode.java.bean.Student");
        Class studentClass = Class.forName("java.lang.Thread");

        s.append(Modifier.toString(studentClass.getModifiers()) + " class " + studentClass.getSimpleName() + " {\n");

        Field[] fields = studentClass.getDeclaredFields();
        for(Field field : fields){
            s.append("\t");
            s.append(Modifier.toString(field.getModifiers()));
            s.append(" ");
            s.append(field.getType().getSimpleName());
            s.append(" ");
            s.append(field.getName());
            s.append(";\n");
        }

        s.append("}");
        System.out.println(s);

    }
}

```

### 16.60 访问对象属性

```java
package com.bjpowernode.java.reflect;

import com.bjpowernode.java.bean.Student;

import java.lang.reflect.Field;

/*
必须掌握：
    怎么通过反射机制访问一个java对象的属性？
        给属性赋值set
        获取属性的值get
 */
public class ReflectTest07 {
    public static void main(String[] args) throws Exception{

        // 我们不使用反射机制，怎么去访问一个对象的属性呢？
        Student s = new Student();

        // 给属性赋值
        s.no = 1111; //三要素：给s对象的no属性赋值1111
                    //要素1：对象s
                    //要素2：no属性
                    //要素3：1111

        // 读属性值
        // 两个要素：获取s对象的no属性的值。
        System.out.println(s.no);

        // 使用反射机制，怎么去访问一个对象的属性。（set get）
        Class studentClass = Class.forName("com.bjpowernode.java.bean.Student");
        Object obj = studentClass.newInstance(); // obj就是Student对象。（底层调用无参数构造方法）

        // 获取no属性（根据属性的名称来获取Field）
        Field noFiled = studentClass.getDeclaredField("no");

        // 给obj对象(Student对象)的no属性赋值
        /*
        虽然使用了反射机制，但是三要素还是缺一不可：
            要素1：obj对象
            要素2：no属性
            要素3：2222值
        注意：反射机制让代码复杂了，但是为了一个“灵活”，这也是值得的。
         */
        noFiled.set(obj, 22222); // 给obj对象的no属性赋值2222

        // 读取属性的值
        // 两个要素：获取obj对象的no属性的值。
        System.out.println(noFiled.get(obj));

        // 可以访问私有的属性吗？
        Field nameField = studentClass.getDeclaredField("name");

        // 打破封装（反射机制的缺点：打破封装，可能会给不法分子留下机会！！！）
        // 这样设置完之后，在外部也是可以访问private的。
        nameField.setAccessible(true);

        // 给name属性赋值
        nameField.set(obj, "jackson");
        // 获取name属性的值
        System.out.println(nameField.get(obj));
    }
}

```

### 16.61 可变长度参数

```java
package com.bjpowernode.java.reflect;
/*
可变长度参数
    int... args 这就是可变长度参数
    语法是：类型...  （注意：一定是3个点。）

    1、可变长度参数要求的参数个数是：0~N个。
    2、可变长度参数在参数列表中必须在最后一个位置上，而且可变长度参数只能有1个。
    3、可变长度参数可以当做一个数组来看待
 */
public class ArgsTest {
    public static void main(String[] args) {
        m();
        m(10);
        m(10, 20);

        // 编译报错
        //m("abc");

        m2(100);
        m2(200, "abc");
        m2(200, "abc", "def");
        m2(200, "abc", "def", "xyz");

        m3("ab", "de", "kk", "ff");

        String[] strs = {"a","b","c"};
        // 也可以传1个数组
        m3(strs);

        // 直接传1个数组
        m3(new String[]{"我","是","中","国", "人"}); //没必要

        m3("我","是","中","国", "人");
    }

    public static void m(int... args){
        System.out.println("m方法执行了！");
    }

    //public static void m2(int... args2, String... args1){}

    // 必须在最后，只能有1个。
    public static void m2(int a, String... args1){

    }

    public static void m3(String... args){
        //args有length属性，说明args是一个数组！
        // 可以将可变长度参数当做一个数组来看。
        for(int i = 0; i < args.length; i++){
            System.out.println(args[i]);
        }
    }

}

```

### 16.62 反射Method

```java
package com.bjpowernode.java.reflect;

import java.lang.reflect.Method;
import java.lang.reflect.Modifier;

/*
作为了解内容（不需要掌握）：
    反射Method
 */
public class ReflectTest08 {
    public static void main(String[] args) throws Exception{

        // 获取类了
        Class userServiceClass = Class.forName("com.bjpowernode.java.service.UserService");

        // 获取所有的Method（包括私有的！）
        Method[] methods = userServiceClass.getDeclaredMethods();
        //System.out.println(methods.length); // 2

        // 遍历Method
        for(Method method : methods){
            // 获取修饰符列表
            System.out.println(Modifier.toString(method.getModifiers()));
            // 获取方法的返回值类型
            System.out.println(method.getReturnType().getSimpleName());
            // 获取方法名
            System.out.println(method.getName());
            // 方法的修饰符列表（一个方法的参数可能会有多个。）
            Class[] parameterTypes = method.getParameterTypes();
            for(Class parameterType : parameterTypes){
                System.out.println(parameterType.getSimpleName());
            }
        }
    }
}

```

### 16.63 反编译Method

```java
package com.bjpowernode.java.reflect;

import java.lang.reflect.Method;
import java.lang.reflect.Modifier;

/*
了解一下，不需要掌握（反编译一个类的方法。）
 */
public class ReflectTest09 {
    public static void main(String[] args) throws Exception{
        StringBuilder s = new StringBuilder();
        //Class userServiceClass = Class.forName("com.bjpowernode.java.service.UserService");
        Class userServiceClass = Class.forName("java.lang.String");
        s.append(Modifier.toString(userServiceClass.getModifiers()) + " class "+userServiceClass.getSimpleName()+" {\n");

        Method[] methods = userServiceClass.getDeclaredMethods();
        for(Method method : methods){
            //public boolean login(String name,String password){}
            s.append("\t");
            s.append(Modifier.toString(method.getModifiers()));
            s.append(" ");
            s.append(method.getReturnType().getSimpleName());
            s.append(" ");
            s.append(method.getName());
            s.append("(");
            // 参数列表
            Class[] parameterTypes = method.getParameterTypes();
            for(Class parameterType : parameterTypes){
                s.append(parameterType.getSimpleName());
                s.append(",");
            }
            // 删除指定下标位置上的字符
            s.deleteCharAt(s.length() - 1);
            s.append("){}\n");
        }

        s.append("}");
        System.out.println(s);
    }
}

```

### 16.64 反射机制调用方法

```java
package com.bjpowernode.java.reflect;

import com.bjpowernode.java.service.UserService;

import java.lang.reflect.Method;

/*
重点：必须掌握，通过反射机制怎么调用一个对象的方法？
    五颗星*****

    反射机制，让代码很具有通用性，可变化的内容都是写到配置文件当中，
    将来修改配置文件之后，创建的对象不一样了，调用的方法也不同了，
    但是java代码不需要做任何改动。这就是反射机制的魅力。
 */
public class ReflectTest10 {
    public static void main(String[] args) throws Exception{
        // 不使用反射机制，怎么调用方法
        // 创建对象
        UserService userService = new UserService();
        // 调用方法
        /*
        要素分析：
            要素1：对象userService
            要素2：login方法名
            要素3：实参列表
            要素4：返回值
         */
        boolean loginSuccess = userService.login("admin","123");
        //System.out.println(loginSuccess);
        System.out.println(loginSuccess ? "登录成功" : "登录失败");

        // 使用反射机制来调用一个对象的方法该怎么做？
        Class userServiceClass = Class.forName("com.bjpowernode.java.service.UserService");
        // 创建对象
        Object obj = userServiceClass.newInstance();
        // 获取Method
        Method loginMethod = userServiceClass.getDeclaredMethod("login", String.class, String.class);
        //Method loginMethod = userServiceClass.getDeclaredMethod("login", int.class);
        // 调用方法
        // 调用方法有几个要素？ 也需要4要素。
        // 反射机制中最最最最最重要的一个方法，必须记住。
        /*
        四要素：
        loginMethod方法
        obj对象
        "admin","123" 实参
        retValue 返回值
         */
        Object retValue = loginMethod.invoke(obj, "admin","123123");
        System.out.println(retValue);
    }
}

```

### 16.65 反射Constructor

```java
package com.bjpowernode.java.reflect;

import java.lang.reflect.Constructor;
import java.lang.reflect.Modifier;

/*
反编译一个类的Constructor构造方法。
 */
public class ReflectTest11 {
    public static void main(String[] args) throws Exception{
        StringBuilder s = new StringBuilder();
        Class vipClass = Class.forName("java.lang.String");
        s.append(Modifier.toString(vipClass.getModifiers()));
        s.append(" class ");
        s.append(vipClass.getSimpleName());
        s.append("{\n");

        // 拼接构造方法
        Constructor[] constructors = vipClass.getDeclaredConstructors();
        for(Constructor constructor : constructors){
            //public Vip(int no, String name, String birth, boolean sex) {
            s.append("\t");
            s.append(Modifier.toString(constructor.getModifiers()));
            s.append(" ");
            s.append(vipClass.getSimpleName());
            s.append("(");
            // 拼接参数
            Class[] parameterTypes = constructor.getParameterTypes();
            for(Class parameterType : parameterTypes){
                s.append(parameterType.getSimpleName());
                s.append(",");
            }
            // 删除最后下标位置上的字符
            if(parameterTypes.length > 0){
                s.deleteCharAt(s.length() - 1);
            }
            s.append("){}\n");
        }

        s.append("}");
        System.out.println(s);
    }
}

```

### 16.66 反射机制调用构造方法

```java
package com.bjpowernode.java.reflect;

import com.bjpowernode.java.bean.Vip;

import java.lang.reflect.Constructor;

/*
比上一个例子(ReflectTest11)重要一些！！！

通过反射机制调用构造方法实例化java对象。（这个不是重点）
 */
public class ReflectTest12 {
    public static void main(String[] args) throws Exception{
        // 不使用反射机制怎么创建对象
        Vip v1 = new Vip();
        Vip v2 = new Vip(110, "zhangsan", "2001-10-11", true);

        // 使用反射机制怎么创建对象呢？
        Class c = Class.forName("com.bjpowernode.java.bean.Vip");
        // 调用无参数构造方法
        Object obj = c.newInstance();
        System.out.println(obj);

        // 调用有参数的构造方法怎么办？
        // 第一步：先获取到这个有参数的构造方法
        Constructor con = c.getDeclaredConstructor(int.class, String.class, String.class,boolean.class);
        // 第二步：调用构造方法new对象
        Object newObj = con.newInstance(110, "jackson", "1990-10-11", true);
        System.out.println(newObj);

        // 获取无参数构造方法
        Constructor con2 = c.getDeclaredConstructor();
        Object newObj2 = con2.newInstance();
        System.out.println(newObj2);
    }
}

```

### 16.67 获取父类和父类接口

```java
package com.bjpowernode.java.reflect;

/*
重点：给你一个类，怎么获取这个类的父类，已经实现了哪些接口？
 */
public class ReflectTest13 {
    public static void main(String[] args) throws Exception{

        // String举例
        Class stringClass = Class.forName("java.lang.String");

        // 获取String的父类
        Class superClass = stringClass.getSuperclass();
        System.out.println(superClass.getName());

        // 获取String类实现的所有接口（一个类可以实现多个接口。）
        Class[] interfaces = stringClass.getInterfaces();
        for(Class in : interfaces){
            System.out.println(in.getName());
        }
    }
}

package com.bjpowernode.java.bean;

public class Vip {
    int no;
    String name;
    String birth;
    boolean sex;

    public Vip() {
    }

    public Vip(int no) {
        this.no = no;
    }

    public Vip(int no, String name) {
        this.no = no;
        this.name = name;
    }

    public Vip(int no, String name, String birth) {
        this.no = no;
        this.name = name;
        this.birth = birth;
    }

    public Vip(int no, String name, String birth, boolean sex) {
        this.no = no;
        this.name = name;
        this.birth = birth;
        this.sex = sex;
    }

    @Override
    public String toString() {
        return "Vip{" +
                "no=" + no +
                ", name='" + name + '\'' +
                ", birth='" + birth + '\'' +
                ", sex=" + sex +
                '}';
    }
}

```

### 16.68 注解的使用和Override注解

``` java
3、注解

	3.1、注解，或者叫做注释类型，英文单词是：Annotation
		疑问：注解到底是干啥的？？？？？？？？？

	3.2、注解Annotation是一种引用数据类型。编译之后也是生成xxx.class文件。

	3.3、怎么自定义注解呢？语法格式？

		 [修饰符列表] @interface 注解类型名{

		 }
	
	3.4、注解怎么使用，用在什么地方？

		第一：注解使用时的语法格式是：
			@注解类型名
		
		第二：注解可以出现在类上、属性上、方法上、变量上等....
		注解还可以出现在注解类型上。
	
	3.5、JDK内置了哪些注解呢？

		java.lang包下的注释类型：

			掌握：
			Deprecated 用 @Deprecated 注释的程序元素，
			不鼓励程序员使用这样的元素，通常是因为它很危险或存在更好的选择。 

			掌握：
			Override 表示一个方法声明打算重写超类中的另一个方法声明。 

			不用掌握：
			SuppressWarnings 指示应该在注释元素（以及包含在该注释元素中的
			所有程序元素）中取消显示指定的编译器警告。 

package com.bjpowernode.java.annotation;

// 默认情况下，注解可以出现在任意位置。

@MyAnnotation
public class AnnotationTest01 {

    @MyAnnotation
    private int no;

    @MyAnnotation
    public AnnotationTest01(){}

    @MyAnnotation
    public static void m1(){
        @MyAnnotation
        int i = 100;
    }

    @MyAnnotation
    public void m2(@MyAnnotation
                   String name,
                   @MyAnnotation
                   int k){

    }
}

@MyAnnotation
interface MyInterface {

}

@MyAnnotation
enum Season {
    SPRING,SUMMER,AUTUMN,WINTER
}

package com.bjpowernode.java.annotation;

/*
关于JDK lang包下的Override注解
源代码：
public @interface Override {
}

标识性注解，给编译器做参考的。
编译器看到方法上有这个注解的时候，编译器会自动检查该方法是否重写了父类的方法。
如果没有重写，报错。

这个注解只是在编译阶段起作用，和运行期无关！

 */

// @Override这个注解只能注解方法。
// @Override这个注解是给编译器参考的，和运行阶段没有关系。
// 凡是java中的方法带有这个注解的，编译器都会进行编译检查，如果这个方法不是重写父类的方法，编译器报错。

//@Override
public class AnnotationTest02 {

    //@Override
    private int no;

    @Override
    public String toString() {
        return "toString";
    }

}


```

### 16.69 元注解

```java
3.6、元注解
		什么是元注解？
			用来标注“注解类型”的“注解”，称为元注解。

		常见的元注解有哪些？
			Target
			Retention
		
		关于Target注解：
			这是一个元注解，用来标注“注解类型”的“注解”
			这个Target注解用来标注“被标注的注解”可以出现在哪些位置上。

			@Target(ElementType.METHOD)：表示“被标注的注解”只能出现在方法上。
			@Target(value={CONSTRUCTOR, FIELD, LOCAL_VARIABLE, METHOD, PACKAGE, MODULE, PARAMETER, TYPE})
				表示该注解可以出现在：
					构造方法上
					字段上
					局部变量上
					方法上
					....
					类上...
		
		关于Retention注解：
			这是一个元注解，用来标注“注解类型”的“注解”
			这个Retention注解用来标注“被标注的注解”最终保存在哪里。

			@Retention(RetentionPolicy.SOURCE)：表示该注解只被保留在java源文件中。
			@Retention(RetentionPolicy.CLASS)：表示该注解被保存在class文件中。
			@Retention(RetentionPolicy.RUNTIME)：表示该注解被保存在class文件中，并且可以被反射机制所读取。
		
package com.bjpowernode.java.annotation;

/*
自定义注解：MyAnnotation
 */
public @interface MyAnnotation {
    // ??????
}

package com.bjpowernode.java.annotation;

// 注解修饰注解。
@MyAnnotation
public @interface OtherAnnotation {
}

```

### 16.70 Deprecated注解

```java
package com.bjpowernode.java.annotation;

// 表示这个类已过时。
@Deprecated
public class AnnotationTest03 {

    @Deprecated
    private String s;

    public static void main(String[] args) {
        AnnotationTest03 at = new AnnotationTest03();
        at.doSome();
    }

    @Deprecated
    public void doSome(){
        System.out.println("do something!");
    }

    // Deprecated这个注解标注的元素已过时。
    // 这个注解主要是向其它程序员传达一个信息，告知已过时，有更好的解决方案存在。
    @Deprecated
    public static void doOther(){
        System.out.println("do other...");
    }
}

class T {
    public static void main(String[] args) {
        AnnotationTest03 at = new AnnotationTest03();
        at.doSome();

        AnnotationTest03.doOther();

        try {
            Class c = Class.forName("java.util.Date");
            Object obj = c.newInstance();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}

```

### 16.71 注解中定义属性

``` java
package com.bjpowernode.java.annotation2;

public @interface MyAnnotation {

    /**
     * 我们通常在注解当中可以定义属性，以下这个是MyAnnotation的name属性。
     * 看着像1个方法，但实际上我们称之为属性name。
     * @return
     */
    String name();

    /*
    颜色属性
     */
    String color();

    /*
    年龄属性
     */
    int age() default 25; //属性指定默认值

}

package com.bjpowernode.java.annotation2;

public class MyAnnotationTest {

    // 报错的原因：如果一个注解当中有属性，那么必须给属性赋值。（除非该属性使用default指定了默认值。）
    /*@MyAnnotation
    public void doSome(){

    }*/

    //@MyAnnotation(属性名=属性值,属性名=属性值,属性名=属性值)
    //指定name属性的值就好了。
    @MyAnnotation(name = "zhangsan", color = "红色")
    public void doSome(){

    }

}
```

### 16.72 属性是value时可以省略和value的省略

```java
package com.bjpowernode.java.annotation3;

public @interface MyAnnotation {

    /*
    指定一个value属性。
     */
    String value();

    //String email();
}

package com.bjpowernode.java.annotation3;

/*
如果一个注解的属性的名字是value，并且只有一个属性的话，在使用的时候，该属性名可以省略。
 */
public class MyAnnotationTest {

    // 报错原因：没有指定属性的值。
    /*@MyAnnotation
    public void doSome(){

    }*/

    @MyAnnotation(value = "hehe")
    public void doSome(){

    }

    @MyAnnotation("haha")
    public void doOther(){

    }
}

package com.bjpowernode.java.annotation3;

public @interface OtherAnnotation {
    String name();
}

package com.bjpowernode.java.annotation3;

// 报错了。因为属性名是name，不能省略。
//@OtherAnnotation("test")
public class OtherAnnotationTest {

    // 正确的。
    @OtherAnnotation(name = "test")
    public void doSome(){

    }
}

```

### 16.73 属性是一个数组

``` java
package com.bjpowernode.java.annotation4;

public @interface MyAnnotation {
    /*
    注解当中的属性可以是哪一种类型？
        属性的类型可以是：
            byte short int long float double boolean char String Class 枚举类型
            以及以上每一种的数组形式。
     */
    int value1();

    String value2();

    int[] value3();

    String[] value4();

    Season value5();

    Season[] value6();

    Class parameterType();

    Class[] parameterTypes();
}

package com.bjpowernode.java.annotation4;

public @interface OtherAnnotation {
    /*
    年龄属性
     */
    int age();

    /*
    邮箱地址属性，支持多个
     */
    String[] email();

    /**
     * 季节数组，Season是枚举类型
     * @return
     */
    Season[] seasonArray();
}

package com.bjpowernode.java.annotation4;


public class OtherAnnotationTest {

    // 数组是大括号
    @OtherAnnotation(age = 25, email = {"zhangsan@123.com", "zhangsan@sohu.com"}, seasonArray = Season.WINTER)
    public void doSome(){

    }

    // 如果数组中只有1个元素：大括号可以省略。
    @OtherAnnotation(age = 25, email = "zhangsan@123.com", seasonArray = {Season.SPRING, Season.SUMMER})
    public void doOther(){

    }

}
package com.bjpowernode.java.annotation4;

public enum Season {
    SPRING,SUMMER,AUTUMN,WINTER
}

```

### 16.74 反射注解

``` java
package com.bjpowernode.java.annotation5;

import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;

//只允许该注解可以标注类、方法
@Target({ElementType.TYPE, ElementType.METHOD})
// 希望这个注解可以被反射
@Retention(RetentionPolicy.RUNTIME)
public @interface MyAnnotation {

    /*
    value属性。
     */
    String value() default "北京大兴区";
}

package com.bjpowernode.java.annotation5;

@MyAnnotation("上海浦东区")
public class MyAnnotationTest {

    //@MyAnnotation
    int i;

    //@MyAnnotation
    public MyAnnotationTest(){

    }

    @MyAnnotation
    public void doSome(){

        //@MyAnnotation
        int i;
    }

}

package com.bjpowernode.java.annotation5;

public class ReflectAnnotationTest {
    public static void main(String[] args) throws Exception{
        // 获取这个类
        Class c = Class.forName("com.bjpowernode.java.annotation5.MyAnnotationTest");
        // 判断类上面是否有@MyAnnotation
        //System.out.println(c.isAnnotationPresent(MyAnnotation.class)); // true
        if(c.isAnnotationPresent(MyAnnotation.class)){
            // 获取该注解对象
            MyAnnotation myAnnotation = (MyAnnotation)c.getAnnotation(MyAnnotation.class);
            //System.out.println("类上面的注解对象" + myAnnotation); // @com.bjpowernode.java.annotation5.MyAnnotation()
            // 获取注解对象的属性怎么办？和调接口没区别。
            String value = myAnnotation.value();
            System.out.println(value);
        }

        // 判断String类上面是否存在这个注解
        Class stringClass = Class.forName("java.lang.String");
        System.out.println(stringClass.isAnnotationPresent(MyAnnotation.class)); // false
    }
}

```

### 16.75 通过反射获取注解对象属性值

```java
package com.bjpowernode.java.annotation6;

import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;

@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface MyAnnotation {

    /*
    username属性
     */
    String username();

    /*
    password属性
     */
    String password();
}

package com.bjpowernode.java.annotation6;

import java.lang.reflect.Method;

public class MyAnnotationTest {

    @MyAnnotation(username = "admin", password = "456456")
    public void doSome(){

    }

    public static void main(String[] args) throws Exception{
        // 获取MyAnnotationTest的doSome()方法上面的注解信息。
        Class c = Class.forName("com.bjpowernode.java.annotation6.MyAnnotationTest");
        // 获取doSome()方法
        Method doSomeMethod = c.getDeclaredMethod("doSome");
        // 判断该方法上是否存在这个注解
        if(doSomeMethod.isAnnotationPresent(MyAnnotation.class)) {
            MyAnnotation myAnnotation = doSomeMethod.getAnnotation(MyAnnotation.class);
            System.out.println(myAnnotation.username());
            System.out.println(myAnnotation.password());
        }
    }

}

package com.bjpowernode.java.annotation7;

/*
自定义异常
 */
public class HasNotIdPropertyException extends RuntimeException {
    public HasNotIdPropertyException(){

    }
    public HasNotIdPropertyException(String s){
        super(s);
    }
}

package com.bjpowernode.java.annotation7;

import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;

// 表示这个注解只能出现在类上面
@Target(ElementType.TYPE)
// 该注解可以被反射机制读取到
@Retention(RetentionPolicy.RUNTIME)
public @interface MustHasIdPropertyAnnotation {

}

// 这个注解@Id用来标注类，被标注的类中必须有一个int类型的id属性，没有就报异常。

package com.bjpowernode.java.annotation7;

import java.lang.reflect.Field;

public class Test {
    public static void main(String[] args) throws Exception{
        // 获取类
        Class userClass = Class.forName("com.bjpowernode.java.annotation7.User");
        // 判断类上是否存在Id注解
        if(userClass.isAnnotationPresent(MustHasIdPropertyAnnotation.class)){
            // 当一个类上面有@MustHasIdPropertyAnnotation注解的时候，要求类中必须存在int类型的id属性
            // 如果没有int类型的id属性则报异常。
            // 获取类的属性
            Field[] fields = userClass.getDeclaredFields();
            boolean isOk = false; // 给一个默认的标记
            for(Field field : fields){
                if("id".equals(field.getName()) && "int".equals(field.getType().getSimpleName())){
                    // 表示这个类是合法的类。有@Id注解，则这个类中必须有int类型的id
                    isOk = true; // 表示合法
                    break;
                }
            }

            // 判断是否合法
            if(!isOk){
                throw new HasNotIdPropertyException("被@MustHasIdPropertyAnnotation注解标注的类中必须要有一个int类型的id属性！");
            }

        }
    }
}

package com.bjpowernode.java.annotation7;

@MustHasIdPropertyAnnotation
public class User {
    int id;
    String name;
    String password;
}

```

### 16.76 注解在开发中的作用

```java

	3.8、Target的源代码
		

	3.9、注解在开发中有什么用呢？

		需求：
			假设有这样一个注解，叫做：@Id
			这个注解只能出现在类上面，当这个类上有这个注解的时候，
			要求这个类中必须有一个int类型的id属性。如果没有这个属性
			就报异常。如果有这个属性则正常执行！

```



