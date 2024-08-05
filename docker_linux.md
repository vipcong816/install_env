使用以下命令在 Ubuntu 中安装 Docker 以及 Docker Compose：

sudo apt install docker.io docker-compose

Docker 包被命名为 docker.io，因为在 Docker 出现之前就已经存在一个名为 docker（用于 Dockerlet 应用）的过渡包。因此，Docker 包必须被命名为其他名称。
安装完成后，你可以使用以下命令检查安装的版本：

docker -v


换源

vi /etc/docker/daemon.json

{ 
  "registry-mirrors" : 
    [ 
      "https://docker.m.daocloud.io", 
      "https://noohub.ru", 
      "https://huecker.io",
      "https://dockerhub.timeweb.cloud" 
    ] 
}

之后重启docker

sudo systemctl daemon-reload
sudo systemctl restart docker
