Docker nginx-proxy Demo
=======================

可以使用nginx-proxy来反向代理其它的docker container中的服务

```
npm run up

curl -H "Host: whoami.local" localhost:10080
```

Will respond:

```
I'm f9e3e73c0cc4
```
