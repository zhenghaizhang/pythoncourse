# python3 与 pip3 安装与使用

## yum -y install openssl*  (pip依赖ssl环境)
## 编译安装python3
* 下载地址:https://www.python.org/ftp/python/
* tar zxvf Python-3.5.2.tgz
* cd Python-3.5.2
* ./configure --prefix=/usr/local/python35
* make && make install
##### PS：用了—prefix选项的另一个好处是卸载软件或移植软件。当某个安装的软件不再需要时，只须简单的删除该安装目录，就可以把软件卸载得干干净净；移植软件只需拷贝整个目录到另外一个机器即可（相同的操作系统）。
##### 一个小选项有这么方便的作用，建议在实际工作中多多使用
注：prefix的作用参考 http://blog.csdn.net/ronnyjiang/article/details/53283258
### 安装完成后默认就有pip3了.
### 安装完成可以装个模块试试
[root@localhost Python-3.5.2]# pip3 install pymysql
Collecting pymysql
* Downloading PyMySQL-0.7.9-py3-none-any.whl (78kB)
*   100% |████████████████████████████████| 81kB 6.3kB/s
* Installing collected packages: pymysql
* Successfully installed pymysql-0.7.9
* You are using pip version 8.1.1, however version 9.0.1 is available.
* You should consider upgrading via the 'pip install --upgrade pip' command.
### 使用它提示的命令就可以升级pip3了..
* 但是注意要把pip命令替换成pip3
* [root@localhost Python-3.5.2]# pip3 install --upgrade pip
*  Collecting pip
*  Downloading pip-9.0.1-py2.py3-none-any.whl (1.3MB)
*  100% |████████████████████████████████| 1.3MB 3.2kB/s
*  Installing collected packages: pip
*  Found existing installation: pip 8.1.1
*  Uninstalling pip-8.1.1:
*    Successfully uninstalled pip-8.1.1
*  Successfully installed pip-9.0.1
* [root@localhost Python-3.5.2]# pip3 --version
* pip 9.0.1 from /usr/local/lib/python3.5/site-packages (python 3.5)


### PS:
如果使用pip3安装插件的时候提示:
pip is configured with locations that require TLS/SSL, however the ssl module in Python is not available.
是因为系统缺少openssl-devel包
yum install openssl-devel -y  安装一下即可.
再按照上面的方法重新 编译一下即可.

#iPython网页启动

##安装必要的软件包：
* pip install "ipython[all]"
## 启动命令：ipython notebook --inline=pylib
* 自动采用默认浏览器打开http://localhost:8888/tree
## 如果想嵌入图表，则需要执行
*   %matplotlib inline

###### 以上参考博客园地址
###### http://www.cnblogs.com/zhzhang/tag/python/
