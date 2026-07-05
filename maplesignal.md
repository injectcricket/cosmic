# WebLink Navigator - 技术资源导航与聚合平台

WebLink Navigator 是一个面向开发人员、技术研究者与开源项目维护者的轻量级外链资源导航系统。该项目旨在解决个人与技术团队在信息检索过程中面临的链接分散、归类模糊、重复查找等问题，通过结构化的资源收录机制与清晰的分类索引，将碎片化的技术文章、案例文档与外部参考资料整合为可快速检索与共享的知识库。

WebLink Navigator 定位于个人开发者与中小型技术团队的日常协作场景，提供纯静态化的资源展示方案，同时支持通过后端接口实现资源的动态更新与权限管理。项目本身不生产内容，而是作为技术内容的高效索引层，帮助用户在信息过载的环境中快速定位高价值外部资源。

## 功能概览

- **结构化资源收录**：支持按技术领域、文档类型、来源站点等多个维度对链接进行分类标记，每条外链均可附加标签与简短描述，便于后续检索与归档。

- **全文检索与过滤**：内置基于关键词的标题与描述检索能力，支持按标签、发布日期、关联项目等条件进行组合过滤，提升资源查找效率。

- **批次导入与管理**：针对大批量链接导入场景提供批次管理功能，每批次可包含数百条资源链接，支持批次状态跟踪、完整性校验与重复检测。

- **访问统计与热度排序**：记录每条外部资源的点击次数与最近访问时间，支持按热度、更新时间或新增时间进行多模式排序，帮助用户识别当前关注度较高的内容。

- **响应式移动端适配**：前端界面针对手机与平板设备进行专门优化，确保在移动环境下仍可流畅完成资源浏览、检索与分享操作。

- **开放数据导出接口**：提供 JSON 与 CSV 格式的资源列表导出接口，便于与其他工具链（如知识库系统、自动化脚本、数据分析平台）进行数据对接。

- **资源状态监控与死链检测**：集成定期链接可用性检查机制，自动标记访问异常的链接，并生成死链报告供维护人员参考。

## 应用场景

- **技术团队内部知识库建设**：团队可将日常开发中积累的官方文档、技术博客、问题排查记录等外部链接统一收录至 WebLink Navigator，形成可共享的团队知识资产，减少重复沟通成本。

- **开源项目文档站的外链附录**：开源项目维护者可将项目依赖的参考文档、社区教程、相关工具站点等资源通过 WebLink Navigator 进行集中管理，作为项目文档站的外链附录，方便贡献者与用户查阅。

- **技术学习路线图配套资源索引**：教育机构或技术社区可围绕特定技术方向（如云原生、前端工程化、机器学习基础）构建配套资源索引，将分散的优质学习材料通过本平台统一呈现，提升学习路径的清晰度。

- **个人开发者的书签管理升级**：个人开发者可将浏览器中累积的大量技术书签迁移至 WebLink Navigator，利用分类、检索与统计功能实现比传统书签管理器更高效的信息组织与回顾。

- **技术调研与竞品分析资料汇集**：在进行技术选型或竞品分析时，分析师可将涉及的多方资料、官方公告、性能测试报告等链接汇总至同一平台，便于横向对比与团队评审。

## 快速开始

以下命令可帮助您在本地环境中快速启动 WebLink Navigator 服务。

```bash
# 克隆项目仓库至本地
git clone https://github.com/weblink-navigator/weblink-navigator.git

# 进入项目根目录
cd weblink-navigator

# 安装项目依赖（使用 npm）
npm install

# 启动开发服务器，默认监听端口 3000
npm run dev
```

启动成功后，打开浏览器访问 http://localhost:3000 即可进入系统主页。生产环境部署请参考 `docs/deployment.md` 文档。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或 20.x LTS | 运行时环境，推荐使用官方二进制版本或 nvm 管理 |
| npm | 9.x 或 10.x | 包管理器，随 Node.js 一同安装 |
| SQLite | 3.x（内置） | 默认本地数据库，无需额外安装，生产环境可切换至 PostgreSQL |
| Redis | 7.x（可选） | 用于会话存储与缓存加速，生产环境推荐配置 |
| Nginx | 1.24+（可选） | 反向代理与静态资源缓存，用于生产环境前端性能优化 |
| Git | 2.30+ | 用于版本克隆与后续更新拉取 |
| PM2 | 5.x（可选） | 生产环境进程守护与管理工具 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | `docs/quick-start.md` | 如何在一小时内完成部署并导入首批资源链接 |
| 使用手册 | `docs/user-guide.md` | 如何对已有资源进行增删改查操作 |
| 管理指南 | `docs/admin-guide.md` | 如何管理用户权限与批量导入导出 |
| 开发参考 | `docs/api-reference.md` | 后端接口定义与前端组件说明 |
| 运维手册 | `docs/operations.md` | 生产环境监控与备份恢复策略 |

完整文档请查阅 `docs/` 目录下的 Markdown 文件，或访问项目在线文档站（链接见资源列表）。

## 资源列表

- http://h5.mobile.cmcvrr.cn/Article/details/517190.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/1478.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/44264.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/370993.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/9346288.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/835677.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/0032839.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/34245.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/813374.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/7577.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/46074.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/224688.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/4793.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/51311.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/562605.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/1517045.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/92270.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/25324.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/0181694.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/75179.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/7682481.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/1212118.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/5837.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/269123.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/3934006.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/042832.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/0613709.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/2592.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/11574.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/1721109.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/22385.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/87816.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/48469.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/35620.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/31264.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/6951957.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/145795.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/83152.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/056807.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/1912184.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/06042.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/506903.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/642675.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/309528.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/672508.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/2426267.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/292565.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/2658.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/90524.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/65673.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/9006.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/97808.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/8572265.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/9222.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/9470.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/364588.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/527837.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/48237.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/2449260.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/7310.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/770136.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/5389.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/07398.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/9382.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/5037.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/2799132.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/0972.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/81563.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/2752588.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/81639.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/0645101.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/9655.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/59555.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/832581.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/84376.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/4121.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/3617557.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/5484911.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/0752.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/104048.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/38893.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/954802.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/1563.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/278507.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/386256.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/5477.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/406045.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/4311.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/9279397.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/522802.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/616634.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/020779.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/525850.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/813553.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/6877017.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/8527.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/1928.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/9901.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/0223.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/9514.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/386477.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/981797.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/619694.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/4678.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/50333.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/03241.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/20236.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/74774.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/9980.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/46769.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/1445.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/948657.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/90417.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/38483.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/3407036.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/2514855.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/275473.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/010585.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/046479.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/1461.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/26073.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/19805.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/653562.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/2866935.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/0612047.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/1376940.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/2692318.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/3987464.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/9039.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/73699.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/8140.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/936815.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/3786697.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/5912.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/8545.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/36288.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/013075.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/566449.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/57258.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/672130.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/03086.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/088598.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/145394.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/805701.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/0051430.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/4195457.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/1862854.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/33887.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/877504.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/1171.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/2566.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/2779585.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/28409.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/82531.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/49444.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/8666.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/21834.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/6417717.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/0900129.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/941093.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/04962.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/0255.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/1064804.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/710471.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/62755.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/85340.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/167428.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/03170.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/274564.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/2641.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/450426.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/47571.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/91382.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/6851.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/725631.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/341036.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/9377.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/7655539.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/6149.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/4898544.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/959755.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/59505.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/3180330.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/8328.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/9114.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/76119.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/517733.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/57958.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/233266.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/35907.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/1135.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/510729.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/7508640.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/73029.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/54613.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/9176.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/34114.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/07709.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/2266.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/00687.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/7168.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/72814.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/5404.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/8743609.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/0824.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/53342.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/93491.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/1421819.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/4185664.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/261027.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/7903.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/5040.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/0097767.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/6082446.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/958168.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/89677.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/6772401.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/4235.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/430382.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/0531.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/4141137.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/552424.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/7988684.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/7546130.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/98945.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/7078.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/43461.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/4083.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/3934.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/40034.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/9718.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/2959507.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/8958718.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/9823383.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/9768041.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/8459.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/1631.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/4862742.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/5634.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/6213429.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/87520.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/4707864.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/341784.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/879402.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/0483.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/5514.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/5536638.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/3223.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/8921460.sHtML
- http://h5.mobile.cmcvrr.cn/Article/details/486113.sHtML

## 项目结构

```
weblink-navigator/
├── backend/                        # 后端服务代码目录
│   ├── src/
│   │   ├── controllers/            # 请求控制器，处理资源增删改查、批次管理等业务逻辑
│   │   ├── models/                 # 数据模型层，定义资源条目、批次、标签等数据库结构
│   │   ├── routes/                 # RESTful 路由定义，映射 URL 路径至对应控制器方法
│   │   ├── services/               # 核心业务服务，含链接检测、统计计算、数据导出等
│   │   └── utils/                  # 通用工具函数，含日期格式化、字符串处理、校验器等
│   ├── tests/                      # 后端单元测试与集成测试用例
│   └── package.json                # 后端依赖声明与脚本配置
├── frontend/                       # 前端用户界面代码目录
│   ├── src/
│   │   ├── components/             # Vue/React 可复用组件，含资源卡片、搜索栏、分页器等
│   │   ├── pages/                  # 页面级组件，对应主页、详情页、导入页、管理面板等
│   │   ├── stores/                 # 状态管理，维护当前资源列表、筛选条件、用户偏好等
│   │   ├── styles/                 # 全局样式表与主题变量定义
│   │   └── utils/                  # 前端工具函数，含请求封装、数据格式化、防抖节流等
│   ├── public/                     # 静态资源文件，含 favicon、站点图标、robots.txt
│   └── package.json                # 前端依赖声明与构建脚本配置
├── docs/                           # 项目文档目录，含快速开始、使用手册、API 文档等
│   ├── quick-start.md
│   ├── user-guide.md
│   ├── admin-guide.md
│   ├── api-reference.md
│   └── operations.md
├── scripts/                        # 运维与辅助脚本，含数据库初始化、死链扫描、数据迁移等
│   ├── init-db.js
│   ├── health-check.js
│   └── batch-import.js
├── config/                         # 环境配置文件目录，含开发、测试、生产环境差异配置
│   ├── development.env
│   ├── production.env
│   └── test.env
├── docker-compose.yml              # Docker Compose 编排文件，用于一键启动全套服务栈
├── Dockerfile                      # 项目容器化构建定义
├── .gitignore                      # Git 版本控制忽略文件配置
├── LICENSE                         # MIT 许可证文件
└── README.md                       # 项目说明文档（当前文件）
```

## 贡献指南

WebLink Navigator 欢迎来自社区的各类贡献，包括但不限于新功能开发、文档完善、缺陷修复与资源推荐。请遵循以下步骤参与项目贡献。

1. 阅读项目行为准则与贡献规范：在提交任何代码或文档变更前，请仔细阅读 `CODE_OF_CONDUCT.md` 与 `CONTRIBUTING.md` 文件，确保理解社区协作的基本要求。

2. 查找或创建议题：访问 GitHub Issues 页面，查找您感兴趣且未被分配的议题，或根据实际需求创建新议题描述待解决的问题或建议的新功能，等待维护者确认后再开始开发。

3. 派生仓库并创建特性分支：将主仓库派生至个人账户下，然后在本地派生仓库中创建以 `feature/` 或 `fix/` 为前缀的新分支，分支命名应简洁描述变更内容。

4. 编写代码与测试：在特性分支上完成代码编写，确保新增或修改的代码通过已有的单元测试，并为新功能补充对应的测试用例。提交信息应遵循 Conventional Commits 规范。

5. 发起合并请求：将特性分支推送至派生仓库后，向主仓库的 `main` 分支发起合并请求。合并请求描述中应清晰说明变更目的、实现方案与测试覆盖情况，等待维护者进行代码审查与合并。

## 常见问题

**问：WebLink Navigator 是否支持从浏览器书签文件（如 HTML 格式）批量导入链接？**

答：当前版本暂未直接支持书签 HTML 文件的解析导入，但项目提供了基于 CSV 与 JSON 格式的批量导入接口。用户可将浏览器书签导出后，通过脚本或在线转换工具将书签列表转换为符合导入格式要求的 CSV 或 JSON 文件，再通过管理面板的批量导入功能完成数据录入。后续版本计划增加对 Netscape 书签格式的原生支持。

**问：部署后访问前端页面出现空白或接口请求失败，应如何排查？**

答：此类问题通常由后端服务未正常启动或前端代理配置错误引起。建议按以下顺序排查：首先使用 `npm run status` 检查后端服务进程是否存活，并确认端口 3000 未被占用；其次检查 `config/production.env` 中的 API_BASE_URL 配置是否与前端构建时指定的后端地址一致；最后查看浏览器开发者工具中的网络请求面板，确认具体请求的响应状态码与错误信息，常见原因包括跨域配置缺失或数据库连接失败。

**问：系统内置的死链检测机制是否会对目标站点造成访问压力？**

答：死链检测采用单线程顺序扫描方式，每次请求之间设置至少 500 毫秒的延迟间隔，且检测频率默认为每 7 天执行一次。对于包含大量链接的实例，检测任务会分散在多个时间窗口内执行，避免在短时间内对同一目标域名的集中请求。用户也可在配置文件中调整检测间隔与并发数，以适应不同规模实例的实际需求。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:15
