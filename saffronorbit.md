# LinkHub - 技术资源导航与文档聚合系统

LinkHub 是一个面向开发者、技术研究人员与内容创作者的轻量级技术资源导航与文档聚合平台。该项目定位于解决海量技术文章、教程、API 文档、开源项目页及行业报告分散于网络各处，难以系统化整理与高效检索的问题。LinkHub 通过结构化的资源收录机制、标签化分类体系与全文元数据提取能力，帮助用户在特定技术领域内快速建立知识索引，降低信息过载带来的决策成本。

LinkHub 不试图替代搜索引擎或 AI 问答系统，而是作为技术信息基础设施的补充层，专注于对已有优质外链进行目录化组织、状态监控与语义描述增强。项目适用于个人知识库建设、团队技术文档库维护、开源项目生态导航页搭建等场景。核心用户包括运维工程师、全栈开发者、技术文档撰写者以及开源社区贡献者。

## 功能概览

**结构化资源收录** 支持按技术领域、难度等级、内容类型（教程、参考手册、案例研究、视频讲稿）对任意 URL 进行多维度标注，内置标签模板与自定义字段。

**自动元数据提取** 对收录链接执行可配置的元数据抓取流程，提取页面标题、发布时间、内容摘要、关键代码片段引用，并生成本地缓存快照。

**链接健康度巡检** 周期性对已收录 URL 发起可用性探测，自动标记失效链接、重定向链过长页面及响应超时资源，提供状态看板与告警通知。

**全文检索与过滤** 基于标题、标签、描述文本、来源域名构建倒排索引，支持布尔查询与模糊匹配，提供按时间、访问热度、内容长度的多级排序。

**批量导入与导出** 支持从 CSV、JSON、OPML 格式批量导入已有书签或订阅列表，同时支持按标签或时间范围导出为 Markdown 表格、HTML 目录页或结构化 JSON 馈送。

**访问统计与热度分析** 记录每个链接的点击次数、最近访问时间与用户来源（本地 / 公网），生成周度与月度热度排行，辅助判断资源价值衰减趋势。

## 应用场景

**技术团队内部文档中心** 开发团队可将日常遇到的第三方依赖库文档、云服务 API 参考、故障排查案例统一收录至 LinkHub，并为每条链接添加负责人标签与适用环境（开发 / 测试 / 生产），新成员入职时可快速浏览团队常用技术栈的外部参考基线。

**开源项目生态导航页** 开源项目维护者可以使用 LinkHub 构建项目周边的插件、工具链、示例代码仓库及视频教程的导航目录，替代传统的 Wiki 外链列表，获得更好的可维护性与链接状态可见性。

**个人技术写作素材库** 技术博主或在线课程讲师可将研究过程中查阅的论文预印本、实验数据仓库、官方规范文档集中收录，在撰写长篇技术报告时通过 LinkHub 的全文检索快速定位之前读过的关键参考来源，避免重复搜索。

**社区技术沙龙资源归档** 技术社区组织者可在活动结束后将讲师幻灯片链接、相关代码仓库、直播回放地址以及延伸阅读材料统一归档至 LinkHub，并按活动日期与主题打标，形成长期可访问的知识资产。

## 快速开始

以下步骤适用于 Linux 与 macOS 环境，Windows 用户建议使用 WSL2 或 Git Bash。

```bash
# 克隆主仓库
git clone https://github.com/linkhub-io/linkhub.git
cd linkhub

# 安装核心依赖（使用 Python 3.10 及以上版本）
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化 SQLite 数据库与缓存目录
python manage.py initdb
python manage.py migrate

# 启动本地开发服务（默认监听 127.0.0.1:8000）
python manage.py runserver
```

启动后访问 http://127.0.0.1:8000 即可进入 LinkHub 仪表板，首次运行将自动创建管理员账户，初始化密码输出于终端日志中。如需部署至生产环境，请参考 `deploy/production.md` 文档配置 uWSGI 与 Nginx。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
| :--- | :--- | :--- |
| Python | 3.10 至 3.12 | 核心运行环境，3.13 暂未完成兼容性测试 |
| SQLite | 3.35 及以上 | 默认内置数据库，用于元数据存储与索引 |
| Redis | 6.2 及以上 | 可选，用于链接健康度巡检的任务队列与缓存加速 |
| BeautifulSoup4 | 4.12 及以上 | HTML 解析与元数据提取核心库 |
| requests | 2.31 及以上 | HTTP 客户端，用于外链资源抓取与探测 |
| lxml | 4.9 及以上 | 高性能 XML/HTML 解析器，BeautifulSoup 后端推荐 |
| uWSGI | 2.0 及以上 | 生产环境部署时的 WSGI 服务器（可选） |
| Node.js | 18 及以上 | 仅用于前端资产构建（Tailwind CSS 与 Alpine.js） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
| :--- | :--- | :--- |
| 用户手册 | `/docs/user/quickstart.md` | 如何添加第一条链接、如何打标签、如何查看健康状态 |
| 用户手册 | `/docs/user/advanced-search.md` | 如何组合多个过滤条件进行精确检索，如何保存常用查询 |
| 运维指南 | `/docs/admin/deployment.md` | 如何配置反向代理、SSL 证书、定时巡检任务与日志轮转 |
| 运维指南 | `/docs/admin/monitoring.md` | 如何解读健康度看板指标，如何设置失效链接的邮件告警 |
| 开发指南 | `/docs/dev/api.md` | 如何通过 REST API 以编程方式增删改查资源，认证方式与限流策略 |
| 开发指南 | `/docs/dev/plugin.md` | 如何编写自定义元数据提取器以适配非标准页面结构 |
| 贡献规范 | `/docs/contrib/coding-standards.md` | 代码风格、提交信息格式、PR 流程与测试覆盖率要求 |

## 资源列表

- http://www.mobile.cmcvrr.cn/Article/details/0211.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4605552.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/620812.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/38790.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/338080.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5507.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8220832.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0087058.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/955369.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/799465.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7119947.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9106114.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2344089.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/12069.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/875536.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/24592.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/547549.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/621591.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/12294.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8598.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0402974.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/681148.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/61052.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/758928.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/97055.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/88785.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6534205.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/146357.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7027841.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6872.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7360366.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2124139.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6033.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7808.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8652.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/795695.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/52598.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6267841.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8446865.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5709967.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/629796.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7767130.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/067957.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8949.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/263890.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/28416.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8244038.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6328591.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0776.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/666163.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7598.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7185279.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8376.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/43297.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1475.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/363704.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0201.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/78852.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/06718.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5612.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4019.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/81043.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/551669.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/317570.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/339916.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/113415.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/39078.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2394883.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4515.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/214304.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2733.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9055.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/39345.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4206037.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/546852.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9605675.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/303745.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/979208.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/79713.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/691858.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/48255.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4964394.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9519.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0677.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/01810.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8834.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/96602.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/658968.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6978.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6629.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1729.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1128.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/73804.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2234597.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/43791.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/061817.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9808.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/70387.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/32111.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/723721.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7394.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/793245.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/62401.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5989501.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6451308.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7668140.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/60105.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7657.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9279.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2402650.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2476.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/46304.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8883.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/353245.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/13044.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0157371.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1386.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9435497.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/74695.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/06905.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/795849.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3878.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8790.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/97427.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1438.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/97687.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/21168.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6334.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6816912.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/629414.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4637488.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/24213.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/93013.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0870.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4969.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/792550.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2817427.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5682.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1565965.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8056016.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/60708.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8219320.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/189075.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4811.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5766431.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2435310.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/29154.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/261329.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/24351.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3188690.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6039.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/13151.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/448782.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/54601.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/123885.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8575.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/188905.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/25096.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0018223.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9448.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/672059.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5480087.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1879.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/400546.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1804.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3431.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/45806.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3242025.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/193276.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9162389.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3024566.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8616407.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5895.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5952818.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5520.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/66775.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/33877.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/15761.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/31176.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4482.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/612468.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0551609.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4239842.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4177971.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1792.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5101.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7003194.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9801.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0610722.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/442156.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/10524.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4025279.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/029551.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/164496.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8975235.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/194536.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/544896.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5769.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0062.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/6842015.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5266100.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8104631.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/86251.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/622498.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/3400.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9129521.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/746519.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4164170.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7566.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9984855.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/569572.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/125881.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/33746.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/71779.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/01393.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1953917.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/78893.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9195.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/04971.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/51316.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/80818.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9379759.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0042415.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/36029.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/95576.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0194.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7744.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/9743.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/618719.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8561876.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/18939.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5870693.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/30401.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8838669.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/022577.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8960.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/15956.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2387.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/216455.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/7899458.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/5043.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/83936.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/19635.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/80677.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/8985.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1601413.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/0655.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/4266.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/1077070.sHtML
- http://www.mobile.cmcvrr.cn/Article/details/2128625.sHtML

## 项目结构

```
linkhub/
├── manage.py                  # 命令行入口，集成开发服务器、数据库迁移与巡检任务
├── requirements.txt           # Python 核心依赖锁定文件
├── pyproject.toml             # 项目元数据与构建配置（PEP 621）
├── .env.example               # 环境变量模板（数据库路径、Redis DSN、密钥种子）
├── deploy/
│   ├── nginx.conf.sample      # 生产环境 Nginx 反向代理配置片段
│   ├── uwsgi.ini              # uWSGI 进程管理与 socket 绑定参数
│   └── systemd/               # systemd 服务单元文件（linkhub.service）
├── src/
│   ├── core/                  # 核心配置与全局依赖容器
│   │   ├── settings.py        # 分层配置（开发 / 测试 / 生产）
│   │   └── database.py        # SQLite 连接池与 ORM 基类
│   ├── models/                # 数据模型定义（资源、标签、访问日志、巡检记录）
│   │   ├── resource.py
│   │   ├── tag.py
│   │   └── health_check.py
│   ├── services/              # 业务逻辑层
│   │   ├── fetcher.py         # 外链抓取与元数据解析策略
│   │   ├── indexer.py         # 倒排索引构建与查询重写
│   │   └── scheduler.py       # 周期巡检任务调度（APScheduler）
│   ├── api/                   # RESTful 接口路由与序列化器
│   │   ├── v1/                # 版本化 API（/api/v1/resources）
│   │   └── middleware.py      # 限流与请求日志中间件
│   ├── web/                   # 服务端渲染的仪表板视图（Flask Blueprint）
│   │   ├── dashboard.py       # 概览统计与最近失效链接卡片
│   │   ├── detail.py          # 单条资源详情页与编辑表单
│   │   └── search.py          # 高级搜索页面与分页组件
│   └── static/                # 前端静态资源（CSS / JS / 图标）
│       ├── css/               # Tailwind 编译输出
│       └── js/                # Alpine.js 交互组件（批量编辑、实时过滤）
├── tests/                     # 单元测试与集成测试（pytest）
│   ├── unit/                  # 模型层与工具函数测试
│   └── integration/           # API 端到端测试与抓取器模拟
├── docs/                      # 完整文档（用户手册、运维指南、API 参考）
│   ├── user/
│   ├── admin/
│   ├── dev/
│   └── contrib/
└── scripts/                   # 运维辅助脚本
    ├── backup_db.sh           # SQLite 热备份与压缩
    └── import_opml.py         # OPML 订阅文件批量导入工具
```

## 贡献指南

我们欢迎并感谢所有形式的贡献，包括但不限于代码实现、文档改进、链接资源补充建议及问题反馈。请遵循以下步骤以确保协作流程顺畅。

1. 在 GitHub 上 Fork 主仓库至个人账户，并将 Fork 后的仓库克隆至本地开发环境。建议在 dev 分支基础上新建特性分支，分支命名采用 `feature/` 或 `fix/` 前缀加简短描述。

2. 完成代码或文档修改后，确保所有现有测试用例通过，并为新增功能补充对应的单元测试与集成测试。测试覆盖率不低于 85%。运行 `pytest tests/` 验证本地环境。

3. 提交信息遵循 Conventional Commits 规范，格式为 `<type>(<scope>): <subject>`，type 包括 feat、fix、docs、style、refactor、perf、test、chore。提交前执行 `pre-commit` 钩子进行代码格式自动修正。

4. 发起 Pull Request 至主仓库的 main 分支，在 PR 描述中清晰说明变更目的、影响范围及测试策略。PR 标题应简明概括改动内容，关联相关的 issue 编号（如有）。

5. 等待至少一位维护者进行 Code Review。若 PR 涉及外部链接收录策略的调整或新增数据模型迁移，需在 PR 描述中附带迁移脚本的可回滚方案。合并后 CI 将自动构建并部署至 staging 环境进行冒烟测试。

## 常见问题

**Q: 为什么我添加的链接无法提取到标题或摘要？**

A: 可能原因包括目标服务器返回非 200 状态码、页面为 SPA 应用（需渲染 JavaScript）、或站点配置了反爬机制（如 Cloudflare 质询页）。LinkHub 默认使用 requests 库配合标准 User-Agent 进行抓取，对于反爬严格的站点，建议在管理后台将该链接标记为“需手动补全元数据”，然后通过编辑表单手工填写标题与描述。我们正在规划基于 Playwright 的渲染引擎作为可选增强插件。

**Q: 健康度巡检会对外部站点造成压力吗？是否会触发流量计费问题？**

A: 巡检任务默认采用指数退避策略，单次巡检周期（24 小时）内对同一域名只

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:16
