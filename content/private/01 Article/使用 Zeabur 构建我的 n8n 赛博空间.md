标题里有两个工具，先简单介绍一番。

[Zeabur](https://zeabur.com/) 是国人开发的一款服务部署平台，无论使用什么编程语言或开发框架，只需要通过几个简单的按钮就可以部署，常见的 Ghost、Halo、Umami 都能部署，就连 WordPress 都可以。

[n8n](https://n8n.io/) 是一个开源的工作流自动化工具，类似于 [IFTTT](https://ifttt.com/)，iOS 用户应该更容易理解，相当于快捷指令，通过某个条件触发某个动作。

![cover.webp](https://huhexian.s3.bitiful.net/2023/08/03/64cbc2762892e.webp)

## 为什么构建一个“赛博空间”

因为每天都在获取信息，文章、音乐、视频等常见的内容形式，以及各种工具、软件，它们分散在不同的平台，管理起来比较麻烦。如果统一转发到一个地方，加以标签分类，对于以后检索会更加方便。于是我选择使用 n8n 转发我阅读的文章、点赞或投币过的视频、喜欢听的音乐、读过的书、看过的电影、收藏的各类工具等内容至 Telegram 频道，不同类型的内容打上不同的标签，通过标签索引，十分快捷方便就可以找到。这便是我的“赛博空间”。

目前为止，看到有人这般操作的有三人，[@novoreorx](https://t.me/reorx_share)、[@rayepeng_](https://t.me/RayeJourney)和[@pseudo_yu](https://t.me/pseudoyulife)，他们的博客里也有很详细的介绍和教程，我的部署过程很大一部分就参考了其中的内容。

## 如何部署 n8n
n8n 需要用到数据库，根据 Zeabur 官方文档，这里选择使用 PostgreSQL，所以事先安装好 PostgreSQL 客户端，我这里使用的是 [PostgreSQL 15](https://www.postgresql.org/download/) 在官网下载即可，这一步的目的是连接 Zeabur 安装的 PostgreSQL 并新建名为 n8n 的 Database。

### 安装 PostgreSQL
Zeabur 中有一个 Marketplace，搜索 PostgreSQL 即可一键部署该服务。

![](https://huhexian.s3.bitiful.net/2023/08/03/64cbb79f4287f.webp)

部署数据库之后就可以在 connect 中看到数据库的相关信息了，这里需要用到 Host、Port、Username。

![](https://huhexian.s3.bitiful.net/2023/08/03/64cbb79f679bc.webp)

接着就打开安装好的 PostgreSQL 15 客户端，右键单击左上角的“Server”，Register→Server，输入上面我提到的 Host、Port、Username，最后点击 Save 保存即可。

![](https://huhexian.s3.bitiful.net/2023/08/03/64cbb7a1ac36d.webp)

![](https://huhexian.s3.bitiful.net/2023/08/03/64cbb7a2d5459.webp)

刚刚我创建的 Server 命名为 n8n，然后右键单击 n8n 下的 Database，点击 Create Database，创建一个名为 n8n 的数据库就可以了，这是非常重要的一步，名字必须命名为 n8n。

![](https://huhexian.s3.bitiful.net/2023/08/03/64cbb7a401e78.webp)

![](https://huhexian.s3.bitiful.net/2023/08/03/64cbb7a41dc12.webp)

至此，有关 PostgreSQL 的设置就结束了。

>关于 Zeabur 的费用，也不用担心，提供了免费方案，每月有5美元的免费额度，我觉得应该是够用。

### 安装 n8n
同样可以在 Marketplace 里找到 n8n，点击一键部署。

![](https://huhexian.s3.bitiful.net/2023/08/03/64cbb7a582c0a.webp)

打开 n8n，右侧会有环境变量 Variable 的设置，本可以不用修改，但需要多加两条变量规则，不然会在使用 n8n 创建 Credential 的时候出错。

按照我给出的环境变量，将其中的自定义域名改为自己的就行，然后全部复制粘贴进去。

```
DB_POSTGRESDB_PASSWORD=${POSTGRES_PASSWORD}
PASSWORD=78nJ3L6u9Oh2
DB_POSTGRESDB_USER=${POSTGRES_USERNAME}
DB_POSTGRESDB_HOST=${POSTGRES_HOST}
DB_POSTGRESDB_DATABASE=n8n
WEBHOOK_URL=https://yourdomain
VUE_APP_URL_BASE_API=https://yourdomain
DB_TYPE=postgresdb
DB_POSTGRESDB_PORT=${POSTGRES_PORT}
EXECUTIONS_DATA_PRUNE=true
EXECUTIONS_DATA_MAX_AGE=72
EXECUTIONS_DATA_SAVE_ON_ERROR=all
EXECUTIONS_DATA_SAVE_ON_SUCCESS=none
EXECUTIONS_DATA_SAVE_ON_PROGRESS=false
EXECUTIONS_DATA_SAVE_MANUAL_EXECUTIONS=false
```

![](https://huhexian.s3.bitiful.net/2023/08/03/64cbbc8c400e0.webp)

最后一步，在 Zeabur 绑定自定义域名，一定要和上面环境变量中的保持一致，具体绑定方法参考 Zeabur 的文档吧。

## 如何使用 n8n
我自己都没玩懂这一方面，所有的 Workflow 都是参考[@novoreorx](https://github.com/reorx/n8n-workflows)和[@pseudo_yu](https://github.com/pseudoyu/yu-workflows)在 GitHub 上分享的代码，一键导入进去，创建好自己的 Credential，将其中的信息修改为自己的，就可以运行了。

YouTube 配置起来有点麻烦，需要申请官方的 API，不过看官方文档和视频操作起来也很简单。至于哔哩哔哩、网易云音乐、Raindrop、GitHub activities 就只需要使用 [RSShub](https://docs.rsshub.app/) 生成相应的 RSS 链接即可。这里说一句 RSS 牛逼，RSShub 牛逼，DIYgod 牛逼。

我的 Workflow 上传到 [GitHub](https://github.com/huhexian/workflow) 了，只需要上传这些 .json 文件至 n8n 即可。

![](https://huhexian.s3.bitiful.net/2023/08/03/64cbc4879f013.webp)

YouTube 采用的是 Google 官方的 API，这一步看文档就行；我将 Raindrop 作为书签工具，一方面收藏工具，另一方面收藏文章，所以我建了两个收藏，分别命名为 article 和 tool，开启分享功能，获取它们的 RSS 地址；GitHub 和豆瓣都有官方的 RSS 地址，直接使用就行；网易云音乐和哔哩哔哩则需要借助 RSShub 生成 RSS 地址。本来还想添加 Twitter，但它的 API 被马斯克搞得太恶心，遂放弃。

---

以上便是我使用 Zeabur 部署 n8n 的整个过程，虽然没有 Docker 部署那样快捷方便，但也值得尝试。同时欢迎关注我的 [Telegram 个人频道](https://t.me/hutalk)，可以看到我感兴趣的内容，或许会有相通之处。