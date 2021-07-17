# PcrGuildLibrary

### 简介

这个Repo是公主连结国服会战万用表的镜像，由目前负责万用表制作的花舞攻略组进行维护。
万用表原始地址：https://docs.qq.com/sheet/DWkdtR2djbnFiUGRk 。

本镜像中包含文档原始数据和转换后的json数据。在app集成万用表数据时建议使用本镜像。

由于只作为镜像，所以不会添加万用表之外的内容。和万用表相关的问题请咨询花舞攻略组组长。

### 数据文件地址

原始数据，以2021年7月会战A面为例：

* 索引：https://gitee.com/acaly/PcrGuildLibrary/raw/master/raw/202107/A/index.json
* 数据文件：https://gitee.com/acaly/PcrGuildLibrary/raw/master/raw/202107/A/<索引中提供的文件名>

转换后数据，以2021年7月会战A面为例：

* https://gitee.com/acaly/PcrGuildLibrary/raw/master/data/202107/A.json
* App中可以将`https://gitee.com/acaly/PcrGuildLibrary/raw/master/data/`记录为地址前缀

### Json数据文件格式

第一版（2021-07）

* 角色要求（`characters[i].requirements`）：目前万用表中没有，因此总是空数组。建议按字符串数组来读取。
* 时间（`time`）：目前只提供完整刀数据，没有尾刀数据，因此总是90秒。后续可能会增加尾刀数据。
* 作者（`sources[j].author`）：转换时使用一个单独的列表进行匹配搜索，不保证匹配成功。找不到作者名字的情况下为null。
* 标签（`labels`）：目前只根据轴名，为自动刀增加一个"Auto"标签。
* 图片（`sources[j].images`）：数组内容为图片下载地址。这些图片文件可以从原始数据文件夹中找到（需要读取index.json）。
* 范围：轴的时间和每个来源的伤害使用的是范围。范围目前有两种模式：单值模式（`value`）和上下界模式（`high`, `low`），后续也可能会允许上下界只有一个的情况（例如X秒以上的尾刀）。
