# 					常见Java基础面试题

##  Java基础知识

### Java语法与常识

#### Java语言的特点

1、面向对象（封装、继承、多态）

2、平台无关（由Java虚拟机实现）

3、编译与解释并存

其中关于面向对象的特点，**封装**是指把一个对象的状态信息（也就是属性）隐藏在对象内部，不允许外部对象直接访问对象的内部信息。**继承**指子类拥有父类的所有属性和方法并且可以对他们进行扩展（但是父类中的私有属性和方法子类是无法访问的，只是拥有）。**多态**表示一个对象具有多种的状态，具体表现为父类的引用指向子类的实例，如animals A=new dog()。

#### Java 和 C++ 的一些异同点

- Java 是纯粹的面向对象语言，所有的对象都继承自 java.lang.Object，C++ 为了兼容 C 即支持面向对象也支持面向过程。
- Java 通过虚拟机从而实现跨平台特性，但是 C++ 依赖于特定的平台。
- Java 没有指针，它的引用可以理解为安全指针，而 C++ 具有和 C 一样的指针。
- Java 支持自动垃圾回收，而 C++ 需要手动回收。
- Java 不支持多重继承，只能通过实现多个接口来达到相同目的，而 C++ 支持多重继承。
- Java 不支持操作符重载，虽然可以对两个 String 对象执行加法运算，但是这是语言内置支持的操作，不属于操作符重载，而 C++ 可以。
- Java 的 goto 是保留字，但是不可用，C++ 可以使用 goto。

####  JDK 、 JRE、JVM 之间的关系

JDK 是 Java Development Kit即Java开发元件的缩写，它拥有 JRE 所拥有的一切，还有编译器（javac）和工具（如 javadoc 和 jdb）。它能够创建和编译程序。

JRE 是 Java 运行时环境。它是运行已编译 Java 程序所需的所有内容的集合，包括 Java 虚拟机（JVM），Java 类库，java 命令和其他的一些基础构件。但是，它不能用于创建新程序。

JVM是运行 Java 字节码的虚拟机。JVM 有针对不同系统的特定实现（Windows，Linux，macOS），目的是使用相同的字节码，它们都会给出相同的结果。字节码和不同系统的 JVM 实现是 Java 语言“一次编译，随处可以运行”的关键所在。

#### 为什么说Java是编译与解释并存？其中字节码又是什么？

因为 Java 程序要经过编译和解释两个步骤。 Java 编写的程序首先需要经过编译，生成字节码（.class 文件），这种字节码由 Java 解释器来解释执行。这样Java就兼顾了编译型语言程序运行快而解释型语言程序性平台无关的优点。其中Java字节码被解释过程较慢的问题，因为引入JIT（just-in-time compilation）这种运行时编译器而得到了解决。这种编译器会在首次编译时保存字节码对应的机器码以便以后直接使用。

在 Java 中，JVM 可以理解的代码就叫做字节码（即扩展名为 .class 的文件），它不面向任何特定的处理器，只面向虚拟机。Java 语言使用字节码的这种方式，是解决传统解释型语言执行效率低的问题的同时保留了解释型语言可移植特点的关键。

#### 标识符和关键字的区别是什么？有哪些常见关键字？

标识符就是一个名字，比如程序、类、变量、方法等所取的名字即是标识符。

关键字是被赋予特殊含义的标识符 。Java语言中国已经赋予了特殊的含义、只能用于特定的情况的特殊标识符就是关键字 。

常见关键字如下：

| 分类                 | 关键字   |            |          |              |            |           |        |
| -------------------- | -------- | ---------- | -------- | ------------ | ---------- | --------- | ------ |
| 访问控制             | private  | protected  | public   |              |            |           |        |
| 类，方法和变量修饰符 | abstract | class      | extends  | final        | implements | interface | native |
|                      | new      | static     | strictfp | synchronized | transient  | volatile  | enum   |
| 程序控制             | break    | continue   | return   | do           | while      | if        | else   |
|                      | for      | instanceof | switch   | case         | default    | assert    |        |
| 错误处理             | try      | catch      | throw    | throws       | finally    |           |        |
| 包相关               | import   | package    |          |              |            |           |        |
| 基本类型             | boolean  | byte       | char     | double       | float      | int       | long   |
|                      | short    |            |          |              |            |           |        |
| 变量引用             | super    | this       | void     |              |            |           |        |
| 保留字               | goto     | const      |          |              |            |           |        |

注意 ：虽然 true, false, 和 null 看起来像关键字但实际上他们是字面值，它们也不可以作为标识符来使用。

#### final和static了解么？

##### final

**1. 修饰数据**

声明数据为常量，可以是编译时常量，也可以是在运行时被初始化后不能被改变的常量。

- 对于基本类型，final 使数值不变；
- 对于引用类型，final 使引用不变，也就不能引用其它对象，但是被引用的对象本身是可以修改的。

```java
final int x = 1;
// x = 2;  // cannot assign value to final variable 'x'
final A y = new A();
y.a = 1;
```

**2. 修饰方法**

声明方法不能被子类重写。

private 方法隐式地被指定为 final，如果在子类中定义的方法和基类中的一个 private 方法签名相同，此时子类的方法不是重写父类方法，而是在子类中定义了一个新的方法。

**3. 修饰类**

声明类不允许被继承。

##### static

只列举了几个常用的场景

**1. 修饰变量**

- 静态变量：使用static修饰的变量又称为类变量，也就是说这个变量属于类的，类所有的实例都共享静态变量，可以直接通过类名来访问它。静态变量在内存中只存在一份。
- （与静态变量相对的就是实例变量：每创建一个实例就会产生一个实例变量，它与该实例同生共死。）

```
public class A {

    private int x;         // 实例变量
    private static int y;  // 静态变量

    public static void main(String[] args) {
        // int x = A.x;  // Non-static field 'x' cannot be referenced from a static context
        A a = new A();
        int x = a.x;
        int y = A.y;
    }
}
```

**2. 修饰方法**

静态方法在类加载的时候就存在了，它不依赖于任何实例。所以静态方法必须有实现，也就是说它不能是抽象方法。

```
public abstract class A {
    public static void func1(){
    }
    // public abstract static void func2();  // Illegal combination of modifiers: 'abstract' and 'static'
}
```

只能访问所属类的静态字段和静态方法，方法中不能有 this 和 super 关键字，因为这两个关键字与具体对象关联。

```
public class A {

    private static int x;
    private int y;

    public static void func1(){
        int a = x;
        // int b = y;  // Non-static field 'y' cannot be referenced from a static context
        // int b = this.y;     // 'A.this' cannot be referenced from a static context
    }
}
```

**3. 修饰语句块**

使用static修饰的语句块称为静态语句块，它在类初始化时必定会运行一次。

```
public class A {
    static {
        System.out.println("123");
    }

    public static void main(String[] args) {
        A a1 = new A();
        A a2 = new A();
    }
}
```

#### 重载和重写有什么区别？

**重载**就是同样的一个方法能够根据输入数据的不同，做出不同的处理。

**重写**就是当子类继承自父类的相同方法，输入数据一样，但要做出有别于父类的响应时就要覆盖父类方法。

| 区别点     | 重载方法 | 重写方法                                                     |
| ---------- | -------- | ------------------------------------------------------------ |
| 发生范围   | 同一个类 | 子类                                                         |
| 参数列表   | 必须修改 | 一定不能修改                                                 |
| 返回类型   | 可修改   | 子类方法返回值类型应比父类方法返回值类型更小或相等           |
| 异常       | 可修改   | 子类方法声明抛出的异常类应比父类方法声明抛出的异常类更小或相等； |
| 访问修饰符 | 可修改   | 一定不能做更严格的限制（可以降低限制）                       |
| 发生阶段   | 编译期   | 运行期                                                       |

#### 对象实体与对象引用有何不同?

**对象实例**在堆内存中；**对象引用**指向对象实例，其存放在栈内存中。一个对象引用只能指向 0 个或 1 个对象，一个对象可以有多个引用指向它。

对象的相等一般比较的是内存中存放的内容是否相等。引用相等一般比较的是他们指向的内存地址是否相等。

#### 接口和抽象类有什么共同点和区别？

**共同点** ：

- 都不能被实例化。
- 都可以包含抽象方法。
- 都可以有默认实现的方法（Java 8 可以用 `default` 关键字在接口中定义默认方法）。

**区别** ：

- 接口主要用于对类的行为进行约束，你实现了某个接口就具有了对应的行为。抽象类主要用于代码复用，强调的是所属关系。
- 一个类只能继承一个类，但是可以实现多个接口。
- 接口中的成员变量只能是 `public static final` 类型的，不能被修改且必须有初始值，而抽象类的成员变量默认 default，可在子类中被重新定义，也可被重新赋值。

#### 深拷贝和浅拷贝区别了解吗？什么是引用拷贝？

- **浅拷贝**：浅拷贝会在堆上创建一个新的对象（区别于引用拷贝的一点），不过如果原对象内部的属性是引用类型的话，浅拷贝会直接复制内部对象的引用地址，也就是说拷贝对象和原对象共用同一个内部对象。也就是只拷贝对象而不拷贝该对象所引用的对象。
- **深拷贝** ：深拷贝会完全复制整个对象，包括这个对象所包含的内部对象，也就是既拷贝对象又拷贝该对象所引用的对象。
- **引用拷贝**：引用拷贝就是两个不同的引用指向同一个对象。

#### Java 中的几种基本数据类型？

Java 中有 8 种基本数据类型，分别为：

- 6 种数字类型：
  - 4 种整数型：`byte`、`short`、`int`、`long`
  - 2 种浮点型：`float`、`double`
- 1 种字符类型：`char`
- 1 种布尔型：`boolean`。

这 8 种基本数据类型的默认值以及所占空间的大小如下：

| 基本类型  | 位数 | 字节 | 默认值  | 取值范围                                   |
| --------- | ---- | ---- | ------- | ------------------------------------------ |
| `byte`    | 8    | 1    | 0       | -128 ~ 127                                 |
| `short`   | 16   | 2    | 0       | -32768 ~ 32767                             |
| `int`     | 32   | 4    | 0       | -2147483648 ~ 2147483647                   |
| `long`    | 64   | 8    | 0L      | -9223372036854775808 ~ 9223372036854775807 |
| `char`    | 16   | 2    | 'u0000' | 0 ~ 65535                                  |
| `float`   | 32   | 4    | 0f      | 1.4E-45 ~ 3.4028235E38                     |
| `double`  | 64   | 8    | 0d      | 4.9E-324 ~ 1.7976931348623157E308          |
| `boolean` | 1    |      | false   | true、false                                |

 这八种基本类型都有对应的包装类分别为：`Byte`、`Short`、`Integer`、`Long`、`Float`、`Double`、`Character`、`Boolean` 。基本类型与其对应的包装类型之间的赋值使用自动装箱与拆箱完成。

```java
Integer x = 2;     // 装箱原理是调用了 Integer.valueOf(2)
int y = x;         // 拆箱原理是调用了 X.intValue()
```

#### 基本数据类型与包装类型的区别

- 成员变量包装类型不赋值就是 `null` ，而基本类型有默认值且不是 `null`。
- 包装类型可用于泛型，而基本类型不可以。
- 基本数据类型的局部变量存放在 Java 虚拟机栈中的局部变量表中，基本数据类型的成员变量（未被 `static` 修饰 ）存放在 Java 虚拟机的堆中。包装类型属于对象类型，我们知道几乎所有对象实例都存在于堆中。
- 相比于对象类型， 基本数据类型占用的空间非常小。

#### 包装类型的缓存机制了解么

Java 基本数据类型的包装类型的大部分都用到了缓存机制来提升性能。

`Byte`,`Short`,`Integer`,`Long` 这 4 种包装类默认创建了数值 **[-128，127]** 的相应类型的缓存数据，`Character` 创建了数值在 **[0,127]** 范围的缓存数据，`Boolean` 直接返回 `True` or `False`。另外两种浮点型基本类型的包装类型`Float`、`Double`则没有设置缓存机制。

当使用new创建包装类型的对象时会创建一个新的对象，使用valueof()时若值在缓存范围内则取得同一个对象的引用。例如：

- new Integer(123) 每次都会新建一个对象
- Integer.valueOf(123) 会使用缓存池中的对象，多次调用会取得同一个对象的引用

#### 面对浮点运算丢失精度以及超过Long整型的数据时如何处理

前者使用BigDecimal 可以实现对浮点数的运算，不会造成精度丢失。通常情况下，大部分需要浮点数精确运算结果的业务场景（比如涉及到钱的场景）都是通过 BigDecimal 来做的。

后者可以使用BigInteger解决，其内部是使用 int[] 数组来存储任意大小整型数据的。不过相对于常规整数类型的运算来说，BigInteger 运算的效率会相对较低。

### Java常见类Object与String

#### Object 类的常见方法有哪些？

Object是所有类的顶层父类，它主要有以下的常见方法：

`getClass()`、`hashCode()`、`equals()`、`clone()`、`toString()`等。

```java
/**
 * native 方法，用于返回当前运行时对象的 Class 对象，使用了 final 关键字修饰，故不允许子类重写。
 */
public final native Class<?> getClass()
/**
 * native 方法，用于返回对象的哈希码，主要使用在哈希表中，比如 JDK 中的HashMap。
 */
public native int hashCode()
/**
 * 用于比较 2 个对象的内存地址是否相等，String 类对该方法进行了重写以用于比较字符串的值是否相等。
 */
public boolean equals(Object obj)
/**
 * naitive 方法，用于创建并返回当前对象的一份拷贝。
 */
protected native Object clone() throws CloneNotSupportedException
/**
 * 返回类的名字实例的哈希码的 16 进制的字符串。建议 Object 所有的子类都重写这个方法。
 */
public String toString()
/**
 * native 方法，并且不能重写。唤醒一个在此对象监视器上等待的线程(监视器相当于就是锁的概念)。如果有多个线程在等待只会任意唤醒一个。
 */
public final native void notify()
/**
 * native 方法，并且不能重写。跟 notify 一样，唯一的区别就是会唤醒在此对象监视器上等待的所有线程，而不是一个线程。
 */
public final native void notifyAll()
/**
 * native方法，并且不能重写。暂停线程的执行。注意：sleep 方法没有释放锁，而 wait 方法释放了锁 ，timeout 是等待时间。
 */
public final native void wait(long timeout) throws InterruptedException
/**
 * 多了 nanos 参数，这个参数表示额外时间（以毫微秒为单位，范围是 0-999999）。 所以超时的时间还需要加上 nanos 毫秒。。
 */
public final void wait(long timeout, int nanos) throws InterruptedException
/**
 * 跟之前的2个wait方法一样，只不过该方法一直等待，没有超时时间这个概念
 */
public final void wait() throws InterruptedException
/**
 * 实例被垃圾回收器回收的时候触发的操作
 */
protected void finalize() throws Throwable { }
```

#### == 和 equals() 的区别

**`==`** 对于基本类型和引用类型的作用效果是不同的：

- 对于基本数据类型来说，`==` 比较的是值。
- 对于引用数据类型来说，`==` 比较的是对象的内存地址。

`equals()` 方法存在两种使用情况：

- **类没有重写 `equals()`方法** ：通过`equals()`比较该类的两个对象时，等价于通过“==”比较这两个对象，使用的默认是 `Object`类的`equals()`方法。
- **类重写了 `equals()`方法** ：一般我们都重写 `equals()`方法来比较两个对象中的属性是否相等；若它们的属性相等，则返回 true(即，认为这两个对象相等)。

#### 为什么要有 hashCode()？为什么重写 equals() 时必须重写 hashCode() 方法？

hashCode() 的作用是获取哈希码（int 整数），这个哈希码的作用是确定该对象在哈希表中的索引位置。hashcode()与equals()一样都能用于比较两个对象是否相等。**hashcode()计算得hash码不同那么和equals()判断的结果一样都为不同，若hashcode()计算的hash码相同则equals()判断的结果可能相同也可能不同。**可见借此特点，hashcode()可以用来减少判断与查找的时间成本。

而重写 equals() 时必须重写 hashCode() 方法，则是为了满足上述hashcode()与equals()判断对象是否相等时的约定，即为了防止出现equals()判断相等而hashcode()却判断不相同的情况。

#### String 为什么是不可变的?

- 保存字符串的数组被 final 修饰且为私有的，并且String 类没有提供/暴露修改这个字符串的方法。
- String 类被 final 修饰导致其不能被继承，进而避免了子类破坏 String 不可变。

#### String、StringBuffer、StringBuilder 的区别？

String 中的对象是不可变的，也就可以理解为常量，线程安全。AbstractStringBuilder 是 StringBuilder 与 StringBuffer 的公共父类，定义了一些字符串的基本操作，如append、insert、indexOf 等公共方法。StringBuffer 对方法加了同步锁或者对调用的方法加了同步锁，所以是线程安全的。StringBuilder 并没有对方法进行加同步锁，所以是非线程安全的。

对于三者使用的总结：

1. 操作少量的数据: 适用 `String`
2. 单线程操作字符串缓冲区下操作大量数据: 适用 `StringBuilder`
3. 多线程操作字符串缓冲区下操作大量数据: 适用 `StringBuffer`

#### 字符串拼接用“+” 还是 StringBuilder?

Java 语言本身并不支持运算符重载，“+”和“+=”是专门为 String 类重载过的运算符，也是 Java 中仅有的两个重载过的运算符。字符串对象通过“+”的字符串拼接方式，实际上是通过 StringBuilder 调用 append() 方法实现的，拼接完成之后调用 toString() 得到一个 String 对象 。

不过使用“+”时存在比较明显的缺陷：**在循环内使用“+”进行字符串的拼接的话，编译器不会创建单个 StringBuilder 以复用，会导致创建过多的 StringBuilder 对象。**直接使用StringBuilder 的append() 方法则不会有这个问题，已经创建的StringBuilder对象可以重复使用。

#### 字符串常量池了解吗？

字符串常量池（String Pool）是 JVM 为了提升性能和减少内存消耗针对字符串（String 类）专门开辟的一块区域，主要目的是为了避免字符串的重复创建，它保存着所有编译时期就确定的字符串字面量；另外使用 String 的 intern() 方法可以在运行过程将字符串添加到 String Pool 中。

```java
//使用new创建字符串对象时会创建一个新的对象并把其字面量加入常量池，前提是该字面量为首次存入
String s1 = new String("aaa");
String s2 = new String("aaa");
System.out.println(s1 == s2);           // false
//使用intern可以在运行时将字面量存入常量池，赋值时调用会返回常量池中的已有字面量的引用
String s3 = s1.intern();
String s4 = s2.intern();
System.out.println(s3 == s4);           // true
//直接使用字面量定义字符串对象会自动将字面量存入常量池
String s5 = "bbb";
String s6 = "bbb";
System.out.println(s5 == s6);  // true
```

### 异常

Exception 和 Error 有什么区别？

Java 中所有的异常都有共同祖先： `java.lang` 包中的 `Throwable` 类。`Throwable` 类有两个重要的子类:

- **`Exception`** :程序本身可以处理的异常，可以通过 `catch` 来进行捕获。`Exception` 又可以分为两种Checked Exception (受检查异常，必须处理) 和 Unchecked Exception (不受检查异常，可以不处理)。
- **`Error`** ：`Error` 属于程序无法处理的错误 ，~~我们没办法通过 `catch` 来进行捕获~~不建议通过`catch`捕获 。例如 Java 虚拟机运行错误（`Virtual MachineError`）、虚拟机内存不够错误(`OutOfMemoryError`)、类定义错误（`NoClassDefFoundError`）等 。这些异常发生时，Java 虚拟机（JVM）一般会选择线程终止。

#### Unchecked Exception和Checked Exception  有什么区别？

非受检异常 ：非受检异常即是`RuntimeException`及其子类在内的程序运行时错误，常见的有除 0 会引发的Arithmetic Exception 算术错误、NumberFormatException 字符串转换为数字格式错误、NullPointerException空指针错误、OfBoundsException 数组越界错误等，可以通过程序的编译但是发生时程序崩溃并且无法恢复。

受检异常 ：需要用 try...catch... 语句捕获并进行处理，并且可以从异常中恢复。 除了`RuntimeException`及其子类以外，其他的所有`Exception`类及其子类都属于受检查异常 。 常见的受检查异常有： IO 相关的异常、ClassNotFoundException 、SQLException等。

#### try-catch-finally 如何使用？

- `try`块 ： 用于捕获异常。其后可接零个或多个 `catch` 块，如果没有 `catch` 块，则必须跟一个 `finally` 块。
- `catch`块 ： 用于处理 try 捕获到的异常。
- `finally` 块 ： 无论是否捕获或处理异常，`finally` 块里的语句都会被执行。当在 `try` 块或 `catch` 块中遇到 `return` 语句时，`finally` 语句块将在方法返回之前被执行。

 **注意：不要在 finally 语句块中使用 return!** 当 try 语句和 finally 语句中都有 return 语句时，try 语句块中的 return 语句会被忽略。这是因为 try 语句中的 return 返回值会先被暂存在一个本地变量中，当执行到 finally 语句中的 return 之后，这个本地变量的值就变为了 finally 语句中的 return 返回值。 

#### finally 中的代码一定会执行吗？

大多数情况下会执行，但是在某些极其特殊的情况下，finally 中的代码不会被执行。

就比如说 finally 之前虚拟机被终止运行的话，finally 中的代码就不会被执行。

```java
try {
    System.out.println("Try to do something");
    throw new RuntimeException("RuntimeException");
} catch (Exception e) {
    System.out.println("Catch Exception -> " + e.getMessage());
    // 终止当前正在运行的Java虚拟机
    System.exit(1);
} finally {
    System.out.println("Finally");
}
```

输出：

```java
Try to do something
Catch Exception -> RuntimeException
```

另外，在以下 2 种特殊情况下，`finally` 块的代码也不会被执行：

1. 程序所在的线程死亡。
2. 关闭 CPU。

#### throw 和 throws 的区别？

throw：在方法体内部，表示抛出异常，由方法体内部的语句处理；throw 是具体向外抛出异常的动作，所以它抛出的是一个异常实例；

throws：在方法声明后面，表示如果抛出异常，由该方法的调用者来进行异常的处理；表示出现异常的可能性，并不一定会发生这种异常。

## Java高级特性

### 泛型

#### 什么是泛型？有什么作用？

**Java 泛型（Generics）** 是 JDK 5 中引入的一个新特性，为了便于简化在集合中存储对象前进行类型转换的操作 。使用泛型参数，可以增强代码的可读性以及稳定性。

编译器可以对泛型参数进行检测，并且通过泛型参数可以指定传入的对象类型。比如 `ArrayList<Persion> persons = new ArrayList<Persion>()`  这行代码就指明了该 `ArrayList` 对象只能传入 `Persion` 对象，如果传入其他类型的对象就会报错。

#### 泛型的使用方式有哪几种？

泛型一般有三种使用方式:**泛型类**、**泛型接口**、**泛型方法**。

**1.泛型类**：

```java
//此处T可以随便写为任意标识，常见的如T、E、K、V等形式的参数常用于表示泛型
//在实例化泛型类时，必须指定T的具体类型
public class Generic<T>{

    private T key;

    public Generic(T key) {
        this.key = key;
    }

    public T getKey(){
        return key;
    }
}
```

如何实例化泛型类：

```java
Generic<Integer> genericInteger = new Generic<Integer>(123456);
```

**2.泛型接口** ：

```java
public interface Generator<T> {
    public T method();
}
```

实现泛型接口，不指定类型：

```java
class GeneratorImpl<T> implements Generator<T>{
    @Override
    public T method() {
        return null;
    }
}
```

实现泛型接口，指定类型：

```java
class GeneratorImpl<T> implements Generator<String>{
    @Override
    public String method() {
        return "hello";
    }
}
```

**3.泛型方法** ：

```java
   public static < E > void printArray( E[] inputArray )
   {
         for ( E element : inputArray ){
            System.out.printf( "%s ", element );
         }
         System.out.println();
    }
```

使用：

```java
// 创建不同类型数组： Integer, Double 和 Character
Integer[] intArray = { 1, 2, 3 };
String[] stringArray = { "Hello", "World" };
printArray( intArray  );
printArray( stringArray  );
```

#### 自己的项目中哪里用到了泛型？

- 自定义接口通用返回结果 `CommonResult` 通过参数 `T` ，可根据具体的返回类型动态指定结果的数据类型
- 定义 `Excel` 处理类 `ExcelUtil` 用于动态指定 `Excel` 导出的数据类型
- 构建集合工具类（参考 `Collections` 中的 `sort`, `binarySearch` 方法）。
- ......

#### <? extends T>和 <? super T>（以及<  ？>）之间有什么区别 ?

前两个声明都是限定通配符的例子，`List<? extends T>`表示可以接受任何继承自T的类型的List来确定上界，而`List<? super T>`表示可以接受任何T的父类构成的List来确定下界，例如`List<? extends Number>`可以接受`List<Integer>`或`List<Float>`。最后的< ？>是非限定通配符，表示可以用任何类型来替代。

#### 可以把List< String >传递给一个接受List< Object >参数的方法吗？

不可以，这样会导致编译错误。下方代码分别展示了错误和正确的赋值情况。

```java
public static void main(String[] args) {

    List<String> list = new ArrayList<String>();
    list.add("测试1");
    list.add("测试2");
    List<Object> result = new ArrayList<Object>();

    for(int i =0;i<list.size();i++){
        result.add(list.get(i));//可以赋值
    }

    test1(list);//但是作为参数传递的话 会报错
    test2(list);//如果这样用 就可以了
    System.out.println(result.toString());
}

public static String test1(List<Object> t){
    return "";
}

public static String test2(List<? extends Object> t){
    return "";
}
```

### 反射

#### 什么是反射？如何使用？

JAVA反射机制是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意一个方法和属性；这种动态获取的信息以及动态调用对象的方法的功能称为java语言的反射机制。

在Java中，Class类与反射包一起对反射技术进行了全力的支持。

- Class类对象的获取

```java
    @Test
    public void classTest() throws Exception {
        // 获取Class对象的三种方式
        logger.info("根据类名:  \t" + User.class);
        logger.info("根据对象:  \t" + new User().getClass());
        logger.info("根据全限定类名:\t" + Class.forName("com.test.User"));
        // 常用的方法
        logger.info("获取全限定类名:\t" + userClass.getName());
        logger.info("获取类名:\t" + userClass.getSimpleName());
        logger.info("实例化:\t" + userClass.newInstance());
    }
    
```

- Constructor类，主要表示Class 对象所表示的类的构造方法，利用它可以在运行时动态创建对象。
- Field类及其用法，表示Class对象所表示的类的成员变量，通过它可以在运行时动态修改成员变量的属性值(包含private)。
- Method类及其用法，Method表示Class对象所表示的类的成员方法，通过它可以动态调用对象的方法(包含private)