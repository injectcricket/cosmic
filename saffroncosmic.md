# WebLink Hub

WebLink Hub 是一个面向开发者和技术研究人员的轻量级外链资源聚合与导航工具。该项目旨在解决技术文档、开发资源、学习资料分散在各个浏览器书签、笔记软件和即时通讯记录中难以统一管理和快速检索的问题。通过将大量分散的链接资源进行结构化整理和集中呈现，WebLink Hub 帮助用户构建个人或团队的技术知识索引体系。

WebLink Hub 定位于中小型技术团队、开源项目维护者以及个人开发者。它不只是一个静态的链接列表，而是提供了一套可本地部署、可定制分类、支持快速检索的资源管理方案。项目本身采用纯静态页面架构，无需数据库支持，所有数据通过 Markdown 和 YAML 配置文件进行管理，便于版本控制和协作编辑。用户可以通过简单的命令行操作完成项目的克隆、依赖安装和本地运行，在数分钟内建立起自己的技术资源导航站。

## 功能概览

**分层分类导航体系**：提供多级分类目录，支持按技术领域、资源类型、适用场景等维度对链接进行精细化归类，帮助用户快速定位目标资源。

**全文检索与快速过滤**：内置客户端全文检索功能，支持对链接标题、描述、标签和正文摘要进行关键词匹配，检索结果实时高亮显示。

**资源状态自动检测**：定期对收录的链接进行可达性检查，自动标记失效或响应超时的资源，并在界面上给出状态提示，确保资源列表的可用性。

**自定义标签与收藏标记**：允许用户为每个链接添加自定义标签，支持将高频使用的资源标记为收藏，并在列表中置顶显示。

**批量导入与导出**：支持通过 CSV 和 JSON 格式批量导入外部链接数据，也支持将当前资源列表导出为 Markdown 表格或 JSON 文件，便于备份和迁移。

**响应式移动端适配**：页面布局针对手机、平板和桌面设备进行了自适应优化，确保在移动设备上也能获得良好的浏览和检索体验。

**暗色主题与阅读模式**：内置浅色和暗色两套主题，支持一键切换。阅读模式可去除页面干扰元素，聚焦于链接内容的纯文本展示。

## 应用场景

技术团队内部知识库建设：开发团队可以将日常工作中积累的 API 文档、运维手册、设计规范、项目脚手架等链接统一收录到 WebLink Hub 中，作为团队共享的技术导航入口，减少重复查找时间，提升协作效率。

开源项目文档聚合：开源项目维护者可以使用 WebLink Hub 整理项目相关的官方文档、社区论坛、贡献指南、示例代码仓库、CI/CD 配置文件等外链资源，为贡献者和用户提供一站式的信息导航服务。

个人开发者学习路线管理：个人开发者可以按学习主题（如前端框架、后端微服务、数据科学、运维监控等）建立分类目录，将在线课程、技术博客、视频教程、官方规范等学习资源集中管理，形成可持续迭代的个人学习知识图谱。

技术活动与会议资料汇总：技术社区组织者或会议筹备人员可以将演讲幻灯片、视频回放链接、嘉宾博客文章、相关工具仓库等会议相关资料统一整理到 WebLink Hub，方便参会者会后回顾和查阅。

## 快速开始

以下命令帮助您在本地环境中快速启动 WebLink Hub 服务。

```bash
# 克隆项目仓库到本地
git clone https://github.com/weblink-hub/weblink-hub.git

# 进入项目目录
cd weblink-hub

# 安装项目依赖（使用 npm）
npm install

# 构建静态资源
npm run build

# 启动本地开发服务器
npm run dev
```

执行完上述步骤后，在浏览器中访问 http://localhost:3000 即可查看 WebLink Hub 的主界面。如需修改默认端口，可在项目根目录下的 .env 文件中设置 PORT 环境变量。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | >= 16.0.0 | 项目运行时环境，用于执行构建脚本和开发服务器 |
| npm | >= 8.0.0 | 包管理器，用于安装项目依赖和执行脚本命令 |
| Git | >= 2.30.0 | 版本控制工具，用于克隆仓库和管理代码变更 |
| 现代浏览器 | Chrome 90+ / Firefox 88+ / Edge 90+ | 前端页面运行环境，需支持 ES2020 和 CSS Grid 特性 |
| 操作系统 | Linux / macOS / Windows | 跨平台支持，Windows 系统建议使用 WSL2 或 PowerShell 7 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | docs/getting-started.md | 如何快速部署 WebLink Hub、如何进行首次配置、如何添加第一批链接资源 |
| 配置手册 | docs/configuration.md | 如何修改站点标题、导航菜单、分类体系、主题颜色等全局配置项 |
| 数据管理 | docs/data-management.md | 链接数据的文件结构是怎样的、如何批量导入导出、如何备份和恢复数据 |
| 开发指南 | docs/development.md | 如何二次开发、如何自定义页面模板、如何提交插件扩展、如何参与项目贡献 |

## 资源列表

- http://h5.mobile.hcbezg.cn/Article/details/204227.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/09732.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/316636.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7135577.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9557984.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6623102.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/210631.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/92866.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1753.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7749920.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/729961.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/920824.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/194783.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6403875.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7106.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/902499.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0357.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/24007.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4453.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/819543.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/41303.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/762103.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/888312.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/122539.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/487292.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/09380.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6364.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/906546.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3158139.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/248710.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/11964.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4454.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/03386.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1499647.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/39968.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/49599.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/76389.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0190814.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/197666.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1660.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/59904.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/030109.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/99410.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2817.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0787.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8668976.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/11571.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/162490.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7967618.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9311194.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9243778.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/819583.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/559391.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/57456.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/82426.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3169962.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4484.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6768572.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/41801.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8016933.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5558554.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1971180.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/25171.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9995973.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/89064.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1309403.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8459.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3569334.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3509973.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/046792.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3380701.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/511189.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/468454.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/49531.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6513.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3683058.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9222.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/684233.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7573.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3975651.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/075593.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0745.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/272342.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/53431.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1849.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/89516.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/82759.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3336.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/017740.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6078738.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0676885.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/21552.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/85755.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7664.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/770720.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/41489.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/75610.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1999133.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/732960.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/39468.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/544386.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/654863.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2297.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/697328.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4948.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/02270.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/643635.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/601772.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6441.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/96768.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/348620.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/00591.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/530661.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9206.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/986025.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2887.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9471949.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/483565.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/566752.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0218555.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9940.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/45536.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8844.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/41611.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8431.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/978318.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/280488.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7624.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/677192.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/84302.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/28323.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/129729.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8313989.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/046404.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/84837.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/78990.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/247893.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0880.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/603383.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/15310.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0094716.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2123.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7603488.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6492.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/301077.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/900013.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0351.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/38334.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/37887.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/579485.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/00600.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/07715.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/00129.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7453.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6719510.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/14912.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/722228.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/544256.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/721394.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/23887.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/090812.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/30977.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5137.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/49962.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0232.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/020414.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4952.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/54085.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/178463.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/752241.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8786426.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4940.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0673.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/41405.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/83210.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7374432.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3329590.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5115.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/456510.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/116432.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/59940.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/89152.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/34085.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2893.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8277.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3409038.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5632075.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4142399.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0656.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2083247.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/627605.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/391137.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/299770.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3442.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4113538.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/50048.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/41044.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5712376.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/261185.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5284.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7835.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/95220.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1964837.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/459498.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/857106.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/252134.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/24981.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/41255.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/19996.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/789958.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/474082.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8911530.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7627.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/058713.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/952568.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3980178.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8548.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1182710.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/58757.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/076275.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/46951.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7416.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4456.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/439317.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2448.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2524.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1014189.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/863582.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0996764.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6684315.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/38255.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6995535.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8836530.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9512.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/802180.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2565.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8274.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7300.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/75929.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/70599.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2209236.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/31733.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7208207.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/10788.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4218.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6763.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/944760.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9137180.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/346762.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/87771.sHtML

## 项目结构

```
weblink-hub/
├── public/                           # 静态资源目录，不经过构建流程直接复制
│   ├── favicon.ico                   # 站点图标文件
│   └── robots.txt                    # 搜索引擎爬虫配置文件
├── src/                              # 项目源代码主目录
│   ├── assets/                       # 静态资产，包含样式、图片和字体文件
│   │   ├── styles/                   # 全局样式表，基于 CSS 变量实现主题切换
│   │   ├── images/                   # 站点徽标、背景图等图片资源
│   │   └── fonts/                    # 自定义字体文件，用于提升排版效果
│   ├── components/                   # 可复用的 UI 组件库
│   │   ├── layout/                   # 页面布局组件，包括头部导航和底部版权
│   │   ├── common/                   # 通用组件，如按钮、输入框、标签、状态徽章
│   │   └── resource/                 # 资源列表专用组件，包括卡片、过滤器和分页器
│   ├── data/                         # 数据管理目录
│   │   ├── sources/                  # 按分类存放的链接数据 YAML 文件
│   │   ├── tags.yaml                 # 全局标签定义和颜色映射配置
│   │   └── categories.yaml           # 分类层级结构定义文件
│   ├── hooks/                        # 自定义 React Hooks，封装状态逻辑
│   │   ├── useSearch.ts              # 全文检索逻辑 Hook
│   │   ├── useFilter.ts              # 分类和标签过滤逻辑 Hook
│   │   └── useStatusCheck.ts         # 链接状态检测逻辑 Hook
│   ├── utils/                        # 工具函数集合
│   │   ├── validator.ts              # URL 格式校验和规范化工具
│   │   ├── parser.ts                 # YAML 和 JSON 数据解析转换工具
│   │   └── export.ts                 # 数据导出为 CSV 和 JSON 格式的工具
│   ├── pages/                        # 页面入口组件
│   │   ├── Home.tsx                  # 首页，展示资源列表和搜索入口
│   │   ├── Category.tsx              # 分类视图页面，按分类展示资源
│   │   └── Settings.tsx              # 设置页面，管理主题、导入导出等
│   ├── App.tsx                       # 应用根组件，配置路由和全局状态
│   └── main.tsx                      # 应用入口文件，初始化渲染
├── config/                           # 项目配置文件目录
│   ├── site.config.ts                # 站点全局配置，包含标题、描述、导航菜单
│   └── build.config.ts               # 构建工具配置，包含入口和输出路径
├── scripts/                          # 辅助脚本目录
│   ├── check-links.js                # 链接可达性检测脚本，可定时执行
│   └── import-data.js                # 批量导入外部数据脚本
├── docs/                             # 项目文档目录
│   ├── getting-started.md            # 入门指南文档
│   ├── configuration.md              # 配置手册文档
│   ├── data-management.md            # 数据管理文档
│   └── development.md                # 开发指南文档
├── tests/                            # 单元测试和集成测试目录
│   ├── components/                   # 组件测试文件
│   └── utils/                        # 工具函数测试文件
├── .env.example                      # 环境变量示例文件，包含端口和 API 配置
├── .gitignore                        # Git 忽略文件配置
├── package.json                      # 项目依赖和脚本命令定义
├── package-lock.json                 # 依赖版本锁定文件
├── tsconfig.json                     # TypeScript 编译配置
├── vite.config.ts                    # Vite 构建工具配置文件
└── README.md                         # 项目说明文件（即本文档）
```

## 贡献指南

我们欢迎并感谢任何形式的贡献，包括但不限于提交问题报告、功能建议、代码修复、文档改进和新功能开发。请遵循以下步骤参与本项目贡献。

首先在 GitHub 上 Fork 本仓库到您的个人账户，然后将 Fork 后的仓库克隆到本地开发环境中。建议在开发前阅读 docs/development.md 文档，了解项目的技术架构和开发规范。

其次创建一个新的功能分支，分支命名规范为 feature/功能简述 或 fix/问题简述，例如 feature/add-import-json 或 fix/search-case-sensitive。请确保分支名称能够清晰表达本次变更的目的。

接着在本地进行代码修改和功能开发，提交代码时请遵循 Conventional Commits 规范，提交信息格式为 type(scope): subject，例如 feat(search): add fuzzy matching support。提交前请运行 npm run lint 和 npm run test 确保代码风格和测试用例通过。

最后将本地分支推送到您 Fork 的远程仓库，然后通过 GitHub 界面发起 Pull Request 到本仓库的 main 分支。Pull Request 描述中请详细说明变更内容、测试方法和影响范围，并关联相关的 Issue 编号（如有）。项目维护者会在收到 Pull Request 后进行代码审查，并在必要时提出修改意见，合并后您的贡献将被列入项目贡献者列表。

## 常见问题

问：启动开发服务器时提示端口被占用，如何解决？

答：当默认端口 3000 被其他进程占用时，可以通过两种方式解决。一是在项目根目录下的 .env 文件中设置 PORT 环境变量为其他可用端口，例如 PORT=3001。二是在启动命令中直接指定端口，执行 npm run dev -- --port 3001。如果仍然

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:15
