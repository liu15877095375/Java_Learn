# == 和 equals 的区别

Java 面试超高频考点，也是日常写代码踩坑最多的地方。

## 一、== 运算符

`==` 是运算符，作用分两种场景：

1. **作用于基本数据类型**（int、double、char、boolean 等）：比较的是**数值本身是否相等**。
2. **作用于引用数据类型**（对象、数组、字符串等）：比较的是**内存地址是否相等**，也就是判断两个引用是不是指向堆中同一个对象。

## 二、equals() 方法

`equals()` 是 `Object` 类的方法，所有 Java 类都继承了这个方法，它的行为取决于类有没有重写它：

1. **默认实现（没重写）**：和 `==` 完全等价，比较对象的内存地址。
2. **重写后**：绝大多数常用类（`String`、`Integer`、`ArrayList` 等）都重写了 `equals()`，改成比较**对象的内容是否相等**。

## 三、代码示例

### 1. 基本类型与引用类型的对比

```java
// 基本类型：== 比数值
int a = 10;
int b = 10;
System.out.println(a == b); // true

// 自定义类：没重写equals，== 和 equals 都比地址
class Person {
    String name;
    Person(String name) { this.name = name; }
}
Person p1 = new Person("张三");
Person p2 = new Person("张三");
System.out.println(p1 == p2);        // false，两个不同对象，地址不同
System.out.println(p1.equals(p2));   // false，默认equals和==一致
```

### 2. 最容易踩坑的 String 场景

```java
String s1 = "abc";          // 字面量，存在字符串常量池
String s2 = "abc";          // 复用常量池里的同一个对象
String s3 = new String("abc"); // new 出来的，在堆里新建对象

System.out.println(s1 == s2);      // true，同一个常量池对象，地址相同
System.out.println(s1 == s3);      // false，一个在常量池，一个在堆，地址不同
System.out.println(s1.equals(s3)); // true，String重写了equals，只比内容
```

## 四、常见误区总结

- ❌ 误区：`==` 比地址，`equals` 比内容
  ✅ 事实：`equals` 默认就是比地址，只有类主动重写后才会比内容。自己写的类如果不重写，`equals` 和 `==` 没有区别。
- ❌ 误区：字符串比较用 `==` 就行
  ✅ 事实：只有字面量赋值的字符串会进入常量池复用，业务代码中接收的字符串大多是动态生成的，**字符串比较一律用 `equals()`**。

## 🔗 关联知识点
- [[String类]] - 字符串常量池、重写 equals 只比内容
- [[Object类]] - equals 方法的源头、默认实现
- [[值传递]] - 引用类型传地址副本，与 == 比地址同源
- [[HashSet]] - 重写 equals 时通常要一并重写 hashCode