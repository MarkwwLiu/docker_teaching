# 在 Docker 中安裝並運行 Jenkins：一步步指南

在本文中，我們將提供在 Docker 中安裝和運行 Jenkins 的詳細步驟。

使用 Docker 可以使 Jenkins 的設置和管理變得更加靈活和方便。

## 步驟 1：安裝 Docker

首先，確保你的系統上已經安裝了 Docker。

如果你尚未安裝，請按照 Docker 官方文檔的指引進行安裝。

## 步驟 2：拉取 Jenkins 映像

在終端中執行以下命令，拉取 Jenkins 的最新 LTS（Long Term Support）版本映像：

```bash
docker pull jenkins/jenkins:lts
```

這將下載 Jenkins 映像，供後續使用。

## 步驟 3：運行 Jenkins 容器

現在，使用以下命令在 Docker 中運行 Jenkins 容器。

此命令將 Jenkins 暴露在本地的 8080 端口，同時將 Jenkins 的數據存儲在 Docker 數據卷中：

```bash
docker run -d -p 8080:8080 -p 50000:50000 --name jenkins -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts
```

- `-d` 參數表示在後台運行容器。
- `-p 8080:8080 -p 50000:50000` 將容器內的 8080 和 50000 端口映射到主機上。
- `--name jenkins` 為容器指定一個名字（這裡為 "jenkins"）。
- `-v jenkins_home:/var/jenkins_home` 將 Jenkins 的數據存儲在 Docker 數據卷中，以便在容器重啟時保留數據。

容器運行後，你可以使用以下命令獲取 Jenkins 初始管理員密碼：

```bash
docker exec -it jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

複製輸出的密碼，然後訪問 [http://localhost:8080](http://localhost:8080)。

## 步驟 4：完成 Jenkins 設置

在瀏覽器中訪問 [http://localhost:8080](http://localhost:8080)，粘貼剛才複製的初始管理員密碼，然後按照設置嚮導完成 Jenkins 的配置。

## 在 Docker 中架設第二個 Jenkins

如果你需要在同一主機上運行第二個 Jenkins 實例，可以按照以下步驟操作：

### 步驟 1：拉取 Jenkins 映像（如果尚未拉取）

```bash
docker pull jenkins/jenkins:lts
```

### 步驟 2：運行第二個 Jenkins 容器

使用以下命令運行第二個 Jenkins 容器，確保使用不同的端口和數據卷：

```bash
docker run -d -p 8081:8080 -p 50001:50000 --name jenkins2 -v jenkins_home2:/var/jenkins_home jenkins/jenkins:lts
```

- `-d` 參數表示在後台運行容器。
- `-p 8081:8080 -p 50001:50000` 將容器內的 8080 和 50000 端口映射到主機上。確保端口未被其他應用程序使用。
- `--name jenkins2` 為容器指定一個不同的名字（這裡為 "jenkins2"）。
- `-v jenkins_home2:/var/jenkins_home` 將 Jenkins 的數據存儲在 Docker 數據卷中。

容器運行後，你可以使用以下命令獲取第二個 Jenkins 實例的初始管理員密碼：

```bash
docker exec -it jenkins2 cat /var/jenkins_home/secrets/initialAdminPassword
```

複製輸出的密碼，然後訪問 [http://localhost:8081](http://localhost:8081) 完成設置。

透過這樣的方式，你就在 Docker 中成功安裝和運行了兩個獨立的 Jenkins 實例，它們分別運行在不同的端口上，並擁有各自的數據存儲。

這為你提供了更大的靈活性，使得 Jenkins 的配置和使用變得更加方便。

### [返回首頁](../README.md)

#### 關於我的連結
- GitHub: https://github.com/MarkwwLiu
- Linkedin: https://www.linkedin.com/in/%E7%B4%8B%E7%91%8B-%E5%8A%89-03356584/
- CakeResume: https://www.cakeresume.com/me/ak790718

##### link: https://github.com/MarkwwLiu/docker_teaching/blob/main/docker_jenkins/docker_jenkins.md
