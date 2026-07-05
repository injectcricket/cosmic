# WapIndexer

WapIndexer 是一个面向移动端内容聚合与结构化外链管理的开源工具集。它主要服务于内容运营团队、个人站长以及移动端 Web 应用开发者，帮助其从零散的文章链接中提取元数据、建立索引目录，并生成可供二次开发使用的 JSON / Markdown 资源清单。该项目不依赖复杂的数据库，以静态文件为核心存储方式，适合部署在低成本的服务器或无服务器环境中。

WapIndexer 定位为轻量级外链中间层，不是搜索引擎，也不是爬虫框架，而是一个可定制的链接整理与分发节点。用户可以通过本项目对来自特定源的大量文章链接进行去重、分类、状态检测和批量导出，从而快速构建移动端导航页、RSS 替代源或内部知识库的原始素材池。项目内置了链接格式化校验器，能够自动识别并保留原始 URL 的协议、域名大小写与路径格式，满足严格的外链还原需求。

## 功能概览

**批量链接注入与解析**：支持一次性导入数百条文章详情页链接，自动提取路径中的资源 ID 与扩展名，生成结构化索引记录。

**原始格式强制保留**：所有输入的 URL 均按照原样存储与展示，不进行协议补全、大小写转换或尾部斜杠修正，确保与上游数据源完全一致。

**移动端优先的目录生成**：根据链接来源域名和文章编号自动生成分类目录树，输出结果适配手机屏幕浏览与触控操作。

**状态码轻量检测**：对每条链接执行可配置的 HTTP 头请求，标记可访问、重定向或失效状态，辅助清理死链。

**多格式导出接口**：支持将索引数据导出为 Markdown 列表、JSON 数组或 CSV 表格，便于导入其他文档系统或静态站点生成器。

**资源批次管理**：内置批次计数器，当前为第 103/200 批，支持按批次增量添加新链接，避免重复处理。

**命令行交互工具**：提供简单的 CLI 命令用于手动添加单条链接、批量导入文本文件以及生成最新的 README 资源章节。

## 应用场景

个人知识库构建：研究员或开发者可以将日常积累的移动端技术文章链接通过 WapIndexer 统一归档，每次新增链接时自动更新本地索引，并生成带注释的目录树，方便后续按主题检索。

团队运营协作：内容运营团队在整理移动端资讯时，可将来自同一源站的大量详情页链接批量导入项目，通过状态检测过滤掉已下线的页面，再将有效链接导出为团队共享的 Markdown 清单，供编辑人员撰写周报或选题策划。

静态导航站数据源：前端开发者可以将 WapIndexer 导出的 JSON 数据直接接入 Vue 或 React 构建的移动端导航页面，实现链接分类展示。项目本身不包含前端界面，但提供标准化的数据出口，方便与任意 UI 框架结合。

迁移辅助工具：当需要将旧站点的文章链接迁移到新域名时，WapIndexer 可以生成原始链接的完整列表，并配合脚本进行批量替换或重定向映射，减少手工遗漏。

## 快速开始

以下命令演示了如何获取项目、安装依赖并运行基础索引生成流程。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/wapindexer.git

# 进入项目目录
cd wapindexer

# 安装依赖（使用 npm 或 yarn）
npm install

# 运行索引生成脚本，默认读取当前批次链接并输出结果到 output/ 目录
npm run build-index
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
| :--- | :--- | :--- |
| Node.js | >= 16.0.0 | 运行时环境，用于执行核心脚本与 CLI 工具 |
| npm | >= 8.0.0 或 yarn >= 1.22 | 包管理器，用于安装第三方依赖库 |
| 文件系统读写权限 | 读写执行 | 项目需要在本地创建临时缓存目录和输出目录 |
| 网络连接 | 出站 HTTP/HTTPS | 用于执行链接状态检测（可选功能，可关闭） |
| 内存 | >= 512 MB | 处理 250 条链接约需 200 MB 堆内存 |
| 磁盘空间 | >= 20 MB | 用于存储索引文件、日志和导出结果 |
| 操作系统 | Linux / macOS / Windows (WSL) | 跨平台支持，推荐 Linux 服务器部署 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
| :--- | :--- | :--- |
| 用户手册 | docs/user-guide.md | 如何配置批次大小、修改导入源、调整输出格式？ |
| 运维指南 | docs/operations.md | 如何部署到云服务器、设置定时任务自动更新索引？ |
| 开发者文档 | docs/development.md | 核心模块的类图、扩展点说明以及如何编写自定义导出插件？ |
| API 参考 | docs/api-reference.md | 命令行参数详解、配置文件 schema 以及错误码对照表 |

## 资源列表

- http://wap.mobile.hcbezg.cn/Article/details/10721.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5697.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2862578.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/576703.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/96147.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/40060.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1772.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/08554.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8160457.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5155.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/47417.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/433079.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2667666.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3813052.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8528.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/954282.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0230296.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/573184.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/598982.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8169991.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6893939.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1851.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6735766.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0659802.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8327036.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/14073.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2717561.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/07526.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7899.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7123234.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4425130.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/093746.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/990826.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1231.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6880551.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/268352.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/424522.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/31408.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2758825.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4272436.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/012784.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/868381.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/439443.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/47154.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3804215.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/18301.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/387001.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2672834.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/747056.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/96421.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/446303.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1518.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/095863.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0165520.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7196453.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/91356.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/00067.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6667059.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/778362.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/27140.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/943065.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3177900.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0637.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0341.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/007401.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6724506.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/94478.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8357.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9948.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4735992.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/51947.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7999.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4203426.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2553.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/576857.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5152.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/44724.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/718869.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1560.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/906029.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6208528.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0813.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1332.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5482447.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2088.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/92544.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4680675.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5710.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6725941.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/71293.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/898698.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/38520.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3177.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/59168.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4114.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/811653.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4785773.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7039.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/31221.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/97621.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4093614.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4732825.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/538589.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2737635.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/460628.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/991878.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/242054.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/817043.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/206721.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/774175.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/06652.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/256496.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2955608.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/00497.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/676279.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/358075.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9574267.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6993270.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1070774.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1221.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6969.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/932664.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/10316.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8807.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0590.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/354142.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/738471.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/570659.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9790880.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8739.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/939508.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/94295.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/07787.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1278.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4798402.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/068420.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3264050.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2314.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7235.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/30576.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/97035.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5582217.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/97305.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8357138.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/90576.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7908.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/819605.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7383.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/815186.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3820295.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2418.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/33322.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/01460.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8484259.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/95070.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8163991.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1598892.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1978673.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/893644.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3605.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/442469.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/61672.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/242308.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/499190.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/94854.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3043976.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4914.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5310.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8118313.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7679910.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/21072.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/938855.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9090.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/086286.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4732.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/442382.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/268049.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/10995.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/209697.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4236767.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3191.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/390225.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6122791.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7842.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/16870.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/438373.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0413359.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/92274.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3041471.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/906902.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2050.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/077309.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9323533.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/017525.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/568059.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6521.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0890.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/217509.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/071464.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2222.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7705.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/414888.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3251725.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8173.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3946.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5859134.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9813.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/25965.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0996.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/77912.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5849892.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/71156.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3294670.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3044921.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3585571.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/91039.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5905546.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/949668.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6834297.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/409304.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3289901.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6536878.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/47825.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5137570.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1921.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2517411.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4548392.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3067.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5268.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/599399.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/223935.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/59064.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6042580.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8291.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/723174.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/35931.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7331673.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/85535.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/778874.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9865807.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0214.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/22580.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/677635.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9018.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5898421.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3678335.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2065.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/34662.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9003.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/78044.sHtML

## 项目结构

```
wapindexer/
├── bin/                                 # CLI 入口文件目录
│   └── wapindexer.js                    # 全局命令行工具入口，解析参数并调用核心模块
├── src/                                 # 源代码主目录
│   ├── core/                            # 核心处理逻辑
│   │   ├── indexer.js                   # 链接索引生成器，负责遍历输入并构建内部数据结构
│   │   └── validator.js                 # URL 格式校验器，严格保留原始字符串格式
│   ├── parsers/                         # 解析器模块
│   │   ├── url-extractor.js             # 从文本或数组中提取 URL 并归类
│   │   └── batch-manager.js             # 批次管理，当前批次计数及增量控制
│   ├── exporters/                       # 导出器实现
│   │   ├── markdown-exporter.js         # 将索引输出为 Markdown 列表
│   │   ├── json-exporter.js             # 输出 JSON 数组结构
│   │   └── csv-exporter.js              # 生成 CSV 表格，包含状态字段
│   ├── utils/                           # 通用工具函数
│   │   ├── fetcher.js                   # 执行轻量级 HTTP 请求，用于状态检测
│   │   └── logger.js                    # 日志记录器，分级输出到控制台和文件
│   └── config/                          # 配置管理
│       └── default.js                   # 默认配置项，包括超时时间、并发数、输出目录
├── tests/                               # 单元测试与集成测试
│   ├── unit/                            # 针对各模块的单元测试用例
│   └── fixtures/                        # 测试用的静态样本数据
├── docs/                                # 文档目录
│   ├── user-guide.md                    # 用户操作手册
│   ├── operations.md                    # 运维部署文档
│   ├── development.md                   # 开发者扩展指南
│   └── api-reference.md                 # API 与 CLI 完整参考
├── output/                              # 默认导出结果存放目录（git 忽略）
├── .gitignore                           # Git 忽略文件配置
├── package.json                         # npm 依赖管理与脚本定义
├── README.md                            # 项目主说明文档（当前文件）
└── LICENSE                              # MIT 许可证文本
```

## 贡献指南

1. 查阅 issue 列表或提议新功能：访问项目的 GitHub Issues 页面，确认当前待解决的问题或提交你的功能建议。对于较大的改动，请先开启一个讨论议题，避免重复劳动。

2. 派生项目并创建特性分支：点击项目页面右上角的 Fork 按钮，将仓库复制到你的账户下。然后在本地切换到新分支，分支命名建议采用 `feature/功能简述` 或 `fix/问题编号` 格式。

3. 编写代码并确保测试通过：在 `src/` 目录下修改或新增模块，并在 `tests/` 目录下补充相应的单元测试。运行 `npm test` 确保所有现有测试用例均能通过，且代码覆盖率不低于 80%。

4. 更新文档与示例：如果本次修改涉及用户可见的行为变化，请同步更新 `docs/` 目录下的相关文档以及本 README 中的功能概览或快速开始部分。同时检查 `output/` 目录下的示例导出文件是否需要刷新。

5. 提交 Pull Request：将你的分支推送到派生仓库，然后向主仓库的 `main` 分支发起 Pull Request。请在 PR 描述中清晰说明改动内容、测试结果以及是否影响已有批次数据格式。PR 合并前需要至少一位维护者审阅通过。

## 常见问题

**Q：为什么我导入的链接在生成的资源列表中发生了变化，比如自动加上了 www 或改变了大小写？**

A：WapIndexer 默认采用严格的原文保留策略。如果发生变动，请检查你的输入文件是否被文本编辑器自动格式化，或者是否使用了外部脚本预处理。项目内部的 `validator.js` 模块会对每条链接执行只读校验，但绝不会修改原始字符串。如果问题依然存在，请在配置中关闭 `normalizeUrl` 选项（默认已关闭）。

**Q：批次管理有什么作用？我如何处理超过 200 批次的链接？**

A：批次编号用于区分不同时间段或不同来源的链接集合。当前项目运行在第 103/200 批，意味着你最多可管理 200 个独立批次。当达到上限时，你可以通过修改 `src/config/default.js` 中的 `maxBatches` 参数来增加上限，或通过 `batch-manager.js` 提供的归档功能将旧批次导出并移出活跃目录。每个批次的数据独立存储，互不干扰。

**Q：状态检测功能会影响链接的原始格式吗？**

A：不会。状态检测仅通过发送 HTTP HEAD 请求获取响应码，该过程不修改链接的存储格式。检测结果会作为额外字段附加在索引数据中，但导出时默认仅输出原始链接列表。如果你希望导出包含状态信息的表格，请使用 `--with-status` 参数调用导出命令。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:15
