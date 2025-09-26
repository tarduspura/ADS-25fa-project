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

>tip:如果clone时需要输入用户名和密码，请注意这里的用户名是你的github用户名，而密码是github生成的个人访问令牌(PAT)，而不是登录github时的密码。以下步骤可以创建你的PAT：1.点击首页右上方的头像，找到settings。2.进入settings后下拉侧边栏到底部找到Developer settings。3.点击Personal access tokens。4.点击Generate new token，classic就行，有效期随便，随时可以生成新的。5.PAT生成之后只会显示一次，要注意复制。

3.检查远程仓库连接

```bash
git remote -v

//输出示例
origin  git@github.com:tarduspura/ADS-25fa-project.git (fetch)
origin  git@github.com:tarduspura/ADS-25fa-project.git (push)
```
这表明你本地的这个文件夹已经和github上的远程仓库建立联系了。

## 创建自己的分支

为了可以在本地自由地修改文件和上传到仓库，如果直接在master分支上修改我们就会改乱了，所以可以创建自己的分支之后先在自己创建的分支结构上修改和写代码

```bash
//查看当前分支
git branch

//查看所有分支
git branch -a

//创建并切换到新分支
git checkout -b feature/your-branch-name

//切换到已有分支
git checkout yout-branch-name

//删除已有分支
git branch -d your-branch-name
```

## 提交修改

接下来就是关键的修改部分，我们的核心目的是，将我们在本地的更新最终合并到main分支

```bash
//检查文件状态，红色表示未暂存，绿色表示已经暂存了
git status

//加入暂存区
git add your-filename
//或者一次性添加所有改动
git add .

//然后提交修改（还是在本地）
git commit -m "描述修改内容，可以让别人知道你修改了什么，需要清晰且简洁"
```

## 推送分支到github远程仓库

第一次推送你创建的新分支时，可以设置远程跟踪
```bash
git push -u origin feature/your-branch-name
```
>远程跟踪就是让github记住这个分支是你会更新的，这样以后你只需要使用git push或git pull同步远程分支而无需指定是你的分支。

```bash
git push origin your-branch-name

//远程跟踪后就可以
git push
```
>tip:这一步还是需要输入用户名和密码，而且亲身体验可能会push的比较慢，如果出现这种情况，可以在上面连接远程仓库的

## 与远程同步更新

在开发过程中，每次进行开发前需要拉取其他人最新修改的仓库的内容（当然也有可能没人更新，但也可以拉一下，不然多人修改同一个文件时会产生冲突）

```bash
git pull origin main
```

## 合并分支

在你完成一个新的修改，并且把修改内容上传到远程仓库之后，可以在github仓库页面，点击Pull Request(PR)->New Pull Request，选择你的分支->main分支，填写修改内容，提交PR，其他组员审核后可以合并到main分支。这样就完成了一次完整的修改



