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


