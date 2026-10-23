# Git（hub）Study

## Git

>  在代码开发工作流中，为了方便代码的维护及多人协作，版本控制系统Git被发明。

Git的仓库：

* 本地仓库 

  > [!NOTE]
  >
  > 相当于本地游戏存档

  

* 远程仓库（Github/Gitee）

  > [!NOTE]
  >
  > 相当于steam云存档

  

### Git工作逻辑

当一个文件夹被Git管理之后，会产生.git子文件夹，存放git相关版本文件

版本控制的基本单元：**Commit**

一个commit就是一个版本,就是local repo,可随时查看对比退回

一个commit对应独一无二的**commit hash**:可以方便的查找某次commit

#### Git指令:

.gitignore:用于声明哪些文件需要git忽略掉,通常是密钥文件, node_modules等,若是声明文件夹,格式是[folder_name]**/**

在VScode中, 若有一次修改不满意, 可直接进行discard操作退回到修改前

回退<u>仅查看</u>操作: 在VScode中右键某次commit选择checkout(detached[^1])[^2]

```shell
git init #使本文件夹被git管理
git reset #未提交远程仓库状态下强制退回某次历史状态
git reverb #生成一个反向提交抵消上次修改, 可防止丢代码, 便于多人协作
git merge #将某个分支merge进入main
git add . #将所有修改放在缓冲区(Stage修改)(Staging area/Index area)
git commit -m "[commit message]" #commit到local repo
git push #推送到remote repo
git clone [URL]# 将远程仓库clone到本地
git rebase main #将当前项目的基地变更到main
```

![image-20261023194725164](https://cdn.jsdelivr.net/gh/SFCFBR/Iamges@main/image-20261023194725164.png)

Branch: 可以进行功能开发而不影响主进程, 在开发完成后可以merge进入main分支, 若merge时遇到冲突的修改会询问用户抉择(或Agent)

> [!NOTE]
>
> Branch在VScode中可以通过右键某次commit来创建
>
> 同时branch之间可嵌套

* WorkTree

  可在Codex中直接创建, 在新产生的工作区中的操作不会影响主文件, 完成之后也可以合并到main



## github

#### 常用快捷键:

1. /: 快速打开github的搜索功能

2. T: 快速定位到文件搜索栏

3. L: 快速定位到x行

4. ?: 快捷键表

5. .: 打开github提供的vscode网页端

#### fork

若想参与协作, 可以先通过fork操作将别人的repo复制一份到自己名下

> [!WARNING]
>
> 在fork之后, 要先创建分支在修改, 这样同步代码就不会冲突

在改动完成后, 即可发起**Pull Request(PR)**[^3]

在主仓库的管理员进行code review之后即可accept合并

* 若管理员将某人设置为"collaborator", 在对方同意后对方可直接PR, 无需fork
#### Cherry Pick-拣选提交

当有多个commit时, 可挑选某几个commit进行push

#### Stash 临时存储

将写一半的任务临时存储(单片机中断逻辑)


[^1]: 意思是更换HEAD指针(类似于硬盘读取头意思¿)
[^2]: 这个状态下改代码容易丢, 用<u>create branch</u>的方法更正统
[^3]: 译为拉取请求(or合并请求)
