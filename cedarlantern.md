# WebLink Catalog Core

WebLink Catalog Core 是一个面向技术文档聚合与外部资源索引的开源静态站点生成工具。该项目定位于为开发者、技术团队及内容创作者提供一套轻量级、可扩展的外链资源管理方案，用于将离散的、编号化的文章链接整合为结构化的导航目录。目标用户包括需要维护内部技术知识库的团队、构建个人学习资源库的开发者，以及希望快速搭建技术外链汇总页面的内容运营人员。通过本工具，用户能够以声明式配置管理海量 URL，自动生成分类索引、标签过滤与全文检索功能，有效解决手动维护链接表格导致的效率低下、条目遗漏和检索困难等问题。

## 功能概览

**批量链接导入解析**：支持从纯文本列表、CSV 文件或编号化 URL 列表中批量导入资源链接，自动识别并提取文章 ID、分类前缀与文件扩展名，生成标准化内部记录。

**多维度分类与标签系统**：允许为每个资源链接赋予一个主分类（如 Article、Tutorial、Reference）和多个自定义标签，支持基于分类与标签的层级化筛选与聚合展示。

**全文内容检索**：基于链接标题、摘要关键词与自定义元数据构建倒排索引，提供毫秒级响应的全文搜索接口，支持模糊匹配与布尔运算符。

**静态站点生成引擎**：内置模板渲染器，可将结构化资源数据输出为纯 HTML 页面、JSON 数据接口或 Markdown 目录文件，适配静态托管、API 服务与文档站点集成。

**周期性健康检查**：集成链接可用性探测模块，支持配置定时任务对已收录 URL 发起 HEAD 请求，自动标记失效链接并生成异常报告。

**权限与访问控制**：提供基于角色的访问控制（RBAC）基础框架，支持管理员、编辑者、访客三级权限划分，便于团队协作管理资源库的增删改操作。

**数据导入导出兼容性**：支持 JSON、YAML、CSV 三种格式的数据导入导出，便于与现有工作流（如 Jira、Confluence、Excel 文档）进行数据交换。

## 应用场景

技术团队内部知识库的链接资产整合。当团队积累了大量分散在邮件、即时通讯或 Wiki 页面中的技术文章链接时，可使用 WebLink Catalog Core 将这些链接统一收录并生成可检索的团队知识导航页，显著降低查找信息的认知负担。

开源项目文档站的外部资源附录构建。开源项目维护者常需要在文档末尾列出参考链接或延伸阅读材料，本工具可根据预设模板自动生成格式规范的附录页面，并支持随项目版本发布自动更新链接列表。

个人开发者构建学习路径资源集合。开发者可将自己在学习某一技术领域（如分布式系统、前端工程化）过程中收集的教程、论文、视频链接通过本工具组织为具有分类层级的学习路径目录，并利用搜索功能快速定位特定主题内容。

内容运营团队制作技术周报或月刊的外链汇总。运营人员可以每周将收集的行业动态、技术博客、开源发布等链接批量导入系统，自动生成带有时间戳和标签分类的周报外链汇总页面，减少手动排版耗时。

## 快速开始

以下命令演示了从 GitHub 克隆项目、安装依赖并启动开发服务器的完整流程。

```bash
# 克隆项目仓库至本地
git clone https://github.com/weblink-catalog/core.git weblink-catalog-core

# 进入项目根目录
cd weblink-catalog-core

# 安装项目依赖（使用 npm）
npm install

# 启动开发服务器，默认监听端口 3000
npm run dev
```

执行上述命令后，可在浏览器中访问 http://localhost:3000 查看初始示例站点。生产环境构建可使用 `npm run build` 命令生成静态文件至 `dist` 目录。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | >= 18.0.0 | 项目运行时环境，需支持 ES2022 特性 |
| npm | >= 9.0.0 或 yarn >= 1.22.0 | 包管理器，用于安装第三方依赖 |
| SQLite3 | >= 3.40.0（内置集成） | 默认元数据存储引擎，无需独立安装 |
| Git | >= 2.30.0 | 版本控制工具，用于克隆仓库及贡献代码 |
| 操作系统 | Linux / macOS / Windows 10+ | 跨平台支持，Windows 下建议使用 WSL2 或 PowerShell 7 |
| 浏览器（开发用） | Chrome >= 100 / Firefox >= 100 | 用于预览开发服务器生成的页面样式 |
| 网络环境 | 可访问公网（用于链接健康检查） | 若在内网环境运行，需配置代理或关闭健康检查模块 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户指南 | /docs/guide/getting-started.md | 如何从零开始配置并运行第一个资源目录实例？ |
| 用户指南 | /docs/guide/import-data.md | 支持哪些数据导入格式？如何映射现有链接列表？ |
| 用户指南 | /docs/guide/customize-theme.md | 如何修改站点标题、配色和页面布局以匹配品牌？ |
| 运维手册 | /docs/ops/deployment.md | 生产环境如何部署到 Nginx、Vercel 或云存储？ |
| 运维手册 | /docs/ops/health-check.md | 链接健康检查的配置参数与告警规则如何设置？ |
| 开发者文档 | /docs/dev/architecture.md | 核心模块（解析器、索引器、渲染器）的架构设计是怎样的？ |
| 开发者文档 | /docs/dev/api-reference.md | 提供哪些 RESTful API 接口用于增删改查资源？ |
| 开发者文档 | /docs/dev/contribute-code.md | 代码规范、提交信息格式与 PR 流程分别是什么？ |

## 资源列表

- http://wap.mobile.cvsifc.cn/Article/details/2892.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9138762.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/977123.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/5970.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/5565743.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/793673.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/4602731.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/109983.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/386002.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/6396.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/2467671.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/402362.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/7315154.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/33859.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/2257.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/5696.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/02871.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/28223.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9587184.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/00091.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/13216.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/8992.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/1995.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/166058.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/606759.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/38775.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/1912.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/6867.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/8376.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/5002.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/3255141.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/98817.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9823228.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/507059.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/867441.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/54345.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/2840442.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/13630.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/42725.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/75049.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/182803.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/753849.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/8449696.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/384583.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/943234.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/2612.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/721650.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/23163.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9487027.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/3967.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/12195.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/08651.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/6269.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/6196682.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/8088.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/6059.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/767252.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/3416.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/60427.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/68926.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/3648065.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/1302874.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/8333939.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9423659.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/8351210.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/87527.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/8869894.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/8168952.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/3392751.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/7970.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/0861.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/5270.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/89922.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/966211.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/118495.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/368362.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/2336.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/709308.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/81235.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9064856.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/4478505.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/037131.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9576927.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9795.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/19357.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9358.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/6151396.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/40274.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/03936.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/649038.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/17520.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/24310.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/861683.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/1418551.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/742777.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/1535.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/485969.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9049881.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/8003.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/4710.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/262964.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/852119.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/823246.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/433299.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/1298274.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/885597.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/58317.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/065057.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/630258.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/6122656.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/931284.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/4597460.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/7388.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/13412.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/85453.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/81169.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/0914837.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/8246644.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/0469.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/58152.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/4812558.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/5983.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/5625.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/5755716.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/298134.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/4309945.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/212611.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9408822.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/71466.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/828624.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/664090.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/857886.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9704.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/8695.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/051568.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/378911.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/22317.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/65047.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9367456.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9175.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/76801.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/295236.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/4766668.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/7921.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/0335.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/2660.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/74835.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/0484.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/8606946.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9986.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/8616.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/697663.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/7293.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/646939.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/38647.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/650652.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/7298.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/6654.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/610702.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/4901557.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/12008.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9367.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/3589461.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/6262.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/80111.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/7147.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/5445244.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/759996.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/3576945.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/24584.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/999591.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9338301.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/8628758.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/115129.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/2747156.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/360026.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/636705.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/7567538.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9338.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/6517.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/6444.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/969872.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/336912.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/885272.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/32303.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/80803.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/85119.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/3627.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/4917382.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/5459.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/832044.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/17109.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/54014.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/2749765.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/4107427.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/370522.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/7828051.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/00243.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/87344.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/74587.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/5179054.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/24171.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/8374.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/69022.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/29396.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/859999.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/4399.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/466877.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/48519.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/0139.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9711.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/7981072.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/1450.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/137770.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/2095262.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/5346.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/4867.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/280736.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/36602.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/7639.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/83848.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/6093.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9920822.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9722831.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/0179.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9573673.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/3393341.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/731389.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/8773425.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/7552602.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/211985.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/2041804.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/8698632.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/701704.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/9325.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/4022.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/78939.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/01607.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/0173.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/506584.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/0799894.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/622354.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/876771.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/2858575.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/49762.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/2509163.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/15635.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/5054080.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/4925.sHtML
- http://wap.mobile.cvsifc.cn/Article/details/97442.sHtML

## 项目结构

```
weblink-catalog-core/
├── packages/                           # 核心功能模块（Monorepo 架构）
│   ├── parser/                         # 链接解析器，负责 URL 标准化与元数据提取
│   │   ├── src/
│   │   │   ├── lexer.ts                # 词法分析，拆分 URL 路径与查询参数
│   │   │   └── validator.ts            # 校验 URL 协议、域名及路径格式合法性
│   │   └── tests/                      # 单元测试用例集
│   ├── indexer/                        # 全文索引构建模块，基于倒排索引实现
│   │   ├── src/
│   │   │   ├── tokenizer.ts            # 中文/英文混合分词器
│   │   │   └── inverted-index.ts       # 倒排索引的核心数据结构与合并算法
│   │   └── tests/
│   ├── renderer/                       # 静态站点渲染引擎，支持多模板输出
│   │   ├── src/
│   │   │   ├── template-engine.ts      # 基于 EJS 的模板渲染器
│   │   │   └── output-writer.ts        # 将渲染结果写入文件系统或内存流
│   │   └── themes/                     # 内置主题资源（默认主题与暗色主题）
│   ├── checker/                        # 链接健康检查模块，支持定时轮询
│   │   ├── src/
│   │   │   ├── http-client.ts          # 基于 axios 的 HTTP 请求封装，支持超时重试
│   │   │   └── reporter.ts             # 生成失效链接报告（JSON / Markdown 格式）
│   │   └── tests/
│   └── cli/                            # 命令行入口，整合所有模块为可执行工具
│       ├── src/
│       │   ├── commands/
│       │   │   ├── build.ts            # 构建静态站点命令
│       │   │   ├── serve.ts            # 启动开发服务器命令
│       │   │   └── check.ts            # 手动触发链接检查命令
│       │   └── index.ts                # CLI 主入口，解析 commander 参数
├── configs/                            # 项目全局配置文件
│   ├── default.yaml                    # 默认配置（端口、缓存路径、分类映射表）
│   └── schema.json                     # 配置文件的 JSON Schema 定义
├── docs/                               # 完整文档（用户指南、运维手册、开发者文档）
│   ├── guide/
│   ├── ops/
│   └── dev/
├── scripts/                            # 辅助脚本（数据库迁移、示例数据生成）
│   ├── seed.ts                         # 生成示例资源数据用于测试
│   └── migrate-db.ts                   # SQLite 数据库表结构升级脚本
├── tests/                              # 端到端测试与集成测试
│   ├── e2e/
│   └── integration/
├── .github/                            # GitHub 社区配置文件
│   ├── workflows/                      # CI/CD 流水线（测试、构建、发布）
│   └── ISSUE_TEMPLATE/                 # 问题与功能请求模板
├── package.json                        # 项目依赖声明与脚本入口
├── tsconfig.json                       # TypeScript 编译配置（严格模式）
├── README.md                           # 项目主文档（即本文档）
└── LICENSE                             # MIT 许可证文本
```

## 贡献指南

本项目遵循开源社区协作规范，欢迎任何形式的贡献。请按照以下步骤参与开发：

1. 查阅项目看板与议题列表。在提交代码或新功能前，请先访问 GitHub Issues 页面确认是否存在相关议题。若无对应议题，请先创建一个新议题描述您要解决的问题或新增的功能，等待维护者反馈后再行开发，以避免重复工作或偏离项目方向。

2. 派生项目仓库并创建功能分支。将主仓库派生至个人账户下，然后克隆派生仓库至本地。请基于 `main` 分支创建一个具有描述性名称的新分支，例如 `feat/import-csv-support` 或 `fix/parser-encoding-issue`。分支命名建议遵循 `<类型>/<简述>` 格式。

3. 编写代码并确保通过所有测试。在 `src/` 或 `packages/` 下完成代码修改后，请补充或更新对应的单元测试用例，确保测试覆盖率达到 80% 以上。运行 `npm run test` 命令验证所有测试用例通过，并执行 `npm run lint` 检查代码风格是否符合项目 ESLint 配置。

4. 提交变更并撰写规范的提交信息。提交信息请遵循 Conventional Commits 规范，使用 `feat:`、`fix:`、`docs:`、`refactor:` 等类型前缀，并附上简明扼要的变更描述。示例：`feat(parser): add support for query parameter sorting`。

5. 发起拉取请求并参与代码评审。将功能分支推送至派生仓库后，在主仓库中发起 Pull Request。请在 PR 描述中关联对应的议题编号，并详细说明变更内容、测试结果以及可能的破坏性影响。至少一位项目维护者评审通过后，PR 将被合并至 `main` 分支。

## 常见问题

**问：导入包含数百个链接的列表时，页面加载速度变慢，如何优化？**

答：对于超过 200 条链接的资源导入操作，建议使用 CLI 模式下的批量导入命令而非通过 Web 界面上传。执行 `npm run cli import --file=./links.txt --batch-size=50` 可分批写入数据库，避免单次事务过大导致内存溢出。此外，可关闭实时索引更新开关，在导入完成后再执行 `npm run cli index --rebuild` 统一重建索引，可显著提升大批量导入效率。

**问：链接健康检查模块是否支持内网地址或需要认证的私有资源？**

答：健康

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:15
