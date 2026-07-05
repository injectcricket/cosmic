# WebIndex 外部技术资源聚合平台

WebIndex 是一个面向开发者与技术研究人员的轻量级外部技术资源聚合与导航系统。项目定位为技术文档、代码示例、工程实践与开源生态信息的统一入口，帮助用户在碎片化信息环境中快速定位高质量外部内容。WebIndex 本身不存储或托管任何原始内容，仅提供结构化索引与元数据描述，所有实际内容均指向经过人工筛选的外部站点。项目适用于个人开发者搭建私有技术书架、技术团队建立团队知识库、以及开源社区维护外部资源导航页等场景。通过自动化提取链接标题、关键词与摘要信息，WebIndex 能够显著降低信息整理与分类的人力成本，将散落在数百个独立页面中的技术资料聚合为可检索、可分类、可分享的统一数据集。

## 功能概览

- **按主题分类索引**：支持将外部链接按编程语言、框架、中间件、算法、运维等一级分类进行划分，每个链接可绑定多个标签，便于多维度检索。

- **自动元数据提取**：系统在首次录入链接时尝试抓取目标页面的标题、meta 描述与正文前 200 个字符，自动生成摘要，减少手动编辑工作。

- **全文检索与过滤**：基于倒排索引提供标题与摘要的全文搜索能力，支持按分类、标签、来源域名、更新时间范围进行组合过滤。

- **链接健康状态监控**：定期对已收录的链接进行可用性探测，标记失效链接并生成报告，帮助维护者及时清理或更新死链。

- **批量导入与导出**：支持从 CSV、JSON 及标准书签文件格式批量导入链接，同时也支持将全量索引导出为静态 HTML 或 Markdown 格式，方便离线浏览或迁移。

- **用户自定义收藏夹**：注册用户可创建个人收藏夹，将常用链接分组保存，支持设置私有或公开可见，便于团队内部分享高质量资源。

- **访问统计与热度排序**：统计每个外部链接在本平台内的点击次数与最近访问时间，支持按热度、最新收录、随机展示等多种排序方式，提升资源发现效率。

- **开放 API 接口**：提供 RESTful API 用于链接的增删改查、分类管理与标签操作，方便与其他内部系统或自动化脚本集成。

## 应用场景

1. **个人开发者构建技术阅读清单**：开发者可以在日常浏览技术博客、官方文档、开源项目仓库时，将值得反复查阅的链接一键收录到 WebIndex 中，并按照学习路线或技术栈进行分类整理，形成长期积累的个人技术资料库。

2. **技术团队内部知识库导航**：团队可以使用 WebIndex 搭建部门级的外部资源导航，统一收录团队常用的云服务控制台、监控面板、日志查询工具、内部文档站以及第三方依赖库的官方文档，新成员入职时可快速了解团队技术生态。

3. **开源项目维护外部生态链接页**：开源项目维护者可将项目依赖的周边工具、插件列表、社区教程、视频讲解等外部资源整理到 WebIndex 中，作为项目 README 或官方文档的补充，降低用户的学习门槛和寻找帮助的成本。

4. **技术社区或自媒体内容聚合**：技术社区运营者或技术博主可以使用 WebIndex 整理过往发布过的文章引用、嘉宾分享材料、线上会议录像链接等，形成可公开访问的资源导航页，提升内容复用率和读者体验。

## 快速开始

以下步骤指导您在本地环境中快速启动 WebIndex 服务。

```bash
# 1. 克隆代码仓库
git clone https://github.com/webindex/webindex.git
cd webindex

# 2. 安装项目依赖（使用 pip 和 npm）
pip install -r requirements.txt
npm install --prefix frontend

# 3. 初始化配置文件与数据库
cp config.example.yaml config.yaml
python scripts/init_db.py

# 4. 启动后端服务与前端开发服务器
python app.py &
npm run dev --prefix frontend
```

访问本地服务地址 http://localhost:3000 即可开始使用。生产环境部署请参考 `docs/deployment.md` 中的说明。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 至 3.11 | 后端服务运行环境，使用 FastAPI 框架 |
| Node.js | 18.x 或 20.x LTS | 前端构建与开发服务器依赖，使用 Vite + React |
| PostgreSQL | 14.x 或更高 | 主数据存储，包含链接、分类、标签及用户数据 |
| Redis | 7.x 或更高 | 用于缓存 API 响应与存储会话数据，提升并发性能 |
| Elasticsearch | 8.x 或更高 | 全文检索与高级过滤的搜索引擎，可独立部署 |
| Nginx | 1.24 或更高 | 生产环境推荐使用 Nginx 作为反向代理与静态资源服务 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide/quick-start.md | 如何使用 WebIndex 收录、分类和检索外部链接，以及个人收藏夹和分享功能的使用方法 |
| 管理员手册 | docs/admin/deployment.md | 生产环境部署方案、配置参数说明、日志管理、备份与恢复策略 |
| 开发者指南 | docs/developer/api-reference.md | RESTful API 的完整端点列表、请求参数与响应结构，以及插件扩展机制的设计说明 |
| 架构设计 | docs/architecture/overview.md | 系统整体架构图、数据流设计、搜索索引更新机制以及性能优化方案 |

## 资源列表

- http://m.mobile.hcbezg.cn/Article/details/127857.sHtML
- http://m.mobile.hcbezg.cn/Article/details/294980.sHtML
- http://m.mobile.hcbezg.cn/Article/details/50225.sHtML
- http://m.mobile.hcbezg.cn/Article/details/498990.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7141.sHtML
- http://m.mobile.hcbezg.cn/Article/details/18126.sHtML
- http://m.mobile.hcbezg.cn/Article/details/52981.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2285.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9328835.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5023.sHtML
- http://m.mobile.hcbezg.cn/Article/details/38923.sHtML
- http://m.mobile.hcbezg.cn/Article/details/36059.sHtML
- http://m.mobile.hcbezg.cn/Article/details/13540.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6294.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6163.sHtML
- http://m.mobile.hcbezg.cn/Article/details/01878.sHtML
- http://m.mobile.hcbezg.cn/Article/details/30436.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9281678.sHtML
- http://m.mobile.hcbezg.cn/Article/details/107825.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8747.sHtML
- http://m.mobile.hcbezg.cn/Article/details/39543.sHtML
- http://m.mobile.hcbezg.cn/Article/details/575333.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0874808.sHtML
- http://m.mobile.hcbezg.cn/Article/details/51637.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7514213.sHtML
- http://m.mobile.hcbezg.cn/Article/details/828442.sHtML
- http://m.mobile.hcbezg.cn/Article/details/53335.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5522946.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3171.sHtML
- http://m.mobile.hcbezg.cn/Article/details/250674.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6710118.sHtML
- http://m.mobile.hcbezg.cn/Article/details/100648.sHtML
- http://m.mobile.hcbezg.cn/Article/details/613217.sHtML
- http://m.mobile.hcbezg.cn/Article/details/790907.sHtML
- http://m.mobile.hcbezg.cn/Article/details/01037.sHtML
- http://m.mobile.hcbezg.cn/Article/details/62821.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3747255.sHtML
- http://m.mobile.hcbezg.cn/Article/details/154874.sHtML
- http://m.mobile.hcbezg.cn/Article/details/996913.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5988.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1759.sHtML
- http://m.mobile.hcbezg.cn/Article/details/742707.sHtML
- http://m.mobile.hcbezg.cn/Article/details/37469.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6746573.sHtML
- http://m.mobile.hcbezg.cn/Article/details/43603.sHtML
- http://m.mobile.hcbezg.cn/Article/details/34172.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0785.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5489342.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3677240.sHtML
- http://m.mobile.hcbezg.cn/Article/details/077690.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8417383.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2941.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6191382.sHtML
- http://m.mobile.hcbezg.cn/Article/details/251004.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8400637.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2029414.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0108741.sHtML
- http://m.mobile.hcbezg.cn/Article/details/607399.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5305.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3378317.sHtML
- http://m.mobile.hcbezg.cn/Article/details/56298.sHtML
- http://m.mobile.hcbezg.cn/Article/details/90937.sHtML
- http://m.mobile.hcbezg.cn/Article/details/58018.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2806.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6877.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4836.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0630.sHtML
- http://m.mobile.hcbezg.cn/Article/details/246449.sHtML
- http://m.mobile.hcbezg.cn/Article/details/646043.sHtML
- http://m.mobile.hcbezg.cn/Article/details/40031.sHtML
- http://m.mobile.hcbezg.cn/Article/details/26840.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3567667.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5982897.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2670776.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4686.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6666559.sHtML
- http://m.mobile.hcbezg.cn/Article/details/023029.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8335376.sHtML
- http://m.mobile.hcbezg.cn/Article/details/881890.sHtML
- http://m.mobile.hcbezg.cn/Article/details/051643.sHtML
- http://m.mobile.hcbezg.cn/Article/details/17273.sHtML
- http://m.mobile.hcbezg.cn/Article/details/42839.sHtML
- http://m.mobile.hcbezg.cn/Article/details/020808.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5436720.sHtML
- http://m.mobile.hcbezg.cn/Article/details/087838.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5978046.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6646.sHtML
- http://m.mobile.hcbezg.cn/Article/details/665851.sHtML
- http://m.mobile.hcbezg.cn/Article/details/262395.sHtML
- http://m.mobile.hcbezg.cn/Article/details/35753.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2576753.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9026.sHtML
- http://m.mobile.hcbezg.cn/Article/details/78351.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5994.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9952961.sHtML
- http://m.mobile.hcbezg.cn/Article/details/795698.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6929696.sHtML
- http://m.mobile.hcbezg.cn/Article/details/198257.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0028163.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9822.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8505.sHtML
- http://m.mobile.hcbezg.cn/Article/details/38516.sHtML
- http://m.mobile.hcbezg.cn/Article/details/09558.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1749082.sHtML
- http://m.mobile.hcbezg.cn/Article/details/508826.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4528.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2300.sHtML
- http://m.mobile.hcbezg.cn/Article/details/625787.sHtML
- http://m.mobile.hcbezg.cn/Article/details/513470.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6821.sHtML
- http://m.mobile.hcbezg.cn/Article/details/361239.sHtML
- http://m.mobile.hcbezg.cn/Article/details/672943.sHtML
- http://m.mobile.hcbezg.cn/Article/details/27081.sHtML
- http://m.mobile.hcbezg.cn/Article/details/044354.sHtML
- http://m.mobile.hcbezg.cn/Article/details/67510.sHtML
- http://m.mobile.hcbezg.cn/Article/details/14434.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5918692.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8981.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9370.sHtML
- http://m.mobile.hcbezg.cn/Article/details/138666.sHtML
- http://m.mobile.hcbezg.cn/Article/details/906991.sHtML
- http://m.mobile.hcbezg.cn/Article/details/47758.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2795.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0342.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8082.sHtML
- http://m.mobile.hcbezg.cn/Article/details/363381.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4840.sHtML
- http://m.mobile.hcbezg.cn/Article/details/56438.sHtML
- http://m.mobile.hcbezg.cn/Article/details/519944.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9200.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6941088.sHtML
- http://m.mobile.hcbezg.cn/Article/details/665078.sHtML
- http://m.mobile.hcbezg.cn/Article/details/37150.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4007.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8556.sHtML
- http://m.mobile.hcbezg.cn/Article/details/286536.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0486929.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2860122.sHtML
- http://m.mobile.hcbezg.cn/Article/details/397161.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7377.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7143.sHtML
- http://m.mobile.hcbezg.cn/Article/details/039347.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1747.sHtML
- http://m.mobile.hcbezg.cn/Article/details/871966.sHtML
- http://m.mobile.hcbezg.cn/Article/details/476416.sHtML
- http://m.mobile.hcbezg.cn/Article/details/481270.sHtML
- http://m.mobile.hcbezg.cn/Article/details/75743.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6371.sHtML
- http://m.mobile.hcbezg.cn/Article/details/400542.sHtML
- http://m.mobile.hcbezg.cn/Article/details/517934.sHtML
- http://m.mobile.hcbezg.cn/Article/details/057944.sHtML
- http://m.mobile.hcbezg.cn/Article/details/529056.sHtML
- http://m.mobile.hcbezg.cn/Article/details/20575.sHtML
- http://m.mobile.hcbezg.cn/Article/details/054463.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5027996.sHtML
- http://m.mobile.hcbezg.cn/Article/details/13001.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6919.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2720.sHtML
- http://m.mobile.hcbezg.cn/Article/details/69471.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7995.sHtML
- http://m.mobile.hcbezg.cn/Article/details/629016.sHtML
- http://m.mobile.hcbezg.cn/Article/details/20079.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2042222.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7685330.sHtML
- http://m.mobile.hcbezg.cn/Article/details/151584.sHtML
- http://m.mobile.hcbezg.cn/Article/details/09198.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1399480.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9251960.sHtML
- http://m.mobile.hcbezg.cn/Article/details/504466.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7445.sHtML
- http://m.mobile.hcbezg.cn/Article/details/91692.sHtML
- http://m.mobile.hcbezg.cn/Article/details/490651.sHtML
- http://m.mobile.hcbezg.cn/Article/details/469834.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0999567.sHtML
- http://m.mobile.hcbezg.cn/Article/details/470573.sHtML
- http://m.mobile.hcbezg.cn/Article/details/15865.sHtML
- http://m.mobile.hcbezg.cn/Article/details/54417.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4266476.sHtML
- http://m.mobile.hcbezg.cn/Article/details/31929.sHtML
- http://m.mobile.hcbezg.cn/Article/details/00682.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2007431.sHtML
- http://m.mobile.hcbezg.cn/Article/details/220532.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6794672.sHtML
- http://m.mobile.hcbezg.cn/Article/details/66945.sHtML
- http://m.mobile.hcbezg.cn/Article/details/50757.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2532.sHtML
- http://m.mobile.hcbezg.cn/Article/details/253406.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5360.sHtML
- http://m.mobile.hcbezg.cn/Article/details/86375.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6057535.sHtML
- http://m.mobile.hcbezg.cn/Article/details/37317.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6203.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8512347.sHtML
- http://m.mobile.hcbezg.cn/Article/details/22153.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9156.sHtML
- http://m.mobile.hcbezg.cn/Article/details/218719.sHtML
- http://m.mobile.hcbezg.cn/Article/details/892950.sHtML
- http://m.mobile.hcbezg.cn/Article/details/17150.sHtML
- http://m.mobile.hcbezg.cn/Article/details/97604.sHtML
- http://m.mobile.hcbezg.cn/Article/details/816864.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4572.sHtML
- http://m.mobile.hcbezg.cn/Article/details/16510.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1725100.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2095411.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7187.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1294.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4976405.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9985.sHtML
- http://m.mobile.hcbezg.cn/Article/details/797567.sHtML
- http://m.mobile.hcbezg.cn/Article/details/810764.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9443147.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2182.sHtML
- http://m.mobile.hcbezg.cn/Article/details/127126.sHtML
- http://m.mobile.hcbezg.cn/Article/details/132227.sHtML
- http://m.mobile.hcbezg.cn/Article/details/50056.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8917.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5744.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8507.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2224.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7247223.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0275290.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6116480.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7107830.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6420.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2831038.sHtML
- http://m.mobile.hcbezg.cn/Article/details/290353.sHtML
- http://m.mobile.hcbezg.cn/Article/details/683086.sHtML
- http://m.mobile.hcbezg.cn/Article/details/235360.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4366760.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8144.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6343735.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2205.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5739.sHtML
- http://m.mobile.hcbezg.cn/Article/details/727121.sHtML
- http://m.mobile.hcbezg.cn/Article/details/36833.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7039955.sHtML
- http://m.mobile.hcbezg.cn/Article/details/396676.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4168693.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5422.sHtML
- http://m.mobile.hcbezg.cn/Article/details/282378.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3782.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5528.sHtML
- http://m.mobile.hcbezg.cn/Article/details/87467.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5199222.sHtML
- http://m.mobile.hcbezg.cn/Article/details/777049.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5670695.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9633546.sHtML
- http://m.mobile.hcbezg.cn/Article/details/308227.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0979174.sHtML
- http://m.mobile.hcbezg.cn/Article/details/848769.sHtML

## 项目结构

```
webindex/
├── app/                          # 后端服务主目录
│   ├── api/                      # RESTful API 路由定义
│   │   ├── v1/                   # API 版本 v1 端点
│   │   │   ├── links.py          # 链接增删改查接口
│   │   │   ├── categories.py     # 分类管理接口
│   │   │   ├── tags.py           # 标签管理接口
│   │   │   └── search.py         # 全文检索接口
│   │   └── deps.py               # 依赖注入与鉴权依赖
│   ├── core/                     # 核心配置与工具模块
│   │   ├── config.py             # 配置加载与环境变量映射
│   │   ├── database.py           # 数据库连接池与 ORM 基类
│   │   └── security.py           # 密码哈希与 JWT 签发验证
│   ├── models/                   # SQLAlchemy 数据模型定义
│   │   ├── link.py               # 链接表模型
│   │   ├── user.py               # 用户与收藏夹模型
│   │   └── audit.py              # 操作日志与健康检查记录
│   ├── services/                 # 业务逻辑层服务
│   │   ├── fetcher.py            # 外部页面元数据抓取服务
│   │   ├── indexer.py            # Elasticsearch 索引更新服务
│   │   └── monitor.py            # 链接可用性定时监控服务
│   └── main.py                   # FastAPI 应用入口
├── frontend/                     # 前端单页应用
│   ├── src/                      # 源代码目录
│   │   ├── pages/                # 页面级组件
│   │   │   ├── Home.jsx          # 首页：搜索与热门链接展示
│   │   │   ├── Library.jsx       # 资源库列表与分类筛选
│   │   │   └── Favorites.jsx     # 个人收藏夹管理
│   │   ├── components/           # 可复用 UI 组件
│   │   │   ├── LinkCard.jsx      # 单个链接展示卡片
│   │   │   └── SearchBar.jsx     # 搜索输入框与过滤面板
│   │   └── store/                # 状态管理 (Zustand)
│   │       └── linkStore.js      # 链接数据与筛选状态
│   └── package.json              # 前端依赖与脚本
├── scripts/                      # 运维与开发辅助脚本
│   ├── init_db.py                # 初始化数据库表与默认分类
│   ├── import_bookmarks.py       # 从浏览器书签导入链接
│   └── health_check.py           # 手动触发全量链接健康检查
├── tests/                        # 单元测试与集成测试
│   ├── test_api/                 # API 端点测试用例
│   └── test_services/            # 业务服务单元测试
├── docs/                         # 文档目录
│   ├── user-guide/               # 用户手册
│   ├── admin/                    # 运维部署手册
│   └── developer/                # 开发与 API 文档
├── docker-compose.yml            # 开发环境容器编排配置
├── Dockerfile                    # 后端服务容器镜像构建文件
├── requirements.txt              # Python 生产依赖清单
└── README.md                     # 项目说明文件（当前文件）
```

## 贡献指南

1. 在 GitHub Issues 中查阅现有任务列表，选择未被认领且与自身技能匹配的 issue，或提交新的 issue 描述建议的功能或缺陷。讨论达成共识后，由项目维护者分配 issue 编号。

2. 从主线分支 checkout 新的功能分支，分支命名采用 `feature/issue-编号-简述` 或 `fix/issue-编号-简述` 格式。确保本地开发环境通过所有已有的单元测试。

3. 完成代码编写后，运行 `make lint` 和 `make test` 检查代码风格与测试覆盖率，新增功能需附带对应的单元测试或集成测试用例，确保覆盖率不低于原有水平。

4. 提交 commit 时遵循 Conventional Commits 规范，使用 `feat:`、`fix:`、`docs:`、`refactor:` 等前缀，并关联对应的 issue 编号。推送分支后在 GitHub 上发起 Pull Request，填写 PR 模板中的检查项。

5. 项目维护者会在 3 个工作日内进行 Code Review，提出修改意见或合并代码。合并后 CI 流水线将自动构建并部署到预发布环境，验证通过后择机合并至主线。

## 常见问题

**Q：WebIndex 是否存储外部链接的完整内容或快照？**

A：WebIndex 仅存储链接的元数据，包括标题、摘要、分类标签和最后访问时间。系统不缓存外部页面的完整 HTML 正文、图片或其他二进制资源。所有实际内容访问均会实时重定向至原始链接，用户点击后直接跳转至外部站点。这种设计确保了版权合规性，同时减少了存储与带宽成本。

**Q：链接健康状态监控的频率和失效处理策略是什么？**

A：系统默认每 24 小时对所有已收录链接进行一次 HTTP HEAD 请求探测。连续三次探测失败（超时或返回 4xx/5xx 状态码）的链接会被标记为“失效”。失效链接会在管理后台高亮显示，并自动从公开搜索结果中降权，但不会自动删除。维护者可定期查看失效报告，手动确认后决定更新链接地址或移除该条目。监控频率可通过配置文件中的 `monitor.interval_hours` 参数进行调整。

**Q：如何从其他导航工具或书签系统迁移数据到 WebIndex？**

A：WebIndex 提供了导入脚本 `scripts/import_bookmarks.py`，支持解析 Netscape HTML 书签导出格式（多数浏览器均支持此导出格式）、CSV 文件（列映射可配置）以及特定格式的 JSON 数组。导入时脚本会自动去重，并根据 URL 域名或路径规则建议分类。如果需要迁移特定字段，可参考 `docs/admin/migration.md` 中的详细列映射说明。对于大规模数据迁移，建议在导入前先在测试环境中

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:14
