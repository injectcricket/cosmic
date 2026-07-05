# CMC Mobile Article Gateway

CMC Mobile Article Gateway 是一个面向移动端内容聚合与分发场景的轻量级文章路由与资源导航系统。该项目定位于技术信息中间层，帮助开发者、内容运营者以及终端用户高效访问来自 cmcvrr.cn 域名下的海量移动端文章资源，并提供统一的入口管理与结构化访问能力。

项目采用静态资源索引与动态路由解析相结合的架构设计，能够对大规模文章 ID 进行有序归集，并生成可读性强、可维护性高的资源导航页面。目标用户包括移动端内容平台开发者、信息聚合工具维护者、数据采集与清洗工程师，以及需要批量访问特定文章详情页的研究人员。

---

## 功能概览

**批量文章路由索引**  
系统根据固定格式的文章详情 URL 模板，自动生成可遍历的资源访问列表，支持对文章 ID 进行排序、过滤与去重。

**移动端适配访问**  
所有输出链接均针对移动设备浏览环境进行优化，确保在手机、平板等小屏幕设备上的加载速度与排版可用性。

**结构化资源导出**  
支持将文章链接列表导出为 Markdown 格式、JSON 格式或纯文本格式，便于集成到其他自动化流程中。

**轻量级本地服务**  
提供基于 Node.js 或 Python 的本地开发服务器，用于快速预览资源导航页面，无需依赖外部数据库。

**可配置文章源**  
允许维护者通过外部配置文件动态增删文章 ID 列表，无需修改核心代码即可更新资源池。

**访问日志记录**  
内置请求日志中间件，记录每次文章链接的访问时间、来源 IP 与 User-Agent，辅助运维分析。

**健康检查端点**  
提供 /health 接口，用于监控服务运行状态，便于容器化部署与集群管理。

---

## 应用场景

**移动内容运营后台辅助工具**  
内容运营人员可通过该系统快速生成每日更新的文章链接汇总，用于推送至第三方渠道或进行人工审核。无需逐一复制 URL，仅需维护 ID 列表即可批量生成完整链接。

**数据采集任务入口管理**  
数据工程师可使用本系统作为采集任务的基础路由表，定时拉取文章链接列表并传入分布式爬虫集群。统一的链接格式降低了采集脚本的维护成本，新增文章仅需更新 ID 配置。

**技术文档与知识库导航**  
内部技术团队可将该系统改造为团队知识库入口，将技术博客、故障复盘报告、设计文档等资源按文章 ID 组织，形成可检索、可分享的轻量级导航门户。

**API 网关前置路由测试**  
开发者在构建移动端 API 网关时，可使用本系统模拟文章详情页的请求路径，测试路由转发、鉴权、限流等中间件逻辑，而无需依赖真实后端服务。

---

## 快速开始

以下命令演示如何在本地环境中克隆代码、安装依赖并启动开发服务。

```bash
# 克隆代码仓库
git clone https://github.com/your-org/cmc-mobile-gateway.git

# 进入项目目录
cd cmc-mobile-gateway

# 安装依赖（使用 npm）
npm install

# 启动本地开发服务（默认端口 3000）
npm run dev
```

启动成功后，在浏览器中访问 http://localhost:3000 即可查看文章资源导航首页。所有文章链接将按照 ID 升序排列展示，并支持分页浏览。

---

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Node.js | 16.x 或更高 | 运行时环境，用于执行核心服务代码 |
| npm | 8.x 或更高 | 包管理器，用于安装项目依赖 |
| Git | 2.25 或更高 | 版本控制工具，用于克隆仓库 |
| 操作系统 | Linux / macOS / Windows | 跨平台支持，建议使用 Linux 生产环境 |
| 浏览器 | Chrome 80+ / Firefox 75+ | 用于访问导航页面，支持现代 CSS 与 ES6 |

---

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | /docs/user-guide.md | 如何配置文章 ID 列表、如何启动服务、如何导出链接 |
| 开发指南 | /docs/development.md | 项目目录结构说明、核心模块职责、本地调试流程 |
| API 参考 | /docs/api-reference.md | 提供的接口端点、请求参数、响应格式与状态码 |
| 部署手册 | /docs/deployment.md | 生产环境构建、容器化部署、反向代理配置示例 |

---

## 资源列表

- http://m.mobile.cmcvrr.cn/Article/details/537613.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/049680.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/39970.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6652.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/107946.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6796.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7048530.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/45433.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/39117.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/55424.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2207778.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4351.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/151433.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/60528.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/163684.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7438.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/517128.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2820521.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8164.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/859018.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3017851.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7670.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/24177.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6487830.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1452627.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/031280.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/095374.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2325.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/00460.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2491603.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2743.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1218.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/19731.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8017.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/26647.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/074177.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/638396.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6740.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/62283.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/612420.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0353.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/27717.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6993233.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7259.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/38135.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7553.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6746661.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4180232.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/284235.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/5213319.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/15173.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3542750.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/01116.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/966059.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3354210.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6601.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/295100.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0462.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/288481.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/108426.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/80704.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/54282.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/958853.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/5195032.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/323178.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/031021.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2237499.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7936380.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/33023.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4789400.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/681319.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/41237.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7176946.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/088462.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/110152.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/582654.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4395.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3888.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/72070.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/283573.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/36851.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1786078.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/222495.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/09267.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2948.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8103.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2894.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/133368.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8719.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/5076736.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8875285.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/18712.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7323.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1439230.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9407689.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8287047.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9380815.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1489819.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/863153.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/000971.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/794268.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4779.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/47871.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/06679.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/813943.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2409.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/50549.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7183.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/27880.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2338.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8336.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/667945.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/668791.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/214154.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6889.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/27040.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1584179.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4120.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9775.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3629.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/64819.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2864586.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3225.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/203622.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0093.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2792.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/175353.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0902465.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9179542.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2528837.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/381346.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1672.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0148115.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2716960.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/662585.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7448.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/996542.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3084661.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4086514.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/47162.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6198.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1572647.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9142.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2993163.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/25852.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7775.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/46806.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9005.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9852086.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/166240.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/87664.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1233450.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/454225.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/91773.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2692.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6536044.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/24963.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/992031.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1292.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7982.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/75366.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/812848.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1112853.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/5827.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/066968.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/64113.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/49362.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7750552.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4672984.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/84500.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/20145.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/46758.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1003.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/87892.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2771.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/40471.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1523047.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2451.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4272.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6337812.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6173.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9309.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6935241.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/180054.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2777632.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7459.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0769.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4625872.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1615.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/48210.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7407.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/33515.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/32558.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/753476.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/16673.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/768721.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6383422.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/726714.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7169589.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/706943.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/209335.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/438663.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/51931.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/12449.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/62765.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/7263519.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/292351.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8071940.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/670177.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/81113.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2807.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/31749.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8327.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/007946.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0954541.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/4230.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/1105088.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/6122.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/597210.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3312429.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/27237.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0943104.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/74691.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/04078.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/73657.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/31581.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/01807.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/79081.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/90826.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/57254.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/904040.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9272330.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/13300.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3943943.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3076682.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/2033537.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/553855.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/570283.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/04211.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/454827.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8920547.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/22724.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/973256.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/07719.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/35332.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/3243.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/53687.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/8521199.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/9928.sHtML
- http://m.mobile.cmcvrr.cn/Article/details/0837030.sHtML

## 项目结构

```
cmc-mobile-gateway/
├── src/                                # 核心源代码目录
│   ├── routes/                         # 路由定义模块
│   │   ├── index.js                    # 基础路由与健康检查端点
│   │   └── articles.js                 # 文章详情链接生成与重定向逻辑
│   ├── middleware/                     # 中间件集合
│   │   ├── logger.js                   # 请求日志记录中间件
│   │   └── errorHandler.js             # 全局异常捕获与统一错误响应
│   ├── services/                       # 业务服务层
│   │   ├── articleService.js           # 文章 ID 解析、校验与链接构造
│   │   └── configService.js            # 外部配置加载与热更新管理
│   ├── utils/                          # 通用工具函数
│   │   ├── validator.js                # URL 格式与 ID 合法性校验
│   │   └── formatter.js                # 链接列表导出格式化（Markdown/JSON）
│   └── app.js                          # 应用入口，初始化 Express 实例
├── config/                             # 配置文件目录
│   ├── default.yaml                    # 默认配置（端口、日志级别、分页大小）
│   └── articles.ids.json               # 文章 ID 白名单列表（可外部维护）
├── docs/                               # 项目文档
│   ├── user-guide.md                   # 用户操作手册
│   ├── development.md                  # 开发者指南
│   ├── api-reference.md                # API 接口文档
│   └── deployment.md                   # 生产部署说明
├── tests/                              # 单元测试与集成测试
│   ├── unit/                           # 单元测试用例
│   └── integration/                    # 接口集成测试脚本
├── scripts/                            # 运维与辅助脚本
│   ├── start.sh                        # 生产环境启动脚本
│   └── seed-articles.js                # 初始化文章 ID 数据库种子数据
├── .gitignore                          # Git 版本控制忽略规则
├── package.json                        # npm 项目清单与依赖声明
├── README.md                           # 项目说明文档（当前文件）
└── LICENSE                             # MIT 许可证文本
```

---

## 贡献指南

**报告缺陷与建议**  
请在 GitHub Issues 中提交缺陷报告或功能建议，描述问题时请附上复现步骤、预期行为与实际行为，并标注系统环境与 Node.js 版本。

**分支开发流程**  
从 main 分支创建新的特性分支，分支命名遵循 feature/xxx 或 fix/xxx 格式。完成开发后提交 Pull Request，并在描述中关联相关 Issue 编号。

**代码风格规范**  
项目使用 ESLint + Prettier 统一代码风格，提交前请确保运行 npm run lint 无错误，且所有测试用例通过（npm test）。

**文档更新要求**  
任何影响配置项、API 接口或部署流程的变更，必须同步更新 docs 目录下对应的文档文件。新增功能需补充使用示例。

**测试覆盖率标准**  
所有新增服务层与工具函数代码，应附带对应的单元测试用例，分支覆盖率不低于 80%。

---

## 常见问题

**问：启动服务后访问页面显示空白，可能是什么原因？**

答：请检查 config/articles.ids.json 文件是否包含有效的文章 ID 列表。若该文件为空或格式不正确，系统将无法生成任何链接。您可以向该数组中添加至少一个数字 ID 后重启服务。同时确认端口 3000 未被其他进程占用，可通过 netstat -tlnp | grep 3000 检查。

**问：如何批量导入新的文章 ID？**

答：您可以直接编辑 config/articles.ids.json 文件，将新的 ID 以逗号分隔追加到数组中。系统支持热更新，保存文件后无需重启服务即可在导航页看到新增链接。若需要从外部数据源同步，可参考 scripts/seed-articles.js 脚本编写自动化导入逻辑。

**问：生产环境下如何修改默认端口？**

答：您可以通过环境变量 PORT 来覆盖默认端口，例如执行 PORT=8080 npm start。也可以修改 config/default.yaml 中的 server.port 字段，但需确保该配置文件在生产环境中被正确加载。

---

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:14
