# WebRead Resource Aggregator

WebRead Resource Aggregator 是一个面向技术研究、数据采集与内容分析场景的轻量化外链汇总与导航系统。该项目旨在解决分散在多个移动端阅读源中的结构化内容难以统一检索、批量访问与持久化引用的问题，适用于需要高频采集移动端文章资源的开发者、数据分析师与内容运营人员。

本项目并非一个通用爬虫框架，而是一个专注于特定数据源格式（.shtml 静态页面）的链接索引与前置校验工具。通过提供标准化的 URL 清单导出、可用性检查与元数据提取接口，帮助用户快速建立私有化的移动内容资源池。

## 功能概览

批量链接导入与去重：支持从文本文件、CSV 或直接粘贴的原始 URL 列表中自动解析并剔除重复条目，保留原始域名与路径结构。

资源存活状态检测：内置轻量级 HTTP HEAD 请求模块，可批量检测每个 URL 的响应状态码，标记异常链接（超时、4xx、5xx）。

域名分拣与归类：根据 URL 中的二级域名（zdvgjr.cn / aovdbk.cn）自动分拣资源，生成独立的域名视图，便于按来源域进行后续处理。

自定义标签注记：允许用户为每条链接添加自由标签（如"技术文档""行业报告""案例研究"），支持按标签快速过滤与导出。

结构化数据预览：解析 .shtml 页面中的常见元数据字段（标题、发布时间、正文前 200 字符），生成可读性良好的摘要列表。

导出格式灵活：支持将当前资源清单导出为纯文本 URL 列表、JSON 结构化数据或 Markdown 表格，适应不同下游工具链。

增量更新机制：支持通过配置文件指定新增 URL 文件路径，自动合并至主库并标记新增时间戳，避免全量重复操作。

## 应用场景

移动端内容采集与归档：内容运营团队可定期将分散在多个移动阅读源的 .shtml 文章链接统一收录至 WebRead 系统，利用存活检测功能筛除失效链接，保留有效资源作为长期参考库。

技术文档元数据分析：技术研究人员可使用预览功能快速提取一批 .shtml 页面的标题与摘要，无需逐个打开页面即可判断内容相关性，大幅提升文献调研效率。

数据源迁移前的链接审计：在计划将旧版移动站点迁移至新平台前，运维人员可导入全部历史文章 URL，通过状态检测识别已删除或重定向的页面，提前准备重定向映射表。

自动化监控脚本的数据输入：开发者可将 WebRead 导出的 JSON 格式链接清单作为定时任务的输入，定期抓取指定域下的新增内容，实现轻量级内容变更通知。

## 快速开始

以下步骤适用于 Linux / macOS / Windows WSL 环境，需预先安装 Git 与 Node.js 18.0 以上版本。

```bash
# 克隆项目仓库至本地
git clone https://github.com/webread-org/webread-aggregator.git

# 进入项目根目录
cd webread-aggregator

# 安装核心依赖（使用 npm）
npm install

# 复制示例配置文件并修改数据源路径
cp config.example.json config.json

# 执行批量 URL 导入与状态检测（默认读取 ./data/urls.txt）
npm run start

# 如需指定自定义输入文件，可使用命令行参数
node index.js --input ./my_urls.txt --output ./report.json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.0.0 或更高 | 运行时环境，提供 ES 模块与原生 fetch 支持 |
| npm | 9.0.0 或更高 | 包管理器，用于安装项目依赖库 |
| Git | 2.30.0 或更高 | 版本控制工具，用于克隆仓库及拉取更新 |
| 网络访问 | 可访问外网 | 用于检测 URL 存活状态及解析 .shtml 页面 |
| 存储空间 | 至少 100 MB 可用 | 存放 URL 列表、缓存文件及导出结果 |
| 操作系统 | Linux / macOS / Windows (WSL2) | 开发与生产环境均支持主流操作系统 |
| 内存 | 建议 512 MB 以上 | 批量处理 1000 条以上 URL 时的性能保障 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何安装、配置并首次运行资源导入流程 |
| 命令参考 | docs/cli-commands.md | 所有可用命令行参数及环境变量的详细说明 |
| 配置手册 | docs/configuration.md | config.json 中每个字段的含义与可选项 |
| 输出格式 | docs/output-formats.md | 导出 JSON / CSV / Markdown 的结构定义与示例 |
| API 接口 | docs/api-reference.md | 核心模块的函数签名及调用示例（适用于二次开发） |
| 故障排除 | docs/troubleshooting.md | 常见错误码、网络超时及解析失败的处理方案 |

## 资源列表

- http://wap.read.zdvgjr.cn/Article/721591.shtml
- http://wap.read.zdvgjr.cn/Article/6964912.shtml
- http://wap.read.aovdbk.cn/Article/339848.shtml
- http://wap.read.aovdbk.cn/Article/58633.shtml
- http://wap.read.zdvgjr.cn/Article/663248.shtml
- http://wap.read.zdvgjr.cn/Article/02211.shtml
- http://wap.read.zdvgjr.cn/Article/8917.shtml
- http://wap.read.zdvgjr.cn/Article/0675047.shtml
- http://wap.read.aovdbk.cn/Article/3977851.shtml
- http://wap.read.aovdbk.cn/Article/8245210.shtml
- http://wap.read.aovdbk.cn/Article/376943.shtml
- http://wap.read.zdvgjr.cn/Article/151991.shtml
- http://wap.read.aovdbk.cn/Article/5619422.shtml
- http://wap.read.aovdbk.cn/Article/8660.shtml
- http://wap.read.zdvgjr.cn/Article/59800.shtml
- http://wap.read.zdvgjr.cn/Article/865605.shtml
- http://wap.read.aovdbk.cn/Article/61541.shtml
- http://wap.read.aovdbk.cn/Article/8163.shtml
- http://wap.read.zdvgjr.cn/Article/7097687.shtml
- http://wap.read.aovdbk.cn/Article/7769.shtml
- http://wap.read.zdvgjr.cn/Article/4937624.shtml
- http://wap.read.aovdbk.cn/Article/682217.shtml
- http://wap.read.aovdbk.cn/Article/8943363.shtml
- http://wap.read.zdvgjr.cn/Article/23185.shtml
- http://wap.read.zdvgjr.cn/Article/20399.shtml
- http://wap.read.aovdbk.cn/Article/5432907.shtml
- http://wap.read.zdvgjr.cn/Article/71429.shtml
- http://wap.read.aovdbk.cn/Article/1132136.shtml
- http://wap.read.zdvgjr.cn/Article/0109.shtml
- http://wap.read.zdvgjr.cn/Article/2850.shtml
- http://wap.read.aovdbk.cn/Article/749516.shtml
- http://wap.read.aovdbk.cn/Article/259009.shtml
- http://wap.read.aovdbk.cn/Article/92597.shtml
- http://wap.read.zdvgjr.cn/Article/0270.shtml
- http://wap.read.aovdbk.cn/Article/864407.shtml
- http://wap.read.aovdbk.cn/Article/49041.shtml
- http://wap.read.zdvgjr.cn/Article/809659.shtml
- http://wap.read.zdvgjr.cn/Article/48366.shtml
- http://wap.read.aovdbk.cn/Article/5601.shtml
- http://wap.read.aovdbk.cn/Article/9122891.shtml
- http://wap.read.zdvgjr.cn/Article/0965748.shtml
- http://wap.read.zdvgjr.cn/Article/68473.shtml
- http://wap.read.zdvgjr.cn/Article/491421.shtml
- http://wap.read.zdvgjr.cn/Article/88652.shtml
- http://wap.read.aovdbk.cn/Article/45454.shtml
- http://wap.read.zdvgjr.cn/Article/387085.shtml
- http://wap.read.zdvgjr.cn/Article/2842170.shtml
- http://wap.read.aovdbk.cn/Article/0967035.shtml
- http://wap.read.zdvgjr.cn/Article/4402469.shtml
- http://wap.read.aovdbk.cn/Article/04329.shtml
- http://wap.read.aovdbk.cn/Article/408047.shtml
- http://wap.read.aovdbk.cn/Article/5570.shtml
- http://wap.read.zdvgjr.cn/Article/20295.shtml
- http://wap.read.zdvgjr.cn/Article/4676.shtml
- http://wap.read.zdvgjr.cn/Article/23664.shtml
- http://wap.read.zdvgjr.cn/Article/458469.shtml
- http://wap.read.zdvgjr.cn/Article/3230.shtml
- http://wap.read.aovdbk.cn/Article/3985.shtml
- http://wap.read.zdvgjr.cn/Article/3793.shtml
- http://wap.read.zdvgjr.cn/Article/0666921.shtml
- http://wap.read.zdvgjr.cn/Article/071945.shtml
- http://wap.read.aovdbk.cn/Article/82476.shtml
- http://wap.read.aovdbk.cn/Article/4514868.shtml
- http://wap.read.aovdbk.cn/Article/844193.shtml
- http://wap.read.aovdbk.cn/Article/5992.shtml
- http://wap.read.zdvgjr.cn/Article/984028.shtml
- http://wap.read.aovdbk.cn/Article/6481109.shtml
- http://wap.read.aovdbk.cn/Article/1847065.shtml
- http://wap.read.zdvgjr.cn/Article/16264.shtml
- http://wap.read.zdvgjr.cn/Article/27394.shtml
- http://wap.read.zdvgjr.cn/Article/6714990.shtml
- http://wap.read.aovdbk.cn/Article/41161.shtml
- http://wap.read.aovdbk.cn/Article/9772335.shtml
- http://wap.read.aovdbk.cn/Article/43829.shtml
- http://wap.read.aovdbk.cn/Article/12365.shtml
- http://wap.read.aovdbk.cn/Article/32506.shtml
- http://wap.read.zdvgjr.cn/Article/1764043.shtml
- http://wap.read.zdvgjr.cn/Article/116940.shtml
- http://wap.read.aovdbk.cn/Article/4544735.shtml
- http://wap.read.zdvgjr.cn/Article/6659.shtml
- http://wap.read.aovdbk.cn/Article/772855.shtml
- http://wap.read.zdvgjr.cn/Article/914300.shtml
- http://wap.read.zdvgjr.cn/Article/0754.shtml
- http://wap.read.zdvgjr.cn/Article/42947.shtml
- http://wap.read.aovdbk.cn/Article/6892.shtml
- http://wap.read.zdvgjr.cn/Article/0845.shtml
- http://wap.read.zdvgjr.cn/Article/0148.shtml
- http://wap.read.aovdbk.cn/Article/8109662.shtml
- http://wap.read.zdvgjr.cn/Article/8114112.shtml
- http://wap.read.aovdbk.cn/Article/1873900.shtml
- http://wap.read.zdvgjr.cn/Article/52340.shtml
- http://wap.read.aovdbk.cn/Article/43067.shtml
- http://wap.read.aovdbk.cn/Article/538867.shtml
- http://wap.read.zdvgjr.cn/Article/5162283.shtml
- http://wap.read.zdvgjr.cn/Article/532772.shtml
- http://wap.read.zdvgjr.cn/Article/9051951.shtml
- http://wap.read.aovdbk.cn/Article/764811.shtml
- http://wap.read.zdvgjr.cn/Article/6704559.shtml
- http://wap.read.aovdbk.cn/Article/15317.shtml
- http://wap.read.aovdbk.cn/Article/40452.shtml
- http://wap.read.aovdbk.cn/Article/1691254.shtml
- http://wap.read.zdvgjr.cn/Article/3240.shtml
- http://wap.read.aovdbk.cn/Article/977187.shtml
- http://wap.read.zdvgjr.cn/Article/16860.shtml
- http://wap.read.aovdbk.cn/Article/4058.shtml
- http://wap.read.zdvgjr.cn/Article/4325776.shtml
- http://wap.read.zdvgjr.cn/Article/7354.shtml
- http://wap.read.aovdbk.cn/Article/4221.shtml
- http://wap.read.zdvgjr.cn/Article/3755.shtml
- http://wap.read.zdvgjr.cn/Article/66300.shtml
- http://wap.read.aovdbk.cn/Article/9686773.shtml
- http://wap.read.zdvgjr.cn/Article/108868.shtml
- http://wap.read.aovdbk.cn/Article/81768.shtml
- http://wap.read.zdvgjr.cn/Article/60608.shtml
- http://wap.read.zdvgjr.cn/Article/8335.shtml
- http://wap.read.zdvgjr.cn/Article/5421965.shtml
- http://wap.read.aovdbk.cn/Article/362451.shtml
- http://wap.read.aovdbk.cn/Article/5792271.shtml
- http://wap.read.aovdbk.cn/Article/174390.shtml
- http://wap.read.aovdbk.cn/Article/2497.shtml
- http://wap.read.zdvgjr.cn/Article/2678.shtml
- http://wap.read.aovdbk.cn/Article/3896.shtml
- http://wap.read.aovdbk.cn/Article/34540.shtml
- http://wap.read.zdvgjr.cn/Article/8191160.shtml
- http://wap.read.zdvgjr.cn/Article/2692.shtml
- http://wap.read.zdvgjr.cn/Article/27050.shtml
- http://wap.read.zdvgjr.cn/Article/534049.shtml
- http://wap.read.aovdbk.cn/Article/9437332.shtml
- http://wap.read.zdvgjr.cn/Article/0508.shtml
- http://wap.read.zdvgjr.cn/Article/0448.shtml
- http://wap.read.zdvgjr.cn/Article/181488.shtml
- http://wap.read.zdvgjr.cn/Article/55759.shtml
- http://wap.read.zdvgjr.cn/Article/4046634.shtml
- http://wap.read.zdvgjr.cn/Article/913011.shtml
- http://wap.read.zdvgjr.cn/Article/181909.shtml
- http://wap.read.zdvgjr.cn/Article/3026727.shtml
- http://wap.read.zdvgjr.cn/Article/080488.shtml
- http://wap.read.zdvgjr.cn/Article/92028.shtml
- http://wap.read.zdvgjr.cn/Article/4545706.shtml
- http://wap.read.aovdbk.cn/Article/92227.shtml
- http://wap.read.aovdbk.cn/Article/9977.shtml
- http://wap.read.aovdbk.cn/Article/43533.shtml
- http://wap.read.aovdbk.cn/Article/34034.shtml
- http://wap.read.zdvgjr.cn/Article/2036997.shtml
- http://wap.read.aovdbk.cn/Article/114261.shtml
- http://wap.read.zdvgjr.cn/Article/2829624.shtml
- http://wap.read.zdvgjr.cn/Article/971694.shtml
- http://wap.read.zdvgjr.cn/Article/7774549.shtml
- http://wap.read.aovdbk.cn/Article/23545.shtml
- http://wap.read.zdvgjr.cn/Article/8514594.shtml

## 项目结构

```
webread-aggregator/
├── index.js                # 主入口，负责解析参数、调度各模块
├── package.json            # npm 声明文件，包含依赖及脚本命令
├── config.json             # 用户配置文件，定义输入路径、超时阈值等
├── config.example.json     # 配置示例，含全部可选项及注释
├── data/                   # 默认数据存放目录
│   ├── urls.txt            # 原始 URL 列表（每行一条）
│   ├── cache/              # 请求缓存目录，避免重复网络调用
│   │   └── head_cache.json # HEAD 请求结果缓存
│   └── exports/            # 导出文件存放目录
│       ├── report.json     # 结构化输出
│       └── report.md       # Markdown 表格导出
├── src/                    # 核心源代码目录
│   ├── loader.js           # 文件读取与 URL 解析模块
│   ├── checker.js          # HTTP 状态检测与超时控制
│   ├── parser.js           # .shtml 元数据提取（标题/时间/摘要）
│   ├── classifier.js       # 按域名、标签进行分拣归类
│   ├── exporter.js         # JSON / CSV / Markdown 格式输出
│   └── utils.js            # 通用工具函数（去重、日志、时间格式化）
├── tests/                  # 单元测试与集成测试
│   ├── loader.test.js
│   ├── checker.test.js
│   └── parser.test.js
├── docs/                   # 完整文档目录
│   ├── getting-started.md
│   ├── cli-commands.md
│   ├── configuration.md
│   ├── output-formats.md
│   ├── api-reference.md
│   └── troubleshooting.md
├── .gitignore              # Git 忽略规则
├── .eslintrc.js            # 代码风格检查配置
└── LICENSE                 # MIT 许可证文本
```

## 贡献指南

欢迎社区开发者参与项目改进。请按照以下步骤提交贡献：

1. 在 GitHub 上 Fork 本仓库至个人账户，并克隆到本地开发环境。
2. 创建新的功能分支，分支名需反映修改内容，例如 `feat/add-timeout-option` 或 `fix/parser-encoding-issue`。
3. 完成代码修改后，确保所有现有单元测试通过，并为新增功能编写对应的测试用例（位于 `tests/` 目录）。
4. 提交前执行 `npm run lint` 检查代码风格，并运行 `npm test` 确认全部测试通过。
5. 提交 Pull Request，在描述中清晰说明修改目的、实现方式及影响范围，等待维护者审核。

## 常见问题

**问：批量检测时出现大量超时或 ECONNRESET 错误，如何解决？**

答：可调整 `config.json` 中的 `timeout` 字段（单位毫秒），默认值为 5000。若网络环境较差，建议增加至 10000 或 15000。同时可降低 `concurrency` 并发数（默认 10），避免源站触发流量限制。

**问：导出的 JSON 文件中 `status` 字段为 null 或 0，表示什么？**

答：这表示检测模块未能成功获取 HTTP 状态码，常见原因包括 DNS 解析失败、目标主机不可达或 TLS/SSL 握手错误（即便本例使用 HTTP 协议，但扩展场景中可能涉及 HTTPS）。建议使用 `--verbose` 参数重新运行，查看详细错误日志定位问题。

**问：如何更新已有资源列表并保留之前添加的自定义标签？**

答：使用增量导入模式，在 `config.json` 中设置 `incremental` 为 `true`，并指定 `new_urls_file` 路径。系统将比对现有 URL 列表，仅追加新链接，同时保留所有已存在的标签注记及历史检测记录。

## 许可证

MIT

> 外链数量: 150 | 生成时间: 2026-07-10 00:06:11
