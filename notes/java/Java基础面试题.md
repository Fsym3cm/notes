### Java中堆和栈有什么不同？

每个线程都有自己的栈内存，用于存储本地变量，方法参数和栈调用，一个线程中存储的变量对其它线程是不可见的。而堆是所有线程共享的一片公用内存区域。对象都在堆里创建，为了提升效率线程会从堆中弄一个缓存到自己的栈，如果多个线程使用该变量就可能引发问题，这时volatile 变量就可以发挥作用了，它要求线程从主存中读取变量的值。


堆：（对象）

引用类型的变量，其内存分配在堆上或者常量池（字符串常量、基本数据类型常量），需要通过new等方式来创建。堆内存主要作用是存放运行时创建(new)的对象。

（主要用于存放对象，存取速度慢，可以运行时动态分配内存，生存期不需要提前确定）


栈：（基本数据类型变量、对象的引用变量）

基本数据类型的变量（int、short、long、byte、float、double、boolean、char等）以及对象的引用变量，其内存分配在栈上，变量出了作用域就会自动释放。

### 构造器（constructor）是否可被重写（override）？

构造器不能被继承，因此不能被重写，但可以被重载。

### 描述一下JVM加载class文件的原理机制

JVM中类的装载是由类加载器（`ClassLoader`）和它的子类来实现的，Java中的类加载器是一个重要的Java运行时系统组件，它负责在运行时查找和装入类文件中的类。类的加载是指把类的.class文件中的数据读入到内存中，通常是创建一个字节数组读入.class文件

### Collection和Collections的区别？

Collection是一个接口，它是Set、List等容器的父接口；Collections是个一个工具类，提供了一系列的静态方法来辅助容器操作，这些方法包括对容器的搜索、排序、线程安全化等等。

###  一个".java"源文件中是否可以包括多个类（不是内部类）？有什么限制？ 

这个是可以的，一个“.java”源文件里面可以包含多个类，但是只允许有一个public类，并且类名必须和文件名一致。

每个编译单元只能有一个public 类。这么做的意思是，每个编译单元只能有一个公开的接口，而这个接口就由其public 类来表示。

你可以根据需要，往这个文件里面添加任意多个提供辅助功能的package 权限的类。但是如果这个编译单元里面有两个或两个以上的public 类的话，程序就不知道从哪里导入了，编译器就会报错。　　

