#### HashMap和HashSet

##### HashMap概述

HashMap是一个散列表，它的存储内容是键值对(key-value)的映射。

![image-20230629161748720](..\pictures\HashMap.png)

- HashMap是Map接口中使用频率最高的实现类
- HashMap是线程不安全的。允许添加null键和null值。
- 存储数据采用哈希表结构，底层使用一维数组+单向链表+红黑树进行Key-value进行数据存储。于HashSet一样，元素的存取顺序不能保持一致。
- HashMap判断两个key相等的标准是：两个key的HashCode值相等，通过equals()方法返回true。
- HashMap判断两个value相等的标准是：两个value通过equals()方法返回true。

##### HashMap类常用方法

###### 定义语法

```java
import java.util.HashMap;//导包

/**
 * @author by YangXinRan
 * @date 2023/6/29.
 */
public class Test07 {
    public static void main(String[] args) {
        HashMap<String, Integer> hashMap = new HashMap<>();//创建一个HashMap对象
    }
}
```

###### 添加元素

​		向HashMap中添加元素利用put(key,value)方法。添加时元素的key不能重复，如果重复，则会覆盖原先的value值。

```java
hashMap.put("yang",100);
```

###### 查找元素值

​		get(key)返回指定键所映射的值，即获取key对应的value，没有该key对应的值则返回null。

```java
hashMap.get("yang");//结果为100
hashMap.get("Tom");//结果为null
```

###### Map集合大小

​		size()返回Map集合中的数据量，也就是返回key-value的对数。

```java
hashMap.size();//结果为1
```

###### clear()清空集合

```java
hashMap.clear();
hashMap.size();//清空后的集合大小为0
```

###### isEmpty()判断

​		isEmpty()判断Map集合中是否有数据；如果没有返回true，否则为false。

```java
hashMap.put("zhang",50);
hashMap.isEmpty();//向hashMap中添加数据后，集合不为空，返回false
hashMap.clear();
hashMap.isEmpty();//清空数据后hashMap为空，返回true
```

###### 删除元素

​		remove(key)方法删除Map集合中键为key的数据并返回其对应的value值。

```java
hashMap.put("Jim",100);
hashMap.put("kebo",100);
hashMap.put("Sam",100);
int secore=hashMap.remove("Sam");//定义整数类型变量接收remove()方法返回的值。
```

###### 查找集合所有值

​		values()返回Map集合中所有value组成的以Collection数据类型格式存储的数据。一般用于遍历HashMap集合中的value值。

```java
Collection<Integer> score_1=hashMap.values();//定义Collection类型的变量接收返回的所有value
```

###### keySet()

​		keySet()返回Map集合中所有key组成的Set集合

```java
Set<String> set = hashMap.keySet();//定义一个Set类型的变量set接收返回的key集合
		for (String key : set) {
			System.out.println(key);//遍历HashMap集合中的key
```

###### *entrySet()

​		entrySet()将Map集合每一个key-value转换为一个Entry对象并返回由该对象组成的集合Set。

```java
Set<Entry<String, Integer>> set = hashMap.entrySet();//将每一组key-value变为一个entry对象存入set集合
		for (Entry<String, Integer> entry : set) {
			System.out.println(entry.getKey() + ":" + entry.getValue());//遍历key-value
		}
```

##### HashSet概述

HashSet是基于HashMap来实现的，是一个不允许有重复元素的集合。

- HashSet允许有null值
- HashSet是无序的，即不会记录插入顺序。
- HashSet实现了Set接口

##### HashSet类常用方法

###### 添加元素

​		使用add()，向Set里添加元素。

```java
import java.util.HashSet;

/**
 * @author by YangXinRan
 * @date 2023/6/29.
 */
public class Test07 {
    public static void main(String[] args) {
        HashSet<String> hashSet = new HashSet<>();
        hashSet.add("Tom");
        hashSet.add("Jom");
    }
}
```

###### 删除元素

​		使用remove删除Set里的元素。

```java
hashSet.remove("Tom"); System.out.println(hashSet);//输出结果为[Jom]
```

###### contains()

​		判断是否包含某一元素。

`bollean con=hashSet.contains("Jom");//con=true`

###### isEmpty()

​		判断是否为空isEmpty()。

`bollean isempty=hashSet.isEmpty();//isEmpty=false`

###### size()

​		获取Set集合大小

`int size=hashSet.size();`

![image-20230629172033159](C:\Users\33611\AppData\Roaming\Typora\typora-user-images\image-20230629172033159.png)