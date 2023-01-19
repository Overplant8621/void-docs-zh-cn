# 使用 Tor 镜像

Tor是一个匿名软件，它通过世界各地的志愿者的计算机提供流量，可以提供访问互联网上的常规网站或隐藏的网站。

以下是 Void 设在 Tor 上的镜像源:

| Repository                                                                             | Location   |
|----------------------------------------------------------------------------------------|------------|
| <http://lysator7eknrfl47rlyxvgeamrv7ucefgrrlhk7rouv3sna25asetwid.onion/pub/voidlinux/> | EU: Sweden |

## 在 Tor 下使用 xbps

XBPS可以使用Tor连接到镜像。这些镜像可以是普通的镜像，通过出口中继，亦或为了匿名性而在网络上隐藏服务镜像。

XBPS可以通过设置走 `SOCKS_PROXY` 环境变量,从而在 Tor 下使用 XBPS

### 安装 Tor

Tor 在 `tor` 软件包中提供

安装Tor以后,用个人用户身份启动之:

```
$ tor
```

或者设置其跟随系统启动.

默认情况下，Tor将作为一个客户端，并在TCP端口9050上打开一个SOCKS5代理。

### 让XBPS走socks5代理

XBPS会读取`SOCKS_PROXY`环境变量并使用其中指定的任何代理。中指定的任何代理。通过简单地将该变量设置为Tor客户端打开的代理的地址和端口，XBPS的所有连接将通过Tor进行。

一个通过Tor升级系统的例子:

```
# export SOCKS_PROXY="socks5://127.0.0.1:9050"
# xbps-install -Su
```

###使用暗网镜像源

要使用隐藏的服务镜像，默认的镜像需要被覆盖到指向内部使用的".onion "地址的配置文件来覆盖默认镜像。镜像需要用指向 Tor 网络内部使用的".onion "地址的配置文件来覆盖。XBPS 允许覆盖仓库地址 `/etc/xbps.d`。

将你的镜像文件从`/usr/share/xbps.d`复制到`/etc/xbps.d`，并将地址替换为Tor网站的地址（以Lysator的Tor地址为例):

```
# mkdir -p /etc/xbps.d
# cp /usr/share/xbps.d/*-repository-*.conf /etc/xbps.d/
# sed -i 's|https://repo-default.voidlinux.org|http://lysator7eknrfl47rlyxvgeamrv7ucefgrrlhk7rouv3sna25asetwid.onion/pub/voidlinux|g' /etc/xbps.d/*-repository-*.conf
```

Tor提供了分层的端到端加密，所以HTTPS是不必要的。(译者注:https还是有必要的)

在安装软件包时，如果像前面的例子那样设置了 `SOCKS_PROXY`，XBPS应该会指出它正在从指定的暗网地址进行同步。

```
# xbps-install -S
[*] Updating `http://lysator7eknrfl47rlyxvgeamrv7ucefgrrlhk7rouv3sna25asetwid.onion/pub/voidlinux/current/aarch64/nonfree/aarch64-repodata' ...
aarch64-repodata: 4030B [avg rate: 54KB/s]
[*] Updating `http://lysator7eknrfl47rlyxvgeamrv7ucefgrrlhk7rouv3sna25asetwid.onion/pub/voidlinux/current/aarch64/aarch64-repodata' ...
aarch64-repodata: 1441KB [avg rate: 773KB/s]
```

### 安全建议

如果你使用暗网，建议在你的环境中自动设置`SOCKS_PROXY`。如果没有这个设置，隐蔽服务的DNS查询会泄露给配置的DNS服务器。

要自动设置环境变量，请将其添加到
`/etc/profile.d`的文件中:

```
# cat - <<EOF > /etc/profile.d/socksproxy.sh
#!/bin/sh
export SOCKS_PROXY="socks5://127.0.0.1:9050"
EOF
```
