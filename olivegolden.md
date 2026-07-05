# LinkVault Core

LinkVault Core 是一个面向技术团队与个人开发者的外链资源聚合与规范化管理平台。该项目并非简单的书签收集工具，而是一个具备结构化索引、元数据提取、状态监控与批量导入导出能力的轻量级外链中台。其核心定位在于帮助用户从杂乱无章的收藏夹或零散文档中解脱出来，建立一套可维护、可追溯、可共享的 external resources 管理体系。

目标用户包括技术文档撰写者、开源项目维护人、技术调研人员以及需要频繁查阅大量外部参考资料的一线研发工程师。LinkVault Core 通过提供统一的 URL 入库规范、自动化的资源可用性检测以及灵活的标签分类机制，有效解决外链失效、分类混乱、检索困难等常见痛点，将分散的网页链接转化为可复用的结构化知识资产。

## 功能概览

**批量链接导入** 支持从纯文本文件、CSV 或直接粘贴的 URL 列表中批量解析并入库，自动去重与格式清洗。

**元数据自动补全** 对入库链接尝试自动抓取页面标题、描述与关键词信息，降低人工标注成本。

**健康状态监控** 定时检测已存储链接的可访问性，标记返回 4xx、5xx 状态码或连接超时的失效条目。

**多级标签体系** 允许为每条链接分配一级分类与二级子标签，支持基于标签组合的快速筛选与视图保存。

**高级检索语法** 提供基于 URL 域名、路径关键词、标题全文、标签集合的组合检索能力，支持正则表达式模式匹配。

**数据导入导出** 支持将整个资源库导出为 JSON、YAML 或 Markdown 格式的结构化清单，便于备份或迁移至其他系统。

**浏览器扩展辅助** 提供可选的浏览器侧边栏插件，支持一键将当前访问页面提交至 LinkVault Core 实例。

**访问统计看板** 展示每日链接点击次数、热门域名 Top 10、失效链接趋势等基础度量指标。

## 应用场景

技术文档维护与审核 技术团队在撰写或更新项目文档时，经常需要引用大量外部规范、API 参考或社区讨论帖。LinkVault Core 可作为文档团队的统一引用源，确保所有外链经过初步可用性验证，并在链接失效时主动预警，避免文档中出现大量死链影响阅读体验。

开源项目资源索引 开源项目维护者可将项目依赖的第三方库主页、教程文章、视频讲解、相关工具等资源集中录入系统，生成公开的资源清单供社区贡献者查阅。新加入的开发者可以通过该系统快速了解项目生态全貌。

技术调研信息归档 在进行技术选型或竞品分析时，调研人员通常需要浏览数十乃至上百个相关网站。LinkVault Core 可以帮助调研者即时记录这些临时性发现，通过标签和备注将零散信息组织为结构化的调研素材库，方便后续撰写正式报告时快速回溯原始出处。

个人知识库外链枢纽 对于坚持记录技术笔记或数字花园的知识工作者，LinkVault Core 可以作为笔记软件（如 Obsidian、Logseq）的外部补充，专门负责管理所有外链资源。笔记中只需保留内部 ID 引用，避免笔记文件被冗长 URL 干扰，同时享受集中式的链接健康管理。

## 快速开始

以下步骤帮助您在本地环境中快速启动 LinkVault Core 实例。

```bash
# 克隆代码仓库
git clone https://github.com/linkvault/core.git linkvault-core
cd linkvault-core

# 安装项目依赖（使用 pnpm 或 npm）
pnpm install

# 根据 .env.example 创建本地环境配置文件
cp .env.example .env.local

# 执行数据库迁移与初始数据填充
pnpm run db:migrate
pnpm run db:seed

# 启动开发服务器
pnpm run dev
```

服务启动后，默认在 http://localhost:5173 提供 Web 管理界面。API 服务监听 http://localhost:3000，可通过 OpenAPI 文档（/api-docs）查看所有接口定义。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或 20.x LTS | 推荐使用最新的 Active LTS 版本，需支持 ES2022 特性 |
| pnpm | 8.x 或 9.x | 项目使用 pnpm workspace 管理多包结构，不推荐使用 npm 或 yarn |
| PostgreSQL | 14.x 或 15.x | 主数据库，需启用 pg_trgm 扩展以支持高效模糊检索 |
| Redis | 7.x | 用于缓存会话与定时任务队列，可选但建议生产环境部署 |
| SQLite | 3.x（内置） | 仅用于本地开发与单元测试环境，生产环境请使用 PostgreSQL |
| Docker（可选） | 20.x 或以上 | 若使用 docker-compose 方式一键启动全部依赖服务，需提前安装 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户入门 | /docs/guide/getting-started.md | 如何安装部署、首次启动、导入第一批链接？ |
| 配置参考 | /docs/reference/configuration.md | 所有环境变量、配置项的含义与默认值分别是什么？ |
| API 手册 | /docs/api/endpoints.md | 每个 REST 接口的请求参数、响应结构与鉴权方式如何？ |
| 架构设计 | /docs/internals/architecture.md | 系统模块划分、数据流走向、扩展点设计说明 |
| 贡献规范 | /docs/contributing/coding-standards.md | 代码风格、提交信息格式、PR 流程要求 |
| 故障排查 | /docs/troubleshooting/common-issues.md | 遇到启动失败、链接检测异常、性能问题时如何排查 |

## 资源列表

- http://m.mobile.cmcvrr.cn/Article/details/29962.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2488349.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9705.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9612.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/59858.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/251775.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/14311.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6521.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6006741.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1267.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/56826.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/223250.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/5558.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/473229.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0158.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6974114.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1230106.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2167540.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/915298.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4456.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3903425.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9854.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4696250.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/48513.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8166485.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/67642.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/609987.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/62731.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0435.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9312.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8338.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/96270.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0234186.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6134.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/882559.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6907235.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/534232.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/15088.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6939758.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/28556.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/16057.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7716644.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/472967.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/45906.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4384.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/30682.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/222110.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7853889.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9561.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9120.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1416327.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0669080.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/5034532.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0078.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/01580.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1814168.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/42818.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/04504.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/411658.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/68269.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/706273.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/471290.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/629037.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/244867.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/59445.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4773.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/33374.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/730481.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/12280.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/755501.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6446685.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/746502.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/23360.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3517278.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/231925.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8176480.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4434.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/28160.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/19820.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/5730.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3312955.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2968.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/42064.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2457208.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/754859.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/669891.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8828.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7122.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/26664.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1892276.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8162471.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3768352.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2106.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4141.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/47438.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1339.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/62853.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/172492.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3226.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1211049.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/35267.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/5808.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2204.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4684626.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/70806.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3553684.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4061.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4345093.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7108883.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2188871.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0930.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3360.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8469.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/34102.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9650104.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/683095.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/396425.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2314.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8672780.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2296214.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0666984.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6215393.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7573.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4483677.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/284878.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/244894.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9315.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/97607.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/232641.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/77898.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0240.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/864729.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/975134.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4496467.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9215939.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3806537.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2529.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1385.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9220740.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1143848.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6739826.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/5846.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0161755.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/322967.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/5966564.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/5475.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2007.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/69814.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1916.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8237844.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2017.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/39369.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1641580.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3086197.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2025.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/665447.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2562865.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/02553.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4864.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/636864.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2306421.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0591186.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/245721.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4178.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8386.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4871.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/342359.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8848.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1286687.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7154.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/303733.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/582307.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/5233642.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3399598.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/85824.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/43081.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/666520.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/33800.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/5992239.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9027.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/130351.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/32420.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1246173.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7377393.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2023250.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7056.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4862527.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/53157.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/224403.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8607.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1780781.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4865.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/276788.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/91518.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/54292.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0009.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8416178.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/124165.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/30152.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1221399.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6761.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/39058.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/65435.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/16417.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/44620.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/913614.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/887421.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/057433.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3747727.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6562379.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0943066.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2574580.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0897.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3617466.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8223.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8624420.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9029.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/393462.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/65701.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/154324.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/07914.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/22322.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/5968473.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/57438.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/702464.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6531.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/78889.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/16545.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7768852.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9093.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/480212.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/35553.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/69965.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/86507.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/5229.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7303.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0912537.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/99673.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3621890.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/50012.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2005500.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/288594.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/84504.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/5316.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2778.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/04343.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7772.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9299.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0891.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2735.sHtML

## 项目结构

```
linkvault-core/
├── apps/
│   ├── web/                           # 主 Web 应用 (React + Vite)
│   │   ├── src/
│   │   │   ├── pages/                 # 路由页面组件 (Dashboard, Links, Tags, Settings)
│   │   │   ├── components/            # 可复用 UI 组件 (DataTable, FilterBar, StatusBadge)
│   │   │   ├── hooks/                 # 自定义 React Hooks (useLinks, useHealthCheck)
│   │   │   └── stores/                # Zustand 状态管理 (linkStore, filterStore)
│   │   └── index.html                 # 入口模板
│   └── api/                           # RESTful API 服务 (Fastify + Prisma)
│       ├── src/
│       │   ├── routes/                # 路由定义 (links, tags, health, import)
│       │   ├── controllers/           # 请求处理与响应组装逻辑
│       │   ├── services/              # 核心业务服务 (LinkService, CheckService)
│       │   ├── repositories/          # 数据访问层 (Prisma 封装)
│       │   └── workers/               # 后台任务队列 (BullMQ 消费者)
│       └── prisma/
│           └── schema.prisma          # 数据库模型定义 (Link, Tag, CheckLog)
├── packages/
│   ├── shared/                        # 跨应用共享类型与工具函数
│   │   └── src/
│   │       ├── types/                 # TypeScript 类型定义 (Link, Pagination)
│   │       └── validators/            # Zod 校验模式 (urlSchema, tagSchema)
│   └── crawler/                       # 独立元数据抓取模块 (Puppeteer + Cheerio)
│       └── src/
│           ├── fetcher/               # 页面请求与重定向处理
│           └── parser/                # 标题、描述、关键词提取器
├── docker-compose.yml                 # 本地开发完整服务编排 (PostgreSQL + Redis + Adminer)
├── .env.example                       # 环境变量模板 (含数据库连接、JWT 密钥、检测间隔)
├── package.json                       # 根 workspace 依赖与脚本定义
├── tsconfig.base.json                 # 全局 TypeScript 编译配置
├── biome.json                         # 代码格式化与 Lint 规则 (Biome)
└── README.md                          # 项目说明文档 (本文件)
```

## 贡献指南

提交 Issue 或功能请求 请先查阅 GitHub Issues 列表，确认当前没有重复或正在处理的相似议题。新建 Issue 时，请使用提供的模板清晰描述问题现象、复现步骤、预期行为与实际表现，并附上相关环境信息（Node 版本、数据库版本、浏览器版本）。

分支开发流程 所有代码变更均通过 Pull Request 提交。请从 main 分支创建新的 feature/xxx 或 fix/xxx 分支进行开发，保持分支命名语义化。提交 PR 前，请确保本地已运行 pnpm run lint 与 pnpm run test 全部通过，并补写必要的单元测试或集成测试。

代码风格规范 项目使用 Biome 作为统一的格式化与 Lint 工具，提交前会自动执行 pre-commit 钩子。请确保编辑器已配置 Biome 插件，避免因格式问题导致 CI 失败。命名上遵循 camelCase（变量、函数）、PascalCase（类、组件、类型）、UPPER_SNAKE_CASE（常量）的常规约定。

文档同步要求 任何影响用户使用方式或配置接口的变更，必须同步更新 /docs 目录下的对应文档文件，并在 PR 描述中标注文档已同步。新增环境变量必须在 .env.example 和配置参考文档中同时添加说明。

测试覆盖要求 核心业务逻辑（链接增删改查、健康检测调度、标签关联）需提供充分的单元测试覆盖，关键 API 端点需有集成测试。测试文件与被测源码放在同一目录下，以 .spec.ts 或 .test.ts 命名。

## 常见问题

启动时提示数据库连接失败如何排查？

首先检查 .env.local 文件中的 DATABASE_URL 是否正确，确保 PostgreSQL 服务已启动且端口可访问。若使用 docker-compose 方式启动依赖服务，请执行 docker-compose up -d 确保容器正常运行。另外请确认数据库已执行过迁移：pnpm run db:migrate。如果仍然失败，可尝试将日志级别调整为 debug 查看详细连接错误信息。

健康检测任务未按预期定时执行，可能原因是什么？

健康检测依赖于 BullMQ 队列与 Redis 连接，请先确认 Redis 服务可用且 REDIS_URL 配置无误。检测任务采用固定的 cron 表达式（默认每小时整点执行），若需调整可在环境变量中修改 CHECK_CRON_PATTERN。同时检查是否有多个 worker 实例竞争消费任务导致重复执行，或队列因异常任务被阻塞。可在 Admin 控制台查看队列监控面板确认任务状态。

导入大量链接时页面响应缓慢，如何优化？

单次导入建议不超过 5000 条，否则建议分批次提交或使用异步导入接口（POST /api/import/async），该接口会将任务放入后台队列处理，并通过任务 ID 轮询进度。浏览器端可启用虚拟滚动列表来渲染大结果集，避免 DOM 节点过多导致卡顿。数据库方面确保在 url 字段上已建立唯一索引和 btree 索引，可显著提升去重和检索性能。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:14
