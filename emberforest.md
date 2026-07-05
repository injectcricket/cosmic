# WebIndex 轻量级技术资源导航站

WebIndex 是一个面向开发者、技术研究者与运维工程师的轻量级技术资源导航与外链汇总工具。该项目专注于将分散于互联网各处的技术文章、文档、工具站与社区讨论按主题归集，提供统一的检索入口与浏览视图。WebIndex 本身不存储任何第三方内容，仅作为索引层与路由层存在，适用于个人知识管理、团队技术文档聚合以及公开技术资源的分类整理场景。

WebIndex 的核心定位是“技术的起点页”。当开发者需要快速查找某个技术点的参考实现、踩坑记录或官方文档时，WebIndex 提供经过初步筛选与分类的链接集合，减少重复搜索成本。项目采用纯静态页面生成方案，无需数据库支持，可直接部署于 Nginx、Apache、S3 或任何静态托管服务之上，也可嵌入现有文档站点作为子模块。

## 功能概览

**多层级分类索引**：支持按技术领域、语言生态、应用场景建立三级分类目录，每个分类下挂载对应的外链资源，分类结构通过 JSON 配置文件定义，便于增删改查。

**全文检索与标签过滤**：集成浏览器端全文搜索能力，基于 Lunr.js 或 MiniSearch 构建索引，支持关键词检索与标签组合过滤，搜索结果实时高亮显示。

**资源状态检测**：定期对收录的外链进行可用性检查，标记失效链接与响应超时的资源，在页面中通过视觉标识区分正常、可疑与失效三种状态。

**自定义元数据扩展**：每条资源记录支持标题、描述、标签、来源站点、收录时间、最后验证时间等元数据字段，元数据 schema 可自由扩展。

**多种视图模式**：提供列表视图与卡片视图两种展示方式，列表视图适合快速浏览大量条目，卡片视图适合展示资源摘要信息与预览图。

**导入导出与批量操作**：支持 CSV 与 JSON 格式的资源清单导入导出，便于与其他书签管理工具或团队知识库进行数据迁移与同步。

**响应式适配与无障碍支持**：前端界面针对桌面端与移动端分别优化布局，遵循 WCAG 2.1 AA 级无障碍标准，确保键盘操作与屏幕阅读器兼容。

**低依赖部署架构**：项目构建产物为纯静态 HTML、CSS 与 JavaScript 文件，无需运行时服务端进程，可放置于任何 HTTP 服务器下直接访问。

## 应用场景

技术团队内部文档聚合：开发团队可将日常使用的 API 文档镜像、内部运维手册、项目部署指南、代码规范文档等链接统一收录至 WebIndex，作为团队知识库的入口页面，新成员入职时可快速了解团队技术栈与常用工具链。

个人开发者的阅读清单管理：独立开发者或技术博主可使用 WebIndex 整理每日阅读的技术博客、GitHub 趋势项目、Hacker News 热点讨论以及各大技术会议演讲视频链接，形成个人技术成长的追踪看板。

技术社区资源共建：开源社区或技术兴趣小组可搭建公共 WebIndex 实例，由社区成员共同维护某一技术领域的外链资源库，例如 Rust 生态工具索引、云原生故障排查案例汇编、前端性能优化最佳实践合集等，通过 Pull Request 机制更新资源清单。

离线文档中心入口：在无互联网接入的内网环境中，WebIndex 可作为内部文档中心的导航页，指向内网部署的 Swagger UI、Javadoc、Sphinx 生成的 HTML 文档、Confluence 空间等，实现内网技术资产的统一路由。

## 快速开始

以下指令适用于 Linux 与 macOS 环境，Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/webindex/webindex-starter.git
cd webindex-starter

# 安装项目依赖（使用 npm）
npm install

# 执行构建流程，生成静态站点至 dist 目录
npm run build

# 启动本地开发服务器，监听端口 8080
npm run serve
```

执行完上述命令后，访问 http://localhost:8080 即可查看本地运行的 WebIndex 实例。如需自定义资源列表，请编辑 `data/resources.json` 文件并重新执行构建命令。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 16.x 或更高 | 用于运行构建脚本与开发服务器，推荐使用 LTS 版本 |
| npm | 8.x 或更高 | 依赖包管理工具，随 Node.js 一同安装 |
| Git | 2.25 或更高 | 用于克隆仓库与版本控制，支持子模块更新 |
| 现代浏览器 | Chrome 90+ / Firefox 88+ / Edge 90+ | 前端运行时环境，需支持 ES2020 与 CSS Grid 特性 |
| HTTP 服务器 | Nginx 1.18+ / Apache 2.4+ / Caddy 2+ | 生产环境部署时需提供静态文件服务，支持 gzip 压缩与缓存头配置 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何快速搭建一个可用的导航站实例，包括初始配置与首次构建 |
| 配置手册 | docs/configuration.md | 资源清单 JSON Schema 详解、分类树定义方法、元数据字段说明 |
| 部署指南 | docs/deployment.md | 各平台部署步骤、环境变量配置、CDN 加速与 HTTPS 强制策略 |
| 扩展开发 | docs/development.md | 自定义主题开发、插件机制说明、前端构建管道定制、API 适配器编写 |

## 资源列表

- http://m.mobile.cvsifc.cn/Article/details/577513.sHtML
- http://m.mobile.cvsifc.cn/Article/details/9162.sHtML
- http://m.mobile.cvsifc.cn/Article/details/2995820.sHtML
- http://m.mobile.cvsifc.cn/Article/details/1089.sHtML
- http://m.mobile.cvsifc.cn/Article/details/4297.sHtML
- http://m.mobile.cvsifc.cn/Article/details/775279.sHtML
- http://m.mobile.cvsifc.cn/Article/details/75561.sHtML
- http://m.mobile.cvsifc.cn/Article/details/422422.sHtML
- http://m.mobile.cvsifc.cn/Article/details/03566.sHtML
- http://m.mobile.cvsifc.cn/Article/details/7038.sHtML
- http://m.mobile.cvsifc.cn/Article/details/1406984.sHtML
- http://m.mobile.cvsifc.cn/Article/details/933782.sHtML
- http://m.mobile.cvsifc.cn/Article/details/8142.sHtML
- http://m.mobile.cvsifc.cn/Article/details/6357.sHtML
- http://m.mobile.cvsifc.cn/Article/details/1285.sHtML
- http://m.mobile.cvsifc.cn/Article/details/66166.sHtML
- http://m.mobile.cvsifc.cn/Article/details/08656.sHtML
- http://m.mobile.cvsifc.cn/Article/details/979545.sHtML
- http://m.mobile.cvsifc.cn/Article/details/8126530.sHtML
- http://m.mobile.cvsifc.cn/Article/details/6615479.sHtML
- http://m.mobile.cvsifc.cn/Article/details/45911.sHtML
- http://m.mobile.cvsifc.cn/Article/details/3050500.sHtML
- http://m.mobile.cvsifc.cn/Article/details/6898.sHtML
- http://m.mobile.cvsifc.cn/Article/details/7889135.sHtML
- http://m.mobile.cvsifc.cn/Article/details/678961.sHtML
- http://m.mobile.cvsifc.cn/Article/details/1345161.sHtML
- http://m.mobile.cvsifc.cn/Article/details/8280896.sHtML
- http://m.mobile.cvsifc.cn/Article/details/6732.sHtML
- http://m.mobile.cvsifc.cn/Article/details/3174.sHtML
- http://m.mobile.cvsifc.cn/Article/details/5587.sHtML
- http://m.mobile.cvsifc.cn/Article/details/7329446.sHtML
- http://m.mobile.cvsifc.cn/Article/details/0848.sHtML
- http://m.mobile.cvsifc.cn/Article/details/0598027.sHtML
- http://m.mobile.cvsifc.cn/Article/details/011241.sHtML
- http://m.mobile.cvsifc.cn/Article/details/541203.sHtML
- http://m.mobile.cvsifc.cn/Article/details/2791329.sHtML
- http://m.mobile.cvsifc.cn/Article/details/84884.sHtML
- http://m.mobile.cvsifc.cn/Article/details/469327.sHtML
- http://m.mobile.cvsifc.cn/Article/details/98267.sHtML
- http://m.mobile.cvsifc.cn/Article/details/1946.sHtML
- http://m.mobile.cvsifc.cn/Article/details/10319.sHtML
- http://m.mobile.cvsifc.cn/Article/details/699299.sHtML
- http://m.mobile.cvsifc.cn/Article/details/22245.sHtML
- http://m.mobile.cvsifc.cn/Article/details/893391.sHtML
- http://m.mobile.cvsifc.cn/Article/details/0135.sHtML
- http://m.mobile.cvsifc.cn/Article/details/16004.sHtML
- http://m.mobile.cvsifc.cn/Article/details/526857.sHtML
- http://m.mobile.cvsifc.cn/Article/details/9032.sHtML
- http://m.mobile.cvsifc.cn/Article/details/792294.sHtML
- http://m.mobile.cvsifc.cn/Article/details/811160.sHtML
- http://m.mobile.cvsifc.cn/Article/details/6283117.sHtML
- http://m.mobile.cvsifc.cn/Article/details/48653.sHtML
- http://m.mobile.cvsifc.cn/Article/details/37393.sHtML
- http://m.mobile.cvsifc.cn/Article/details/765172.sHtML
- http://m.mobile.cvsifc.cn/Article/details/9699.sHtML
- http://m.mobile.cvsifc.cn/Article/details/5385500.sHtML
- http://m.mobile.cvsifc.cn/Article/details/736678.sHtML
- http://m.mobile.cvsifc.cn/Article/details/48931.sHtML
- http://m.mobile.cvsifc.cn/Article/details/7915.sHtML
- http://m.mobile.cvsifc.cn/Article/details/96401.sHtML
- http://m.mobile.cvsifc.cn/Article/details/32951.sHtML
- http://m.mobile.cvsifc.cn/Article/details/9123.sHtML
- http://m.mobile.cvsifc.cn/Article/details/5629929.sHtML
- http://m.mobile.cvsifc.cn/Article/details/9220.sHtML
- http://m.mobile.cvsifc.cn/Article/details/437645.sHtML
- http://m.mobile.cvsifc.cn/Article/details/9511.sHtML
- http://m.mobile.cvsifc.cn/Article/details/9702380.sHtML
- http://m.mobile.cvsifc.cn/Article/details/681074.sHtML
- http://m.mobile.cvsifc.cn/Article/details/2274190.sHtML
- http://m.mobile.cvsifc.cn/Article/details/15062.sHtML
- http://m.mobile.cvsifc.cn/Article/details/2052587.sHtML
- http://m.mobile.cvsifc.cn/Article/details/39994.sHtML
- http://m.mobile.cvsifc.cn/Article/details/2109.sHtML
- http://m.mobile.cvsifc.cn/Article/details/79006.sHtML
- http://m.mobile.cvsifc.cn/Article/details/1135.sHtML
- http://m.mobile.cvsifc.cn/Article/details/039044.sHtML
- http://m.mobile.cvsifc.cn/Article/details/26818.sHtML
- http://m.mobile.cvsifc.cn/Article/details/06346.sHtML
- http://m.mobile.cvsifc.cn/Article/details/133689.sHtML
- http://m.mobile.cvsifc.cn/Article/details/2967.sHtML
- http://m.mobile.cvsifc.cn/Article/details/1394.sHtML
- http://m.mobile.cvsifc.cn/Article/details/065583.sHtML
- http://m.mobile.cvsifc.cn/Article/details/733111.sHtML
- http://m.mobile.cvsifc.cn/Article/details/151272.sHtML
- http://m.mobile.cvsifc.cn/Article/details/4647251.sHtML
- http://m.mobile.cvsifc.cn/Article/details/0096.sHtML
- http://m.mobile.cvsifc.cn/Article/details/27030.sHtML
- http://m.mobile.cvsifc.cn/Article/details/0071178.sHtML
- http://m.mobile.cvsifc.cn/Article/details/0880509.sHtML
- http://m.mobile.cvsifc.cn/Article/details/174491.sHtML
- http://m.mobile.cvsifc.cn/Article/details/3362026.sHtML
- http://m.mobile.cvsifc.cn/Article/details/10391.sHtML
- http://m.mobile.cvsifc.cn/Article/details/2335298.sHtML
- http://m.mobile.cvsifc.cn/Article/details/0362183.sHtML
- http://m.mobile.cvsifc.cn/Article/details/975225.sHtML
- http://m.mobile.cvsifc.cn/Article/details/5012.sHtML
- http://m.mobile.cvsifc.cn/Article/details/6693938.sHtML
- http://m.mobile.cvsifc.cn/Article/details/2349349.sHtML
- http://m.mobile.cvsifc.cn/Article/details/667620.sHtML
- http://m.mobile.cvsifc.cn/Article/details/52117.sHtML
- http://m.mobile.cvsifc.cn/Article/details/72565.sHtML
- http://m.mobile.cvsifc.cn/Article/details/11434.sHtML
- http://m.mobile.cvsifc.cn/Article/details/105431.sHtML
- http://m.mobile.cvsifc.cn/Article/details/10825.sHtML
- http://m.mobile.cvsifc.cn/Article/details/0337965.sHtML
- http://m.mobile.cvsifc.cn/Article/details/058170.sHtML
- http://m.mobile.cvsifc.cn/Article/details/515278.sHtML
- http://m.mobile.cvsifc.cn/Article/details/0002148.sHtML
- http://m.mobile.cvsifc.cn/Article/details/4681.sHtML
- http://m.mobile.cvsifc.cn/Article/details/7900075.sHtML
- http://m.mobile.cvsifc.cn/Article/details/1764.sHtML
- http://m.mobile.cvsifc.cn/Article/details/8155705.sHtML
- http://m.mobile.cvsifc.cn/Article/details/6834658.sHtML
- http://m.mobile.cvsifc.cn/Article/details/672086.sHtML
- http://m.mobile.cvsifc.cn/Article/details/6660.sHtML
- http://m.mobile.cvsifc.cn/Article/details/0040.sHtML
- http://m.mobile.cvsifc.cn/Article/details/792065.sHtML
- http://m.mobile.cvsifc.cn/Article/details/0696303.sHtML
- http://m.mobile.cvsifc.cn/Article/details/0499.sHtML
- http://m.mobile.cvsifc.cn/Article/details/86599.sHtML
- http://m.mobile.cvsifc.cn/Article/details/7722.sHtML
- http://m.mobile.cvsifc.cn/Article/details/642610.sHtML
- http://m.mobile.cvsifc.cn/Article/details/65536.sHtML
- http://m.mobile.cvsifc.cn/Article/details/30252.sHtML
- http://m.mobile.cvsifc.cn/Article/details/62748.sHtML
- http://m.mobile.cvsifc.cn/Article/details/351938.sHtML
- http://m.mobile.cvsifc.cn/Article/details/4051407.sHtML
- http://m.mobile.cvsifc.cn/Article/details/080759.sHtML
- http://m.mobile.cvsifc.cn/Article/details/642960.sHtML
- http://m.mobile.cvsifc.cn/Article/details/2674241.sHtML
- http://m.mobile.cvsifc.cn/Article/details/085155.sHtML
- http://m.mobile.cvsifc.cn/Article/details/9426135.sHtML
- http://m.mobile.cvsifc.cn/Article/details/07667.sHtML
- http://m.mobile.cvsifc.cn/Article/details/8557.sHtML
- http://m.mobile.cvsifc.cn/Article/details/423809.sHtML
- http://m.mobile.cvsifc.cn/Article/details/8138668.sHtML
- http://m.mobile.cvsifc.cn/Article/details/088824.sHtML
- http://m.mobile.cvsifc.cn/Article/details/3298843.sHtML
- http://m.mobile.cvsifc.cn/Article/details/2403.sHtML
- http://m.mobile.cvsifc.cn/Article/details/10232.sHtML
- http://m.mobile.cvsifc.cn/Article/details/02069.sHtML
- http://m.mobile.cvsifc.cn/Article/details/64550.sHtML
- http://m.mobile.cvsifc.cn/Article/details/7911.sHtML
- http://m.mobile.cvsifc.cn/Article/details/486097.sHtML
- http://m.mobile.cvsifc.cn/Article/details/239905.sHtML
- http://m.mobile.cvsifc.cn/Article/details/3776.sHtML
- http://m.mobile.cvsifc.cn/Article/details/7772418.sHtML
- http://m.mobile.cvsifc.cn/Article/details/81396.sHtML
- http://m.mobile.cvsifc.cn/Article/details/46366.sHtML
- http://m.mobile.cvsifc.cn/Article/details/49743.sHtML
- http://m.mobile.cvsifc.cn/Article/details/7000360.sHtML
- http://m.mobile.cvsifc.cn/Article/details/50729.sHtML
- http://m.mobile.cvsifc.cn/Article/details/02443.sHtML
- http://m.mobile.cvsifc.cn/Article/details/2808475.sHtML
- http://m.mobile.cvsifc.cn/Article/details/0465.sHtML
- http://m.mobile.cvsifc.cn/Article/details/6460554.sHtML
- http://m.mobile.cvsifc.cn/Article/details/901287.sHtML
- http://m.mobile.cvsifc.cn/Article/details/52423.sHtML
- http://m.mobile.cvsifc.cn/Article/details/3171.sHtML
- http://m.mobile.cvsifc.cn/Article/details/1422.sHtML
- http://m.mobile.cvsifc.cn/Article/details/1644795.sHtML
- http://m.mobile.cvsifc.cn/Article/details/784723.sHtML
- http://m.mobile.cvsifc.cn/Article/details/7015962.sHtML
- http://m.mobile.cvsifc.cn/Article/details/48681.sHtML
- http://m.mobile.cvsifc.cn/Article/details/0219150.sHtML
- http://m.mobile.cvsifc.cn/Article/details/82236.sHtML
- http://m.mobile.cvsifc.cn/Article/details/4082652.sHtML
- http://m.mobile.cvsifc.cn/Article/details/268909.sHtML
- http://m.mobile.cvsifc.cn/Article/details/1775.sHtML
- http://m.mobile.cvsifc.cn/Article/details/6666788.sHtML
- http://m.mobile.cvsifc.cn/Article/details/1798974.sHtML
- http://m.mobile.cvsifc.cn/Article/details/10118.sHtML
- http://m.mobile.cvsifc.cn/Article/details/059044.sHtML
- http://m.mobile.cvsifc.cn/Article/details/97843.sHtML
- http://m.mobile.cvsifc.cn/Article/details/36081.sHtML
- http://m.mobile.cvsifc.cn/Article/details/04501.sHtML
- http://m.mobile.cvsifc.cn/Article/details/97357.sHtML
- http://m.mobile.cvsifc.cn/Article/details/322037.sHtML
- http://m.mobile.cvsifc.cn/Article/details/8766190.sHtML
- http://m.mobile.cvsifc.cn/Article/details/40384.sHtML
- http://m.mobile.cvsifc.cn/Article/details/51534.sHtML
- http://m.mobile.cvsifc.cn/Article/details/80535.sHtML
- http://m.mobile.cvsifc.cn/Article/details/6489186.sHtML
- http://m.mobile.cvsifc.cn/Article/details/92077.sHtML
- http://m.mobile.cvsifc.cn/Article/details/2223.sHtML
- http://m.mobile.cvsifc.cn/Article/details/4764039.sHtML
- http://m.mobile.cvsifc.cn/Article/details/3005.sHtML
- http://m.mobile.cvsifc.cn/Article/details/1675.sHtML
- http://m.mobile.cvsifc.cn/Article/details/9106818.sHtML
- http://m.mobile.cvsifc.cn/Article/details/0063.sHtML
- http://m.mobile.cvsifc.cn/Article/details/72559.sHtML
- http://m.mobile.cvsifc.cn/Article/details/3710.sHtML
- http://m.mobile.cvsifc.cn/Article/details/859527.sHtML
- http://m.mobile.cvsifc.cn/Article/details/2114.sHtML
- http://m.mobile.cvsifc.cn/Article/details/8723662.sHtML
- http://m.mobile.cvsifc.cn/Article/details/6189.sHtML
- http://m.mobile.cvsifc.cn/Article/details/3439.sHtML
- http://m.mobile.cvsifc.cn/Article/details/2439.sHtML
- http://m.mobile.cvsifc.cn/Article/details/201976.sHtML
- http://m.mobile.cvsifc.cn/Article/details/8474.sHtML
- http://m.mobile.cvsifc.cn/Article/details/468455.sHtML
- http://m.mobile.cvsifc.cn/Article/details/3916583.sHtML
- http://m.mobile.cvsifc.cn/Article/details/8195521.sHtML
- http://m.mobile.cvsifc.cn/Article/details/8745936.sHtML
- http://m.mobile.cvsifc.cn/Article/details/6584.sHtML
- http://m.mobile.cvsifc.cn/Article/details/804281.sHtML
- http://m.mobile.cvsifc.cn/Article/details/6586850.sHtML
- http://m.mobile.cvsifc.cn/Article/details/127825.sHtML
- http://m.mobile.cvsifc.cn/Article/details/883440.sHtML
- http://m.mobile.cvsifc.cn/Article/details/4060.sHtML
- http://m.mobile.cvsifc.cn/Article/details/6112326.sHtML
- http://m.mobile.cvsifc.cn/Article/details/5656.sHtML
- http://m.mobile.cvsifc.cn/Article/details/01787.sHtML
- http://m.mobile.cvsifc.cn/Article/details/266683.sHtML
- http://m.mobile.cvsifc.cn/Article/details/9277077.sHtML
- http://m.mobile.cvsifc.cn/Article/details/1915815.sHtML
- http://m.mobile.cvsifc.cn/Article/details/108193.sHtML
- http://m.mobile.cvsifc.cn/Article/details/03663.sHtML
- http://m.mobile.cvsifc.cn/Article/details/1452.sHtML
- http://m.mobile.cvsifc.cn/Article/details/678184.sHtML
- http://m.mobile.cvsifc.cn/Article/details/235959.sHtML
- http://m.mobile.cvsifc.cn/Article/details/4933140.sHtML
- http://m.mobile.cvsifc.cn/Article/details/9281085.sHtML
- http://m.mobile.cvsifc.cn/Article/details/7064559.sHtML
- http://m.mobile.cvsifc.cn/Article/details/3706366.sHtML
- http://m.mobile.cvsifc.cn/Article/details/0257275.sHtML
- http://m.mobile.cvsifc.cn/Article/details/346837.sHtML
- http://m.mobile.cvsifc.cn/Article/details/9869.sHtML
- http://m.mobile.cvsifc.cn/Article/details/3905.sHtML
- http://m.mobile.cvsifc.cn/Article/details/30764.sHtML
- http://m.mobile.cvsifc.cn/Article/details/7814183.sHtML
- http://m.mobile.cvsifc.cn/Article/details/8235.sHtML
- http://m.mobile.cvsifc.cn/Article/details/6978.sHtML
- http://m.mobile.cvsifc.cn/Article/details/06185.sHtML
- http://m.mobile.cvsifc.cn/Article/details/52323.sHtML
- http://m.mobile.cvsifc.cn/Article/details/1473593.sHtML
- http://m.mobile.cvsifc.cn/Article/details/992524.sHtML
- http://m.mobile.cvsifc.cn/Article/details/01825.sHtML
- http://m.mobile.cvsifc.cn/Article/details/3783.sHtML
- http://m.mobile.cvsifc.cn/Article/details/5592882.sHtML
- http://m.mobile.cvsifc.cn/Article/details/61730.sHtML
- http://m.mobile.cvsifc.cn/Article/details/73863.sHtML
- http://m.mobile.cvsifc.cn/Article/details/87928.sHtML
- http://m.mobile.cvsifc.cn/Article/details/19916.sHtML
- http://m.mobile.cvsifc.cn/Article/details/30883.sHtML
- http://m.mobile.cvsifc.cn/Article/details/65571.sHtML
- http://m.mobile.cvsifc.cn/Article/details/7085.sHtML
- http://m.mobile.cvsifc.cn/Article/details/29510.sHtML
- http://m.mobile.cvsifc.cn/Article/details/1713.sHtML
- http://m.mobile.cvsifc.cn/Article/details/026277.sHtML

## 项目结构

```
webindex-starter/
├── build/                               # 构建脚本目录
│   ├── compile.js                       # 主编译流程，负责读取数据并生成页面
│   ├── resources.js                     # 资源清单解析与校验逻辑
│   └── templates.js                     # HTML 模板渲染引擎封装
├── data/
│   ├── resources.json                   # 核心资源数据文件，包含所有外链及元数据
│   ├── categories.json                  # 分类树定义，配置层级结构与显示顺序
│   └── settings.json                    # 站点标题、描述、主题色等全局配置
├── src/
│   ├── assets/                          # 静态资源原始文件
│   │   ├── css/                         # 主题样式源文件（SCSS）
│   │   ├── js/                          # 前端交互脚本（ES6 模块）
│   │   └── images/                      # Logo、图标等图片资源
│   ├── layouts/                         # 页面布局组件
│   │   ├── default.html                 # 默认页面骨架
│   │   └── embed.html                   # 嵌入模式布局（无导航栏）
│   └── partials/                        # 可复用模板片段
│       ├── header.html                  # 站点头部与导航菜单
│       ├── footer.html                  # 底部版权与链接
│       └── resource-card.html           # 资源卡片视图模板
├── dist/                                # 构建输出目录（部署时使用）
│   ├── index.html                       # 首页生成文件
│   ├── category/                        # 分类页面子目录
│   └── assets/                          # 编译后的 CSS 与 JS 文件
├── tests/                               # 单元测试与集成测试
│   ├── resource.test.js                 # 资源解析函数测试
│   └── build.test.js                    # 构建流程端到端测试
├── docs/                                # 项目文档
│   ├── getting-started.md
│   ├── configuration.md
│   ├── deployment.md
│   └── development.md
├── .github/                             # GitHub 社区配置
│   ├── workflows/                       # CI 工作流定义
│   │   └── build.yml                    # 每次推送执行构建与链接检测
│   └── ISSUE_TEMPLATE/                  # 问题反馈模板
├── package.json                         # npm 依赖与脚本定义
├── package-lock.json                    # 依赖版本锁定文件
├── .eslintrc.js                         # JavaScript 代码风格检查配置
├── .prettierrc                          # 代码格式化配置
└── README.md                            # 项目说明文档（本文件）
```

## 贡献指南

WebIndex 欢迎社区贡献，包括但不限于新增资源收录、分类结构调整、前端界面优化以及文档完善。请遵循以下步骤提交贡献。

第一步，Fork 本项目仓库至个人账户，然后克隆到本地开发环境。建议在 dev 分支上进行所有修改，保持 main 分支与上游同步。

第二步，修改资源清单或代码后，务必运行本地构建与测试命令，确保无语法错误与构建失败。执行 `npm run test` 运行单元测试，执行 `npm run build` 验证完整构建流程。

第三步，提交变更时请遵循语义化提交规范，提交信息格式为 `<类型>: <简短描述>`，类型包括 feat、fix、docs、style、refactor、test、chore 等。提交前请确保代码已通过 ESLint 检查。

第四步，向原仓库的 main 分支发起 Pull Request，并在描述中清晰说明变更目的、影响范围以及测试情况。若新增资源链接，请附带来源说明与分类建议。

第五步，等待项目维护者进行代码审查。审查通过后，Pull Request 将被合并。若审查过程中有修改意见，请在原分支上继续提交并推送，Pull Request 会自动更新。

## 常见问题

问：WebIndex 是否支持自定义域名和 HTTPS？

答：WebIndex 作为静态站点，完全支持自定义域名与 HTTPS。部署时只需将域名 DNS 解析指向托管服务器的 IP 地址，并在服务器或 CDN 层面配置 SSL 证书即可。项目本身不参与 TLS 终止，所有 HTTPS 相关配置由前端 Web 服务器负责。

问：资源链接失效时，WebIndex 如何处理？

答：项目内置了链接状态检测机制。用户可通过命令行运行 `npm run check` 触发对所有收录链接的批量 HEAD 请求检测，检测结果会写入 `data/status.json` 文件。前端页面渲染时读取该状态文件，对失效链接显示特殊标记。检测频率可由用户自行决定，建议每周执行一次。

问：能否将 WebIndex 与现有静态站点生成器（如 VuePress、Hexo）集成？

答：可以。WebIndex 的构建产物为纯静态文件，可以放置在任何静态站点的 `public` 或 `static` 目录下，作为子路径提供服务。同时，WebIndex 也提供了 JSON 数据导出接口，开发者可编写脚本将资源数据转换为其他站点生成器所需的格式，实现数据互通。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:14
