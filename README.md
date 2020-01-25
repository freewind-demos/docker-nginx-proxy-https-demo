Docker nginx-proxy Https Demo
=======================

可以使用nginx-proxy来处理https，它来处理https的解析，转发后端时会使用简单的http

对于本地开发，我们可以手动生成相关的证书（注意在浏览器访问时会有警告）：

```
openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -nodes -subj '/CN=localhost' -days 3650
```

将生成的两个文件`cert.pem`和`key.pem`改名为相应的host name加上`crt`与`key`后缀。

```
npm run up

curl -H "Host: whoami.local" localhost:10080
curl -H "Host: whoami.local" https://localhost:10443
```

注意在command line下，后者会提示一大堆警告，看不出来。

为了在浏览器下看，需要先在`/etc/hosts`里增加`whoami.local`指向`127.0.0.1`，然后访问：

```
https://localhost:10443
```

正常的话会出来警告页面，选择unsafe后，可以看到期待的信息。
