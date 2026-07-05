# WebLink Navigator

WebLink Navigator 是一个面向开发者和技术研究人员的轻量级外链资源聚合与导航系统。该项目旨在解决个人或团队在浏览、整理和复用分散于多个平台的碎片化技术文章、工具文档和参考链接时缺乏统一入口与检索手段的问题。通过将外部 URL 资源与本地元数据标签体系关联，WebLink Navigator 提供了一套可自托管的链接仓库管理方案，适用于需要长期维护技术书签库、构建个人知识体系或搭建团队公用资源面板的场景。

本项目不依赖任何重型前端框架或数据库系统，核心设计基于静态 Markdown 与 JSON 索引，配合轻量级 HTTP 服务实现资源的快速检索与分类浏览。目标用户包括但不限于开源贡献者、技术博主、运维工程师以及需要频繁查阅外部技术文档的研发人员。WebLink Navigator 以最小化运维成本为原则，所有资源链接以纯文本形式维护，支持通过脚本批量导入、校验去重以及生成可视化的分类目录页。

## 功能概览

**多级分类索引**：支持无限层级的资源分类目录，每个分类可关联描述文本与图标标识，便于按技术栈、业务域或阅读状态进行分组管理。

**全文元数据检索**：基于标题、来源域名、添加日期和自定义标签对链接进行快速过滤，检索结果按匹配度排序并高亮关键词。

**链接健康状态检测**：内置异步 HTTP 探活模块，可定期检查已收录资源的可达性，对返回 4xx 或 5xx 状态码的链接输出告警日志。

**批量导入与去重**：支持通过命令行参数或 CSV 文件批量添加 URL，导入过程中自动基于标准化后的 URL 字符串进行去重，避免重复录入。

**静态站点生成模式**：提供 `build` 命令将当前资源库渲染为一组静态 HTML 页面，可直接托管至 Nginx、Caddy 或 GitHub Pages，无需运行时服务。

**自定义标签与备注**：每个链接条目可附加多个自定义标签（如 `#backend`、`#tutorial`、`#zh-CN`）以及不超过 500 字的备注说明，用于记录阅读心得或使用注意事项。

**导出与备份机制**：支持将全量资源数据导出为 JSON 或 YAML 格式，便于迁移至其他工具或进行版本控制备份。

## 应用场景

**个人技术书签库的长期维护**：开发者可以将日常浏览中遇到的优质博客、API 文档、在线工具和视频教程统一收录到 WebLink Navigator 中，按语言、框架或难度等级分类。配合定期健康检查，能够及时清理失效链接，保持书签库的可用性。

**团队内部公共资源面板**：技术团队可使用该工具搭建一个只读的团队资源门户，集中存放运维手册、设计规范、项目脚手架地址和内网监控面板链接。通过静态站点生成模式，可将该面板部署到内部服务器，供全体成员随时查阅，减少重复问答。

**离线文档资源索引中心**：对于需要频繁查阅多份离线 PDF、本地 API 文档或内部 Wiki 页面的场景，WebLink Navigator 支持 `file://` 协议链接的收录，能够构建统一的本地资源入口。配合备注字段，可记录文件存放路径、版本信息和查阅优先级。

**开源项目外链引用清单管理**：开源项目维护者可以使用该工具整理项目 README、文档站点或社区 Wiki 中引用的所有外部链接，形成一份独立的外链清单。这不仅便于审计外部依赖的可用性，也方便在链接变更时快速定位并更新所有引用处。

## 快速开始

以下命令演示了从 GitHub 克隆项目、安装依赖并启动开发服务的完整流程。

```bash
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator
npm install
npm run serve
```

执行上述命令后，服务默认监听 `http://127.0.0.1:3000`。访问该地址即可进入 Web 管理界面，通过界面右上角的「添加链接」按钮或使用命令行工具 `./bin/add-link` 开始收录资源。如需生成静态站点，请执行 `npm run build`，产物将输出至 `dist/` 目录。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | >= 18.12.0 | 运行时环境，推荐使用 LTS 版本 |
| npm | >= 8.19.0 | 包管理器，用于安装项目依赖 |
| Git | >= 2.30.0 | 用于克隆仓库及版本管理 |
| curl 或 wget | 任意稳定版 | 可选，用于远程资源探活模块 |
| 文件系统读写权限 | 对安装目录具有 rwx 权限 | 用于存储索引 JSON 文件和静态资源缓存 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户指南 | `docs/guide/getting-started.md` | 如何安装、配置并启动第一个资源导航实例？ |
| 用户指南 | `docs/guide/link-management.md` | 如何添加、编辑、删除和分类链接？有哪些批量操作方式？ |
| 运维手册 | `docs/ops/health-check.md` | 如何配置链接健康检查的周期与告警策略？ |
| 运维手册 | `docs/ops/static-deploy.md` | 如何将导航站点部署为纯静态服务？支持哪些 Web 服务器？ |
| 开发者文档 | `docs/dev/api-usage.md` | 内部 JSON 索引的数据结构是怎样的？如何通过脚本读写？ |
| 开发者文档 | `docs/dev/contributing.md` | 如何提交代码、报告缺陷或建议新特性？ |

## 资源列表

- http://h5.mobile.fuvxie.cn/Article/details/913835.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/52176.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/6070645.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/5043327.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/5858503.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/94603.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/1478649.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/1323.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/739214.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/59865.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/6988803.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/325054.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/0709.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/4089.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/7305591.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/09160.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/45608.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/4967.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/0309546.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/7754.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/2954.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/3545377.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/987805.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/86196.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/07121.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/3237271.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/4490.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/4715.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/1230.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/8956.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/72192.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/7534795.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/204483.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/2633033.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/1285347.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/723218.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/07737.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/1723685.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/2828478.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/341675.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/057379.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/23618.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/893259.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/05825.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/131430.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/048831.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/77623.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/8966.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/3595419.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/24081.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/2831.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/614279.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/9225.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/9954.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/6088636.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/4403554.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/083545.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/147708.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/72549.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/0739.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/45923.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/4347278.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/507951.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/87735.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/974104.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/014585.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/950424.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/99875.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/2534.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/2062524.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/22902.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/9824227.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/0357.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/1264.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/284352.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/40554.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/384009.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/0929526.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/40845.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/6331956.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/171796.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/4134.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/7863593.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/377407.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/970964.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/2604499.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/516949.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/3281819.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/75126.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/8547.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/2659.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/72031.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/7194.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/7427.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/9943.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/160732.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/41467.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/1333.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/7357837.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/6028.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/380065.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/1414613.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/550020.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/9251401.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/268270.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/3282520.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/168832.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/3238.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/1216697.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/440275.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/0107.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/6878817.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/516763.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/7071.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/6125.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/5122008.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/6054564.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/2116786.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/2271517.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/6067.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/8346542.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/6762.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/627479.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/03282.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/83756.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/7681251.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/706931.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/9504.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/79838.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/7599.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/8972388.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/446083.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/595979.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/3142652.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/835228.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/2944990.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/14363.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/8299.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/6732.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/0147.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/9689786.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/86449.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/328749.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/0693.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/66660.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/13696.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/9242667.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/527884.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/9464.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/45749.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/5643968.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/5695249.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/735461.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/583040.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/146138.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/8927852.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/439392.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/588235.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/0749.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/5069129.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/064762.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/4194948.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/56403.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/6295.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/4856.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/8007369.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/0139.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/9962049.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/35182.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/24117.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/8999110.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/236183.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/2727201.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/363835.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/229209.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/0550.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/5865.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/72669.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/4239240.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/68371.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/7405.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/4397364.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/69258.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/8011677.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/687955.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/5492.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/5149.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/99332.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/282889.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/3570.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/4665041.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/99831.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/38317.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/926039.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/5425.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/9597.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/09940.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/1424.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/5848433.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/69822.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/20659.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/9214.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/863393.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/3040654.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/041979.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/1379.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/221606.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/6446050.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/80079.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/884952.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/7836.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/259669.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/727264.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/43907.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/8082859.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/6618667.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/904681.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/8213181.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/09523.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/0815039.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/65753.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/124060.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/8924543.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/994754.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/57792.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/2332.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/85149.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/41353.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/41854.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/03832.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/3624.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/5355786.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/0603.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/9793.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/7708522.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/94128.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/6218280.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/139139.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/27033.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/7060.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/0422231.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/2257547.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/7111.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/5146.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/4749497.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/04354.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/24892.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/03769.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/2914.sHtML
- http://h5.mobile.fuvxie.cn/Article/details/44778.sHtML

## 项目结构

```
weblink-navigator/
├── bin/                                # 命令行入口脚本
│   ├── add-link                        # 添加单条链接的交互式脚本
│   ├── batch-import                    # 批量导入 CSV 或 JSON 数据
│   └── health-check                    # 触发全量链接健康检查
├── config/                             # 配置文件目录
│   ├── default.yaml                    # 默认配置（端口、缓存路径、探活超时）
│   └── schema.json                     # 配置项的 JSON Schema 校验文件
├── docs/                               # 完整项目文档
│   ├── guide/                          # 用户指南
│   ├── ops/                            # 运维手册
│   └── dev/                            # 开发者文档
├── src/                                # 核心源码
│   ├── core/                           # 索引读写、去重、校验核心模块
│   ├── server/                         # HTTP 服务与路由定义
│   ├── static/                         # 静态站点生成器
│   └── utils/                          # 通用工具函数（日志、HTTP 客户端等）
├── tests/                              # 单元测试与集成测试用例
│   ├── unit/                           # 单元测试
│   └── fixtures/                       # 测试用的样例数据
├── data/                               # 运行时数据目录（用户资源索引）
│   ├── index.json                      # 主索引文件，存储所有链接元数据
│   └── cache/                          # 健康检查结果缓存
├── public/                             # Web 界面静态资源
│   ├── css/                            # 样式表
│   ├── js/                             # 前端交互脚本
│   └── index.html                      # 管理面板入口页面
├── .eslintrc.js                        # ESLint 代码规范配置
├── .gitignore                          # Git 忽略文件列表
├── package.json                        # npm 项目描述与依赖声明
├── README.md                           # 项目说明文档（本文件）
└── LICENSE                             # MIT 许可证文本
```

## 贡献指南

1. 在 GitHub 仓库的 Issue 列表中查找未被指派的待办事项，或提交新 Issue 描述您希望修复的缺陷或新增的特性。等待维护者确认需求可行性后再进行开发，以避免无效工作。

2. 将本仓库复刻（Fork）至您的个人账户下，在复刻仓库中创建一个新的功能分支，分支命名规则为 `feature/简短描述` 或 `fix/缺陷编号`。请确保分支基于最新的 `main` 分支创建。

3. 完成代码修改后，运行 `npm run test` 确保所有现有测试用例通过。如果新增了功能，请同步补充对应的单元测试或集成测试用例，测试覆盖率不得低于现有基线。同时，请更新 `docs/` 目录下相关的文档内容。

4. 提交代码时请遵循 Conventional Commits 规范，提交信息格式为 `<类型>(<范围>): <简短描述>`，例如 `feat(core): 添加链接批量导出为 YAML 格式`。提交前请执行 `npm run lint` 进行代码风格检查。

5. 向原仓库的 `main` 分支发起 Pull Request，并在 PR 描述中清晰关联对应的 Issue 编号，概述实现方案和测试结果。PR 将由项目维护者进行 Code Review，通过后即可合并。

## 常见问题

**问：WebLink Navigator 是否支持私有仓库或需要身份认证的外部链接？**

答：本项目本身不存储任何外部链接的认证凭据或会话信息。对于需要登录才能访问的资源，您可以在备注字段中记录访问方式（如内部 VPN 地址、SSH 隧道命令或团队共享账号的提示信息），但系统本身不提供代理转发或 Cookie 管理功能。建议将敏感链接与公开链接分目录存放，并利用静态站点生成模式将面板部署在内网环境。

**问：收录的链接数量超过一万条时，系统性能是否会显著下降？**

答：索引数据基于 JSON 文件存储，单文件大小与链接条目数成正比。对于一万条链接，索引文件大小约为 2 至 4 MB，内存占用和检索响应时间仍在可接受范围内。如果条目数超过五万条，建议启用 `data/cache/` 目录下的分片存储模式（需修改配置文件），或定期导出旧数据至归档文件，仅保留近期活跃链接在主索引中。健康检查模块默认采用并发探活，并发数可在配置文件中调整，以避免网络带宽或文件描述符耗尽。

**问：如何将现有浏览器书签或 Pinboard、Raindrop.io 等第三方服务的数据迁移到 WebLink Navigator？**

答：项目提供了一个独立的迁移脚本 `bin/migrate`，支持导入 Netscape HTML 书签导出格式（所有主流浏览器均支持导出）、Raindrop.io 的 CSV 导出以及 Pinboard 的 JSON 备份。执行 `bin/migrate --help` 可查看详细的参数说明。对于未提供直接导入格式的服务，建议先将其数据导出为 CSV，再使用 `bin/batch-import --csv`

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:14
