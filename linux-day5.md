Ssh:就是连接本地电脑终端和远程服务器的一条密道（可以理解为一条线）
本地电脑：遥控器负责输入指令   远程服务器：负责跑代码
1. & 符号：放到后台运行
作用：命令末尾加 &，让程序在后台跑，终端还能继续敲别的命令。
缺点：一旦关掉 ssh 终端，这个进程直接被杀掉
sleep 300 &      输出 [1] 12345   [1]：任务编号（job 号）      12345：进程 PID
2. jobs：查看当前终端下的后台任务 
输入jobs   输出： [1]+  Running     sleep 300 & 	Running：正在后台跑
Stopped：暂停挂起的任务
3. fg + 任务编号，把后台程序拉到前台，占据当前终端
fg 1： 现在 sleep 跑到前台，终端卡住，只能等它跑完；
如果想暂停前台任务：按 Ctrl + z → 任务暂停，回到命令行。
4. bg：把暂停的任务放到后台继续跑    bg  1
刚才按Ctrl+z暂停任务后，任务状态是 Stopped，不会继续执行。bg 唤醒它后台运行
Ctrl+z：前台程序暂停
bg：暂停任务 → 后台继续跑
fg：后台任务 → 切回前台
5. nohup(no hang up)：让进程脱离终端，就算关掉 ssh 也继续跑（忽略掉ssh这根线）
nohup python train.py &   （即使关掉本地终端，程序依然在远程服务器跑）
搭配 & 一起用：nohup 命令 &
默认输出日志保存到 nohup.out      想看训练日志：tail -f nohup.out
nohup 的进程，jobs 看不到，要用ps aux | grep python查看进程

6.tmux相当于远程终端服务器   tmux会话就是在这个tmux远程服务器终端开一个房间（可以开多个房间/会话，根据不同任务）  tmux窗口：就是在这个tmux房间中开不同的标签窗口，不同标签对应不同的功能。  
操作：
（1）.新建 tmux 会话：tmux new -s train1   -s train1：给会话起名叫 train1
执行后，直接进入 tmux 窗口，现在你敲的所有命令，都在 tmux 里面。

（2）.分离会话：快捷键 Ctrl+b，松开，再单独按 d
效果：离开 tmux 窗口，回到原来 ssh 终端，但是 tmux 里面的程序继续在服务器跑！
重点：不要直接关 ssh，优先 Ctrl+b d 分离；就算意外断 ssh，会话依旧保留。

（3）.查看所有 tmux 会话：tmux list

（4）. 重新接入（attach）会话   tmux attach  -t train1

（5）tmux 分屏（左右 / 上下）
进入 tmux 内部之后：
Ctrl+b 松开，再按 %：左右分屏
Ctrl+b 松开，再按 "：上下分屏
Ctrl+b 松开，方向键：在多个分屏之间切换光标
Ctrl+b 松开，x：关闭当前分屏窗口（会提示确认 y）

（6）.关闭 tmux 会话（彻底销毁）
tmux  kill-session -t train1   销毁train1会话

nohup：单纯保进程，看不到实时输出，日志存文件，调试不方便
tmux：完整虚拟终端，可以实时看打印、随时切窗口，算法训练首选



7. nvidia-smi 查看显卡信息（深度学习必用！） nvidia-smi
输出内容：
GPU 编号 0,1,2...
GPU 名称（RTX3090/A100）
Memory-Usage：显存占用
GPU-Util：GPU 算力使用率
Processes：哪个进程占用显卡

8. watch -n 1 nvidia-smi  持续监控显卡状态，实时刷新 ，退出 watch：按 Ctrl + c 
watch：周期性重复执行命令
-n 1：每隔 1 秒执行一次     

9. df -h 查看整块磁盘分区使用情况  disk filesystem

10. du -sh 查看文件夹大小
查看当前目录总大小 du -sh

查看data文件夹大小（数据集）du -sh ./data
df 发现磁盘满，用 du 一层层找哪个数据集、日志文件太大。

11.lsblk
作用：列出服务器上所有硬盘、硬盘里面的分区，以及每个分区挂载到哪个目录
lsblk：看硬件有什么。列出有几块硬盘 sda/sdb，有哪些分区。
就像：看电脑上插了多少块硬盘，不管有没有启用。

12: mount(查看磁盘挂载情况): 不带参数：查询，看现在哪些设备已经挂载、挂到哪个目录、是什么文件系统。
带参数：执行挂载，把一块没挂载的硬盘分区，手动挂到某个目录（新增硬盘的时候用）。

例子：mount /dev/sdb1 /data 含义：把 sdb1 这个硬盘分区，挂载到 /data 目录

敲 mount  输出; /dev/sdb1 on /data type ext4 (rw,relatime)
/dev/sdb1：第二块硬盘的 1 号分区
on /data：挂载到 /data 目录
type ext4：文件系统类型（Linux 常用格式）
rw：read+write，可读可写
👉 含义：sdb1 这个硬盘分区，挂在了 /data，访问 /data 就是读写这块硬盘。



Windows：硬盘插上，自动分配 C 盘、D 盘盘符，直接点开用。
Linux：没有盘符。硬盘分区必须挂载到某个目录（挂载点），你才能读写里面文件。
Linux 所有文件都在一棵大树上，树根是 /（根目录）。
挂载 = 把硬盘分区，“接到” 这棵大树的某个树枝（目录）上。
这个树枝的名字，就叫挂载点。


