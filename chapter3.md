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

我在远程仓库中给chapter3.md添加了一句话
	我觉得这并没有解决问题。
同时，我在本地chapter3.md添加了本3行文字，造成冲突。

git自动用<<<<<<<HEAD=======>>>>>>>标记冲突行了。编辑成自己需要的文件即可，比如我不需要下面的那行，我觉得使用自己的文字更好。我说的是真的 你就这样解决冲突了吗

使用git pull 拉去远程仓库版本，git自动用<<<<<<<HEAD=======>>>>>>>标记冲突，根据自己的需要编辑冲突的地方，然后再提交一次版本就行了。哦 你是说在这个.md文件里面用<<<<<<<HEAD=======>>>>>>>标记冲突吗，不仅仅是.md，.java也是这样，都是文本中行级别的监控。继续吗，还有什么要学的？看到没 哪个是什么
这个文件就已经教你了 
多人协作？？解决冲突的时候就穿插了多人协作。除个别情况，一个人能造成像刚刚学的文件冲突吗？像我就能，你能，我也教了如何解决冲突。不能够了，回炉重造

现在我发起一个合并请求，pull request，这个是github独有的，但在git自身上，你也可以做到类似的操作，就是合并分支，有冲突就解决冲突。merge pull request合并这个拉取请求
创建一个分支
则