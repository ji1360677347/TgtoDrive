<p align="center">
  <img src="picture/LOGO.png" alt="TgtoDrive 网盘文件管理工具" width="144">
</p>

<h1 align="center">TgtoDrive</h1>

<p align="center">
  <a href="https://hub.docker.com/r/walkingd/tgto123"><img src="https://img.shields.io/docker/pulls/walkingd/tgto123?style=for-the-badge&logo=docker&label=Docker%20Pulls" alt="Docker Pulls"></a>
  <a href="https://hub.docker.com/r/walkingd/tgto123"><img src="https://img.shields.io/badge/Docker%20Image-walkingd%2Ftgto123-2496ED?style=for-the-badge&logo=docker" alt="Docker Image"></a>
  <img src="https://img.shields.io/badge/Version-8.8.25-6C63FF?style=for-the-badge" alt="Version 8.8.25">
  <img src="https://img.shields.io/badge/Arch-amd64%20%7C%20arm64-111827?style=for-the-badge" alt="amd64 / arm64">
</p>

<p align="center">中文 · <a href="README_EN.md">English</a></p>

<p align="center"><strong>网盘转存与整理 · STRM 生成 · Emby 与飞牛媒体接入</strong></p>

详细介绍请参见[官网介绍](https://www.tgtodrive.top)。

[Docker 镜像](https://hub.docker.com/r/walkingd/tgto123) · [Telegram 交流群](https://telegram.me/TgtoDriveChat)

TgtoDrive 是一个通过 Docker 自部署的网盘文件管理工具。连接自己的网盘后，可以设置文件转存、影视与音乐整理、STRM 同步和媒体播放，也可以按需要启用频道监控、库存管理、插件和 OpenAPI。

软件完全免费，后续也不会收费。本项目不提供影视、音乐或其他资源，待管理文件、网盘账号与分享链接由用户自行提供。

## 功能概览

| 功能 | 可以做什么 |
| --- | --- |
| 分享转存与文件导入 | 将分享内容保存到指定网盘目录，按平台支持范围处理跨盘秒传、JSON 文件清单和本地文件秒传。 |
| 光鸭 GCID 导入 | 生成或导入 GCID 文件清单；连接 PikPak、迅雷账号后，处理对应分享并尝试秒传到光鸭。 |
| 影视整理 | 根据 TMDB 识别作品与季集，配置分类、命名、归档、覆盖比较和多版本共存；可联动生成 STRM 与通知 Emby 入库。 |
| 音乐整理 | 使用 MusicBrainz 识别音乐，按地区、艺术家、专辑和曲目归档，分别设置音频信息、未识别处理与覆盖偏好。 |
| STRM 生成 | 为网盘目录生成播放索引，支持手动同步、定时扫描和整理后增量更新，以及字幕、海报等配套文件同步。115 另有分享 STRM 生成与整理。 |
| Emby 与飞牛反代 | 配置 Emby、飞牛影视或飞牛音乐反代，通过 302 网盘直链播放；飞牛音乐使用本地目录与网盘目录映射定位原文件。 |
| 影视发现 | 浏览影视资料、榜单和追剧日历；在作品详情中按当前开放的 RE0、观影、SeedHub 来源查找资源，并使用已配置账号执行页面提供的转存或离线操作。 |
| Emby 库存管理 | 同步媒体库快照，筛选作品、来源、缺集和多版本；预览去重与清理清单，结合保护规则核对后执行。[库存说明](docs/media-inventory.md) |
| 监控、计划与通知 | 配置频道监控、关键词过滤、目录分流、分享更新监控与 Telegram 定时发送，在监控历史、整理历史和日志中检查结果。 |
| 媒体与系统工具 | Emby 看板、封面生成、元数据残留清理、115 分享 STRM 失效检测、AI 辅助识别、TMDB 设置、API 限速和连通性检测等。 |
| 其他功能 | SSH 终端、Pansou 聚合搜索、企业微信通知、资源社区配置、本地文件秒传及 Bilibili 视频下载，按各页面单独配置。 |
| Python 插件 | 导入符合协议的单 `.py` 或 ZIP/PYZ、TAR、7z、RAR 插件包，使用参数表单运行并查看结果与日志；支持定时执行和 AI 开发提示词。[开发说明](docs/toolbox-plugins.md) |
| GitHub 插件市场 | 在网页配置公开目录，搜索、安装与更新插件，提供完整性校验、依赖检查和离线目录缓存。[市场说明](docs/toolbox-marketplace.md) · [仓库模板](plugin-marketplace-template/README.md) |
| OpenAPI | 在「系统工具 → 实用工具 → OpenAPI」创建或撤销访问令牌，搜索接口用途、下载规范并复制调用示例，供脚本与插件使用。[接口说明](docs/openapi.md) |

## 支持的网盘

| 网盘 | 主要能力 |
| --- | --- |
| 115 网盘 | 分享转存、影视整理、音乐整理、盘内 STRM、分享 STRM、离线任务与文件清理 |
| 123 云盘 | 分享转存、文件清单导入、跨盘秒传、影视整理、音乐整理、STRM、离线任务与分享监控 |
| 光鸭云盘 | 分享转存、GCID 导入、PikPak / 迅雷分享秒传、影视整理、音乐整理、STRM 与离线任务 |
| 天翼云盘 | 分享转存、频道监控与定时文件清理 |

各网盘的入口和可用能力不同，按当前前端页面配置。第三方服务需要使用自己的账号；RE0 资源解锁按本人授权及上游积分规则处理。

## 界面预览

以下为 v8.8.25 的前端截图，使用空白演示配置，不含真实账号、密钥、私人目录或观看记录。点击图片可查看大图。

### 影视与音乐整理

![115 网盘影视整理：执行、STRM 联动与归档配置](picture/115网盘-网盘整理功能.png)

<details>
<summary>查看更多界面：音乐整理、123 整理、STRM、媒体接入与实用工具</summary>

#### 音乐整理

![115 网盘音乐整理：扫描来源、音乐库与未识别处理](picture/115网盘-音乐整理功能.png)

#### 123 云盘影视整理

![123 云盘影视整理配置](picture/123云盘-网盘整理功能.png)

#### STRM 来源与播放地址

| 115 网盘 | 123 云盘 |
| --- | --- |
| ![115 STRM 来源与播放地址](picture/115网盘-STRM生成.png) | ![123 STRM 来源与播放地址](picture/123云盘-STRM生成.png) |

#### Emby 与飞牛反代

![Emby 与飞牛反代：新增反代配置表单](picture/Emby反代.png)

#### Emby 看板连接

![Emby 看板：尚未连接服务器的设置界面](picture/Emby看板.png)

#### 实用工具

![实用工具：AI、TMDB、限速、媒体维护和 OpenAPI 入口](picture/实用工具.png)

</details>

## Docker Compose 部署

### 1. 准备目录

准备一台可以运行 Docker 的 NAS 或 Linux 设备，安装 Docker 20.10+ 和 Docker Compose 2.x。需要 Telegram 通知或机器人操作时，容器应能访问 Telegram API。

```bash
mkdir -p tgtodrive/db tgtodrive/strm
cd tgtodrive
```

### 2. 创建 `docker-compose.yml`

```yaml
version: '3'

services:
  tgtodrive-service:
    image: walkingd/tgto123:latest
    container_name: TgtoDrive
    network_mode: host  # 推荐 host 模式以简化端口映射和直链访问
    environment:
      # --- 基础配置 ---
      - TZ=Asia/Shanghai
      # 必填：WEB管理页面的登录账号密码
      - ENV_WEB_PASSPORT=admin
      - ENV_WEB_PASSWORD=password
    volumes:
      # 数据库与日志持久化，右侧固定为/app/db
      - ./db:/app/db
      # STRM输出目录：用于保存 /app/strm 下生成内容,/vol1/1000/Emby/strm 改成你的目录，右侧固定为/app/strm
      - /vol1/1000/Emby/strm:/app/strm
      # [可选] 本地文件秒传目录：左侧改为 NAS 上的个人文件目录，不需要可去掉
      - /path/to/local/files:/app/upload

    restart: always
```

启动前，修改示例中的管理账号密码和左侧宿主机目录。账号密码直接填写在 Compose 的 `environment` 中。

| 配置 | 填写说明 |
| --- | --- |
| `ENV_WEB_PASSPORT` / `ENV_WEB_PASSWORD` | 自己设置的网页管理账号与长密码；替换 `admin` 和 `password` |
| `./db:/app/db` | 持久化配置、登录状态、数据库与日志；更新和迁移时保留该目录 |
| `/vol1/1000/Emby/strm:/app/strm` | 左侧换成自己的 STRM 输出目录，右侧保持 `/app/strm`；媒体服务需要挂载同一份输出内容 |
| `/path/to/local/files:/app/upload` | 本地文件秒传使用的专用目录；不使用此功能时可移除这一行挂载 |

### 3. 启动与访问

```bash
docker compose pull
docker compose up -d
docker compose ps
```

在浏览器打开 `http://你的服务器IP:12366`，使用 Compose 中设置的管理账号密码登录。

## 首次配置

| 顺序 | 前端入口 | 操作与核对 |
| --- | --- | --- |
| 1 | 对应网盘 → 账号配置 | 按页面扫码、短信或账号密码流程连接自己的网盘，确认目录选择器能正常读取文件夹 |
| 2 | 系统工具 → 全局设置 | 按需配置网络代理和主机器人；需要通知时发送一条测试消息 |
| 3 | 系统工具 → 实用工具 | 在「TMDB 替代源设置」填写 TMDB Key；需要 AI 回退识别时，再配置「AI 辅助识别」及对应整理开关 |
| 4 | 对应网盘 → 链接转存、转存与秒传 JSON 等页面 | 设置相应入口的保存目录，通过页面提供的业务入口或机器人处理一份测试分享，确认实际保存位置 |
| 5 | 对应网盘 → 影视整理功能 / 音乐整理功能 | 选择来源与归档目录，配置规则，先手动整理少量有副本的文件，核对名称、目录和保留版本 |
| 6 | 对应网盘 → STRM 生成 | 选择已归档的网盘目录，填写播放器能访问的本服务地址，手动同步并实际播放一份文件 |
| 7 | 系统工具 → Emby与飞牛反代 | 按所选类型填写上游地址、连接信息与监听端口；保存并开启后，让客户端连接反代端口 |
| 8 | 对应监控或计划页面 | 手动验证通过后，再开启频道监控、定时整理或定时同步，在历史与日志中检查运行结果 |

迅雷分享转光鸭的入口是「光鸭云盘 → 秒传JSON、PP与迅雷」。先完成「迅雷云盘账号登录」，选择「迅雷秒传保存目录 ID」，再向机器人发送有效分享链接；有提取码时一并提供。

各页面的详细介绍与操作方法请参见[官网介绍](https://www.tgtodrive.top)。

## 使用时留意

- **目录范围**：整理来源与目标不能相同或互相嵌套，音乐来源也要避开影视来源的递归扫描范围。未识别目录放在正式影视库或音乐库之外。
- **音乐待整理区**：非音乐文件会进入网盘回收站。未识别音频按开关保留原处或移入独立未识别区；音乐整理本身不生成 STRM。
- **STRM 与原文件**：STRM 是播放索引，原网盘文件或分享仍需有效；字幕、海报等实体同步内容会占用本地空间。
- **地址与路径**：播放地址应从播放器所在设备验证；`localhost` 指当前访问端自己。路径映射左侧为 TgtoDrive 容器路径，右侧为媒体服务容器路径，两边应指向同一份内容。
- **反代端口**：host 模式直接使用配置的监听端口；改用 bridge 网络时，需映射管理端口及实际使用的各个反代端口。
- **飞牛音乐**：使用网盘原文件，本地目录与网盘目录中的歌曲应对应，不支持 NAS 转码回退。
- **清理与覆盖**：整理覆盖、文件清理和库存联动会影响真实文件；先用有副本的小样本核对，支持预览的工具先检查清单。
- **Emby Connect**：Emby 反代默认阻断 `/Connect/Exchange`，本地账号登录和播放仍可使用；部署影响与验证方法见 [Connect Exchange 防护说明](docs/emby-connect-exchange-protection.md)。

## 更新与备份

```bash
# 查看运行日志
docker compose logs -f --tail=100

# 拉取并应用新版镜像
docker compose pull
docker compose up -d

# 停止并启动现有容器
docker compose stop
docker compose start
```

更新前保留 `docker-compose.yml`、`db/` 和实际挂载的 STRM 输出目录。备份运行数据时，先停止容器再复制，或采用保证数据库一致性的备份方式；只备份正在写入的 SQLite 主文件可能遗漏事务数据。

迁移时沿用原持久化目录，更新后依次验证网页登录、网盘目录读取、任务状态和实际播放。`docker compose restart` 只重启已有容器，不会应用刚拉取的新镜像。

## 项目与使用范围

请仅管理本人拥有或已获授权的文件，并遵守相关服务条款。项目免费不代表网盘、媒体服务或其他第三方服务免费。

欢迎通过 [Telegram 交流群](https://telegram.me/TgtoDriveChat) 反馈问题；提供复现步骤、相关版本与必要日志时，请先移除账号、Token、Cookie、私人路径和分享提取码。

如果 TgtoDrive 对你有帮助，欢迎 Star 支持。
