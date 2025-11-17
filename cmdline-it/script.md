## 引入
- 一些刻板印象

## 开始 
- 从纯黑的bash开始
- 解释 `mcig@MciGUBT:~$` 是什么
    - 计算机的世界是没有魔法的
    - 查手册
    - 介绍第一个命令: man
        - man是什么， man man 看看
        - 看不懂，全是英文，怎么办：
            - 方法一： pipe 给claude code/ qwen code（介绍pipe）
            ```
            man ls | qwen -p "将这个手册翻译成中文"
            ```
            - 方法二： tldr（too long didn't read）
    - ok我们现在知道man是什么了，那我们现在回到最开始的问题， mcig@MciGUBT:~$ 是什么。 眼尖的同学可能看到我执行了 `bash` 然后进入到当前这个界面， 那我们来搜下`bash`是什么
        - man bash, 一大串，看不懂
        - tldr bash, 大概解释了bash是什么， Bourne-Again SHell,。。。
        - 问ai： 
        ```
        man bash | qwen -p "根据这个手册,解释下我bash每一行前面的mcig@MciGUBT:~$是什么，用中文解释"
        ```
        输出结果：
        ```         
            ╭─   ~ ······································· took  54s at  09:35:47
            ╰─❯ man bash | qwen -p "根据这个手册,解释下我bash每一行前面的mcig@MciGUBT:~$是什么，用中文解释"
            好的，我来解释一下你bash命令行提示符 `mcig @MciGUBT:~` 每个部分的含义：
            这是由你 `.bashrc` 文件中的 `PS1` 变量定义的提示符格式：

            ```bash
            PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '（在.bashrc里）
            ```

            具体分解如下：
            - **`mcig`** - 这部分对应 `PS1` 中的 `\u`，代表当前登录的**用户名** (user)。在你的系统中，用户名是 `mcig`。
            - **`@`** - 这是一个固定的分隔符，直接写在 `PS1` 中。它将用户名和主机名分开，这是常见的显示格式。
            - **`MciGUBT`** - 这部分对应 `PS1` 中的 `\h`，代表当前系统的**主机名** (hostname)。你的系统主机名是 `MciGUBT`。
            - **`:`** - 这也是一个固定的分隔符，用于分隔主机名和当前工作目录。
            - **`~`** - 这部分对应 `PS1` 中的 `\w`，代表**当前工作目录的路径** (working directory)。`~` 是 `/home/mcig` 目录的**波浪号缩写**，表示你当前正在主目录中。
            - **`$`** - 这部分对应 `PS1` 中的 `\$`，是命令行提示符的结尾符号。`$` 表示当前是普通用户（如果是 `#` 则表示 root 用户）。
            **总结来说**：`mcig @MciGUBT:~` 这个提示符告诉你的信息是：
            - 当前用户是 `mcig`
            - 当前所在的计算机是 `MciGUBT`
            - 当前所在的目录是主目录 `~` (即 `/home/mcig`)
            - `$` 表示你当前是普通用户，可以输入命令了
            这个格式是 Debian/Ubuntu 系统的典型默认 bash 提示符格式，清晰地显示了用户身份、主机和当前目录。
        ```
    - 题外话，讲一下为什么 .bashrc会被ls忽略（. and .. dir， 顺便讲一下 cd -）
    - 题外话，叫markdown格式（打开vscode, 预览markdown,大概讲一下语法）
    - 再讲下ssh,连一下树莓派
## 命令行的使用

- ok, 那为什么要用命令行呢，肯定是在某些时候，比用GUI（Graphic User Interface）方便
    - 在宿舍看到舍友问ai问题，给ai仓库的目录结构，居然是手动截图。。。
        - `tree`
            - 目录太复杂，手动划终端很麻烦，甚至有的终端不支持滚动，怎么办
            - *有问题就有解决办法*
            - 用 | pipe 到 相关的可以把命令行输出复制到剪贴板的命令行工具
                - wayland原生 'wl-copy'
                - 大概解释下linux发行版，（其实我也不是很了解wayland,x11）
### 方便之处
1. 编辑单个文件
编辑单个文件，首先你要找到文件吧，有时候你不知道文件在哪，
    ```
    find, fzf | vim -  （管道的利用）
    fzf:fuzzy finder（模糊搜索）
    ```
2. 批量化工作（bash脚本）
这才是重点，`自动化`才是
(脚本例子)
    
## something fun

1. 一些远古命令的现代化替代
- cd -> zoxide
- ls -> eza / lsd
- cat -> bat
- tree -> eza --tree/-T
- find -> fd
- grep -> ripgrep
- top -> btop/htop
- man -> tldr

2. fun things
- 终端可以看视频
- 配置zsh
- fastfetch
- 放命令行的艺术 `https://www.bilibili.com/video/BV1WBVUzZEG9/?spm_id_from=333.337.search-card.all.click&vd_source=33bea32fef66aebde44b59203bc786b`
- 星爷视频 `【【入门】如何克服对黑漆漆的命令行的恐惧，相关知识串讲】 https://www.bilibili.com/video/BV1BFMVzuE4b/?share_source=copy_web&vd_source=dc976e99507908c280e5f8105591da52`

3. ssh下树莓派，显示器
4. build your own shell: https://app.codecrafters.io/courses/shell/overview
