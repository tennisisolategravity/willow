# LinkVault 外链资源聚合系统

LinkVault 是一个面向技术内容创作者、开发者文档维护者以及开源项目运营者的外链资源批量管理与合规性校验平台。该项目旨在解决大规模外链资源收录过程中的格式一致性检查、来源追溯、状态监控与批量导出问题。目标用户包括技术博客运营团队、开源社区文档管理员以及需要维护大量参考链接的科研或工程团队。LinkVault 通过结构化解析 URL 组件、自动识别协议与域名变体、生成符合严格格式要求的资源清单，显著降低人工整理外链列表时的遗漏率与格式错误率。

## 功能概览

批量 URL 导入与规范性校验：支持从纯文本、CSV 或 JSON 文件导入大量 URL，自动检测并标记缺失协议头、大小写不一致、结尾多余斜杠或含有多余空白字符的条目。

裸域名与带协议 URL 的区分输出引擎：根据项目配置的严格模式，对裸域名、带 http:// 前缀、带 https:// 前缀及带 www. 子域的 URL 实施差异化原样保留策略，禁止任何自动补全或协议升级行为。

资源列表格式化生成器：按照每行单条 URL、固定前缀 "- " 的列表格式输出，支持按域名、按文章编号或按导入顺序排序，并自动过滤重复条目。

项目文档脚手架生成：基于已导入的 URL 集合，自动填充 README 中的资源列表章节、生成 ASCII 目录树占位结构，并维护依赖关系表格。

URL 状态健康检查：通过异步 HTTP 请求检测每个外链的可访问性，记录响应状态码与响应时间，支持超时重试与失败标记，便于后续人工复核。

分类标签与备注系统：允许用户为每条 URL 关联自定义标签（如 "参考文档"、"API 规范"、"社区讨论"）和备注说明，并支持按标签筛选导出。

多批次分页管理：针对超过 50 条的大规模资源集合，自动拆分为多个批次文件，并维护批次序号、总数统计与当前进度，便于增量式处理第 22/60 批等场景。

## 应用场景

技术文档团队批量整理外部参考链接：当编写一份包含数百条外部引用的技术规格说明书时，团队成员使用 LinkVault 导入原始收集的 URL 列表，系统自动识别出缺少协议头的条目并提示补全，最终输出严格符合文档规范的一行一条资源列表，可直接粘贴至 Markdown 文件中。

开源项目 README 资源章节自动化生成：开源项目维护者需要定期更新 README 中的相关项目或工具链接。通过 LinkVault，维护者仅需维护一个纯文本 URL 清单，系统即按照预设的章节结构生成包含 "资源列表" 等完整内容的 README 草案，避免手动排版导致格式混乱。

外链合规性审计与迁移辅助：在网站域名迁移或协议升级（如 HTTP 转向 HTTPS）过程中，运营人员使用 LinkVault 导入所有历史外链，系统严格区分原始协议并标记出所有 http:// 开头的条目，提供清晰的待升级清单，防止迁移过程中误改第三方资源的原始地址。

## 快速开始

以下步骤帮助您在本地环境中快速启动 LinkVault 服务，并完成首批外链资源的导入与导出。

```bash
# 克隆项目仓库至本地
git clone https://github.com/your-organization/linkvault.git

# 进入项目根目录
cd linkvault

# 安装核心依赖（使用 pip 安装 Python 后端依赖）
pip install -r requirements.txt

# 初始化本地数据库与配置目录
python scripts/init_db.py

# 启动开发服务器（默认监听 127.0.0.1:5000）
python app.py
```

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Python | 3.9 或更高 | 核心后端运行环境，用于 URL 解析、状态检测与格式化输出 |
| Flask | 2.2.x | Web 服务框架，提供 RESTful API 与简易管理界面 |
| requests | 2.28.x | 用于异步外链健康检查，发送 HTTP/HTTPS 探针请求 |
| pandas | 1.5.x | 用于批量导入 CSV 与 Excel 格式的 URL 列表，进行数据帧操作 |
| PyYAML | 6.0 | 用于解析项目配置文件 config.yaml，管理严格模式与输出规则 |
| markdown | 3.4.x | 用于在导出功能中渲染 README 预览，辅助检查最终输出效果 |
| pytest | 7.2.x | 单元测试框架，用于验证 URL 解析器与格式化器的正确性（仅开发依赖） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | /docs/user_guide.md | 如何导入 URL、配置严格输出模式、执行健康检查以及导出不同格式的资源列表 |
| 运维指南 | /docs/administration.md | 如何部署生产环境、配置反向代理、设置定时健康检查任务以及备份数据库 |
| API 参考 | /docs/api_reference.md | 后端提供的批量导入接口、状态查询接口与格式化导出接口的请求与响应规范 |
| 贡献者指南 | /docs/contributing.md | 代码风格要求、提交规范、测试用例编写指南以及 PR 评审流程 |

## 资源列表

- http://map.mobile.cvsifc.cn/Article/8336.shtml
- http://map.mobile.cvsifc.cn/Article/74109.shtml
- http://map.mobile.hcbezg.cn/Article/6053.shtml
- http://map.mobile.hcbezg.cn/Article/5602.shtml
- http://map.mobile.hcbezg.cn/Article/0937.shtml
- http://map.mobile.cvsifc.cn/Article/3025723.shtml
- http://map.mobile.fuvxie.cn/Article/4582812.shtml
- http://map.mobile.cvsifc.cn/Article/067789.shtml
- http://map.mobile.hcbezg.cn/Article/1589979.shtml
- http://map.mobile.hcbezg.cn/Article/7160908.shtml
- http://map.mobile.fuvxie.cn/Article/6903.shtml
- http://map.mobile.hcbezg.cn/Article/9927.shtml
- http://map.mobile.fuvxie.cn/Article/1016359.shtml
- http://map.mobile.hcbezg.cn/Article/06335.shtml
- http://map.mobile.hcbezg.cn/Article/7426.shtml
- http://map.mobile.fuvxie.cn/Article/9386692.shtml
- http://map.mobile.hcbezg.cn/Article/429501.shtml
- http://map.mobile.hcbezg.cn/Article/1247085.shtml
- http://map.mobile.hcbezg.cn/Article/491066.shtml
- http://map.mobile.cvsifc.cn/Article/564986.shtml
- http://map.mobile.fuvxie.cn/Article/2711.shtml
- http://map.mobile.hcbezg.cn/Article/595155.shtml
- http://map.mobile.cvsifc.cn/Article/55215.shtml
- http://map.mobile.hcbezg.cn/Article/9831211.shtml
- http://map.mobile.cvsifc.cn/Article/4117.shtml
- http://map.mobile.hcbezg.cn/Article/703554.shtml
- http://map.mobile.hcbezg.cn/Article/0980792.shtml
- http://map.mobile.fuvxie.cn/Article/0367.shtml
- http://map.mobile.fuvxie.cn/Article/77795.shtml
- http://map.mobile.cvsifc.cn/Article/2326.shtml
- http://map.mobile.cvsifc.cn/Article/2236849.shtml
- http://map.mobile.fuvxie.cn/Article/44080.shtml
- http://map.mobile.hcbezg.cn/Article/5547.shtml
- http://map.mobile.hcbezg.cn/Article/579248.shtml
- http://map.mobile.hcbezg.cn/Article/6328.shtml
- http://map.mobile.cvsifc.cn/Article/383660.shtml
- http://map.mobile.cvsifc.cn/Article/4059.shtml
- http://map.mobile.hcbezg.cn/Article/2436.shtml
- http://map.mobile.fuvxie.cn/Article/09754.shtml
- http://map.mobile.hcbezg.cn/Article/7541528.shtml
- http://map.mobile.fuvxie.cn/Article/9130041.shtml
- http://map.mobile.hcbezg.cn/Article/4106.shtml
- http://map.mobile.fuvxie.cn/Article/4949299.shtml
- http://map.mobile.fuvxie.cn/Article/963899.shtml
- http://map.mobile.cvsifc.cn/Article/262392.shtml
- http://map.mobile.cvsifc.cn/Article/9226172.shtml
- http://map.mobile.hcbezg.cn/Article/6443.shtml
- http://map.mobile.cvsifc.cn/Article/8370.shtml
- http://map.mobile.hcbezg.cn/Article/0069.shtml
- http://map.mobile.fuvxie.cn/Article/01809.shtml
- http://map.mobile.fuvxie.cn/Article/024786.shtml
- http://map.mobile.hcbezg.cn/Article/74541.shtml
- http://map.mobile.cvsifc.cn/Article/813010.shtml
- http://map.mobile.fuvxie.cn/Article/3172.shtml
- http://map.mobile.hcbezg.cn/Article/11771.shtml
- http://map.mobile.fuvxie.cn/Article/2046046.shtml
- http://map.mobile.fuvxie.cn/Article/722656.shtml
- http://map.mobile.hcbezg.cn/Article/2785.shtml
- http://map.mobile.hcbezg.cn/Article/143625.shtml
- http://map.mobile.fuvxie.cn/Article/473204.shtml
- http://map.mobile.fuvxie.cn/Article/57692.shtml
- http://map.mobile.fuvxie.cn/Article/038743.shtml
- http://map.mobile.cvsifc.cn/Article/19150.shtml
- http://map.mobile.cvsifc.cn/Article/1606997.shtml
- http://map.mobile.hcbezg.cn/Article/1112.shtml
- http://map.mobile.hcbezg.cn/Article/9527766.shtml
- http://map.mobile.fuvxie.cn/Article/72600.shtml
- http://map.mobile.fuvxie.cn/Article/6335.shtml
- http://map.mobile.hcbezg.cn/Article/30529.shtml
- http://map.mobile.fuvxie.cn/Article/7409968.shtml
- http://map.mobile.hcbezg.cn/Article/41391.shtml
- http://map.mobile.hcbezg.cn/Article/8241.shtml
- http://map.mobile.hcbezg.cn/Article/9705.shtml
- http://map.mobile.cvsifc.cn/Article/7403.shtml
- http://map.mobile.hcbezg.cn/Article/8151.shtml
- http://map.mobile.cvsifc.cn/Article/786136.shtml
- http://map.mobile.fuvxie.cn/Article/0485.shtml
- http://map.mobile.fuvxie.cn/Article/700970.shtml
- http://map.mobile.hcbezg.cn/Article/194676.shtml
- http://map.mobile.hcbezg.cn/Article/7337.shtml
- http://map.mobile.fuvxie.cn/Article/6689.shtml
- http://map.mobile.fuvxie.cn/Article/288852.shtml
- http://map.mobile.cvsifc.cn/Article/9375134.shtml
- http://map.mobile.cvsifc.cn/Article/1025182.shtml
- http://map.mobile.fuvxie.cn/Article/9470334.shtml
- http://map.mobile.hcbezg.cn/Article/28088.shtml
- http://map.mobile.hcbezg.cn/Article/8280.shtml
- http://map.mobile.hcbezg.cn/Article/474337.shtml
- http://map.mobile.fuvxie.cn/Article/5489.shtml
- http://map.mobile.cvsifc.cn/Article/00985.shtml
- http://map.mobile.hcbezg.cn/Article/4576.shtml
- http://map.mobile.fuvxie.cn/Article/6490325.shtml
- http://map.mobile.hcbezg.cn/Article/6724.shtml
- http://map.mobile.fuvxie.cn/Article/4626134.shtml
- http://map.mobile.hcbezg.cn/Article/9452.shtml
- http://map.mobile.fuvxie.cn/Article/5403890.shtml
- http://map.mobile.cvsifc.cn/Article/468952.shtml
- http://map.mobile.fuvxie.cn/Article/6583.shtml
- http://map.mobile.hcbezg.cn/Article/29817.shtml
- http://map.mobile.cvsifc.cn/Article/5525755.shtml
- http://map.mobile.cvsifc.cn/Article/4404605.shtml
- http://map.mobile.fuvxie.cn/Article/2598.shtml
- http://map.mobile.hcbezg.cn/Article/9097795.shtml
- http://map.mobile.cvsifc.cn/Article/6067.shtml
- http://map.mobile.fuvxie.cn/Article/3690042.shtml
- http://map.mobile.fuvxie.cn/Article/33953.shtml
- http://map.mobile.cvsifc.cn/Article/1892.shtml
- http://map.mobile.cvsifc.cn/Article/537349.shtml
- http://map.mobile.fuvxie.cn/Article/40821.shtml
- http://map.mobile.fuvxie.cn/Article/88575.shtml
- http://map.mobile.cvsifc.cn/Article/207569.shtml
- http://map.mobile.hcbezg.cn/Article/1331056.shtml
- http://map.mobile.fuvxie.cn/Article/5618.shtml
- http://map.mobile.cvsifc.cn/Article/0838933.shtml
- http://map.mobile.cvsifc.cn/Article/6293939.shtml
- http://map.mobile.cvsifc.cn/Article/7639.shtml
- http://map.mobile.hcbezg.cn/Article/06179.shtml
- http://map.mobile.cvsifc.cn/Article/4673.shtml
- http://map.mobile.fuvxie.cn/Article/918698.shtml
- http://map.mobile.hcbezg.cn/Article/5339.shtml
- http://map.mobile.hcbezg.cn/Article/52262.shtml
- http://map.mobile.hcbezg.cn/Article/7041.shtml
- http://map.mobile.cvsifc.cn/Article/22713.shtml
- http://map.mobile.fuvxie.cn/Article/701214.shtml
- http://map.mobile.cvsifc.cn/Article/6566045.shtml
- http://map.mobile.hcbezg.cn/Article/71555.shtml
- http://map.mobile.fuvxie.cn/Article/579070.shtml
- http://map.mobile.cvsifc.cn/Article/5478.shtml
- http://map.mobile.fuvxie.cn/Article/96358.shtml
- http://map.mobile.fuvxie.cn/Article/06934.shtml
- http://map.mobile.hcbezg.cn/Article/785976.shtml
- http://map.mobile.cvsifc.cn/Article/210274.shtml
- http://map.mobile.hcbezg.cn/Article/9820544.shtml
- http://map.mobile.hcbezg.cn/Article/620298.shtml
- http://map.mobile.fuvxie.cn/Article/051020.shtml
- http://map.mobile.hcbezg.cn/Article/958768.shtml
- http://map.mobile.cvsifc.cn/Article/8387669.shtml
- http://map.mobile.fuvxie.cn/Article/4917.shtml
- http://map.mobile.cvsifc.cn/Article/943752.shtml
- http://map.mobile.hcbezg.cn/Article/46415.shtml
- http://map.mobile.hcbezg.cn/Article/0146718.shtml
- http://map.mobile.fuvxie.cn/Article/85554.shtml
- http://map.mobile.fuvxie.cn/Article/9541025.shtml
- http://map.mobile.fuvxie.cn/Article/817549.shtml
- http://map.mobile.cvsifc.cn/Article/97395.shtml
- http://map.mobile.fuvxie.cn/Article/039460.shtml
- http://map.mobile.cvsifc.cn/Article/268382.shtml
- http://map.mobile.hcbezg.cn/Article/7772185.shtml
- http://map.mobile.fuvxie.cn/Article/187477.shtml
- http://map.mobile.cvsifc.cn/Article/37800.shtml
- http://map.mobile.hcbezg.cn/Article/5400.shtml
- http://map.mobile.hcbezg.cn/Article/0839.shtml
- http://map.mobile.cvsifc.cn/Article/8134281.shtml
- http://map.mobile.fuvxie.cn/Article/914632.shtml
- http://map.mobile.cvsifc.cn/Article/264648.shtml
- http://map.mobile.hcbezg.cn/Article/16485.shtml
- http://map.mobile.cvsifc.cn/Article/95067.shtml
- http://map.mobile.hcbezg.cn/Article/05760.shtml
- http://map.mobile.cvsifc.cn/Article/765978.shtml
- http://map.mobile.hcbezg.cn/Article/3011.shtml
- http://map.mobile.fuvxie.cn/Article/02315.shtml
- http://map.mobile.fuvxie.cn/Article/3324564.shtml
- http://map.mobile.cvsifc.cn/Article/0617090.shtml
- http://map.mobile.cvsifc.cn/Article/1454.shtml
- http://map.mobile.hcbezg.cn/Article/310956.shtml
- http://map.mobile.cvsifc.cn/Article/1414.shtml
- http://map.mobile.fuvxie.cn/Article/886001.shtml
- http://map.mobile.cvsifc.cn/Article/8272.shtml
- http://map.mobile.fuvxie.cn/Article/74867.shtml
- http://map.mobile.hcbezg.cn/Article/0020.shtml
- http://map.mobile.cvsifc.cn/Article/70725.shtml
- http://map.mobile.fuvxie.cn/Article/351182.shtml
- http://map.mobile.fuvxie.cn/Article/6104134.shtml
- http://map.mobile.cvsifc.cn/Article/6343.shtml
- http://map.mobile.hcbezg.cn/Article/5286266.shtml
- http://map.mobile.hcbezg.cn/Article/85693.shtml
- http://map.mobile.hcbezg.cn/Article/1721661.shtml
- http://map.mobile.fuvxie.cn/Article/16491.shtml
- http://map.mobile.cvsifc.cn/Article/922512.shtml
- http://map.mobile.cvsifc.cn/Article/687852.shtml
- http://map.mobile.fuvxie.cn/Article/193348.shtml
- http://map.mobile.cvsifc.cn/Article/06725.shtml
- http://map.mobile.fuvxie.cn/Article/428039.shtml
- http://map.mobile.hcbezg.cn/Article/572195.shtml
- http://map.mobile.fuvxie.cn/Article/36181.shtml
- http://map.mobile.hcbezg.cn/Article/2069.shtml
- http://map.mobile.cvsifc.cn/Article/568485.shtml
- http://map.mobile.fuvxie.cn/Article/033867.shtml
- http://map.mobile.fuvxie.cn/Article/2650.shtml
- http://map.mobile.fuvxie.cn/Article/39832.shtml
- http://map.mobile.fuvxie.cn/Article/879563.shtml
- http://map.mobile.hcbezg.cn/Article/6586.shtml
- http://map.mobile.cvsifc.cn/Article/5864.shtml
- http://map.mobile.cvsifc.cn/Article/9421711.shtml
- http://map.mobile.cvsifc.cn/Article/3732.shtml
- http://map.mobile.cvsifc.cn/Article/232303.shtml
- http://map.mobile.hcbezg.cn/Article/4681499.shtml
- http://map.mobile.hcbezg.cn/Article/7261885.shtml
- http://map.mobile.hcbezg.cn/Article/57574.shtml
- http://map.mobile.hcbezg.cn/Article/33941.shtml
- http://map.mobile.hcbezg.cn/Article/972263.shtml
- http://map.mobile.cvsifc.cn/Article/416177.shtml
- http://map.mobile.fuvxie.cn/Article/3820136.shtml
- http://map.mobile.hcbezg.cn/Article/7310.shtml
- http://map.mobile.hcbezg.cn/Article/1715.shtml
- http://map.mobile.fuvxie.cn/Article/42679.shtml
- http://map.mobile.cvsifc.cn/Article/2131567.shtml
- http://map.mobile.cvsifc.cn/Article/47677.shtml
- http://map.mobile.fuvxie.cn/Article/8025.shtml
- http://map.mobile.cvsifc.cn/Article/722886.shtml
- http://map.mobile.fuvxie.cn/Article/091946.shtml
- http://map.mobile.fuvxie.cn/Article/31511.shtml
- http://map.mobile.hcbezg.cn/Article/6645070.shtml
- http://map.mobile.cvsifc.cn/Article/09107.shtml
- http://map.mobile.fuvxie.cn/Article/1919.shtml
- http://map.mobile.fuvxie.cn/Article/184606.shtml
- http://map.mobile.fuvxie.cn/Article/1573694.shtml
- http://map.mobile.hcbezg.cn/Article/7539775.shtml
- http://map.mobile.cvsifc.cn/Article/9958849.shtml
- http://map.mobile.hcbezg.cn/Article/5253.shtml
- http://map.mobile.fuvxie.cn/Article/4895.shtml
- http://map.mobile.cvsifc.cn/Article/3909.shtml
- http://map.mobile.cvsifc.cn/Article/06582.shtml
- http://map.mobile.hcbezg.cn/Article/6989.shtml
- http://map.mobile.cvsifc.cn/Article/833229.shtml
- http://map.mobile.cvsifc.cn/Article/848865.shtml
- http://map.mobile.fuvxie.cn/Article/3973.shtml
- http://map.mobile.hcbezg.cn/Article/43981.shtml
- http://map.mobile.hcbezg.cn/Article/0458174.shtml
- http://map.mobile.cvsifc.cn/Article/058359.shtml
- http://map.mobile.fuvxie.cn/Article/59897.shtml
- http://map.mobile.cvsifc.cn/Article/9420.shtml
- http://map.mobile.hcbezg.cn/Article/2314493.shtml
- http://map.mobile.fuvxie.cn/Article/38368.shtml
- http://map.mobile.hcbezg.cn/Article/9626947.shtml
- http://map.mobile.fuvxie.cn/Article/1520138.shtml
- http://map.mobile.fuvxie.cn/Article/040127.shtml
- http://map.mobile.hcbezg.cn/Article/132085.shtml
- http://map.mobile.cvsifc.cn/Article/741243.shtml
- http://map.mobile.hcbezg.cn/Article/776526.shtml
- http://map.mobile.hcbezg.cn/Article/2020.shtml
- http://map.mobile.fuvxie.cn/Article/8279031.shtml
- http://map.mobile.fuvxie.cn/Article/8568169.shtml
- http://map.mobile.cvsifc.cn/Article/66182.shtml
- http://map.mobile.hcbezg.cn/Article/1314930.shtml
- http://map.mobile.cvsifc.cn/Article/667330.shtml
- http://map.mobile.cvsifc.cn/Article/790560.shtml
- http://map.mobile.fuvxie.cn/Article/661558.shtml
- http://map.mobile.fuvxie.cn/Article/6328765.shtml
- http://map.mobile.fuvxie.cn/Article/6964577.shtml

## 项目结构

```
linkvault/
├── app.py                         # Flask 应用主入口，注册路由与启动服务
├── config.yaml                    # 项目核心配置文件，定义严格模式、超时阈值与输出规则
├── requirements.txt               # Python 依赖清单，锁定各库版本号
├── src/                           # 源代码主目录
│   ├── core/                      # 核心业务逻辑模块
│   │   ├── url_parser.py          # URL 解析器，负责拆解协议、域名、路径与查询参数
│   │   ├── formatter.py           # 格式化输出引擎，实现一行一条列表与表格生成
│   │   └── validator.py           # 合规性校验器，检查是否包含非法字符或缺失协议头
│   ├── services/                  # 服务层，封装外部调用与批处理逻辑
│   │   ├── health_checker.py      # 外链健康状态异步检查服务
│   │   ├── batch_importer.py      # 批量导入服务，支持 CSV / JSON / 纯文本
│   │   └── exporter.py            # 导出服务，输出 Markdown / JSON / YAML 格式
│   ├── web/                       # Web 界面相关模块
│   │   ├── routes/                # 路由蓝本，按功能拆分
│   │   │   ├── import_routes.py   # 导入相关接口
│   │   │   └── export_routes.py   # 导出相关接口
│   │   └── static/                # 静态资源（CSS / JavaScript）
│   └── utils/                     # 通用工具函数
│       ├── logger.py              # 日志配置与统一日志记录器
│       └── file_io.py             # 文件读写辅助，处理大文件分块
├── scripts/                       # 运维与初始化脚本
│   ├── init_db.py                 # 初始化 SQLite 数据库表结构
│   └── migrate_legacy.py          # 从旧版格式迁移数据的脚本
├── tests/                         # 单元测试与集成测试目录
│   ├── test_parser.py             # URL 解析器测试用例
│   └── test_formatter.py          # 格式化器输出一致性测试
├── docs/                          # 项目文档
│   ├── user_guide.md              # 用户手册
│   ├── administration.md          # 运维部署手册
│   └── api_reference.md           # API 接口文档
└── README.md                      # 项目说明文件（即本文档）
```

## 贡献指南

1. 查阅 issue 列表与项目看板，选择未被指派的 bug 修复或功能增强任务，在对应 issue 下回复确认认领，避免重复工作。

2. 从 main 分支创建新的功能分支，分支命名遵循 `feature/功能简述` 或 `fix/问题编号` 格式，例如 `feature/support-json-export`。

3. 编写或修改代码时，需同步更新位于 `tests/` 目录下的对应单元测试用例，确保新增逻辑的测试覆盖率不低于 85%，并保证现有测试全部通过。

4. 提交代码前运行 `scripts/pre-commit.sh` 执行代码风格检查（基于 flake8 与 black），修复所有报错后，提交清晰的 commit message，内容需说明修改原因与影响范围。

5. 发起 Pull Request 至 main 分支，PR 描述中需关联对应的 issue 编号，并填写自测结果与影响评估。至少需要一位项目维护者进行 Code Review，通过后即可合并。

## 常见问题

Q: 导入 URL 后系统提示 "裸域名无法识别"，但我希望保留裸域名格式不被自动补全，应该如何配置？

A: 请在项目根目录下的 config.yaml 文件中设置 `strict_mode: true` 以及 `auto_complete_protocol: false`。开启严格模式后，系统将完全按照用户输入的原始字符串输出，不会为裸域名添加 http:// 或 https:// 前缀，同时也不会移除用户自带的协议头。修改配置后需要重启服务生效。

Q: 健康检查功能对大量 URL 执行时出现超时或连接拒绝，是否会影响后续导出？

A: 健康检查结果仅用于标记和提示，不会阻塞导出流程。若某个 URL 在检查中超时，系统会将其状态记录为 "TIMEOUT" 并保留最近一次成功检查的备注。导出功能默认只输出 URL 列表本身，不包含健康状态。如需导出包含状态的报告，可在导出接口中增加参数 `include_status=true`，此时超时条目会显示为 "unreachable" 而非错误中断流程。

Q: 如何批量更新已经导入的 URL 的标签或备注信息？

A: 您可以通过 CSV 文件重新导入的方式实现批量更新。在导入文件中增加 "tags" 和 "notes" 两列，系统将根据 URL 的完整字符串（包含协议与路径）作为主键进行匹配，如果匹配成功则覆盖原有的标签与备注信息，如果匹配失败则作为新条目插入。该操作不会影响已存在的健康检查历史记录。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
