#### no matches found
因为 zsh 不能扩展 rysn 和 scp 的 **\*** 所以会报这个错，有两种解决方式

- `echo “setopt nonomatch” >> ~/.zshrc `
- `命令加 “”`