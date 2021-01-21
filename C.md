# gcc
- QT gcc path
 `D:\Programs\QT\Tools\mingw810_64\bin`

| 选项        | 含义                              |
| ----------- | --------------------------------- |
| \-o file    | 指定生成的输出文件名为file        |
| \-E         | 只进行预处理 ,生成`.i`            |
| \-S\(大写\) | 只进行预处理和编译,生成`.s`       |
| \-c\(小写\) | 只进行预处理、编译和汇编,生成`.o` |


| ***\*文件后缀\**** | ***\*含义\****        |
| ------------------ | --------------------- |
| .c                 | C 语言文件            |
| .i                 | 预处理后的 C 语言文件 |
| .s                 | 编译后的汇编文件      |
| .o                 | 编译后的目标文件      |

| ***\*整型常量\**** | ***\*所需类型\****         |
| ------------------ | -------------------------- |
| 10                 | 代表int类型                |
| 10l, 10L           | 代表long类型               |
| 10ll, 10LL         | 代表long long类型          |
| 10u, 10U           | 代表unsigned int类型       |
| 10ul, 10UL         | 代表unsigned long类型      |
| 10ull, 10ULL       | 代表unsigned long long类型 |

| ***\*打印格式\**** | ***\*含义\****             |
| ------------------ | -------------------------- |
| %hd                | 输出short类型              |
| %d                 | 输出int类型                |
| %ld                | 输出long类型               |
| %lld               | 输出long long类型          |
| %hu                | 输出unsigned short类型     |
| %u                 | 输出unsigned int类型       |
| %lu                | 输出unsigned long类型      |
| %llu               | 输出unsigned long long类型 |


- 输入/输出函数家族

| 家族名  | 目的       | 可用于所有流 | 只用于stdin和stdout |
| ------- | ---------- | ------------ | ------------------- |
| getchar | 字符输入   | fgetc、getc  | getchar             |
| putchar | 字符输出   | fputc、putc  | putchar             |
| gets    | 文本行输入 | fgets        | gets                |
| puts    | 文本行输出 | fputs        | puts                |
| scanf   | 格式化输入 | fscanf       | scanf               |
| printf  | 格式化输出 | fprintf      | printf              |







## include头文件包含

- #include的意思是头文件包含，#include <stdio.h>代表包含stdio.h这个头文件
- 使用C语言库函数需要提前包含库函数对应的头文件，如这里使用了printf()函数，需要包含stdio.h头文件
- 可以通过`man 3 printf`查看printf所需的头文件

# # 动态库的封装和使用

## **12.1 库的基本概念**

库是已经写好的、成熟的、可复用的代码。每个程序都需要依赖很多底层库，不可能每个人的代码从零开始编写代码，因此库的存在具有非常重要的意义。

在我们的开发的应用中经常有一些公共代码是需要反复使用的，就把这些代码编译为库文件。

库可以简单看成一组目标文件的集合，将这些目标文件经过压缩打包之后形成的一个文件。像在Windows这样的平台上，最常用的c语言库是由集成按开发环境所附带的运行库，这些库一般由编译厂商提供。

## **12.2 windows下静态库创建和使用**

### **12.2.1 静态库的创建**

\1. 创建一个新项目，在已安装的模板中选择“常规”，在右边的类型下选择“空项目”，在名称和解决方案名称中输入staticlib。点击确定。

2.在解决方案资源管理器的头文件中添加,mylib.h文件，在源文件添加mylib.c文件（即实现文件）。

3.在mylib.h文件中添加如下代码：
```C++
#ifndef TEST_H
#define TEST_H int myadd**(**int a**,**int b**);**
#endif
```
4.在mylib.c文件中添加如下代码：
```C
#include"test.h"
int myadd**(**int a**,** int b**)
{**	**return** a **+** b**;****}** 
```
\5. 配置项目属性。因为这是一个静态链接库，所以应在项目属性的“配置属性”下选择“常规”，在其下的配置类型中选择“静态库（.lib）。

6.编译生成新的解决方案，在Debug文件夹下会得到mylib.lib (对象文件库），将该.lib文件和相应头文件给用户，用户就可以使用该库里的函数了。

### **12.2.2 静态库的使用**

***\*方法一：配置项目属性\****

A、添加工程的头文件目录：工程---属性---配置属性---c/c++---常规---附加包含目录：加上头文件存放目录。B、添加文件引用的lib静态库路径：工程---属性---配置属性---链接器---常规---附加库目录：加上lib文件存放目录。C  然后添加工程引用的lib文件名：工程---属性---配置属性---链接器---输入---附加依赖项：加上lib文件名。

***\*方法二：使用编译语句\****

#pragma comment(lib,"./mylib.lib")

***\*方法三：添加工程中\****

就像你添加.h和.c文件一样,把lib文件添加到工程文件列表中去.切换到"解决方案视图",--->选中要添加lib的工程-->点击右键-->"添加"-->"现有项"-->选择lib文件-->确定.

 

### **12.2.3 静态库优缺点**

 

- 静态库对函数库的链接是放在编译时期完成的，静态库在程序的链接阶段被复制到了程序中，和程序运行的时候没有关系；
- 程序在运行时与函数库再无瓜葛，移植方便。
- 浪费空间和资源，所有相关的目标文件与牵涉到的函数库被链接合成一个可执行文件。

 

 

***\*内存和磁盘空间\****

静态链接这种方法很简单，原理上也很容易理解，在操作系统和硬件不发达的早期，绝大部门系统采用这种方案。随着计算机软件的发展，这种方法的缺点很快暴露出来，那就是静态链接的方式对于计算机内存和磁盘空间浪费非常严重。特别是多进程操作系统下，静态链接极大的浪费了内存空间。在现在的linux系统中，一个普通程序会用到c语言静态库至少在1MB以上，那么如果磁盘中有2000个这样的程序，就要浪费将近2GB的磁盘空间。

***\*程序开发和发布\****

空间浪费是静态链接的一个问题，另一个问题是静态链接对程序的更新、部署和发布也会带来很多麻烦。比如程序中所使用的mylib.lib是由一个第三方厂商提供的，当该厂商更新容量mylib.lib的时候，那么我们的程序就要拿到最新版的mylib.lib，然后将其重新编译链接后，将新的程序整个发布给用户。这样的做缺点很明显，即一旦程序中有任何模块更新，整个程序就要重新编译链接、发布给用户，用户要重新安装整个程序。

 

## **12.3 windows下动态库创建和使用**

要解决空间浪费和更新困难这两个问题，最简单的办法就是把程序的模块相互分割开来，形成独立的文件，而不是将他们静态的链接在一起。简单地讲，就是不对哪些组成程序的目标程序进行链接，等程序运行的时候才进行链接。也就是说，把整个链接过程推迟到了运行时再进行，这就是动态链接的基本思想。

### **12.3.1 动态库的创建**

\1. 创建一个新项目，在已安装的模板中选择“常规”，在右边的类型下选择“空项目”，在名称和解决方案名称中输入mydll。点击确定。

2.在解决方案资源管理器的头文件中添加,mydll.h文件，在源文件添加mydll.c文件（即实现文件）。

3.在test.h文件中添加如下代码：

#ifndef TEST_H#define TEST_H __declspec**(**dllexport**)** int myminus**(**int a**,** int b**);** #endif

5.在test.c文件中添加如下代码：

#include"test.h"__declspec**(**dllexport**)** int myminus**(**int a**,** int b**){**	**return** a **-** b**;****}**

\5. 配置项目属性。因为这是一个动态链接库，所以应在项目属性的“配置属性”下选择“常规”，在其下的配置类型中选择“动态库（.dll）。

6.编译生成新的解决方案，在Debug文件夹下会得到mydll.dll (对象文件库），将该.dll文件、.lib文件和相应头文件给用户，用户就可以使用该库里的函数了。

***\*疑问一：\****__declspec(dllexport)是什么意思？动态链接库中定义有两种函数：导出函数(export  function)和内部函数(internal  function)。 导出函数可以被其它模块调用，内部函数在定义它们的DLL程序内部使用。 ***\*疑问二：\****动态库的lib文件和静态库的lib文件的区别？在使用动态库的时候，往往提供两个文件：一个引入库（.lib）文件（也称“导入库文件”）和一个DLL（.dll）文件。虽然引入库的后缀名也是“lib”，但是，动态库的引入库文件和静态库文件有着本质的区别，对一个DLL文件来说，其引入库文件（.lib）包含该DLL导出的函数和变量的符号名，而.dll文件包含该DLL实际的函数和数据。在使用动态库的情况下，在编译链接可执行文件时，只需要链接该DLL的引入库文件，该DLL中的函数代码和数据并不复制到可执行文件，直到可执行程序运行时，才去加载所需的DLL，将该DLL映射到进程的地址空间中，然后访问DLL中导出的函数。

 

### **12.3.2 动态库的使用**

***\*方法一：隐式调用\****

   创建主程序TestDll，将mydll.h、mydll.dll和mydll.lib复制到源代码目录下。(P.S：头文件Func.h并不是必需的，只是C++中使用外部函数时，需要先进行声明)在程序中指定链接引用链接库 : #pragma comment(lib,"./mydll.lib")

 

***\*方法二：显式调用\****

​	HANDLE hDll**;** //声明一个dll实例文件句柄	hDll **=** LoadLibrary**(**"mydll.dll"**);** //导入动态链接库	MYFUNC minus_test**;** //创建函数指针	//获取导入函数的函数指针	minus_test **=** **(**MYFUNC**)**GetProcAddress**(**hDll**,** "myminus"**);**