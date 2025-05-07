# 2025cloud Image Project

此專案提供兩個 Docker Image。

## Images 說明

1. **Nginx Image**
2. **Flask Python App Image**

---

## 如何透過 docker build 打包你的應用程式
可以透過以下指令打包：

打包 Nginx Image：
```bash
docker build -f nginx.dockerfile -t fifi1030/2025cloud:nginx .
```

打包 Flask App Image：
```bash
docker build -f app.dockerfile -t fifi1030/2025cloud:flaskapp .
```

說明：
* -f：指定 Dockerfile 路徑
* -t：設定 Image 的名稱與 Tag
* .：指定 Docker 可以存取當前目錄

## 如何透過 docker run 運行你Container Image
可以透過以下指令運行：

運行 Nginx Image：
```bash
docker run -d -p 8080:80 fifi1030/2025cloud:nginx
```

運行 Flask App Image：
```bash
docker run -d -p 5000:5000 fifi1030/2025cloud:flaskapp
```

說明：
* -d：讓容器在背景模式執行
* -p：指定主機與容器的 Port 對應
* Image Name：使用先前打包好的 Image

## 圖文的方式描述目前專案自動化產生 Container Image 的邏輯，以及 Tag 的選擇邏輯
1. 自動化產生 Container Image 的邏輯
   觸發事件有以下兩種：
   * Push 到 master
   * 建立 Pull Request

   自動化產生流程：
   * 當 Push 到 master 分支時，自動執行：
       * 檢查程式碼
       * 登入 DockerHub
       * Build nginx.dockerfile -> 產生 Tag：2025cloud:nginx
          * 成功後自動 Push 至 DockerHub
       * Build flaskapp.dockerfile -> 產生 Tag：2025cloud:flaskapp
          * 成功後自動 Push 至 DockerHub

2. Tag 的選擇邏輯
   | Dockerfile | 產生的 Tag |
   | :----: | :----: |
   | nginx.dockerfile | 2025cloud:nginx |
   | app.dockerfile | 2025cloud:flaskapp |

   Tag 命名原則：
   * 依據 Dockerfile 內容功能命名
       * nginx 對應 Web Server
       * flaskapp 對應 Python App
