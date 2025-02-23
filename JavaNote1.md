##### 数据类型

###### 基本数据类型

基本数据类型只有8种，可按照如下分类
①整数类型：`long、int、short、byte`
②浮点类型：`float、double`
③字符类型：`char`
④布尔类型：`boolean`

###### 引用类型

引用数据类型非常多，大致包括：类、 接口类型、 数组类型、 枚举类型、 注解类型、 字符串型
例如，String类型就是引用类型，还有Double，Byte,Long,Float,Char,Boolean,Short（注意这里和基本类型相比首字母是大写）
简单来说，所有的非基本数据类型都是引用数据类型

##### Java 方法重载(Overload)

Java 允许同一个类中定义多个**同名方法**，只要它们的**形参列表不同**即可。如果同一个类中包含了两个或两个以上方法名相同的方法，但形参列表不同(**形参的个数、类型、顺序至少一个不同和参数名无关**)且对返回类型无要求，这种情况被称为方法重载（overload）。

判断两、三个数最大(小)值：三元运算 例如：a>b?a:b

低精度类型可以自动转化为高精度类型

##### 可变参数(VariableParameter)：

同一个类中**多个同名 同功能** 但**参数个数不同**的方法，分装成一个方法

基本语法：访问修饰符 返回类型 方法名(数据类型... 形参名){

} 

例如：public void VarParameter(double... nums){

} 

double...  表示接受的是可变参数，类型是double 即可以接受多个double（0-多）

使用可变参数时 可以当做数组使用 即 nums 可以当做数组

细节：可变参数的实参可以为数组

可变参数可以和普通类型的参数一起放在形参列表中 但必须保证**可变参数在最后** 

一个形参列表中只能出现一个可变参数 

##### 作用域(scope):

在java编程中 主要的变量就是成员变量(属性)和局部变量

局部变量一般指在成员方法中定义的变量

java中作用域的分类：

    全局变量：也就是属性 作用域为整个类体

        属性在定义时可以直接赋值

    局部变量：也就是除属性之外的其他变量 作用域为定于它的代码块中

**全局变量（属性）可以不赋值** 因为它有默认值 **局部变量必须赋值**后才能使用 应为它没有默认值。具体说: int 0，short 0, byte 0, long 0, float 0.0,double 0.0，char \u0000，
boolean false，String null

属性和局部变量可以重名 访问时遵守就近原则 

在同一个作用域中 比如在同一个成员方法中 两个局部变量 不能重名

属性生命周期较长，伴随着对象的创建而创建 伴随着对象销毁而销毁。局部变量 生命周期较短 伴随着他的代码块的执行而创建 伴随着代码块的结束而销毁 即在一次方法调用过程中。

作用域范围不同 ：

    全局变量/属性：可以被本类使用 或者其他类使用(通过对象调用)

例如：public void test() {
            Person p1 = new Person();
            System.out.println(p1.name);//jack
           }
           }
            class Person {
                String name;

            }

或者：

            public void test2(Person p) {
            System.out.println(p.name);//jack
            }

            class Person {
                String name;

            }

    局部变量：只能在本类中对应的方法中使用

修饰符不同：

全局变量/属性可以加修饰符

局部变量不可以加修饰符

##### 构造方法/构造器(constructor)

基本语法：

[修饰符] 方法名(形参列表){

    方法体

}

说明：

构造器的修饰符可以默认 也可以是public protected private 

构造器没有返回值

**方法名 和类名必须一样**

参数列表和成员方法规则一样

构造器的调用是由系统完成

构造器是 类的一种特殊的方法 他的主要作用是完成对**新对象的初始化**，有以下几个特点：

方法名和类名相同    

没有返回值     

在创建对象时系统会自动的调用改类的构造器完成对对象的初始化

注意和细节：

一个类可以定义多个不同的构造器 即构造器重载

如果程序员没有定义构造器 系统会自动给类生成一个默认无参构造器(也叫默认构造方法/器) 例如：Pig(){}

一旦定义了自己的构造器 默认的构造器就被覆盖 就不能在使用默认的无参构造器 除非显式定义一下，即Pig(){} 

##### 对象创建的流程分析：

案例：

class Person{

 int age = 90;

 String name;

 Person (String n,int a){ 

  name = n;

  age = a;

 }

}

Person p = new Person("小钱",20);

流程分析

1.加载Person类信息(Person.class)，只会加载一次

2.在堆中分配对象空间(地址)

3.完成对象初始化：先 默认初始化 age = 0，name = null  再进行显式初始化 age = 90，name = null  最后 构造初始化 age = 20， name = 小钱

4.把对象在堆中的地址返回给 p (p是对象名 也可以理解成对象的引用)

##### this：

java虚拟机会给每个对象分配this 代表当前对象

哪个对象调用 this 就代表哪个对象

注意事项和使用细节：

1.this关键字可以 用来访问本类的属性 方法 构造器

2.this用于区分当前类的属性和局部变量

3.访问成员方法的语法  this.方法名(形参列表)；

4.访问构造器语法  this(形参列表)； 注意 只能在构造器中使用，只能在构造器中访问另外一个构造器  注意：如果有this访问构造器的语法，该语句必须放在第一条

5.this不能在类定义的外部使用 只能在类定义的方法中使用 

匿名对象： 例如 new Test()  匿名对象使用一次后就不能再使用

new Test().count1() 创建好匿名对象后 就调用 count1()

Tips:

后++： 先赋值 再自增  前++： 先自增 再赋值

Arrays.sort()   系统提供的 Arrays 完成数组排序

##### 包：

注意事项和细节：

package 的作用是声明当前类所在的包  需要放在类的最上面  一个类最多有一句package

import 指令 位置放在package的下面， 在类定义前面，可以有多句且没有顺序要求

##### 访问修饰符：

java四种访问控制修饰符(modifier)，用于控制方法和属性(成员变量)的访问权限(范围)：

公开级别：public 对外公开

受保护级别：protected 对子类和同一个包中的类公开

默认级别：无访问修饰符  对同一个包的类公开

私有级别： private 只有类本身可以访问，不对外公开

<img title="" src="file:///C:/Users/Pretender/AppData/Roaming/marktext/images/2022-09-21-19-25-25-image.png" alt="" data-align="inline">

使用注意事项：

修饰符可以修饰类中的属性 成员方法以及类

只有默认的和public才能修饰类，并且遵循以上访问权限的特点

成员方法的访问规则和属性完全一样

##### 封装(encapsulation)：

把抽象出来的属性和方法封装在一起，数据被保护在内部，程序的其他部分只有通过被授权的方法才能对数据进行操作

封装的理解和好处：

隐藏实现细节 方法

可以对数据进行验证 保证安全合理

封装的实现步骤：

(1)将属性进行私有化private

(2)提供一个公有的public  set 方法用于对属性判断并赋值

例： public void setXxx(类型 参数名){

    //加入数据验证的业务逻辑

    属性 = 参数名；

}

(3) 提供一个公共的get方法用于获取属性的值

例：public XX getXxx(){

return xx;    

} 

##### 继承(extends)：

类的继承格式

class 父类 {

 }

 class 子类 extends 父类 {

 }

继承的细节：

1.子类继承了所有的属性和方法，非私有的属性和方法可以在子类直接访问, 但是私有属性和方法不能在子类直接访 问，要通过父类提供公共的方法去访问

2.子类必须调用父类的构造器，完成父类的初始化( super() 默认调用父类的无参构造器 )。

3.当创建子类对象时，不管使用子类的哪个构造器，默认情况下总会去调用父类的无参构造器，如果父类没有提供无参构造器，则必须在子类的构造器中用 super 去指定使用父类的哪个构造器完成对父类的初始化工作，否则，编译不会通过。

4.如果希望指定去调用父类的某个构造器，则显示的调用一下：super(形参列表)

5.super在使用时，必须放在构造器的第一行(只能在构造器中使用)

6.super() 和 this() 都只能放在构造器第一行，因此这两个方法不能共存在同一个构造器

7.java所有类都是Object类的子类，Object是所有类的基类

8.父类构造器的调用不限于直接父类，将一直往上追溯知道Object类(顶级父类)。

9.子类最多只能继承一个父类(指直接继承)，即java中是单继承机制，思考：如何让A类继承B类和C类。【 implements】

10.不能滥用继承，子类和父类之间必须满足is-a的逻辑关系

(继承提高了类之间的耦合性（继承的缺点，耦合度高就会造成代码之间的联系越紧密，代码独立性越差）)。

###### 继承的本质(Theory)分析：

方法调用规则

// 要按照查找关系来返回信息
//(1) 首先看子类是否有该属性
//(2) 如果子类有这个属性，并且可以访问，则返回信息
//(3) 如果子类没有这个属性，就看父类有没有这个属性(如果父类有该属性，并且可以访问，就返回信息..)
//(4) 如果父类没有就按照(3)的规则，继续找上级父类，直到 Object...

##### super：

super代表父类的引用，用于访问父类的属性、方法、构造器

1.访问父类的属性，但不能访问父类的private属性

super.属性名

2.访问父类的方法，但不能访问父类的private方法

super.方法名(参数列表)；

3.访问父类的构造器，只能放在构造器的第一句，且只能出现一句

super(参数列表);

super细节：

1.调用父类的构造器的好处:分工明确，父类属性由父类初始化，子类属性由子类初始化

2.当子类中有与和父类中的成员(属性和方法)重名时，为了访问父类的成员，必须通过super。如果没有重名，使用super、this、直接访问是一样的效果。

3.super的访问不限于直接父类，如果爷爷类和本类中有同名成员，也可以使用super去访问爷爷类的成员；如果多个基类(上级类 )中都有同名的成员，使用super访问遵循就近原则，当然也需要遵守访问权限的相关规则。

###### super和this的比较：

<img title="" src="file:///C:/Users/Pretender/AppData/Roaming/marktext/images/2022-09-28-16-08-36-image.png" alt="" data-align="inline">

![image-20240219001941769](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240219001941769.png)

##### 方法重写/覆盖(override):

方法覆盖就是子类有一个方法 和父类的某个方法的名称、返回类型、参数一样，那么这个子类的方法覆盖了父类的方法。

注意事项和使用细节：

 方法重写也叫方法覆盖，需要满足以下条件：

1.子类的方法参数、方法名称，要和父类方法的参数，方法名称完全一样

2.子类方法的返回类型和父类方法返回类型一样，或者是父类返回类型的子类，比如 父类 返回类型是object 子类方法返回类型是String(返回类型与被重写方法的返回类型可以不相同，但是必须是父类返回值的派生类)

3.子类方法不能缩小父类方法的访问权限。(子类访问权限>=父类访问权限)

<img title="" src="file:///C:/Users/Pretender/AppData/Roaming/marktext/images/2022-09-29-22-32-33-image.png" alt="" data-align="inline" width="729">

##### 多态(polymorphic)：

方法或对象具有多种形态，是面向对象的第三大特征，多态是建立在封装和继承基础之上的。

具体的体现：

1.方法的多态

    重写和重载就体现多态

2.对象的多态

(1)一个对象的编译类型和运行类型可以不一致

(2)编译类型在定义对象时，就确定了不能改变

(3)运行类型是可以变化的

(4)编译类型看定义时 = 号 的左边， 运行类型看 = 号的右边

多态细节：

多态的前提是：两个对象(类)存在继承关系

**多态的向上转型**：

本质：**父类的引用指向子类的对象**

语法：父类类型 引用名  = new 子类类型();

特点：**编译类型看左边，运行类型看右边。**

可以调用父类中的所有成员(遵守访问权限)

不能调用子类中的特有成员

运行最终效果看子类的具体实现即调用方法时，按照从子类(运行类型)开始查找方法，然后调用，规则和前面讲的方法调用规则一致。

**多态的向下转型**：

若需要调用子类特有的方法，则需要 将父类对象再还原为子类对象

语法：子类类型 引用名 = (子类类型) 父类引用；

只能强转父类的引用，不能强转父类的对象

要求父类的引用必须指向的是当前目标类型的对象

当向下转型后可以调用子类类型中所有成员  

属性没有重写之说，属性的值看编译类型  

**instanceof** 比较操作符，用于判断对象的类型是否为xx类型或xx类型的子类型。  



属性看编译类型  方法看运行类型

###### 动态绑定(dynamicbinding)机制：

当调用对象方法的时候，该方法会和该对象的内存地址/运行类型绑定。

当调用对象属性时，没有动态绑定机制，哪里声明，哪里使用。

###### 多态的应用：

多态数组：

数组的定义类型为父类类型，里面保存的实际元素类型为子类类型.

多态参数(parameter)：

方法定义的形参类型为父类类型，实参类型允许为子类类型

##### Object类详解：

equal方法：

###### ==和equals的对比：

==是一个比较运算符

1.== 既可以判断基本类型，又可以判断引用类型

2.== 如果判断基本类型，则判断的是值是否相等。例如：int i = 10；double d = 10.0；

3.== 如果判断引用类型，判断的是地址是否相等，即判定是不是同一个对象

equals: 是object类中的方法，只能判断引用类型

默认判断的是地址是否相等，子类中往往重写该方法，用于判断内容是否相等。

(xx).equals(xxx)

![image-20240218175339656](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240218175339656.png)

###### 查看JDK源码：

//equals 方法 源码查看 ctrl + B 或 ctrl  + 左键  
"hello".equals("abd"); 
//Object类的 equals： 
Object 的 equals  方法默认 就是比较对象地址是否相同 
也就是判断两个对象是否为同一个对象 
public boolean equals(Object obj) { 
    return (this == obj);}  

———————————————————————————

//Integer的 equals方法

从源码中可以看到 Integer 也重写了 equals方法 
变成了判断两个值是否相等 
public boolean equals(Object obj) { 
  if (obj instanceof Integer) {    

    return value == ((Integer)obj).intValue();  

} 

return false; 

———————————————————————————

String 的 equals 方法：

把Object的equals方法重写 变成了比较两个字符串值是否相同

###### ASCLL码对照表：

<img src="C:\Users\Pretender\OneDrive\桌面\JavaNote1.assets\2022-10-09-17-28-36-image.png" title="" alt="" data-align="inline">

###### hashCode:

返回该对象的哈希码值，支持此方法是为了提高哈希表值的性能。

6个小结：

![](C:\Users\Pretender\AppData\Roaming\marktext\images\2022-10-09-22-53-17-image.png)

###### toString：

![image-20240202001438408](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240202001438408.png)

![image-20240202001455943](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240202001455943.png)

基本介绍：全类名+@+哈希值的十六进制（全类名：包名加类名）

Object 的toString源码 
1.getClass().getName()类的全类名(包名+类名) 
2.Integer.toHexString(hashCode() 将对象的哈希值转化为16进制字符串 
public String toString() { 
    return getClass().getName() + "@" + Integer.toHexString(hashCode());

}

子类往往重写toString方法 用于返回对象的属性信息

重写toString方法 打印对象或拼接对象时 都会自动调用该对象的toString形式。

###### finalize：

![](C:\Users\Pretender\AppData\Roaming\marktext\images\2022-10-10-14-27-31-image.png)

##### 断点调试：

![](C:\Users\Pretender\AppData\Roaming\marktext\images\2022-10-11-16-07-01-image.png)

##### 类变量(静态变量)和类方法

###### **类变量**，可以通过类名来访问

静态变量被所在类的对象共享 不论它在堆还是方法区 都不影响使用

static类变量在类加载的时候就生成了

**什么是类变量：**

类变量也叫静态变量/静态属性，是该类的所有对象共享的变量,任何一个该类的对象去访问它时,取到的都是相同的值,同样任何一个该类的对象去修改它时,修改的也是同一个变量。这个从前面的图也可看出来。

**定义类变量：**

访问修饰符 static 数据类型 变量名；[推荐]

static 访问修饰符 数据类型 变量名；

**访问类变量：**

类名.类变量名 或 对象名.类变量名

注：静态变量的访问修饰符的访问权限和范围 和 普通属性是一样的 推荐使用前者

**细节：**

1.什么时候需要用类变量
当我们需要让某个类的所有对象都共享一个变量时，就可以考虑使用类变量(静态变量):比如:

​	定义学生类，统计所有学生共交多少钱。Student (name, static fee)

2.类变量与实例变量(普通属性)区别
类变量是该类的所有对象共享的,而实例变量是每个对象独享的。

3.加上static称为类变量或静态变量，否则称为实例变量/普通变量/非静态变量
4.类变量可以通过类名.类变量名或者对象名.类变量名来访问，但java设计者推荐我们使用类名.类变量名方式访问。【前提是满足访问修饰符的访问权限和范围】

5.实例变量(普通变量)不能通过类名.类变量名方式访问。
6.类变量是在类加载时就初始化了，也就是说，即使你没有创建对象，只要类加载了,就可以使用类变量了。
7.类变量的生命周期是随类的加载开始,随着类消亡而销毁。

###### **类方法(静态方法):**

**形式**如下：

访问修饰符 static 数据返回类型 方法名(){ }；[推荐]

static 访问修饰符 数据返回类型 方法名(){ }；

**类方法的调用：**

类名.类方法名 或 对象名.类方法名【前提是满足访问修饰符的访问权限和范围】

**类方法的使用场景：**

当方法不涉及到任何和对象相关的成员 则可以将方法设计为静态方法 提高效率

如果我们希望不创建实例，也可以调用某个方法(即当做工具来使用)，这时，把方法做成静态方法时非常合适

比如工具类中的utils方法 Math类 Arrays类 Collections集合类等

在实际开发中 往往会将一些通用的方法 设计成静态方法 这样我们就不需要创建对象就可以使用了 比如打印一组数组 冒泡排序或完成某个计算任务等

**类方法的使用细节：**

1)类方法和普通方法都是随着类的加载而加载，将结构信息存储在方法区∶类方法中无this的参数
普通方法中隐含着this的参数
2)类方法可以通过类名调用，也可以通过对象名调用。
3)普通方法和对象有关，需要通过对象名调用，比如对象名.方法名(参数)，不能通过类名调用。

4)类方法中不允许使用和对象有关的关键字，比如this和super。普通方法(成员方法)可以
5)类方法(静态方法)中只能访问静态变量或静态方法。【如何理解】

6)普通成员方法,既可以访问非静态成员，也可以访问静态成员。
小结:静态方法，只能访问静态的成员，非静态的方法，可以访问静态成员和非静态成员(**必须遵守访问权限**)

ps:由加载时间决定，对象创建前会先加载类，即静态成员加载之前普通成员还没有被加载，所以静态成员不能调用普通成员，反过来却可以

##### main 方法语法

![image-20240222002252547](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240222002252547.png)



**特别提示：**

1.在main()方法中，我们可以直接调用main 方法所在类的静态方法或静态属性。 

2.但是，不能直接访问该类中的非静态成员，必须创建该类的一个实例对象后，才能通过这个对象去访问类中的非静 态成员，[举例说明] Main01.java

##### 代码块

代码块又称为初始化块 属于类中的成员 类似于方法 将逻辑语句封装在方法体中,通过{ }包围起来。
但和方法不同，没有方法名，没有返回，没有参数，只有方法体，而且不用通过对象或类显式调用,而是加载类时,或创建对象时隐式调用。

**基本语法**

![image-20240222163727342](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240222163727342.png)

**好处**

![image-20240222163835425](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240222163835425.png)



我们可以把相同的语句，放入到一个代码块中，即可  这样当我们不管调用哪个构造器，创建对象，都会先调用代码块的内容   代码块调用的顺序优先于构造器..



**细节：**

<img src="C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240222165000891.png" alt="image-20240222165000891" style="zoom:80%;" />



<img src="C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240222174516290.png" alt="image-20240222174516290" style="zoom:80%;" />

<img src="C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240222180428730.png" alt="image-20240222180428730" style="zoom:80%;" />



<img src="C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240222181826066.png" alt="image-20240222181826066" style="zoom:80%;" />



##### 单例设计模式：

单例(单个的实例) 
1.所谓类的单例设计模式，就是采取一定的方法保证在整个的软件系统中，**对某个类只能存在一个对象实例，并且该类只提供一个取得其对象实例**的方法
2.单例模式有两种方式:1)饿汉式2)懒汉式

###### **饿汉式：**

是立即加载的方式，无论是否会用到这个对象，都会加载

饿汉式单例实现步骤如下：

1)构造器私有化=》防止直接new

2)类的内部创建对象(为了能在下面静态方法中返回对象需要将其修饰为static)
3)向外暴露一个**静态的公共方法**。getlnstance
4)代码实现 SingleTon01 .java 

![image-20240406001752395](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240406001752395.png)

###### **懒汉式：**

是延迟加载的方式，只有使用的时候才会加载。 并且有*线程安全*的考量

步骤如下：

1、仍然将构造器私有化

2、定义一个static静态属性对象

3、提供一个public的static方法 可以返回一个对象

4、懒汉式 只有当用户使用getInstance方法时 才会返回cat对象 后面再次调用时 会返回上次创建cat对象 从而保证了单例

![image-20240222234230776](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240222234230776.png)

[Single Ton02.java]

**小结：**

1．二者最主要的区别在于创建对象的时机不同:饿汉式是在类加载就创建了对象实例, 而懒汉式是在使用时才创建。
2．饿汉式不存在线程安全问题，懒汉式存在线程安全问题。(后面学习线程后，会完善)
3．饿汉式存在浪费资源的可能。因为如果程序员一个对象实例都没有使用，那么饿汉式创建的对象就浪费了，懒汉式是使用时才创建，就不存在这个问题。
4.在我们javaSE标准类中，java.lang.Runtime就是经典的单例模式。

##### final

final可以修饰类、属性、方法和局部变量

在以下情况下，会使用到final

1)当不希望类被继承时,可以用final修饰.【案例演示】
2)当不希望父类的某个方法被子类覆盖/重写(override)时,可以用final关键字修饰。【案例演示:访问修饰符final返回类型方法名】
3)当不希望类的的某个属性的值被修改,可以用final修饰.【案例演示】
4)当不希望某个局部变量被修改，可以使用final修饰【案例演示 】

**细节：**

1.final修饰的属性又叫常量,一般用XX_XX_XX来命名

2.final修饰的属性在定义时,**必须赋初值**,并且以后**不能再修改**，赋值可以在如
下位置之一【选择一个位置赋初值即可】:
	(1)定义时:如public final double TAX_RATE=0.08;

​	(2)在构造器中
​	(3)在代码块中
3.如果final修饰的属性是静态的，则初始化的位置只能是①定义时②在静态代码块 不能在构造器中赋值。(静态属性在类加载时就已经完成了，而构造器要创建对象实例时才加载，晚于类加载。)

4.final类不能继承，但是可以实例化对象。[A2类]
5.如果类不是final类,但是含有final方法，则该方法虽然不能重写，但是可以被继承。[A3类]

6.一般来说，如果一个类已经是final类了，就没有必要再将方法修饰成final方法。

7.final不能修饰构造方法(即构造器)

8.final和static往往搭配使用，效率更高，不会导致类加载.底层编译器做了优化处理。

​	class Demo{

​		public static final int i = 16;

​		static{

​			System.out.println("aaa");

​		}

​	}

![image-20240224224336307](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240224224336307.png)

9.包装类(Integer,Double,Float,Boolean等都是final),String也是final类,不能被继承。

##### 抽象类

当父类的某些方法,需要声明，但是又不确定如何实现时，可以将其声明为抽象方法,那么这个类就是抽象类

所谓抽象方法就是没有实现的方法 所谓没有实现就是指，没有方法体  

当一个类中存在抽象方法时，需要将该类声明为 abstract 类 

一般来说，抽象类会被继承，有其子类来实现抽象方法.

**抽象类介绍：**

1.用abstract关键字来**修饰一个类时** 这个类就叫抽象类

访问修饰符 abstract 类名{ }

2.用abstract关键字修饰一个方法时 这个方法就是抽象方法

访问修饰符 abstract 返回类型 方法名(参数列表);//没有方法体

3.抽象类的价值更多作用是在于设计 是设计者设计好后 让子类继承并实现抽象类

4.抽象类是常考知识点 在框架和设计模式使用较多

**细节：**

<img src="C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240225182926576.png" alt="image-20240225182926576"  />

<img src="C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240225182950772.png" alt="image-20240225182950772" style="zoom: 67%;" />

<img src="C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240225183049102.png" alt="image-20240225183049102" style="zoom:67%;" />



##### 模版设计模式(抽象类的最佳实践)

![image-20240226002512760](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240226002512760.png)

![image-20240226002525043](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240226002525043.png)



##### 接口：

<img src="C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240227160737253.png" alt="image-20240227160737253" style="zoom:80%;" />

jdk8后 可以有默认实现方法 需要用default关键字修饰 

**细节：**

![image-20240227164600517](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240227164600517.png)

![image-20240227165848521](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240227165848521.png)

###### 抽象类和接口的异同：

相同点

（1）都不能被实例化 （2）接口的实现类或抽象类的子类都只有实现了接口或抽象类中的方法后才能实例化。

不同点

（1）接口只有定义，不能有方法的实现，java 1.8中可以定义default方法体，而抽象类可以有定义与实现，方法可在抽象类中实现。

（2）实现接口的关键字为implements，继承抽象类的关键字为extends。一个类可以实现多个接口，但一个类只能继承一个抽象类。所以，使用接口可以间接地实现多重继承。

（3）接口强调特定功能的实现，而抽象类强调所属关系。

（4）接口成员变量默认为public static final，必须赋初值，不能被修改；其所有的成员方法都是public、abstract的。抽象类中成员变量默认default，可在子类中被重新定义，也可被重新赋值；抽象方法被abstract修饰，不能被private、static、synchronized和native等修饰，必须以分号结尾，不带花括号。



###### 实现和继承：

当子类继承了父类，就自动的拥有父类的功能，如果子类需要扩展，可以通过实现接口的方式扩展。

可以理解为 实现接口 是对Java单继承机制的一种补充。

![image-20240407170356360](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240407170356360.png)

###### 接口的多态特性：

![image-20240407174147213](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240407174147213.png)

##### 内部类：

![image-20240407212543421](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240407212543421.png)

类的五大成员：属性、方法、构造器、代码块、内部类

###### 内部类的分类：

如果定义类在局部位置(方法中/代码块):

​	(1) 局部内部类(有类名) 

​	(2) 匿名内部类(没有类名)

定义在成员位置:

​	(1) 成员内部类(没用static修饰)

​	(2) 静态内部类(使用static修饰)

###### 局部内部类：

![image-20240407213747820](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240407213747820.png)

![image-20240407213725604](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240407213725604.png)

###### 匿名内部类(重点)：

![image-20240408164220041](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240408164220041.png)

![image-20240408182600163](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240408182600163.png)

匿名内部类最佳实践 当做实参直接传递 简洁高效

###### 成员内部类：

![image-20240408230644025](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240408230644025.png)

![image-20240409010034517](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240409010034517.png)

![image-20240408230713062](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240408230713062.png)

###### 静态内部类：

![image-20240409011746035](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240409011746035.png)

![image-20240409012504857](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240409012504857.png)

![image-20240409012540245](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240409012540245.png)

![image-20240409013940587](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240409013940587.png)



##### 枚举：

枚举是一组常量的集合，可以这里理解：枚举属于一种特殊的类，里面只包含一组有限的特定的对象

枚举的二种实现方式： 1) 自定义类实现枚举 2) 使用 enum 关键字实现枚举

![image-20240409170032688](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240409170032688.png)

![image-20240409174840698](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240409174840698.png)

###### enum关键字实现枚举注意事项：

![image-20240409175203314](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240409175203314.png)



###### Enum常用方法：

说明：使用关键字 enum时，会隐式继承 Enum类, 这样我们就可以使用 Enum类相关的方法

![image-20240409222142825](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240409222142825.png)

![image-20240409225019226](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240409225019226.png)

Enum类的compareTo()方法比较同一枚举类型的两个枚举常量。它返回两个枚举常量的序数差。如果两个枚举常量相同，则返回零。

###### enum实现接口:

1.使用 enum关键字后，就不能再继承其它类了，因为 enum会隐式继承 Enum，而 Java 是单继承机制。

2.enum实现的枚举类，仍然是一个类，所以还是可以实现接口的.



##### 注解(Annotation)：

注解(Annotation)也被称为元数据(Metadata)，用于修饰解释 包、类、方法、属性、构造器、局部变量等数据信息

和注释一样，注解不影响程序逻辑，但注解可以被编译或运行，相当于嵌入在代码中的补充信息。

在 JavaSE 中，注解的使用目的比较简单，例如标记过时的功能，忽略警告等。在 JavaEE 中注解占据了更重要的角 色，例如用来配置应用程序的任何切面，代替 java EE 旧版中所遗留的繁冗代码和XML 配置等。



使用 Annotation 时要在其前面增加 @ 符号, 并把该 Annotation 当成一个修饰符使用。用于修饰它支持的程序元素 

###### 三个基本的 Annotation:

@Override: 限定某个方法，是重写父类方法, 该注解只能用于方法 

@Deprecated: 用于表示某个程序元素(类, 方法等)已过时 

@SuppressWarnings: 抑制编译器警告

![image-20240410144828971](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240410144828971.png)

![image-20240410144955235](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240410144955235.png)



![image-20240410145208735](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240410145208735.png)



![image-20240410160616274](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240410160616274.png)

![image-20240410160643987](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240410160643987.png)

![image-20240410160712938](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240410160712938.png)



#####  异常(Exception)

![image-20240411185306717](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240411185306717.png)

![image-20240411224510266](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240411224510266.png)

![image-20240411231235855](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240411231235855.png)

![image-20240411233305145](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240411233305145.png)

###### 常见的运行时异常：

NullPointerException 空指针异常 

ArithmeticException 数学运算异常 

ArrayIndexOutOfBoundsException 数组下标越界异常 

ClassCastException 类型转换异常 

NumberFormatException 数字格式不正确异常[]

###### 空指针异常：

当应用程序试图在需要对象的地方使用 null 时，抛出该异常

###### 数学运算异常：

当出现异常的运算条件时，抛出此异常。例如，一个整数“除以零”时，抛出此类的一个实例。

###### 数组下标越界异常：

用非法索引访问数组时抛出的异常。如果索引为负或大于等于数组大小，则该索引为非法索引

###### 类型转换异常：

当试图将对象强制转换为不是实例的子类时，抛出该异常

###### 数字格式不正确异常：

当应用程序试图将字符串转换成一种数值类型，但该字符串不能转换为适当格式时，抛出该异常 => 使用异常我们 可以确保输入是满足条件数字.

###### 常见的编译时异常：

编译异常是指在编译期间，就必须处理的异常，否则代码不能通过编译

![image-20240411234709700](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240411234709700.png)



###### 异常处理：

![image-20240411235736245](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240411235736245.png)

![image-20240411235801340](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240411235801340.png)

![image-20240412000150961](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240412000150961.png)



###### try-catch异常处理：

![image-20240412001455898](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240412001455898.png)

![image-20240412001528947](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240412001528947.png)

![image-20240412011034356](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240412011034356.png)

//1.如果 try 代码块有可能有多个异常

//2.可以使用多个 catch 分别捕获不同的异常，相应处理 

//3.要求子类异常写在前面，父类异常写在后面

![image-20240412011807751](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240412011807751.png)

![image-20240412015025585](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240412015025585.png)



###### throws异常处理：

![image-20240412194504609](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240412194504609.png)

![image-20240412210242762](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240412210242762.png)

![image-20240412224504744](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240412224504744.png)



###### 自定义异常：

![image-20240412235205743](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240412235205743.png)

![image-20240412235215437](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240412235215437.png)

 

###### throw和throws的区别：

![image-20240413003537548](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240413003537548.png)





##### 包装类：

###### 分类：

![image-20240414225818745](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240414225818745.png)

###### 包装类和基本数据的转化：

![image-20240414230404824](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240414230404824.png)



###### 包装类和String的转换：

![image-20240415155620392](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240415155620392.png)



###### 常用方法：

![image-20240415162939142](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240415162939142.png) 

###### 习题

![image-20240415173954880](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240415173954880.png)

![image-20240415173930162](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240415173930162.png)



##### String类：

![image-20240415174802640](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240415174802640.png)

![image-20240415180820483](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240415180820483.png)

![image-20240415191244884](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240415191244884.png)





###### 两种创建方式及区别：

![image-20240415191926810](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240415191926810.png)

![image-20240415192010830](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240415192010830.png)

![image-20240415192022906](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240415192022906.png)



![image-20240415201845772](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240415201845772.png)



###### 特性

![image-20240415234713051](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240415234713051.png)

![image-20240415234920029](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240415234920029.png)

![image-20240416001153292](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240416001153292.png)

![image-20240416164514593](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240416164514593.png)





###### 常见方法：

 ![image-20240416164755589](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240416164755589.png)

![image-20240416164808711](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240416164808711.png)

![image-20240416174646992](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240416174646992.png)

str1.compareTo(str2);

其返回的是一个int类型值。

若Str1等于参数字符串Str2字符串，则返回0；

若该Str1按字典顺序小于参数字符串Str2，则返回值小于0；

若Str1按字典顺序大于参数字符串Str2，则返回值大于0。





###### StringBuffer类：

![image-20240416212515909](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240416212515909.png)

![image-20240416213005376](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240416213005376.png)

###### String和StringBuffer对比：

![image-20240416213801761](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240416213801761.png)



![image-20240416224411163](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240416224411163.png)



###### String和StringBuffer转换

![image-20240417175002300](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240417175002300.png)



###### StringBuffer 类常见方法

![image-20240417175209655](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240417175209655.png)





###### StringBuilder：

![image-20240417193200406](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240417193200406.png)

![image-20240417203739351](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240417203739351.png)



###### String、StringBuffer 和 StringBuilder 的比较

![image-20240417211704855](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240417211704855.png)

效率 ： StringBuilder > StringBuffer > String

![image-20240417235750735](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240417235750735.png)



##### Math类

![image-20240418002148981](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240418002148981.png)

![image-20240418004916514](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240418004916514.png)





##### Arrays类

![image-20240418005321095](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240418005321095.png)

![image-20240418005337838](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240418005337838.png)



##### System类

![image-20240419142654934](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240419142654934.png)





##### BigInteger 和 BigDecimal 类

![image-20240419183233620](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240419183233620.png)



##### 日期类

###### 第一代日期类

![image-20240419234649329](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240419234649329.png)





###### 第二代日期类

![image-20240420013850760](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240420013850760.png)





###### 第三代日期类(JDK8)

![image-20240420014858546](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240420014858546.png)

![image-20240420015909067](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240420015909067.png)

![image-20240420015934417](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240420015934417.png)

![image-20240420020411991](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240420020411991.png)



##### 集合

![image-20240421015756476](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240421015756476.png)

######  集合的框架体系

Java 的集合类很多，主要分为两大类，如图

![image-20240421022410196](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240421022410196.png)





###### Collection 接口和常用方法

![image-20240421183846740](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240421183846740.png)

![image-20240421183923164](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240421183923164.png)



###### Collection 接口遍历元素方式 1

使用 Iterator(迭代器)

![image-20240421205646435](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240421205646435.png)

![image-20240421212047004](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240421212047004.png)



###### Collection 接口遍历对象方式 2

for 循环增强

![image-20240421215944716](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240421215944716.png)



###### List 接口和常用方法

![image-20240421221847053](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240421221847053.png)

![image-20240421225208409](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240421225208409.png)

![image-20240421235650039](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240421235650039.png)





###### ArrayList 底层结构和源码分析

![image-20240422010558484](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240422010558484.png)



JDK1.8下的源码

![image-20240422184616247](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240422184616247.png)

![image-20240422184640171](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240422184640171.png)



###### Vector

![image-20240422223144856](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240422223144856.png)



###### Vector 和ArrayList 的比较

![image-20240422223541269](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240422223541269.png)





###### LinkedList

![image-20240422230250184](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240422230250184.png)



增加

![image-20240423153621813](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240423153621813.png)



删除

![image-20240423165515363](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240423165515363.png)



###### ArrayList 和 LinkedList 的比较

![image-20240423173443712](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240423173443712.png)





###### Set 接口和常用方法

![image-20240423173825566](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240423173825566.png)



###### Set 接口的常用方法

和 List 接口一样, Set 接口也是 Collection 的子接口，因此，常用方法和 Collection 接口一样

![image-20240423175503917](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240423175503917.png)



###### HashSet

![image-20240423184747583](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240423184747583.png)



###### HashSet 底层机制说明

![image-20240423193527859](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240423193527859.png)

![image-20240423193621897](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240423193621897.png)



![image-20240424191313043](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240424191313043.png)



###### LinkedHashSet

![image-20240425193252182](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240425193252182.png)

![image-20240425220005777](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240425220005777.png)





###### Map

![image-20240426175051046](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240426175051046.png)

![image-20240426182727681](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240426182727681.png)

(table 中的HashMap$Node的key 和 value值 用Entry封装 然后被entrySet引用 存放Entry， Entry提供了两个方法用于便利key和value值 )



###### Map 接口常用方法

![image-20240426191833599](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240426191833599.png)

![image-20240426191848531](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240426191848531.png)



###### Map 接口遍历方法

![image-20240426193307470](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240426193307470.png)

![image-20240426193358426](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240426193358426.png)

###### HashMap 小结

![image-20240427004741719](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240427004741719.png)

![image-20240428180917675](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240428180917675.png)



###### HashMap 底层机制

![image-20240428181036801](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240428181036801.png)

如果每一条的链表都没有超过8，且size已经到达了12就会开始扩容，如果其中一条链表达到了8个，也会进行扩容。



###### HashTable

![image-20240429012321408](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240429012321408.png)



###### Hashtable 和 HashMap 对比

![image-20240429014824728](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240429014824728.png)



###### Properties

![image-20240429023450797](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240429023450797.png)



###### 开发中如何选择集合实现类

![image-20240429024358662](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240429024358662.png)



###### TreeSet

TreeSet是一个有序集合，它扩展了AbstractSet类并实现了NavigableSet接口。

###### TreeMap

与TreeSet同见代码



###### Collections 工具类

![image-20240501025045971](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240501025045971.png)



###### Execrise

![image-20240501212144389](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240501212144389.png)

![image-20240501230350174](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240501230350174.png)

![image-20240501231129092](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240501231129092.png)

1.p1的name发生改变 因为重写了hashcode 所以哈希值发生改变 不在原来p1所在的位置 当执行remove时 回去找改变哈希值后的位置去删除 发现该位置没有内容 所以没删掉什么 输出两个

2.添加的new Person(1001, “CC”)哈希值和改变后的p1相同 所以会占用改变后p1哈希值对应的位置 所以这里会输出三个

3.添加的new Person(1001, “AA”)的哈希值和初始的p1相同 因为p1的内容已经发生改变变成1001 CC 且equals方法重写比较的是内容 所以会挂载到p1后面 从而输出四个

![image-20240502033018117](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240502033018117.png)





##### 泛型

![image-20240502180328162](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240502180328162.png)

![image-20240502182902053](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240502182902053.png)



###### 介绍

可以理解为表示数据类型的数据类型

![image-20240502183049632](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240502183049632.png)



###### 泛型的语法

![image-20240502194314806](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240502194314806.png)





###### 泛型使用的注意事项和细节

![image-20240502203654179](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240502203654179.png)



###### 自定义泛型

![image-20240506173739939](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240506173739939.png)

![image-20240506180650215](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240506180650215.png)

![image-20240506183448244](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240506183448244.png)



###### 泛型的继承和通配符

![image-20240506225825696](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240506225825696.png)

###### JUnit

![image-20240507012913100](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240507012913100.png)

![image-20240507012954913](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240507012954913.png)



##### 坦克大战1.0

###### java 绘图坐标体系

![image-20240507023006415](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240507023006415.png)



![image-20240507180613315](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240507180613315.png)



![image-20240507215315931](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240507215315931.png)



![image-20240507230923985](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240507230923985.png)

↑演示方法仍在DrawCircle





###### Java事件处理机制

![image-20240508221122505](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240508221122505.png)

![image-20240508221252161](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240508221252161.png)

![image-20240508221414788](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240508221414788.png)

![image-20240508221734357](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240508221734357.png)

![image-20240508221827650](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240508221827650.png)



##### 多线程基础

###### 相关概念

![image-20240509180015968](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240509180015968.png)

![image-20240509180153014](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240509180153014.png)

![image-20240509181354758](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240509181354758.png)

![image-20240509181522310](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240509181522310.png)

![image-20240509181534702](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240509181534702.png)

并发和并行可以同时存在



###### 创建线程的两种方式

在java中线程使用有两种方法。

1.继承Thread 类，重写 run方法

2.实现Runnable接口，重写 run方法

![image-20240509182647193](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240509182647193.png)



###### 继承 Thread 类

![image-20240509222935662](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240509222935662.png)

多线程编程中主线程结束但进程不一定结束 (主线程结束 但子线程还在运行并不会造成应用程序结束)



![image-20240509230328102](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240509230328102.png)



###### 实现Runnable 接口

![image-20240511161535231](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240511161535231.png)



###### 多线程执行

![image-20240511171149016](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240511171149016.png)

![image-20240511174359955](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240511174359955.png)

![image-20240511174431753](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240511174431753.png)





###### Thread 和 Runnable 的区别

![image-20240511210619173](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240511210619173.png)



###### 线程终止

![image-20240511224124397](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240511224124397.png)



###### 线程常用方法

![image-20240511230559223](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240511230559223.png)

![image-20240512001913417](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240512001913417.png)

![image-20240513121538096](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240513121538096.png)

![image-20240513144713910](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240513144713910.png)

Daemon 守护 



###### 线程的生命周期

![image-20240513163739548](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240513163739548.png)

1. 初始(NEW)：新创建了一个线程对象，但还没有调用start()方法。
2. 运行(RUNNABLE)：Java线程中将就绪（ready）和运行中（running）两种状态笼统的称为“运行”。
线程对象创建后，其他线程(比如main线程）调用了该对象的start()方法。该状态的线程位于可运行线程池中，等待被线程调度选中，获取CPU的使用权，此时处于就绪状态（ready）。就绪状态的线程在获得CPU时间片后变为运行中状态（running）。
3. 阻塞(BLOCKED)：表示线程阻塞于锁。
4. 等待(WAITING)：进入该状态的线程需要等待其他线程做出一些特定动作（通知或中断）。
5. 超时等待(TIMED_WAITING)：该状态不同于WAITING，它可以在指定的时间后自行返回。
6. 终止(TERMINATED)：表示该线程已经执行完毕。

![image-20240513164619221](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240513164619221.png)

[Java线程的6种状态及切换(透彻讲解)_线程的状态-CSDN博客](https://blog.csdn.net/pange1991/article/details/53860651)



###### 线程同步 Synchronized

![image-20240513175346422](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240513175346422.png)



###### 互斥锁

![image-20240513181410357](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240513224647493.png)

![image-20240513224910684](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240513224910684.png)

![image-20240513235959573](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240513235959573.png)





###### 线程的死锁

![image-20240514210302823](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240514210302823.png)





###### 释放锁

下面操作会释放锁

![image-20240514211355183](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240514211355183.png)



下面操作不会释放锁

![image-20240514211632009](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240514211632009.png)



##### IO流

###### 文件

![image-20240516231542458](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240516231542458.png)

###### 文件操作

创建文件对象相关构造器和方法

![image-20240516235234166](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240516235234166.png)

![image-20240517010445701](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240517010445701.png)

![image-20240517015225492](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240517015225492.png)





###### IO流原理及流的分类

![image-20240517135853846](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240517135853846.png)



流的分类

![image-20240517140134698](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240517140134698.png)

###### 常用的类

![image-20240517141159782](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240517141159782.png)

流是文件传输路径

文件是计算机管理数据的基本单位，同时也是应用程序保存和读取数据的一个重要场所。

流是字节序列的抽象概念，例如文件、输入/输出设备、内部进程通信管道等。流提供一种向后备存储器写入字节和从后备存储器读取字节的方式。



###### InputStream 字节输入流

![image-20240517163944440](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240517163944440.png)



InputStream抽象类是所有类字节输入流的超类

常用的子类：

​	FileInputStream：文件输入流

​	BufferedInputStream：缓冲字节输入流

​	ObjectInputStream：对象字节输入流

![image-20240517164956359](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240517164956359.png)



###### FileOutputStream字节输出流

![image-20240517201827904](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240517201827904.png)

![image-20240517201735437](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240517201735437.png)



###### FileReader 和 FileWriter 字符输入、输出流

![image-20240518142424542](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240518142424542.png)

![image-20240518162506983](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240518162506983.png)



###### 节点流和处理流

![image-20240519130626986](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240519130626986.png)

数据源：存储数据的地方

![image-20240519134101583](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240519134101583.png)

![image-20240519140622137](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240519140622137.png)

![image-20240519162428216](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240519162428216.png)



###### 处理流-BufferedReader 和BufferedWriter

BufferedReader 和 BufferedWriter属于字符流，是按照字符来读取数据的 关闭处理流时，只需要关闭外层流即可[后面看源码]

![image-20240519192843196](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240519192843196.png)

![image-20240519192859781](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240519192859781.png)



###### 处理流-BufferedInputStream和 BufferedOutputStream

BufferedInputStream是字节流 在创建BufferedInputStream时 会创建一个内部缓冲区数组

BufferedOutputStream是字节流,实现缓冲的输出流,可以将多个字节写入底层输出流中，而不必对每次字节写入调用底层系统

![image-20240519202040135](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240519202040135.png)

![image-20240519202057492](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240519202057492.png)



###### 对象流-ObjectInputStream和ObjectOutputStream

![image-20240520113605714](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240520113605714.png)

![image-20240520114626454](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240520114626454.png)

对象流介绍(处理流)

功能：提供了对基本类型或对象类型的序列化和反序列化的方法 

ObjectOutputStream 提供 序列化功能 

ObjectInputStream 提供 反序列化功能

![image-20240520114719022](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240520114719022.png)

![image-20240520165629882](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240520165629882.png)



###### 标准输入输出流

![image-20240520181525768](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240520181525768.png)



###### 转换流-InputStreamReader 和 OutputStreamWriter

![image-20240520220732187](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240520220732187.png)

![image-20240520221115739](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240520221115739.png)

![image-20240520221159114](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240520221159114.png)



###### 打印流-PrintStream 和 PrintWriter

PrintStream 字节输出流  PrintWriter字符输出流 打印流只有输出流 没有输入流

![image-20240520224609983](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240520224609983.png)



###### Properties 类

![image-20240521112404483](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240521112404483.png)





##### 网络编程

![image-20240522141803501](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240522141803501.png)

![image-20240522142215299](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240522142215299.png)

主机号全0表示网关，主机号全为1表示广播

![image-20240522143629974](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240522143629974.png)

![image-20240522152736820](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240522152736820.png)

协议三要素：语法 语义 同步

![image-20240522155903598](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240522155903598.png)

![image-20240522155959385](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240522155959385.png)



###### InetAddress 类

![image-20240522164310010](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240522164310010.png)



Socket

![image-20240522171937110](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240522171937110.png)

![image-20240522173443375](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240522173443375.png)



###### TCP 网络通信编程

![image-20240522173615336](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240522173615336.png)

应用案例1

![image-20240522200635626](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240522200635626.png)



应用案例2

![image-20240523140237766](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240523140237766.png)



应用案例3

![image-20240523144119310](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240523144119310.png)



应用案例 4

![image-20240523234754719](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240523234754719.png)



###### netstat 指令

![image-20240524140049298](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240524140049298.png)

1、LISTENING状态
FTP服务启动后首先处于侦听（LISTENING）状态。

2、ESTABLISHED状态
ESTABLISHED的意思是建立连接。表示两台机器正在通信。

3、CLOSE_WAIT

  对方主动关闭连接或者网络异常导致连接中断，这时我方的状态会变成CLOSE_WAIT 此时我方要调用close()来使得连接正确关闭

4、TIME_WAIT

  我方主动调用close()断开连接，收到对方确认后状态变为TIME_WAIT。TCP协议规定TIME_WAIT状态会一直持续2MSL(即两倍的分 段最大生存期)，以此来确保旧的连接状态不会对新连接产生影响。处于TIME_WAIT状态的连接占用的资源不会被内核释放，所以作为服务器，在可能的情 况下，尽量不要主动断开连接，以减少TIME_WAIT状态造成的资源浪费。

  目前有一种避免TIME_WAIT资源浪费的方法，就是关闭socket的LINGER选项。但这种做法是TCP协议不推荐使用的，在某些情况下这个操作可能会带来错误。

5、SYN_SENT状态

　 　SYN_SENT状态表示请求连接，当你要访问其它的计算机的服务时首先要发个同步信号给该端口，此时状态为SYN_SENT，如果连接成功了就变为 ESTABLISHED，此时SYN_SENT状态非常短暂。但如果发现SYN_SENT非常多且在向不同的机器发出，那你的机器可能中了冲击波或震荡波 之类的病毒了。这类病毒为了感染别的计算机，它就要扫描别的计算机，在扫描的过程中对每个要扫描的计算机都要发出了同步请求，这也是出现许多 SYN_SENT的原因。

![image-20240524142956656](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240524142956656.png)



###### UDP 网络通信编程[了解]

![image-20240524145024640](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240524145024640.png)

![image-20240524150050535](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240524150050535.png)



##### 反射(reflection)

###### 反射机制

![image-20240610101226476](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240610101226476.png)

![image-20240610111551140](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240610111551140.png)

![image-20240610112904011](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240610112904011.png)

![image-20240610112939702](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240610112939702.png)

![image-20240610115635487](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240610115635487.png)

![image-20240610180231033](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240610180231033.png)



###### Class类

![image-20240610212557312](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240610212557312.png)



**Class 类的常用方法**

![image-20240610214759132](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240610214759132.png)



**获取 Class 类对象**

![image-20240610221226212](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240610221226212.png)



**哪些类型有 Class 对象**

![image-20240610224417918](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240610224417918.png)



**类加载**

![image-20240610224753994](C:\Users\Pretender\AppData\Roaming\Typora\typora-user-images\image-20240610224753994.png)



######  类加载





































##### --------------------------------

------



##### **思想：**

**化繁为简 先死后活**

**一段代码完成一个小功能**

**过关斩将 校验 找不正确条件**
