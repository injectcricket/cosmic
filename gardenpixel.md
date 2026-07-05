# WebLink Navigator

WebLink Navigator 是一个面向技术内容聚合与知识导航的开源项目，旨在为开发者、技术写作者以及信息检索人员提供结构化的外链资源归集方案。本项目并非简单的书签管理工具，而是一套围绕 URL 元数据组织、分类索引与快速访问设计的轻量级静态站点生成框架。其核心定位是帮助技术团队或个人将散落在各处的优质外链文章、文档与工具地址，统一整理为可检索、可分享、可版本控制的资源清单，从而降低信息流失与重复查找的损耗。

目标用户包括但不限于：维护技术周报的编辑、构建知识库的文档工程师、梳理学习路径的教研人员，以及希望将浏览器收藏夹转化为结构化资产的中高级开发者。WebLink Navigator 不依赖数据库，所有资源数据以 Markdown 或 YAML 文件存储，便于集成到现有的 CI/CD 工作流中，并支持导出为 JSON、HTML 或 CSV 格式，以便嵌入其他平台。

## 功能概览

- **批量 URL 导入与去重**：支持从文本文件、CSV 或浏览器书签导出文件中批量导入链接，并基于域名与路径进行智能去重，避免冗余条目。

- **多维度分类标签系统**：允许为每个链接分配多个标签（如 "backend"、"tutorial"、"api"），并支持创建层级目录结构，实现按主题、难度或项目阶段的多角度索引。

- **全文检索与过滤**：内置基于标题、描述、标签及路径关键词的模糊搜索功能，配合按域名、文件类型或更新时间范围的过滤器，帮助用户在海量链接中快速定位目标。

- **自动化元数据抓取**：在导入或刷新时，可自动请求目标 URL 并提取页面标题、元描述及响应状态码，用于验证链接有效性并补充概要信息。

- **静态站点生成与导出**：提供内置模板引擎，支持将资源列表渲染为响应式 HTML 文档，便于部署为内部知识门户或公开技术导航站；同时支持导出为纯 Markdown 表格或 JSON API 格式。

- **链接健康检查与报告**：定期或手动触发对已存 URL 的 HEAD/GET 请求，检测 HTTP 状态变化，生成失效链接报告，并支持标记为 "待复查" 或 "已归档"。

- **版本化变更记录**：每次增删改操作均写入变更日志文件，配合 Git 提交历史，可追溯任意时间点的资源集合状态，便于团队协作审核。

## 应用场景

**技术团队内部知识库维护**  
技术团队在项目迭代中会积累大量参考文档、设计稿链接和运维手册地址。使用 WebLink Navigator 可以将这些分散于聊天记录或个人便签的 URL 统一收录，并按微服务、前端、数据库等模块分类，新成员入职时即可通过导航树快速了解项目相关资源全貌。

**技术博客与周报素材管理**  
技术内容创作者在撰写周报或专题文章时，需要频繁引用外部资讯、开源项目发布页或性能测试报告。该工具可作为素材暂存池，通过标签标记阅读状态（待读/已读/引用），并一键生成引用列表，极大缩短稿件编排时间。

**开源项目文档外链整合**  
开源项目的 README 或官网常常需要列举依赖库、学习资料、社区论坛等外部链接。随着项目发展，这些链接可能变动或失效。WebLink Navigator 提供链接健康检查能力，维护者定期运行检查即可发现死链，保持文档质量。

**技术培训课程资源包构建**  
培训机构或企业大学在准备技术课程时，需要为学生提供课前预习、课后拓展和实验手册等大量参考链接。本工具支持按课程阶段（基础/进阶/实战）建立目录，并为每个链接添加难度等级和预估阅读时长，方便学员自主安排学习节奏。

## 快速开始

以下命令演示了从克隆仓库到启动本地服务的完整流程。请确保系统已安装 Git 和 Node.js（v16 及以上）。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-navigator/weblink-navigator.git

# 进入项目根目录
cd weblink-navigator

# 安装项目依赖（使用 npm）
npm install

# 构建核心模块并生成初始资源索引
npm run build

# 启动开发服务器，默认监听 3000 端口
npm start
```

执行完成后，访问控制台输出的本地地址（通常为 http://localhost:3000 ）即可看到资源导航界面。首次启动会自动创建示例数据目录 `./data/links`，您可以直接在该目录下添加或编辑 Markdown 文件来管理链接。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | v16.20.0 及以上 | 运行时环境，用于执行构建脚本与开发服务器 |
| npm | v8.0.0 及以上 | 包管理器，用于安装依赖与运行脚本命令 |
| Git | v2.25.0 及以上 | 版本控制工具，用于克隆仓库及提交变更记录 |
| 操作系统 | Linux (glibc 2.28+), macOS (10.15+), Windows (10+ with WSL) | 支持主流 POSIX 环境及 Windows 子系统 |
| 网络访问 | 出站 HTTPS/HTTP 可达 | 用于元数据抓取及健康检查功能，需允许访问目标 URL 的 80/443 端口 |
| 磁盘空间 | 至少 200 MB 可用 | 存储源码、依赖包及生成的资源索引文件 |
| 内存 | 推荐 1 GB 以上 | 构建大型索引（超过 5000 条链接）时需更多内存 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide/installation.md, /docs/user-guide/import.md | 如何安装、配置、导入链接及日常使用流程 |
| 开发者指南 | /docs/developer/api-reference.md, /docs/developer/plugin-dev.md | 如何扩展数据源、自定义模板或集成第三方服务 |
| 运维参考 | /docs/operator/health-check.md, /docs/operator/deployment.md | 如何定期维护链接有效性、部署生产环境及性能调优 |
| 设计说明 | /docs/design/data-model.md, /docs/design/architecture.md | 数据存储结构、模块划分及设计决策背景 |

## 资源列表

- http://h5.mobile.hcbezg.cn/Article/details/3909081.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/858917.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8160988.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2877.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8921982.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2677656.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/248281.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/65607.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/71257.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7400894.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3635310.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9197.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6546.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/65792.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/628810.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/22999.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2097.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/831255.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6255805.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4560603.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0517752.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/859706.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9404094.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9173880.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9096257.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/995347.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5955.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6077265.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4718.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3479.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7225038.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9071032.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4802.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/773515.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/132573.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/22989.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/43753.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2050937.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/772585.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2962.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0991644.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/73274.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8847.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/903505.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0928.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/87152.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1590133.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/54175.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/13906.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/60777.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/591069.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/74109.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/299644.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7381400.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/00295.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/02254.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/10719.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/02142.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6527.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/77498.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/57758.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/01686.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4537328.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/50705.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3405.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4399.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/365506.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3761625.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/67310.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3027.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/120626.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9496345.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9831.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/387899.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6088153.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/99754.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1272827.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6021.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/541717.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5552934.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5174387.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/87577.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9032.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4796025.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/803184.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7108899.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1656.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/86772.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9575093.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5969.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0026.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/66958.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4568188.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/34976.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/74373.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/15030.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4604.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/98721.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0980.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/35008.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/88428.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/18021.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/637242.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/954702.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2477.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0276080.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/983875.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/723092.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/823217.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2462.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/15910.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/36226.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/402557.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/631629.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/837989.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9500430.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8494.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/872477.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7647517.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/954284.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/72608.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2768457.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8560296.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8439.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2301.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/311825.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8281.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9001.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/38630.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7321.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/422498.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/024932.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/263715.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/099447.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6471.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/778078.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6331.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/430560.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/08148.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3673.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8393.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/59343.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0006830.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/763594.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7203.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2384.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/371275.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/63450.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/39531.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0434.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/865377.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3598216.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5027396.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/628468.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/327140.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4627175.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/43900.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/148324.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4377.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7265534.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5447.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2774621.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/483162.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9955602.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3335.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/864436.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5579207.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9511582.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/683762.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5283.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1678601.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5134.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9445457.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/777771.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/084199.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4433257.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3005.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2086.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/660455.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4651258.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/1275655.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3436014.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/195262.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/722481.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/017656.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/557449.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/00838.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/421845.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/250094.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/340561.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/911324.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/842150.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/23811.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/64473.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7631.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3187.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/78607.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/31320.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3913136.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5598.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/39772.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/856526.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/370198.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/163443.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/65108.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5544.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/451347.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9315.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6202636.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/771574.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/317898.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/86293.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/70801.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6260.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0800886.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/09598.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/511200.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/01322.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/05813.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7713.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5094.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3578.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/883607.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/73406.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/9371.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3404.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/10793.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/2156.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/6819679.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/207160.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7038.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5643.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/52679.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/3886667.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/301131.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4137.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/8131052.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/112235.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/591936.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/102761.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/486493.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/271066.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7500650.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/4385876.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/7462973.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/0700926.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/5818.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/382865.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/108325.sHtML
- http://h5.mobile.hcbezg.cn/Article/details/92424.sHtML

## 项目结构

```
weblink-navigator/
├── src/
│   ├── core/
│   │   ├── indexer.js          # 核心索引引擎，负责扫描数据目录并构建内存索引
│   │   ├── parser.js           # 解析 Markdown 或 YAML 格式的链接条目
│   │   └── validator.js        # 校验 URL 格式与去重逻辑
│   ├── cli/
│   │   ├── commands/
│   │   │   ├── import.js       # 实现 import 命令，支持批量导入外部数据源
│   │   │   ├── check.js        # 实现 check 命令，执行链接健康检查并输出报告
│   │   │   └── build.js        # 实现 build 命令，生成静态 HTML 站点
│   │   └── runner.js           # CLI 入口路由，解析参数并调用对应命令
│   ├── server/
│   │   ├── app.js              # Express 应用实例，定义 API 路由与中间件
│   │   ├── routes/
│   │   │   ├── search.js       # 全文搜索接口 (/api/search)
│   │   │   └── links.js        # 链接 CRUD 操作接口 (/api/links)
│   │   └── static/             # 开发服务器静态资源目录（CSS、JS 前端）
│   └── templates/
│       ├── layout.hbs          # 主布局模板（Handlebars）
│       └── index.hbs           # 首页列表模板，渲染分页后的链接卡片
├── data/
│   ├── links/                  # 用户存放链接数据文件的目录（支持 .md / .yaml）
│   │   └── example/
│   │       ├── backend-tutorials.md
│   │       └── dev-tools.yaml
│   ├── cache/                  # 元数据抓取缓存（避免频繁请求目标站点）
│   └── reports/                # 健康检查报告输出目录（JSON 格式）
├── tests/
│   ├── unit/                   # 单元测试（使用 Jest）
│   └── integration/            # 集成测试（模拟 CLI 与 API 调用）
├── docs/                       # 完整文档目录（见上方导航表）
├── scripts/
│   ├── pre-commit.sh           # Git pre-commit 钩子，运行 lint 与格式检查
│   └── seed-data.sh            # 初始化示例数据脚本
├── .env.example                # 环境变量模板（端口、缓存 TTL 等配置）
├── package.json                # npm 项目清单，包含 scripts 与 dependencies
├── README.md                   # 本文件
└── LICENSE                     # MIT 许可证文本
```

## 贡献指南

1. 阅读项目行为准则与贡献者契约，确保认同社区协作规范。所有贡献者需签署开发者原创声明，确认所提交代码或文档未侵犯第三方权利。

2. 在 GitHub Issues 中查找标记为 "help wanted" 或 "good first issue" 的任务，或提出新的功能建议/缺陷报告。请使用提供的模板清晰描述问题或方案，避免重复。

3. Fork 本仓库至个人账号，创建特性分支（命名格式为 `feature/功能简述` 或 `fix/问题编号`），并在本地完成开发。提交信息应遵循 Conventional Commits 规范（如 `feat: add batch import from csv`）。

4. 编写或更新相应的单元测试与集成测试，确保代码覆盖率不低于原有水平。所有测试用例须在本地通过，并附上新增功能的用法示例文档。

5. 发起 Pull Request 至主仓库的 `main` 分支，等待至少一位维护者审核。审核通过后，代码将被合并，并自动触发 CI 流水线进行构建与部署预览。

## 常见问题

**Q：导入的链接数量较多时，首次构建索引速度很慢，如何优化？**  
A：索引速度主要受元数据抓取网络延迟影响。建议在导入时使用 `--no-fetch` 选项跳过自动抓取，仅基于本地文件字段建立索引。之后在低峰时段运行 `npm run check -- --update` 分批更新元数据。此外，可将缓存目录挂载至 tmpfs 或 SSD 存储以提升读写性能。

**Q：健康检查报告显示大量链接为 403 或 429

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:14
