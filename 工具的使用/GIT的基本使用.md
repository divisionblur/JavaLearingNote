# GIT的基本使用(2.29.2版)

* ## Git的常用命令

  **==1.添加文件： add   提交文件：commit==**

  展示：
  【1】先创建一个文件：

  ![image-20201109194306824](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083051.png)

  【2】将文件提交到暂存区：

  ![image-20201109194328306](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083055.png)

  【3】将暂存区的内容提交到本地库：

  ![image-20201109194336753](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083058.png)


  注意事项：

  （1）不放在本地仓库中的文件，git是不进行管理(untracked)
  （2）即使放在本地仓库的文件，git也不管理，必须通过add,commit命令操作才可以将内容提交到本地库。

  

  **==2. git status看的是工作区和暂存区的状态==**

  创建一个文件，然后查看状态：

  ![image-20201109194535571](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083102.png)

  然后将Demo2.txt通过git add命令提交至：暂存区：

  ![image-20201109194544192](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083105.png)

  查看状态：

  ![image-20201109194553356](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083107.png)

  利用git commit 命令将文件提交至：本地库

  ![image-20201109194600434](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083115.png)

  

  现在修改Demo2.txt文件中内容：

  ![image-20201109194617537](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083118.png)

  然后再查看状态：

  ![image-20201109194625689](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083124.png)

  重新添加至：暂存区：

  ![image-20201109194643103](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083335.png)


  然后将暂存区的文件提交到本地库：

  ![image-20201109194702624](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083702.png)

  提交完再查看状态：

  ![image-20201109194711197](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083703.png)

  **==3.git log 可以让我们查看提交的，显示从最近到最远的日志==**

  

  ![image-20201109194747050](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083704.png)

  **log命令2：**

  当历史记录过多的时候，查看日志的时候，有分页效果，分屏效果，一页展示不下：

  ![image-20201109195021795](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083705.png)

  下一页：空格
  上一页： b
  到尾页了 ，显示END

  ![image-20201109195041202](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083706.png)

  退出：q

  日志展示方式：
  【1】方式1：git log  ---》分页
  【2】方式2：git log --pretty=onelint

  ![image-20201109195223426](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083707.png)

  【3】方式3：git --oneline

  ![image-20201109195248545](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083708.png)

  【4】方式4：git reflog
  多了信息：HEAD@{数字}
  这个数字的含义：指针回到当前这个历史版本需要走多少步

  ![image-20201109195309447](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083709.png)

* ## reset

  当需要进行版本回退的时候可以先用```git reflog```查看版本号(可以用q退出git reflog)

  然后用git reset --hard 版本号的方式进行回退

* ## hard,mixed,soft几个参数的区别

  **1.git reset --hard 版本号**

  ​	本地库指针移动的同时，重置暂存区，重置工作区。 (这三个地方的文件都回退到对应版本号的文件)

  ![image-20201109195400011](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083710.png)

  **2.git reset --mixed 版本号**

  ​	本地库指针移动的同时，==重置暂存区，而工作区不变。==

  ![image-20201109195410525](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083711.png)

  **3.git reset --soft 版本号**
  
  ​	本地库指针移动的时候，==暂存区和工作区都不动==。
  
  ![image-20201109195422856](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083712.png)
  
  **注意：日常开发中用的最多的还是带--hard参数的命令**





* ### 冲突问题的解决

  ![image-20201109195843104](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083713.png)

![image-20201109195921972](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083714.png)

【2】将分支切换到master:

![image-20201109200215063](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083715.png)

然后在主分支下 加入内容：

![image-20201109200246141](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083716.png)

![image-20201109200229242](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083717.png)

【3】再次切换到branch01分支查看：

![image-20201109200306363](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083718.png)

【4】将branch01分支  合并到  主分支 ：
（1）进入主分支：

![image-20201109200318189](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083719.png)

（2）将branch01中的内容和主分支内容进行合并：

![image-20201109200328730](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083720.png)

查看文件：**出现冲突**：

![image-20201109200349828](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083721.png)

解决：
公司内部商议解决，或者自己决定  人为决定，留下想要的即可：

![image-20201109200416938](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083722.png)

将工作区中内容添加到暂存区：

![image-20201109200435794](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083723.png)

然后进行commit操作：

![image-20201109200447481](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083724.png)

* ## git diff命令介绍

  1.用 `git diff 文件名 `比较工作区和暂存区的区别

  2.用`git diff` 后面什么都不加 比较的是工作区和暂存区中==所有文件==的区别

  3.用`git diff 版本号 文件名` 比较工作区和版本之前的区别

  ​	1.当用`git diff HEAD 文件名` 时比较的是工作区和当前版本的区别

  ​	2.用`git diff 版本号 文件名` 时比较的是版本号对应的版本与工作区指定文件的区别

  ​	3.比较两个版本的不同 比如用

  ​		`git diff HEAD HEAD^ 文件名` 来比较当前版本和上一个版本的却别

  ​		`git diff 74dec0d  1810739 文件名` 比较两个对应版本号 对应文件的区别

  ​		![image-20201106121203200](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083725.png) 

  ==红色的是前面的版本号对应文件的内容，绿色的是后面版本号对应文件的内容==



* ## 本地库与远程仓库的交互

  1.将本地库和远端仓库建立连接用如下的命令

  ​	`git add remote origin 远端仓库的地址`

  2.本地库的内容第一次push到远端仓库时用如下的命令

  ​	`git push origin -u master` (-u 的意思是将本地库的mater分支和远端仓库的分支对应起来,远程仓库origin)

  

  ​	以后再推送就可以直接使用命令`git push origin master`

  

  当协同开发的时候我首先把远端仓库的代码拷贝到自己的电脑上

  用`git clone 仓库地址`命令将仓库主分支克隆到电脑上(此时本地库的master分支和远端master分支对应),如果此时想把远程仓库的一个其他分支dev对应到本地来

  那么用命令`git checkout -b dev origin/dev`  不但把远端的分支弄到了本地，而且还把本地的这个分支和远端分支关联了起来。
  
  ```java
  git checkout -b dev origin/dev
  Switched to a new branch 'dev'
  Branch 'dev' set up to track remote branch 'dev' from 'origin'.

  ```

  

  当不同的人推送修改了同一处地方的文件到远端时会出错 这个时候git就会提醒你需要将代码pull到本地处理好冲突后 再push到远端仓库  如果此时是 不是由git checkout -b dev origin/dev 建立本地分支的人来拉取代码的话  那么就要将  他的本地分支和远端分支建立链接

  用如下的命令：
  
   ```git 
git branch --set-upstream-to=origin/<branch> dev
   ```

  就会出现提示：

  ```Branch 'dev' set up to track remote branch 'dev' from 'origin'.```  说明已经建立好跟踪关系
  
  这个时候就可以使用命令 ` git pull`拉取远端的代码 到本地就行手动处理冲突,将冲突处理完毕后再`git push origin dev`推送到远端。





* ## 对文件修改和删除的撤销

* ### 文件修改撤销

  1. 先说文件修改的撤销，当你正在编辑一个从没有添加的缓存区和提交到本地库的文件你想对修改进行撤销对 不起你只能手动删除  没有命令 ，而且也不需要命令啊手动删就行了嘛! 我为什么老是想着用命令来做

  2. 当你编辑了一个文件并且将它添加到了缓存区但是并没有提交到本地库，这个时候你想撤销这个暂存操作重新回到工作区那么输入命令`git restore --staged 文件名`   (我此时的版本是git 2.29.2可能有些版本并不是这个命令)

     ![image-20201106184900889](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083726.png)

     此时重新回到了工作区中并没有被追踪的状态

  3. ①.==如果你已经将正在修该的文件提交过本地库了==，这个时候你对工作区的文件进行修改如果想撤销这个修改那么你可以输入命令`git restore 文件名`来撤销修改

     ②.如果你修改了工作区中的文件而且还提交到了暂存区但是此时你后悔了想撤销修改可以输入命令

     `git restore --staged 文件名`撤销暂存此时又回到了① 如果连修改都不想要了执行①的操作即可

  4. 你修改了一个文件，添加到了暂存区又提交到了本地库那么只能进行版本回退了

  5. 

* ### 文件删除撤销

  ==同样的如果你已经将删除的文件提交过本地库了== 此时你在工作区误删了一个文件如果想要恢复文件使用命令

  `git restore 文件名`即可将删除的文件恢复。

  ![image-20201106191806458](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083727.png)

  如果将删除操作添加到了暂存区这时候就要

  ![image-20201106192455977](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083728.png)

  使用`git restore --staged 文件名`来撤销暂存，又回到了工作区中恢复删除文件的情况

  ![image-20201106192949430](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083729.png)

如果不但将删除操作添加到了暂存区，还提交到了本地库此时想恢复文件就只能进行版本回退了



免密操作：

【1】进入用户的主目录中：

![image-20201109202828032](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083730.png)

【2】执行命令，生成一个.ssh的目录：

![image-20201109202837930](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083731.png)

keygen  --- >  key generation
注意：C要大写
后面的邮箱，是你的github注册的账号的时候对应的邮箱
==三次回车确认默认值即可== 

发现在.ssh目录下有两个文件：

![image-20201109202942933](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083732.png)

![image-20201109202912359](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083733.png)

id_rsa是私钥不能让别人知道 id_rsa.pub是公钥


【3】打开id_rad.pub文件，将里面的内容进行复制操作：



【4】打开github账号：

![image-20201109203054926](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083734.png)

![image-20201109203128606](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083735.png)



【5】生成密钥以后，就可以正常进行push操作了：
对ssh远程地址起别名：

![image-20201109203148656](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083736.png)

展示别名：

![image-20201109203157022](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083737.png)

创建一个文件：

添加到暂存区，提交到本地库，然后push到远程库（地址用的是ssh方式的地址）

![image-20201109203210123](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083738.png)

**ssh方式好处：   不用每次都进行身份验证**
**缺陷：只能针对一个账号**

# Git与IDEA关联

当然也是要下载Git的

![image-20201109200751920](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083739.png)

本地库的初始化操作：

![image-20201109200832618](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083740.png)

然后会让你指定一个目录,这个目录就是用来建新的git repository的 如下图:

![image-20201109201119549](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083741.png)

添加到暂存区，再提交到本地库操作；  add +commit:（双击项目点击git再依次点击1和2）

![image-20201109201316485](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083742.png)

![image-20201109201210934](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083743.png)

![image-20201109201221077](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083744.png)

![image-20201109201439043](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083745.png)

利用IDEA进行克隆项目：

![image-20201109201711168](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115083746.png)

![image-20201109201720243](C:\Users\joy division\AppData\Roaming\Typora\typora-user-images\image-20201109201720243.png)

克隆到本地后：
这个目录既变成了一个本地仓库，又变成了工作空间。



**如何避免冲突**

【1】团队开发的时候避免在一个文件中改代码 
【2】在修改一个文件前，在push之前，先pull操作