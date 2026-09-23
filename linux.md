markdown速查表：
命令                     |                        作用             |             示例
 pwd:展示当前路径 
 ls:列出当前文件夹里面的文件和子目录 
 cd:切换文件夹（就是进入）    cd ..返回上一级   cd ~ 回到家目录 操作均在家目录操作    cd 文件名 进入一个文件夹 
 mkdir:创建文件夹           可同时创建多个
 touch:创建单个文件 .txt    可同时创建多个
 cp:复制一个文件夹的内容 给另一个名字不同文件夹 两个文件夹都会保留   cp  a.py  b.py   cp -r folder1 folder2(文件夹前-r递归)
 mv:移除 把一个文件夹的内容移动到另一个文件夹 就是重命名    mv old.py new.py
 rm:删除 尤其注意对于文件夹的操作要递归（-r） -r表示贯穿整个文件夹   -r(递归)  -rf强制删除
 cat:查看文件内容 直接打印到终端 
 clear:清屏操作 
 echo:写入文件，并创建文件test.txt   echo "hello robot r1">test.txt   
 > :  这个写入会把文件中的原有内容给删掉      >>:追加，这个写入只是加在原文件的后面

 1.find . -name "1.txt" 查找当前目录下名为1.txt的文件    find . -name "*.txt"查找当前目录下的所有文件   2.find -type d 查找全部目录    find -type f 查找所有普通文件       find . -size +1k查找内存大于1k的文件

3.tree以树状图展示所有所有目录和子文件      tree -L 1:只展示一层不进入子目录

4.ln -s 软链接 :软连接就是一个指路者，一个到达源文件的快捷方式，点击软连接直接到达源文件位置  语法： ln -s 源文件 软连接文件 ln -s 1.txt link_1.txt

5.ls -L:查看文件详情：每行第一个字符代表文件类型 -：普通文件 d:文件夹 l:软连接文件   可以指定查看某一个文件的详情  ls -l file1.txt

6.tar(打包)：tar -zcvf test.tar.gz dir1 (打包dir1压缩为test.tar.gz) 语法：tar 参数 压缩包名字 要打包的文件 tar -zxvf test.tar.gz 解压文件test.gar.gz 解压到指定的目录：tar -zxvf test.tar.gz -C ./dir2  -c:change directory 解压到当前目录下dir2

7.zip/unzip: zip -r myzip.zip dir1 1.txt 把dir1与1.txt一起压缩成压缩包myzip.zip    unzip:解压  unzip  myzip.zip

8.less分页查看 q:推出less 

9.head 查看头部文件 默认前十行 head -n 3 log.txt查看前3行

10：tail 查看尾部文件，默认最后十行 tail -n 5 log.txt   tail -n 20 -f log.txt 查看末尾20行，并监测新增的内容 -f:follow跟踪 

11：wc:统计行数，单词数，字节数 wc -l test.txt行 wc -w test.txt单词 wc -c test.txt字节数 

12：通道符 “|” 前面命令的输出作为后面命令的输入


grep:抓取  grep "reward" train.log | wc -l   在train.log中抓取 reward

sort:按字母和数字进行排序  

uniq:去重 ：他只能去掉埃在一起的重复行  标准使用 先sort|unqi  grep "reward" test.txt |sort|uniq

whoami:查看登陆用户名 

sudo :以管理员权限执行命令  sudo 仅对后面的一条命令起作用

chmod:修改文件权限 谁可以读写运行这个文件  三类人： u:主人  g:同组的人  o:其他人   权限 r:4 w:2 x:1 

例子：chmod u+x  test.txt    chmod +x test.sh(默认给所有人加x)     chmod 755 test.sh   

chown:改变文件归属   sudo chown root:root test.sh      sudo chmod ubantu:ubantu test.sh

ps aux:一次性列出所有正在执行的系统的图片  ps aux | grep sleep

top: 实时动态查看进程 P：cpu占用     M：内存占用      

kill:根据PID，停止程序    获取PID：ps aux | grep sleep

pkill:根据名字终止程序   pkill sleep



