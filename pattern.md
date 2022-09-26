# 设计模式


<!-- vscode-markdown-toc -->
* 1. [单例模式的析构](#Singleton)

<!-- vscode-markdown-toc-config
	numbering=true
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->



---

##  1. <a name='Singleton'></a>单例模式的析构

**为什么要析构？**

如果单例模式中存在打开的文件或占用了资源

**怎么析构？**

[参考](https://blog.csdn.net/littesss/article/details/78413149)

1.采用静态指针实现的单例模式，直接在析构函数中delete会造成循环调用析构函数

2.在内部嵌套类（私有）的析构函数中析构（内部类的实例化对象要设置成static类型，在单例模式的类的构造函数中声明或者在类中声明都是可以的）

**问题：使用静态局部变量实现的单例模式要怎么在程序运行中销毁？**

局部静态变量（非静态指针）的生命周期是程序开始到程序结束，好像没法子？如果占用了资源那单独写一个释放资源的接口呢？需要考虑线程安全的问题？