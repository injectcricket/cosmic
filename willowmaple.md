# LinkVault Resource Aggregator

LinkVault 是一个面向技术研究者、内容策展人和开发者的轻量级外链资源汇总与导航系统。该项目旨在解决分散信息难以追溯、碎片化阅读效率低下的问题，通过结构化收录和分类索引，将散落于网络各处的深度技术文章、工具文档和案例剖析进行统一归档。LinkVault 不生产内容，而是做最可靠的数字资源路由层，帮助用户在特定技术栈或业务领域中快速定位到高价值的外部参考资料。

项目定位为“技术外链的 Git 仓库”，每个链接条目均附带抓取时间、状态码校验和内容摘要哈希，确保引用可追溯、链接可验证。LinkVault 适用于个人知识库构建、团队技术周报素材源、以及自动化文档系统的外部依赖管理。

## 功能概览

**自动链接存活检测**：每日定时对入库 URL 发起 HEAD 请求，标记失效链接并记录响应码变化趋势。

**多维度标签分类**：支持自定义标签体系，可根据文章主题、技术领域、难度等级进行灵活标注与筛选。

**内容摘要快照**：对目标页面提取元描述和首段文本，生成 160 字符以内的内容快照，辅助快速判断相关性。

**批量导入与去重**：支持从 CSV、JSON 或纯文本列表批量导入 URL，自动识别重复条目并合并标签。

**RESTful API 输出**：提供 JSON 格式的列表接口，可按照时间、标签、域名等参数排序和过滤，便于集成到其他系统。

**全文检索支持**：基于标题、标签和摘要快照构建轻量级倒排索引，支持布尔查询和模糊匹配。

**访问统计看板**：记录每个外链的点击次数、最后访问时间和来源 Referer，生成简单的热度排行。

## 应用场景

**技术团队周报素材整理**：团队技术负责人或运营人员可以每周将分散在各大技术社区、博客、官方文档中的优质文章链接统一录入 LinkVault，并打上“后端架构”、“性能优化”、“安全漏洞”等标签，周报编写时直接按标签导出列表，大幅减少重复检索时间。

**自动化文档系统的外部依赖管理**：当技术文档中引用了大量外部规范（如 RFC 文档、IETF 草案、W3C 标准）或第三方库的官方公告时，LinkVault 可作为这些外链的中间管理层，统一检测链接可用性，在文档构建流程中提前预警死链，避免用户点击后遇到 404。

**个人技术阅读工作流**：开发者可以将日常浏览中遇到的待读文章、待验证的代码示例、待对比的方案讨论统统存入 LinkVault，利用标签和摘要快照做初步筛选，周末集中深度阅读，形成“收集-筛选-消化”的闭环阅读习惯。

**开源项目外部参考索引**：开源项目维护者可以将项目依赖的参考实现、设计决策依据、竞品分析报告等外链集中托管在 LinkVault 的某个分支中，新加入的贡献者可以通过查看这些外链快速了解项目的技术选型背景和演进脉络。

## 快速开始

以下命令演示了如何在本地环境中克隆代码仓库、安装依赖并启动开发服务。

```bash
# 克隆仓库到本地
git clone https://github.com/yourorg/linkvault.git
cd linkvault

# 安装 Python 依赖（使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化 SQLite 数据库并执行迁移
python manage.py migrate

# 导入示例数据（包含测试链接列表）
python manage.py loaddata fixtures/test_links.json

# 启动开发服务器
python manage.py runserver 0.0.0.0:8000
```

访问 http://localhost:8000 即可进入 LinkVault 的 Web 管理界面。默认管理员账号为 admin，密码在首次启动时由初始化脚本生成并输出到控制台日志中。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 及以上 | 核心运行环境，推荐使用 3.11 LTS |
| Django | 4.2.x LTS | Web 框架，用于提供管理界面和 API 端点 |
| SQLite | 3.35 及以上 | 默认数据库，支持 JSON 字段存储标签和元数据 |
| requests | 2.31.x | 用于执行链接存活检测和内容摘要抓取 |
| beautifulsoup4 | 4.12.x | HTML 解析库，用于提取页面元描述和正文首段 |
| django-cors-headers | 4.3.x | 处理跨域资源共享，便于前端独立部署时调用 API |
| redis | 7.0 及以上 | 可选，用于缓存链接状态和加速看板统计查询 |
| uWSGI | 2.0.x | 生产环境推荐部署网关，与 Nginx 配合使用 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | /docs/user-guide/ | 如何添加链接、编辑标签、查看统计和导出列表？普通用户的操作流程是怎样的？ |
| 管理员指南 | /docs/admin-guide/ | 如何配置存活检测的间隔时间？如何管理用户权限和审核队列？如何备份数据库？ |
| API 参考 | /docs/api-reference/ | API 的鉴权方式是什么？有哪些端点可以调用？请求和响应的数据结构如何定义？ |
| 部署运维 | /docs/deployment/ | 在生产环境中如何搭配 Nginx + uWSGI 部署？如何使用 Docker Compose 一键启动全套服务？ |

## 资源列表

- http://wap.mobile.hcbezg.cn/Article/details/4957696.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/55586.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4311.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2965.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8880.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/68638.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/479963.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1880334.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0837205.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4953.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8066651.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/53863.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2969.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9859.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3921.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/21402.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0540.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/740917.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2689091.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/52266.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/75521.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/24684.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/56406.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/45963.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/822232.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/23196.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7588235.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2981.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8571965.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/17734.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7169545.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/201497.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/011546.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/71588.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/587984.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8235021.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/738277.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/269692.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/75054.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/962039.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4085.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/175303.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/67913.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/557892.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/735464.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/024268.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/96423.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/851644.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/25534.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2958008.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8095.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/241909.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1687.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3752131.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1521.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/93261.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6004.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2331.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/97896.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/394137.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/695355.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5237.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2059.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0392.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3327.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7195963.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/126550.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1085778.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8769.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/531086.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5061.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3246114.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0115267.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/37791.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0135391.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/31597.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/918129.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/932730.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/92185.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0349356.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/468692.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/640085.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/664040.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4373647.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/35150.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4152.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/382529.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4014782.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3593.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/54826.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/14745.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9599.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/23570.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8883.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/47413.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6068191.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/294322.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0022.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7264.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/95409.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2463.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/620004.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/215897.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/11924.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4169740.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/967982.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6929.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0134.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4893701.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3247262.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/644962.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5647376.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2587.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/64457.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/44106.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/819104.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0832.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1736120.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9235.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/49230.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7988916.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/41330.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/25003.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/714578.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/31159.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6482870.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1993816.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6057.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7744454.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/29386.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1149537.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8544337.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9606904.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/89473.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/498814.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/69479.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7870.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/276900.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/68649.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3586.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/605311.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0249895.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/94713.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4092912.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/36954.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/663763.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0946.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3411.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/07405.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/843659.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/545755.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2536.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6205.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6294604.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/46372.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/939798.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/393985.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/99646.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6983671.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1342894.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9377.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9051794.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/20018.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/26434.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/00629.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/608046.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1568944.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6728.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7011897.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/59283.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/424134.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0699.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/25134.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/50002.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2388.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/385851.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/55112.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1540707.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/500533.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/915345.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8644997.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8330575.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7152.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/47483.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2368570.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9709.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7622255.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/242081.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0352890.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/28381.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3828749.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3042958.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/03799.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/361685.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/638687.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/179487.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/491253.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6141146.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/903976.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/145297.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6103457.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7971027.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8785.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2394307.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/23981.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3470561.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7982864.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/83257.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/01125.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2315942.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/66688.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5841604.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/56006.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/107474.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/65085.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7777.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0100042.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8306.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/43671.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6995072.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6029.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/425955.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3014.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3155.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/29701.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/64589.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/06178.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/93043.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1490950.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/45339.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/71227.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/499025.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/33410.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/29751.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/64758.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/851614.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/084530.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/660124.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5832098.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/85729.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1053945.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/156452.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1827.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9458332.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6098851.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/58746.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9581.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2257504.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9157269.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1824.sHtML

## 项目结构

```
linkvault/
├── manage.py                 # Django 项目管理入口，用于启动、迁移和 shell 交互
├── requirements.txt          # 生产环境 Python 依赖清单，锁定主要版本号
├── docker-compose.yml        # 容器编排文件，定义 web、redis、worker 三个服务
├── .env.example              # 环境变量模板，包含 SECRET_KEY、DATABASE_URL 等配置项
│
├── linkvault/                # 项目核心配置目录
│   ├── settings.py           # 主配置文件，包含中间件、数据库、静态文件、缓存等
│   ├── urls.py               # 根路由分发，挂载 admin、api 和 web 界面路由
│   ├── wsgi.py               # WSGI 网关入口，供 uWSGI / Gunicorn 调用
│   └── celery.py             # Celery 应用定义，配置任务队列和周期性调度
│
├── apps/                     # 所有自定义 Django 应用存放目录
│   ├── links/                # 链接管理核心应用
│   │   ├── models.py         # 定义 Link、Tag、Snapshot、ClickLog 四个数据模型
│   │   ├── admin.py          # 后台管理界面定制，支持批量导入和标签过滤
│   │   ├── tasks.py          # Celery 定时任务：链接存活检测和摘要更新
│   │   └── utils/            # 工具函数：HTML 解析、状态码映射、摘要生成
│   ├── api/                  # RESTful API 应用
│   │   ├── views.py          # 基于 Django REST Framework 的视图集
│   │   ├── serializers.py    # 序列化器，控制输出字段和验证逻辑
│   │   └── paginations.py    # 自定义分页器，支持游标分页和偏移分页
│   └── dashboard/            # 统计看板应用
│       ├── views.py          # 聚合查询视图，输出热度排行和趋势数据
│       └── templates/        # 看板 HTML 模板，使用 Chart.js 渲染图表
│
├── static/                   # 收集后的静态资源（CSS、JS、图片），生产环境由 Nginx 托管
├── media/                    # 用户上传文件（如批量导入的 CSV 示例文件）
├── fixtures/                 # 初始数据固件，包含演示链接和标签分类
├── scripts/                  # 运维脚本：数据库备份、日志轮转、健康检查
│   ├── backup_db.sh          # 每日凌晨执行 SQLite 数据库冷备
│   └── check_links.py        # 独立运行的链接巡检脚本，可配合 cron 使用
│
├── docs/                     # 完整文档源码，采用 Markdown + MkDocs 构建
│   ├── user-guide/           # 用户操作手册，含截图和常见工作流
│   ├── admin-guide/          # 管理员部署和配置手册
│   ├── api-reference/        # API 端点详细说明与示例代码
│   └── deployment/           # 生产环境部署指南（Nginx、uWSGI、Docker）
│
└── tests/                    # 单元测试与集成测试用例
    ├── test_models.py        # 数据模型层的测试，覆盖创建、更新、级联删除
    ├── test_api.py           # API 端点的测试，覆盖鉴权、参数校验、返回码
    └── test_tasks.py         # Celery 任务的模拟测试，使用 mock 避免真实网络请求
```

## 贡献指南

**报告缺陷或提出新功能建议**：请在 GitHub Issues 中新建工单，使用提供的模板填写复现步骤、运行环境、期望行为和实际表现。对于功能建议，请清晰描述使用场景和预期收益。

**提交代码变更**：Fork 本仓库到个人账户，在本地新建功能分支（命名格式为 feature/简短描述 或 fix/问题编号），完成开发后确保所有单元测试通过（执行 python manage.py test），然后发起 Pull Request 到主仓库的 develop 分支。PR 描述中需关联相关 Issue 编号，并列出测试覆盖情况。

**完善文档**：文档源码位于 docs/ 目录下，使用 MkDocs 构建。修改后可在本地运行 mkdocs serve 预览效果。翻译工作请先查阅 docs/i18n/ 下的语言目录，新增语种需同步更新导航配置。

**参与链接审核**：LinkVault 的公共实例允许用户提交新链接，但需要审核通过后才正式入库。社区贡献者可以申请成为审核员，负责检查链接内容是否合规、摘要是否准确、标签是否恰当。审核操作通过管理后台完成，操作日志会被记录以便回溯。

**提供测试用例**：欢迎补充更多边界情况的测试代码，尤其是针对各类非标准 HTML 页面的摘要提取逻辑、以及高并发场景下的链接检测任务调度。测试代码请放入 tests/ 目录，并遵循已有的命名和断言风格。

## 常见问题

**问：LinkVault 会存储外部页面的完整内容吗？**

答：不会。LinkVault 仅存储目标页面的元描述（meta description）和正文第一段文本，且截取长度不超过 160 个字符。这些摘要信息仅用于帮助用户在列表页快速判断链接主题，不构成对原始内容的复制或重新分发。页面标题和摘要的抓取行为遵循 robots.txt 的约定，并会在 User-Agent 中声明自身身份。

**问：链接存活检测对目标服务器会造成压力吗？**

答：检测任务采用单线程顺序执行，且每次请求之间间隔至少 2 秒。每个链接在 24 小时内只会被检测一次，对于单个目标域名，检测器会自动将请求间隔延长至 5 秒以上。如果目标服务器返回 429 状态码（Too Many Requests），检测器会将该链接标记为“暂缓检测”并推迟到下一个检测周期。用户也可以在后端配置文件中自定义请求间隔和并发数。

**问：如何将 LinkVault 与其他系统（如 Confluence、Notion 或自建 Wiki）集成？**

答：推荐使用 LinkVault 提供的 RESTful API 进行集成。例如

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:15
