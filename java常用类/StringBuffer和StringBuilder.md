## 介绍

String、StringBuffer、StringBuilder三者的异同

String:不可变的字符序列，底层使用char[]存储

StringBuffer:可变的字符序列 ，线程安全的，效率低，底层使用char[]存储

StringBuilder:可变的字符序列，线程不安全的，效率高，底层使用char[]存储

效率从高到低：StringBuilder>StringBuffer>String

源码分析：

```java
String str=new String();//char[] value=new char[0]

String str1=new String("abc");//char[] value =new char[]{'a','b','c'};

StringBuffer sb1=new StringBuffer();//char[] value=new char[16];底层创建了 一个长度是16的数组

System.out.println(sb1.length());//0

sb1.append('a');//value[0]='a';
sb1.append('b');//value[1]='b';

StringBuffer sb2=new StringBuffer("abc");//char[] value=new char["abc".length()+16]
System.out.println(sb2.length());//3

//扩容问题：如果要添加的数据底层数组盛不下，那就需要扩容底层数组
//默认情况下，扩容为原来容量的2倍+2，同时将原来数组中的元素复制到新的数组中
```



## 常用方法

1. StringBuffer append(xxx)：字符串拼接
2. StringBuffer delete(int start,int end)：删除指定位置的内容（左闭右开）
3. StringBuffer replace(int start,int end,String str)：把[start,end)位置替换为str
4. StringBuffer insert(int offset,xxx)：在指定位置插入xxx
5. StringBuffer reverse()：把当前字符序列逆转
6. public void setCharAt(int n,char ch)：替换指定位置的字符

























































