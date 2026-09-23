学了什么？
1.创建仓库 git init myrepo     mkdir A   cd A  git init
2.git工作区：工作 暂存 仓库    文件状态：未跟踪  未修改 以修改 已暂存
3.添加文件到暂存区 git add .  git add    对于新文件跟踪并暂存
4.git status:查看文件状态
5.git log:查看提交记录   git log --oneline 查看简洁提交记录
6.git reset:退回   git reset --soft  提交号 （工作/暂存）   git reset --hard 提交号  (删)   git reset  --mixed  提交号   （工作）
7.git diff：查看差异  git  diff HEAD(工作/版本库差异)    git diff --cached (暂存/版本库差异)  比较特定版本差异 git diff 版本号1 版本号2
git diff 版本号3  HEAD(当前版本)     git diff HEAD～ HEAD    HEAD～（上一个版本）    
git  diff 文件名  只查看该文件名的差异    git diff  HEAD~3   HEAD  file3.txt   (比较file3当前版本，和前三个版本的差异)
8.git rm (删除操作)：删除工作内容，并加入暂存   执行git commit删除操作，才会执行
   git rm --cached other.log （删除版本区，工作区不删)   
9.gitignore忽略文件   把文件名输入.gitignore仓库 ，git commit文件就可以被忽略  
  也可以修改.gitignore的内容，vi .gitignore  在.gitignore中添加要修改的文件类型  git commit  git status 就看不见了
  .gitignore生效的前提是：这个文件不能已经加入版本库的文件
  注意：.gitignore中可以输入文件夹。忽略文件夹，前提文件夹不能被跟踪过，否则无效

  10:远程到本地：git clone   
  11.本地到远程git push  本地仓库和远程仓库之间第一次push要执行三条指令，之后两个仓库之间直接git push
  

