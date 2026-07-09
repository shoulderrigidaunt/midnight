# H5 Read Resource Aggregator

H5 Read Resource Aggregator 是一个面向移动端阅读内容聚合与分发场景的技术资源导航项目。项目定位于收集、整理并结构化呈现来自多个内容源的高价值技术文章与开发文档链接，为前端开发者、移动端工程师以及技术决策者提供系统化的外链参考体系。

项目本身不存储任何实体内容，仅作为索引层与路由层，通过规范化 URL 收录与分类标签体系，解决技术阅读资源碎片化、检索效率低下以及跨源内容难以统一管理的问题。适用于个人知识库构建、团队技术选型参考以及自动化内容采集管道的种子数据源。

## 功能概览

多源链接统一收录：支持从不同域名与路径结构的内容源批量导入链接，自动识别来源域名并保留完整原始 URL。

分类标签自动推断：基于 URL 路径特征与数字 ID 区间，对收录链接进行技术领域、文章类型与内容层级的自动标记。

链接状态巡检：定期对收录链接进行 HTTP 状态码检测，标记失效链接并生成报告，保证资源库的可用性。

全文元数据提取：从目标页面自动提取标题、发布时间、作者与摘要信息，构建结构化索引字段。

批量导入导出：支持 CSV 与 JSON 格式的链接批量导入，以及按筛选条件导出指定集合。

RESTful API 查询接口：提供基于标签、域名、时间范围的组合查询接口，便于与其他系统集成。

静态站点生成模式：支持将链接集合渲染为静态 HTML 导航页面，可直接部署于 Nginx 或 CDN。

## 应用场景

技术团队内部知识库构建：团队成员在日常阅读中发现的优质技术文章，可通过本项目提供的导入接口统一收录，并按标签分类，形成团队共享的阅读资源池。新人入职时可快速浏览团队沉淀的推荐阅读列表。

个人开发者的阅读工作流管理：开发者可将不同来源的技术博客、官方文档链接集中管理，通过标签过滤快速定位特定主题（如 React 性能优化、Kubernetes 调度策略）的参考材料，避免重复搜索。

自动化内容采集管道的数据源：数据采集系统可将本项目导出的链接列表作为起始种子 URL，批量抓取页面内容进行全文检索、关键词提取或文本分析，用于构建技术趋势分析报表。

技术文档归档前的链接核查：在进行技术文档或项目 README 编写时，通过本项目的链接状态巡检功能，批量验证所有引用外链的有效性，提前发现并替换失效引用。

## 快速开始

以下命令可在 Ubuntu 22.04 / macOS 13 及以上环境中完成项目的克隆、安装与启动。

```bash
git clone https://github.com/read-resource/h5-read-aggregator.git
cd h5-read-aggregator
npm install
npm run build
npm start
```

启动后服务默认监听 3000 端口，可通过 `http://127.0.0.1:3000/api/links` 访问链接列表接口。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Node.js | 18.x 或 20.x LTS | 运行时环境，建议使用 nvm 管理 |
| npm | 9.x 或 10.x | 包管理器，用于安装项目依赖 |
| SQLite3 | 3.39 或更高 | 嵌入式数据库，用于存储链接索引 |
| PM2 | 5.x（可选） | 生产环境进程守护，非开发必需 |
| curl / wget | 任意版本 | 用于链接状态巡检的外部工具调用 |
| git | 2.25 或更高 | 版本控制，用于克隆仓库 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user-guide.md | 如何使用导入导出功能、如何配置标签规则、如何生成静态站点 |
| 管理员手册 | docs/admin-guide.md | 如何部署到生产服务器、如何设置定时巡检任务、如何备份数据库 |
| API 参考 | docs/api-reference.md | 各接口的请求参数、响应格式、状态码含义与错误处理方式 |
| 架构设计 | docs/architecture.md | 系统模块划分、数据流走向、扩展点设计与性能考量 |

## 资源列表

- http://h5.read.aovdbk.cn/Article/1099162.shtml
- http://h5.read.aovdbk.cn/Article/41636.shtml
- http://h5.read.zdvgjr.cn/Article/337639.shtml
- http://h5.read.aovdbk.cn/Article/4131909.shtml
- http://h5.read.zdvgjr.cn/Article/73287.shtml
- http://h5.read.aovdbk.cn/Article/6921479.shtml
- http://h5.read.zdvgjr.cn/Article/782878.shtml
- http://h5.read.zdvgjr.cn/Article/55780.shtml
- http://h5.read.zdvgjr.cn/Article/924985.shtml
- http://h5.read.zdvgjr.cn/Article/1118.shtml
- http://h5.read.zdvgjr.cn/Article/692809.shtml
- http://h5.read.aovdbk.cn/Article/018990.shtml
- http://h5.read.aovdbk.cn/Article/4801050.shtml
- http://h5.read.zdvgjr.cn/Article/773091.shtml
- http://h5.read.zdvgjr.cn/Article/14510.shtml
- http://h5.read.zdvgjr.cn/Article/66401.shtml
- http://h5.read.zdvgjr.cn/Article/503693.shtml
- http://h5.read.zdvgjr.cn/Article/9977736.shtml
- http://h5.read.aovdbk.cn/Article/80972.shtml
- http://h5.read.zdvgjr.cn/Article/7739399.shtml
- http://h5.read.zdvgjr.cn/Article/1357336.shtml
- http://h5.read.aovdbk.cn/Article/946914.shtml
- http://h5.read.zdvgjr.cn/Article/1340962.shtml
- http://h5.read.aovdbk.cn/Article/47842.shtml
- http://h5.read.zdvgjr.cn/Article/6654587.shtml
- http://h5.read.zdvgjr.cn/Article/4917.shtml
- http://h5.read.zdvgjr.cn/Article/9193.shtml
- http://h5.read.aovdbk.cn/Article/862084.shtml
- http://h5.read.aovdbk.cn/Article/6497.shtml
- http://h5.read.aovdbk.cn/Article/8694.shtml
- http://h5.read.aovdbk.cn/Article/058813.shtml
- http://h5.read.zdvgjr.cn/Article/19170.shtml
- http://h5.read.aovdbk.cn/Article/372060.shtml
- http://h5.read.aovdbk.cn/Article/1849149.shtml
- http://h5.read.aovdbk.cn/Article/8756889.shtml
- http://h5.read.zdvgjr.cn/Article/87031.shtml
- http://h5.read.aovdbk.cn/Article/380147.shtml
- http://h5.read.zdvgjr.cn/Article/0062839.shtml
- http://h5.read.zdvgjr.cn/Article/9367.shtml
- http://h5.read.aovdbk.cn/Article/963394.shtml
- http://h5.read.zdvgjr.cn/Article/0455.shtml
- http://h5.read.aovdbk.cn/Article/16502.shtml
- http://h5.read.zdvgjr.cn/Article/7468.shtml
- http://h5.read.aovdbk.cn/Article/40035.shtml
- http://h5.read.aovdbk.cn/Article/8663154.shtml
- http://h5.read.zdvgjr.cn/Article/3023.shtml
- http://h5.read.zdvgjr.cn/Article/36781.shtml
- http://h5.read.aovdbk.cn/Article/63276.shtml
- http://h5.read.aovdbk.cn/Article/6272.shtml
- http://h5.read.aovdbk.cn/Article/18629.shtml
- http://h5.read.zdvgjr.cn/Article/5491.shtml
- http://h5.read.aovdbk.cn/Article/875303.shtml
- http://h5.read.aovdbk.cn/Article/9014.shtml
- http://h5.read.aovdbk.cn/Article/5030.shtml
- http://h5.read.aovdbk.cn/Article/420954.shtml
- http://h5.read.aovdbk.cn/Article/408421.shtml
- http://h5.read.aovdbk.cn/Article/81476.shtml
- http://h5.read.aovdbk.cn/Article/850962.shtml
- http://h5.read.aovdbk.cn/Article/5663.shtml
- http://h5.read.aovdbk.cn/Article/111965.shtml
- http://h5.read.zdvgjr.cn/Article/31330.shtml
- http://h5.read.zdvgjr.cn/Article/048970.shtml
- http://h5.read.aovdbk.cn/Article/417386.shtml
- http://h5.read.aovdbk.cn/Article/96040.shtml
- http://h5.read.aovdbk.cn/Article/6278288.shtml
- http://h5.read.aovdbk.cn/Article/111500.shtml
- http://h5.read.aovdbk.cn/Article/5592.shtml
- http://h5.read.zdvgjr.cn/Article/60298.shtml
- http://h5.read.zdvgjr.cn/Article/18463.shtml
- http://h5.read.zdvgjr.cn/Article/7119902.shtml
- http://h5.read.aovdbk.cn/Article/40353.shtml
- http://h5.read.zdvgjr.cn/Article/4289489.shtml
- http://h5.read.aovdbk.cn/Article/7825.shtml
- http://h5.read.zdvgjr.cn/Article/8705602.shtml
- http://h5.read.aovdbk.cn/Article/13856.shtml
- http://h5.read.aovdbk.cn/Article/3708572.shtml
- http://h5.read.aovdbk.cn/Article/821539.shtml
- http://h5.read.aovdbk.cn/Article/9583048.shtml
- http://h5.read.aovdbk.cn/Article/0969071.shtml
- http://h5.read.zdvgjr.cn/Article/8535.shtml
- http://h5.read.aovdbk.cn/Article/76807.shtml
- http://h5.read.zdvgjr.cn/Article/8635459.shtml
- http://h5.read.zdvgjr.cn/Article/2667.shtml
- http://h5.read.zdvgjr.cn/Article/4800299.shtml
- http://h5.read.aovdbk.cn/Article/9457.shtml
- http://h5.read.zdvgjr.cn/Article/67102.shtml
- http://h5.read.aovdbk.cn/Article/64961.shtml
- http://h5.read.aovdbk.cn/Article/197916.shtml
- http://h5.read.zdvgjr.cn/Article/35120.shtml
- http://h5.read.zdvgjr.cn/Article/561577.shtml
- http://h5.read.aovdbk.cn/Article/4918.shtml
- http://h5.read.zdvgjr.cn/Article/9935.shtml
- http://h5.read.aovdbk.cn/Article/3700004.shtml
- http://h5.read.aovdbk.cn/Article/011117.shtml
- http://h5.read.aovdbk.cn/Article/5420442.shtml
- http://h5.read.aovdbk.cn/Article/9144.shtml
- http://h5.read.zdvgjr.cn/Article/532857.shtml
- http://h5.read.zdvgjr.cn/Article/0032673.shtml
- http://h5.read.zdvgjr.cn/Article/89958.shtml
- http://h5.read.aovdbk.cn/Article/01632.shtml
- http://h5.read.aovdbk.cn/Article/1480.shtml
- http://h5.read.aovdbk.cn/Article/1270218.shtml
- http://h5.read.aovdbk.cn/Article/4738580.shtml
- http://h5.read.aovdbk.cn/Article/13667.shtml
- http://h5.read.aovdbk.cn/Article/0333396.shtml
- http://h5.read.zdvgjr.cn/Article/085252.shtml
- http://h5.read.aovdbk.cn/Article/6848177.shtml
- http://h5.read.aovdbk.cn/Article/3356822.shtml
- http://h5.read.aovdbk.cn/Article/498216.shtml
- http://h5.read.zdvgjr.cn/Article/119777.shtml
- http://h5.read.zdvgjr.cn/Article/04384.shtml
- http://h5.read.aovdbk.cn/Article/1272.shtml
- http://h5.read.zdvgjr.cn/Article/0257420.shtml
- http://h5.read.aovdbk.cn/Article/8968.shtml
- http://h5.read.zdvgjr.cn/Article/42752.shtml
- http://h5.read.zdvgjr.cn/Article/1598.shtml
- http://h5.read.aovdbk.cn/Article/0881122.shtml
- http://h5.read.zdvgjr.cn/Article/121150.shtml
- http://h5.read.zdvgjr.cn/Article/781942.shtml
- http://h5.read.zdvgjr.cn/Article/54108.shtml
- http://h5.read.aovdbk.cn/Article/987084.shtml
- http://h5.read.zdvgjr.cn/Article/9036.shtml
- http://h5.read.zdvgjr.cn/Article/4806.shtml
- http://h5.read.zdvgjr.cn/Article/222507.shtml
- http://h5.read.zdvgjr.cn/Article/407642.shtml
- http://h5.read.aovdbk.cn/Article/4511377.shtml
- http://h5.read.zdvgjr.cn/Article/997651.shtml
- http://h5.read.aovdbk.cn/Article/0900.shtml
- http://h5.read.zdvgjr.cn/Article/0367944.shtml
- http://h5.read.aovdbk.cn/Article/2176001.shtml
- http://h5.read.aovdbk.cn/Article/179131.shtml
- http://h5.read.aovdbk.cn/Article/652302.shtml
- http://h5.read.aovdbk.cn/Article/2914884.shtml
- http://h5.read.aovdbk.cn/Article/058648.shtml
- http://h5.read.zdvgjr.cn/Article/1144909.shtml
- http://h5.read.zdvgjr.cn/Article/7321887.shtml
- http://h5.read.zdvgjr.cn/Article/02686.shtml
- http://h5.read.aovdbk.cn/Article/7432362.shtml
- http://h5.read.zdvgjr.cn/Article/5720.shtml
- http://h5.read.zdvgjr.cn/Article/9975.shtml
- http://h5.read.zdvgjr.cn/Article/81099.shtml
- http://h5.read.zdvgjr.cn/Article/99792.shtml
- http://h5.read.zdvgjr.cn/Article/7639752.shtml
- http://h5.read.aovdbk.cn/Article/2007576.shtml
- http://h5.read.zdvgjr.cn/Article/4964.shtml
- http://h5.read.aovdbk.cn/Article/646832.shtml
- http://h5.read.aovdbk.cn/Article/271861.shtml
- http://h5.read.aovdbk.cn/Article/3740679.shtml
- http://h5.read.aovdbk.cn/Article/6535494.shtml
- http://h5.read.aovdbk.cn/Article/70199.shtml

## 项目结构

```
h5-read-aggregator/
├── src/
│   ├── core/                         # 核心逻辑模块
│   │   ├── indexer.js                # 链接索引器，负责解析与入库
│   │   ├── validator.js              # URL 校验与规范化处理
│   │   └── classifier.js             # 基于路径与 ID 的自动标签分类
│   ├── api/                          # RESTful API 路由层
│   │   ├── routes.js                 # 路由注册与中间件挂载
│   │   └── handlers/                 # 各接口请求处理器
│   │       ├── list.js               # 链接列表查询
│   │       ├── import.js             # 批量导入接口
│   │       └── status.js             # 巡检状态查询
│   ├── scheduler/                    # 定时任务模块
│   │   ├── cron.js                   # 任务调度配置
│   │   └── checker.js                # 链接有效性巡检执行器
│   ├── static/                       # 静态站点生成模板
│   │   ├── template.ejs              # 导航页主模板
│   │   └── assets/                   # CSS 与客户端脚本
│   └── utils/                        # 通用工具函数
│       ├── fetcher.js                # HTTP 请求封装
│       ├── parser.js                 # HTML 元数据解析
│       └── logger.js                 # 结构化日志输出
├── config/
│   ├── default.json                  # 默认配置项
│   └── production.json               # 生产环境覆盖配置
├── data/
│   └── links.db                      # SQLite 索引数据库文件
├── tests/                            # 单元测试与集成测试
│   ├── unit/
│   └── integration/
├── scripts/
│   ├── init-db.js                    # 数据库初始化脚本
│   └── export-csv.js                 # CSV 导出工具
├── docs/                             # 完整文档目录
├── package.json
├── README.md
└── LICENSE
```

## 贡献指南

提交 Issue 报告链接收录异常或功能缺陷时，请附上目标 URL 的完整原始地址、预期行为与实际表现的详细对比，并标明项目版本号。

Fork 本仓库后，在 feat/ 或 fix/ 前缀的分支上进行开发，保持 commit 信息采用语义化格式（type(scope): subject），并确保所有现有测试用例通过。

新增链接源适配器时，需在 src/core/classifier.js 中补充对应的域名匹配规则与标签映射逻辑，并在 tests/unit/classifier.test.js 中追加覆盖用例。

提交 Pull Request 前，请执行 npm run lint 与 npm run test 进行代码规范检查与全量测试，确认无错误后方可发起合并请求。

文档类贡献（包括 README 翻译、API 示例补充）同样欢迎，修改 docs/ 目录下的对应文件即可，无需通过代码审查流程。

## 常见问题

Q: 项目如何避免因目标站点反爬策略而导致巡检失败？

A: 巡检模块默认启用 User-Agent 轮换与请求间隔随机延迟，间隔范围为 1000 至 5000 毫秒。用户可在 config/default.json 中调整 checker.interval 与 checker.randomDelay 参数。对于返回 403 或 429 状态码的链接，系统会自动标记为需人工复核并暂停对该域名的后续巡检。

Q: 如何迁移已有链接集合到新部署实例？

A: 使用项目提供的 export-csv 脚本从旧实例导出完整数据，生成 CSV 文件后，通过新实例的导入接口批量写入。若需保留标签与时间戳等元数据，请在导出的 CSV 中包含 id、url、label、createdAt 等列，导入时系统会依据 id 进行去重更新。

Q: 静态站点生成模式是否支持自定义主题？

A: 支持。src/static/template.ejs 为 EJS 模板文件，用户可自行修改 HTML 结构与 CSS 样式。生成时系统会将 links 数据作为模板变量传入，用户可通过遍历 links 数组渲染任意布局。

## 许可证

MIT

> 外链数量: 150 | 生成时间: 2026-07-10 00:06:11
