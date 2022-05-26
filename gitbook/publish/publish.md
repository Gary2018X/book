# 发布到线上

## Github Pages

1. 在github新建一个仓库
2. 仓库下新建一个gh-pages分支 保证gh-pages分支为空 如果原本main分支有readme 需要删除gh-pages分支下的readme
3. 然后把打包好的_book下的所有文件提交到gh-pages分支等待一会
4. 通过访问<https://用户名.github.io/仓库名/>即可访问

## 自己通过服务器发布

1. 将打包好的静态html文件上传到服务器的特定位置。
2. 通过nginx设置反向代理即可。将以下代码修改放到nginx配置下的http下面，然后启动或重启nginx服务就好。

```bash
server {
    listen       8089;#自定义端口 安全策略需要放通
    server_name  ip;#公网ip
    location / {
      root   /usr/_book;#项目地址
      index  index.html;#首页
      try_files $uri $uri/ /index.html;
    }
  }
}
```
