# JDBC 与 MyBatis

## 🔌 JDBC

JDBC 是一种 **Java API**，允许 Java 程序与数据库进行连接和交互，它定义了标准，如图所示。

![](images/2026-08-27-23-13-39-2026-08-27-22-48-21-image.png)

如果用原生 JDBC，会有大量重复代码。

## 🧩 MyBatis

MyBatis 就是**把 JDBC 的那些重复代码封装掉**，其底层还是基于 JDBC。

---

## ⚖️ ORM 框架对比

| 框架 | 特点 |
|---|---|
| **MyBatis** | 半 ORM，SQL 自己写，灵活，互联网后端主流 |
| **JPA / Hibernate** | 全 ORM，几乎不用写 SQL，封装太重，SQL 不好调优 |

---

## 🔗 关联知识点
- [[MySQL索引]] - 数据库性能优化
- [[SpringBoot]] - MyBatis/Repository 常与 Spring 整合
- [[接口]] - Dao/Mapper 层通过接口定义
- [[框架]] - MyBatis 是持久层框架