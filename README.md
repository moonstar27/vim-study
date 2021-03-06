# Vim 学习、练习
> # 目录
> 1. [模式切换](#模式切换)
> 1. [命令模式](#命令模式)
>    1. [插入光标](#插入光标)
>    2. [光标定位](#光标定位)
>    2. [滚屏](#滚屏)
>    3. [删除/剪切](#删除剪切)
>    4. [复制，粘贴](#复制粘贴)
>    5. [替换，取消](#替换取消)
>    6. [全文搜索，替换](#全文搜索替换)
>    7. [重复上一次操作](#重复上一次操作)
>    8. [插入模式和替换模式切换](#插入模式和替换模式切换)
> 2. [插入模式](#插入模式)
> 3. [末行命令模式](#末行命令模式)
> 4. [可视块模式](#可视块模式)
> 5. [小技巧](#小技巧)
>    1. [在不退出Vim下执行Linux命令](#在不退出Vim下执行Linux命令)
>    2. [导入命令执行结果](#导入命令执行结果)
>    3. [定义快捷键](#定义快捷键)
>    4. [连续行注释](#连续行注释)
>    5. [替换](#替换)
>    6. [多文件编辑](#多文件编辑)
>	 7. [排版](#排版)
>	 8. [缩进](#缩进)
>	 9. [跨文件复制、粘贴](#跨文件复制、粘贴)
> 6. [设置环境](#设置环境)

## 模式切换
> 下图出自：[Linux vi/vim | 菜鸟教程](http://www.runoob.com/linux/linux-vim.html)
> ![模式切换](./images/vim-vi-workmodel.png "模式切换")

## 命令模式
### 插入光标
| 命令 | 作用 |
| --- | --- |
| a | 在光标所在的字符后插入 |
| A | 在光标所在行尾后插入 |
| i | 在光标所在的字符前插入 |
| I | 在光标所在的行首前插入 |
| o | 在光标所在的下一行插入 |
| O | 在光标所在的上一行插入 |
| [n]s | 删除光标所在处往后n个字符，并进入插入模式 |
| [n]S | 删除当前行往下n行，并进入插入模式 |
| C | 删除光标后的内容，并进入插入模式 |

### 光标定位
| 命令 | 作用 |
| --- | --- |
| [n]h | 向左移动n个字符 |
| [n]j | 向下移动n行 |
| [n]k | 向上移动n行 |
| [n]l | 向右移动n个字符 |
| gg/1G | 移动到文件第1行 |
| G | 移动到文件最后一行 |
| :[n] | 在末行命令模式，移动到第n行 |
| [n]G | 在命令模式，移动到第n行 |
| [n]gg | 在命令模式，移动到第n行 |
| $ | 移动到光标所在行的行尾 |
| End | 移动到光标所在行的行尾 |
| 0 | 移动到光标所在行的行首 |
| ^ | 移动到光标所在行的第一个非空格字符 |
| Home | 移动到光标所在行的行首 |
| H | 移动到当前屏幕的第一行 |
| M | 移动到当前屏幕的中间一行 |
| L | 移动到当前屏幕的最后一行 |
| [n]space | 向右移动n个字符 |
| [n]enter | 向下移动n行 |
| [n]-     | 向上移动n行,至行首非空格字符处 |
| [n]+     | 向下移动n行,至行首非空格字符处 |
| [n]w/W      | 向右移动n个单词至词首,大写W会忽略符号、英文字母和汉字的区别,只把空格当做单词的分隔,可以通过底部的一段内容进行练习 |
| [n]b/B      | 光标左移n个单词至词首 |
| [n]e/E      | 光标右移n个单词至词尾 |

```
练习：systemctl start openvpn@server.service          #启动openvpn的命令

```
### 滚屏 ###
| 命令 | 作用 |
| --- | --- |
| Ctrl+f | 向下翻页 |
| Ctrl+b | 向上翻页 |
| Ctrl+d | 向下滚动半页 |
| Ctrl+u | 向上滚动半页 |
| Ctrl+e | 向下滚动一行 |
| Ctrl+y | 向上滚动一行 |

### 删除剪切
| 命令 | 作用 |
| --- | --- |
| x | 向后删除光标所在处的字符 |
| X | 向前删除光标所在处的字符 |
| [n]x | 删除光标所在处n个字符 |
| dw | 删除光标所在处开始，到第一个空格之间的所有字符 |
| de | 删除光标所在处开始，到第一个单词词尾 |
| daw | 删除光标所在处整个单词 |
| D | 删除光标所在处到行尾 |
| dd | 删除光标所在行 |
| [n]dd | 删除光标所在行后的n行 |
| d1G | 删除光标所在行到第一行的数据 |
| dG | 删除光标所在行到文件末尾 |
| d0 | 删除光标所在处到行首 |
| d$ | 删除光标所在处到行尾 |
| [n1],[n2]d | 删除从n1行到n2行 |

### 复制粘贴
| 命令 | 作用 |
| --- | --- |
| yy | 复制光标所在行 |
| [n]yy | 复制光标所在行以下n行 |
| y1G | 复制光标所在行到第一行的所有数据 |
| yG | 复制光标所在行到最后一行的所有数据 | 
| p | 粘贴在光标所在当前行的下1行 |
| P | 粘贴在光标所在当前行的上1行 |

### 替换取消
| 命令 | 作用 |
| --- | --- |
| r | 替换光标所在字符 |
| R | 从光标所在处开始替换字符，直到按Esc结束 |
| u | 撤销上一步操作 |
| U | 撤销整行操作 |
| ctrl+r | 取消撤销操作 |

### 全文搜索替换
| 命令 | 作用 |
| --- | --- |
| /string | 搜索指定的字符串；搜索时忽略大小写 (:set ic) |
| ?string | 从光标处向后搜索 |
| n | 搜索指定字符串出现的下一个位置 |
| N | 搜索指定字符串出现的上一个位置 |
| :%s/[旧值]/[新值]   | 在当前行进行替换 |
| :%s/[旧值]/[新值]/g | 全文替换字符串 |
| :[n1],[n2]s/[旧值]/[新值]/g | 在一定范围内替换字符串 |
| :%s/[旧值]/[新值]/c | 全文替换字符串,替换前进行询问 |
| :[n]s/[旧值]/[新值]/g | 在指定行进行替换 |
| :[n]s/[旧值]/[新值] | 只对搜索范围的每行首次匹配进行替换 |
| :[n],$s/word1/word2/c | 从第n行到最后一行，并进行确认 |

### 重复上一次操作
```
.
```

### 插入模式和替换模式切换 ###
```
Insert
```


## 插入模式

### 更正错误输入 ###
| 命令 | 作用 |
| --- | --- |
| Ctrl+h | 删除前一个字符 |
| Ctrl+w | 删除前一个单词 |
| Ctrl+u | 删除至行首 |

### 上下行同列复制 ###
| 命令 | 作用 |
| --- | --- |
| Ctrl+y | 复制上一行相同列的字符 |
| Ctrl+e | 复制下一行相同列的字符 |

### 调整缩进 ###
| 命令 | 作用 |
| --- | --- |
| Ctrl+t | 增加缩进 |
| Ctrl+d | 减少缩进 |

## 末行命令模式
 - 保存退出

  | 命令 | 作用 |
  | --- | --- |
  | :w | 保存 |
  | :w [filename] | 另存为 |
  | :n1,n2 w [filename] | 将n1到n2行的内容存储为filename这个文件 
  | :w! | 强制保存 |
  | :q | 不保存退出 |
  | :q! | 不保存强制退出 |
  | :wq | 保存退出 |
  | :wq! | 强制保存并退出 |
  | :x | 保存退出 |
  | ZZ | 保存退出 |
  | :r [filename] | 将filename文件的内容读入光标所在当前行的行后 |
 - 执行外部命令
执行外部命令
  | 命令 | 作用 |
  | --- | --- |
  | :! [command] | 切换到terminal执行command命令，然后按enter键返回编辑器 |
  | :r! [command] | 执行command命令，然后将命令执行结果输出到光标所在行的下一行 |
  | :r [filename] | 将指定文件的内容追加到光标后 |
 - 缩进
  ```
  :[n]>
  :[n]>>
  :[n1],[n2]<
  ```
 - 文本替换
  ```
  :3 /s/str1/str2
  :3 /s/str1/str2/g
  :% /s/[]/[]/g
  :% /s/[]/[]/gi
  ```
  - 取消搜索高亮显示
  ```
  :noh
  ```
## 可视模式
```
v
```
## 可视行模式
```
Shift+v
```
## 可视块模式
```
Linux: Ctrl+v
Windows: Ctrl+q
```

## 小技巧
### 在不退出Vim下执行Linux命令
```
:!<命令>
```
### 导入命令执行结果
```
:r !<命令>
:r <文件>
```
### 定义快捷键
```
:map ^P I#<ESC>               #在行首插入#号注释
:map ^B 0x                    #在行首删除第一个字符
```
### 连续行注释
```
:[n1],[n2]s/^/#/g
:[n1],[n2]s/^#//g
:[n1],[n2]s/^/\/\//g
```
### 替换
```
:ab [mymail] [fengchaoxhao@qq.com]         #输入mymail之后按回车或按空格键或按Esc，
                                           #停顿1秒后mymail自动被替换为fengchaoxhao@qq.com
```

### 多文件编辑
```
vim -o file1.txt file2.txt                  #以上下展示
vim -O file1.txt file2.txt                  #以左右展示
Ctrl+ww                                     #切换窗口
:qa                                         #全部退出
```
### 排版 ###
```
第一种方法：
	1. 在命令模式下输入gg将光标跳转到文件首部。
	2. 输入v进入可视模式。
	3. 输入V将光标跳转到文件尾部。
	4. 输入=进行格式化
第二种方法：
	gg=G
```
### 缩进 ###
```
单行缩进：
	Shift>>,Shift<<
	==		#注：执行该操作的时候，上一行必须已经缩进了，否则不起作用。
多行缩进：
第一种方法：
	1. 按v进入可视块模式。
	2. 选中多行。
	3. 用>或<选择缩进或缩出。
第二种方法：
	[n]==
```
### 跨文件复制、粘贴 ###
```
1.在末行命令模式下输入:sp横向切分一个窗口，或输入:vsp竖向切分一个窗口;
2.通过Ctrl+w+[方向键/hjkl]进行窗口光标切换;
3.输入:e [filename] 打开另一个文件;
4.接下来就可以在两个文件之间进行复制、粘贴操作了;
```

## 设置环境 ##
### 常用配置　###
| 命令 | 作用 |
| --- | --- |
| :set number | 显示行号 |
| :set nonumber | 取消显示行号 |
| :set ic | 搜索时忽略大小写 |

### 常用插件 ###
- [Molokai主题](https://github.com/tomasr/molokai "molokai")  
	```
	将molokai.vim配置文件放在/usr/share/vim/vim74/colors目录下
	```
- [Vundle插件管理器](https://github.com/VundleVim/Vundle.vim "Vundle插件管理器")  
	```
	先克隆Vundle仓库，然后将.vimrc文件拷贝到home目录下，然后执行:PluginInstall命令安装插件
	git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
	```
- [nerdtree插件](https://github.com/scrooloose/nerdtree "nerdtree插件")
- [YouCompleteMe自动补全插件](https://github.com/Valloric/YouCompleteMe.git)
- [javacomplete2自动补全插件](https://github.com/artur-shaik/vim-javacomplete2.git)
- [nerdtree-git-plugin](https://github.com/Xuyuanp/nerdtree-git-plugin.git)
- [airline底部状态栏插件](displays the mode + additional flags like crypt/spell/paste (INSERT))

	> 以下内容翻译自插件官方文档：
	> https://github.com/vim-airline/vim-airline.git

	```
	+-----------------------------------------------------------------------------+
	|~                                                                            |
	|~                                                                            |
	|~                     VIM - Vi IMproved                                      |
	|~                                                                            |
	|~                       version 8.0                                          |
	|~                    by Bram Moolenaar et al.                                |
	|~           Vim is open source and freely distributable                      |
	|~                                                                            |
	|~           type :h :q<Enter>          to exit                               |
	|~           type :help<Enter> or <F1>  for on-line help                      |
	|~           type :help version8<Enter> for version info                      |
	|~                                                                            |
	|~                                                                            |
	+-----------------------------------------------------------------------------+
	| A | B |                     C                            X | Y | Z |  [...] |
	+-----------------------------------------------------------------------------+
	```
- [taglist](https://github.com/vim-scripts/taglist.vim.git)
