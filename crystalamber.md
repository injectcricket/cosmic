# TechRef Navigator

TechRef Navigator 是一个面向技术文档聚合与快速检索的开源外链汇总系统。该项目定位于为开发者、技术研究者及运维工程师提供结构化、可分类、可追溯的高质量技术参考资料索引。系统本身不存储文章内容，而是通过精心维护的 URL 资源列表，将分散于各技术站点的高价值内容汇聚于统一入口，解决技术阅读中信息碎片化、检索效率低、优质内容难以沉淀的核心问题。

本项目适用于需要系统化构建个人或团队技术知识库的使用者，可作为日常技术阅读的起点，也可作为技术培训、方案评审或故障排查时的参考依据。通过明确的资源分类和稳定的索引结构，TechRef Navigator 帮助用户从海量信息中快速定位所需内容。

## 功能概览

**多维度资源分类**：支持按技术领域、文章类型、发布时间等多个维度对资源进行标签化分类，便于用户按需筛选。

**全文元数据提取**：自动抓取每个资源链接的标题、摘要、发布时间、作者等元信息，无需手动录入。

**快速关键词检索**：提供基于标题和描述的轻量级搜索接口，支持模糊匹配与精确查询两种模式。

**资源状态监控**：定期检测链接可用性，对失效或重定向的资源进行标记，保证索引库的活跃度。

**自定义标签系统**：用户可为每个资源添加自定义标签，实现个性化分类与后续快速召回。

**导入导出机制**：支持资源列表的批量导入（JSON/CSV）与导出，便于迁移、备份或与其他工具集成。

**访问统计看板**：记录每个资源的点击次数与最近访问时间，辅助判断内容热度与实际价值。

**响应式浏览界面**：适配桌面端与移动端，支持暗色主题与字体缩放，提升长文阅读体验。

## 应用场景

技术团队内部知识库构建：团队负责人可将本项目的资源列表作为团队技术周报的素材源，每周精选若干链接分发至成员，形成持续的学习闭环。

个人技术阅读工作流：开发者可在每日晨间使用本项目的检索功能，快速浏览当天更新的技术文章，替代碎片化的社交媒体信息流。

技术方案调研辅助：在系统设计或技术选型阶段，工程师可通过本项目的分类索引，批量获取相关领域的实践案例与对比分析文章。

技术培训材料准备：培训讲师可借助本项目的资源聚合能力，快速收集特定主题的入门教程、最佳实践和常见问题解答，缩短课件准备周期。

## 快速开始

以下命令演示了从克隆代码到启动本地服务的完整过程。

```bash
# 克隆项目仓库
git clone https://github.com/techref-navigator/navigator.git

# 进入项目目录
cd navigator

# 安装依赖（使用 npm）
npm install

# 启动开发服务器
npm run dev
```

启动成功后，访问控制台输出的本地地址（默认为 http://localhost:3000 ）即可使用本系统。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Node.js | 18.x 或 20.x LTS | 运行时环境，用于执行构建和开发服务器 |
| npm | 9.x 或以上 | 包管理器，用于安装项目依赖 |
| Git | 2.30 或以上 | 版本控制系统，用于克隆仓库和管理更新 |
| SQLite | 3.35 或以上（嵌入式） | 本地元数据存储引擎，无需单独安装 |
| 现代浏览器 | Chrome 90+ / Firefox 88+ / Edge 90+ | 前端界面运行环境，支持 ES2020 特性 |
| 网络连接 | 外网访问 | 用于首次启动时获取资源元数据（可离线运行） |
| 磁盘空间 | 至少 200 MB | 用于存放依赖包和本地索引缓存 |
| 操作系统 | Windows 10+ / macOS 11+ / Linux (glibc 2.28+) | 跨平台支持 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户指南 | /docs/user-guide/ | 如何使用检索、分类和标签功能，如何自定义个人视图 |
| 管理员手册 | /docs/admin/ | 如何批量导入资源、管理标签体系、检查链接状态 |
| 开发文档 | /docs/developer/ | 项目架构、API 接口说明、如何扩展新的数据源适配器 |
| 部署指南 | /docs/deployment/ | 生产环境部署选项（Docker / 裸机 / 云平台）和性能调优参数 |
| 设计文档 | /docs/design/ | 数据模型设计、缓存策略、前端状态管理方案 |

## 资源列表

- http://h5.mobile.cvsifc.cn/Article/details/4360.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3295857.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/305427.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1442323.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5270981.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2961945.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7747.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4998179.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/983025.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/32611.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2183136.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/31167.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/100801.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/259223.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9874.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/127653.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2991.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6147.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/27878.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/96851.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/57538.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0486.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1148814.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/05593.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/96506.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3296448.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7144312.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8755390.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0293.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/34027.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/745945.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/59594.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1570.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1245828.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5308.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6020.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/47200.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3533356.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0271.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2957.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2426.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4446248.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9021882.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0757459.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/552009.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5033.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9288.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/449480.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9417.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/89149.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0483800.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1555.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/977754.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/327036.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1016332.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/241588.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/051621.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/93419.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5808798.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7167427.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9893.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/95734.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/196697.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4282023.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7612545.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/178087.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9956.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/17321.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0598129.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9197917.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2520.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/837036.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/17505.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5524.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/03751.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/770087.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/72732.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/549247.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/65541.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9277.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/01998.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0710133.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4088.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0399822.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/521955.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8242500.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/047250.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/01866.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6577504.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5685.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9950.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3479285.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4375.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/405351.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/48100.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4316538.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1333.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6398.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8333.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7608121.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/754734.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5491236.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6444104.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/236427.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/340428.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/13603.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/92937.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/89800.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2880.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/600845.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5943.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/653981.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/121314.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/577689.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/57263.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/022589.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5382.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/071305.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7075445.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/09654.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3098.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6757562.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1699.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/16935.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2503068.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4951.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/596846.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0169261.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7570.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/743303.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8816306.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8277.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8002.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/755505.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9039.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/541629.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/910931.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0813227.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/56095.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/218825.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7794006.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/38861.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/047399.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9463874.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/151050.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/95038.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/398039.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/54342.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9123830.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4575661.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3159775.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9261.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1668688.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/922837.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1120800.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8385.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/465755.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/31810.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/777688.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7747885.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/429202.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5125.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/88149.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6769722.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8569.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5006682.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4212.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/680157.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8061891.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/37581.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7290605.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/52304.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0196878.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/13859.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9947338.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/92728.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/106290.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/15801.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0934.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/088984.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5297419.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/431598.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/834260.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/193541.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/64474.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/885005.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/923128.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6940752.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6261.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/890941.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/554743.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/700268.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/8242037.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/08068.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7949409.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6311.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6767.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/463116.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1996413.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/579331.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/413625.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2586.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/58490.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/853788.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/2348.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1669994.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/83284.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/87576.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/22250.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3112527.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/99794.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/778886.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1304.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3573.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/559206.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/25094.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/502799.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0256095.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/173695.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/52997.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7900717.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4352256.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/0800480.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/602784.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/56544.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7338225.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/3788289.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/891087.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/5111.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/1718854.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/10208.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/92558.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/891048.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/526336.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/729412.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9666355.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/33602.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/882510.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/58511.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4013025.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/49366.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/6717141.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/9225259.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7507.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/86623.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4213775.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/4603402.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/82652.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/7145109.sHtML
- http://h5.mobile.cvsifc.cn/Article/details/119803.sHtML

## 项目结构

```
navigator/
├── src/                                # 源代码主目录
│   ├── api/                            # 后端 API 路由与控制器
│   │   ├── resources/                  # 资源 CRUD 接口
│   │   ├── metadata/                   # 元数据抓取与更新接口
│   │   └── health/                     # 健康检查与状态接口
│   ├── core/                           # 核心业务逻辑
│   │   ├── crawler/                    # 元数据爬取模块（支持多源适配器）
│   │   ├── indexer/                    # 本地索引构建与查询引擎
│   │   └── monitor/                    # 链接可用性检测调度器
│   ├── db/                             # 数据访问层
│   │   ├── migrations/                 # SQLite 表结构迁移脚本
│   │   ├── models/                     # 数据模型定义（Resource, Tag, Log）
│   │   └── seed/                       # 初始示例数据
│   ├── frontend/                       # 前端单页应用源码
│   │   ├── components/                 # React/Vue 可复用组件（列表、搜索、标签）
│   │   ├── pages/                      # 页面级组件（主页、详情、看板）
│   │   └── styles/                     # 主题变量与全局样式
│   ├── utils/                          # 通用工具函数
│   │   ├── validator/                  # URL 校验与规范化
│   │   └── formatter/                  # 日期、大小写等格式化
│   └── config/                         # 环境配置与常量定义
├── tests/                              # 单元测试与集成测试
│   ├── unit/                           # 核心模块单测
│   └── integration/                    # API 与数据库集成测试
├── docs/                               # 完整文档（用户、管理、开发、部署）
│   ├── user-guide/
│   ├── admin/
│   ├── developer/
│   └── deployment/
├── scripts/                            # 运维与辅助脚本
│   ├── import.js                       # 批量导入资源列表
│   ├── export.js                       # 导出资源为 JSON/CSV
│   └── check-links.js                  # 手动触发链接检测
├── public/                             # 静态资源（favicon, robots.txt）
├── docker-compose.yml                  # 容器编排配置（含 Redis 缓存）
├── Dockerfile                          # 生产环境镜像构建文件
├── package.json                        # npm 依赖与脚本定义
├── tsconfig.json                       # TypeScript 编译配置
└── README.md                           # 项目入口文档（本文件）
```

## 贡献指南

1. 复刻主仓库至个人账户下，并在本地克隆复刻后的副本。创建新的功能分支，分支命名需遵循 `feature/描述` 或 `fix/描述` 的格式。

2. 在本地完成代码修改后，运行测试套件确保所有现有用例通过，并为新增功能添加对应的测试用例。使用 `npm run lint` 检查代码风格。

3. 提交变更时，遵循约定式提交规范（Conventional Commits），提交信息需包含类型、范围和简短描述，例如 `feat(api): add batch import endpoint`。

4. 将分支推送至远程复刻仓库，随后向主仓库的 `main` 分支发起拉取请求。在请求描述中清晰说明变更目的、影响范围及测试情况。

5. 等待项目维护者审阅。审阅过程中如有修改意见，在原有提交基础上进行修正并推送，避免关闭原请求创建新请求。

## 常见问题

**问：资源列表中的链接无法访问时，系统会如何处理？**

系统内置的监控模块会以可配置的周期（默认每 24 小时）对所有资源链接进行 HEAD 请求检测。当检测到连续三次返回非 2xx 状态码或连接超时时，该资源在界面上会被标记为"疑似失效"，并记录最后一次成功访问的时间。失效链接不会自动删除，但会被降权排序，用户也可在管理后台手动确认后移除。

**问：是否支持添加自定义资源或批量导入私有链接？**

支持。用户可通过管理界面的"添加资源"表单逐条录入，也可通过 `scripts/import.js` 脚本批量导入 JSON 或 CSV 格式的数据。导入时需提供标题和 URL 两个必填字段，其他元数据（描述、标签、分类）为可选。私有链接仅在本地存储，不会同步至公共索引库。

**问：项目使用什么缓存策略，能否离线使用？**

系统在首次访问资源时，会将其元数据（标题、描述、发布时间等）缓存在本地 SQLite 数据库中。后续检索和分类操作完全基于本地缓存，无需网络请求。但点击具体资源链接跳转至原始文章时，仍需外网访问。若需完全离线浏览，可使用导出功能将资源列表和元数据导出为静态 HTML 快照。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:14
