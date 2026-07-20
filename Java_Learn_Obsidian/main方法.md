# main方法

Java程序的入口，是一个特殊的[[static关键字|静态方法]]。

---

## 🎯 特点
main方法本身也是一个静态方法，[[static关键字]]的三个原则全部适用：
1. 只能直接访问静态成员
2. 不能直接访问非静态成员（需要对象）
3. 没有[[this关键字]]

```java
public static void main(String[] args) {
    // 程序入口
}
```

---

## 🔗 关联知识点
- [[static关键字]] - main是静态方法
- [[this关键字]] - 静态方法中无this
- [[面向对象基础]] - 程序入口
