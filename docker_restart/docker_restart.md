# 在主機重啟後自動啟動 Docker 容器的方法

在使用 Docker 運行應用程序時，經常希望容器能夠在主機重新啟動後自動啟動。

這對於保持服務的穩定運行非常重要。

在這篇文章中，我們將探討如何使用 Docker 命令以及一些相關的技巧來實現這一目標。

## 更改重新啟動策略

假設你已經運行了一個 Jenkins 容器，但想要更改其重新啟動策略為 "always"，以確保容器在任何情況下都會重新啟動。

以下是相應的步驟：

### 1. 停止和刪除現有 Jenkins 容器

首先，需要停止和刪除當前正在運行的 Jenkins 容器。你可以使用以下命令：

```bash
docker stop jenkins
docker rm jenkins
```

### 2. 使用新的啟動命令

然後，使用新的啟動命令來啟動 Jenkins 容器，並包含 `--restart always` 選項：

```bash
docker run -d -p 8080:8080 -p 50000:50000 --name jenkins -v jenkins_home:/var/jenkins_home --restart always jenkins/jenkins:lts
```

這樣就設置了 Jenkins 容器的重新啟動策略為 "always"。

該容器將在停止時或主機重啟後自動重新啟動。

### 3. 使用 docker update 命令（可選）

如果你想在不刪除現有 Jenkins 容器的情況下更改重新啟動策略，可以使用 `docker update` 命令。
這可以在 Docker 1.12 及更高版本中使用。以下是一個示例命令：

```bash
docker update --restart always jenkins
```

這將更新 Jenkins 容器的重新啟動策略為 "always"，而不需要停止或刪除容器。

請注意，這種方法可能不適用於所有容器配置，某些配置可能需要完全重新啟動容器才能應用。

### 4. 確認設置

你可以使用以下命令來確認容器的重新啟動策略是否已成功設置：

```bash
docker inspect --format '{{.HostConfig.RestartPolicy.Name}}' jenkins
```

如果返回的值是 "always"，則表示重新啟動策略已經成功應用。

### 5. 啟動 Jenkins 容器

最後，如果 Jenkins 容器沒有立即啟動，你可以使用以下命令手動啟動它：

```bash
docker start jenkins
```

這樣就確保了 Jenkins 容器在主機重啟後自動重新啟動，並且使用 `--restart always` 重新啟動策略。

## 總結

通過遵循以上步驟，你可以輕鬆地更改 Docker 容器的重新啟動策略，確保它們在主機重新啟動後能夠自動啟動。

這對於維護服務的穩定性和持久運行非常重要。

請確保在更改容器配置之前仔細了解容器的特定需求和限制。

### [返回首頁](../README.md)

#### 關於我的連結
- GitHub: https://github.com/MarkwwLiu
- Linkedin: https://www.linkedin.com/in/%E7%B4%8B%E7%91%8B-%E5%8A%89-03356584/
- CakeResume: https://www.cakeresume.com/me/ak790718

##### link: https://github.com/MarkwwLiu/docker_teaching/blob/main/docker_restart/docker_restart.md
