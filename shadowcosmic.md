# LinkVault

LinkVault 是一个面向技术研究、数据归档与内容聚合场景的轻量级外链管理平台。该项目定位于帮助个人研究员、内容策展人及小型技术团队高效收集、分类、验证和复用散落在互联网各处的信息型 URL 资源。LinkVault 不提供搜索引擎或爬虫功能，而是通过人工策展与结构化元数据标注，将零散的网页链接转化为可检索、可审计、可分享的知识资产。目标用户包括技术文档撰写者、渗透测试人员、漏洞情报分析师以及需要长期维护外部参考索引的工程团队。

## 功能概览

- **批量链接入库**：支持通过文本文件或 API 一次性导入大量 URL，自动完成去重、协议规范化与域名黑名单过滤。
- **元数据自动补全**：对入库 URL 自动发起 HEAD 请求，采集 Content-Type、Last-Modified、Content-Length 及响应状态码，并提取 HTML title 与 meta description。
- **自定义标签与分类树**：允许用户为每个链接赋予多个标签，并基于标签构建多级分类树，满足不同视角下的资源组织需求。
- **链接健康巡检**：周期性对已入库链接发起可用性探测，记录 HTTP 状态码变化、响应时间及重定向链，自动标记失效或内容变更的链接。
- **全文检索与过滤**：基于标题、描述、标签、域名及自定义备注进行全文检索，支持按状态码、协议类型、最后验证时间等多维度过滤排序。
- **数据导入导出**：支持将全量或筛选后的链接列表导出为 CSV、JSON 及 Markdown 表格格式，便于离线归档或嵌入技术文档。
- **审计日志**：记录所有链接的创建、修改、验证及删除操作，保留操作人、时间戳与变更前后差异，满足内部合规要求。

## 应用场景

- **漏洞情报跟踪**：安全研究员在分析公开漏洞报告时，需要将大量指向厂商公告、补丁说明及第三方技术分析的 URL 统一收纳，并定期检查这些链接是否仍然有效或内容是否更新。LinkVault 的健康巡检与标签系统可帮助研究员快速定位失效链接，避免引用过期情报。
- **技术文档外部参考管理**：技术文档团队在编写系统设计文档或用户手册时，常需要引用外部规范、API 文档或社区讨论。LinkVault 允许文档撰写者将外部引用链接集中管理，并自动生成包含标题和最后验证时间的参考附录，减少文档中的死链风险。
- **数据爬虫源站维护**：数据采集工程师维护爬虫任务时，需要管理目标网站的入口 URL 及备用镜像地址。LinkVault 的元数据补全功能可帮助工程师快速识别 URL 对应的内容类型，标签系统则可用于区分生产环境源站、测试环境源站及历史归档源站。
- **开源项目依赖文档索引**：开源项目维护者需要整理项目所依赖的第三方库官网、镜像站、代码仓库及问题跟踪系统地址。LinkVault 提供分类树与全文检索，帮助维护者快速查找特定依赖的官方文档链接，并在依赖升级时批量验证所有相关链接的可访问性。

## 快速开始

以下命令演示了如何在本地环境中完成 LinkVault 的克隆、依赖安装及服务启动。

```bash
git clone https://github.com/your-org/linkvault.git
cd linkvault
pip install -r requirements.txt
cp .env.example .env
python manage.py migrate
python manage.py runserver 0.0.0.0:8000
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 至 3.11 | 核心运行环境，不兼容 3.12 及以上版本 |
| PostgreSQL | 13 至 15 | 主数据库，用于存储链接元数据及审计日志 |
| Redis | 6.2 或更高 | 缓存层，用于链接健康巡检任务队列及临时缓存 |
| Nginx | 1.20 或更高 | 生产环境推荐反向代理服务器，用于静态文件服务 |
| Celery | 5.2 或更高 | 异步任务处理器，用于执行周期性链接巡检任务 |
| supervisor | 4.2 或更高 | 进程守护工具，用于生产环境管理 Celery Worker 及 Beat 进程 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | /docs/quickstart.md | 如何在 10 分钟内完成初次安装并导入第一批链接 |
| 操作手册 | /docs/usage/import.md | 支持哪些导入格式、如何配置自动元数据补全、标签如何创建 |
| 运维手册 | /docs/ops/health-check.md | 巡检周期如何配置、告警阈值如何设定、日志如何轮转 |
| API 参考 | /docs/api/v1/links.md | 所有 RESTful 接口的请求参数、响应结构及错误码说明 |
| 架构设计 | /docs/architecture/task-queue.md | Celery 任务拆分策略、Redis 队列监控及 Worker 横向扩展方案 |

## 资源列表

- http://m.mobile.cvsifc.cn/Article/8336.shtml
- http://m.mobile.cvsifc.cn/Article/74109.shtml
- http://m.mobile.hcbezg.cn/Article/6053.shtml
- http://m.mobile.hcbezg.cn/Article/5602.shtml
- http://m.mobile.hcbezg.cn/Article/0937.shtml
- http://m.mobile.cvsifc.cn/Article/3025723.shtml
- http://m.mobile.fuvxie.cn/Article/4582812.shtml
- http://m.mobile.cvsifc.cn/Article/067789.shtml
- http://m.mobile.hcbezg.cn/Article/1589979.shtml
- http://m.mobile.hcbezg.cn/Article/7160908.shtml
- http://m.mobile.fuvxie.cn/Article/6903.shtml
- http://m.mobile.hcbezg.cn/Article/9927.shtml
- http://m.mobile.fuvxie.cn/Article/1016359.shtml
- http://m.mobile.hcbezg.cn/Article/06335.shtml
- http://m.mobile.hcbezg.cn/Article/7426.shtml
- http://m.mobile.fuvxie.cn/Article/9386692.shtml
- http://m.mobile.hcbezg.cn/Article/429501.shtml
- http://m.mobile.hcbezg.cn/Article/1247085.shtml
- http://m.mobile.hcbezg.cn/Article/491066.shtml
- http://m.mobile.cvsifc.cn/Article/564986.shtml
- http://m.mobile.fuvxie.cn/Article/2711.shtml
- http://m.mobile.hcbezg.cn/Article/595155.shtml
- http://m.mobile.cvsifc.cn/Article/55215.shtml
- http://m.mobile.hcbezg.cn/Article/9831211.shtml
- http://m.mobile.cvsifc.cn/Article/4117.shtml
- http://m.mobile.hcbezg.cn/Article/703554.shtml
- http://m.mobile.hcbezg.cn/Article/0980792.shtml
- http://m.mobile.fuvxie.cn/Article/0367.shtml
- http://m.mobile.fuvxie.cn/Article/77795.shtml
- http://m.mobile.cvsifc.cn/Article/2326.shtml
- http://m.mobile.cvsifc.cn/Article/2236849.shtml
- http://m.mobile.fuvxie.cn/Article/44080.shtml
- http://m.mobile.hcbezg.cn/Article/5547.shtml
- http://m.mobile.hcbezg.cn/Article/579248.shtml
- http://m.mobile.hcbezg.cn/Article/6328.shtml
- http://m.mobile.cvsifc.cn/Article/383660.shtml
- http://m.mobile.cvsifc.cn/Article/4059.shtml
- http://m.mobile.hcbezg.cn/Article/2436.shtml
- http://m.mobile.fuvxie.cn/Article/09754.shtml
- http://m.mobile.hcbezg.cn/Article/7541528.shtml
- http://m.mobile.fuvxie.cn/Article/9130041.shtml
- http://m.mobile.hcbezg.cn/Article/4106.shtml
- http://m.mobile.fuvxie.cn/Article/4949299.shtml
- http://m.mobile.fuvxie.cn/Article/963899.shtml
- http://m.mobile.cvsifc.cn/Article/262392.shtml
- http://m.mobile.cvsifc.cn/Article/9226172.shtml
- http://m.mobile.hcbezg.cn/Article/6443.shtml
- http://m.mobile.cvsifc.cn/Article/8370.shtml
- http://m.mobile.hcbezg.cn/Article/0069.shtml
- http://m.mobile.fuvxie.cn/Article/01809.shtml
- http://m.mobile.fuvxie.cn/Article/024786.shtml
- http://m.mobile.hcbezg.cn/Article/74541.shtml
- http://m.mobile.cvsifc.cn/Article/813010.shtml
- http://m.mobile.fuvxie.cn/Article/3172.shtml
- http://m.mobile.hcbezg.cn/Article/11771.shtml
- http://m.mobile.fuvxie.cn/Article/2046046.shtml
- http://m.mobile.fuvxie.cn/Article/722656.shtml
- http://m.mobile.hcbezg.cn/Article/2785.shtml
- http://m.mobile.hcbezg.cn/Article/143625.shtml
- http://m.mobile.fuvxie.cn/Article/473204.shtml
- http://m.mobile.fuvxie.cn/Article/57692.shtml
- http://m.mobile.fuvxie.cn/Article/038743.shtml
- http://m.mobile.cvsifc.cn/Article/19150.shtml
- http://m.mobile.cvsifc.cn/Article/1606997.shtml
- http://m.mobile.hcbezg.cn/Article/1112.shtml
- http://m.mobile.hcbezg.cn/Article/9527766.shtml
- http://m.mobile.fuvxie.cn/Article/72600.shtml
- http://m.mobile.fuvxie.cn/Article/6335.shtml
- http://m.mobile.hcbezg.cn/Article/30529.shtml
- http://m.mobile.fuvxie.cn/Article/7409968.shtml
- http://m.mobile.hcbezg.cn/Article/41391.shtml
- http://m.mobile.hcbezg.cn/Article/8241.shtml
- http://m.mobile.hcbezg.cn/Article/9705.shtml
- http://m.mobile.cvsifc.cn/Article/7403.shtml
- http://m.mobile.hcbezg.cn/Article/8151.shtml
- http://m.mobile.cvsifc.cn/Article/786136.shtml
- http://m.mobile.fuvxie.cn/Article/0485.shtml
- http://m.mobile.fuvxie.cn/Article/700970.shtml
- http://m.mobile.hcbezg.cn/Article/194676.shtml
- http://m.mobile.hcbezg.cn/Article/7337.shtml
- http://m.mobile.fuvxie.cn/Article/6689.shtml
- http://m.mobile.fuvxie.cn/Article/288852.shtml
- http://m.mobile.cvsifc.cn/Article/9375134.shtml
- http://m.mobile.cvsifc.cn/Article/1025182.shtml
- http://m.mobile.fuvxie.cn/Article/9470334.shtml
- http://m.mobile.hcbezg.cn/Article/28088.shtml
- http://m.mobile.hcbezg.cn/Article/8280.shtml
- http://m.mobile.hcbezg.cn/Article/474337.shtml
- http://m.mobile.fuvxie.cn/Article/5489.shtml
- http://m.mobile.cvsifc.cn/Article/00985.shtml
- http://m.mobile.hcbezg.cn/Article/4576.shtml
- http://m.mobile.fuvxie.cn/Article/6490325.shtml
- http://m.mobile.hcbezg.cn/Article/6724.shtml
- http://m.mobile.fuvxie.cn/Article/4626134.shtml
- http://m.mobile.hcbezg.cn/Article/9452.shtml
- http://m.mobile.fuvxie.cn/Article/5403890.shtml
- http://m.mobile.cvsifc.cn/Article/468952.shtml
- http://m.mobile.fuvxie.cn/Article/6583.shtml
- http://m.mobile.hcbezg.cn/Article/29817.shtml
- http://m.mobile.cvsifc.cn/Article/5525755.shtml
- http://m.mobile.cvsifc.cn/Article/4404605.shtml
- http://m.mobile.fuvxie.cn/Article/2598.shtml
- http://m.mobile.hcbezg.cn/Article/9097795.shtml
- http://m.mobile.cvsifc.cn/Article/6067.shtml
- http://m.mobile.fuvxie.cn/Article/3690042.shtml
- http://m.mobile.fuvxie.cn/Article/33953.shtml
- http://m.mobile.cvsifc.cn/Article/1892.shtml
- http://m.mobile.cvsifc.cn/Article/537349.shtml
- http://m.mobile.fuvxie.cn/Article/40821.shtml
- http://m.mobile.fuvxie.cn/Article/88575.shtml
- http://m.mobile.cvsifc.cn/Article/207569.shtml
- http://m.mobile.hcbezg.cn/Article/1331056.shtml
- http://m.mobile.fuvxie.cn/Article/5618.shtml
- http://m.mobile.cvsifc.cn/Article/0838933.shtml
- http://m.mobile.cvsifc.cn/Article/6293939.shtml
- http://m.mobile.cvsifc.cn/Article/7639.shtml
- http://m.mobile.hcbezg.cn/Article/06179.shtml
- http://m.mobile.cvsifc.cn/Article/4673.shtml
- http://m.mobile.fuvxie.cn/Article/918698.shtml
- http://m.mobile.hcbezg.cn/Article/5339.shtml
- http://m.mobile.hcbezg.cn/Article/52262.shtml
- http://m.mobile.hcbezg.cn/Article/7041.shtml
- http://m.mobile.cvsifc.cn/Article/22713.shtml
- http://m.mobile.fuvxie.cn/Article/701214.shtml
- http://m.mobile.cvsifc.cn/Article/6566045.shtml
- http://m.mobile.hcbezg.cn/Article/71555.shtml
- http://m.mobile.fuvxie.cn/Article/579070.shtml
- http://m.mobile.cvsifc.cn/Article/5478.shtml
- http://m.mobile.fuvxie.cn/Article/96358.shtml
- http://m.mobile.fuvxie.cn/Article/06934.shtml
- http://m.mobile.hcbezg.cn/Article/785976.shtml
- http://m.mobile.cvsifc.cn/Article/210274.shtml
- http://m.mobile.hcbezg.cn/Article/9820544.shtml
- http://m.mobile.hcbezg.cn/Article/620298.shtml
- http://m.mobile.fuvxie.cn/Article/051020.shtml
- http://m.mobile.hcbezg.cn/Article/958768.shtml
- http://m.mobile.cvsifc.cn/Article/8387669.shtml
- http://m.mobile.fuvxie.cn/Article/4917.shtml
- http://m.mobile.cvsifc.cn/Article/943752.shtml
- http://m.mobile.hcbezg.cn/Article/46415.shtml
- http://m.mobile.hcbezg.cn/Article/0146718.shtml
- http://m.mobile.fuvxie.cn/Article/85554.shtml
- http://m.mobile.fuvxie.cn/Article/9541025.shtml
- http://m.mobile.fuvxie.cn/Article/817549.shtml
- http://m.mobile.cvsifc.cn/Article/97395.shtml
- http://m.mobile.fuvxie.cn/Article/039460.shtml
- http://m.mobile.cvsifc.cn/Article/268382.shtml
- http://m.mobile.hcbezg.cn/Article/7772185.shtml
- http://m.mobile.fuvxie.cn/Article/187477.shtml
- http://m.mobile.cvsifc.cn/Article/37800.shtml
- http://m.mobile.hcbezg.cn/Article/5400.shtml
- http://m.mobile.hcbezg.cn/Article/0839.shtml
- http://m.mobile.cvsifc.cn/Article/8134281.shtml
- http://m.mobile.fuvxie.cn/Article/914632.shtml
- http://m.mobile.cvsifc.cn/Article/264648.shtml
- http://m.mobile.hcbezg.cn/Article/16485.shtml
- http://m.mobile.cvsifc.cn/Article/95067.shtml
- http://m.mobile.hcbezg.cn/Article/05760.shtml
- http://m.mobile.cvsifc.cn/Article/765978.shtml
- http://m.mobile.hcbezg.cn/Article/3011.shtml
- http://m.mobile.fuvxie.cn/Article/02315.shtml
- http://m.mobile.fuvxie.cn/Article/3324564.shtml
- http://m.mobile.cvsifc.cn/Article/0617090.shtml
- http://m.mobile.cvsifc.cn/Article/1454.shtml
- http://m.mobile.hcbezg.cn/Article/310956.shtml
- http://m.mobile.cvsifc.cn/Article/1414.shtml
- http://m.mobile.fuvxie.cn/Article/886001.shtml
- http://m.mobile.cvsifc.cn/Article/8272.shtml
- http://m.mobile.fuvxie.cn/Article/74867.shtml
- http://m.mobile.hcbezg.cn/Article/0020.shtml
- http://m.mobile.cvsifc.cn/Article/70725.shtml
- http://m.mobile.fuvxie.cn/Article/351182.shtml
- http://m.mobile.fuvxie.cn/Article/6104134.shtml
- http://m.mobile.cvsifc.cn/Article/6343.shtml
- http://m.mobile.hcbezg.cn/Article/5286266.shtml
- http://m.mobile.hcbezg.cn/Article/85693.shtml
- http://m.mobile.hcbezg.cn/Article/1721661.shtml
- http://m.mobile.fuvxie.cn/Article/16491.shtml
- http://m.mobile.cvsifc.cn/Article/922512.shtml
- http://m.mobile.cvsifc.cn/Article/687852.shtml
- http://m.mobile.fuvxie.cn/Article/193348.shtml
- http://m.mobile.cvsifc.cn/Article/06725.shtml
- http://m.mobile.fuvxie.cn/Article/428039.shtml
- http://m.mobile.hcbezg.cn/Article/572195.shtml
- http://m.mobile.fuvxie.cn/Article/36181.shtml
- http://m.mobile.hcbezg.cn/Article/2069.shtml
- http://m.mobile.cvsifc.cn/Article/568485.shtml
- http://m.mobile.fuvxie.cn/Article/033867.shtml
- http://m.mobile.fuvxie.cn/Article/2650.shtml
- http://m.mobile.fuvxie.cn/Article/39832.shtml
- http://m.mobile.fuvxie.cn/Article/879563.shtml
- http://m.mobile.hcbezg.cn/Article/6586.shtml
- http://m.mobile.cvsifc.cn/Article/5864.shtml
- http://m.mobile.cvsifc.cn/Article/9421711.shtml
- http://m.mobile.cvsifc.cn/Article/3732.shtml
- http://m.mobile.cvsifc.cn/Article/232303.shtml
- http://m.mobile.hcbezg.cn/Article/4681499.shtml
- http://m.mobile.hcbezg.cn/Article/7261885.shtml
- http://m.mobile.hcbezg.cn/Article/57574.shtml
- http://m.mobile.hcbezg.cn/Article/33941.shtml
- http://m.mobile.hcbezg.cn/Article/972263.shtml
- http://m.mobile.cvsifc.cn/Article/416177.shtml
- http://m.mobile.fuvxie.cn/Article/3820136.shtml
- http://m.mobile.hcbezg.cn/Article/7310.shtml
- http://m.mobile.hcbezg.cn/Article/1715.shtml
- http://m.mobile.fuvxie.cn/Article/42679.shtml
- http://m.mobile.cvsifc.cn/Article/2131567.shtml
- http://m.mobile.cvsifc.cn/Article/47677.shtml
- http://m.mobile.fuvxie.cn/Article/8025.shtml
- http://m.mobile.cvsifc.cn/Article/722886.shtml
- http://m.mobile.fuvxie.cn/Article/091946.shtml
- http://m.mobile.fuvxie.cn/Article/31511.shtml
- http://m.mobile.hcbezg.cn/Article/6645070.shtml
- http://m.mobile.cvsifc.cn/Article/09107.shtml
- http://m.mobile.fuvxie.cn/Article/1919.shtml
- http://m.mobile.fuvxie.cn/Article/184606.shtml
- http://m.mobile.fuvxie.cn/Article/1573694.shtml
- http://m.mobile.hcbezg.cn/Article/7539775.shtml
- http://m.mobile.cvsifc.cn/Article/9958849.shtml
- http://m.mobile.hcbezg.cn/Article/5253.shtml
- http://m.mobile.fuvxie.cn/Article/4895.shtml
- http://m.mobile.cvsifc.cn/Article/3909.shtml
- http://m.mobile.cvsifc.cn/Article/06582.shtml
- http://m.mobile.hcbezg.cn/Article/6989.shtml
- http://m.mobile.cvsifc.cn/Article/833229.shtml
- http://m.mobile.cvsifc.cn/Article/848865.shtml
- http://m.mobile.fuvxie.cn/Article/3973.shtml
- http://m.mobile.hcbezg.cn/Article/43981.shtml
- http://m.mobile.hcbezg.cn/Article/0458174.shtml
- http://m.mobile.cvsifc.cn/Article/058359.shtml
- http://m.mobile.fuvxie.cn/Article/59897.shtml
- http://m.mobile.cvsifc.cn/Article/9420.shtml
- http://m.mobile.hcbezg.cn/Article/2314493.shtml
- http://m.mobile.fuvxie.cn/Article/38368.shtml
- http://m.mobile.hcbezg.cn/Article/9626947.shtml
- http://m.mobile.fuvxie.cn/Article/1520138.shtml
- http://m.mobile.fuvxie.cn/Article/040127.shtml
- http://m.mobile.hcbezg.cn/Article/132085.shtml
- http://m.mobile.cvsifc.cn/Article/741243.shtml
- http://m.mobile.hcbezg.cn/Article/776526.shtml
- http://m.mobile.hcbezg.cn/Article/2020.shtml
- http://m.mobile.fuvxie.cn/Article/8279031.shtml
- http://m.mobile.fuvxie.cn/Article/8568169.shtml
- http://m.mobile.cvsifc.cn/Article/66182.shtml
- http://m.mobile.hcbezg.cn/Article/1314930.shtml
- http://m.mobile.cvsifc.cn/Article/667330.shtml
- http://m.mobile.cvsifc.cn/Article/790560.shtml
- http://m.mobile.fuvxie.cn/Article/661558.shtml
- http://m.mobile.fuvxie.cn/Article/6328765.shtml
- http://m.mobile.fuvxie.cn/Article/6964577.shtml

## 项目结构

```
linkvault/
├── cmd/                                 # 命令行入口及运维工具
│   ├── server/                          # Web 服务启动入口
│   │   └── main.go                      # 主服务启动逻辑，含端口及中间件配置
│   └── cli/                             # 独立 CLI 工具，用于批量导入及数据导出
│       └── import.go                    # 实现从本地文件或远程 URL 批量导入链接
├── internal/                            # 内部私有包，不对外暴露
│   ├── core/                            # 核心数据模型及业务逻辑
│   │   ├── link.go                      # Link 结构体定义，包含 URL、标题、描述、标签等字段
│   │   └── validator.go                 # URL 协议校验、域名黑名单、去重逻辑
│   ├── storage/                         # 数据库及缓存访问层
│   │   ├── postgres/                    # PostgreSQL 实现，含迁移脚本及索引定义
│   │   └── redis/                       # Redis 缓存操作，用于巡检任务队列及临时状态存储
│   ├── probe/                           # 链接健康巡检模块
│   │   ├── checker.go                   # 并发 HTTP 探测，支持超时控制及重定向跟踪
│   │   └── scheduler.go                 # 基于 cron 表达式的周期性任务调度
│   └── api/                             # HTTP 处理器及路由注册
│       ├── handler/                     # 每个路由对应的请求处理函数
│       └── middleware/                  # 鉴权、日志记录、限流等中间件
├── pkg/                                 # 可被外部项目引用的公共库
│   ├── httputil/                        # HTTP 辅助函数，如 User-Agent 轮转、重试策略
│   └── markdown/                        # 将链接列表渲染为 Markdown 表格或列表的工具
├── web/                                 # 前端静态资源及模板
│   ├── static/                          # CSS、JavaScript、图片等静态文件
│   └── templates/                       # Go 模板文件，用于服务端渲染管理后台
├── configs/                             # 配置文件模板及环境变量定义
│   ├── config.yaml                      # 主配置文件，含数据库连接、巡检间隔、日志级别
│   └── .env.example                     # 环境变量示例，用于敏感信息注入
├── scripts/                             # 辅助脚本，用于开发环境初始化及数据迁移
│   ├── bootstrap.sh                     # 一键安装依赖并初始化数据库
│   └── seed_links.sh                    # 通过 API 批量写入测试链接数据
├── docs/                                # 完整项目文档
│   ├── quickstart.md                    # 快速入门指南
│   ├── api/                             # API 接口文档，按版本组织
│   └── ops/                             # 生产环境部署及监控指南
├── go.mod                               # Go 模块依赖定义
├── go.sum                               # 依赖校验和文件
├── Makefile                             # 常用开发命令封装，如 make build、make test
└── README.md                            # 项目概述及快速指引
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库至个人账户，并克隆到本地开发环境。请确保本地 Go 版本不低于 1.21，且已正确配置 GOPATH 与 Go Modules。
2. 创建新的功能分支，分支命名遵循 `feature/功能简述` 或 `fix/问题简述` 格式。提交前请运行 `make lint` 与 `make test` 确保代码风格与单元测试均通过。
3. 若涉及数据库 Schema 变更，需在 `internal/storage/postgres/migrations` 目录下创建新的迁移文件，并提供回滚脚本。迁移文件命名规则为 `YYYYMMDDHHMMSS_描述.sql`。
4. 提交 Pull Request 时，请填写完整模板内容，包括本次变更的目的、测试覆盖情况、是否影响现有 API 兼容性以及对应文档更新链接。
5. 所有新增或修改的公开函数、接口及配置项必须在 `docs/` 目录下同步更新对应文档，文档变更需与代码变更在同一 PR 中提交。

## 常见问题

**Q：导入大量 URL 时页面响应缓慢或超时，应如何优化？**

A：LinkVault 的设计建议将超过 500 条链接的导入操作通过 CLI 工具而非 Web 界面执行。CLI 模式会分批提交任务并绕过 HTTP 超时限制。若仍需通过 API 导入，可在请求头中添加 `X-Batch-Mode: async`，使服务将导入任务放入 Celery 队列后立即返回任务 ID，后续通过任务状态接口查询导入进度。

**Q：健康巡检任务是否会对目标站点造成过大请求压力？**

A：LinkVault 默认巡检并发数为 5，且在每个请求之间加入 200 毫秒至 500 毫秒的随机延迟。用户可在配置文件中调整 `probe.concurrency` 与 `probe.delay_range_ms` 参数。对于生产环境，建议将巡检任务安排在目标站点的低峰时段执行，并通过 `probe.whitelist_hours` 配置项限制每日巡检时间窗口。

**Q：如何迁移 LinkVault 数据至另一套数据库实例？**

A：使用内置的导出工具生成完整 JSON 或 CSV 导出文件，命令为 `linkvault-cli export --format json --output backup.json`。在目标实例上完成数据库初始化后，使用导入命令 `linkvault-cli import --file backup.json` 即可恢复全部链接记录及标签关系。注意导入前需确保目标环境的 PostgreSQL 版本与源环境一致，且已创建相同的扩展如 `pg_trgm`。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
