# Docker_Setup
setup docker in ubuntu steps

#在国内的proedure
ubuntu下自带了docker的库，不需要添加新的源。
但是ubuntu自带的docker版本太低，需要先卸载旧的再安装新的。

注：docker的旧版本不一定被称为docker，docker.io 或 docker-engine也有可能，所以我们卸载的命令为：
$ apt-get remove docker docker-engine docker.io containerd runc

如果不能正常卸载，出现如下情况，显示无权限时，需要添加管理员权限才可进行卸载：
![image](https://github.com/user-attachments/assets/2e7fe544-7c30-49c9-b32c-8eb3c9a9ab96)

安装步骤
更新软件包
在终端中执行以下命令来更新Ubuntu软件包列表和已安装软件的版本:

sudo apt update
sudo apt upgrade

安装docker依赖
Docker在Ubuntu上依赖一些软件包。执行以下命令来安装这些依赖:

apt-get install ca-certificates curl gnupg lsb-release
添加Docker官方GPG密钥
执行以下命令来添加Docker官方的GPG密钥:

curl -fsSL http://mirrors.aliyun.com/docker-ce/linux/ubuntu/gpg | sudo apt-key add -
结果如下：
![image](https://github.com/user-attachments/assets/6f9592f3-7008-4435-9c1d-ae23f7df1e17)

添加Docker软件源
执行以下命令来添加Docker的软件源:
sudo add-apt-repository "deb [arch=amd64] http://mirrors.aliyun.com/docker-ce/linux/ubuntu $(lsb_release -cs) stable"
注：该命令需要使用root权限

安装docker
执行以下命令来安装Docker:

apt-get install docker-ce docker-ce-cli containerd.io

配置用户组（可选）
默认情况下，只有root用户和docker组的用户才能运行Docker命令。我们可以将当前用户添加到docker组，以避免每次使用Docker时都需要使用sudo。命令如下：

sudo usermod -aG docker $USER

注：重新登录才能使更改生效。
运行docker
我们可以通过启动docker来验证我们是否成功安装。命令如下：

systemctl start docker
安装工具

apt-get -y install apt-transport-https ca-certificates curl software-properties-common

重启docker

service docker restart
验证是否成功

sudo docker run hello-world




