# Docker 基本指令及操作指南

Docker 是一個強大的容器化平台，提供了許多方便的命令和功能，讓開發者能夠更輕鬆地建立、運行和管理應用程序。以下是一份 Docker 基本指令及操作指南，助你熟悉 Docker 的常用操作。

## 基本命令

- `docker version`：查看 Docker 客戶端和伺服器的版本信息。
- `docker info`：顯示 Docker 系統信息，如容器和映像的數量。
- `docker help`：獲取 Docker 的幫助信息。

## 映像相關命令

- `docker images` 或 `docker image ls`：列出本地的 Docker 映像。
- `docker pull <image>`：下載 Docker 映像。
- `docker rmi <image>`：刪除本地的 Docker 映像。

## 容器相關命令

- `docker ps`：列出正在運行的容器。
- `docker ps -a`：列出所有容器，包括停止的。
- `docker run <options> <image>`：運行一個容器。
- `docker start <container>`：啟動一個停止的容器。
- `docker stop <container>`：停止一個運行中的容器。
- `docker restart <container>`：重啟一個容器。
- `docker exec -it <container> <command>`：在運行的容器中執行命令。
- `docker rm <container>`：刪除容器。

## 容器日誌和狀態

- `docker logs <container>`：查看容器的日誌。
- `docker top <container>`：查看容器中運行的進程。
- `docker stats <container>`：顯示容器的資源使用情況。

## 容器網路和端口

- `docker network ls`：列出 Docker 網路。
- `docker port <container>`：顯示容器的端口映射。
- `docker inspect <container>`：顯示容器的詳細信息，包括網路配置。

## 資料卷

- `docker volume ls`：列出 Docker 資料卷。
- `docker volume create <name>`：創建一個 Docker 資料卷。
- `docker volume inspect <name>`：顯示資料卷的詳細信息。
- `docker volume rm <name>`：刪除單一 volume。
- `docker volume prune`：刪除所有未使用的 volumes。

## Docker Compose

- `docker-compose up`：啟動容器組。
- `docker-compose down`：停止容器組並刪除相關容器。
- `docker-compose ps`：列出容器組中的容器。

## 清理命令

- `docker system prune`：清理未使用的數據（包括停止的容器、未被引用的網路和資料卷等）。

## 刪除容器

你可以使用以下命令刪除 Docker 中的容器：

- 刪除指定容器：

  ```bash
  docker rm <container_name_or_id>
  ```

- 刪除所有已停止的容器：

  ```bash
  docker rm $(docker ps -a -q)
  ```

- 刪除所有容器（包括運行中的）：

  ```bash
  docker rm -f $(docker ps -a -q)
  ```

- 刪除具有特定標籤的容器：

  ```bash
  docker rm $(docker ps -a -q --filter "label=<your_label>")
  ```

  將 `<your_label>` 替換為你想要匹配的標籤。

## Docker 容器改名稱

你可以使用 `docker rename` 命令來更改容器的名稱：

```bash
docker rename jenkins jenkins_mark
```

請確保容器目前處於停止狀態，然後再執行 `docker rename`。

```bash
docker stop jenkins
docker rename jenkins jenkins_mark
```

然後，你可以使用新名稱 "jenkins_mark" 來啟動容器：

```bash
docker start jenkins_mark
```

這樣你就完成了容器名稱的更改。請小心使用刪除容器的命令，確保你刪除的是正確的容器。

### [返回首頁](../README.md)

#### 關於我的連結
- GitHub: https://github.com/MarkwwLiu
- Facebook: https://www.facebook.com/TestMrMark
- Linkedin: https://www.linkedin.com/in/%E7%B4%8B%E7%91%8B-%E5%8A%89-03356584/
- CakeResume: https://www.cakeresume.com/me/ak790718

##### link: https://github.com/MarkwwLiu/docker_teaching/blob/main/docker_base/docker_base.md
