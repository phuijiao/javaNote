# 1 概览

String被声明为final，因此它不可被继承。（Integer等包装类也不能被继承）

在Java8中，String内部使用char数组存储数据。

在Java9之后，String类的实现改用byte数组存储字符串，同时使用coder来标识使用了哪种编码。



# 2 不可变的好处

1. **可以缓存hash值。**

   因为String的hash值经常被使用，例如String用作HashMap的key。不可变的特性可以使得hash值也不可变，因此只需要进行一次计算。

2. **String Pool的需要。**

   如果一个String对象已经被创建过，那么就会从String Pool中取得引用。只有String是不可变的，才可能使用String Pool。

3. String经常作为参数，String不可变性可以保证参数不可变。

4. String不可变性天生具备线程安全，可以在多个线程中安全地使用。



# 3 String Pool

字符串常量池（String Pool）保存着所有字符串字面量（literal strings)，这些字面量在编译时期就确定。不仅如此，还可以使用String的intern()方法在运行过程中将字符串添加到String Pool中。

当一个字符串调用intern()方法时，如果String Pool中已经存在一个字符串和该字符串值相等，那么就会返回String Pool中字符串的引用；否则，就会在String Pool中添加一个新的字符串，并返回这个字符串的引用。

在Java7之前，String Pool被放在运行时常量池中，它属于永久代。而在Java7，String Pool被移动到堆中。这是因为永久代的空间有限，在大量使用字符串的场景下会导致OOM错误。

