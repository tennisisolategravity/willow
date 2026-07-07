# WebIndex 聚合导航系统

WebIndex 是一个面向技术研究与信息聚合的轻量级外链资源导航系统，专为需要从分散源头批量采集、归档与检索外部文章链接的开发者、数据分析师与内容运营团队设计。系统以静态站点形态交付，不依赖后端数据库，所有资源条目以结构化 Markdown 和 JSON 混合存储，支持通过 GitHub Actions 或本地脚本完成每日增量更新。

WebIndex 不提供爬虫功能，也不存储任何第三方内容副本，仅作为 URL 元信息的整理与展示层。目标用户包括：需要维护技术周报的编辑、需要跟踪特定域名发布动态的研究人员、以及希望自建轻量导航站点的开源爱好者。

## 功能概览

**批量链接导入** 支持通过 CSV 或纯文本列表批量追加外部文章链接，系统自动解析域名、路径与扩展名，生成标准化的条目记录。

**多级标签分类** 每个资源条目可关联一个或多个主题标签，标签体系完全由用户自定义，系统提供标签云与按标签筛选视图。

**源站聚合视图** 自动按顶级域名或二级域名分组展示所有收录链接，便于快速识别信息密度最高的外部来源。

**全文元数据提取** 对每个 URL 自动发起 HEAD 请求（可配置超时与重试），提取 Content-Type、Last-Modified、Content-Length 等标准响应头信息，并存入元数据缓存。

**失效链接检测** 每日定时任务执行链接可达性检查，标记返回 4xx 或 5xx 状态的条目，支持导出失效报告。

**静态站点生成** 基于模板引擎将全部资源数据渲染为纯 HTML 静态页面，无需运行后端服务即可部署到任何 Web 服务器或 CDN。

**JSON 数据导出** 提供完整的资源列表 JSON 导出接口，方便其他系统或脚本进行二次处理。

**增量更新支持** 通过记录每次导入的时间戳与批次编号，支持仅处理新增链接，避免全量重建。

## 应用场景

技术团队内部知识库辅助：团队可以将日常阅读中发现的优质外部技术文章链接统一收录到 WebIndex，按技术栈（如 Rust、Python、Kubernetes）打标，新成员入职时可快速浏览团队推荐的阅读材料。

个人开发者信息聚合：独立开发者可将订阅的多个技术博客、官方文档更新日志、社区讨论帖集中收录，通过 WebIndex 的源站聚合视图在一处查看所有外部动态，避免频繁切换浏览器标签。

开源项目外部引用追踪：开源项目维护者可以将项目文档中引用的所有外部链接纳入 WebIndex 管理，定期运行失效检测，及时发现并修复文档中的死链，提升文档质量。

离线阅读准备：研究人员可在联网环境下将一批待读文章链接导入 WebIndex，利用元数据提取功能记录文章标题与时间，再通过导出 JSON 或静态页面在隔离环境中进行阅读清单管理。

## 快速开始

以下命令适用于 Linux 与 macOS 环境，Windows 用户建议使用 WSL2 或 Git Bash 执行。

```bash
# 克隆代码仓库
git clone https://github.com/webindex/webindex.git
cd webindex

# 安装 Python 依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 运行导入示例数据（包含 250 条测试链接）
python scripts/import_batch.py --batch 52 --source data/batch_52.txt

# 构建静态站点
python scripts/build_static.py --output dist/

# 启动本地预览服务
python -m http.server 8000 --directory dist/
```

执行完成后，打开浏览器访问 `http://localhost:8000` 即可查看导航站点首页。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.9 及以上 | 核心运行环境，低于 3.9 版本不支持类型注解与部分标准库特性 |
| pip | 21.0 及以上 | Python 包管理工具，用于安装 requirements.txt 中列出的第三方库 |
| Git | 2.25 及以上 | 用于克隆仓库以及后续拉取更新，Windows 需配置 Git Bash 环境 |
| 网络连接 | 出口 443/80 可达 | 元数据提取与失效链接检测需要对外发起 HTTP 请求，需确保网络策略允许 |
| 磁盘空间 | 至少 200 MB | 存储源码、缓存元数据与生成的静态页面，随收录链接数量线性增长 |
| 内存 | 最低 512 MB | 构建静态站点时需加载全部资源数据至内存，超过 50000 条链接建议提升至 1 GB |
| 操作系统 | Linux / macOS / WSL2 | 开发与生产环境均以 POSIX 兼容系统为首选，Windows 原生支持有限 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | docs/getting-started.md | 如何第一次运行并导入链接？系统目录结构是什么样的？有哪些关键配置文件？ |
| 导入与更新 | docs/import-workflow.md | 支持哪些导入格式？如何批量追加链接？增量更新如何工作？批次编号有什么作用？ |
| 配置参考 | docs/configuration.md | 环境变量有哪些？如何修改元数据提取的超时与重试参数？标签体系如何自定义？ |
| 部署指南 | docs/deployment.md | 静态站点可以部署到哪些平台？如何配置自定义域名？如何使用 CDN 加速访问？ |
| API 与导出 | docs/api-export.md | JSON 导出接口的字段定义是什么？如何与其他系统集成？是否支持 RSS 输出？ |
| 故障排查 | docs/troubleshooting.md | 元数据提取失败如何处理？失效链接检测误报怎么办？构建过程内存不足如何解决？ |

## 资源列表

- http://h5.mobile.cvsifc.cn/Article/32104.shtml
- http://h5.mobile.fuvxie.cn/Article/5640902.shtml
- http://h5.mobile.fuvxie.cn/Article/1167128.shtml
- http://h5.mobile.hcbezg.cn/Article/588985.shtml
- http://h5.mobile.hcbezg.cn/Article/225323.shtml
- http://h5.mobile.hcbezg.cn/Article/6124972.shtml
- http://h5.mobile.hcbezg.cn/Article/1505.shtml
- http://h5.mobile.hcbezg.cn/Article/552297.shtml
- http://h5.mobile.cvsifc.cn/Article/1421218.shtml
- http://h5.mobile.fuvxie.cn/Article/8989.shtml
- http://h5.mobile.cvsifc.cn/Article/803573.shtml
- http://h5.mobile.cvsifc.cn/Article/83512.shtml
- http://h5.mobile.hcbezg.cn/Article/51233.shtml
- http://h5.mobile.fuvxie.cn/Article/349984.shtml
- http://h5.mobile.hcbezg.cn/Article/2075.shtml
- http://h5.mobile.hcbezg.cn/Article/63383.shtml
- http://h5.mobile.hcbezg.cn/Article/372653.shtml
- http://h5.mobile.hcbezg.cn/Article/3491.shtml
- http://h5.mobile.fuvxie.cn/Article/659939.shtml
- http://h5.mobile.cvsifc.cn/Article/70900.shtml
- http://h5.mobile.cvsifc.cn/Article/91518.shtml
- http://h5.mobile.fuvxie.cn/Article/42856.shtml
- http://h5.mobile.hcbezg.cn/Article/674202.shtml
- http://h5.mobile.cvsifc.cn/Article/0999.shtml
- http://h5.mobile.hcbezg.cn/Article/4528.shtml
- http://h5.mobile.fuvxie.cn/Article/40473.shtml
- http://h5.mobile.cvsifc.cn/Article/9986.shtml
- http://h5.mobile.cvsifc.cn/Article/9962.shtml
- http://h5.mobile.fuvxie.cn/Article/024084.shtml
- http://h5.mobile.cvsifc.cn/Article/8062899.shtml
- http://h5.mobile.hcbezg.cn/Article/9213047.shtml
- http://h5.mobile.hcbezg.cn/Article/5641.shtml
- http://h5.mobile.cvsifc.cn/Article/8873027.shtml
- http://h5.mobile.fuvxie.cn/Article/394605.shtml
- http://h5.mobile.fuvxie.cn/Article/3945349.shtml
- http://h5.mobile.cvsifc.cn/Article/3066.shtml
- http://h5.mobile.hcbezg.cn/Article/738491.shtml
- http://h5.mobile.cvsifc.cn/Article/031352.shtml
- http://h5.mobile.hcbezg.cn/Article/59420.shtml
- http://h5.mobile.cvsifc.cn/Article/8084.shtml
- http://h5.mobile.hcbezg.cn/Article/6385.shtml
- http://h5.mobile.cvsifc.cn/Article/741398.shtml
- http://h5.mobile.fuvxie.cn/Article/39373.shtml
- http://h5.mobile.hcbezg.cn/Article/5628263.shtml
- http://h5.mobile.hcbezg.cn/Article/34126.shtml
- http://h5.mobile.hcbezg.cn/Article/379456.shtml
- http://h5.mobile.fuvxie.cn/Article/43562.shtml
- http://h5.mobile.fuvxie.cn/Article/2442.shtml
- http://h5.mobile.hcbezg.cn/Article/08554.shtml
- http://h5.mobile.hcbezg.cn/Article/449426.shtml
- http://h5.mobile.fuvxie.cn/Article/5508779.shtml
- http://h5.mobile.cvsifc.cn/Article/802973.shtml
- http://h5.mobile.fuvxie.cn/Article/01989.shtml
- http://h5.mobile.cvsifc.cn/Article/06529.shtml
- http://h5.mobile.cvsifc.cn/Article/746327.shtml
- http://h5.mobile.fuvxie.cn/Article/4961128.shtml
- http://h5.mobile.fuvxie.cn/Article/2050919.shtml
- http://h5.mobile.fuvxie.cn/Article/58122.shtml
- http://h5.mobile.fuvxie.cn/Article/235865.shtml
- http://h5.mobile.hcbezg.cn/Article/3641.shtml
- http://h5.mobile.fuvxie.cn/Article/5850183.shtml
- http://h5.mobile.hcbezg.cn/Article/92564.shtml
- http://h5.mobile.cvsifc.cn/Article/6794683.shtml
- http://h5.mobile.cvsifc.cn/Article/5894713.shtml
- http://h5.mobile.fuvxie.cn/Article/6884.shtml
- http://h5.mobile.cvsifc.cn/Article/3288.shtml
- http://h5.mobile.hcbezg.cn/Article/5745.shtml
- http://h5.mobile.hcbezg.cn/Article/0353.shtml
- http://h5.mobile.hcbezg.cn/Article/4911.shtml
- http://h5.mobile.hcbezg.cn/Article/424427.shtml
- http://h5.mobile.cvsifc.cn/Article/49854.shtml
- http://h5.mobile.hcbezg.cn/Article/767928.shtml
- http://h5.mobile.cvsifc.cn/Article/87654.shtml
- http://h5.mobile.hcbezg.cn/Article/536530.shtml
- http://h5.mobile.cvsifc.cn/Article/9768670.shtml
- http://h5.mobile.cvsifc.cn/Article/551735.shtml
- http://h5.mobile.hcbezg.cn/Article/7958406.shtml
- http://h5.mobile.fuvxie.cn/Article/618566.shtml
- http://h5.mobile.fuvxie.cn/Article/6249.shtml
- http://h5.mobile.fuvxie.cn/Article/1987.shtml
- http://h5.mobile.cvsifc.cn/Article/4555.shtml
- http://h5.mobile.fuvxie.cn/Article/1558.shtml
- http://h5.mobile.hcbezg.cn/Article/7892.shtml
- http://h5.mobile.fuvxie.cn/Article/217771.shtml
- http://h5.mobile.fuvxie.cn/Article/1084661.shtml
- http://h5.mobile.fuvxie.cn/Article/4015.shtml
- http://h5.mobile.hcbezg.cn/Article/1263982.shtml
- http://h5.mobile.cvsifc.cn/Article/51545.shtml
- http://h5.mobile.cvsifc.cn/Article/84900.shtml
- http://h5.mobile.hcbezg.cn/Article/2631.shtml
- http://h5.mobile.cvsifc.cn/Article/2521.shtml
- http://h5.mobile.hcbezg.cn/Article/489654.shtml
- http://h5.mobile.fuvxie.cn/Article/204439.shtml
- http://h5.mobile.cvsifc.cn/Article/3135.shtml
- http://h5.mobile.cvsifc.cn/Article/2513.shtml
- http://h5.mobile.cvsifc.cn/Article/2883.shtml
- http://h5.mobile.fuvxie.cn/Article/5829.shtml
- http://h5.mobile.hcbezg.cn/Article/5688296.shtml
- http://h5.mobile.hcbezg.cn/Article/2344.shtml
- http://h5.mobile.fuvxie.cn/Article/5656205.shtml
- http://h5.mobile.hcbezg.cn/Article/1997490.shtml
- http://h5.mobile.fuvxie.cn/Article/9524.shtml
- http://h5.mobile.cvsifc.cn/Article/2752.shtml
- http://h5.mobile.hcbezg.cn/Article/92691.shtml
- http://h5.mobile.hcbezg.cn/Article/1167515.shtml
- http://h5.mobile.cvsifc.cn/Article/76690.shtml
- http://h5.mobile.hcbezg.cn/Article/732144.shtml
- http://h5.mobile.cvsifc.cn/Article/9446.shtml
- http://h5.mobile.cvsifc.cn/Article/75212.shtml
- http://h5.mobile.fuvxie.cn/Article/2315476.shtml
- http://h5.mobile.fuvxie.cn/Article/336636.shtml
- http://h5.mobile.hcbezg.cn/Article/1418.shtml
- http://h5.mobile.cvsifc.cn/Article/5767376.shtml
- http://h5.mobile.fuvxie.cn/Article/5480.shtml
- http://h5.mobile.cvsifc.cn/Article/9174.shtml
- http://h5.mobile.fuvxie.cn/Article/579617.shtml
- http://h5.mobile.hcbezg.cn/Article/6609966.shtml
- http://h5.mobile.cvsifc.cn/Article/975965.shtml
- http://h5.mobile.cvsifc.cn/Article/9490.shtml
- http://h5.mobile.hcbezg.cn/Article/23595.shtml
- http://h5.mobile.cvsifc.cn/Article/679874.shtml
- http://h5.mobile.hcbezg.cn/Article/10715.shtml
- http://h5.mobile.cvsifc.cn/Article/22126.shtml
- http://h5.mobile.cvsifc.cn/Article/941250.shtml
- http://h5.mobile.fuvxie.cn/Article/850132.shtml
- http://h5.mobile.hcbezg.cn/Article/32819.shtml
- http://h5.mobile.hcbezg.cn/Article/6107.shtml
- http://h5.mobile.hcbezg.cn/Article/2245999.shtml
- http://h5.mobile.fuvxie.cn/Article/6784444.shtml
- http://h5.mobile.hcbezg.cn/Article/98595.shtml
- http://h5.mobile.fuvxie.cn/Article/4586744.shtml
- http://h5.mobile.cvsifc.cn/Article/784357.shtml
- http://h5.mobile.hcbezg.cn/Article/817919.shtml
- http://h5.mobile.fuvxie.cn/Article/323704.shtml
- http://h5.mobile.fuvxie.cn/Article/5741.shtml
- http://h5.mobile.fuvxie.cn/Article/6886.shtml
- http://h5.mobile.cvsifc.cn/Article/177315.shtml
- http://h5.mobile.cvsifc.cn/Article/3836.shtml
- http://h5.mobile.hcbezg.cn/Article/5231829.shtml
- http://h5.mobile.fuvxie.cn/Article/5335.shtml
- http://h5.mobile.fuvxie.cn/Article/826424.shtml
- http://h5.mobile.cvsifc.cn/Article/6638175.shtml
- http://h5.mobile.hcbezg.cn/Article/41192.shtml
- http://h5.mobile.cvsifc.cn/Article/1418.shtml
- http://h5.mobile.hcbezg.cn/Article/0840.shtml
- http://h5.mobile.fuvxie.cn/Article/624649.shtml
- http://h5.mobile.fuvxie.cn/Article/1074.shtml
- http://h5.mobile.cvsifc.cn/Article/5170042.shtml
- http://h5.mobile.fuvxie.cn/Article/5027.shtml
- http://h5.mobile.hcbezg.cn/Article/8785492.shtml
- http://h5.mobile.fuvxie.cn/Article/905280.shtml
- http://h5.mobile.fuvxie.cn/Article/1720.shtml
- http://h5.mobile.cvsifc.cn/Article/1530.shtml
- http://h5.mobile.fuvxie.cn/Article/4581.shtml
- http://h5.mobile.fuvxie.cn/Article/88611.shtml
- http://h5.mobile.cvsifc.cn/Article/8477938.shtml
- http://h5.mobile.fuvxie.cn/Article/035910.shtml
- http://h5.mobile.hcbezg.cn/Article/099912.shtml
- http://h5.mobile.fuvxie.cn/Article/2593.shtml
- http://h5.mobile.fuvxie.cn/Article/5995.shtml
- http://h5.mobile.cvsifc.cn/Article/0581454.shtml
- http://h5.mobile.cvsifc.cn/Article/8827405.shtml
- http://h5.mobile.cvsifc.cn/Article/2998843.shtml
- http://h5.mobile.fuvxie.cn/Article/65626.shtml
- http://h5.mobile.fuvxie.cn/Article/21695.shtml
- http://h5.mobile.fuvxie.cn/Article/8191299.shtml
- http://h5.mobile.fuvxie.cn/Article/6963649.shtml
- http://h5.mobile.cvsifc.cn/Article/5724.shtml
- http://h5.mobile.fuvxie.cn/Article/88219.shtml
- http://h5.mobile.hcbezg.cn/Article/428483.shtml
- http://h5.mobile.hcbezg.cn/Article/489936.shtml
- http://h5.mobile.fuvxie.cn/Article/983202.shtml
- http://h5.mobile.hcbezg.cn/Article/8770327.shtml
- http://h5.mobile.hcbezg.cn/Article/1634.shtml
- http://h5.mobile.hcbezg.cn/Article/4045.shtml
- http://h5.mobile.cvsifc.cn/Article/0050246.shtml
- http://h5.mobile.hcbezg.cn/Article/644399.shtml
- http://h5.mobile.fuvxie.cn/Article/0012084.shtml
- http://h5.mobile.cvsifc.cn/Article/8956.shtml
- http://h5.mobile.hcbezg.cn/Article/9714439.shtml
- http://h5.mobile.hcbezg.cn/Article/98973.shtml
- http://h5.mobile.cvsifc.cn/Article/1428.shtml
- http://h5.mobile.fuvxie.cn/Article/5269224.shtml
- http://h5.mobile.cvsifc.cn/Article/84788.shtml
- http://h5.mobile.hcbezg.cn/Article/74354.shtml
- http://h5.mobile.hcbezg.cn/Article/2370455.shtml
- http://h5.mobile.hcbezg.cn/Article/0194.shtml
- http://h5.mobile.fuvxie.cn/Article/60925.shtml
- http://h5.mobile.fuvxie.cn/Article/6787.shtml
- http://h5.mobile.fuvxie.cn/Article/774603.shtml
- http://h5.mobile.fuvxie.cn/Article/821155.shtml
- http://h5.mobile.hcbezg.cn/Article/77059.shtml
- http://h5.mobile.cvsifc.cn/Article/6543.shtml
- http://h5.mobile.hcbezg.cn/Article/9742622.shtml
- http://h5.mobile.fuvxie.cn/Article/9864.shtml
- http://h5.mobile.cvsifc.cn/Article/31932.shtml
- http://h5.mobile.hcbezg.cn/Article/615367.shtml
- http://h5.mobile.hcbezg.cn/Article/9545917.shtml
- http://h5.mobile.hcbezg.cn/Article/6927961.shtml
- http://h5.mobile.cvsifc.cn/Article/85936.shtml
- http://h5.mobile.cvsifc.cn/Article/3592.shtml
- http://h5.mobile.fuvxie.cn/Article/5639533.shtml
- http://h5.mobile.fuvxie.cn/Article/376048.shtml
- http://h5.mobile.fuvxie.cn/Article/7928890.shtml
- http://h5.mobile.hcbezg.cn/Article/8645.shtml
- http://h5.mobile.fuvxie.cn/Article/897843.shtml
- http://h5.mobile.cvsifc.cn/Article/84486.shtml
- http://h5.mobile.fuvxie.cn/Article/7534585.shtml
- http://h5.mobile.cvsifc.cn/Article/87192.shtml
- http://h5.mobile.cvsifc.cn/Article/215446.shtml
- http://h5.mobile.fuvxie.cn/Article/54895.shtml
- http://h5.mobile.cvsifc.cn/Article/384385.shtml
- http://h5.mobile.hcbezg.cn/Article/0415.shtml
- http://h5.mobile.cvsifc.cn/Article/565718.shtml
- http://h5.mobile.fuvxie.cn/Article/4692.shtml
- http://h5.mobile.cvsifc.cn/Article/65968.shtml
- http://h5.mobile.fuvxie.cn/Article/72577.shtml
- http://h5.mobile.cvsifc.cn/Article/120844.shtml
- http://h5.mobile.cvsifc.cn/Article/280258.shtml
- http://h5.mobile.fuvxie.cn/Article/05788.shtml
- http://h5.mobile.cvsifc.cn/Article/2397.shtml
- http://h5.mobile.cvsifc.cn/Article/1229.shtml
- http://h5.mobile.hcbezg.cn/Article/9184.shtml
- http://h5.mobile.cvsifc.cn/Article/7382435.shtml
- http://h5.mobile.fuvxie.cn/Article/2746756.shtml
- http://h5.mobile.hcbezg.cn/Article/791250.shtml
- http://h5.mobile.fuvxie.cn/Article/2052135.shtml
- http://h5.mobile.cvsifc.cn/Article/4195968.shtml
- http://h5.mobile.cvsifc.cn/Article/392943.shtml
- http://h5.mobile.fuvxie.cn/Article/137177.shtml
- http://h5.mobile.cvsifc.cn/Article/187256.shtml
- http://h5.mobile.hcbezg.cn/Article/37600.shtml
- http://h5.mobile.fuvxie.cn/Article/608151.shtml
- http://h5.mobile.cvsifc.cn/Article/9160.shtml
- http://h5.mobile.fuvxie.cn/Article/87067.shtml
- http://h5.mobile.hcbezg.cn/Article/7969.shtml
- http://h5.mobile.cvsifc.cn/Article/3679.shtml
- http://h5.mobile.fuvxie.cn/Article/6874.shtml
- http://h5.mobile.fuvxie.cn/Article/6540.shtml
- http://h5.mobile.hcbezg.cn/Article/6541914.shtml
- http://h5.mobile.fuvxie.cn/Article/134060.shtml
- http://h5.mobile.cvsifc.cn/Article/1789.shtml
- http://h5.mobile.hcbezg.cn/Article/684730.shtml
- http://h5.mobile.fuvxie.cn/Article/11584.shtml
- http://h5.mobile.fuvxie.cn/Article/462815.shtml
- http://h5.mobile.fuvxie.cn/Article/855355.shtml
- http://h5.mobile.fuvxie.cn/Article/820212.shtml
- http://h5.mobile.fuvxie.cn/Article/8147271.shtml
- http://h5.mobile.cvsifc.cn/Article/5289632.shtml
- http://h5.mobile.hcbezg.cn/Article/1308485.shtml

## 项目结构

```
webindex/
├── data/                                 # 数据存储目录，所有链接与元数据均存放于此
│   ├── batches/                          # 批次导入原始记录，按批次编号分文件存储
│   │   ├── batch_51.json                 # 第 51 批次数据（示例）
│   │   └── batch_52.json                 # 第 52 批次数据（当前批次）
│   ├── cache/                            # HTTP 元数据缓存，避免重复请求外部资源
│   │   ├── headers/                      # 按 URL 哈希分片存储响应头
│   │   └── etags/                        # 存储 ETag 与 Last-Modified 用于增量检测
│   ├── tags/                             # 标签索引，每个标签对应一个链接 ID 列表
│   │   ├── kubernetes.json               # 标签为 kubernetes 的链接索引
│   │   └── rust.json                     # 标签为 rust 的链接索引
│   └── index.json                        # 全局链接索引，包含所有条目的摘要信息
├── src/                                  # 核心源代码目录
│   ├── core/                             # 核心模块
│   │   ├── importer.py                   # 导入器，负责解析外部数据并写入索引
│   │   ├── metadata.py                   # 元数据提取器，封装 HTTP HEAD 请求逻辑
│   │   └── checker.py                    # 链接检查器，执行可达性检测与状态更新
│   ├── render/                           # 渲染模块
│   │   ├── static.py                     # 静态站点生成器，将数据渲染为 HTML
│   │   └── templates/                    # Jinja2 模板目录，控制输出页面外观
│   │       ├── base.html                 # 基础布局模板
│   │       └── index.html                # 首页模板
│   ├── cli/                              # 命令行接口
│   │   ├── main.py                       # CLI 入口，注册所有子命令
│   │   └── commands/                     # 子命令实现
│   │       ├── import_cmd.py             # import 命令
│   │       ├── build_cmd.py              # build 命令
│   │       └── check_cmd.py              # check 命令
│   └── utils/                            # 工具函数
│       ├── url_parser.py                 # URL 解析与规范化工具
│       └── file_utils.py                 # 文件读写与路径处理
├── scripts/                              # 运维与辅助脚本
│   ├── import_batch.py                   # 批量导入快捷脚本
│   └── build_static.py                   # 静态构建快捷脚本
├── tests/                                # 单元测试与集成测试
│   ├── test_importer.py                  # 导入器测试用例
│   └── test_metadata.py                  # 元数据提取器测试用例
├── docs/                                 # 文档目录
│   ├── getting-started.md                # 入门指南
│   ├── import-workflow.md                # 导入与更新工作流
│   └── configuration.md                  # 配置参考
├── requirements.txt                      # Python 依赖列表
├── Makefile                              # 常用任务快捷命令（make install / make test）
└── README.md                             # 本文件
```

## 贡献指南

我们欢迎任何形式的贡献，包括但不限于功能建议、代码提交、文档改进与问题反馈。请遵循以下步骤参与项目。

第一步，查阅问题列表与项目看板。访问 GitHub Issues 页面查看当前已知问题与待办功能，选择未被认领的任务或提出新的改进建议。重大变更建议先创建 Issue 进行讨论，避免无效工作。

第二步，派生代码仓库并创建特性分支。从主仓库派生副本到个人账户下，克隆至本地后使用 `git checkout -b feature/your-feature-name` 创建新分支。分支命名建议遵循 `feature/`、`fix/`、`docs/` 前缀规范。

第三步，编写代码并确保测试通过。所有新增功能需包含对应的单元测试，运行 `make test` 或 `pytest tests/` 确认全部测试用例通过。代码风格需符合 PEP 8 规范，提交前使用 `black` 与 `isort` 进行格式化。

第四步，提交变更并发起 Pull Request。提交信息应简洁明了，采用 `<类型>: <描述>` 格式（如 `feat: add batch deduplication option`）。PR 描述中需说明变更内容、测试覆盖情况以及相关 Issue 编号。

第五步，接受代码审查与持续集成检查。维护者将审查代码，可能提出修改意见。所有 PR 需通过 CI 流水线（包括 lint 检查、单元测试与构建测试）后方可合并。

## 常见问题

**问：系统是否会自动抓取并存储外部链接的完整页面内容？**

答：不会。WebIndex 只存储 URL 本身以及通过标准 HEAD 请求获取的响应头元数据（如 Content-Type、Last-Modified），不下载或存储任何页面正文内容。系统定位为链接导航与聚合工具，而非爬虫或镜像系统。如需获取页面标题或摘要，用户可自行扩展或集成第三方提取服务。

**问：导入大量链接后，构建静态站点的速度会明显下降吗？**

答：构建性能主要受限于 JSON 数据读取与模板渲染。在 250 条链接规模下，构建时间通常在 2 秒以内。当链接数量超过 10000 条时，建议使用 `--incremental` 增量构建模式，该模式仅重新渲染发生变更的页面部分。若内存不足，可在配置文件中降低 `render_batch_size` 参数值，采用分批渲染策略。

**问：如何定期自动更新失效链接检测结果？**

答：推荐使用 GitHub Actions 或系统 crontab 定时任务。项目提供了 `scripts/check_links.py` 脚本，可配合 `--schedule daily` 参数运行。在 GitHub Actions 中，可配置为每日 UTC 0 点执行，检测结果会以 JSON 报告形式提交至仓库的 `reports/` 目录，或通过配置的 webhook 发送通知。

## 许可证

MIT License

Copyright (c) 2026 WebIndex Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
