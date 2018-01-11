
### 初始化 提交到本地仓库 
    # 在目录下初始化仓库    
    git init
    # 添加所有的文件到暂存区
    git add .
    # 提交到本地的master
    git  commit  -m "提交说明"

###  查看状态  （ 这里面有很多的命令提示）
    git status

###  回退到某个节点 
    #回退到某个节点 HEAD 最新提交的版本 HEAD^ 上一个版本 HEAD^^^ 上上一个版本
    git reset  --hard 000000000
    #  把暂存区的修改  撤销掉  重新放到工作区（撤销了先前add的操作）
    git rest HEAD  readme.md
    # 丢弃工作区的修改(以版本库的为准)  
    git checkout  -- readme.md

### 删除文件  
    git  rm   readme.md
### 代码管理的两种方式  
- ssh 管理代码： 生成公私钥 ， 公钥放到github上 ，私钥自己留着  
   ```
    ssh-keygen -t rsa -C  "lingshui2008@qq.com"
    #打印公钥  这个东西有用
    cat ~/.ssh/id_rsa.pub 
    ```
- https管理代码：和仓库交流时需要用户名 密码、或者生成私人访问token 




###  提交到远程仓库 
    #添加远程仓库 进行关联 （origin 为远程仓库的名称   + 地址）
    git remote  add origin git@github.com:BigManing/gitLearn.git
    # 提交到远程仓库的master分支   -u  设定 pull push 的 上游 （upstream）
    git push  -u  origin  master

###   分支管理
    #查看
    git branch
    #创建
    git branch  xxx
    #切换
    git checkout  xxx

    #创建并切换到新分支
    git checkout  -b  xxx
    
    #合并分支到当前分支
    git merge xxx
    #删除分支
    git branch -d xxx
    
- 我们的解决冲突