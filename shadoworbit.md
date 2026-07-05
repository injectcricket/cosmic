# WebLink Navigator

WebLink Navigator 是一个面向技术调研、内容聚合与知识管理场景的轻量化外链资源汇总与导航系统。该项目定位于帮助开发团队、技术内容运营者以及个人研究员，对分散在多个来源的 URL 资源进行统一收录、分类展示与快速检索，降低链接遗忘与信息碎片化带来的管理成本。

项目本身不依赖数据库，采用纯静态 Markdown 与 HTML 混合架构，所有外链资源通过结构化文档进行集中维护，支持一键生成可部署的导航页面。目标用户包括开源文档维护者、技术社区运营人员、企业知识库管理员以及需要长期跟踪大量参考链接的研发人员。

## 功能概览

**批量链接收录**：支持将大量原始 URL 以列表形式直接导入系统，自动识别链接格式并生成标准化条目。

**分类标签生成**：根据 URL 路径特征与来源域名自动生成分类标签，便于按主题浏览。

**全文检索支持**：内置简单的关键词匹配机制，可通过页面搜索快速定位目标链接。

**收录批次追踪**：每一批资源入库均记录批次编号与收录时间，便于追溯与更新。

**资源状态标记**：每个链接可标注为有效、待验证或失效三种状态，辅助链接健康度管理。

**页面模板渲染**：提供响应式 HTML 模板，可将链接列表渲染为适合桌面与移动设备浏览的导航页面。

**导出与备份**：支持将当前链接列表导出为纯文本格式或 CSV 文件，便于离线备份与迁移。

## 应用场景

技术文档团队维护外部参考链接库。文档撰写过程中需要引用大量第三方资料、规范文档与工具主页，使用 WebLink Navigator 可以集中管理这些引用来源，并在文档更新时快速核对链接有效性。

开源项目聚合社区资源。开源项目维护者可以将相关的教程文章、视频讲解、周边工具和镜像站链接统一收录，为新用户提供一站式的学习与入门路径。

企业内部知识库的外链治理。企业内部的 Confluence 或 Notion 知识库中往往散落着大量外部链接，通过本系统可以定期汇总并审查这些链接的可用性，防止知识库中出现大量死链。

技术培训与课程资料配套。培训讲师可以将课程中涉及的所有参考文章、代码仓库和在线工具的链接整理为导航页，学员无需自行搜索，直接通过导航页访问全部资源。

## 快速开始

以下命令演示了如何从 GitHub 克隆项目、安装依赖并启动本地开发服务。

```bash
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator
npm install
npm run build
npm start
```

若使用 yarn 作为包管理器，可替换为：

```bash
yarn install
yarn build
yarn start
```

项目默认启动在 localhost:3000，访问后可看到示例导航页面。如需加载自定义链接列表，请将资源文件放入 `data/links` 目录并执行 `npm run refresh`。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 16.0.0 或更高 | 运行时环境，用于构建与启动服务 |
| npm | 8.0.0 或更高 | 包管理器，用于安装项目依赖 |
| Git | 2.30.0 或更高 | 版本控制工具，用于克隆仓库 |
| Markdown 解析器 | 内置 | 项目自带 markdown-it 作为解析引擎 |
| 操作系统 | Linux / macOS / Windows | 跨平台支持，Windows 下建议使用 WSL2 环境 |
| 浏览器 | 现代浏览器（Chrome / Firefox / Edge） | 用于访问生成的导航页面 |
| 磁盘空间 | 至少 50 MB | 用于存放源码、依赖与生成的静态文件 |
| 内存 | 至少 512 MB | 构建过程的内存需求 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | /docs/user-guide.md | 如何添加链接、生成页面、导出数据 |
| 配置参考 | /docs/config-reference.md | 项目配置文件各字段的含义与示例 |
| API 接口 | /docs/api.md | 如果启用服务端模式，提供哪些接口 |
| 贡献指南 | /CONTRIBUTING.md | 如何参与项目开发与提交改进 |
| 更新日志 | /CHANGELOG.md | 每个版本新增了哪些特性与修复 |
| 设计文档 | /docs/design.md | 系统的整体架构与设计决策 |

## 资源列表

- http://www.mobile.cvsifc.cn/Article/details/859893.sHtML
- http://www.mobile.cvsifc.cn/Article/details/082007.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3852.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8099.sHtML
- http://www.mobile.cvsifc.cn/Article/details/92426.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5014.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7923.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4719.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3591524.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8715371.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9664189.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5284.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7069313.sHtML
- http://www.mobile.cvsifc.cn/Article/details/46592.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7076949.sHtML
- http://www.mobile.cvsifc.cn/Article/details/03473.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0967819.sHtML
- http://www.mobile.cvsifc.cn/Article/details/928681.sHtML
- http://www.mobile.cvsifc.cn/Article/details/474290.sHtML
- http://www.mobile.cvsifc.cn/Article/details/28456.sHtML
- http://www.mobile.cvsifc.cn/Article/details/67877.sHtML
- http://www.mobile.cvsifc.cn/Article/details/529835.sHtML
- http://www.mobile.cvsifc.cn/Article/details/283561.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4769.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1281933.sHtML
- http://www.mobile.cvsifc.cn/Article/details/019010.sHtML
- http://www.mobile.cvsifc.cn/Article/details/37214.sHtML
- http://www.mobile.cvsifc.cn/Article/details/676790.sHtML
- http://www.mobile.cvsifc.cn/Article/details/93881.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6764422.sHtML
- http://www.mobile.cvsifc.cn/Article/details/115189.sHtML
- http://www.mobile.cvsifc.cn/Article/details/375944.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3857.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8392110.sHtML
- http://www.mobile.cvsifc.cn/Article/details/77711.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1810135.sHtML
- http://www.mobile.cvsifc.cn/Article/details/10336.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5268817.sHtML
- http://www.mobile.cvsifc.cn/Article/details/00508.sHtML
- http://www.mobile.cvsifc.cn/Article/details/68824.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7862.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6204268.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5791113.sHtML
- http://www.mobile.cvsifc.cn/Article/details/744225.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1342.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0742.sHtML
- http://www.mobile.cvsifc.cn/Article/details/678881.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8912.sHtML
- http://www.mobile.cvsifc.cn/Article/details/730105.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6044789.sHtML
- http://www.mobile.cvsifc.cn/Article/details/50076.sHtML
- http://www.mobile.cvsifc.cn/Article/details/25679.sHtML
- http://www.mobile.cvsifc.cn/Article/details/439804.sHtML
- http://www.mobile.cvsifc.cn/Article/details/745880.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4490.sHtML
- http://www.mobile.cvsifc.cn/Article/details/84499.sHtML
- http://www.mobile.cvsifc.cn/Article/details/81391.sHtML
- http://www.mobile.cvsifc.cn/Article/details/745774.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4249174.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1608045.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1728.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1402.sHtML
- http://www.mobile.cvsifc.cn/Article/details/33382.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9627291.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7528.sHtML
- http://www.mobile.cvsifc.cn/Article/details/72199.sHtML
- http://www.mobile.cvsifc.cn/Article/details/77112.sHtML
- http://www.mobile.cvsifc.cn/Article/details/04676.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2832.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3602.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2780.sHtML
- http://www.mobile.cvsifc.cn/Article/details/821886.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3131.sHtML
- http://www.mobile.cvsifc.cn/Article/details/80250.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4214693.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9531863.sHtML
- http://www.mobile.cvsifc.cn/Article/details/055174.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2928229.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2880284.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5259.sHtML
- http://www.mobile.cvsifc.cn/Article/details/868132.sHtML
- http://www.mobile.cvsifc.cn/Article/details/77387.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3942.sHtML
- http://www.mobile.cvsifc.cn/Article/details/871298.sHtML
- http://www.mobile.cvsifc.cn/Article/details/72235.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9705.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0029486.sHtML
- http://www.mobile.cvsifc.cn/Article/details/84989.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5755742.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2817.sHtML
- http://www.mobile.cvsifc.cn/Article/details/793551.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2061164.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0804547.sHtML
- http://www.mobile.cvsifc.cn/Article/details/766011.sHtML
- http://www.mobile.cvsifc.cn/Article/details/180359.sHtML
- http://www.mobile.cvsifc.cn/Article/details/680609.sHtML
- http://www.mobile.cvsifc.cn/Article/details/60029.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6827562.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5578033.sHtML
- http://www.mobile.cvsifc.cn/Article/details/13427.sHtML
- http://www.mobile.cvsifc.cn/Article/details/088943.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9003227.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1966897.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4156633.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1599955.sHtML
- http://www.mobile.cvsifc.cn/Article/details/39973.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4013.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3194284.sHtML
- http://www.mobile.cvsifc.cn/Article/details/11899.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4888.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7629.sHtML
- http://www.mobile.cvsifc.cn/Article/details/06456.sHtML
- http://www.mobile.cvsifc.cn/Article/details/35360.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1281703.sHtML
- http://www.mobile.cvsifc.cn/Article/details/14727.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4440624.sHtML
- http://www.mobile.cvsifc.cn/Article/details/753896.sHtML
- http://www.mobile.cvsifc.cn/Article/details/80337.sHtML
- http://www.mobile.cvsifc.cn/Article/details/314026.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5801038.sHtML
- http://www.mobile.cvsifc.cn/Article/details/152111.sHtML
- http://www.mobile.cvsifc.cn/Article/details/074946.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1781.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7935436.sHtML
- http://www.mobile.cvsifc.cn/Article/details/382348.sHtML
- http://www.mobile.cvsifc.cn/Article/details/947382.sHtML
- http://www.mobile.cvsifc.cn/Article/details/01864.sHtML
- http://www.mobile.cvsifc.cn/Article/details/39966.sHtML
- http://www.mobile.cvsifc.cn/Article/details/915746.sHtML
- http://www.mobile.cvsifc.cn/Article/details/759923.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2015381.sHtML
- http://www.mobile.cvsifc.cn/Article/details/15749.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3088.sHtML
- http://www.mobile.cvsifc.cn/Article/details/54005.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3624790.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0263502.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4515.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4334.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4113.sHtML
- http://www.mobile.cvsifc.cn/Article/details/51776.sHtML
- http://www.mobile.cvsifc.cn/Article/details/694404.sHtML
- http://www.mobile.cvsifc.cn/Article/details/55560.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4077305.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2435.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0852510.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4364.sHtML
- http://www.mobile.cvsifc.cn/Article/details/57516.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9629724.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1714673.sHtML
- http://www.mobile.cvsifc.cn/Article/details/75348.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7092.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2192042.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7853629.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4809640.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5353244.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7531.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5348.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6367.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0330.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8530.sHtML
- http://www.mobile.cvsifc.cn/Article/details/391391.sHtML
- http://www.mobile.cvsifc.cn/Article/details/18426.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6968.sHtML
- http://www.mobile.cvsifc.cn/Article/details/09361.sHtML
- http://www.mobile.cvsifc.cn/Article/details/96087.sHtML
- http://www.mobile.cvsifc.cn/Article/details/37110.sHtML
- http://www.mobile.cvsifc.cn/Article/details/90720.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8124784.sHtML
- http://www.mobile.cvsifc.cn/Article/details/55716.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4795960.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4241749.sHtML
- http://www.mobile.cvsifc.cn/Article/details/70304.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8431.sHtML
- http://www.mobile.cvsifc.cn/Article/details/613575.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0407.sHtML
- http://www.mobile.cvsifc.cn/Article/details/809906.sHtML
- http://www.mobile.cvsifc.cn/Article/details/33514.sHtML
- http://www.mobile.cvsifc.cn/Article/details/967500.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1779999.sHtML
- http://www.mobile.cvsifc.cn/Article/details/197111.sHtML
- http://www.mobile.cvsifc.cn/Article/details/413450.sHtML
- http://www.mobile.cvsifc.cn/Article/details/72167.sHtML
- http://www.mobile.cvsifc.cn/Article/details/52688.sHtML
- http://www.mobile.cvsifc.cn/Article/details/920633.sHtML
- http://www.mobile.cvsifc.cn/Article/details/76848.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8746.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1120.sHtML
- http://www.mobile.cvsifc.cn/Article/details/45786.sHtML
- http://www.mobile.cvsifc.cn/Article/details/648751.sHtML
- http://www.mobile.cvsifc.cn/Article/details/122051.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7920.sHtML
- http://www.mobile.cvsifc.cn/Article/details/031473.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1706507.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2989.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3452.sHtML
- http://www.mobile.cvsifc.cn/Article/details/503574.sHtML
- http://www.mobile.cvsifc.cn/Article/details/357692.sHtML
- http://www.mobile.cvsifc.cn/Article/details/615855.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9498887.sHtML
- http://www.mobile.cvsifc.cn/Article/details/29579.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7140833.sHtML
- http://www.mobile.cvsifc.cn/Article/details/334717.sHtML
- http://www.mobile.cvsifc.cn/Article/details/872154.sHtML
- http://www.mobile.cvsifc.cn/Article/details/68415.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4546.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1449454.sHtML
- http://www.mobile.cvsifc.cn/Article/details/88390.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0648255.sHtML
- http://www.mobile.cvsifc.cn/Article/details/53118.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7814.sHtML
- http://www.mobile.cvsifc.cn/Article/details/465045.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1033.sHtML
- http://www.mobile.cvsifc.cn/Article/details/557496.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4481621.sHtML
- http://www.mobile.cvsifc.cn/Article/details/97201.sHtML
- http://www.mobile.cvsifc.cn/Article/details/828221.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3248.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4965.sHtML
- http://www.mobile.cvsifc.cn/Article/details/182001.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2043.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0592.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4510131.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4860.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6668.sHtML
- http://www.mobile.cvsifc.cn/Article/details/70480.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7420.sHtML
- http://www.mobile.cvsifc.cn/Article/details/101869.sHtML
- http://www.mobile.cvsifc.cn/Article/details/721489.sHtML
- http://www.mobile.cvsifc.cn/Article/details/02479.sHtML
- http://www.mobile.cvsifc.cn/Article/details/44723.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4341385.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0169305.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1953.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7329260.sHtML
- http://www.mobile.cvsifc.cn/Article/details/699779.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2080.sHtML
- http://www.mobile.cvsifc.cn/Article/details/55794.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8494575.sHtML
- http://www.mobile.cvsifc.cn/Article/details/023356.sHtML
- http://www.mobile.cvsifc.cn/Article/details/519264.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5188250.sHtML
- http://www.mobile.cvsifc.cn/Article/details/272770.sHtML
- http://www.mobile.cvsifc.cn/Article/details/434167.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4803.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8901444.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6740789.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4364886.sHtML
- http://www.mobile.cvsifc.cn/Article/details/10892.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0304900.sHtML
- http://www.mobile.cvsifc.cn/Article/details/646248.sHtML

## 项目结构

```
weblink-navigator/
├── src/                                # 源代码主目录
│   ├── core/                           # 核心处理模块
│   │   ├── linkParser.js               # URL 解析与验证逻辑
│   │   ├── batchManager.js             # 批次管理与追踪
│   │   └── statusChecker.js            # 链接有效性检查
│   ├── render/                         # 渲染引擎
│   │   ├── markdownRenderer.js         # Markdown 转 HTML 渲染器
│   │   ├── templateEngine.js           # 页面模板引擎
│   │   └── assetPipeline.js            # 静态资源处理
│   ├── cli/                            # 命令行入口
│   │   ├── index.js                    # CLI 主入口
│   │   ├── commands/                   # 子命令实现
│   │   │   ├── build.js                # 构建命令
│   │   │   ├── serve.js                # 服务启动命令
│   │   │   └── refresh.js              # 刷新链接列表命令
│   │   └── utils/                      # CLI 辅助工具
│   └── shared/                         # 跨模块共享代码
│       ├── constants.js                # 全局常量定义
│       ├── validators.js               # 通用校验函数
│       └── logger.js                   # 日志记录器
├── data/                               # 数据目录
│   ├── links/                          # 链接数据存储
│   │   ├── batch_125.json              # 第125批次链接数据
│   │   └── batch_126.json              # 第126批次链接数据
│   └── cache/                          # 缓存文件
│       └── statusCache.json            # 链接状态缓存
├── docs/                               # 项目文档
│   ├── user-guide.md                   # 用户手册
│   ├── config-reference.md             # 配置参考
│   ├── api.md                          # API 文档
│   └── design.md                       # 设计文档
├── public/                             # 静态资源目录
│   ├── css/                            # 样式文件
│   │   ├── main.css                    # 主样式
│   │   └── theme.css                   # 主题变量
│   ├── js/                             # 前端脚本
│   │   ├── search.js                   # 搜索功能
│   │   └── filter.js                   # 筛选功能
│   └── assets/                         # 图片与其他资源
│       └── logo.svg                    # 项目标识
├── tests/                              # 单元测试
│   ├── core/                           # 核心模块测试
│   ├── render/                         # 渲染模块测试
│   └── cli/                            # CLI 测试
├── .github/                            # GitHub 配置
│   └── workflows/                      # CI/CD 工作流
│       ├── ci.yml                      # 持续集成配置
│       └── deploy.yml                  # 部署配置
├── package.json                        # npm 项目配置
├── package-lock.json                   # 依赖锁定文件
├── .eslintrc.js                        # ESLint 代码检查配置
├── .prettierrc                         # Prettier 代码格式化配置
├── .gitignore                          # Git 忽略文件列表
├── LICENSE                             # MIT 许可证
├── README.md                           # 项目说明文档
└── CHANGELOG.md                        # 版本更新日志
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库到个人账户，然后 clone 到本地开发环境。请确保本地 Node.js 版本满足安装要求。

2. 创建一个新的分支用于您的修改，分支名称应简洁描述修改内容，例如 `fix-link-parser` 或 `add-export-feature`。请不要在 main 分支上直接修改。

3. 完成代码修改后，请确保所有单元测试通过。运行 `npm test` 执行测试套件，若新增功能请同步添加对应的测试用例。

4. 提交代码前运行 `npm run lint` 和 `npm run format` 以统一代码风格。提交信息请遵循 Conventional Commits 规范，使用 `feat:`、`fix:`、`docs:` 等前缀。

5. 推送分支到您的 fork 仓库，然后通过 GitHub 界面发起 Pull Request 到主仓库的 main 分支。PR 描述中请清晰说明修改目的与影响范围，并关联相关 issue 编号。

## 常见问题

**Q：项目是否必须联网才能使用？**

A：项目核心功能完全离线可用。所有链接数据存储在本地 JSON 文件中，页面生成与渲染不依赖外部网络。唯一的例外是链接有效性检查功能，若开启实时检查则需要网络访问以验证目标地址是否可访问。您可以选择关闭该功能，仅维护链接列表本身。

**Q：如何导入历史遗留的大量 URL 列表？**

A：项目提供了批量导入工具。您可以将 URL 列表按行存放在一个纯文本文件中，每行一个 URL，然后执行 `npm run import -- --file=your-list.txt`。导入工具会自动去重、校验格式并生成对应的批次 JSON 文件。如果您有 CSV 或 Excel 格式的数据，建议先转换为纯文本格式再导入。

**Q：生成的导航页面能否部署到静态托管服务？**

A：可以。运行 `npm run build` 后，所有静态文件会输出到 `dist` 目录，该目录包含完整的 HTML、CSS 与 JavaScript 文件。您可以将 `dist` 目录的内容部署到任何支持静态文件托管的平台，如 GitHub Pages、Netlify、Vercel 或任何 Nginx / Apache 服务器。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:15
