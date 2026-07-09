# LinkHarbor 技术资源导航聚合系统

LinkHarbor 是一个面向开发者、技术研究人员及内容聚合场景的轻量化外链管理与资源导航平台。该项目旨在解决个人或团队在维护大量技术文档、教程、工具站及内部知识库链接时面临的分类混乱、检索低效和重复录入问题，通过结构化的数据组织与静态站点生成能力，将零散的 URL 资源转化为可维护、可分享、可快速访问的导航目录。项目主要服务对象为开源技术博主、技术社群维护者、企业内训知识管理员以及需要高频访问特定技术参考链接的研发人员。

LinkHarbor 不提供动态后台服务，而是采用纯静态资源聚合方案，所有链接数据以标记文件形式存储，支持通过命令行工具进行批量导入、去重校验、分类标签生成以及响应式前端界面的自动化构建。系统核心设计理念为数据与表现分离，用户可通过编辑结构化配置文件或 CSV 数据源来更新资源库，构建过程无需数据库支持，产出物为可直接部署至对象存储或 Web 服务器的完整静态站点。当前批次为第 59/67 批资源导入，累计处理外链数量已达 150 条，覆盖技术阅读、知识文档、行业资讯等多个子类目。

## 功能概览

批量链接导入解析：支持从纯文本列表、CSV 文件或剪贴板数据中批量读取 URL，自动识别协议头与域名层级，并生成初始分类标签。

自动去重与冲突检测：对导入的每条链接进行 MD5 哈希校验，与现有资源库对比，自动标记重复项并输出冲突报告，避免冗余录入。

智能标签推荐：基于 URL 路径关键词、域名特征以及资源标题中的高频词，为每条链接生成 2 至 4 个候选分类标签，降低人工归类成本。

响应式静态站点生成：内置基于 Flexbox 与 CSS Grid 的响应式模板，生成的导航页面在桌面、平板与移动设备上均能保持良好的浏览体验。

全文标题检索：构建阶段为每条链接抓取页面标题并生成索引文件，支持前端基于标题关键词的即时筛选与模糊匹配。

自定义分类层级管理：允许用户通过修改 YAML 配置文件定义多级分类结构，支持分类重命名、合并及排序操作，无需修改前端代码。

增量构建与缓存复用：仅对有变动的资源文件重新生成对应页面，未变更部分直接复用上次构建的缓存，大幅缩短大型资源库的构建时间。

## 应用场景

技术博客文章附件导航：技术博主在发布系列教程时，可使用 LinkHarbor 整理每篇文章中引用的外部参考资料、代码仓库及工具文档，生成独立的资源导航页附于文末，方便读者一键直达。

企业内训知识库外链管理：企业内部培训部门将分散在邮件、即时通讯群组中的学习视频链接、官方文档地址和练习平台入口统一收录至 LinkHarbor，按课程模块分类，生成专属学习门户，新员工入职时可快速获取全部必读资源。

开源项目周边生态汇总：开源项目维护者利用 LinkHarbor 收集与项目相关的插件列表、社区教程、兼容性测试工具以及部署示例，作为项目 README 的补充资源页面，降低社区贡献者的信息查找成本。

技术社群每周精选推荐：技术交流社群管理员每周整理群内讨论中出现的优质文章、工具更新公告及线上活动报名链接，导入 LinkHarbor 生成周报形式的资源导航，通过静态页面的固定地址分享给全体成员，避免重要信息被聊天记录淹没。

个人知识体系外链备份：独立开发者或研究人员将长期积累的技术收藏夹（如浏览器书签导出）导入 LinkHarbor，按技术领域、语言生态或问题域重新组织，构建个人专属的轻量级知识图谱，便于跨设备访问及版本回溯。

## 快速开始

以下指令适用于 Linux 及 macOS 环境，Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库至本地
git clone https://github.com/linkharbor/core.git linkharbor

# 进入项目工作目录
cd linkharbor

# 安装项目依赖（需要 Node.js 18 及以上版本）
npm install

# 执行资源导入与站点构建（示例数据为批次 59/67）
npm run build -- --batch=59

# 启动本地预览服务，默认监听端口 8080
npm run serve
```

执行完成后，打开浏览器访问 http://localhost:8080 即可查看生成的导航站点。如需导入自定义链接列表，请将 URL 数据存放于 `data/import/latest.txt` 文件后再次执行 `npm run build`。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Node.js | 18.0.0 或更高 | 运行时环境，用于执行构建脚本与依赖管理 |
| npm | 9.0.0 或更高 | 包管理器，用于安装项目依赖及运行自定义脚本 |
| Git | 2.25.0 或更高 | 版本控制工具，用于克隆仓库及获取更新 |
| 文件系统权限 | 读写 | 项目需要在工作目录下创建缓存、输出及临时文件目录 |
| 网络访问 | 外网连通 | 构建过程中需要抓取链接标题，依赖对外部域名的 HTTPS 访问 |
| 内存 | 至少 512 MB | 构建 1000 条以内资源时推荐最低内存配置 |
| 磁盘空间 | 至少 200 MB | 包含依赖安装、缓存及静态输出文件的总占用空间 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户指南 | docs/user-guide/quick-start.md | 如何首次安装、配置数据源并生成第一个导航站点 |
| 配置手册 | docs/configuration/schema.md | 分类层级配置文件的结构、字段含义及示例模板 |
| 数据处理 | docs/data-processing/import-formats.md | 支持哪些导入格式、如何自定义字段映射及清洗规则 |
| 部署指南 | docs/deployment/hosting-options.md | 构建产物如何部署至 Vercel、Netlify 或自建 Nginx 服务器 |
| API 参考 | docs/api/cli-commands.md | 构建工具提供的全部命令行参数、环境变量及退出码说明 |

## 资源列表

- http://h5.read.aovdbk.cn/Article/1691254.shtml
- http://h5.read.zdvgjr.cn/Article/3240.shtml
- http://h5.read.aovdbk.cn/Article/977187.shtml
- http://h5.read.zdvgjr.cn/Article/16860.shtml
- http://h5.read.aovdbk.cn/Article/4058.shtml
- http://h5.read.zdvgjr.cn/Article/4325776.shtml
- http://h5.read.zdvgjr.cn/Article/7354.shtml
- http://h5.read.aovdbk.cn/Article/4221.shtml
- http://h5.read.zdvgjr.cn/Article/3755.shtml
- http://h5.read.zdvgjr.cn/Article/66300.shtml
- http://h5.read.aovdbk.cn/Article/9686773.shtml
- http://h5.read.zdvgjr.cn/Article/108868.shtml
- http://h5.read.aovdbk.cn/Article/81768.shtml
- http://h5.read.zdvgjr.cn/Article/60608.shtml
- http://h5.read.zdvgjr.cn/Article/8335.shtml
- http://h5.read.zdvgjr.cn/Article/5421965.shtml
- http://h5.read.aovdbk.cn/Article/362451.shtml
- http://h5.read.aovdbk.cn/Article/5792271.shtml
- http://h5.read.aovdbk.cn/Article/174390.shtml
- http://h5.read.aovdbk.cn/Article/2497.shtml
- http://h5.read.zdvgjr.cn/Article/2678.shtml
- http://h5.read.aovdbk.cn/Article/3896.shtml
- http://h5.read.aovdbk.cn/Article/34540.shtml
- http://h5.read.zdvgjr.cn/Article/8191160.shtml
- http://h5.read.zdvgjr.cn/Article/2692.shtml
- http://h5.read.zdvgjr.cn/Article/27050.shtml
- http://h5.read.zdvgjr.cn/Article/534049.shtml
- http://h5.read.aovdbk.cn/Article/9437332.shtml
- http://h5.read.zdvgjr.cn/Article/0508.shtml
- http://h5.read.zdvgjr.cn/Article/0448.shtml
- http://h5.read.zdvgjr.cn/Article/181488.shtml
- http://h5.read.zdvgjr.cn/Article/55759.shtml
- http://h5.read.zdvgjr.cn/Article/4046634.shtml
- http://h5.read.zdvgjr.cn/Article/913011.shtml
- http://h5.read.zdvgjr.cn/Article/181909.shtml
- http://h5.read.zdvgjr.cn/Article/3026727.shtml
- http://h5.read.zdvgjr.cn/Article/080488.shtml
- http://h5.read.zdvgjr.cn/Article/92028.shtml
- http://h5.read.zdvgjr.cn/Article/4545706.shtml
- http://h5.read.aovdbk.cn/Article/92227.shtml
- http://h5.read.aovdbk.cn/Article/9977.shtml
- http://h5.read.aovdbk.cn/Article/43533.shtml
- http://h5.read.aovdbk.cn/Article/34034.shtml
- http://h5.read.zdvgjr.cn/Article/2036997.shtml
- http://h5.read.aovdbk.cn/Article/114261.shtml
- http://h5.read.zdvgjr.cn/Article/2829624.shtml
- http://h5.read.zdvgjr.cn/Article/971694.shtml
- http://h5.read.zdvgjr.cn/Article/7774549.shtml
- http://h5.read.aovdbk.cn/Article/23545.shtml
- http://h5.read.zdvgjr.cn/Article/8514594.shtml
- http://h5.read.aovdbk.cn/Article/86499.shtml
- http://h5.read.zdvgjr.cn/Article/639305.shtml
- http://h5.read.aovdbk.cn/Article/74091.shtml
- http://h5.read.zdvgjr.cn/Article/37877.shtml
- http://h5.read.zdvgjr.cn/Article/996971.shtml
- http://h5.read.aovdbk.cn/Article/6809479.shtml
- http://h5.read.zdvgjr.cn/Article/3956921.shtml
- http://h5.read.aovdbk.cn/Article/2910.shtml
- http://h5.read.aovdbk.cn/Article/7131376.shtml
- http://h5.read.aovdbk.cn/Article/4880.shtml
- http://h5.read.zdvgjr.cn/Article/37605.shtml
- http://h5.read.zdvgjr.cn/Article/9409.shtml
- http://h5.read.aovdbk.cn/Article/1818094.shtml
- http://h5.read.zdvgjr.cn/Article/066761.shtml
- http://h5.read.zdvgjr.cn/Article/8985594.shtml
- http://h5.read.aovdbk.cn/Article/69826.shtml
- http://h5.read.aovdbk.cn/Article/55878.shtml
- http://h5.read.aovdbk.cn/Article/0768884.shtml
- http://h5.read.zdvgjr.cn/Article/8253688.shtml
- http://h5.read.aovdbk.cn/Article/0097943.shtml
- http://h5.read.aovdbk.cn/Article/304847.shtml
- http://h5.read.zdvgjr.cn/Article/128361.shtml
- http://h5.read.zdvgjr.cn/Article/76078.shtml
- http://h5.read.zdvgjr.cn/Article/593471.shtml
- http://h5.read.aovdbk.cn/Article/1564262.shtml
- http://h5.read.zdvgjr.cn/Article/5473.shtml
- http://h5.read.aovdbk.cn/Article/9410810.shtml
- http://h5.read.aovdbk.cn/Article/88448.shtml
- http://h5.read.zdvgjr.cn/Article/3344.shtml
- http://h5.read.zdvgjr.cn/Article/38510.shtml
- http://h5.read.aovdbk.cn/Article/99853.shtml
- http://h5.read.aovdbk.cn/Article/9509411.shtml
- http://h5.read.zdvgjr.cn/Article/0224060.shtml
- http://h5.read.aovdbk.cn/Article/0747497.shtml
- http://h5.read.zdvgjr.cn/Article/5424.shtml
- http://h5.read.zdvgjr.cn/Article/016193.shtml
- http://h5.read.aovdbk.cn/Article/35181.shtml
- http://h5.read.zdvgjr.cn/Article/99814.shtml
- http://h5.read.zdvgjr.cn/Article/2575182.shtml
- http://h5.read.zdvgjr.cn/Article/9498.shtml
- http://h5.read.zdvgjr.cn/Article/567971.shtml
- http://h5.read.aovdbk.cn/Article/987562.shtml
- http://h5.read.aovdbk.cn/Article/5093.shtml
- http://h5.read.aovdbk.cn/Article/3402984.shtml
- http://h5.read.zdvgjr.cn/Article/64274.shtml
- http://h5.read.zdvgjr.cn/Article/7822.shtml
- http://h5.read.zdvgjr.cn/Article/568334.shtml
- http://h5.read.zdvgjr.cn/Article/9611.shtml
- http://h5.read.zdvgjr.cn/Article/4318026.shtml
- http://h5.read.zdvgjr.cn/Article/72898.shtml
- http://h5.read.zdvgjr.cn/Article/4599.shtml
- http://h5.read.zdvgjr.cn/Article/323729.shtml
- http://h5.read.zdvgjr.cn/Article/581959.shtml
- http://h5.read.aovdbk.cn/Article/48535.shtml
- http://h5.read.aovdbk.cn/Article/1957.shtml
- http://h5.read.aovdbk.cn/Article/60947.shtml
- http://h5.read.aovdbk.cn/Article/2324.shtml
- http://h5.read.zdvgjr.cn/Article/5973907.shtml
- http://h5.read.zdvgjr.cn/Article/59099.shtml
- http://h5.read.aovdbk.cn/Article/3402.shtml
- http://h5.read.zdvgjr.cn/Article/643746.shtml
- http://h5.read.zdvgjr.cn/Article/06174.shtml
- http://h5.read.zdvgjr.cn/Article/5445.shtml
- http://h5.read.zdvgjr.cn/Article/896416.shtml
- http://h5.read.zdvgjr.cn/Article/488609.shtml
- http://h5.read.zdvgjr.cn/Article/2246.shtml
- http://h5.read.aovdbk.cn/Article/2690.shtml
- http://h5.read.zdvgjr.cn/Article/09450.shtml
- http://h5.read.zdvgjr.cn/Article/473740.shtml
- http://h5.read.aovdbk.cn/Article/6951.shtml
- http://h5.read.aovdbk.cn/Article/289948.shtml
- http://h5.read.zdvgjr.cn/Article/70674.shtml
- http://h5.read.aovdbk.cn/Article/63791.shtml
- http://h5.read.zdvgjr.cn/Article/024601.shtml
- http://h5.read.zdvgjr.cn/Article/8780090.shtml
- http://h5.read.zdvgjr.cn/Article/5075207.shtml
- http://h5.read.aovdbk.cn/Article/108936.shtml
- http://h5.read.zdvgjr.cn/Article/044360.shtml
- http://h5.read.aovdbk.cn/Article/7958182.shtml
- http://h5.read.aovdbk.cn/Article/2659.shtml
- http://h5.read.zdvgjr.cn/Article/13727.shtml
- http://h5.read.aovdbk.cn/Article/0133.shtml
- http://h5.read.aovdbk.cn/Article/003847.shtml
- http://h5.read.zdvgjr.cn/Article/2817.shtml
- http://h5.read.zdvgjr.cn/Article/2091.shtml
- http://h5.read.aovdbk.cn/Article/4046586.shtml
- http://h5.read.aovdbk.cn/Article/2611336.shtml
- http://h5.read.aovdbk.cn/Article/06246.shtml
- http://h5.read.aovdbk.cn/Article/0314324.shtml
- http://h5.read.aovdbk.cn/Article/831691.shtml
- http://h5.read.aovdbk.cn/Article/9629649.shtml
- http://h5.read.aovdbk.cn/Article/2391369.shtml
- http://h5.read.zdvgjr.cn/Article/5877675.shtml
- http://h5.read.zdvgjr.cn/Article/683557.shtml
- http://h5.read.zdvgjr.cn/Article/21913.shtml
- http://h5.read.zdvgjr.cn/Article/2129.shtml
- http://h5.read.zdvgjr.cn/Article/8803.shtml
- http://h5.read.zdvgjr.cn/Article/7298.shtml
- http://h5.read.zdvgjr.cn/Article/539221.shtml
- http://h5.read.aovdbk.cn/Article/006506.shtml

## 项目结构

```
linkharbor/
├── bin/
│   └── linkharbor.js               # CLI 入口文件，解析命令行参数并调度构建流程
├── config/
│   └── default.yaml                # 默认分类体系、标签规则及输出路径配置
├── data/
│   ├── import/                     # 存放待导入的原始链接列表文件
│   │   └── latest.txt              # 当前批次导入数据（批次 59/67）
│   ├── cache/                      # 构建缓存目录，存储已抓取的标题及哈希索引
│   │   ├── titles.db               # SQLite 轻量数据库，记录 URL 与标题映射
│   │   └── checksums.json          # 链接哈希索引，用于快速去重
│   └── output/                     # 构建产出的静态站点根目录
│       ├── index.html              # 导航首页，包含全部分类入口及搜索框
│       ├── categories/             # 分类详情页目录，每个分类生成独立页面
│       │   ├── devops.html
│       │   ├── frontend.html
│       │   └── backend.html
│       ├── assets/                 # 样式表、JavaScript 及字体等静态资源
│       │   ├── css/
│       │   ├── js/
│       │   └── images/
│       └── sitemap.xml             # 站点地图，供搜索引擎爬取
├── docs/                           # 完整项目文档，涵盖使用指南与开发参考
│   ├── user-guide/
│   ├── configuration/
│   ├── data-processing/
│   ├── deployment/
│   └── api/
├── src/                            # 核心源代码目录
│   ├── parsers/                    # 链接解析模块，处理不同格式的导入数据
│   │   ├── csv-parser.js
│   │   └── plaintext-parser.js
│   ├── builders/                   # 静态页面生成器
│   │   ├── page-builder.js
│   │   └── index-builder.js
│   ├── utils/                      # 通用工具函数集
│   │   ├── hash-util.js
│   │   ├── fetch-title.js
│   │   └── logger.js
│   └── index.js                    # 模块入口，导出主要构建函数
├── tests/                          # 单元测试与集成测试用例
│   ├── parsers.test.js
│   ├── builders.test.js
│   └── fixtures/                   # 测试用的固定数据样本
├── package.json                    # npm 项目清单，声明依赖与脚本
├── README.md                       # 本文件，项目概览与快速指引
└── LICENSE                         # MIT 许可证文本
```

## 贡献指南

1.  Fork 本仓库至个人账号下，克隆至本地开发环境，并确保通过 `npm install` 安装所有开发依赖。建议使用 Node.js 18 及以上版本，并开启 Corepack 以使用项目指定的包管理器版本。

2.  在 `src/` 目录下完成功能修改或缺陷修复后，需在 `tests/` 对应文件中补充单元测试用例，确保新增代码覆盖率达到 80% 以上。提交前执行 `npm run test` 与 `npm run lint` 验证代码规范与测试通过率。

3.  提交变更时请遵循 Conventional Commits 规范，使用 `feat:`、`fix:`、`docs:`、`refactor:` 等类型前缀，并在提交信息中清晰描述变更原因与影响范围。提交信息建议采用英文撰写，长度不超过 72 字符。

4.  向本仓库的 `develop` 分支发起 Pull Request，并在 PR 描述中关联相关 Issue 编号（如有），详细说明测试结果与手动验证步骤。PR 合并前需要至少一位项目维护者进行 Code Review 并批准。

5.  若涉及数据导入格式或配置结构的变更，请同步更新 `docs/` 目录下的对应文档，并确保示例配置文件与实际代码保持一致。文档变更应与代码变更在同一次 PR 中提交。

## 常见问题

Q: 构建过程中出现 "ECONNRESET" 或 "ETIMEDOUT" 网络错误，导致标题抓取失败，应如何处理？

A: 该问题通常由于目标站点对频繁请求进行限流或网络环境不稳定导致。建议首先检查本地网络连通性，并确认是否配置了代理环境变量（如 HTTP_PROXY）。若问题持续，可在构建命令中添加 `--retry=3` 参数启用重试机制，或使用 `--skip-fetch` 跳过标题抓取，仅基于 URL 路径生成导航条目。对于需要稳定抓取的场景，推荐在低峰时段执行构建或使用稳定的 VPN 出口 IP。

Q: 如何将现有浏览器书签导出文件导入至 LinkHarbor？

A: LinkHarbor 目前不直接支持 HTML 书签格式解析，但您可以将浏览器书签管理器中的链接批量复制为纯文本列表（每行一个 URL），保存至 `data/import/latest.txt` 后执行构建。如需保留书签文件夹分类信息，建议先将书签导出为 CSV 格式，并使用项目提供的 `tools/convert-bookmark.js` 辅助脚本将 CSV 转换为项目支持的导入格式。转换后的数据会保留分类层级，并自动映射至配置文件中定义的分类体系。

Q: 构建生成的静态页面在移动端显示时分类标签重叠，如何调整？

A: 该问题通常与自定义分类名称过长或嵌套层级过深有关。请检查 `config/default.yaml` 中的分类名称，将长度控制在 6 个中文字符以内。若需深层嵌套，建议通过修改 `src/templates/category.ejs` 中的栅格布局参数（如将 `grid-template-columns` 从 `repeat(4, 1fr)` 调整为 `repeat(2, 1fr)`）来适配移动设备。项目不提供自动响应式修复工具，但您可以覆写 `assets/css/custom.css` 文件中的媒体查询断点，以覆盖默认样式。

## 许可证

MIT

> 外链数量: 150 | 生成时间: 2026-07-10 00:06:11
