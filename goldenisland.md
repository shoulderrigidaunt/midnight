# WapRead External Resource Aggregator

WapRead External Resource Aggregator is a structured curation system designed to collect, categorize, and provide stable access to distributed mobile-optimized reading resources across multiple domain sources. This project targets developers, content aggregators, and research institutions that require programmatic access to a large-scale, continuously updated repository of article-level references originating from heterogeneous wap-based content providers.

The system addresses the fundamental challenge of managing fragmented external reading links that are scattered across different domain zones and lack a unified indexing mechanism. By providing a centralized manifest with version-controlled snapshots, the project enables reliable batch processing, link health monitoring, and metadata enrichment for downstream applications such as recommendation engines, archival crawlers, and academic citation trackers.

## 功能概览

**Multi-Domain Source Normalization** - The aggregator consolidates article endpoints from distinct wap domains into a single uniform resource listing, preserving original URL integrity while enabling cross-source queries.

**Batched Resource Indexing** - Each project release packages exactly 150 article references per batch, providing predictable chunk sizes for parallel processing pipelines and quota-managed scraping workflows.

**Read-Only Static Distribution** - The resource list is distributed as a static Markdown manifest, eliminating runtime database dependencies and ensuring maximum compatibility with CDN caching and offline analysis tools.

**Versioned Batch Tracking** - Every batch is tagged with a sequential identifier (currently Batch 51 of 67), allowing consumers to detect incremental additions, detect removed entries, and maintain local synchronization state.

**Minimal Dependency Footprint** - The project requires no proprietary runtime environment or external API keys; the manifest is human-readable and machine-parseable without custom parsers.

**Link Integrity Placeholder Support** - The system reserves fields for future annotations including response status codes, content-type hints, and estimated response time metrics without modifying the original URL strings.

## 应用场景

**Content Aggregation Pipeline Development** - Engineers building automated reading list generators can use this project as a seed dataset for testing crawler politeness policies, retry logic, and HTML structure extraction heuristics across multiple wap subdomains.

**Academic Reference Collection** - Researchers studying mobile content distribution patterns can leverage the batch structure to analyze domain concentration, article ID entropy, and publication frequency trends over the 67-batch sequence.

**Monitoring and Alerting System Calibration** - Operations teams can deploy health check scripts that periodically validate each URL against the manifest, generating uptime reports and latency histograms for capacity planning.

**Data Migration Validation** - Organizations migrating from legacy wap platforms can use the resource list as a test corpus to verify URL rewriting rules, redirect chain correctness, and TLS compatibility before production cutover.

## 快速开始

Clone the repository and navigate to the project root directory. The following commands initialize the environment, install the minimal validation toolchain, and execute a basic integrity check against the current batch manifest.

```bash
git clone https://github.com/example/wapread-aggregator.git
cd wapread-aggregator

# Install Python 3.9+ virtual environment and dependencies
python3 -m venv venv
source venv/bin/activate
pip install --upgrade pip
pip install requests==2.31.0 click==8.1.7

# Run the built-in validator to check URL format compliance
python scripts/validate_manifest.py --batch 51 --strict

# Generate a plaintext report of all live URLs (timeout 5s, retry 2)
python scripts/health_check.py --input BATCH_51.md --output report_51.json --timeout 5 --retries 2
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 - 3.12 | 核心脚本运行环境，用于验证和健康检查 |
| pip | 23.0+ | Python 包管理器，用于安装 requests 和 click |
| requests | 2.31.0 | HTTP 客户端库，用于执行可选的链接可达性探测 |
| click | 8.1.7 | 命令行接口解析器，提供子命令和参数验证 |
| Git | 2.30+ | 版本控制系统，用于克隆仓库和切换批次标签 |
| 网络连接 | 任意 | 仅当运行健康检查时需访问外部域名；静态读取无需网络 |
| 磁盘空间 | 10 MB | 存储当前批次 Manifest 及历史批次归档（最多保留 12 个月） |
| 操作系统 | Linux / macOS / Windows WSL2 | 跨平台兼容，路径分隔符已做抽象处理 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户指南 | docs/usage.md | 如何获取最新批次、如何导出为 CSV/JSON、如何过滤特定域名条目 |
| 开发参考 | docs/architecture.md | 批次编号规则、新增域名流程、Manifest 格式版本升级策略 |
| 运维手册 | docs/operations.md | 健康检查频率建议、告警阈值设定、域名黑名单维护机制 |
| 设计决策 | docs/design.md | 为何选择静态 Markdown、为何保留原 URL 大小写、为何不自动添加协议前缀 |

## 资源列表

- http://wap.read.aovdbk.cn/Article/3048859.shtml
- http://wap.read.aovdbk.cn/Article/2582.shtml
- http://wap.read.zdvgjr.cn/Article/072920.shtml
- http://wap.read.aovdbk.cn/Article/822895.shtml
- http://wap.read.aovdbk.cn/Article/3798733.shtml
- http://wap.read.aovdbk.cn/Article/79253.shtml
- http://wap.read.zdvgjr.cn/Article/18589.shtml
- http://wap.read.zdvgjr.cn/Article/948502.shtml
- http://wap.read.zdvgjr.cn/Article/2348.shtml
- http://wap.read.zdvgjr.cn/Article/3507.shtml
- http://wap.read.zdvgjr.cn/Article/964337.shtml
- http://wap.read.aovdbk.cn/Article/260346.shtml
- http://wap.read.aovdbk.cn/Article/985429.shtml
- http://wap.read.zdvgjr.cn/Article/0431.shtml
- http://wap.read.zdvgjr.cn/Article/8626.shtml
- http://wap.read.zdvgjr.cn/Article/99688.shtml
- http://wap.read.aovdbk.cn/Article/61203.shtml
- http://wap.read.aovdbk.cn/Article/67691.shtml
- http://wap.read.aovdbk.cn/Article/42911.shtml
- http://wap.read.zdvgjr.cn/Article/3754.shtml
- http://wap.read.aovdbk.cn/Article/09604.shtml
- http://wap.read.aovdbk.cn/Article/374036.shtml
- http://wap.read.aovdbk.cn/Article/731208.shtml
- http://wap.read.zdvgjr.cn/Article/1689.shtml
- http://wap.read.zdvgjr.cn/Article/3694992.shtml
- http://wap.read.zdvgjr.cn/Article/6707.shtml
- http://wap.read.aovdbk.cn/Article/0821365.shtml
- http://wap.read.aovdbk.cn/Article/3864902.shtml
- http://wap.read.zdvgjr.cn/Article/9457.shtml
- http://wap.read.aovdbk.cn/Article/0387681.shtml
- http://wap.read.aovdbk.cn/Article/8515.shtml
- http://wap.read.aovdbk.cn/Article/764844.shtml
- http://wap.read.aovdbk.cn/Article/044497.shtml
- http://wap.read.aovdbk.cn/Article/320851.shtml
- http://wap.read.zdvgjr.cn/Article/9910731.shtml
- http://wap.read.zdvgjr.cn/Article/1149475.shtml
- http://wap.read.aovdbk.cn/Article/4213.shtml
- http://wap.read.zdvgjr.cn/Article/7606.shtml
- http://wap.read.aovdbk.cn/Article/0762.shtml
- http://wap.read.zdvgjr.cn/Article/6427624.shtml
- http://wap.read.aovdbk.cn/Article/291046.shtml
- http://wap.read.aovdbk.cn/Article/09597.shtml
- http://wap.read.aovdbk.cn/Article/8662875.shtml
- http://wap.read.aovdbk.cn/Article/0736823.shtml
- http://wap.read.zdvgjr.cn/Article/7161.shtml
- http://wap.read.zdvgjr.cn/Article/484659.shtml
- http://wap.read.zdvgjr.cn/Article/1135.shtml
- http://wap.read.zdvgjr.cn/Article/6486177.shtml
- http://wap.read.aovdbk.cn/Article/22231.shtml
- http://wap.read.aovdbk.cn/Article/613874.shtml
- http://wap.read.zdvgjr.cn/Article/021562.shtml
- http://wap.read.zdvgjr.cn/Article/129070.shtml
- http://wap.read.aovdbk.cn/Article/0556988.shtml
- http://wap.read.aovdbk.cn/Article/0638.shtml
- http://wap.read.aovdbk.cn/Article/1340.shtml
- http://wap.read.zdvgjr.cn/Article/186650.shtml
- http://wap.read.zdvgjr.cn/Article/9141276.shtml
- http://wap.read.aovdbk.cn/Article/952218.shtml
- http://wap.read.zdvgjr.cn/Article/248939.shtml
- http://wap.read.zdvgjr.cn/Article/9351.shtml
- http://wap.read.zdvgjr.cn/Article/80820.shtml
- http://wap.read.zdvgjr.cn/Article/51004.shtml
- http://wap.read.aovdbk.cn/Article/062536.shtml
- http://wap.read.aovdbk.cn/Article/7605.shtml
- http://wap.read.zdvgjr.cn/Article/434301.shtml
- http://wap.read.zdvgjr.cn/Article/83034.shtml
- http://wap.read.zdvgjr.cn/Article/7301.shtml
- http://wap.read.zdvgjr.cn/Article/93902.shtml
- http://wap.read.aovdbk.cn/Article/8214.shtml
- http://wap.read.zdvgjr.cn/Article/8339288.shtml
- http://wap.read.zdvgjr.cn/Article/11750.shtml
- http://wap.read.zdvgjr.cn/Article/50573.shtml
- http://wap.read.zdvgjr.cn/Article/86814.shtml
- http://wap.read.zdvgjr.cn/Article/43722.shtml
- http://wap.read.aovdbk.cn/Article/2935688.shtml
- http://wap.read.aovdbk.cn/Article/8779.shtml
- http://wap.read.aovdbk.cn/Article/4232.shtml
- http://wap.read.zdvgjr.cn/Article/34986.shtml
- http://wap.read.aovdbk.cn/Article/823143.shtml
- http://wap.read.aovdbk.cn/Article/8581264.shtml
- http://wap.read.aovdbk.cn/Article/4771871.shtml
- http://wap.read.aovdbk.cn/Article/99294.shtml
- http://wap.read.aovdbk.cn/Article/6747868.shtml
- http://wap.read.zdvgjr.cn/Article/523652.shtml
- http://wap.read.zdvgjr.cn/Article/53079.shtml
- http://wap.read.zdvgjr.cn/Article/6481.shtml
- http://wap.read.zdvgjr.cn/Article/12216.shtml
- http://wap.read.aovdbk.cn/Article/2870559.shtml
- http://wap.read.aovdbk.cn/Article/13344.shtml
- http://wap.read.aovdbk.cn/Article/4025.shtml
- http://wap.read.zdvgjr.cn/Article/3177.shtml
- http://wap.read.aovdbk.cn/Article/3100.shtml
- http://wap.read.zdvgjr.cn/Article/7598.shtml
- http://wap.read.aovdbk.cn/Article/2292546.shtml
- http://wap.read.aovdbk.cn/Article/1625491.shtml
- http://wap.read.zdvgjr.cn/Article/785195.shtml
- http://wap.read.zdvgjr.cn/Article/1416967.shtml
- http://wap.read.zdvgjr.cn/Article/91626.shtml
- http://wap.read.aovdbk.cn/Article/55562.shtml
- http://wap.read.aovdbk.cn/Article/2476.shtml
- http://wap.read.aovdbk.cn/Article/882414.shtml
- http://wap.read.zdvgjr.cn/Article/0008756.shtml
- http://wap.read.zdvgjr.cn/Article/8860.shtml
- http://wap.read.aovdbk.cn/Article/0633194.shtml
- http://wap.read.zdvgjr.cn/Article/59483.shtml
- http://wap.read.zdvgjr.cn/Article/969254.shtml
- http://wap.read.aovdbk.cn/Article/5308756.shtml
- http://wap.read.aovdbk.cn/Article/27357.shtml
- http://wap.read.aovdbk.cn/Article/950743.shtml
- http://wap.read.aovdbk.cn/Article/95711.shtml
- http://wap.read.aovdbk.cn/Article/214021.shtml
- http://wap.read.zdvgjr.cn/Article/44233.shtml
- http://wap.read.zdvgjr.cn/Article/920017.shtml
- http://wap.read.zdvgjr.cn/Article/9866677.shtml
- http://wap.read.aovdbk.cn/Article/048113.shtml
- http://wap.read.aovdbk.cn/Article/67226.shtml
- http://wap.read.aovdbk.cn/Article/65012.shtml
- http://wap.read.zdvgjr.cn/Article/5596062.shtml
- http://wap.read.aovdbk.cn/Article/939980.shtml
- http://wap.read.aovdbk.cn/Article/801792.shtml
- http://wap.read.zdvgjr.cn/Article/479891.shtml
- http://wap.read.zdvgjr.cn/Article/028683.shtml
- http://wap.read.zdvgjr.cn/Article/31570.shtml
- http://wap.read.zdvgjr.cn/Article/45731.shtml
- http://wap.read.zdvgjr.cn/Article/04700.shtml
- http://wap.read.zdvgjr.cn/Article/9167.shtml
- http://wap.read.aovdbk.cn/Article/91503.shtml
- http://wap.read.aovdbk.cn/Article/6805.shtml
- http://wap.read.aovdbk.cn/Article/786337.shtml
- http://wap.read.aovdbk.cn/Article/78208.shtml
- http://wap.read.aovdbk.cn/Article/9656388.shtml
- http://wap.read.zdvgjr.cn/Article/15122.shtml
- http://wap.read.aovdbk.cn/Article/167469.shtml
- http://wap.read.zdvgjr.cn/Article/070593.shtml
- http://wap.read.zdvgjr.cn/Article/0179400.shtml
- http://wap.read.aovdbk.cn/Article/89204.shtml
- http://wap.read.zdvgjr.cn/Article/31289.shtml
- http://wap.read.aovdbk.cn/Article/7662606.shtml
- http://wap.read.aovdbk.cn/Article/69383.shtml
- http://wap.read.zdvgjr.cn/Article/6122.shtml
- http://wap.read.aovdbk.cn/Article/74067.shtml
- http://wap.read.aovdbk.cn/Article/4643243.shtml
- http://wap.read.aovdbk.cn/Article/5586.shtml
- http://wap.read.zdvgjr.cn/Article/8972558.shtml
- http://wap.read.aovdbk.cn/Article/0877917.shtml
- http://wap.read.aovdbk.cn/Article/796009.shtml
- http://wap.read.zdvgjr.cn/Article/8195.shtml
- http://wap.read.aovdbk.cn/Article/1620721.shtml
- http://wap.read.zdvgjr.cn/Article/9166587.shtml
- http://wap.read.zdvgjr.cn/Article/27071.shtml

## 项目结构

```
wapread-aggregator/
├── BATCH_51.md                  # 当前批次主清单，包含 150 条原始 URL
├── BATCH_52.md                  # 下一批次占位模板（持续集成自动填充）
├── archive/                     # 历史批次归档（批次 1-50 压缩存储）
│   ├── batch_001-010.tar.gz     # 早期批次打包，保留用于回归测试
│   ├── batch_011-020.tar.gz     # 中间批次，含域名变动记录
│   └── manifest_index.json      # 所有批次的 SHA-256 校验和索引
├── scripts/                     # 工具脚本集合
│   ├── validate_manifest.py     # 检查 URL 格式、去重、协议一致性
│   ├── health_check.py          # 并发探测响应状态，生成 JSON 报告
│   ├── generate_csv.py          # 将 Markdown 列表转换为 CSV 格式
│   └── batch_rotator.sh         # 每周自动轮换批次编号并更新文档
├── tests/                       # 单元测试与集成测试
│   ├── test_validator.py        # 覆盖边缘用例（空行、多余空格、非 HTTP）
│   ├── test_health.py           # 模拟 HTTP 响应，验证重试和超时逻辑
│   └── fixtures/                # 固定测试数据，包含畸形 URL 样本
├── docs/                        # 完整文档体系
│   ├── usage.md                 # 命令行参数详解与输出示例
│   ├── architecture.md          # 批次编号语义、域名权重分配策略
│   ├── operations.md            # 生产环境部署清单与故障排查树
│   └── design.md                # URL 规范化决策记录与弃用策略
├── .github/                     # CI/CD 工作流定义
│   └── workflows/
│       └── nightly_health.yml   # 每日凌晨 2:00 执行全量链接健康检查
├── config/                      # 运行时配置文件
│   ├── domains_whitelist.txt    # 允许收录的域名前缀列表
│   └── timeout_policy.yaml      # 按域名分组的超时与重试阈值
└── README.md                    # 项目入口文档（即当前文件）
```

## 贡献指南

1.  Fork 本仓库并在本地克隆，创建以 `batch-{编号}-{描述}` 命名的功能分支，例如 `batch-52-add-zdvgjr`。所有分支必须基于最新的 `main` 分支创建。

2.  在 `archive/manifest_index.json` 中为新批次生成唯一的递增编号，并同步更新 `BATCH_{编号}.md` 文件。每个批次必须恰好包含 150 条 URL，且所有 URL 必须来自已批准的域名白名单。

3.  运行 `scripts/validate_manifest.py --batch {编号} --strict` 进行本地验证，确保无重复条目、无协议缺失、无格式异常。验证通过后提交变更，提交信息需包含批次编号和来源域名变更摘要。

4.  发起 Pull Request 到 `main` 分支，PR 描述中需附上 `health_check` 脚本的预运行结果摘要，至少包含响应成功率、平均响应时间、失败域名分类。PR 需要至少一名核心维护者审核。

5.  合并后，CI 流水线将自动触发全量健康检查并更新 `docs/operations.md` 中的监控面板链接。若检查失败率超过 5%，合并将被回滚并通知提交者。

## 常见问题

**Q: 为什么某些 URL 不包含协议前缀（http:// 或 https://），或者域名前缺少 www？**
A: 本项目严格遵循用户提供的原始 URL 字符串，不进行任何自动补全、规范化或重写。这样做的目的是保留数据源的原始意图，避免因假设协议或子域名而导致实际访问失败。使用者应根据自身网络环境自行决定是否添加重定向或重写规则。

**Q: 如何判断某个批次中的 URL 是否仍然有效？**
A: 项目提供了 `scripts/health_check.py` 工具，该工具使用 requests 库发送 HEAD 请求并记录状态码。建议用户定期（例如每周）运行该脚本，并结合 `--timeout` 和 `--retries` 参数调整探测强度。健康检查结果会输出为 JSON 文件，便于进一步分析。注意，部分域名可能拒绝 HEAD 请求，此时脚本会自动降级为 GET 请求并仅读取响应头。

**Q: 当前批次只有 150 条，但实际业务需要更多样本，如何扩展？**
A: 本项目采用固定批次大小设计，每个批次包含 150 条 URL，总共规划 67 个批次。若需更大规模数据集，可以通过组合多个批次（例如 Batch 1-50）构建自定义合集。项目仓库中的 `archive/` 目录提供了历史批次的压缩包，用户可解压后使用 `scripts/generate_csv.py` 合并为单一大文件。如需新增额外批次，请按照贡献指南提交 PR，核心团队会根据域名资源可用性评估是否扩展批次总数。

## 许可证

MIT

> 外链数量: 150 | 生成时间: 2026-07-10 00:06:11
