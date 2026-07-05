# LinkMaster 技术资源索引平台

LinkMaster 是一个面向开发者、技术研究者与内容策展人的轻量级技术资源外链汇总与导航系统。该项目旨在解决技术信息碎片化、优质内容分散于各独立站点难以集中检索的问题，通过结构化的文章索引与分类导航，帮助用户快速定位特定主题下的深度技术文章、案例分析及解决方案文档。LinkMaster 不存储任何实际内容，仅提供元数据索引与外部链接跳转，适用于搭建个人技术书架、团队知识库导航或公开技术资源聚合站。

## 功能概览

**多维度文章索引**：基于文章ID、分类标签与发布时间建立索引，支持按唯一标识符精确检索特定技术文档。

**分类导航体系**：内置前端工程、后端架构、运维监控、算法设计、移动开发等主流技术分类树，便于按领域浏览资源。

**快速检索接口**：提供基于文章ID的模糊匹配搜索，支持通过URL参数直接跳转至目标外链，降低用户查找成本。

**批量资源导入**：支持通过结构化数据文件（JSON/CSV）批量导入外部文章链接，便于从其他系统迁移或同步资源。

**访问统计追踪**：记录每个外链的点击次数与最后访问时间，帮助识别热门内容与沉寂资源。

**响应式管理面板**：提供基于Web的管理界面，支持资源的增删改查、分类调整及链接可用性检测。

**开放数据导出**：支持将索引数据导出为Markdown表格、JSON或OPML格式，便于与其他知识管理工具集成。

**自定义标签系统**：允许用户为文章添加自定义标签，实现超越分类树的灵活内容组织。

## 应用场景

**个人技术知识库构建**：开发者可将日常阅读的优质技术博客、官方文档、解决方案帖子通过LinkMaster统一索引，形成私人外链知识库，避免书签混乱和链接失效问题。

**团队技术文档导航**：技术团队可使用LinkMaster搭建内部技术文档导航页，将分散于Wiki、GitHub、Confluence等平台的核心文档集中索引，减少新成员寻找资料的时间成本。

**技术社区资源聚合**：开源社区或技术论坛可基于LinkMaster建立社区推荐资源列表，将有价值的讨论帖、教程文章按主题分类，降低内容发现门槛。

**技术调研信息整理**：在进行技术选型或竞品分析时，可将相关文章、官网链接、评测报告集中收录，通过标签和分类辅助对比决策。

## 快速开始

以下指令适用于Linux/macOS环境，Windows用户建议使用WSL或Git Bash。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/linkmaster.git
cd linkmaster

# 安装Node.js依赖（后端）
npm install --production

# 安装前端管理面板依赖
cd admin && npm install && cd ..

# 初始化SQLite数据库
node scripts/init-db.js

# 启动开发服务器（默认监听3000端口）
npm run dev
```

访问 http://localhost:3000 即可浏览前端导航页面，管理面板位于 http://localhost:3000/admin 。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 16.x 或 18.x LTS | 运行时环境，推荐使用nvm管理版本 |
| npm | 8.x 或 9.x | 包管理器，随Node.js一同安装 |
| SQLite3 | 3.36.0 及以上 | 嵌入式数据库，无需额外安装服务 |
| Git | 2.30 及以上 | 用于克隆仓库及版本管理 |
| 现代浏览器 | Chrome 90+ / Firefox 88+ / Safari 14+ | 管理面板前端界面需要ES2020支持 |
| 磁盘空间 | 至少 50MB | 用于存放代码、数据库及日志文件 |
| 内存 | 最低 256MB，推荐 512MB | 生产环境建议升级至1GB以上 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide/overview.md | 如何浏览、搜索和访问索引资源；如何注册账户并管理个人收藏 |
| 管理员指南 | docs/admin/management.md | 如何添加、编辑或删除文章索引；如何管理分类标签和检测链接可用性 |
| 开发者文档 | docs/developer/api-reference.md | 如何调用RESTful API进行资源查询、批量导入或导出数据 |
| 部署运维 | docs/operations/deployment.md | 如何在生产环境（Nginx + PM2）中部署LinkMaster，以及如何进行日志监控和备份 |

## 资源列表

- http://www.mobile.hcbezg.cn/Article/details/5882.sHtML
- http://www.mobile.hcbezg.cn/Article/details/304978.sHtML
- http://www.mobile.hcbezg.cn/Article/details/81224.sHtML
- http://www.mobile.hcbezg.cn/Article/details/32805.sHtML
- http://www.mobile.hcbezg.cn/Article/details/17840.sHtML
- http://www.mobile.hcbezg.cn/Article/details/37258.sHtML
- http://www.mobile.hcbezg.cn/Article/details/139865.sHtML
- http://www.mobile.hcbezg.cn/Article/details/56468.sHtML
- http://www.mobile.hcbezg.cn/Article/details/70032.sHtML
- http://www.mobile.hcbezg.cn/Article/details/6861871.sHtML
- http://www.mobile.hcbezg.cn/Article/details/323409.sHtML
- http://www.mobile.hcbezg.cn/Article/details/6959153.sHtML
- http://www.mobile.hcbezg.cn/Article/details/484336.sHtML
- http://www.mobile.hcbezg.cn/Article/details/28631.sHtML
- http://www.mobile.hcbezg.cn/Article/details/4726263.sHtML
- http://www.mobile.hcbezg.cn/Article/details/9876220.sHtML
- http://www.mobile.hcbezg.cn/Article/details/42982.sHtML
- http://www.mobile.hcbezg.cn/Article/details/9685190.sHtML
- http://www.mobile.hcbezg.cn/Article/details/742563.sHtML
- http://www.mobile.hcbezg.cn/Article/details/6727888.sHtML
- http://www.mobile.hcbezg.cn/Article/details/5652.sHtML
- http://www.mobile.hcbezg.cn/Article/details/823280.sHtML
- http://www.mobile.hcbezg.cn/Article/details/339452.sHtML
- http://www.mobile.hcbezg.cn/Article/details/227143.sHtML
- http://www.mobile.hcbezg.cn/Article/details/144507.sHtML
- http://www.mobile.hcbezg.cn/Article/details/8622723.sHtML
- http://www.mobile.hcbezg.cn/Article/details/958878.sHtML
- http://www.mobile.hcbezg.cn/Article/details/58964.sHtML
- http://www.mobile.hcbezg.cn/Article/details/01691.sHtML
- http://www.mobile.hcbezg.cn/Article/details/2154239.sHtML
- http://www.mobile.hcbezg.cn/Article/details/8399.sHtML
- http://www.mobile.hcbezg.cn/Article/details/2239.sHtML
- http://www.mobile.hcbezg.cn/Article/details/5495.sHtML
- http://www.mobile.hcbezg.cn/Article/details/1151453.sHtML
- http://www.mobile.hcbezg.cn/Article/details/249806.sHtML
- http://www.mobile.hcbezg.cn/Article/details/405177.sHtML
- http://www.mobile.hcbezg.cn/Article/details/7401778.sHtML
- http://www.mobile.hcbezg.cn/Article/details/210368.sHtML
- http://www.mobile.hcbezg.cn/Article/details/4795104.sHtML
- http://www.mobile.hcbezg.cn/Article/details/81887.sHtML
- http://www.mobile.hcbezg.cn/Article/details/885023.sHtML
- http://www.mobile.hcbezg.cn/Article/details/2117817.sHtML
- http://www.mobile.hcbezg.cn/Article/details/19096.sHtML
- http://www.mobile.hcbezg.cn/Article/details/4304951.sHtML
- http://www.mobile.hcbezg.cn/Article/details/83121.sHtML
- http://www.mobile.hcbezg.cn/Article/details/1746600.sHtML
- http://www.mobile.hcbezg.cn/Article/details/3158.sHtML
- http://www.mobile.hcbezg.cn/Article/details/4447.sHtML
- http://www.mobile.hcbezg.cn/Article/details/0355538.sHtML
- http://www.mobile.hcbezg.cn/Article/details/931323.sHtML
- http://www.mobile.hcbezg.cn/Article/details/306690.sHtML
- http://www.mobile.hcbezg.cn/Article/details/99128.sHtML
- http://www.mobile.hcbezg.cn/Article/details/039934.sHtML
- http://www.mobile.hcbezg.cn/Article/details/3107.sHtML
- http://www.mobile.hcbezg.cn/Article/details/839495.sHtML
- http://www.mobile.hcbezg.cn/Article/details/67406.sHtML
- http://www.mobile.hcbezg.cn/Article/details/39003.sHtML
- http://www.mobile.hcbezg.cn/Article/details/658178.sHtML
- http://www.mobile.hcbezg.cn/Article/details/625052.sHtML
- http://www.mobile.hcbezg.cn/Article/details/996242.sHtML
- http://www.mobile.hcbezg.cn/Article/details/65975.sHtML
- http://www.mobile.hcbezg.cn/Article/details/809103.sHtML
- http://www.mobile.hcbezg.cn/Article/details/7726.sHtML
- http://www.mobile.hcbezg.cn/Article/details/590896.sHtML
- http://www.mobile.hcbezg.cn/Article/details/66632.sHtML
- http://www.mobile.hcbezg.cn/Article/details/0123564.sHtML
- http://www.mobile.hcbezg.cn/Article/details/5826.sHtML
- http://www.mobile.hcbezg.cn/Article/details/869073.sHtML
- http://www.mobile.hcbezg.cn/Article/details/770479.sHtML
- http://www.mobile.hcbezg.cn/Article/details/248926.sHtML
- http://www.mobile.hcbezg.cn/Article/details/7774.sHtML
- http://www.mobile.hcbezg.cn/Article/details/5118034.sHtML
- http://www.mobile.hcbezg.cn/Article/details/7696493.sHtML
- http://www.mobile.hcbezg.cn/Article/details/16507.sHtML
- http://www.mobile.hcbezg.cn/Article/details/02964.sHtML
- http://www.mobile.hcbezg.cn/Article/details/500227.sHtML
- http://www.mobile.hcbezg.cn/Article/details/9623.sHtML
- http://www.mobile.hcbezg.cn/Article/details/4755.sHtML
- http://www.mobile.hcbezg.cn/Article/details/2266559.sHtML
- http://www.mobile.hcbezg.cn/Article/details/044373.sHtML
- http://www.mobile.hcbezg.cn/Article/details/180735.sHtML
- http://www.mobile.hcbezg.cn/Article/details/18710.sHtML
- http://www.mobile.hcbezg.cn/Article/details/2683.sHtML
- http://www.mobile.hcbezg.cn/Article/details/8828834.sHtML
- http://www.mobile.hcbezg.cn/Article/details/8491393.sHtML
- http://www.mobile.hcbezg.cn/Article/details/282968.sHtML
- http://www.mobile.hcbezg.cn/Article/details/282098.sHtML
- http://www.mobile.hcbezg.cn/Article/details/840651.sHtML
- http://www.mobile.hcbezg.cn/Article/details/31459.sHtML
- http://www.mobile.hcbezg.cn/Article/details/3730669.sHtML
- http://www.mobile.hcbezg.cn/Article/details/5578120.sHtML
- http://www.mobile.hcbezg.cn/Article/details/985345.sHtML
- http://www.mobile.hcbezg.cn/Article/details/987939.sHtML
- http://www.mobile.hcbezg.cn/Article/details/141758.sHtML
- http://www.mobile.hcbezg.cn/Article/details/84295.sHtML
- http://www.mobile.hcbezg.cn/Article/details/3453735.sHtML
- http://www.mobile.hcbezg.cn/Article/details/5957557.sHtML
- http://www.mobile.hcbezg.cn/Article/details/038696.sHtML
- http://www.mobile.hcbezg.cn/Article/details/047797.sHtML
- http://www.mobile.hcbezg.cn/Article/details/698113.sHtML
- http://www.mobile.hcbezg.cn/Article/details/58073.sHtML
- http://www.mobile.hcbezg.cn/Article/details/8610329.sHtML
- http://www.mobile.hcbezg.cn/Article/details/866169.sHtML
- http://www.mobile.hcbezg.cn/Article/details/33171.sHtML
- http://www.mobile.hcbezg.cn/Article/details/27814.sHtML
- http://www.mobile.hcbezg.cn/Article/details/39384.sHtML
- http://www.mobile.hcbezg.cn/Article/details/43602.sHtML
- http://www.mobile.hcbezg.cn/Article/details/4406988.sHtML
- http://www.mobile.hcbezg.cn/Article/details/9823113.sHtML
- http://www.mobile.hcbezg.cn/Article/details/9195688.sHtML
- http://www.mobile.hcbezg.cn/Article/details/0537.sHtML
- http://www.mobile.hcbezg.cn/Article/details/5961.sHtML
- http://www.mobile.hcbezg.cn/Article/details/114047.sHtML
- http://www.mobile.hcbezg.cn/Article/details/2318309.sHtML
- http://www.mobile.hcbezg.cn/Article/details/1390.sHtML
- http://www.mobile.hcbezg.cn/Article/details/61690.sHtML
- http://www.mobile.hcbezg.cn/Article/details/8810245.sHtML
- http://www.mobile.hcbezg.cn/Article/details/3407.sHtML
- http://www.mobile.hcbezg.cn/Article/details/6449.sHtML
- http://www.mobile.hcbezg.cn/Article/details/5349.sHtML
- http://www.mobile.hcbezg.cn/Article/details/58933.sHtML
- http://www.mobile.hcbezg.cn/Article/details/06257.sHtML
- http://www.mobile.hcbezg.cn/Article/details/9050.sHtML
- http://www.mobile.hcbezg.cn/Article/details/3308.sHtML
- http://www.mobile.hcbezg.cn/Article/details/2981909.sHtML
- http://www.mobile.hcbezg.cn/Article/details/16647.sHtML
- http://www.mobile.hcbezg.cn/Article/details/7569374.sHtML
- http://www.mobile.hcbezg.cn/Article/details/1282.sHtML
- http://www.mobile.hcbezg.cn/Article/details/987834.sHtML
- http://www.mobile.hcbezg.cn/Article/details/4615324.sHtML
- http://www.mobile.hcbezg.cn/Article/details/9574.sHtML
- http://www.mobile.hcbezg.cn/Article/details/87794.sHtML
- http://www.mobile.hcbezg.cn/Article/details/8273.sHtML
- http://www.mobile.hcbezg.cn/Article/details/83646.sHtML
- http://www.mobile.hcbezg.cn/Article/details/9081309.sHtML
- http://www.mobile.hcbezg.cn/Article/details/1310.sHtML
- http://www.mobile.hcbezg.cn/Article/details/441249.sHtML
- http://www.mobile.hcbezg.cn/Article/details/38898.sHtML
- http://www.mobile.hcbezg.cn/Article/details/88995.sHtML
- http://www.mobile.hcbezg.cn/Article/details/98071.sHtML
- http://www.mobile.hcbezg.cn/Article/details/9819.sHtML
- http://www.mobile.hcbezg.cn/Article/details/8592383.sHtML
- http://www.mobile.hcbezg.cn/Article/details/519917.sHtML
- http://www.mobile.hcbezg.cn/Article/details/9395632.sHtML
- http://www.mobile.hcbezg.cn/Article/details/9552699.sHtML
- http://www.mobile.hcbezg.cn/Article/details/3065184.sHtML
- http://www.mobile.hcbezg.cn/Article/details/991083.sHtML
- http://www.mobile.hcbezg.cn/Article/details/12820.sHtML
- http://www.mobile.hcbezg.cn/Article/details/789079.sHtML
- http://www.mobile.hcbezg.cn/Article/details/996914.sHtML
- http://www.mobile.hcbezg.cn/Article/details/677006.sHtML
- http://www.mobile.hcbezg.cn/Article/details/451326.sHtML
- http://www.mobile.hcbezg.cn/Article/details/0265.sHtML
- http://www.mobile.hcbezg.cn/Article/details/633020.sHtML
- http://www.mobile.hcbezg.cn/Article/details/1747169.sHtML
- http://www.mobile.hcbezg.cn/Article/details/94153.sHtML
- http://www.mobile.hcbezg.cn/Article/details/430739.sHtML
- http://www.mobile.hcbezg.cn/Article/details/283574.sHtML
- http://www.mobile.hcbezg.cn/Article/details/19390.sHtML
- http://www.mobile.hcbezg.cn/Article/details/2529.sHtML
- http://www.mobile.hcbezg.cn/Article/details/024458.sHtML
- http://www.mobile.hcbezg.cn/Article/details/6693216.sHtML
- http://www.mobile.hcbezg.cn/Article/details/900140.sHtML
- http://www.mobile.hcbezg.cn/Article/details/57748.sHtML
- http://www.mobile.hcbezg.cn/Article/details/048366.sHtML
- http://www.mobile.hcbezg.cn/Article/details/79491.sHtML
- http://www.mobile.hcbezg.cn/Article/details/452204.sHtML
- http://www.mobile.hcbezg.cn/Article/details/1535.sHtML
- http://www.mobile.hcbezg.cn/Article/details/3201885.sHtML
- http://www.mobile.hcbezg.cn/Article/details/695031.sHtML
- http://www.mobile.hcbezg.cn/Article/details/24866.sHtML
- http://www.mobile.hcbezg.cn/Article/details/33508.sHtML
- http://www.mobile.hcbezg.cn/Article/details/9925.sHtML
- http://www.mobile.hcbezg.cn/Article/details/273073.sHtML
- http://www.mobile.hcbezg.cn/Article/details/0640.sHtML
- http://www.mobile.hcbezg.cn/Article/details/2040.sHtML
- http://www.mobile.hcbezg.cn/Article/details/144637.sHtML
- http://www.mobile.hcbezg.cn/Article/details/760121.sHtML
- http://www.mobile.hcbezg.cn/Article/details/074437.sHtML
- http://www.mobile.hcbezg.cn/Article/details/7247119.sHtML
- http://www.mobile.hcbezg.cn/Article/details/41939.sHtML
- http://www.mobile.hcbezg.cn/Article/details/560060.sHtML
- http://www.mobile.hcbezg.cn/Article/details/08764.sHtML
- http://www.mobile.hcbezg.cn/Article/details/9615.sHtML
- http://www.mobile.hcbezg.cn/Article/details/463545.sHtML
- http://www.mobile.hcbezg.cn/Article/details/4893.sHtML
- http://www.mobile.hcbezg.cn/Article/details/7513285.sHtML
- http://www.mobile.hcbezg.cn/Article/details/8984.sHtML
- http://www.mobile.hcbezg.cn/Article/details/1959180.sHtML
- http://www.mobile.hcbezg.cn/Article/details/0001830.sHtML
- http://www.mobile.hcbezg.cn/Article/details/9412.sHtML
- http://www.mobile.hcbezg.cn/Article/details/4080568.sHtML
- http://www.mobile.hcbezg.cn/Article/details/4284.sHtML
- http://www.mobile.hcbezg.cn/Article/details/66522.sHtML
- http://www.mobile.hcbezg.cn/Article/details/1177578.sHtML
- http://www.mobile.hcbezg.cn/Article/details/4917269.sHtML
- http://www.mobile.hcbezg.cn/Article/details/2985444.sHtML
- http://www.mobile.hcbezg.cn/Article/details/727328.sHtML
- http://www.mobile.hcbezg.cn/Article/details/7856156.sHtML
- http://www.mobile.hcbezg.cn/Article/details/90245.sHtML
- http://www.mobile.hcbezg.cn/Article/details/6772.sHtML
- http://www.mobile.hcbezg.cn/Article/details/67171.sHtML
- http://www.mobile.hcbezg.cn/Article/details/49511.sHtML
- http://www.mobile.hcbezg.cn/Article/details/2760944.sHtML
- http://www.mobile.hcbezg.cn/Article/details/182450.sHtML
- http://www.mobile.hcbezg.cn/Article/details/73060.sHtML
- http://www.mobile.hcbezg.cn/Article/details/54906.sHtML
- http://www.mobile.hcbezg.cn/Article/details/0109662.sHtML
- http://www.mobile.hcbezg.cn/Article/details/215538.sHtML
- http://www.mobile.hcbezg.cn/Article/details/518940.sHtML
- http://www.mobile.hcbezg.cn/Article/details/0484.sHtML
- http://www.mobile.hcbezg.cn/Article/details/32540.sHtML
- http://www.mobile.hcbezg.cn/Article/details/13148.sHtML
- http://www.mobile.hcbezg.cn/Article/details/016990.sHtML
- http://www.mobile.hcbezg.cn/Article/details/9632.sHtML
- http://www.mobile.hcbezg.cn/Article/details/24483.sHtML
- http://www.mobile.hcbezg.cn/Article/details/7125800.sHtML
- http://www.mobile.hcbezg.cn/Article/details/671757.sHtML
- http://www.mobile.hcbezg.cn/Article/details/4287753.sHtML
- http://www.mobile.hcbezg.cn/Article/details/611400.sHtML
- http://www.mobile.hcbezg.cn/Article/details/292040.sHtML
- http://www.mobile.hcbezg.cn/Article/details/4941060.sHtML
- http://www.mobile.hcbezg.cn/Article/details/7676680.sHtML
- http://www.mobile.hcbezg.cn/Article/details/0815430.sHtML
- http://www.mobile.hcbezg.cn/Article/details/1465128.sHtML
- http://www.mobile.hcbezg.cn/Article/details/2266422.sHtML
- http://www.mobile.hcbezg.cn/Article/details/562828.sHtML
- http://www.mobile.hcbezg.cn/Article/details/9861.sHtML
- http://www.mobile.hcbezg.cn/Article/details/35829.sHtML
- http://www.mobile.hcbezg.cn/Article/details/897081.sHtML
- http://www.mobile.hcbezg.cn/Article/details/27971.sHtML
- http://www.mobile.hcbezg.cn/Article/details/8532659.sHtML
- http://www.mobile.hcbezg.cn/Article/details/1262.sHtML
- http://www.mobile.hcbezg.cn/Article/details/821697.sHtML
- http://www.mobile.hcbezg.cn/Article/details/9223.sHtML
- http://www.mobile.hcbezg.cn/Article/details/7905.sHtML
- http://www.mobile.hcbezg.cn/Article/details/4206975.sHtML
- http://www.mobile.hcbezg.cn/Article/details/764617.sHtML
- http://www.mobile.hcbezg.cn/Article/details/2334877.sHtML
- http://www.mobile.hcbezg.cn/Article/details/3327117.sHtML
- http://www.mobile.hcbezg.cn/Article/details/27718.sHtML
- http://www.mobile.hcbezg.cn/Article/details/7260.sHtML
- http://www.mobile.hcbezg.cn/Article/details/6473.sHtML
- http://www.mobile.hcbezg.cn/Article/details/30304.sHtML
- http://www.mobile.hcbezg.cn/Article/details/68972.sHtML
- http://www.mobile.hcbezg.cn/Article/details/432121.sHtML
- http://www.mobile.hcbezg.cn/Article/details/45283.sHtML
- http://www.mobile.hcbezg.cn/Article/details/95267.sHtML
- http://www.mobile.hcbezg.cn/Article/details/1359.sHtML
- http://www.mobile.hcbezg.cn/Article/details/014875.sHtML

## 项目结构

```
linkmaster/
├── app/                                 # 核心应用代码
│   ├── controllers/                     # 路由控制器，处理HTTP请求与响应逻辑
│   │   ├── articleController.js         # 文章资源的CRUD操作控制器
│   │   ├── categoryController.js        # 分类树的管理控制器
│   │   └── statsController.js           # 访问统计与点击追踪控制器
│   ├── models/                          # 数据模型层，定义SQLite表结构与ORM映射
│   │   ├── ArticleModel.js              # 文章索引模型（字段：id, title, url, category, tags等）
│   │   ├── CategoryModel.js             # 分类模型（支持无限级父子嵌套）
│   │   └── ClickLogModel.js             # 点击日志模型（记录访问时间、IP、User-Agent）
│   ├── services/                        # 业务逻辑服务层
│   │   ├── crawlerService.js            # 外链可用性检测与元数据抓取服务
│   │   ├── importService.js             # 批量导入（JSON/CSV）解析与校验服务
│   │   └── exportService.js             # 数据导出为Markdown/JSON/OPML的格式化服务
│   └── utils/                           # 通用工具函数集
│       ├── database.js                  # SQLite连接池管理与查询构建器
│       ├── validator.js                 # URL格式校验、XSS过滤与输入清洗
│       └── logger.js                    # 基于winston的日志记录器（按日切割）
├── admin/                               # 管理面板前端项目（React + Ant Design）
│   ├── src/
│   │   ├── pages/                       # 管理界面页面组件（资源列表、分类管理、导入导出）
│   │   ├── api/                         # 与管理后端通信的API请求封装
│   │   └── components/                  # 可复用UI组件（数据表格、标签选择器、链接预览）
│   └── package.json                     # 前端依赖声明（react, axios, antd等）
├── public/                              # 前端导航页面静态资源（面向普通访客）
│   ├── index.html                       # 导航首页入口HTML
│   ├── css/                             # 响应式CSS样式（基于Flexbox与Grid布局）
│   └── js/                              # 前端导航页交互脚本（搜索、分类筛选、点击跳转）
├── scripts/                             # 运维与工具脚本
│   ├── init-db.js                       # 初始化数据库表结构与默认分类数据
│   ├── seed-data.js                     # 填充示例文章索引数据用于开发测试
│   └── health-check.js                  # 定时检测所有外链可用性并标记失效链接
├── docs/                                # 项目文档（用户手册、管理员指南、API文档、部署说明）
│   ├── user-guide/
│   ├── admin/
│   ├── developer/
│   └── operations/
├── tests/                               # 单元测试与集成测试（基于Jest）
│   ├── unit/                            # 模型与工具函数单元测试
│   └── integration/                     # API路由与数据库交互集成测试
├── .env.example                         # 环境变量配置模板（端口、数据库路径、日志级别）
├── package.json                         # 后端项目依赖与脚本命令（dev, start, test）
├── server.js                            # 应用启动入口（Express服务器初始化）
└── README.md                            # 项目说明文档（当前文件）
```

## 贡献指南

1.  **分支管理规范**：从 `main` 分支切出功能分支，命名格式为 `feature/功能简述` 或 `fix/问题简述`，禁止直接在 `main` 分支上提交代码。

2.  **代码风格要求**：JavaScript代码遵循ESLint配置（基于Airbnb规范），提交前请运行 `npm run lint` 进行自动修复，确保无语法警告和格式错误。

3.  **提交信息格式**：使用Conventional Commits规范，提交信息头部必须包含类型（feat/fix/docs/style/refactor/test/chore）和简短描述，例如 `feat: add batch import endpoint for JSON files`。

4.  **测试覆盖要求**：新增功能或修复缺陷时，需同步编写或更新对应的单元测试和集成测试用例，确保测试通过率不低于95%。

5.  **文档同步更新**：涉及用户可见的功能变动或API变更时，必须同步更新 `docs/` 目录下对应的中文文档，并在PR描述中指明文档变更位置。

## 常见问题

**Q1：LinkMaster 是否存储外部文章的实际内容或静态资源？**
LinkMaster 仅存储文章的元数据（标题、源URL、分类、标签等）和索引信息，不缓存或代理任何外部站点的实际内容。所有文章详情均通过跳转至原始URL进行访问，因此版权归属原始发布者。

**Q2：如何批量导入自有书签或现有文章列表？**
您可以在管理面板的「导入」功能中上传符合格式要求的JSON或CSV文件。系统支持从Chrome书签导出文件、Pocket导出数据以及通用CSV模板导入。具体格式说明请参考 `docs/admin/management.md` 中的批量导入章节。

**Q3：外链失效或站点无法访问时如何处理？**
系统后台会通过 `scripts/health-check.js` 脚本定时（默认每24小时）检测所有索引外链的HTTP状态码。连续三次检测返回非200状态码的链接将被标记为「失效」，并在管理面板中高亮显示。管理员可手动编辑或删除失效链接，也可触发即时重检。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:15
