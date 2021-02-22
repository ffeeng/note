[TOC]

### git操作

常用操作

```bash
git branch 查看本地分支
git remote -v 查看仓库地址
git fetch origin 查询远程分支
git checkout feature/gonghang-privacy 检出远程分支
```





git配置操作

```git
git config --list
git config --global user.name feng
git config --global user.email 123@qq.com
```

git查看状态和日志

```shell
git status #查看git状态
git log #查看日志
```

git初始化

```shell
git init
git clone
```
git从指定分支检出

```shell
git fetch origin
git checkout -b mq_bug_20180524  origin/mq_bug_20180524 #本地分支 远程分支
```

删除暂存区

```
git rm --cache . -r //删除整个暂存区
git rm --cache 文件名
```

git提交代码

```
git commit -m “消息”
```

git的对比

- git diff 工作区和暂存区
- git diff 分支名  工作区和历史区
- git diff --cached 暂存区和历史区比较

git撤销

```
git checkout 文件名  //从暂存区中将工作区内容覆盖掉
```

git回滚历史版本(本地的不是中央仓库)

```bash
git reset --hard 版本号

git rest --hard HEAD^：回退到上一版；
git rest --hard HEAD^^：回退到倒数第二版；
git rest --hard 3628164：回退到commit id为3628164的版本；

git reflog 查看所有版本
```

分支管理

```
git branch //查看分支
git branch 分支名    //创建分支
git checkout 分支名  //切换分支
git branch -D 分支名 //删除分支
git checkout -b 分支名 //创建并切换分支
```

linux文件操作

```
rm -rf .git //删除文件夹
rm 2.txt
mkdir git-project 
ls -al //显示隐藏文件
touch 1.txt //创建文件
cat 1.txt //查看文件
```

vi编辑器

```
i:插入模式 esc 退出编辑  :q!强制退出 :wq保存退出
```

- 参考
 [git如何回滚远程仓库](https://www.cnblogs.com/iloveyou-sky/p/6534409.html)
 [git flow](https://www.cnblogs.com/cnblogsfans/p/5075073.html)
