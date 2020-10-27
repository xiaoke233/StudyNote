## String类

> String:字符串

1. String 声明为final的，不可被继承

2. String实现了Serializable接口：表示String是支持序列化的

   实现了Comparable接口：表示String可以比较大小

3. String内部定义了final char[] value用于存储字符串数据

4. String：代表不可变的字符序列。简称：不可变性

   1. 当对字符串重新赋值时，需要重写指定内存区域赋值，不能使用原有的value进行赋值
   2. 当对现有的字符串进行连接操作时，也需要重新指定内存区域赋值，不能使用原有的value进行赋值
   3. 当调用String的replace()方法修改指定字符或字符串时，也需要重新指定内存区域

5. 通过字面量的方式（区别于new）给一个字符串赋值，此时的字符串声明在字符串常量池中。

6. 字符串常量池中不会存储相同内容的字符串

```java
        String s1="abc";//字面量的定义方式
        String s2="abc";

        System.out.println(s1 == s2);//比较s1和s2的地址值 true

        s1="hello";
        System.out.println(s1);//hello
        System.out.println(s2);//abc

        System.out.println("--------------------");

        String s3="abc";
        s3+="def";
        System.out.println(s3);//abcdef

        System.out.println("-----------------------");

        String s4="abc";
        String s5=s4.replace('a','m');
        System.out.println(s4);//abc
        System.out.println(s5);//mbc
```





> String对象的构建

String str="hello";

String s1=new String();//本质上this.value=new char[0];

```java
        String s1="hello";
        String s2="hello";
        String s3=new String("hello");
        String s4=new String("hello");

        System.out.println(s1 == s2);//true
        System.out.println(s1 == s3);//false
        System.out.println(s1 == s4);//false
        System.out.println(s3 == s4);//false

        System.out.println("----------------");

        Person p1=new Person("Tom",12);
        Person p2=new Person("Tom",12);

        System.out.println(p1.name.equals(p2.name));//true
        System.out.println(p1.name==p2.name);//true

        p1.name="Jerry";
        System.out.println(p2.name);//Tom
```

面试题：String s=new String("abc");方式创建对象，在内存中创建了几个对象？

两个。一个是堆空间中new结构，另一个是char[]对应的常量池中的数据:"abc"。



> String不同的拼接操作

```java
        String s1="hello";
        String s2="world";
        String s3="helloworld";
        String s4="hello"+"world";
        String s5=s1+"world";
        String s6="hello"+s2;
        String s7=s1+s2;

        System.out.println(s3 == s4);//true
        System.out.println(s3 == s5);//flase
        System.out.println(s3 == s6);//flase
        System.out.println(s3 == s7);//flase
        System.out.println(s5 == s6);//flase
        System.out.println(s5 == s7);//flase
        System.out.println(s6 == s7);//flase

        String s8=s5.intern();
        System.out.println(s3 == s8);//true
```



结论：

1. 常量与常量的拼接结果在常量池。且常量池中不会存在相同的常量。
2. 只要其中有一个变量，结果就在堆中。
3. 如果拼接的结果调用intern（）方法，返回值就在常量池中。



## 常用方法

1. **int length()**:返回字符串的长度
2. **char charAt(int index)**：返回索引处的字符
3. **boolean isEmpty()**：判断是否为空字符串
4. **String toLowerCase()**：将String中的所有字符转换为小写
5. **String toUpperCase()**：将String中的所有字符转换为大写
6. **String trim()**：返回字符串的副本，忽略前导空白和尾部空白
7. **boolean equals(Object obj)**：比较字符串的内容是否相同
8. **boolean equalsIgnoreCase(String anotherString)**：与equals方法类似，忽略大小写
9. **String concat(String str)**：将指定字符串连接到此字符串的结尾。等价于用“+”
10. **int compareTo(String anotherString)**：比较两个字符串的大小。返回第一个不相同字符的ASCii码差值
11. **String substring(int beginIndex)**：返回一个新字符串，它是此字符串从beginIndex开始截取到最后的一个子字符串
12. **String substring(int beginIndex,int endIndex)**：返回一个新字符串，它是字符串从beginIndex开始截取到endIndex（不包含）的一个子字符串。（左闭右开）
13. **boolean endsWith(String suffix)**:测试此字符串是否以指定的后缀结束
14. **boolean startsWith(string prefix)**:测试此字符串是否以指定的前缀开始
15. **boolean startsWith(string prefix,int roffset)**:测试此字符串从指定索引开始的子字符串是否以指定前缀开始
16. **boolean contains(CharSequence s)**：当且仅当此字符串包含指定的char值序列时，返回true
17. **int indexof(String str)**：返回自定子字符串在此字符串中第一次出现处的索引（未找到返回-1）
18. **int indexof(String str,int fromIndex)**：返回自定子字符串在此字符串中第一次出现处的索引，从指定的索引开始
19. **int lastIndexOf(string str)**：返回指定子字符串在此字符串中最右边出现处的索引（未找到返回-1）
20. **int lastIndexOf(string str,int fromIndex)**：返回指定子字符串在此字符串中最右边出现处的索引，从指定的索引开始反向搜索
21. **String replace(char oldChar,char newChar)：**返回一个新的字符串，它是通过用newChar替换此字符串中出现的所有oldChar得到的。
22. **String replace(CharSequence target,CharSequence replacement)：**使用指定的字面值替换序列替换此字符串所有匹配字面值目标序列的子字符串。
23. **String replaceAll(String regex,String repalcement)：**使用给定的replacement替换此字符串所有匹配给定的正则表达式的子字符串。
24. **String replaceFirst(String regex,String replacement)：**使用给定的replacement替换此字符串匹配给定的正则表达式的第一个子字符串。



## 类型转换

String -->基本数据类型、包装类

调用包装类的静态方法：parseXXX(str)

```java
String s1="123";
int num=Integer.parseInt(s1);
```

基本数据类型、包装类--->String

调用String重载的valueOf(XXX)

```java
String s2=String.valueOf(num);
```



String--->char[]       toCharArray()

```java
String s1="helloworld";
char[] charArray=s1.toCharArray();
```

char[]--->String

```java
char[] arr=new char[]{'h','e','l','l','o'};
String s2=new String(arr);
```



String--->byte[]    (编码)     getBytes()

```java
String s1="hello你好";
byte[] bytes=s1.getBytes();//使用默认的字符集，进行编码
System.out.println(Arrays.toString(bytes));
//[104, 101, 108, 108, 111, -28, -67, -96, -27, -91, -67]

byte[] gbks=s1.getBytes("gbk");//使用gbk字符集进行编码
System.out.println(Arrays.toString(gbks));
//[104, 101, 108, 108, 111, -60, -29, -70, -61]
```

byte[]--->String （解码） 

```java
String s2=new String(bytes);
System.out.println(s2);//hello你好

String s3=new String(gbks);
System.out.println(s3);//hello���    出现乱码

String s4=new String(gbks,"gbk");
System.out.println(s4);//hello你好
//解码使用的字符集必须与编码的字符集一致
```

















































