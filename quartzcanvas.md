# LinkVault Core

LinkVault Core 是一个面向技术内容聚合场景的轻量级外链资源管理与导航系统。项目定位为技术团队、独立开发者与内容运营者提供一套可私有化部署的结构化外链目录方案，用于对批量分散的技术文章、文档、工具站点与行业动态进行统一编号、分类索引与快速检索。目标用户包括技术博客作者、开源项目维护者、企业知识库管理员以及需要定期整理大量参考链接的研究人员。LinkVault Core 不依赖外部数据库，通过静态文件与元数据标记实现资源的可维护性与可移植性，同时保留完整的原始链接记录，确保数据在多次迁移与版本迭代中不丢失原始出处。

## 功能概览

批量链接导入与原始地址保留：系统提供纯文本或 CSV 格式的链接导入接口，在入库过程中强制保留用户提供的原始 URL 字符串，不进行任何自动补全、协议转换或大小写修正，确保每条外链的精确可溯源性。

多层级标签分类体系：允许用户为每一条链接自定义一级分类、二级主题与场景标签，支持一对多标签关联，便于按技术栈、业务模块或内容类型进行多维筛选。

资源状态标记与审核工作流：内置未审核、已发布、已归档、待更新四种状态，支持团队协作场景下的链接上架审批与过期内容标记，状态变更记录写入本地日志文件。

全文检索与字段过滤：基于 SQLite FTS5 扩展提供对链接标题、摘要、分类标签与备注字段的全文检索能力，同时支持按域名、文件类型、时间范围等字段进行组合过滤。

响应式目录视图与嵌入组件：提供移动端适配的列表视图与卡片视图两种展示模式，同时对外暴露可嵌入任意网页的 JavaScript 小组件，用于在第三方站点中展示当前活跃链接列表。

数据快照导出与备份：支持将当前全量链接数据导出为 JSON、CSV 与静态 HTML 三种格式，导出文件可按日期命名归档，便于定期备份与跨平台迁移。

## 应用场景

技术团队内部知识库维护：开发团队可将日常调研中积累的技术文章、API 参考文档、故障排查案例链接统一录入 LinkVault Core，按项目或技术领域分类，在团队内部共享访问，避免重复搜索与链接散落。

开源项目 README 外链管理：开源项目维护者可将项目依赖的规范标准、上下游工具、社区讨论帖等参考链接集中托管于 LinkVault Core，生成稳定的索引页面，减少 README 文件中的冗长外链列表，提升文档可读性。

技术内容运营与周刊编辑：内容运营人员可利用 LinkVault Core 的标签与状态管理功能，快速筛选出本周推荐的技术资源，一键导出为 HTML 列表，用于技术周刊或邮件通讯的内容编排。

个人开发者的学习路径整理：独立学习者可将学习过程中遇到的优质教程、视频课程、代码示例链接按学习阶段分类存储，配合备注字段记录学习心得与完成进度，形成个人知识索引。

## 快速开始

以下命令可在 Ubuntu 22.04 或 macOS 12 及以上环境中完成 LinkVault Core 的克隆、安装与启动。

```bash
git clone https://github.com/linkvault/core.git linkvault-core
cd linkvault-core
cp .env.example .env
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python3 manage.py migrate
python3 manage.py load_initial_links --source ./data/seed.csv
python3 manage.py runserver 0.0.0.0:8000
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10 及以上 | 核心运行环境，需支持 asyncio 与 dataclasses |
| SQLite | 3.38 及以上 | 内置数据库，需启用 FTS5 扩展以支持全文检索 |
| pip | 22.0 及以上 | Python 包管理器，用于安装 requirements.txt 中列出的依赖 |
| Git | 2.30 及以上 | 用于克隆仓库及后续版本更新拉取 |
| 系统时区数据 | tzdata 2022a 及以上 | 确保链接时间戳记录与时区转换准确，Linux 系统需安装 tzdata 包 |
| 可用磁盘空间 | 至少 500 MB | 用于存放 SQLite 数据库文件、日志及导出快照，建议 SSD 存储 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user/quick-start.md | 如何快速导入第一批链接并进行分类与状态设置 |
| 用户手册 | /docs/user/advanced-filter.md | 如何组合使用标签、状态、时间范围进行复杂筛选 |
| 开发者指南 | /docs/dev/api-endpoints.md | 后端提供了哪些 RESTful 接口用于增删改查链接记录 |
| 开发者指南 | /docs/dev/embed-widget.md | 如何将链接列表组件嵌入到外部静态页面或 React 项目中 |
| 运维参考 | /docs/ops/backup-strategy.md | 数据快照自动备份的周期配置与恢复操作步骤 |
| 运维参考 | /docs/ops/migration.md | 在不同服务器之间迁移完整数据（含文件附件）的标准流程 |

## 资源列表

- http://h5.mobile.cvsifc.cn/Article/details/6354.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2316.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/064552.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/06874.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3247914.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7536833.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/65301.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8205576.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/751448.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8042.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5840.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/980754.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/038455.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/195627.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2498.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1680.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/48294.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/933649.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/105489.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/060231.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/94177.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8525689.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/24338.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3141.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7751845.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/301616.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/01227.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5479.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/358310.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/10743.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7533656.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5308258.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/95098.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0765755.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/70958.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/27479.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7969.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/732875.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/486619.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9732.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9630.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2712119.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/731691.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8402.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7733970.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/92300.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/609252.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/142768.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/329421.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1479.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/86700.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/79364.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8874393.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5652.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/561746.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7043466.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5804238.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3679348.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5495.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/32023.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/36575.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/805951.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3522617.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2610989.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/232602.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/882609.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5196.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/32508.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/581100.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7874.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/876945.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/304364.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/79800.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/78157.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/253433.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/10307.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6834596.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/43962.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6422833.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/10196.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8490.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/693073.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8679622.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2631.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3701764.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/88975.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1467908.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/69052.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0327340.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5482.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9194069.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/898189.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3364.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/03649.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2935658.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/065118.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/042228.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7583.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4117.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/179493.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9181912.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/247841.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/629581.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/51463.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/70321.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9404406.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8708.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1136571.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7832969.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/58487.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/053519.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/627817.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/48449.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/57526.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0890.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/11327.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6462881.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/23963.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/577023.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/154605.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3157011.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/383623.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/073349.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/822654.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9248.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5368373.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/665517.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9836859.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/22457.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/22311.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/530049.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0381124.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8850.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0864673.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/475058.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1279.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/65778.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/171906.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5197.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/93363.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/465462.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/627210.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/25663.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/457907.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/709170.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3861.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/617920.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2147280.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7055.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/093610.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3811.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/783518.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/85406.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6825.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8232.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9229952.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/01233.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/44421.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0085.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3045.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1778.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6678285.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1871931.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/38798.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6982.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9449.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4383366.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6939925.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0308797.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2711.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5677161.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0006.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/522948.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5006847.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/32690.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0220543.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/07028.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/14403.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1980560.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/14748.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/68913.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/581777.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/609278.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2162.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9276853.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/158213.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/50224.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2317.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7455.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9890.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/860112.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2064.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6414.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2706.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/19241.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/720891.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/068090.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6853.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7413.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/94915.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/78484.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/881063.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/29596.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/82993.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/590674.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7542610.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2108183.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/96310.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/530660.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6377.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1921.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/62610.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/86465.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9121440.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/656286.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/743638.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/14111.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1853.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3444.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6401676.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/054256.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/03381.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6123281.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/489738.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/91449.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/94705.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/198445.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9232377.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/16553.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8663802.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6689178.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/52211.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2085.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/511432.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4823.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4715290.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4106720.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/38343.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3041942.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9924399.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/32698.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6127921.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/699964.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/617084.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/354798.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/15534.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0846.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/542123.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1084738.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/024032.sHtML

## 项目结构

```
linkvault-core/
├── .env.example                                 # 环境变量配置模板，包含数据库路径与端口设置
├── .gitignore                                   # Git 忽略规则，排除 venv、__pycache__ 与本地快照目录
├── README.md                                    # 项目说明文档，即当前文件
├── requirements.txt                             # Python 依赖清单，包含 Django、django-fts5 与 python-dotenv
├── manage.py                                    # Django 项目管理入口，用于启动服务与执行命令
├── data/                                        # 数据存储目录
│   ├── seed.csv                                 # 初始链接种子文件，用于首次导入示例数据
│   ├── snapshots/                               # 定期导出的 JSON/CSV 快照归档目录
│   └── logs/                                    # 操作日志与状态变更记录文件存放位置
├── src/                                         # 核心源码目录
│   ├── __init__.py                              # 包初始化文件
│   ├── settings/                                # 多环境配置子目录
│   │   ├── base.py                              # 基础配置，包含数据库、时区与中间件定义
│   │   ├── development.py                       # 开发环境配置，启用调试与本地缓存
│   │   └── production.py                        # 生产环境配置，关闭调试并配置静态文件服务
│   ├── urls.py                                  # 全局路由分发定义
│   └── wsgi.py                                  # WSGI 应用入口，用于部署至 Gunicorn 或 uWSGI
├── apps/                                        # 功能应用模块
│   ├── links/                                   # 链接管理核心应用
│   │   ├── models.py                            # Link 数据模型定义，含 URL 字段、状态、标签与时间戳
│   │   ├── admin.py                             # Django Admin 后台定制，支持批量导入与状态筛选
│   │   ├── views/                               # 视图函数目录
│   │   │   ├── api.py                           # RESTful 接口，提供增删改查与筛选操作
│   │   │   └── pages.py                         # 页面渲染视图，处理列表页、详情页与嵌入组件
│   │   ├── services/                            # 业务逻辑服务层
│   │   │   ├── importer.py                      # CSV/JSON 导入解析器，负责原始 URL 字段的强制保留
│   │   │   ├── exporter.py                      # 数据导出器，支持多格式输出与快照命名
│   │   │   └── fts.py                          # 全文检索服务，封装 SQLite FTS5 查询接口
│   │   └── migrations/                          # 数据库迁移文件目录，记录模型变更历史
│   ├── tags/                                    # 标签管理应用，提供标签创建、合并与层级关系维护
│   │   ├── models.py                            # Tag 与 TagGroup 模型定义
│   │   └── views.py                             # 标签 API 与标签云渲染视图
│   └── widgets/                                 # 嵌入组件应用
│       ├── templates/                           # 可嵌入的 HTML 模板片段
│       └── static/                              # 组件静态资源（CSS/JS），用于外部站点引用
├── static/                                      # 全局静态文件，包含基础样式与前端交互脚本
├── templates/                                   # 全局模板目录，包含基础布局与错误页面
└── tests/                                       # 单元测试与集成测试用例目录
    ├── test_models.py                           # 数据模型字段约束与保存逻辑测试
    ├── test_importer.py                         # 导入服务对异常 URL 格式的处理测试
    └── test_api.py                              # API 接口返回数据结构与状态码测试
```

## 贡献指南

问题跟踪与讨论：在提交任何代码变更之前，请先在 Issues 列表中搜索是否已有相关讨论。若无重复议题，请新建一个 Issue 并详细描述你发现的问题或希望新增的功能，等待核心维护者的初步反馈。

分支模型与提交规范：所有代码变更应基于 develop 分支创建新的特性分支，分支命名格式为 feature/简短描述 或 fix/问题编号。提交信息需遵循 Conventional Commits 规范，即使用 feat:、fix:、docs:、refactor: 等前缀，并在正文中说明变更动机与影响范围。

本地开发环境准备：Fork 主仓库后，在本地执行上述快速开始步骤完成环境搭建。运行 python3 manage.py test 确保全部现有测试用例通过。新增功能需同步编写对应单元测试，测试覆盖率不得低于 80%。

Pull Request 提交流程：完成开发与自测后，将特性分支推送至你的 Fork 仓库，然后向主仓库的 develop 分支发起 Pull Request。PR 标题应简洁概括变更内容，正文需关联对应的 Issue 编号，并列出人工测试步骤或截图以便审核。

文档与变更日志更新：若你的贡献涉及用户可见的功能变化或配置变更，需同步更新 /docs 下的相关手册，并在 CHANGELOG.md 文件的 Unreleased 章节下记录本次变更条目。文档更新应随 PR 一同提交。

## 常见问题

问题：导入 CSV 文件时，系统是否会对我提供的 URL 进行自动补全或规范化处理？

回答：不会。LinkVault Core 的导入器在设计上强制保留用户输入的原始 URL 字符串，不会添加 http:// 或 https:// 前缀，不会移除或补全 www 子域名，也不会转换协议或调整大小写。这一

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:14
