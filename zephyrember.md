# NavSphere 技术外链资源聚合站

NavSphere 是一个面向技术研发与信息检索场景的轻量级外链资源汇总平台，专注于将分散在不同业务系统、文档库与知识库中的深度链接进行集中化索引与分类管理。项目定位为技术团队内部的知识导航辅助工具，帮助开发者、研究员与运维人员在大量历史文档与工单系统中快速定位有效信息入口。

本项目不提供内容存储服务，仅作为 URL 元数据索引层，通过结构化的目录树与标签体系，将原本孤立的技术文章、案例解析、问题修复记录与配置说明文档进行逻辑归集。目标用户包括但不限于技术文档维护者、质量保障工程师、系统架构师以及需要频繁查阅历史决策记录的项目管理人员。

NavSphere 的核心设计理念是轻索引、重导航、零侵入。所有外链资源均以只读方式收录，不修改原始资源的任何字段，不缓存页面副本，不追踪用户行为。项目本身基于静态 Markdown 生成，可部署于任意支持 HTTP 服务的环境，无需数据库依赖，完全符合开源软件的可审计、可自托管要求。

## 功能概览

**多层级目录索引**：支持按技术领域、业务模块、文档类型等多维度建立分类目录，每个目录节点可挂载任意数量的外链资源。

**原始链接直出**：所有收录的 URL 保持原始形态输出，不进行重定向封装、不附加跟踪参数、不修改协议与域名，确保链接行为的可预期性。

**批量导入与校验**：提供基于文本列表的批量链接导入接口，自动执行可达性校验与重复项检测，降低人工整理成本。

**标签化检索**：为每个链接赋予技术栈、业务线、文档状态等多标签，支持多标签组合筛选与模糊匹配检索。

**版本快照记录**：每次链接列表更新时自动生成变更快照，记录新增、失效与修改的条目，便于回溯审核。

**纯静态输出**：构建阶段生成完整的 HTML 与 Markdown 静态页面，无需运行时动态解析，可直接托管于对象存储或 CDN。

**权限分级视图**：支持公开视图与内部视图的双轨渲染，内部视图展示完整链接元数据，公开视图仅展示摘要信息。

## 应用场景

技术文档库的补充索引：当企业技术文档分散在 Confluence、GitLab Wiki 与外部博客平台时，NavSphere 可作为统一入口层，将各平台的深度链接按项目维度归并，减少开发者在多个系统间切换查找的时间。

历史工单与问题追踪：运维团队可将历年工单系统中的典型案例链接按故障类型、发生时间、影响范围进行重新组织，形成可快速查阅的故障知识图谱，辅助故障根因分析。

技术选型与方案对比：架构团队在评估不同中间件或云服务时，将各候选方案的官方文档、社区评测、性能测试报告链接汇总至同一目录下，便于横向对比与决策记录。

新员工技术栈引导：为新入职的研发人员提供按技术栈编排的学习资源索引，涵盖内部规范文档、核心项目仓库地址、关键服务监控面板链接，缩短上手周期。

## 快速开始

以下操作指导用户在本机完成 NavSphere 的克隆、依赖安装与服务启动。

```bash
git clone https://github.com/navsphere/navsphere.git
cd navsphere
npm install --production
npm run build
npm start
```

执行上述命令后，服务默认监听 3000 端口，访问 http://localhost:3000 即可进入索引首页。如需更改端口，可设置环境变量 PORT。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x LTS 或更高 | 运行时环境，建议使用长期支持版本 |
| npm | 9.x 或更高 | 包管理器，用于安装项目依赖 |
| Git | 2.30 或更高 | 版本控制工具，用于克隆仓库与提交更新 |
| curl | 7.68 或更高 | 用于链接可达性校验的外部调用 |
| markdownlint-cli | 0.33 或更高 | 可选依赖，用于本地 Markdown 格式检查 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | /docs/getting-started.md | 如何在一分钟内完成首次部署并导入第一批链接 |
| 链接管理 | /docs/link-management.md | 如何添加、删除、修改链接条目以及如何批量导入 |
| 目录架构 | /docs/directory-schema.md | 目录树的设计规范、命名约束与扩展方法 |
| 构建与部署 | /docs/build-deploy.md | 静态构建流程、环境变量配置与多种部署方式对比 |

## 资源列表

- http://www.mobile.cvsifc.cn/Article/details/2892.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9138762.sHtML
- http://www.mobile.cvsifc.cn/Article/details/977123.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5970.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5565743.sHtML
- http://www.mobile.cvsifc.cn/Article/details/793673.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4602731.sHtML
- http://www.mobile.cvsifc.cn/Article/details/109983.sHtML
- http://www.mobile.cvsifc.cn/Article/details/386002.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6396.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2467671.sHtML
- http://www.mobile.cvsifc.cn/Article/details/402362.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7315154.sHtML
- http://www.mobile.cvsifc.cn/Article/details/33859.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2257.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5696.sHtML
- http://www.mobile.cvsifc.cn/Article/details/02871.sHtML
- http://www.mobile.cvsifc.cn/Article/details/28223.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9587184.sHtML
- http://www.mobile.cvsifc.cn/Article/details/00091.sHtML
- http://www.mobile.cvsifc.cn/Article/details/13216.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8992.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1995.sHtML
- http://www.mobile.cvsifc.cn/Article/details/166058.sHtML
- http://www.mobile.cvsifc.cn/Article/details/606759.sHtML
- http://www.mobile.cvsifc.cn/Article/details/38775.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1912.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6867.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8376.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5002.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3255141.sHtML
- http://www.mobile.cvsifc.cn/Article/details/98817.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9823228.sHtML
- http://www.mobile.cvsifc.cn/Article/details/507059.sHtML
- http://www.mobile.cvsifc.cn/Article/details/867441.sHtML
- http://www.mobile.cvsifc.cn/Article/details/54345.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2840442.sHtML
- http://www.mobile.cvsifc.cn/Article/details/13630.sHtML
- http://www.mobile.cvsifc.cn/Article/details/42725.sHtML
- http://www.mobile.cvsifc.cn/Article/details/75049.sHtML
- http://www.mobile.cvsifc.cn/Article/details/182803.sHtML
- http://www.mobile.cvsifc.cn/Article/details/753849.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8449696.sHtML
- http://www.mobile.cvsifc.cn/Article/details/384583.sHtML
- http://www.mobile.cvsifc.cn/Article/details/943234.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2612.sHtML
- http://www.mobile.cvsifc.cn/Article/details/721650.sHtML
- http://www.mobile.cvsifc.cn/Article/details/23163.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9487027.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3967.sHtML
- http://www.mobile.cvsifc.cn/Article/details/12195.sHtML
- http://www.mobile.cvsifc.cn/Article/details/08651.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6269.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6196682.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8088.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6059.sHtML
- http://www.mobile.cvsifc.cn/Article/details/767252.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3416.sHtML
- http://www.mobile.cvsifc.cn/Article/details/60427.sHtML
- http://www.mobile.cvsifc.cn/Article/details/68926.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3648065.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1302874.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8333939.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9423659.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8351210.sHtML
- http://www.mobile.cvsifc.cn/Article/details/87527.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8869894.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8168952.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3392751.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7970.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0861.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5270.sHtML
- http://www.mobile.cvsifc.cn/Article/details/89922.sHtML
- http://www.mobile.cvsifc.cn/Article/details/966211.sHtML
- http://www.mobile.cvsifc.cn/Article/details/118495.sHtML
- http://www.mobile.cvsifc.cn/Article/details/368362.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2336.sHtML
- http://www.mobile.cvsifc.cn/Article/details/709308.sHtML
- http://www.mobile.cvsifc.cn/Article/details/81235.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9064856.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4478505.sHtML
- http://www.mobile.cvsifc.cn/Article/details/037131.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9576927.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9795.sHtML
- http://www.mobile.cvsifc.cn/Article/details/19357.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9358.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6151396.sHtML
- http://www.mobile.cvsifc.cn/Article/details/40274.sHtML
- http://www.mobile.cvsifc.cn/Article/details/03936.sHtML
- http://www.mobile.cvsifc.cn/Article/details/649038.sHtML
- http://www.mobile.cvsifc.cn/Article/details/17520.sHtML
- http://www.mobile.cvsifc.cn/Article/details/24310.sHtML
- http://www.mobile.cvsifc.cn/Article/details/861683.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1418551.sHtML
- http://www.mobile.cvsifc.cn/Article/details/742777.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1535.sHtML
- http://www.mobile.cvsifc.cn/Article/details/485969.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9049881.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8003.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4710.sHtML
- http://www.mobile.cvsifc.cn/Article/details/262964.sHtML
- http://www.mobile.cvsifc.cn/Article/details/852119.sHtML
- http://www.mobile.cvsifc.cn/Article/details/823246.sHtML
- http://www.mobile.cvsifc.cn/Article/details/433299.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1298274.sHtML
- http://www.mobile.cvsifc.cn/Article/details/885597.sHtML
- http://www.mobile.cvsifc.cn/Article/details/58317.sHtML
- http://www.mobile.cvsifc.cn/Article/details/065057.sHtML
- http://www.mobile.cvsifc.cn/Article/details/630258.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6122656.sHtML
- http://www.mobile.cvsifc.cn/Article/details/931284.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4597460.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7388.sHtML
- http://www.mobile.cvsifc.cn/Article/details/13412.sHtML
- http://www.mobile.cvsifc.cn/Article/details/85453.sHtML
- http://www.mobile.cvsifc.cn/Article/details/81169.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0914837.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8246644.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0469.sHtML
- http://www.mobile.cvsifc.cn/Article/details/58152.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4812558.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5983.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5625.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5755716.sHtML
- http://www.mobile.cvsifc.cn/Article/details/298134.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4309945.sHtML
- http://www.mobile.cvsifc.cn/Article/details/212611.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9408822.sHtML
- http://www.mobile.cvsifc.cn/Article/details/71466.sHtML
- http://www.mobile.cvsifc.cn/Article/details/828624.sHtML
- http://www.mobile.cvsifc.cn/Article/details/664090.sHtML
- http://www.mobile.cvsifc.cn/Article/details/857886.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9704.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8695.sHtML
- http://www.mobile.cvsifc.cn/Article/details/051568.sHtML
- http://www.mobile.cvsifc.cn/Article/details/378911.sHtML
- http://www.mobile.cvsifc.cn/Article/details/22317.sHtML
- http://www.mobile.cvsifc.cn/Article/details/65047.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9367456.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9175.sHtML
- http://www.mobile.cvsifc.cn/Article/details/76801.sHtML
- http://www.mobile.cvsifc.cn/Article/details/295236.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4766668.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7921.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0335.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2660.sHtML
- http://www.mobile.cvsifc.cn/Article/details/74835.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0484.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8606946.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9986.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8616.sHtML
- http://www.mobile.cvsifc.cn/Article/details/697663.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7293.sHtML
- http://www.mobile.cvsifc.cn/Article/details/646939.sHtML
- http://www.mobile.cvsifc.cn/Article/details/38647.sHtML
- http://www.mobile.cvsifc.cn/Article/details/650652.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7298.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6654.sHtML
- http://www.mobile.cvsifc.cn/Article/details/610702.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4901557.sHtML
- http://www.mobile.cvsifc.cn/Article/details/12008.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9367.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3589461.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6262.sHtML
- http://www.mobile.cvsifc.cn/Article/details/80111.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7147.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5445244.sHtML
- http://www.mobile.cvsifc.cn/Article/details/759996.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3576945.sHtML
- http://www.mobile.cvsifc.cn/Article/details/24584.sHtML
- http://www.mobile.cvsifc.cn/Article/details/999591.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9338301.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8628758.sHtML
- http://www.mobile.cvsifc.cn/Article/details/115129.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2747156.sHtML
- http://www.mobile.cvsifc.cn/Article/details/360026.sHtML
- http://www.mobile.cvsifc.cn/Article/details/636705.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7567538.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9338.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6517.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6444.sHtML
- http://www.mobile.cvsifc.cn/Article/details/969872.sHtML
- http://www.mobile.cvsifc.cn/Article/details/336912.sHtML
- http://www.mobile.cvsifc.cn/Article/details/885272.sHtML
- http://www.mobile.cvsifc.cn/Article/details/32303.sHtML
- http://www.mobile.cvsifc.cn/Article/details/80803.sHtML
- http://www.mobile.cvsifc.cn/Article/details/85119.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3627.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4917382.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5459.sHtML
- http://www.mobile.cvsifc.cn/Article/details/832044.sHtML
- http://www.mobile.cvsifc.cn/Article/details/17109.sHtML
- http://www.mobile.cvsifc.cn/Article/details/54014.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2749765.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4107427.sHtML
- http://www.mobile.cvsifc.cn/Article/details/370522.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7828051.sHtML
- http://www.mobile.cvsifc.cn/Article/details/00243.sHtML
- http://www.mobile.cvsifc.cn/Article/details/87344.sHtML
- http://www.mobile.cvsifc.cn/Article/details/74587.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5179054.sHtML
- http://www.mobile.cvsifc.cn/Article/details/24171.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8374.sHtML
- http://www.mobile.cvsifc.cn/Article/details/69022.sHtML
- http://www.mobile.cvsifc.cn/Article/details/29396.sHtML
- http://www.mobile.cvsifc.cn/Article/details/859999.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4399.sHtML
- http://www.mobile.cvsifc.cn/Article/details/466877.sHtML
- http://www.mobile.cvsifc.cn/Article/details/48519.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0139.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9711.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7981072.sHtML
- http://www.mobile.cvsifc.cn/Article/details/1450.sHtML
- http://www.mobile.cvsifc.cn/Article/details/137770.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2095262.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5346.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4867.sHtML
- http://www.mobile.cvsifc.cn/Article/details/280736.sHtML
- http://www.mobile.cvsifc.cn/Article/details/36602.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7639.sHtML
- http://www.mobile.cvsifc.cn/Article/details/83848.sHtML
- http://www.mobile.cvsifc.cn/Article/details/6093.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9920822.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9722831.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0179.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9573673.sHtML
- http://www.mobile.cvsifc.cn/Article/details/3393341.sHtML
- http://www.mobile.cvsifc.cn/Article/details/731389.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8773425.sHtML
- http://www.mobile.cvsifc.cn/Article/details/7552602.sHtML
- http://www.mobile.cvsifc.cn/Article/details/211985.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2041804.sHtML
- http://www.mobile.cvsifc.cn/Article/details/8698632.sHtML
- http://www.mobile.cvsifc.cn/Article/details/701704.sHtML
- http://www.mobile.cvsifc.cn/Article/details/9325.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4022.sHtML
- http://www.mobile.cvsifc.cn/Article/details/78939.sHtML
- http://www.mobile.cvsifc.cn/Article/details/01607.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0173.sHtML
- http://www.mobile.cvsifc.cn/Article/details/506584.sHtML
- http://www.mobile.cvsifc.cn/Article/details/0799894.sHtML
- http://www.mobile.cvsifc.cn/Article/details/622354.sHtML
- http://www.mobile.cvsifc.cn/Article/details/876771.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2858575.sHtML
- http://www.mobile.cvsifc.cn/Article/details/49762.sHtML
- http://www.mobile.cvsifc.cn/Article/details/2509163.sHtML
- http://www.mobile.cvsifc.cn/Article/details/15635.sHtML
- http://www.mobile.cvsifc.cn/Article/details/5054080.sHtML
- http://www.mobile.cvsifc.cn/Article/details/4925.sHtML
- http://www.mobile.cvsifc.cn/Article/details/97442.sHtML

## 项目结构

```
navsphere/
├── src/                           # 核心源代码目录
│   ├── indexer/                   # 链接索引引擎模块
│   │   ├── collector.ts           # 链接收集与去重逻辑
│   │   └── validator.ts           # 链接可达性校验实现
│   ├── parser/                    # 目录解析与路由生成
│   │   ├── tree-builder.ts        # 目录树结构构建器
│   │   └── tag-processor.ts       # 标签解析与规范化
│   ├── renderer/                  # 静态页面渲染引擎
│   │   ├── markdown-render.ts     # Markdown 转 HTML 渲染管线
│   │   └── template-engine.ts     # 模板变量注入与布局组装
│   └── cli/                       # 命令行入口与交互
│       ├── commands.ts            # 子命令定义与路由
│       └── logger.ts              # 结构化日志输出
├── data/                          # 数据存储目录
│   ├── links/                     # 链接原始数据 JSON 文件
│   ├── snapshots/                 # 变更历史快照
│   └── tags/                      # 标签索引与别名映射
├── docs/                          # 项目文档与用户手册
│   ├── getting-started.md
│   ├── link-management.md
│   ├── directory-schema.md
│   └── build-deploy.md
├── tests/                         # 单元测试与集成测试
│   ├── unit/                      # 单元测试用例
│   └── fixtures/                  # 测试固定数据集
├── config/                        # 环境配置与运行时参数
│   ├── default.yaml               # 默认配置项
│   └── production.yaml            # 生产环境覆盖配置
├── scripts/                       # 辅助运维脚本
│   ├── import-batch.sh            # 批量链接导入脚本
│   └── health-check.sh            # 服务健康状态检查
├── dist/                          # 构建输出目录
│   ├── public/                    # 静态资源文件
│   └── pages/                     # 生成的 HTML 页面
├── package.json                   # npm 项目清单与依赖声明
├── tsconfig.json                  # TypeScript 编译配置
└── README.md                      # 项目说明文档
```

## 贡献指南

1. 复刻项目仓库至个人账户，在本地创建功能分支，分支命名遵循 feat/功能描述 或 fix/问题描述 的格式。

2. 在 data/links 目录下新增或修改链接 JSON 文件，确保每个条目包含 url、title、tags、status 四个必需字段，并执行 npm run validate 进行格式校验。

3. 编写或更新对应的单元测试文件，测试用例需覆盖新增功能的正常路径与边界条件，保证测试通过率不低于 95%。

4. 提交变更前运行 npm run lint 与 npm run build 确认无语法错误且构建成功，提交信息采用语义化提交规范。

5. 发起 Pull Request 至主仓库的 develop 分支，在 PR 描述中清晰说明变更目的、影响范围与测试结果，等待至少一位维护者审核。

## 常见问题

**问：收录的链接如果发生失效或内容变更，项目如何处理？**

答：NavSphere 不主动探测链接的实时可用性，但提供了手动校验命令 npm run check:links，用户可定期执行以标记失效链接。标记为失效的链接会在界面中以灰色状态展示，并记录失效时间。用户亦可手动更新链接地址或移除条目。

**问：项目是否支持私有化部署与内网环境使用？**

答：完全支持。NavSphere 为纯静态构建产物，所有页面在构建时生成，无需外部网络访问。用户可将 dist 目录完整拷贝至内网 Web 服务器，或通过 Docker 镜像在隔离环境中启动服务。不依赖任何外部 CDN 或在线 API。

**问：如何从旧版本迁移链接数据至新版本？**

答：每个版本的数据结构变更会在 docs/migration.md 中详细说明。通常情况下，data/links 目录下的 JSON 文件保持向后兼容，用户仅需在新版本运行 npm run migrate 命令即可自动完成数据格式转换与校验。建议在迁移前对 data 目录进行完整备份。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:15
