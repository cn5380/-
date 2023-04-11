



# 第一章	初始JAVA

------

核心机制

垃圾核心机制

# 第二章	数据类型

------



## 标识符

1.标识符：读音		biao 	zhi	fu

2.什么是标识符？

包，类，变量，方法……等等，只要是起名字的地方，那个名字就是标识符。

3.标识符定义规则：

```
1.四个可以(组成部分)：数字，字母，下划线_，美元符号$
注意：字母概念比较宽泛，指的是英文字母，汉子，日语，俄语。。。。
但是我们一般起名字尽量使用英文字母
2.两个不可以：不可以以数字开头，不可以使用java中的关键字
3.见名知意：增加可读性
4.大小写敏感：int a; int A;
5.遵照驼峰命名：
类名：首字母大写，其余遵循驼峰命名
方法名，变量名：首字母小写，其余遵循驼峰命名
包名：全部小写， 不遵循驼峰命名
6.长度无限制，但是不建议太长

```

## 关键字

```java
关键字一律用小写字母标识，按其用途划分为如下几组。
(1)用于数据类型。
用于数据类型的关键字有 boolean、byte、char、 double、 float、int、long、new、short、void、instanceof。
(2)用于语句。
用于语句的关键字有break、case、 catch、 continue、 default 、do、 else、 for、 if、return、switch、try、 while、 finally、 throw、this、 super。
(3)用于修饰
用于修饰的关键字有 abstract、final、native、private、 protected、public、static、synchronized、
transient、 volatile。
(4)用于方法、类、接口、包和异常。
用于方法、类、接口、包和异常的关键字有 class、 extends、 implements、interface、 package、import、throws。
还有些关键字,如 future、 generic、 operator、 outer、rest、var等都是Java保留的没有意义的关键字。 [4] 
另外，Java还有3个保留字:goto、const、null。它们不是关键字，而是文字。包含Java定义的值。和关键字一样,它们也不可以作为标识符使用
```

## 变量和常量

常量分为两种：

```
常量通常指的是一个固定的值，例如：1，2，3，4，’a’，’d’ ,true, ‘helwoda’等。
在Java语言中，主要是利用关键字final来定义一个常量，常量一旦被初始化之后不能在更改其值。
为了更好的区分和表达，一般将1，2，3，4，’a’，’d’ ,true, ‘helwoda’等称为字面常量，而使用final修饰的PI等称为符号常量(字符常量)。

字面常量的类型：
整型变量  123 	33
实型常量	3.234425
字符常量	'a'
逻辑常量	true 	false
字符串常量		"helloworld"

注意：逻辑常量就两个值，一个是true，一个是false。
```

### 变量

#### 1.变量声明格式

```
type varName [=value], [varName[=value]….]; //[]中的内容为可选项，即可有可无
数据类型 变量名 [=初始值] [变量名 [=初始值]…]； 
案例：
int age = 19, age2 = 90;
int age, age2;
```

#### 2.变量的声明

如果在定义一个变量的时候没有赋值，那就相当于没有定义。输出变量时会报错,:尚未初始化变量

![image-20220922201434645](/Users/rain/Library/Application Support/typora-user-images/image-20220922201434645.png)

3.变量的赋值：

变量不可以重复定义，我们在定义的时候直接就可以一句话定义： int age = 100;

![image-20220922202101282](/Users/rain/Library/Application Support/typora-user-images/image-20220922202101282.png)

4.变量的使用：

![image-20220922202155124](/Users/rain/Library/Application Support/typora-user-images/image-20220922202155124.png)

扩展：javap -v TestVar01.class 可以查看字节码

![image-20220922202342065](/Users/rain/Library/Application Support/typora-user-images/image-20220922202342065.png)

```
 0: bipush        10
         2: istore_1
         3: iconst_1
         4: istore_1
         5: iconst_2
         6: istore_1
         7: bipush        42
         9: istore_1
        10: bipush        62
        12: istore_1
```

5.变量的内存：

内存只占用一块空间，就像去电影院观看电影，每个人拿着票根据上面的编号去找对应的位置，然后落座观影。同样的，我们的内存要存放各种各样的数据，内存就好比座位也要进行编号，这就是第一个概念——内存编址。座位可以是遵循“一个座位 对应一个号码”的原则，从“第 1 号”开始编号。而内存则是按一个字节接着一 个字节的次序进行编址，如上图所示。每个字节都有个编号，我们称之为内存地址。

6.变量的作用域：

作用域就是作用范围，变量在什么范围中有效

```
  局部变量
   在函数内部定义的变量称为局部变量，也称为内部变量。局部变量只在定义它的函数内有效，即只有定义他们的函数才能使用，不能被其他函数使用；
   
   小知识点：形式参数也是局部变量，只在它所在的函数中有效，其他的函数不能使用。
  全局变量
  在函数外定义的变量称为全局变量，又称为外部变量。全局变量的作用域是从定义点开始直到文件尾，可以被作用域内的所有函数共用；
```

## 基本数据类型

Java 是一种强类型语言，每个变量都必须声明其数据类型。

Java的数据类型可分为两大类：基本数据类型（private data type）和引用数据类型（reference data type）。

除了基本数据类型以外的数据类型都属与引用数据类型，本章重点：基本数据类型

```
数据类型：
1.基本数据类型
	1.数值型
		整数类型(byte, short, int, long)
		浮点类型(float,doublie)
	2.字符型(char)
	3.布尔型(boolean)
2.引用数据类型
	1.类(class)
	2.接口(interface)
	3.数组
```

#### 整数类型

整数类型变量

十进制 D 		二进制 B		八进制 Q		十六进制 H

整数类型常量

```java
	基本数据类型来存储数值字符和布尔值基本数据类型数值型整数类型浮点类型字符型布尔型整数类型
	整数类型来存储整数数值，即没有数部分的数值，可以是正数也可以是负数，整型数据在Java中有三种表形式，分别是八进制，十进制和十六进制。
	十进制：除了数字0不能以0作为其他进制数的开头
	八进制：必须以0开头
	十六进制：必须以0x或0X开头，
	整型数据根据它所占内存的不同，可分为byte、short、int、long四种类型，它们具有不同的取值范围，
	整形数据类型
	byte数据类型，占内存空间为8位（8位等于1字节）取值范围是 -128～127		正负2的7次方
	short数据类型，占内存空间为16位，取值范围是-32768～32767						正负2的15次方
	int数据类型，占内存空间32位，取值范围是-2147483648～2147483648		 正负2的31次方
	long数据类型，占内存空间为64位，取值范围是 -9223372036854775808～9223372036854775808	  正负2的63次方
	在定义以上四种类型变量的时候，要注意变量的取值范围，超出相应的范围就会出错，对于long型值,若赋予的值于int型的最值或者小于int型的最小值，则需要在数字后加L或者l,表名该数值为长整数，如long num = 123456799998L
```



#### 浮点类型

浮点类型主要有两种：float型、double型。其中float型即单精度浮点型，使用float关键字来定义float型变量，可以一次定义多个变量并对其进行赋值，也可以不进行赋值。 

float 的小数位只有 23 位，即二进制的 23 位，能表示的最大的十进制数为 2 的 23 次方，即 8388608，即十进制的 7 位，严格点，精度只能百分百保证十进制的 6 位运算。

double 的小数位有 52 位，对应十进制最大值为 4 503 599 627 370 496，这个数有 16 位，所以计算精度只能百分百保证十进制的 15 位运算。

float 单精度占 4 个字节，在结尾必须添加“F”或者“f”，double 双精度占 8 个字节,  可以使用后缀“D”或“d”，有效数字指的是小数点后第一个不为0的数字开始数到最后

#### 字符类型

编码和字符集

1.什么是编码？

```
编码是信息从一种形式或格式转换为另一种形式的过程，也称为计算机编程语言的代码简称编码。用预先规定的方法将文字、数字或其它对象编成数码，或将信息、数据转换成规定的电脉冲信号。编码在电子计算机、电视、遥控和通讯等方面广泛使用。编码是信息从一种形式或格式转换为另一种形式的过程。解码，是编码的逆过程。
```

2.解码

发送：你好 -》1001         	接收：1001 -〉你好

3.字符集

```
ASCLL
	英文字符集
	用一个字节的7位表示
IOS8859-1
	西欧字符集
	用一个字节的8位表示
GB2321
	简体中文字符集
	最多使用两个字节编码
GBK
	GB2312的升级。加入了繁体字
	最多使用两个字节编码
	首位是0，一个字节代表一个字符。
	首位是1，两个字节代表一个字符。
Unicode
	国际通用字符集，融合了目前人类使用的所以字符，为每个字符分配唯一的字符码。
	推出了UTF标准：
	三种编码方案， UTF-8， UTF-16， UTF-32

以UTF-8为案例讲解：
中文： 珊		编码： 1110 0111 10 001111 10 001010
UTF-8最多用6个字节表示
底层存储：1110xxxx 10xxxxxx 10xxxxxx
	
```

1.java中使用单引号来表示字符常量，字符型在内存中占有两个字节。chrt类型用来表示在Unicode编码表中的字符，Unicode编码被设计用来处理各种语言的文字，它占两个字节，可运行有65536个字符。

2.转义字符

| 转义符 | 含义   | Unicode值 |
| ------ | ------ | --------- |
| \b     | 退格   | \u0008    |
| \n     | 换行   | \u000a    |
| \r     | 回车   | \u000d    |
| \t     | 制表符 | \u0009    |
| \ "    | 双引号 | \u0022    |
| \ '    | 单引号 | \u0027    |
| \\     | 反斜杠 | \u005c    |

3.ASCLL字符

![image-20230215133057271](/Users/rain/Library/Application Support/typora-user-images/image-20230215133057271.png)

解释乱码问题

用记事本选择编码方法的时候一般要选择ANSl—>获取当前操作系统的编码格式：GBK



#### 布尔类型

布尔类型有两个常量值，true和false，在内存中占一位（不是一个字节），不可以使用0或者非0的整数代替true或者false，这点和C语言不同，boolean类型用来判断逻辑条件，一般用于程序流程控制。

#### 基本数据类型类型的转换

1.什么是类型转换

```
在赋值运算或者算数运算的时候，要求数据类型一致，就要进行类型的转换。
```

2.类型转换的种类

```
自动转换，强制转换
```

3.内存演示

```
int 10.  -->byte	10
int	270	 -->byte	14
```

4.代码演示

```java
public class TestVar10 {
    public static void main(String[] args) {
        double d = 6;//int-->double
        System.out.println(d);

        //java: 不兼容的类型: 从double转换到int可能会有损失
        int i = (int) 6.5; //double-->int ,类型强制转换
        System.out.println(i);

        //在同一个表达式中，有多个数据类型的时候，应该如何处理。
        //多种数据类型参与运算的时候，整数类型，浮点类型，字符类型都可以参与运算，唯独布尔类型不可以参与运算。
        double d2 = 12 + 44 + 4324 + 432L + 33F + 'a';
        System.out.println(d2);

        /*
        类型级别（从低到高）
        byte,short,char,-->int-->long-->float-->double
        级别用来做什么？当一个表达式中有多种数据类型，要找出当前表达式中级别最高的那个类型，然后其余的
        类型都转换为当前表达式中级别最高的类型进行运算。
        double d2 = 12+22L+8.5F+3.95+'a';
                  = 12.0+22.0+8.5+3.95+97.0
         */
        int i2 = (int) (12 + 22L + 8.5F + 3.95 + 'a');
        System.out.println(i2);

        /*
        在进行运算的时候
        左=右  :直接赋值
        左<右  ：强转
        左>右  ：直接自动转换
         */

        //以下情况属于特殊情况，对于byte,short,char类型来说，只要在他们的表述范围中，赋值的时候就不需要进行强制转换直接赋值即可，
        byte b = 12;
        System.out.println(b);}}
```



练习：final、字符常量及Scanner的使用

```java
package S_1;

//形象理解：在Java.uil下将Scanner拿过来用
import java.util.Scanner;

public class TestVar11 {
    public static void main(String[] args) {
        //实现功能：求圆的周长和面积
        //1.提取变量；提取变量，就是为了一劳永逸，以后只需要改变量的值，下面用到这个变量的地方，取值都变化了。
        //2.一个变量一旦被final修饰，这个变量就变成了常量，这个常量的值就不可变了
        //   这个常量就是我们所说的 字符常量-->pi
        //   约定俗称的规定，字符常量的名字全部大写。
        //3.使用扫描器：Scanner的使用->注意通过形象的理解去使用
        final double PI = 3.1415926;
        //拿来一个扫描器
        Scanner sc = new Scanner(System.in);
        //给一个友好性的提示
        System.out.println("请输入半径：");
        //让扫描器扫描键盘录入的int类型数据；
        int r = sc.nextInt();

        //求周长：
        double c = 2 * PI * r;
        System.out.println("周长为：" + c);

        //求面积：
        double s = PI * 5 * r;
        System.out.println("面积为：" + s);}}
```



练习：加深对Scanner的使用

```java
public static void main(String[] args) {
        //键盘录入学生的信息：年龄，身高，姓名，性别
        //键盘录入年龄：（接收int类型数据）
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入你的年龄：");
        int age = sc.nextInt();
        //键盘录入身高：（接收double类型数据）
        System.out.println("请输入你的身高：");
        double length = sc.nextDouble();
        //键盘录入名字：（接收String类型数据）
        System.out.println("请输入你的名字：");
        String name = sc.next();
        //键盘录入性别：（接收char类型数据）
        System.out.println("请输入你的性别：");
        char sex = sc.next().charAt(0);
        System.out.println("年龄：" + age + " 身高： "+ length + " 名字： " + name + " 性别：" + sex);}
```



------

# 第三章	运算符

## Java中的运算符

1.Java语言支持如下运算符

- 算术运算符

  +, -, *, /(除), %(取余), ++(自增), —(自减)

- 赋值运算符

  =

- 扩展赋值运算符

   +=, -=, *=, /=

- 关系运算符

   ,>,<,>=,<=,==,!=

- 逻辑运算符

   &,|,&&,||,!,^

- 位运算符

   &,|,^,~,>>,<<,>>>(了解！！1)

- 条件运算符

   ？ ：

2.相关概念辨析

```
+		           运算符		操作符	 Operator
5+6			       表达式					 Expression
5 6 		       操作数					 Operand
int m = 5+6;   语句							Sentence
```

## 算术运算符

/和%

```java
        //1.任意给出一个四位数
        int num = 1234;

        //2.求出每位上的数字：
        //个位数：
        int num1 = num % 10;
        //十位数：
        int num2 = num / 10 % 10;    //1234--->123--->3
        //百位数：
        int num3 = num / 100 % 10;   //1234--->12--->2
        //千位数：
        int num4 = num / 1000;       //1234-->1
```

+

1.+的作用：

- 表示正数
- 表示相加操作
- 表示字符串的拼接

2.代码

```java
        //表示正数
        System.out.println(+5);
        //相加操作
        System.out.println(5 + 6);
        System.out.println(5 + '6');
        //字符串的拼接
        //规则：+左右两侧的任意一侧有字符串，那么这个加号就是字符串拼接的作用，结果一定是字符串
        int num = 56;
        System.out.println("num=" + num);
        System.out.println(5 + 6 + "7");//11+"7"---"117"----117
        System.out.println(5 + '6' + "7");
        System.out.println("5" + '6' + "7");
        System.out.println("5" + '6' + 7);
```

++代码【练习1】

```java
package S_2;

public class TestOpe04 {
    public static void main(String[] args) {
        int a = 5;
        a++;//理解为：相当于 a = a+1 操作
        System.out.println(a);

        a = 5;
        ++a;//理解为：相当于 a = a+1 操作
        System.out.println(a);

        //总结：++单独使用的时候，无论放在前还是后，都是加1操作

        //将a 参与到运算中
        a = 5;
        int m = a++ + 7;  //先运算 m = a+7; 再加1: a = a+1
        System.out.println(m); //12
        System.out.println(a); //6

        a = 5;
        int n = ++a + 7;  //先运算 a = a+1 ,  再加1: m = a+7;
        System.out.println(n); //13
        System.out.println(a); //6
    }
}
```

无论这个变量是否会参与到运算中，只要用++运算符，这个变量本身就加1操作，只是说如果变量参与到运算中去的话，对运算结果是产生影响，看++在前还是在后，如果++在后，先运算，后加1, 如果++在前，先加1, 后运算，

【练习2】

运算符的优先级级别： ++ > +

```java
        int a = 5;
        System.out.println(a++ + a++);
        System.out.println(a++ + ++a);
        System.out.println(++a + ++a);
        System.out.println(++a + a++);
```



## 扩展赋值运算符

+=, -= /+ *=

1.a+=b 和 a=a+b区别：

```
1. a+=b 可读性稍差，编译效率高，底层自动进行类型转换
2. a=a+b 可读性好，编译效率低，手动进行类型转换
```

2.面试题

```java
1.请问a+=b相当于a=a+b,那么也相当于a=b+a吗？
对于基本数据类型来说：没区别
        int x = 5,y=6;
        x+=y;
        x=x+y;

对于String类型就不一样了：
        
        char m = 'a';
        char n = 'b';
        m = (char) (m+n);
        Ã
        m+=n;
        ĥ
```



```java
		2.下面哪句话出错：4	
			1	byte a = 10;
      2  int b = 20;
      3  a+=b; //自动强制转换
			4	 a = a+b;
			更正
      4  a = (byte) (a+b); //手动强制转换


```

## 关系运算符

```java
public class TestOpe08 {
    public static void main(String[] args) {
        //>,<,>=,<=,==,!=
        //关系运算符最终结果
        System.out.println(4>9);
        System.out.println(4>=9);
        System.out.println(4<9);
        System.out.println(4<=9);
        System.out.println(4==9);
        System.out.println(4!=9);
        System.out.println((5<0)!=(6==8));
        /*
false
false
true
true
false
true
false
*/
    }
}
```

## 逻辑运算符

进行逻辑运算的符号，运算符两边连接的都是布尔类型的操作数，最终表达式的结果是布尔值，要么是true，要么是false。

```java
public class TestOpe09 {
    public static void main(String[] args) {
        //与：&   规律：只要有一个操作数是false
        System.out.println(true&false);
        System.out.println(true&true);
        System.out.println(false&false);
        System.out.println(false&true);

        //短路与： &&  规律： 效率高一些，只要有一个表达式是false，那么第二个表达式就不用写了，结果一定是false
        System.out.println(true&false);
        System.out.println(true&true);
        System.out.println(false&false);
        System.out.println(false&true);

        //逻辑或: |   规律： 只要有一个操作数是true，那么结果一定是true。
        System.out.println(true|false);
        System.out.println(true|true);
        System.out.println(false|false);
        System.out.println(false|true);

        //短路或： ||  规律： 效率高一些，只要有一个表达式是true，那么第二个表达式就不用写了，结果一定是true。
        System.out.println(true||false);
        System.out.println(true||true);
        System.out.println(false||false);
        System.out.println(false||true);

        //逻辑非：  ！  规律：相反结果
        System.out.println(!false);
        System.out.println(!true);

        //逻辑异或 ^    规律： 两个操作数相同，结果为false，不相同，结果为true
        System.out.println(true^false);
        System.out.println(true^true);
        System.out.println(false^false);
        System.out.println(false^true);
    }
}
```

## 条件运算符

1.条件运算符：又称： 三元运算符/三目运算符

2.格式：a?b:c

其中a 是一个布尔类型的表达式，返回结果要么是true要么是false，结果由a来决定。

如果结果是true，执行b,

如果结果是false，执行c,

练习：

```java
    public static void main(String[] args) {
        //实现功能：男孩女孩选择晚饭吃什么，如果意见一致，听男生的，如果意见不一致，听女生的，
        Scanner sc = new Scanner(System.in);
        System.out.print("请选择男孩吃什么：（输入1-9）；");
        int a = sc.nextInt();
        System.out.print("请选择女孩吃什么：（输入1-9）：");
        int b = sc.nextInt();
        System.out.print(a==b?"听男孩的":"听女孩的");
```



## 位运算符

&,|,^,~,>>,<<,>>>

如何区分逻辑运算符和位运算符：

逻辑运算符：左右连接的是布尔类型的操作数

位运算符：左右连接的是具体的操作数

1. <<    左移

   面试题：4乘以8的最后方式、：4<<3

   左移几次就是乘多少次2

   ```java
   3<<2
   00000000 00000000 00000000 00000011。  ---》3
   00000000 00000000 00000000 00001100。  ---》12
   
   ```

2. ,>>. 有符号右移

   右移几次就是除多少次3

   ```java
   6>>2
   00000000 00000000 00000000 00000110。  ---》6
   00000000 00000000 00000000 00000001。  ---》1
   ```

3,  ,>>> 无符号右移

6>>>2=1

4. &与

6&3 = 2

5.| 或

6|3 =7

6. ^ 异或

   6^3 = 5

7. ~反

   ～6 = -7

PS：byte类型的表数范围 -128是怎么算出来的

127: 01111111

-128: 1000000

一看就是负数，减1: 01111111，取反： 10000000， 2^128  加负号： -128

## 运算符总结

算术运算符

| 运算符 | 含义                   |
| ------ | ---------------------- |
| /      | 除法                   |
| %      | 求余数                 |
| +      | 加号、正数、字符串拼接 |
| ++     | 自增                   |
| --     | 自减                   |

赋值运算符

| 运算符 | 含义 |
| ------ | ---- |
| =      | 赋值 |

扩展赋值运算符

| 运算符 | 用法举例 | 等效的表达式 |
| ------ | -------- | ------------ |
| +=     | a+=b     | a=a+b        |
| -=     | a-=b     | a=a-b        |
| *=     | a*=b     | a=a*b        |
| /=     | a/=b     | a=a/b        |
| %=     | a%=b     | a=a%b        |



| 优先级 |          运算符          |           类           |  结合性  |
| :----: | :----------------------: | :--------------------: | :------: |
|   1    |            0             |       括号运算符       | 由左至右 |
|   2    | ！，+（正号），-（负号） |       一元运算符       | 由左至右 |
|   2    |            ～            |      位逻辑运算符      | 由右至左 |
|   2    |          ++，--          |    递增与递减运算符    | 由右至左 |
|   3    |         *，/，%          |       算术运算符       | 由左至右 |
|   4    |           +，-           |       算术运算符       | 由左至右 |
|   5    |          <<,>>           |   位左移、右移运算符   | 由左至右 |
|   6    |        >,>=,<,<=         |       关系运算符       | 由左至右 |
|   7    |          ==,!=           |       关系运算符       | 由左至右 |
|   8    |            &             |  位逻辑符、逻辑运算符  | 由左至右 |
|   9    |            ^             |  位逻辑符、逻辑运算符  | 由左至右 |
|   10   |            \|            |  位逻辑符、逻辑运算符  | 由左至右 |
|   11   |            &&            |       逻辑运算符       | 由左至右 |
|   12   |           \|\|           |       逻辑运算符       | 由左至右 |
|   13   |            ?:            |       条件运算符       | 由右至左 |
|   14   |     =,+=,-=,*=,/=,%=     | 赋值运算符、扩展运算符 | 由右至左 |





## 运算符的优先级

赋值<三目<逻辑<关系<算术<单目

PS:实际开发中不会写特别特别复杂的运算式，你要想先用谁就用（）

案例：

```
5<6|’A’>’a’&&12*6<=45+23&&!true
= 5<6|’A’>’a’&&12*6<=45+23&&false
= 5<6|’A’>’a’&&172<=45+23&&fasle
= true|fasle&&fasle&&fasle
= false
```



# 第四章  流程控制

## 引入

1.流程控制的作用：

```
流程控制是用来控制程序中执行顺序的语句，可以把语句组合成能完成一定功能的小逻辑模块。
```

2.控制语句的分类：

```
控制语句分为三类：顺序、选择、循环
"顺序结构"代表 "先执行a、再执行b"的逻辑。
"条件判断结构"代表 "如果...,则...."的逻辑。
"循环结构"代表，"如果....则再继续.."的逻辑
```

三种流程控制语句就能表示所有的事情，任何一种高级语言 都具备以上两种结构。

## 分支结构

### if

单分支

```
        if-单分支
        （1）结构
        if（条件表达式），这个表达式的结果是布尔值，要么是false，要么是true，
            如果表达式的结果是true，那么执行{}中代码
            如果表达式的结果是false，那么不执行{}中代码
         (2)上面的代码中， 我们用四个单分支，拼凑出四个选择，每个选择是独立的，依次判断执行，
         （3）if后面的（）中的条件，要按照自己需求尽量完善。
```

多分支

```
        //利用if多分支
//
//        (1)结构
//        if(){}
//        else if ("") { }
//        else {}
//        (2)
//        else 隐藏了与上面不同的条件
//       （3）
//        好处：只要满足一个分支以后，后面的分支就不需要判断了
//          (4) 我们写代码的时候,尽量保证else的存在
```

双分支

```
//        if (sum>=14) {
//            System.out.println("一等奖");
//        }else {
//            System.out.println("没中奖");
//        }

        //利用三目运算符
        System.out.println(sum>=14?"一等奖":"没中奖");
```

随机数：在这个数生成之前我们不确定这个数是多少，不可知

在Java中依靠一个类，Math类帮助我们生成，这个类中有一个方法专门用来生成随机数：

Random()：返回带正号的double值，0.0<=值<=1.0

举例；int num = (int)(math.random()*6) + 1;



### switch

```
1.语法结构
switch(){
case *:
case *:
......
}
2.switch后面是一个()，()中表达式返回的结果是一个等值，这个等值的类型为：int,byte,short,char,String,枚举类型
3.这个()中的等值与依次根case后面的值进行比较，如果匹配成功，就执行：后面的代码
4.为了防止代码的“穿透”效果，：在每个分后面加上一个关键词break，遇到break这个分支就结束了。
5.类似else的“兜底”"备胎"分支：default分支
6.default分支可以写在任意的位置上，但是如果没有最后一行，后面必须加上break关键字，
7.相邻分支逻辑是一样的，那么就可以保留一只分支，上面的都可以省去不写了
8，相邻分支和if分支区别：
表达式是等值判断的话，if,switch都可以
如果表达式是区间判断的话，if最好
```



## 循环结构

### while

1.语法结构

```
while(布尔表达式){
循环体
}
```

在循环刚开始时，会计算一次，“布尔表达式”的值，若条件为真，执行循环体，而对于后来每一次额外的循环时，都会在开始前重新计算一次，语句中应有使循环趋向于结束的语句，否则会出现无限循环——“死”循环。

总结：

1.循环作用：将部分代码重复执行

循环只是提高了程序员编写代码的效率，但是底层执行的时候还是重复执行

2.循环四要素：

```
   //功能： 1+2+3+4+5
        
        int num1 = 1;//1.条件初始化
        int sum = 0;

        while (num1 <= 5) //2.条件判断
        {
            sum += num1; //3.循环体
            num1++;      //4.迭代
        }
        System.out.println(sum);
```

初始化谁，就判断谁，判断谁，就迭代谁

### do-while

1.语法结构

```
do{
	循环体
}while(布尔表达式)
```

do-while循环结构会先执行循环体，然后在判断布尔表达式的值，若条件为真，执行循环体，当条件为假时结束循环，do-while循环的循环体至少执行一次，

### for

1.语法结构

```
for(条件初始化；条件判断；迭代){
循环体；
}
```

对（）进行判定，若判断结果为true，则执行循环体，否则，终止循环，最后在每一次反复的时候，进行某种形式的“步进”，即执行迭代因子

```
1.初始化部分设置循环变量的初值
2.条件判断部分为任意布尔表达式
3.迭代因子控制循环变量的增减
```

for循环在执行条件判定后，先执行的循环体部分，在执行步进，。

关键字

break:  return， continue

```
在任何循环语句的主体部分，均可用于break控制循环的流程。break用于强行退出循环，不执行循环中剩余的语句。continue语句用在循环语句体中，用于终止某次循环过程，即跳过循环体中尚未执行的语句，接着进行下一次是否执行循环的判定。
return的作用，结束当前所在方法的执行：
```



break:作用 ：停止循环，停止距今它自己最近的循环

```
        //功能：求1-100的和，当和第一次超过300的时候，停止程序
        int sum = 0;
        for (int i = 0; i <= 100; i++) {
            sum += i;

            if (sum > 300) {
                //停止循环
                break;}  
         System.out.println(sum);}
```

continute 作用：结束本次循环，继续下一次循环

```
//        功能：输出1-100被6整除的数：
//        方式1:
        for (int i = 0; i < 100;i++) {
            if (i%6 == 0) {  //被6整除
                System.out.println(i);
        }
        }
        for (int i = 0; i < 100;i++) {
            if (i%6 != 0) { //不被6整除
                continue;  //停止本次循环，继续下一次循环
            }
            System.out.println(i);
        }
```

```
    public static void main(String[] args) {
        for (int i = 1; i <= 100;i++) {
            if (i==36) {
                continue;
            }
        System.out.println(i);
        }

        for (int i = 1; i <= 100; i++) {
            while (i==36){
                continue;//1-35+ 死循环
            }
            System.out.println(i);
        }
    }
```

```
      outer ：跳出带有outer的循环
      outer:
        for (int i = 0; i <=100;i++) {
            while (i==36) {
                continue outer; //1-100没有35
            }
            System.out.println(i);
        }
    }
```

Return	作用：跟循环无关，就是程序中遇到return那么return所在的那个地方就停止执行了。

```java
    public static void main(String[] args) {
        //return :遇到return结束当前正在执行的方法
        for (int i = 0; i < 100;i++) {
            while (i==36){
                return;
            }
            System.out.println(i);
}
```



乘法口诀练习

```java
        int j = 1;
        while (j < 10) {
            for(int i =1;i<=j;i++){
                int sum = j*i;
                System.out.print(i + "*" + j + "=" + sum + "\t");
            }
            System.out.print("\n");
            j ++;
}
//        int j = 9;
//        while (j >0) {
//            for(int i =1;i<=j;i++){
//                int sum = j*i;
//                System.out.print(i + "*" + j + "=" + sum + "\t");
//            }
//            System.out.print("\n");
//            j --;
//        }
```

打印各种形状

```java
package S_3;

public class TestFor11{
    public static void main(String[] args) {
          //打印长方形
    /*
    *********
    *********
    *********
     */
//        for(int i = 1; i <=4; i++) {
//            for(int j=1;j<=9;j++){
//                System.out.print("*");}
//            System.out.println();}

        //距离前面有一定空隙的长方形：
//        for (int i = 1; i <= 4; i++) {
//            for (int j = 1; j <= 5; j++) {
//                System.out.print(" ");
//            }
//            for (int j = 1; j <= 9; j++) {
//                System.out.print("*");
//            }
//            System.out.println();
//
//        }
        //平行四边形
//        for(int j = 1; j <= 4; j++){
//            for (int i = 1; i <= (9-i); i++) {
//                System.out.print(" ");
//            }
//            for (int i = 1; j <= 9;i++) {
//                System.out.print("*");
//            }
//            System.out.println();
//        }

        //三角形
//        for(int j=1;j<=4;j++){
//            //加入空格
//            for (int i = 1; i <= (9-i);i++) {
//                System.out.print(" ");
//            }
//            for (int i = 1; i <= (2*j-1); i++) {
//                System.out.print("*");
//            }
//            System.out.println();
//        }

        //菱形
//        for(int j=1;j<=4;j++){
//            //加入空格
//            for (int i = 1; i <= (9-i);i++) {
//                System.out.print(" ");
//            }
//            for (int i = 1; i <= (2*j-1); i++) {
//                System.out.print("*");
//            }
//            System.out.println();
//        }
//        for(int j=1;j<=3;j++){
//            //加入空格
//            for (int i = 1; i <= (9-i);i++) {
//                System.out.print(" ");
//            }
//            for (int i = 1; i <= (7-2*j); i++) {
//                System.out.print("*");
//            }
//            System.out.println();
//        }


        for(int j=1;j<=4;j++){
            //加入空格
            for (int i = 1; i <= (9-i);i++) {
                System.out.print(" ");
            }
            for (int i = 1; i <= (2*j-1); i++) {
                if (i == 1||i==(2*j-1)) {
                    System.out.print("*");
}else {
    System.out.print(" ");
}

            }
            System.out.println();
        }
        for(int j=1;j<=3;j++){
            //加入空格
            for (int i = 1; i <= (9-i);i++) {
                System.out.print(" ");
            }
            for (int i = 1; i <= (7-2*j); i++) {
                if (i == 1||i==(7-2*j)) {
                    System.out.print("*");
                }else {
                    System.out.print(" ");
                }
            }
            System.out.println();
        }}}
```

实心菱形

```java
 public static void main(String[] args) {
        //先打印一个正方形，然后某些位置上打印*某些位置上打印空格。
        int size=17;
        int startNum=size/2+1;  //起始序号
        int endNum = size/2+1; //终止序号

        //引入一个布尔类型的变量，理解为开关
        boolean flag = true;
        for (int j = 1; j <=size;j++) {
            for (int i = 1; i <=size;i++) {
                if (i >= startNum&&i<=endNum) {
                    System.out.print("*");
                }else {
                    System.out.print(" ");
                }
            }
            //换行
            System.out.println();
            if (endNum==size) {
                flag = false;
            }
            if (flag) {
                startNum--;
                endNum++;
            }else {
                startNum++;
                endNum--;
```

## 第五章	方法的定义和调用

1.什么是方法？

```
方法（method）就是一段用来完成特定功能的代码片段，类似于其他语言的函数（function）。方法用于定义该类或该类的实例的行为特征和功能实现，方法是类和对象行为特征的抽象，方法很类似于面向过程中的函数。面向过程中，函数是最基本单位，整个程序由一个个函数调用组成。面向对象中，整个程序的基本单位是类，方法是从属于类和对象的。
```

2.方法声明格式：

```
[修饰符1 修饰符2 ...] 返回值类型		方法名(形式参数列表){
	java语句；......

}
```

3.方法的调用方式：

```
对象名.方法名(实参列表)
```

4.方法的详细说明

```
- 形式参数：在方法声明时用于接收外界传入的数据
- 实参：调用方法时实际传给方法的数据。
- 返回值：方法在执行完毕后返还给调用它的环境的数据
- 返回值类型：事先约定的返回值的数据类型，如无返回值，必须显示指定为void。
```

5.代码

```java
    public static int add(int num1, int num2){
        int sum = 0;
        sum += num1;
        sum += num2;
        return sum;
    }

    public static void main(String[] args) {
        System.out.println(add(10,222));
    }
```

总结：

```
1.方法是：对特定的功能进行提取，形成一个代码片段，这个代码片段就是我们说的方法
2.方法和定义是并列的方法，所以我们定义的方法不能写到main方法中
3.方法的定义-->格式：
修饰符 方法返回值类型 方法名（形参列表）{
方法体；
return 方法返回值；
}
4.方法的作用：提高代码的复用性
5.总结方法定义的格式：
(1)修饰符：暂时使用public static ---》面向对象一章讲解
(2)方法返回值类型：方法的返回值对应的数据类型（byte,long,int,double,float.char），也可以是引用数据类型
(3)方法名：见名知意，首字母小写，其余遵循驼峰命名，eg:addNum,一般尽量使用英文名命名
(4)形参列表：方法定义的时候需要的形式参数：int num1.int num2.--》相当于告诉方法的调用者：需要传入几个参数，需要传入的参数的类型
	实际参数：方法调用的时候传入的具体的参数：10，20 --》根据形式参数的需要传入的
(5)方法体：具体的业务逻辑代码
(6)return 方法返回值：
方法如果有返回值的话：return+方法返回值，将返回值返回到方法的调用处
方法没有返回值的话：return可以省略不写，并且返回值类型处写void。
```

6.方法的定义需要注意什么？

```
1.形参列表要怎么写：定义几个参数，分别是什么类型的
2.方法到底是否需要返回值，如果需要的话，返回值的类型是什么
```

7.方法的调用需要注意什么：

```
1.实际参数要怎么传入：传入几个参数，传入什么类型的
2.方法是否有返回值需要接收。
```

### 方法的重载

1.什么是方法的重载？

方法的重载是指一个类中可以定义多个方法名相同，但参数不同的方法，调用时，会根据不同的参数自动匹配对应的方法。

注意本质：重载的方法，实际是完全不同的方法，只是名称相同而已。

2.构成方法重载的条件

```
不同的含义：形参类型、形参个数、形参顺序不同
只有返回值不同不构成方法的重载
如：int a(String str){} 与 void a(String str){}不构成方法重载
只有形参的名称不同，不构成方法的重载
如：int a(String str){}与int a(String s){}不构成方法重载
```

3.代码

```java
package S_4;

public class TestMethod05 {
    public static void main(String[] args){
        int sum = add(10,20);

        System.out.println(add(22,add(12,23)));

    }

    //定义一个方法：两个数相加，
    public static int add(int num1, int num2){
        return num1+num2;
    }

    ///定义一个方法：三个数相加，
    public static int add(int num1, int num2, int num3) {
        return num1 + num2+num3;
    }

    ///定义一个方法：三个数相加，类型为double
    public static double add(double num1, int num2, int num3) {
        return num1 + num2+num3;
    }
}
```



```
总结：
1.方法的重载：在同一个类中，方法名相同，形参列表不同的多个方法，构成了方法的重载
2.方法的重载只跟：方法名和形参个数有关，与修饰符，返回值类型无关
3.注意：形参列表不同值得是什么？
(1)个数不同
add() add(int num1) add(int num1,int num2)
(2)顺序不同
add(double num1,int num2) add(int num1, double num2)
(3)类型不同
add(int num1) add(double num1)
4.请问下面的方法是否构成了方法的重载？
(1)add(int a) 和add(int b)  不构成，相当于方法的重复定义
(2)public static int add(int a)和 public static void add(int b)    不构成

```

## 第六章	数组

### 数组的引入

```
  //功能：键盘录入十个学生的成绩，求和：求平均数：
        //定义一个求和的变量
        int sum= 0;
        Scanner sc = new Scanner(System.in);
        for (int i = 1; i <= 10;i++) {
            System.out.print("请录入第" + i + "学生的成绩： ");
            int score = sc.nextInt();
            sum+=score;
        }

        System.out.println("十个学生的成绩和是：" + sum);
        System.out.println("十个学生的成绩平均数是：" + sum/10);
    }
```

缺点：就是不能求每个学生的成绩具体是多少

解决：将成绩进行存储 —引入：数组 

感受到数组的作用：数组用来存储数据的，在程序设计中，为了处理方便，数组用来将相同类型的若干数据组织起来。这个若干数据的集合我们称为数组。

### 数组的学习

1.数组的定义

```
数组是相同类型数据的有序集合，数组描述的是相同类型的若干个数据，按照一定的先后次序排列组合而成。其中，每一个数据称作一个元素，每个元素可以通过一个索引(下标)来访问它们。数组的四个基本特点。
1.长度是确定的。数组一旦被创建，它的大小就是不可以改变的。
2.其元素的类型必须是相同类型，不允许出现混合类型
3.数组类型可以是任何数据的类型，包括基本类型和引用类型。
4.数组有索引的：从0开始，到length-1结束。
5.数组变量属于引用类型， 数组也是对象
PS；数组变量属于引用类型，数组也是对象，数组中的每个元素相当于该对象的成员变量，数组本身就是对象，JAVA中的对象是在堆中的，因此数组无论保存原始类型还是其他对象类型，数组对象本身是在堆中存储的。
```

2.数组的学习

```
package S_5;

public class TestArray02 {
    public static void main(String[] args) {
        //数组的作用：用来存储相同的数据
        //以int类型数据为案例：数组用来存储list类型数据
        //1.声明（定义数组）
        int[] arr; //定义一个int类型的数组，名字叫做arr
        int arr2[];
        //如果数组只声明，没有后续操作，那么这个数组相当于没有定义
        //int[] arr3 = null; //空， 辨别：数组赋值为null和什么都没有赋值  不一样的效果
//        2.创建
        arr = new int[4]; //给数组开辟了一块长度为4的空间

//        3.赋值
        arr[0] = 123;
        arr[1] = 213;
        arr[2] = 121;
        arr[3] = 13;

//        4.使用
        System.out.println(arr[3]);
        System.out.println(arr[0]+100);
        //通过数组属性来获取 数组长度
        System.out.println(arr.length);
    }
}
```

### 数组引入的习题—数组的遍历

```
package S_5;

import java.util.Scanner;

public class TestArray03 {
    public static void main(String[] args) {
        //        //练习
        int[] arr2 = new int[10];
        Scanner sc = new Scanner(System.in);
        //定义一个求和的变量
        int sum= 0;
        for (int i = 0; i <=arr2.length-1; i++) {
            //功能：键盘录入十个学生的成绩，求和：求平均数：

            System.out.print("请录入第" + (i+1) + "学生的成绩： ");
            arr2[i]= sc.nextInt();
            sum+=arr2[i];
        }
//        System.out.println("十个学生的成绩和是：" + sum);
//        System.out.println("十个学生的成绩平均数是：" + sum/10);

        //将数组中的每个元素进行查看 ，，，数组的遍历：
//        1.：普通for循环
        for (int i = 0; i<=9;i++) {
            System.out.println("第 " +(i+1)+  "个学生的成绩是："+ arr2[i]);
}
//        2. 增强型for循环
        int count= 0;
        for (int num:arr2){
            count ++;
            System.out.println("第 " +count+  "个学生的成绩是："+ num);        }

//        3.利用for循环，逆向遍历
        for (int i = 9; i >=0; i--) {
            System.out.println("第 " +(i+1)+  "个学生的成绩是："+ arr2[i]);
        }}}
```



### 数组的三种初始化方式

```
数组的初始化方式共有三种：静态初始化、动态初始化、默认初始化

静态初始化
除了用new关键字来产生数组以外，还可以直接在定义数组的同时就为数组元素分配空间并赋值。
eg:
int[] arr = {1,23,4,5,63};
int[] arr = new int[]{1,23,4,5,63};
注意：
1.new int[3]{1,2,3,4}  ---错误
2.int[] arr;
arr={12,34};

动态初始化
数组定义与为数组元素分配空间并赋值的操作分开进行。
eg:
int[] arr = new int[3];
arr[0]=12;
arr[1]=13;
arr[2]=14;

默认初始化
数组是引用类型，它的元素相当于类的实例变量，因此数组一经分配空间，其中的每个元素也被按照实例变量同样的方式被隐式的初始化。
int[] arr = new int[3];   ---数组有默认的初始化值
数组有默认的初始化值：
要看是什么类型的数组：

基本数据类型的数组：
byte[]:0
short[]:0
int[]:0
```

### 数组的引用题

最值问题

```
package S_5;

public class TestArray04 {
    public static void main(String[] args) {
//        /获取数组最大最小值问题
//        定义数组
        int[] arr = {1,2,3,3,34,532,3,432};

        System.out.println("数组最大值是："+getBig(arr));
        System.out.println("数组最小值是："+getSmall(arr));
    }
    
    //返回最大值
    public static int getBig(int[] arr){
        int num =0;

        //将数组中的一个数赋给num，然后对比数组的所有值。
        num = arr[0];
        for(int i =0;i < arr.length; i++) {
            if (arr[i] > num) {
                num = arr[i];
            }
        }
        return num;
    }

    //返回最小值
    public static int getSmall(int[] arr) {
        int num = 0;

        //将数组中的一个数赋给num，然后对比数组的所有值。
        num = arr[0];
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] < num) {
                num = arr[i];
            }
        }
        return num;
    }
}
```

添加元素

```
package S_5;

import java.util.Arrays;
import java.util.Scanner;

public class TestArray06 {
    public static void main(String[] args) {
        //添加元素
        int[] arr = {1,2,3,4,5,2,3,4342};
        System.out.println("原数组为："+Arrays.toString(arr));
        Scanner sc = new Scanner(System.in);
        System.out.print("请输入你要插入的位置：");
        int index = sc.nextInt();
        System.out.print("请输入你要插入的值：");
        int value = sc.nextInt();

        addValue(arr,index,value);

        System.out.println("添加过元素后的数组为："+Arrays.toString(arr));
    }

    public static void addValue(int[] arr,int index,int value){
        for (int i = arr.length - 2; i >= index-1; i--) {
            arr[i+1] = arr[i];
        }
        arr[index-1] = value;
    }
}
```

删除元素

```java
    public static void main(String[] args) {
        //删除指定索引的元素
        int[] arr = {1,2,3,4,5,2,3,4342};
        System.out.println("原数组为："+ Arrays.toString(arr));
        Scanner sc = new Scanner(System.in);
        System.out.print("请输入你要删除的位置：");
        int index = sc.nextInt();

        deleteArrayValue(arr,index);
        System.out.println("现数组为："+Arrays.toString(arr));
    }

    public static void deleteArrayValue(int[] arr,int index){
        for (int i = index; i < arr.length; i++) {
            arr[i-1] = arr[i];
        }
        arr[arr.length - 1] = 0;
    }


public static void main(String[] args) {
        //删除某个元素
        //创建数组
        int[] arr = {1,2,3,4,5,4342};
        //遍历数组元素
        System.out.println("原数组为："+ Arrays.toString(arr));

        //输入想要删除的元素，如果不存在首先报出。
        Scanner sc = new Scanner(System.in);
        System.out.print("请输入你要删除的值：");
        int value = sc.nextInt();

        //判断要删除的值是否在数组中
        forArray(arr,value);

    }

    public static void forArray(int[] arr, int value){
        //增强型for循环遍历
        boolean flag = false;
        int index = -1;
        for (int i=0;i < arr.length; i++){
            if (value == arr[i]) {
                index  = i;
                flag = true;
        }
        }
        if (flag) {
            System.out.println("元素存在！");
            deleteArray(arr,index);
        }else {
            System.out.println("元素不存在！");
        }
    }

    public static void deleteArray(int[] arr, int index){
        for (int i = index+1; i < arr.length; i++) {
            arr[i-1] = arr[i];
        }
        arr[arr.length - 1] = 0;
        System.out.println("现数组为："+Arrays.toString(arr));
    }
```

详解main方法

1.main方法：程序的入口，在同一个类中，如果有多个方法，那么虚拟机就会识别main方法，从这个方法作为程序的入口

2.main方法格式严格要求：

```
pubilc static void main(String[] args){}

public static:  --修饰符，暂时用这个 ---面向对象详解
void：  --- 代表方法没有返回值，对应的类型为void
main：  --- 见名知意名字
String[] args   ---形参 ---不确定因素
```

3.问题：程序中是否可以有其他的方法也叫main方法？

可以，构成了方法的重载。

4.形参为String[] args 那么实参到底是什么？

```
        public static void main(String[] args) {
            //从侧面验证：
//            int[] arr2 = null;
//            System.out.println(arr2.length);Exception in thread "main" java.lang.NullPointerException: Cannot read the array length because "arr2" is null
//            int[] arr3 = new int[0];
//            System.out.println(arr3.length);
            int[] arr3 = new int[3];
            System.out.println(args.length);
            //从这结果来看，参数是String[],实参是 new String[] 类型
            //默认情况下，虚拟机在调用main方法时就是传入了一个长度为0的数组

            System.out.println(args.length);
            for (String str:args) {
                System.out.println(str);
            }
```

手动传入实参：

有特殊符号的时候可以加上 “”

没有特殊符号用空格隔开，

#### 可变参数：

```java
package S_5;

public class TestArray12 {

    /*
    1.可变参数：作用提供了一个方法，参数的个数是可变的
    int..num
    double..num
    boolean..num
    作用：解决了部分方法的重载问题

    2.可变参数是在JDK1.5之后加入的新特性
    3.方法的内部对可变参数的处理根数组一样
    4.可变参数和其他数据一起作为形参的时候，可变参数一定要放在最后
    5.我们自己在写代码的时候，建议不要使用可变参数
     */
    public static void main(String[] args) {
        method01(10);
        method01(10,123,23,13,21321,321);
        method01(10);
        method01(10);
    }

    public static void method01(int ...num)
    {
        System.out.println("--------");
        for(int i:num){
            System.out.println(i+"\t");
        }
        System.out.println();
    }
}
```



Arrays工具类的使用

```java
package S_5;

import java.util.Arrays;

public class TestArray13 {
    public static void main(String[] args) {
        //给定一个数组
        int[] arr  = {1,2,4,5,5,6,7,54,3,45,1,2,5,8,3,2,1};
        //toString:对数组进行遍历查看的，返回的是一个字符串，这个字符串比较好看。
        System.out.println(Arrays.toString(arr));

        //binarySearch:二分法查找：找出指定数组中的指定元素对应的索引
        //这个方法的使用前提：数组已经排好序
        Arrays.sort(arr);
        System.out.println(Arrays.toString(arr));
        System.out.println(Arrays.binarySearch(arr,4));

        int[] arr2=  {1,23,4,8,7,6,5};
        //copyof:完成数组的复制：
        int[] newArr = Arrays.copyOf(arr2,4);
        System.out.println(Arrays.toString(newArr));

        //copyOfRange:区间复制
        int[] newArr2 = Arrays.copyOfRange(arr2,1,4);
        System.out.println(Arrays.toString(newArr2));

        //equals:比较两个数组的值是否一样
        int[] arr3 = {1,2,3,4,5,6,7,8};
        int[] arr4 = {1,2,3,4,5,6,7,8};
        System.out.println(Arrays.equals(arr3,arr4));
        System.out.println(arr3==arr4); //比较的是数组的地址值


        //fill:数组的填充,将一个数填充为这个数组所有的值
        int[] arr5 = {1,2,3,4,5,6,7,8};
        Arrays.fill(arr5,10);
        System.out.println(Arrays.toString(arr5));}}
```

#### 数组的复制操作

```
    public static void main(String[] args) {
        //给一个源数组
        int[] srcArr = {11,22,33,44,5,64,3};
        //给一个目标数组
        int[] destArr = new int[7];

        //复制：
        System.arraycopy(srcArr, 0, destArr, 0, 7);
        System.out.println(Arrays.toString(destArr));
    }
```

#### 二维数组的定义和遍历

```
package S_5;

public class TestArray15 {
    public static void main(String[] args) {
        //定一个二维数组
        int[][] arr = new int[3][];

        int[] a1 = {1,2,3};
        arr[0] = a1;
        arr[1] = new int[] {4,5,6};
        arr[2] = new int[] {7,8,9,10};

        //读取6这个元素
        System.out.println(arr[1][2]);

        //对二维数组进行遍历
        //外层for，内层for
        for (int i = 0; i <= 2; i++) {
            for (int j = 0; j < arr[i].length; j++) {
                System.out.print(arr[i][j] +  "\t");
            }
            System.out.println();
        }

        //2.外层for，内层增强for
        for (int i = 0; i < arr[i].length; i++) {
            for(int num:arr[i]){
                System.out.print(num + "\t");
            }
            System.out.println();
        }

        //3.外层增强for循环+内层增强for循环
        for (int[] a:arr){
            for (int num:a){
                System.out.print(num + "\t");
            }
            System.out.println();
        }

        //4.外层增强。内部普通
        for (int[] a : arr) {
            for (int i = 0;i < a.length; i++)
            {
                System.out.print(arr[i] + "\t");
            }
            System.out.println();

        }
    }
}
```

二维数组的初始化

```
数组的初始化方式共有三种：静态初始化、动态初始化、默认初始化

静态初始化
除了用new关键字来产生数组以外，还可以直接在定义数组的同时就为数组元素分配空间并赋值。
eg:
int[][] arr = {{1},{23,4},5,63};
int[][] arr = new int[][]{{1},{23,4},5,63};


动态初始化
数组定义与为数组元素分配空间并赋值的操作分开进行。
eg:
int[][] arr = new int[3][];
arr[0]={1,2};
arr[1]={1,3};
arr[2]={1,4};

eg:
       int[][] arr = new int[3][2];
        //本质上：定义了一维数组，长度为3，每个数组"格子"中，有一个默认长度为2的数组。

        arr[1] = new int[]{1,2,3,4};

        //数组遍历：
        for (int[] a:arr){
            for (int num:a){
                System.out.print(num+"\t");
            }
            System.out.println();
        }
默认初始化
数组是引用类型，它的元素相当于类的实例变量，因此数组一经分配空间，其中的每个元素也被按照实例变量同样的方式被隐式的初始化。
int[][] arr = new int[3][2];   ---数组有默认的初始化值
数组有默认的初始化值：
要看是什么类型的数组：

```

## 第八章	面向对象

面向过程和面向对象的区别

```
面向过程：当事件比较简单的时候，利用面向过程，注重的是事件的具体的步骤/过程，注重的是过程中的具体行动。以函数为最小单位，考虑怎么做？
面向对象：注重“参与者"，将功能封装进对象，强调具备功能的对象，以类/对象为最小单位，考虑谁来做

面向对象


面向过程---面向对象，其实就是由执行者----指挥者的过程
二者相辅相成，并不是对立的，解决复杂问题，通过面向对象方法便与我们从宏观上把握事物之间复杂的关系，方便我们分析整个系统，具体到微观操作，仍然使用面向过程方式处理。
```

### 类和对象

1.万事万物皆对象

2.对象：具体的事物，具体的实体

类：对对象向上抽取出像的部分，形成类，类是抽象的，是一个模板。

3.一般在写代码时先创建类，在根据类创建对象

### 面向对象三个阶段：

1.面向对象分析OOA — Object Oriented Analysis

```
对象：张三、李四、你、我
抽取出一个类 ---人类

类里面有什么：
动词 -- 动态特性 --方法
名词 -- 静态特性 -- 属性
```

2.面向对象设计OOD — Object Oriented Design

```
先有类，再有对象：
类：人类： Person
对象：张三，李四，。。。
```

3.面向对象编程OOP — Object Oriented Programming

### 创建类

(1)属性（field 成员变量）

```
属性用于定义该类或该类对象包含的数据或者说静态特征。属性作用范围是整个类体。
属性定义格式：
[修饰符] 属性类型 属性名 = [默认值]；
```

（2）方法

```
方法用于定义该类或该类实例的行为特征和功能实现，方法是类和对象行为特征的抽象，方法很类似于面向过程中的函数，面向过程中，函数是最基本单位，整个程序由一个个函数调用组成。面向对象中，整个程序的基本单位是类，方法是从属于类和对象的。
[修饰符] 方法返回值类型 方法名(形参列表){
 // 语句；
}
void代表没有返回值，方法的作用：重用代码，封装功能，便于修改。
```

```java
public class Person {
    //名词--属性（注意：我们只把有需要的内容写到代码里，不相关的东西不要放在代码中）
    int age;   //年龄
    String name;   //名字
    double height; //身高
    double weight; //体重

    //动词 --方法
    //吃饭
    public void eat(){
        System.out.println("我喜欢吃饭");
    }

    //睡觉
    public void sleep(String address){
        System.out.println("我在" + address + "睡觉");
    }

    //自我介绍：
    public String introduce() {
        return "我的名字是：" + name +"，我的年龄是：" + age +",我的身高是："+ height + ",我的体重是：" +weight + ",";
    }
}
```



### 创建对象

```java
package S_1;

/**
 * @Auther: rain
 * @date: 2022/9/28 - 09 - 28 - 6:58 下午
 * @Description:
 * @version: 1.0
 */

public class Test {  //测试类
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //创建一个人类的具体的对象/实例：
        //创建一个对象，对象的名字是：zs
        //preson 属于引用数据类型
        //第一次加载类的时候，会进行类的加载，初始化创建对象的时候，对象的属性没有给赋值，有默认的初始化的值。
        Person zs = new Person();
        zs.name = "zhangsan";
        zs.height = 167.4;
        zs.weight = 67;
        zs.age = 23;

        //再创建一个对象
        //再次创建类的时候，就不会进行类的加载了
        Person ls = new Person();
        ls.name = "李四";
        ls.age = 23;
        ls.weight = 16.4;
        ls.height = 178.3;

        //对属性值进行读取
        System.out.println(ls.name);
        System.out.println(zs.name);


        //对方法进行操作：
        //不同的对象，属性有自己的特有的值，但是方法都是调用类中通用的方法。
        //属性：各个对象的属性是独立的
        //方法：各个对象的方法是共享的
        zs.eat();
        ls.eat();
        zs.sleep("教室");
        System.out.println(zs.introduce());
    }
}
```

### 局部变量和成员变量的区别

```
区别1:代码中位置不同
	成员变量：类中方法外定义的量
	局部变量：方法中定义的变量		代码块中定义的变量
```

```
区别2:代码的作用范围
	成员变量：当前类的很多方法
	局部变量：当前一个方法(当前代码块)
```

```
区别3:是否有默认值
	成员变量：有
	局部变量：没有
```



| 基本数据 | 默认值         |
| -------- | -------------- |
| Boolean  | Flase          |
| Char     | ‘\u0000’(null) |
| Byte     | (byte)0        |
| Short    | (short)0       |
| Int      | 0              |
| Long     | 0L             |
| Float    | 0.0f           |
| Double   | 0.0d           |

引用数据类型：null

```
区别4: 是否要初始化	
	成员变量：不需要，不建议初始化，后续使用的时候在赋值即可。
	局部变量：一定需要，不然直接使用的时候报错。
```

```
区别5:内存中位置不同
	成员变量：堆内存
	局部变量：栈内存
```

```
区别6:作用时间不同
	成员变量：当前对象从创建到销毁
	局部变量：当前方法从开始执行到结束执行
```

### 构造器 

```java
package com;

public class Person {

    //构造器：没有任何参数的构造方法--空参构造方法--空参构造器
    public Person(){
        age = 19;
        name = "zhangsan";
        height = 167.7;
    }

    //成员变量
    double height;
    int age;
    String name;

    //方法
    public void eat(){
        System.out.println("吃饭！");
    }
}

public class Test {
    public static void main(String[] args) {
        //创建一个Person类的对象

        //创建对象的过程：
        /*
        1.第一次遇到Person的时候，进行类的加载（只加载一次）
        2.创建对象，为这个对象在堆中开辟空间
        3.为对象进行属性的初始化动作

        new 关键字实际上是在调用一个方法，这个方法叫做构造器方法（构造器）
        调用构造器的时候，如果你的类中没有写构造器，那么系统会默认给你分配一个构造器，只是我们看不到
        构造器的格式：
        【修饰符】 构造器的方式（）{
        }
        构造器和方法的区别：
        1.没有方法的返回值类型
        2.方法体内部不能有return语句
        3.构造器的名字很特殊，必须根类名一样

        构造器的作用：不是为了创建对象，因为在调用构造器之前，这个对象就已经创建好了，并且属性有默认的初始化的值。
        调用构造器的目的是给属性进行赋值操作的。

        注意：我们一般不会在空构造器中进行初始化操作，因为那样的话每个对象的属性就一样了
        实际上，我们只要保证空构造器的存在就行了。里面不用写东西
        */
        Person p = new Person();
        System.out.println(p.age);
        System.out.println(p.height);
        System.out.println(p.name);

        Person p2 = new Person();
        System.out.println(p2.age);
        System.out.println(p2.height);
        System.out.println(p2.name);
    }
}
```

### 构造器的重载

```java
package com1;

/**
 * @Auther: rain
 * @date: 2022/9/28 - 09 - 28 - 7:56 下午
 * @Description:
 * @version: 1.0
 */

public class Person {
    /*
    1.一般保证空构造器的存在，空构造器中一般不会进行属性的赋值操作
    2.一般我们会重载构造器，在重载的构造器中进行属性赋值操作
    3.在重载构造器以后，假设空构造器忘写了。系统也不会给你分配默认的空构造器了，那么你要调用的时候就会报错了。
    4.在要表示对象的属性前加上this，来修饰，因为this代表的就是你创建的那个对象
     */
    //构造器：没有任何参数的构造方法--空参构造方法--空参构造器
    public Person(){

    }

//  public Person(int age, double height,String name)  error
    public Person(int a, double b,String c){
        //当形参名字根属性名字重合时，会出现就近原则
        this.height = b;
        this.age = a;
        this.name = c;
    }

    public Person(int a, double b){
        height = b;
        age = a;
    }

    //成员变量
    double height;
    int age;
    String name;

    //方法
    public void eat(){
        System.out.println("吃饭！");
    }
}
```

### 内存分析

代码1

```java
public class Person{
  int id;
  int age;
  
  public static void main(String[] args){
    Person p1 = new Person();
  }
}
```

代码2

```java
public class Person{
	int id;
	int age;
	String school;
  public Person(int a,int b,String c){
    	id=a;
    	age=b;
    	school=c;
  }
  public static void main(String[] args){
    Person p = new Person(1,20,"sss");
  }
}
```



代码3

```java
class Person {
    int id;
    int age;
    String school;
    Person(int a,int b,String c){
        id = a;
        age = b;
        school = c;
    }

    public void setAge(int a){
        age = a;
    }
}

public class Text{
    public static void main(String[] args){
        Test t = new Test();
        int age = 40;
        Person tom = new Person(1,20,"海淀");
        Person jack = new Person(2,440,"朝阳");
        t.change1(age);
        t.change2(com);
        t.change3(jack);
        System.out.println(age);
        System.out.println("id:" + jack.id + ",age:" + jack.age + ",school:" + jack.school);
    }

    public void change1(int i){
        i = 3344;
    }

    public void change2(int i) {
        p = new Person(3,22,"天赋");
    }    
    
    public void change2(int i) {
        p.setAge(66);
    }
}
```

### this的使用

this指代的是正在调用这个方法的对象，

```
[1] 创建对象的过程：
(1)在第一次遇到一个类的时候，对这个类要进行加载，只加载一次。
(2)创建对象，在堆中开辟空间
(3)对对象进行初始化操作，属性赋值都是默认的初始值
(4)new关键字调用构造器，执行构造方法，在构造器中对属性重新进行赋值
```

this关键字用法：

（1）this可以修饰属性：

总结：当属性名字和形参发生重名的时候，或者属性名字和局部变量重名的时候，都会发生就近原则，所以如果要是直接使用变量名字的话就指的是离的近的那个形参或者局部变量，这时候如果我想要表示属性的话，在前面要加上：this.修饰。

如果不发生重名问题的话，实际上你要是访问属性也可以省略this

```java
        //有参构造器
        public Person(int age,String name, double height){
            this(age,name);
            this.name = name;
            this.height = height;
        }

        //方法
    public void eat(){
            int age = 10;
            System.out.println(age); //指的是就近的age，
            System.out.println(this.age);//这里指代的就是当前对象的属性age，
    }
```

（2）this可以修饰方法

总结：在同一个类中，方法可以互相调用，this.可以省略不写

```java
        //方法
    public void eat(){
            int age = 10;
            this.play();
            System.out.println(age); //指的是就近的age，
            System.out.println(this.age);//这里指代的就是当前对象的属性age，
    }

    public void play(){
            System.out.println("玩电脑");
    }
```

（3）this可以修饰构造器

总结：同一个类中的构造器可以相互用this调用，注意：this修饰构造器必须放在第一行

```java
        //有参构造器
        public Person(int age,String name, double height){
            this(age,name);
            this.name = name;
            this.height = height;
        }

        public Person(int age,String name){
            this(age);
            this.name = name;
        }

        public Person(int age){
            this.age = age;
        }
```

### static

【1】static可以修饰：属性、方法、代码块、内部类。

【2】static修饰属性

```java
    //属性
    int id;
    static int sid;

    //这是一个main方法，是程序的入口
    public static void main(String[] args) {
        //创建一个Test类的具体的对象
        Test t1 = new Test();
        t1.id = 10;
        sid = 10;

        Test t2 = new Test();
        t2.id = 20;
        sid = 20;

        Test t3 = new Test();
        t3.id = 30;
        sid = 30;

      //读取属性的值
        System.out.println(t1.id);
        System.out.println(t2.id);
        System.out.println(t3.id);

        System.out.println(sid);
        System.out.println(sid);
        System.out.println(sid);
    }
```

一般官方的推荐访问方式，可以通过类名.属性名的方式来访问

Test.sid=100;   System.out.print(test.sid);

static修饰属性总结：

```
（1）在类加载的时候一起加载入方法区中的静态域中
(2) 先于对象存在
(3) 访问方式：对象名.属性名。类名.属性名 
属性：
静态属性 (类变量)
非静态属性(实例变量)
```

【3】static修饰方法

```java
package com4;

/**
 * @Auther: rain
 * @date: 2022/10/8 - 10 - 08 - 2:04 下午
 * @Description:
 * @version: 1.0
 */

public class Demo {
    int id;
    static int sid;

    public void a(){
        System.out.println(sid);
        System.out.println(id);
        System.out.println("-----a");
    }

    //1.static和public都是修饰符，并列的没有先后顺序，先写谁后写谁都行
    static  public void b() {
//        System.out.println(this.id); 4.在静态方法中不能使用this.关键字
        //a();  //3.在静态方法中不能访问非静态的方法
        System.out.println(sid);
//        System.out.println(id);//2,静态方法中不能访问非静态的属性
        System.out.println("-----b");
    }

    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //5.非静态的方法可以用对象名.方法名来调用
        Demo demo = new Demo();
        demo.a();
        //6.静态的方法可以用  对象名.方法名去调用， 也可以用类名.方法名来调用
        Demo.b();
        demo.b();
      
        b();//在类中可以直接调用
    }
}
```

内存分析

![截屏2022-10-09 下午8.42.39](/Users/rain/Desktop/截屏2022-10-09 下午8.42.39.png)



### 代码块

【1】类的组成：属性、方法、构造器、代码块、内部类

【2】代码块分类：普通块、构造块、静态块、同步块（多线程）

【3】代码：

```java
package com5_msb6;

/**
 * @Auther: rain
 * @date: 2022/10/8 - 10 - 08 - 2:20 下午
 * @Description:
 * @version: 1.0
 */

public class Test {
    //属性
    int a;
    static int b;

    //方法
    public void a(){
        System.out.println("------a");
        {
            //普通块限制类局部变量的作用范围
            System.out.println("这是普通块");
            System.out.println("----------");
            int num = 1;
            System.out.println(num);
        }
    }
    static public void b(){
        System.out.println("------b");
    }

    //构造器
    public Test(int a){
        this.a = a;
    }

    public Test(){
        System.out.println("这是空构造器");
    }

    //构造块
    {
        System.out.println("这是构造块！");
    }

    //静态块
    static{
        System.out.println("这是静态块");
        //在静态块中只能访问：静态属性、静态方法
        System.out.println(b);
        b();
    }

    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        Test t= new Test();
        t.a();
    }
}
```

总结：

```
1.代码执行顺序：
最先执行静态块，只在类加载的时候执行一次，所以一般写实战项目：创建工厂，数据库的初始化信息都放入静态块，一般用于执行一些全局性的初始化操作。

在执行构造块
在执行构造器
在执行方法中的普通块。
```

### 三大特性

#### 封装 (Encapluation）

通过属性感受封装：

```java
package com_msb_test01;

/**
 * @Auther: rain
 * @date: 2022/10/8 - 10 - 08 - 2:43 下午
 * @Description:
 * @version: 1.0
 */

public class Girl {

    //属性
    private int age;

    //读取年龄
    public int duquAge(){
        return age;
    }

    //设置年龄
    public void shezhiAge(int age){
        if (age >= 30) {
            this.age = 18;
        }else {
            this.age = age;
        }
    }
}
```

```java
package com_msb_test01;

/**
 * @Auther: rain
 * @date: 2022/10/8 - 10 - 08 - 2:41 下午
 * @Description:
 * @version: 1.0
 */

public class Test {

    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //创建一个girl类的对象
        Girl g = new Girl();
        g.shezhiAge(18);
        System.out.println(g.duquAge());
    }
}
```

```java
上面的代码，对于属性age来说，加了修饰符private，这样外界对它的访问就受到了限制，现在我还想加上其他的限制条件，但是在属性本身上没有办法再加了，所以我门通过定义方法来进行限制条件的添加。
以属性案例：
进行封装
(1) 将属性私有化，被private属性修饰 ---加入权限修饰符
一旦加入了权限修饰符，其他人就不可以随意的获取这个属性
(2) 提供public修饰的方法让别人来访问/使用
(3) 即使外界可以通过方法来访问属性，但是也不能随意访问，因为咱们在方法中可以加入限制条件。
```

5.实际开发中，方法一般会写成setter，getter方法：

可以利用idea快捷键：

6.加深练习：

```java
package commsbtest02;

/**
 * @Auther: rain
 * @date: 2022/10/8 - 10 - 08 - 3:21 下午
 * @Description:
 * @version: 1.0
 */

public class Student {

    //属性
    private String name;
    private int age;
    private String sex;


    //构造器
    public Student(){

    }

    public Student(String name, int age, String sex) {
        this.name = name;
        this.age = age;
        this.sex = sex;
    }

    //name的构造方法
    public void setName(String name){
        this.name = name;
    }

    public String getName() {
        return this.name;
    }

    //age的构造方法
    public void setAge(int age){
        this.age = age;
    }

    public int getAge() {
        return this.age;
    }

    //sex的构造方法
    public void setSex(String sex){
        if("男" == sex || "女" == sex){
            this.sex = sex;
        }else{
            this.sex = "男";
        }

    }

    public String getSex() {
        return this.sex;
    }

}


package commsbtest02;

/**
 * @Auther: rain
 * @date: 2022/10/8 - 10 - 08 - 3:21 下午
 * @Description:
 * @version: 1.0
 */

public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //创建一个student对象
        Student s1 = new Student();
        s1.setName("张三");
        s1.setAge(17);
        s1.setSex("sssss");
        System.out.println(s1.getName() + "-----" + s1.getAge() + "------" + s1.getSex());

        Student s2 = new Student("萌萌", 18, "女");
        System.out.println(s2.getName() + "-----" + s2.getAge() + "------" + s2.getSex());
    }
}
```



#### 继承 

【1】类是对对象的抽象：

【2】继承是对类的抽象：

继承关系，是在合理的范围中进行抽取，抽取出父类的关系

【3】代码层面的理解：

```java
package com.msb.test03;

/**
 * @Auther: rain
 * @date: 2022/10/8 - 10 - 08 - 4:22 下午
 * @Description:
 * @version: 1.0
 */

public class Person {
    //属性
    private int age;
    private String name;
    private double height;

    //构造方法
    public void setName(String name) {
        this.name = name;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public void setHeight(double height) {
        this.height = height;
    }

    public String getName() {
        return name;
    }

    public double getHeight() {
        return height;
    }

    public int getAge() {
        return age;
    }

    //方法
    public void eat(){
        System.out.println("吃饭");
    }

    public void sleep(){
        System.out.println("睡觉");
    }
}

```

```java
package com.msb.test03;

/**
 * @Auther: rain
 * @date: 2022/10/8 - 10 - 08 - 4:28 下午
 * @Description:
 * @version: 1.0
 */

public class Student extends Person{
    //属性
    private int sno;//学号

    public Student() {

    }

    public void setSno(int sno) {
        this.sno = sno;
    }

    public int getSno() {
        return sno;
    }

    public void study(){
        System.out.println("学生也可以学习");
    }
}
```

```java
package com.msb.test03;

/**
 * @Auther: rain
 * @date: 2022/10/8 - 10 - 08 - 4:45 下午
 * @Description:
 * @version: 1.0
 */

public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        Student s = new Student();
        s.setAge(17);
        s.setSno(1234553);
        s.setName("张三");
        s.setHeight(165.6);

        System.out.println(s.getAge() + "----" + s.getSno() + "-----" + s.getName()+ "----" + s.getHeight());
    }
}
```

【4】继承的好处：提高代码的复用性

父类定义的内容，子类可以直接拿过来用就可以了，不用代码上重复定义

需注意：父类private的内容，子类也继承了，只是因为封装特性阻碍了直接调用，可以通过方法间接调用。

【5】总结：

```
（1）继承关系：
父类/基类/超类
子类/派生类
子类继承父类一定在合理的范围内进行继承
(2）继承的好处
1.提高了代码的复用性，父类定义的内容，子类可以直接拿过来用就可以了，不用代码上反复重复定义了
2.便于代码的发展
3.为了以后多态的使用。是多态的前提。
(3) 父类private修饰的内容，子类也继承过来了
(4)一个父类可以有多个子类
(5)一个子类只能有一个直接父类。
```

##### 权限修饰符

|           | 同一个类 | 同一个包 | 子类 | 所有类 |
| --------- | -------- | -------- | ---- | ------ |
| private   | 1        |          |      |        |
| default   | 1        | 1        |      |        |
| protected | 1        | 1        | 1    |        |
| public    | 1        | 1        | 1    | 1      |

[1]private

权限：同一个包的同一个类

```java
public class A {
    private int age;

    public void eat(){
        System.out.println(age);
        age = 10;
    }
}  同一个类中可以访问

public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        A a = new A();
//        a.age; 私有属性不能访问
    } 不同一个类不能访问
```

【2】default：缺省修饰符

权限：同一个包下的其他类

【3】protected

##### 方法的重写

[1]重写：

发生在子类和父类中，当子类对父类提供的方法不满意的时候，要对父类的方法进行重写。

【2】重写有严格的格式要求：

子类的方法名字和父类必须一致，参数列表（个数，类型，顺序）也必须和父类一致

【3】代码

```java
父类
public class Person {
    public void eat(){
        System.out.println("吃食物");
    }
}
子类
public class Student extends Person{
    @Override
    public void eat() {
        System.out.println("-----1");
    }
}
实现类
public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        Student s = new Student();
        s.eat();
    }
}
```

【4】内存分析

【5】重载和重写的区别：

重载：在同一个类中，当方法名相同，形参列表不同的时候，多个方法构成了重载。

重写：在不同的类中，子类对父类提供的方法不满意的时候，要对父类的方法进行重写。

|      | 英文     | 位置不同   | 修饰符 | 返回值                   | 方法名   | 参数     | 抛出异常 | 方法体 |
| ---- | -------- | ---------- | ------ | ------------------------ | -------- | -------- | -------- | ------ |
| 重载 | overload | 同一类中   | 无关   | 无关                     | 必须相同 | 必须不同 | 无关     | 不同   |
| 重写 | override | 子类父类中 | 无关   | 父类的返回值类型大于子类 | 必须相同 | 必须相同 | 小于等于 | 不同   |

##### super

[1] super指的是：父类

【2】super可以修饰属性，可以修饰方法

在子类的方法中，可以通过super.属性	super.方法的方式，显示的去调用父类提供的属性，方法。在通常情况下，super.可以省略不写。

```java
父类
public class Person {
    int age=10;

    public void eat() {
        System.out.println("吃饭");
    }

    public void sleep() {
        System.out.println("睡觉");
    }
}
子类
public class Student extends Person{
    double score;
    int age = 20;

    public void study() {
        System.out.println("学习");
    }

    @Override
    public void eat(){
        System.out.println("---1");
    }

    public void a(){
        System.out.println(/*super.*/age);
        /*super.*/eat();
    }
}
```

在特殊情况下，当子类和父类的属性重名时，你想要使用父类的属性，必须加上修饰符super.，只能通过super.属性来调用

在特殊情况下，当子类和父类的属性重名时，你想要使用父类的方法，必须加上修饰符super.，只能通过super.属性来调用

在特殊情况下，super.就不可以省略不写。

```java
public class Student extends Person{
    double score;
    int age = 20;

    public void study() {
        System.out.println("学习");
    }

    @Override
    public void eat(){
        System.out.println("这个是子类");
    }

    public void a(){
        System.out.println(/*super.*/age);
        System.out.println("子类的 "+this.age);
        System.out.println("父类的 "+super.age);
        /*super.*/eat();
        this.eat();
        super.eat();
    }
}
```

[3] super修饰构造器

其实我们平时写的空构造器的第一行都有：super（） —作用：调用父类的空构造器，只是我们一般都省略不写（所以构造器的第一行默认情况下都有super();但是一旦你的构造器显示的使用了super调用父类构造器，那么第一行都有super(),可以省略不写）

```java
public class Student extends Person{
    double score;
    public Student(){
        /*super();*/
    }
}
```

如果构造器中已经显示的调用super父类构造器，那么它的第一行就没有默认分配的super（）；

```java
    public Student(int age, String name, double score){
        //super();
        /*this.age = age;
        this.name = name;*/
        /*super.age = age;
        super.name = name;*/
        super(age,name);  //利用super调用父类构造器
        this.score = score;
    }
```

在构造器中，super调用父类构造器和this调用子类构造器只能存在一个，两者不能共存：因为super修饰构造器要放在第一行,this修饰构造器也要放在第一行。

```java
    public Student(int age, String name, double score){
        super(age,name);  //利用super调用父类构造器
        this(score);
        //super();
        /*this.age = age;
        this.name = name;*/
        /*super.age = age;
        super.name = name;*/
    }
```

【4】以后写代码，构造器的生成可以使用快捷键IDEA，ctrl + insert

##### 继承条件下构造方法怎么运行的

##### Object类

所以类都直接或间接的继承自Object类，Object类是所以Java类的根基类。也就意味着所有的Java对象都拥有Object类的属性和方法。如果在类的声明中未使用extends关键字指明其父类，则默认继承Object类。

###### 【1】 toString()方法

返回该对象的字符串显示。

方法的原理

```
getClass().getName() + "@" + Integer.toHexString(hashCode())
com.msb.test01.Student  @      54bedef2
全限定路径：包名+类名的完整表示       hasCode() ---》将对象在堆中的地址进行哈希算法，返回一个码 --》哈希吗。将这个哈希吗传入到中，返回一个字符串，这个字符串是一个十六进制的数对应的字符串

对象。-- 堆中分配地址 -- 进行哈希吗操作 -- 哈希吗 -- 转成十六进制 -- String

```

现在，使用toString()方法的时候，打印出来的东西“不好看”，对于其他人来说不友好，可读性不好，我们现在想知道对象的信息。，名字、年龄等

```java
    public static void main(String[] args) {
        int a = 10;

        System.out.println(a);
        //创建一个Student类的具体的实例
        Student s = new Student("张三",17,165.5);
        System.out.println(s);  //com.msb.test01.Student@54bedef2
        System.out.println(s.toString());   //com.msb.test01.Student@54bedef2
    }
```

出现的问题：子类Student对父类Object提供的toString()方法不满意，进行重写。

```java
    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", height=" + height +
                '}';
    }
```

可使用快捷键 ：ctrl+insert



###### 【2】Equals()方法

```java
    package com.msb.test02;

import java.util.Objects;

/**
 * @Auther: rain
 * @date: 2022/10/9 - 10 - 09 - 4:19 下午
 * @Description:
 * @version: 1.0
 */

public class Phone {  //手机类
    //属性
    private String brand;  //品牌型号
    private double price;  //价格
    private int age;       //生产年份

    public void setBrand(String brand) {
        this.brand = brand;
    }

    public void setPrice(double price) {
        this.price = price;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getBrand() {
        return brand;
    }

    public double getPrice() {
        return price;
    }

    public int getAge() {
        return age;
    }

  	//构造器
    public Phone() {
    }

    public Phone(String brand, double price, int age) {
        this.brand = brand;
        this.price = price;
        this.age = age;
    }

    @Override
    public int hashCode() {
        return Objects.hash(brand, price, age);
    }

    //对equals方法进行重写
    @Override
    public boolean equals(Object obj){  //Object obj = new Phone();
        //将Obj转为Phone类型
        Phone other = (Phone) obj;   //向下转型，为了获取子类特有的内容
        if (this.getBrand() == other.getBrand() || this.getAge() == other.getAge() || this.getPrice() == other.getPrice() ) {
            return true;
        }
        return false;
    }

}
    
    
    public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //创建Phone类的对象
        Phone p1 = new Phone("华为P20",2133.2,2020);
        Phone p2 = new Phone("华为P20",2133.2,2020);
        //比较两个对象：p1和p2对象
        // ==的作用：比较左右两侧的值是否相等，相等返回true，否则返回false
        System.out.println(p1==p2); //对于引用数据类型来说，比较的是地址值，

        //Object类提供了一个方法：equals方法，比较对象具体的内容是否相等。
        boolean flag = p1.equals(p2); //点进源码发现：底层依旧比较的是 ==，比较的还是地址值
        System.out.println(flag);

    }
```

代码优化（使用instanceof运算符）

```java
    //对equals方法进行重写
    @Override
    public boolean equals(Object obj){
        /*
        instanceof运算符：
        a instanceof b
        判断a对象是否是b这个类的实例，如果是，返回true，如果不是返回false
        */
        if (obj instanceof Phone) { //属于Student类的对象
            //将Obj转为Phone类型
            Phone other = (Phone) obj;
            if (this.getBrand() == other.getBrand() || this.getAge() == other.getAge() || this.getPrice() == other.getPrice() ) {
                return true;
            }
        }
        return false;
    }
```

利用IDEA自动生成equals方法

```
    @Override
    public boolean equals(Object o) {
        if (this == o) {
            return true;
        }
        if (o == null || getClass() != o.getClass()) {
            return false;
        }
        Phone phone = (Phone) o;
        return Double.compare(phone.price, price) == 0 && age == phone.age && Objects.equals(brand, phone.brand);
    }
```



##### 类和类的关系

代码

```java
package com.msb.test03;

/**
 * @Auther: rain
 * @date: 2022/10/9 - 10 - 09 - 5:03 下午
 * @Description:
 * @version: 1.0
 */

public class Boy {
    //属性
    String name;
    int age;

    //方法
    public void Buy(){
        System.out.println("买东西");
    }

    //构造器

    public Boy() {
    }

    public Boy(String name,int age) {
        this.age = age;
        this.name = name;
    }
}


package com.msb.test03;

/**
 * @Auther: rain
 * @date: 2022/10/9 - 10 - 09 - 5:05 下午
 * @Description:
 * @version: 1.0
 */

public class Gril {
    //属性
    int age;
    String name;
    double height;

    Mom m;

    //方法
    //谈恋爱的方法
    public void love(Boy b){  //参数是引用数据类型Boy
        System.out.println("我男朋友的名字是：" + b.name + ",我男朋友的年龄是；" + b.age);
        b.Buy();
    }

    //构造器

    //女孩根妈妈聊天
    public void wechat(){
        m.say();
    }



    public Gril() {
    }

    public Gril(int age, String name, double height) {
        this.age = age;
        this.name = name;
        this.height = height;
    }
}


package com.msb.test03;

/**
 * @Auther: rain
 * @date: 2022/10/9 - 10 - 09 - 5:12 下午
 * @Description:
 * @version: 1.0
 */

public class Mom {
    //方法
    public void say() {
        System.out.println("听妈妈的话！");
    }
}


package com.msb.test03;

/**
 * @Auther: rain
 * @date: 2022/10/9 - 10 - 09 - 5:06 下午
 * @Description:
 * @version: 1.0
 */

public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        Boy boy1 = new Boy("张三",41);
        Gril gril1 = new Gril(18,"xixi",176.4);

        //谈恋爱
        gril1.love(boy1);

        gril1.m = new Mom();
        gril1.wechat();
    }
}

```

总结

```
[1]面向对象的思维：找参与者，找女孩类，找男孩类
[2]体会了什么叫方法的形参，什么叫方法的实参：
[3]类和类可以产生关系：
(1)将一个类作为另一个类中的方法的形参
(2)将一个类当作另一个的属性
```







#### 多态

一个父类可以被子类创建，子类继承，或实现了父类中的所有方法。在java中，多态是指使用子类对象去创建父类对象

 一般的使用方法： 父类 变量名 = new 子类名();

多态的理解：

在创建一个新的对象时，调用方法看右边，如果右边类中没有，则会向上寻找方法。在使用成员变量时，会先在左边的类中查找，没有则向上查找父类变量。

【1】多态跟属性无关，多态值的是方法的多态，而不是属性的多态。

【2】案例：

```java
父类：
public class Anmial {
    public void shout() {
        System.out.println("我是动物");
    }
}
子类：
public class Cat extends Anmial{
    //喊叫方法
    @Override
    public void shout(){
        System.out.println("喊叫");
    }

    public void atch(){
        System.out.println("会抓人");
    }
}

public class Pig extends Anmial{
    @Override
    public void shout() {
        System.out.println("我是小猪，我会嗯嗯");
    }
}

public class Dog extends Anmial{
    @Override
    public void shout(){
        System.out.println("汪汪叫");
    }
    public void play(Dog dog) {
        System.out.println("女孩根狗玩");

    }
}

女孩类
public class Gril {
//    public void play(Cat cat) {
//        System.out.println("女孩根猫玩耍");
//    }
//    public void play(Dog dog){
//        System.out.println("女孩根狗玩耍");
//    }

    public void play(Anmial an){
        an.shout();
    }
}
测试类：
public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //创建一个猫对象
        Cat cat = new Cat();
        //创建一个女孩对象
        Gril gril = new Gril();
        //调用女孩类玩法玩
//        gril.play(cat);

        Dog d = new Dog();
//        gril.play(d);

        Pig p = new Pig();
        Anmial a = p;
        gril.play(a);
    }
}
```

【3】总结：

```
(1)先有父类，再有子类， -- 继承		先有子类，再有父类 --泛化

(2)什么是多态：
多态就是多种状态：同一个行为，不同的子类表现出来不同的形态
多态指的就是同一个方法调用，然后由对象不同或产生不同的行为。

(3)多态的好处：
为了提供代码的好处，符号面向对象的设计原则：开闭原则
开闭原则：指的就是扩展是开放的，修改是关闭的。
注意：多态可以提高扩展性，但是扩展性没有达到最好，以后会学习反射，

(4)多态的要素：
一，继承：Cat extends Animal , Pig extends Animal, Dod extends Animal
二，重写：子类对父类的shout方法重写
三，父类引用子类的对象

1.Pig p = new Pig();
2.Animal an = p;

将上面的代码合为一句话：
Animal an = new Pig();
=左侧：编译器的类型
=右侧：运行期的类型

Animal an = new Pig():
g.play(an);

1.    public void play(Anmial an){ //Animal an = an = new Pig()
2.        an.shout();
3.    }
```

上面的代码，也是多态的一种非常常见的应用场合：父类当方法的形参，然后传入的是具体的子类的对象，然后调用同一个方法，根据传入的子类的不同展现出来的效果也不同，构成了多态。

##### 向上转型，向下转型

```java
父类：
public class Anmial {
    public int age;

    public void shout() {
        System.out.println("我是动物");
    }
}
子类：
public class Pig extends Anmial{
    public double weight;


    @Override
    public void shout() {
        System.out.println("我是小猪，我会嗯嗯");
    }

    public void eat(){
        System.out.println("猪喜欢吃");
    }
}
```

测试类

```
    public static void main(String[] args) {
        Pig p = new Pig();
        Anmial an = p;  //转型：向上转型
        an.shout();

        an.eat();
        an.age = 9;
        an.weight = 88.7;
```

![截屏2022-10-09 下午8.39.30](/Users/rain/Desktop/截屏2022-10-09 下午8.39.30.png)

```java
    public static void main(String[] args) {
        Pig p = new Pig();
        Anmial an = p;  //转型：向上转型
        an.shout();

        //加入转型的代码
        //将Animal转为Pig类型
        Pig pig = (Pig)an; //转型：向下转型
        pig.eat();
        pig.age = 10;
        pig.weight = 77.7;
    }
```

![截屏2022-10-09 下午8.38.32](/Users/rain/Desktop/截屏2022-10-09 下午8.38.32.png)

思考之前的equals方法。

    @Override
    public boolean equals(Object obj){  //Object obj = new Phone();
        //将Obj转为Phone类型
        Phone other = (Phone) obj;   //向下转型，为了获取子类特有的内容
        if (this.getBrand() == other.getBrand() || this.getAge() == other.getAge() || this.getPrice() == other.getPrice() ) {
            return true;
        }
        return false;
    }
##### 简单工厂设计模式

不仅可以使用父类实现方法的形参，还可以使用父类做方法的返回值类型，真实返回的对象可以是该类的任意一个子类对象，简单工厂模式的实现，它是解决大量对象创建问题的一个解决方案，将创建和使用分开，工厂负责创建，使用者直接调用即可，简单工厂模式的基本要求是：

- 定义一个static方法，通过类名直接调用
- 返回值类型是父类类型，返回的可以是任意子类类型
- 传入一个字符串类型的参数，工厂根据参数创建对应的子类产品

代码实现：

```java
public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {

        Gril g = new Gril();

        Animal an = PetStore.getAnimal("狗");
        g.play(an);
    }
}
```

```java
package com.msb.test01;

/**
 * @Auther: rain
 * @date: 2022/10/9 - 10 - 09 - 8:49 下午
 * @Description: 简单工厂设计模式
 * @version: 1.0
 */

public class PetStore {
    //方法：提供动物
    public static Animal getAnimal(String petName) {
        Animal an = null;

        if ("猫".equals(petName)) {
            an = new Cat();
        }
        if ("狗".equals(petName)) {
            an = new Dog();
        }
        if ("猪".equals(petName)) {
            an = new Pig();
        }

        return an;
    }
}
```

### final关键字

【1】修饰变量：

```java
package com.msb.test02;

import com.msb.test01.Dog;

/**
 * @Auther: rain
 * @date: 2022/10/9 - 10 - 09 - 9:15 下午
 * @Description:
 * @version: 1.0
 */

public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //第一中情况
        //final修饰一个变量，变量的值不可以改变，这个变量也变成了一个字符常量，约定俗成的规定：名字大写
        final int A = 20;  //final修饰基本数据类型
        //A = 10; 报错

        //第二种情况
        final Dog d= new Dog();  //final修饰引用数据类型，那么地址值就不可以改变
        //d = new Dog();  //地址值不可以改变
        d.age = 10;
        d.weight = 13.3;

        //第三种情况
//        a();
        final Dog d2 = new Dog();
        a(d2);
        //第四种情况
        b(d2);
    }

    public static void a(Dog d) {
        d = new Dog();
    }

    public static void b (final Dog d){ //d被final修饰，指向不可改变
//        d = new Dog();
    }
}
```

【2】修饰方法：

一旦在父类中使用final修饰方法，那么子类就不能够重写这个方法

```java
public class Person {
    public final void eat(){
        System.out.println("吃东西");
    }
}

class Student extends Person {
    @Override
    public void eat() {
        super.eat();
    }
}
```



【3】修饰类

final修饰类，代表没有子类，该类不可以继承：一旦一个类被final修饰，那么里面的方法也没有必要用final修饰了（final可以省略不写）

```java
public final class Person {
    public final void eat(){
        System.out.println("吃东西");
    }
}

class Student extends Person {
    @Override
    public void eat() {
        super.eat();
    }
}
```

【4】案例：JDK提供的Math类：

（1）使用Math类的时候无需导包，直接使用即可：

```java
package java.lang;
```

(2)Math类没有子类，不能被其他类继承：

```java
public final class Math
```

（3）里面的属性全部被final修饰，方法也是别final修饰的，只是省略不写，原因：子类没有必要重写。

（4）外界不可以创建对象：

Math m = new Math();

```java
/**
 * Don't let anyone instantiate this class.
 */
private Math() {}
```

(5) 发现Math类中的所有的属性，方法都被static修饰，那么不用创建对象去调用，只能通过类名.属性名，类型.方法名 去调用。



### 抽象类、抽象方法

【1】抽象类和抽象方法的关系：

```
一个抽象类中可以有0-n个抽象方法
```

【2】抽象类作用：

在抽象类中定义抽象方法，目的是为了为子类提供一个通用的模版，子类可以在模版的基础上进行开发，先重写父类的抽象方法，然后可以扩展子类自己的内容，抽象类设计避免了子类设计的随意性，通过抽象类，子类的设计变得更加严格，进行某些程度上的限制，是子类更加通用。

【3】 代码

```java
package com.msb.test03;

/**
 * @Auther: rain
 * @date: 2022/10/10 - 10 - 10 - 11:06 上午
 * @Description:
 * @version: 1.0
 */

//5.一个抽象类中可以有0-n个抽象方法
//4.一个类中如果有方法是抽象方法，那么这个类也要变成一个抽象类。§
public abstract class Person {

    //1.在一个类中，会有一类方法，子类对这个方法非常满意，无需重写，直接使用
    public void eat(){
        System.out.println("一顿不出饿的湖");
    }

    //2.在一个类中，会有一类方法，子类这个方法永远不满意，会对这个方法进行重写
    //3.一个方法的方法体去掉，然后被abstract修饰，那么这个方法就变成了一个抽象方法
    public abstract void say();
    public abstract void play();
}

//6.抽象类可以被其他类继承
//7.一个类继承一个抽象类，那么这个类可以变成抽象类
//8.一般子类不会加abstract修饰，一般会让子类重写父类中的抽象方法
//9。子类继承抽象类，必须重写全部的抽象方法
//10，子类如果没有重写父类全部的抽象方法，那么子类也可以变成一个抽象类。
class Student extends Person {

    @Override
    public void say() {
        System.out.println("说话");
    }

    @Override
    public void play() {
        System.out.println("玩游戏");
    }
}

class Demo{
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //11.抽象类不可以创建对象：
//        Person p = new Person();

        //12.创建子类对象
        Student s =new Student();

        //13.多态的写法，父类引用指向子类对象
        Person p = new Student();
        p.say();
        p.play();
    }
}
```

【4】面试题：

（1）抽象类不能创建对象，那么抽象类中是否有构造器？

抽象类中一定有构造器，构造器的作用：是给子类初始化对象的时候先super调用父类的构造器。

（2）抽象类是否可以被final修饰？

不能被final修饰，因为抽象类设计的初衷就是给子类继承用的，要是被final修饰了这个抽象类了，就不存在继承了，就没有子类。

### 接口

【1】接口声明格式：

【访问修饰符】interface 接口名 【extends 父接口1，父接口2…】{

​	常量定义：

​	方法定义：

}

【2】代码：

```java
package com.msb.test04;

/**
 * @Auther: rain
 * @date: 2022/10/10 - 10 - 10 - 2:03 下午
 * @Description:
 * @version: 1.0
 */

/*
* 1.类是类，接口是接口，它们是同一层次的概念。
* 2.接口中没有构造器
* 3.接口如何声明：interface
* 4.在JDK1.8之前，接口中只有两部分内容：
*   （1）常量：固定修饰符：public static final
*    (2) 抽象方法：固定修饰符：public static abstract
*   注意：修饰符可以省略不写，
* */
public interface Testtonet {
    //常量：
    public static final int NUM = 10;


    //抽象方法：
    public abstract boolean a();
    public abstract void b(int num);
    public abstract int c(String name);

}

interface Test02{

    void e();
    void f();
}

/*
5.类和接口的关系是什么？ 实现关系，类实现接口：
6.一旦实现一个接口，那么实现类要重写接口中的全部的抽象方法
7.如果没有全部重写抽象方法，那么这个类可以变成一个抽象类
8.Java只有单继承，Java还有多实现
一个类继承其他类，只能直接继承一个父类，但是实现接口可以实现多个接口
9.写法：先继承，再实现：extends .... implements ....
 */

class Student implements Testtonet,Test02 {
    @Override
    public boolean a() {

        return false;
    }

    @Override
    public void b(int num) {

    }

    @Override
    public int c(String name) {
        return 0;
    }

    @Override
    public void e() {

    }

    @Override
    public void f() {

    }
}


class Test{
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //10.接口不是创建对象
//        Testtonet t = new Testtonet();
        Testtonet t = new Student();
        Student s = new Student();

        //11.接口中常量如何访问：
        System.out.println(Testtonet.NUM);
        System.out.println(s.a());
        s.b(10);
    }
}
```

【3】接口的作用是什么？

定义规则，只是根抽象类不同地方在哪？它是接口不是类

接口定义好规则之后，实现类负责实现即可。

【4】

继承：子类对父类的继承

实现：实现类对接口的实现

手机不是照相机

继承：手机 extend 照相机。“is-a”的关系，手机是一个照相机

上面的写法不好：

实现：手机 implement 拍照功能，  “has-a”的关系，手机具备照相的能力

案例： 飞机、小鸟、风筝

定义一个接口：Flyable

【5】多态的应用场合：

（1）父类当作方法的形参，传入具体的子类的对象

（2）父类当作方法的返回值，返回的是具体的子类的对象

（3）接口当作方法的形参，传入具体的实现类的对象

（4）接口当作方法的返回值，返回的是具体的实现类的对象

【6】抽象类和接口的区别：



#### JDK1.8之前新增的内容

在JDK1.8之前：接口中只有两部分内容

（1）常量：固定修饰符，public static final

（2）抽象方法：固定修饰符:public abstract 

在JDK1.8之前：接口中新增非抽象方法

（1）被public default 修饰的抽象方法

注意1：default 修饰符必须要加上，否则会报错

注意2:  实现类中要是想重写接口中的非抽象方法，那么default修饰符必须不能加，否则出错。

```java
package com.msb.test05;

/**
 * @Auther: rain
 * @date: 2022/10/10 - 10 - 10 - 8:26 下午
 * @Description:
 * @version: 1.0
 */

public interface Person {
    //属性
    public final String name = null;

    //抽象方法
    public abstract void a();
    public abstract void b();

    //被public default修饰的非抽象方法
    public default void c(){
        System.out.println("被public default修饰的非抽象方法----c");
    }
}

class Students implements Person {

    @Override
    public void a() {
        System.out.println("这是实现了Person接口的抽象方法---a");
    }

    @Override
    public void b() {
        System.out.println("这是实现了Person接口的抽象方法---b");
    }

    public void eat(){
        System.out.println("这是实例方法---eat");

        //用一下接口中的c方法
        c();

        Person.super.c();
    }

    @Override
    public void c(){
        System.out.println("这是实现了Person接口的抽象方法---c");
    }
}

class A extends Students{
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        A a = new A();
        a.eat();
        a.a();
        a.b();
        a.c();
    }}
```

（2）静态方法：

注意1：静态方法的static修饰符不能不省略

注意2: 静态方法不能重写

```
package com.msb.test06;

/**
 * @Auther: rain
 * @date: 2022/10/10 - 10 - 10 - 8:38 下午
 * @Description:
 * @version: 1.0
 */

public interface TestInterface {
    //常量
    public static final int NUM = 10;

    //抽象方法
    public abstract void a();
    public abstract void b();


//    public default 修饰的非抽象方法
    public default void c(){
        System.out.println("public default 修饰的非抽象方法");
    }

    //静态方法
    public static void d() {
        System.out.println("这是接口中的静态方法");
    }
}

class Demo implements TestInterface{
    @Override
    public void a() {
        System.out.println("重写了a方法");
    }

    @Override
    public void b() {
        System.out.println("重写了b方法");
    }

//    @Override
//    public void c() {
//        System.out.println("");
//    }

    public static void d() {
        System.out.println("DEMO的静态方法");
    }
}


class Test{
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        Demo demo = new Demo();
        demo.a();
        demo.b();

        //调用静态方法必须要使用类名.方法名
        Demo.d();
        TestInterface.d();

    }
}
```

疑问：为什么要在接口中加入非抽象方法？

如果接口中只能定义抽象方法的话，那么我要是修改接口中内容，那么对实现类的影响太大了，所以实现类都会受到影响，现在在接口中加入非抽象方法，对实现类没有影响，想调用就去调用即可。

### 内部类

#### 成员内部类

```java
       package com.msb.test07;

/**
 * @Auther: rain
 * @date: 2022/10/10 - 10 - 10 - 8:50 下午
 * @Description:
 * @version: 1.0
 */

    /*
    1.类的组成：属性、方法、构造器、代码块（普通块、静态块、构造块、同步块）、内部类
    2.一个类的内部TestOuter的内部的类SubTest叫内部类， 内部类：SubTest   外部类：TestOuter
    3.内部类：成员内部类(静态和非静态的) 和 局部内部类（位置：方法内，块内：构造器内）
    4.成员内部类：
        里面属性，方法，构造器等。
        修饰符：private,default,protect,public,final
    * */

public class TestOuter {

    //非静态成员内部类
    public class D{
        String name;
        int age = 20;
        public void method(){
            //5.内部类可以访问外部类的内容
//            System.out.println(age);
//            a();
            int age = 30;

            //8.内部类和外部类属性重名的时候，如何进行调用
            System.out.println(age);
            System.out.println(this.age);
            System.out.println(TestOuter.this.age);
        }
    }

    //静态成员内部类
    static class E{
        public void method(){
            //6.静态内部类中只能访问外部类中被static修饰的内容
//            System.out.println(age);
//            a();
        }
    }

    //属性
    int age = 10;

    //方法：
    public void a(){
        System.out.println("这是a方法");
        {
            System.out.println("这是一个普通块");
            class B{

            }
        }

        //7.外部类想要访问内部类的内容，需要创建内部类对象，在进行调用。
        D d = new D();
        d.method();
        System.out.println(d.name);

        class A{

        }
    }

    static {
        System.out.println("这是静态块");
    }

    {
        System.out.println("这是一个构造块");
    }

    //构造器
    public TestOuter() {
        class c{

        }
    }

    public TestOuter(int age) {
        this.age = age;
    }
}


class Demo{
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        TestOuter to = new TestOuter();
        to.a();

        //创建内部类的对象
        //静态成员内部类的对象
        TestOuter.E e = new TestOuter.E();
        e.method();
        //非静态成员内部类的对象
//        TestOuter.D d = new TestOuter.D();错误
        TestOuter t = new TestOuter();
        TestOuter.D d = t.new D();
        
    }
}
```

#### 局部内部类

```java
package com.msb.test08;

/**
 * @Auther: rain
 * @date: 2022/10/11 - 10 - 11 - 9:35 上午
 * @Description:
 * @version: 1.0
 */

public class TestOuter {
    //1.在局部内部类中访问到的变量必须是被final修饰的。
    public void method(){
        final int num = 10;
        class A{
            public void a(){
//                num = 20;
                System.out.println(num);
            }
        }
    }

    //2.如果类B在整个项目中只使用一次的时候，那么就没有必要创建一个B类，使用内部类就可以了
    public Comparable method2(){
        //实现一个接口就要重写接口的方法。
        class B implements Comparable{
            @Override
            public int compareTo(Object o) {
                return 100;
            }
        }
        return new B();
    }

    public Comparable method3(){
        //3.匿名内部类，直接创建匿名内部类的对象，返回这个对象给Comparable接收
        return new Comparable() {

            @Override
            public int compareTo(Object o) {
                return 2000;
            }
        };
    }

    public void test(){
        Comparable com = new Comparable() {
            @Override
            public int compareTo(Object o) {
                return 200;
            }
        };
        
        System.out.println(com.compareTo("123"));
    }
}
```

### 面向对象：设计工厂买匹莎

```java
父类：
public class Pizza {
    //名称
    private String name;
    //大小
    private int size;
    //价格
    private int price;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getSize() {
        return size;
    }

    public void setSize(int num) {
        this.size = num;
    }

    public int getPrice() {
        return price;
    }

    public void setPrice(int price) {
        this.price = price;
    }

    //构造器
    public Pizza() {
    }

    public Pizza(String name, int size, int price) {
        this.name = name;
        this.size = size;
        this.price = price;
    }

    public String showMessage(){
        return "名称：" + this.getName() + "\n" +
                "价格：" + this.getPrice() + "元\n" +
                "大小：" + this.getSize() + "寸\n";
    }
}
子类：
package CreatePizza;/**
 * @ClassName: BaconPizza
 * @Author: rain
 * @Date: 2022/10/11 - 10 - 11 - 2:17 下午
 * @Description:
 * @Version: 1.0
 */


/**
 *@ClassName: BaconPizza
 *@Description TODO
 *@Author: rain
 *@Date: 2022/10/11 2:17 下午
 *@Version: 1.0
 **/
public class FriutPizza extends Pizza{
    //属性：配料表
    private String burdensheet;


    public String getBurdensheet() {
        return burdensheet;
    }

    public void setBurdensheet(String burdensheet) {
        this.burdensheet = burdensheet;
    }

    //构造器
    public FriutPizza() {

    }

    public FriutPizza(String burdensheet) {
        this.burdensheet = burdensheet;
    }

    public FriutPizza(String name, int size, int price, String burdensheet) {
        super(name, size, price);
        this.burdensheet = burdensheet;
    }


    @Override
    public String showMessage() {
        return super.showMessage() + "配料水果：" + this.getBurdensheet() + "\n";
    }
}

package CreatePizza;/**
 * @ClassName: FriutPizza
 * @Author: rain
 * @Date: 2022/10/11 - 10 - 11 - 2:13 下午
 * @Description:
 * @Version: 1.0
 */


/**
 *@ClassName: FriutPizza
 *@Description TODO
 *@Author: rain
 *@Date: 2022/10/11 2:13 下午
 *@Version: 1.0
 **/
public class BaconPizza extends Pizza{
    //属性：克数
    private int grammage;


    public int getGrammage() {
        return grammage;
    }

    public void setGrammage(int grammage) {
        this.grammage = grammage;
    }

    //构造器
    public BaconPizza(int grammage) {
        this.grammage = grammage;
    }

    public BaconPizza(String name, int num, int price, int grammage) {
        super(name, num, price);
        this.grammage = grammage;
    }

    @Override
    public String showMessage() {
        return super.showMessage() + "培根克数：" + this.getGrammage() + "g\n";
    }
}

设计工厂类：
package CreatePizza;/**
 * @ClassName: PizzaStore
 * @Author: rain
 * @Date: 2022/10/11 - 10 - 11 - 3:28 下午
 * @Description:
 * @Version: 1.0
 */


import java.util.Scanner;

/**
 *@ClassName: PizzaStore
 *@Description TODO
 *@Author: rain
 *@Date: 2022/10/11 3:28 下午
 *@Version: 1.0
 **/
public class PizzaStore {
    public static Pizza getPizza(int choice) {

        Pizza p = null;
        Scanner sc = new Scanner(System.in);
        switch (choice) {
            case 1:
            {String baconName = "培根披萨";
                System.out.print("请输入培根的克数：");
                int baconGrammar = sc.nextInt();
                System.out.print("请输入披萨的大小：");
                int baconSize = sc.nextInt();
                System.out.print("请输入披萨的价格：");
                int baconPrice = sc.nextInt();

                //将信息录入培根匹莎的对象
                BaconPizza bp = new BaconPizza(baconName, baconSize, baconPrice, baconGrammar);
                p = bp;}
                break;
            case 2:
            {String fruitName = "水果披萨";
                System.out.print("请输入你想要加入的水果：");
                String fruitType = sc.next();
                System.out.print("请输入披萨的大小：");
                int fruitSize = sc.nextInt();
                System.out.print("请输入披萨的价格：");
                int fruitPrice = sc.nextInt();

                //将信息录入水果匹莎的对象
                FriutPizza fp = new FriutPizza(fruitName, fruitSize, fruitPrice, fruitType);
                p = fp;}
                break;
            default:
                System.out.println("-------");

        }
        return p;
    }
}

主程序：
package CreatePizza;/**
 * @ClassName: Test
 * @Author: rain
 * @Date: 2022/10/11 - 10 - 11 - 2:23 下午
 * @Description:
 * @Version: 1.0
 */


import java.util.Scanner;

/**
 *@ClassName: Test
 *@Description TODO
 *@Author: rain
 *@Date: 2022/10/11 2:23 下午
 *@Version: 1.0
 **/
public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //选择购买披萨
        System.out.println("请输入你要制作的匹莎：（1，培根披萨 2，水果匹莎）");
        Scanner sc = new Scanner(System.in);
        int choice = sc.nextInt();

        //通过工厂获取披萨
        Pizza p = PizzaStore.getPizza(choice);
        System.out.println(p.showMessage());
        }
    }
```

## 第九章	异常

### 习题的引入

```java
public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //键盘录入两个数，求商
        Scanner sc = new Scanner(System.in);
        System.out.print("请录入第一个数:");
        int num1 = sc.nextInt();
        System.out.print("请录入第二个数:");
        int num2 = sc.nextInt();

        int sum = num1/num2;
        System.out.print("结果为："+ sum);
    }
}

结果：
1.
 类型错误的异常：
请录入第一个数:问我
Exception in thread "main" java.util.InputMismatchException
	at java.base/java.util.Scanner.throwFor(Scanner.java:943)
	at java.base/java.util.Scanner.next(Scanner.java:1598)
	at java.base/java.util.Scanner.nextInt(Scanner.java:2263)
	at java.base/java.util.Scanner.nextInt(Scanner.java:2217)
	at com.msb.test01.Test.main(Test.java:25)
2.
  除数为0的异常：
请录入第一个数：4
请录入第二个数：0
Exception in thread "main" java.lang.ArithmeticException: / by zero
	at com.msb.test01.Test.main(Test.java:29)
```

异常：Exception：在程序的运行过程中，发生了不正常现象，阻止了程序的运行，我们称之为运行。

### 用if-else解决代码：

```
public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //键盘录入两个数，求商
        Scanner sc = new Scanner(System.in);
        System.out.print("请录入第一个数:");
        if (sc.hasNextInt()) {
            int num1 = sc.nextInt();
            System.out.print("请录入第二个数:");
            if (sc.hasNextInt()){
                int num2 = sc.nextInt();
                if (num2 == 0) {
                    System.out.println("对不起，除数不能为0!");
                }else {
                    System.out.print("结果为："+ num1/num2);
                }
            }
        }else {
            System.out.println("对不起，你录入的数据不是INT类型");
        }
    }
}
```

用if-else堵漏洞的缺点：

（1）代码臃肿，业务代码和处理代码太多

（2）可读性差

（3）程序员需要花费大量的时间来维护

（4）很难解决所有的漏洞

### try-catch

【1】基于if-else处理异常缺点太多，所以Java中有一个异常处理机制：try-catch- final

【2】异常出现了怎么看？

```java
Exception in thread "main" java.util.InputMismatchException
	at java.base/java.util.Scanner.throwFor(Scanner.java:943)
	at java.base/java.util.Scanner.next(Scanner.java:1598)
	at java.base/java.util.Scanner.nextInt(Scanner.java:2263)
	at java.base/java.util.Scanner.nextInt(Scanner.java:2217)
	at com.msb.test01.Test.main(Test.java:25)
```

看第一行和最后一行

【3】

```java
public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //键盘录入两个数，求商
        try {
            Scanner sc = new Scanner(System.in);
            System.out.print("请录入第一个数:");
            int num1 = sc.nextInt();
            System.out.print("请录入第二个数:");
            if (sc.hasNextInt()){
                int num2 = sc.nextInt();
                if (num2 == 0) {
                    System.out.println("对不起，除数不能为0!");
                }else {
                    System.out.print("结果为："+ num1/num2);
                }
            }
        }catch (Exception e) {
            System.out.println("程序出错！");
        }
        System.out.println("-------");
    }
}
```

原理：

把可能出现异常的代码放入try代码块中，然后将异常封装为对象，被catch后面的（）中的那个异常对象接收，接收以后：执行catch后面的的{}里面的代码，然后try-catch后面的代码，该怎么执行就怎么执行。

详细说一下：

（1）try中没有异常，catch中代码不执行

（2）try中有异常，catch进行捕获

如果catch中异常类型和你处的异常类型匹配的话：走catch中的代码 — 进行捕获

如果catch中异常类型和你出的异常类型不匹配的话：不走catch中的代码 --没有捕获成功，程序相当于遇到异常了，中断了，后续代码不执行。

注意：

（1）try中如果没有出现异常，然后用catch捕获成功的话，那吗try中后续的代码是不会执行的

（2）如果catch捕获异常成功，那么try-catch 后面的代码改执行还是执行没有影响

### catch如何处理异常

```java
package com.msb.test01;/**
 * @ClassName: Test01
 * @Author: rain
 * @Date: 2022/10/11 - 10 - 11 - 4:22 下午
 * @Description:
 * @Version: 1.0
 */


import java.util.Scanner;

/**
 *@ClassName: Test01
 *@Description TODO
 *@Author: rain
 *@Date: 2022/10/11 4:22 下午
 *@Version: 1.0
 **/
public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //键盘录入两个数，求商
        try {
            Scanner sc = new Scanner(System.in);
            System.out.print("请录入第一个数:");
            int num1 = sc.nextInt();
            System.out.print("请录入第二个数:");

            int num2 = sc.nextInt();
            if (num2 == 0) {
                System.out.println("对不起，除数不能为0!");
            }else {
                System.out.print("结果为："+ num1/num2);
            }
        }catch (Exception ex) {
            //第一种处理：什么都不写，不做

            //第二种处理：
            //System.out.println("程序出错！");

            //第三种异常处理方法：
            /*（1）调用toString方法，显示异常的类名（全限定路径）
            System.out.println(e);*/

            /*（2）显示异常描述信息对应的字符串，如果没有就显示null
            System.out.println(e.toString());*/

            /*(3) 显示异常的堆栈信息，将异常信息捕获以后，在控制台将异常的效果给我门展示出来，方便我们查看错误。
            */
//            e.printStackTrace();

            //第四种：抛出异常
            throw ex;
        }
        System.out.println("-------");
    }
}
```

### Try-catch-finaly

【1】在什么情况下，try-catch才会抛出异常

```
（1）throw抛出异常的情况
（2）catch中没有正常的进行异常捕获
（3）在try中遇到return
```

【2】怎么样才可以将try-catch后面的代码必须执行？

只要将必须执行的代码放入final中，那么这个代码无论如何一定执行

【3】return和final执行顺序？

先执行finally最后执行return

【4】什么代码会放在finally中呢？

关闭数据库资源，关闭IO流资源，关闭socket资源

【5】有一句代码可以让finally中的代码不执行

```
System.exit(2); 终止当前虚拟机
```

代码

```java
public class Test02 {

    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //键盘录入两个数，求商
        try {
            Scanner sc = new Scanner(System.in);
            System.out.print("请录入第一个数:");
            int num1 = sc.nextInt();
            System.out.print("请录入第二个数:");

            int num2 = sc.nextInt();
            if (num2 == 0) {
                System.out.println("对不起，除数不能为0!");
            }else {
                System.out.print("结果为："+ num1/num2);
            }
        }catch (Exception ex) {
            throw ex;
        }finally {
            System.out.println("-------");
        }
    }
}
```

### 多重catch

【1】try中出现异常以后，将异常类型根catch后面的类型依次比较，按照代码的顺序进行比对，执行第一个与异常类型匹配的catch语句

【2】一旦执行其中一条catch语句之后，之后的catch语句就会被忽略了

【3】在安排catch语句的顺序的时候，一般会将特殊异常放在前面（并列），一般化的异常放在后面

【4】在JDK1.7以后，异常的新处理方式。可以用｜符号连接。

```java
public static Integer getInteger(String nm, Integer val) {
    String v = null;
    try {
        v = System.getProperty(nm);
    } catch (IllegalArgumentException | NullPointerException e) {
    }
    if (v != null) {
        try {
            return Integer.decode(v);
        } catch (NumberFormatException e) {
        }
    }
    return val;
}
```

### 异常的分类

【1】层次结构

【2】运行时异常

```java
public class Test04 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        int[] arr = {1, 23, 4, 5,4,6,7,3};
        System.out.println(arr.length);

        //运行时异常
        int[] arr2 = null;
        System.out.println(arr2.length);
    }
}
```

【3】检查异常

```java
处理1:
public class Test05 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //检查异常
        try {
            try {
                Class.forName("eeee").newInstance();
            }catch (InstantiationException e) {
                
            } catch (IllegalAccessException e) {
                e.printStackTrace();
            }
        }catch (ClassNotFoundException e){
            e.printStackTrace();
        }
    }
}
```

```java
处理2:
public class Test05 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //检查异常
        try {
                Class.forName("eeee").newInstance();
            
        }catch (InstantiationException | IllegalAccessException | ClassNotFoundException e){
            e.printStackTrace();
        }
    }
}
```

```java
处理3:
public class Test05 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws ClassNotFoundException, IllegalAccessException, InstantiationException {
        //检查异常
        Class.forName("eeee").newInstance();
    }
}
```

### throw和throws

代码：

```java
package com.msb.test01;/**
 * @ClassName: Test06
 * @Author: rain
 * @Date: 2022/10/11 - 10 - 11 - 7:29 下午
 * @Description:
 * @Version: 1.0
 */


import java.util.Scanner;

public class Test06 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //实现一个功能：两个数相除，当除数为0的时候，程序出现异常
        try {
            devide();
        }catch (Exception e) {
            e.printStackTrace();
        }
//        devide();
    }

    public static void devide() throws Exception {
        Scanner sc = new Scanner(System.in);
        System.out.print("请录入第一个数:");
        int num1 = sc.nextInt();
        System.out.print("请录入第二个数:");
        if (sc.hasNextInt()){
            int num2 = sc.nextInt();
            if (num2 == 0) {
                //制作运行时异常
//                throw new RuntimeException();

                //制造检查异常
//                try {
//                    throw new Exception();
//                }catch (Exception e){
//                    e.printStackTrace();
//                }

                throw new Exception();
            }else {
                System.out.print("结果为："+ num1/num2);
            }
        }
    }
}
```

总结：

throw和throws的区别：

（1）位置不同：

throw：方法内部

throws：方法的签名处，方法的声明处

（2）内容不同

throw + 异常对象 （检查异常，运行时异常）

throws + 异常的类型（可以多个类型，用，拼接）

（3）作用不同：

throw：异常出现的源头，制造异常

throws：在方法的声明处，告诉方法的调用者，这个方法中可能会出现我声明的这些异常，然后调用者对这个异常进行处理，要么自己处理，要么继续向外抛出异常。

### 练习

```java
package com.msb.tets02;/**
 * @ClassName: Student
 * @Author: rain
 * @Date: 2022/10/11 - 10 - 11 - 7:39 下午
 * @Description:
 * @Version: 1.0
 */


/**
 *@ClassName: Student
 *@Description TODO
 *@Author: rain
 *@Date: 2022/10/11 7:39 下午
 *@Version: 1.0
 **/
public class Student {
    public int age;
    public String name;
    public String sex;

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getSex() {
        return sex;
    }

    public void setSex(String sex) throws Exception {
        if (sex.equals("男")  || sex.equals("女")) {
            this.sex = sex;
        }else {
            //解决方法1:
//            this.sex = "男";

            //解决方法2:
//            System.out.println("对不起，你输入的性别错误");

            //解决方法3:
            //制造运行时异常
//            throw new RuntimeException("性别不对");
            //制造检查时异常
//            try {
//                throw new Exception();
//            }catch (Exception e) {
//                e.printStackTrace();
//            }

            throw new Exception();
        }
    }

    public Student() {
    }

    public Student(int age, String name, String sex) {
        this.age = age;
        this.name = name;
//        this.sex = sex;

        try {
            this.sex = sex;
        }catch (Exception e) {
            e.printStackTrace();
        }
    }

    @Override
    public String toString() {
        return "Student{" +
                "age=" + age +
                ", name='" + name + '\'' +
                ", sex='" + sex + '\'' +
                '}';
    }
}


Test类
package com.msb.tets02;/**
 * @ClassName: Test
 * @Author: rain
 * @Date: 2022/10/11 - 10 - 11 - 7:40 下午
 * @Description:
 * @Version: 1.0
 */

public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //创建一个Student对象
        Student s = new Student();
        s.setAge(16);
        s.setName("zizi");
        try {
            s.setSex("sssss");
        }catch (Exception e) {
            e.printStackTrace();
        }
        System.out.println(s.toString());
    }
}
```

### 重载和重写异常

|      | 英文     | 位置不同   | 修饰符 | 返回值                   | 方法名   | 参数     | 抛出异常 | 方法体 |
| ---- | -------- | ---------- | ------ | ------------------------ | -------- | -------- | -------- | ------ |
| 重载 | overload | 同一类中   | 无关   | 无关                     | 必须相同 | 必须不同 | 无关     | 不同   |
| 重写 | override | 子类父类中 | 无关   | 父类的返回值类型大于子类 | 必须相同 | 必须相同 | 小于等于 | 不同   |

【1】重载

```java
public class Demo {
    public void a() throws Exception {

    }

    public void a(int age) throws RuntimeException {

    }
}
```

【2】重写：

![截屏2022-10-11 下午7.59.14](/Users/rain/Desktop/截屏2022-10-11 下午7.59.14.png)

![截屏2022-10-11 下午7.59.57](/Users/rain/Desktop/截屏2022-10-11 下午7.59.57.png)

父类根子类异常的关系： 子类的异常必须小于父类。

### 自定义异常

继承运行时异常

```
public class MyException extends RuntimeException{

    static final long serialVersionUID = -22222222142323L;

    public MyException() {

    }

    public MyException(String message){
        super(message);
    }
}
```

继承检查异常：

```java
public class MyException extends Exception{

    static final long serialVersionUID = -22222222142323L;

    public MyException() {

    }

    public MyException(String message){
        super(message);
    }
}
```

如果继承的事运行时异常，那么在使用的时候无限额外处理，

如果继承的是检查异常，那么使用的需要try-catch捕获异常或者throws 向上抛

## 第10章	常用类

### 包装类

【1】什么是包装类，经常使用基本数据类型，

对于基本数据类型来说，它就是一个数，加点属性，加点方法，加点构造器。将基本数据类型对应进行了一个封装，产生了一个新的类， —包装类

Int,byte ---基本数据类型

包装类 — 引用数据类型

【2】对应关系

```java
基本数据类型 					对应的包装类            继承关系

 byte									Byte								Number --- Object
short									Short         			Number --- Object
int                   Integer							Number --- Object
long									Long								Number --- Object
float									Float								Number --- Object
double								Double							Number --- Object
char									Character						Object
boolean								Boolean							Object
```

【3】已经有了基本数据类型，为什么要封装为包装类？

（1）Java语言是面向对象的语言，最擅长的操作各种各样的类

（2）以前学习装数据的 — 数组，int[]. String[], double[], Student[]

以后学习的装数据的 ———集合， 有一个特点，只能装引用数据类型的数据

【4】是不是有了包装类以后就不用基本数据类型流？

不是



#### Integer 

【1】直接使用，无需导包

![截屏2022-10-11 下午8.47.39](/Users/rain/Desktop/截屏2022-10-11 下午8.47.39.png)

​																类 Integer

【2】类的继承关系：

![截屏2022-10-12 上午9.40.47](/Users/rain/Desktop/截屏2022-10-12 上午9.40.47.png)

【3】实现接口：

![截屏2022-10-12 上午9.41.16](/Users/rain/Desktop/截屏2022-10-12 上午9.41.16.png)

【4】这个类被final修饰，表示不能有子类，不能被继承。

![截屏2022-10-12 上午9.41.31](/Users/rain/Desktop/截屏2022-10-12 上午9.41.31.png)

【5】包装类是对基本数据类型的封装：对int类型封装产生了Integer

![截屏2022-10-12 上午9.43.13](/Users/rain/Desktop/截屏2022-10-12 上午9.43.13.png)

【6】类的历史：

![截屏2022-10-12 上午9.43.21](/Users/rain/Desktop/截屏2022-10-12 上午9.43.21.png)

【7】属性

```java
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //属性：
        System.out.println(Integer.MAX_VALUE);
        System.out.println(Integer.MIN_VALUE);

        System.out.println(Integer.MAX_VALUE+1);
        System.out.println(Integer.MIN_VALUE-1);
    }
}
```

【8】没有空参构造器

（1）int类型作为构造器的参数

```java
public Integer(int value) {
    this.value = value;
}
```

传入的INt类型的数据， 将你传入的数据封装为你创建的类

（2）String类型作为构造器的参数

```java
public Integer(String s) throws NumberFormatException {
    this.value = parseInt(s, 10);
}
```

传入一个字符串类型数据，将字符串转为int类型的数据，然后赋给底层的value。

当你调用这个方法的时候可以会抛出异常，

【9】包装类的特有机制：自动装箱，自动拆箱

```java
//自动装箱：int --- Integer
Integer i = 12;
System.out.println(i);
//自动拆箱： Integer -- int
Integer i2 = new Integer(15);
int num = i2;
System.out.println(num);
```

（1）自动装箱 自动拆箱是从JDK1.5以后新出的特性

（2）将基本数据类型和包装类进行快速的类型转换。

验证：

```java
//自动装箱：int --- Integer
Integer i = Integer.valueOf(12);
System.out.println(i);
//自动拆箱： Integer -- int
Integer i2 = new Integer(15);
int num = i2.intValue();
System.out.println(num);
```

可以打断点测试：

```java
//这是一个main方法，是程序的入口：
public static void main(String[] args) {
    //自动装箱：int --- Integer
    Integer i = Integer.valueOf(12);
    System.out.println(i);
    //自动拆箱： Integer -- int
    Integer i2 = new Integer(15);
    int num = i2.intValue();
    System.out.println(num);
```

```java
package com.msb.test01;/**
 * @ClassName: Test04
 * @Author: rain
 * @Date: 2022/10/12 - 10 - 12 - 10:53 上午
 * @Description:
 * @Version: 1.0
 */


/**
 *@ClassName: Test04
 *@Description TODO
 *@Author: rain
 *@Date: 2022/10/12 10:53 上午
 *@Version: 1.0
 **/
public class Test04 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //compareTo:只返回三个值： 0，-1，1中的一个
        Integer i1 = new Integer(10);
        Integer i2 = new Integer(20);
        System.out.println(i1.compareTo(i2));
        //eqauls:Integer对Object中的equals方法进行了重写，比较的是底层封装的那个value的值
        //Integer对象是通过new关键字创建的对象。
        Integer i3 = new Integer(43);
        Integer i4 = new Integer(43);
        boolean flag = i3.equals(i4);
        System.out.println(i3==i4); //false  因为 == 比较的是两个对象的地址
        System.out.println(flag);

        //Integer 对象通过自动装箱来完成
        Integer i5 = 130;
        Integer i6 = 130;
        System.out.println(i5.equals(i6));
        System.out.println(i5 == i6);
        // System.out.println(i5 == i6); 如果自动装箱的值在 -127~128之间，比较的就是数值，如果不再这个范围，比较的就是地址


        //intValue() ---作用：将Integer ---int
        Integer i7 = 130;
        int i = i7.intValue();
        System.out.println(i);

        //parseInt(String s): String -- int
        int i8 = Integer.parseInt("12");
        System.out.println(i8);

        //toString: Integer -- String
        Integer i10 = 130;
        System.out.println(i10.toString());

    }
}
```

### 日期类

#### Java.util.Date

```java
package com.msb.test02;/**
 * @ClassName: Test
 * @Author: rain
 * @Date: 2022/10/12 - 10 - 12 - 2:04 下午
 * @Description:
 * @Version: 1.0
 */


import java.util.Date;

/**
 *@ClassName: Test
 *@Description TODO
 *@Author: rain
 *@Date: 2022/10/12 2:04 下午
 *@Version: 1.0
 **/
public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //java.util.Date
        Date d = new Date();
        System.out.println(d);
        System.out.println(d.toString());
        //格林尼治时间
        System.out.println(d.toGMTString());
        System.out.println(d.toLocaleString());

        System.out.println(d.getYear());
        System.out.println(d.getMonth());
        System.out.println(d.getMinutes());
        System.out.println(d.getSeconds());

        //返回自1970年1月1日00:00:00GMT以来此间的毫秒数
        System.out.println(d.getTime());

        System.out.println(System.currentTimeMillis());
        /*
        * （1）疑问：以后获取时间差用：getTime()还是currentTimeMilles()
        * 答案：currentTimeMillis() --- 因为这个方法是静态的，可以用类名.方法名来调用
        *   (2) public static native long currentTimeMillis();
        * 本地方法
        * 为什么没有方法体？因为这个方法的具体实现不是通过Java写的
        * （3）这个方法的作用：
        * 一般会衡量一些算法所用的时间
        * */
        long startTime = System.currentTimeMillis();
        for (int i = 0; i < 10000; i++) {
            System.out.println("124");
        }
        long endTime = System.currentTimeMillis();
        System.out.println(endTime-startTime);
    }
}
```

#### Java.sql.Date

```java
package com.msb.test02;/**
 * @ClassName: Test02
 * @Author: rain
 * @Date: 2022/10/12 - 10 - 12 - 2:21 下午
 * @Description:
 * @Version: 1.0
 */


import java.sql.Date;

/**
 *@ClassName: Test02
 *@Description TODO
 *@Author: rain
 *@Date: 2022/10/12 2:21 下午
 *@Version: 1.0
 **/
public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //java.sql.Date:
        Date d = new Date(1665555751336L);
        System.out.println(d);

        /*
        * (1)java.util.Date和java.sql.Date的区别：
        * java.util.Date:年月日  时分秒
        * java.sql.Date：年月日
        * （2）两个包之间的关系：
        * 继承
        * java.util.Date -- 父类   java.sql.Date  --  子类
        * */

        //【1】util - sql：
        java.util.Date date = new Date(1665555751336L);  //创建util.Date对象
        //方式1：向下转型
        Date date1 = (Date) date;
        //方式2: 利用构造器
        Date date2 = new Date(date.getTime());

        //[2] sql --util:
        java.util.Date date3 = d;

        //[3]String --sql.Date:
        Date date4 = Date.valueOf("2019-3-18");
    }
}
```

#### 日期转换 SimpleDateFormat

【1】String — Java.sql.Date

【2】Java.sql.Date — Java.util.Date

(1) String — java.sql.Date

(2) java.sql.Date — java.util.Date

```java
public class Test04 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //(1) String -- java.sql.Date
        java.sql.Date date = java.sql.Date.valueOf("2019-09-24");
        //(2) java.swl.Date --- java.util.Date
        java.util.Date date2 = date;
        System.out.println(date2.toString());
    }
}
```

上面的代码有局限性，字符串的格式只能是年-月-日拼接的格式，换成其他类型，就会出现异常：

Exception in thread "main" java.lang.IllegalArgumentException
	at java.sql/java.sql.Date.valueOf(Date.java:141)
	at com.msb.test02.Test04.main(Test04.java:21)

【2】引入新的类

```java
package com.msb.test02;/**
 * @ClassName: Test03
 * @Author: rain
 * @Date: 2022/10/12 - 10 - 12 - 3:31 下午
 * @Description:
 * @Version: 1.0
 */


import java.text.DateFormat;
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;

public class Test03 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //日期转换,
        //public class SimpleDateFormat(子类) extends DateFormat （父类）利用多态创建对象
        //定义格式化标准
        DateFormat df = new SimpleDateFormat("yyyy-dd-MM HH:mm:ss");
        //String -- Date
        try {
            Date date = df.parse("2019-09-11 11:22:33");
            System.out.println(date);
        }catch (ParseException e) {
            e.printStackTrace();
        }


        //Date --String
        String format = df.format(new Date());
        System.out.println(format);


        Date d = new Date();
        System.out.println(d.toString());
        
    }
}
```

【3】日期格式：

![截屏2022-10-12 下午3.34.40](/Users/rain/Desktop/截屏2022-10-12 下午3.34.40.png)

#### Calendar

```java
package com.msb.test02;/**
 * @ClassName: Test05
 * @Author: rain
 * @Date: 2022/10/12 - 10 - 12 - 3:45 下午
 * @Description:
 * @Version: 1.0
 */


import java.util.Calendar;
import java.util.GregorianCalendar;
public class Test05 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //Calendar 是一个抽象类，通过子类创建对象
        //public class GregorianCalendar extends Calendar
        Calendar cal = new GregorianCalendar();
        Calendar cal2 = Calendar.getInstance();
        System.out.println(cal);


        //常用的方法：get方法，传入参数：Calendar中定义的常量
        System.out.println(cal.get(Calendar.YEAR));
        System.out.println(cal.get(Calendar.MONTH));
        System.out.println(cal.get(Calendar.DATE));
        System.out.println(cal.getActualMaximum(Calendar.DATE));  //获取当月日期的最大天数
        System.out.println(cal.getActualMinimum(Calendar.DATE));  //获取当月日期的最小天数

        //set方法，可以改变Calendar中的内容
        cal.set(Calendar.YEAR,1990);
        cal.set(Calendar.MONTH,9);
        cal.set(Calendar.DATE,16);
        System.out.println(cal);


        //String  ---Calendar
        //分解：
        //String  --java.sql.Date:
        java.sql.Date date = java.sql.Date.valueOf("2020-02-02");
        System.out.println(date);

        //java.sql.Date  -- Calendar:
        cal.setTime(date);
        System.out.println(cal);


    }
}
```

Canlendar练习：



```java
package com.msb.test02;/**
 * @ClassName: Test06
 * @Author: rain
 * @Date: 2022/10/12 - 10 - 12 - 4:06 下午
 * @Description: 做一个日历表
 * @Version: 1.0
 */


import java.util.Calendar;
import java.util.Scanner;

public class Test06 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        System.out.println("请输入你要查看的日期：年-月-日：xxxx-xx-xx");
        String date = sc.next();

        //String -- Calendar.
        //String -- Date
        java.sql.Date d = java.sql.Date.valueOf(date);

        //Date  -- Calendar:
        Calendar cal = Calendar.getInstance();
        cal.setTime(d);

        //后续操作
        System.out.println("日\t一\t二\t三\t四\t五\t六\t");

        //获取本月的最大天数
        int maxDay = cal.getActualMaximum(Calendar.DATE);
        //获取当前日期的日
        int trueDay = cal.get(Calendar.DATE);

        //设置为1号
        cal.set(Calendar.DATE,1);
        //获取这个月的1号是第几天
       int fristDay = cal.get(Calendar.DAY_OF_WEEK);
//       System.out.println(fristDay);

        for (int i= 1;i<=fristDay;i++) {
            System.out.print("\t");
    }

        //遍历
        int count = fristDay-1;
        for (int i = 1; i <= maxDay; i++ ) {
            if (trueDay == i) {
                System.out.print(i + "*" + "\t");
        }else {
                System.out.print(i+"\t");
        }
            count++;
            if(count%7 == 0){
                System.out.println();
            }
        }
    }
}
```

#### JDK1.8新增日期时间API

- JDK1.0中使用java.util.Date类。 — 第一批日期时间API
- JDK1.1引入了Calendar类 —第二批日期时间API
- 缺陷：
- 可变形：像日期和时间这样的类应该是不可变的
- 偏移性：Date中的年份是从1900开始的，而月份都从0开始的。
- 格式化：格式化只对Date有用，Calendar则不行

JDK1.8新增日期时间API———第三批日期时间API。

```java
package com.msb.test02;

import java.time.LocalDate;
import java.time.LocalDateTime;
import java.time.LocalTime;

/**
 * @ClassName: Test07
 * @Author: rain
 * @Date: 2022/10/12 - 10 - 12 - 6:36 下午
 * @Description:
 * @Version: 1.0
 */


public class Test07 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //方法1:now（）---获取当前的日期。时间，日期+时间
        LocalDate LocalDate1 = java.time.LocalDate.now();
        System.out.println(LocalDate1);
        LocalTime time1 = LocalTime.now();
        System.out.println(time1);
        LocalDateTime LocalDateTime1 = java.time.LocalDateTime.now();
        System.out.println(LocalDateTime1);

        //方法2:设置年月日时间
        java.time.LocalDate lo1 = LocalDate.of(2022,1,4);
        LocalDateTime lo2 = LocalDateTime.of(20,10,1,3,4);
        LocalTime lo3 = LocalTime.of(1,13,3);
        System.out.println(lo1);
        System.out.println(lo2);
        System.out.println(lo3);


        //详解LocationTime类
        System.out.println(LocalDateTime1.getYear()); //2022
        System.out.println(LocalDateTime1.getMonth()); //OCTOBER
        System.out.println(LocalDateTime1.getMinute()); //56
        System.out.println(LocalDateTime1.getDayOfMonth()); //12
        System.out.println(LocalDateTime1.getDayOfYear());  //285
        System.out.println(LocalDateTime1.getHour());  //18
        System.out.println(LocalDateTime1.getSecond()); //18


        //LocationDateTime设置时间
        LocalDateTime localDateTime2 = LocalDateTime1.withMonth(2);
        System.out.println(LocalDateTime1);
        System.out.println(localDateTime2);

        //提供加减的操作
        //加
        LocalDateTime localDateTime3 = LocalDateTime1.plusDays(14);
        System.out.println(LocalDateTime1);
        System.out.println(localDateTime3);

        //减
        LocalDateTime localDateTime4 = LocalDateTime1.minusDays(14);
        System.out.println(LocalDateTime1);
        System.out.println(localDateTime4);
    }
}
```

#### 日期格式的设置

```java
package com.msb.test02;/**
 * @ClassName: Test08
 * @Author: rain
 * @Date: 2022/10/12 - 10 - 12 - 7:20 下午
 * @Description:
 * @Version: 1.0
 */


import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;
import java.time.format.FormatStyle;
import java.time.temporal.TemporalAccessor;

/**
 *@ClassName: Test08
 *@Description TODO
 *@Author: rain
 *@Date: 2022/10/12 7:20 下午
 *@Version: 1.0
 **/
public class Test08 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //格式化类：DateTimeFormatter

        //方式一：预定义的标准格式：。如：ISO_LOCAL_DATE_TIME, ISO_LOCAL_DATE,ISO_LOCAL_TIME
        DateTimeFormatter df1 = DateTimeFormatter.ISO_LOCAL_DATE_TIME;
        //df1就可以帮我们完成LocalDateTime和String之间的相互转换。
        //LocalDateTime -- String
        LocalDateTime now = LocalDateTime.now();
        String str = df1.format(now);
        System.out.println(str); //2022-10-12T19:25:04.415609

        //String ---LocationDateTime
        TemporalAccessor parse = df1.parse("2022-10-12T19:25:04.415609");
        System.out.println(parse);


        //方式二：本地化相关的格式：
        //参数：FormatStyle.LONG / FormatStyle.MEDIUM  / FormatStyle.SHORT
        //2022年10月12日 下午8:02:54   FormatStyle.MEDIUM
        //SHORT   2022/10/12 下午8:05
        DateTimeFormatter df2 = DateTimeFormatter.ofLocalizedDateTime(FormatStyle.SHORT);
        //LocalDateTime --String
        LocalDateTime now1 = LocalDateTime.now();
        String str2 = df2.format(now1);
        System.out.println(str2);

        //String  --LocationDateTime
        TemporalAccessor parse1 = df2.parse("2022/10/12 下午8:05");
        System.out.println(parse1);

        //方式3:自定义格式，如，ofPattern("yyyy-MM-dd hh:mm:ss") 重点：以后常用
        DateTimeFormatter df3 = DateTimeFormatter.ofPattern("yyyy-MM-dd hh:mm:ss");
        //LocalDateTime --String:
        LocalDateTime now2 = LocalDateTime.now();
        System.out.println(now2);
        String format2 = df3.format(now2);
        System.out.println(format2);  //2022-10-12 08:08:30
        //Stirng --- LocationDateTime
        TemporalAccessor parse2 = df3.parse("2022-10-12 08:08:30");
        System.out.println(parse2);

    }
}
```

### Math类

【1】直接使用，不需导包

packge java.lang;

【2】final修饰类，这个类不能被继承

public final class Math{}

【3】构造器私有化，不能创建Math类对象：

```java
/**
 * Don't let anyone instantiate this class.
 */
private Math() {}
```

Math a = new Math();  错误的

【4】Math内部的所有的属性和方法，都被static修饰： 类名.直接调用，无需创建对象

```java
/**
 * The {@code double} value that is closer than any other to
 * <i>e</i>, the base of the natural logarithms.
 */
public static final double E = 2.7182818284590452354;

/**
 * The {@code double} value that is closer than any other to
 * <i>pi</i>, the ratio of the circumference of a circle to its
 * diameter.
 */
public static final double PI = 3.14159265358979323846;

/**
 * Constant by which to multiply an angular value in degrees to obtain an
 * angular value in radians.
 */
private static final double DEGREES_TO_RADIANS = 0.017453292519943295;

/**
 * Constant by which to multiply an angular value in radians to obtain an
 * angular value in degrees.
 */
private static final double RADIANS_TO_DEGREES = 57.29577951308232;
```

【5】部分方法代码

```java
package com.msb.test03;/**
 * @ClassName: Test01
 * @Author: rain
 * @Date: 2022/10/12 - 10 - 12 - 8:15 下午
 * @Description:
 * @Version: 1.0
 */

public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //常用属性
        System.out.println(Math.PI);
        //常用方法
        System.out.println("随机数：" + random()); // [0.0, 1.0)
        System.out.println("绝对值：" + Math.abs(-80));
        System.out.println("向上取值：" + Math.ceil(9.1));
        System.out.println("向下取值：" + Math.floor(10.5));
        System.out.println("四舍五入：" + Math.round(3.6));
        System.out.println("取最大的值：" + Math.max(146,44));
        System.out.println("取最小的值：" + Math.min(3,6));

    }

    //如果根math中方法重复了，那么会优先走本类中的方法（就近原则）
    public static int random(){
        return 100;
    }
}
```



### Random类

```java
package com.msb.test03;/**
 * @ClassName: Test02
 * @Author: rain
 * @Date: 2022/10/12 - 10 - 12 - 8:24 下午
 * @Description:
 * @Version: 1.0
 */


import java.util.Random;

public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //返回带正号的double值，该值大于等于0，小于1.0
        System.out.println("随机数："+ Math.random());

        //学习Random类
        //(1)利用带参数的构造器创建对象
        Random r1 = new Random(System.currentTimeMillis());
        int i = r1.nextInt();
        System.out.println(i);

        //(2) 利用空参构造器创建对象
        Random r2 = new Random();  //表面是在调用无参数构造器，实际底层还是调用了带参构造器 
        System.out.println(r2.nextInt(10));  //在 0（包括）和指定值（不包括）之间均匀分布的int 值
        System.out.println(r2.nextDouble());   //在0.0和1.0之间均匀分布的double值

    }
}
```

### String类

【1】直接使用，不需导包

packge java.lang;

【2】

The String class represents character strings. All string literals in Java programs, such as "abc", are implemented as instances of this class.
Strings are constant; their values cannot be changed after they are created. String buffers support mutable strings. Because String objects are immutable they can be shared. For example:
       String str = "abc";

[3]

```java
String str = "abc";
"abc"就是 String类的具体的对象
```

【4】字符串是不可变的

String are constant

【5】这个String类不可以被继承，不能有子类

public final class String

【6】String底层是一个char类型的数组

```java
   char data[] = {'a', 'b', 'c'};
   String str = new String(data);
```
#### 常用方法

```java
        String s4 = "abc";
        System.out.println("字符串的长度为：" + s4.length());

        String s5 = new String("abc");
        System.out.println("判读字符串是否为空：" + s5.isEmpty());

        String s6 = new String("asdgf");
        System.out.println("获取字符串下标对应的字符是："+s6.charAt(3));


```

【7】equals（源码讲解）

```java
    String s7 = new String("dd");
    String s8 = s6;
    //比较两个数是否相等,比较的是指向的地址
    System.out.println(s6.equals(s7));
    System.out.println(s6.equals(s8));
```
![image-20221012211848318](/Users/rain/Library/Application Support/typora-user-images/image-20221012211848318.png)

【8】String类实现了Comparable,里面有一个抽象方法叫做compareTo方法，所以String中一定要对这个方法进行重写

```java
//compareTo方法
//返回两种情况
//1. 返回结果是两个比较字符的长度差值
//2. 返回结果是不一样的位的ASCLL码
String s9 = new String("ax");
String s10 = new String("aabb");
System.out.println(s9.compareTo(s10));
```

![image-20221012212735036](/Users/rain/Library/Application Support/typora-user-images/image-20221012212735036.png)

```java
        //字符串的截取
        String s11 = new String("afjsejf");
        System.out.println(s11.substring(4));
        System.out.println(s11.substring(2, 6));

        //字符串的拼接
        String s12 = new String("efjd");
        System.out.println(s12.concat(s11));

        //字符串的替换
        String s13 = new String("rrra");
        System.out.println(s13.replace("r", "c"));

        //按照指定的字符串进行分裂为数组的形式：
        String s14 = "a-b-n-f-d-r-t";
        String[] strs = s14.split("-");
        System.out.println(Arrays.toString(strs));

        //转大小写的方法
        String s15 = "abc";
        System.out.println(s15.toUpperCase());
        System.out.println(s15.toUpperCase().toLowerCase());

        //去除首位空白符
        String s16 = "   a b b ";
        System.out.println(s16.trim());

        //toString()
        String s17 = "abccc";
        System.out.println(s17.toString());

        
        String s18 = String.valueOf(123);
        System.out.println(s18.toString());
```

#### String的内存分析

【1】字符串拼接：

```java
public class Test03 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        String s1 = "a" + "b"+"c";
        String s2 = "ab" +"c";
        String s3 = "a" + "bc";
        String s4 = "abc";
        String s5 = "abc" +"";
        System.out.println(s1 == s3);
        System.out.println(s2 == s5);
        System.out.println(s1.equals(s5));
    }
}
```

上面的字符串，会进行编译器优化，直接合并为完整的字符串，在常量池中，常量池的特点就是第一次如果没有这个字符串，就放进去，如果有这个字符串，就直接从常量池中取。

内存：

![image-20221013170656542](/Users/rain/Library/Application Support/typora-user-images/image-20221013170656542.png)

【2】new关键字创建：

```java
String s6 = new String("asd");
```

内存：

![image-20221013170713557](/Users/rain/Library/Application Support/typora-user-images/image-20221013170713557.png)

【3】有变量参与的字符串拼接：

```java
public class Test04 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        String a = "abv";
        String b = a + "dec";
        System.out.println(b.toString());
    }
}
```

a变量在编译的时候不知道a是“abc”字符串，所以不会进行编译优化，不会直接合并“abvdec“，

反编译：javap -c xxx.class

![image-20221013170733248](/Users/rain/Library/Application Support/typora-user-images/image-20221013170733248.png)

### StringBuilder类

【1】字符串的分类：

（1）不可变字符串：String

（2）可变字符串：StringBuilder，StringBuffer

疑问？

（1）可变不可变？

（2）重点：StringBuilder

（3）StringBuilder和StringBuffer的区别：

【2】StirngBuilder底层：非常重要的两个属性：

```java
    /**
     * The value is used for character storage.
     */
    byte[] value;
```

 value就是StringBuilder底层的存储

```java
/**
 * The count is the number of characters used.
 */
int count;
```

count指的是value数组中被使用的长度

【3】对应内存分析 ：

```java
//创建StringBuilder对象
//表面上调用StringBuilder的空参构造器，实际底层是对value的长度进行初始化，长度16
StringBuilder sb1 = new StringBuilder();
//表面上调用StringBuilder的有参构造器。传入一个int类型的数，实际底层是对value数组进行初始化，长度为你传入的数字
StringBuilder sb2 = new StringBuilder(3);
StringBuilder sb3 = new StringBuilder("abc");
System.out.println(sb3.append("asew").append("fhdhfifh").append("djdw"));
```



### 解释可变和不可变字符串

【1】String		---	类

String a = “abc”；   a = “abcdef”;//error

不可变：在地址不变的情况下，想把“abc”变成“abcdef”是不可能的

【2】StringBuilder 类

可变，添加之后，两个对象地址相同。

```java
//这是一个main方法，是程序的入口：
public static void main(String[] args) {
    StringBuilder sb = new StringBuilder("abc");
    StringBuilder sb1 = sb.append("def");
    System.out.println(sb.equals(sb1));
```

【3】StringBuilder常用方法

```java
package com.msb.test05;

/**
 * @ClassName: Test03
 * @Author: rain
 * @Date: 2022/10/14 - 10 - 14 - 2:59 下午
 * @Description:
 * @Version: 1.0
 */


public class Test03 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder("aaa");
        sb.append("124dcvbnbvcxcvghgfdsxcvbnhgfdszx");
        System.out.println(sb);

        //删除
        sb.delete(3, 6);
        System.out.println(sb);

        //删除指定位置
        sb.deleteCharAt(20);
        System.out.println(sb);

        //改--插入
        StringBuilder sb1 = new StringBuilder("$fhusfesfesf");
        sb1.insert(2, "你好");
        System.out.println(sb1);

        //改---替换
        StringBuilder sb2 = new StringBuilder("dsudbuaid女单打外等你");
        sb2.replace(4, 8, "你好哇我i的肌肤带娃");
        System.out.println(sb2);
        sb2.setCharAt(2, 'd');
        System.out.println(sb2);

        //查
        StringBuilder sb3 = new StringBuilder("abvgdifr");
        for (int i = 0; i < sb3.length(); i++) {
            System.out.println(sb3.charAt(i) + "\t");
        }

        //截取
        String str = sb3.substring(2,4);//返回的是一个新的String,对StringBuilder没影响
        System.out.println(str);
        System.out.println(sb3);
    }}
```

StringBuilder类用法和StringBuffer类一样

面试题：String、StringBuffer、StringBuilder的区别和联系

```java
1.String类是不可变类，即一旦一个String对象被创建后，包含在这个对象中的字符序列是不可改变的，直至这个对象销毁，2.StringBuffer类则代表了一个字符序列可变的字符串，可以通过append、intsert,reverse,setCharAt,setLength等方法改变其内容，一旦生成了最终的字符串，调用toString()方法将其转变为String.
3.JDK1.5新增了一个StringBuilder类，与StringBufferr相似，构造方法和方法基本相同，不同是StringBuffer是线程安全的，而StringBuilder是线程不安全的，所以性能略高，通常情况下，创建一个内容可变的字符串，应该优先考虑使用StringBuilder。

StringBuilder:JDK1.5开始			效率高			线程不安全
StringBuffer：JDK1.0开始				效率低			线程安全
```

## 第11章 	Junt&注释&枚举

### Junt单元测试

#### 引入

【1】软件测试的目的：

【2】测试分类：

（1）黑盒测试

（2）白盒测试

#### 没有JUnt的情况下测试

缺点：

```
1.测试一定走main方法，是程序的入口，main方法的格式不能写错
2.要是在同一个main方法中测试的话，那么不需要测试的东西必须注释掉
3.测试逻辑如果分开的话，需要定义多个测试类，
4.业务逻辑和测试代码混淆，
```

代码：

```java
package com.msb.test01;

/**
 * @ClassName: Calculator
 * @Author: rain
 * @Date: 2022/10/14 - 10 - 14 - 3:51 下午
 * @Description:
 * @Version: 1.0
 */


public class Calculator {
    //加法：
    public static int add(int i, int j){
        return  i+j;
    }

    //减法
    public static int sub(int i,int j){
        return i-j;
    }
}
```

```java
package com.msb.test01;

/**
 * @ClassName: Test01
 * @Author: rain
 * @Date: 2022/10/14 - 10 - 14 - 3:51 下午
 * @Description:
 * @Version: 1.0
 */


public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        Calculator cal = new Calculator();
        //测试加法
        int sum = cal.add(10,29);
        System.out.println(sum);

        //测试减法
        int sub = cal.sub(10,29);
        System.out.println(sub);
    }
}
```

#### Junt的使用

【1】一般将测试和正常业务分离，分离为不同的包

建议起名：公司域名倒着写+test

以后测试类就单独放在这个包下

【2】测试类的名字：****Test

【3】测试方法的定义。---可以独立运行，不依托于main方法

名字 : testAdd(). testSub()

参数：无参

返回值：void

【4】测试方法定义以后，不能直接独立运行，必须要子啊方法前加一个注释：@Test

【5】倒入Junt依赖的环境

【6】代码

```java
public class Calcuator {
    //测试add方法
    @Test
    public void testAdd(){
        System.out.println("测试add方法");
        Calculator calc = new Calculator();
        int sum = calc.add(10,39);
        System.out.println(sum);
    }

    //测试sub方法
    @Test
    public void testSub(){
        System.out.println("测试sub方法");
        Calculator calc = new Calculator();
        int sum = calc.sub(10,39);
        System.out.println(sum);
    }
}
```

【7】判定结果：

绿色：正常结果

红色：出现异常

【8】即使出现绿色结果，也不意味着测试通过，需要加入断言来判断》

```java
package com.msb.test;

import com.msb.test01.Calculator;
import org.junit.Assert;
import org.junit.Test;

/**
 * @ClassName: Calcuator
 * @Author: rain
 * @Date: 2022/10/14 - 10 - 14 - 4:04 下午
 * @Description:
 * @Version: 1.0
 */

public class Calcuator {
    //测试add方法
    @Test
    public void testAdd(){
        System.out.println("测试add方法");
        Calculator calc = new Calculator();
        int sum = calc.add(10,39);
//        System.out.println(sum);程序的运行结果可以不关注
        //加入断言，预测一下结果，判断一下我预测的结果与实际的结果是否一致
        Assert.assertEquals(49,sum);
    }

    //测试sub方法
    @Test
    public void testSub(){
        System.out.println("测试sub方法");
        Calculator calc = new Calculator();
        int sum = calc.sub(10,39);
        System.out.println(sum);
    }
}
```

#### @Befor, @After：

@Befor：

某个方法中，加入这个注释后，那么这个方法中的功能会在测试方法执行前执行

一般会在@Befor中加入：一些申请资源的代码，申请数据库资源，申请IO资源，申请网络资源

@After：

某个方法中，加入这个注释后，那么这个方法中的功能会在测试方法执行后执行

一般会在@Befor中加入：加入释放申请资源的代码，释放数据库资源，释放IO资源，释放网络资源

### 注解

#### 引入

【1】历史：

JDK5.0新增 —注释（Annotation），也叫元数据

【2】什么是注解？

```
注解其实就是代码里的特殊标记，这些标记可以在编译、类加载、运行时被读取，并执行相应的处理，通过使用注释，程序员可以在不改变原有逻辑的情况下，在源文件中嵌入一些补充信息。代码分析工具、开发工具和部署工具可以通过这些补充信息进行验证或者进行部署。
```

【3】注解的重要性：

```
Annotation 可以想修饰符一样被使用，可用与修饰包，类，构造器，方法，成员变量，参数，局部变量的声明，这些信息被保存在Annotation的"name=value"对中，在JavaSE中，注释的使用目的比较简单，例如标记过时的功能，忽略警告等。在JavaSe/Arldroid中注解占据了更重要的角色，例如用配置应用程序的任何切面，代替javase旧版中所遗留的繁亢代码和XML配置等，未来的开发模式都是基于注解的，JPA(java的持久性API)是基于注释的，Spring2.5以上都是基于注解的，Hibernate3.x以后也是基于注解的，现在的Strust2有一部分也是基于注解的，注解是一种趋势，一定程度上说：框架=注解+反射+设计模式
```



#### 注解的使用实例

##### Junt的注解：

```java
public class Calcuator {
    //测试add方法
    @Test
    public void testAdd(){
        System.out.println("测试add方法");
        Calculator calc = new Calculator();
        int sum = calc.add(10,39);
//        System.out.println(sum);程序的运行结果可以不关注
        //加入断言，预测一下结果，判断一下我预测的结果与实际的结果是否一致
        Assert.assertEquals(49,sum);
    }

```

##### 文档注解：



```
标签	描述	示例
@author	标识一个类的作者，一般用于类注释	@author description
@deprecated	指名一个过期的类或成员，表明该类或方法不建议使用	@deprecated description
{@docRoot}	指明当前文档根目录的路径	Directory Path
@exception	可能抛出异常的说明，一般用于方法注释	@exception exception-name explanation
{@inheritDoc}	从直接父类继承的注释	Inherits a comment from the immediate surperclass.
{@link}	插入一个到另一个主题的链接	{@link name text}
{@linkplain}	插入一个到另一个主题的链接，但是该链接显示纯文本字体	Inserts an in-line link to another topic.
@param	说明一个方法的参数，一般用于方法注释	@param parameter-name explanation
@return	说明返回值类型，一般用于方法注释，不能出现再构造方法中	@return explanation
@see	指定一个到另一个主题的链接	@see anchor
@serial	说明一个序列化属性	@serial description
@serialData	说明通过 writeObject() 和 writeExternal() 方法写的数据	@serialData description
@serialField	说明一个 ObjectStreamField 组件	@serialField name type description
@since	说明从哪个版本起开始有了这个函数	@since release
@throws	和 @exception 标签一样.	The @throws tag has the same meaning as the @exception tag.
{@value}	显示常量的值，该常量必须是 static 属性。	Displays the value of a constant, which must be a static field.
@version	指定类的版本，一般用于类注释	@version info
```



```java
package com.msb.anno;



public class Person {

    /**
     *
     * @param num1 数字1
     * @param num2 数字2
     */
    public void eat(int num1, int num2){

    }

    /**
     *
     * @param age 年龄
     * @return int
     * @exception IllegalArgumentException 1234
     * @exception RuntimeException 6579
     * @see Student
     */
    public int sleep(int age){
        new Student();
        if (age>100) {
            throw new IllegalArgumentException();
        }
        if (age < 100) {
            throw new RuntimeException();
        }

        return 100;
    }
}
```

##### JDK内置的三个注解

@override:限定重写父类方法，该注解只能用于方法

```java
public class Person {
    public void eat(){
        System.out.println("124214");
    }
}
```

```java
public class Student extends Person{
    @Override
    public void eat(){
        System.out.println("....");
    }
}
```



@Desprecated:用于表示所修饰的元素（类，方法，构造器，属性等）已过时，通常是因为所修饰的结构危险或存在更好的选择

```java
public class Student extends Person{
    /*限定重写的方法，只要重写方法有问题，就用错误提示*/
    @Override
    public void eat(){
        System.out.println("....");
        study();
    }

    /*
   在方法前加入@Deprecated 修饰，表示这个方法已过期
   * */
    @Deprecated
    public void study(){
        System.out.println("学习...");
    }
}
```

```java
public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        Date d = new Date();
        d.setTime(2033-22-24);
        d.setYear(2022);
        Student st = new Student();
        st.study();
    }
}
```

@SuppressWarning:抑制编译器警告

```java
public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        @SuppressWarnings("unused")
        int age = 10;

        int num = 20;
        System.out.println(num);
        @SuppressWarnings("usused")
        ArrayList a1 = new ArrayList();
    }
}
```

##### 实现替代配置文件功能的注释



#### 自定义注解

【1】自定义注解使用很少，一般情况下都是用现成的注解

【2】如何自定义注解

```java
public @interface MyAnnotation {
}
```

发现定义的注解的声明使用的关键字：@interface，跟接口一点关系都没有

【3】注解的内部：

以@SuppressWarnings为例，发现内部：

![截屏2022-10-14 下午5.10.57](/Users/rain/Desktop/截屏2022-10-14 下午5.10.57.png)

这value是属性还是方法？

答案：看上去是无参数方法，实际上理解为一个成员变量一个属性，

无参数方法的名字 —  成员变量的名字

无参数方法的返回值 —成员变量的类型

这个参数叫做配置参数

无参数方法的类型：基本数据类型（八种），String，枚举，注解类型，还可以是以上类型对应的数组

PS：如果只有一个成员变量的话，名字尽量叫value

【4】使用注解

（1）使用注解的话，如果你定义了配置参数，就必须给配置参数进行赋值操作

```java
@MyAnnotation(value={"123","@12"})
public class Person {
}
```

（2）如果你只有一个参数，并且这个参数的名字为value的话，那么value=可以省略不写

```java
@MyAnnotation({"123","@12"})
public class Person {
}
```

（3）如果你给配置参数设置默认值，那么使用的时候可以无需传值

```java
@MyAnnotation2
@MyAnnotation({"123","@12"})
public class Person {
}

public @interface MyAnnotation2 {
    String value() default "aaa";
}
```

（4）一个注解的内部是可以不配置参数的：

```java
public @interface MyAnnotation3 { 
}
```

内部没有定义配置参数的注解 ---可以叫做标记

内部有定义配置参数的注解 ---可以叫做元数据

【5】注解的使用：

现在只学习注解大致技能，以后在学习怎么使用

#### 元注解

元注解是用于修饰其他注解的注解

举例：

![截屏2022-10-14 下午6.54.51](/Users/rain/Desktop/截屏2022-10-14 下午6.54.51.png)

JDK5.0提供了四种元注解：Retention，Target，Documented，Inherited

##### Retention

@Retention:用于修饰注解，用于指定修饰的那个注解的生命周期，@Retention包含一个RetentionPolicy枚举类型的成员变量，使用@Retention时必须为该value成员变量指定值：

- RetentionPolicy.SOURCE：在源文件中有效（即源文件保留），编译器直接丢弃这种策略的注释，在.class文件中不会保留注解信息

  ```java
  @Retention(RetentionPolicy.SOURCE)
  public @interface MyAnnotation {
      String[] value();
  }
  ```

- ```java
  package com.msb.test03;
  
  public class Person {
      public Person() {
      }
  }
  ```

  

- RetentionPolicy.CLASS: 在class文件中有效（即class保留），保留在.class文件中，但是当运行Java程序时，他就不会继续加载了，不会保留在内存中，jvm不会保留注释，如果注释没有加Retention元注解，那么相当于默认的注解就是此状态。

```java
@Retention(RetentionPolicy.CLASS)
public @interface MyAnnotation {
    String[] value();
}
```

- ```java
  @MyAnnotation({"123", "@12"})
  public class Person {
      public Person() {
      }
  }
  ```

- RetentionPolicy.RUNTIME：在运行时有效（即运行时保留），当运行Java程序时，jvm会保留注释，加载在内存中，那么程序可以通过反射获取该注释

##### Target

用于修饰注解的注解，用于指定被修饰的注解能用于修饰哪些程序元素，@Target也包含一个名为value的成员变量

案例：

```java
package com.msb.test03;

import java.lang.annotation.Target;
import static java.lang.annotation.ElementType.*;


@Target({TYPE, CONSTRUCTOR,METHOD})
public @interface MyAnnotation4 {
}
```

```java
@MyAnnotation4
public class Student {
    
    @MyAnnotation4
    int eat;
    
    @MyAnnotation4
    public void eat(){

    }
}
```

##### Documented

用于指定被该元注解修饰的注解类将被Javadoc工具提取成文档，默认情况下，Javadoc是不包括注解的，但是加上了这个注解生成的文档中就会带着注解了。

##### Inherited

被它修饰的Annotation将具有继承性，如果某个类使用了被@Inherited修饰的Annotation，那其子类将自动具有该注释。

案例：

注解：如果MyAnno注解使用了@Inherited之后，就具备了继承性，那么相当于子类Student也是用了这个MyAnno

```java
@Inherited
public @interface MyAnno {
}
```

父类：

```java
@MyAnno
public class Person {
}
```

子类：

```java
public class Student extends Person{
}
```

### 枚举

#### 引入

【1】数学：枚举法

1<x<4				2<y<5

求x+y=6

枚举法：一枚一枚的列举出来，前提：有限，确定

【2】在Java中，类的对象是有限个，确定的，这个类我们可以定义为枚举类。

举例：

【3】自定义枚举类

```java
package com.msb.enum01;

/**
 * @ClassName: Season
 * @Author: rain
 * @Date: 2022/10/14 - 10 - 14 - 7:40 下午
 * @Description:自定义枚举类
 * @Version: 1.0
 */

public class Season {
    //属性
    private final String seasonName; //季节名字
    private final String seasonDesc; //季节描述


    //利用构造器对属性进行赋值操作：
    //构造器私有化，外界不能调用这个构造器，只能Season内部自己调用
    Season(String seasonName, String seasonDesc) {
        this.seasonName = seasonName;
        this.seasonDesc = seasonDesc;
    }

    //多个对象之间用逗号连接，最后用分号连接
    Season SPRING = new Season("春天", "春暖花开");
    Season SUMMER = new Season("夏天", "我永远也忘不了那个夏天》");
    Season AUTUMN = new Season("秋天", "收获");
    Season WINTER = new Season("冬天", "下雪");

    //利用get方法获取类的两个属性

    public String getSeasonName() {
        return seasonName;
    }

    public String getSeasonDesc() {
        return seasonDesc;
    }

    //重写toString方法

    @Override
    public String toString() {
        return "Season{" +
                "seasonName='" + seasonName + '\'' +
                ", seasonDesc='" + seasonDesc + '\'' +
                '}';
    }
}
```



#### JDK1.5以后使用enum关键字创建枚举类

```java
package com.msb.enum01;

/**
 * @ClassName: Season
 * @Author: rain
 * @Date: 2022/10/14 - 10 - 14 - 7:40 下午
 * @Description:
 * @Version: 1.0
 */

public enum Season {
    //提供枚举类的数量是有限的, enum枚举类要求对象（常量）必须放在最开始位置
    //多个对象之间用逗号连接，最后用分号连接
    SPRING("春天", "春暖花开"),
    SUMMER("夏天", "我永远也忘不了那个夏天》"),
    AUTUMN("秋天", "收获"),
    WINTER("冬天", "下雪");

    //属性
    private final String seasonName; //季节名字
    private final String seasonDesc; //季节描述


    //利用构造器对属性进行赋值操作：
    //构造器私有化，外界不能调用这个构造器，只能Season内部自己调用
    Season(String seasonName, String seasonDesc) {
        this.seasonName = seasonName;
        this.seasonDesc = seasonDesc;
    }


    //利用get方法获取类的两个属性

    public String getSeasonName() {
        return seasonName;
    }

    public String getSeasonDesc() {
        return seasonDesc;
    }

    //重写toString方法

    @Override
    public String toString() {
        return "Season{" +
                "seasonName='" + seasonName + '\'' +
                ", seasonDesc='" + seasonDesc + '\'' +
                '}';
    }
}
```

```java
public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        Season summer = Season.SUMMER;
        System.out.println(summer);
        System.out.println(summer.getSeasonName());
    }
}
```

使用枚举类：

```java
public class TestSeanson {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        Season winter = Season.WINTER;
        System.out.println(winter.SPRING);
        //enum关键字对应的枚举类的上层父类是：java.lang.Enum
        //但是我们自定义的枚举类的上层父类是：Object
        System.out.println(Season.class.getSuperclass().getName());
    }
}
```

在源码中经常看到别人的枚举类形态

```java

public enum Season {
    SPRING,
    SUMMER,
    AUTUMN,
    WINTER;}

```

为什么这么简单：因为这个枚举类底层没有属性，属性，构造器，toString，get方法斗删掉不写了，然后案例来说应该写为SPRING（），现在连（）都删掉不写

案例：Thread类中的State

```java
public enum State {
    /**
     * Thread state for a thread which has not yet started.
     */
    NEW,

    /**
     * Thread state for a runnable thread.  A thread in the runnable
     * state is executing in the Java virtual machine but it may
     * be waiting for other resources from the operating system
     * such as processor.
     */
    RUNNABLE,

    /**
     * Thread state for a thread blocked waiting for a monitor lock.
     * A thread in the blocked state is waiting for a monitor lock
     * to enter a synchronized block/method or
     * reenter a synchronized block/method after calling
     * {@link Object#wait() Object.wait}.
     */
    BLOCKED,

    /**
     * Thread state for a waiting thread.
     * A thread is in the waiting state due to calling one of the
     * following methods:
     * <ul>
     *   <li>{@link Object#wait() Object.wait} with no timeout</li>
     *   <li>{@link #join() Thread.join} with no timeout</li>
     *   <li>{@link LockSupport#park() LockSupport.park}</li>
     * </ul>
     *
     * <p>A thread in the waiting state is waiting for another thread to
     * perform a particular action.
     *
     * For example, a thread that has called {@code Object.wait()}
     * on an object is waiting for another thread to call
     * {@code Object.notify()} or {@code Object.notifyAll()} on
     * that object. A thread that has called {@code Thread.join()}
     * is waiting for a specified thread to terminate.
     */
    WAITING,

    /**
     * Thread state for a waiting thread with a specified waiting time.
     * A thread is in the timed waiting state due to calling one of
     * the following methods with a specified positive waiting time:
     * <ul>
     *   <li>{@link #sleep Thread.sleep}</li>
     *   <li>{@link Object#wait(long) Object.wait} with timeout</li>
     *   <li>{@link #join(long) Thread.join} with timeout</li>
     *   <li>{@link LockSupport#parkNanos LockSupport.parkNanos}</li>
     *   <li>{@link LockSupport#parkUntil LockSupport.parkUntil}</li>
     * </ul>
     */
    TIMED_WAITING,

    /**
     * Thread state for a terminated thread.
     * The thread has completed execution.
     */
    TERMINATED;
}
```

#### 枚举类的常用方法

```java
package com.msb.enum02;

/**
 * @ClassName: Season
 * @Author: rain
 * @Date: 2022/10/14 - 10 - 14 - 8:44 下午
 * @Description:
 * @Version: 1.0
 */

public enum Season {
    SPRING,
    SUMMER,
    AUTUMN,
    WINTER;
}
```

```java
package com.msb.enum02;

/**
 * @ClassName: TestSeason
 * @Author: rain
 * @Date: 2022/10/14 - 10 - 14 - 8:44 下午
 * @Description:
 * @Version: 1.0
 */


public class TestSeason {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {

        //enum关键字创建的Season枚举类上面的上层父类是：java.lang.Enum，常用方法子类Seanson可以直接拿来用
        //toString
        Season autumn = Season.AUTUMN;
        System.out.println(autumn);

        System.out.println("------");
        //values：返回枚举类对象的数组
        Season[] values = Season.values();
        for(Season s:values){
            System.out.println(s);
        }
        System.out.println("------");
        //valueof:通过对象名字获取这个枚举对象
        //注意：对象的名字必须传正确，否则抛出异常
        Season autumn1 = Season.valueOf("AUTUMN");
        System.out.println(autumn1);
    }
}
```



#### 枚举类实现接口

如果枚举类内部方法这样写

```java
public enum TestEnum implements TestInterface{
    SPRING,
    SUMMER,
    AUTUMN,
    WINTER;
    @Override
    public void show(){
        System.out.println("1234");
    }
}
```

上面的枚举类对象，调用show方法都是同一个方法



实现接口

```java
package com.msb.enum03;

/**
 * @ClassName: TestInterface
 * @Author: rain
 * @Date: 2022/10/14 - 10 - 14 - 8:57 下午
 * @Description:实现接口
 * @Version: 1.0
 */

public interface TestInterface {
    public void show();
}
```

实现枚举类

```java
package com.msb.enum03;

/**
 * @ClassName: TestEnum
 * @Author: rain
 * @Date: 2022/10/14 - 10 - 14 - 9:00 下午
 * @Description:实现枚举类
 * @Version: 1.0
 */


public enum TestEnum implements TestInterface{
    SPRING{
        @Override
        public void show(){
            System.out.println("这是春天");
        }
    },
    SUMMER{
        @Override
        public void show(){
            System.out.println("这是夏天");
        }
    },
    AUTUMN{
        @Override
        public void show(){
            System.out.println("这是秋天");
        }
    },
    WINTER{
        @Override
        public void show(){
            System.out.println("这是冬天");
        }
    };
}
```

实现类

```java
public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        TestEnum spring = TestEnum.SPRING;
        spring.show();

        TestEnum winter = TestEnum.WINTER;
        winter.show();
    }
}
```

实际应用：

使用枚举类代替具体属性

```java
package com.msb.enum04;

/**
 * @ClassName: Person
 * @Author: rain
 * @Date: 2022/10/14 - 10 - 14 - 9:09 下午
 * @Description:
 * @Version: 1.0
 */


public class Person {
    private int age;
    private String name;
    private Gandet sex;

    public Person() {
    }

    public Person(int age) {
        this.age = age;
    }
    public Person(String name){
        this.name = name;
    }
    

    public Gandet getSex() {
        return sex;
    }

    public void setSex(Gandet sex) {
        this.sex = sex;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }



    @Override
    public String toString() {
        return "Person{" +
                "age=" + age +
                ", name='" + name + '\'' +
                ", sex='" + sex + '\'' +
                '}';
    }
}
```

枚举类

```java
package com.msb.enum04;

/**
 * @ClassName: Gandet
 * @Author: rain
 * @Date: 2022/10/14 - 10 - 14 - 9:19 下午
 * @Description:
 * @Version: 1.0
 */

public enum Gandet {
    男,女;
}
```

测试类

```java
package com.msb.enum04;

/**
 * @ClassName: Test
 * @Author: rain
 * @Date: 2022/10/14 - 10 - 14 - 9:21 下午
 * @Description:
 * @Version: 1.0
 */


public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        Person p = new Person();
        p.setAge(10);
        p.setName("张三");
        p.setSex(Gandet.男);
        System.out.println(p.toString());
    }
}
```

枚举与swicth的应用

```java
package com.msb.enum04;

/**
 * @ClassName: Test02
 * @Author: rain
 * @Date: 2022/10/14 - 10 - 14 - 9:23 下午
 * @Description:
 * @Version: 1.0
 */

public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        Gandet sex = Gandet.男;
        //switch后面的括号中可以传入枚举类型
        //switch后面可以放入：int,byte,char,String,枚举
        switch (sex){
            case 女 -> System.out.println("是女孩");
            case 男 -> System.out.println("是男孩");
        }
    }
}
```

------



## 第12章 IO流

### File类

#### 引入

【1】文件，目录

文件：文件属于文件的一种，与普通文件载体不同，文件是以[硬盘](https://baike.baidu.com/item/硬盘/159825?fromModule=lemma_inlink)为载体存储在计算机上的信息集合。

文件可以是[文本文档](https://baike.baidu.com/item/文本文档?fromModule=lemma_inlink)、[图片](https://baike.baidu.com/item/图片/372416?fromModule=lemma_inlink)、[程序](https://baike.baidu.com/item/程序/13831935?fromModule=lemma_inlink)等等。文件通常具有点+三个字母的[文件扩展名](https://baike.baidu.com/item/文件扩展名?fromModule=lemma_inlink)，用于指示[文件类型](https://baike.baidu.com/item/文件类型?fromModule=lemma_inlink)（例如，图片文件常常以[JPEG](https://baike.baidu.com/item/JPEG/213408?fromModule=lemma_inlink)格式保存并且文件扩展名为.[jpg](https://baike.baidu.com/item/jpg/880403?fromModule=lemma_inlink)

文件夹（目录）：目录文件是长度固定的记录式文件。大多数操作系统如[UNIX](https://baike.baidu.com/item/UNIX?fromModule=lemma_inlink)、[DOS](https://baike.baidu.com/item/DOS/32025?fromModule=lemma_inlink)采用多级目录机构 ，称为树型目录结构。 从根目录出发到任一[非叶](https://baike.baidu.com/item/非叶?fromModule=lemma_inlink)结点或树页结点都有且只有一条路径。系统为用户提供一个目前使用的工作目录，称为当前目录。 目录分解法：将目录项分为：名号目录项，基本目录项。 目录文件也分为名号目录文件和基本目录文件。 文件存取控制通过文件的共享，保护和保密三方面体现。 文件的共享是一个文件可以允许多个用户共同使用。

【2】查看文件/目录的信息：

右键-属性

【3】在Java程序中操作文件/目录 ？

Java将盘符上的文件/目录，将它的信息进行了封装，封装为一个对象，Java程序最擅长的就是操纵对象，这个对象就是 — file类

盘符上的文件 — 封装为对象 — 对象属于file类的对象 — 有了这个对象，我们程序就可以直接操纵这个对象，通过这个对象获取文件的各种信息，还可以对文件进行创建，删除。

#### 对文件进行操作

```java
package com.msb.file;

import java.io.File;
import java.io.IOException;

/**
 * @ClassName: Test01
 * @Author: rain
 * @Date: 2022/10/15 - 10 - 15 - 10:30 上午
 * @Description:
 * @Version: 1.0
 */


public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws IOException {
        //将文件封装为一个File类的对象
        File f1 = new File("/Users/rain/Desktop/createcsv/TestFile/text01.txt");
        //File.separator会自动识别当前系统的文件分割符
        File f2 = new File("d:"+ File.separator+"test.txt"); //建议使用这种

        System.out.println("文件是否可读："+ f1.canRead());
        System.out.println("文件是否可写："+ f1.canWrite());
        System.out.println("文件的名字："+ f1.getName());
        System.out.println("上级目录："+ f1.getParent());
        System.out.println("是否是一个目录："+ f1.isDirectory());
        System.out.println("是否是一个文件："+ f1.isFile());
        System.out.println("是否隐藏："+f1.isHidden());
        System.out.println("文件的大小："+f1.length());

        //如果文件存在，就删除，如果文件不存在就创建
//        if(f1.exists()){
//            f1.delete();
//        }else {
//            f1.createNewFile();
//        }
        System.out.println(f1==f2); //比较两个对象的地址
        System.out.println(f1.equals(f2)); //比较两个对象对应的文件的地址


        //跟路径相关的,toString() 方法根相对路径一样
        System.out.println("绝对路径："+ f1.getAbsolutePath());
        System.out.println("相对路径："+ f1.getPath());
        System.out.println(f1.toString());


        File f4 = new File("demo.txt");
        if (!f4.exists()) {
            f4.createNewFile();
        }else {
            f4.delete();
        }

        System.out.println("绝对路径："+ f4.getAbsolutePath());
        System.out.println("相对路径："+ f4.getPath());
        System.out.println(f4.toString());
    }
}
```

#### 对目录进行操作

```java
package com.msb.file;

import java.io.File;

/**
 * @ClassName: Test02
 * @Author: rain
 * @Date: 2022/10/15 - 10 - 15 - 10:49 上午
 * @Description:对目录相关的操作
 * @Version: 1.0
 */


public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        File f1 = new File("/Users/rain/Desktop/Pragom/JAVA/马士兵");

        //跟文件相关的方法
        System.out.println("文件是否可读："+ f1.canRead());
        System.out.println("文件是否可写："+ f1.canWrite());
        System.out.println("文件的名字："+ f1.getName());
        System.out.println("上级目录："+ f1.getParent());
        System.out.println("是否是一个目录："+ f1.isDirectory());
        System.out.println("是否是一个文件："+ f1.isFile());
        System.out.println("是否隐藏："+f1.isHidden());
        System.out.println("文件的大小："+f1.length());
        System.out.println("绝对路径："+ f1.getAbsolutePath());
        System.out.println("相对路径："+ f1.getPath());
        System.out.println(f1.toString());

        //根目录相关的方法
        File f2 = new File("/Users/rain/Desktop/createcsv/TestFile/a/b/f/d");
        //创建目录
//        f2.mkdir();//创建单层目录
        //f2.mkdirs();//创建多层目录

        //删除目录：如果删除目录的话，只会删除一层，前提：这层目录是空的，里面没有内容，如果有内容就不会删除
        f2.delete();

        //查看：
        String[] list = f1.list();//文件夹下目录/文件对应的名字的数组
        for (String s:list) {
            System.out.println(s);
        }

        System.out.println("================");
        File[] files = f1.listFiles();//作用更广泛
        for (File f : files) {
            System.out.println("文件的名字："+f.getName()+","+f);
        }

    }
}
```

### IO流

#### 引入

【1】File类：封装文件/目录的各种信息，对目录/文件进行操作，但是我们不可以获取到文件/目录中的内容。

【2】引入：IO流

 I/O：Input/Output的缩写，用于处理设备之间的数据传输。

【3】形象理解：IO流 当作一根管：

【4】IO流的体系结构：





#### 案例：通过java程序完成文件的复制操作

##### 功能分解1：文件 —》程序：FileReader

通过FileReader类读取文件，这种是一个字符一个字符的进行读取，速度慢

```java
package com.msb.io01;

import java.io.File;
import java.io.FileReader;
import java.io.IOException;

/**
 * @ClassName: Test01
 * @Author: rain
 * @Date: 2022/10/15 - 10 - 15 - 3:32 下午
 * @Description: FileReader 读取文件
 * @Version: 1.0
 */


public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws IOException {
        //文件 --- 程序
        //有一个文件  -- 创建File类的对象
        File f = new File("/Users/rain/Desktop/createcsv/TestFile/text01.txt");
        //利用FileReader这个流，将这个管对到源文件上   --》  创建一个FileReader的流的对象
        FileReader fr = new FileReader(f);
        //进行操作"吸"的动作   ---》 读取动作
        //当文件读取完之后，在读取得到的返回值是-1
//        int n1 = fr.read();
//        int n2 = fr.read();
//        int n3 = fr.read();
//        int n4 = fr.read();
//        int n5 = fr.read();
//        int n6 = fr.read();
//        System.out.println(n1);
//        System.out.println(n2);
//        System.out.println(n3);
//        System.out.println(n4);
//        System.out.println(n5);
//        System.out.println(n6);

        //方式1
//        int n = fr.read();
//        while (n != -1) {
//            System.out.println(n);
//            n = fr.read();
//        }
        //方式2:
        int n;
        while ((n = fr.read())!=-1) {
            System.out.println((char)n);
        }

        //"管" 不用了，就要关闭  --》 关闭流
        fr.close();
    }
}
```



想一次五个字符的读取:

```java
package com.msb.io01;

import java.io.File;
import java.io.FileReader;

/**
 * @ClassName: Test02
 * @Author: rain
 * @Date: 2022/10/15 - 10 - 15 - 3:50 下午
 * @Description: 基于FileReader利用缓冲数组读取文件
 * @Version: 1.0
 */


public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception {
        //文件 --- 程序
        //1。有一个文件  -- 创建File类的对象
        File f = new File("/Users/rain/Desktop/createcsv/TestFile/text01.txt");
        //2。利用FileReader这个流，将这个管对到源文件上   --》  创建一个FileReader的流的对象
        FileReader fr = new FileReader(f);
        //3.进行操作"吸"的动作   ---》 读取动作
        //引入一个小车，这个小车一次读取五个快递
        char[] ch = new char[5];
        int len = fr.read(ch);  //一次性读取五个；返回值是这个数组中的有效长度
        while (len != -1) {
            //错误方式
//            for (int i = 0; i < ch.length; i++) {
//                System.out.println(ch[i]);
//            }
            //正确方式1:
            for(int i = 0; i < len; i++){
                System.out.print(ch[i]);
            }

            //正确方式2:将数组转为String
//            String str = new String(ch, 0, len);
//            System.out.print(str);
            len = fr.read(ch);
        }
        //"管" 不用了，就要关闭  --》 关闭流
        fr.close();
    }
}
```

##### 功能分解2:	程序 —》 文件： FileWriter

一个字符一个字符的输出：

```java
package com.msb.io01;

import java.io.File;
import java.io.FileWriter;
import java.io.IOException;

/**
 * @ClassName: Test03
 * @Author: rain
 * @Date: 2022/10/15 - 10 - 15 - 4:07 下午
 * @Description: 一个字符一个字符的输出：
 * @Version: 1.0
 */


public class Test03 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws IOException {
        //1.有个目标文件
        File f = new File("/Users/rain/Desktop/createcsv/TestFile/demo.txt");
        //2.FileWriter 管对到文件上去
        FileWriter fw = new FileWriter(f);
        //3.开始动作：输出动作
        //一个字符一个字符的输出
        String str = "1244";
        for (int i = 0; i < str.length(); i++) {
            fw.write(str.charAt(i));
        }
        //4.关闭流
        fw.close();
    }
}
```



```
如果目标文件不存在的话，那么会自动创建文件
如果目标文件存在的话：
new FileWriter(f),  相当于对源文件进行覆盖操作
new FileWriter(f，true), 相当于对源文件进行覆盖操作，不是追加
new FileWriter(f，false),相当于对源文件进行追加，而不是覆盖
```

利用缓冲数组进行输出：

```java
public class Test03 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws IOException {
        //1.有个目标文件
        File f = new File("/Users/rain/Desktop/createcsv/TestFile/demo.txt");
        //2.FileWriter 管对到文件上去
        FileWriter fw = new FileWriter(f);
        //3.开始动作：输出动作
        //一个字符一个字符的输出
        String str = "1244";
        char[] chars = str.toCharArray();
        fw.write(chars);
        //4.关闭流
        fw.close();
    }
}
```



##### 功能分解3:	文件 — 程序 — 文件： FileReader-FileWriter 实现文件复制

```java
package com.msb.io01;

import java.io.File;
import java.io.FileReader;
import java.io.FileWriter;

/**
 * @ClassName: Test04
 * @Author: rain
 * @Date: 2022/10/15 - 10 - 15 - 4:17 下午
 * @Description: 利用FileReader类和FileWriter类进行文件的复制，字符流传输
 * @Version: 1.0
 */


public class Test04 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception{
        StringBuilder sb = fileCopy("/Users/rain/Desktop/createcsv/TestFile/text01.txt");
        fileWriter("/Users/rain/Desktop/createcsv/TestFile/filecopy" ,sb);
    }

    //将从文件中得到的内容返回给StringBuilder类中
    public static StringBuilder fileCopy(String pathName) throws Exception{
        File f = new File(pathName);
        FileReader fr = new FileReader(f);
        StringBuilder sb = new StringBuilder();
        char[] ch = new char[10];
        int len = fr.read(ch);
        while (len != -1) {
            for (int i = 0; i < len; i++) {
                System.out.print(ch[i]);
                sb.append(ch[i]);
            }
            len = fr.read(ch);
        }
        fr.close();
        return sb;
    }

    /**
     *
     * @param pathName 要传入的文件地址
     * @param sb  传入的内容，类型为StringBuilder
     * @throws Exception 可能会出现异常
     */
    public static void fileWriter(String pathName,StringBuilder sb) throws Exception{
        File f = new File(pathName);
        if (!f.exists()) {
            f.createNewFile();
        }

        FileWriter fw = new FileWriter(f);
        fw.write(String.valueOf(sb));
        fw.close();
    }
}
```



```java
package com.msb.io01;

import java.io.File;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;

/**
 * @ClassName: Test05
 * @Author: rain
 * @Date: 2022/10/15 - 10 - 15 - 7:08 下午
 * @Description: 文件传输
 * @Version: 1.0
 */


public class Test05 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws IOException {
        //原文件
        File f1 = new File("/Users/rain/Desktop/createcsv/TestFile/demo.txt");

        //目标文件
        File f2 = new File("/Users/rain/Desktop/createcsv/TestFile/file1");

        //3.搞一个读取的管，插到原文件上
        FileReader fr = new FileReader(f1);

        //4.搞一个输出的管，插到目标文件上
        FileWriter fw = new FileWriter(f2);

        //5.开始
        //方式1:一个字符一个字符的传输
//        int n = fr.read();
//        while (n != -1) {
//            fw.write(n);
//            n = fr.read();
//        }

        //方式2:利用缓冲字符数组：
//        char[] ch = new char[5];
//        int len = fr.read(ch);
//        while (len != -1) {
//            fw.write(ch, 0, len); //将缓冲数组中有效长度输出
//            len = fr.read(ch);
//        }

        //方式3:利用缓冲数组，将数组转为String写出
        char[] ch = new char[5];
        int len = fr.read(ch);
        while (len != -1) {
            String s = new String(ch,0,len);
            fw.write(s);
            len = fr.read(ch);
        }

        fw.close();
        fr.close();

    }
}
```

#### 警告：不要用字符流操作非文本文件

文本文件：.txt. .java. 	.c	.cpp	—建议用字符流操作：FileReader，FileWriter 

非文本文件： jpg	mp3  mp4	doc	ppt	--建议用字节流操作：

#### 利用try/catch处理异常的方式

```java
package com.msb.io01;

import java.io.*;

/**
 * @ClassName: Test05
 * @Author: rain
 * @Date: 2022/10/15 - 10 - 15 - 7:08 下午
 * @Description: 文件传输
 * @Version: 1.0
 */


public class Test05 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //原文件
        File f1 = new File("/Users/rain/Desktop/createcsv/TestFile/demo.txt");
        //目标文件
        File f2 = new File("/Users/rain/Desktop/createcsv/TestFile/file1");
        FileReader fr = null;
        FileWriter fw = null;
        try {
            //3.搞一个读取的管，插到原文件上
            fr = new FileReader(f1);

            //4.搞一个输出的管，插到目标文件上
            fw = new FileWriter(f2);

            //5.开始
            //方式1:一个字符一个字符的传输
//        int n = fr.read();
//        while (n != -1) {
//            fw.write(n);
//            n = fr.read();
//        }

            //方式2:利用缓冲字符数组：
//        char[] ch = new char[5];
//        int len = fr.read(ch);
//        while (len != -1) {
//            fw.write(ch, 0, len); //将缓冲数组中有效长度输出
//            len = fr.read(ch);
//        }

            //方式3:
            char[] ch = new char[5];
            int len = fr.read(ch);
            while (len != -1) {
                String s = new String(ch,0,len);
                fw.write(s);
                len = fr.read(ch);
            }
        }catch (FileNotFoundException e){
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            try {
                if (fw != null) {
                    fw.close();
                }
            } catch (IOException e) {
                e.printStackTrace();
            }
            try {
                if (fr != null) {
                    fr.close();
                }
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```



#### FileInputStream读取文件，FileOutPut输出文件

【1】利用字节流读取文本文件：

```java
package com.msb.io02;

import java.io.File;
import java.io.FileInputStream;

/**
 * @ClassName: Test01
 * @Author: rain
 * @Date: 2022/10/15 - 10 - 15 - 7:31 下午
 * @Description:
 * @Version: 1.0
 */


public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception{
        //功能：利用字节流将文件中的内容来读取到程序中
        //1.有个源文件
        File file = new File("/Users/rain/Desktop/createcsv/TestFile/demo.txt");
        //2.将一个字节流这个管兑到源文件中
        FileInputStream fis = new FileInputStream(file);
        //3.开始读取动作
         /*
        细节1:
        文件是utf-8进行存储的，所以英文字符，底层实际占有1个字节
        但是中文字符，底层实际占有3个字节

        细节2:
        如果文件是文本文件，那么就不要使用字节流来读取文件了，建议使用字符流

        细节3:
        read()读取一个字符，返回值是int类型，而不是byte类型？
        read方法对底层进行流处理，让返回的数据都是"正数"
        就是为了避免如果字节返回的是-1的话，那到底是读入的字节，还是到文件结尾。
         */
        int count = 0;
        int n = fis.read();
        while(n!=-1){
            count++;
            System.out.println(n);
            n=fis.read();
        }
        System.out.println("count = " +count);

        //4.关闭流
        fis.close();
    }
}
```

【2】利用字节流读取非文本文件：（以图片为案例：）

```java
package com.msb.io02;

import java.io.File;
import java.io.FileInputStream;

/**
 * @ClassName: Test02
 * @Author: rain
 * @Date: 2022/10/15 - 10 - 15 - 7:49 下午
 * @Description:
 * @Version: 1.0
 */

public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception{
        //功能：利用字节流将文件中的内容来读取到程序中
        //1.有个源文件
        File file = new File("/Users/rain/Desktop/createcsv/TestFile/123.jpg");
        //2.将一个字节流这个管兑到源文件中
        FileInputStream fis = new FileInputStream(file);
        //3.开始读取动作
        int count = 0;
        int n = fis.read();
        while(n!=-1){
            count++;
            System.out.println(n);
            n=fis.read();
        }
        System.out.println("count = " +count);
        //4.关闭流
        fis.close();
    }
}
```

【3】利用字节流缓冲数组读取文件

```java
package com.msb.io02;

import java.io.File;
import java.io.FileInputStream;

/**
 * @ClassName: Test03
 * @Author: rain
 * @Date: 2022/10/15 - 10 - 15 - 7:52 下午
 * @Description: 利用字节缓冲数组读取文件
 * @Version: 1.0
 */


public class Test03 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception{
        //功能：利用字节流将文件中的内容来读取到程序中
        //1.有个源文件
        File file = new File("/Users/rain/Desktop/createcsv/TestFile/123.jpg");
        //2.将一个字节流这个管兑到源文件中
        FileInputStream fis = new FileInputStream(file);
        //3.开始读取动作
        //制作一个快递员的数组小车
        byte[] ch = new byte[1024*6];
        int count = 0;
        int len = fis.read(ch);
        while (len!=-1){
            for (int i = 0; i < len; i++) {
                count++;
                System.out.println(ch[i]);
            }
            len = fis.read(ch);
        }
        System.out.println("count = "+count);
        fis.close();
    }
}
```

【4】利用FileInputStream，FileOutputStream完成非文本文件的复制

```java
package com.msb.io02;

import java.io.File;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;

/**
 * @ClassName: Test04
 * @Author: rain
 * @Date: 2022/10/15 - 10 - 15 - 8:03 下午
 * @Description: 利用FileInputStream 和 FileOutputStream 来完成非文本文件的复制，利用try/catch异常处理
 * @Version: 1.0
 */

public class Test04 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //源文件
        File f1 = new File("/Users/rain/Desktop/createcsv/TestFile/123.jpg");
        //目标文件
        File f2 = new File("/Users/rain/Desktop/createcsv/TestFile/abc.jpg");

        //创建字节输入流
        FileInputStream fis = null;
        //创建字节输出流
        FileOutputStream fos = null;

        try {
            fis = new FileInputStream(f1);
            fos = new FileOutputStream(f2);

            //设置计数器，来查看文件大小
            int count = 0;
            //创建缓冲数组来存储管道中传来的字节
            byte[] data = new byte[1024*10];
            //读取开始
            int len = fis.read(data);
            //开始输出
            while (len != -1) {
                count = count +len;
                //提取从data数组中，从0到数组有效长度的数据
                fos.write(data, 0, len);
                //再次从输入字节流管道读取数据
                len = fis.read(data);
            }
            System.out.println("文件大小为：" + count + "B.");
        }catch (Exception e) {
            e.printStackTrace();
        }
        finally {
            //关闭流管道，后用先关
            try {
                if (fos != null) {
                    fos.close();
                }
            } catch (IOException e) {
                e.printStackTrace();
            }
            try {
                if (fis != null) {
                    fis.close();
                }
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```

### 缓冲字节流（处理流）BufferInputStream, BufferOutputStream

【1】一个字节一个字节

```java
public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception{
        //功能：利用字节流将文件中的内容来读取到程序中
        //1.有个源文件
        File file = new File("/Users/rain/Desktop/createcsv/TestFile/123.jpg");
        //2.将一个字节流这个管兑到源文件中
        FileInputStream fis = new FileInputStream(file);
        //3.开始读取动作
        int count = 0;
        int n = fis.read();
        while(n!=-1){
            count++;
            System.out.println(n);
            n=fis.read();
        }
        System.out.println("count = " +count);

        //4.关闭流
        fis.close();
    }
}
```



【2】利用缓冲字节数组

```java
public class Test03 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception{
        //功能：利用字节流将文件中的内容来读取到程序中
        //1.有个源文件
        File file = new File("/Users/rain/Desktop/createcsv/TestFile/123.jpg");
        //2.将一个字节流这个管兑到源文件中
        FileInputStream fis = new FileInputStream(file);
        //3.开始读取动作
        //制作一个快递员的数组小车
        byte[] ch = new byte[1024*6];
        int count = 0;
        int len = fis.read(ch);
        while (len!=-1){
            for (int i = 0; i < len; i++) {
                count++;
                System.out.println(ch[i]);
            }
            len = fis.read(ch);
        }
        System.out.println("count = "+count);
        fis.close();
    }
}
```



【3】利用缓冲区：

单纯靠 FileInputStream,FileOutStream是不可以完成的，这个时候就需要功能的加强，这个加强就需要引入新的流（在FileInputStream,FileOutStream外面再套一层流）：BufferedInputStream,BufferedOutputStream ——处理流

缓冲区内部也是一个数组,byte[] nuf = 8192

代码：

```java
package com.msb.io02;

import java.io.*;

/**
 * @ClassName: Test05
 * @Author:rain
 * @Date:2022/10/15 - 10 - 15 - 8:33 下午
 * @Description:利用缓冲数组来完成文件传输
 * @Version: 1.0
 */


public class Test05 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception{
        //1.有个源图片
        File f1 = new File("/Users/rain/Desktop/createcsv/TestFile/abc.jpg");
        //2.有一个目标图片
        File f2 = new File("/Users/rain/Desktop/createcsv/TestFile/222.jpg");
        //3.有一个输入的管道对到源文件：
        FileInputStream fis = new FileInputStream(f1);
        //4.有一个输出的管道 对到目标文件：
        FileOutputStream fos = new FileOutputStream(f2);
        //5.功能加强：在FileInputStram外面在套一个管：BufferedInputStream
        BufferedInputStream bis = new BufferedInputStream(fis);
        //6.功能加强：在FileOutputStream外面套一个管：BufferedOutputStream
        BufferedOutputStream bos = new BufferedOutputStream(fos);

        //7.开始动作：
        //1.利用缓冲数组来中间缓冲
        long startTime = System.currentTimeMillis();
        byte[] buf = new byte[1024*7];
        int len = bis.read(buf);
        while (len != -1) {
            bos.write(buf, 0, len);
//            bos.flush();  底层已经帮我门做了刷新缓冲区的操作，不用我们手动完成，底层调用flushBuffer（）
            len = bis.read(buf);
        }

        long endTime = System.currentTimeMillis();
        System.out.println("文件传输用的时间为："+(endTime - startTime));

        //8.关闭流
        //倒着关
        bos.close();
        bis.close();
    }
}
```

### 对非文本文件复制的三种方式的效率

利用缓冲区最快

```java
    long startTime = System.currentTimeMillis();
    long endTime = System.currentTimeMillis();
    System.out.println("文件传输用的时间为："+(endTime - startTime));
```
利用两个时间差计算效率



### 用BufferedReader,BufferWriter字符缓冲流，来完成文本文件的复制

【1】转换流：作用：将字节流和字符流进行转换

【2】转换流：属于字节流还是字符流？

InputStreamReader

OutputStreamWriter

【3】图解：



【4】将输入的字节流转换为字符流：代码：

```java
package com.msb.io02;

import java.io.*;

/**
 * @ClassName: Test06
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 10:09 上午
 * @Description: 利用BufferReader, BufferWriter 字符流完成文本文件传输
 * @Version: 1.0
 */


public class Test06 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception{
        //1.有个源文件
        File f1 = new File("/Users/rain/Desktop/createcsv/TestFile/demo.txt");
        //2.有一个目标文件
        File f2 = new File("/Users/rain/Desktop/createcsv/TestFile/log03.txt");
        //3.需要一个管对到源文件
        FileWriter fw = new FileWriter(f2);
        //4.需要一个管对到目标文件
        FileReader fr = new FileReader(f1);
        //5.创建一个输入缓冲区对到输入管中
        BufferedWriter bw = new BufferedWriter(fw);
        //6.创建一个输出缓冲区对到输出管中
        BufferedReader br = new BufferedReader(fr);

        //7.开始传输
        //设置开始时间
        long startTime = System.currentTimeMillis();
        //方式1:读取一个字符，输出一个字符
//        int len = br.read();
//        while (len != -1){
//            bw.write(len);
//            len = br.read();
//        }

        //方式2:利用char缓冲数组
//        char[] buf = new char[10];
//        int len = br.read(buf);
//        while (len != -1){
//            for (int i = 0; i < len; i++) {
//                bw.write(buf, 0,i);
//            }
//            len = br.read(buf);
//        }

        //方式3:利用String类型
        String str = br.readLine(); //每次读取文本文件中的一行，返回字符串
        while (str != null) {
            bw.write(str);
            //在文本文件中重写换行
            bw.newLine();
            str = br.readLine();
        }


        long endTime = System.currentTimeMillis();
        System.out.println("所用时间："+ (endTime - startTime));
        //8.关闭流
        bw.close();
        br.close();
    }
}
```

### 转换流- InputStreamReader, OutputStreamWriter完成文件转换

【1】利用FileInputStream字节流输入文件。通过InputStreamReader完成字节流对字符流的转换，输出到系统控制台

```java
package com.msb.io03;

import java.io.File;
import java.io.FileInputStream;
import java.io.InputStreamReader;

/**
 * @ClassName: Test01
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 10:50 上午
 * @Description: FileInputStream字节流输入文件。通过InputStreamReader完成字节流对字符流的转换，
 * @Version: 1.0
 */


public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception{
        //1.输入源文件
        File f = new File("/Users/rain/Desktop/createcsv/TestFile/demo.txt");
        //2.利用字节流输入文件
        FileInputStream fis = new FileInputStream(f);
        //3.加入转换流，将字节流转换为字符流
        //将字节转换为字符的时候，需要指定一个编码，这个编码根文件本身的编码格式统一
        //如果编码不同意的话，将会出现乱码格式
        InputStreamReader isr = new InputStreamReader(fis, "utf-8");

        //4.完成文件读取
        char[] buf = new char[20];
        int len = isr.read(buf);
        while (len != -1) {
            System.out.println(new String(buf,0,len));
            len = isr.read(buf);
        }
    }
}
```

【2】利用InputStreamReader, OutputStreamWriter完成文件复制。

```java
package com.msb.io03;

import java.io.*;

/**
 * @ClassName: Test02
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 11:19 上午
 * @Description: FileInputStream字节流输入文件。通过InputStreamReader完成字节流对字符流的转换,在用
 * OutputStreamWriter字节流转换字节流 FileOutputStream.
 * @Version: 1.0
 */

public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception{
        //1.有一个源文件
        File f1 = new File("/Users/rain/Desktop/createcsv/TestFile/demo.txt");
        //2.有一个目标文件
        File f2 = new File("/Users/rain/Desktop/createcsv/TestFile/demo01.txt");
        //3.输入方向
        FileInputStream fis = new FileInputStream(f1);
        InputStreamReader isr = new InputStreamReader(fis, "gbk");

        //4.输出方向
        FileOutputStream os = new FileOutputStream(f2);
        OutputStreamWriter osw = new OutputStreamWriter(os,"gbk");

        //5.开始动作
        char[] ch = new char[1024*8];
        int len = isr.read(ch);
        while(len != -1){
            osw.write(ch, 0, len);
            len = isr.read(ch);
        }

        //6.关闭流
        osw.close();
        isr.close();
    }
}
```

### System类对IO流的支持：

【1】System的属性：

System.in ： “标准”输入流—— 默认情况下，从键盘输入

System.out ： “标准”输出流 —— 默认情况下，输出到控制台

【2】System.in: “标准”输入流

```java
package com.msb.io04;

import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import java.util.Scanner;

/**
 * @ClassName: Test01
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 1:50 下午
 * @Description:
 * @Version: 1.0
 */


public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception {
        //得到的是标准的输入流：---从键盘输入：
        InputStream in = System.in;
        //调用方法:
        int n = in.read();
        System.out.println(n);

        //以前的案例：从键盘录入一个int类型的数据
        //从上面的代码证明，键盘录入实际是System.in
        //形象的理解：System.in管，这个管对到键盘上，所以你从键盘录入的话，就从管中到程序了
//        Scanner的作用：扫描器，其扫描作用，扫键盘的从这根管出来的数据
//        Scanner sc = new Scanner(System.in);
//        int c = sc.nextInt();
//        System.out.println(c);

        //既然scanner的作用是扫描，不一定得扫System.in进来的东西，还可以扫描其他的东西
        Scanner sc = new Scanner(new FileInputStream(new File("/Users/rain/Desktop/createcsv/TestFile/demo.txt")));
        while(sc.hasNext()){
            System.out.println(sc.next());
        }
    }
}
```

【3】System.out：返回的输出流，打印流，（PrintStream）

```java
package com.msb.io04;

import java.io.PrintStream;

/**
 * @ClassName: Test02
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 1:59 下午
 * @Description: system.out
 * @Version: 1.0
 */


public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //写到控制台：
        PrintStream out = System.out;
        //调用方法
        out.print("你打哈"); //直接在控制台写出，不换行
        out.print("但动物啊");
        out.print("挖大");
        out.print("大大");

        out.println("342343"); //直接在控制台写出，并换行
        out.println("342343");
        out.println("342343");
        out.println("342343");

        System.out.println("fff");
    }
}
```





### 练习：键盘录入的东西输出到文件中

![image-20221018161002956](/Users/rain/Library/Application Support/typora-user-images/image-20221018161002956.png)

代码：

```java
package com.msb.io04;

import java.io.*;

/**
 * @ClassName: Test03
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 2:05 下午
 * @Description: 从键盘录入内容，输出到文件中
 * @Version: 1.0
 */


public class Test03 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception {
        //1.输入方向,
        //键盘录入，
        InputStream is = System.in; //输入字节流
        //将字节流转换字符流
        InputStreamReader isr = new InputStreamReader(is,"utf-8");
        //在isr上套一个缓冲流
        BufferedReader br = new BufferedReader(isr);

        //2. 输出方向 -- 目标文件
        //创建目标文件
        File file = new File("/Users/rain/Desktop/createcsv/TestFile/demo02.txt");
        //创建输出字符流
        FileWriter fw = new FileWriter(file);
        //在fw上套一个缓冲流
        BufferedWriter bw = new BufferedWriter(fw);

        //3.开始动作
        String s = br.readLine();
        while(!s.equals("exit")){
            bw.write(s);
            bw.newLine(); //文件中换行
            s = br.readLine();
        }


        //4.关闭流
        bw.close();
        br.close();
    }
}
```

### 数据流：DataInputStream,DataOutputStream

【1】数据流：用来操作基本数据类型和字符串的

【2】

DataInputStream: 将文件中存储的基本数据类型和字符串，写入内存的变量中

代码：

```java
package com.msb.io05;

import java.io.DataOutputStream;
import java.io.File;
import java.io.FileOutputStream;

/**
 * @ClassName: Test01
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 2:25 下午
 * @Description:  DataOutputStream： 将内存中的基本数据类型和字符串的变量写出文件中
 * @Version: 1.0
 */


public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception{
//        DataOutputStream： 将内存中的基本数据类型和字符串的变量写出文件中
         //目标文件
//        File f = new File("/Users/rain/Desktop/createcsv/TestFile/demo02.txt");
//        FileOutputStream fos = new FileOutputStream(f);
//        DataOutputStream dos = new DataOutputStream(fos);

        DataOutputStream dos = new DataOutputStream(new FileOutputStream(new File("/Users/rain/Desktop/createcsv/TestFile/demo02.txt")));

        String s = "2123";
        dos.writeUTF(s);
        dos.writeLong(344);
        dos.writeBoolean(true);
        dos.writeDouble(33.3);
        dos.close();
    }
}
```

DataOutputStream： 将内存中的基本数据类型和字符串的变量写出文件中

代码：

```java
package com.msb.io05;

import java.io.DataInputStream;
import java.io.File;
import java.io.FileInputStream;

/**
 * @ClassName: Test02
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 2:57 下午
 * @Description:
 * @Version: 1.0
 */


public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception{
        DataInputStream dis = new DataInputStream(new FileInputStream(new File("/Users/rain/Desktop/createcsv/TestFile/demo02.txt")));

        //将文件中的内容读取到程序
        System.out.println(dis.readUTF());
        System.out.println(dis.readLong());;
        System.out.println(dis.readBoolean());
        System.out.println(dis.readDouble());;

        dis.close();
    }
}
```

读入，读出的文件，必须要匹配

对象流：ObjectInputStream,ObjectOutputStream

【1】对象流：ObjectInputStream,ObjectOutputStream

用于存储和读取基本数据类型或对象的处理流。它的强大之处就是可以把java中的对象写入到数据源中，也能把对象从数据源中还原回来。

【2】序列化和反序列化：

ObjectInputStream类：把内存中的java对象转换成平台无关的二进制数据，从而允许把这种二进制数据持久的保持在磁盘上，

用ObjectOutputStream类：当其他程序获取了这种二进制数据，就可以恢复到原来的Java对象 —反序列化

代码：

首先将一个字符串对象写到文件中(序列化的过程)

```java
package com.msb.io06;

import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.ObjectOutputStream;

/**
 * @ClassName: Test01
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 3:18 下午
 * @Description: 用ObjectOutputStream完成对象到文件的输出过程 --- 序列化
 * @Version: 1.0
 */


public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws IOException {
        ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream(new File("/Users/rain/Desktop/createcsv/TestFile/demo03.txt")));

        //创建字符串对象
        String s = "乃低洼";
        //进行读取动作，输出到文件中
        oos.writeObject(s);
        oos.close();
    }
}
```

将对象从文件中读取（反序列化的过程）

代码：

```java
package com.msb.io06;

import java.io.File;
import java.io.FileInputStream;
import java.io.ObjectInputStream;

/**
 * @ClassName: Test02
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 3:20 下午
 * @Description: 用ObjectInputStream完成文件 到程序的输入 -- 反序列化
 * @Version: 1.0
 */


public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception{
        ObjectInputStream ois = new ObjectInputStream(new FileInputStream(new File("/Users/rain/Desktop/createcsv/TestFile/demo03.txt")));

        String s = (String) (ois.readObject());
        System.out.println(s);
        ois.close();
    }
}
```

结果：

![截屏2022-10-17 下午3.23.29](/Users/rain/Desktop/截屏2022-10-17 下午3.23.29.png)

【4】代码：操作自定义类的对象：

自定义的Person类：

```java
package com.msb.test07;

/**
 * @ClassName: Person
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 3:27 下午
 * @Description: 
 * @Version: 1.0
 */

public class Person {
    public String name;
    public int age;

    public Person() {
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```

测试类：

```java
package com.msb.test07;

import java.io.File;
import java.io.FileOutputStream;
import java.io.ObjectOutputStream;

/**
 * @ClassName: test01
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 3:26 下午
 * @Description:
 * @Version: 1.0
 */


public class test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception{
        //序列化：将内存中对象 -- 文件：
        //有一个对象
        Person p = new Person("张三",28);

        ObjectOutputStream ois = new ObjectOutputStream(new FileOutputStream(new File("/Users/rain/Desktop/createcsv/TestFile/demo03.txt")));
        ois.writeObject(p);
    }
}
```

发生异常：

![截屏2022-10-17 下午3.34.50](/Users/rain/Desktop/截屏2022-10-17 下午3.34.50.png)

原因：

你想要序列化的那个对象对应的类，必须实现一个接口：

```java
public interface Serializable {
}
```

接口内部，什么都没有，这种接口叫做标识接口。

起到标识作用，标识什么呢？只要实现这个接口的类的对象才能序列化，否则不可以

解决办法：将Person类实现这个标识接口/

```java
package com.msb.test07;

import java.io.Serializable;

/**
 * @ClassName: Person
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 3:27 下午
 * @Description:
 * @Version: 1.0
 */

public class Person implements Serializable {
    public String name;
    public int age;

    public Person() {
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```

序列化成功

![截屏2022-10-17 下午3.40.58](/Users/rain/Desktop/截屏2022-10-17 下午3.40.58.png)

Person具备了序列化的能力，这个二进制文件我们看不懂，但是程序可以看懂。我们可以进行反序列化

代码：

```java
package com.msb.test07;

import java.io.File;
import java.io.FileInputStream;
import java.io.ObjectInputStream;

/**
 * @ClassName: Test02
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 3:42 下午
 * @Description:
 * @Version: 1.0
 */


public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception{
        ObjectInputStream ois = new ObjectInputStream(new FileInputStream(new File("/Users/rain/Desktop/createcsv/TestFile/demo03.txt")));

      //读入对象 -- 读到内存中
        Person p = (Person)(ois.readObject());
        ois.close();

        System.out.println(p);
    }
}
```

反序列化成功：

![截屏2022-10-17 下午3.43.58](/Users/rain/Desktop/截屏2022-10-17 下午3.43.58.png)

因为没有重写toString方法，所以结果这样

二进制数据		— 内存 ， 成功

【5】serialVersionUID

凡是实现serialVersion接口（标识接口）的类都有一个表示序列化版本标识符的静态变量：

- private static final long serialVersionUID；
- serialVersionUID用来表明类的不同版本间的兼容性。简言之，其目的是以序列化对象进行版本控制，有关各版本反序列化时是否兼容
- 如果类没有显示定义这个静态变量，他 的值是Java运行环境根据类的内部细节自动生成的，若类的实例变量做了修改，serialVersionUID可能发生变化，故建议，显式声明。
- 简单来说，Java的反序列化机制是通过在运行判断类的serialVersionUID来验证版本一致性的，在进行反序列化时，jvm会把传来的字节流中的serialVersionUID与本地相应实体类的serialVersionUID相比较，如果相同就认为一致的，可以进行反序列化，否则就会出现序列化版本不一致的异常，（InvalidCastException）

加入toString方法后，再次进行序列化

```java
package com.msb.test07;

import java.io.Serializable;

/**
 * @ClassName: Person
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 3:27 下午
 * @Description:
 * @Version: 1.0
 */

public class Person implements Serializable {
    public String name;
    public int age;

    public Person() {
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}
```

这时发生异常

```
序列化： 将Person对象 — 文件
当时那个 Person类没有 toString方法

现在在Person类中加入了toString方法，然后在进行反序列化，读进来的对象的类不带toString,本身这个类你加ltoString
这两个类不匹配问题
```

解决：给这个类加入一个序列号：serialVersionUID

```java
public class Person implements Serializable {
    public String name;
    public int age;
    private static final long serialVersionUID = 12355L;
```

【7】序列化的细节：

（1）被序列化的类的内部的所以属性，必须是可以序列化的（基本数据类型都是可序列化的）

（2）static , transient修饰的属性，不可以被序列化

进行序列化，反序列化

```java
package com.msb.test07;

import java.io.Serial;
import java.io.Serializable;

/**
 * @ClassName: Person
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 3:27 下午
 * @Description:
 * @Version: 1.0
 */

public class Person implements Serializable {
    @Serial
    private static final long serialVersionUID = -6868065656039973071L;
    private transient String name;
    private static int age;
    private Student f = new Student();



    public Person() {
    }


    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", f=" + f + ",age=" + age +
                '}';
    }
}
```

结果：

```java
public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception{
        ObjectInputStream ois = new ObjectInputStream(new FileInputStream(new File("/Users/rain/Desktop/createcsv/TestFile/demo03.txt")));

        Person p = (Person)(ois.readObject());
        ois.close();

        System.out.println(p);
    }
}
```

```
Person{name='null', f=com.msb.test07.Student@4629104a,agr0}
```

------



## 第14章 网络编程

### 引入

【1】网络编程：

把分布在不同地理区域的计算机与专门的外部设备用通信线路互连成一个规模大、功能强的网络系统，从而使总多的计算机可以方便地互相传递信息、共享硬件、软件、数据信息等资源。

设备之间在网络中进行数据传输，发生/接收数据。

网络：两台或两台以上的机器就能构成网络

【2】通信的两个重要因素：port + IP

通过IP进行定位，每个机器都有自己的唯一IP，

端口号：每个应用程序都有自己唯一的端口号

域名 —— DNS解析器 —— IP地址

【3】设置之间进行传输的时候，必须遵照一定的规则， —— 通信协议

TCP/IP协议

【4】TCP协议：可靠

建立连接：（三次挥手）

断开连接：（四次挥手）

【5】UDP协议：不可靠的

### InetAddress,InetSocketAddress

【1】InetAddress，封装了IP地址

InetAddress的相关练习

```java
import java.net.InetAddress;
import java.net.UnknownHostException;

/**
 * @ClassName: Test01
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 4:30 下午
 * @Description:
 * @Version: 1.0
 */


public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws UnknownHostException {
        //封装Ip
        //InetAddress 不能直接创建对象，因为InetAddress()被default修饰了
//        InetAddress ia = new InetAddress();
        InetAddress ia = InetAddress.getByName("172.18.49.36");
        System.out.println(ia);

        InetAddress ib = InetAddress.getByName("localhost"); //localhost指代的是本机IP地址
        System.out.println(ib);
        InetAddress ia1 = InetAddress.getByName("127.0.0.1"); //127.0.0.1指代的是本机的ip地址
        System.out.println(ia1);
        InetAddress ia2 = InetAddress.getByName("Rain.local");//封装计算机名
        System.out.println(ia2);
        InetAddress ia3 = InetAddress.getByName("www.baidu.com");
        System.out.println(ia3);

        System.out.println(ia2.getHostName()); //获取域名
        System.out.println(ia2.getHostAddress()); //获取IP地址
    }
}
```

【2】InetSocketAddress封装了端口号，IP地址

InetSocketAddress的相关练习

```java
public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        InetSocketAddress isa = new InetSocketAddress("172.18.49.36", 8080);
        System.out.println(isa);
        System.out.println(isa.getHostName());
        System.out.println(isa.getAddress().getHostAddress());
    }
}
```

### 网络通信原理 — 套接字

![image-20221018160942627](/Users/rain/Library/Application Support/typora-user-images/image-20221018160942627.png)

#### 基于TCP的网络编程

功能：模拟网站的登录，客户端录入密码， 然后服务队进行验证。

##### 功能分解1：单向通行

客户端发送信息，服务端接收：

```java
package com.msb.test02;

import java.io.DataOutputStream;
import java.io.IOException;
import java.io.OutputStream;
import java.net.Socket;

/**
 * @ClassName: TestClient
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 5:03 下午
 * @Description: 单向通信客户端
 * @Version: 1.0
 */


public class TestClient {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws IOException {
        //1.创建套接字：指定端口号和IP
        Socket s = new Socket("172.18.49.36", 8888);
        //2.对于程序员来说，向外发送数据 ， -- 利用输出流
        OutputStream os = s.getOutputStream();
        DataOutputStream dos = new DataOutputStream(os);
        //利用这个OutputStream就可以发送数据了，但是没有直接发送String的方法
        //所以我们又在OutputStream外面套了一个处理流：DataOutputStream。
        dos.writeUTF("你好");

        //3.关闭流
        dos.close();
        os.close();
        s.close();
    }

}
```

```java
package com.msb.test02;

import java.io.DataInputStream;
import java.io.IOException;
import java.io.InputStream;
import java.net.ServerSocket;
import java.net.Socket;

/**
 * @ClassName: TestServer
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 7:35 下午
 * @Description:单向通信服务端
 * @Version: 1.0
 */


public class TestServer {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws IOException {
        //1.创建套接字：指定服务器的端口号
        ServerSocket ss = new ServerSocket(8888);
        //2. 等待客户端发送信息
        Socket s = ss.accept(); //阻塞方法：等待接收客户端的信息，什么时候接收到信息。什么时候继续走
//        accept()返回值为一个Socket,这个Socket其实就是客户端的Socket
        //3.感受到的操作流：
        InputStream is = s.getInputStream();
        DataInputStream dis = new DataInputStream(is);

        //4.读取客户端发来的数据
        String str = dis.readUTF();
        System.out.println("客户端发来的数据为："+str);

        //5.关闭流
        dis.close();
        is.close();
        s.close();
    }
}
```



##### 功能分解2:   双向通信

服务端：

```java
package com.msb.test02;

import java.io.*;
import java.net.ServerSocket;
import java.net.Socket;

/**
 * @ClassName: TestServer
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 7:35 下午
 * @Description:
 * @Version: 1.0
 */


public class TestServer {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws IOException {
        //1.创建套接字：指定服务器的端口号
        ServerSocket ss = new ServerSocket(8888);
        //2. 等待客户端发送信息
        Socket s = ss.accept(); //阻塞方法：等待接收客户端的信息，什么时候接收到信息。什么时候继续走
//        accept()返回值为一个Socket,这个Socket其实就是客户端的Socket
        //3.感受到的操作流：
        InputStream is = s.getInputStream();
        DataInputStream dis = new DataInputStream(is);

        //4.读取客户端发来的数据
        String str = dis.readUTF();
        System.out.println("客户端发来的数据为："+str);

        //向客户端输出一句话  --- 操作流 -- 输出流
        OutputStream os = s.getOutputStream();
        DataOutputStream dos = new DataOutputStream(os);
        dos.writeUTF("数据已经接收");

        //5.关闭流
        dis.close();
        is.close();
        s.close();
    }
}
```

客户端：

```java
package com.msb.test02;

import java.io.*;
import java.net.Socket;

/**
 * @ClassName: TestClient
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 5:03 下午
 * @Description: 单向通信客户端
 * @Version: 1.0
 */


public class TestClient {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws IOException {
        //1.创建套接字：指定端口号和IP
        Socket s = new Socket("172.18.49.36", 8888);
        //2.对于程序员来说，向外发送数据 ， -- 利用输出流
        OutputStream os = s.getOutputStream();
        DataOutputStream dos = new DataOutputStream(os);
        //利用这个OutputStream就可以发送数据了，但是没有直接发送String的方法
        //所以我们又在OutputStream外面套了一个处理流：DataOutputStream。
        dos.writeUTF("你好");

        //接收从服务器的回话，--利用输入流
        InputStream is = s.getInputStream();
        DataInputStream dis = new DataInputStream(is);
        String str = dis.readUTF();
        System.out.println(str);

        //3.关闭流
        dos.close();
        os.close();
        s.close();
    }

}
```



##### 功能分解3: 	传送对象流

```java
package com.msb.test02;

import java.io.Serial;
import java.io.Serializable;

/**
 * @ClassName: User
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 8:08 下午
 * @Description: 传输的封装类
 * @Version: 1.0
 */


public class User implements Serializable {
    @Serial
    private static final long serialVersionUID = 2438935633985766289L;
    private String name;
    private String pwd;

    public User() {
    }

    public User(String name, String pwd) {
        this.name = name;
        this.pwd = pwd;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getPwd() {
        return pwd;
    }

    public void setPwd(String pwd) {
        this.pwd = pwd;
    }

}
```



客户端：

```java
package com.msb.test02;

import java.io.*;
import java.net.Socket;
import java.util.Scanner;

/**
 * @ClassName: TestClient
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 5:03 下午
 * @Description: 客户端
 * @Version: 1.0
 */


public class TestClient {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws IOException {
        //1.创建套接字：指定端口号和IP
        Socket s = new Socket("172.18.49.36", 8888);

        //录如账号密码
        Scanner sc = new Scanner(System.in);
        System.out.println("请录入你的账号");
        String name = sc.next();
        System.out.println("请录入你的密码");
        String pwd = sc.next();

        //将账号密码封装为一个对象
        User user = new User(name,pwd);

        //2.对于程序员来说，向外发送数据 ， -- 利用输出流
        OutputStream os = s.getOutputStream();
        ObjectOutputStream oos = new ObjectOutputStream(os);
        //利用这个OutputStream就可以发送数据了，但是没有直接发送String的方法
        //所以我们又在OutputStream外面套了一个处理流：DataOutputStream。
        oos.writeObject(user);

        //接收从服务器的回话，--利用输入流
        InputStream is = s.getInputStream();
        DataInputStream dis = new DataInputStream(is);
        boolean b = dis.readBoolean();
        if (b) {
            System.out.println("登录成功");
        }else{
            System.out.println("登录失败");
        }

        //3.关闭流
        dis.close();
        is.close();
        oos.close();
        os.close();
        s.close();
    }

}
```



服务端：

```java
package com.msb.test02;

import java.io.*;
import java.net.ServerSocket;
import java.net.Socket;

/**
 * @ClassName: TestServer
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 7:35 下午
 * @Description: 服务端
 * @Version: 1.0
 */


public class TestServer {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws IOException, ClassNotFoundException {
        //1.创建套接字：指定服务器的端口号
        ServerSocket ss = new ServerSocket(8888);
        //2. 等待客户端发送信息
        Socket s = ss.accept(); //阻塞方法：等待接收客户端的信息，什么时候接收到信息。什么时候继续走
//        accept()返回值为一个Socket,这个Socket其实就是客户端的Socket
        //3.感受到的操作流：
        InputStream is = s.getInputStream();
        ObjectInputStream ois = new ObjectInputStream(is);

        //4.读取客户端发来的数据
        User user = (User) ois.readObject();

        //对账号进行验证
        boolean flag = false;
        if ( user.getName().equals("娜娜") && user.getPwd().equals("1234") ) {
            flag = true;
        }

        //向客户端输出结果  --- 操作流 -- 输出流
        OutputStream os = s.getOutputStream();
        DataOutputStream dos = new DataOutputStream(os);
        dos.writeBoolean(flag);


        //5.关闭流
        dos.close();
        os.close();
        ois.close();
        is.close();
        s.close();
    }
}
```



##### 功能分解4:  使用try/catch异常捕获的对象流

测试类：

```java
package com.msb.work01;

import java.io.Serial;
import java.io.Serializable;

/**
 * @ClassName: User
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 8:50 下午
 * @Description:
 * @Version: 1.0
 */


public class User implements Serializable {
    @Serial
    private static final long serialVersionUID = -3918599886426951588L;
    private String name;
    private String pwd;

    //创建构造器
    public User() {
    }

    public User(String name, String pwd) {
        this.name = name;
        this.pwd = pwd;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getPwd() {
        return pwd;
    }

    public void setPwd(String pwd) {
        this.pwd = pwd;
    }
}
```

客户端：

```java
package com.msb.work01;

import java.io.*;
import java.net.Socket;
import java.net.UnknownHostException;
import java.util.Scanner;

/**
 * @ClassName: TestClient
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 8:37 下午
 * @Description: 使用异常捕获的TCP客户端
 * @Version: 1.0
 */


public class TestClient {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        Socket s = null;
        Scanner sc = null;
        String name = null;
        String pwd = null;
        User user = null;
        OutputStream os = null;
        ObjectOutputStream oos = null;
        InputStream is = null;
        DataInputStream dis = null;

        try {
            //1.创建套接字
            s = new Socket("172.18.49.36",9000);

            //录入信息
            sc = new Scanner(System.in);
            System.out.println("请输入你的账号：");
            name = sc.next();
            System.out.println("请输入你的密码：");
            pwd = sc.next();
            //将数据包装为对象
            user = new User(name,pwd);

            //2.对数据进行处理，利用对象流进行发送
            os = s.getOutputStream();
            oos = new ObjectOutputStream(os);
            oos.writeObject(user);

            //3.对服务的返回信息进行接收
            is = s.getInputStream();
            dis = new DataInputStream(is);
            boolean b = dis.readBoolean();
            if (b) {
                System.out.println("登录成功");
            }else {
                System.out.println("登录失败");
            }
        } catch (UnknownHostException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }finally {
            //4.关闭流
            try {
                if (dis != null) {
                    dis.close();
                }
            } catch (IOException e) {
                e.printStackTrace();
            }

            try {
                if (is != null) {
                    is.close();
                }
            } catch (IOException e) {
                e.printStackTrace();
            }

            try {
                if (oos != null) {
                    oos.close();
                }
            } catch (IOException e) {
                e.printStackTrace();
            }

            try {
                if (os != null) {
                    os.close();
                }
            } catch (IOException e) {
                e.printStackTrace();
            }

            try {
                if (s != null) {
                    s.close();
                }
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```

服务端：

```java
package com.msb.work01

import java.io.*;
import java.net.ServerSocket;
import java.net.Socket;

/**
 * @ClassName: TestServer
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 8:36 下午
 * @Description:使用异常捕获的TCP服务端
 * @Version: 1.0
 */


public class TestServer {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        ServerSocket ss = null;
        Socket s = null;
        InputStream is = null;
        ObjectInputStream ois = null;
        User user = null;
        OutputStream os = null;
        DataOutputStream dos = null;


        try {
            //1.创建服务端套接字
            ss = new ServerSocket(9000);
            s = ss.accept();

            //2.数据处理,将客户端发送的类的信息
            is = s.getInputStream();
            ois = new ObjectInputStream(is);
            user = (User) (ois.readObject());

            //判断录入的账号信息是否正确
            boolean flag = false;
            if (user.getName().equals("张三") && user.getPwd().equals("1234")) {
                flag = true;
            }

            //发送判断信息反馈到客户端
            os = s.getOutputStream();
            dos = new DataOutputStream(os);
            dos.writeBoolean(flag);
        } catch (IOException e) {
            e.printStackTrace();
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        }finally {
            //关闭流
            try {
                if(dos!=null){
                    dos.close();
                }
            }catch (IOException e) {
                e.printStackTrace();
            }

            try {
                if(ois!=null){
                    ois.close();
                }
            }catch (IOException e) {
                e.printStackTrace();
            }

            try {
                if(is!=null){
                    is.close();
                }
            }catch (IOException e) {
                e.printStackTrace();
            }

            try {
                if(s!=null){
                    s.close();
                }
            }catch (IOException e) {
                e.printStackTrace();
            }

            try {
                if(ss!=null){
                    ss.close();
                }
            }catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```

##### 功能分解5：多线程接收用户请求

遗留问题：服务器针对一个请求服务，之后服务器就关闭了，（程序自然就关闭了）

现在需要解决：服务器必须一直在坚听，一直开着，等待客户端的请求

在当前代码中，客户端不用动了

![截屏2022-10-18 上午10.45.14](/Users/rain/Desktop/截屏2022-10-18 上午10.45.14.png)

更改账号的服务器端：

```java
package com.msb.test02;

import java.io.*;
import java.net.ServerSocket;
import java.net.Socket;

/**
 * @ClassName: TestServer
 * @Author: rain
 * @Date: 2022/10/17 - 10 - 17 - 7:35 下午
 * @Description: 多线程服务端
 * @Version: 1.0
 */

public class TestServer {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        System.out.println("服务端启动。。");
        ServerSocket ss = null;
        Socket s = null;

        int count = 0; //定义一个计算器，用来统计登录用户的数量
        try {
            //1.创建服务端套接字，指定服务器的端口号
            ss = new ServerSocket(9000);
            //加入死循环，服务器一直监听客户端是否发送数据
            while (true) {
                //阻塞方法，等待客户端的数据，
                s = ss.accept();
                //每次过来的客户端请求要线程处理
                new TestServerThead(s).start();
                count++;
                //输出请求的客户端的信息
                System.out.println("当前是第"+count+"个用户访问服务器，对应的IP地址为:"+ s.getLocalAddress() );
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

服务器线程处理代码

```java
package com.msb.test02;

import java.io.*;
import java.net.Socket;

/**
 * @ClassName: TestServerThead
 * @Author: rain
 * @Date: 2022/10/18 - 10 - 18 - 10:30 上午
 * @Description:
 * @Version: 1.0
 */


public class TestServerThead extends Thread{
    //创建套接字对象
    public Socket s = null;

    public TestServerThead (Socket s){
        this.s = s;
    }

    @Override
    public void run() {
        InputStream is = null;
        ObjectInputStream ois = null;
        User user = null;
        OutputStream os = null;
        DataOutputStream dos = null;
        try{
            //2.数据处理,将客户端发送的类的信息
            is = s.getInputStream();
            ois = new ObjectInputStream(is);
            user = (User) (ois.readObject());

            //判断录入的账号信息是否正确
            boolean flag = false;
            if (user.getName().equals("张三") && user.getPwd().equals("1234")) {
                flag = true;
            }
            //发送判断信息反馈到客户端
            os = s.getOutputStream();
            dos = new DataOutputStream(os);
            dos.writeBoolean(flag);
        }catch (Exception e) {
            e.printStackTrace();
        }finally {//关闭流
            try {
                if(dos!=null){
                    dos.close();
                }
            }catch (IOException e) {
                e.printStackTrace();
            }
            try {
                if(ois!=null){
                    ois.close();
                }
            }catch (IOException e) {
                e.printStackTrace();
            }
            try {
                if(is!=null){
                    is.close();
                }
            }catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```



#### 基于UDP的网络编程



```
TCP：
客户端：Socket
服务器端：ServerSocket -- Socket
(客户端和服务器地位不平等)


UDP：
发送方：DatagramSocket   发送：数据包		DatagramPacket
接收方：DatagramSocket	 接收：数据包		DatagramPacket
(发送方和接收法地位平等)
```

案例：完成网站的咨询

##### 功能分解1: 单向通信

发送端：

```java
package com.msb.test03;

import java.io.IOException;
import java.net.*;

/**
 * @ClassName: TestSend
 * @Author: rain
 * @Date: 2022/10/18 - 10 - 18 - 1:34 下午
 * @Description:
 * @Version: 1.0
 */


public class TestSend {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws IOException {
        System.out.println("学生上线");
        //1.准备套接字：指定发送方的端口号
        DatagramSocket ds = new DatagramSocket(8888);
        //2.准备数据包
        String str  ="你好";
        byte[] bytes = str.getBytes();
        /*
            需要四个参数：
            1。指的是传送数据转为字节数据
            2.字节数组的长度
            3.封装接收方的IP
            4.指定接收方的端口号
        */
        DatagramPacket dp = new DatagramPacket(bytes, bytes.length, InetAddress.getByName("localhost"),9999);
        //发送
        ds.send(dp);

        //关闭流
        ds.close();

    }
}
```

接收端：

```java
package com.msb.test03;

import java.net.DatagramPacket;
import java.net.DatagramSocket;

/**
 * @ClassName: TestRecive
 * @Author: rain
 * @Date: 2022/10/18 - 10 - 18 - 1:39 下午
 * @Description:
 * @Version: 1.0
 */


public class TestRecive {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception{
        System.out.println("老师上线来");
        //1.创建套接字，指定接收方的端口
        DatagramSocket ds = new DatagramSocket(9999);
        //2.有一个空的数据包，打算用来接收，对方传过来的数据包
        byte[] bytes = new byte[1024];
        DatagramPacket dp = new DatagramPacket(bytes, bytes.length);
        //3.接收对方的数据包，然后放入我们的dp数据包中填充
        ds.receive(dp); //接收完后dp里面就填充好内容了

        //4.取出数据
        byte[] data = dp.getData();
        String str = new String(data,0,dp.getLength()); //取出数组中有效数据的长度
        System.out.println("学生对我说："+ str);

        //5.关闭流
        ds.close();
    }
}
```

##### 功能分解2: 双向通信

发送方：

```java
package com.msb.test03;

import java.io.IOException;
import java.net.*;
import java.util.Scanner;

/**
 * @ClassName: TestSend
 * @Author: rain
 * @Date: 2022/10/18 - 10 - 18 - 1:34 下午
 * @Description:
 * @Version: 1.0
 */


public class TestSend {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws IOException {
        System.out.println("学生上线。。");
        //1.准备套接字：指定发送方的端口号
        DatagramSocket ds = new DatagramSocket(8888);
        //2.准备数据包
        Scanner sc = new Scanner(System.in);
        System.out.print("学生说话：");
        String str  =sc.next();
        byte[] bytes = str.getBytes();
        /*
            需要四个参数：
            1。指的是传送数据转为字节数据
            2.字节数组的长度
            3.封装接收方的IP
            4.指定接收方的端口号
        */
        DatagramPacket dp = new DatagramPacket(bytes, bytes.length, InetAddress.getByName("localhost"),9999);
        //发送
        ds.send(dp);

        //接收老师的消息
        byte[] b1 = new byte[1024];
        DatagramPacket dp1 = new DatagramPacket(b1,b1.length);
        ds.receive(dp1);

        //取出数据
        byte[] data = dp1.getData();
        String s = new String(data,0, dp1.getLength());
        System.out.print("老师对我说：" + s);

        //关闭流
        ds.close();

    }
}
```

接收方：

```java
package com.msb.test03;

import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.InetAddress;
import java.util.Scanner;

/**
 * @ClassName: TestRecive
 * @Author: rain
 * @Date: 2022/10/18 - 10 - 18 - 1:39 下午
 * @Description:
 * @Version: 1.0
 */


public class TestRecive {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws Exception{
        System.out.println("老师上线了。。");
        //1.创建套接字，指定接收方的端口
        DatagramSocket ds = new DatagramSocket(9999);
        //2.有一个空的数据包，打算用来接收，对方传过来的数据包
        byte[] bytes = new byte[1024];
        DatagramPacket dp = new DatagramPacket(bytes, bytes.length);
        //3.接收对方的数据包，然后放入我们的dp数据包中填充
        ds.receive(dp); //接收完后dp里面就填充好内容了

        //4.取出数据
        byte[] data = dp.getData();
        String str = new String(data,0, dp.getLength()); //取出数组中有效数据的长度
        System.out.println("学生对我说："+ str);

        //老师回复消息
        //2.准备数据包
        Scanner sc = new Scanner(System.in);
        System.out.print("老师说：");
        String str1  = sc.next();
        byte[] b = str1.getBytes();
        DatagramPacket dp1 = new DatagramPacket(b, b.length, InetAddress.getByName("localhost"),8888);
        //发送
        ds.send(dp1);

        //5.关闭流
        ds.close();
    }
}
```

##### 功能分解3: 加入异常捕获处理

接收方：

```java
package com.msb.test03;

import java.io.IOException;
import java.net.*;
import java.util.Scanner;

/**
 * @ClassName: TestRecive
 * @Author: rain
 * @Date: 2022/10/18 - 10 - 18 - 1:39 下午
 * @Description:
 * @Version: 1.0
 */


public class TestRecive {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        System.out.println("老师上线了。。");
        DatagramSocket ds = null;
        try {
            //1.创建套接字，指定接收方的端口
            ds = new DatagramSocket(9999);
            //2.有一个空的数据包，打算用来接收，对方传过来的数据包
            byte[] bytes = new byte[1024];
            DatagramPacket dp = new DatagramPacket(bytes, bytes.length);
            //3.接收对方的数据包，然后放入我们的dp数据包中填充
            ds.receive(dp); //接收完后dp里面就填充好内容了

            //4.取出数据
            byte[] data = dp.getData();
            String str = new String(data,0, dp.getLength()); //取出数组中有效数据的长度
            System.out.println("学生对我说："+ str);

            //老师回复消息
            //2.准备数据包
            Scanner sc = new Scanner(System.in);
            System.out.print("老师说：");
            String str1  = sc.next();
            byte[] b = str1.getBytes();
            DatagramPacket dp1 = new DatagramPacket(b, b.length, InetAddress.getByName("localhost"),8888);
            //发送
            ds.send(dp1);
        } catch (UnknownHostException e) {
            e.printStackTrace();
        } catch (SocketException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }finally {
            try {
                if (ds != null) {
                    //5.关闭流
                    ds.close();
                }
            }catch (Exception e) {
                e.printStackTrace();
            }
        }
    }
}
```

发送方：

```java
package com.msb.test03;

import java.io.IOException;
import java.net.*;
import java.util.Scanner;

/**
 * @ClassName: TestSend
 * @Author: rain
 * @Date: 2022/10/18 - 10 - 18 - 1:34 下午
 * @Description:
 * @Version: 1.0
 */


public class TestSend {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        System.out.println("学生上线。。");
        DatagramSocket ds = null;
        try {
            //1.准备套接字：指定发送方的端口号
            ds = new DatagramSocket(8888);
            //2.准备数据包
            Scanner sc = new Scanner(System.in);
            System.out.print("学生说话：");
            String str  =sc.next();
            byte[] bytes = str.getBytes();
        /*
            需要四个参数：
            1。指的是传送数据转为字节数据
            2.字节数组的长度
            3.封装接收方的IP
            4.指定接收方的端口号
        */
            DatagramPacket dp = new DatagramPacket(bytes, bytes.length, InetAddress.getByName("localhost"),9999);
            //发送
            ds.send(dp);

            //接收老师的消息
            byte[] b1 = new byte[1024];
            DatagramPacket dp1 = new DatagramPacket(b1,b1.length);
            ds.receive(dp1);

            //取出数据
            byte[] data = dp1.getData();
            String s = new String(data,0, dp1.getLength());
            System.out.print("老师对我说：" + s);
        } catch (UnknownHostException e) {
            e.printStackTrace();
        } catch (SocketException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }finally {
            //关闭流
            try {
                if(ds != null) {
                    ds.close();
                }
            }catch(Exception e){
                e.printStackTrace();
            }
        }
    }
}
```

##### 功能分解4:完整通信

接收方：

```java
package com.msb.test03;

import java.io.IOException;
import java.net.*;
import java.util.Scanner;

/**
 * @ClassName: TestRecive
 * @Author: rain
 * @Date: 2022/10/18 - 10 - 18 - 1:39 下午
 * @Description:
 * @Version: 1.0
 */


public class TestRecive {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        System.out.println("老师上线了。。");
        DatagramSocket ds = null;
        try {
            //1.创建套接字，指定接收方的端口
            ds = new DatagramSocket(9999);
            while (true) {
                //2.有一个空的数据包，打算用来接收，对方传过来的数据包
                byte[] bytes = new byte[1024];
                DatagramPacket dp = new DatagramPacket(bytes, bytes.length);
                //3.接收对方的数据包，然后放入我们的dp数据包中填充
                ds.receive(dp); //接收完后dp里面就填充好内容了

                //4.取出数据
                byte[] data = dp.getData();
                String str = new String(data,0, dp.getLength()); //取出数组中有效数据的长度
                System.out.println("学生对我说："+ str);
                if (str.equals("byebye")) {
                    System.out.println("学生已经下线，我也要下线。");
                    break;
                }

                //老师回复消息
                //2.准备数据包
                Scanner sc = new Scanner(System.in);
                System.out.print("老师说：");
                String str1  = sc.next();
                byte[] b = str1.getBytes();
                DatagramPacket dp1 = new DatagramPacket(b, b.length, InetAddress.getByName("localhost"),8888);
                //发送
                ds.send(dp1);
            }
        } catch (UnknownHostException e) {
            e.printStackTrace();
        } catch (SocketException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }finally {
            try {
                if (ds != null) {
                    //5.关闭流
                    ds.close();
                }
            }catch (Exception e) {
                e.printStackTrace();
            }
        }
    }
}
```

发送方：

```java
package com.msb.test03;

import java.io.IOException;
import java.net.*;
import java.util.Scanner;

/**
 * @ClassName: TestSend
 * @Author: rain
 * @Date: 2022/10/18 - 10 - 18 - 1:34 下午
 * @Description:
 * @Version: 1.0
 */


public class TestSend {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        System.out.println("学生上线。。");
        DatagramSocket ds = null;
        try {
            //1.准备套接字：指定发送方的端口号
            ds = new DatagramSocket(8888);
            while (true) {
                //2.准备数据包
                Scanner sc = new Scanner(System.in);
                System.out.print("学生说话：");
                String str  =sc.next();
                byte[] bytes = str.getBytes();
        /*
            需要四个参数：
            1。指的是传送数据转为字节数据
            2.字节数组的长度
            3.封装接收方的IP
            4.指定接收方的端口号
        */
                DatagramPacket dp = new DatagramPacket(bytes, bytes.length, InetAddress.getByName("localhost"),9999);
                //发送
                ds.send(dp);

                if(str.equals("byebye")){
                    System.out.println("学生要下线了");
                    break;
                }
                //接收老师的消息
                byte[] b1 = new byte[1024];
                DatagramPacket dp1 = new DatagramPacket(b1,b1.length);
                ds.receive(dp1);

                //取出数据
                byte[] data = dp1.getData();
                String s = new String(data,0, dp1.getLength());
                System.out.print("老师对我说：" + s + "\n");
            }
        } catch (UnknownHostException e) {
            e.printStackTrace();
        } catch (SocketException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }finally {
            //关闭流
            try {
                if(ds != null) {
                    ds.close();
                }
            }catch(Exception e){
                e.printStackTrace();
            }
        }
    }
}
```

------

## 第11章  	集合

### 什么是算法和数据结构

【1】算法：

（1）可以解决具体问题：例如   1+2+3+4+5+。。。+100

解题流程 = 算法

（2）有设计解决的具体的流程：

算法1: 1+2=3 3+3=6 6+4=10 加到100

算法2:（1+100）* 50 = 101 * 50 — 高斯算法

（3）评价算法的具体的指标 — 时间复杂度和空间复杂度（从数学角度考虑）

--------------------------------------------------

【2】数据结构：就是在计算机的缓存，内存，硬盘，如何组织管理数据的。重点在结构上，是按照什么结构来组织管理我们的数据。

数据结构分为：

（1）逻辑结构： — 思想上的结构  — 线性表（数组，链表），图，树，栈，队列

（2）物理结构： — 真是结构。— 紧密结构（顺序结构），挑战结构（链式结构）

【3】紧密结构（顺序结构），跳转结构（链式结构）



### 集合的引入

【1】数组，集合都是对多个数据进行存储操作的，简称为容器。

PS：这里的存储指的都是内存层面的存储，而不是持久化存储（文件，音乐，图片，数据库）。

【2】数组：特点

（1）数组一旦指定了长度，那么长度就确定了，不可以更改

int[] arr =new int[6];

（2）数组一旦声明了类型以后，数组中只能存放这个类型的数据，只能存放同一类型的数据

int[] arr, String[] str, double[] d

【3】数组：缺点：

（1）数组一旦指定了长度，那么长度就被确定了，不可以更改

（2）删除，增加元素，效率低。

（3）数组中实际元素的数量是没有办法获取的，没有提供对应的方法或者属性来获取。

（4）数组存储：有序、重复、对于无序的，不可重复的数组不能满足要求

【4】正因为上面的缺点，引入了一个新的存储数据的结构		--		集合

【5】集合一章我们会学习了很多种集合，为什么要学习这么多集合呢？

因为不同集合底层数据结构不一样。

### 简要集合结构图

![image-20221018161027435](/Users/rain/Library/Application Support/typora-user-images/image-20221018161027435.png)

### 集合的应用场合

![image-20221018161040491](/Users/rain/Library/Application Support/typora-user-images/image-20221018161040491.png)

当需要将相同结构的个体整合到一起的时候，就需要集合。



### Collection接口

【1】ollection(接口)的概念:
作为单例集合中的顶级接口,里面定义了单例集合所共有的方法:以增添,删除,更改,查询,判断,转换方法为主

【2】Collection(接口)中的方法:
![截屏2022-10-18 下午4.21.42](/Users/rain/Desktop/截屏2022-10-18 下午4.21.42.png)

```java
package com.msb.test01;

import java.util.ArrayList;
import java.util.Collection;

/**
 * @ClassName: Test01
 * @Author: rain
 * @Date: 2022/10/18 - 10 - 18 - 3:48 下午
 * @Description:
 * @Version: 1.0
 */


public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        /*
        Collection接口的常用方法：
        增加：add()  addAll(Collection<? extends E> c)
        删除：clear()  remove(Object o)
        修改：
        查看：iterator()  size()
        判断：contains(Object o)  equals(Object o)   isEmpty()
         */
//        创建对象
        Collection col = new ArrayList();

        //增加元素
        col.add(19);
        col.add(1);
        col.add(39);
        col.add(5);
        System.out.println(col);
        ArrayList al = new ArrayList();
        al.add(19);
        al.add(1);
        al.add(39);
        al.add(5);
        //添加接口中的元素
//        col.addAll(al);
        System.out.println(al);

        col.remove(10); //删除指定元素
        System.out.println(col);

        System.out.println("接口中的元素个数为：" +col.size());
        System.out.println("接口的地址为：" +col.iterator());

        System.out.println(col.contains(5)); //如果此collection包含指定的元素，则返回 true 。
        System.out.println(col.equals(al)); //只要两个集合的元素都一样，就是true

        col.clear();//删除所有元素
        System.out.println(col.isEmpty());
    }
}
```

### Collection集合的遍历

```java
package com.msb.test01;

import java.util.ArrayList;
import java.util.Collection;
import java.util.Iterator;

/**
 * @ClassName: Test02
 * @Author: rain
 * @Date: 2022/10/18 - 10 - 18 - 4:47 下午
 * @Description:
 * @Version: 1.0
 */


public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //        创建对象
        Collection col = new ArrayList();

        //增加元素
        col.add(19);
        col.add(1);
        col.add(39);
        col.add(5);
        System.out.println(col);

        //对集合进行遍历（对元素进行遍历）

        //方式2:增强for循环
        for(Object o:col){
            System.out.println(o);
        }

        //方式3:iterator()
        Iterator it = col.iterator();
        while (it.hasNext()) {
            System.out.println(it.next());
        }
    }
}
```

### List接口常用方法和遍历方式

```java
package com.msb.test01;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

/**
 * @ClassName: Test03
 * @Author: rain
 * @Date: 2022/10/18 - 10 - 18 - 4:58 下午
 * @Description:
 * @Version: 1.0
 */


public class Test03 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        /*
        List接口中常用方法：
        增加：add(int index, E element) set(int index, E element)
        删除：remove(int index)  remove（obgect o）
        修改：set(int index, E element)
        查看：get(int index)
        判断：
         */
        List list = new ArrayList();
        list.add(23);
        list.add(256);
        list.add(3);
        list.add(1);
        list.add(5);
        list.add("abc");
        System.out.println(list);

        list.add(2,44);
        System.out.println(list);
        list.set(2,3);
        System.out.println(list);
        list.remove(2);//在集合中存入的是Integer类型数据的时候，调用remove方法的：remove(int index)
        list.remove("abc");
        System.out.println(list);

        Object o = list.get(0);
        System.out.println(o);


        //List集合：遍历：
        //方式1:普通for遍历
        System.out.println("-------");
        for (int i = 1; i < list.size(); i++) {
            System.out.println(list.get(i));
        }

        //方式2:增强for循环
        for (Object i:list){
            System.out.println(i);
        }

        //方式3:迭代器 Integer
        Iterator it = list.iterator();
        while (it.hasNext()) {
            System.out.println(it.next());
        }


    }
}
```

### ArrayList实现类（JDK1.7）

【1】在idea中切换JDK的方法：

![img](https://img-blog.csdnimg.cn/20210512230629496.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3R4eV8yMDE4,size_16,color_FFFFFF,t_70)

【2】ArrayList实现List接口的失误：

集合创始人 承认了这个失误，但是在后续的版本中没有删除，觉得没必要：![img](https://img-blog.csdnimg.cn/20210512230718395.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3R4eV8yMDE4,size_16,color_FFFFFF,t_70)

【3】底层重要属性：![img](https://img-blog.csdnimg.cn/20210512230803138.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3R4eV8yMDE4,size_16,color_FFFFFF,t_70)在JDK1.7中：在调用构造器的时候给底层数组elementData初始化，数组初始化长度为10：![img](https://img-blog.csdnimg.cn/20210512230825121.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3R4eV8yMDE4,size_16,color_FFFFFF,t_70)对应内存：![img](https://img-blog.csdnimg.cn/20210512230852599.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3R4eV8yMDE4,size_16,color_FFFFFF,t_70)调用add方法：

```java
    ArrayList al = new ArrayList();
    System.out.println(al.add("abc"));
    System.out.println(al.add("def"));
```
![img](https://img-blog.csdnimg.cn/20210512230941690.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3R4eV8yMDE4,size_16,color_FFFFFF,t_70)
当数组中的10个位置都满了的时候就开始进行数组的扩容，扩容长度为 原数组的1.5倍：![img](https://img-blog.csdnimg.cn/20210512231007130.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3R4eV8yMDE4,size_16,color_FFFFFF,t_70)

![img](https://img-blog.csdnimg.cn/20210512231016424.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3R4eV8yMDE4,size_16,color_FFFFFF,t_70)

![img](https://img-blog.csdnimg.cn/20210512231035113.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3R4eV8yMDE4,size_16,color_FFFFFF,t_70)



### ArrayList实现类（JDK1.8）

【1】JDK1.8底层依旧是[Object类](https://so.csdn.net/so/search?q=Object类&spm=1001.2101.3001.7020)型的数组，size:数组中有效长度：

![img](https://img-blog.csdnimg.cn/2021051223122987.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3R4eV8yMDE4,size_16,color_FFFFFF,t_70)

【2】[ArrayList](https://so.csdn.net/so/search?q=ArrayList&spm=1001.2101.3001.7020) al = new ArrayList();调用空构造器：

![img](https://img-blog.csdnimg.cn/20210512231245261.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3R4eV8yMDE4,size_16,color_FFFFFF,t_70)

【3】add方法：

![img](https://img-blog.csdnimg.cn/20210512231313692.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3R4eV8yMDE4,size_16,color_FFFFFF,t_70)

![img](https://img-blog.csdnimg.cn/20210512231323507.png)

![img](https://img-blog.csdnimg.cn/20210512231334807.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3R4eV8yMDE4,size_16,color_FFFFFF,t_70)

![img](https://img-blog.csdnimg.cn/20210512231343261.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3R4eV8yMDE4,size_16,color_FFFFFF,t_70)



### Vector实现类

【1】底层Object[数组](https://so.csdn.net/so/search?q=数组&spm=1001.2101.3001.7020)，int类型属性表示数组中有效长度：

![img](https://img-blog.csdnimg.cn/20210512231813224.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3R4eV8yMDE4,size_16,color_FFFFFF,t_70)

【2】[Vector](https://so.csdn.net/so/search?q=Vector&spm=1001.2101.3001.7020) v=new Vector();调用构造器：

![img](https://img-blog.csdnimg.cn/20210512231827802.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3R4eV8yMDE4,size_16,color_FFFFFF,t_70)

【3】add方法：![img](https://img-blog.csdnimg.cn/20210512231844106.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3R4eV8yMDE4,size_16,color_FFFFFF,t_70)

ArrayList和Vector类都是基于数组实现的List类，所以ArrayList和Vector类封装了一个动态的、允许再分配的Object[]数组。ArrayList或Vector对象使用initialCapacity参数来设置该数组的长度，当向ArrayList或Vector中添加元素超出了该数组元素的长度时，它们的initialCapacity会自动增加。
对于通常的编程场景，程序员无须关心ArrayList或Vector的initialCapaccity。但如果向ArrayList或Vector集合添加大量元素时，可以使用ensureCapacity（int minCapacity）方法一次性地增加initialCapacity。这可以减少重分配的次数。从而提高性能。
如果开始就知道ArrayList或Vector集合需要保存多少个元素，则可以在创建它们时就指定initialCapacity大小。如果创建空的initialCapacity集合时 不指定initialCapacity参数，则Object[]数组的长度默认为10。
除此之外，ArrayList和Vector还提供了如下两个方法来重新分配Object[]数组。
--void ensureCapacity(int minCapacity):将ArrayList或Vector几个的Object[]数组长度增加大于或等于minCapacity值。
--void trimToSize():调整ArrayList或Vector集合的Object[]数组长度为当前元素的个数。调用该方法可减少ArrayList或Vector集合对象占用的存储空间。
ArrayList和Vector在用法上几乎完全相同，但由于Vector是一个古老的集合，那时候Java还没有提供系统的几个框架，所以Vector里提供了一些方法名很长的方法，例如addElement(Object obj),实际上这个方法与add（Object obj）没有任何区别。从JDK1.2以后，Java提供了系统的集合框架，就将Vector改为实现List接口，作为List的实现之一，从而导致Vector里有一些功能重复的方法。
Vector的系列方法中方法名更短的方法属于后来新增的方法，方法名更长的方法则是Vector原有的方法。Java改写了Vector原有的方法，将其方法名缩短是为了简化编程。而ArrayList开始就作为List的主要实现类，因此没有那些方法名很长的方法，实际上，Vector具有很多缺点，通常尽量少用Vector实现类。
除此之外，ArrayList和Vector的显著区别是：ArrayList是线程不安全的，当多个线程访问同一个ArrayList集合时，如果有超过一个线程修改了ArrayList集合，则程序必须手动保证该集合的同步性：但Vector集合则是线程安全的，无须程序保证该集合的同步性，因为Verctor是线程安全的，所以Vector的性能比ArrayList的性能要低。实际上，即使需要保证List集合线程安全，也同样不推荐使用Vector是实现类。后面会介绍一个Collections工具类，它可以将一个ArrayList变成线程安全的。
Vector还提供了一个Stack子类，它用于模拟"栈"这种数据结构，”栈“通常是指”后进先出“的容器。最后push进栈的元素，将最先被”pop“出栈。与Java中的其他集合一样，进栈出栈的都是Objcet，因此从栈中取出元素后必须进行类型转换，除非你只是使用Object具有的操作。所以Stack类里提供了如下几个方法。
--Object peek()：返回”栈“的第一个元素，但并不将该元素”pop“出栈。
--Object pop():返回”栈“的第一个元素，并将该元素”pop“出栈。
void push(Object item):将一个元素”push“出栈，最后一个进"栈"的元素总是位于栈顶。
需要指出的是，由于Stack继承了Vector，因此它也是一个非常古老的Java集合类，它同样是线程安全的、性能较差的，因此应该尽量少用Stack类。

代码：

```java
package com.asse.ljb;

import java.util.ArrayList;
import java.util.List;
import java.util.ListIterator;

/**
 * list集合
 * 1.代表一个元素有序的集合,集合中的每个元素都有其对应的顺序索引
 * 2.允许使用重复元素,可以通过索引来访问指定位置的集合元素
 * 3.默认按元素的添加顺序设置元素的索引
 * 4.根据索引来操作集合元素的方法
 * 5.List 额外提供了一个 listIterator() 方法，该方法返回一个 ListIterator 对象，
 * 	 ListIterator 接口继承了 Iterator 接口，提供了专门操作 List 的方法:
 * 6.ArrayList 和 Vector 是 List 接口的两个典型实现,区别：
 *    ·Vector 是一个古老的集合，通常建议使用 ArrayList
 *    ·ArrayList 是线程不安全的，而 Vector 是线程安全的。
 *  ·即使为保证 List 集合线程安全，也不推荐使用 Vector
 */
public class ListTest {
	public static void main(String[] args) {
		List l = new ArrayList();
		l.add("123");
		l.add("cde");
		l.add("0123");
		System.out.println("for方法+get()方法输出集合中的所有数");
		for(int i = 0;i < l.size();i++) {
			System.out.println(l.get(i));
		}
		System.out.println("foreach方法输出集合中所有数");
		for (Object object : l) {
			System.out.println(object);
		}
		//sublist(index,index)方法输出左开右闭
		System.out.println("sublist(index,index)方法输出:" + l.subList(0, 3));
		System.out.println("sublist(index,index).size()方法输出长度:" + l.subList(0, 3).size());
		System.out.println("----list iterator----");
		System.out.println("ListIterator方法输出");
		ListIterator li = l.listIterator();
		while(li.hasNext()) {
			System.out.println(li.next());
		}
		System.out.println("list iterator prev");
		System.out.println("hasPrevious()方法倒序输出");
		while(li.hasPrevious()) {
			System.out.println(li.previous());
		}
	}
}
```



### 泛型

#### 引入

【1】什么是泛型（Generic）：

```j
泛型（generics）是Java 1.5中引入的新特性，泛型提供了编译时类型安全检测机制，该机制允许程序员在编译时检测到非法的类型。只要编译时不出现问题，运行时就不会出现ClassCastException（类型转换异常）。
        泛型的本质是参数化类型，也就是说所操作的数据类型被指定为一个参数。这种参数类型可以用在类、接口和方法的创建中，分别称为泛型类、泛型接口、泛型方法。
        Java集合都实现了泛型，允许程序在创建集合时就可以指定集合元素的类型，例如List<String>就表明这是一个只能存放String类型的List。List<String>就是参数化类型，也就是泛型，而String就是该List<String>泛型的类型参数。
        泛型只在编译阶段有效，在编译之后会进行泛型擦除的操作，不会传递到运行阶段。也就是说编译后的class文件中是不包含任何泛型信息的。
```

【2】没有泛型的时候使用集合代码：

```java
package com.msb.test01;

import java.util.ArrayList;

/**
 * @ClassName: Test01
 * @Author: rain
 * @Date: 2022/10/18 - 10 - 18 - 8:33 下午
 * @Description:
 * @Version: 1.0
 */


public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //创建一个ArrayList集合，向这个集合中存入学生的成绩：
        ArrayList al = new ArrayList();
        al.add(32);
        al.add(31);
        al.add(2);
        al.add(344);
        al.add(66);
        al.add(562);
        al.add("丽丽");

        //对集合遍历查看
        for (Object o : al){
            System.out.println(o);
        }
    }
}
```

如果不使用泛型的话，有缺点：

一般我们在使用泛型的时候，基本上往集合中存入的都是相同类型的数据， 便于管理，所以现在什么引用数据类型都可以存入集合，不方便。

【3】jdk 1.5 之后开始使用泛型，集合中使用泛型：

```java
package com.msb.test01;

import java.util.ArrayList;

/**
 * @ClassName: Test01
 * @Author: rain
 * @Date: 2022/10/18 - 10 - 18 - 8:33 下午
 * @Description:使用泛型
 * @Version: 1.0
 */

public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //创建一个ArrayList集合，向这个集合中存入学生的成绩：
        //加入泛型的优点：在编译时期就会对类型进行检查，不是泛型对应的类型就不可以添加入这个集合
        ArrayList <Integer> al = new ArrayList();
        al.add(32);
        al.add(31);
        al.add(2);
        al.add(344);
        al.add(66);
        al.add(562);
//        al.add("丽丽");
//        al.add(9.4);

        //对集合遍历查看
//        for (Object o : al){
//            System.out.println(o);
//        }

        for(Integer a:al){
            System.out.println(a);
        }
    }
}
```

【4】泛型总结：

（1）JDK1.5以后

（2）泛型实际就是一个<>引起来的 参数类型，这个参数类型 具体在使用的时候才会被确定

```java
public class ArrayList<E> extends AbstractList<E>
        implements List<E>, RandomAccess, Cloneable, java.io.Serializable
```

（3）使用了泛型以后，可以确定集合中存放数据的类型，在编译时期就可以检查出来

（4）使用泛型你可能觉得麻烦，实际使用了泛型才会简单，后续的遍历等操作简单。

（5）泛型的类型：都是引用数据类型，不能是基本数据类型

（6）ArrayList <Integer> al = new ArrayList<Integer>(); 在JDK1.7以后可以写为：ArrayList <Integer> al = new ArrayList<>();  —  <> — 钻石运算符



#### 自定义泛型结构



##### 泛型类，泛型接口

【1】泛型的定义和实例化

```java
package com.msb.test02;

/**
 * @ClassName: GenericTest
 * @Author: rain
 * @Date: 2022/10/18 - 10 - 18 - 8:48 下午
 * @Description:  GenericTest 这就是一个普通的类
 * GenericTest <A>  就是一个泛型类：
 *<>里面就是一个参数类型，但是这个类型是什么呢？这个类型现在是不确定的，相当于一个占位
 * 但是里面现在确定的是这个类型一定是一个引用数据类型，而不是基本数据类型
 * @Version: 1.0
 */

public class GenericTest<E> {
    int age;
    String name;
    E sex;

    public void a(E n){
    }
    public void b(E[] m){
    }
}

class Test{
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //GenericTest实例化
        //(1)实例化的时候不指定泛型：
        GenericTest gt1 = new GenericTest();
        gt1.a("adaf");
        gt1.a(19);
        gt1.a(2.44);
        gt1.b(new String[]{"dd","23"});

        //2。实例化的时候指定泛型  --- 推荐使用这种
        GenericTest<String> gt2 = new GenericTest<>();
        gt2.sex = "男";
        gt2.a("abf");
        gt2.b(new String[] {"你好","33"});
    }
}
```

【2】继承情况：

（1）父类指定泛型

```java
class SubGenericTest extends GenericTest<Integer> {

}

class Demo{
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //指定父类泛型，那么子类就不需要指定泛型了，直接使用
        SubGenericTest sgt = new SubGenericTest();
        sgt.a(19);
    }
}
```

（2）父类不指定泛型：

如果父类不指定泛型，那么子类也会变成一个泛型类，那这个E的类型可以在创建子类对象的时候确定：

```java
class SubGenericTest2<E> extends GenericTest<E>{

}

class Demo2{
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        SubGenericTest2<Stirngr> sgt = new SubGenericTest2<>();
        sgt.a("男");
        sgt.age = "你好";
    }
}
```

【3】应用场合

```java
public class ArrayList<E> extends AbstractList<E>
        implements List<E>, RandomAccess, Cloneable, java.io.Serializable
{
```

【4】细节：

（1）泛型类可以定义多个参数类型

```java
public class TestGeneric<A,B,C> {
    A age;
    B name;
    C sex;

    public void a(A m,B n,C y){
        
    }
}
```

(2)泛型类的构造器的写法：

```java
public TestGeneric() {
}
```

（3）不同泛型的引用类型不可以相互赋值 — 下面这样是错误的

```java
public void b(){
    ArrayList<String> list1 = null;
    ArrayList<Integer> list2 = null;
    list1 = list2;
}
```

（4）泛型如果不确定，那么就会被搽除，泛型对应的类型为Object类型

```java
    GenericTest gt1 = new GenericTest();
    gt1.a("adaf");
    gt1.a(19);
    gt1.a(2.44);
    gt1.b(new String[]{"dd","23"});
```
（5）泛型类中的静态方法不能使用类的泛型：

```java
public class TestGeneric<A,B,C> {
    A age;
    B name;
    C sex;

    public static int c(A a){
        return 10;
    }
```

（6）不能直接使用E[]的创建：

```java
    public void b(A m,B n,C g){
//        A[] i = new A[10]; 错误
        A[] q = (A[])new Object[10];
    }
```



##### 泛型方法

```java
package com.msb.Test04;

/**
 * @ClassName: TestGeneric
 * @Author: rain
 * @Date: 2022/10/18 - 10 - 18 - 9:16 下午
 * @Description: 1.什么是泛型方法？
 * 不是带泛型的方法就是泛型方法
 * 泛型方法有要求：这个方法的泛型的参数类型和当前的类的泛型无关
 * 换个角度：
 * 泛型方法对应的那个泛型参数类型 和 当前所在的这个类 是否是泛型类，泛型是啥 无关
 * 2. 泛型方法定义的时候。前面要加上<T>
 *      原因：如果不加的话，会把T当作一种数据类型，然而代码中没有T类型那么就会报错
 * 3. T的类型是在调用方法的时候确定的
 * 4. 泛型方法可否是静态方法？可以是静态方法
 * @Version: 1.0
 */


public class TestGeneric<E> {
    //不是泛型方法 （不能是静态方法）
    public void a(E e){
    }
    //泛型方法
    public <T> void b(T n){
    }
}

class Demo{
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        TestGeneric<String> tg = new TestGeneric<>();
        tg.a("dad");

        tg.b(222);
        tg.b("adad");
    }}
```

##### 泛型参数存在继承关系的情况

```java
package com.msb.Test04;

import java.util.ArrayList;
import java.util.List;

/**
 * @ClassName: Test
 * @Author: rain
 * @Date: 2022/10/19 - 10 - 19 - 9:24 上午
 * @Description:
 * @Version: 1.0
 */


public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        Object obj = new Object();
        String s = new String();
        obj = s; //多态


        Object[] objArray = new Object[10];
        String[] strArr = new String[10];
        objArray = strArr;


        List<Object> list1 = new ArrayList<Object>();
        List<String> list2 = new ArrayList<String>();
//        list1 = list2;
        //总结：A和B是子类父类的关系，但是G<A>和G<B>不存在继承关系的，是并列关系
    }
}
```

##### 通配符

【1】在没有通配符的时候，下面的a方法相当于重复定义

```java
public class Test {
    public void a(List<String> e){
        
    }    
    public void a(List<Integer> e){
        
    }    
    public void a(List<Double> e){
        
    }
}
```

【2】引入通配符：

```java
public class Demo {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        List<Object> list1 = new ArrayList<>();
        List<String> list2 = new ArrayList<>();
        List<Integer> list3 = new ArrayList<>();
        
        List<?> list = null;
        list = list1;
        list = list2;
        list = list3;
    }
}
```

发现：A和B是子类父类的关系，G<A>和G<B>不存在子类父类关系，是并列的关系，

加入通配符？之后，G<A>和G<B>就是子类父类关系

【3】使用通配符

```java
public class Demo {
    //这是一个main方法，是程序的入口：
    public void a(List<?> list){
        //内部遍历的时候，用object即可
        for(Object o : list){
            System.out.println(o);
        }
    }
}

class Test01{
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        Demo d1 = new Demo();
        d1.a(new ArrayList<Object>());
        d1.a(new ArrayList<String>());
        d1.a(new ArrayList<Double>());
    }
}
```

##### 使用通配符的细节

```java
package com.msb.test06;

import java.util.ArrayList;
import java.util.List;

/**
 * @ClassName: Demo
 * @Author: rain
 * @Date: 2022/10/19 - 10 - 19 - 9:42 上午
 * @Description:
 * @Version: 1.0
 */


public class Demo {
    //这是一个main方法，是程序的入口：
    public void a(List<?> list){
        //内部遍历的时候，用object即可
        for(Object o : list){
            System.out.println(o);
        }

        //2.数据的写入操作:
        //List.add("abc");  ---出错，不能随意的添加数据
        list.add(null);

        //3.数据的读写操作
        Object s = list.get(0);
    }
}

class Test01{
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        Demo d1 = new Demo();
        d1.a(new ArrayList<Object>());
        d1.a(new ArrayList<String>());
        d1.a(new ArrayList<Double>());
    }
}
```

##### 泛型受限

```java
package com.msb.test07;

import java.util.ArrayList;
import java.util.List;

/**
 * @ClassName: Test
 * @Author: rain
 * @Date: 2022/10/19 - 10 - 19 - 10:05 上午
 * @Description:
 * @Version: 1.0
 */


public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //a,b,c三个集合是并列的关系
        List<Object> a = new ArrayList<>();
        List<Person> b = new ArrayList<>();
        List<Student> c = new ArrayList<>();

        //开始使用泛型受限：泛型的上限
        /*
        List<? extends Person>:
        就相当于:
        List<? extends Person>是list<Person>的父类,是list<Peson的子类>的父类
        */
        List<? extends Person> list1 = null;//意味着能使用Person和它的子类，
        /*list1 = a;
        list1 = b;
        list1 = c;
         */
        /*
        开始使用泛型受限：泛型的下限
        List<? super Person>
        就相当于：
        List<? super Person>是list<Person>的父类，是list<Person的父类>的父类
         */
        List<? super Person > list2 = null;//能使用Person类和Person的父类
        /*list2 = a;
        list2 = b;
        list2 = c;
         */
    }
}
```

### LinkList实现类

```
LinkedList 是一个继承于AbstractSequentialList的双向链表。它也可以被当作堆栈、队列或双端队列进行操作。
LinkedList 实现 List 接口，能对它进行队列操作。
LinkedList 实现 Deque 接口，即能将LinkedList当作双端队列使用。
LinkedList 实现了Cloneable接口，即覆盖了函数clone()，能克隆。
LinkedList 实现java.io.Serializable接口，这意味着LinkedList支持序列化，能通过序列化去传输。
LinkedList 是非同步的。

为什么要继承自AbstractSequentialList ?

AbstractSequentialList 实现了get(int index)、set(int index, E element)、add(int index, E element) 和 remove(int index)这些骨干性函数。降低了List接口的复杂度。这些接口都是随机访问List的，LinkedList是双向链表；既然它继承于AbstractSequentialList，就相当于已经实现了“get(int index)这些接口”。

此外，我们若需要通过AbstractSequentialList自己实现一个列表，只需要扩展此类，并提供 listIterator() 和 size() 方法的实现即可。若要实现不可修改的列表，则需要实现列表迭代器的 hasNext、next、hasPrevious、previous 和 index 方法即可。
```

LinkedList底层的数据结构是基于双向循环链表的，且头结点中不存放数据,如下：

![image-20221019165149162](/Users/rain/Library/Application Support/typora-user-images/image-20221019165149162.png)



常用方法

```java
package com.msb.test02;

import java.util.Iterator;
import java.util.LinkedList;

/**
 * @ClassName: test01
 * @Author: rain
 * @Date: 2022/10/19 - 10 - 19 - 10:24 上午
 * @Description:
 * @Version: 1.0
 */


public class test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //LinkList常用方法
        /*
        增加：addFirst(E e) addLast(E e)
            offer(E e) offerFirst(E e)  offerLast(E e)
        删除： poll()
              pollFirst()  pollLast()
              removeFirst()  removeLast()
        修改：
        查看： element()
                getFirst() getLast()
                indexOf(Object o)  LastIndexOf(Object o)
                peek()
                peekFirst() peekLast()
         */

        LinkedList<String> list = new LinkedList<String>();
        list.add("ad");
        list.add("bb");
        list.add("vv");
        list.add("cc");
        list.add("tt");

        System.out.println(list);
        list.addFirst("re");
        list.addLast("dww");

        list.offer("oo"); //添加元素在尾端
        list.offerFirst("weq");
        list.offerLast("qeq");
        System.out.println(list);//LinkList可以添加重复元素
        System.out.println(list.poll()); //删除头上的元素并将元素输出
        System.out.println(list.pollFirst());
        System.out.println(list.pollLast());

        System.out.println(list.removeFirst());
        System.out.println(list);

        System.out.println("---------------");
        //集合的遍历
        //普通for循环
        for (int i = 0; i < list.size(); i++) {
            System.out.println(list.get(i));
        }
        System.out.println("---------------");
        //增强for：
        for(String s : list){
            System.out.println(s);
        }
        System.out.println("---------------");
        //迭代器：
        Iterator<String> it = list.iterator();
        while (it.hasNext()) {
            System.out.println(it.next());
        }
        //下面这种方式好，节省内存
        for(Iterator<String> it1 = list.iterator(); it1.hasNext();){
            System.out.println(it1.next());
        }
    }
}
```

#### 模拟实现LinkList源码



```java
package com.msb.test03;

/**
 * @ClassName: Node
 * @Author: rain
 * @Date: 2022/10/19 - 10 - 19 - 2:03 下午
 * @Description:
 * @Version: 1.0
 */


public class Node {  //节点类
    //三个属性
    //首节点
    private Node pre;
    //数据
    private Object obj;
    //尾节点
    private Node next;

    public Node() {
    }

    public Node(Node pre, Object obj, Node next) {
        this.pre = pre;
        this.obj = obj;
        this.next = next;
    }

    public Node getPre() {
        return pre;
    }

    public void setPre(Node pre) {
        this.pre = pre;
    }

    public Object getObj() {
        return obj;
    }

    public void setObj(Object obj) {
        this.obj = obj;
    }

    public Node getNext() {
        return next;
    }

    public void setNext(Node next) {
        this.next = next;
    }

    @Override
    public String toString() {
        return "Node{" +
                "preNode=" + pre +
                ", obj=" + obj +
                ", next=" + next +
                '}';
    }
}

```

```java
package com.msb.test03;

/**
 * @ClassName: MyLinlkist
 * @Author: rain
 * @Date: 2022/10/19 - 10 - 19 - 2:07 下午
 * @Description:
 * @Version: 1.0
 */


public class MyLinlkist {
    //链中有一个首节点
    Node first;
    //链中有一个尾节点
    Node last;
    //计算元素的个数
    int count = 0;

    public MyLinlkist() {
    }

    public void add(Object o) {
        if(first == null){
//            将添加的元素封装为一个Node对象
            Node n = new Node();
            n.setPre(null);
            n.setObj(o);
            n.setNext(null);
            //当前链中第一个节点为N
            first = n;
            //当前链中最后一个节点为N
            last = n;
        }else {
            Node n = new Node();
            n.setPre(last);
            n.setObj(o);
            n.setNext(null);

            //当前链中的最后一个节点的下一个元素指向n
            last.setNext(n);
            //将最后一个节点变为n
            last = n;
        }
        count++;
    }

    //得到集合中元素的数量
    public int getSize(){
        return count;
    }

    //通过下标获取元素
    public Object get(int index){
        //获取链表的头元素
        Node n = first;
        for (int i = 0; i < index; i++) {
            n = n.getNext();
        }

        return n.getObj();
    }
}

class Test{
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //创建一个MyLinklist对象
        MyLinlkist ml = new MyLinlkist();
        ml.add("aaa");
        ml.add("dda");
        ml.add("fa");
        ml.add("aad");
        System.out.println(ml.getSize());

        System.out.println(ml.get(3));
    }
}
```

#### LinkList源码解析

【1】JDK1.7和JDK1.8 的源码是一样的

【2】部分代码

```java
public class LinkedList<E>{  //E是一个泛型，具体的类型要在实例化的时候才会最终确定
    transient int size = 0;  //集合中元素的数量

    private static class Node<E> {
        E item; //当前元素
        Node<E> next; //指向下一个元素地址
        Node<E> prev; //上一个元素地址

        Node(Node<E> prev, E element, Node<E> next) {
            this.item = element;
            this.next = next;
            this.prev = prev;
        }

        transient Node<E> first; //链表的首节点
        transient Node<E> last;  //链表的尾节点

        public LinkedList() { //空构造器
        }
        //添加元素操作
        public boolean add(E e) {
            linkLast(e);
            return true;
        }
        void linkLast(E e) { //添加的元素e
            final Node<E> l = last; //将链表中的last节点给l,如果是第一个元素的话，l为null
            //将元素封装为一个Node的具体的对象
            final Node<E> newNode = new Node<>(l, e, null);
            //将链表的last节点指向新的创建的对象
            last = newNode;
            if (l == null) //如果添加的是di第一个节点
                first = newNode; //将链表的first节点指向为新节点
            else  //如果添加的不是第一个节点
                l.next = newNode; // 将l的下一个指向为新的节点
            size++;  //集合中元素数量加1操作
            modCount++;
        }
        //获取集合中元素的数量
        public int size() {
            return size;
        }
        //通过索引得到元素
        public E get(int index) {
            checkElementIndex(index);
            return node(index).item;
        }

        Node<E> node(int index) {
            // 如果index在链表的前半段，从前递增;

            if (index < (size >> 1)) {
                Node<E> x = first;
                for (int i = 0; i < index; i++)
                    x = x.next;
                return x;
            } else { // 如果index在链表的后半段，从后递减;
                Node<E> x = last;
                for (int i = size - 1; i > index; i--)
                    x = x.prev;
                return x;
            }
        }
    }
}
```

### 面试题：iterator(),Iterator,Iterable的关系

【1】对应的关系：

ArrayList实现了List接口，而List又继承了java.util.Collection接口，而Collection又继承了Iterable接口，而该接口只有一个方法，就是： public abstract Iterator iterator();一个返回迭代器的方法，因此得出结论：实现了iterator接口就可以实现使用迭代器。这里特别说明一下反过来能使用迭代器的未必就一定实现了该接口，例如数组（具体原因尚不明确，知道的小伙伴请留言）。还有提到一下Collection接口的作用是给有序集合的接口的公共方法的再一次抽象。因为Collection实现了Iterable接口，所以有序集合都可以使用迭代器。

```
  1，ArrayList实现接口List
  2，List继承接口Collection
  3，Collection继承接口Iterable
  4，接口Iterator中有抽象方法hasNext();--E next();
  5，接口iterator的返回值Iterable是一个接口
  
iterator()是Iterable接口中的一个方法，方法的返回值是Iterator。
Iterator中的方法：
1、hasNext() ：此方法用来判断迭代器对象指向的索引位置有没有元素
2、next() ：获取迭代器对象当前索引位置的元素并将索引下标移至下一个元素
3、remove() ：删除参数中指定元素
..
这些抽象方法均由实现类（ArrayList的内部类Itr）实现。
```

![image-20221019165048802](/Users/rain/Library/Application Support/typora-user-images/image-20221019165048802.png)

【2】hasNext.next()![image-20221019165102382](/Users/rain/Library/Application Support/typora-user-images/image-20221019165102382.png)

【3】增强for循环，底层也是通过迭代器实现的

```
1、因为集合没有索引，所以不能用索引来获取元素的
2、集合只能使用迭代器挨个遍历元素
3、调用方法时会先到子类中找对应的方法，没有的话才会执行默认方法
4、hasNext() 方法用来表示当前索引位置有没有元素
5、next() 方法用来获取当前索引位置的元素并将下标移至下一个元素
6、当需要对索引位置的元素进行操作，只能通过迭代器对象来调用方法，不然会抛出 ConcurrentModificationException 异常，也就是并发修改异常
```

![image-20221019165218323](/Users/rain/Library/Application Support/typora-user-images/image-20221019165218323.png)



##### LinkIterator迭代器

【1】加入字符串：

```java
public class TestString {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        ArrayList<String> array = new ArrayList<>();
        array.add("qq");
        array.add("qda");
        array.add("qqf");
        array.add("rfq");
        array.add("qfs");
        array.add("vbb");

        Iterator it = array.iterator();
        while (it.hasNext()) {
            if (it.next().equals("qqf")) {
                array.add("aa");
            }
        }
    }
}
```

【2】发生异常

![截屏2022-10-19 下午5.08.53](/Users/rain/Desktop/截屏2022-10-19 下午5.08.53.png)

原因：迭代器和list同时对集合进行操作：

解决办法：事先让一个人单独使用迭代器 ： ListIterator

迭代和添加操作都是靠ListIterator

```java
package com.msb.test06;

import java.util.ArrayList;
import java.util.ListIterator;

/**
 * @ClassName: Test02
 * @Author: rain
 * @Date: 2022/10/19 - 10 - 19 - 5:11 下午
 * @Description:
 * @Version: 1.0
 */


public class Test02 {
    public static void main(String[] args) {
        ArrayList<String> arr = new ArrayList<>();
        arr.add("qq");
        arr.add("qda");
        arr.add("qqf");
        arr.add("rfq");
        arr.add("qfs");
        arr.add("vbb");
        System.out.println(arr);
        ListIterator<String> it = arr.listIterator();
        while (it.hasNext()) {
            if ("qq".equals(it.next())) {
                it.add("aa");
            }
        }
        System.out.println(it.hasNext());
        System.out.println(it.hasPrevious());

        //逆向遍历
        while (it.hasPrevious()) {
            System.out.println(it.previous());
        }
        System.out.println(it.hasNext());
        System.out.println(it.hasPrevious());
    }
}
```





### Set接口

#### HashSet实现类的使用

【1】放入Integer类型：

```java

public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //创建一个HashSet集合：
        HashSet<Integer> hs = new HashSet<Integer>();
        hs.add(19);
        hs.add(3);
        hs.add(4);
        hs.add(5);
        hs.add(6);
        hs.add(6);
        hs.add(99);
        System.out.println(hs);
        System.out.println(hs.size()); //唯一，无序
    }
}
```

【2】放入String类型数据：

```java
package com.msb.test05;

import java.util.HashSet;

/**
 * @ClassName: TestString
 * @Author: rain
 * @Date: 2022/10/19 - 10 - 19 - 4:20 下午
 * @Description:
 * @Version: 1.0
 */


public class TestString {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        HashSet<String> hs = new HashSet<String>();
        hs.add("dad");
        hs.add("ad");
        hs.add("ded");
        hs.add("gg");
        hs.add("44");
        hs.add("44");
        System.out.println(hs);
        System.out.println(hs.size());
    }
}
```

【3】放入自定义引用数据类型

```java
package com.msb.test05;

import java.util.HashSet;

/**
 * @ClassName: TestStudent
 * @Author: rain
 * @Date: 2022/10/19 - 10 - 19 - 4:28 下午
 * @Description:
 * @Version: 1.0
 */


public class TestStudent {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        HashSet<Student> hs = new HashSet<Student>();
        hs.add(new Student("lili",19));
        hs.add(new Student("lili",19));
        hs.add(new Student("张三",19));
        hs.add(new Student("lii",19));
        hs.add(new Student("对方i",12));
        hs.add(new Student("王武",99));
        System.out.println(hs.size());
        System.out.println(hs);
    }
}
```

上面自定义的类型不满足唯一，无序的特点

【4】HashSet原理图：

![image-20221019165017428](/Users/rain/Library/Application Support/typora-user-images/image-20221019165017428.png)

【5】疑问：

1.数组的长度是多少

2.数组的类型是什么？

3.hashCode,equals方法的真的调用了吗？验证

4.底层表达式是什么？

5.用一个位置的数据向前放，还是向后放

6.放入数组中的数据，是直接放的吗？是否封装为对象了？

#### LinkedHashSet的使用

LinkedHashSet就是在HashSet的基础上，多了一个总链表，这个总链表将放入的元素串在一起，方便有序的遍历：

```java
public class Test03 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        LinkedHashSet<Integer> lhs = new LinkedHashSet<Integer>();
        lhs.add(13);
        lhs.add(15);
        lhs.add(4);
        lhs.add(7);
        lhs.add(13);
        lhs.add(9);
        lhs.add(13);
        System.out.println(lhs);
    }
}
```



### 比较器的使用

【1】以int类型为案例：

比较的思路：将比较的数据做差，然后返回一个int类型的数据，将这个int类型的数值，按照 =0 >0 <0

```java
        int a = 10;
        int b = 20;
        System.out.println(a-b);   =0 >0 <0
```

【2】以String类型为案例：

String类中实现了Comparable接口，这个接口中有一个抽象方法compareTo,String类中重写这个方法

```java
String a = "A";
String b = "B";
System.out.println(a.compareTo(b));
```

【3】比较double类型数据：

```java
double a = 100;
double b = 10.4;
System.out.println(((Double)a).compareTo((Double)b));
```

【4】比较自定义类型：

（1）内部比较器

```java
package com.msb.test07;

/**
 * @ClassName: Student
 * @Author: rain
 * @Date: 2022/10/19 - 10 - 19 - 7:55 下午
 * @Description:
 * @Version: 1.0
 */


public class Student {
    private String name;
    private int age;
    private double height;

    public Student(String name, int age, double height) {
        this.name = name;
        this.age = age;
        this.height = height;
    }

    public Student() {
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public double getHeight() {
        return height;
    }

    public void setHeight(double height) {
        this.height = height;
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", height=" + height +
                '}';
    }

	  @override
    public int compareTo(Student o){
        //按照年龄比较
        /*return this.age - o.getAge(); */
        //按照身高比较
//        return ((Double)this.getHeight()).compareTo((Double)o.getHeight());
        //按照名字进行比较
        return this.getName().compareTo(o.getName());

    }
}
```

测试类：

```java
package com.msb.test07;

/**
 * @ClassName: Test02
 * @Author: rain
 * @Date: 2022/10/19 - 10 - 19 - 7:56 下午
 * @Description:
 * @Version: 1.0
 */


public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //比较两个学生
        Student s1 = new Student("张三",19,22.3);
        Student s2 = new Student("李四",33,532.3);
        System.out.println(s1.compareTo(s2));;

    }
}
```

（2）外部比较器：

```java
package com.msb.test08;

import java.util.Comparator;

/**
 * @ClassName: Student
 * @Author: rain
 * @Date: 2022/10/19 - 10 - 19 - 8:05 下午
 * @Description:
 * @Version: 1.0
 */


public class Student {
    private String name;
    private int age;
    private double height;

    public Student(String name, int age, double height) {
        this.name = name;
        this.age = age;
        this.height = height;
    }

    public Student() {
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public double getHeight() {
        return height;
    }

    public void setHeight(double height) {
        this.height = height;
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", height=" + height +
                '}';
    }
}

class Bijiaoqi implements Comparator<Student> {
    //比较年龄
    @Override
    public int compare(Student o1, Student o2) {
        return o1.getAge() - o2.getAge();
    }
}

class Bijiaoqi2 implements Comparator<Student> {
    //比较身高
    @Override
    public int compare(Student o1, Student o2) {
        return ((Double)o1.getHeight()).compareTo(((Double)o2.getHeight()));
    }
}

class Bijiaoqi3 implements Comparator<Student>{
    @Override
    public int compare(Student o1, Student o2) {
        //在年龄相同的话比较身高，在身高相同的话比较名字
        if ((o1.getAge()-o2.getAge())== 0) {
            return ((Double)o1.getHeight()).compareTo(((Double)o2.getHeight()));
        }else {
            return o1.getAge()-o2.getAge();
        }
    }
}

```

```java
package com.msb.test08;

import java.util.Comparator;

/**
 * @ClassName: Test01
 * @Author: rain
 * @Date: 2022/10/19 - 10 - 19 - 8:11 下午
 * @Description:
 * @Version: 1.0
 */


public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //比较两个学生
        Student s1 = new Student("张三",50,22.3);
        Student s2 = new Student("李四",33,532.3);
        Comparator com = new Bijiaoqi3();
        System.out.println(com.compare(s1,s2));
    }
}
```

【5】外部比较器和内部比较器那个好？

答案：外部比较好，使用多态，扩展性高

### TreeSet实现类

TreeSet是Set的子类，TreeSet和Set都是java.util 下的，使用时需要导入java.util包。Set是collection的子类，collection不能实例化，但是它的子类可以，其关系图为：

```
一、TreeSet
1、TreeSet集合底层实际上是一个TreeMap；TreeMap集合底层是一个二叉树
2、放到TreeSet集合中的元素，等同于放到TreeMap集合key部分了。
3、TreeSet集合存储元素特点：无序不可重复的，但是存储的元素可以自动按照大小顺序排序
 称为：可排序集合。
无序指的是存进去的顺序和取出来的顺序不同，并且没有下标

二、比较器
1、TreeSet中有两种排序，一个是自然排序，一个是重写compareTo()方法自定义排序。
自然排序可以参考Integer，String等类中的实现。其顺序也是我们常见的“1,2,3,4”，“a,b,c,d”。

2、重写compareTo()方法自定义排序

（1）对自定义的类型来说，TreeSet无法排序， 因为没有指定 自定义类型对象之间的比较规则

 程序运行的时候出现异常：
java.lang.ClassCastException: class com.collection.XX cannot be cast to class
java.lang.Comparable 出现这个异常的原因是： 自定义类型对象没有实现java.lang.Comparable接口

3、TreeSet集合中元素可排序包括两种方式：

（1）放在集合中的元素实现java.lang.Comparable接口

（2）在构造TreeSet或者TreeMap集合的时候给传一个比较器对象Comparator

TreeSet提供了四种构造器

TreeSet()
TreeSet(Collection< ? extends E> c)
TreeSet(Comparator< ? super E> comparator)
TreeSet(SortedSet< E > s)


4、Comparable 和 Comparator选择

当比较规则不会发生改变时（比较规则只有1个的时候），可实现Comparable接口
如果比较规则有多个，并且需要多个比较规则之间频繁切换，可使用Comparator接口
```

TreeSet底层是二叉树，可以对对象元素进行排序，但是自定义类需要实现comparable接口，重写comparaTo() 方法。TreeSet 可以保存对象元素的唯一性（并不是一定保证唯一性，需要根据重写的compaaTo方法来确定）

![截屏2022-10-19 下午9.27.43](/Users/rain/Desktop/截屏2022-10-19 下午9.27.43.png)

![截屏2022-10-19 下午9.27.57](/Users/rain/Desktop/截屏2022-10-19 下午9.27.57.png)



【1】以Integer类型为例：（底层运用的是内部比较器）

```java
public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        TreeSet<Integer> ts = new TreeSet<Integer>();
        ts.add(38);
        ts.add(18);
        ts.add(58);
        ts.add(43);
        ts.add(38);
        System.out.println(ts);
        System.out.println(ts.size());
    }
}
```

特点：唯一，无序（没有按照输入顺序进行输出），有序（按照升序进行遍历）

【2】原理：底层：二叉树（数据结构中的一个结构）



【3】以Stirng类型数据比较

```java
public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        TreeSet<String> ts = new TreeSet<String>();
        ts.add("elili");
        ts.add("elili");
        ts.add("qlili");
        ts.add("ylili");
        ts.add("rlili");
        ts.add("elili");
        System.out.println(ts);
        System.out.println(ts.size());
    }
}
```

【4】自定义数据类型比较

(1)利用内部比较器

```java
package com.msb.test09;

/**
 * @ClassName: Student
 * @Author: rain
 * @Date: 2022/10/19 - 10 - 19 - 8:52 下午
 * @Description:
 * @Version: 1.0
 */

public class Student implements Comparable<Student> {
    private String name;
    private int age;

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

    @Override
    public int compareTo(Student o) {
        return this.getAge()-o.getAge();
    }
}
```

```java
public class Test03 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        TreeSet<Student> s1 = new TreeSet<>();
        s1.add(new Student("张三",18));
        s1.add(new Student("李四",34));
        s1.add(new Student("王武",58));
        s1.add(new Student("张三",19));
        System.out.println(s1);
    }
}
```

（2）利用外部比较器

```java
package com.msb.test09;

import java.util.Comparator;

/**
 * @ClassName: Student
 * @Author: rain
 * @Date: 2022/10/19 - 10 - 19 - 8:52 下午
 * @Description:
 * @Version: 1.0
 */

public class Student{
    private String name;
    private int age;

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}

class Bjq implements Comparator<Student>{

    @Override
    public int compare(Student o1, Student o2) {
        return o1.getName().compareTo(o2.getName());
    }
}
```

```java
public class Test03 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //创建一个TreeSet：
        //利用外部比较器，必须自己制定：
        Comparator<Student> cp = new Bjq();
        TreeSet<Student> s1 = new TreeSet<>(cp); //一旦指定外部比较器，那么就会按照外部比较器来比较
        s1.add(new Student("张三",18));
        s1.add(new Student("李四",34));
        s1.add(new Student("王武",58));
        s1.add(new Student("张三",19));
        System.out.println(s1);
    }
}
```

在实际开发中，使用外部比较器更好，

换一种写法：

```java
package com.msb.test09;

import java.util.Comparator;
import java.util.TreeSet;

/**
 * @ClassName: Test03
 * @Author: rain
 * @Date: 2022/10/19 - 10 - 19 - 8:52 下午
 * @Description:
 * @Version: 1.0
 */


public class Test03 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //创建一个TreeSet：
        //利用外部比较器，必须自己制定：
        /*Comparator<Student> cp = new Comparator<Student>() {
            @Override
            public int compare(Student o1, Student o2) {
                return o1.getName().compareTo(o2.getName());
            }
        };*/


        TreeSet<Student> s1 = new TreeSet<>(new Comparator<Student>() {
            @Override
            public int compare(Student o1, Student o2) {
                return o1.getName().compareTo(o2.getName());
            }
        }); //一旦指定外部比较器，那么就会按照外部比较器来比较
        s1.add(new Student("张三",18));
        s1.add(new Student("李四",34));
        s1.add(new Student("王武",58));
        s1.add(new Student("张三",19));
        System.out.println(s1);
    }
}
```

【5】TreeSet底层的二叉树的遍历是按照升序的结果出现的，这个升序是靠中序遍历得到的：



      二叉树
    1、Teet/TreeMap是自平衡二叉树（AVL），遵循左小右大原则存放
      存放是要依靠左小右大原则，存放时，要进行比较
    2、遍历二叉树三种方式
    
    （1）前序遍历:根左右
    （2）中序遍历:左根右
    （3）后序遍历:左右根
    
    注：
    前中后说的是“根” 的位置
    根在前面是前序；根在中间是中序；根在后面是后序
    
    3、 TreeSet集合/TreeMap集合采用的是：中序遍历方式（左根右）
    Iterator迭代器采用的是中序遍历方式
    存放的过程就是排序的过程，取出来就是自动按照大小顺序排列的
    如下数据：
    
    5        2        8        1        4        7        9        3
    在二叉树中表示如下：

![img](https://img-blog.csdnimg.cn/83827f2578b64f7f8c694bcacd9f46b0.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBATWluZ2dlUWluZ2NodW4=,size_20,color_FFFFFF,t_70,g_se,x_16)



### Map接口

#### 常用方法

```java
package com.msb.test010;

import java.util.Collection;
import java.util.HashMap;
import java.util.Map;
import java.util.Set;

/**
 * @ClassName: Test01
 * @Author: rain
 * @Date: 2022/10/20 - 10 - 20 - 16:48
 * @Description:
 * @Version: 1.0
 */


public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        /*增加：put(K key, V value)
        删除：clear()
        修改：
        查看：entrySet() get(Object key) keySet() size() values()
        判断：containsKey() containsValue(Object value)
            equals(Object o) isEmpty()
         */
      //创建一个Map集合，唯一，无序
        Map<String,Integer> map = new HashMap<>();
        map.put("lili", 24);
        map.put("zahngsan", 24);
        map.put("wemg", 24);
        map.put("lcui", 24);
        map.put("lili", 19);

//        map.clear();
        System.out.println(map);
        System.out.println(map.size());
//        System.out.println(map.entrySet());
        System.out.println(map.get("lili"));//输入key，得到values
        System.out.println(map.keySet()); //得到所以key
        System.out.println(map.values()); //得到所有的values
        System.out.println(map.containsKey("lili"));
        System.out.println(map.containsValue(24));
        System.out.println(map.equals("lili"));


        //遍历
        System.out.println("----------------");
        //用values()对集合中的value进行遍历查看
        Collection<Integer> values = map.values();
        for (Integer s : values) {
            System.out.println(s);
        }
        System.out.println("----------------");
        //get(Object key) keySet()
        Set<String> set2 = map.keySet();
        for (String s : set2) {
            System.out.println(map.get(s));
        }
        System.out.println("----------------");
        //entrySet
        Set<Map.Entry<String,Integer>> en = map.entrySet();
        for (Map.Entry<String, Integer> e : en) {
            System.out.println(e.getKey() + "--" + e.getValue());
        }
    }
}
```

#### TreeMap

##### TreeMap底层原理

【1】简单原理

![image-20221022194643749](/Users/rain/Library/Application Support/typora-user-images/image-20221022194643749.png)

【2】源码分析

```java
package com.msb.test01;

import java.util.Comparator;
import java.util.Map;

public class Test03 {
}

public class TreeMap<K,V>{
    //重要属性
    //外部比较器
    private final Comparator<? super K> comparator;
    //树的根节点：
    private transient Entry<K,V> root = null;
    //集合中元素的数量：
    private transient int size = 0;
    //空构造器：
    public TreeMap() {
        comparator = null; //如果使用空构造器，那么底层就不使用外部比较器
    }
    //有参构造器
    public TreeMap(Comparator< ? super K > comparator){
        this.comparator = comparator;  //如果使用有参构造器，那么就相当于制定了外部比较器
    }

public V put(K key,V value){  //K,V的值在创建对象的时候就已经确定了
    //如果放入的是第一对元素，那么t的值为null
    Entry<K,V> t = root; //在放入第二个节点的时候，root已经是根节点了
    //如果放入的是第一个元素的话，走入这个if中
    if(t == null){
        //自己根自己比
        compare(key,key); //type (and possibly null) check
        //根节点确定为root
        root = new Entry<>(key, value,null);
        size = 1;
        //size的值为1
        modCount++;
        return null;
    }
    int cmp;
    Entry<K,V> parent;
    //split comparator and comparable paths
    //将外部比较器赋给cpr
    Comparator< ? super K> cpr = comparator;
    //cpr不等于null,意味着你刚才创建对象的时候调用了有参构造器，指定了外部比较器
    if (cpr != null){
        do{
            parent = t;
            cmp = cpr.compare(key,t.key); //将元素的key值做比较
            //cmp返回的值就是int类型的数据
            //要是这个值 <0 =0 >0
            if(cmp <0)
                t = t.left;
            else if (cmp >0)
                t=t.right;
            else //cmp==0
            //如果key的值一样，那么新的value赋给老得value
                return t.setValue(value);
        }
        //cpr等于null,意味着你刚才创建对象的时候调用了空构造器，没有指定外部比较器，使用内部比较器
    }else{
        if(key==null)
            throw new NullPointerException();
        Comparator< ? super K> k = Comparable<? super K> key;
        do{
            parent = t;
            cmp = k.compareTo(t.key); //将元素的值做比较
            if(cmp <0)
                t=t.left;
            else if (cmp > 0)
                t=t.right;
            else
                return t.setValue(value);
        }while (t != null);
    }
    Entry<K,V> e = new Entry<>(key,value,parent);
    if(cmp<0)
        parent.left = e;
    else
        parent.right = e;
    fixAfterInsertion(e);
    size++;
    modCount;
    return null;
}
```


##### 常用方法

【1】使用Treemap

```java
public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        Map<String, Integer> hs = new TreeMap<>();
        hs.put("alili",36);
        hs.put("blili",20);
        hs.put("lcili",19);
        hs.put("rlili",18);
        hs.put("rlili",34);
        System.out.println(hs.size());
        System.out.println(hs);
    }
}
```

【2】key的类型是一个自定义引用数据类型

【1】使用内部比较器

```java
package com.msb.test010;

/**
 * @ClassName: Student
 * @Author: rain
 * @Date: 2022/10/21 - 10 - 21 - 14:06
 * @Description:
 * @Version: 1.0
 */


public class Student implements Comparable<Student>{
    private String name;
    private int age;
    private double height;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public double getHeight() {
        return height;
    }

    public void setHeight(double height) {
        this.height = height;
    }

    public Student() {
    }

    public Student(String name, int age, double height) {
        this.name = name;
        this.age = age;
        this.height = height;
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", height=" + height +
                '}';
    }

    @Override
    public int compareTo(Student o) {
        return this.age - o.age;
    }
}
```

测试类：

```java
package com.msb.test010;

import java.util.Map;
import java.util.TreeMap;

/**
 * @ClassName: Test02
 * @Author: rain
 * @Date: 2022/10/21 - 10 - 21 - 14:02
 * @Description:
 * @Version: 1.0
 */


public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        Map<Student, Integer> hs = new TreeMap<>();

        hs.put(new Student("rlili",120,538.4),1001);
        hs.put(new Student("alili",23,138.4),1001);
        hs.put(new Student("blili",22,258.4),1001);
        hs.put(new Student("vlili",20,1358.4),1001);
        hs.put(new Student("clili",19,18.4),1001);
        hs.put(new Student("clili",18,248.1),1001);
        System.out.println(hs.toString());
        System.out.println(hs.size());
    }
}
```

【2】使用外部比较器

```java
package com.msb.test010;

import java.util.Comparator;

/**
 * @ClassName: Student
 * @Author: rain
 * @Date: 2022/10/21 - 10 - 21 - 14:06
 * @Description:
 * @Version: 1.0
 */


public class Student {
    private String name;
    private int age;
    private double height;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public double getHeight() {
        return height;
    }

    public void setHeight(double height) {
        this.height = height;
    }

    public Student() {
    }

    public Student(String name, int age, double height) {
        this.name = name;
        this.age = age;
        this.height = height;
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", height=" + height +
                '}';
    }
}

class Bjq implements Comparator<Student>{

    @Override
    public int compare(Student o1, Student o2) {
//        return o1.getAge()-o2.getAge();
//        return o1.getName().compareTo(o2.getName());
        return ((Double)o1.getHeight()).compareTo((Double)(o2.getHeight()));
    }
}
```

```java
public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        Comparator<Student> com = new Bjq();
        Map<Student, Integer> hs = new TreeMap<>(com);

        hs.put(new Student("rlili",120,538.4),1001);
        hs.put(new Student("alili",23,138.4),1001);
        hs.put(new Student("blili",22,258.4),1001);
        hs.put(new Student("vlili",20,1358.4),1001);
        hs.put(new Student("clili",19,18.4),1001);
        hs.put(new Student("clili",18,248.1),1001);
        System.out.println(hs.toString());
        System.out.println(hs.size());
    }
}
```

#### HashMap

什么是链表散列呢？

　　通过数组和链表结合在一起使用，就叫做链表散列。这其实就是hashmap存储的原理图

![img](https://img2020.cnblogs.com/blog/2506022/202109/2506022-20210924141513237-1293331758.png)。

【1】简单原理图

![image-20221022194743659](/Users/rain/Library/Application Support/typora-user-images/image-20221022194743659.png)

```
 HashMap的数据结构就是用的链表散列，大概是怎么存储的呢？分两步

　　1、HashMap内部有一个entry的内部类，其中有四个属性，我们要存储一个值，则需要一个key和一个value，存到map中就会先将key和value保存在这个Entry类创建的对象中。
　　2、构造好了entry对象，然后将该对象放入数组中，如何存放就是这hashMap的精华所在了。
大概的一个存放过程是：通过entry对象中的hash值来确定将该对象存放在数组中的哪个位置上，如果在这个位置上还有其他元素，则通过链表来存储这个元素。
```

![img](https://img2020.cnblogs.com/blog/2506022/202109/2506022-20210924141735806-1475465640.png)

```
1.HashMap存放元素的大概过程？
　　通过key、value封装成一个entry对象，然后通过key的值来计算该entry的hash值，通过entry的hash值和数组的长度length来计算出entry放在数组中的哪个位置上面，每次存放都是将entry放在第一个位置。在这个过程中，就是通过hash

2.loadFactor加载因子
 　　loadFactor加载因子是控制数组存放数据的疏密程度，loadFactor越趋近于1，那么数组中存放的数据(entry)也就越多，也就越密，也就是会让链表的长度增加，loadFactor越小，也就是趋近于0，那么数组中存放的数据也就越稀，也就是可能数组中每个位置上就放一个元素。那有人说，就把loadFactor变为1最好吗，存的数据很多，但是这样会有一个问题，就是我们在通过key拿到我们的value时，是先通过key的hashcode值，找到对应数组中的位置，如果该位置中有很多元素，则需要通过equals来依次比较链表中的元素，拿到我们的value值，这样花费的性能就很高，如果能让数组上的每个位置尽量只有一个元素最好，我们就能直接得到value值了，所以有人又会说，那把loadFactor变得很小不就好了，但是如果变得太小，在数组中的位置就会太稀，也就是分散的太开，浪费很多空间，这样也不好，所以在hashMap中loadFactor的初始值就是0.75，一般情况下不需要更改它。

3.Size的意思？
　　size就是在该HashMap的实例中实际存储的元素的个数

4.threshold的作用？
　　threshold = capacity * loadFactor，当Size>=threshold的时候，那么就要考虑对数组的扩增了，也就是说，这个的意思就是衡量数组是否需要扩增的一个标准。注意这里说的是考虑，因为实际上要扩增数组，除了这个size>=threshold条件外，还需要另外一个条件，这个就等在源码中看吧。
　　
5.什么是桶？
　　根据前面画的HashMap存储的数据结构图，你这样想，数组中每一个位置上都放有一个桶，每个桶里就是装一个链表，链表中可以有很多个元素(entry)，这就是桶的意思。也就相当于把元素都放在桶中。

6.capacity
　　这个就代表的数组的容量，也就是数组的长度，同时也是HashMap中桶的个数。默认值是16.
　　
7.HashMap的继承结构和实现的接口
	继承结构很简单：上面就继承了一个abstractMap，也就是用来减轻实现Map接口的编写负担
	实现的接口：
		Map<K,V>：在AbstractMap抽象类中已经实现过的接口，这里又实现，实际上是多余的。但每个集合都有这样的错误，也没过大影响
　　Cloneable：能够使用Clone()方法
   Serializable：能够使之序列化
```

【2】源码分析

https://www.cnblogs.com/Chang-LeHung/p/16472308.html



#### HashSet底层原理

```
HashSet 基于 HashMap 来实现的，是一个不允许有重复元素的集合。

HashSet 允许有 null 值。

HashSet 是无序的，即不会记录插入的顺序。

HashSet 不是线程安全的， 如果多个线程尝试同时修改 HashSet，则最终结果是不确定的。 您必须在多线程访问时显式同步对 HashSet 的并发访问。

HashSet 实现了 Set 接口。
```

底层原理就是HashMap

```java
public class HashSet<E>
    extends AbstractSet<E>
    implements Set<E>, Cloneable, java.io.Serializable
{
    @java.io.Serial
    static final long serialVersionUID = -5024744406713321676L;

    private transient HashMap<E,Object> map;

    // Dummy value to associate with an Object in the backing Map
    private static final Object PRESENT = new Object();

    /**
     * Constructs a new, empty set; the backing {@code HashMap} instance has
     * default initial capacity (16) and load factor (0.75).
     */
    public HashSet() {
        map = new HashMap<>();
    }
```

#### TreeSet底层源码

Treeset底层是TreeMap，在调用空构造器的时候，底层创建了一个TreeMap。

### Collections工具类

常用方法

```java
package com.msb.test11;

import java.util.ArrayList;
import java.util.Collections;

/**
 * @ClassName: Test01
 * @Author: rain
 * @Date: 2022/10/24 - 10 - 24 - 14:26
 * @Description:
 * @Version: 1.0
 */


public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //Collections不支持创建对象，因为构造器私有化了
//        Collections col = new Collections();
        //里面的属性和方法都是被static修饰的，我们可以直接使用类名. 去调用
        //常用方法：
        //addAll;
        ArrayList<Integer> array = new ArrayList<>();
        array.add(23);
        array.add(13);
        array.add(3);
        array.add(4);
        array.add(99);
        Collections.addAll(array,33,53,43,45);
        Collections.addAll(array,new Integer[]{12,42,24,67});
        System.out.println(array);
        //binarySearch 必须在有序的集合中查找 --  排序
        Collections.sort(array);
        System.out.println(array);
        //binarySearch
        System.out.println(Collections.binarySearch(array,42));

        //copy 替换方法
        ArrayList<Integer> list = new ArrayList<Integer>();
        Collections.addAll(list,46,42);
        Collections.copy(array,list);
        System.out.println(array);
        System.out.println(list);

        //fill 填充
        Collections.fill(list,343);
        System.out.println(list);

    }

}
```

## 第13章 多线程

### 程序、进程、线程

【1】程序、进程、线程

- 程序（program）：是为了完成特定任务，用某种语言编写的一组指令的集合，是一段静态的代码。（程序是静态的）
- 进程（process）：是程序的一次执行过程，正在运行的一个程序，进程作为资源分配的单位，在内存中会为每个进程分配不同的内存区域。
- 线程（thread）:进程可进一步细化为线程，是一个程序内部的一条执行路径。若一个线程同一时间并行执行多个线程，就是支持多线程的

【2】单核CPU与多核CPU的任务执行：



【3】并行和并发：

并行：多个CPU同时执行多个任务

并发：一个CPU“同时”执行多个任务（采用时间片切换）

### 创建线程的三种方式

【1】在学习多线程一章之前，以前的代码是单线程的吗？不是，以前也是有三个线程同时执行的



【2】创建线程	—如何创建？

#### 第一种：继承Thread类

线程类：

```java
public class TestThread extends Thread {
    /*
    一会线程对象就要争抢CPU资源，这个线程要执行的任务到底是啥？这个任务你要放在方法中
    但是这个方法不能是随便写的一个方法，必须是重写Thread类中的run方法
    然后线程的任务/逻辑写在run放法中
     */
    @Override
    public void run() {
        for (int i = 0; i < 99;i++) {
            System.out.println(i);
        }
    }
}
```

测试类：

```java
public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        for (int i = 0; i < 10; i++) {
            System.out.println("main1: ------ "+i);
        }
        //制造其他线程，争抢资源
        //具体的线程对象：子线程
        TestThread th1 = new TestThread();
        //th1.run();  //调用run方法，输出对象, -- 这个run方法不能直接调用，直接调用就会被当作普通方法
        //想要th1直接启动，必须调用 start方法
        th1.start(); //start()是Thread类的方法
        //主线程也要输出十个数：
        for (int i = 0; i < 10; i++) {
            System.out.println("main2: ------ "+i);
        }
    }
}
```

##### 读取线程名字

【1】通过Thread类读取

```java
public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //获取main主线程的名字：
        //Thread.currentThread() 获取当前正在执行的线程
        Thread.currentThread().setName("主线程");
        for (int i = 0; i < 10; i++) {
            System.out.println(Thread.currentThread().getName()+"1----"+i);
        }
        //制造其他线程，争抢资源
        //具体的线程对象：子线程
        TestThread th1 = new TestThread();
        th1.setName("子线程");
        //th1.run();  //调用run方法，输出对象, -- 这个run方法不能直接调用，直接调用就会被当作普通方法
        //想要th1直接启动，必须调用 start方法
        th1.start(); //start()是Thread类的方法
        //主线程也要输出十个数：
        for (int i = 0; i < 10; i++) {
            System.out.println(Thread.currentThread().getName()+"2----"+i);
        }
    }
}
```

【2】通过构造器设置名字

```java
package com.msb.test01;

/**
 * @ClassName: Test
 * @Author: rain
 * @Date: 2022/10/24 - 10 - 24 - 15:28
 * @Description:
 * @Version: 1.0
 */


public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //获取main主线程的名字：
        //Thread.currentThread() 获取当前正在执行的线程
        Thread.currentThread().setName("主线程");
        for (int i = 0; i < 10; i++) {
            System.out.println(Thread.currentThread().getName()+"1----"+i);
        }
        //制造其他线程，争抢资源
        //具体的线程对象：子线程
        TestThread th1 = new TestThread("子线程");
        //th1.run();  //调用run方法，输出对象, -- 这个run方法不能直接调用，直接调用就会被当作普通方法
        //想要th1直接启动，必须调用 start方法
        th1.start(); //start()是Thread类的方法
        //主线程也要输出十个数：
        for (int i = 0; i < 10; i++) {
            System.out.println(Thread.currentThread().getName()+"2----"+i);
        }
    }
}

线程类：
public class TestThread extends Thread {
    public TestThread(String name){
        super(name); //调用父类的方法
    }

    /*
    一会线程对象就要争抢CPU资源，这个线程要执行的任务到底是啥？这个任务你要放在方法中
    但是这个方法不能是随便写的一个方法，必须是重写Thread类中的run方法
    然后线程的任务/逻辑写在run放法中
     */
    @Override
    public void run() {
        for (int i = 0; i < 50;i++) {
            System.out.println(this.getName()+i);
        }
    }
}
```

##### 买火车票

```java
public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //多个窗口抢票：三个窗口三个线程对象：
        BuyTicketThread th1 = new BuyTicketThread("窗口1");
        th1.start();
        BuyTicketThread th2 = new BuyTicketThread("窗口2");
        th2.start();
        BuyTicketThread th3 = new BuyTicketThread("窗口3");
        th3.start();
    }
}
```

```java
public class BuyTicketThread extends Thread{
    public BuyTicketThread(String name){
        super(name);
    }
    //一共10张票
    static int ticketNum = 10; //多个对象共享这十张票
    //每个窗口都是一个线程对象，每个对象执行的代码放入run方法中
    @Override
    public void run() {
        //每个窗口后面有100个人在抢票：
        for (int i = 0; i <=100;i++ ) {
            if (ticketNum >0) {
                System.out.println("我"+this.getName()+"买到了从北京到哈尔滨的票" + ticketNum-- + "张车票");
            }
        }
    }
}
```

#### 第二种：实现Runnable接口

##### 线程实现

```java
package com.msb.test03;

import com.msb.test01.TestThread;

/**
 * @ClassName: Test
 * @Author: rain
 * @Date: 2022/10/24 - 10 - 24 - 16:11
 * @Description:
 * @Version: 1.0
 */


public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //创建子线程对象：
        TestThread tt = new TestThread();
        Thread t = new Thread(tt,"子线程");
        t.start();

        //主线程方法
        for (int i = 0; i < 60;i++) {
            System.out.println(Thread.currentThread().getName()+"--"+ i);
        }
    }
}
```

```java
package com.msb.test03;

/**
 * @ClassName: TestThread
 * @Author: rain
 * @Date: 2022/10/24 - 10 - 24 - 16:10
 * @Description: TestThread类实现了Runnable接口，才会变成一个线程类
 * @Version: 1.0
 */


public class TestThread implements Runnable{
    @Override
    public void run() {
        //输出 1- 10数字
        for (int i = 0; i < 10;i++) {
            System.out.println(Thread.currentThread()+"------"+i);
        }
    }
}
```

##### 买火车票

【1】代码

```java
package com.msb.test04;

/**
 * @ClassName: BuyTicketThread
 * @Author: rain
 * @Date: 2022/10/24 - 10 - 24 - 16:21
 * @Description:
 * @Version: 1.0
 */


public class BuyTicketThread implements Runnable{
   int tickNum = 20;

    @Override
    public void run() {
        for (int i = 0; i < 99; i++) {
            if (tickNum >0 ) {
                System.out.println("我在"+Thread.currentThread().getName() + "买到了第"+tickNum--+"张票");
            }
        }
    }
}
```

```java
package com.msb.test04;

/**
 * @ClassName: Test
 * @Author: rain
 * @Date: 2022/10/24 - 10 - 24 - 16:23
 * @Description: 用Runnable实现买火车票
 * @Version: 1.0
 */


public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        BuyTicketThread by1 = new BuyTicketThread();
        Thread th1 = new Thread(by1,"窗口1");
        th1.start();
        Thread th2 = new Thread(by1,"窗口2");
        th2.start();
        Thread th3 = new Thread(by1,"窗口3");
        th3.start();
    }
}
```

【2】实际开发中，方式1继承Thread类，还是方式2实现Runnable接口这种方式多呢？

（1）方式1的话有Java单继承的局限性，因为继承了Thread类，就不能在继承其他的类了。

（2）方式2的共享资源的能力还是强一些，不需要非得加个static来修饰

【3】Thread类和Runnable接口有关系吗？

Thread类也是Runnable接口的子类，那么在之前继承Thread类的时候实际上还是复写的Runnable接口的run()方法

#### 第三种：实现Cable接口

对比第一种和第二种创建线程的方式，无论第一种继承Thread类的方式还是第二种实现Runnable接口，都需要有一个run方法，但是这个run方法有不足：

```java
@Override
public void run() {
    for (int i = 0; i < 99; i++) {
        if (tickNum >0 ) {
            System.out.println("我在"+Thread.currentThread().getName() + "买到了第"+tickNum--+"张票");
        }
    }
}
```

（1）没有返回值

（2）不能抛出异常

```
基于上面的两个不足，在JDK1.5之后出现了第三种创建线程的方式：实现Callable接口：
实现Callable接口好处：（1）又返回值 	（2）能抛出异常
缺点：线程创建比较麻烦
```

```java
package com.msb.test05;

import java.util.Random;
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.FutureTask;

/**
 * @ClassName: TestRandom
 * @Author: rain
 * @Date: 2022/10/24 - 10 - 24 - 18:38
 * @Description:
 * @Version: 1.0
 */


public class TestRandom implements Callable<Integer> {

    /*
    1.实现Callable接口，可以不带泛型，如果不带泛型，那么call方法的返回值就是Object类型
    2.如果带泛型，那么call的返回值就是泛型对应的类型
    3.从call方法看到：方法又返回值，可以抛出异常
     */
    @Override
    public Integer call() throws Exception {
        return new Random().nextInt(10); //返回从0到10之间的随机数
    }
}

class Test{
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws ExecutionException, InterruptedException {
        //定义一个线程对象
        TestRandom tr = new TestRandom();
        FutureTask ft = new FutureTask(tr);
        Thread th1 = new Thread(ft);
        th1.start();
        //获取线程得到的返回值
        Object obj = ft.get();
        System.out.println(obj);
    }
}
```

### 线程的生命周期

【1】线程生命周期：线程开始 — 线程消亡

【2】线程要经历哪些阶段

![image-20221024191642774](/Users/rain/Library/Application Support/typora-user-images/image-20221024191642774.png)



### 线程常见方法

（1）start(). :启动当前线程，表明上调用start方法，实际在调用线程里面的run方法

（2）run() : 线程类 继承Thread类或者实现Runnable接口的时候，都要重新实现这个run方法，run方法里面是线程要执行的内容

（3）currentThread: Thread 类中一个静态方法：获取当前正在执行的线程

（4）setName： 设置线程名字

  (5)	getName ：读取线程名字

#### 设置优先级 

Thread.setPriority

【1】同优先级别的线程，采取的策略是先到先服务，使用时间片策略

【2】如果优先级别高，被CPU调度的概率就高

【3】级别：1-10，默认的级别为5

```java
/**
 * The minimum priority that a thread can have.
 */
public static final int MIN_PRIORITY = 1;

/**
 * The default priority that is assigned to a thread.
 */
public static final int NORM_PRIORITY = 5;

/**
 * The maximum priority that a thread can have.
 */
public static final int MAX_PRIORITY = 10;
```

代码：

```java
package com.msb.test06;

/**
 * @ClassName: TestThread
 * @Author: rain
 * @Date: 2022/10/24 - 10 - 24 - 19:54
 * @Description:
 * @Version: 1.0
 */


public class TestThread01 extends Thread{
    @Override
    public void run() {
        for (int i = 0; i < 88;i++) {
            System.out.println(i);
        }
    }
}

class TestThread02 extends Thread {
    @Override
    public void run() {
        for (int i = 100; i < 200;i++) {
            System.out.println(i);
        }
    }
}
class Test{
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        TestThread01 th1 = new TestThread01();
        th1.setPriority(10);
        th1.start();

        TestThread02 th2 = new TestThread02();
        th2.setPriority(1);
        th2.start();
    }
}
```



#### join()方法

当一个线程调用了join方法，这个线程会先被执行，他执行结束后才可以去执行其余的线程。

注意：必须先start，再join有效

代码：

```java
package com.msb.test07;

/**
 * @ClassName: TestThread
 * @Author: rain
 * @Date: 2022/10/24 - 10 - 24 - 20:04
 * @Description:
 * @Version: 1.0
 */


public class TestThread extends Thread{
    public TestThread(String name){
        super(name);
    }

    @Override
    public void run() {
        for (int i = 0; i < 8;i++) {
            System.out.println(this.getName()+"---"+i);
        }
    }
}

class Test{
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) throws InterruptedException {
        for (int i = 0; i < 99;i++) {
            if (i ==6) {
                TestThread th1 = new TestThread("子线程");
                th1.start();
                th1.join();
            }
            System.out.println(Thread.currentThread().getName()+i);
        }
    }
}
```

#### sleep方法

【1】人为的阻塞方法

```java
public class Test01 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        try {
            Thread.sleep(3000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("000000000");
    }
}
```

【2】案例：秒表

```java
public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        //2.定义一个时间格式：
        DateFormat df = new SimpleDateFormat("HH:mm:ss");
        while (true) {
            //1.获取当前时间
            Date d = new Date();
            //3.按照上面定义的格式将date类型转为指定格式的字符串
            System.out.println(df.format(d));
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}
```

#### setDaemon方法

【1】设置伴随线程

将子线程设置为主线程的伴随线程，主线程停止的时候，子线程跟着停止

```java
package msb.test09;

/**
 * @ClassName: TestThread
 * @Author: rain
 * @Date: 2022/10/24 - 10 - 24 - 20:42
 * @Description:
 * @Version: 1.0
 */


public class TestThread extends Thread{
    @Override
    public void run() {
        for (int i = 0; i < 1000;i++) {
            System.out.println("子线程---"+i);
}
    }
}

class Test{
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        TestThread th = new TestThread();
        th.setDaemon(true);
        th.start();

        for (int i = 0; i < 10; i++) {
            System.out.println("main---"+i);
        }
    }
}
```

#### stop方法

执行这个方法的时候，线程停止

```java
public class TestThread {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        for (int i = 0; i < 10;i++) {
            if (i == 6) {
                Thread.currentThread().stop();
            }
            System.out.println(i);
        }
    }
}
```

### 线程安全问题

【1】出现问题：

（1）出现了两个10张票或三张10张票

（2）出现了 0张票，-1张票

原因：多个线程，在争抢资源的过程中，导致共享的资源出现问题。一个线程还没执行完，另一个线程就参与进来了，开始争抢。

解决：

在程序中加入“锁”。—  同步监视器 — 加同步

#### 方法1:同步代码块

【1】方法1

```java
public class BuyTicketThread implements Runnable{
   int tickNum = 20;

    @Override
    public void run() {
        for (int i = 0; i < 99; i++) {
            synchronized (this){  //把具有安全隐患的代码锁住就行，如果锁多了就会效率低，this就是这个锁
                if (tickNum >0 ) {
                    System.out.println("我在"+Thread.currentThread().getName() + "买到了第"+tickNum--+"张票");
                }
            }
        }
    }
}
```

【2】: 利用字节码信息

```java
public class BuyTicketThread extends Thread{
    public BuyTicketThread(String name){
        super(name);
    }
    //一共10张票
    static int ticketNum = 10; //多个对象共享这十张票
    //每个窗口都是一个线程对象，每个对象执行的代码放入run方法中
    @Override
    public void run() {
        //每个窗口后面有100个人在抢票：
        for (int i = 0; i <=100;i++ ) {
           synchronized (BuyTicketThread.class){  //锁必须是多个线程用的是同一把锁
               if (ticketNum >0) {
                   System.out.println("我"+this.getName()+"买到了从北京到哈尔滨的票" + ticketNum-- + "张车票");
               }
           }
        }
    }
}
```



【3】同步监视器总结：

```java
总结1:认识同步监视器(锁子)    ----- synchronized(同步监视器)
1.必须是引用数据类型，不能是基本数据类型 
2.也可以创建一个专门的同步监视器，没有任何业务含义
3.一般使用共享资源做同步监视器即可
4.在同步代码块中不能改变同步监视器对象的引用
public class BuyTicketThread extends Thread{
    final String a = "aaa";
    public BuyTicketThread(String name){
        super(name);
    }
    //一共10张票
    static int ticketNum = 10; //多个对象共享这十张票
    //每个窗口都是一个线程对象，每个对象执行的代码放入run方法中
    @Override
    public void run() {
        //每个窗口后面有100个人在抢票：
        for (int i = 0; i <=100;i++ ) {
           synchronized (a){  //锁必须是多个线程用的是同一把锁
               if (ticketNum >0) {
                   System.out.println("我"+this.getName()+"买到了从北京到哈尔滨的票" + ticketNum-- + "张车票");
               }
           }
        }
    }
}
5.尽量不要String和包装类Integer做同步监视器
6.建议使用final修饰同步监视器

总结2:同步代码块的执行过程
1.第一个线程来到同步代码块，发现同步监视器open状态，需要close，然后执行其中的代码
2.第一个线程执行过程中，发生了线程切换(阻塞 就绪)，第一个线程失去了CPU，但是没有开锁open
3.第二个线程获取了CPU，来到了同步代码块，发现同步监视器close状态，无法执行其中的代码，第二个线程也进入阻塞状态
4，第一个线程再次获取CPU，接着执行后续的代码；同步代码执行完毕，释放锁open
5.第二个线程也再次获取CPU，来到了同步代码块，发现同步监视器open状态，拿到锁并上锁，由阻塞状态进入就绪状态，在进入运行状态，重复第一个线程的处理过程(加锁)
  强调：同步代码块中能发送CPU的切换吗？能，但是后续的被执行的过程也无妨执行同步代码块(因为锁仍然close)
  
总结3:其他
1.多个代码块使用了同一个监视器(锁)，锁住一个代码块的同时，也锁住所以使用该锁的所以的代码块，其他线程无法访问其中的任意一个代码块
2.多个代码块使用了同一个同步监视器(锁)，锁住一个代码的同时，也锁住所以使用该锁的所以代码块，但是没有锁住使用同步监视器的代码块，其他线程有机会访问其他同步监视器的代码块。

```

#### 方法2:同步方法

【1】代码展示：

```java
//继承Thread类
public class BuyTicketThread extends Thread{
    public BuyTicketThread(String name){
        super(name);
    }
    //一共10张票
    static int ticketNum = 100; //多个对象共享这十张票
    //每个窗口都是一个线程对象，每个对象执行的代码放入run方法中
    @Override
    public void run() {
        //每个窗口后面有100个人在抢票：
        for (int i = 0; i <=140;i++ ) {
                buyTicket();
            }
        }
    public static synchronized void buyTicket(){  //锁住的是 BuyTicketThread.class 字节码信息
        if (ticketNum >0) {
            System.out.println("我"+Thread.currentThread().getName()+"买到了从北京到哈尔滨的票" + ticketNum-- + "张车票");
        }
    }
}
```



```java
//实现Runnable接口
public class BuyTicketThread implements Runnable{
   int tickNum = 20;

    @Override
    public void run() {
        for (int i = 0; i < 99; i++) {
                buyTicket();
            }
        }
    public synchronized void buyTicket(){  //锁住的是this，谁调用这个方法
            if (tickNum >0 ) {
                System.out.println("我在"+Thread.currentThread().getName() + "买到了第"+tickNum--+"张票");
            }
    }
}
```

【2】总结：

总结1: 

```
多线程在争抢资源，就要实现线程的同步(就要进行加锁，并且这个锁必须是共享的，必须是唯一的。)咱们的锁一般都是引用数据类型的。
```

目的：解决了线程安全问题。



总结2: 关于同步方法

```
1.不要将run()定义为同步方法
2.非静态同步方法的同步监视器是this
	静态同步方法的同步监视器是 类名.class字节码信息对象
3.同步代码块的效率要高于同步方法
	原因：同步方法是将线程挡在了方法的外部，而同步代码块锁将线程挡在了代码块的外部，但是却是方法的内部
4.同步方法的锁是this，一旦锁住了一个方法，就锁住了所有的同步方法；同步代码块只是锁住使用该同步监视器的代码块，而没有锁住使用其他监视器的代码块。
```

#### 方法3:Lock锁

【1】Lock锁引入：

JDK1.5后新增新一代的线程同步方式：Lock锁，与采用synchronized相比，lock可提供多种锁方案，更灵活

synchronized是Java中的关键字，这个关键字的识别是靠JVM来识别完成的，是虚拟机级别的。但是Lock锁是API级别的，提供了相应的接口和对应的实现类，这个方式更灵活，表现出来的性能优于之前的方式。



【2】代码演示：

```java
package com.msb.test04;

import java.util.concurrent.locks.Lock;
import java.util.concurrent.locks.ReentrantLock;

/**
 * @ClassName: BuyTicketThread
 * @Author: rain
 * @Date: 2022/10/24 - 10 - 24 - 16:21
 * @Description:
 * @Version: 1.0
 */


public class BuyTicketThread implements Runnable{
   int tickNum = 20;
   Lock lock = new ReentrantLock(); / 多态，使用接口 -- 实现了实现

    @Override
    public void run() {
        for (int i = 0; i < 99; i++) {
            lock.unlock();
            try {
                if (tickNum >0 ) {
                    System.out.println("我在"+Thread.currentThread().getName() + "买到了第"+tickNum--+"张票");
                }
            }catch (Exception e){
                e.printStackTrace();
            }finally {
                lock.unlock(); //一定要关闭锁
            }
            }
        }
}
```

【3】Lock和synchronized的区别

```
1.Lock是显式锁，(手动开启和手动关闭锁，别忘记关闭锁)，synchronized是隐式锁
2.Lock只有代码块锁，synchronized有代码块锁和方法锁
3.使用Lock锁，JVM将花费时间较少的时间来调度线程，性能更好，并且具有更好的扩展性(提供了更多的子类，使用多态实现)
```

【4】优先使用顺序：

Lock锁。— 同步代码块 （已经进入了方法体，分配了相应资源） —— 同步方法（在方法体之外）



#### 线程同步的优缺点

【1】对比：

线程安全，效率低

线程不安全，效率高

【2】可能造成死锁：

死锁：

- 不同的线程分别占用对方需要的同步资源不放弃，都在等待对方放弃自己需要的同步资源，就形成了线程的死锁
- 出现死锁后，不会出现异常，不会出现提示，只是所有的线程都处于阻塞状态，无法继续

【3】代码演示：

```java
package com.msb.test11;

/**
 * @ClassName: Test01
 * @Author: rain
 * @Date: 2022/10/25 - 10 - 25 - 14:01
 * @Description: 死锁演示
 * @Version: 1.0
 */

线程类

public class Test01 extends Thread{
    public int flag = 1;
    static Object o1 = new Object(), o2 = new Object();

    @Override
    public void run(){
        System.out.println("flag="+flag);

        if (flag==1) {
            synchronized (o1){
                try {
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                synchronized (o2){
                    System.out.println("o1锁住了o2");
                }
            }
        }
        if (flag == 0){
            synchronized (o2){
                try {
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                synchronized (o1){
                    System.out.println("o2锁住了o1");
                }
            }
        }
    }
}

测试类
public class Test02 {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        Test01 t1 = new Test01();
        t1.flag = 1;
        Test01 t2 = new Test01();
        t2.flag = 0;

        t1.start();
        t2.start();
    }
}
```

### 线程通信问题

生产消费问题

#### 分解1:

出现问题：

1.生产者和消费者没有交替输出

2.打印数据错乱

代码展示：

```java
package com.msb.test12;

/**
 * @ClassName: ProducterThread
 * @Author: rain
 * @Date: 2022/10/25 - 10 - 25 - 14:48
 * @Description: 生产者线程
 * @Version: 1.0
 */


public class ProducterThread extends Thread{
    private Product p;

    public ProducterThread(Product p) {
        this.p = p;
    }

    @Override
    public void run() {
        for (int i = 0; i < 10;i++) { //生产十个商品
            if(i%2==0){
                p.setBrand("啤酒");
                try {
                    Thread.sleep(300);
                }catch (Exception e) {
                    e.printStackTrace();
                }
                p.setName("哈尔滨");
            }else{
                p.setBrand("巧克力");
                try {
                    Thread.sleep(300);
                }catch (Exception e) {
                    e.printStackTrace();
                }
                p.setName("费力罗");
            }
            //将生产信息做一个打印
            System.out.println("生产者生产了："+ p.getBrand()+"---"+p.getName());
        }
    }
}
```

```java
package com.msb.test12;

/**
 * @ClassName: CusmoerThread
 * @Author: rain
 * @Date: 2022/10/25 - 10 - 25 - 14:57
 * @Description: 消费者线程
 * @Version: 1.0
 */


public class CusmoerThread extends Thread{
    private Product p;

    public CusmoerThread(Product p) {
        this.p = p;
    }

    @Override
    public void run() {
        for(int i=0;i<10;i++){
            System.out.println("消费者消费了："+p.getBrand()+"---"+p.getName());
        }
    }
}
```

```java
package com.msb.test12;

/**
 * @ClassName: Product
 * @Author: rain
 * @Date: 2022/10/25 - 10 - 25 - 14:43
 * @Description:
 * @Version: 1.0
 */


public class Product {
    private String Brand = null;
    private String Name = null;

    public String getBrand() {
        return Brand;
    }

    public void setBrand(String brand) {
        Brand = brand;
    }

    public String getName() {
        return Name;
    }

    public void setName(String name) {
        Name = name;
    }
}
```

```java
package com.msb.test12;

/**
 * @ClassName: Test
 * @Author: rain
 * @Date: 2022/10/25 - 10 - 25 - 15:01
 * @Description:
 * @Version: 1.0
 */


public class Test {
    //这是一个main方法，是程序的入口：
    public static void main(String[] args) {
        Product p = new Product();
        ProducterThread pt = new ProducterThread(p);

        CusmoerThread cm = new CusmoerThread(p);
        pt.start();
        cm.start();
    }
}
```

#### 分解2:

利用同步代码块

```java
public class CusmoerThread extends Thread{
    private Product p;

    public CusmoerThread(Product p) {
        this.p = p;
    }

    @Override
    public void run() {
        for(int i=0;i<10;i++){
            synchronized (p){
                System.out.println("消费者消费了："+p.getBrand()+"---"+p.getName());
            }
        }
    }
}
```

```java
public class ProducterThread extends Thread{
    private Product p;

    public ProducterThread(Product p) {
        this.p = p;
    }

    @Override
    public void run() {
        for (int i = 0; i < 10;i++) { //生产十个商品
            synchronized (p){
                if(i%2==0){
                    p.setBrand("啤酒");
                    try {
                        Thread.sleep(300);
                    }catch (Exception e) {
                        e.printStackTrace();
                    }
                    p.setName("哈尔滨");
                }else{
                    p.setBrand("巧克力");
                    try {
                        Thread.sleep(300);
                    }catch (Exception e) {
                        e.printStackTrace();
                    }
                    p.setName("费力罗");
                }
                //将生产信息做一个打印
                System.out.println("生产者生产了："+ p.getBrand()+"---"+p.getName());
            }
        }
    }
}
```

利用同步方法

代码演示：

```java
package com.msb.test13;

/**
 * @ClassName: Producr
 * @Author: rain
 * @Date: 2022/10/25 - 10 - 25 - 15:41
 * @Description:
 * @Version: 1.0
 */


public class Producr {
        private String Brand = null;
        private String Name = null;

        public String getBrand() {
            return Brand;
        }

        public void setBrand(String brand) {
            Brand = brand;
        }

        public String getName() {
            return Name;
        }

        public void setName(String name) {
            Name = name;
        }

        //生产商品
        public synchronized void setProduct(String Brand, String Name){
            this.setBrand(Brand);
            try{
                Thread.sleep(100);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            this.setName(Name);
            //将生产信息做一个打印
            System.out.println("生产者生产了："+ this.getBrand()+"---"+this.getName());
        }

        //消费产品
        public synchronized void getProduct(){
            System.out.println("消费者消费了："+this.getBrand()+"---"+this.getName());
        }
}
```

```java
package com.msb.test13;

/**
 * @ClassName: ProducterThread
 * @Author: rain
 * @Date: 2022/10/25 - 10 - 25 - 16:07
 * @Description:
 * @Version: 1.0
 */


public class ProducterThread extends Thread{

    private Producr p;

    public ProducterThread(Producr p) {
        this.p = p;
    }

    @Override
    public void run() {
        for (int i = 0; i < 10; i++) { //生产十个商品
            if (i % 2 == 0) {
                p.setProduct("啤酒","哈尔滨");
            }else {
                p.setProduct("巧克力","费力罗");
            }
        }
}   }
```

```java
package com.msb.test13;


/**
 * @ClassName: CusmoerThread
 * @Author: rain
 * @Date: 2022/10/25 - 10 - 25 - 14:57
 * @Description: 消费者线程
 * @Version: 1.0
 */


public class CusmoerThread extends Thread{
    private Producr p;

    public CusmoerThread(Producr p) {
        this.p = p;
    }

    @Override
    public void run() {
        for (int i = 0; i < 10;i++){
            p.getProduct();
        }
    }
}
```

#### 分解3:交替执行

```java
package com.msb.test13;

/**
 * @ClassName: Producr
 * @Author: rain
 * @Date: 2022/10/25 - 10 - 25 - 15:41
 * @Description:
 * @Version: 1.0
 */


public class Producr {
    private String Brand = null;
    private String Name = null;

    boolean flag = false; //没有商品

    public String getBrand() {
        return Brand;
    }

    public void setBrand(String brand) {
        Brand = brand;
    }

    public String getName() {
        return Name;
    }

    public void setName(String name) {
        Name = name;
    }

    //生产商品
    public synchronized void setProduct(String Brand, String Name){
        if(flag== true){
            try {
                wait();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }

        this.setBrand(Brand);
        try{
            Thread.sleep(100);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        this.setName(Name);
        //将生产信息做一个打印
        System.out.println("生产者生产了："+ this.getBrand()+"---"+this.getName());
        //告诉消费者来消费
        flag = true;
        //等待其他进程执行
        notify();
        }


    //消费产品
    public synchronized void getProduct(){
        if (flag == false) {
            try {
                wait();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        System.out.println("消费者消费了："+this.getBrand()+"---"+this.getName());
        //消费完等待生产
        flag = false;
        notify();
    }
}
```

【原理】：