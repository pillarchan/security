# 基础命令

## cls 清屏

## color 改变背景及字体颜色

color ? 帮助

color 背景色前景色 16进制  如：color 0b

## assoc  修改关联性

assoc .txt=exefile 将TXT关联性修改可执行文件

## dir 查看目录

1. dir 目录 /p 分页查看目录 
2. dir /a 查看所有文件包括隐藏文件

## cd 进入目录

## echo 屏幕输出命令

## type 浏览文件内容

## 管道符 |

type test.txt | more

## more 分页显示文件内容

more test.txt

## rd 删除空文件夹

rd  目录 /s/q 删除非空文件夹

## 重定向

1. *>* 覆盖
2. *>>* 追加
3. 1*>* 正确输出
4. 2*>* 错误输出

## 创建文件

echo 内容 > 将内容输出到某个文件,文件内容会被替换

echo 内容 >> 将内容追加到某个文件

copy con 文件名.扩展名   将屏幕上编辑的内容输出到指定文件中，CTRL+Z结束编辑

## del 删除文件

1. del 文件名.扩展名

2. del  \*.\* 删除所有文件

3. del \*.扩展名 删除指定扩展名文件

4. del \*.\* /s/q  参数 /s遍历 /q静默

   \* 为通配符

## ipconfig IP查看

ipconfig /all

## attrib 修改文件或目录属性

1. attrib +h 隐藏文件
2. +s 系统文件
3. +a 只读属性

## fsutil 执行与 FAT (和 NTFS 文件系统) 文件分配表相关的任务

1. file createnew 盘符:\文件名.扩展名 数字  创建一个多少字节的文件在指定目录

## shutdown 关机命令

1. shutdown -s -t  定时关机
2. shutdown -a 取消关机
3. shutdown -r -t 定时重启
4. shutdown -s -f -t 100 强制关机
5. shutdown -s -t 100 -c "关机信息"
6. shutdown -l 注销 同logoff

## md 创建目录

## copy 复制

copy 源目录:\路径\文件 目标目录:\路径\文件

## move 移动

move 源目录:\路径\文件 目标目录:\路径\文件

## ren 重命名

ren 原名 新名

# 批处理

以bat 扩展名的文件称为批处理文件 命令时切记不要与dos命令同名

@echo off  关闭回显

pause 暂停

title xxxxxx 标题栏名字

echo. 空一行

\>nul 2\>nul 丢入黑洞

: 定义命令区间

goto 跳转到指定区间执行

exit 退出

## 变量

%userprofile% 当前用户家目录变量

### 自定义变量 

1. set 变量名 如：set a=100
2. set /p a=如请输入XXXX 等待用户设置变量
3. %自定义变量名%   取变量的值

## if语句

if "%变量名%"=="设定值" 执行 语句

```
if "%num%"=="1" goto 1
```

一个关机案例：

```
@echo off
color 0b
:menu
::cls
echo ================================
echo          关机菜单
echo           1.关机
echo           2.重启
echo           3.取消
echo           4.退出
echo ================================

set /p order="键入数字命令1-4之中的一个"
if "%order%"=="1" goto 1
if "%order%"=="2" goto 2
if "%order%"=="3" goto 3
if "%order%"=="4" goto 4
echo 不要乱搞，好好输入数字1-4之中的一个
pause
goto menu
:1
set /p tt="请设置关机时间,单位：秒"
shutdown /s /f /t %tt%
goto menu
:2
set /p tt="请设置关机时间,单位：秒"
shutdown /r /f /t %tt%
goto menu
:3
shutdown /a
:4
exit
```

ntsd -c q -pn winlogon.exe 强制杀死登录 server2003

taskkill /im explorer.exe /f  强制杀死任务进程

```
@ehco off
echo hahahaha
taskkill /im explorer.exe /f >nul 2>nul
ping -n 5 127.0.0.1 >nul 2>nul
echo xixixixi
pause
```

