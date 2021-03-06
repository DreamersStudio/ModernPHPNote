## Modern PHP学习笔记
>### PHP: Hypertext Preprocessor
***
# 第2章
***
## 特性
>### 命名空间
- 命名空间在PHP 5.3.0中引入，是一个很重要的工具，其作用是按照一种虚拟的层次结构组织PHP代码，这种层次结构雷西操作系统中文件系统的目录结构。现代的PHP组件和框架都放在各自的全局唯一的厂商命名空间中，以免与其他厂商使用的常见类名冲突。
- 命名空间（或子命名空间）的作用是封装和组织相关的PHP类，就像在文件系统中把相关的文件放在同一个目录中一样。[从技术层面来看，命名空间只是PHP语言中的一种记号，PHP解释器会将其作为前缀添加到类、接口、函数和常量的名称前面。]

>### 为什么使用命名空间
- 在大型项目中，如果引入大量的依赖，可能会存在类名冲突的问题，使用命名空间可以解决这个问题。

>### 声明命名空间
- ```<?php namespace Oreilly\ModernPHP;```

>### 导入和别名
- ```<?php 
	use Symfony\Component\HttpFoundation\Response as Res;
	$r = new Res('Oops', 400);
	$r->send();``` 
- use关键字必须出现在全局作用域中（即不能字类或函数中），因为这个关键字在编译时使用。不过，use关键字可以在命名空间声明语句之后使用，导入其他命名空间中的代码。
- 从PHP 5.6开始可以导入函数和常量。用法：
- 导入函数```<?php 
	use func Namespace\functionName;
	functionName();```
- 导入常量```<?php 
	use constant Namespace\CONST_NAME;
	echo CONST_NAME;```
- **其中函数和常量的别名雨类别名的创建方式一样**

>### 实用技巧 
- 多重导入
 - ```<?php
		use Symfony\Component\HttpFoundation\Request;
		use Symfony\Component\HttpFoundation\Respose;
		use Symfony\Component\HttpFoundation\Cookie;
	   ```
- 全局命名空间
 - 有些代码可能没有命名空间，这些代在全局命名空间中。PHP原生的Exception类就是如此。在命名空间中引用全局没看见中的代码时，要在类、接口、函数或常量名称前加上\符号。
- 自动加载 
 - 命名空间为PHP Framework Interop Group（PHP-FIG）制定的PSR-4自动加载器标准奠定基础。Composer可以自动加载项目的依赖。
