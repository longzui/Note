### Typora+GitHub

- 配置Typora图片

  ![image-20221124234818478](C:\Users\longzui\AppData\Roaming\Typora\typora-user-images\image-20221124234818478.png)

- 获取ssh密钥，并在github上添加ssh密钥

  - 获取ssh密钥
    - 生成ssh密钥：cmd =>  `ssh-keygen  -t  rsa -C your_email`
    - 获取ssh密钥：`cd ~/.ssh    cat ~/.ssh/id_rsa.pub`
    - 复制ssh密钥
  - 在github进入Settings,再点击里面的SSH and GPG KEYS ==> New SSH key
    - ![image-20221124235443018](C:\Users\longzui\AppData\Roaming\Typora\typora-user-images\image-20221124235443018.png)

- 创建远端仓库，先拉取远端仓库，在推送给远端仓库

  - `git clone 远端仓库地址`
  - **将要推送到远端的数据复制到拉取的仓库文件夹下，然后进入文件夹在进行推送**
  - `git add .`
  - `git commit -m '说明'`
  - `git push origin master`
  - `git push -u origin master`如果新建的远程仓库是空的，所以要加上 **-u** 这个参数。



`git config --global user.name your_name` 配置用户名

`git config --global user.email your_email` 配置邮箱

`git clone 需要克隆的代码地址 -b 分支名称`  可以直接克隆指定分支的代码

`git remote add origin 仓库地址` 本地仓库与git仓库进行关联



