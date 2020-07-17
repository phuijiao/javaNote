###### Scanner类

系统输入

```java
import util.Scanner
    
Scanner sc = new Scanner(System.in);
int i = sc.nextInt();
String str = sc.next();
```



###### Random类

随机数

```java
import java.util.Random;

Random r = new Random();
int i = r.nextInt();
```



###### ArrayList类

ArrayList对象不能存储基本类型，只能存储引用类型的数据。

```java
import java.util.ArrayList;

ArrayList<String> list = new ArrayList<>();
public boolean add(E e);	//将指定的元素添加到此集合的尾部。
public E remove(int index);	//移除此集合中指定位置上的元素。返回被删除的元素
public E get(int index);	//返回此集合中指定位置上的元素。返回获取的元素
public int size();	//返回此集合中的元素数。遍历集合时，可控制索引范围，防止越界
```



###### String类

字符串不变：字符串的值在创建后不能被更改，可以被共享

```java
public boolean equals(Object anObject); //将此字符串与指定对象进行比较。比较字符串的内同是否相同
public boolean equalsIgnoreCase (String anotherString); //将此字符串与指定对象进行比较，忽略大小写。
public int length ()；   //返回此字符串的长度。
public String concat (String str)；  //将指定的字符串连接到该字符串的末尾。
public char charAt (int index)； //返回指定索引处的 char值。
public int indexOf (String str)；    //返回指定子字符串第一次出现在该字符串内的索引。
public String substring (int beginIndex)；   //返回一个子字符串，从beginIndex开始截取字符串到字符串结尾。
public String substring (int beginIndex, int endIndex)； //返回一个子字符串，从beginIndex到endIndex截取字符串。含beginIndex，不含endIndex
public char[] toCharArray ()；	//将此字符串转换为新的字符数组。
public byte[] getBytes ()；	//使用平台的默认字符集将该 String编码转换为新的字节数组。
public String replace (CharSequence target, CharSequence replacement)；	//将与target匹配的字符串使用replacement字符串替换。
public String[] split(String regex)；	//将此字符串按照给定的regex（规则）拆分为字符串数组。
```



###### static关键字

类变量：当static修饰成员变量时，该变量称为类变量。该类的每个对性都共享同一个类变量的值。任何对象都可以更改该类变量的值，但也可以在不创建类的对象的情况下对类变量进行操作。

静态方法：当static修饰成员方法时，该方法称为类方法。静态方法在声明中有static，建议使用类名来调用，而不需要创建类的对象。

静态方法调用的注意事项：

1. 静态方法可以直接访问类变量和静态方法。
2. 静态方法不能直接访问普通成员变量和成员方法。反之，成员方法可以直接访问类变量或静态方法。
3. 静态方法中，不能使用this关键字。

static修饰的内容

1. 是随着类的加载而加载的，且只加载一次。
2. 存储于一块固定的内存区域（静态区），所以，可以直接被类名调用。
3. 它优先于对象存在，所以，可以被所有对象共享。

静态代码块：定义在成员位置，使用static修饰的代码块{ }

1. 位置：类中方法外。
2. 执行：随着类的加载而执行且执行一次，优先于main方法和构造方法的执行。
3. 作用:给类变量进行初始化赋值。



###### Arrays类

```java
public static String toString(数组)；	//将参数数组转变成字符串
public static void sort(数组);	//按照默认升序对数组的元素进行排序
```



###### Math类

```java
public static double abs(double num)：获取绝对值。有多种重载。
public static double ceil(double num)：向上取整。
public static double floor(double num)：向下取整。
public static long round(double num)：四舍五入。
```



###### 继承

关键字 extends

继承后成员变量不重名时：访问是没有影响的。

继承后成员变量重名：

1. 在子类中访问父类中非私有成员变量时，需使用super关键字

   super.父类成员变量名

2. 父类中私有成员变量，子类不能直接访问，可用get/set方法

继承后成员方法重名：重写(Override)

1. 必须要保证权限大于等于父类权限
2. 返回值、函数名和参数列表要一样

继承后构造方法

1. 子类无法继承父类的构造方法
2. 子类初始化过程中，必须先执行父类的初始化动作。子类的构造方法中默认有一个“super()调用“,表示调用父类的构造方法，父类成员变量初始化后，才可以给子类使用。
3. super的父类构造调用，必须是子类构造方法的第一条语句。不能一个子类构造调用多次super构造。
4. 子类必须调用父类构造方法，不写则赠送super();写了则用写的指定的super调用，super调用只能有一个，还必须是第一个。

java只支持单继承，不支持多继承，支持多层继承。顶层父类是Object类。



###### 抽象类

抽象方法：没有方法体的方法

抽象类：包含抽象方法的类

关键字：abstract

```java
修饰符 abstract 返回值类型 方法名 (参数列表)；
```

继承抽象类的子类必须重写父类所有的抽象方法。否则该子类也必须声明为抽象类。

抽象类不能创建对象



###### 接口

接口不是类，是一种引用数据类型，不能创建对象，但可以被实现（implements）。一个实现接口的类需要实现接口中所有的抽象方法，否则它必须是一个抽象类。

关键字：interface

```java
public interface 接口名称 {
    // 抽象方法
    // 默认方法
    // 静态方法
    // 私有方法
}
```

```java
class 类名 implements 接口名 {
    // 重写接口中抽象方法【必须】
    // 重写接口中默认方法【可选】
}
```

默认方法：使用default修饰，不可省略，供子类调用或者子类重写。

静态方法：使用static修饰，供接口直接调用。只能使用接口名调用。

私有方法：使用private修饰，只有默认方法可以调用。

私有静态方法：使用private static修饰，供接口中的默认方法或者静态方法调用。

接口的多实现

1. 一个类只能继承一个父类，同时实现多个接口。
2. 如果抽象方法有重名，只需要重写一次。
3. 如果默认方法有重名，必须重写一次。
4. 接口中存在同名的静态方法不会冲突，原因是只能通过各自接口名访问静态方法。
5. 当一个类既继承一个父类，又实现若干个接口时，父类中的成员方法与接口中的默认方法重名，子类就近选择执行父类的成员方法。
6. 一个接口能继承另一个或多个接口，接口继承使用extends关键字，子接口继承父接口的方法。如果父接口中的默认方法有重名的，那么子接口需要重写一次。
7. 接口中无法定义成员变量，但可以定义常量，默认使用public static final修饰。
8. 接口中没有静态代码块。



###### 多态

```java
父类类型 变量名 = new 子类对象；
变量名.方法名();
```

向上转型：子类类型向父类类型向上转换的过程，这个过程是默认的。

向下转型：父类类型向子类类型向下转换的过程，这个过程是强制的。

```java
子类类型 变量名 = (子类类型) 父类变量名;
```

Java提供了 instanceof 关键字，给引用变量做类型的校验

```java
变量名 instanceof 数据类型
如果变量属于该数据类型，返回true。
如果变量不属于该数据类型，返回false。
```



###### final关键字

`final`:不可改变。可用于修饰类、方法和变量

1. 类：被修饰的类，不能被继承
2. 方法：被修饰的方法，不能被重写
3. 变量：被修饰的变量，不能被重新赋值，只能赋值一次



###### 日期时间类

DateFormat类

子类java.text.SimpleDateFormat

```java
public String format(Date date)；	//将Date对象格式化为字符串。
public Date parse(String source)；	//将字符串解析为Date对象。
```

Calendar类

```java
public static Calendar getInstance()；//使用默认时区和语言环境获得一个日历
Calendar cal = Calendar.getInstance();

public int get(int field);	//返回给定日历字段的值。
public void set(int field, int value);	//将给定的日历字段设置为给定值。
public abstract void add(int field, int amount);	//根据日历的规则，为给定的日历字段添加或减去指定的时间量。
public Date getTime();	//返回一个表示此Calendar时间值（从历元到现在的毫秒偏移量）的Date对象。
```



###### System类

- `public static long currentTimeMillis()`：返回以毫秒为单位的当前时间。
- `public static void arraycopy(Object src, int srcPos, Object dest, int destPos, int length)`：将数组中指定的数据拷贝到另一个数组中。



###### StringBuilder类

StringBuilder又称为可变字符序列，它是一个类似于String的字符串缓冲区，通过某些方法调用可以改变该序列的长度和内容。

- `public StringBuilder()`：构造一个空的StringBuilder容器。
- `public StringBuilder(String str)`：构造一个StringBuilder容器，并将字符串添加进去。

- `public StringBuilder append(...)`：添加任意类型数据的字符串形式，并返回当前对象自身。
- `public String toString()`：将当前StringBuilder对象转换为String对象。



###### Collection集合

Collection:单列集合的根接口。

List集合的特点是元素有序、元素可重复。

Set集合的特点是元素无序、元素不可重复。

Collection是所有单列集合的父接口，因此在Collection中定义了单列集合(List和Set)通用的一些方法，这些方法可用于操作所有的单列集合。方法如下：

* `public boolean add(E e)`：  把给定的对象添加到当前集合中 。
* `public void clear()` :清空集合中所有的元素。
* `public boolean remove(E e)`: 把给定的对象在当前集合中删除。
* `public boolean contains(E e)`: 判断当前集合中是否包含给定的对象。
* `public boolean isEmpty()`: 判断当前集合是否为空。
* `public int size()`: 返回集合中元素的个数。
* `public Object[] toArray()`: 把集合中的元素，存储到数组中。



Iterator迭代器

```java
public Iterator iterator();	//获取集合对应的迭代器
public E next();	//返回迭代器的下一个元素
public boolean hasNext();	//如果仍有元素可以迭代，则返回true
```

增强for

它的内部原理是Iterator迭代器，所以在遍历的过程中，不能对集合中的元素进行增删操作。

```java
for(元素的数据类型  变量 : Collection集合or数组){ 
  	//写操作代码
}
```



###### 泛型

```java
修饰符 class 类名<代表泛型的变量> {  }
修饰符 <代表泛型的变量> 返回值类型 方法名(参数){  }
修饰符 interface 接口名<代表泛型的变量> {  }
```

泛型通配符

当使用泛型类或者接口时，传递的数据中，泛型类型不确定，可以通过通配符<?>表示。但是一旦使用泛型的通配符后，只能使用Object类中的共性方法，集合元素自身方法无法使用。

指定泛型时，不写泛型默认为Object类型

泛型的上限：

- 格式：类型名称<? extends 类> 对象名称
- 意义：只能接收该类型及其子类

泛型的下限：

- 格式：类型名称<? super 类> 对象名称
- 意义：只能接收该类型及其父类型



```java
static void shuffle(List<?> list);	//使用默认随机源对指定列表进行置换（打乱顺序）
```



###### List集合

List接口特点：

1. 它是一个元素存取有序的集合
2. 它是一个带有索引的集合，通过索引就可以精确的操作集合的元素
3. 集合中可以有重复的元素，通过元素的equals方法，来比较是否为重复的元素。

ArrayList集合数据存储的结构是数组结构。元素增删慢，查找快。

LinkedList集合数据存储的结构是链表结构。方便元素添加、删除。是双向链表。



###### Set接口

Set接口中元素无序，并且都会以某种规则保证存入的元素不出现重复。

HashSet地层的实现是HashMap支持。HashSet是根据对象的哈希值来确定元素在集合中的存储位置，因此具有良好的存取和查询性能。保证元素唯一性的方式依赖于hashCode与equals方法。

在JDK1.8中，哈希表存储采用数组+链表+红黑树实现，当链表长度超过阀值（8）时，将链表转换为红黑树，这样大大减少了查询时间。

给HashSet中存放自定义类型元素时，需要重写对象的hashCode和equals方法，建立自己的比较方式，才能保证HashSet集合中的对象唯一。

LinkedHashSet是链表和哈希表组合的一个数据存储结构。存取有序。



可变参数：在JDK1.5之后，如果一个方法需要接受多个参数，并且多个参数的类型一致，可以简化成如下格式：

```java
修饰符 返回值类型 方法名（参数类型... 形参名）{}
```

可变参数注意事项：

1. 一个方法的参数列表，只能有一个可变参数
2. 如果方法的参数类型有多个，那么可变参数必须写在参数列表的末尾



###### Collections集合工具类

```java
public static <T> void sort(List<T> list);	//将集合中元素按照默认规则排序。
public static <T> void sort(List<T> list，Comparator<? super T> );	//将集合中的元素按照指定规则排序。
public int compare(String o1, String o2) ：比较其两个参数的顺序。
    两个对象比较的结果有三种：大于，等于，小于。
    如果要按照升序排序， 则o1 小于o2，返回（负数），相等返回0，o1大于o2返回（正数）如果要按照
    降序排序 则o1 小于o2，返回（正数），相等返回0，01大于02返回（负数）
    
Collections.sort(list, new Comparator<String>() {
    @Override
    public int compare(String o1, String o2) {
   		return o2.charAt(0) ‐ o1.charAt(0);
    }
});

public class Student implements Comparable<Student>{
    ....
    @Override
    public int compareTo(Student o) {
    	return this.age‐o.age;//升序
    }
}
```



###### Map集合

HashMap：存储数据采用哈希表结构，元素的存取顺序不能保证一致。由于要保证键的唯一性、不重复，需要重写键的hashCode()方法、equals()方法。

LinkedHashMap：存储数据采用哈希表结构+链表结构。通过链表结构可以保证元素的存取顺序一致。通过哈希表结构可以保证键的唯一性、不重复，需要重写键的hashCode()方法、equals()方法。

Entry将键值对的对应关系封装成了对象，即键值对对象。



###### 多线程

java使用java.lang.thread类代表线程，所有的线程对象都必须是Thread类或其子类的实例。

实现Runnable接口

同步代码块：`synchronized`关键字可以用于方法中的某个区块中，表示只对这个区块的资源实行互斥访问。

```java
synchronized(同步锁){
    需要同步操作的代码
}
```

同步方法：`使用synchronized`修饰的方法叫做同步方法，保证A线程执行该方法的时候，其他线程只能在方法外等着。

```java
public synchronized void method(){
    可能会产上线程安全问题的代码
}
```

同步锁是谁？

1. 对于非static方法，同步锁就是this
2. 对于static方法，我们使用当前方法；所在类的字节码对象（类名.class）

Lock锁

- public void lock() :加同步锁。
- public void unlock() :释放同步锁。

等待唤醒机制：一个线程进行了规定操作后，就进入等待状态（wait()），等待其他线程执行完他们的指定代码过后，在将其唤醒（notify()），在有多个线程进行等待时，如果需要，可以使用notifyAll()来唤醒所有的等待线程。



###### 线程池

```java
java.util.concurrent.Executor
public static ExecutorService newFixedThreadPool(int nThreads);	//返回线程池对象。
public Future<?> submit(Runnable task);	//获取线程池中的某一个线程对象，并执行。
```



###### Lambda表达式

```java
标准格式：(参数类型 参数名称) -> {代码语句}
```

省略规则：

1. 小括号内参数类型可以省略
2. 如果小括号内有且仅有一个参数，则小括号可以省略
3. 如果大括号内有且仅有一条语句，则无论是否有返回值，都可以省略大括号、return关键字及语句分好

Lambda的使用前提

1. 使用Lambda必须具有接口，且要求接口中有且仅有一个抽象方法
2. 使用Lambda必须具有上下文推断



###### IO流

顶级父类

|        | 输入流                 | 输出流                  |
| ------ | ---------------------- | ----------------------- |
| 字节流 | 字节输入流 InputStream | 字节输出流 OutputStream |
| 字符流 | 字符输入流 Reader      | 字符输出流 Writer       |

**字节输出流 OutputStream**抽象类是表示字节输出流的所有类的超类，将指定的字节信息写出到目的地。它定义了字节输出流的基本共性功能方法。

```java
public void close();//关闭此输出流并释放与此流相关联的任何系统资源
public void flush();//刷新此输出流并强制任何缓冲的输出字节被写出
public void write(byte[] b);//将b.length字节从指定的字节数组写入此输出流
public void write(byte[] b, int off, int len);//从指定的字节数组写入len字节，从偏移量off开始输出到此输出流
public abstract void write(int b);//将指定的字节输出流
```

java.io.FileOutputStream 类是文件输出流，用于将数据写出到文件。

构造方法

```java
public FileOutputStream(File file);	//创建文件输出流以写入由指定的 File对象表示的文件。
public FileOutputStream(String name);//创建文件输出流以指定的名称写入文件。
```

当你创建一个流对象时，必须传入一个文件路径。该路径下，如果没有这个文件，会创建该文件。如果有这个文
件，会清空这个文件的数据。

数据追加续写

```java
public FileOutputStream(File file, boolean append);//创建文件输出流以写入由指定的 File对象表示的文件。
public FileOutputStream(String name, boolean append);//创建文件输出流以指定的名称写入文件。
```

这两个构造方法，参数中都需要传入一个boolean类型的值， true 表示追加数据， false 表示清空原有数据。



**字节输入流 InoutStream**

```java
public void close();//关闭此输入流并释放与此流相关联的任何系统资源。
public abstract int read();//从输入流读取数据的下一个字节。每次可以读取一个字节的数据，提升为int类型，读取到文件末尾，返回 -1 
public int read(byte[] b);//从输入流中读取一些字节数，并将它们存储到字节数组 b中。每次读取b的长度个字节到数组中，返回读取到的有效字节个数，读取到末尾时，返回 -1 
```

java.io.FileInputStream 类是文件输入流，从文件中读取字节。

```java
FileInputStream(File file);//通过打开与实际文件的连接来创建一个 FileInputStream ，该文件由文件系统中的 File对象 file命名。
FileInputStream(String name);//通过打开与实际文件的连接来创建一个 FileInputStream ，该文件由文件系统中的路径名 name命名。
```



**字符输入流Reader**

```java
public void close() ：关闭此流并释放与此流相关联的任何系统资源。
public int read() ： 从输入流读取一个字符。
public int read(char[] cbuf) ： 从输入流中读取一些字符，并将它们存储到字符数组 cbuf中 。
```

java.io.FileReader 类是读取字符文件的便利类。构造时使用系统默认的字符编码和默认字节缓冲区。

```java
FileReader(File file);//创建一个新的 FileReader ，给定要读取的File对象。
FileReader(String fileName);//创建一个新的 FileReader ，给定要读取的文件的名称。
```



**字符输出流 Writer**

```java
void write(int c);//写入单个字符。
void write(char[] cbuf);//写入字符数组。
abstract void write(char[] cbuf, int off, int len);//写入字符数组的某一部分,off数组的开始索引,len写的字符个数。
void write(String str);//写入字符串。
void write(String str, int off, int len);//写入字符串的某一部分,off字符串的开始索引,len写的字符个数
void flush();//刷新该流的缓冲。
void close();//关闭此流，但要先刷新它。
```

java.io.FileWriter 类是写出字符到文件的便利类。构造时使用系统默认的字符编码和默认字节缓冲区。

```java
FileWriter(File file);//创建一个新的 FileWriter，给定要读取的File对象。
FileWriter(String fileName);//创建一个新的 FileWriter，给定要读取的文件的名称。
```



**try-with-resoource的改进**

无需手动关闭资源

```java
// 被final修饰的对象
final Resource resource1 = new Resource("resource1");
// 普通对象
Resource resource2 = new Resource("resource2");
// 引入方式：直接引入
try (resource1; resource2) {
	// 使用对象
}
```



###### 属性集

java.util.Properties继承Hashtable，来表示一个持久的属性集。它使用键值结构存储数据，每个键及其对应值都是一个字符串。

```java
public Properties();//创建一个空的属性列表。
public Object setProperty(String key, String value);//保存一对属性。
public String getProperty(String key);//使用此属性列表中指定的键搜索属性值。
public Set<String> stringPropertyNames();//所有键的名称的集合。
public void load(InputStream inStream);//从字节输入流中读取键值对。
void load(Reader reader);
void store(OutputStream out, String comments);//OutputStream out:字节输出流,不能写入中文
void store(Writer writer, String comments);//Writer writer:字符输出流,可以写中文.String comments:注释,用来解释说明保存的文件是做什么用的,不能使用中文,会产生乱码,默认是Unicode编码,一般使用""空字符串
```



###### 缓冲流

字节缓冲流

```java
public BufferedInputStream(InputStream in);//创建一个新的缓冲输入流。
public BufferedOutputStream(OutputStream out);//创建一个新的缓冲输出流
```



字符缓冲流

```java
public BufferedReader(Reader in);//创建一个 新的缓冲输入流。
public BufferedWriter(Writer out);//创建一个新的缓冲输出流。
```

特有方法

```java
BufferedReader： public String readLine();//读一行文字。
BufferedWriter： public void newLine();//写一行 行分隔符,由系统属性定义符号。
```



###### 转换流

```java
InputStreamReader(InputStream in);//创建一个使用默认字符集的字符流。
InputStreamReader(InputStream in, String charsetName);//创建一个指定字符集的字符流。
```

```java
OutputStreamWriter(OutputStream in);//创建一个使用默认字符集的字符流。
OutputStreamWriter(OutputStream in, String charsetName);//创建一个指定字符集的字符流
```



###### 序列化

java.io.ObjectOutputStream 类，将Java对象的原始数据类型写出到文件,实现对象的持久存储。  

```java
public ObjectOutputStream(OutputStream out);//创建一个指定OutputStream的ObjectOutputStream。
```

对象序列化需满足的条件

1. 该类必须实现java.io.Serializable接口，Serializable是一个标记接口，不实现此接口的类将不会使任何状态序列化或反序列化，会抛出NotSerializableException。
2. 该类的所有属性必须是可序列化的。如果有一个属性不需要可序列化的，则该属性必须注明是瞬态的，使用**transient**关键字修饰。
3. 被static修饰的成员变量不能被序列化,序列化的都是对象

```java
public final void writeObject (Object obj);//将指定的对象写出。
```



ObjectInputStream反序列化流，将之前使用ObjectOutputStream序列化的原始数据恢复为对象。  

```java
public ObjectInputStream(InputStream in);//创建一个指定InputStream的ObjectInputStream。
```

```java
public final Object readObject ();//读取一个对象。
```

对于JVM可以反序列化对象，它必须是能够找到class文件的类。如果找不到该类的class文件，则抛出一个ClassNotFoundException 异常  

Serializable 接口给需要序列化的类，提供了一个序列版本号。 serialVersionUID 该版本号的目的在于验证序列化的对象和对应类是否版本匹配。  



###### 打印流

```java
public PrintStream(File file);//输出的目的地是一个文件
public PrintStream(OutputStream out);//输出的目的地是一个字节输出流
public PrintStream(String fileName);//使用指定的文件名创建一个新的打印流。
```

改变打印流向

```java
// 创建打印流,指定文件的名称
PrintStream ps = new PrintStream("ps.txt");
// 设置系统的打印流流向,输出到ps.txt
System.setOut(ps);
// 调用系统的打印流,ps.txt中输出97
System.out.println(97);
```



###### TCP通信

- 客户端：java.net.Socket类表示创建Socket对象，向服务器端发出连接请求，服务器响应请求，两者建立连接开始通信。

```java
public Socket(String host, int port);//创建套接字对象并将其连接到指定主机上的指定端口号。如果指定的host是null ，则相当于指定地址为回送地址
```

```java
public InputStream getInputStream();//返回此套接字的输入流。
    如果此Scoket具有相关联的通道，则生成的InputStream 的所有操作也关联该通道。
    关闭生成的InputStream也将关闭相关的Socket。
public OutputStream getOutputStream();//返回此套接字的输出流。
    如果此Scoket具有相关联的通道，则生成的OutputStream 的所有操作也关联该通道。
    关闭生成的OutputStream也将关闭相关的Socket。
public void close();//关闭此套接字。
    一旦一个socket被关闭，它不可再使用。
    关闭此socket也将关闭相关的InputStream和OutputStream 。
public void shutdownOutput();// 禁用此套接字的输出流。
	任何先前写出的数据将被发送，随后终止输出流。  
```



- 服务端：java.net.ServerSocket类表示创建ServerSocket对象，相当于开启一个服务，并等待客户端的连接。

```java
public ServerSocket(int port);//使用该构造方法在创建ServerSocket对象时，就可以将其绑定到一个指定的端口号上，参数port就是端口号。
```

```java
public Socket accept();//侦听并接受连接，返回一个新的Socket对象，用于和客户端实现通信。该方法会一直阻塞直到建立连接。
```



###### 函数式接口

有且仅有一个抽象方法的接口。

@FunctionalInterface注解，该注解可用于一个接口的定义上。

一旦使用该注解来定义接口，编译器将会强制检查该接口是否确实有且仅有一个抽象方法。



###### Stream流

java.util.stream.Stream<T>是Java 8新加入的最常用的流接口。

获取流的方法：

- 所有的Collection集合都可以通过stream()默认方法获取流
- Stream接口的静态方法of()可以获取数组对应的流

```java
list.stream();
Stream.of(1, 2, 3, 4, 5);
Stream.of(arr);
```



###### 反射

将类的各个组成部分封装为其他对象，这就是反射机制。

好处：

1. 可以在程序运行过程中，操作这些对象。
2. 可以解耦，提高程序的可扩展性。

获取Class对象的方式：

1. Class.forName("全类名")：将字节码文件加载进内存，返回Class对象。
   - 多用于配置文件，将类名定义在配置文件中，读取文件加载类
2. 类名.class：通过类名的属性class获取
   - 多用于参数的传递
3. 对象.getClass()：getClass()方法在Object类中定义着。
   - 多用于对象的获取字节码的方式

- 结论：同一个字节码文件(*.class)在一次程序运行过程中，只会加载一次，不论通过哪一种方式获取的Class对象都是同一个。



###### mysql

```shell
sudo service mysql start	#开启mysql
ps ajx | grep mysql			#查看mysql进程
sudo service mysql stop		#关闭mysql
sudo service mysql restart	#重启mysql
```

SQL分类

```mysql
1.DDL(Data Definition Language)数据定义语言
	用来定义数据库对象：数据库、表、列等。关键字 create,drop,alter等
2.DML(Data Manipulation Language)数据操作语言
	用来对数据库中表的数据进行增删改。关键字 insert,delete,update等
3.DQL(Data Query Language)数据查询语言
	用来查询数据库中表的记录(数据)。关键字 select,where等
4.DCL(Data Control Language)数据控制语言
	用来定义数据库的访问权限和安全级别，及创建用户。关键字：GRANT,REVOKE等
```

DDL:操作数据库、表、列

1.操作数据库：CRUD

```mysql
1.C(create):创建
	创建数据库：
		create database 数据库名称;
		create database if not exists 数据库名称;
		create database 数据库名称 character set 字符集名称;
2.R(retrieve):查询
	查询所有数据库名称：
		show databases;
	查询某个数据库的字符集：查询某个数据库的创建语句
		show create database 数据库名称;
3.U(update):修改
	修改数据库的字符集
		alter database 数据库名称 character set 字符集名称;
4.D(delete):删除
	删除数据库
		drop database 数据库名称;
		drop database if exists 数据库名称；
5.使用数据库
	查询当前正在使用的数据库名称
		select database();
	使用数据库
		use 数据库名词;		
```

2.操作表CRUD

```mysql
1.C(create):创建
	create table 表名 (
    列名1 数据类型1，
        ....
    列名n 数据类型n
    );
    *注意：最后一列，不需要加逗号(,)
2.R(retrieve)：查询
	查询某个数据库中所有的表名称
		show tables;
	查询表结构
		desc 表名称;
3.U(update):修改
	修改表名称
		alter table 表名 rename to 新的表名;
	修改表的字符集
		alter table 表名 character set 字符集名称;
	添加一列
		alter table 表名 add 列名 数据类型;
	修改列名 类型
		alter table 表名 change 列名 新列名 新数据类型;
		alter table 表名 modify 列名 新数据类型;
	删除列
		alter table 表名 drop 列名;
4.D(delete):删除
	drop table 表名;
	drop table if exists 表名;
```

DML:增删改表中数据

```mysql
1.添加数据
	insert into 表名(列名1, ... , 列名n) values (值1, ... , 值n);
		注意：列名和值要一一对应，除了数字类型，其他类型需要使用引号引起来。
	insert into 表名 values (值1, ... , 值n);
		注意：如果表名后不定义列名，则默认给所有列添加值
2.删除数据
	delete from 表名 [where 条件]
		注意：
            1.如果不加条件，则删除表中所有记录
            2.如果要删除所有记录
                1.delete from 表名; -- 不推荐使用。有多少条记录就会执行多少次删除操作
                2.TRUNCATE TABLE 表名; -- 推荐使用，效率更高。先删除表，然后创建表
3.修改数据
	update 表名 set 列名1=值1，列名2=值2,... [where 条件]；
		注意：如果不加任何条件，则会将表中所有记录全部修改
```

DQL:查询表中的记录

```mysql
select * from 表明;
语法：
	select
		字段列表
	from
		表名列表
	where
		条件列表
	group by
		分组字段
	having
		分组之后的条件
	order by
		排序
	limit
		分页限定

去除重复：
	distinct
起别名：
 as:as也可以省略

条件查询
	1.where子句后跟条件
    2.运算符
    	> , < , <= , >= , = , <>
    	between...and
    	in(集合)
    	like:模糊查询
    		占位符：
    			_ :单个任意字符
    			% :多个任意字符
    	is null
    	and 或 &&
    	or  或 ||
    	not 或 ！
    	
```



###### JDBC

概念：Java DataBase Connectivity		Java数据库连接，Java语言操作数据库

```java
1.加载和注册驱动
    Class.forName("com.mysql.jdbc.Driver");
	注：从JDBC3开始，目前已经普遍使用的版本，可以不用注册驱动而直接使用。
2.DriverManager类
    管理和注册驱动，创建数据库的连接
    Connection getConnection(String url, String user, String password);//通过连接字符串， 用户名， 密码来得到数据库的连接对象
	Connection getConnection (String url, Properties info);//通过连接字符串， 属性对象来得到连接对象
3.Connection接口
    Statement createStatement();//创建一条sql语句对象
		int executeUpdate(String sql)；//用于发送 DML 语句，增删改的操作， insert、 update、 delete，参数： SQL 语句，返回值：返回对数据库影响的行数
        ResultSet executeQuery(String sql);//用于发送 DQL 语句，执行查询的操作。 select,参数： SQL 语句,返回值：查询的结果集
4.释放资源
    先开的后关，后开的先关。 ResultSet -> Statement -> Connection
```



###### 数据库连接池

概念：存放数据连接的容器（集合）。当系统初始化好后，容器被创建，容器中会申请一些连接对象，当用户来访问数据库时，从容器中获取连接对象，访问完之后，会将连接对象归还给容器。

实现：

​	标准接口：DataSource	javax.sql包下的

​	获取连接：getConnection();

​	归还连接：Connection.close();



###### BOM

概念：Browser Object Model	浏览器对象模型

​		将浏览器的各个组成部分封装成对象

组成：

* Window：窗口对象
* Navigator：浏览器对象
* Screen：显示器屏幕对象
* History：历史记录对象
* Location：地址栏对象



###### DOM

概念：Document Object Model	文档对象模型

​		将标记语言文档的各个组成部分，封装为对象。可以使用这些对象，对标记语言文档进行CRUD的动态操作。

 W3C DOM 标准被分为 3 个不同的部分：

* 核心 DOM - 针对任何结构化文档的标准模型
	* Document：文档对象
	* Element：元素对象
	* Attribute：属性对象
	* Text：文本对象
	* Comment:注释对象

	* Node：节点对象，其他5个的父对象
* XML DOM - 针对 XML 文档的标准模型
* HTML DOM - 针对 HTML 文档的标准模型



###### 事件监听机制

概念：某些组件被执行了某些操作后，触发某些代码的执行。



###### AJAX

Ajax是一种在无需重新加载整个网页的情况下，能够更新部分网页的技术。



###### JSON

JavaScript对象表示法

基本规则

1. 数据在名称/值对中，：json数据是由键值对构成的
   - 键用引号引起来，也可以不使用引号
   - 值的取值类型
2. 数据由逗号分隔：多个键值对由逗号分隔
3. 花括号保存对象：使用{ }定义json格式
4. 方括号保存数据：[ ]



