---  
title: 'spring笔记01'  
subtitle: '' 
tags: Java basis note Spring
---  

  
  
* content  
{:toc}  
  
  
  
  

### Spring 简介
Spring框架由Rod Johnson开发,2004年发布了 Spring框架的第一版.Spring是一个从实际开发中抽取出来的框架,因此它完成了大量开发中的通用步骤,留给开发者的仅仅是与特定应用相关的部分,从而大大提高了企业应用的开发效率.

Spring总结起来优点如下:
- 低侵入式设计,代码的污染极低.
- 独立于各种应用服务器,基于Spring框架的应用,可以真正实现Write Once,Run Anywhere的承诺.
- Spring的IoC容器降低了业务对象替换的复杂性,提高了组件之间的解耦.
- Spring的AOP支持允许将一些通用任务如安全,事务,日志等进行集中式管理,从而提供了更好的复用.
- Spring的高度开发性,并不强制应用完全依赖于Spring,开发者可自由选用Spring框架的部分或全部.

Spring框架的组成结构图如下所示:

![Spring组成结构图](/img/posts/java/spring/spring01.png)

### Spring 的核心机制
#### 管理Bean
程序主要是通过Spring容器来访问容器中的Bean,ApplicationContext是Spring容器最常用的接口,该接口如下两个实现类:

- ClassPathXMLApplicationContext:从类加载路径下搜索配置文件,并根据配置文件来创建Spring容器.
- FileSystemXMLApplicationContext:从文件系统的相对路径或绝对路径下去搜索配置文件,并根据配置文件来创建Spring容器.

```java
public class BeanTest{
    public static void main(String args[]) throws Exception{
        ApplicationContext ctx = new ClassPathXmlApplicationContext("beans.xml");
        Person p = ctx.getBean("person", Person.class);
        p.say();
    }
}
```
















