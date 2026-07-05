# LinkPilot — 技术资源导航与文档外链治理工具

LinkPilot 是一个面向技术团队与内容运营者的轻量级外链资源归集与健康度检查系统。项目定位于解决大规模分散链接的收录、分类、可用性探测与访问路径梳理问题，特别适用于文档站、导航站、技术博客及移动端 H5 资源聚合场景。目标用户包括前端开发者、DevOps 工程师、技术文档撰写者以及需要批量维护外链资源的站点管理员。

LinkPilot 本身不存储任何第三方内容，仅对用户提交的 URL 进行结构化存储、元数据抽取与可达性探测，并生成可导出的资源清单与状态报表。项目采用静态站点生成思路，可无状态部署，同时支持通过定时任务对已收录链接进行存活校验。第 175/200 批资源导入工作已集成至主分支，共计收录 250 条外链条目，涵盖技术文档、开源镜像、API 参考、移动端组件库及运维手册等类别。

## 功能概览

- **批量 URL 归集与去重**：支持按批次导入海量链接，自动识别重复条目并做合并处理，保留首次收录时间戳与来源标记。

- **链接协议与大小写保持**：严格遵循原始 URL 的协议头（http/https）、域名大小写、路径大小写及文件扩展名大小写，不做任何自动补全或规范化改写，确保与源站资源寻址行为完全一致。

- **资源可达性探测**：基于 HTTP 状态码与响应时间对已收录链接进行周期性探测，标记异常链接（4xx、5xx、超时），并生成健康度趋势报表。

- **目录树映射与分类标签**：支持为每条链接添加自定义分类标签（如「前端框架」「运维工具」「数据库中间件」），并基于 URL 路径模式自动生成目录树结构，方便按业务模块浏览。

- **链接状态变更通知**：当批量探测发现链接状态从可用变为不可用时，支持通过 Webhook 或邮件方式向订阅者发送告警通知。

- **资源清单导出**：支持将当前批次或全量资源列表导出为 Markdown 表格、JSON 结构化数据或纯文本列表，便于嵌入其他文档系统。

- **批次管理**：每批导入的资源独立存储批次号（如 175/200）、导入时间、链接总数与异常率，支持按批次回滚或重新校验。

## 应用场景

1. **技术文档站点外链健康检查**：技术文档中通常引用大量外部资源链接（CDN、API 参考、SDK 下载地址）。使用 LinkPilot 可定期扫描这些链接，及时发现失效引用并通知文档维护者更新。

2. **开源项目 README 资源清单维护**：开源项目 README 中常列有大量相关工具、镜像站或社区资源链接，手工维护成本高。LinkPilot 可导入这些链接并生成标准化的资源列表章节，减少手动排版错误。

3. **移动端 H5 页面资源聚合导航**：移动端 H5 运营活动页常需引用多个第三方统计、分享、地图或支付组件。LinkPilot 可归集这些组件地址，并通过可达性探测预判上游服务可用性，降低线上故障风险。

4. **企业内部知识库外链审计**：企业 Confluence、Notion 或 GitLab Wiki 中存在大量外部链接，合规与安全团队需定期审计这些外链的合法性及可用性。LinkPilot 提供批量探测与审计日志功能，满足内控需求。

5. **静态站点生成器（如 Hugo、VuePress）的链接预处理**：在静态站点构建流程中嵌入 LinkPilot，可在构建前对全部外链做一次快速可达性检查，若发现高危不可用链接则中断构建并输出警告，保障站点质量。

## 快速开始

以下指令适用于 Linux / macOS / Windows WSL 环境，依赖 Git、Node.js 20.x 及 npm。

```bash
# 克隆主仓库
git clone https://github.com/your-org/linkpilot.git

# 进入项目目录
cd linkpilot

# 安装项目依赖（包括核心探测引擎与 CLI 工具）
npm install

# 运行批次导入示例（默认加载 data/batch_175_200.json）
npm run import -- --batch 175

# 启动本地开发服务器，查看资源列表与状态面板
npm run dev
```

执行上述命令后，LinkPilot 将在本地 3000 端口启动 Web 界面，可通过浏览器访问 http://localhost:3000 查看第 175/200 批资源的收录情况与实时探测状态。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 20.x 或更高 | 运行时环境，需支持 ES2022 特性与原生 fetch API |
| npm | 9.x 或更高 | 包管理器，用于安装依赖与执行脚本 |
| Git | 2.30 或更高 | 版本控制工具，用于克隆仓库及管理分支 |
| SQLite | 3.40 或更高 | 嵌入式数据库，用于存储链接元数据与探测历史（生产环境可换 PostgreSQL） |
| curl / wget | 任意较新版本 | 探测引擎底层依赖，用于执行实际 HTTP 请求（备选 fallback 模式） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide/import.md | 如何导入新批次资源、如何为链接添加分类标签、如何导出清单 |
| 运维指南 | docs/ops/deployment.md | 如何部署至生产环境（Docker / K8s / 裸机）、如何配置探测周期与告警 |
| 开发指南 | docs/dev/architecture.md | 项目整体模块划分、核心数据流、扩展探测器的接口规范 |
| API 参考 | docs/api/endpoints.md | 提供的 RESTful API 列表、请求参数与响应示例（含批量导入接口） |
| 批次管理 | docs/batch/batch_175.md | 当前批次资源统计、异常链接列表、人工复核建议 |

## 资源列表

- http://map.mobile.fuvxie.cn/Article/details/3528.sHtML
- http://map.mobile.fuvxie.cn/Article/details/01827.sHtML
- http://map.mobile.fuvxie.cn/Article/details/9327290.sHtML
- http://map.mobile.fuvxie.cn/Article/details/8022024.sHtML
- http://map.mobile.fuvxie.cn/Article/details/5514.sHtML
- http://map.mobile.fuvxie.cn/Article/details/932297.sHtML
- http://map.mobile.fuvxie.cn/Article/details/87934.sHtML
- http://map.mobile.fuvxie.cn/Article/details/874369.sHtML
- http://map.mobile.fuvxie.cn/Article/details/77713.sHtML
- http://map.mobile.fuvxie.cn/Article/details/5311189.sHtML
- http://map.mobile.fuvxie.cn/Article/details/3311274.sHtML
- http://map.mobile.fuvxie.cn/Article/details/3477.sHtML
- http://map.mobile.fuvxie.cn/Article/details/5249658.sHtML
- http://map.mobile.fuvxie.cn/Article/details/59941.sHtML
- http://map.mobile.fuvxie.cn/Article/details/7574717.sHtML
- http://map.mobile.fuvxie.cn/Article/details/456319.sHtML
- http://map.mobile.fuvxie.cn/Article/details/35357.sHtML
- http://map.mobile.fuvxie.cn/Article/details/272482.sHtML
- http://map.mobile.fuvxie.cn/Article/details/92828.sHtML
- http://map.mobile.fuvxie.cn/Article/details/61230.sHtML
- http://map.mobile.fuvxie.cn/Article/details/756120.sHtML
- http://map.mobile.fuvxie.cn/Article/details/135729.sHtML
- http://map.mobile.fuvxie.cn/Article/details/0617652.sHtML
- http://map.mobile.fuvxie.cn/Article/details/7063838.sHtML
- http://map.mobile.fuvxie.cn/Article/details/1200725.sHtML
- http://map.mobile.fuvxie.cn/Article/details/6136870.sHtML
- http://map.mobile.fuvxie.cn/Article/details/32050.sHtML
- http://map.mobile.fuvxie.cn/Article/details/602112.sHtML
- http://map.mobile.fuvxie.cn/Article/details/2236.sHtML
- http://map.mobile.fuvxie.cn/Article/details/407432.sHtML
- http://map.mobile.fuvxie.cn/Article/details/9757.sHtML
- http://map.mobile.fuvxie.cn/Article/details/61862.sHtML
- http://map.mobile.fuvxie.cn/Article/details/1181417.sHtML
- http://map.mobile.fuvxie.cn/Article/details/0677669.sHtML
- http://map.mobile.fuvxie.cn/Article/details/435278.sHtML
- http://map.mobile.fuvxie.cn/Article/details/635958.sHtML
- http://map.mobile.fuvxie.cn/Article/details/4451.sHtML
- http://map.mobile.fuvxie.cn/Article/details/2089.sHtML
- http://map.mobile.fuvxie.cn/Article/details/9366.sHtML
- http://map.mobile.fuvxie.cn/Article/details/767812.sHtML
- http://map.mobile.fuvxie.cn/Article/details/2142.sHtML
- http://map.mobile.fuvxie.cn/Article/details/3552599.sHtML
- http://map.mobile.fuvxie.cn/Article/details/8134184.sHtML
- http://map.mobile.fuvxie.cn/Article/details/95774.sHtML
- http://map.mobile.fuvxie.cn/Article/details/2257105.sHtML
- http://map.mobile.fuvxie.cn/Article/details/30532.sHtML
- http://map.mobile.fuvxie.cn/Article/details/3089291.sHtML
- http://map.mobile.fuvxie.cn/Article/details/895935.sHtML
- http://map.mobile.fuvxie.cn/Article/details/1501.sHtML
- http://map.mobile.fuvxie.cn/Article/details/97739.sHtML
- http://map.mobile.fuvxie.cn/Article/details/5013.sHtML
- http://map.mobile.fuvxie.cn/Article/details/316301.sHtML
- http://map.mobile.fuvxie.cn/Article/details/8749.sHtML
- http://map.mobile.fuvxie.cn/Article/details/638258.sHtML
- http://map.mobile.fuvxie.cn/Article/details/80595.sHtML
- http://map.mobile.fuvxie.cn/Article/details/4728.sHtML
- http://map.mobile.fuvxie.cn/Article/details/77345.sHtML
- http://map.mobile.fuvxie.cn/Article/details/467687.sHtML
- http://map.mobile.fuvxie.cn/Article/details/472761.sHtML
- http://map.mobile.fuvxie.cn/Article/details/8981852.sHtML
- http://map.mobile.fuvxie.cn/Article/details/846840.sHtML
- http://map.mobile.fuvxie.cn/Article/details/69728.sHtML
- http://map.mobile.fuvxie.cn/Article/details/814615.sHtML
- http://map.mobile.fuvxie.cn/Article/details/508171.sHtML
- http://map.mobile.fuvxie.cn/Article/details/5181984.sHtML
- http://map.mobile.fuvxie.cn/Article/details/244446.sHtML
- http://map.mobile.fuvxie.cn/Article/details/414522.sHtML
- http://map.mobile.fuvxie.cn/Article/details/6682149.sHtML
- http://map.mobile.fuvxie.cn/Article/details/65575.sHtML
- http://map.mobile.fuvxie.cn/Article/details/3335.sHtML
- http://map.mobile.fuvxie.cn/Article/details/123294.sHtML
- http://map.mobile.fuvxie.cn/Article/details/6239.sHtML
- http://map.mobile.fuvxie.cn/Article/details/614224.sHtML
- http://map.mobile.fuvxie.cn/Article/details/26505.sHtML
- http://map.mobile.fuvxie.cn/Article/details/0191.sHtML
- http://map.mobile.fuvxie.cn/Article/details/6478780.sHtML
- http://map.mobile.fuvxie.cn/Article/details/5010.sHtML
- http://map.mobile.fuvxie.cn/Article/details/62612.sHtML
- http://map.mobile.fuvxie.cn/Article/details/0562453.sHtML
- http://map.mobile.fuvxie.cn/Article/details/06204.sHtML
- http://map.mobile.fuvxie.cn/Article/details/7003797.sHtML
- http://map.mobile.fuvxie.cn/Article/details/2266.sHtML
- http://map.mobile.fuvxie.cn/Article/details/4327363.sHtML
- http://map.mobile.fuvxie.cn/Article/details/4781477.sHtML
- http://map.mobile.fuvxie.cn/Article/details/0755686.sHtML
- http://map.mobile.fuvxie.cn/Article/details/53141.sHtML
- http://map.mobile.fuvxie.cn/Article/details/6795905.sHtML
- http://map.mobile.fuvxie.cn/Article/details/8540451.sHtML
- http://map.mobile.fuvxie.cn/Article/details/3697.sHtML
- http://map.mobile.fuvxie.cn/Article/details/6509.sHtML
- http://map.mobile.fuvxie.cn/Article/details/2796.sHtML
- http://map.mobile.fuvxie.cn/Article/details/57495.sHtML
- http://map.mobile.fuvxie.cn/Article/details/8804697.sHtML
- http://map.mobile.fuvxie.cn/Article/details/2786.sHtML
- http://map.mobile.fuvxie.cn/Article/details/7414.sHtML
- http://map.mobile.fuvxie.cn/Article/details/7383624.sHtML
- http://map.mobile.fuvxie.cn/Article/details/340710.sHtML
- http://map.mobile.fuvxie.cn/Article/details/6250231.sHtML
- http://map.mobile.fuvxie.cn/Article/details/1375.sHtML
- http://map.mobile.fuvxie.cn/Article/details/37951.sHtML
- http://map.mobile.fuvxie.cn/Article/details/0124.sHtML
- http://map.mobile.fuvxie.cn/Article/details/2035.sHtML
- http://map.mobile.fuvxie.cn/Article/details/95695.sHtML
- http://map.mobile.fuvxie.cn/Article/details/59604.sHtML
- http://map.mobile.fuvxie.cn/Article/details/85892.sHtML
- http://map.mobile.fuvxie.cn/Article/details/223631.sHtML
- http://map.mobile.fuvxie.cn/Article/details/403475.sHtML
- http://map.mobile.fuvxie.cn/Article/details/6834299.sHtML
- http://map.mobile.fuvxie.cn/Article/details/85390.sHtML
- http://map.mobile.fuvxie.cn/Article/details/7694552.sHtML
- http://map.mobile.fuvxie.cn/Article/details/9517443.sHtML
- http://map.mobile.fuvxie.cn/Article/details/1061.sHtML
- http://map.mobile.fuvxie.cn/Article/details/578862.sHtML
- http://map.mobile.fuvxie.cn/Article/details/59874.sHtML
- http://map.mobile.fuvxie.cn/Article/details/0672.sHtML
- http://map.mobile.fuvxie.cn/Article/details/7043552.sHtML
- http://map.mobile.fuvxie.cn/Article/details/31340.sHtML
- http://map.mobile.fuvxie.cn/Article/details/5512065.sHtML
- http://map.mobile.fuvxie.cn/Article/details/4207.sHtML
- http://map.mobile.fuvxie.cn/Article/details/23985.sHtML
- http://map.mobile.fuvxie.cn/Article/details/5205960.sHtML
- http://map.mobile.fuvxie.cn/Article/details/13254.sHtML
- http://map.mobile.fuvxie.cn/Article/details/1143.sHtML
- http://map.mobile.fuvxie.cn/Article/details/72272.sHtML
- http://map.mobile.fuvxie.cn/Article/details/1193601.sHtML
- http://map.mobile.fuvxie.cn/Article/details/2200.sHtML
- http://map.mobile.fuvxie.cn/Article/details/8025210.sHtML
- http://map.mobile.fuvxie.cn/Article/details/8163602.sHtML
- http://map.mobile.fuvxie.cn/Article/details/4660.sHtML
- http://map.mobile.fuvxie.cn/Article/details/9163.sHtML
- http://map.mobile.fuvxie.cn/Article/details/46560.sHtML
- http://map.mobile.fuvxie.cn/Article/details/405098.sHtML
- http://map.mobile.fuvxie.cn/Article/details/8185.sHtML
- http://map.mobile.fuvxie.cn/Article/details/3254.sHtML
- http://map.mobile.fuvxie.cn/Article/details/11554.sHtML
- http://map.mobile.fuvxie.cn/Article/details/57965.sHtML
- http://map.mobile.fuvxie.cn/Article/details/1546730.sHtML
- http://map.mobile.fuvxie.cn/Article/details/222618.sHtML
- http://map.mobile.fuvxie.cn/Article/details/5085169.sHtML
- http://map.mobile.fuvxie.cn/Article/details/573621.sHtML
- http://map.mobile.fuvxie.cn/Article/details/1172059.sHtML
- http://map.mobile.fuvxie.cn/Article/details/32092.sHtML
- http://map.mobile.fuvxie.cn/Article/details/5374.sHtML
- http://map.mobile.fuvxie.cn/Article/details/821313.sHtML
- http://map.mobile.fuvxie.cn/Article/details/72564.sHtML
- http://map.mobile.fuvxie.cn/Article/details/7683623.sHtML
- http://map.mobile.fuvxie.cn/Article/details/2948.sHtML
- http://map.mobile.fuvxie.cn/Article/details/7816.sHtML
- http://map.mobile.fuvxie.cn/Article/details/844740.sHtML
- http://map.mobile.fuvxie.cn/Article/details/9182.sHtML
- http://map.mobile.fuvxie.cn/Article/details/60282.sHtML
- http://map.mobile.fuvxie.cn/Article/details/29152.sHtML
- http://map.mobile.fuvxie.cn/Article/details/54740.sHtML
- http://map.mobile.fuvxie.cn/Article/details/4446.sHtML
- http://map.mobile.fuvxie.cn/Article/details/6313191.sHtML
- http://map.mobile.fuvxie.cn/Article/details/6858.sHtML
- http://map.mobile.fuvxie.cn/Article/details/94445.sHtML
- http://map.mobile.fuvxie.cn/Article/details/26814.sHtML
- http://map.mobile.fuvxie.cn/Article/details/0275588.sHtML
- http://map.mobile.fuvxie.cn/Article/details/079888.sHtML
- http://map.mobile.fuvxie.cn/Article/details/1191.sHtML
- http://map.mobile.fuvxie.cn/Article/details/401347.sHtML
- http://map.mobile.fuvxie.cn/Article/details/252151.sHtML
- http://map.mobile.fuvxie.cn/Article/details/7565341.sHtML
- http://map.mobile.fuvxie.cn/Article/details/38329.sHtML
- http://map.mobile.fuvxie.cn/Article/details/623660.sHtML
- http://map.mobile.fuvxie.cn/Article/details/96043.sHtML
- http://map.mobile.fuvxie.cn/Article/details/83537.sHtML
- http://map.mobile.fuvxie.cn/Article/details/075385.sHtML
- http://map.mobile.fuvxie.cn/Article/details/44719.sHtML
- http://map.mobile.fuvxie.cn/Article/details/3286917.sHtML
- http://map.mobile.fuvxie.cn/Article/details/519528.sHtML
- http://map.mobile.fuvxie.cn/Article/details/92720.sHtML
- http://map.mobile.fuvxie.cn/Article/details/19791.sHtML
- http://map.mobile.fuvxie.cn/Article/details/68364.sHtML
- http://map.mobile.fuvxie.cn/Article/details/3442.sHtML
- http://map.mobile.fuvxie.cn/Article/details/9391208.sHtML
- http://map.mobile.fuvxie.cn/Article/details/39116.sHtML
- http://map.mobile.fuvxie.cn/Article/details/31495.sHtML
- http://map.mobile.fuvxie.cn/Article/details/91981.sHtML
- http://map.mobile.fuvxie.cn/Article/details/9745191.sHtML
- http://map.mobile.fuvxie.cn/Article/details/346789.sHtML
- http://map.mobile.fuvxie.cn/Article/details/2534167.sHtML
- http://map.mobile.fuvxie.cn/Article/details/920216.sHtML
- http://map.mobile.fuvxie.cn/Article/details/2135968.sHtML
- http://map.mobile.fuvxie.cn/Article/details/4132.sHtML
- http://map.mobile.fuvxie.cn/Article/details/8236105.sHtML
- http://map.mobile.fuvxie.cn/Article/details/3926273.sHtML
- http://map.mobile.fuvxie.cn/Article/details/96344.sHtML
- http://map.mobile.fuvxie.cn/Article/details/35861.sHtML
- http://map.mobile.fuvxie.cn/Article/details/32011.sHtML
- http://map.mobile.fuvxie.cn/Article/details/9315248.sHtML
- http://map.mobile.fuvxie.cn/Article/details/842371.sHtML
- http://map.mobile.fuvxie.cn/Article/details/80632.sHtML
- http://map.mobile.fuvxie.cn/Article/details/112164.sHtML
- http://map.mobile.fuvxie.cn/Article/details/27601.sHtML
- http://map.mobile.fuvxie.cn/Article/details/0137.sHtML
- http://map.mobile.fuvxie.cn/Article/details/029412.sHtML
- http://map.mobile.fuvxie.cn/Article/details/6563017.sHtML
- http://map.mobile.fuvxie.cn/Article/details/0121183.sHtML
- http://map.mobile.fuvxie.cn/Article/details/45590.sHtML
- http://map.mobile.fuvxie.cn/Article/details/8204933.sHtML
- http://map.mobile.fuvxie.cn/Article/details/8254.sHtML
- http://map.mobile.fuvxie.cn/Article/details/52801.sHtML
- http://map.mobile.fuvxie.cn/Article/details/63499.sHtML
- http://map.mobile.fuvxie.cn/Article/details/0536.sHtML
- http://map.mobile.fuvxie.cn/Article/details/4056743.sHtML
- http://map.mobile.fuvxie.cn/Article/details/34608.sHtML
- http://map.mobile.fuvxie.cn/Article/details/424586.sHtML
- http://map.mobile.fuvxie.cn/Article/details/19051.sHtML
- http://map.mobile.fuvxie.cn/Article/details/64959.sHtML
- http://map.mobile.fuvxie.cn/Article/details/7602.sHtML
- http://map.mobile.fuvxie.cn/Article/details/0191224.sHtML
- http://map.mobile.fuvxie.cn/Article/details/38149.sHtML
- http://map.mobile.fuvxie.cn/Article/details/624789.sHtML
- http://map.mobile.fuvxie.cn/Article/details/2270421.sHtML
- http://map.mobile.fuvxie.cn/Article/details/9403884.sHtML
- http://map.mobile.fuvxie.cn/Article/details/90495.sHtML
- http://map.mobile.fuvxie.cn/Article/details/8474092.sHtML
- http://map.mobile.fuvxie.cn/Article/details/7153585.sHtML
- http://map.mobile.fuvxie.cn/Article/details/8489134.sHtML
- http://map.mobile.fuvxie.cn/Article/details/4623412.sHtML
- http://map.mobile.fuvxie.cn/Article/details/5652.sHtML
- http://map.mobile.fuvxie.cn/Article/details/193274.sHtML
- http://map.mobile.fuvxie.cn/Article/details/1683.sHtML
- http://map.mobile.fuvxie.cn/Article/details/023526.sHtML
- http://map.mobile.fuvxie.cn/Article/details/7494126.sHtML
- http://map.mobile.fuvxie.cn/Article/details/8239.sHtML
- http://map.mobile.fuvxie.cn/Article/details/55001.sHtML
- http://map.mobile.fuvxie.cn/Article/details/69533.sHtML
- http://map.mobile.fuvxie.cn/Article/details/1454.sHtML
- http://map.mobile.fuvxie.cn/Article/details/0063.sHtML
- http://map.mobile.fuvxie.cn/Article/details/4552.sHtML
- http://map.mobile.fuvxie.cn/Article/details/685780.sHtML
- http://map.mobile.fuvxie.cn/Article/details/04507.sHtML
- http://map.mobile.fuvxie.cn/Article/details/4372545.sHtML
- http://map.mobile.fuvxie.cn/Article/details/28744.sHtML
- http://map.mobile.fuvxie.cn/Article/details/2033604.sHtML
- http://map.mobile.fuvxie.cn/Article/details/2590303.sHtML
- http://map.mobile.fuvxie.cn/Article/details/5872.sHtML
- http://map.mobile.fuvxie.cn/Article/details/53032.sHtML
- http://map.mobile.fuvxie.cn/Article/details/99762.sHtML
- http://map.mobile.fuvxie.cn/Article/details/1996851.sHtML
- http://map.mobile.fuvxie.cn/Article/details/1733957.sHtML
- http://map.mobile.fuvxie.cn/Article/details/84590.sHtML
- http://map.mobile.fuvxie.cn/Article/details/2994110.sHtML
- http://map.mobile.fuvxie.cn/Article/details/29286.sHtML
- http://map.mobile.fuvxie.cn/Article/details/7406628.sHtML
- http://map.mobile.fuvxie.cn/Article/details/9512.sHtML
- http://map.mobile.fuvxie.cn/Article/details/9548.sHtML

## 项目结构

```text
linkpilot/
├── src/                                # 核心源码目录
│   ├── core/                           # 核心引擎模块
│   │   ├── crawler.js                  # 链接探测与状态抓取逻辑
│   │   ├── dedup.js                    # 基于 URL 完整字符串的去重算法
│   │   └── batch_loader.js             # 批次 JSON 文件加载与校验
│   ├── api/                            # RESTful API 路由层
│   │   ├── import.js                   # 批量导入接口
│   │   ├── status.js                   # 链接状态查询接口
│   │   └── export.js                   # 清单导出接口（json / md / txt）
│   ├── db/                             # 数据库访问层
│   │   ├── sqlite_adapter.js           # SQLite 初始化与 CRUD 操作
│   │   └── migration.js                # 表结构版本管理
│   ├── cli/                            # 命令行工具入口
│   │   ├── index.js                    # CLI 主命令路由
│   │   └── commands/                   # 子命令实现（import / check / export）
│   └── web/                            # 内置 Web 控制台
│       ├── routes/                     # 页面路由
│       └── static/                     # 前端静态资源（CSS / JS）
├── data/                               # 数据目录
│   ├── batches/                        # 批次定义 JSON 文件
│   │   └── batch_175_200.json          # 第 175/200 批资源定义（含 250 条链接）
│   └── reports/                        # 探测报告输出目录
│       └── 2026-07-06.md               # 按日期生成的 Markdown 格式报告
├── docs/                               # 项目文档（详见文档导航）
│   ├── user-guide/                     # 用户手册
│   ├── ops/                            # 运维指南
│   ├── dev/                            # 开发指南
│   └── api/                            # API 参考
├── tests/                              # 单元测试与集成测试
│   ├── unit/                           # 核心函数单元测试（Jest）
│   └── e2e/                            # 端到端探测流程测试
├── scripts/                            # 辅助脚本
│   ├── pre-commit-hook.sh              # Git 提交前检查
│   └── seed-demo-data.sh               # 填充演示数据
├── .env.example                        # 环境变量模板（含探测超时、告警 webhook 等）
├── docker-compose.yml                  # 本地开发环境编排（含 SQLite + 探测 worker）
├── Dockerfile                          # 生产镜像构建定义（基于 node:20-alpine）
├── package.json                        # npm 依赖声明与脚本定义
├── README.md                           # 本文件
└── LICENSE                             # MIT 许可证
```

## 贡献指南

1. 复刻主仓库至个人账号，并在本地新建功能分支（如 `feat/batch-import-optimize`），所有开发工作均在该分支上进行，禁止直接向主分支提交。

2. 在 `data/batches/` 目录下按批次模板新增或修改资源定义文件，遵循 JSON Schema 校验（包含 `batchId`、`source`、`links` 数组字段），并通过 `npm run validate` 检查格式合法性。

3. 提交代码前运行完整测试套件 `npm test`，确保单元测试与集成测试通过率 100%，同时使用 `npm run lint` 统一代码风格（ESLint + Prettier）。

4. 发起 Pull Request 至主仓库的 `main` 分支，PR 描述中需注明本次变更的批次号、新增链接数量、是否涉及探测逻辑改动，并附上本地手动验证截图或日志。

5. 项目维护者将在 48 小时内完成 Code Review，若涉及外部依赖变更或数据库表结构调整，需额外补充迁移脚本与回滚方案。

## 常见问题

**问：LinkPilot 是否会篡改或重新编码用户提交的 URL？**

答：不会。LinkPilot 对所有 URL 采用原样存储策略，包括协议头（http 或 https）、域名大小写、路径大小写以及文件扩展名后缀（如 .sHtML）。系统不做任何自动补全、大小写归一化或协议升级处理，完全保留用户输入的原始字符串，以保证与源站资源定位方式完全一致。

**问：如何自定义链接探测的并发数和超时时间？**

答：探测引擎的并发数（默认 10）和单次请求超时时间（默认 5000ms）可通过项目根目录下的 `.env` 文件调整，对应环境变量为 `PROBE_CONCURRENCY` 和 `PROBE_TIMEOUT_MS`。修改后需重启服务或重新执行 CLI 命令方可生效。

**问：已导入的链接如何更新元数据（如分类标签或备注）？**

答：可通过 Web 控制台逐条编辑，也可通过批处理接口 `POST /api/batch/update` 提交增量更新 JSON 文件。更新操作会保留原始 URL 字符串不变，仅修改附加属性字段。若需彻底删除某条链接，建议使用 `DELETE /api/links/{id}` 接口并注明删除原因，系统会记录审计日志。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 02:14:16
