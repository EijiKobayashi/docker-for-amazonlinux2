# docker-for-docker-for-amazonlinux2

Docker (Docker compose)
Amazon Linux 2 + Nginx + PHP7-fpm + mysql + phpMyAdmin の環境構築

- docker
- Amazon Linux 2
- Nginx
- php-fpm (7.2)
- MySQL
- phpMyAdmin

## 設定

Docker Desktop をインストールしてください。

[Docker Desktop](https://www.docker.com/products/docker-desktop)

---

## 使い方

#### 構築

プロジェクトディレクトリに移動して

```
$ docker-compose build --no-cache
```

#### 起動

- Web: [localhost:3000](http//localhost:3000)
- phpMyAdmin: [localhost:8080](http://localhost:8080)

```
$ docker-compose up -d
```

#### 状態

```
$ docker-compose ps
```

#### 終了

```
$ docker-compose down
```
