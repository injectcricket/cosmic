# HCBEZG Mobile Article Gateway

HCBEZG Mobile Article Gateway 是一个面向移动端的技术文章聚合与导航系统，专注于采集、索引和展示来自 hcbezg.cn 域名的深度技术内容。该项目旨在为开发者、技术研究人员和内容策展人提供一个轻量级、可自托管的文章入口平台，解决移动端技术文档分散、检索效率低下的问题。

该项目基于静态站点生成技术，将原始文章链接转化为结构化的知识网络，支持按分类、标签和时间维度进行检索。适用于个人知识库构建、团队技术分享以及小型内容站点的快速部署。

## 功能概览

**多源文章聚合**：系统通过统一的入口地址自动识别并归类不同 ID 的技术文章，支持批量链接的索引与管理。

**移动端优先渲染**：所有页面均针对移动设备屏幕进行优化，确保在手机和平板上的阅读体验流畅。

**按 ID 精确路由**：每篇文章通过唯一的数字 ID 进行访问，URL 结构清晰，便于书签收藏和二次传播。

**静态缓存机制**：内置本地缓存层，对高频访问的文章进行静态化存储，降低源站负载并提升响应速度。

**分类标签自动提取**：从文章 URL 路径和内容元数据中自动生成分类标签，支持按主题浏览。

**全文检索支持**：集成轻量级全文检索引擎，允许用户在已索引的文章标题和摘要中进行关键词搜索。

**批量导入导出**：提供命令行工具，支持以 CSV 或 JSON 格式批量导入文章链接，以及导出索引报告。

**自定义主题系统**：允许开发者通过修改 CSS 变量和模板文件来定制站点外观，适配品牌需求。

## 应用场景

**技术团队内部知识库**：开发团队可将本系统部署在内网，用于汇总团队输出的技术博客或故障排查记录，统一入口便于成员查阅。

**个人技术文章收藏夹**：独立开发者或技术爱好者可以使用该系统整理自己关注的技术文章链接，通过 ID 快速定位并添加备注标签，构建个人学习资料库。

**内容策展与简报生成**：内容运营人员可利用批量导入功能，将每周精选的技术文章链接导入系统，自动生成带分类的周报页面，分享给订阅者。

**移动端技术文档镜像**：对于需要频繁查阅特定技术文档的研发人员，可以在本地或云服务器上运行该系统，作为文档的快速导航页，减少重复搜索时间。

## 快速开始

以下步骤指导您在本地环境中快速启动 HCBEZG Mobile Article Gateway 服务。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/hcbezg-gateway.git

# 进入项目目录
cd hcbezg-gateway

# 安装依赖项（使用 npm）
npm install

# 启动开发服务器
npm run dev

# 构建生产版本
npm run build

# 启动生产服务器
npm start
```

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Node.js | >= 18.0.0 | 项目运行时环境，用于执行 JavaScript 代码 |
| npm | >= 9.0.0 | 包管理器，用于安装项目依赖 |
| SQLite3 | >= 3.40.0 | 嵌入式数据库，用于存储文章索引和元数据 |
| Git | >= 2.30.0 | 版本控制系统，用于克隆仓库和管理代码 |
| Nginx 或 Apache | 可选 | 生产环境推荐使用的反向代理服务器 |
| PM2 | 可选 | Node.js 进程管理器，用于生产环境守护 |
| curl 或 wget | 任意版本 | 用于测试接口和健康检查的 HTTP 客户端工具 |
| openssl | >= 3.0.0 | 用于生成安全证书和加密校验和 |
| tar | 任意版本 | 用于解压项目归档文件 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | /docs/user-guide/ | 如何添加文章、使用搜索、自定义主题和导出数据 |
| 运维指南 | /docs/operations/ | 如何部署到生产环境、配置 SSL 证书、执行备份和恢复 |
| API 参考 | /docs/api/ | 如何通过 RESTful 接口访问文章元数据、分类列表和统计信息 |
| 开发者指南 | /docs/developer/ | 如何扩展解析器、增加新主题、提交代码和运行测试套件 |
| 架构说明 | /docs/architecture/ | 项目整体设计、数据流向、缓存策略和扩展点说明 |
| 常见任务 | /docs/tasks/ | 如何批量更新链接、清理过期缓存、迁移数据库 |

## 资源列表

- http://m.mobile.hcbezg.cn/Article/details/204227.sHtML
- http://m.mobile.hcbezg.cn/Article/details/09732.sHtML
- http://m.mobile.hcbezg.cn/Article/details/316636.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7135577.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9557984.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6623102.sHtML
- http://m.mobile.hcbezg.cn/Article/details/210631.sHtML
- http://m.mobile.hcbezg.cn/Article/details/92866.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1753.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7749920.sHtML
- http://m.mobile.hcbezg.cn/Article/details/729961.sHtML
- http://m.mobile.hcbezg.cn/Article/details/920824.sHtML
- http://m.mobile.hcbezg.cn/Article/details/194783.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6403875.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7106.sHtML
- http://m.mobile.hcbezg.cn/Article/details/902499.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0357.sHtML
- http://m.mobile.hcbezg.cn/Article/details/24007.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4453.sHtML
- http://m.mobile.hcbezg.cn/Article/details/819543.sHtML
- http://m.mobile.hcbezg.cn/Article/details/41303.sHtML
- http://m.mobile.hcbezg.cn/Article/details/762103.sHtML
- http://m.mobile.hcbezg.cn/Article/details/888312.sHtML
- http://m.mobile.hcbezg.cn/Article/details/122539.sHtML
- http://m.mobile.hcbezg.cn/Article/details/487292.sHtML
- http://m.mobile.hcbezg.cn/Article/details/09380.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6364.sHtML
- http://m.mobile.hcbezg.cn/Article/details/906546.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3158139.sHtML
- http://m.mobile.hcbezg.cn/Article/details/248710.sHtML
- http://m.mobile.hcbezg.cn/Article/details/11964.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4454.sHtML
- http://m.mobile.hcbezg.cn/Article/details/03386.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1499647.sHtML
- http://m.mobile.hcbezg.cn/Article/details/39968.sHtML
- http://m.mobile.hcbezg.cn/Article/details/49599.sHtML
- http://m.mobile.hcbezg.cn/Article/details/76389.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0190814.sHtML
- http://m.mobile.hcbezg.cn/Article/details/197666.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1660.sHtML
- http://m.mobile.hcbezg.cn/Article/details/59904.sHtML
- http://m.mobile.hcbezg.cn/Article/details/030109.sHtML
- http://m.mobile.hcbezg.cn/Article/details/99410.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2817.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0787.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8668976.sHtML
- http://m.mobile.hcbezg.cn/Article/details/11571.sHtML
- http://m.mobile.hcbezg.cn/Article/details/162490.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7967618.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9311194.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9243778.sHtML
- http://m.mobile.hcbezg.cn/Article/details/819583.sHtML
- http://m.mobile.hcbezg.cn/Article/details/559391.sHtML
- http://m.mobile.hcbezg.cn/Article/details/57456.sHtML
- http://m.mobile.hcbezg.cn/Article/details/82426.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3169962.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4484.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6768572.sHtML
- http://m.mobile.hcbezg.cn/Article/details/41801.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8016933.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5558554.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1971180.sHtML
- http://m.mobile.hcbezg.cn/Article/details/25171.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9995973.sHtML
- http://m.mobile.hcbezg.cn/Article/details/89064.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1309403.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8459.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3569334.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3509973.sHtML
- http://m.mobile.hcbezg.cn/Article/details/046792.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3380701.sHtML
- http://m.mobile.hcbezg.cn/Article/details/511189.sHtML
- http://m.mobile.hcbezg.cn/Article/details/468454.sHtML
- http://m.mobile.hcbezg.cn/Article/details/49531.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6513.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3683058.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9222.sHtML
- http://m.mobile.hcbezg.cn/Article/details/684233.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7573.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3975651.sHtML
- http://m.mobile.hcbezg.cn/Article/details/075593.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0745.sHtML
- http://m.mobile.hcbezg.cn/Article/details/272342.sHtML
- http://m.mobile.hcbezg.cn/Article/details/53431.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1849.sHtML
- http://m.mobile.hcbezg.cn/Article/details/89516.sHtML
- http://m.mobile.hcbezg.cn/Article/details/82759.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3336.sHtML
- http://m.mobile.hcbezg.cn/Article/details/017740.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6078738.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0676885.sHtML
- http://m.mobile.hcbezg.cn/Article/details/21552.sHtML
- http://m.mobile.hcbezg.cn/Article/details/85755.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7664.sHtML
- http://m.mobile.hcbezg.cn/Article/details/770720.sHtML
- http://m.mobile.hcbezg.cn/Article/details/41489.sHtML
- http://m.mobile.hcbezg.cn/Article/details/75610.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1999133.sHtML
- http://m.mobile.hcbezg.cn/Article/details/732960.sHtML
- http://m.mobile.hcbezg.cn/Article/details/39468.sHtML
- http://m.mobile.hcbezg.cn/Article/details/544386.sHtML
- http://m.mobile.hcbezg.cn/Article/details/654863.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2297.sHtML
- http://m.mobile.hcbezg.cn/Article/details/697328.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4948.sHtML
- http://m.mobile.hcbezg.cn/Article/details/02270.sHtML
- http://m.mobile.hcbezg.cn/Article/details/643635.sHtML
- http://m.mobile.hcbezg.cn/Article/details/601772.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6441.sHtML
- http://m.mobile.hcbezg.cn/Article/details/96768.sHtML
- http://m.mobile.hcbezg.cn/Article/details/348620.sHtML
- http://m.mobile.hcbezg.cn/Article/details/00591.sHtML
- http://m.mobile.hcbezg.cn/Article/details/530661.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9206.sHtML
- http://m.mobile.hcbezg.cn/Article/details/986025.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2887.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9471949.sHtML
- http://m.mobile.hcbezg.cn/Article/details/483565.sHtML
- http://m.mobile.hcbezg.cn/Article/details/566752.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0218555.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9940.sHtML
- http://m.mobile.hcbezg.cn/Article/details/45536.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8844.sHtML
- http://m.mobile.hcbezg.cn/Article/details/41611.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8431.sHtML
- http://m.mobile.hcbezg.cn/Article/details/978318.sHtML
- http://m.mobile.hcbezg.cn/Article/details/280488.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7624.sHtML
- http://m.mobile.hcbezg.cn/Article/details/677192.sHtML
- http://m.mobile.hcbezg.cn/Article/details/84302.sHtML
- http://m.mobile.hcbezg.cn/Article/details/28323.sHtML
- http://m.mobile.hcbezg.cn/Article/details/129729.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8313989.sHtML
- http://m.mobile.hcbezg.cn/Article/details/046404.sHtML
- http://m.mobile.hcbezg.cn/Article/details/84837.sHtML
- http://m.mobile.hcbezg.cn/Article/details/78990.sHtML
- http://m.mobile.hcbezg.cn/Article/details/247893.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0880.sHtML
- http://m.mobile.hcbezg.cn/Article/details/603383.sHtML
- http://m.mobile.hcbezg.cn/Article/details/15310.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0094716.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2123.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7603488.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6492.sHtML
- http://m.mobile.hcbezg.cn/Article/details/301077.sHtML
- http://m.mobile.hcbezg.cn/Article/details/900013.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0351.sHtML
- http://m.mobile.hcbezg.cn/Article/details/38334.sHtML
- http://m.mobile.hcbezg.cn/Article/details/37887.sHtML
- http://m.mobile.hcbezg.cn/Article/details/579485.sHtML
- http://m.mobile.hcbezg.cn/Article/details/00600.sHtML
- http://m.mobile.hcbezg.cn/Article/details/07715.sHtML
- http://m.mobile.hcbezg.cn/Article/details/00129.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7453.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6719510.sHtML
- http://m.mobile.hcbezg.cn/Article/details/14912.sHtML
- http://m.mobile.hcbezg.cn/Article/details/722228.sHtML
- http://m.mobile.hcbezg.cn/Article/details/544256.sHtML
- http://m.mobile.hcbezg.cn/Article/details/721394.sHtML
- http://m.mobile.hcbezg.cn/Article/details/23887.sHtML
- http://m.mobile.hcbezg.cn/Article/details/090812.sHtML
- http://m.mobile.hcbezg.cn/Article/details/30977.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5137.sHtML
- http://m.mobile.hcbezg.cn/Article/details/49962.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0232.sHtML
- http://m.mobile.hcbezg.cn/Article/details/020414.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4952.sHtML
- http://m.mobile.hcbezg.cn/Article/details/54085.sHtML
- http://m.mobile.hcbezg.cn/Article/details/178463.sHtML
- http://m.mobile.hcbezg.cn/Article/details/752241.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8786426.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4940.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0673.sHtML
- http://m.mobile.hcbezg.cn/Article/details/41405.sHtML
- http://m.mobile.hcbezg.cn/Article/details/83210.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7374432.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3329590.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5115.sHtML
- http://m.mobile.hcbezg.cn/Article/details/456510.sHtML
- http://m.mobile.hcbezg.cn/Article/details/116432.sHtML
- http://m.mobile.hcbezg.cn/Article/details/59940.sHtML
- http://m.mobile.hcbezg.cn/Article/details/89152.sHtML
- http://m.mobile.hcbezg.cn/Article/details/34085.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2893.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8277.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3409038.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5632075.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4142399.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0656.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2083247.sHtML
- http://m.mobile.hcbezg.cn/Article/details/627605.sHtML
- http://m.mobile.hcbezg.cn/Article/details/391137.sHtML
- http://m.mobile.hcbezg.cn/Article/details/299770.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3442.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4113538.sHtML
- http://m.mobile.hcbezg.cn/Article/details/50048.sHtML
- http://m.mobile.hcbezg.cn/Article/details/41044.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5712376.sHtML
- http://m.mobile.hcbezg.cn/Article/details/261185.sHtML
- http://m.mobile.hcbezg.cn/Article/details/5284.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7835.sHtML
- http://m.mobile.hcbezg.cn/Article/details/95220.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1964837.sHtML
- http://m.mobile.hcbezg.cn/Article/details/459498.sHtML
- http://m.mobile.hcbezg.cn/Article/details/857106.sHtML
- http://m.mobile.hcbezg.cn/Article/details/252134.sHtML
- http://m.mobile.hcbezg.cn/Article/details/24981.sHtML
- http://m.mobile.hcbezg.cn/Article/details/41255.sHtML
- http://m.mobile.hcbezg.cn/Article/details/19996.sHtML
- http://m.mobile.hcbezg.cn/Article/details/789958.sHtML
- http://m.mobile.hcbezg.cn/Article/details/474082.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8911530.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7627.sHtML
- http://m.mobile.hcbezg.cn/Article/details/058713.sHtML
- http://m.mobile.hcbezg.cn/Article/details/952568.sHtML
- http://m.mobile.hcbezg.cn/Article/details/3980178.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8548.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1182710.sHtML
- http://m.mobile.hcbezg.cn/Article/details/58757.sHtML
- http://m.mobile.hcbezg.cn/Article/details/076275.sHtML
- http://m.mobile.hcbezg.cn/Article/details/46951.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7416.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4456.sHtML
- http://m.mobile.hcbezg.cn/Article/details/439317.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2448.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2524.sHtML
- http://m.mobile.hcbezg.cn/Article/details/1014189.sHtML
- http://m.mobile.hcbezg.cn/Article/details/863582.sHtML
- http://m.mobile.hcbezg.cn/Article/details/0996764.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6684315.sHtML
- http://m.mobile.hcbezg.cn/Article/details/38255.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6995535.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8836530.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9512.sHtML
- http://m.mobile.hcbezg.cn/Article/details/802180.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2565.sHtML
- http://m.mobile.hcbezg.cn/Article/details/8274.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7300.sHtML
- http://m.mobile.hcbezg.cn/Article/details/75929.sHtML
- http://m.mobile.hcbezg.cn/Article/details/70599.sHtML
- http://m.mobile.hcbezg.cn/Article/details/2209236.sHtML
- http://m.mobile.hcbezg.cn/Article/details/31733.sHtML
- http://m.mobile.hcbezg.cn/Article/details/7208207.sHtML
- http://m.mobile.hcbezg.cn/Article/details/10788.sHtML
- http://m.mobile.hcbezg.cn/Article/details/4218.sHtML
- http://m.mobile.hcbezg.cn/Article/details/6763.sHtML
- http://m.mobile.hcbezg.cn/Article/details/944760.sHtML
- http://m.mobile.hcbezg.cn/Article/details/9137180.sHtML
- http://m.mobile.hcbezg.cn/Article/details/346762.sHtML
- http://m.mobile.hcbezg.cn/Article/details/87771.sHtML

## 项目结构

```
hcbezg-gateway/
├── src/
│   ├── core/                           # 核心引擎模块
│   │   ├── crawler.js                  # 文章链接抓取与解析逻辑
│   │   ├── cache.js                    # LRU 缓存管理实现
│   │   └── router.js                   # 基于 ID 的路由分发器
│   ├── middleware/                     # 中间件层
│   │   ├── auth.js                     # 简易访问鉴权（可选）
│   │   ├── logger.js                   # 请求日志记录
│   │   └── rate-limit.js               # 接口限流控制
│   ├── routes/                         # 路由定义
│   │   ├── article.js                  # 文章详情接口
│   │   ├── search.js                   # 全文检索接口
│   │   └── health.js                   # 健康检查端点
│   ├── services/                       # 业务服务层
│   │   ├── indexer.js                  # 文章索引构建服务
│   │   ├── exporter.js                 # 数据导出服务（CSV/JSON）
│   │   └── tagger.js                   # 自动标签生成服务
│   ├── utils/                          # 工具函数库
│   │   ├── validator.js                # URL 和 ID 校验器
│   │   ├── formatter.js                # 日期和文本格式化
│   │   └── crypto.js                   # 校验和与加密工具
│   └── app.js                          # 应用入口文件
├── templates/                          # 视图模板
│   ├── layouts/                        # 基础布局模板
│   │   ├── default.ejs                 # 默认页面框架
│   │   └── mobile.ejs                  # 移动端适配布局
│   ├── partials/                       # 可复用组件
│   │   ├── header.ejs                  # 站点头部
│   │   ├── footer.ejs                  # 站点底部
│   │   └── nav.ejs                     # 导航菜单
│   └── pages/                          # 页面模板
│       ├── home.ejs                    # 首页
│       ├── detail.ejs                  # 文章详情页
│       └── search.ejs                  # 搜索结果页
├── public/                             # 静态资源目录
│   ├── css/                            # 样式文件
│   │   ├── base.css                    # 基础样式
│   │   └── theme-dark.css              # 暗色主题
│   ├── js/                             # 前端脚本
│   │   ├── search.js                   # 搜索交互逻辑
│   │   └── analytics.js                # 简单统计脚本
│   └── assets/                         # 图片和字体
│       ├── logo.svg                    # 项目 Logo
│       └── favicon.ico                 # 站点图标
├── config/                             # 配置文件
│   ├── default.json                    # 默认配置
│   ├── production.json                 # 生产环境配置
│   └── development.json                # 开发环境配置
├── data/                               # 数据存储目录
│   ├── articles.db                     # SQLite 主数据库
│   ├── cache/                          # 静态缓存文件
│   └── exports/                        # 导出数据存放处
├── tests/                              # 测试用例
│   ├── unit/                           # 单元测试
│   ├── integration/                    # 集成测试
│   └── fixtures/                       # 测试数据
├── scripts/                            # 运维脚本
│   ├── import.js                       # 批量导入脚本
│   ├── export.js                       # 批量导出脚本
│   └── clean-cache.js                  # 缓存清理脚本
├── docs/                               # 文档源码
│   ├── user-guide/                     # 用户手册
│   ├── operations/                     # 运维指南
│   └── api/                            # API 参考文档
├── .env.example                        # 环境变量示例
├── .gitignore                          # Git 忽略文件列表
├── package.json                        # NPM 项目配置
├── package-lock.json                   # NPM 依赖锁定文件
├── README.md                           # 项目说明文档
├── LICENSE                             # MIT 许可证文本
└── docker-compose.yml                  # Docker 编排文件（可选）
```

## 贡献指南

我们欢迎并鼓励开发者以多种方式参与 HCBEZG Mobile Article Gateway 项目的改进。请遵循以下步骤提交您的贡献。

第一步：查阅现有的 Issue 列表和项目看板，确认您想要解决的问题或希望添加的功能尚未被他人认领。如有必要，可创建新的 Issue 详细描述您的想法或遇到的缺陷。

第二步：从主分支 fork 项目仓库到您的个人账户，并在本地创建一个新的功能分支。分支命名建议采用 `feature/功能简述` 或 `fix/问题简述` 的格式。

第三步：在您的分支上完成代码编写或文档更新。请确保代码风格与项目现有风格保持一致，并为新增功能编写相应的单元测试。所有测试用例必须通过。

第四步：提交代码前，运行项目的代码检查工具（如 ESLint）和测试套件，确保无风格错误和回归缺陷。提交信息应遵循语义化提交规范，清晰描述变更内容。

第五步：向主仓库的 `main` 分支发起 Pull Request，并在 PR 描述中引用相关的 Issue 编号，详细说明您的修改内容和测试覆盖情况。PR 将由项目维护者进行审查。

## 常见问题

**问：系统支持多少篇文章的并发索引？**

答：在默认配置下，系统使用 SQLite 作为后端存储，单机可稳定支持 10 万篇以内的文章索引。索引速度受限于网络 IO 和源站响应时间，实测平均每秒可处理 15-20 条链接。对于更大规模的场景，建议配置 Redis 作为缓存层，并调整 SQLite 的同步设置以提升写入性能。

**问：如何更新已导入文章的内容？**

答：系统默认不会自动刷新已导入的文章内容。如需更新特定文章，可以通过调用 `scripts/refresh.js` 脚本并传入文章 ID 来触发重新抓取和更新。批量更新时，可使用 `--batch` 参数配合文件列表。更新操作会保留原有的分类标签和创建时间，仅覆盖文章标题、摘要和正文内容。

**问：能否将系统部署到无数据库环境的纯静态托管服务？**

答：本系统依赖 SQLite 进行数据索引和检索，因此不适合直接部署到完全不支持数据库的纯静态托管平台（如 GitHub Pages）。但您可以在本地或 CI 环境中执行 `npm run export:static` 命令，将当前所有文章生成为一组静态 HTML 文件，然后将这些文件部署到任意静态托管服务上。导出时系统会生成完整的站点目录结构，包括首页、详情页和搜索页（搜索功能在静态模式下会降级为前端本地查找）。

## 许可证

MIT License

Copyright (c) 2025 HCBEZG Gateway Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:14
