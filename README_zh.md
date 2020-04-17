# electron-download

利用 electron 封装的 客户端。内部使用 ffmpeg 下载rtmp视频流，并保存在本地。

## 类似的客户端

## 支持

- mac
- window
- linux


## 测试

可以利用nginx rtmp 插件 转发流

具体配置: https://www.jianshu.com/p/cf74a34af15d

``` nginx
rtmp {
  server {
    listen 1935;

    application rtmplive {
        live on;
        max_connections 1024;
    }
    application hls {

        live on;
        hls on;
        hls_path /usr/local/var/www/hls;
        hls_fragment 1s;

   }

  }

}
```


然后使用ffmpeg 进行推流

```
ffmpeg -re -i [你的视频文件的绝对路径] -vcodec copy -f flv rtmp://localhost:1935/abcs/room
```

然后使用客户端下载流。

# 截图

<img src="./image/1.png"></img>