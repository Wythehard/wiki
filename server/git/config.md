[pro git 中文版书籍](https://git-scm.com/book/zh/v2)

优化 log 显示 使用 git lg 即可呈现

`git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"`