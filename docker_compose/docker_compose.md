# 使用 Docker Compose 管理多容器應用程式

Docker Compose 是一個強大的工具，用於定義和運行多容器 Docker 應用程式。

透過 Docker Compose，你可以使用單個 YAML 文件配置整個應用程式的服務、網路和卷，然後使用一條命令啟動或停止整個應用程式。

## Docker Compose 基本指令

### 啟動應用程式

要啟動應用程式，可以使用以下命令，並加上 `-d` 標誌表示在後台運行容器：

```bash
docker-compose up -d
```

這將根據 `docker-compose.yml` 文件配置的服務啟動應用程式。

### 停止應用程式

要停止應用程式，使用以下命令：

```bash
docker-compose down
```

這會停止並刪除應用程式的所有容器、網路和卷。

### 查看容器狀態

如果你想查看正在運行的容器的狀態，可以使用以下命令：

```bash
docker-compose ps
```

這將顯示應用程式的容器狀態。

### 查看容器日誌

要查看應用程式的容器日誌，可以使用以下命令：

```bash
docker-compose logs
```

這將顯示應用程式容器的日誌。

### 在容器中執行命令

如果需要在服務容器中執行特定命令，可以使用 `exec` 命令。

例如，在 WordPress 容器中運行 bash shell：

```bash
docker-compose exec wordpress bash
```

### 重新構建服務容器

當你修改了 Dockerfile 或構建上下文時，需要重新構建服務容器。

使用以下命令：

```bash
docker-compose build
```

### 從遠端倉庫拉取最新鏡像

如果你的服務容器有依賴的基礎鏡像，可以使用以下命令拉取最新的鏡像：

```bash
docker-compose pull
```

### 重新啟動應用程式

要重新啟動應用程式的所有服務容器，可以使用以下命令：

```bash
docker-compose restart
```

這些是一些基本的 Docker Compose 命令，可用於協助你管理和操作使用 Docker Compose 部署的應用程式。

根據需要，你可以參考 Docker Compose 官方文檔以獲取更多詳細信息。

希望這份文章能夠幫助你更好地使用 Docker Compose 來管理多容器應用程式。

### [返回首頁](../README.md)

#### 關於我的連結
- GitHub: https://github.com/MarkwwLiu
- Facebook: https://www.facebook.com/TestMrMark
- Linkedin: https://www.linkedin.com/in/%E7%B4%8B%E7%91%8B-%E5%8A%89-03356584/
- CakeResume: https://www.cakeresume.com/me/ak790718

##### link: https://github.com/MarkwwLiu/docker_teaching/blob/main/docker_compose/docker_compose.md
