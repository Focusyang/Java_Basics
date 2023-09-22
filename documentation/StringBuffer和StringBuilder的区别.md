#### StringBuffer和StringBuilder的区别

##### 一、StringBuffer和StringBuilder的相同之处

1、都继承了AbstractStringBuilder抽象类，实现了CharSequence和Appendable接口。

 ![image-20230626091629285](/pictures/StringBuffer和StringBuilder.png)

2、append方法都是super.append(str),调用了父类AbstractStringBuilder的append(String str)方法。

```java
    @Override
    public StringBuilder append(String str) {
        super.append(str);
        return this;
    }
 
    @Override
    public synchronized StringBuffer append(String str) {
        toStringCache = null;
        super.append(str);
        return this;
    }
```

3、扩容机制：StringBuffer和StringBuilder的扩容机制都是(初始容量)*2+2;初始容量都是16个字符。

4、底层都是用Char[]字符型数组实现的，且字符型数组都是可变的。这与String不同。

##### 二、StringBuffer和StringBuilder的不同之处

（1）线程安全性

StringBuffer：线程安全；StringBuilder：线程不安全

这是因为StringBuffer几乎所有的方法都使用synchronized实现了同步，线程比较安全，在多线程系统中可以保证数据同步；而StringBuilder 没有实现同步，线程不安全，在多线程系统中不能使用 StringBuilder。

```java
  @Override
    public synchronized StringBuffer append(String str) {
        toStringCache = null;
        super.append(str);
        return this;
    }

```

**用于实现多线程同步。它可以用于修饰方法或代码块，确保在同一时间只有一个线程可以访问被synchronized修饰的方法或代码块。*

（2）性能

StringBuffer是线程安全的，所有公开方法都是同步的，而StringBuilder是没有对方法加锁同步的，所以StringBuilder的性能要远大于StringBuffer。

**相同情况下使用 StringBuilder 相比使用 StringBuffer 仅能获得 10%~15% 左右的性能提升，但却要冒多线程不安全的风险。而在现实的模块化编程中，负责某一模块的程序员不一定能清晰地判断该模块是否会放入多线程的环境中运行，因此：除非确定系统的瓶颈是在 StringBuffer 上，并且确定你的模块不会运行在多线程模式下，才可以采用 StringBuilder；否则还是用 StringBuffer。*

（3）作用领域

- StringBuffer作用于多线程操作字符串(大量数据）
- StringBuilder作用于单线程操作字符串(大量数据）

##### 三、StringBuffer类、StringBuilder类API文档

（1）[StringBuffer](https://www.apiref.com/java11-zh/java.base/java/lang/StringBuffer.html)API文档

（2）[StringBuilder](https://www.apiref.com/java11-zh/java.base/java/lang/StringBuilder.html)API文档
