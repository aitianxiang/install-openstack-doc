# install-openstack-doc

安装openstack文档

1，下载ubuntu16.04镜像，在vmware中安装ubuntu虚拟机；

2，打开虚拟机；

3，sudo apt-get update

4，sudo apt-get install vim

5，sudo apt-get install git

6，sudo apt-get install python-pip

7，换source源，ubuntu和pip的源

8，新建stack用户，授权stack用户并切换到stack用户

9，在stack用户根目录下git clone https://github.com/openstack-dev/devstack.git

10，git checkout stable/pike

11，cd devstack

12，将samples下的两个文件拷贝到devstack根目录

13，修改local.conf中的密码都统一为secret
```
ADMIN_PASSWORD=secret
DATABASE_PASSWORD=$ADMIN_PASSWORD
RABBIT_PASSWORD=$ADMIN_PASSWORD
SERVICE_PASSWORD=$ADMIN_PASSWORD
```

Hostip改为你自己机器的ip

```
HOST_IP=192.168.244.128
```

在最后一行加上下面几行：

```
GIT_BASE=http://git.trystack.cn
NOVNC_REPO=http://git.trystack.cn/kanaka/noVNC.git
SPICE_REPO=http://git.trystack.cn/git/spice/spice-html5.git
```
14，注释local.Sh最后两行
```
 #openstack security group rule create --project $OS_PROJECT_NAME default --protocol tcp --ingress --dst-port 22
 #openstack security group rule create --project $OS_PROJECT_NAME default --protocol icmp
```

15，开始安装： ./stack.sh

16，注意：

如果安装过程中ubuntu的源出现网络问题，就将sources.list文件换成原来的；

如果安装过程中python-pip也出现问题，将~/.pip文件夹删掉
