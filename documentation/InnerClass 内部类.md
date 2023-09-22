#### InnerClass 内部类

1.定义

将一个类A定义在另一个类B里边，类A就称为内部类，类B称为外部类。

![image-20230728153520799](..\pictures\内部类.png)

2.为什么需要内部类？

具体来说：当一个事物A的内部，还有一个部分需要一个完整的结构B需要描述，而这个内部的完整结构B又只为外部事物A提供服务，不在其它地方单独使用，那么整个内部的完整结构B最好使用内部类。

> 优点 ：```高内聚、低耦合```

3.举例

Thread类内部声明了State类，表示线程生命周期

HashMap类中声明了Node类，表示封装的key和value

4.内部类的分类

> 成员内部类:直接声明在外部类的里面
>
> > 使用static修饰的：静态成员内部类
> >
> > 不使用static修饰的：非静态的成员内部类
>
> 局部内部类:声明在方法内、构造器内、代码块内。
>
> > 匿名的局部内部类
> >
> > 非匿名的局部内部类

```java
public class OuterClassTest {
}
class  Person{
    //静态内部类
    static class Dog{
        
    }
    //非静态内部类
    class Bird{
        
    }
    public void method(){
        //局部内部类
        class InnerClass1{
            
        }
    }
}
```

5.成员内部类的理解

> ​     从类的角度看：
>
> 内部可以声明属性、方法、构造器、代码块、内部类等结构。
>
> 此内部类可以声明父类，可以实现接口
>
> 可以使用final修饰
>
> 可以使用abstract修饰

> ​     从外部类的成员的角度看：
>
> 在内部可以调用外部类的结构。比如：属性、方法等
>
> 除了使用public、缺省权限修饰之外，还可以protected、private修饰
>
> 可以使用static修饰

```java
public class OuterClassTest {
    public static void main(String[] args) {
        //创建静态成员内部类的实例
        Person.Dog dog = new Person.Dog();
        dog.eat();
        //创建非静态成员内部类实例
        Person p = new Person();
        Person.Bird bird=p.new Bird();
        bird.eat();
        bird.show("黄鹂");
        bird.show1();
    }
}
class  Person{
    String name="tom";
    int age=1;
    public void eat(){
        System.out.println("人吃饭");
    }

    //静态内部类
    static class Dog{
        public void eat(){
            System.out.println("狗吃骨头");
        }
    }
    //非静态内部类
    class Bird{
        String name="啄木鸟";
        public void eat(){
            System.out.println("鸟吃虫子");
        }
        public void show(String name){
            System.out.println("age = " +age);//省略了person.this
            System.out.println("name = " + name);
            System.out.println("name = " + this.name);
            System.out.println("name = " + Person.this.name);
        }
        public void show1(){
            eat();
            this.eat();
            Person.this.eat();
        }
    }
    public void method(){
        //局部内部类
        class InnerClass1{

        }
    }
}
```

```java
public class ObjectTest {
public static void main(String[] args) {
//    SubObject o = new SubObject();
//    o.test();
   new Object(){
        public void test(){
            System.out.println("尚硅谷");
        }
    }.test();
    A a=new A(){
        @Override
        public void test(){
            System.out.println("匿名对象A");
        }
    };
    a.test();
}
}
//class SubObject extends Object{
//    public void test(){
//        System.out.println("尚硅谷");
//    }
//}
//
class A{
    public  void test(){
        System.out.println("A");
    };
}
```