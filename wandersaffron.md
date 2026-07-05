# TechResource Hub

TechResource Hub 是一个面向开发者与技术研究人员的轻量级技术资源外链聚合平台，专注于从移动端开发、前后端工程、运维监控到算法研究的全链路技术资料索引。项目本身不存储任何实际内容，仅提供结构化、可检索的外部资源导航能力，帮助技术团队在碎片化信息环境中快速定位高质量技术文档、案例分析与工程实践。

本项目定位为技术团队的内部知识中台补充工具，也可作为个人开发者构建技术阅读清单的基础设施。通过统一的条目化管理，将分散于各类技术社区、官方文档与个人博客的优质文章按主题归类，并提供基础的全文检索与分类筛选接口，便于二次开发或嵌入现有知识库系统。

## 功能概览

**多维度分类索引**：按技术栈、应用场景、难度等级与发布时间对每条外链进行多维标记，支持组合过滤。

**轻量级全文检索**：基于标题与标签的模糊匹配检索，不依赖外部搜索引擎，响应时间控制在 200 毫秒以内。

**每日自动快照验证**：通过定时任务检测已收录链接的可达性与响应状态码，自动标记失效链接并生成报告。

**RESTful API 输出**：提供 JSON 格式的数据导出接口，便于与其他内部系统（如 Wiki、工单系统）集成。

**手动精选标注**：支持管理员对高价值内容添加“编辑推荐”与“深度阅读”标记，辅助团队新人快速建立学习路径。

**访问统计分析**：记录每条链接的点击频次与来源 IP 地域分布（聚合脱敏），为内容优化提供数据支撑。

**开放数据导入**：支持 CSV 与 Markdown 列表格式的批量导入，方便从旧系统迁移或团队协作维护。

## 应用场景

技术团队内部知识库维护。团队技术负责人或文档管理员可使用本平台统一收集团队成员推荐的优质技术文章，避免知识散落在聊天记录或邮件中，降低新人 onboarding 期间的信息收集成本。

个人开发者的每周技术阅读清单管理。开发者可将自己关注的领域（如 iOS 性能优化、前端构建工具、数据库调优）相关的文章集中收录，利用分类与检索功能快速回顾，减少重复搜索消耗的时间。

技术会议与黑客松活动的参考资料站。活动组织者可提前按主题（如机器学习部署、移动端跨平台方案）整理相关外链，供参会者现场查阅，提升活动技术深度与参与体验。

开源项目文档的外部引用规范化。开源项目维护者可将项目依赖的参考文档、社区讨论、衍生教程统一收录于本平台，替代散落在 README 中的零散链接，使项目文档更加整洁且便于版本追踪。

## 快速开始

以下步骤适用于 Linux 与 macOS 开发环境，Windows 用户建议使用 WSL2 或 Git Bash。

```bash
# 克隆仓库
git clone https://github.com/techresource-hub/trh-core.git
cd trh-core

# 安装依赖（使用 pip 虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化本地数据库（SQLite）
python manage.py migrate

# 导入示例数据（包含本批次资源占位记录）
python manage.py loaddata fixtures/seed_batch_129.json

# 启动开发服务器
python manage.py runserver 0.0.0.0:8000
```

访问 http://localhost:8000 即可查看前端界面，API 根路径为 http://localhost:8000/api/v1/links。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 ~ 3.11 | 核心运行环境，3.12 暂不支持部分依赖库 |
| Django | 4.2.7 LTS | Web 框架，长期支持版本 |
| SQLite | 3.35+ | 默认数据库，生产环境建议切换至 PostgreSQL 14+ |
| Redis | 6.2+ | 可选，用于缓存 API 响应与任务队列（生产环境推荐） |
| Celery | 5.3.4 | 异步任务调度，用于链接状态验证与统计聚合 |
| lxml | 4.9.3 | 用于解析部分网页标题与描述（仅限管理员主动操作） |
| requests | 2.31.0 | HTTP 客户端，用于健康检查与快照验证 |
| django-cors-headers | 4.3.1 | 跨域支持，便于前端分离部署 |
| python-dotenv | 1.0.0 | 环境变量管理，用于敏感配置分离 |
| gunicorn | 21.2.0 | 生产级 WSGI 服务器，推荐用于部署 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | /docs/quickstart.md | 如何在三分钟内完成本地部署并加载第一批量数据？ |
| 管理员手册 | /docs/admin-guide.md | 如何批量导入链接、管理分类标签、查看失效报告？ |
| API 参考 | /docs/api-reference.md | 如何通过 RESTful 接口获取链接列表、详情及统计信息？ |
| 部署运维 | /docs/deployment.md | 如何配置 PostgreSQL、Redis 与 Nginx 进行生产环境部署？ |
| 贡献规范 | /docs/contributing.md | 提交新链接或代码贡献时需要遵循哪些格式与流程？ |
| 常见问题 | /docs/faq.md | 遇到数据库迁移错误、检索无结果或验证超时如何处理？ |

完整文档目录位于仓库根目录的 docs/ 文件夹下，推荐使用 MkDocs 构建为静态站点进行浏览。

## 资源列表

- http://www.mobile.cvsifc.cn/Article/details/7137443.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2108524.sHtML
- http://www.mobile.cvsifc.cn/Article/details/18360.sHtML
- http://www.mobile.cvsifc.cn/Article/details/096837.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0009700.sHtML
- http://www.mobile.cvsifc.cn/Article/details/98359.sHtML
- http://www.mobile.cvsifc.cn/Article/details/33832.sHtML
- http://www.mobile.cvsifc.cn/Article/details/233790.sHtML
- http://www.mobile.cvsifc.cn/Article/details/873124.sHtML
- http://www.mobile.cvsifc.cn/Article/details/51335.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3344956.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3284.sHtML
- http://www.mobile.cvsifc.cn/Article/details/650992.sHtML
- http://www.mobile.cvsifc.cn/Article/details/085768.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5556208.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9870305.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7918.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4874118.sHtML
- http://www.mobile.cvsifc.cn/Article/details/38125.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7857231.sHtML
- http://www.mobile.cvsifc.cn/Article/details/67621.sHtML
- http://www.mobile.cvsifc.cn/Article/details/07817.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3085.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7224.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7371.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4451.sHtML
- http://www.mobile.cvsifc.cn/Article/details/74756.sHtML
- http://www.mobile.cvsifc.cn/Article/details/111416.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3911.sHtML
- http://www.mobile.cvsifc.cn/Article/details/507794.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0432804.sHtML
- http://www.mobile.cvsifc.cn/Article/details/816622.sHtML
- http://www.mobile.cvsifc.cn/Article/details/619306.sHtML
- http://www.mobile.cvsifc.cn/Article/details/32489.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5151270.sHtML
- http://www.mobile.cvsifc.cn/Article/details/497947.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6038.sHtML
- http://www.mobile.cvsifc.cn/Article/details/79101.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7149071.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6446.sHtML
- http://www.mobile.cvsifc.cn/Article/details/632481.sHtML
- http://www.mobile.cvsifc.cn/Article/details/774185.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2341.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1298.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3225253.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4570698.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0409716.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3905676.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7892277.sHtML
- http://www.mobile.cvsifc.cn/Article/details/816358.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0311.sHtML
- http://www.mobile.cvsifc.cn/Article/details/02830.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7094266.sHtML
- http://www.mobile.cvsifc.cn/Article/details/879189.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3257806.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5358.sHtML
- http://www.mobile.cvsifc.cn/Article/details/570062.sHtML
- http://www.mobile.cvsifc.cn/Article/details/095439.sHtML
- http://www.mobile.cvsifc.cn/Article/details/96312.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6095.sHtML
- http://www.mobile.cvsifc.cn/Article/details/13205.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3581.sHtML
- http://www.mobile.cvsifc.cn/Article/details/524312.sHtML
- http://www.mobile.cvsifc.cn/Article/details/822455.sHtML
- http://www.mobile.cvsifc.cn/Article/details/562472.sHtML
- http://www.mobile.cvsifc.cn/Article/details/61207.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0636.sHtML
- http://www.mobile.cvsifc.cn/Article/details/334417.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7196.sHtML
- http://www.mobile.cvsifc.cn/Article/details/839629.sHtML
- http://www.mobile.cvsifc.cn/Article/details/554203.sHtML
- http://www.mobile.cvsifc.cn/Article/details/96386.sHtML
- http://www.mobile.cvsifc.cn/Article/details/333449.sHtML
- http://www.mobile.cvsifc.cn/Article/details/19693.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6492.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1941947.sHtML
- http://www.mobile.cvsifc.cn/Article/details/38719.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3768.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0166810.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1066739.sHtML
- http://www.mobile.cvsifc.cn/Article/details/239383.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6239.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5801746.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6063405.sHtML
- http://www.mobile.cvsifc.cn/Article/details/86833.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6946.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5050112.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9024885.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1820.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7314.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4416.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4827.sHtML
- http://www.mobile.cvsifc.cn/Article/details/84112.sHtML
- http://www.mobile.cvsifc.cn/Article/details/814880.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8910997.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7252.sHtML
- http://www.mobile.cvsifc.cn/Article/details/12264.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0280.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0092.sHtML
- http://www.mobile.cvsifc.cn/Article/details/613146.sHtML
- http://www.mobile.cvsifc.cn/Article/details/88480.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7334.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8226.sHtML
- http://www.mobile.cvsifc.cn/Article/details/164182.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0559182.sHtML
- http://www.mobile.cvsifc.cn/Article/details/87229.sHtML
- http://www.mobile.cvsifc.cn/Article/details/02853.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6456728.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8369369.sHtML
- http://www.mobile.cvsifc.cn/Article/details/551233.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2429419.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6534477.sHtML
- http://www.mobile.cvsifc.cn/Article/details/39027.sHtML
- http://www.mobile.cvsifc.cn/Article/details/87946.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2567.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3758298.sHtML
- http://www.mobile.cvsifc.cn/Article/details/716592.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2561005.sHtML
- http://www.mobile.cvsifc.cn/Article/details/85458.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2963968.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0560957.sHtML
- http://www.mobile.cvsifc.cn/Article/details/65866.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1431.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8585.sHtML
- http://www.mobile.cvsifc.cn/Article/details/173280.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4741.sHtML
- http://www.mobile.cvsifc.cn/Article/details/13367.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0723842.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0517464.sHtML
- http://www.mobile.cvsifc.cn/Article/details/89167.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2364485.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1211570.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9465.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9471421.sHtML
- http://www.mobile.cvsifc.cn/Article/details/629792.sHtML
- http://www.mobile.cvsifc.cn/Article/details/73028.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6305715.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2124787.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6729.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0396947.sHtML
- http://www.mobile.cvsifc.cn/Article/details/76228.sHtML
- http://www.mobile.cvsifc.cn/Article/details/404222.sHtML
- http://www.mobile.cvsifc.cn/Article/details/31049.sHtML
- http://www.mobile.cvsifc.cn/Article/details/027860.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9871.sHtML
- http://www.mobile.cvsifc.cn/Article/details/948639.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1918.sHtML
- http://www.mobile.cvsifc.cn/Article/details/539520.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6914.sHtML
- http://www.mobile.cvsifc.cn/Article/details/42031.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5570292.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8939.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6104.sHtML
- http://www.mobile.cvsifc.cn/Article/details/057488.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3441.sHtML
- http://www.mobile.cvsifc.cn/Article/details/327950.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9094628.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3242.sHtML
- http://www.mobile.cvsifc.cn/Article/details/61150.sHtML
- http://www.mobile.cvsifc.cn/Article/details/64736.sHtML
- http://www.mobile.cvsifc.cn/Article/details/18969.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1568.sHtML
- http://www.mobile.cvsifc.cn/Article/details/77123.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4124.sHtML
- http://www.mobile.cvsifc.cn/Article/details/538677.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6453892.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2940.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9671.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8415814.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4864469.sHtML
- http://www.mobile.cvsifc.cn/Article/details/86633.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7926.sHtML
- http://www.mobile.cvsifc.cn/Article/details/94795.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6564245.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9840.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3946785.sHtML
- http://www.mobile.cvsifc.cn/Article/details/297984.sHtML
- http://www.mobile.cvsifc.cn/Article/details/951233.sHtML
- http://www.mobile.cvsifc.cn/Article/details/56666.sHtML
- http://www.mobile.cvsifc.cn/Article/details/545192.sHtML
- http://www.mobile.cvsifc.cn/Article/details/876878.sHtML
- http://www.mobile.cvsifc.cn/Article/details/26159.sHtML
- http://www.mobile.cvsifc.cn/Article/details/16459.sHtML
- http://www.mobile.cvsifc.cn/Article/details/439595.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3809.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2560.sHtML
- http://www.mobile.cvsifc.cn/Article/details/62148.sHtML
- http://www.mobile.cvsifc.cn/Article/details/232267.sHtML
- http://www.mobile.cvsifc.cn/Article/details/052960.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9099.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6400.sHtML
- http://www.mobile.cvsifc.cn/Article/details/38218.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6071.sHtML
- http://www.mobile.cvsifc.cn/Article/details/348167.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8419348.sHtML
- http://www.mobile.cvsifc.cn/Article/details/936125.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0303554.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2360207.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5777915.sHtML
- http://www.mobile.cvsifc.cn/Article/details/071835.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0391408.sHtML
- http://www.mobile.cvsifc.cn/Article/details/97138.sHtML
- http://www.mobile.cvsifc.cn/Article/details/048254.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3981773.sHtML
- http://www.mobile.cvsifc.cn/Article/details/52543.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2194.sHtML
- http://www.mobile.cvsifc.cn/Article/details/451893.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0391748.sHtML
- http://www.mobile.cvsifc.cn/Article/details/661725.sHtML
- http://www.mobile.cvsifc.cn/Article/details/174993.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5178779.sHtML
- http://www.mobile.cvsifc.cn/Article/details/401746.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0835.sHtML
- http://www.mobile.cvsifc.cn/Article/details/656898.sHtML
- http://www.mobile.cvsifc.cn/Article/details/51183.sHtML
- http://www.mobile.cvsifc.cn/Article/details/033020.sHtML
- http://www.mobile.cvsifc.cn/Article/details/00039.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5740425.sHtML
- http://www.mobile.cvsifc.cn/Article/details/87899.sHtML
- http://www.mobile.cvsifc.cn/Article/details/094240.sHtML
- http://www.mobile.cvsifc.cn/Article/details/42311.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9807.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7584.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5086132.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3614.sHtML
- http://www.mobile.cvsifc.cn/Article/details/09865.sHtML
- http://www.mobile.cvsifc.cn/Article/details/541729.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8002411.sHtML
- http://www.mobile.cvsifc.cn/Article/details/26381.sHtML
- http://www.mobile.cvsifc.cn/Article/details/23926.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3119487.sHtML
- http://www.mobile.cvsifc.cn/Article/details/98058.sHtML
- http://www.mobile.cvsifc.cn/Article/details/40191.sHtML
- http://www.mobile.cvsifc.cn/Article/details/26165.sHtML
- http://www.mobile.cvsifc.cn/Article/details/718546.sHtML
- http://www.mobile.cvsifc.cn/Article/details/205810.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1103.sHtML
- http://www.mobile.cvsifc.cn/Article/details/396033.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6270.sHtML
- http://www.mobile.cvsifc.cn/Article/details/90148.sHtML
- http://www.mobile.cvsifc.cn/Article/details/94068.sHtML
- http://www.mobile.cvsifc.cn/Article/details/03750.sHtML
- http://www.mobile.cvsifc.cn/Article/details/122515.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1846816.sHtML
- http://www.mobile.cvsifc.cn/Article/details/755599.sHtML
- http://www.mobile.cvsifc.cn/Article/details/32529.sHtML
- http://www.mobile.cvsifc.cn/Article/details/376439.sHtML
- http://www.mobile.cvsifc.cn/Article/details/934465.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5462268.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1102.sHtML

## 项目结构

```
trh-core/                          # 项目根目录
├── manage.py                      # Django 管理入口，用于启动、迁移与 shell
├── requirements.txt               # 生产环境依赖锁定文件
├── .env.example                   # 环境变量模板（数据库/Redis/密钥）
├── config/                        # 项目全局配置
│   ├── settings.py               # 主配置（含分环境加载逻辑）
│   ├── urls.py                   # 根路由映射
│   └── celery.py                 # Celery 应用声明与周期性任务注册
├── apps/                          # 所有业务模块
│   ├── links/                    # 链接核心模块（模型/视图/序列化）
│   │   ├── models.py             # Link、Category、Tag、HealthCheck 模型
│   │   ├── views.py              # 列表/详情/检索/统计接口
│   │   ├── serializers.py        # DRF 序列化与字段校验
│   │   └── tasks.py              # 异步任务：状态验证、点击统计
│   ├── importer/                 # 数据导入模块（CSV/列表解析）
│   │   ├── parsers.py            # 支持 Markdown 列表与标准 CSV
│   │   └── validators.py         # URL 格式与重复检测
│   └── dashboard/                # 管理后台（基于 Django Admin 扩展）
│       ├── admin.py              # 自定义列表展示与过滤器
│       └── widgets.py            # 标签输入与日期范围选择器
├── static/                        # 前端静态资源（CSS/JS）
│   ├── css/                      # 基于 Tailwind 的简洁样式
│   └── js/                       # 检索防抖与分页加载逻辑
├── templates/                     # Django 模板文件
│   ├── base.html                 # 基础骨架，含导航与页脚
│   └── links/                    # 列表页与详情页模板
│       ├── list.html
│       └── detail.html
├── docs/                          # 完整文档（Markdown 格式）
│   ├── quickstart.md
│   ├── admin-guide.md
│   ├── api-reference.md
│   ├── deployment.md
│   ├── contributing.md
│   └── faq.md
├── fixtures/                      # 初始数据（批次导入样例）
│   └── seed_batch_129.json       # 本批次 250 条链接占位记录
├── scripts/                       # 运维辅助脚本
│   ├── batch_import.py           # 命令行导入工具
│   └── health_check.py           # 手动触发全量验证
└── tests/                         # 单元测试与集成测试
    ├── test_models.py
    ├── test_api.py
    └── test_tasks.py
```

## 贡献指南

我们欢迎并期待来自社区的贡献，无论是新增链接资源、改进文档还是提交代码修复。请遵循以下步骤以确保协作顺畅。

第一步：查阅现有 Issue 与 Project Board。访问 GitHub Issues 页面查看是否有已记录的待办事项或功能请求，避免重复工作。对于新增资源推荐，请先确认该链接尚未被收录。

第二步：Fork 本仓库并创建特性分支。从主分支 checkout 一个新分支，命名规范为 `feature/功能简述` 或 `fix/问题简述`，例如 `feature/add-android-performance-links`。

第三步：实施变更并遵循代码规范。Python 代码请遵循 PEP 8，Django 模型变更需生成迁移文件。新增链接资源时，需在 fixtures 目录下补充对应的 JSON 条目，并确保 `url` 字段值与原始数据完全一致。

第四步：编写或更新单元测试。对于 API 接口变更，需在 tests/ 目录下补充对应的测试用例，确保覆盖率不低于原有水平。运行 `python manage.py test` 验证全部用例通过。

第五步：提交 Pull Request。PR 描述中请明确说明变更内容、影响范围及测试结果。合并前至少需要一位维护者审阅，CI 流水线将通过 GitHub Actions 自动执行语法检查与测试套件。

## 常见问题

**Q：导入资源列表时提示“URL 格式无效”，但链接在浏览器中可正常访问。**
A：本平台默认对 URL 进行严格的协议与格式校验，要求必须包含协议头（http:// 或 https://）。请检查原始数据是否包含不可见字符（如零宽空格或换行符），可使用 `strip()` 方法清理后再尝试导入。若仍无法通过，可临时调整 `validators.py` 中的正则表达式为宽松模式，但生产环境不推荐。

**Q：每日快照验证任务执行超时，导致 Celery worker 阻塞。**
A：当收录链接数量超过 5000 条时，全量验证可能超过默认的 300 秒超时阈值。建议将验证任务拆分为分页批量执行，每批 50 条，间隔 5 秒。已在 `tasks.py` 中提供 `batch_health_check` 方法，可通过设置 `CELERY_TASK_TIME_LIMIT = 600` 并启用 `acks_late` 选项缓解。

**Q：检索接口返回结果为空，但明明存在匹配的标题或标签。**
A：请检查数据库所使用的全文索引配置。SQLite 默认启用的是分词简单的 FTS5，对中文支持有限。若使用 PostgreSQL，建议安装 `pg_trgm` 扩展并启用 `django.contrib.postgres.search` 的 TrigramSimilarity 功能。在 `settings.py` 中切换 `SEARCH_ENGINE = 'trigram'` 即可。

## 许可证

MIT License

Copyright (c) 2026 TechResource Hub Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:15
