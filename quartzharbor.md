# ResourceLink Aggregate Catalog

ResourceLink Aggregate Catalog 是一个面向技术内容聚合与结构化外链管理的开源项目。项目定位为轻量级技术资源导航枢纽，服务于开发者、技术内容运营者以及信息密集型团队的日常外链整理与快速查阅需求。项目本身不存储任何实体内容，仅提供统一的链接收录规范、分类索引框架与可部署的静态目录界面，帮助用户在碎片化信息环境中建立可维护、可审计、可分享的外链资产库。

本项目解决的核心问题在于：技术团队在文档撰写、项目调研或日常学习中，往往积累大量散落的文章链接、官方文档入口与临时参考页。这些链接分散在即时通讯记录、本地书签或多人协作文档中，缺乏统一的元数据描述与健康检查机制，导致链接失效、归属不明、复用困难。ResourceLink Aggregate Catalog 通过标准化的目录树结构、依赖无关的纯静态部署方式以及严格的 URL 原样保留策略，为上述问题提供工程化解决方案。

## 功能概览

**原始链接原样收录** 系统对用户提交的所有 URL 执行严格的原样输出策略，不补全协议、不添加或移除 www 前缀、不修改大小写、不添加尾部斜杠，确保链接地址与原始来源完全一致，满足审计合规与引用准确性要求。

**双域名资源隔离管理** 项目内置对 aovdbk.cn 与 zdvgjr.cn 两个主要内容域的识别与分类逻辑，在索引视图中自动区分来源域名，便于用户按站点维度筛选和查阅文章资源。

**轻量级静态目录生成** 基于项目根目录下的资源清单与配置文件，自动生成符合人类阅读习惯的层级化索引页面，支持按文章编号、批次归属、域名来源等多维度排序与检索。

**零依赖部署架构** 项目不依赖任何第三方运行时环境或数据库系统，编译后产出物为纯静态 HTML 与 Markdown 文件，可直接挂载至任意 Web 服务器或对象存储服务。

**批次化数据管理** 每批次资源链接独立归档，支持批次编号、资源总数统计与批次间切换浏览，便于运营团队按时间线或项目阶段回溯历史数据。

**链接健康状态可观测** 提供基础的外链存活检测钩子接口，用户可结合定时任务对收录链接进行 HTTP 状态码检查，并生成失效链接报表。

**多端适配的浏览界面** 索引页面采用响应式布局，在桌面端、平板与移动设备上均能完整展示长链接列表，支持一键复制原始 URL 到系统剪贴板。

## 应用场景

技术文档团队的外链资产沉淀
技术文档撰写过程中，编辑人员需要引用大量外部规范、RFC 文档、开源项目仓库地址以及社区讨论帖。通过 ResourceLink Aggregate Catalog，团队可将每篇文档涉及的外部链接统一收录至项目仓库，并在文档末尾自动生成可追溯的参考链接附录，避免链接散落在各个 Word 文件或在线文档评论中。

开源项目 README 的多源引用管理
开源项目的 README 文件常需列举依赖项目、同类产品对比链接、社区教程与视频资源。项目维护者可使用本项目的批次管理功能，将不同来源的链接按主题分批导入，再通过项目结构中的 resources 目录统一维护，最终在 README 中仅保留指向本项目的链接索引地址，大幅缩减 README 篇幅。

技术调研与竞品分析的信息收集
进行技术选型或竞品分析时，分析师需打开数十个相关页面并反复切换。本项目允许分析师一次性将所有调研链接导入系统，并在索引页面为每条链接添加人工备注字段，形成可分享的调研素材库，提升信息收集与团队评审效率。

内容聚合站点的外链中间层
内容聚合平台或导航站点运营方，可通过本项目作为外链数据的中转校验层。在将用户提交的链接正式写入数据库之前，先经过本项目的链接归一化与批次归档流程，确保入库链接格式统一、来源清晰，并可追溯每次批量导入的变更记录。

## 快速开始

以下指令适用于 Linux 与 macOS 环境，Windows 用户建议使用 Git Bash 或 WSL 执行。

```bash
# 克隆项目仓库至本地
git clone https://github.com/resourcelink/aggregate-catalog.git

# 进入项目工作目录
cd aggregate-catalog

# 安装项目依赖（仅用于本地开发预览，生产环境无需执行）
npm install

# 执行资源索引构建脚本，生成静态目录页面
npm run build

# 启动本地开发服务器，预览生成的索引页面
npm run serve
```

执行完毕后，在浏览器中访问 http://localhost:8080 即可查看当前批次的资源索引首页。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 16.x 或更高 | 仅本地构建与预览时需要，生产环境静态部署无需安装 |
| npm | 8.x 或更高 | 用于安装构建工具链与开发依赖 |
| Git | 2.25 或更高 | 用于克隆仓库与版本管理 |
| 现代浏览器 | Chrome 90+ / Firefox 88+ / Edge 90+ | 预览索引页面时建议使用最新版本 |
| 文件系统权限 | 读/写 | 项目构建过程需在 .cache 与 dist 目录写入临时文件 |
| 网络连接 | 外网可访问 | 构建时需从 npm  registry 下载依赖包，运行时无需网络 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide.md | 如何导入新批次链接、如何自定义索引页排序规则、如何导出链接清单 |
| 运营指南 | docs/operations.md | 如何检查链接有效性、如何更新已有链接的备注信息、如何生成批次报告 |
| 开发者文档 | docs/developer.md | 项目目录结构说明、构建流程详解、如何扩展新的输出格式（JSON/CSV） |
| 设计决策 | docs/design-decisions.md | 为何采用纯静态架构、为何严格保留原始 URL、链接去重策略的取舍 |

## 资源列表

- http://wap.read.aovdbk.cn/Article/637344.shtml
- http://wap.read.aovdbk.cn/Article/704483.shtml
- http://wap.read.aovdbk.cn/Article/746825.shtml
- http://wap.read.aovdbk.cn/Article/35916.shtml
- http://wap.read.zdvgjr.cn/Article/261066.shtml
- http://wap.read.aovdbk.cn/Article/98690.shtml
- http://wap.read.zdvgjr.cn/Article/3705.shtml
- http://wap.read.zdvgjr.cn/Article/1157992.shtml
- http://wap.read.zdvgjr.cn/Article/5454406.shtml
- http://wap.read.zdvgjr.cn/Article/013735.shtml
- http://wap.read.aovdbk.cn/Article/87983.shtml
- http://wap.read.zdvgjr.cn/Article/9582364.shtml
- http://wap.read.zdvgjr.cn/Article/455570.shtml
- http://wap.read.zdvgjr.cn/Article/3296.shtml
- http://wap.read.aovdbk.cn/Article/11935.shtml
- http://wap.read.aovdbk.cn/Article/773932.shtml
- http://wap.read.zdvgjr.cn/Article/3444551.shtml
- http://wap.read.aovdbk.cn/Article/1461.shtml
- http://wap.read.zdvgjr.cn/Article/5493.shtml
- http://wap.read.aovdbk.cn/Article/3876099.shtml
- http://wap.read.aovdbk.cn/Article/4430347.shtml
- http://wap.read.aovdbk.cn/Article/2862.shtml
- http://wap.read.aovdbk.cn/Article/2920732.shtml
- http://wap.read.aovdbk.cn/Article/1703.shtml
- http://wap.read.aovdbk.cn/Article/8476.shtml
- http://wap.read.zdvgjr.cn/Article/83525.shtml
- http://wap.read.zdvgjr.cn/Article/459025.shtml
- http://wap.read.aovdbk.cn/Article/4383491.shtml
- http://wap.read.zdvgjr.cn/Article/9003.shtml
- http://wap.read.aovdbk.cn/Article/3881.shtml
- http://wap.read.zdvgjr.cn/Article/15258.shtml
- http://wap.read.aovdbk.cn/Article/919371.shtml
- http://wap.read.aovdbk.cn/Article/118685.shtml
- http://wap.read.zdvgjr.cn/Article/937318.shtml
- http://wap.read.zdvgjr.cn/Article/0126261.shtml
- http://wap.read.zdvgjr.cn/Article/010167.shtml
- http://wap.read.aovdbk.cn/Article/16657.shtml
- http://wap.read.zdvgjr.cn/Article/7574.shtml
- http://wap.read.aovdbk.cn/Article/921817.shtml
- http://wap.read.zdvgjr.cn/Article/965143.shtml
- http://wap.read.aovdbk.cn/Article/620558.shtml
- http://wap.read.aovdbk.cn/Article/038583.shtml
- http://wap.read.aovdbk.cn/Article/6365.shtml
- http://wap.read.aovdbk.cn/Article/3024988.shtml
- http://wap.read.aovdbk.cn/Article/016458.shtml
- http://wap.read.aovdbk.cn/Article/9542.shtml
- http://wap.read.zdvgjr.cn/Article/765130.shtml
- http://wap.read.aovdbk.cn/Article/2748903.shtml
- http://wap.read.aovdbk.cn/Article/346307.shtml
- http://wap.read.zdvgjr.cn/Article/828580.shtml
- http://wap.read.aovdbk.cn/Article/296778.shtml
- http://wap.read.zdvgjr.cn/Article/88678.shtml
- http://wap.read.aovdbk.cn/Article/46462.shtml
- http://wap.read.zdvgjr.cn/Article/7994.shtml
- http://wap.read.aovdbk.cn/Article/429189.shtml
- http://wap.read.aovdbk.cn/Article/7187.shtml
- http://wap.read.aovdbk.cn/Article/9986610.shtml
- http://wap.read.aovdbk.cn/Article/082299.shtml
- http://wap.read.aovdbk.cn/Article/58763.shtml
- http://wap.read.zdvgjr.cn/Article/191575.shtml
- http://wap.read.zdvgjr.cn/Article/50330.shtml
- http://wap.read.aovdbk.cn/Article/505780.shtml
- http://wap.read.aovdbk.cn/Article/2650303.shtml
- http://wap.read.aovdbk.cn/Article/764059.shtml
- http://wap.read.aovdbk.cn/Article/9294.shtml
- http://wap.read.zdvgjr.cn/Article/3348.shtml
- http://wap.read.zdvgjr.cn/Article/5663584.shtml
- http://wap.read.zdvgjr.cn/Article/364251.shtml
- http://wap.read.aovdbk.cn/Article/6003075.shtml
- http://wap.read.aovdbk.cn/Article/29367.shtml
- http://wap.read.zdvgjr.cn/Article/43819.shtml
- http://wap.read.zdvgjr.cn/Article/37884.shtml
- http://wap.read.aovdbk.cn/Article/6792680.shtml
- http://wap.read.aovdbk.cn/Article/2774.shtml
- http://wap.read.aovdbk.cn/Article/58750.shtml
- http://wap.read.aovdbk.cn/Article/185411.shtml
- http://wap.read.zdvgjr.cn/Article/55653.shtml
- http://wap.read.zdvgjr.cn/Article/38337.shtml
- http://wap.read.zdvgjr.cn/Article/2748.shtml
- http://wap.read.aovdbk.cn/Article/22812.shtml
- http://wap.read.zdvgjr.cn/Article/61815.shtml
- http://wap.read.zdvgjr.cn/Article/5748923.shtml
- http://wap.read.aovdbk.cn/Article/1368.shtml
- http://wap.read.zdvgjr.cn/Article/3408400.shtml
- http://wap.read.aovdbk.cn/Article/17410.shtml
- http://wap.read.zdvgjr.cn/Article/429852.shtml
- http://wap.read.aovdbk.cn/Article/4023120.shtml
- http://wap.read.zdvgjr.cn/Article/574657.shtml
- http://wap.read.aovdbk.cn/Article/93487.shtml
- http://wap.read.zdvgjr.cn/Article/9955464.shtml
- http://wap.read.aovdbk.cn/Article/760294.shtml
- http://wap.read.aovdbk.cn/Article/8950724.shtml
- http://wap.read.aovdbk.cn/Article/647218.shtml
- http://wap.read.aovdbk.cn/Article/70502.shtml
- http://wap.read.zdvgjr.cn/Article/727645.shtml
- http://wap.read.zdvgjr.cn/Article/8977.shtml
- http://wap.read.aovdbk.cn/Article/3252.shtml
- http://wap.read.aovdbk.cn/Article/65754.shtml
- http://wap.read.aovdbk.cn/Article/635424.shtml
- http://wap.read.zdvgjr.cn/Article/4433205.shtml
- http://wap.read.aovdbk.cn/Article/709949.shtml
- http://wap.read.aovdbk.cn/Article/7247494.shtml
- http://wap.read.zdvgjr.cn/Article/9401179.shtml
- http://wap.read.aovdbk.cn/Article/7102734.shtml
- http://wap.read.aovdbk.cn/Article/99380.shtml
- http://wap.read.aovdbk.cn/Article/45697.shtml
- http://wap.read.zdvgjr.cn/Article/42982.shtml
- http://wap.read.aovdbk.cn/Article/382874.shtml
- http://wap.read.aovdbk.cn/Article/97088.shtml
- http://wap.read.aovdbk.cn/Article/0640.shtml
- http://wap.read.aovdbk.cn/Article/2100.shtml
- http://wap.read.zdvgjr.cn/Article/9416.shtml
- http://wap.read.zdvgjr.cn/Article/92819.shtml
- http://wap.read.zdvgjr.cn/Article/5894718.shtml
- http://wap.read.zdvgjr.cn/Article/49802.shtml
- http://wap.read.aovdbk.cn/Article/145523.shtml
- http://wap.read.aovdbk.cn/Article/05640.shtml
- http://wap.read.aovdbk.cn/Article/6798996.shtml
- http://wap.read.aovdbk.cn/Article/14778.shtml
- http://wap.read.zdvgjr.cn/Article/4578830.shtml
- http://wap.read.aovdbk.cn/Article/361785.shtml
- http://wap.read.zdvgjr.cn/Article/1364.shtml
- http://wap.read.zdvgjr.cn/Article/57595.shtml
- http://wap.read.zdvgjr.cn/Article/140174.shtml
- http://wap.read.zdvgjr.cn/Article/3096.shtml
- http://wap.read.aovdbk.cn/Article/47226.shtml
- http://wap.read.aovdbk.cn/Article/46674.shtml
- http://wap.read.aovdbk.cn/Article/9812962.shtml
- http://wap.read.zdvgjr.cn/Article/3175280.shtml
- http://wap.read.zdvgjr.cn/Article/102781.shtml
- http://wap.read.zdvgjr.cn/Article/636066.shtml
- http://wap.read.zdvgjr.cn/Article/025680.shtml
- http://wap.read.zdvgjr.cn/Article/484901.shtml
- http://wap.read.aovdbk.cn/Article/5469170.shtml
- http://wap.read.aovdbk.cn/Article/89681.shtml
- http://wap.read.zdvgjr.cn/Article/1137.shtml
- http://wap.read.aovdbk.cn/Article/9984187.shtml
- http://wap.read.aovdbk.cn/Article/084914.shtml
- http://wap.read.aovdbk.cn/Article/87358.shtml
- http://wap.read.aovdbk.cn/Article/3328.shtml
- http://wap.read.aovdbk.cn/Article/8410734.shtml
- http://wap.read.aovdbk.cn/Article/042454.shtml
- http://wap.read.zdvgjr.cn/Article/1736.shtml
- http://wap.read.zdvgjr.cn/Article/5650.shtml
- http://wap.read.zdvgjr.cn/Article/885822.shtml
- http://wap.read.zdvgjr.cn/Article/82542.shtml
- http://wap.read.zdvgjr.cn/Article/73693.shtml
- http://wap.read.aovdbk.cn/Article/2027.shtml
- http://wap.read.zdvgjr.cn/Article/9610942.shtml
- http://wap.read.aovdbk.cn/Article/5734.shtml

## 项目结构

```
aggregate-catalog/
├── .cache/                          # 构建工具缓存目录，自动生成，勿手动修改
├── dist/                            # 生产环境静态输出目录，可部署至任意 Web 服务器
│   ├── index.html                   # 资源索引首页，展示当前批次所有链接
│   ├── batch-41.json                # 第 41 批次结构化数据，供前端 JavaScript 读取
│   └── assets/                      # CSS 与 JavaScript 静态资源
│       ├── main.css                 # 响应式布局样式表
│       └── app.js                   # 索引页交互逻辑（排序、复制、域名过滤）
├── docs/                            # 项目文档目录
│   ├── user-guide.md                # 用户手册：导入、配置、导出流程
│   ├── operations.md                # 运营指南：链接巡检与批次报告生成
│   ├── developer.md                 # 开发者文档：构建流程与扩展接口
│   └── design-decisions.md          # 设计决策记录：URL 策略与去重方案
├── scripts/                         # 构建与运维脚本
│   ├── build.js                     # 核心构建脚本，读取资源清单并生成 dist 目录
│   ├── validate-urls.js             # URL 格式校验脚本，检查是否包含非法字符
│   └── health-check.js              # 外链存活检测脚本（需用户配置定时任务）
├── src/                             # 源代码目录
│   ├── templates/                   # HTML 模板文件
│   │   ├── index.ejs                # 首页模板，支持动态渲染链接列表
│   │   └── partials/                # 可复用的模板片段
│   │       ├── header.ejs           # 页面头部区域
│   │       └── footer.ejs           # 页面底部信息
│   ├── styles/                      # 样式源文件（Sass 格式）
│   │   ├── base.scss                # 全局变量与重置样式
│   │   └── layout.scss              # 栅格系统与响应式断点
│   └── scripts/                     # 前端交互源代码
│       ├── index.js                 # 入口脚本，初始化应用
│       └── filters.js               # 域名过滤与排序逻辑
├── data/                            # 数据目录，存放所有批次资源清单
│   ├── batch-41.json                # 第 41 批次原始数据（本批次共 150 个链接）
│   └── manifest.json                # 批次索引清单，记录所有批次编号与说明
├── tests/                           # 单元测试与集成测试目录
│   ├── url-format.test.js           # URL 格式保留策略的测试用例
│   └── build.test.js                # 构建流程输出完整性测试
├── .gitignore                       # Git 版本管理忽略文件配置
├── package.json                     # npm 项目配置文件，定义依赖与脚本命令
├── package-lock.json                # 依赖锁定文件，确保构建环境一致性
├── README.md                        # 项目主文档（即当前文档）
└── LICENSE                          # MIT 许可证文件
```

## 贡献指南

第一，Fork 本仓库至个人账户，并在本地克隆 Fork 后的副本。创建新的功能分支，分支命名建议使用 feature/ 或 fix/ 前缀，后接简短描述，例如 feature/batch-42-import 或 fix/url-validate-regex。

第二，在 data/ 目录下新增批次 JSON 文件，严格按照 batch-41.json 的结构组织数据。确保每个链接对象的 url 字段值为原始未修改字符串，title 字段为人工阅读标题，source 字段标注来源域名。新增或修改任何链接后，须在项目根目录执行 npm run validate 以通过格式校验。

第三，若对核心构建逻辑、模板渲染方式或前端交互行为进行修改，需同步更新 docs/developer.md 文档，并在 tests/ 目录下补充相应的单元测试用例。所有测试用例须在提交前通过 npm test 命令确认。

第四，提交代码前请执行 npm run lint 进行代码风格检查，修复所有警告与错误。提交信息格式遵循 Conventional Commits 规范，使用 feat:、fix:、docs:、chore: 等类型前缀，正文描述变更原因与影响范围。

第五，向本仓库主分支发起 Pull Request，在 PR 描述中清晰列出变更清单、测试覆盖情况以及是否涉及破坏性改动。项目维护者将在 48 小时内进行 Code Review，并通过自动化构建检查后方可合并。

## 常见问题

**问：为什么必须严格保留原始 URL，甚至不能补全 http:// 前缀？**

答：本项目定位为链接收录与索引系统，而非链接修正工具。原始 URL 的文本形态可能隐含特定的访问协议偏好、端口信息或路径大小写敏感细节，任何人为改写都可能导致目标服务器返回 404 或重定向循环。此外，某些内部系统或旧版 API 仅接受特定格式的请求头，补全协议会改变请求行为。因此，项目设计上完全信任用户输入的原始值，仅做容器化展示，不执行任何智能修复。

**问：如何导入第 42 批或后续批次的链接？**

答：在 data/ 目录下复制 batch-41.json 文件并重命名为 batch-42.json，然后清空其中的 links 数组，按相同结构填入新链接。注意每批次文件中的 id 字段必须从 1 开始连续递增，且不可与历史批次 id 重复。修改完成后，在 manifest.json 中注册新批次信息，包含批次编号、导入日期、链接总数与简短描述。最后执行 npm run build 重新生成 dist 目录，即可在前端页面通过批次切换下拉菜单访问新批次。

**问：部署到生产环境后，链接列表不显示任何内容，可能的原因是什么？**

答：此问题通常由以下几种情况导致：第一，dist/ 目录下缺少对应的批次 JSON 文件，请确认构建过程完整执行且无报错；第二，Web 服务器未正确配置 MIME 类型，导致 .json 文件被当作 text/plain 返回，前端 fetch 请求解析失败，请确认服务器对 .json 文件返回 application/json 内容类型；第三，若部署在子目录路径下，前端 JavaScript 中请求 JSON 文件的相对路径可能错误，需在 src/scripts/index.js 中调整 baseUrl 配置项，或使用绝对路径访问资源。

> 外链数量: 150 | 生成时间: 2026-07-10 00:06:11
