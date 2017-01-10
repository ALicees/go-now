# 本章解决版本冲突问题

你现在所在的分支有3个版本。
``` cmd
commit b98477578486c59f51a30a1ffa19d5ee7f5fe607
Author: 张晓灿 <13593881971@163.com>
Date:   Mon Jan 9 11:40:52 2017 +0800

    Created chapter2.md

commit 6f8cb0020d34eef4cd7cdac95d51bcab4dca4f0e
Author: ALicees <13593881971@163.com>
Date:   Mon Jan 9 11:33:17 2017 +0800

    Update chapter1.md

commit abe73cf6ee94575263fba12a262430aea775c9f7
Author: 张晓灿 <13593881971@163.com>
Date:   Mon Jan 9 11:26:43 2017 +0800

    update one
```

现在的你高高兴兴创建了文件chapter3.md，但是不知道仓库中有第4个版本或者更新的版本。但你此时要做版本并且推送到远程仓库。
当你push的时候会提示错误：
``` cmd
$ git push
To https://github.com/ALicees/go-now
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'https://github.com/ALicees/go-now'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
原因是，你现在的修改是基于第3个版本，远程仓库的修改也是基于第3个版本，或者更新的版本，产生了版本上的冲突。明白？那是你自己的问题，你基于哪个版本就是基于哪个版本。我在远程仓库添加readme.md文件，在做一个版本的时候所在分支最后一个版本就是第3个版本，现在我编辑的文件是基于第4个版本，因为我现在的版本中有4个版本。所以你现在commit的时候，它就成了第5个版本。绕口令

我在版本1创建1.txt
我基于版本1创建版本2，版本中的1.txt会消失吗？不会，所以有个继承的关系。
我基于版本1创建版本3，版本2和版本3是什么关系？是并列的，版本2添加了2.txt，版本3添加了3.txt。
我想同时保留2.txt和3.txt，并且能同时使用他们两个文件，要怎么办？合并这两个版本就可以了。
这就是解决版本冲突。

使用`git pull`拉去远程修改信息，git会自动合并。
Merge branch 'master' of https://github.com/ALicees/go-now意思是合并本地master版本到远远程仓库，可以是Merge branch 'master' of dev合并本地master分支到本地dev分支。要理解这个意思。merge合并，从哪合并到哪。

# 解决版本中的文件冲突。
git可以自动合并版本，但如果两个版本中文件上有冲突，就需要人工介入，然后再合并。
现在远程仓库中修改了chatper3.md并创建了第7个版本。
而你现在也再修改chatper3.md，修改完后也会再本地创建第7个版本。都在第6个版本上，编辑了相同的文件。
此时怎么解决？合并，你可以看看你之前自己自学到的东西。

我觉得这并没有解决问题。
