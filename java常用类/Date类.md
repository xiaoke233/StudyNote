java.util.Date类

​    |--- java.sql.Date类



1.两个构造器的使用

2.两个方法的使用

toString()：显示当前的年、月、日、时、分、秒

getTime()：获取当前Date对象对应的毫秒数（时间戳）

```java
Date d1=new Date();
System.out.println(d1.toString());//Thu Oct 22 16:43:19 CST 2020
System.out.println(d1.getTime());//1603356199077
        
Date d2=new Date(1603356199077L);//long型
System.out.println(d2.toString());//Thu Oct 22 16:43:19 CST 2020
System.out.println(d2.getTime());//1603356199077
```



将java.util.Date对象转换为java.sql.Date对象

```java
Date d4=new java.sql.Date(122354353453L);
java.sql.Date d5=(java.sql.Date)d4;

Date d6=new Date();
java.sql.Date d7=new java.sql.Date(d6.getTime());
```











































