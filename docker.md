在 AlmaLinux 8.10 上安装 Docker 是一个重要的步骤，以便在生产环境中有效地管理和部署容器化应用。以下是详细的安装教程以及需要注意的事项。

### 一、系统要求

在安装 Docker 之前，请确保你的系统满足以下要求：

- **操作系统**：AlmaLinux 8.10
- **内核版本**：Docker 需要 Linux 内核版本 3.10 或更高版本。

### 二、安装 Docker

以下是在 AlmaLinux 8.10 上安装 Docker 的步骤：

#### 1. 更新系统

首先，确保你的系统是最新的：

```bash
sudo dnf update -y
```

#### 2. 安装必要的依赖

安装一些必要的工具和库：

```bash
sudo dnf install -y yum-utils
```

#### 3. 添加 Docker 的官方仓库

使用以下命令添加 Docker 的官方仓库：

```bash
sudo dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

#### 4. 安装 Docker CE（社区版）

使用以下命令安装 Docker：

```bash
sudo dnf install -y docker-ce docker-ce-cli containerd.io
```

#### 5. 启动 Docker 服务

安装完成后，启动 Docker 服务并设置为开机自启：

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

#### 6. 验证 Docker 是否安装成功

运行以下命令以验证 Docker 是否安装成功：

```bash
sudo docker run hello-world
```

如果看到 "Hello from Docker!" 的消息，说明 Docker 安装成功。

### 三、配置 Docker 权限

为了避免每次使用 Docker 命令时都需要使用 `sudo`，可以将当前用户添加到 `docker` 组：

```bash
sudo usermod -aG docker $USER
```

执行完上述命令后，注销并重新登录，或者使用以下命令使组更改生效：

```bash
newgrp docker
```

### 四、注意事项

1. **安全性**：
   - 确保 Docker 守护进程的安全配置，考虑使用 TLS 加密 Docker API。
   - 定期检查 Docker 的安全更新。

2. **资源限制**：
   - 根据应用需求，合理配置 Docker 容器的 CPU 和内存限制，避免资源争用。

3. **数据持久化**：
   - 使用 Docker 卷（Volumes）来持久化数据，确保容器重启或删除后数据不会丢失。

4. **监控与日志**：
   - 使用监控工具（如 Prometheus、Grafana）和日志管理工具（如 ELK Stack）来监控 Docker 容器的运行状态。

5. **定期更新**：
   - 定期检查并更新 Docker 版本，以获取最新的功能和安全补丁。

### 五、总结

通过以上步骤，你可以在 AlmaLinux 8.10 上成功安装 Docker，并进行基本的配置。确保遵循安全最佳实践，以保护你的容器化应用。如果有其他问题，请随时询问！






sudo dnf -y install docker-compose-plugin




vi /etc/docker/daemon.json

{
 "registry-mirrors": ["https://docker-proxy.lingyiitech.com"],
"insecure-registries": ["http://10.0.24.65:8081","http://10.80.251.25:6006"],
"log-driver":"json-file",
"log-opts":{"max-size" :"50m","max-file":"1"}
}
 
systemctl daemon-reload 
systemctl restart docker











#安装git
sudo yum install -y git
#安装maven
sudo yum install -y maven
#安装依赖
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
#设置源
sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
sudo yum makecache fast
#安装docker
sudo yum install -y docker-ce
#启动服务
sudo systemctl start docker
#安装docker-compose
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" \
  -o /usr/local/bin/docker-compose


sudo chmod +x /usr/local/bin/docker-compose
#授权
sudo chmod +x /usr/local/bin/docker-compose
#检测版本号
docker-compose -v






#### 4. 安装 Docker CE（社区版）

使用以下命令安装 Docker：

```bash
sudo dnf install -y docker-ce docker-ce-cli containerd.io
```

#### 5. 启动 Docker 服务

安装完成后，启动 Docker 服务并设置为开机自启：

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

#### 6. 验证 Docker 是否安装成功

运行以下命令以验证 Docker 是否安装成功：

```bash
sudo docker run hello-world
```

如果看到 "Hello from Docker!" 的消息，说明 Docker 安装成功。

### 三、配置 Docker 权限

为了避免每次使用 Docker 命令时都需要使用 `sudo`，可以将当前用户添加到 `docker` 组：

```bash
sudo usermod -aG docker $USER
```

执行完上述命令后，注销并重新登录，或者使用以下命令使组更改生效：

```bash
newgrp docker
```

docker system df


