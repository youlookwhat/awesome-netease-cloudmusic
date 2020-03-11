### Kotlin | 1.定义和目的

- 书籍：[《Kotlin实战》](https://book.douban.com/subject/27093660/)

<!-- more -->

本章内容包括：
> - Kotlin 的基本示范
> - Kotlin 语言的主要特征
> - Android 和服务端开发的可能性
> - Kotlin 与其他语言的区别
> - 用 Kotlin 编写并运行代码


 - Kotlin和Java一样是一种静态类型的编程语言。编译时即可检查代码正确性。动态语言：Groovy,JRuby。
 - 根据上下问判断变量类型： val x=1
 - 性能、可靠性、可维护性、工具支持。

---

支持函数式编程风格，不强制使用：

 - 函数类型，允许函数接受其他函数作为参数，或者返回其他函数。
 - lambda表达式
 - 数据类，提供了创建不可变值对象的简明语法
 - 标准库中包含了丰富的API集合，让你用函数式编程风格操作对象和集合。

---
自动检查空指针：

 - val s: String? = null  可以为null，也会检查，禁止可能导致的空指针
 - val s2: String = ""    不能为null

避免类型转换异常：

```kotlin
if(value is String)               检查类型
  println(value.toUpperCase())    调用该类型的方法
```

---

 - 源代码文件存放在后缀名为.kt的文件中，编辑器生成.class文件。
 - AndriodSdudio中使用：**"Setting(设置) - Plugins(插件) - Install JetBrains Plugin - Kotlin"**