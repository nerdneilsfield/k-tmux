# k-tmux

# Introduction

A tmux conf, which can work with [k-vim](https://github.com/wklken/k-vim)

简要说明 [k-tmux](http://www.wklken.me/posts/2015/08/06/linux-tmux.html)

# Screenshot

![screenshot](https://raw.githubusercontent.com/wklken/gallery/master/tmux/tmux.png)

# Install

Recommend

```
1. backup old tmux config if it is necessary

cp ~/.tmux.conf ~/.tmux.conf_bak

2. just get the file

curl https://raw.githubusercontent.com/nerdneilsfield/k-tmux/master/tmux.conf > ~/.tmux.conf

3. Done, enjoy it
```

Use github

```
git clone https://github.com/wklken/k-tmux.git
ln -s $PWD/k-tmux/tmux.conf ~/.tmux.conf
```


# 使用说明

我的TMUX配置及说明【K-TMUX】
我的tmux配置及说明【k-tmux】
安装
简要说明
1. session
2. window
3. pane
4. 复制粘贴
5. 其他
6. 增强
1. Tmuxinator
2. vim插件
7. 资源及参考
配置了一份 k-tmux

以下快捷键是对这份配置的说明, 大部分为tmux通用, 部分为修改自定义

安装
mac
$ brew install tmux
$ brew install reattach-to-user-namespace

ubuntu
$ sudo apt-get install tmux
简要说明
tmux -> session -> window -> pane

Tmux可以管理多组会话
一个会话（Session）可以包含多个窗口，一个窗口（Window）可以包含多个窗格（Pane）
操作前缀 PREFIX = Ctrl-a

1. session
# 创建, tmux new -s <name-of-my-session> 创建一个新的会话
$ tmux new -s basic

# 在tmux中创建一个会话
[PREFIX-:] new -s <name-of-my-session>

# 分离会话 detach
[PREFIX-d]
[detached (from session basic)]
or
$ tmux detach
or
[PREFIX-Ctrl-z]

# 查看已有会话列表(list-session)
$ tmux ls
basic: 1 windows (created Wed Aug  5 14:54:04 2015) [200x49]

# 在tmux中查看会话列表并切换
[PREFIX-s]

# 连接会话(只有一个)
$ tmux attach
$ tmux attach -t basic
$ tmux a -t basic

# 杀掉会话
$ tmux kill-session -t

# 重命名会话
[PREFIX-$]
2. window
# 创建一个新的窗口
[PREFIX-c]

# 重命名一个窗口
[PREFIX-,] 之后输入名字回车

# 切换到下一个窗口, k-tmux另外配置了PREFIX-t/T
[PREFIX-n]

# 切换到对应窗口
[PREFIX-1/2/3]

# 可视化选择切换到的窗口
[PREFIX-w]

# 查找窗口
[PREFIX-f]

# 退出窗口
exit or
[PREFIX-&] 会有确认
3. pane
分割 原先未修改键位的分割方式是[PREFIX-%]和[PREFIX-"] 重新映射为

# 垂直/水平分割窗口
[PREFIX-\] / [PREFIX--]
关闭pane

# 关闭一个面板, 要确认
[PREFIX-x]

或者
exit [面板里执行]
切换

[PREFIX-hjkl] pane之间移动

[Ctrl-hjkl]   pane之间移动
[Ctrl-\]      最近使用两个窗口之间切换
[PREFIX-q]    展示窗口数字并选择跳转
[PREFIX-o]    循环切换
大小调整

[Ctrl-HJKL] pane大小调整
[PREFIX-z]  trigger暂时把窗口变大
关闭及移动

[PREFIX-x] 关闭当前pane, 需确认
[PREFIX-}] 当前pane移到左边
[PREFIX-{] 当前pane移到右边
其他

[PREFIX-!]     当前pane在新的window中打开
[PREFIX-space] 会自动切换依次使用这些布局(几种窗口布局轮流切换)
4. 复制粘贴
[PREFIX-[] 进入复制模式

=> 可以进行的操作
space/v    开始选择
Ctrl-v     整块选择
hjkl       方向键移动
w/b        向前向后移动一个单词
fx/Fx      行内移动到下一个字符位置
ctrl-b/f   在缓冲区里面翻页
g/G        到缓冲区最顶/底端
/ ?        向下, 向上查找
n/N        查找后下一个, 上一个
Enter/y    复制
[PREFIX-]] 粘贴
其他增强:

# 复制整个pane可见区域
[PREFIX-:] capture-pane

# 查看缓冲区内容
[PREFIX-:] show-buffer

# 列出缓冲区列表
[PREFIX-:] list-buffers

# 从缓冲区列表选择并插入到当期面板
[PREFIX-:] choose-buffer => 回车
5. 其他
获得快捷键列表

[PREFIX-?]
进入命令模式

[PREFIX-:]

一些命令模式下的命令
# 新建窗口
new-window -n console

# 新建并执行命令
new-window -n processes "top"
6. 增强
1. Tmuxinator
Tmuxinator 是一个 Ruby 的 gem 包，可用于创建 Tmux 的会话。它的工作方式是先在配置文件中定义会话中的细节，然后用 1 条命令创建出这些会话

gem install tmuxinator
tmuxinator new project_a => ~/.tmuxinator/project_a.yml => 配置

启动: tmuxinator start project_a
可以别名: mux start project_a
2. vim插件
christoomey/vim-tmux-navigator, 安装更便捷的导航跳转
