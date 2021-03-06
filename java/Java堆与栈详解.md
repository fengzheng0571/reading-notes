# Java堆与栈详解  
Java把内存分为两种，分别是堆与栈。Java自动管理栈与堆，程序员不能直接地设置栈或堆。

## 一、栈
>位于通用RAM（随机访问存储器）中，通过栈指针可以从处理器那里获得直接支持。栈指针若向下移动，则分配新的内存；若向上移动，则释放那些内存。这是一种快速有效的分配存储方法，仅次于寄存器。创建程序时，Java系统必须知道存储在栈内所有项的确切生命周期，以便上下移动栈指针。

特点：存取速度比堆快，仅次于寄存器。但缺点是，存在栈中的数据大小与生存期必须是确定的，缺乏灵活性。

**栈用于存放在方法中定义的基本类型变量（boolean, byte, char, short, int, long, float, double）和对象的引用变量**。
```
int i = 10;
String s;
```
当在一段代码块中定义一个基本类型变量时，Java就在栈中为该变量分配内存空间，当超过该变量的作用域后，Java会自动释放掉为该变量分配的内存空间，该内存空间可以立刻被另作他用。


## 二、堆
>一种通用的内存池（也位于RAM区），用于存储所有的Java对象。堆不同于栈的好处是：编译器不需要知道存储的数据在堆里存活多长时间。因此，在堆里分配存储有很大的灵活性。当然为这种灵活性必须要付出相应的代价：用堆进行存储分配和清理可能比用栈进行存储分配需要更多的时间。

特点：存储在堆中的数据大小、生存周期不必事先告诉编译器，因为它是在运行时动态分配的。但缺点是，由于要在运行时动态分配内存，存取速度较慢。

**堆用于存放由new关键字创建的对象和数组。**  
```
int[] arr = new int[10];
String s = new String("Hello World");
//arr和s都是引用变量
```
在堆中产生了一个数组后，同时可以在栈中定义一个变量，这个变量的取值等于对象在堆内存中的首地址，在栈中的这个变量就变成了对象的引用变量，后续可以在程序中使用栈内存中的引用变量来访问堆中的对象，引用变量相当于C中的指针。  
引用变量定义时在栈中分配内存，引用变量在程序运行到作用域外释放。而对象本身在堆中分配，即使程序运行到引用变量作用域之外，对象本身占用的堆内存也不会被释放，对象直到没有引用变量指向它的时候，才变成垃圾，但是仍然占着内存，在随后的一个不确定的时间被垃圾回收器释放掉。
