# WebLink Navigator

WebLink Navigator 是一个面向技术调研、内容聚合与知识管理场景的轻量级外链资源汇总平台。该项目定位于帮助开发者、技术写作人员、运维工程师以及数据分析师，以结构化方式收集、分类、检索和共享散布于互联网各处的技术文章、案例文档与参考手册。项目本身不存储原始内容，而是以索引和导航方式组织外部资源链接，并提供清晰的分类标签、状态标记和访问辅助信息，从而降低信息分散带来的认知负担，提升研发团队或个人知识库的构建效率。

作为第 139/200 批次发布的资源导航模块，WebLink Navigator 当前收录了 250 个来自移动端技术社区的文章详情页链接。这些链接覆盖了前端开发、后端架构、移动应用优化、安全实践、数据库调优、DevOps 工具链等多个技术子领域，适用于技术周报素材收集、竞品分析文档编写、故障排查参考库建设等实际工作流。项目本身采用纯静态 Markdown 构建，可无缝集成至 VuePress、Hugo、Docsify 等主流文档生成器，也可作为独立的资源清单嵌入任何 Web 应用的后台管理界面。

## 功能概览

**链接分级索引**  
系统根据 URL 路径中的 Article 分类标识自动生成一级分类标签，并支持用户自定义二级标签，便于按技术栈或业务域筛选。

**状态标记系统**  
每条资源记录可标记为待读、已读、已归档、失效链接四种状态，支持手动更新和定期批量校验。

**全文检索辅助**  
通过资源标题关键词和描述字段进行快速模糊匹配，帮助用户在大量链接中定位目标条目。

**批量导入导出**  
支持 CSV 和 JSON 格式的链接列表批量导入，同时允许将选中的资源集合导出为 HTML 书签文件或结构化数据文件。

**访问频率统计**  
内置简易计数器，记录每条链接被点击或查阅的次数，辅助判断内容的热度和复用价值。

**备注与批注功能**  
每条链接可附加不超过 500 字的文本备注，用于记录阅读心得、关键结论或待验证的技术点。

**多视图切换**  
提供列表视图、卡片视图和表格视图三种展示模式，适应不同屏幕尺寸和阅读偏好。

**链接可用性探测**  
提供可选的网络连通性预检功能，在用户点击前提示目标站点是否可访问，减少无效点击。

## 应用场景

技术团队内部知识库建设  
开发团队可将 WebLink Navigator 作为日常技术周报或事故复盘材料的素材池。当团队成员在日常浏览中遇到有价值的外部分析文章时，可一键将链接提交至导航系统并添加标签，后续由专人定期整理并输出为团队周报附件或 Wiki 页面引用。

个人技术阅读工作流管理  
技术爱好者或独立开发者可使用本系统管理每日订阅的 RSS 源、技术博客和论坛精华帖。通过状态标记和备注功能，可追踪每篇文章的阅读进度，避免重复阅读或遗漏关键信息，同时为后续撰写技术笔记或博客提供引用来源。

运维故障排查参考库建设  
运维团队可将常见的线上问题排查文档、官方修复公告、社区讨论帖等外链统一收录至 WebLink Navigator，并按服务模块或问题类型分类。当出现类似故障时，团队成员能够快速检索到历史参考案例，缩短平均修复时间。

技术方案选型对比素材收集  
在架构评审或技术选型阶段，工程师可围绕特定中间件、框架或云服务收集大量对比评测文章、性能测试报告和官方文档链接，通过本系统的标签和备注功能记录各方案的优缺点与适用条件，辅助决策过程。

## 快速开始

以下命令演示了如何将 WebLink Navigator 项目克隆至本地，安装基础依赖并启动开发服务器。项目采用 Node.js 环境，使用 npm 进行包管理。

```bash
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator
npm install
npm run dev
```

执行上述命令后，开发服务器将默认启动于 localhost:3000。用户可通过浏览器访问该地址，在本地查看资源列表及分类视图。如需构建生产环境静态文件，请使用 `npm run build` 命令，构建产物将输出至 `dist` 目录，可部署至任意静态托管服务。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Node.js | >= 16.14.0 | 运行时环境，用于执行构建脚本和开发服务器 |
| npm | >= 8.0.0 | 包管理器，用于安装项目依赖 |
| Git | >= 2.25.0 | 版本控制工具，用于克隆仓库和管理提交 |
| 现代浏览器 | Chrome 90+ / Firefox 88+ / Edge 90+ | 用于访问开发服务器和预览构建结果 |
| 磁盘空间 | >= 200 MB | 用于存放源码、依赖包及构建产物 |
| 操作系统 | Windows 10 / macOS 11+ / Linux (glibc 2.28+) | 支持主流桌面操作系统 |
| 网络环境 | 可访问 public npm registry | 用于下载依赖包，企业内部可使用镜像源 |
| Python | >= 3.8 (可选) | 仅在启用链接可用性探测脚本时需要 |
| curl | >= 7.68 (可选) | 用于远程链接状态检查脚本的执行 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户层面 | /docs/user-guide/ | 如何添加链接、如何分类、如何导出收藏集、如何切换视图 |
| 管理员层面 | /docs/admin-guide/ | 如何批量校验链接可用性、如何备份数据、如何迁移至生产环境 |
| 开发层面 | /docs/developer-guide/ | 项目目录结构说明、核心数据流设计、插件扩展机制、API 接口规范 |
| 部署层面 | /docs/deployment/ | 静态构建配置、Nginx 示例配置、CDN 接入步骤、环境变量清单 |
| 贡献层面 | /docs/contributing/ | 编码规范、提交信息格式、PR 流程、测试用例编写指南 |

## 资源列表

- http://www.mobile.fuvxie.cn/Article/details/9720.sHtML
- http://www.mobile.fuvxie.cn/Article/details/942444.sHtML
- http://www.mobile.fuvxie.cn/Article/details/86886.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7218211.sHtML
- http://www.mobile.fuvxie.cn/Article/details/62482.sHtML
- http://www.mobile.fuvxie.cn/Article/details/531365.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4414.sHtML
- http://www.mobile.fuvxie.cn/Article/details/53936.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7898853.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3188811.sHtML
- http://www.mobile.fuvxie.cn/Article/details/625546.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0473.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8508.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6836.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8630965.sHtML
- http://www.mobile.fuvxie.cn/Article/details/215545.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9923602.sHtML
- http://www.mobile.fuvxie.cn/Article/details/43715.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8656040.sHtML
- http://www.mobile.fuvxie.cn/Article/details/369133.sHtML
- http://www.mobile.fuvxie.cn/Article/details/158398.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8015155.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6678960.sHtML
- http://www.mobile.fuvxie.cn/Article/details/275100.sHtML
- http://www.mobile.fuvxie.cn/Article/details/32562.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2667.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3352.sHtML
- http://www.mobile.fuvxie.cn/Article/details/56473.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9440.sHtML
- http://www.mobile.fuvxie.cn/Article/details/049475.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1579953.sHtML
- http://www.mobile.fuvxie.cn/Article/details/239817.sHtML
- http://www.mobile.fuvxie.cn/Article/details/294535.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0952.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7403757.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2612.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1518830.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8417.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0343.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9824128.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8611794.sHtML
- http://www.mobile.fuvxie.cn/Article/details/53876.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1816.sHtML
- http://www.mobile.fuvxie.cn/Article/details/33917.sHtML
- http://www.mobile.fuvxie.cn/Article/details/10237.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7822.sHtML
- http://www.mobile.fuvxie.cn/Article/details/432855.sHtML
- http://www.mobile.fuvxie.cn/Article/details/88732.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2671.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8144.sHtML
- http://www.mobile.fuvxie.cn/Article/details/621660.sHtML
- http://www.mobile.fuvxie.cn/Article/details/20588.sHtML
- http://www.mobile.fuvxie.cn/Article/details/51646.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7912.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0589412.sHtML
- http://www.mobile.fuvxie.cn/Article/details/234389.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6570097.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7714.sHtML
- http://www.mobile.fuvxie.cn/Article/details/997093.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2019.sHtML
- http://www.mobile.fuvxie.cn/Article/details/90297.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5182.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4524.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8681518.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1809.sHtML
- http://www.mobile.fuvxie.cn/Article/details/256539.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3371832.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3319085.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3413.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7826258.sHtML
- http://www.mobile.fuvxie.cn/Article/details/574890.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6344951.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4082753.sHtML
- http://www.mobile.fuvxie.cn/Article/details/70548.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9670662.sHtML
- http://www.mobile.fuvxie.cn/Article/details/521268.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9114.sHtML
- http://www.mobile.fuvxie.cn/Article/details/17807.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2178.sHtML
- http://www.mobile.fuvxie.cn/Article/details/703357.sHtML
- http://www.mobile.fuvxie.cn/Article/details/72251.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5445.sHtML
- http://www.mobile.fuvxie.cn/Article/details/24086.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3516.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4525.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2661993.sHtML
- http://www.mobile.fuvxie.cn/Article/details/66574.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6388070.sHtML
- http://www.mobile.fuvxie.cn/Article/details/52880.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8294842.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7721543.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0519.sHtML
- http://www.mobile.fuvxie.cn/Article/details/10073.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0771.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2121079.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9521583.sHtML
- http://www.mobile.fuvxie.cn/Article/details/792805.sHtML
- http://www.mobile.fuvxie.cn/Article/details/961983.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5234424.sHtML
- http://www.mobile.fuvxie.cn/Article/details/256813.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5735841.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9208.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8056.sHtML
- http://www.mobile.fuvxie.cn/Article/details/850307.sHtML
- http://www.mobile.fuvxie.cn/Article/details/65995.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6361.sHtML
- http://www.mobile.fuvxie.cn/Article/details/524791.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9338044.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0764.sHtML
- http://www.mobile.fuvxie.cn/Article/details/594659.sHtML
- http://www.mobile.fuvxie.cn/Article/details/583707.sHtML
- http://www.mobile.fuvxie.cn/Article/details/679275.sHtML
- http://www.mobile.fuvxie.cn/Article/details/316059.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2709601.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2460.sHtML
- http://www.mobile.fuvxie.cn/Article/details/18061.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7173766.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9073.sHtML
- http://www.mobile.fuvxie.cn/Article/details/77172.sHtML
- http://www.mobile.fuvxie.cn/Article/details/73523.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8022407.sHtML
- http://www.mobile.fuvxie.cn/Article/details/09024.sHtML
- http://www.mobile.fuvxie.cn/Article/details/734067.sHtML
- http://www.mobile.fuvxie.cn/Article/details/32922.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0256.sHtML
- http://www.mobile.fuvxie.cn/Article/details/208906.sHtML
- http://www.mobile.fuvxie.cn/Article/details/57761.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1757.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0388335.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9120.sHtML
- http://www.mobile.fuvxie.cn/Article/details/113647.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7796.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7151.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0071434.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9529576.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3195.sHtML
- http://www.mobile.fuvxie.cn/Article/details/73820.sHtML
- http://www.mobile.fuvxie.cn/Article/details/32816.sHtML
- http://www.mobile.fuvxie.cn/Article/details/42540.sHtML
- http://www.mobile.fuvxie.cn/Article/details/526168.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2117.sHtML
- http://www.mobile.fuvxie.cn/Article/details/674771.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9849.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3645.sHtML
- http://www.mobile.fuvxie.cn/Article/details/460852.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9224.sHtML
- http://www.mobile.fuvxie.cn/Article/details/156416.sHtML
- http://www.mobile.fuvxie.cn/Article/details/62095.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0270151.sHtML
- http://www.mobile.fuvxie.cn/Article/details/86305.sHtML
- http://www.mobile.fuvxie.cn/Article/details/896874.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0187472.sHtML
- http://www.mobile.fuvxie.cn/Article/details/732884.sHtML
- http://www.mobile.fuvxie.cn/Article/details/032718.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0597.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2419.sHtML
- http://www.mobile.fuvxie.cn/Article/details/194816.sHtML
- http://www.mobile.fuvxie.cn/Article/details/374849.sHtML
- http://www.mobile.fuvxie.cn/Article/details/95942.sHtML
- http://www.mobile.fuvxie.cn/Article/details/964233.sHtML
- http://www.mobile.fuvxie.cn/Article/details/218551.sHtML
- http://www.mobile.fuvxie.cn/Article/details/732664.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0678.sHtML
- http://www.mobile.fuvxie.cn/Article/details/34839.sHtML
- http://www.mobile.fuvxie.cn/Article/details/436422.sHtML
- http://www.mobile.fuvxie.cn/Article/details/774933.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0264890.sHtML
- http://www.mobile.fuvxie.cn/Article/details/67121.sHtML
- http://www.mobile.fuvxie.cn/Article/details/06499.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4699114.sHtML
- http://www.mobile.fuvxie.cn/Article/details/209518.sHtML
- http://www.mobile.fuvxie.cn/Article/details/977469.sHtML
- http://www.mobile.fuvxie.cn/Article/details/700407.sHtML
- http://www.mobile.fuvxie.cn/Article/details/18452.sHtML
- http://www.mobile.fuvxie.cn/Article/details/611628.sHtML
- http://www.mobile.fuvxie.cn/Article/details/642543.sHtML
- http://www.mobile.fuvxie.cn/Article/details/80699.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7373360.sHtML
- http://www.mobile.fuvxie.cn/Article/details/310631.sHtML
- http://www.mobile.fuvxie.cn/Article/details/64790.sHtML
- http://www.mobile.fuvxie.cn/Article/details/35383.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0975.sHtML
- http://www.mobile.fuvxie.cn/Article/details/7155.sHtML
- http://www.mobile.fuvxie.cn/Article/details/62642.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8216.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4299742.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0825.sHtML
- http://www.mobile.fuvxie.cn/Article/details/277680.sHtML
- http://www.mobile.fuvxie.cn/Article/details/07654.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2994744.sHtML
- http://www.mobile.fuvxie.cn/Article/details/570276.sHtML
- http://www.mobile.fuvxie.cn/Article/details/10459.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9621.sHtML
- http://www.mobile.fuvxie.cn/Article/details/11284.sHtML
- http://www.mobile.fuvxie.cn/Article/details/917837.sHtML
- http://www.mobile.fuvxie.cn/Article/details/19859.sHtML
- http://www.mobile.fuvxie.cn/Article/details/68096.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0595097.sHtML
- http://www.mobile.fuvxie.cn/Article/details/625550.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8979.sHtML
- http://www.mobile.fuvxie.cn/Article/details/53145.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1493.sHtML
- http://www.mobile.fuvxie.cn/Article/details/8709505.sHtML
- http://www.mobile.fuvxie.cn/Article/details/89540.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6961.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5565588.sHtML
- http://www.mobile.fuvxie.cn/Article/details/315122.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2242.sHtML
- http://www.mobile.fuvxie.cn/Article/details/548390.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9102268.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1427555.sHtML
- http://www.mobile.fuvxie.cn/Article/details/314204.sHtML
- http://www.mobile.fuvxie.cn/Article/details/72462.sHtML
- http://www.mobile.fuvxie.cn/Article/details/074570.sHtML
- http://www.mobile.fuvxie.cn/Article/details/51411.sHtML
- http://www.mobile.fuvxie.cn/Article/details/14401.sHtML
- http://www.mobile.fuvxie.cn/Article/details/68427.sHtML
- http://www.mobile.fuvxie.cn/Article/details/5465.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6109.sHtML
- http://www.mobile.fuvxie.cn/Article/details/391918.sHtML
- http://www.mobile.fuvxie.cn/Article/details/32321.sHtML
- http://www.mobile.fuvxie.cn/Article/details/15257.sHtML
- http://www.mobile.fuvxie.cn/Article/details/12664.sHtML
- http://www.mobile.fuvxie.cn/Article/details/32072.sHtML
- http://www.mobile.fuvxie.cn/Article/details/251840.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6628.sHtML
- http://www.mobile.fuvxie.cn/Article/details/3935027.sHtML
- http://www.mobile.fuvxie.cn/Article/details/07109.sHtML
- http://www.mobile.fuvxie.cn/Article/details/402781.sHtML
- http://www.mobile.fuvxie.cn/Article/details/715903.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4856596.sHtML
- http://www.mobile.fuvxie.cn/Article/details/50728.sHtML
- http://www.mobile.fuvxie.cn/Article/details/876229.sHtML
- http://www.mobile.fuvxie.cn/Article/details/6834.sHtML
- http://www.mobile.fuvxie.cn/Article/details/45931.sHtML
- http://www.mobile.fuvxie.cn/Article/details/42748.sHtML
- http://www.mobile.fuvxie.cn/Article/details/158684.sHtML
- http://www.mobile.fuvxie.cn/Article/details/4247169.sHtML
- http://www.mobile.fuvxie.cn/Article/details/9636.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2255987.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0075707.sHtML
- http://www.mobile.fuvxie.cn/Article/details/18244.sHtML
- http://www.mobile.fuvxie.cn/Article/details/57078.sHtML
- http://www.mobile.fuvxie.cn/Article/details/670814.sHtML
- http://www.mobile.fuvxie.cn/Article/details/2415.sHtML
- http://www.mobile.fuvxie.cn/Article/details/1855.sHtML
- http://www.mobile.fuvxie.cn/Article/details/383469.sHtML
- http://www.mobile.fuvxie.cn/Article/details/0132461.sHtML
- http://www.mobile.fuvxie.cn/Article/details/11775.sHtML
- http://www.mobile.fuvxie.cn/Article/details/98919.sHtML

## 项目结构

```
weblink-navigator/
├── src/                                 # 源代码主目录
│   ├── core/                           # 核心数据模型与状态管理
│   │   ├── linkRegistry.js            # 链接注册与索引逻辑
│   │   └── tagEngine.js               # 标签分类与过滤引擎
│   ├── ui/                             # 用户界面组件
│   │   ├── components/                # 可复用 Vue 组件
│   │   │   ├── LinkTable.vue          # 表格视图组件
│   │   │   ├── LinkCard.vue           # 卡片视图组件
│   │   │   └── StatusBadge.vue        # 状态标记徽章组件
│   │   ├── layouts/                   # 页面布局模板
│   │   │   ├── defaultLayout.vue      # 默认布局
│   │   │   └── fullscreenLayout.vue   # 全屏专注模式布局
│   │   └── styles/                    # 全局样式与主题变量
│   ├── utils/                          # 工具函数集合
│   │   ├── httpChecker.js             # 链接可用性探测模块
│   │   ├── exporter.js                # 数据导出工具（CSV/JSON/HTML）
│   │   └── validator.js               # URL 格式校验与规范化
│   ├── plugins/                        # 插件扩展机制
│   │   ├── rssFeeder.js              # RSS 订阅源生成插件
│   │   └── tagAutoComplete.js        # 标签智能补全插件
│   └── config/                         # 配置文件目录
│       ├── siteConfig.js              # 站点基本配置（标题、描述、分页数）
│       └── categoryMapping.js         # URL 路径到分类标签的映射规则
├── public/                             # 静态资源文件
│   ├── favicon.ico                    # 站点图标
│   └── robots.txt                     # 搜索引擎爬虫规则
├── docs/                               # 项目文档（用户手册、开发指南、部署说明）
│   ├── user-guide/
│   ├── admin-guide/
│   ├── developer-guide/
│   └── deployment/
├── tests/                              # 单元测试与集成测试脚本
│   ├── unit/
│   └── integration/
├── scripts/                            # 运维辅助脚本
│   ├── batchCheck.sh                 # 批量链接状态检查 Shell 脚本
│   └── dataMigrate.js                # 数据格式迁移工具
├── .gitignore                          # Git 忽略文件规则
├── package.json                        # npm 依赖清单与脚本定义
├── README.md                           # 项目说明文档（本文件）
└── LICENSE                             # MIT 许可证文件
```

## 贡献指南

1. 复刻仓库并创建功能分支  
   访问 GitHub 仓库页面，点击 "Fork" 按钮将项目复刻至个人账户，随后使用 `git checkout -b feature/your-feature-name` 创建本地分支，确保分支名称清晰描述所实现的功能或修复的问题。

2. 遵循编码规范与提交信息格式  
   所有 JavaScript 代码需通过 ESLint 配置检查，提交信息须遵循 Conventional Commits 规范，格式为 `<type>(<scope>): <subject>`，其中 type 包括 feat、fix、docs、style、refactor、test、chore 等。提交时需确保单元测试全部通过。

3. 新增或修改资源链接条目  
   若需在资源列表中添加新链接或更新现有链接信息，请修改 `src/core/linkRegistry.js` 中的静态数据数组，并同步更新对应的分类映射表。对于批量操作，可使用 `scripts/dataMigrate.js` 工具进行数据导入。

4. 编写或更新相关文档  
   任何涉及用户可见功能的变化，均需同步更新 `docs/` 目录下对应的用户手册或管理员指南。新增配置项或环境变量必须在部署文档中予以说明。

5. 发起 Pull Request 并等待审核  
   将本地分支推送至个人远程仓库后，在 GitHub 上向主仓库的 `main` 分支发起 Pull Request。PR 描述中需包含变更目的、实现方式、测试结果以及相关的 issue 编号（若有）。项目维护者将在 3 个工作日内进行代码审查。

## 常见问题

**Q：资源列表中的链接访问时返回 404，如何处理？**  
A：WebLink Navigator 本身不托管原始内容，仅提供链接索引。用户可通过界面中的状态标记功能将对应链接标记为 "失效链接"。项目管理员可定期运行 `scripts/batchCheck.sh` 脚本对所有链接进行批量连通性检测，并依据检测结果统一更新状态。若发现大量失效链接，建议联系原始站点管理员确认内容迁移情况，或从列表中移除该条目。

**Q：能否将本系统部署到内网环境，且不连接互联网？**  
A：可以。WebLink Navigator 构建后为纯静态文件，所有资源链接以 JSON 数据格式嵌入 JavaScript 文件中，无需额外网络请求。将 `dist` 目录下的所有文件复制到内网 Web 服务器（如 Nginx、Apache 或 SMB 共享目录）即可正常访问。需要注意的是，链接可用性探测功能依赖外网请求，在内网环境中该功能将无法生效，但不影响其他核心功能的使用。

**Q：如何迁移已有资源数据至新版本？**  
A：项目在每次发布版本时均会提供数据迁移指南。一般情况下，用户仅需保留 `src/core/linkRegistry.js` 中的自定义链接数组，并将其复制到新版本的对应文件中。若数据结构发生变更，可使用 `scripts/dataMigrate.js --from v1 --to v2` 命令进行自动格式转换。建议在执行迁移前备份原始数据文件。

**Q：

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:15
