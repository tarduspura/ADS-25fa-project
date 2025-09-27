这是我们小组的 ADS 课程项目仓库  
本仓库用于存放相关的 **C 语言代码、报告、资料** 等文件。以下是使用这个仓库进行合作的一个小小教程，基本不需要git基础，可以参考一下：

---

## 1.克隆仓库到本地

（1）打开终端，进入你想存放项目的目录。

（2）在wsl中执行以下命令克隆仓库：

```bash
git clone https://github.com/tarduspura/ADS-25fa-project.git
```
这样你就可以拉取最新的文件夹结构到你的本地。

>tip:如果clone时需要输入用户名和密码，请注意这里的用户名是你的github用户名，而密码是github生成的个人访问令牌(PAT)，而不是登录github时的密码。以下步骤可以创建你的PAT：1.点击首页右上方的头像，找到settings。2.进入settings后下拉侧边栏到底部找到Developer settings。3.点击Personal access tokens。4.点击Generate new token，classic就行，有效期随便，随时可以生成新的。5.PAT生成之后只会显示一次，要注意复制。

（3）检查远程仓库连接

```bash
git remote -v

//输出示例
origin  git@github.com:tarduspura/ADS-25fa-project.git (fetch)
origin  git@github.com:tarduspura/ADS-25fa-project.git (push)
```
这表明你本地的这个文件夹已经和github上的远程仓库建立联系了。

## 2.创建自己的分支

为了可以在本地自由地修改文件和上传到仓库，如果直接在master分支上修改我们就会改乱了，所以可以创建自己的分支之后先在自己创建的分支结构上修改和写代码

```bash
//查看当前分支
git branch

//查看所有分支
git branch -a

//创建并切换到新分支
//feature/xxx可以说是git的一个命名规范
//不是硬性要求，可以让别人知道你这个分支在进行什么操作
//但我们人比较的少，任务也很少，所以不一定要遵循
//commit的时候在message里加就可以
//出于方便，下面的branch就省略了
git checkout -b feature/your-branch-name

//切换到已有分支
git checkout yout-branch-name

//删除已有分支
git branch -d your-branch-name
```

## 3.修改和推送

在本地修改了代码，或者新写了报告之后，需要把修改提交到仓库大家都能看到的地方。
```bash
//检查文件状态，红色表示未暂存，绿色表示已经暂存了
git status

//加入暂存区（在本地）
git add your-filename
//或者一次性添加所有改动
git add .

//然后提交修改
git commit -m "描述修改内容，可以让别人知道你修改了什么，需要清晰且简洁"

//最后上传到远程仓库
git push origin your-branch-name
```

## 4.合并修改

接下来就是关键的修改部分，我们的核心目的是，将我们在本地的更新最终合并到main分支当中。一般来说我们有两种方法。

### （1）合并主分支之后提交

```bash
//1.先切换回主分支
git checkout main

//2.拉取最新主分支代码到本地，这很重要，可以防止出现冲突
git pull origin main

//3.合并你的分支到主分支，这样主分支就合并了你的修改
git merge your-branch-name

//4.add/commit/push三件套
git add .
git commit -m "description"
git push origin main
```
这样仓库的主分支中就包含你的修改了！

### （2）Pull Request(recommend)
好处在于，需要申请合并后由其他组员审核后再决定是否合并，可以防止误操作导致主分支受到污染（但就我们这点小破东西也污染不了什么）。也可以追溯合并历史，方便回溯。
操作方式也特别简单，上一步中不是已经在我们的分支上push新的修改到仓库了吗，那就可以点击仓库上方的Pull Request/New，然后设置从什么分支合并到什么分支（一般是main），然后别人就可以看到你的PR并且审核了，通过后就可以按照你的设置合并。

## 5.删除本地分支（可选）
其实，一次分支可以只是针对一次更新，或者一个功能的更新。在merge到main分支后这个分支也就功德圆满了，下次更新我们大可以创建别的分支，所以我们可以把合并后的分支删除。

```bash
//删除本地分支
git branch -d your-used-branch
//删除远程分支
git push origin --delete your-used-branch
```

## 6.远程跟踪分支

### （1）什么是远程跟踪分支

远程跟踪分支是本地 Git 仓库中对远程仓库分支状态的“快照”或“镜像”，它们不是你直接操作的分支（不能 checkout 修改），而是用来记录远程仓库的最新状态，供你拉取、合并、对比使用。
```bash
//格式为<远程名>/<分支名>
origin/main
```


### （2）查看远程跟踪分支

```bash
git branch -r

//输出示例
origin/main
origin/develop
origin/feature/张三-登录页
origin/feature/李四-注册页
```

### （3）设置远程跟踪分支

方法一：创建本地分支并指定追踪远程分支
```bash
git checkout -b your-branch-name origin/your-branch-name
```
这样你就创建了一个本地分支your-branch-name，并且它追踪着远程分支origin/your-branch-name

方法二：对已有的分支设置远程追踪

```bash
git branch --set-upstream-to=origin/your-branch-name your-branch-name
```

### （4）取消远程跟踪

```bash
git branch --unset-upstream
```

### (5)如何使用远程追踪分支
远程追踪分支的好处是可以在本地方便地查看别人都做了些什么

1.``git fetch``
```bash
git fetch origin
```
相当于把远程仓库的所有最新提交“同步”到你的本地远程跟踪分支（如 origin/main、origin/feature/xxx），但不会影响你当前工作的本地分支，你只是可以在origin/your-branch-name中查看最新的修改。

2.``git pull``
等价于``git fetch`` + ``git merge``，从远程仓库拉取所有最新的变化，并合并到你的当前分支。
```bash
git pull origin main
```

3.查看当前仓库和远程的差别

```bash
//查看本地（main）与远程（origin/main）的差异
git diff main origin/main
//查看当前分支是否落后
git status
```


## 7.注意事项

### （1）与远程同步更新

在开发过程中，每次进行开发前需要拉取其他人最新修改的仓库的内容（当然也有可能没人更新，但也可以拉一下，不然多人修改同一个文件时会产生冲突）。当然你也可以先用远程追踪分支看两眼有没有不同，但一般来说没这个必要，直接pull就是了。

```bash
git pull origin main
```
>tip：但注意，只能在主分支上执行这个操作，在功能分支上执行就有可能会把功能分支污染了。

### （2）多多使用

git其实就是一个有助于多人协同完成线上任务的工具，我们最终的目的就是要一起建设我们的主分支，但在建设过程中为了避免冲突和便利操作，才引入了分支概念，可以创建新的分支，提交修改，申请合并，整个逻辑还是很清晰的，只要多多使用肯定会体会到它的优势。




