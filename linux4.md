Linux第四天学习笔记:
vim:文本编辑器  两模式：命令模式（不可以动），插入模式（编辑模式）
1. `a/e/i` ：在光标位置**进入插入模式**，开始打字写内容
2. `Esc`：退出插入模式，回到命令模式（必记！）
3. `:wq`：命令模式下输入，**保存文件并退出 vim**（w=write 保存，q=quit 退出）
4. `:q!`：命令模式下输入，**不保存修改，强制退出**（改坏了放弃修改用这个）
5. `/关键词`：命令模式下输入 `/`，然后输入文字，**向下搜索内容**，回车；按`n`跳到下一个匹配结果
6. `dd`：命令模式，**删除光标所在整行**
7. `yy`：命令模式，**复制光标所在整行**
8. `p`：命令模式，**粘贴刚刚复制 / 删除的内容到光标下一行**
9.dd+y ： 剪切
          vim arm_config.yaml


apt:用来安装软件   sudo apt update(刷新可安装的软件列表)      sudo apt install vim

dpkg:用来安装本地的软件包      apt是联网下载     dpkg -i xxx.deb        dpkg -l (查看已安装的软件)


conda:是用来创建不同环境的   给不同任务创建不同的环境 （相当于给不同人创建不同的房间）
**两个机器人项目**

1. 项目 A：机械臂强化学习，要求 `python=3.9`，`torch=1.10`
2. 项目 B：移动机器人导航，要求 `python=3.11`，`torch=2.2`
A任务：
conda create -n arm_env  python=3.9  
conda activate arm_env  
pip install torch==1.10 numpy gym
conda deactivate   退出环境

B任务：
conda create -n nav_env  python=3.11
conda activate nav_env
pip install torch==2.2 numpy gym
conda deactivate


pip:用于在conda环境中安装pyhon软件包  pip install numpy torch(同时安装numpy/torch两个软件包)  pip  list(查看当前环境装了哪些python包)

export： 临时设置环境变量，  **当前终端生效，关闭终端就失效**  

举个例子：播放器播放需要解码器软件     ，但是播放器在播放时：它不知道解码器软件在哪里    设置export环境变量就是告诉播放器去哪里找解码器
export LD_LIBRARY_PATH=/home/robot/lib:$LD_LIBRARY_PATH   先去/home/robot/lib  在去$LD_LIBRARY_PATH找

source ~/.bashrc:     ~/.bashrc 就是一个备忘录   新终端会自动读取~/.bashrc   但是若修改了~/.bashrc里面的内容  终端不会自动读取
需要sorce ~/.bashrc(重新读一遍备忘录)   ~/.bashrc内容才会生效


alias:起别名  # 临时生效  alias arm='cd /home/robot/arm_ws'   想要永久生效 将 alias arm='cd /home/robot/arm_ws' 写入~/.bashrc
在执行source~/.bashrc

 

