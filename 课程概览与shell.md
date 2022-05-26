# shell

一种与计算机交互的文字接口

```
missing:~$ 
```
**~** ：表示home

**$** : 表示现在身份不是root用户

---

```
missing:~$ date
Fri 10 Jan 2020 11:49:31 AM EST
```
执行date程序

---

```
missing:~$ echo hello
hello
```
执行echo程序，并且传递了参数hello

> 如果您希望传递的参数中包含空格（例如一个名为 My Photos 的文件夹），您要么用使用单引号，双引号将其包裹起来，要么使用转义符号 \ 进行处理（My\ Photos）

# 在shell中导航

如果某个路径以 **/** 开头，那么它是一个 绝对路径，其他的都是 相对路径 

相对路径是指相对于当前工作目录的路径，当前工作目录可以使用 **pwd** 命令来获取

切换目录需要使用 cd 命令

在路径中，**.** 表示的是当前目录，而 **..** 表示上级目录

```
missing:~$ pwd         # 获取当前工作目录
/home/missing

missing:~$ cd /home    # 切换绝对路径
missing:/home$ pwd
/home

missing:/home$ cd ..
missing:/$ pwd
/

missing:/$ cd ./home    # 切换到当前目录下的home
missing:/home$ pwd
/home

missing:/home$ cd missing  # 切换到missing(相对路径)
missing:~$ pwd
/home/missing

missing:~$ ../../bin/echo hello
hello
```

# ls

为了查看指定目录下包含哪些文件，我们使用 **ls** 命令，更多的信息使用：**ls -l**
```
missing:~$ ls -l /home
drwxr-xr-x 1 missing  users  4096 Jun 15  2019 missing
```
本行第一个字符 d 表示 missing 是一个目录。

然后接下来的九个字符，每三个字符构成一组。 （rwx）. 它们分别代表了文件所有者（missing），用户组（users） 以及其他所有人具有的权限。

其中 - 表示该用户不具备相应的权限。从上面的信息来看，只有文件所有者可以修改（w），missing 文件夹 （例如，添加或删除文件夹中的文件）。

为了进入某个文件夹，用户需要具备该文件夹以及其父文件夹的“搜索”权限（以“可执行”：x）权限表示。为了列出它的包含的内容，用户必须对该文件夹具备读权限（r）。对于文件来说，权限的意义也是类似的。

# 常用命令

mv（用于重命名或移动文件）

cp（拷贝文件）

mkdir（新建文件夹）

man 程序，用于了解相关用户手册

# 程序间创建连接：>  >>  |

在 shell 中，程序有两个主要的“流”：

它们的输入流和输出流。 当程序尝试读取信息时，它们会从输入流中进行读取，当程序打印信息时，它们会将信息输出到输出流中。

通常，一个程序的输入输出流都是您的终端。也就是，您的键盘作为输入，显示器作为输出。 但是，我们也可以重定向这些流！

最简单的重定向是 < file 和 > file。这两个命令可以将程序的输入输出流分别重定向到文件：

```
missing:~$ echo hello > hello.txt
missing:~$ cat hello.txt
hello

missing:~$ cat < hello.txt
hello

missing:~$ cat < hello.txt > hello2.txt
missing:~$ cat hello2.txt
hello
```

# sude