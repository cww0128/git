# Github搭建事宜

## 第一节
### 一、下载git软件
（官网地址：[https://git-scm.com/](https://git-scm.com/ "https://git-scm.com/")）也可以找国内镜像下载，文件不大无关紧要。

### 二、不停的下一步下一步同意同意，安装完成git。

 
### 三、远程仓库的搭建

<blockquote>
<p>现在的情景是，你已经在本地创建了一个Git仓库后，又想在GitHub创建一个Git仓库，并且让这两个仓库进行远程同步，这样，GitHub上的仓库既可以作为备份，又可以让其他人通过该仓库来协作，真是一举多得。</p>

<p>首先，登陆GitHub，然后，在右上角找到“Create a new repo”按钮，创建一个新的仓库：
</p>

<p>在Repository name填入learngit(库名，可自定义)，其他保持默认设置，点击“Create repository”按钮，就成功地创建了一个新的Git仓库
</p>
</blockquote>





    
### 四、创建一个本地版本库

创建一个版本库非常简单，首先，选择一个合适的地方，创建一个空目录：
<pre><code>$ mkdir learngit
$ cd learngit
$ pwd
/Users/michael/learngit
pwd命令用于显示当前目录。
$ git init 
通过git init命令把这个目录变成Git可以管理的仓库
</code></pre>

<pre><code>Initialized empty Git repository in /Users/michael/learngit/.git/</code></pre>


瞬间Git就把仓库建好了，而且告诉你是一个空的仓库（empty Git repository），细心的读者可以发现当前目录下多了一个.git的目录，这个目录是Git来跟踪管理版本库的，没事千万不要手动修改这个目录里面的文件，不然改乱了，就把Git仓库给破坏了。

如果你没有看到.git目录，那是因为这个目录默认是隐藏的，用<code>ls -ah</code>命令就可以看见。

### 五、创建密钥
<pre><code>$ git config --global user.name "xxx"
$ git config --global user.email "xxx@xxx.com"
$ ssh-keygen -t rsa -C  "xxx@xxx.com"
cd ~/.ssh    （查看是否已经有了ssh密钥）
pwd    查看密钥存放的位置
$ pwd
/c/Users/admin/.ssh  
</code></pre>
找到这个文件夹里面的文件‘id_rsa.pub’ ，并且复制里面的公钥

在github个人中心setting上添加ssh密钥，这要添加的
是“id_rsa.pub”里面的公钥。


### 六、接下来提交文件


首先回到git库文件夹下面执行

<pre><code>git remote add origin https://github.com/cww0128/url.git          
   
git push -u origin master   
</code></pre>




<pre><code>git add . 
git commit -m "提交信息" 
git push origin master

当遇到下面的提示时：
fatal: 'origin' does not appear to be a git repository
fatal: Could not read from remote repository.

则需要重新输入
$ git remote add origin https://github.com/cww0128/url.git
</code></pre>


                


基本上到这里已经可以上传更新文件了


#### Git库基本操作
>廖雪峰的博客git相关
***
[https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013752340242354807e192f02a44359908df8a5643103a000](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013752340242354807e192f02a44359908df8a5643103a000 "廖雪峰博客")



## 第二节

##### 远程仓库直接拿下来
<pre><code>Git-bush   新建一个文件夹

$ git init    把当前目录编程git可以管理的仓库

git clone https://github.com/cww0128/url.git 即可
</code></pre>

   

   

   

##### 然后更新到远程目录的操作跟上面雷同：
<pre><code>git add .          
   
git commit -m "提交信息"   
  
git push origin master
</code></pre>


>这里提交后会提示用户名密码的输入，只需要输入github的用户名及密码就可以了。



###### 其余的操作基本如下：

版本控制

删除等，可以在上面提到的廖雪峰博客链接里面找到！这是关于github的操作，码云也是一样的操作思路。

#  在操作码云的时候遇到版本不同步的问题，需要先git pull  同步下载，不然就一直报错如下：


<pre><code>$ git push -u origin master
To git@github.com:******/Demo.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'git@github.com:******/Demo.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Merge the remote changes (e.g. 'git pull')
hint: before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.</code></pre>

### 解决办法：
<pre><code>$ git push -u origin master -f </code></pre>

### 解决思路地址
[http://blog.csdn.net/commshare/article/details/31771203](http://blog.csdn.net/commshare/article/details/31771203 "http://blog.csdn.net/commshare/article/details/31771203")


### 从线上下载代码到本地
第一次是克隆

- $ git clone git://github.com/schacon/grit.git

后面就是抓取


- git fetch origin master


- git merge origin/master 
