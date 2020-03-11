## 3.函数的定义与调用

本章内容包括：
> - 用于处理集合、字符串和正则表达式的函数
> - 使用命名参数、默认参数，以及中辍调用的语法
> - 通过扩展函数和属性来适配Java库
> - 使用顶层函数、局部函数和属性架构代码

### 1、在Kotlin中创建集合
```kotlin
// 支持数字创建
        val set = hashSetOf(1, 7, 53)

        // 用类似的方法创建一个 list 或 map:
        val list = arrayListOf(1, 7, 53)
        val map = hashMapOf(1 to "one", 7 to "seven, 53 to fifty-three")
        /**注意： to 并不是一个特殊的结构，而是一个普通函数。后面讨论。*/

        // javaClass 相当于 java 中的getClass()
        LogUtil.e(set.javaClass.toString())
        LogUtil.e(list.javaClass.toString())
        LogUtil.e(map.javaClass.toString())
        /**
         * class java.util.HashSet
         * class java.util.ArrayList
         * class java.util.HashMap
         * Kotlin 没有采用它自己的集合类，而是采用的标准的Java集合类。
         */

        // 获取最后一个元素
        val string = listOf("first", "second", "fourteenth")
        LogUtil.e(string.last())

        // 取最大值
        val numbers = setOf(1, 14, 2)
        LogUtil.e(numbers.max().toString())


        // 2.让函数更好的调用  测试
        val list2 = listOf(1, 2, 3)
        LogUtil.e(joinToString(list2, ";", "(", ")"))
```

### 2、让函数更好的调用
```kotlin
/**
     * val list = listOf(1,2,3)
     * println(list)    --- 触发了 toString()的调用
     * 默认输出  [1,2,3]
     * 想要效果  (1;2;3)
     *
     * joinToString() 的基本实现
     * 通过在元素中间添加分割符号，从直接重写实现函数开始，然后再过渡到Kotlin更惯用的方法来重写。
     */
    /**
     * @param collection 集合
     * @param separator 分割符
     * @param prefix 前缀
     * @param postfix 后缀
     * 有默认值的参数
     */
    fun <T> joinToString(collection: Collection<T>,
                         separator: String = ",",
                         prefix: String = "",
                         postfix: String = ""
    ): String {

        val result = StringBuilder(prefix)

        for ((index, element) in collection.withIndex()) {
            // 不用在第一个元素前添加分隔符
            if (index > 0) {
                result.append(separator)
            }
            result.append(element)
        }
        result.append(postfix)
        return result.toString()
    }
```

```kotlin
 /*---------------2.1、命名参数---------------*/
        joinToString(collection = list2, separator = "", prefix = "", postfix = ".")

        /*---------------2.2、默认参数值  解决 [重载] 重复问题---------------*/
//        fun <T> joinToString(
//                collection: Collection<T>,
//                separator: String = ",",
//                prefix: String = "",
//                postfix: String = ""
//        ): String {
//
//        }


        LogUtil.e(joinToString(list2))
        LogUtil.e(joinToString(list2, ";"))
        LogUtil.e(joinToString(list2, ",", ",", ","))
        LogUtil.e(joinToString(list2, postfix = ",", prefix = "#"))

        /*---------------2.3、消除静态工具类：顶层函数和属性---------------*/
        /*
         *  顶层函数:
         *  声明joinToString()作为顶层函数
         *  新建 strings 包，里面直接放置 joinToStrings
         */
        joinToStrings(list2, ",", ",", ",")
```

```kotlin
package com.kotlin.jingbin.kotlinapp.function.strings

import com.kotlin.jingbin.kotlinapp.utils.LogUtil

/**
 * Created by jingbin on 2019/1/28.
 * 3.2.3、消除静态工具类：顶层函数和属性
 */
fun <T> joinToStrings(collection: Collection<T>,
                      separator: String = ",",
                      prefix: String = "",
                      postfix: String = ""): String {

    val result = StringBuilder(prefix)

    for ((index, element) in collection.withIndex()) {
        // 不用在第一个元素前添加分隔符
        if (index > 0) {
            result.append(separator)
        }
        result.append(element)
    }
    result.append(postfix)
    return result.toString()
}


// 声明一个 顶层属性
var opCount = 0

// 改变属性的值
fun performOperation() {
    // 改变属性的值
    opCount++
    // ...
}

// 读取属性的值
fun reportOperationCount() {
    LogUtil.e("Operation performed $opCount times")
}

// 如果是val就只有一个getter，如果是var就对应一对getter和setter

const val UNIX_LINE_SEPATOR = "\n"
// 等同于 Java
//public static final String UNIX_LINE_SEPATOR = "\n";


/*
* String: 接受者类型
* this: 接受者对象
* */
fun String.lastChar(): Char = this.get(this.length - 1)
```

### 3.给别人的类添加方法：扩展函数和属性
类 `join.kt`:

```kotlin
/**
 * 扩展函数：
 * String: 接受者类型
 * this: 接受者对象
 * */
fun String.lastChar(): Char = this.get(this.length - 1)

fun String.lastChar2(): Char = get(length - 1)

/**
 * 扩展属性：
 * */
val String.lastChar: Char
    get() = get(length - 1)

/**
 * 可变的扩展属性：
 */
var StringBuilder.lastChar2: Char
    // getter 属性
    get() = get(length - 1)
    // setter 属性
    set(value: Char) {
        this.setCharAt(length - 1, value)
    }

```

```kotlin
        LogUtil.e("Kotlin".lastChar())

        /*---------------3.1、导入和扩展函数---------------*/
        // import com.kotlin.jingbin.kotlinapp.function.strings.lastChar
        val lastChar = "Kotlin".lastChar()
        // 可以用关键字as 来修改导入的类或者函数名称:  [可以用来解决命名冲突]
        // import com.kotlin.jingbin.kotlinapp.function.strings.lastChar as last
        val last = "Kotlin".last()


        /*---------------3.2、从Java中调用扩展函数---------------*/
        // java    -->   StringUtil.lastChar("Kotlin");
        // java    -->   lastChar("Kotlin");
        // kotlin  -->   "Kotlin".lastChar()


        /*---------------3.3、作为扩展函数的工具函数---------------*/
        // joinToString 函数的终极版本，和kotlin标准库中看到的一模一样
        // 为Collection<T> 声明一个扩展函数
        fun <T> Collection<T>.joinToString(separator: String = ",", prefix: String = "", postfix: String = ""): String {
            val result = StringBuilder(prefix)

            for ((index, element) in this.withIndex()) {
                // 不用在第一个元素前添加分隔符
                if (index > 0) {
                    result.append(separator)
                }
                result.append(element)
            }
            result.append(postfix)
            return result.toString()
        }
        LogUtil.e(list2.joinToString(";", "((", "))"))

        // 扩展函数无非是静态函数的一个高效语法糖
        fun Collection<String>.join(separator: String = ",", prefix: String = "", postfix: String = "") = joinToString(separator, prefix, postfix)

        LogUtil.e(listOf("one", "two", "eight").join(" "))


        /*---------------3.4、不可重写的扩展函数---------------*/
        // 在Kotlin中，重写成员函数是很平常的一件事情。但是，不能重写扩展函数。

        /**这是扩展函数的写法！扩展了 View.class 的函数方法*/
        fun View.showOff() = LogUtil.e("I'm a view")

        /**
         * 这是扩展函数的写法！扩展了 Button.class 的函数方法。
         * 而 Button 继承于 View ,但是输出为 View的扩展函数的内容，因为 “扩展函数并不存在重写，因为Kotlin会把它们当做作静态函数对待”
         * 如果 Button 直接重写 View 类里面的 showOff() ，则是生效的，因为不是扩展函数，写法不一样！！
         * */
        fun Button.showOff() = LogUtil.e("I'm a Button")

        val view: View = Button(this)
        LogUtil.e(view.showOff()) //  I'm a view
        // 扩展函数并不存在重写，因为Kotlin会把它们当做作静态函数对待


        /*---------------3.5、扩展属性  join.kt  ---------------*/
        // val kotlin.String.lastChar: Char
        //     get() = get(length - 1)
        "Kotlin".lastChar
        val builder = StringBuilder("Kotlin?")
        builder.lastChar2 = '!'
        LogUtil.e(builder) // Kotlin!
```

### 4.处理集合: 可变参数、中辍调用和库的支持
这一节将会展示 Kotlin 标准库中用来处理集合的一些方法。另外也会涉及几个相关的语法特性：

 - 可变参数的关键字 vararg ,可以用来声明一个函数将可能有任意数量的参数。
 - 一个`中辍`表示法，当你在调用一些只有一个参数的函数时，使用它会让代码更简练
 - `解构声明`，用来把一个单独的组合值展开到多个变量中


```kotlin
        /*---------------4.1、扩展 Java集合的API  ---------------*/

        // 基于 Kotlin中的集合与Java的类相同，但是对API做了扩展。
        val strings = listOf("first", "second", "fourteenth")
        LogUtil.e(strings.last())
        val of = setOf(1, 15, 3)
        val numbers2: Collection<Int> = setOf(1, 14, 2)
        println(of.max())       //15
        println(numbers2.max()) //14


        /*---------------4.2、可变参数: 让函数支持任意数量的参数  ---------------*/

        // 当你创建一个函数列表的时候，可以传任意个人的参数给它
        val listOf = listOf(2, 3, 4, 5, 6)
        // 如果看看这个函数在库中的声明：
        fun <T> listOf(vararg elements: T): List<T> = if (elements.size > 0) elements.asList() else emptyList()

        /**
         * 可变参数与Java类似
         * 不同点：
         *  - java   使用的是 三个点
         *  - kotlin 使用的是 vararg
         *
         *  另一个区别：当需要传递的参数已经包装在数组中时，调用该函数的语法。
         *  技术来讲，这个功能称为  展开运算符，使用的时候不过是在对应的参数前面放一个 *
         */
        fun main(args: Array<String>) {
            // 展开运算符展开数组内容
            val list = kotlin.collections.listOf("args:", *args)
            println(list)
        }


        /*---------------4.3、键值对的处理：中辍调用和解构声明  ---------------*/

        // 可以使用 mapOf 函数来创建map:
        val mapOf = mapOf(1.to("one"), 2 to "two", 7 to "seven")
        /**
         *  单词 to 不是内置的结构，而是一种特殊的函数调用，被称为 中辍调用。
         *  中辍调用中，没有添加额外的分隔符，函数名称是直接放在目标对象名称和参数之间的。
         *  等价：
         *   - 1.to("one")   // 一般 to 函数的调用
         *   - *  2 to "two" // 使用中辍符号调用的 to 函数
         */

        // 如果使用中辍符号，需要使用 infix 修饰符类标记它 (Any 超类)
        infix fun Any.to(ohther: Any) = Pair(this, ohther)


        /**
         * 解构声明：
         * 用 to 函数创建一个pair，然后用解构声明来展开
         */
        val (number, name) = 1 to "one"
        LogUtil.e(number)
        LogUtil.e(name)


        // 解构声明不止运用于 pair 也适用于循环
        // 打印 val strings = listOf("first", "second", "fourteenth")
        for ((index, element) in strings.withIndex()) {
            LogUtil.e("$index: $element")
        }
```

### 5.字符串和正则表达式的处理
```kotlin
        /*---------------5.1 分割字符串  ---------------*/
        val split = "12.345-6.A".split(".")
        // 指定多个分隔符
        val split2 = "12.345-6.A".split(".", "-")

        // 12 345-6  A
        LogUtil.e(split)
        // 12  345  6   A
        LogUtil.e(split2)
        // java处理
        SetOfJava().start()


        /*---------------5.2 正则表达式和三重引号的字符串---------------*/

        // 使用String的扩展函数来解析文件路径
        fun parsePath(path: String) {
            val directory = path.substringBeforeLast("/")
            val fullName = path.substringAfterLast("/")
            val fileName = fullName.substringBeforeLast(".")
            val extension = fullName.substringBeforeLast(".")
            LogUtil.e("Dir: $directory, name: $fileName, ext: $extension")
        }
        parsePath("/Users/yole/kotlin-book/chapter.adoc")

        // 使用正则表达式解析文件路径
        fun parsePath2(path: String) {
            val toRegex = """(.+)/(.+)\.(.+)""".toRegex()
            val matchResult = toRegex.matchEntire(path)
            if (matchResult != null) {
                val (directory, fileName, extension) = matchResult.destructured
                LogUtil.e("Dir2: $directory, name2: $fileName, ext2: $extension")
            }
        }
        parsePath2("/Users/yole/kotlin-book/chapter.adoc")

        """  (.+)        /     (.+)       \.         (.+)"""
        """  目录   最后一个斜线  文件名    最后一个点     扩展名"""


        /*---------------5.3 多行三重引号的字符串---------------*/
        val kotlinLogo = """|//
            .|//
            .|/\"""
        // trimMargin 来删除每行中的前缀和前面的空格
        LogUtil.e(kotlinLogo.trimMargin("."))
        /*
        |//
        |//
        |/\
        */

        // 不用转义字符 \
        """C://Users\yole\kotlin-book"""
        // 使用美元💲字符
        """${'$'}99.9"""
```

### 6.让你的代码更整洁：局部函数和扩展
```kotlin

        // 带重复代码的函数
        class User(val id: Int, val name2: String, val address: String)

        fun saveUser(user: User) {
            if (user.name2.isEmpty()) {
                throw IllegalArgumentException("Can't save user ${user.name2}: empty Name")
            }

            if (user.address.isEmpty()) {
                throw IllegalArgumentException("Can't save user ${user.address}: empty Address")
            }
            // 保存user到数据库
        }

        // 提取局部函数避免重复 -->  在局部函数中访问外层函数的参数 --> 提取逻辑到扩展函数
        fun saveUser2(user: User) {
            fun validate(user: User, value: String, field: String) {
                if (value.isEmpty()) {
                    // 可以直接访问外部函数的参数
                    throw IllegalArgumentException("Can't save user ${user.id}: empty $field")
                }
            }

            // 在局部函数中访问外层函数的参数
            // 不需要在 saveUser2 函数中重复 user 参数
            fun validate2(value: String, field: String) {
                if (value.isEmpty()) {
                    throw IllegalArgumentException("Can't save user ${user.id}: empty $field")
                }
            }
            validate(user, user.name2, "Name")
            validate2(user.name2, "Name")
        }

        // 提取逻辑到扩展函数
        fun User.validateBeforeSave() {
            fun validate3(value: String, fieldName: String) {
                if (value.isEmpty()) {
                    // 可以直接访问 user 的属性
                    throw IllegalArgumentException("Can't save user $id: empty $fieldName")
                }
            }
            validate3(name2, "Name")
            validate3(address, "Address")
        }

        fun saveUser3(user: User) {
            // 扩展函数
            user.validateBeforeSave()
            // 保存user到数据库
        }

        // java.lang.IllegalArgumentException: Can't save user 2: empty Name
        saveUser3(User(2, "haha", "china"))
```

### 总结
 - Kotlin 没有定义自己的集合类，而是在Java集合类的基础上提供了更丰富的API。
 - Kotlin 可以给函数参数定义默认值，这样大大降低了重载函数的必要性，而且命名参数让多参数函数的调用更加易读。
 - Kotlin 允许更灵活的代码结构：函数和属性都可以直接在文件中声明，而不仅仅在类中作为成员。
 - Kotlin 可以用扩展函数和属性来扩展任何类的API,包括在外部中定义的类，而不需要修改其源代码，也没有运行时的开销。
 - 中辍调用提供了处理单个参数的，类似调用运算符方法的简明语法。
 - Koltin 为普通字符串和正则表达式都提供了大量的方便字符串处理的函数。
 - 三重引号的字符串提供了一种简洁的方式，解决了原本在Java中需要进行大量啰嗦的转义和字符串连接的问题。
 - 局部函数帮助你保持代码的整洁的同时，避免重复。







