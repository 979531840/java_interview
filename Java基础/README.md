# Java基础

### 1、Java的四个基本特征（抽象、封装、继承、多态），对多态的理解。以及项目中哪里用到了多态。

* 抽象-就是把客观事物抽象出来。一般称为类或者接口。分为两部分，一种是数据抽象，就是对象的属性。另一种是过程的抽象，就是对象的行为特征。比如鸟这样一个类，属性可以抽象为翅膀、脚、羽毛等。过程抽象例如鸟飞，鸟叫等。

* 封装-封装是面向对象的核心思维。把对象的属性和行为封装起来。客观的事务封装成抽象的类。例如鸟类抽象成数据和过程后，把两个封装起来为一个对象。

* 继承-描述类与类之间的关系，允许和鼓励类的重用。继承是为了重用父类的代码，为实现多态性做准备。

* 多态-同一个事件发生在不同的对象上会产生不同的结果。实现多态的技术称为 `动态绑定`。多态的作用：`消除类型之间的耦合关系`。

举例子：老师和同学分别登录教务系统，但是进入的页面是不一样的。他们有相同的方法Login，但是登录的时候有不同的操作。两种角色继承了父类的方法，但是都有具体的实现。

* 多态存在的三个必要条件
	* 一、要有继承
	* 二、要有重写
	* 三、父类引用指向子类对象

* 多态实现的两种方式
	* 重载(Overload) 实现的是编译时的多态性（前绑定）
	* 重写(Override)  实现的是运行时的多态性（后绑定）

* 重载（Overload）和重写（Override）的区别： 
	* 重载就是同一个类中，有多个方法名相同，但参数列表不同（包括参数个数和参数类型），与返回值无关，与权限修饰符也无关。调用重载的方法时通过传递给它们不同的参数个数和参数类型来决定具体使用哪个方法。 
	* 重写就是子类重写基类（父类）的方法，方法名，参数列表和返回值都必须相同，否则就不是重写而是重载。权限修饰符不能小于被重写方法的修饰符。重写方法不能抛出新的异常或者是比被重写方法声明更加宽泛的检查型异常。

* 方法的重写Override要遵循“两同两小一大”规则：
	* 一、“两同”即方法名相同，形参列表相同
	* 二、“两小”指的是子类方法返回值类型应比父类方法返回值类型更小或相等，子类方法声明抛出的异常类应比父类方法声明抛出的异常类更小或相等
	* 三、“一大”指的是子类方法的访问权限应比父类方法的访问权限更大或相等

		注：构造方法不受以上规则约束。

* 方法的重载Overload要注意以下的几点：
	* 一、在使用重载时只能通过不同的参数样式。例如，不同的参数类型，不同的参数个数，不同的参数顺序
	* 二、不能通过访问权限、返回类型和抛出异常的差异进行重载
	* 三、方法的异常类型和数目不会对重载造成影响

* 重载（Overload）：只要方法名一致，其他（参数列表、返回值）怎么折腾随便。

* 重写（Overriding）：只有实现的功能代码不一致，其他的（函数名、参数列表、返回值类型）必须都一致。

### 2、Java中的数据类型分类。

* 基本数据类型（或叫做原生类、内置类型）8种：
* 整数：byte，short，int，long（默认是int类型）
* 浮点类型： float，double（默认是double类型）
* 字符类型：char
* 布尔类型：boolean

* 引用数据类型3种：数组，类，接口
* 其中，基本数据类型之间除了boolean，其他数据类型之间可以任意的相互转换

* byte的取值范围为-128~127，占用1个字节（-2的7次方到2的7次方-1）
* short的取值范围为-32768~32767，占用2个字节（-2的15次方到2的15次方-1）
* int的取值范围为（-2147483648~2147483647），占用4个字节（-2的31次方到2的31次方-1）
* long的取值范围为（-9223372036854774808~9223372036854774807），占用8个字节（-2的63次方到2的63次方-1）
* 浮点型 float和double是表示浮点型的数据类型，他们之间的区别在于他们的精确度不同 float 3.402823e+38~ 1.401298e-45（e+38表示是乘以10的38次方，同样，e-45表示乘以10的负45次方）占用4个字节 double 1.797693e+308~4.9000000e-324 占用8个字节 double型比float型存储范围更大，精度更高
* char型（文本型） 用于存放字符的数据类型，占用2个字节，采用unicode编码，它的前128字节编码与ASCII兼容 字符的存储范围在\u0000~\uFFFF

### 3、面向过程和面向对象的区别。
	面向过程 是一件事 `怎么做` 具体到细节
	面向对象 是一件事 `谁来做` `谁`就是对象 他怎么做我不关心
* 例如 对于人吃东西来说 用面向过程 就是人 张开嘴 然后把东西放到嘴里 然后合上嘴 然后咀嚼 然后再挖一勺 用面向对象 就是 人 他有一个方法叫吃 至于怎么吃 细节实现 我不管 我直接调用就好

### 4、面向对象开发的（OOP）六个基本原则（单一职责、开放封闭、里氏替换、依赖倒置、迪米特法则、接口隔离），合成聚合复用。在项目中用过哪些原则。
* 六个基本原则
	* 单一职责 
		* 定义：一个类只负责一项职责。（高内聚、低耦合）
		* 一、可以降低类的复杂度。一个类只负责一项职责，逻辑简单。
		* 二、可以提高类的可读性，提高系统可维护性。
		* 三、降低变更引起的风险。
	* 开放封闭（开闭原则）
		* 定义：一个软件实体如类、模块和函数应该对扩展开放，对修改关闭。
	* 里氏替换
		* 定义：子类可以扩展父类的功能，但不能改变父类原有的功能。尽量不要重写父类的方法，也尽量不要重载父类的方法。
	* 依赖倒置
		* 定义：高层模块不应该依赖低层模块，二者都应该依赖其抽象；抽象不应该依赖细节；细节应该依赖抽象。
	* 迪米特法则
		* 定义：一个对象应该对其他对象保持最少的了解。尽量降低类与类之间的耦合。（不要与陌生人说话）
	* 接口隔离
		* 定义：客户端不应该依赖它不需要的接口；一个类对另一个类的依赖应该建立在最小的接口上。
	* 合成聚合复用
		* 定义：要尽量使用合成和聚合，尽量不要使用继承。就是在一个新的对象里面使用一些已有的对象，使之成为新对象的一部分，新对象通过向这些对象的委派达到复用已有功能的目的。

* 抽象、单一职责、高内聚、低耦合

### 5、static和final的区别和用途。
* static：表示静态或者全局，可以修饰属性、方法、代码块，静态属性和静态方法是属于类的（也可以说是属于类的所有对象的），可以用类名.静态属性/静态方法来访问，用static修饰的代码块是静态代码块，当虚拟机（JVM）加载该类时，就会执行静态代码块。 
* 修饰属性：当static修饰属性时，该属性称为静态变量或者类变量，该变量是在JVM加载类时初始化的；不被static修饰的属性是实例变量，在创建对象时被初始化，实例变量是各个对象独有的。使用一个类的静态变量并不会触发该类的加载。
* 修饰方法：被static修饰的方法称为类方法或者静态方法，一般通过类名调用。静态方法中不能使用this、super关键字，也不能访问实例变量和实例方法，只能访问静态变量和静态方法。父子类中，静态方法只能被静态方法覆盖，非静态方法只能被非静态方法覆盖。
* 修饰代码块：被static修饰的代码块被称为静态代码块，和代码块和属性以及方法是同一个等级的成员，可以有多个，位置可以随便放。JVM加载类时会执行这些静态代码块，如果static代码块有多个，JVM将按照它们在类中出现的先后顺序依次执行它们，每个代码块只会被执行一次。

* final：表示常量、最终，final可以修饰变量、方法、类。final修饰的局部变量为常量，一旦赋值不能修改。final修饰的成员变量必须在声明时赋值，或者在构造函数中，或者在代码块中赋初值，一旦赋值不能更改。final方法不能被子类重写。final类不能被继承，没有子类，final类中的方法默认是final的。final不能修饰构造方法。java中的String、Math等类就是final的。 
* 修饰变量：final修饰的局部变量为常量，一旦赋值不能修改。final修饰的成员变量必须在声明时赋值，或者在构造函数中，或者在代码块中赋初值，一旦赋值不能更改。如果final修饰的是对象引用，则引用不可变，引用的对象可以改变。
* 修饰方法：final修饰的方法不能被子类重写。
* 修饰类：final修饰的类不能被继承。

### 6、String、StringBuffer、StringBuilder的区别？对String不变性的理解。
* 都是final类，不能被继承。
* String 字符串常量。长度不可变。String final char[]。
* StringBuffer 字符串变量（线程安全）（synchronized）长度可变。
* StringBuilder 字符串变量（非线程安全）。长度可变。

* 对于String不变性的理解
	* String不能被继承。
	* String的+号链接可以创建新的字符串。
	* String a = new String("hahah")；可能会创建两个对象可能创建一个。如果常量池没有的话会在常量池创建一个新的对象。
	* Java的+号，底层使用StringBuilder的append来实现的。


### 7、String有重写Object的hashcode和toString方法吗？如果重新equals不重写hashcode会出现什么问题？

* Object的toString方法源码如下：

```
public String toString() {
    return getClass().getName() + "@" + Integer.toHexString(hashCode());
}
```

* String的toString方法源码如下：
```
public String toString() {
    return this;
}
```

* 两个都需要重写。因为要满足以下三个条件。
	* 两个String，equals方法返回true，hashcode方法一定是true。
	* 两个String，equals方法返回false，hashcode方法一定是false。
	* 两个String，hashcode方法返回false，equals方法不一定是false。

* 如果不重写hashcode方法会出现什么问题？
	* 在存储hashMap的时候，如果原对象equals新对象，但是hashCode没有重写。则两个对象拥有了不同的hashCode，会在集合中存储两个值相同的对象，导致混淆。所以两个必须同时重写。
### 8、Java如何序列化，如何实现序列化和反序列化，常见的序列化协议有哪些？
* Java序列化定义
	* 将那些实现了Serializable接口的对象转换成一个字节序列，并能在以后将这个字节序列完全恢复成原来的对象，序列化可以弥补操作系统之间的差异。

* 如何实现序列化和反序列化
	* 实现序列化
	* 1、实现java.io.Serializable接口，就可实现序列化。
	* 2、通过ObjectOutputStream和ObjectInputStream就可以对对象进行序列化和反序列化。
	* 3、虚拟机是否允许反序列化，取决于（private static final long serialVersionUID）
	* 4、序列化不保存静态变量
	* 5、要想将父类对象也序列化，就需要让父类也实现Serializable 接口。
	* 6、Transient 关键字控制变量的序列化。在变量名上加该关键字，可以阻止该变量序列化到文件，反序列化后，变量设为初始值，int为0，对象为null。

	* `在序列化过程中，如果被序列化的类中定义了writeObject 和 readObject 方法，虚拟机会试图调用对象类里的 writeObject 和 readObject 方法，进行用户自定义的序列化和反序列化。`

* 常见的序列化协议：XML，JSON。

### 9、常见异常分为哪两种？常见异常的基类以及常见的异常？

* Java中有两种异常：受检查的异常(checked)和不受检查的异常(unchecked)。
	* 不受检查的异常不需要在方法或者构造函数上声明，就算方法或者构造函数的声明可能会抛出这样的异常。 
	* 受检查的异常必须要用throws抛出异常。

	![图片](http://img.blog.csdn.net/20140825105709593?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaHVodWlfY3M=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)


常见的异常，NullPointerException,ClassNotFoundException,FileNotFoundException,ArrayIndexOutOfBoundsException 

### 10、Java中的NIO、BIO、AIO分别是什么？
* 网络编程的基本模型是C/S模型，即两个进程间的通信。
	* 传统的同步阻塞模型开发中，ServerSocket负责绑定IP地址，启动监听端口；Socket负责发起连接操作。连接成功后，双方通过输入和输出流进行同步阻塞式通信。 
	* 简单的描述一下BIO的服务端通信模型：采用BIO通信模型的服务端，通常由一个独立的Acceptor线程负责监听客户端的连接，它接收到客户端连接请求之后为每个客户端创建一个新的线程进行链路处理每处理完成后，通过输出流返回应答给客户端，线程销毁。即典型的一请求一应答通宵模型。
	* 为了改进这种一连接一线程的模型，我们可以使用线程池来管理这些线程（需要了解更多请参考前面提供的文章），实现1个或多个线程处理N个客户端的模型（但是底层还是使用的同步阻塞I/O），通常被称为"伪异步I/O模型"。


*  NIO我们一般认为是New I/O（也是官方的叫法），因为它是相对于老的I/O类库新增的（其实在JDK 1.4中就已经被引入了，但这个名词还会继续用很久，即使它们在现在看来已经是“旧”的了，所以也提示我们在命名时，需要好好考虑），做了很大的改变。但民间跟多人称之为Non-block I/O，即非阻塞I/O，因为这样叫，更能体现它的特点。而下文中的NIO，不是指整个新的I/O库，而是非阻塞I/O。

    * NIO提供了与传统BIO模型中的Socket和ServerSocket相对应的SocketChannel和ServerSocketChannel两种不同的套接字通道实现。

    新增的着两种通道都支持阻塞和非阻塞两种模式。

    阻塞模式使用就像传统中的支持一样，比较简单，但是性能和可靠性都不好；非阻塞模式正好与之相反。

    对于低负载、低并发的应用程序，可以使用同步阻塞I/O来提升开发速率和更好的维护性；对于高负载、高并发的（网络）应用，应使用NIO的非阻塞模式来开发。


    *  Buffer是一个对象，包含一些要写入或者读出的数据。

    在NIO库中，所有数据都是用缓冲区处理的。在读取数据时，它是直接读到缓冲区中的；在写入数据时，也是写入到缓冲区中。任何时候访问NIO中的数据，都是通过缓冲区进行操作。

    缓冲区实际上是一个数组，并提供了对数据结构化访问以及维护读写位置等信息。

    具体的缓存区有这些：ByteBuffe、CharBuffer、 ShortBuffer、IntBuffer、LongBuffer、FloatBuffer、DoubleBuffer。他们实现了相同的接口：Buffer。


    * 我们对数据的读取和写入要通过Channel，它就像水管一样，是一个通道。通道不同于流的地方就是通道是双向的，可以用于读、写和同时读写操作。

    底层的操作系统的通道一般都是全双工的，所以全双工的Channel比流能更好的映射底层操作系统的API。

    Channel主要分两大类：

    SelectableChannel：用户网络读写
    FileChannel：用于文件操作


    * Selector是Java  NIO 编程的基础。

    Selector提供选择已经就绪的任务的能力：Selector会不断轮询注册在其上的Channel，如果某个Channel上面发生读或者写事件，这个Channel就处于就绪状态，会被Selector轮询出来，然后通过SelectionKey可以获取就绪Channel的集合，进行后续的I/O操作。

    一个Selector可以同时轮询多个Channel，因为JDK使用了epoll()代替传统的select实现，所以没有最大连接句柄1024/2048的限制。所以，只需要一个线程负责Selector的轮询，就可以接入成千上万的客户端。

* AIO
	*  NIO 2.0引入了新的异步通道的概念，并提供了异步文件通道和异步套接字通道的实现。
	* 异步的套接字通道时真正的异步非阻塞I/O，对应于UNIX网络编程中的事件驱动I/O（AIO）。他不需要过多的Selector对注册的通道进行轮询即可实现异步读写，从而简化了NIO的编程模型。


* 同步阻塞IO（JAVA BIO）： 
    同步并阻塞，服务器实现模式为一个连接一个线程，即客户端有连接请求时服务器端就需要启动一个线程进行处理，如果这个连接不做任何事情会造成不必要的线程开销，当然可以通过线程池机制改善。 

* 同步非阻塞IO(Java NIO) ： 
	同步非阻塞，服务器实现模式为一个请求一个线程，即客户端发送的连接请求都会注册到多路复用器上，多路复用器轮询到连接有I/O请求时才启动一个线程进行处理。用户进程也需要时不时的询问IO操作是否就绪，这就要求用户进程不停的去询问。 

* 异步阻塞IO（Java NIO）：  
   此种方式下是指应用发起一个IO操作以后，不等待内核IO操作的完成，等内核完成IO操作以后会通知应用程序，这其实就是同步和异步最关键的区别，同步必须等待或者主动的去询问IO是否完成，那么为什么说是阻塞的呢？因为此时是通过select系统调用来完成的，而select函数本身的实现方式是阻塞的，而采用select函数有个好处就是它可以同时监听多个文件句柄（如果从UNP的角度看，select属于同步操作。因为select之后，进程还需要读写数据），从而提高系统的并发性！  


* （Java AIO(NIO.2)）异步非阻塞IO:  
   在此种模式下，用户进程只需要发起一个IO操作然后立即返回，等IO操作真正的完成以后，应用程序会得到IO操作完成的通知，此时用户进程只需要对数据进行处理就好了，不需要进行实际的IO读写操作，因为真正的IO读取或者写入操作已经由内核完成了。    

### 11、什么是匿名内部类？如何访问在其外面定义的变量？

* 匿名内部类也就是没有名字的内部类,正因为没有名字，所以匿名内部类只能使用一次，它通常用来简化代码编写。

	* 1、使用匿名内部类时，我们必须是继承一个类或者实现一个接口，但是两者不可兼得，同时也只能继承一个类或者实现一个接口。
    * 2、匿名内部类中是不能定义构造函数。
    * 3、匿名内部类中不能存在任何的静态成员变量和静态方法。
    * 4、匿名内部类为局部内部类，所以局部内部类的所有限制同样对匿名内部类生效。

* 最常用的情况就是在多线程的实现上，因为要实现多线程必须继承Thread类或是继承Runnable接口。

### 12、Servlet的生存周期。
* Servlet 通过调用 init () 方法进行初始化。
* Servlet 调用 service() 方法来处理客户端的请求。
* Servlet 通过调用 destroy() 方法终止（结束）。
* 最后，Servlet 是由 JVM 的垃圾回收器进行垃圾回收的。

### 13、Jsp和Servlet的区别？

* 最简单的理解。Jsp就是html中可以写Java代码。Servlet就是Java中可以写html代码。

### 14、你知道的开源协议有哪些？

* BSD、Apache、GPL、LGPL。

### 15、你知道的开源软件有哪些？

* Apache、Nginx、Mysql、Wordpress。

### 16、对于高负载、集群、高并发、分布式、集群、消息队列的了解。

	* 高负载 等待磁盘I/O完成的进程过多，导致进程队列长度过大，但是cpu运行的进程却很少，这样就体现到负载过大了，cpu使用率低。
	* 高并发 是互联网分布式系统架构设计中必须考虑的因素之一，它通常是指，通过设计保证系统能够同时并行处理很多请求。
	* 分布式 一个业务分拆多个子业务，部署在不同的服务器上。
	* 集群 同一个业务，部署在多个服务器上。
	* 消息队列 使用降低了系统间耦合度，避免了大量请求的同时涌入导致系统崩溃，起到了削峰填谷的作用。

### 17、object类你知道的方法。

* toString, hashCode，wait，notify，notifyAll。

* wait
	* public final void wait() throws InterruptedException,IllegalMonitorStateException

	* 方法必须在同步方法或者同步块里面进行调用，在调用前，需要获得该对象的对象级别锁。如果在调用wait方法时没有获得锁，则会抛出IllegalMonitorStateException异常，是RuntimeException的之类。

	在进入wait方法后，当前线程释放锁，进入阻塞状态，在从wait方法返回之前，线程会与其他线程竞争重新获得锁，

* notify
	* public final native void notify() throws IllegalMonitorStateException
	* 方法必须在同步方法或者同步块里面进行调用，在调用前，需要获得该对象的对象级别锁。如果在调用notify方法时没有获得锁，则会抛出IllegalMonitorStateException异常，是RuntimeException的之类。

	* 该方法用来通知那些等待唤醒的线程。如果有多个线程等待唤醒，则从线程规划器中（我认为是栈）选取一个线程进行唤醒，当前线程也不会马上释放该对象锁，需要等待当前的同步代码块执行完毕，当前线程释放锁，其他线程才能获得锁，才能从wait方法进行返回，其他线程继续阻塞，等待其他的线程发出notify或者notifyAll。他们等待的是notify或者notifyAll，而不是锁。一个线程被唤醒，才会等待锁，获得锁才可以继续执行。

* notifyAll
	* public final native void notifyAll() throws IllegalMonitorStateException
	* notifyAll使所有的原来在wait的线程全部退出wait状态，全部被唤醒，但是还没有获得锁，所以不能继续执行。变成等待获取该对象上的锁，一旦该对象锁被释放，他们就会去竞争。一个对象获得锁后就回去继续执行，直到他退出synchronized代码块，其他已经被唤醒的线程会继续竞争该锁，然后直到都有的线程都执行完毕。

* 深入理解
	* 在Java中，每个对象都有两个池，锁(monitor)池和等待池。

	* 如果线程调用了该对象的wait方法，那么线程进入该对象等待池，等待池中的线程不会去竞争该对象的锁。
	
	* 锁池:假设线程A已经拥有了某个对象(注意:不是类)的锁，而其它的线程想要调用这个对象的某个synchronized方法(或者synchronized块)，由于这些线程在进入对象的synchronized方法之前必须先获得该对象的锁的拥有权，但是该对象的锁目前正被线程A拥有，所以这些线程就进入了该对象的锁池中。

	* 等待池:假设一个线程A调用了某个对象的wait()方法，线程A就会释放该对象的锁(因为wait()方法必须出现在synchronized中，这样自然在执行wait()方法之前线程A就已经拥有了该对象的锁)，同时线程A就进入到了该对象的等待池中。如果另外的一个线程调用了相同对象的notifyAll()方法，那么处于该对象的等待池中的线程就会全部进入该对象的锁池中，准备争夺锁的拥有权。如果另外的一个线程调用了相同对象的notify()方法，那么仅仅有一个处于该对象的等待池中的线程(随机)会进入该对象的锁池.

### 18、Java的finalize，finally，final三个关键字的区别和应用场景。
* final：可用来定义变量、方法传入的参数、类、方法。
* finally：只能跟在try/catch语句中，并且附带一个语句块，表示最后执行。
* finalize：是垃圾回收器操作的运行机制中的一部分，进行垃圾回收器操作时会调用finalize方法，因为finalize方法是object的方法，所以每个类都有这个方法并且可以重写这个方法，在这个方法里实现释放系统资源及其他清理工作，JVM不保证此方法总被调用。

### 19、Tomcat服务器的原理，自己写一个tomcat服务器，你会怎么写。

* Tomcat
　|---bin：存放启动和关闭Tomcat脚本文件；
　|---conf：存放不同的配置文件（server.xml和web.xml）；
　|---lib：存放Tomcat运行需要的库文件（JARS）；
　|---logs：存放Tomcat执行时的日志文件；
　|---webapps：Tomcat的主要Web发布目录（包括应用程序示例）；

* Tomcat架构及常用的组件：
	server:
		1、port 指定一个端口，这个端口负责监听关闭tomcat的请求
    	2、shutdown 指定向端口发送的命令字符串

    service:          
    	1、name 指定service的名字 

    Connector (表示客户端和service之间的连接)：
          1、port指定服务器端要创建的端口号，并在这个断口监听来自客户端的请求
          2、minProcessors 服务器启动时创建的处理请求的线程数 
          3、maxProcessors 最大可以创建的处理请求的线程数 
          4、enableLookups 如果为true，则可以通过调用request.getRemoteHost()进行DNS查询来得到远程客户端的实际主机名，若为false则不进行DNS查询，而是返回其ip地址 
          5、redirectPort 指定服务器正在处理http请求时收到了一个SSL传输请求后重定向的端口号 
          6、acceptCount 指定当所有可以使用的处理请求的线程数都被使用时，可以放到处理队列中的请求数，超过这个数的请求将不予处理 
          7、connectionTimeout 指定超时的时间数(以毫秒为单位) 

    Engine(表示指定service中的请求处理机，接收和处理来自Connector的请求)：
          1、defaultHost 指定缺省的处理请求的主机名，它至少与其中的一个host元素的name属性值是一样的 
    Context (表示一个web应用程序)：
          1、docBase 应用程序的路径或者是WAR文件存放的路径 
          2、path 表示此web应用程序的url的前缀，这样请求的url为http://localhost:8080/path/**** 
          3、reloadable 这个属性非常重要，如果为true，则tomcat会自动检测应用程序的/WEB-INF/lib 和/WEB-INF/classes目录的变化，自动装载新的应用程序，我们可以在不重起tomcat的情况下改变应用程序 
    
    host (表示一个虚拟主机)：
          1、name 指定主机名 
          2、appBase 应用程序基本目录，即存放应用程序的目录 
          3、unpackWARs 如果为true，则tomcat会自动将WAR文件解压，否则不解压，直接

	定义连接器可以使用多种属性，有些属性也只适用于某特定的连接器类型。一般说来，常见于server.xml中的连接器类型通常有4种：
	1) HTTP连接器 2) SSL连接器 3) AJP 1.3连接器 4) proxy连接器

	以下为常用属性的说明：
	1) address：指定连接器监听的地址，默认为所有地址，即0.0.0.0； 可以自己指定的，如
	2) maxThreads：支持的最大并发连接数，默认为200；
	3) port：监听的端口，默认为0；
	4) protocol：连接器使用的协议，默认为HTTP/1.1，定义AJP协议时通常为AJP/1.3；
	5) redirectPort：如果某连接器支持的协议是HTTP，当接收客户端发来的HTTPS请求时，则转发至此属性定义的端口；
	6) connectionTimeout：等待客户端发送请求的超时时间，单位为毫秒，默认为60000，即1分钟；
	7) enableLookups：是否通过request.getRemoteHost()进行DNS查询以获取客户端的主机名；默认为true； 进行反解的，可以设置为false
	8) acceptCount：设置等待队列的最大长度；通常在tomcat所有处理线程均处于繁忙状态时，新发来的请求将被放置于等待队列中；

* Tomcat Server处理一个HTTP请求的过程
	创建了一个HttpServer对象，并调用了该对象的await方法。看名字，该方法应该是等待http请求之类的东东。我们来看看方法内部.创建了一个Socket服务器，并循环阻塞监听http请求，当有http请求到来时， 该方法便创建一个Request对象，构造参数是socket获取的输入流对象， 用于读取客户端请求的数据并解析。 然后再创建一个Response对象，构造参数是socket的输出流对象， 并含有一个Request对象的成员变量。Response对象用于将静态页面发送给浏览器或者是其他的客户端。最后， 该方法校验请求中是否含有关闭命令的字符串，如果有，就停止服务器的运行。我们继续看看Request 是如何解析Http请求的吧。Request 类代表一个 HTTP 请求。从负责与客户端通信的 Socket 中传递过来 InputStream 对象来构造这个类的一个实例。你调用 InputStream 对象其中一个 read 方法来获 取 HTTP 请求的原始数据。其中最主要的方法就是parse 和 parseUri ，他们用于逐个解析每个从客户端传递过来的字节，我们先看parse方法：我们也看到该方法是十分的简单， 创建一个StringBuffer 对象，然后从流中读取字节，然后循环将字节转成字符写入到Stringbuffer对象中。最后传入到parseUri方法中进行解析。我们总结一下Request类，这个类其实就是解析HTTP 消息头内容的，先将流中数据转成字节，然后将转成字符，最后将字符解析，得到自己感兴趣的内容。奏是这么简单。好了，我们再看看Response类。看看他是怎么实现的。可以看到，该方法也非常的简单， sendStaticResource 方法是用来发送一个静态资源，例如一个 HTML 文件。它首先通过传递 上一级目录的路径和子路径给 File 累的构造方法来实例化 java.io.File 类。然后它检查该文件是否存在。假如存在的话，通过传递 File 对象让 sendStaticResource 构造一个 java.io.FileInputStream 对象。然后，它调用 FileInputStream 的 read 方法并把字 节数组写入 OutputStream 对象。请注意，这种情况下，静态资源是作为原始数据发送给浏览器的。假如文件并不存在，sendStaticResource 方法发送一个错误信息到浏览器。


	1、用户点击网页内容，请求被发送到本机端口8080，被在那里监听的Coyote HTTP/1.1 Connector获得。 2、Connector把该请求交给它所在的Service的Engine来处理，并等待Engine的回应。 3、Engine获得请求localhost/test/index.jsp，匹配所有的虚拟主机Host。 4、Engine匹配到名为localhost的Host（即使匹配不到也把请求交给该Host处理，因为该Host被定义为该Engine的默认主机），名为localhost的Host获得请求/test/index.jsp，匹配它所拥有的所有的Context。Host匹配到路径为/test的Context（如果匹配不到就把该请求交给路径名为“ ”的Context去处理）。 5、path=“/test”的Context获得请求/index.jsp，在它的mapping table中寻找出对应的Servlet。Context匹配到URL PATTERN为*.jsp的Servlet,对应于JspServlet类。 6、构造HttpServletRequest对象和HttpServletResponse对象，作为参数调用JspServlet的doGet（）或doPost（）.执行业务逻辑、数据存储等程序。 7、Context把执行完之后的HttpServletResponse对象返回给Host。 8、Host把HttpServletResponse对象返回给Engine。 9、Engine把HttpServletResponse对象返回Connector。 10、Connector把HttpServletResponse对象返回给客户Browser。

### 20、动态代理的实现方式和区别。

 * 代理模式是一种设计模式，提供了对目标对象额外的访问方式，即通过代理对象访问目标对象，这样可以在不修改原目标对象的前提下，提供额外的功能操作，扩展目标对象的功能。
 * 举个例子，我们生活中经常到火车站去买车票，但是人一多的话，就会非常拥挤，于是就有了代售点，我们能从代售点买车票了。这其中就是代理模式的体现，代售点代理了火车站对象，提供购买车票的方法。

* 静态代理
	这种代理方式需要代理对象和目标对象实现一样的接口。
	优点：
		可以在不修改目标对象的前提下扩展目标对象的功能。
	缺点：
		冗余。由于代理对象要实现与目标对象一致的接口，会产生过多的代理类。
		不易维护。一旦接口增加方法，目标对象与代理对象都要进行修改。

* 动态代理
	动态代理利用了JDK API，动态地在内存中构建代理对象，从而实现对目标对象的代理功能。动态代理又被称为JDK代理或接口代理。

	* 静态代理与动态代理的区别主要在：
		静态代理在编译时就已经实现，编译完成后代理类是一个实际的class文件。
		动态代理是在运行时动态生成的，即编译完成后没有实际的class文件，而是在运行时动态生成类字节码，并加载到JVM中
		特点：
		动态代理对象不需要实现接口，但是要求目标对象必须实现接口，否则不能使用动态代理。

* cglib
	cglib (Code Generation Library )是一个第三方代码生成类库，运行时在内存中动态生成一个子类对象从而实现对目标对象功能的扩展。

	cglib特点

	JDK的动态代理有一个限制，就是使用动态代理的对象必须实现一个或多个接口。
	如果想代理没有实现接口的类，就可以使用CGLIB实现。
	CGLIB是一个强大的高性能的代码生成包，它可以在运行期扩展Java类与实现Java接口。
	它广泛的被许多AOP的框架使用，例如Spring AOP和dynaop，为他们提供方法的interception（拦截）。
	CGLIB包的底层是通过使用一个小而快的字节码处理框架ASM，来转换字节码并生成新的类。
	不鼓励直接使用ASM，因为它需要你对JVM内部结构包括class文件的格式和指令集都很熟悉。
	cglib与动态代理最大的区别就是

	使用动态代理的对象必须实现一个或多个接口
	使用cglib代理的对象则无需实现接口，达到代理类无侵入。

### 21、怎么实现负载均衡。
* 负载均衡是一种服务器或网络设备的集群技术。负载均衡将特定的业务(网络服务、网络流量等)分担给多个服务器或网络设备，从而提高了业务处理能力，保证了业务的高可用性。

HTTP重定向、DNS负载均衡，Nginx负载均衡等。

* HTTP重定向
 	* HTTP重定向服务器是一台普通的应用服务器，其唯一个功能就是根据用户的HTTP请求计算出一台真实的服务器地址，并将该服务器地址写入HTTP重定向响应中（重定向响应状态码为302）返回给用户浏览器。用户浏览器在获取到响应之后，根据返回的信息，重新发送一个请求到真实的服务器上。

 这种负载均衡方案的有点是比较简单，缺点是浏览器需要两次请求服务器才能完成一次访问，性能较差；同时，重定向服务器本身的处理能力有可能成为瓶颈，整个集群的伸缩性规模有限；使用HTTP返回码302重定向，有可能使搜索引擎判断为SEO作弊，降低搜索排名。因此实践中很少使用这种负载均衡方案来部署。

* DNS负载均衡
	* 利用域名解析实现负载均衡，在DNS服务器，配置多个A记录，这些A记录对应的服务器构成集群。大型网站总是部分使用DNS解析，作为第一级负载均衡。
 
 DNS（Domain Name System）是因特网的一项服务，它作为域名和IP地址相互映射的一个分布式数据库，能够使人更方便的访问互联网。人们在通过浏览器访问网站时只需要记住网站的域名即可，而不需要记住那些不太容易理解的IP地址。在DNS系统中有一个比较重要的的资源类型叫做主机记录也称为A记录，A记录是用于名称解析的重要记录，它将特定的主机名映射到对应主机的IP地址上。如果你有一个自己的域名，那么要想别人能访问到你的网站，你需要到特定的DNS解析服务商的服务器上填写A记录，过一段时间后，别人就能通过你的域名访问你的网站了。DNS除了能解析域名之外还具有负载均衡的功能。


	* DNS域名解析负载均衡有如下优点：
		* 1. 将负载均衡的工作交给DNS，省去了网站管理维护负载均衡服务器的麻烦。
		* 2. 技术实现比较灵活、方便，简单易行，成本低，使用于大多数TCP/IP应用。
		* 3. 对于部署在服务器上的应用来说不需要进行任何的代码修改即可实现不同机器上的应用访问。
		* 4. 服务器可以位于互联网的任意位置。
		* 5. 同时许多DNS还支持基于地理位置的域名解析，即会将域名解析成距离用户地理最近的一个服务器地址，这样就可以加速用户访问，改善性能。
		 
	* 同时，DNS域名解析也存在如下缺点：
		* 1. 目前的DNS是多级解析的，每一级DNS都可能缓存A记录，当某台服务器下线之后，即使修改了A记录，要使其生效也需要较长的时间，这段时间，DNS仍然会将域名解析到已下线的服务器上，最终导致用户访问失败。
		* 2. 不能够按服务器的处理能力来分配负载。DNS负载均衡采用的是简单的轮询算法，不能区分服务器之间的差异，不能反映服务器当前运行状态，所以其的负载均衡效果并不是太好。
		* 3. 可能会造成额外的网络问题。为了使本DNS服务器和其他DNS服务器及时交互，保证DNS数据及时更新，使地址能随机分配，一般都要将DNS的刷新时间设置的较小，但太小将会使DNS流量大增造成额外的网络问题。

* 事实上，大型网站总是部分使用DNS域名解析，利用域名解析作为第一级负载均衡手段，即域名解析得到的一组服务器并不是实际提供服务的物理服务器，而是同样提供负载均衡服务器的内部服务器，这组内部负载均衡服务器再进行负载均衡，请请求发到真实的服务器上，最终完成请求。

* 常用负载均衡算法通常有以下几种：

	* 轮询（Round Robin，RR）
		所有请求被一次分发到每台应用服务器上，即每台服务器需要处理的请求数目都相同，适合于素有服务器硬件都相同的场景。

	* 加权轮询（Weighted Round Robin，WRR）
		根据应用服务器硬件性能的 情况，在 轮询的基础上，按照配置的权重将请求分发到每个服务器，高性能的服务器能分配更多请求。

	* 随机（Random）
		请求被随机分配到各个应用服务器，在许多场合下，这种方案都很简单实用，因为好的随机数本身就很均衡。即使应用服务器硬件配置不同，也可以使用加权随机算法。

	* 最少连接（Least Connections）
		记录每个应用服务器正在处理额连接数（请求数），将新到的请求分发到最少连接的服务器上，应该说，这是最符合负载均衡定义的算法。同样，最少连接算法也可以实现加权最少连接。

	* 源地址散列（Source hashing）
		根据请求来源的IP地址进行Hash计算，得到应用服务器，这样来自同一个IP地址的请求总在同一个服务器上处理，该请求的上下文信息可以存储在这台服务器上，在一个会话周期内重复使用，从而实现会话黏滞。

* Nginx负载均衡

	* 内置负载策略
	Nginx负载均衡是通过upstream模块来实现的，内置实现了三种负载策略，配置还是比较简单的。

	轮询（默认） 
		Nginx根据请求次数，将每个请求均匀分配到每台服务器。

	最少连接 
		将请求分配给连接数最少的服务器。Nginx会统计哪些服务器的连接数最少。

	IP Hash 
		绑定处理请求的服务器。第一次请求时，根据该客户端的IP算出一个HASH值，将请求分配到集群中的某一台服务器上。后面该客户端的所有请求，都将通过HASH算法，找到之前处理这台客户端请求的服务器，然后将请求交给它来处理。

	* 第三方负载策略
	fair
		根据服务器的响应时间来分配请求，响应时间短的优先分配，即负载压力小的优先会分配。
		
### 22、Select，poll，epoll的区别。

[内容较多](https://blog.csdn.net/davidsguo008/article/details/73556811)

### 23、一致性hash算法

[内容较多](https://blog.csdn.net/cywosp/article/details/23397179)
