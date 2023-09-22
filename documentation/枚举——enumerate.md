#### 枚举——enumerate

##### 1.理解

枚举类型本质上是一种类，只不过这个类的对象是有限的，固定的几个，不能让用户随意创建。

##### 2.举例

- 星期：Monday(星期一)......Sunday(星期天）
- 性别：Man(男)、Woman(女)  
- 月份：January(1 月)......December(12 月) 
- 季节：Spring(春节)......Winter(冬天)
- 三原色：red(红色)、green(绿色)、blue(蓝色) 
- 支付方式：Cash（现金）、WeChatPay（微信）、Alipay(支付宝)、 BankCard(银行卡)、CreditCard(信用卡) 
- 就职状态：Busy(忙碌)、Free(空闲)、Vocation(休假)、Dimission(离职) 
-  订单状态：Nonpayment（未付款）、Paid（已付款）、Fulfilled（已配货）、 Delivered（已发货）、Checked（已确认收货）、Return（退货）、Exchange （换货）、Cancel（取消）
-  线程状态：创建、就绪、运行、阻塞、死亡 

• 若枚举只有一个对象, 则可以作为一种单例模式的实现方式。

##### 3.jdk5.0中自定义枚举类

```java
public class SeasonTest {
    public static void main(String[] args) {
        System.out.println(Season.SPRING.toString());
    }
}
//jdk5.0之前定义枚举方式
class Season{
    //声明当前类的对象的实例变量
    private final String seasonName;
    private final String seasonDesc;
    private Season(String seasonName, String seasonDesc){

        this.seasonName = seasonName;
        this.seasonDesc = seasonDesc;
    }

    public String getSeasonName() {
        return seasonName;
    }

    public String getSeasonDesc() {
        return seasonDesc;
    }
    public static final Season SPRING=new Season("春天","春暖花开");
    public static final Season SUMMER=new Season("夏天","夏日炎炎");
    public static final Season AUTUMN=new Season("秋天","秋高气爽");

    public static final Season WINTER=new Season("冬天","白雪皑皑");

    @Override
    public String toString() {
        return "Season{" +
                "seasonName='" + seasonName + '\'' +
                ", seasonDesc='" + seasonDesc + '\'' +
                '}';
    }
}
```

##### 4.jdk5.0中enum关键字定义枚举类

```java
public class SeasonTest1 {
    public static void main(String[] args) {
        System.out.println(Season1.SPRING.toString());
        System.out.println(Season1.SPRING.getClass());
        System.out.println(Season1.SPRING.getClass().getSuperclass());
    }
}
enum Season1 {
    SPRING("春天","春暖花开"),
    SUMMER("夏天","夏日炎炎"),
    AUTUMN("秋天","秋高气爽"),

    WINTER("冬天","白雪皑皑");
    private final String seasonName;
    private final String seasonDesc;

    Season1(String seasonName, String seasonDesc) {
        this.seasonName = seasonName;
        this.seasonDesc = seasonDesc;
    }

    public String getSeasonName() {
        return seasonName;
    }

    public String getSeasonDesc() {
        return seasonDesc;
    }

    @Override
    public String toString() {
        return "Season1{" +
                "seasonName='" + seasonName + '\'' +
                ", seasonDesc='" + seasonDesc + '\'' +
                '}';
    }
}
```

##### 5.常用方法

```java
public class SeasonTest1 {
    public static void main(String[] args) {
        System.out.println(Season1.SPRING.toString());
        System.out.println(Season1.SPRING.name());
        //static 枚举类型[] values():返回枚举类型对象数组，该方法可以很方便的遍历枚举类型的所有枚举值。静态方法
        Season1[] values=Season1.values();
        for (Season1 s:values
             ) {
            System.out.println(s);
        }
        //valuesOf(String objName):返回当前枚举类中名称为objName的枚举类对象。
        //如果枚举类中不存在objName对象，则报错
        String seasonName="WINTER";
        System.out.println(Season1.valueOf(seasonName));
        //int ordinal():返回当前枚举常量的次序号，默认从O开始。
        System.out.println(Season1.WINTER.ordinal());
    }
}
```