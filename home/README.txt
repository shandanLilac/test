#Git命令

# 初始化仓库
git init
rm .git  //逆操作
//?? index.html 表示未跟踪文件

# 跟踪新文件,或暂存已修改的文件
git add index.html
git add .
git reset  //逆操作，这里加上HEAD为什么会报错

# 提交新文件,提交到仓库
git commit -m "msg" 
（working tree clean）
git commit -a -m "msg"  //这个命令有问题，不执行
git ls-files  //查看本地仓库文件
# 撤销对文件的修改,用仓库的文件替换工作区的文件，工作区文件的修改会丢失，谨慎操作。
git checkout -- index.html

# 从仓库中移除文件
  # 从git仓库和工作区同时移除
  git rm -f index.html
  # 只从git仓库中移除，工作区保留
  git rm -cached text.txt
  (逆)git restore --staged text.txt  git restore text.txt  //还原到仓库

# .gitignore
  # **/ /** !**
# glob
* [abc] ? [0-9] doc/**/*.pdf

# 查看提交历史
git log  //若终端卡在（END），输入q
git log -2
git log -2 --pretty=oneline
git log -2 --pretty=format:"%h | %an | %ar | %s"

# 回退到制定版本
git reset --hard <CommitID>  //Q1:怎么回退到我不认识的版本，还操作我的本地文件？
git reflog --pretty=oneline  //在旧版本中查看操作历史
git reset --hard <CommitID> 


# GitHub远程仓库的使用
https：0配置，但每次都输入密码
ssh：需要一些配置，之后就再不用输入账号密码
  ssh key：ssh-keygen -t rsa -b 4096 -C"your_email@example.com",3次回车，生成id_rsa id_rsa.pub两个文件夹；
  复制id_rsa.pub中的文本，粘贴到github点击头像->Setting->SSH and GPG Keys ->New SSH Key中，Title备注从何而来
  检测：ssh -T git@github.com  -> yes
  

#将远程仓库克隆到本地
git clone 远程仓库地址