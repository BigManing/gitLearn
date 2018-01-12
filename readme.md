
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
    #回退到某个节点 HEAD 最新提交的版本 HEAD^ 上一个版本 HEAD^^^ 上上一个版本    节点之后的修改都没有了  这个尽量少用
    git reset  --hard 000000000
    # 回退到某个节点   好消息是 修改内容还在
    git reset   000000000
    #  把暂存区的修改  撤销掉  重新放到工作区（撤销了先前add的操作）
    git rest HEAD  readme.md
    # 丢弃工作区的修改(以版本库的为准)  
    git checkout  -- readme.md
    # 查看commit过的 log引用 
    git reflog 


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
- 创建 合并命令

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
    

- 解决冲突

  如果两个分支都对相同文件做了修改，merge时会提示我们先修改  add   push

- 分支管理策略
        
        #在master分支上运行这句话
        git  meger  --no-ff  -m "不使用 fastforward模式"  dev

    master为稳定分支，发布正式版本。
    dev分支为开发环境，每个人再新建自己的分支，开发好后向dev分支合并。待dev开发ok了再向master分支合并。
    
    ![正常开发策略](https://cdn.liaoxuefeng.com/cdn/files/attachments/001384909239390d355eb07d9d64305b6322aaf4edac1e3000/0)
- bug分支
    
    master：上面有bug
    dev：开发到一半 暂时还不能commit到dev本地分支
    此时，我们需要暂存dev的工作状态，把bug修复好后，在切换过来就ok。
        
        #暂存
        git  stash
        #查看暂存
        git stash list
        #恢复暂存(同时删除备份)
        git stash pop
        #恢复暂存（不会删除备份）
        git stash  apply stash@{0}
###   标签

 - 创建 
    
        git tag v1.0 <或指定提交号>
        #查看标签

 - 查看 

        git tag 
        #显示详情
        git show  v1.0
        # 切换到tag处的工作目录
        git checkout  v1.0

 - 向远程仓库
 
        #推送指定tag
        git push origin v1.0
        #推送所有tag
        git push origin --tags 
        #删除本地标签
        git tag -d v0.4        
        #删除远程标签
        git push  origin :refs/tags/v0.4

###   使用github  码云
fork别人项目-> clone->修改提交->pull->request

多远程仓库可以是多个 ，仓库名要区分开：

    git  remote  rm origin
    git remote  add github  xxx
    git remote add gitee xxx

    git push  github master
    git push gitee  master

 ###  gitignore

有的时候 值允许在本地工作区中有，不希望推送到仓库中
。我们需要在根目录下建立一个`.ignore`文件，提交的时候忽略指定文件（官方实例）：https://github.com/github/gitignore。如果文件被忽略了就不会被追踪。

    touch .gitignore

查看文件被哪个规则忽略了：

    git check-ignore  -v  readme.md
