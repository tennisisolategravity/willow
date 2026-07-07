# WebIndex 移动端资源聚合索引

WebIndex 是一个面向移动端技术内容聚合与索引的开源项目，旨在系统化地收集、整理和归档分布在各类移动子域名下的技术文章、教程和开发文档。本项目定位于技术资源的外链汇总站，目标用户包括技术文档撰写者、开发者社区运营人员以及需要批量获取技术参考资料的研究人员。通过结构化索引，WebIndex 帮助用户从分散的移动端内容源中快速定位有效信息，避免重复爬取和手工整理的低效工作。

## 功能概览

**多源内容聚合**：支持从多个移动端子域名站点并行抓取文章元数据，覆盖技术教程、开发笔记和案例分析等类型。

**批量链接管理**：提供链接去重、状态检测和分类标注能力，方便维护大规模外链资源池。

**结构化索引输出**：将所有收录链接按站点来源、文章编号和更新时间生成可读性强的索引表格。

**快速检索过滤**：内置基于关键词和来源域名的过滤查询接口，支持命令行与 HTTP API 两种方式。

**增量更新机制**：支持定时扫描新增文章，仅处理上次索引之后发布的内容，减少冗余操作。

**导出与集成**：索引结果可导出为 JSON、CSV 或 Markdown 格式，便于集成到静态站点生成器或文档系统中。

**健康检查模块**：对外链资源进行周期性访问可达性检测，自动标记失效链接并生成报告。

**权限分级管理**：支持多用户角色划分，不同操作者拥有查看、编辑或审核索引条目的不同权限。

## 应用场景

**技术文档站点的外链补充**：团队在维护技术博客或文档站时，可使用 WebIndex 批量引入相关外部参考链接，丰富文章引用来源，无需手动检索多个移动站点。

**开发者每日阅读清单生成**：开发者可通过配置 WebIndex 的过滤规则，每日自动生成一份来自指定移动来源的技术文章列表，用于个人学习或团队晨会分享。

**技术社区内容运营**：社区运营人员可以利用 WebIndex 的聚合能力，快速发现多个移动子域名下的热门技术话题，作为社区话题策划的数据参考。

**学术研究数据采集**：研究人员在进行技术趋势分析或文献计量研究时，可通过 WebIndex 建立稳定的移动端技术文章样本集，支撑长期追踪和统计。

## 快速开始

以下步骤帮助您在本地环境快速启动 WebIndex 服务。

```bash
# 克隆代码仓库
git clone https://github.com/webindex/webindex.git
cd webindex

# 安装项目依赖（使用 pip 安装 Python 依赖）
pip install -r requirements.txt

# 初始化本地索引数据库（SQLite）
python scripts/init_db.py

# 启动索引服务（默认监听 127.0.0.1:8080）
python server.py
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，用于服务端和脚本执行 |
| SQLite | 3.35 及以上 | 内置索引存储数据库，无需额外安装 |
| requests | 2.28.0 及以上 | 处理 HTTP 请求与内容获取 |
| beautifulsoup4 | 4.11.0 及以上 | 解析 HTML 文章内容提取元数据 |
| lxml | 4.9.0 及以上 | 作为 BeautifulSoup 的解析器后端 |
| pytest | 7.2.0 及以上 | 单元测试和集成测试框架（仅开发需要） |
| flask | 2.2.0 及以上 | 提供可选的 HTTP API 服务（非必需，仅当启用 API 时） |
| croniter | 1.3.0 及以上 | 用于定时调度增量更新任务（非必需） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户入门 | docs/getting-started.md | 如何安装、配置并首次运行索引服务 |
| 配置参考 | docs/configuration.md | 所有环境变量和配置文件项的含义与默认值 |
| API 手册 | docs/api-reference.md | HTTP 接口的请求路径、参数和返回格式说明 |
| 运维指南 | docs/operations.md | 日志管理、性能调优和故障排查方法 |
| 开发指引 | docs/development.md | 二次开发的代码结构、编码规范和提交流程 |
| 数据格式 | docs/data-format.md | 索引条目各字段的定义、类型和取值范围 |

## 资源列表

- http://m.mobile.hcbezg.cn/Article/397632.shtml
- http://m.mobile.cvsifc.cn/Article/5574172.shtml
- http://m.mobile.cvsifc.cn/Article/1862.shtml
- http://m.mobile.cvsifc.cn/Article/069021.shtml
- http://m.mobile.fuvxie.cn/Article/15587.shtml
- http://m.mobile.cvsifc.cn/Article/002716.shtml
- http://m.mobile.hcbezg.cn/Article/542631.shtml
- http://m.mobile.hcbezg.cn/Article/808134.shtml
- http://m.mobile.fuvxie.cn/Article/027831.shtml
- http://m.mobile.cvsifc.cn/Article/1277370.shtml
- http://m.mobile.fuvxie.cn/Article/6299.shtml
- http://m.mobile.cvsifc.cn/Article/617721.shtml
- http://m.mobile.hcbezg.cn/Article/6404.shtml
- http://m.mobile.cvsifc.cn/Article/52736.shtml
- http://m.mobile.hcbezg.cn/Article/7505.shtml
- http://m.mobile.fuvxie.cn/Article/7659.shtml
- http://m.mobile.fuvxie.cn/Article/6126.shtml
- http://m.mobile.cvsifc.cn/Article/6384.shtml
- http://m.mobile.cvsifc.cn/Article/8191488.shtml
- http://m.mobile.fuvxie.cn/Article/3448.shtml
- http://m.mobile.hcbezg.cn/Article/911483.shtml
- http://m.mobile.hcbezg.cn/Article/1133.shtml
- http://m.mobile.fuvxie.cn/Article/471889.shtml
- http://m.mobile.cvsifc.cn/Article/210261.shtml
- http://m.mobile.hcbezg.cn/Article/177630.shtml
- http://m.mobile.hcbezg.cn/Article/8071.shtml
- http://m.mobile.fuvxie.cn/Article/684321.shtml
- http://m.mobile.fuvxie.cn/Article/303014.shtml
- http://m.mobile.cvsifc.cn/Article/0601137.shtml
- http://m.mobile.cvsifc.cn/Article/7266588.shtml
- http://m.mobile.cvsifc.cn/Article/4656712.shtml
- http://m.mobile.fuvxie.cn/Article/8982.shtml
- http://m.mobile.fuvxie.cn/Article/643097.shtml
- http://m.mobile.cvsifc.cn/Article/0957474.shtml
- http://m.mobile.hcbezg.cn/Article/39094.shtml
- http://m.mobile.fuvxie.cn/Article/542285.shtml
- http://m.mobile.hcbezg.cn/Article/5912039.shtml
- http://m.mobile.hcbezg.cn/Article/4773.shtml
- http://m.mobile.fuvxie.cn/Article/288166.shtml
- http://m.mobile.cvsifc.cn/Article/60361.shtml
- http://m.mobile.hcbezg.cn/Article/82829.shtml
- http://m.mobile.hcbezg.cn/Article/0672.shtml
- http://m.mobile.cvsifc.cn/Article/816150.shtml
- http://m.mobile.cvsifc.cn/Article/9166.shtml
- http://m.mobile.hcbezg.cn/Article/16699.shtml
- http://m.mobile.hcbezg.cn/Article/8699.shtml
- http://m.mobile.cvsifc.cn/Article/1437595.shtml
- http://m.mobile.cvsifc.cn/Article/7782.shtml
- http://m.mobile.cvsifc.cn/Article/263152.shtml
- http://m.mobile.cvsifc.cn/Article/0667.shtml
- http://m.mobile.fuvxie.cn/Article/461516.shtml
- http://m.mobile.cvsifc.cn/Article/05937.shtml
- http://m.mobile.fuvxie.cn/Article/9908235.shtml
- http://m.mobile.hcbezg.cn/Article/53800.shtml
- http://m.mobile.hcbezg.cn/Article/91474.shtml
- http://m.mobile.cvsifc.cn/Article/83972.shtml
- http://m.mobile.cvsifc.cn/Article/8947417.shtml
- http://m.mobile.fuvxie.cn/Article/9702482.shtml
- http://m.mobile.cvsifc.cn/Article/8509.shtml
- http://m.mobile.fuvxie.cn/Article/0454.shtml
- http://m.mobile.cvsifc.cn/Article/5013.shtml
- http://m.mobile.cvsifc.cn/Article/29427.shtml
- http://m.mobile.fuvxie.cn/Article/8946.shtml
- http://m.mobile.fuvxie.cn/Article/33673.shtml
- http://m.mobile.hcbezg.cn/Article/4291232.shtml
- http://m.mobile.fuvxie.cn/Article/132265.shtml
- http://m.mobile.fuvxie.cn/Article/9621.shtml
- http://m.mobile.hcbezg.cn/Article/960785.shtml
- http://m.mobile.hcbezg.cn/Article/679924.shtml
- http://m.mobile.fuvxie.cn/Article/10408.shtml
- http://m.mobile.fuvxie.cn/Article/474654.shtml
- http://m.mobile.fuvxie.cn/Article/7837.shtml
- http://m.mobile.fuvxie.cn/Article/5235144.shtml
- http://m.mobile.hcbezg.cn/Article/84713.shtml
- http://m.mobile.hcbezg.cn/Article/176384.shtml
- http://m.mobile.hcbezg.cn/Article/14851.shtml
- http://m.mobile.hcbezg.cn/Article/9832.shtml
- http://m.mobile.cvsifc.cn/Article/3783.shtml
- http://m.mobile.hcbezg.cn/Article/9136.shtml
- http://m.mobile.fuvxie.cn/Article/105590.shtml
- http://m.mobile.cvsifc.cn/Article/861125.shtml
- http://m.mobile.cvsifc.cn/Article/6468.shtml
- http://m.mobile.fuvxie.cn/Article/9735531.shtml
- http://m.mobile.cvsifc.cn/Article/94870.shtml
- http://m.mobile.hcbezg.cn/Article/22017.shtml
- http://m.mobile.cvsifc.cn/Article/06789.shtml
- http://m.mobile.cvsifc.cn/Article/098568.shtml
- http://m.mobile.cvsifc.cn/Article/251230.shtml
- http://m.mobile.cvsifc.cn/Article/44166.shtml
- http://m.mobile.fuvxie.cn/Article/261512.shtml
- http://m.mobile.cvsifc.cn/Article/83362.shtml
- http://m.mobile.cvsifc.cn/Article/1420618.shtml
- http://m.mobile.fuvxie.cn/Article/412198.shtml
- http://m.mobile.fuvxie.cn/Article/62453.shtml
- http://m.mobile.hcbezg.cn/Article/7871354.shtml
- http://m.mobile.cvsifc.cn/Article/0361112.shtml
- http://m.mobile.cvsifc.cn/Article/0939.shtml
- http://m.mobile.hcbezg.cn/Article/2004942.shtml
- http://m.mobile.cvsifc.cn/Article/9946639.shtml
- http://m.mobile.cvsifc.cn/Article/62430.shtml
- http://m.mobile.hcbezg.cn/Article/0971093.shtml
- http://m.mobile.cvsifc.cn/Article/41776.shtml
- http://m.mobile.hcbezg.cn/Article/1235.shtml
- http://m.mobile.hcbezg.cn/Article/4509.shtml
- http://m.mobile.fuvxie.cn/Article/7287495.shtml
- http://m.mobile.cvsifc.cn/Article/6964966.shtml
- http://m.mobile.fuvxie.cn/Article/58488.shtml
- http://m.mobile.fuvxie.cn/Article/6817210.shtml
- http://m.mobile.cvsifc.cn/Article/76490.shtml
- http://m.mobile.hcbezg.cn/Article/74677.shtml
- http://m.mobile.fuvxie.cn/Article/2732.shtml
- http://m.mobile.hcbezg.cn/Article/92019.shtml
- http://m.mobile.cvsifc.cn/Article/0180.shtml
- http://m.mobile.fuvxie.cn/Article/368634.shtml
- http://m.mobile.fuvxie.cn/Article/05714.shtml
- http://m.mobile.fuvxie.cn/Article/825542.shtml
- http://m.mobile.fuvxie.cn/Article/1373.shtml
- http://m.mobile.fuvxie.cn/Article/1167.shtml
- http://m.mobile.cvsifc.cn/Article/977876.shtml
- http://m.mobile.cvsifc.cn/Article/7816.shtml
- http://m.mobile.cvsifc.cn/Article/8831633.shtml
- http://m.mobile.hcbezg.cn/Article/17925.shtml
- http://m.mobile.fuvxie.cn/Article/198762.shtml
- http://m.mobile.fuvxie.cn/Article/8744447.shtml
- http://m.mobile.hcbezg.cn/Article/997415.shtml
- http://m.mobile.cvsifc.cn/Article/943982.shtml
- http://m.mobile.fuvxie.cn/Article/21444.shtml
- http://m.mobile.hcbezg.cn/Article/728966.shtml
- http://m.mobile.cvsifc.cn/Article/6311.shtml
- http://m.mobile.cvsifc.cn/Article/38495.shtml
- http://m.mobile.cvsifc.cn/Article/5732.shtml
- http://m.mobile.fuvxie.cn/Article/7983.shtml
- http://m.mobile.hcbezg.cn/Article/82002.shtml
- http://m.mobile.cvsifc.cn/Article/25212.shtml
- http://m.mobile.hcbezg.cn/Article/25277.shtml
- http://m.mobile.fuvxie.cn/Article/623399.shtml
- http://m.mobile.cvsifc.cn/Article/272460.shtml
- http://m.mobile.cvsifc.cn/Article/7236392.shtml
- http://m.mobile.hcbezg.cn/Article/867569.shtml
- http://m.mobile.cvsifc.cn/Article/078860.shtml
- http://m.mobile.hcbezg.cn/Article/654235.shtml
- http://m.mobile.fuvxie.cn/Article/024121.shtml
- http://m.mobile.fuvxie.cn/Article/31789.shtml
- http://m.mobile.fuvxie.cn/Article/9485834.shtml
- http://m.mobile.hcbezg.cn/Article/1015181.shtml
- http://m.mobile.cvsifc.cn/Article/3721171.shtml
- http://m.mobile.hcbezg.cn/Article/9148.shtml
- http://m.mobile.hcbezg.cn/Article/82308.shtml
- http://m.mobile.cvsifc.cn/Article/6587010.shtml
- http://m.mobile.cvsifc.cn/Article/79098.shtml
- http://m.mobile.fuvxie.cn/Article/61206.shtml
- http://m.mobile.cvsifc.cn/Article/6744.shtml
- http://m.mobile.cvsifc.cn/Article/3010974.shtml
- http://m.mobile.fuvxie.cn/Article/53968.shtml
- http://m.mobile.cvsifc.cn/Article/835066.shtml
- http://m.mobile.hcbezg.cn/Article/1829707.shtml
- http://m.mobile.cvsifc.cn/Article/22937.shtml
- http://m.mobile.fuvxie.cn/Article/7331.shtml
- http://m.mobile.fuvxie.cn/Article/90704.shtml
- http://m.mobile.cvsifc.cn/Article/5607.shtml
- http://m.mobile.fuvxie.cn/Article/97835.shtml
- http://m.mobile.fuvxie.cn/Article/1033757.shtml
- http://m.mobile.cvsifc.cn/Article/4168.shtml
- http://m.mobile.hcbezg.cn/Article/9615567.shtml
- http://m.mobile.fuvxie.cn/Article/3118338.shtml
- http://m.mobile.fuvxie.cn/Article/519486.shtml
- http://m.mobile.hcbezg.cn/Article/2178939.shtml
- http://m.mobile.fuvxie.cn/Article/6304567.shtml
- http://m.mobile.cvsifc.cn/Article/3591025.shtml
- http://m.mobile.hcbezg.cn/Article/12769.shtml
- http://m.mobile.cvsifc.cn/Article/2997387.shtml
- http://m.mobile.cvsifc.cn/Article/683346.shtml
- http://m.mobile.hcbezg.cn/Article/821657.shtml
- http://m.mobile.cvsifc.cn/Article/218640.shtml
- http://m.mobile.hcbezg.cn/Article/3190.shtml
- http://m.mobile.hcbezg.cn/Article/010414.shtml
- http://m.mobile.fuvxie.cn/Article/1153028.shtml
- http://m.mobile.cvsifc.cn/Article/28480.shtml
- http://m.mobile.hcbezg.cn/Article/2296040.shtml
- http://m.mobile.cvsifc.cn/Article/6625034.shtml
- http://m.mobile.hcbezg.cn/Article/798627.shtml
- http://m.mobile.fuvxie.cn/Article/3889.shtml
- http://m.mobile.hcbezg.cn/Article/080678.shtml
- http://m.mobile.hcbezg.cn/Article/7059.shtml
- http://m.mobile.hcbezg.cn/Article/3102953.shtml
- http://m.mobile.hcbezg.cn/Article/999325.shtml
- http://m.mobile.fuvxie.cn/Article/897944.shtml
- http://m.mobile.fuvxie.cn/Article/313787.shtml
- http://m.mobile.fuvxie.cn/Article/845359.shtml
- http://m.mobile.fuvxie.cn/Article/312251.shtml
- http://m.mobile.fuvxie.cn/Article/73744.shtml
- http://m.mobile.hcbezg.cn/Article/4067.shtml
- http://m.mobile.fuvxie.cn/Article/1684.shtml
- http://m.mobile.fuvxie.cn/Article/5940.shtml
- http://m.mobile.hcbezg.cn/Article/8641.shtml
- http://m.mobile.cvsifc.cn/Article/8360429.shtml
- http://m.mobile.cvsifc.cn/Article/91700.shtml
- http://m.mobile.fuvxie.cn/Article/284542.shtml
- http://m.mobile.hcbezg.cn/Article/9718.shtml
- http://m.mobile.hcbezg.cn/Article/305306.shtml
- http://m.mobile.fuvxie.cn/Article/0225.shtml
- http://m.mobile.hcbezg.cn/Article/53012.shtml
- http://m.mobile.hcbezg.cn/Article/1463.shtml
- http://m.mobile.fuvxie.cn/Article/18186.shtml
- http://m.mobile.hcbezg.cn/Article/1671736.shtml
- http://m.mobile.fuvxie.cn/Article/07983.shtml
- http://m.mobile.hcbezg.cn/Article/5663679.shtml
- http://m.mobile.fuvxie.cn/Article/1686.shtml
- http://m.mobile.cvsifc.cn/Article/241345.shtml
- http://m.mobile.fuvxie.cn/Article/82744.shtml
- http://m.mobile.fuvxie.cn/Article/5286.shtml
- http://m.mobile.fuvxie.cn/Article/162532.shtml
- http://m.mobile.cvsifc.cn/Article/905311.shtml
- http://m.mobile.fuvxie.cn/Article/6772415.shtml
- http://m.mobile.hcbezg.cn/Article/230058.shtml
- http://m.mobile.hcbezg.cn/Article/5123741.shtml
- http://m.mobile.fuvxie.cn/Article/51452.shtml
- http://m.mobile.fuvxie.cn/Article/505019.shtml
- http://m.mobile.fuvxie.cn/Article/582291.shtml
- http://m.mobile.hcbezg.cn/Article/5189098.shtml
- http://m.mobile.hcbezg.cn/Article/60244.shtml
- http://m.mobile.cvsifc.cn/Article/011909.shtml
- http://m.mobile.fuvxie.cn/Article/9920.shtml
- http://m.mobile.hcbezg.cn/Article/78252.shtml
- http://m.mobile.cvsifc.cn/Article/02777.shtml
- http://m.mobile.cvsifc.cn/Article/7681.shtml
- http://m.mobile.cvsifc.cn/Article/494791.shtml
- http://m.mobile.cvsifc.cn/Article/1388.shtml
- http://m.mobile.fuvxie.cn/Article/704216.shtml
- http://m.mobile.fuvxie.cn/Article/049377.shtml
- http://m.mobile.fuvxie.cn/Article/5504746.shtml
- http://m.mobile.fuvxie.cn/Article/114958.shtml
- http://m.mobile.fuvxie.cn/Article/1007119.shtml
- http://m.mobile.cvsifc.cn/Article/14583.shtml
- http://m.mobile.hcbezg.cn/Article/695082.shtml
- http://m.mobile.hcbezg.cn/Article/240838.shtml
- http://m.mobile.cvsifc.cn/Article/306303.shtml
- http://m.mobile.hcbezg.cn/Article/8698.shtml
- http://m.mobile.hcbezg.cn/Article/9694.shtml
- http://m.mobile.fuvxie.cn/Article/9581365.shtml
- http://m.mobile.hcbezg.cn/Article/45001.shtml
- http://m.mobile.hcbezg.cn/Article/2479836.shtml
- http://m.mobile.cvsifc.cn/Article/3800.shtml
- http://m.mobile.hcbezg.cn/Article/1877219.shtml
- http://m.mobile.fuvxie.cn/Article/94134.shtml
- http://m.mobile.cvsifc.cn/Article/88475.shtml
- http://m.mobile.fuvxie.cn/Article/5543118.shtml
- http://m.mobile.hcbezg.cn/Article/0155.shtml
- http://m.mobile.cvsifc.cn/Article/6712.shtml
- http://m.mobile.hcbezg.cn/Article/6753720.shtml

## 项目结构

```
webindex/
├── src/                                 # 核心源代码目录
│   ├── core/                            # 核心引擎模块
│   │   ├── crawler.py                   # 多源抓取调度器，管理并发请求和超时重试
│   │   ├── parser.py                    # 文章元数据解析器，基于 BeautifulSoup 实现
│   │   └── indexer.py                   # 索引写入和更新逻辑，与 SQLite 交互
│   ├── api/                             # HTTP API 服务模块
│   │   ├── routes.py                    # Flask 路由定义，包含查询、导出和状态接口
│   │   └── middleware.py                # 请求日志、跨域和鉴权中间件
│   ├── scripts/                         # 辅助运维脚本
│   │   ├── init_db.py                   # 初始化数据库表结构和默认配置
│   │   ├── incremental_update.py        # 增量更新触发器，配合 cron 使用
│   │   └── health_check.py              # 外链健康检测脚本，输出失效链接报告
│   └── utils/                           # 通用工具函数
│       ├── logger.py                    # 日志配置和格式化输出
│       ├── validators.py                # URL 合法性校验和域名白名单过滤
│       └── exporters.py                 # 索引结果导出为 JSON / CSV / Markdown
├── tests/                               # 测试套件
│   ├── unit/                            # 单元测试，覆盖解析器和索引器核心逻辑
│   └── integration/                     # 集成测试，模拟实际抓取和 API 调用
├── docs/                                # 项目文档（详见文档导航章节）
├── config/                              # 配置文件目录
│   ├── default.yaml                     # 默认配置，包含超时时间、并发数和重试策略
│   └── production.yaml                  # 生产环境覆盖配置，含日志级别和 API 密钥
├── data/                                # 数据存储目录
│   ├── index.db                         # SQLite 索引数据库文件
│   └── logs/                            # 运行日志文件按日期滚动存放
├── requirements.txt                     # Python 依赖清单（固定版本）
├── server.py                            # 服务启动入口，加载配置并启动 API 服务
├── LICENSE                              # MIT 许可证文件
└── README.md                            # 本文件
```

## 贡献指南

1. **问题反馈与功能建议**：请先查阅现有 Issues 列表，确认无人提交相同议题后，新建 Issue 并详细描述使用场景、预期行为和当前表现，附带必要的环境信息。

2. **代码贡献流程**：Fork 本仓库到个人账户，在 dev 分支基础上新建功能分支，完成代码修改并补充对应的单元测试，确保所有测试用例通过后方可发起 Pull Request。

3. **文档改进**：欢迎对 README、配置说明和 API 手册进行修正或翻译。文档修改需保持 Markdown 格式规范，并确保术语与代码实现一致。

4. **链接资源补充**：如果您有稳定的移动端技术文章源，可按项目规定的数据格式提交索引建议，经过审核后合并到资源池中。提交前请确认链接可访问且内容与开发技术相关。

5. **代码风格与规范**：提交的 Python 代码需遵循 PEP 8 风格指南，使用 black 和 isort 进行格式化，变量命名应具有自描述性，关键逻辑处添加清晰注释。

## 常见问题

**Q：项目启动后无法抓取任何链接，返回超时错误，如何排查？**

A：首先检查网络环境是否能够访问外网，以及目标域名是否被防火墙拦截。然后查看 config/default.yaml 中的 timeout 和 max_retries 参数，适当增加超时时间（例如从 10 秒调整到 30 秒）。如果问题持续，使用 scripts/health_check.py 单独测试目标链接的可达性，确认是否为临时性服务不可用。

**Q：索引数据库文件 data/index.db 体积增长过快，如何清理历史数据？**

A：项目内置了数据保留策略，您可以在配置文件中设置 retention_days 参数，默认保留 90 天内的索引记录。如需手动清理，可使用 SQLite 命令行执行 VACUUM 命令回收空间，或运行 scripts/archive_old_records.py 进行归档迁移。

**Q：如何将索引结果集成到我自己的静态站点中？**

A：您可以使用导出功能将索引结果输出为 Markdown 表格或 JSON 格式。推荐使用 API 接口 `/api/export?format=markdown` 直接获取格式化文本，然后通过脚本或 CI 流水线将其嵌入到您的站点仓库中。若需要定时同步，可配置 cron 任务定期调用导出接口并提交变更。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
