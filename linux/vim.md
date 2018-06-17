### 插入命令

a 光标后一个 A 移到最后 i 光标 o 新建下一行 s 删除当前字符 O 新建上一行

### 设置字符集

set encoding=utf-8

### 删除命令

x 删除光标字符 dw 光标开始删到空格 daw 删除光标所在的单词 "" () 不删 .删

### 替换命令

r 替换一个字符  \# 查找光标所在的单词。

### 跳转

nG 跳转到第n行 G 末尾 gg 头 w 下一个单词 e 下一个单词末尾 b 上一个单词 ge 上一个单词末尾 $ 行末尾 ^ 行头

Shift + 零 下一行头

### 合并

J 去除两行之间的空格

### 粘贴复制

y 复制 p 粘贴

删除操作的字符会进入剪切板 dd dw daw 等

`系统剪切板和vim剪切板 “+p ”+y 不能使`


#### 撤销

u U 当前行所有修改的撤销

反撤销 Ctrl + R

### 命令模式

### 退出

：e! 撤销修改重新载入

### 剪切板历史记录

：reg

### 多行插入

多行注释： V 选中 ctrl + v 大写i插入 俩次 esc 取消多行注释：上述选中 按d键就可全部取消注释

### vim配置

```
set encoding=utf-8
set termencoding=utf-8 "屏幕/键盘的编码
set fileencoding=utf-8 "存储时的编码
set fileencodings=ucs-bom,utf-8,gbk,default,latin1 "打开文件时的尝试使用的编码
set nu "设置行号

```



### 查找删除

:%s/find/update 全局

http://www.cnblogs.com/jianyungsun/archive/2011/03/20/1989276.html


-----

### 查找

在normal模式下按下  `/`  即可进入查找模式，按下`n`查找下一个，按下`N`查找上一个。

Vim通过正则来匹配，例如 `/vim$` 匹配行尾的 `"vim"` 。 需要查找特殊字符需要转义，例如 `/vim\$` 匹配 `"vim$"`。

> 注意查找回车应当用`\n`，而替换为回车应当用`\r`（相当于`<CR>`）。

### 大小写敏感查找

在查找模式中加入`\c`表示大小写不敏感查找，`\C`表示大小写敏感查找。例如：

```
/foo\c

```

将会查找所有的`"foo"`,`"FOO"`,`"Foo"`等字符串。

### 大小写敏感配置

Vim 默认采用大小写敏感的查找，为了方便我们常常将其配置为大小写不敏感：

```
" 设置默认进行大小写不敏感查找
set ignorecase
" 如果有一个大写字母，则切换到大小写敏感查找
set smartcase 

```

> 将上述设置粘贴到你的`~/.vimrc`，重新打开Vim即可生效。

### 查找当前单词

在normal模式下按下`*`即可查找光标所在单词（word）， 要求每次出现的前后为空白字符或标点符号。例如当前为`foo`， 可以匹配`foo bar`中的`foo`，但不可匹配`foobar`中的`foo`。 这在查找函数名、变量名时非常有用。

按下`g*`即可查找光标所在单词的字符序列，每次出现前后字符无要求。 即`foo bar`和`foobar`中的`foo`均可被匹配到。

### 查找与替换

`:s`（substitute）命令用来查找和替换字符串。语法如下：

```
:{作用范围}s/{目标}/{替换}/{替换标志}

```

例如`:%s/foo/bar/g`会在全局范围(`%`)查找`foo`并替换为`bar`，所有出现都会被替换（`g`）。

### 作用范围

作用范围分为当前行、全文、选区等等。

当前行：

```
:s/foo/bar/g

```

全文：

```
:%s/foo/bar/g

```

选区，在Visual模式下选择区域后输入`:`，Vim即可自动补全为 `:'<,'>`。

```
:'<,'>s/foo/bar/g

```

2-11行：

```
:5,12s/foo/bar/g

```

当前行`.`与接下来两行`+2`：

```
:.,+2s/foo/bar/g

```

### 替换标志

上文中命令结尾的`g`即是替换标志之一，表示全局`global`替换（即替换目标的所有出现）。 还有很多其他有用的替换标志：

空替换标志表示只替换从光标位置开始，目标的第一次出现：

```
:%s/foo/bar

```

`i`表示大小写不敏感查找，`I`表示大小写敏感：

```
:%s/foo/bar/i
### 等效于模式中的\c（不敏感）或\C（敏感）
:%s/foo\c/bar

```

`c`表示需要确认，例如全局查找`"foo"`替换为`"bar"`并且需要确认：

```
:%s/foo/bar/gc

```

回车后Vim会将光标移动到每一次`"foo"`出现的位置，并提示

```
replace with bar (y/n/a/q/l/^E/^Y)?

```

按下`y`表示替换，`n`表示不替换，`a`表示替换所有，`q`表示退出查找模式， `l`表示替换当前位置并退出。`^E`与`^Y`是光标移动快捷键，参考： [Vim中如何快速进行光标移动](http://harttle.land/2015/11/07/vim-cursor.html)。

### 高亮设置

#### 高亮颜色设置

如果你像我一样觉得高亮的颜色不太舒服，可以在 `~/.vimrc` 中进行设置：

```
highlight Search ctermbg=yellow ctermfg=black 
highlight IncSearch ctermbg=black ctermfg=yellow 
highlight MatchParen cterm=underline ctermbg=NONE ctermfg=NONE

```

上述配置指定 Search 结果的前景色（foreground）为黑色，背景色（background）为灰色； 渐进搜索的前景色为黑色，背景色为黄色；光标处的字符加下划线。

> 更多的CTERM颜色可以查阅：[http://vim.wikia.com/wiki/Xterm256\_color\_names\_for\_console\_Vim](http://vim.wikia.com/wiki/Xterm256_color_names_for_console_Vim)

#### 禁用/启用高亮

有木有觉得每次查找替换后 Vim 仍然高亮着搜索结果？ 可以手动让它停止高亮，在normal模式下输入：

```
:nohighlight
" 等效于
:nohl

```

其实上述命令禁用了所有高亮，只禁用搜索高亮的命令是`:set nohlsearch`。 下次搜索时需要`:set hlsearch`再次启动搜索高亮。

#### 延时禁用

怎么能够让Vim查找/替换后一段时间自动取消高亮，发生查找时自动开启呢？

```
" 当光标一段时间保持不动了，就禁用高亮
autocmd cursorhold * set nohlsearch
" 当输入查找命令时，再启用高亮
noremap n :set hlsearch\<cr\>n
noremap N :set hlsearch\<cr\>N
noremap / :set hlsearch\<cr\>/
noremap ? :set hlsearch\<cr\>?
noremap * *:set hlsearch\<cr\>

```

> 将上述配置粘贴到`~/.vimrc`，重新打开vim即可生效。

#### 一键禁用

如果延时禁用搜索高亮仍然不够舒服，可以设置快捷键来一键禁用/开启搜索高亮：

```
noremap n :set hlsearch<cr>n
noremap N :set hlsearch<cr>N
noremap / :set hlsearch<cr>/
noremap ? :set hlsearch<cr>?
noremap * *:set hlsearch<cr>

nnoremap <c-h> :call DisableHighlight()<cr>
function! DisableHighlight()
    set nohlsearch
endfunc

```

希望关闭高亮时只需要按下 `Ctrl+H`，当发生下次搜索时又会自动启用。

### 参考阅读

* XTERM 256色：[http://vim.wikia.com/wiki/Xterm256\_color\_names\_for\_console\_Vim](http://vim.wikia.com/wiki/Xterm256_color_names_for_console_Vim)
* Vim Wikia - 查找与替换：[http://vim.wikia.com/wiki/Search\_and\_replace](http://vim.wikia.com/wiki/Search_and_replace)
* 用 Vim 打造 IDE 环境：<http://harttle.land/2015/11/04/vim-ide.html>


### 设置 paste

set paste

