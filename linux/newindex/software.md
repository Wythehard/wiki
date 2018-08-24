#### socat 的使用

`socat TCP_LISTEN:90 -` 监听本机 90 端口

`socat TCP:ip:90 -` 连接远程 90 端口

`socat - TCP:IP:90` 从标准输入到远程


#### tmux 的使用
`vi ~/.tmux.conf`

键入以下内容
```
# 开启鼠标模式
set -g mode-mouse on

# 允许鼠标选择窗格
set -g mouse-select-pane on
```
