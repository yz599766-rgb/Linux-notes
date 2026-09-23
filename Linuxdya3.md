Linux第三天学习了：
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

