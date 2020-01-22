# gitskills
返回主页
leaf930814
博客园
首页
新随笔
联系
订阅
管理
git报错：'fatal:remote origin already exists'怎么处理？附上git常用操作以及说明。
git添加远程库的时候有可能出现如下的错误，



怎么解决？

只要两步：

1、先删除

1
$ git remote rm origin
2、再次执行添加就可以了。　　

 ----------------------------------------------git常用操作------------------------------------------------

说明，以下整理来自廖雪峰大神的《git教程》。

各位童鞋要下载git但是网速不给力的，可以从这里下载：https://pan.baidu.com/s/1qYdgtJY

1、安装git

git config --global user.name 'XXX'

git config --global user.email 'XXX'

 

 

2、创建本地库

mkidir learngit //自定义文件夹
cd learngit

touch test.md //创建test.md文件
pwd //显示当前目录


3、常用CRT

git init //初始化代码仓库
git add learngit.txt                               //把所有要提交的文件修改放到暂存区
git commit -m 'add a file'                      //把暂存区的所有内容提交到当前分支
git status                                            //查看工作区状态
git diff                                                //查看文件修改内容
git log                                                //查看提交历史
git log --pretty=oneline                       //单行显示
git reset --hard HEAD^　　　　　　　　 //回退到上一个版本，其中（HEAD^^(上上版本),HEAD~100(往上100个版本)）

commit id                                          //(版本号) 可回到指定版本
git reflog                                           //查看历史命令

其中说明【
工作区（Working Directory）
版本库（Repository） #.git
stage(index) 暂存区
master Git自动创建的分支
HEAD 指针

】

git diff HEAD -- <file>                                  //查看工作区和版本库里最新版本的区别
git checkout -- <file>                                   //用版本库的版本替换工作区的版本，无论是工作区的修改还是删除，都可以'一键还原'
git reset HEAD <file>                                   //把暂存区的修改撤销掉，重新放回工作区。
git rm <file>                                               //删除文件，若文件已提交到版本库，不用担心误删，但是只能恢复文件到最新版本


4、创建SSH Key，建立本地Git仓库和GitHub仓库之间的传输的秘钥

ssh-keygen -t rsa -C 'your email'                                                    //创建SSH Key
git remote add origin git@github.com:username/repostery.git          //关联本地仓库，远程库的名字为origin
//第一次把当前分支master推送到远程，-u参数不但推送，而且将本地的分支和远程的分支关联起来
git push -u origin master
git push origin master                                                                  //把当前分支master推送到远程
git clone git@github.com:username/repostery.git                            //从远程库克隆一个到本地库


5、分支
git checkout -b dev                                   //创建并切换分支
#相当于git branch dev 和git checkout dev
git branch                                                //查看当前分支，当前分支前有个*号
git branch <name>                                   //创建分支
git checkout <name>                                //切换分支
git merge <name>                                   //合并某个分支到当前分支
git branch -d <name>                               //删除分支
git log --graph                                          //查看分支合并图
git merge --no-ff -m 'message' dev            //禁用Fast forward合并dev分支

git stash                                                 //隐藏当前工作现场，等恢复后继续工作
git stash list                                            //查看stash记录
git stash apply                                         //仅恢复现场，不删除stash内容
git stash drop                                          //删除stash内容
git stash pop                                           //恢复现场的同时删除stash内容
git branch -D <name>                              //强行删除某个未合并的分支

//开发新feature最好新建一个分支
git remote                                               //查看远程仓库
git remote -v                                           //查看远程库详细信息

git pull                                                   //抓取远程提交
git checkout -b branch-name origin/branch-name                  //在本地创建和远程分支对应的分支
git branch --set-upstream branch-name origin/branch-name   //建立本地分支和远程分支的关联

6、其他---标签
git tag v1.0                                                                      //给当前分支最新的commit打标签
git tag -a v0.1 -m 'version 0.1 released' 3628164                 //-a指定标签名，-m指定说明文字
git tag -s <tagname> -m 'blabla'                                        //可以用PGP签名标签
git tag                                                                             //查看所有标签
git show v1.0                                                                   //查看标签信息
git tag -d v0.1                                                                 //删除标签
git push origin <tagname>                                               //推送某个标签到远程
git push origin --tags                                                       //推送所有尚未推送的本地标签

 

分类: 错误提示
好文要顶 关注我 收藏该文  
leaf+
关注 - 10
粉丝 - 24
+加关注
60
« 上一篇： Uncaught RangeError: Maximum call stack size exceeded-栈溢出
» 下一篇： 模块机制 之commonJs、node模块 、AMD、CMD
posted @ 2017-04-08 00:04  leaf+  阅读(43859)  评论(2)  编辑  收藏

评论列表
  #1楼 2019-07-04 18:48 恋晨有徐
挺好用的
支持(0) 反对(0)
  #2楼 2019-10-16 11:40 咚咚呱
创建本地库应该是mkdir learngit吧，楼主看一下
支持(0) 反对(0)
刷新评论刷新页面返回顶部
注册用户登录后才能发表评论，请 登录 或 注册， 访问 网站首页。
【推荐】超50万行VC++源码: 大型组态工控、电力仿真CAD与GIS源码库
【活动】开发者上云必备，腾讯云1核4G 2M云服务器11元/月起
【推荐】百度智能云岁末感恩季，明星产品低至1元新老用户畅享
【活动】京东云限时优惠1.5折购云主机，最高返价值1000元礼品！

相关博文：
· git报错：'fatal:remote origin already exists
· Git 学习笔记
· Git命令大全
· git的基本使用命令操作
· Git提示fatal:remoteoriginalreadyexists错误解决办法
» 更多推荐...

最新 IT 新闻:
· 沃达丰宣布退出天秤币项目，创始成员仅剩20家
· 小米消费金融公司落户重庆江北
· 被指迫于FBI压力，苹果放弃iCloud备份加密计划
· Netflix实现重要财务里程碑：用22年让年营收破200亿美元
· 微软CEO：Azure才是最大硬件业务 致力于打造“世界计算机”
» 更多新闻...
公告
前端技术分享


昵称： leaf+
园龄： 3年1个月
粉丝： 24
关注： 10
+加关注
<	2020年1月	>
日	一	二	三	四	五	六
29	30	31	1	2	3	4
5	6	7	8	9	10	11
12	13	14	15	16	17	18
19	20	21	22	23	24	25
26	27	28	29	30	31	1
2	3	4	5	6	7	8
搜索
 
 
随笔分类
CRT(2)
CSS(12)
HTML(5)
JavaScript(61)
node(9)
php(2)
tool集(1)
VUE(12)
错误提示(4)
构建工具gulp、webpack(4)
兼容性(7)
算法(8)
网络安全(5)
随笔档案
2019年12月(1)
2019年10月(1)
2018年7月(1)
2018年6月(4)
2018年5月(21)
2018年4月(1)
2018年3月(12)
2018年2月(5)
2018年1月(1)
2017年12月(2)
2017年11月(3)
2017年9月(2)
2017年8月(5)
2017年7月(15)
2017年6月(14)
2017年5月(22)
2017年4月(14)
2017年3月(3)
2017年2月(6)
2017年1月(3)
文章分类
web(1)
最新评论
1. Re:git报错：'fatal:remote origin already exists'怎么处理？附上git常用操作以及说明。
创建本地库应该是mkdir learngit吧，楼主看一下
--咚咚呱
2. Re:从Object.definedProperty中看vue的双向数据的绑定
学到了，不错
--pecool
3. Re:setTimeout、setInterval被遗忘的第三个参数
楼主是从这里知道的吗？
--关中刀客在青岛
4. Re:git报错：'fatal:remote origin already exists'怎么处理？附上git常用操作以及说明。
挺好用的
--恋晨有徐
5. Re:设置元素text-overflow: ellipsis后引起的文本对齐问题
原因是什么？
--BuleDog
阅读排行榜
1. git报错：'fatal:remote origin already exists'怎么处理？附上git常用操作以及说明。(43858)
2. JS的forEach和map方法的区别(41619)
3. Vue this.$nextTick原理(33409)
4. 怎么判断一个对象是不是数组类型？(28736)
5. setTimeout、setInterval被遗忘的第三个参数(17037)
评论排行榜
1. git报错：'fatal:remote origin already exists'怎么处理？附上git常用操作以及说明。(2)
2. getElementById和querySelector方法的区别(2)
3. setTimeout、setInterval被遗忘的第三个参数(2)
4. 从Object.definedProperty中看vue的双向数据的绑定(1)
5. JS中数组和字符串的方法大全(1)
推荐排行榜
1. git报错：'fatal:remote origin already exists'怎么处理？附上git常用操作以及说明。(6)
2. setTimeout、setInterval被遗忘的第三个参数(6)
3. JS的forEach和map方法的区别(3)
4. 怎么判断一个对象是不是数组类型？(2)
5. Vue this.$nextTick原理(2)
Copyright © 2020 leaf+
Powered by .NET Core 3.1.0 on Linux
