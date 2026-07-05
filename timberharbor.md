# WebLink Navigator

WebLink Navigator 是一个面向开发人员、技术研究人员与信息分析师的轻量级外链资源聚合与导航系统。该项目定位于解决技术信息分散、优质外链难以追溯、文章资源缺乏统一管理入口的问题，通过结构化的资源收录机制，将散落在各处的技术文章、文档页面与参考资料集中归档，并提供清晰的分类导航与全文检索支持。

WebLink Navigator 并非一个传统的爬虫或采集平台，而是一个以人工精选与结构化整理为核心的外链编目系统。项目内置资源索引引擎，支持按来源域名、内容类型、收录批次、关键词等多维度进行筛选与排序。目标用户包括需要持续跟踪特定技术领域动态的研发工程师、撰写技术博客需要引用素材的创作者，以及需要为团队建立共享知识库的技术管理者。通过本系统，用户可以在海量碎片化信息中快速定位到有效资源，显著降低信息筛选成本。

## 功能概览

**批量资源导入与去重** 系统支持通过 CSV 或 JSON 格式批量导入外链数据，自动识别并去除重复条目，同时保留原始来源域名与路径结构，确保资源列表的完整性与纯净度。

**多维度筛选与全文检索** 用户可根据收录批次、域名后缀、内容类型（文章/文档/公告）以及自定义标签进行组合筛选；内置轻量级全文检索引擎，支持对文章标题、摘要及正文片段进行关键词匹配。

**资源状态监控与有效性检测** 系统定时对已收录的外链发起 HEAD 请求，检测资源是否仍可访问，并记录响应状态码与响应时间，对失效链接进行自动标记与告警。

**自定义标签与备注系统** 允许用户为每条外链添加自定义标签（如“Python”、“性能优化”、“安全”等）和备注说明，便于团队协作时共享对资源的理解与评价。

**收录批次管理** 针对批量导入的资源自动生成批次编号，支持按批次查看、导出或删除资源，方便进行周期性资源整理与审核。

**数据导出与快照生成** 支持将当前资源列表导出为 Markdown、HTML 或 JSON 格式，方便嵌入到其他文档系统或生成静态站点快照。

**用户权限与操作审计** 提供基础的多用户角色管理（管理员/编辑者/只读用户），所有增删改操作均记录审计日志，满足团队协作场景下的可追溯需求。

## 应用场景

**技术团队内部知识库构建** 研发团队在阅读技术博客、官方文档或解决方案文章时，可将有价值的外链统一收录至 WebLink Navigator，并添加团队内部标签与备注，逐步形成团队专属的知识导航库。新成员入职时可通过系统快速了解团队关注的技术领域与优质资源。

**技术资讯周报素材采集** 技术编辑或社区运营人员可在日常浏览过程中将待引用的文章链接批量导入系统，利用标签和备注功能对素材进行分类整理，在撰写周报或技术月刊时通过筛选功能快速提取相关资源，极大提升内容产出效率。

**个人技术阅读工作流管理** 独立开发者或研究人员可将系统作为个人阅读清单管理工具，对已读、待读和收藏的文章进行状态标记，利用检索功能快速找回数月前阅读过的某篇特定文章，避免浏览器书签杂乱无章且难以检索的问题。

**开源项目文档外链整合** 开源项目维护者可将项目依赖的参考文档、API 手册、社区讨论帖等外链集中收录，并在项目 README 或官网中引用 WebLink Navigator 生成的资源列表，为使用者提供一站式的参考资料入口。

## 快速开始

以下命令演示了从克隆代码到启动服务的完整流程。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/weblink-navigator.git

# 进入项目目录
cd weblink-navigator

# 安装 Python 依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 初始化 SQLite 数据库并创建表结构
python manage.py initdb

# 导入示例资源数据
python manage.py import --batch 106 --source ./data/batch_106.json

# 启动开发服务器
python manage.py runserver --host 0.0.0.0 --port 8080
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 - 3.12 | 核心运行环境，推荐使用 3.11 版本以获得最佳性能 |
| SQLite | 3.35.0 或更高 | 默认内置数据库，用于存储资源索引与元数据，无需额外安装 |
| Flask | 2.3.3 | Web 框架，提供路由、模板渲染与请求处理能力 |
| requests | 2.31.0 | 用于外链状态检测时发送 HTTP 请求，验证资源可用性 |
| python-dotenv | 1.0.0 | 加载 .env 环境变量配置文件，支持多环境部署 |
| click | 8.1.7 | 命令行交互框架，用于实现 manage.py 中的子命令 |
| markdown | 3.5.1 | 将资源备注中的 Markdown 文本渲染为 HTML，提升备注可读性 |
| pytest | 8.2.0 | 单元测试框架，仅在开发环境中需要，用于运行测试套件 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | /docs/user-guide/ | 如何导入资源、筛选与检索、管理标签和批次、导出数据 |
| 运维手册 | /docs/ops-guide/ | 如何部署生产环境、配置反向代理、设置定时任务检测资源状态 |
| 开发者指南 | /docs/dev-guide/ | 项目架构设计、插件开发规范、API 接口文档、数据库 ER 图 |
| 设计文档 | /docs/design/ | 数据模型设计决策、外链检测策略、性能优化方案与扩展性考量 |

## 资源列表

- http://wap.mobile.hcbezg.cn/Article/details/3909081.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/858917.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8160988.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2877.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8921982.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2677656.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/248281.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/65607.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/71257.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7400894.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3635310.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9197.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6546.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/65792.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/628810.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/22999.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2097.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/831255.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6255805.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4560603.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0517752.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/859706.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9404094.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9173880.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9096257.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/995347.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5955.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6077265.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4718.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3479.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7225038.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9071032.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4802.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/773515.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/132573.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/22989.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/43753.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2050937.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/772585.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2962.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0991644.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/73274.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8847.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/903505.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0928.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/87152.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1590133.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/54175.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/13906.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/60777.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/591069.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/74109.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/299644.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7381400.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/00295.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/02254.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/10719.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/02142.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6527.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/77498.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/57758.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/01686.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4537328.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/50705.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3405.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4399.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/365506.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3761625.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/67310.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3027.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/120626.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9496345.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9831.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/387899.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6088153.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/99754.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1272827.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6021.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/541717.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5552934.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5174387.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/87577.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9032.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4796025.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/803184.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7108899.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1656.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/86772.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9575093.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5969.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0026.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/66958.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4568188.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/34976.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/74373.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/15030.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4604.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/98721.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0980.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/35008.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/88428.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/18021.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/637242.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/954702.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2477.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0276080.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/983875.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/723092.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/823217.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2462.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/15910.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/36226.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/402557.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/631629.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/837989.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9500430.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8494.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/872477.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7647517.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/954284.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/72608.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2768457.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8560296.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8439.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2301.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/311825.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8281.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9001.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/38630.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7321.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/422498.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/024932.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/263715.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/099447.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6471.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/778078.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6331.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/430560.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/08148.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3673.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8393.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/59343.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0006830.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/763594.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7203.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2384.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/371275.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/63450.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/39531.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0434.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/865377.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3598216.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5027396.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/628468.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/327140.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4627175.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/43900.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/148324.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4377.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7265534.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5447.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2774621.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/483162.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9955602.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3335.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/864436.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5579207.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9511582.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/683762.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5283.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1678601.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5134.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9445457.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/777771.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/084199.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4433257.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3005.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2086.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/660455.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4651258.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1275655.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3436014.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/195262.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/722481.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/017656.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/557449.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/00838.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/421845.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/250094.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/340561.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/911324.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/842150.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/23811.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/64473.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7631.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3187.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/78607.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/31320.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3913136.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5598.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/39772.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/856526.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/370198.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/163443.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/65108.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5544.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/451347.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9315.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6202636.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/771574.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/317898.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/86293.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/70801.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6260.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0800886.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/09598.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/511200.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/01322.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/05813.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7713.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5094.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3578.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/883607.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/73406.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9371.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3404.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/10793.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2156.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6819679.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/207160.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7038.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5643.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/52679.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3886667.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/301131.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4137.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8131052.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/112235.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/591936.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/102761.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/486493.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/271066.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7500650.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4385876.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7462973.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0700926.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5818.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/382865.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/108325.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/92424.sHtML

## 项目结构

```
weblink-navigator/
├── app/                                # 核心应用包
│   ├── __init__.py                     # 应用工厂函数，创建 Flask 实例
│   ├── models.py                       # SQLAlchemy 数据模型定义（Resource, Batch, Tag）
│   ├── routes/                         # 路由蓝图模块
│   │   ├── __init__.py                 # 蓝图注册与统一前缀配置
│   │   ├── resource.py                 # 资源增删改查、筛选、导出接口
│   │   ├── batch.py                    # 批次管理、导入、删除接口
│   │   └── status.py                   # 资源状态检测与告警接口
│   ├── services/                       # 业务逻辑层
│   │   ├── __init__.py
│   │   ├── importer.py                 # CSV/JSON 导入解析与去重逻辑
│   │   ├── checker.py                  # 外链 HTTP 状态检测与超时控制
│   │   └── exporter.py                 # 数据导出为 Markdown/JSON/HTML
│   ├── templates/                      # Jinja2 模板文件
│   │   ├── base.html                   # 基础布局模板，包含导航与全局样式
│   │   ├── index.html                  # 资源列表主页，含筛选表单
│   │   └── detail.html                 # 单条资源详情页
│   └── static/                         # 静态资源（CSS、JavaScript）
│       ├── style.css                   # 自定义样式表，基于 Flexbox 布局
│       └── app.js                      # 前端交互逻辑（筛选、分页、标签编辑）
├── data/                               # 数据存储目录
│   ├── batch_106.json                  # 第 106 批次导入的原始资源数据示例
│   └── weblink.db                      # SQLite 数据库文件（运行时生成）
├── tests/                              # 单元测试与集成测试
│   ├── test_models.py                  # 数据模型层测试（CRUD 与约束）
│   ├── test_importer.py                # 导入解析功能测试
│   └── test_checker.py                 # 外链状态检测功能测试
├── scripts/                            # 运维与辅助脚本
│   ├── cron_check.sh                   # 定时检测外链状态的 crontab 调用脚本
│   └── backup_db.sh                    # 数据库每日备份脚本
├── docs/                               # 项目文档（Markdown 格式）
│   ├── user-guide/                     # 用户手册
│   ├── ops-guide/                      # 运维部署手册
│   └── dev-guide/                      # 开发者指南
├── .env.example                        # 环境变量模板文件
├── .gitignore                          # Git 忽略规则
├── requirements.txt                    # Python 依赖清单（固定版本）
├── manage.py                           # CLI 命令行入口（initdb、import、runserver）
└── README.md                           # 项目自述文件（当前文件）
```

## 贡献指南

欢迎并感谢所有形式的贡献，包括但不限于功能建议、缺陷报告、代码提交与文档完善。请遵循以下流程以确保协作顺畅。

1. 查阅问题追踪列表与贡献看板
访问 GitHub Issues 页面，查看现有待办任务与缺陷报告。如发现尚未记录的缺陷或希望新增功能，请先创建一个 Issue 并详细描述问题或需求，等待维护者确认后再开始工作，避免重复劳动或不必要的代码返工。

2. 派生项目仓库并创建功能分支
将主仓库 Fork 至个人账户，然后克隆派生仓库到本地。创建独立的功能分支，分支名称应遵循 `feature/功能简述` 或 `fix/缺陷简述` 的命名规范，例如 `feature/batch-import-json`。

3. 编写代码并确保测试通过
在本地开发环境中完成代码修改后，运行完整的测试套件以确保未引入回归缺陷。新增功能应附带相应的单元测试用例，测试覆盖率不低于原有水平。提交前执行代码格式化工具（如 black）以保持代码风格一致。

4. 推送分支并发起拉取请求
将本地功能分支推送到派生仓库，然后向主仓库的 `main` 分支发起 Pull Request。PR 描述中应引用相关的 Issue 编号，并简要说明修改内容与测试结果。维护者会在约定时间内进行 Code Review，如有修改意见将在 PR 下留言沟通。

5. 签署开发者贡献者许可协议
首次提交 Pull Request 前，需在 PR 评论中明确声明同意项目的 DCO（Developer Certificate of Origin），或在项目根目录下执行 `make dco-sign` 脚本完成电子签署。此举旨在确保所有贡献均可追溯且符合开源合规要求。

## 常见问题

**Q：系统支持从哪些数据源导入外链？是否支持从浏览器书签导入？**

A：当前版本支持 CSV（逗号分隔）和 JSON 两种格式的批量导入。对于 Chrome 或 Firefox 导出的书签 HTML 文件，暂不支持直接导入，但用户可将书签中的 URL 列表提取为 CSV 格式后通过系统导入。CSV 文件需包含 `url` 列，可选包含 `title` 和 `tags` 列。未来版本将考虑增加对 Netscape 书签格式的直接解析支持。

**Q：外链状态检测的频率和超时策略是怎样的？**

A：系统默认每 24 小时对所有已收录的外链执行一次状态检测，检测超时时间设定为 10 秒。对于连续三次检测返回 4xx 或 5xx 状态码，或连接超时的资源，系统会将其标记为“失效”并记录首次失效时间。失效资源不会被自动删除，用户可在管理界面中手动筛选并决定是否保留或移除。检测任务通过系统级定时任务（如 cron）触发，生产

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:15
