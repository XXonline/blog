---
title: Git笔记
date: 2017-08-05 01:05
tags: git
categories: git
---
> 这些是平时我工作学习中使用频率较高的git指令，归纳如下：
---
查看分支：```git branch```

创建分支：```git branch <name>```

切换分支：```git checkout <name>```

创建+切换分支：```git checkout -b <name>```

合并某分支到当前分支：```git merge <name>```

删除分支：```git branch -d <name>```

查看分支合并图：```git log --graph```

把当前工作现场“储藏”起来：```git stash```

查看stash隐藏工作现场（未提交的）存到哪去了：```git stash list```

恢复stash隐藏的工作现场（未提交的）：```git stash apply```

删除stash内容git stash drop


---
> 分支bug

###  ```git stash apply + git stash drop = git stash pop```

> 撤销修改

### ```保存到暂存区的情况，其实可以一条命令搞定：git reset --hard head```

(未完待续)






