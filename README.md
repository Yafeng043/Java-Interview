# Java-Interview

主要内容来自互联网上的整理与自我理解。

[重要参考：Java面试通关要点汇总集（部分解答）](https://segmentfault.com/a/1190000013447750?utm_source=tag-newest)

## 一、基础篇
* 面向对象的特征
封装，继承，多态
多态：父对象的同一个行为能在其多个子对象表现出不同的行为

* 面向对象的五大原则
> (1)单一职责原则(Single-Resposiblity-Principle):一个类应该仅有一个引起它变化的原因
(2)开放封闭原则(Open-Closed-Principle):对扩展开放，对更改时封闭的
(3)里氏替换原则(Liskov-Substituion Principle):子类可以替换父类，并且出现在父类能够出现的任何地方。GOF倡导面向接口编程
(4)接口隔离原则(Interface-Segregation Principle)：使用多个接口比使用单个接口要好的多。
(5)依赖倒置原则(Dependecy-Invarsion Principle):让高层模块不要依赖低层模块。

* final, finally, finalize

   1、final修饰符(关键字)

    final用于控制成员、方法、或者是一个类是否可以被重写或者继承功能。

    (1)、如果类被声明为final，意味着它不能被派生出新的子类，不能作为父类被继承。
    (2)、将变量或方法声明为final，可以保证他们在使用中不会被改变，其初始化可以在两个地方：

    在final定义时直接给赋值，
    在构造函数中，二者只能选其一，在以后的引用中只能读取，不可修改
    2、finally(用于异常处理)
    一般是用于异常处理中，提供finally块来执行任何的清楚操作，try{}catch{}finally{}.finally结构使代码块总会执行，不管有无异常发生。使得finally可以维护对象的内部状态，并可以清理非内存资源。用于关闭文件的读写操作或者关闭数据库连接操作。

    3、finalize(用于垃圾回收)

    finalize这个是方法名。在Java中，允许使用finalize()方法在垃圾收集器将对象从内存中清理出去之前做必要的清理工作。这个方法是由垃圾收集器在确定这个对象没有被引用时对这个对象调用的。它是Object中定义的。因此，所有类都继承了它，finalize方法是在垃圾收集器删除对象之前对这个对象调用的。

    finally联想到try catch finally，
    主要记住finalize

* Exception、error、运行时异常和一般异常有何异同
[参考](https://blog.csdn.net/m0_37531231/article/details/79502778)

* 请写出5种常见的runtime exception
[参考](https://blog.csdn.net/m0_37531231/article/details/79502778)

* int 和 Integer 有什么区别？Integer的值缓存范围
[参考](https://blog.csdn.net/why15732625998/article/details/79437930)

* 包装类，装箱和拆箱

* String、StringBuilder、StringBuffer
String 字符串常量
StringBuffer 字符串变量（线程安全）
StringBuilder 字符串变量（非线程安全）

* 重载与重写
方法重载
重写方法

* 抽象类与接口的区别
含有抽象方法的类一定是抽象类。

* 说说反射的用途及实现
[参考](https://www.jianshu.com/p/d6035d5d4d12)

* 说说自定义注解的场景与实现

* 列出自己常用的JDK包
> 1、java.lang
2、java.sql
3、java.io
4、java.math
5、java.text
6、java.net
7、java.util
8、java.awt
9、java.applet
10、java.nio

* JDBC 流程
准备 private static final URL、、、 也可以用properties从文件中读取。load()、

1、首先注册驱动啊？怎么注册？反射啊，Class.forName("xx.xx.xx.Driver");底层怎么实现的？静态代码，DriverManager.registerDriver?启动的时候，会自动调用静态代码块的内容。

2、接下来就是获取连接啊，怎么连接？远程连接(三次握手操作)，连接放哪里？作为资源必须放池子里。这样能提高性能。常见的连接池有DBCP，C3P0，传说中最安全，性能最好的Druid(国产)，而且还能监控。

3、你总的有SQL语句吧，之后就是Statement编译那。这里会出现SQL注入的安全问题。在语句后面加"1=1"成立。所以我们采用预编译的方式，PreparedStatement。可以防止这种问题的出现。

4、查完之后获取结果集。rs.getString().

5、头疼的来了，释放资源。各种 if(xx != nu) {try{ xx.close();}catch{}} 不用担心JDK8 出来一个新特性，可以放在try-withresource中。还有各种异常可以采用通道的形式 XxxException | XxxException

6、各种异常需要你放到一个try{}catch{}中，出问题你也不知道问题在哪里？

麻烦吗？不用担心，我们可以封装成一个工具类，需要的时候调用工具类.getConnection();

还是麻烦啊，可以用Spring框架为我们集成提供了jdbcTemplate，HibernaterTemplate。用模板代码消除了大量的样板代码。

为啥不早告诉我JDBC连接这么简单？同志们，我们需要知其然的同时，还要知其所以然。这样出现问题的时候才能找到更好的解决方法。

* hashCode和equals方法的区别于联系
[参考](https://www.cnblogs.com/keyi/p/7119825.html)
[参考](https://blog.csdn.net/haobaworenle/article/details/53819838)

* 什么是Java的序列化与反序列化
[参考](https://blog.csdn.net/m0_37531231/article/details/79574461)

* 为什么wait()和notify()属于Object类
[参考](https://www.cnblogs.com/lirenzhujiu/p/5927241.html)
不是特别懂

* JAVA详细运行过程及与平台无关性
JRE由JVM和API构成。
https://www.cnblogs.com/beyourself/p/3279503.html

* Java中JDK和JRE的区别是什么？它们的作用分别是什么？
https://blog.csdn.net/qq_33642117/article/details/52143824

* Java中ArrayList和LinkedList区别
ArrayList和LinkedList的大致区别如下:
1.ArrayList是实现了基于动态数组的数据结构，LinkedList基于链表的数据结构。 
2.对于随机访问get和set，ArrayList觉得优于LinkedList，因为LinkedList要移动指针。 
3.对于新增和删除操作add和remove，LinedList比较占优势，因为ArrayList要移动数据。 

* ArrayList和Vector的主要区别
ArrayList，Vector主要区别为以下几点： 
（1）：Vector是线程安全的，源码中有很多的synchronized可以看出，而ArrayList不是。导致Vector效率无法和ArrayList相比； 
（2）：ArrayList和Vector都采用线性连续存储空间，当存储空间不足的时候，ArrayList默认增加为原来的50%，Vector默认增加为原来的一倍； 
（3）：Vector可以设置capacityIncrement，而ArrayList不可以，从字面理解就是capacity容量，Increment增加，容量增长的参数。
https://blog.csdn.net/ldxlz224/article/details/52574821

* HashTable和HashMap的区别详解

https://blog.csdn.net/fujiakai/article/details/51585767

* HashMap 在 JDK 1.8 后新增的红黑树结构
https://blog.csdn.net/u011240877/article/details/53358305

* 多线程环境下hashmap死循环
https://www.cnblogs.com/ITtangtang/p/3966467.html

* HashMap出现了hash DOS攻击的问题
http://www.freebuf.com/articles/web/14199.html

* 多线程 ---并发与并行概念总结
https://blog.csdn.net/qq_33290787/article/details/51790605


## 设计模式
* 设计模式六大原则
https://www.cnblogs.com/dolphin0520/p/3919839.html
单一职责原则 高内聚，低耦合
开闭原则(Open-Closed Principle, OCP)：一个软件实体应当对扩展开放，对修改关闭。即软件实体应尽量在不修改原有代码的情况下进行扩展。
> 如果一个系统在扩展时只涉及到修改配置文件，而原有的Java代码或C#代码没有做任何修改，该系统即可认为是一个符合开闭原则的系统。

里氏代换原则(Liskov Substitution Principle, LSP)：
在软件中将一个基类对象替换成它的子类对象，程序将不会产生任何错误和异常，反过来则不成立，如果一个软件实体使用的是一个子类对象的话，那么它不一定能够使用基类对象。例如：我喜欢动物，那我一定喜欢狗，因为狗是动物的子类；但是我喜欢狗，不能据此断定我喜欢动物，因为我并不喜欢老鼠，虽然它也是动物。
里氏代换原则是开闭原则的具体实现手段之一。


依赖倒转原则(Dependency Inversion  Principle, DIP)：抽象不应该依赖于细节，细节应当依赖于抽象。换言之，要针对接口编程，而不是针对实现编程.
依赖倒转原则要求我们在程序代码中传递参数时或在关联关系中，尽量引用层次高的抽象层类，即使用接口和抽象类进行变量类型声明、参数类型声明、方法返回类型声明，以及数据类型的转换等，而不要用具体类来做这些事情。为了确保该原则的应用，一个具体类应当只实现接口或抽象类中声明过的方法，而不要给出多余的方法，否则将无法调用到在子类中增加的新方法。
在大多数情况下，这三个设计原则会同时出现，开闭原则是目标，里氏代换原则是基础，依赖倒转原则是手段，它们相辅相成，相互补充，目标一致，只是分析问题时所站角度不同而已。

接口隔离原则(Interface  Segregation Principle, ISP)：使用多个专门的接口，而不使用单一的总接口，即客户端不应该依赖那些它不需要的接口.
 在使用接口隔离原则时，我们需要注意控制接口的粒度，接口不能太小，如果太小会导致系统中接口泛滥，不利于维护；接口也不能太大，太大的接口将违背接口隔离原则，灵活性较差，使用起来很不方便。一般而言，接口中仅包含为某一类用户定制的方法即可，不应该强迫客户依赖于那些它们不用的方法。

迪米特法则(Law of  Demeter, LoD)：一个软件实体应当尽可能少地与其他实体发生相互作用。迪米特法则又称为最少知识原则(LeastKnowledge Principle, LKP)
迪米特法则(Law of  Demeter, LoD)：一个软件实体应当尽可能少地与其他实体发生相互作用。

* 设计模式适用场景整理
https://blog.csdn.net/qq_34244317/article/details/77808913

* spring用到了哪些设计模式
https://www.cnblogs.com/yuefan/p/3763898.html

* MyBatis用到了哪些设计模式

## 网络/IO基础
* BIO与NIO、AIO的区别
https://blog.csdn.net/skiof007/article/details/52873421
https://www.cnblogs.com/ygj0930/p/6543960.html


## 数据存储于消息队列

* MySQL索引使用的注意事项
* 事务的隔离级别（Read uncommitted 、Read committed 、Repeatable read 、Serializable ）
https://blog.csdn.net/qq_33290787/article/details/51924963

大多数数据库默认的事务隔离级别是Read committed，比如Sql Server , Oracle。Mysql的默认隔离级别是Repeatable read。

* 脏读、幻读、不可重复读
* 数据库的几大范式
其实就是设计表的原则
https://www.cnblogs.com/waj6511988/p/7027127.html
https://www.cnblogs.com/knowledgesea/p/3667395.html


































