这是我们小组的 ADS 课程项目仓库  
本仓库用于存放相关的 **C 语言代码、报告、资料** 等文件。在提交代码、更新仓库时可以参考以下工作流：

---

## 第一次使用：克隆仓库到本地

1. 打开终端，进入你想存放项目的目录。
2. 在wsl中执行以下命令克隆仓库（替换为实际的仓库地址）：

```bash
git clone https://github.com/tarduspura/ADS-25fa-project.git
```
这样你就可以拉取最新的文件夹结构到你的本地。

>tip:如果clone时需要输入用户名和密码，请注意这里的用户名是你的github用户名，而密码是github生成的密钥而不是登录github时的密码。关于密钥的生成，可以


## 创建自己的分支

为了可以在本地自由地修改文件和上传到仓库，如果直接在main分支上修改我们就会改乱了，所以可以创建自己的分支之后先在自己创建的分支结构上修改和写代码

```bash
//查看当前分支
git branch

//创建并切换到新分支
git checkout -b your-branch-name

//查看所有分支
git branch -a
```

## 提交修改

在自己的分支修改好代码或报告之后，我们需要把修改从本地推送到远程仓库你的分支上，让其他人来 review

```bash
//检查文件状态
git status

//加入暂存区
git add your-filename
//或者一次性添加所有改动
git add .

//然后提交修改（还是在本地）
git commit -m "描述修改内容，可以让别人知道你修改了什么"
```

## 推送到github远程仓库的分支

```bash
git push origin your-branch-name
```

## 更新代码

在开发过程中，每次进行开发前需要拉取其他人最新修改的仓库的内容（当然也有可能没人更新，但也可以拉一下，不然多人修改同一个文件时会产生冲突）

```bash
git pull origin main
```

## 合并分支

在你完成一个新的修改，并且把修改内容上传到远程仓库之后，可以在github仓库页面，点击Pull Request(PR)->New Pull Request，选择你的分支->main分支，填写修改内容，提交PR，其他组员审核后可以合并到main分支。这样就完成了一次完整的修改



