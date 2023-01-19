# 镜像源

Void Linux在几个地理区域都有镜像供你使用。一个新的安装将默认使用欧洲的主镜像，但你也可以 [选择一个不同的镜像]（./changing.md）
## 一级镜像

第1级镜像由Void Linux基础设施团队维护。这些镜像直接从构建主站同步，并且总是有最新的软件包。

默认情况下，XBPS将联系<https://repo-default.voidlinux.org>，它可以映射到任何一级镜像。

| 镜像源                                          | 地区              | 
|------------------------------------------------|------------------|
| <https://repo-fi.voidlinux.org/>               | 欧洲: 芬兰          |
| <https://mirrors.servercentral.com/voidlinux/> | 美国: 芝加哥        |
| <https://repo-us.voidlinux.org/>               | 美国: 堪萨斯       |
| <https://repo-de.voidlinux.org/>               | 欧洲: 德国          |

## 二级镜像

在可能的情况下，第2级镜像从附近的第1级镜像同步。这些镜像不是由Void管理的，也不保证软件包的新度和完整性,也不要求它们同步每个可用的架构或子库。

### 全球镜像

| Repository                                         | Location          |
|----------------------------------------------------|-------------------|
| <https://mirror.ps.kz/voidlinux/>                  | 亚洲: 哈萨克斯坦            |
| <https://mirrors.bfsu.edu.cn/voidlinux/>           | Asia: China       |
| <https://mirrors.cnnic.cn/voidlinux/>              | Asia: China       |
| <https://mirrors.tuna.tsinghua.edu.cn/voidlinux/>  | Asia: China       |
| <https://mirror.sjtu.edu.cn/voidlinux/>            | Asia: China       |
| <https://mirror.nju.edu.cn/voidlinux/>             | Asia: China       |
| <https://void.webconverger.org/>                   | Asia: Singapore   |
| <https://mirror.aarnet.edu.au/pub/voidlinux/>      | AU: Canberra      |
| <https://ftp.swin.edu.au/voidlinux/>               | AU: Melbourne     |
| <https://voidlinux.com.br/repo/>                   | BR: Ouro Preto    |
| <http://void.chililinux.com/voidlinux/>            | BR: Pimenta Bueno |
| <https://void.cijber.net/>                         | EU: Amsterdam, NL |
| <http://ftp.dk.xemacs.org/voidlinux/>              | EU: Denmark       |
| <https://mirrors.dotsrc.org/voidlinux/>            | EU: Denmark       |
| <https://quantum-mirror.hu/mirrors/pub/voidlinux/> | EU: Hungary       |
| <https://voidlinux.mirror.garr.it/>                | EU: Italy         |
| <http://ftp.debian.ru/mirrors/voidlinux/>          | EU: Russia        |
| <https://mirror.yandex.ru/mirrors/voidlinux/>      | EU: Russia        |
| <https://mirror.accum.se/mirror/voidlinux/>        | EU: Sweden        |
| <https://ftp.lysator.liu.se/pub/voidlinux/>        | EU: Sweden        |
| <https://void.sakamoto.pl/>                        | EU: Warsaw, PL    |
| <https://mirror.vofr.net/voidlinux/>               | USA: California   |
| <https://mirror2.sandyriver.net/pub/voidlinux/>    | USA: Kentucky     |
| <https://mirror.clarkson.edu/voidlinux/>           | USA: New York     |
| <https://mirror.puzzle.ch/voidlinux/>              | EU: Bern, CH      |

## Tor Mirrors

Void Linux is also mirrored on the Tor network. See [Using Tor
Mirrors](./tor.md) for more information.

## Creating a mirror

If you'd like to set up a mirror, and are confident you can keep it reasonably
up-to-date, follow one of the many guides available for mirroring with
[rsync(1)](https://man.voidlinux.org/rsync.1), then submit a pull request to
[the void-docs repository](https://github.com/void-linux/void-docs) to add your
mirror to the appropriate mirror table on this page.

A full mirror requires around 1TB of storage. It is also possible to mirror only
part of the repositories. Excluding debug packages is one way of decreasing the
load on the Tier 1 mirrors, with low impact on users.

Please keep in mind that we pay bandwidth for all data sent out from the Tier 1
mirrors. You can respect this by only mirroring if your use case for your mirror
will offset the network throughput consumed by your mirror syncing.
