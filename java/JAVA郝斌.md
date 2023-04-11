# GUI

## 组件

组件（Component）是图形用户界面的基本组成元素，凡是能够以图形化方式显示在屏幕上并能够与用户进行交互的对象均为组件，如菜单、按钮、标签、文本框、滚动条等。

组件分类：1.java.awt.Component  2. Java.awt.MenuComponent 3.说明：抽象类Java.awt.Component是除菜单相关组件之外所有Java AWT 组件类的根父类，该类规定了GUI组件的基本特性，如尺寸、位置和颜色效果等，并实现了作为一个GUI部件所应具备的基本功能。

## 容器

1. 组件通常不能独立地显示出来，必须将组件放在一定的容器中才可以显示出来。
2. 有一类特殊的组件是专门用来包含其他组件的，这类组件叫做容器，java.awt.Container是所有包含容器的父类，java.awt.Container继续自java.awt.Component
3. 容器类对象本身也是一个组件，具有组件的所有性质，但反过来组件却不一定是容器。

### Panel

1. panel 是容纳其他组件的组件

2. panel 是容器

3. panel不能单独存在，必须得被添加到其他容器中。

   ```java
   panel类拥有从其父类继承来的
   setBounds(int x,int y,int width,int height)
   setSize(int width, int hight)
   setLocation(int x, int y)
   setBackground(Color c)
   setLayout(LayoutManager mgr)等方法
   panel的构造方法为：
   panel()使用默认的Flow Layout类布局管理器初始化。
   Panel(LayoutManger layout)使用指定的布局管理器初始化
   ```

   



### 布局管理器总结

Frame是一个顶级窗口，Frame的缺省布局管理器为BorderLayout，

Panel无法单独显示必须添加到某个容器中，Panel的缺省布局管理器为FlowLayout。当把Panel作为一个组件添加到某个容器中，该Panel仍然可以有自己的布局管理器。使用布局管理器是，布局管理器负责各个组件的大小和位置，因此用户无法在这种情况下设置组件大小和位置属性，如果试图使用Java语言提供的setLocation(),setSize(),setBounds()等方法时，则都会被布局管理器覆盖。

如果用户确实需要亲自设置组件大小或位置，则应取消该容器的布局管理器，方法为：setLayout(null)。

### 

## 事件

### 事件处理相关概念

事件（Event）:用户对组件的一个操作，称之为一个事件。

事件源（Event Source）：能够产生事件的GUI组件对象，如按钮、文本框等。

事件处理方法（Event Handler）：能够接收、解析和处理事件类对象，实现与用户交互功能的方法。

事件监听器（Event Listener）：可以处理事件的一个类。

默认情况下事件源不会自动产生任何事件，程序员需要做两件事：1. 告诉事件源可以自动产生哪类事件，即：事件源注册某种事件的事件监听器对象。 2. 设计好可以处理这种事件的事件监听器

一旦完成了这两步操作，当用户对事件源进行操作时，事件源就会自动产生事件，事件源就会自动把产生的事件封装成一个事件对象，事件源就会自动把封装好的事件对象传递给事件监听器

事件监听器收到事件源发送过来的事件时，事件监听器就会自动调用相应的事件处理方法来对该事件进行相应的处理。



### 事件处理步骤

假设事件为XXXX

1. 像事件源注册某种事件的事件监听器对象 

    addXXXXListener(...);

2. 设计好可以处理这种事件的事件监听器

   ```JAVA
   1. class 类名 implements XXXXListener
   
      {
   
      ​	重写XXXXListener 接口中的方法
   
      }
   
      说明：要想设计出能够处理XXXX事件的监听器，只需要编写出实现了XXXXListener接口的类就OK了，因为XXXXListener 接口中已经定义了可以处理XXXX事件的方法
   
   
   ```

#  内部类

内部类定义：

​	在A类的内部但是所有方法的外部定义了一个B类，则B类就是A类的内部类，A是B的外部类。

内部类访问原则

​	内部类的方法可以访问外部类所有的成员

​	外部类的方法不可以直接访问内部类的成员

内部类的优点：

​	可以让一个类方便的访问另一个类中的所有成员

​	增加程序的安全性，有效避免其他不相关类对该类的访问

何时使用内部类

​	如果一个A类要使用B类的所有成员，并且A类不需要被除B类以外的其他类访问，则我们应当把A类定义为B类的内部类。

# 匿名类

匿名类是一种特殊的内部类

如果在一个方法内部定义了一个匿名类，则该匿名类可以访问：

​	外部类的所有成员

​	包裹该匿名类的方法中的所有final类型的局部变量

​		·注意：非final类型的局部变量无法被匿名类访问



创建匿名类的三种方式

1. 继承父类

2. ```
   假设A是类名
   格式：
   new A(){
   				实现A类中的方法代码
   				添加了自己的方法或属性代码
   }；
   功能：生成了一个A类的子类对象，该匿名类对象继承了A的所有非private成员。
   ```

   

3. 实现接口

   ```java
   假设A是接口类
   格式：
   new A(){
   				实现接口中方法的代码
   }；
   功能：生成了一个实现A接口的匿名类
   ```

   

4. 实现抽象类

   ```Java
   假设A是抽象类
   格式：
   new A(){
   				实现A类中的所有抽象类的方法代码
   				添加了自己的方法或属性代码
   }；
   功能：生成了一个匿名类，该匿名类必须的实现了A类的所有抽象方法，当然该匿名类也可以定义自己的属性和方法
   ```

   # 可运行jar包的生成步骤

1.新建一个记事本文件，假设为1.txt,文件内容：

​	Main- class：可运行类的名字

​	附注：记着敲回车	

2.dos下命令

​	jar cvfm haha.jar 1.txt*.class

​	记住：只有GUI程序生成的class文件才可以作为mainclass.



# 流

流就是程序和设备之间嫁接起来的一根用于数据传输的管道，这个管道上有很多按钮，不同的按钮可以实现不同的功能。

这根带按钮的用于数据传输的管道就是流

流就是一根管道

## 四大基本抽象流

- InputStream 和 OutputStream 读写数据的单位是一个字节，Reader 和 Writer 读写数据的单位是一个字符，在Java 中一个字符占两个字节。

- InputStream 和 OutputStream、Reader 、 Writer都是抽象类，或者说都是抽象流，通常我们使用的都是它们的子类。

- 凡是以Stream结尾的都是字节流。-



## 字节流与字符流区别

- FileInputStream 和 FileOutPutStream 可以完成所有格式文件的赋值

- FileReader 和 FileWriter只可以完成文本文件的复制，却无法完成视频格式文件的复制

- 因为字节是不需要解码和编码的，将字节转化为字符才存在解码和编码的问题

- 字节流可以从所有格式的设备中读写数据，但字符流只能从文本格式的设备中读写数据。

## 缓冲流

- 缓冲流就是带有缓冲区的输入输出流

- 缓冲可以显著的减少我们对IO访问的次数，保护我们的硬盘。

- 缓冲流本身就是处理流（处理流也叫包裹流），缓冲流必须的依附于节点流（节点流也叫原始流）

- 处理流是包裹在原始节点流上的流，相当于包括在管道上的管道

### BuffrtedOutputStream 和 BufferedInputStream

BufferedInputStream流中有 public int read (byte[] b) 方法用来把从当前流关联到的设备中读取出来的数据存入一个byte数组中。 

BuffrtedOutputStream流中有 public int write(byte[] b)方法用来把byte数组中的数据输出到当前流关联的设备中。

如果我们希望用BuffrtedOutputStream 和 BufferedInputStream完成“将一个设备中的数据导入另一个设备中，我们就应该定义一个临时的byte类型的数组，用这个临时数组作为输入流和输出流进行交互的中转枢纽。”

### DataInputStream

DataInputStream 能够以一种与机器无关的方式，直接从底层字节输入流读取Java基本类型和String类型的数据，

DataInputStream是包裹流，必须依附于INputStream。





# 容器

## 为什么需要容器？

数组存在两个缺陷：

— 数组长度难以扩充

— 数组中元素类型必须相同

容器可以弥补数组的这两个缺陷

举例：

```java
假设A是类名
A[] arr = new A[10];
表示分配了一个数组，数组的每个元素都是A类对象的一个饮用，但是如果想扩充数组的长度，比如希望数组的长度变成15，我们是不能直接在原数组内存的后面追加内存的，必须得另外分配长度为15的内存空间，利用System.arraycopy()方法来吧原数组的内容拷贝到新内存中，
所以一旦数组内存已分配，想改变数组的长度，效率就会变得很低。
```



## 容器的分类和使用

### 容器与现实的对应关系

集合就是将若干用途、性质相同或相近的“数据”组合而成一个整体。

数学上，集合类型可以归纳为三类：

```
集(Set)
Set集合中不区分元素的顺序，不允许出现重复元素。
列表(List)
List不表示链表的意思，而是表示线性结构
List集合区分元素的顺序，且允许包含重复元素。
映射(Map)
映射中保存成对的“键-值”(Key- value)信息，映射中不能包含重复的键，每个键最多只能映射一个值。
Java设计了三个接口来对于数学上的三种集合类型，这三个接口名字分别为Set List Map。
```



### collection

— collection接口-定义了存取一组对象的方法，其子接口Set和List分别定义了存储方式。set中的数据对象没有顺序且不可以重复，List中的数据对象有顺序且可以重复。

```java
import java.util.*;
/*
* 所以添加到Collection容器中的对象，都应该重写父类Obeject里面的toString方法
* */
public class TestCollection {
    public static void main(String[] args){
        Collection c= new LinkedList();
        c.add(new Student("zhangsan", 80));
        c.add(66.6);
        System.out.println(c);
    }
}

class Student {
    private String name;
    private int age;
    public  Student(String name, int age){
        this.age = age;
        this.name = name;
    }

    //如果注释掉tostring方法，那么容器的添加的student对象就是他的名字加hash地址。
    public String toString(){
        return name + " " + age;
    }
}
```



### Collection接口中的方法介绍

```java
int size();
	返回此collection中的元素数
boolean isEmpty();
boolean containesAll(Collection c);
	判断形参c指向的集合中所有的元素是不是已经全部包含在了当前集合中，是，返回true，否则返回false
Iterator iterator()；
	返回能够遍历当前集合所有元素的迭代器。
Object[] toArrat()
	容器不是数组，不能通过下标的方式访问容器中的元素
	只有数组才可以通过下标来访问
	返回一个包含此collection中所有元素的数组
boolean add(Object e);
	把e添加到当前集合中
boolean remove(Object o);
boolean addAll(Collection c);
	把c中所有的元素添加到当前集合中
boolean removeAll(Collection c)
```



#### Set

##### HashSet类

```
HashSet类实现了Set接口
HashSet类容器中的元素是不能重复的，无顺序的
存放入HashSet容器中的类必须要实现equals()和hashCode方法
```

##### 重写hashCode()方法的必要

- string和integer这些java自带的类都重写了hashCode方法，如果String和Integer new出来的对象的内容是一样的，则这些对象的hashCode返回值也是一样的，尽管这些对象占用的是不同的内存，

- 不过用户自定义类型则不同，如本程序的A类，即便是两个内容一模一样的A类对象，它们返回的hashCode值也是不一样的，但是两个内容一模一样的Integer类对象和String类对象的hashCode值却是一样的，因为系统自带的String和Integer类都已经重写了Object的hashCode方法。

- 如果程序员希望自己定义的类对象，占有不同内存空间但内容却是一样的对象调用hashCode方法返回值是一样的，则程序员就必须自己重写hashcode方法，

##### 什么容器必须重写equals方法和hashCode方法

-  散列码：

  Object中的hashCode方法会返回该对象的内存真实地址的整数化显示，这个形象的不是真正地址的整数值就是哈希码

-  向HashSet中添加对象时，Hashset先通过该对象的hashCode方法计算出相应的桶，然后在根据equals方法想到相对应的对象，如果容器中已经存在该对象则不在添加，如果不存在，则添加进去

- 添加到hashMap和Hashtable容器中的键必须的同时实现equals（）方法和hashCode()方法，否则很可能导致容器中出现重复的映射，所谓重复映射是指同一个键值映射在容器中出现了多次。

- 添加到HashSet容器中的对象也必须得同时实现equals（）方法和HashCode（）方法，否则很可能导致容器中出现重复的对象。
- Hashtable HashSet HashMap 都必须的同时实现equals()方法和hashCode()方法，TreeSet和TreeMap则不需要实现equals（）方法和HashCode()方法

##### 怎样重写equals（）和hashCode()方法

```java
如何重写equals()
public boolean equals (Object obj){
		如果this和obj的内容是一模一样的
					返回true
		否则
					返回false
}
如何重写hashCode()方法
public int hashCode()
{
  return 当前类中基本类型数据对象的hashCode()方法
}
```



#### List

```java
ArrayList和LinkedList都实现了List接口中的方法，但两者内部实现不同。
ArrayList底层采用数组完成，而LinkedList则是以一般的双向链表(double-linkedlist)完成，其内每个对象除了数据本身外，还有两个饮用，分别指向前一个元素和后一个元素。
如果我们经常在List的开始处增加元素，或者在List中进行插入和删除操作，我们应该使用LinkedList,否则的话，使用ArrayList将更加快速。
ArrayList存取速度快，插入删除慢。
LinkedList存取速度慢，插入删除速度快。
```

List接口是collection的子接口，实现List接口的容器类中的元素是有顺序的，而且可以重复。

List容器中的元素都对应一个整数型的序号记载其在容器中的位置，可以根据序号存取容器的元素。

List容器类有ArratList,LinkedList等。

```java
Object get(int index);
Object get(int index, Object element);
void get(int index, Object element);
Object remove(int index);
int indexof(Obect o);
int lastIndexOf(Object o);
```



#### Map

— Map接口定义了存储“键（key）— 值（value）映射对”的方法。

```java
java.util.Map接口描述了映射结构，Map结构允许以键集、值集合或键-值映射关系集的形式查看某个映射的内容。
主要方法：
	Object put(Object key, Object value)
	Object get(Object key)
		注意map接口中并没有 	Object get(Object value)
	boolean isEmpty()
	void clear()
	int size()
	boolean containsKey(Object key)
	boolean containsValue(Object value)
```



## Collections类

Collection接口的实现类，如ArratList,LinkedList本身并没有提供排序，倒置和查找方法，这些方法是由Collections类来实现的，该类有很多public static 方法，可以直接对collection接口的实现类进行操作。

java.util.Collections 提供了一些静态方法，实现了基于List容器的一些常用算法。

```java
void sort(List)  对List容器中的元素进行排序
void shuffle(List)  对List容器中的对象进行随机排序
void reverse(List)  对List容器中的对象进行逆序排序
void fill(List， Object)  用一个特定的对象重写整个List容器
void sort(List dest， List src)  将src List容器内容拷贝到dest List容器
int binarySearch(List, Object)]对于顺序的List容器，采用折半查找的方法查找特定对象
```



## Comparale接口

### 为什么要使用Comparable接口

```
基本类型数据和String类型数据，它们彼此的比较标准Java语言本身已经提供好了。
用户自定义类对象之间比较的标准Java语言本身是没有提供的
所以如果一个容器中含有用户自定义类型的数据，并且我们需要对容器中元素进行排序，或查找某一元素时，我们就必须得制定容器中元素与元素之间比较的标准。
凡是需要进行对象比较/排序的场合均可考虑实现Comparable接口。
```



## Iterator接口

### Iterator方法介绍

- Boolean hasNext();

  用来判断当前游标的后面是否还存在元素，如果存在返回真，否则返回假，

- Object next();

  先返回当前游标右边的元素，然后游标后移一个位置

- void remove() 

  删除最近返回的元素，在调用remove之前，我们至少保证先调用一次next方法，而且调用next之后只能调用一次 remove方法不推荐使用

  

### TreeSet类

- TreeSet类实现了Set接口

- TreeSet是一个有序集合，TreeSet中元素将按照升序排列，缺省时按照自然顺序进行排列，因此TreeSet中元素要实现Comparable接口，

- 所以可以进行排序的类都应该实现Comparable接口

  

### HashSet和TreeSet的比较

HashSet是基于Hash算法实现的，其性能通常都优于TreeSet,我们通常都应该使用HashSet,在我们需要排序的功能是时，我们才使用TreeSet.

# 泛型

泛型是用来限制传入容器、接口中的数据类型。可以指定容器中传入数据的类型。

------

# 网络编程

## 网络程序

- 能够接受另一台计算机发送过来的数据或者能够向另一台计算机发送数据的程序叫做网络程序。

## IP

- 能够在网络中唯一标示一台主机的编号就是IP。
- 网络中每台主机都必须有一个唯一的IP地址
- IP地址是一个逻辑地址。
- 因特网上的IP地址具有全球唯一性。
- 32位，4个字节，常用点粉十进制的格式表示，例如：192.168.0.16

## 端口

- 一台计算机上可以同时运行多个网络程序
- 一台计算机从网卡接受过来的数据到底应该是交给本地的哪个网络程序来处理的，这是有端口号决定的
- 端口号是用一个16位的数字来表示，他的范围是0～65535，1024以下的端口号保留给预定义的服务。例如：80端口访问网页，25端口用来邮件发送，oralce92默认的端口号是1521，tomcat默认的端口号是8080

## 协议

为进行网络中的数据交换（通信）而建立的规则、标准或约定。

### http协议

- http是浏览器和服务器之间进行数据传输到一个协议。
- 浏览器发送到服务器的数据称为请求信息。
- 服务器发送到浏览器的数据称为响应信息。

#### http协议下的请求信息

一个完整的http协议下的请求消息包括三部分内容

- 请求行
- 若干可选消息头
- 正文内容（可以为空）

请求行包含三部分内容，彼此之间用空格分割

- 请求方式
  - 如get post
- 资源路径
  - 用户想访问的资源的地址
- HTTP版本号

#### http协议下的响应信息

一个完整的http协议下的响应消息包括三部分内容

- 一个状态行
- 若干可选消息头
- 正文内容

状态行包含三部分内容，彼此之间用空格分隔

- HTTP版本号
- 状态吗
- 原因叙述

### 常见协议

- TCP：面向连接的可靠的传输协议，类似于打电话。
- UDP：是无连接的，不可靠的传输协议，类似于写信。

## 套接字的引用

- 为了能够方便的开发网络应用软件，由美国伯克利大学在Unix上推出了一种应用程序访问通信协议的操作系统调用socket套接字，socket的出现，使程序员可以很方便的访问TCP/IP，从而开发各种网络应用的程序。
- 随着Unix的应用推广，套接字在编写网络软件中得到了极大的普及，后来，套接字又被引用了window等操作系统中，Java语言也引入了套接字模型。

### 基于UDP的socket编程步骤

1. 定义码头
   - 即：定义一个DatagramSocket对象ds

2. 定义可以用来接受或发送数据的集装箱
   - 定义DatagramPacket对象dp

3. 在码头上用集装箱接收对方发送过来的数据（ds.receive(dp);）或者在码头上把集装箱中的数据发送给对方（ds.send(dp)）
4. 关闭码头（disclose()）



接收端程序编写：

1.调用DatagramSocket（int port）创建一个数据报套接字，并绑定到指定端口上，2.调用DatagramPacket（byte[] buf, int length）,建立一个字节数组以接收UDP包，3，调用DatagramSocket类的receive（），接收UDP包，4，最后关闭数据报套接字。

```java
//package S_24;

import java.io.ByteArrayInputStream;
import java.io.DataInputStream;
import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.SocketException;

public class TestUDPServer {
    public static void main(String[] args) throws Exception {

        //定义码头
        DatagramSocket ds = new DatagramSocket(5678); //5678表示该码头占有这个5678编号，因为一台计算机可以有多个码头接收多个数据，这些码头用不同的编号来表示，这些编号的专业术语就是端口号。

        //定义可以用来接受数据的集装箱,无论发送数据还是接收数据，都是用包来实现，这个包的内核就是字节数组。把这个字节数组封装为dp对象。
        byte[] buf = new byte[1024];
        DatagramPacket dp = new DatagramPacket(buf, buf.length);

        try{
            //使用while循环不停接收收据
            while(true)
            {
                //在码头上用集装箱接收对方发送过来的数据
                ds.receive(dp); //注意：本语句执行完毕就意味着，dp数据包中已经有了从客户端接收过来的数据。

                //从集装箱中取出对方发送过来的数据。
                ByteArrayInputStream bais = new ByteArrayInputStream(dp.getData());//1.ByteArrayInputStream的内核必须是个字节数组，并且是从该字节数组中读取数据，2.dp.getData()表示把dp集装箱的数据转化为一个字节数组，并且返回该字节数组
                DataInputStream dis = new DataInputStream(bais);
                System.out.println(dis.readLong());
            }
        }
        catch (Exception e){
            e.printStackTrace();
            ds.close(); //关闭码头
        }}}
```

发送端程序编写：

1.调用DatagramSocket（）创建一个数据报套接字，2，调用DatagramPacket（byte[] buf, int offset, int length, InetAddress address, int port). 建立要发送的UDP包，3，调用DatagramSocket（）类的send（），发送UDP包，4，最后关闭数据报套接字。

```java
//package S_24;

import java.io.*;
import java.net.*;

public class TestUDPClient {
    public static void main(String[] args) throws IOException {

        //定义码头
        DatagramSocket ds = new DatagramSocket();

        //13 行到23 行完成的功能是：定义可以发送数据的集装箱dp，dp中保存着n的二进制代码
        long n = 10000L; //13行
        ByteArrayOutputStream baos = new ByteArrayOutputStream();//内部是一个默认缓冲字节流，把n的数据放入默认缓冲区中。它并没有byte[] buf这样的形参，即定义ByteArrayOutputStream流对象时是不能指定byte数组的，因为这个连接到的byte数组是默认生成的，new ByteArrayOutputStream();创建一个新的byte数组输出流，缓冲区的容量最初是32字节，如有需要可增加其大小。"
        //10行代码执行完毕，意味着两点： 1， 在内存中生成一个大小为32个字节的字节数组 2.有一根叫做baos的管道已链接到了该byte数组中，并可以通过这个管道向该数组中写入数据。
        //虽然此时可以通过baos向baos所连接到的在内存中分配好的byte数组中写入数据，但是ByteArrayOutputStream流中并没有提供可以直接把long类型数据直接写入ByteArrayOutputStream流所连接到的数组的方法，简单地说我们没办法通过baos向baos所连接到的byte数组中写入long类型的数据。ByteArrayOutputStream流中没有类似writeLong（）这样的方法，但是DataOutputStream流中却有writeLong方法

        DataOutputStream dos = new DataOutputStream(baos);
        dos.writeLong(n); //把n变量所代表的10000L写入dos所依附的管道baos所连接到的内存大小为32字节的byte数组中，

        byte[] buf = baos.toByteArray(); //dos流中并没有toByteArray()方法，但是ByteArrayOutputStream流中却有toByteArray()方法，所以不可以把baos改为dos，否则编译会报错，ByteArrayOutputStream流中toByteArray()方法的含义：摘自API"创建一个新分配的byte数组，其大小是此输出"
        DatagramPacket dp = new DatagramPacket(buf, buf.length, new InetSocketAddress("127.0.0.1", 5678));

        //在码头上把集装箱中的数据发送给对方。
        ds.send(dp);

        //关闭码头
        ds.close();
    }}
```



### 基于TCP的socket编程步骤

服务端

```java

import java.io.*;
import java.net.*;

public class TestTCPServer {
    public static void main(String[] args) throws Exception {
        ServerSocket ss = new ServerSocket(8888);
        //8 行 6666 是端口号，表示该服务器程 序在监听 666 端口是否有客户端程序的连接
        // new出的ServerSocket对象ss 并不会自动监听客户端有没有向6666 端口发送请求，要想监听 6666 端口是否有客户端的请求，则必须的调用 ss 对象的 accept 方法
        // 如果本程序只有 8 行这一行的代码的话，本程序运行时将无任何输 出结果并会立即终止
        while(true){
            Socket s =  ss.accept();
            s = ss.accept(); //accept()功能：等待客户端的连接，没有连接，则继续 监听，程序停滞不前，如果接收到客户端的一个连接，则自动将该连接封装为一个 Socket 对象，程序将不再阻塞，而是继续放下执行
            //  这里的s实际是链接到客户端的s ，服务器端的 s.getInputStream() 和客户端的 s.getOutputStream()实际是同一根管道
            // accept()是阻塞式方法，如果接收不到客户端的连接，则程序将停止不前
            System.out.println("一个连接已建立！");
            DataInputStream dis = new DataInputStream(s.getInputStream());//通过 Socket 对象可以获得 InputStream 和 OutputStream 两个管道
            System.out.println(dis.readUTF());//readUTF()方法也是阻塞式方法，如果接收 不到客户端数据，则程序将停止不前
            dis.close();//DataInputStream 和 InputStream 流中都没有flush 方法DataOutputStream 和 OutputStream 流中都有 flush 方法
            s.close();
        }}}
```

客户端

```java
import java.io.*;
import java.net.Socket;

public class TestTCPClient {
    public static void main(String[] args) throws Exception {
        Socket s = new Socket("127.0.0.1", 6666);
        //8行，第一个参数是要连接到的主机IP，即表示要连接到哪台机器上，
        // 127.0.0.1 表示链接到本机，第二个参数表示要链接到哪个网络程序上
        //new Socket("127.0.0.1", 6666) 一旦构造对象成功，就意味着这时已经产生了一个试图和IP 为"127.0.0.1" 端口为 6666 的网络程序进行连接的请求
        // 如果这时 IP 为"127.0.0.1" 的机器上正好有一个网络程序在监听 6666 端口，这时连接就会建立成功
        // 所谓连接成功是指这两个网络程序建立了一个通信管道，双方都可以通过这个管道写数据和读数据，并且一方写入的数据实际就是另一方要读取的数据，一方要读取的数据实际就是另一放要写入的数据，
        // 即这个管道实际是双向的，任何一方都可以 通过 getInputStream() 和 getOutputStream()获取输入流和输出流两个流，并且一方的输入流 实际就是另一方的输出流，这是同一个流，一方的输出流实际就是另一方的输入流，这也是同一个流即一个通信管道两个流，双方各自都可以得到两个流，这两个流分别是输入流和输出流
        // 记住：一旦new出了Socket对象，该对象就会自动向服务器端发送连接请求，如果连接不成功则程序立即终止
        // 因此我们在 TCP 编程的客户端是找不到请求连接的代码，但是在服务器端却存在监听客户端连接请求的代码, 代码类似于：ss.accept()
      
        OutputStream os = s.getOutputStream();
        //16 行一旦连接成功，相当于建立了一根管道，这根管道在客户端相当于输出流管道，在服务器端相当于输入流管道!
        // 程序如果能执行到 16行说明已经连接成功，因为 8行执行完后就会自动立即发送一个连接请求，如果服务器端没有打开，或者服务器端虽然已经打开但是却没有监听客户端的连接请求，则程序会立即终止，是不会执行到 16 行的， 如果执行到 了 16 行那说明连接成功了

        DataOutputStream dos = new DataOutputStream(os);
        dos.writeUTF("同志们好！");
        dos.flush();
        dos.close();
        s.close();
    }}
```

