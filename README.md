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
* 例子
1. 在本地D盘新建立一个名为blog的文件夹
2.打开powershell，利用命令，切换到该文件夹
```powershell
cd D:/blog
```
2. 在该文件夹内利用git命令初始化该文件夹
```powershell
git init
```
3. 在该文件内新建一个README.md文件，里面可以写上你的博客介绍
```powershell
New-Item -ItemType File -Path "D:/blog/README.md"
```
## 创建一个github远程库用于储存代码
1. 创建一个GitHub账号
2. 来到如下主页，点击`New repository`

![alt text](https://github.com/senai6667/senai6667.github.io/blob/main/magic/new%20repository.png "ways one")

3. 输入博客的名字，格式必须是`yourname.github.io`，repository类型选择`public`

![alt text](https://github.com/senai6667/senai6667.github.io/blob/main/magic/new%20repository.png "ways two")

4. 最后点击`create repository`一个github远程库就创建完成了

![alt text](https://github.com/senai6667/senai6667.github.io/blob/main/magic/new%20repository.png "ways three")

## 将本地库与远程库连接
1. 回到powershell并且此时应该处于本地库的目录，如`D:/blog`
2. 逐次运行以下命令
```powershell
git add .
git commit -m "first commit"
git push -u origin main
```
