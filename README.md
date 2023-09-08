# 利用代码编写自己的博客步骤（持续更新中）2023/09/08
本次演示的系统是windows
## 下载powershell，最好是最新版
> https://learn.microsoft.com/zh-cn/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.3
## 在powershell中下载git包
```powershell
Install-Package -Name Git -ProviderName NuGet
```
如果执行失败可以下载一个choco，一个windows系统的包管理器
> https://chocolatey.org/install#psdsc
或者安装一个winget，也是一个windows系统的包管理器
> https://learn.microsoft.com/en-us/windows/package-manager/winget/
## 在本地磁盘（建议不要在c盘）建立一个文件夹作为github的本地库
*例子
1. 在本地D盘新建立一个名为blog的文件夹
2.打开powershell，利用命令，切换到该文件夹
```powershell
cd D:/blog
```
2. 在该文件夹内利用git命令初始化该文件夹
```powershell
git init
```
3.
