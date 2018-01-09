```
# 在目录下初始化仓库
git init
# 添加所有的文件到暂存区
git add .
# 提交到本地的master
git  commit  -m "提交说明"
# 查看 工作区状态   这里面有很多的命令提示
git status
# HEAD 最新提交的版本 HEAD^ 上一个版本 HEAD^^^ 上上一个版本
git reset  --hard 000000000
#  把暂存区的修改  撤销掉  重新放到工作区（撤销了先前add的操作）
git rest HEAD  readme.md
# 丢弃工作区的修改(以版本库的为准)  
git checkout  -- readme.md
# 版本库  删除文件
git  rm   readme.md
```