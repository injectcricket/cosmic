# WebLink Navigator

WebLink Navigator 是一个面向技术研究者和内容聚合场景的轻量级外链资源导航系统。该项目定位于对分散在多个内容源、不同格式的技术文档与信息页面进行统一索引、快速检索和结构化展示，帮助用户从海量外链中高效定位到具体技术细节、原始参考资料或特定版本的存档页面。

项目核心目标用户包括技术文档维护者、开源社区运营人员、数据采集工程师以及需要定期跟踪大量外部信息源的研发团队。WebLink Navigator 不生产内容，也不重新托管任何第三方资源，仅提供链接元数据的采集、清洗、分类和检索能力，确保用户能够以最小的心智负担访问到原始信息所在位置。

## 功能概览

**批量链接导入与解析**：支持从纯文本列表、CSV 文件或特定格式的日志中批量导入原始 URL，自动解析路径参数、文件扩展名和 query 字符串，提取文章 ID 或资源标识符。

**自动元数据抓取**：对导入的每个链接执行轻量级 HEAD 请求与 HTML 标题提取，在不违反 robots 协议的前提下获取页面标题、内容类型、最后修改时间等基础元数据，用于后续检索和展示。

**多维度标签分类**：允许用户为每个链接标记自定义标签，支持标签树形结构管理，便于按技术领域、文档类型、来源站点或业务归属进行聚合筛选。

**全文检索引擎**：基于元数据字段与页面标题构建倒排索引，支持模糊匹配、前缀匹配和布尔组合查询，响应时间控制在 200 毫秒以内，适配 10 万级链接规模。

**状态监控与失效检测**：定期对已收录链接进行可用性探测，自动标记 4xx、5xx 状态码或超时链接，生成失效报告，辅助用户及时清理或更新资源。

**数据导入导出标准化**：支持 JSON、YAML 和 Markdown 表格三种格式的批量导出，便于嵌入技术文档、项目 Wiki 或外部知识库，也支持从标准格式反向导入更新。

**访问统计与热度排序**：记录每个链接的访问次数与最近访问时间，支持按热度、添加时间或字母序对资源列表进行动态排序，帮助用户发现高频使用的参考资料。

## 应用场景

技术文档团队的参考链接管理：技术文档中往往包含大量外部参考链接，手工维护容易出现链接失效或描述不准确的问题。WebLink Navigator 提供集中式链接登记、批量校验和元数据补充能力，文档编写者可以在撰写文档前将参考链接批量导入系统，生成格式化的链接清单，直接嵌入文档附录。

开源项目的外部依赖追溯：开源项目在声明依赖库、引用算法论文或使用第三方数据源时，需要明确记录每个外部资源的原始出处。WebLink Navigator 允许项目维护者按模块或版本对链接进行分组，当外部资源发生迁移或下线时，系统能够快速定位受影响的依赖链路。

数据采集任务的目标源管理：数据采集工程师通常需要维护一个庞大的目标 URL 列表，这些 URL 可能来自不同站点、不同目录层级。WebLink Navigator 支持批量链接导入和状态监控，能够直观展示哪些目标源可以正常访问、哪些需要更换代理或调整请求间隔，降低采集任务中的链接维护成本。

技术资讯的聚合与分发：技术社区运营人员可以将每日阅读到的技术文章、工具库、在线演示等链接统一收录到 WebLink Navigator，通过标签分类生成不同主题的推荐列表，再以 Markdown 或 JSON 格式导出，用于周报、月刊或社交媒体内容分发。

## 快速开始

以下命令演示了如何从代码仓库克隆 WebLink Navigator、安装依赖并启动开发服务器。

```bash
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator
npm install
npm run dev
```

执行上述命令后，开发服务器将在本地 3000 端口启动。访问 http://localhost:3000 即可进入链接管理界面。首次启动时，系统会自动创建 SQLite 数据库文件并初始化必要的表结构。如需使用 MySQL 或 PostgreSQL，请在启动前修改 config/database.js 中的连接配置。

生产环境部署建议使用 npm run build 构建静态资源，再通过 npm start 启动服务器进程。项目默认使用环境变量 PORT 来指定监听端口，若不设置则回退到 3000。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 16.20.0 或更高 | 运行时环境，建议使用 LTS 版本 |
| npm | 8.0.0 或更高 | 包管理器，用于安装项目依赖 |
| SQLite3 | 3.32.0 或更高 | 默认内置数据库，无需额外安装；若使用 MySQL 需额外配置 |
| 内存 | 512 MB 及以上 | 开发环境最低内存要求，生产环境建议 2 GB 以上 |
| 磁盘空间 | 200 MB 及以上 | 用于存储数据库文件及日志，实际需求随链接数量线性增长 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide/ | 如何导入链接、如何打标签、如何执行检索和导出数据 |
| 部署指南 | docs/deployment/ | 如何在不同操作系统上安装依赖、配置数据库和反向代理 |
| API 参考 | docs/api/ | 每个 RESTful 接口的请求参数、响应格式和错误码含义 |
| 开发指南 | docs/development/ | 项目目录结构说明、代码规范、单元测试编写和提交流程 |

## 资源列表

- http://wap.mobile.hcbezg.cn/Article/details/204227.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/09732.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/316636.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7135577.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9557984.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6623102.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/210631.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/92866.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1753.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7749920.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/729961.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/920824.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/194783.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6403875.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7106.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/902499.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0357.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/24007.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4453.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/819543.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/41303.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/762103.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/888312.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/122539.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/487292.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/09380.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6364.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/906546.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3158139.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/248710.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/11964.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4454.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/03386.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1499647.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/39968.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/49599.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/76389.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0190814.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/197666.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1660.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/59904.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/030109.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/99410.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2817.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0787.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8668976.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/11571.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/162490.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7967618.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9311194.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9243778.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/819583.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/559391.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/57456.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/82426.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3169962.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4484.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6768572.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/41801.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8016933.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5558554.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1971180.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/25171.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9995973.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/89064.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1309403.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8459.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3569334.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3509973.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/046792.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3380701.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/511189.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/468454.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/49531.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6513.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3683058.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9222.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/684233.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7573.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3975651.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/075593.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0745.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/272342.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/53431.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1849.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/89516.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/82759.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3336.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/017740.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6078738.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0676885.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/21552.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/85755.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7664.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/770720.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/41489.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/75610.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1999133.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/732960.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/39468.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/544386.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/654863.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2297.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/697328.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4948.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/02270.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/643635.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/601772.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6441.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/96768.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/348620.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/00591.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/530661.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9206.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/986025.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2887.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9471949.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/483565.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/566752.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0218555.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9940.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/45536.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8844.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/41611.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8431.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/978318.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/280488.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7624.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/677192.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/84302.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/28323.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/129729.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8313989.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/046404.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/84837.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/78990.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/247893.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0880.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/603383.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/15310.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0094716.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2123.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7603488.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6492.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/301077.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/900013.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0351.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/38334.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/37887.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/579485.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/00600.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/07715.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/00129.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7453.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6719510.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/14912.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/722228.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/544256.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/721394.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/23887.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/090812.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/30977.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5137.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/49962.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0232.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/020414.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4952.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/54085.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/178463.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/752241.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8786426.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4940.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0673.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/41405.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/83210.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7374432.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3329590.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5115.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/456510.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/116432.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/59940.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/89152.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/34085.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2893.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8277.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3409038.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5632075.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4142399.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0656.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2083247.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/627605.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/391137.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/299770.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3442.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4113538.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/50048.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/41044.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5712376.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/261185.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/5284.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7835.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/95220.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1964837.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/459498.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/857106.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/252134.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/24981.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/41255.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/19996.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/789958.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/474082.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8911530.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7627.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/058713.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/952568.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/3980178.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8548.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1182710.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/58757.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/076275.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/46951.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7416.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4456.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/439317.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2448.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2524.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/1014189.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/863582.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/0996764.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6684315.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/38255.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6995535.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8836530.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9512.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/802180.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2565.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/8274.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7300.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/75929.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/70599.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/2209236.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/31733.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/7208207.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/10788.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/4218.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/6763.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/944760.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/9137180.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/346762.sHtML
- http://wap.mobile.hcbezg.cn/Article/details/87771.sHtML

## 项目结构

```
weblink-navigator/
├── src/
│   ├── core/                         # 核心业务逻辑模块
│   │   ├── crawler.js                # 链接抓取与元数据提取
│   │   ├── indexer.js                # 倒排索引构建与检索
│   │   ├── monitor.js                # 链接可用性定时检测
│   │   └── exporter.js               # 数据导出为 JSON / YAML / Markdown
│   ├── routes/                       # HTTP 路由层
│   │   ├── api.js                    # RESTful API 端点定义
│   │   └── web.js                    # 管理界面路由
│   ├── models/                       # 数据模型与数据库操作
│   │   ├── link.js                   # 链接实体的 CRUD 操作
│   │   ├── tag.js                    # 标签树管理
│   │   └── visit.js                  # 访问日志记录
│   ├── services/                     # 外部服务适配
│   │   ├── fetcher.js                # 封装 axios 请求与重试策略
│   │   └── parser.js                 # HTML 标题解析与编码处理
│   ├── utils/                        # 通用工具函数
│   │   ├── validator.js              # URL 校验与规范化
│   │   ├── logger.js                 # 日志分级输出
│   │   └── config.js                 # 环境变量与配置加载
│   └── app.js                        # 应用入口与中间件装配
├── tests/                            # 单元测试与集成测试
│   ├── unit/                         # 各模块独立测试用例
│   └── integration/                  # 端到端 API 测试
├── docs/                             # 完整文档源文件
│   ├── user-guide/                   # 用户手册
│   ├── deployment/                   # 部署指南
│   ├── api/                          # API 参考文档
│   └── development/                  # 开发指南
├── config/                           # 配置文件目录
│   ├── database.js                   # 数据库连接配置
│   └── monitor.js                    # 检测间隔与超时参数
├── public/                           # 前端静态资源
│   ├── css/                          # 样式表
│   └── js/                           # 管理界面交互脚本
├── package.json                      # npm 项目清单
├── README.md                         # 本文档
└── LICENSE                           # MIT 许可协议
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库，将 fork 后的仓库克隆到本地开发环境。建议在 dev 分支上进行所有修改，保持 main 分支与上游同步。

2. 遵循项目代码风格，JavaScript 文件使用 ESLint 配置（基于 Standard 规范），提交前请运行 npm run lint 检查代码格式，确保无警告和错误。

3. 新增功能或修复缺陷时，请同步编写对应的单元测试用例，测试文件放置在 tests/unit 目录下，命名与被测试文件保持一致，使用 Mocha 和 Chai 作为测试框架。

4. 提交 commit 时使用语义化消息格式，即 <type>(<scope>): <subject>，其中 type 包括 feat、fix、docs、style、refactor、test、chore 等，scope 表示影响的模块名称。

5. 提交 pull request 之前，请确保本地所有测试通过（npm test），并更新 docs/ 目录下相关文档，特别是 API 变更时需要同步更新 API 参考文档。

## 常见问题

**问：导入大量链接时页面响应变慢，应该如何处理？**

答：当单次导入链接数量超过 1000 条时，建议使用命令行批量导入模式，而非通过 Web 界面上传。项目提供了 scripts/batch-import.js 脚本，可通过 node scripts/batch-import.js --file links.json 执行。该脚本会分批提交插入任务，并输出每批处理的进度日志。同时，请确保数据库连接池的最小连接数设置为 5 以上，具体可调整 config/database.js 中的 pool.min 参数。

**问：链接失效检测会不会对目标站点造成过大请求压力？**

答：WebLink Navigator 默认使用指数退避策略和随机抖动来控制检测频率。每个目标链接的检测间隔不低于 3600 秒，且同一域名下的并发请求数限制为 2 个。此外，系统会遵守目标站点 robots.txt 中规定的 Crawl-delay 指令，若目标站点未声明该指令，则使用全局默认的 500 毫秒请求间隔。用户也可在 config/monitor.js 中自定义全局 QPS 上限。

**问：能否将收录的链接数据迁移到其他系统？**

答：可以。WebLink Navigator 支持将完整数据导出为 JSON Lines 格式（每行一个链接对象），该格式被多数数据分析工具和数据库迁移脚本兼容。导出命令为 npm run export -- --format jsonl --output backup.jsonl。同时，项目也支持导出为标准的 CSV 表格，包含 URL、标题、标签、添加时间、最后检测状态等关键字段，便于在 Excel 或 Google Sheets 中进一步编辑。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:15
