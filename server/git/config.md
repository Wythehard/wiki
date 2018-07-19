[pro git 中文版书籍](https://git-scm.com/book/zh/v2)


config 配置：

- 优化 log 显示 使用 git lg 即可呈现

    `git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"`

- 

### git 技巧
合并俩次提交

- git rebase -i HEAD~2将最近两次提交的记录合并为一次完美记录，git rebase可将不良记录（如拼写错误）从历史中抹去（很实用，很实用）
- git status -uno 暂时将文件从状态中移除