﻿title: 在win命令行执行python程序
date: 2016/9/25 12:34:09
tags: Python
---

今天尝试了在windows命令提示符中选择python文件并执行，也发现了一些问题，现在把在win命令行中执行python程序的方法记录一下。

- 首先，我们需要用`cd`命令来**将当前目录切换为你的python文件（.py)保存目录**。
- -  如果我们要切换的目录位于同一盘符中*（例如c:/work1移动到c:/work2）*时，直接进行切换就可以了。
``` 
C:\work1>cd c:\work2
c:\work2> 
```

- - 如果我们要切换的目录不属于同一盘符*（例如c:/work移动到e:/python）*时，我们会发现cmd中不可以直接进行切换，所以我们需要用以下三种方法进行切换。    
- - - 方法一：在命令提示符的DOS窗口下直接输入`e:`。回车后就可以直接转跳到E盘符下了，然后我们就可以用`cd`指令进行操作了。
```
C:\work>e:

E:\>cd e:\python
        
E:\python>
```
 - - - 方法二：输入cd /e e:也同样可以转跳到E盘符下,然后通过`cd`指令进行操作。
```
C:\work>cd /e e:

E:\>cd e:\python
        
E:\python>
```
- - - 方法三：先用`cd`命令切换到目标文件，发现没有切换到目标盘符下的相应目录，这时我们再输入`盘符名:`就发现成功切换到相应目录。
```
C:\work>cd e:\python

C:\work>e:
        
E:\python>
```
- 然后我们可以使用`dir`命令来**查看当前目录的文件和参数**。
```
 c:\work>dir
驱动器 C 中的卷没有标签。
卷的序列号是 62BD-615D
    
c:\work 的目录
    
        2016/09/16  21:49    <DIR>          .
        2016/09/16  21:49    <DIR>          ..
        2016/08/31  22:27             1,404 aa.py
        2016/09/16  21:52               133 bb.py
                   2 个文件          1,537 字节
                   2 个目录 18,823,954,432 可用字节
```
 *我之前在work文件夹中放入了aa.py和bb.py两个文件，如上所示，`dir`命令成功展示了work文件夹的创建时间以及这两个python文件的修改时间。*

- 最后我们就可以直接输入python文件的文件名来**执行python文件**了
 
**请注意！！**
**这里并不需要使用python命令进入命令行交互环境即可调用py文件。**
```
     C:\work>aa.py 我可以猜到您设置的一个0到100的整数，快来试试吧 请输入你想让我猜的整数（0到100之间）55
     您让我猜的数是50吗？ 如果我猜对了，请输入c；如果我猜的比您输入的大，请输入h；如果我猜的比您输入小，请输入l： l
     您让我猜的数是75吗？ 如果我猜对了，请输入c；如果我猜的比您输入的大，请输入h；如果我猜的比您输入的小，请输入l： h
     您让我猜的数是62吗？ 如果我猜对了，请输入c；如果我猜的比您输入的大，请输入h；如果我猜的比您输入的小，请输入l： h
     您让我猜的数是56吗？ 如果我猜对了，请输入c；如果我猜的比您输入的大，请输入h；如果我猜的比您输入的小，请输入l： h
     您让我猜的数是53吗？ 如果我猜对了，请输入c；如果我猜的比您输入的大，请输入h；如果我猜的比您输入的小，请输入l： l
     您让我猜的数是54吗？ 如果我猜对了，请输入c；如果我猜的比您输入的大，请输入h；如果我猜的比您输入的小，请输入l： l
     您让我猜的数是55吗？ 如果我猜对了，请输入c；如果我猜的比您输入的大，请输入h；如果我猜的比您输入的小，请输入l： c
     您让我猜的数果然是55，哈哈，我真厉害。
```
  *我这里的aa文件是一个利用二分搜索猜数的小程序~*