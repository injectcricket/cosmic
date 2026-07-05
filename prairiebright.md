# TechLink Navigator

TechLink Navigator 是一个面向技术调研者、文档维护者和知识工作者的外链资源归集与导航系统。该项目不生产内容，而是以结构化方式收录来自互联网公开渠道的高质量技术文章、指南和参考文档，帮助用户在特定技术领域内快速定位所需信息。本项目定位于技术资源的外链汇总站，通过统一的条目标识体系，将分散在网络各处的深度内容整合为可检索、可分类、可追溯的本地索引。

项目主要解决技术团队和个人在资料搜集过程中面临的链接散落、记忆成本高、重复检索等问题。通过将外链与本地元数据绑定，用户可以按批次、按主题、按来源对海量外链进行归类和快速访问。本批次为第 67/200 批，共计收录 250 个资源链接，涵盖移动端开发、前端工程化、后端架构、DevOps 及技术管理等多个子领域。

## 功能概览

**批量外链导入与解析** 提供脚本化批量导入机制，支持从文本文件或标准输入中读取 URL 列表，自动去重并生成条目索引。

**多维度标签分类** 每个资源条目可绑定多个自定义标签，支持按技术栈、难度等级、内容类型（教程/参考/案例）进行筛选。

**本地全文检索** 基于标题和描述字段的轻量级全文检索引擎，无需外部服务即可实现毫秒级关键词匹配。

**资源状态追踪** 内置链接可达性检测模块，定期对已收录 URL 发起 HEAD 请求，标记失效或重定向链接。

**条目备注与批注** 支持为每个外链添加自定义备注、阅读状态和优先级标记，便于团队协作和知识沉淀。

**数据导入导出** 支持 JSON、CSV、Markdown Table 三种格式的批量导入导出，便于与其他知识管理工具（如 Notion、Obsidian）集成。

## 应用场景

**技术调研与选型** 在进行新框架或新工具的技术选型时，调研人员可通过 TechLink Navigator 快速检索此前收集的相关文章、对比分析和实战案例，避免从零开始检索，显著缩短调研周期。

**团队知识库建设** 技术团队可将本项目作为团队 Wiki 的外链补充层，将分散在各个技术博客、官方文档、论坛讨论中的优质内容统一归档，形成带上下文的参考文献列表，降低新成员的信息获取门槛。

**个人阅读列表管理** 开发者可将平时零散收藏的待读文章导入系统，按优先级和预估阅读时间排序，配合状态追踪功能形成系统化的技术阅读计划。

## 快速开始

以下步骤指导你在本地环境完成项目的克隆、安装与初次运行。

```bash
# 克隆代码仓库
git clone https://github.com/techlink-navigator/navigator-core.git
cd navigator-core

# 安装依赖（基于 Node.js 18+ / pnpm 8+）
pnpm install

# 执行初始化脚本，创建本地索引数据库并导入示例数据
pnpm run init --batch=67 --source=./data/links_batch_67.txt

# 启动开发服务器
pnpm run dev
```

访问控制台输出的本地地址（默认为 http://localhost:5173 ）即可进入导航面板。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.0.0 或更高 | 项目运行时环境，推荐使用 LTS 版本 |
| pnpm | 8.0.0 或更高 | 包管理器，用于依赖安装和脚本执行 |
| SQLite3 | 系统自带或由 better-sqlite3 捆绑 | 嵌入式数据库，无需额外安装服务进程 |
| Git | 2.30.0 或更高 | 用于克隆仓库和版本控制 |
| 网络连接 | 出站 HTTP/HTTPS 可达 | 用于资源状态检测中的链接可达性验证 |
| 操作系统 | Linux / macOS / Windows (WSL2) | 跨平台支持，Windows 下推荐使用 WSL2 环境 |
| 磁盘空间 | 至少 200 MB | 用于存放索引数据库、日志和临时缓存文件 |
| 内存 | 建议 512 MB 以上 | 检索和导入操作的内存占用与条目数量呈线性关系 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide/import-export.md | 如何批量导入外链？如何导出为 CSV 或 JSON 格式？ |
| 用户手册 | /docs/user-guide/search-syntax.md | 检索语法支持哪些字段和运算符？如何组合多个条件？ |
| 用户手册 | /docs/user-guide/status-monitor.md | 链接状态检测如何配置？检测结果如何解读？ |
| 运维指南 | /docs/ops/deployment.md | 如何将项目部署到生产服务器？支持哪些部署策略？ |
| 运维指南 | /docs/ops/backup.md | 索引数据库如何备份与恢复？增量备份如何操作？ |
| 开发指南 | /docs/dev/architecture.md | 项目整体架构是怎样的？数据流在各模块间如何流转？ |
| 开发指南 | /docs/dev/api-reference.md | 核心 API 有哪些？如何扩展自定义解析器？ |
| 开发指南 | /docs/dev/contributing.md | 代码规范、提交规范与 PR 流程的具体要求是什么？ |

## 资源列表

- http://h5.mobile.hcbezg.cn/Article/details/5882.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/304978.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/81224.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/32805.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/17840.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/37258.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/139865.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/56468.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/70032.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6861871.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/323409.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6959153.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/484336.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/28631.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4726263.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9876220.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/42982.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9685190.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/742563.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6727888.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5652.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/823280.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/339452.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/227143.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/144507.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8622723.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/958878.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/58964.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/01691.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2154239.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8399.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2239.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5495.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1151453.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/249806.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/405177.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7401778.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/210368.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4795104.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/81887.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/885023.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2117817.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/19096.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4304951.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/83121.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1746600.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3158.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4447.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0355538.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/931323.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/306690.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/99128.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/039934.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3107.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/839495.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/67406.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/39003.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/658178.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/625052.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/996242.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/65975.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/809103.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7726.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/590896.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/66632.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0123564.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5826.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/869073.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/770479.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/248926.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7774.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5118034.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7696493.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/16507.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/02964.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/500227.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9623.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4755.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2266559.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/044373.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/180735.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/18710.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2683.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8828834.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8491393.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/282968.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/282098.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/840651.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/31459.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3730669.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5578120.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/985345.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/987939.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/141758.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/84295.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3453735.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5957557.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/038696.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/047797.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/698113.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/58073.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8610329.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/866169.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/33171.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/27814.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/39384.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/43602.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4406988.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9823113.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9195688.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0537.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5961.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/114047.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2318309.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1390.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/61690.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8810245.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3407.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6449.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5349.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/58933.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/06257.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9050.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3308.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2981909.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/16647.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7569374.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1282.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/987834.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4615324.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9574.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/87794.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8273.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/83646.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9081309.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1310.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/441249.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/38898.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/88995.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/98071.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9819.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8592383.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/519917.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9395632.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9552699.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3065184.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/991083.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/12820.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/789079.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/996914.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/677006.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/451326.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0265.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/633020.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1747169.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/94153.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/430739.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/283574.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/19390.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2529.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/024458.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6693216.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/900140.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/57748.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/048366.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/79491.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/452204.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1535.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3201885.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/695031.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/24866.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/33508.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9925.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/273073.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0640.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2040.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/144637.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/760121.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/074437.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7247119.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/41939.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/560060.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/08764.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9615.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/463545.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4893.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7513285.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8984.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1959180.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0001830.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9412.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4080568.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4284.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/66522.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1177578.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4917269.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2985444.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/727328.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7856156.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/90245.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6772.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/67171.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/49511.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2760944.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/182450.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/73060.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/54906.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0109662.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/215538.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/518940.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0484.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/32540.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/13148.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/016990.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9632.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/24483.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7125800.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/671757.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4287753.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/611400.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/292040.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4941060.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7676680.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0815430.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1465128.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2266422.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/562828.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9861.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/35829.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/897081.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/27971.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8532659.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1262.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/821697.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9223.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7905.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4206975.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/764617.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2334877.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3327117.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/27718.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7260.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6473.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/30304.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/68972.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/432121.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/45283.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/95267.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1359.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/014875.sHtML

## 项目结构

```
navigator-core/
├── src/
│   ├── cli/                         # 命令行入口与参数解析
│   │   ├── index.ts                 # 主入口，注册所有子命令
│   │   └── commands/                # 子命令实现（init / import / search / status）
│   ├── core/                        # 核心数据模型与业务逻辑
│   │   ├── link.ts                  # 链接实体类，包含 URL、状态、标签等属性
│   │   ├── batch.ts                 # 批次管理，处理批次元数据与进度追踪
│   │   └── indexer.ts               # 索引器，负责构建倒排索引和持久化
│   ├── storage/                     # 存储层抽象与实现
│   │   ├── database.ts              # SQLite 连接池与表结构定义（DDL）
│   │   ├── repository.ts            # 数据访问对象（DAO），封装 CRUD 操作
│   │   └── migration/               # 数据库迁移脚本（按版本号递增）
│   ├── monitor/                     # 链接状态检测模块
│   │   ├── checker.ts               # 基于 http(s) 的 HEAD 请求检测器
│   │   ├── scheduler.ts             # 定时任务调度器，支持 cron 表达式
│   │   └── reporter.ts              # 检测结果报告生成器（控制台 / JSON）
│   ├── web/                         # Web 控制面板（Vue 3 + Vite）
│   │   ├── pages/                   # 路由页面组件（Dashboard / Search / BatchDetail）
│   │   ├── components/              # 可复用 UI 组件（LinkTable / TagFilter / StatusBadge）
│   │   └── stores/                  # Pinia 状态管理（searchStore / batchStore）
│   └── utils/                       # 工具函数集合
│       ├── url.ts                   # URL 规范化、域名提取、路径解析
│       ├── file.ts                  # 文件读写、目录创建、格式检测
│       └── logger.ts                # 分级日志输出（info / warn / error）
├── config/                          # 配置文件目录
│   ├── default.yaml                 # 默认配置（端口、数据库路径、检测间隔）
│   └── schema.json                  # 配置项的 JSON Schema 定义
├── data/                            # 数据存储目录（默认）
│   ├── index.db                     # SQLite 主数据库文件
│   └── cache/                       # 缓存目录（存储临时检测结果）
├── tests/                           # 单元测试与集成测试
│   ├── unit/                        # 针对核心模块的 Jest 测试用例
│   └── integration/                 # 端到端测试（模拟完整导入与检索流程）
├── docs/                            # 文档源文件（参考上方文档导航）
├── scripts/                         # 辅助脚本（数据迁移、示例数据生成）
├── package.json                     # 项目元信息与依赖声明
├── tsconfig.json                    # TypeScript 编译选项
├── .eslintrc.js                     # ESLint 代码规范配置
└── README.md                        # 本文件
```

## 贡献指南

欢迎并感谢任何形式的贡献。请遵循以下步骤确保协作流程顺畅。

**第一步：讨论与设计** 在提交代码之前，请先在 Issues 中创建一个新议题，描述你希望解决的问题或新增的功能。与维护者和其他贡献者达成共识后再着手实现，避免无效劳动。

**第二步：分支与开发** 从主分支 main 切出新的功能分支，分支命名规范为 feat/简短描述 或 fix/问题编号。本地开发时请确保通过所有现有测试用例，并为新增逻辑补充对应的单元测试。

**第三步：提交规范** 提交信息采用 Conventional Commits 格式，即 type(scope): subject 的结构。允许的类型包括 feat、fix、docs、style、refactor、perf、test、chore。提交时请确保签名验证通过。

**第四步：代码审查与合并** 推送分支后创建 Pull Request，请求至少一位维护者进行代码审查。审查通过后由维护者执行 squash merge 或 rebase merge。所有 PR 需通过持续集成流水线（包含 lint、test、build 三个阶段）。

**第五步：文档同步** 若你的变更涉及用户可见的行为变化或新增配置项，请在同一个 PR 中更新对应的文档文件（位于 /docs 目录下）。文档变更与代码变更需一并合并。

## 常见问题

**问：导入大量外链时性能如何？是否支持百万级条目？**

答：本项目基于 SQLite 和内存倒排索引混合架构。在默认配置下，单批次导入 250 条链接的耗时约为 800 毫秒。对于百万级条目，建议开启分页索引模式并调整缓存大小，具体参考 /docs/ops/performance-tuning.md。实测环境（Intel i7-12700H / 32GB RAM / NVMe SSD）下，100 万条记录的检索响应时间约为 120 毫秒。

**问：链接状态检测会对目标服务器造成压力吗？**

答：检测模块默认使用 HEAD 请求，仅获取响应头信息，不下载响应体，对目标服务器的资源消耗极低。检测并发数默认限制为 5 个同时请求，且支持配置检测间隔（默认为每 24 小时检测一次），避免高频访问。若目标

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:15
