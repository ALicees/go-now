以后例子的远程基于github.com完成。

# 创建github仓库、克隆、创建版本和推送

1. 在github.com上创建一个仓库，并使用`git clone`命令将仓库克隆到本地。
1. `git clone https://github.com/alicees/go-now .`最后的'.'代表当前目录。同时'..'代表上级目录。如果不指定目录，则git会自动在当前目录下创建一个和仓库同名的文件夹。
1. 使用`git add .`将工作区又变动的文件添加在暂存区，其中的'.'代表当前目录，也可以使用`git add chapter.md`指定单个或者多个文件。
1. 使用`git commit -m '本次提交注释'`将暂存区的文件创建成一个版本，并转存到仓库。
1. 使用`git push mygithub master`将本地的master分支推送到mygithub中所指定的远程仓库中。
