
Git —— 记录笔记的修改过程......

[官网](https://git-scm.com/) | [中文教程](https://git-scm.com/book/zh/v2/Git-%E5%9F%BA%E7%A1%80-%E8%8E%B7%E5%8F%96-Git-%E4%BB%93%E5%BA%93) | [Cheatsheet](https://education.github.com/git-cheat-sheet-education.pdf)

版本控制系统 (Version Control Systems, VCS)：记录文件内容的变化
    
    - 集中化的版本控制系统 (Centralized VCS)
    - **分布式版本控制系统** (Distributed VCS)
        + 基于文件累积的差异 (delta-based)
        + **基于文件系统的快照流**

## 常用命令

- 远程 remote
    
    ```shell
    git remote
    git remote -v      # 显示需要读写远程仓库使用的 Git 保存的简写与其对应的 URL
    git remote add <shortname> <url>    # 添加一个新的远程 Git 仓库；
                                        # 同时指定一个方便使用的简写
    git remote db https://github.com/doufubeier/EcoNotes.git  # 一个例子
                       # 随后可以使用 db 来代替整个 url
    ```
    
- 跟踪 track
- **暂存 stage**
    
    ```shell
    git status
    git all <file>     # 精确地将内容添加到下一次提交中：跟踪、暂存、解决冲突等
    git status -s      # 状态简览
    ```
    
    ```
    git diff           # 比较工作目录中当前文件和暂存区域快照之间的差异
    git diff --stage   # 比对已暂存文件与最后一次提交的文件差异
    git diff --cached  # 同 --stage
    git difftool --tool=<tool>       # git diff 的插件版本
                                     # 可选：gvimdiff, vimdiff2, vimdiff3 等
    ```
    
- **提交 commit**
    
    ```
    git commit         # 提交并启动文本编辑器来输入提交说明
    git commit -m "你的提交说明"     # 将提交信息与命令放在同一行
    git commit -a -m "你的提交说明"  # 自动暂存已跟踪过的文件并提交
    git commit --amend # 重新提交，覆盖上一次的提交信息；
                       # 最终你只会有一个提交——第二次提交将代替第一次提交的结果
    ```
    
    ```
    git rm <file>      # 从已跟踪文件清单中移除，即从暂存区域移除；
                       # 连带从工作目录中删除指定的文件
    git rm -f <file>   # （强制）删除之前修改过或已经放到暂存区的文件；
                       # 用于删除尚未添加到快照的数据，不能被 Git 恢复
    git rm --cached <file>           # 从 Git 仓库中删除，即从暂存区域移除，
                                     # 但仍然保留在当前工作目录中
    git mw <file_from> <file_to>     # 重命名、移动
    ```
    
    ```
    git reset HEAD <file>            # 取消暂存的文件；注意命令危险！
    git checkout -- <file>           # 撤消对文件的修改；注意命令危险！
                                     # 对文件在本地的任何修改都会消失，
                                     # Git 会用最近提交的版本覆盖掉它
    ```
    
    ```
    git log            # 按时间先后顺序列出所有的提交历史
    git log -p <次数>  # 显示每次提交所引入的差异；
                       # 可使用次数限制显示的日志条目数量
    git log --stat     # 提交的简略统计信息
    git log --since=2.weeks          # 列出最近两周的所有提交历史
    ```

- **推送 push**
    
    ```
    git push <remote> <branch>       # 推送到远程仓库
    git push origin master
    ```
    
    ```
    git remote show <remote>         # 查看某个远程仓库
    git remote show origin
    git remote show
    
    git remote rename  # 修改一个远程仓库的简写名
    git remote db doufubeier         # 一个例子
    git remote remove  # 移除一个远程仓库
    git remote remove doufubeier     # 所有和这个远程仓库相关的远程跟踪分支，
                                     # 以及配置信息也会一起被删除
    git remote
    ```
    
- **拉取 pull**
    
    ```
    git fetch <shortname | remote>   # 拉取 doufubeier 的仓库中有但你没有的信息
                                     # 从远程仓库 url 拉取所有你还没有的数据
    git fetch origin   # 抓取上一次抓取或克隆后，新推进的所有工作；
                       # 仅下载，并不会自动合并或修改你当前的工作
    git pull           # 抓取数据并自动尝试合并该远程分支到当前所在的分支
    ```

## 扩展命令

- 打标签 tag
    + 轻量标签 lightweight：将提交_校验和_存储到一个文件中——没有保存任何其他信息
    + 附注标签 annotated：包含打标签者的名字、电子邮件地址、日期时间，及标签信息
    
    ```
    git tag            # 列出已有的标签
    git tag -a v1.4 -m "my version 1.4"    # -a 附注标签，后接标签名；
                                           # -m 写入标签信息
    git show v1.4      # 查看标签信息及其提交信息
    git tag v1.4-lw    # 轻量标签
    git push origin <tagname>        # 共享标签，显示推送到远程仓库的服务器上
    
    git tag -d <tagname>             # 删除标签
    git push <remote> :refs/tags/<tagname> # 方法一，从远程仓库中移除标签
    git push origin --delete <tagname>     # 方法二
    ```

