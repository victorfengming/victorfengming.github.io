---  
title: 'JavaWeb笔记05-解决线程安全问题'  
tags: Java basis note
---  
  
  
* content  
{:toc}  
  
  
  
  

### 线程安全问题:
Servlet的service方法,每次被请求是,调用.

这个调用很特殊,是在新的子线程中调用的,当service方法执行完毕,子线程死亡了.

可以简单的理解为:service方法每次执行都是一个新的线程.


