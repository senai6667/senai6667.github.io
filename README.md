# 利用代码编写自己的博客步骤（持续更新中）2023/09/08
**本次演示的系统是`windows`**
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
3. 在该文件夹内利用git命令初始化该文件夹
```powershell
git init
```
4. 在该文件内新建一个README.md文件，里面可以写上你的博客介绍
```powershell
New-Item -ItemType File -Path "D:/blog/README.md"
```
## 创建一个github远程库用于储存代码
1. 创建一个GitHub账号
2. 来到如下主页，点击`New repository`

![alt text](https://github.com/senai6667/senai6667.github.io/blob/main/magic/new%20repository.png "ways one")

3. 输入博客的名字，格式必须是`yourname.github.io`，repository类型选择`public`

![alt text](https://github.com/senai6667/senai6667.github.io/blob/main/magic/repository%20name.png "ways two")

4. 最后点击`create repository`一个github远程库就创建完成了

![alt text](https://github.com/senai6667/senai6667.github.io/blob/main/magic/create%20repository.png "ways three")

## 将本地库与远程库连接
1. 回到powershell并且此时应该处于本地库的目录，如`D:/blog`
2. 逐次运行以下命令
```powershell
git add .
git commit -m "first commit"
git remote add origin https://github.com/yourname/yourname.github.io
git push -u origin main
```
此时，本地库和github远程库连接成功，以后可以在本地库写代码，然后通过命令`git push origin main`推到github上面即可
## 以上步骤有可能出现的问题
1. 运行`git push -u origin main`时出现`failed to push some refs to https://github.com/yourname/TEST2.git`
原因：新建远程仓库的时候如果你勾选了Initialize this repository with a README（就是创建仓库的时候自动给你创建一个README文件）
解决方案：由于你新创建的那个仓库里面的README文件不在本地仓库目录中，这时我们可以通过`it pull --rebase origin master`命令先将内容合并,此时再push就能成功了
2. 运行`git remote add origin`时无法连接成功，或者运行`git push -u origin main`时无法推上去
原因：国内上github很慢，这是网络问题，可以待会再试试或是挂了代理
解决方法：
```powershell
git config --global https.proxy http://127.0.0.1:xxxx
```
其中`xxxx`为你的代理窗口编号
