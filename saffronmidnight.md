# WebLink Archive Gateway

WebLink Archive Gateway 是一个面向技术研究、数据挖掘与内容回溯场景的轻量级外链归档与导航系统。该项目聚焦于对特定域名下历史文章资源的结构化收录与分类呈现，解决技术文档散落、外链失效、阅读路径不可溯等问题，适用于需要长期维护外部知识引用索引的开发者、研究团队与内容策展人。

项目本身不依赖数据库，采用纯静态文件生成机制，以 Markdown 为数据源，通过构建流程输出可部署的 HTML 目录页与 JSON 索引文件，便于集成至现有文档站点或内部知识库。目标用户包括开源项目维护者、技术博主、数据采集工程师以及需要批量管理外链资源的运营人员。

## 功能概览

- 多源外链统一收录：支持将分散在不同二级域名下的文章链接汇聚至单一索引体系，并自动识别来源域与文章编号。
- 批量链接状态检测：内置链接可用性校验模块，可定期检查资源是否可访问，输出失效报告。
- 分类标签自动生成：基于 URL 路径特征与文章 ID 数值范围，自动生成初步分类标签（如技术手册、版本公告、案例分析等）。
- 静态索引页构建：通过模板引擎生成响应式目录页，支持按发布时间、来源域、文章编号排序与筛选。
- JSON 数据导出：提供标准化 JSON 格式的索引数据，便于第三方工具调用或进一步分析处理。
- 增量更新支持：支持新增链接的增量导入，不影响已有索引结构，适用于持续增长的外链资源池。
- 自定义元数据扩展：允许为每条链接附加备注、优先级、阅读状态等自定义字段，满足个性化管理需求。

## 应用场景

- 技术文档归档与检索：团队可将散落在多个临时域名下的历史技术文章统一纳入索引，通过本地构建生成可检索的目录页面，方便成员快速定位特定编号或来源的文章。
- 外部引用溯源管理：开源项目在 README 或 Wiki 中引用大量外部链接时，可使用本系统维护一份结构化列表，定期检查链接有效性，避免引用断裂。
- 内容迁移辅助工具：在更换文档托管平台或域名重组期间，通过本系统导出完整链接清单与元数据，辅助进行 301 重定向映射或内容迁移校验。
- 研究数据样本收集：数据采集研究者可利用本系统的批量导入与分类功能，快速构建特定域名的文章样本集，并导出 JSON 格式供数据分析流水线使用。

## 快速开始

以下命令演示了从克隆仓库到启动本地预览服务的完整流程。

```bash
git clone https://github.com/example/weblink-archive-gateway.git
cd weblink-archive-gateway
pip install -r requirements.txt
python build.py --input ./data/links.txt --output ./dist
python -m http.server 8000 --directory ./dist
```

执行完毕后，访问 http://localhost:8000 即可查看生成的索引页面。如需导入自定义链接列表，请将 URL 逐行放入 `./data/links.txt` 文件后重新执行构建命令。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心构建脚本与链接检测模块的运行环境 |
| pip | 20.0 及以上 | Python 包管理工具，用于安装依赖库 |
| requests | 2.25.0 及以上 | 发送 HTTP 请求以执行链接状态检测 |
| jinja2 | 3.0.0 及以上 | 模板引擎，用于生成 HTML 索引页 |
| markdown | 3.3.0 及以上 | 将 README 及文档目录中的 Markdown 文件渲染为 HTML |
| pytest | 6.0.0 及以上 | 可选依赖，用于运行单元测试套件 |
| flake8 | 3.8.0 及以上 | 可选依赖，用于代码风格检查 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide.md | 如何导入链接、自定义分类规则、生成索引页 |
| 配置参考 | docs/configuration.md | 构建脚本支持哪些命令行参数与环境变量 |
| 开发指南 | docs/development.md | 如何扩展分类器、添加新的输出格式、提交代码变更 |
| API 说明 | docs/api.md | 构建核心模块的类与方法定义，供二次开发参考 |
| 故障排除 | docs/troubleshooting.md | 常见构建错误、链接检测超时、模板渲染异常的解决方案 |
| 变更日志 | CHANGELOG.md | 每个版本的功能新增、修复与破坏性变更记录 |

## 资源列表

- http://wap.read.zdvgjr.cn/Article/5491.shtml
- http://wap.read.aovdbk.cn/Article/875303.shtml
- http://wap.read.aovdbk.cn/Article/9014.shtml
- http://wap.read.aovdbk.cn/Article/5030.shtml
- http://wap.read.aovdbk.cn/Article/420954.shtml
- http://wap.read.aovdbk.cn/Article/408421.shtml
- http://wap.read.aovdbk.cn/Article/81476.shtml
- http://wap.read.aovdbk.cn/Article/850962.shtml
- http://wap.read.aovdbk.cn/Article/5663.shtml
- http://wap.read.aovdbk.cn/Article/111965.shtml
- http://wap.read.zdvgjr.cn/Article/31330.shtml
- http://wap.read.zdvgjr.cn/Article/048970.shtml
- http://wap.read.aovdbk.cn/Article/417386.shtml
- http://wap.read.aovdbk.cn/Article/96040.shtml
- http://wap.read.aovdbk.cn/Article/6278288.shtml
- http://wap.read.aovdbk.cn/Article/111500.shtml
- http://wap.read.aovdbk.cn/Article/5592.shtml
- http://wap.read.zdvgjr.cn/Article/60298.shtml
- http://wap.read.zdvgjr.cn/Article/18463.shtml
- http://wap.read.zdvgjr.cn/Article/7119902.shtml
- http://wap.read.aovdbk.cn/Article/40353.shtml
- http://wap.read.zdvgjr.cn/Article/4289489.shtml
- http://wap.read.aovdbk.cn/Article/7825.shtml
- http://wap.read.zdvgjr.cn/Article/8705602.shtml
- http://wap.read.aovdbk.cn/Article/13856.shtml
- http://wap.read.aovdbk.cn/Article/3708572.shtml
- http://wap.read.aovdbk.cn/Article/821539.shtml
- http://wap.read.aovdbk.cn/Article/9583048.shtml
- http://wap.read.aovdbk.cn/Article/0969071.shtml
- http://wap.read.zdvgjr.cn/Article/8535.shtml
- http://wap.read.aovdbk.cn/Article/76807.shtml
- http://wap.read.zdvgjr.cn/Article/8635459.shtml
- http://wap.read.zdvgjr.cn/Article/2667.shtml
- http://wap.read.zdvgjr.cn/Article/4800299.shtml
- http://wap.read.aovdbk.cn/Article/9457.shtml
- http://wap.read.zdvgjr.cn/Article/67102.shtml
- http://wap.read.aovdbk.cn/Article/64961.shtml
- http://wap.read.aovdbk.cn/Article/197916.shtml
- http://wap.read.zdvgjr.cn/Article/35120.shtml
- http://wap.read.zdvgjr.cn/Article/561577.shtml
- http://wap.read.aovdbk.cn/Article/4918.shtml
- http://wap.read.zdvgjr.cn/Article/9935.shtml
- http://wap.read.aovdbk.cn/Article/3700004.shtml
- http://wap.read.aovdbk.cn/Article/011117.shtml
- http://wap.read.aovdbk.cn/Article/5420442.shtml
- http://wap.read.aovdbk.cn/Article/9144.shtml
- http://wap.read.zdvgjr.cn/Article/532857.shtml
- http://wap.read.zdvgjr.cn/Article/0032673.shtml
- http://wap.read.zdvgjr.cn/Article/89958.shtml
- http://wap.read.aovdbk.cn/Article/01632.shtml
- http://wap.read.aovdbk.cn/Article/1480.shtml
- http://wap.read.aovdbk.cn/Article/1270218.shtml
- http://wap.read.aovdbk.cn/Article/4738580.shtml
- http://wap.read.aovdbk.cn/Article/13667.shtml
- http://wap.read.aovdbk.cn/Article/0333396.shtml
- http://wap.read.zdvgjr.cn/Article/085252.shtml
- http://wap.read.aovdbk.cn/Article/6848177.shtml
- http://wap.read.aovdbk.cn/Article/3356822.shtml
- http://wap.read.aovdbk.cn/Article/498216.shtml
- http://wap.read.zdvgjr.cn/Article/119777.shtml
- http://wap.read.zdvgjr.cn/Article/04384.shtml
- http://wap.read.aovdbk.cn/Article/1272.shtml
- http://wap.read.zdvgjr.cn/Article/0257420.shtml
- http://wap.read.aovdbk.cn/Article/8968.shtml
- http://wap.read.zdvgjr.cn/Article/42752.shtml
- http://wap.read.zdvgjr.cn/Article/1598.shtml
- http://wap.read.aovdbk.cn/Article/0881122.shtml
- http://wap.read.zdvgjr.cn/Article/121150.shtml
- http://wap.read.zdvgjr.cn/Article/781942.shtml
- http://wap.read.zdvgjr.cn/Article/54108.shtml
- http://wap.read.aovdbk.cn/Article/987084.shtml
- http://wap.read.zdvgjr.cn/Article/9036.shtml
- http://wap.read.zdvgjr.cn/Article/4806.shtml
- http://wap.read.zdvgjr.cn/Article/222507.shtml
- http://wap.read.zdvgjr.cn/Article/407642.shtml
- http://wap.read.aovdbk.cn/Article/4511377.shtml
- http://wap.read.zdvgjr.cn/Article/997651.shtml
- http://wap.read.aovdbk.cn/Article/0900.shtml
- http://wap.read.zdvgjr.cn/Article/0367944.shtml
- http://wap.read.aovdbk.cn/Article/2176001.shtml
- http://wap.read.aovdbk.cn/Article/179131.shtml
- http://wap.read.aovdbk.cn/Article/652302.shtml
- http://wap.read.aovdbk.cn/Article/2914884.shtml
- http://wap.read.aovdbk.cn/Article/058648.shtml
- http://wap.read.zdvgjr.cn/Article/1144909.shtml
- http://wap.read.zdvgjr.cn/Article/7321887.shtml
- http://wap.read.zdvgjr.cn/Article/02686.shtml
- http://wap.read.aovdbk.cn/Article/7432362.shtml
- http://wap.read.zdvgjr.cn/Article/5720.shtml
- http://wap.read.zdvgjr.cn/Article/9975.shtml
- http://wap.read.zdvgjr.cn/Article/81099.shtml
- http://wap.read.zdvgjr.cn/Article/99792.shtml
- http://wap.read.zdvgjr.cn/Article/7639752.shtml
- http://wap.read.aovdbk.cn/Article/2007576.shtml
- http://wap.read.zdvgjr.cn/Article/4964.shtml
- http://wap.read.aovdbk.cn/Article/646832.shtml
- http://wap.read.aovdbk.cn/Article/271861.shtml
- http://wap.read.aovdbk.cn/Article/3740679.shtml
- http://wap.read.aovdbk.cn/Article/6535494.shtml
- http://wap.read.aovdbk.cn/Article/70199.shtml
- http://wap.read.zdvgjr.cn/Article/424543.shtml
- http://wap.read.zdvgjr.cn/Article/0888.shtml
- http://wap.read.aovdbk.cn/Article/3446.shtml
- http://wap.read.aovdbk.cn/Article/0035884.shtml
- http://wap.read.zdvgjr.cn/Article/577962.shtml
- http://wap.read.aovdbk.cn/Article/0854.shtml
- http://wap.read.zdvgjr.cn/Article/3687.shtml
- http://wap.read.aovdbk.cn/Article/898776.shtml
- http://wap.read.aovdbk.cn/Article/3006.shtml
- http://wap.read.zdvgjr.cn/Article/9743828.shtml
- http://wap.read.zdvgjr.cn/Article/1835.shtml
- http://wap.read.aovdbk.cn/Article/9941929.shtml
- http://wap.read.zdvgjr.cn/Article/198982.shtml
- http://wap.read.aovdbk.cn/Article/8237503.shtml
- http://wap.read.aovdbk.cn/Article/50102.shtml
- http://wap.read.zdvgjr.cn/Article/928519.shtml
- http://wap.read.aovdbk.cn/Article/2210573.shtml
- http://wap.read.zdvgjr.cn/Article/6525012.shtml
- http://wap.read.aovdbk.cn/Article/132758.shtml
- http://wap.read.zdvgjr.cn/Article/7792.shtml
- http://wap.read.zdvgjr.cn/Article/959812.shtml
- http://wap.read.aovdbk.cn/Article/459916.shtml
- http://wap.read.zdvgjr.cn/Article/2725594.shtml
- http://wap.read.aovdbk.cn/Article/08030.shtml
- http://wap.read.zdvgjr.cn/Article/8333641.shtml
- http://wap.read.zdvgjr.cn/Article/537816.shtml
- http://wap.read.aovdbk.cn/Article/7478805.shtml
- http://wap.read.aovdbk.cn/Article/0257.shtml
- http://wap.read.zdvgjr.cn/Article/612576.shtml
- http://wap.read.aovdbk.cn/Article/694208.shtml
- http://wap.read.zdvgjr.cn/Article/3495554.shtml
- http://wap.read.aovdbk.cn/Article/37201.shtml
- http://wap.read.aovdbk.cn/Article/5896987.shtml
- http://wap.read.aovdbk.cn/Article/39376.shtml
- http://wap.read.zdvgjr.cn/Article/73444.shtml
- http://wap.read.zdvgjr.cn/Article/12683.shtml
- http://wap.read.zdvgjr.cn/Article/0736.shtml
- http://wap.read.zdvgjr.cn/Article/13953.shtml
- http://wap.read.zdvgjr.cn/Article/351814.shtml
- http://wap.read.zdvgjr.cn/Article/21070.shtml
- http://wap.read.aovdbk.cn/Article/8780895.shtml
- http://wap.read.zdvgjr.cn/Article/042030.shtml
- http://wap.read.aovdbk.cn/Article/4215228.shtml
- http://wap.read.zdvgjr.cn/Article/2623038.shtml
- http://wap.read.zdvgjr.cn/Article/2767.shtml
- http://wap.read.aovdbk.cn/Article/6422.shtml
- http://wap.read.aovdbk.cn/Article/7387978.shtml
- http://wap.read.zdvgjr.cn/Article/7749.shtml
- http://wap.read.aovdbk.cn/Article/684677.shtml
- http://wap.read.aovdbk.cn/Article/98180.shtml

## 项目结构

```
weblink-archive-gateway/
├── build.py                 # 主构建脚本，协调链接导入、检测与页面生成流程
├── config.yaml              # 项目配置文件，定义分类规则、输出路径与检测参数
├── requirements.txt         # Python 依赖声明文件
├── CHANGELOG.md             # 版本变更历史记录
├── LICENSE                  # MIT 许可证文本
├── data/                    # 数据目录
│   ├── links.txt            # 用户自定义链接列表，每行一个 URL
│   └── metadata/            # 元数据扩展目录
│       ├── tags.csv         # 为链接手动指定的标签或分类覆盖
│       └── notes.json       # 每条链接的备注与优先级信息
├── src/                     # 核心源码目录
│   ├── __init__.py
│   ├── fetcher.py           # 链接状态检测模块，封装 requests 请求逻辑
│   ├── parser.py            # URL 解析与分类标签生成模块
│   ├── indexer.py           # 索引数据结构管理，支持增删改查与序列化
│   └── exporter.py          # 输出模块，负责生成 HTML 与 JSON 文件
├── templates/               # Jinja2 模板目录
│   ├── base.html            # 基础页面骨架，包含响应式头部与尾部
│   ├── index.html           # 链接列表页模板，支持分页与排序
│   └── detail.html          # 单条链接详情页模板，展示全部元数据
├── static/                  # 静态资源目录
│   ├── css/                 # 样式文件，包含暗色主题与打印优化
│   ├── js/                  # 前端交互脚本，实现客户端筛选与排序
│   └── assets/              # 图片及字体等通用资源
├── tests/                   # 单元测试目录
│   ├── test_parser.py       # 解析器模块的测试用例
│   ├── test_fetcher.py      # 链接检测模块的模拟网络测试
│   └── test_indexer.py      # 索引数据结构的增删改查覆盖测试
└── docs/                    # 项目文档目录
    ├── user-guide.md        # 用户手册
    ├── configuration.md     # 配置参考
    ├── development.md       # 开发指南
    ├── api.md               # API 说明
    └── troubleshooting.md   # 故障排除
```

## 贡献指南

1. 在 GitHub 仓库页面点击 Fork 按钮，将项目复制至个人账户下，然后克隆到本地开发环境。
2. 创建新的功能分支，分支名称需反映变更类型与简要描述，例如 `feat/add-rss-output` 或 `fix/parser-encoding-issue`。
3. 编写或修改代码后，请确保所有现有单元测试通过，并为新增功能补充对应的测试用例。执行 `pytest tests/` 验证。
4. 提交前运行 `flake8 src/` 检查代码风格，确保符合 PEP 8 规范且无语法警告。
5. 发起 Pull Request 至主仓库的 `main` 分支，在描述中清晰说明变更目的、实现方式与测试结果。维护者将在 3 个工作日内进行审查。

## 常见问题

- 问：链接检测超时或失败，构建过程中断如何处理？
  答：可调整 `config.yaml` 中的 `timeout` 参数值（单位秒），默认设置为 5 秒。若部分链接始终无法访问，可将其加入 `skip_check_list` 跳过检测，或使用 `--skip-errors` 命令行参数忽略失败继续构建。

- 问：如何导入来自不同域名的链接并自动分类？
  答：系统默认根据 URL 中的域名二级部分（如 `zdvgjr` 与 `aovdbk`）以及文章 ID 的数值区间生成初步分类标签。用户可在 `data/metadata/tags.csv` 中为特定 ID 或域名覆盖自定义标签，构建时会优先采用手动标注。

- 问：生成的索引页面能否部署到 GitHub Pages 或 Nginx 静态服务？
  答：完全可以。`./dist` 目录包含完整的 HTML、CSS、JavaScript 及 JSON 数据文件，均为静态内容。将此目录上传至任意静态托管服务即可直接访问，无需额外后端支持。

## 许可证

MIT

> 外链数量: 150 | 生成时间: 2026-07-10 00:06:11
