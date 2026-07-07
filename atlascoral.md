# WebLink Collective Asset

WebLink Collective Asset 是一个面向技术调研、数据采集和信息归档的开源外链资源汇总工具。该项目面向数据分析师、爬虫开发者、SEO 技术人员以及学术研究者，提供结构化的文章链接索引与分类导航，帮助用户快速定位分散在多个内容源站点上的特定主题文章。项目本身不存储任何文章内容，仅维护 URL 索引与元信息映射关系，可作为上游数据源接入各类 ETL 管道或自动化采集系统。

## 功能概览

- 多源链接统一聚合：将来自不同域名的文章链接纳入同一索引体系，支持跨源检索与去重。

- 文章级元信息提取：通过可配置的解析器，从目标 URL 对应的 HTML 页面中提取标题、发布时间、正文摘要等关键字段。

- 批次化导入机制：支持按批次（当前为第 45/60 批）导入链接清单，便于追踪数据采集进度与版本迭代。

- 链接状态健康检查：内置 HTTP 状态码探测与响应时间监控，自动标记失效或重定向的链接。

- 分类标签系统：允许用户为每个链接添加自定义标签（如「技术文档」「行业报告」「案例研究」），实现多维筛选。

- 数据导出接口：提供 JSON、CSV 和 Markdown 表格三种导出格式，可无缝对接数据分析工具或静态站点生成器。

- 增量更新支持：支持基于时间戳或批次号的增量拉取模式，避免全量重复处理。

## 应用场景

技术调研与竞品分析：调研人员可将本项目作为数据源索引，批量获取特定域名下的文章链接，结合第三方解析服务快速抽取正文内容，用于竞品动态追踪或行业趋势分析。

爬虫任务队列构建：爬虫开发者可直接读取本项目维护的链接列表，将其注入分布式爬虫的任务队列，避免手动收集起始 URL 的重复劳动，尤其适合需要定期抓取多个来源站点的场景。

学术文献与参考资料归档：学术研究者可利用本项目的批次管理能力，按照研究课题或时间范围组织参考文献链接，配合健康检查功能确保引用的在线资源长期可访问。

SEO 外链审计与监控：SEO 人员可借助本项目的链接状态检查和分类标签功能，定期审计外链资源的存活率和响应质量，及时发现并处理失效链接。

## 快速开始

以下命令演示了从克隆代码仓库到启动本地服务的完整流程。

```bash
git clone https://github.com/weblink-collective/asset.git
cd asset
pip install -r requirements.txt
python manage.py migrate
python manage.py load_batch --batch 45 --source ./data/batch_45.json
python manage.py runserver
```

执行完毕后，本地服务默认监听 8000 端口。访问 http://127.0.0.1:8000/api/links 可获取当前批次已导入的链接列表。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，建议使用 pyenv 或 conda 管理版本 |
| Django | 4.2 LTS | Web 框架，用于提供 API 接口和管理后台 |
| SQLite | 3.35 及以上 | 默认数据库，用于开发和测试环境；生产环境可切换至 PostgreSQL |
| requests | 2.31.0 | 用于发送 HTTP 请求进行链接健康检查 |
| beautifulsoup4 | 4.12.0 | HTML 解析库，用于提取文章元信息 |
| lxml | 4.9.0 | 高性能 XML/HTML 解析器，作为 beautifulsoup4 的后端引擎 |
| redis | 7.0 及以上 | 可选依赖，用于缓存链接状态结果以提升性能 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user/quickstart.md | 如何安装、配置和首次运行本项目？ |
| 用户手册 | docs/user/batch-management.md | 如何创建新批次、导入链接以及查看批次状态？ |
| 开发指南 | docs/developer/api-reference.md | API 端点有哪些？请求和响应的数据结构是什么？ |
| 开发指南 | docs/developer/parser-plugin.md | 如何为新的来源站点编写自定义解析器插件？ |
| 运维手册 | docs/ops/health-check.md | 链接健康检查的调度策略和告警规则如何配置？ |
| 运维手册 | docs/ops/deployment.md | 如何在生产环境中使用 PostgreSQL 和 Gunicorn 部署？ |

## 资源列表

- http://wap.mobile.hcbezg.cn/Article/9716.shtml
- http://wap.mobile.hcbezg.cn/Article/4395909.shtml
- http://wap.mobile.cvsifc.cn/Article/9384.shtml
- http://wap.mobile.hcbezg.cn/Article/6944377.shtml
- http://wap.mobile.cvsifc.cn/Article/165142.shtml
- http://wap.mobile.hcbezg.cn/Article/7890033.shtml
- http://wap.mobile.cvsifc.cn/Article/1493112.shtml
- http://wap.mobile.hcbezg.cn/Article/979332.shtml
- http://wap.mobile.cvsifc.cn/Article/0539.shtml
- http://wap.mobile.hcbezg.cn/Article/713733.shtml
- http://wap.mobile.fuvxie.cn/Article/7908.shtml
- http://wap.mobile.cvsifc.cn/Article/1844268.shtml
- http://wap.mobile.cvsifc.cn/Article/698074.shtml
- http://wap.mobile.hcbezg.cn/Article/3920852.shtml
- http://wap.mobile.hcbezg.cn/Article/153248.shtml
- http://wap.mobile.hcbezg.cn/Article/568952.shtml
- http://wap.mobile.fuvxie.cn/Article/1677935.shtml
- http://wap.mobile.cvsifc.cn/Article/2387269.shtml
- http://wap.mobile.cvsifc.cn/Article/967148.shtml
- http://wap.mobile.hcbezg.cn/Article/53156.shtml
- http://wap.mobile.fuvxie.cn/Article/67468.shtml
- http://wap.mobile.cvsifc.cn/Article/8548.shtml
- http://wap.mobile.cvsifc.cn/Article/53717.shtml
- http://wap.mobile.cvsifc.cn/Article/9541489.shtml
- http://wap.mobile.hcbezg.cn/Article/0255.shtml
- http://wap.mobile.hcbezg.cn/Article/63210.shtml
- http://wap.mobile.fuvxie.cn/Article/938860.shtml
- http://wap.mobile.hcbezg.cn/Article/6372644.shtml
- http://wap.mobile.hcbezg.cn/Article/3058.shtml
- http://wap.mobile.cvsifc.cn/Article/90089.shtml
- http://wap.mobile.fuvxie.cn/Article/899095.shtml
- http://wap.mobile.hcbezg.cn/Article/8238273.shtml
- http://wap.mobile.fuvxie.cn/Article/535335.shtml
- http://wap.mobile.fuvxie.cn/Article/7395298.shtml
- http://wap.mobile.cvsifc.cn/Article/84485.shtml
- http://wap.mobile.cvsifc.cn/Article/24373.shtml
- http://wap.mobile.fuvxie.cn/Article/5077.shtml
- http://wap.mobile.fuvxie.cn/Article/4043970.shtml
- http://wap.mobile.fuvxie.cn/Article/1740304.shtml
- http://wap.mobile.cvsifc.cn/Article/7588669.shtml
- http://wap.mobile.hcbezg.cn/Article/94977.shtml
- http://wap.mobile.cvsifc.cn/Article/8300342.shtml
- http://wap.mobile.hcbezg.cn/Article/8990224.shtml
- http://wap.mobile.hcbezg.cn/Article/82530.shtml
- http://wap.mobile.hcbezg.cn/Article/3344612.shtml
- http://wap.mobile.hcbezg.cn/Article/0766394.shtml
- http://wap.mobile.hcbezg.cn/Article/06205.shtml
- http://wap.mobile.cvsifc.cn/Article/0058.shtml
- http://wap.mobile.hcbezg.cn/Article/68724.shtml
- http://wap.mobile.fuvxie.cn/Article/303040.shtml
- http://wap.mobile.fuvxie.cn/Article/0565076.shtml
- http://wap.mobile.fuvxie.cn/Article/27677.shtml
- http://wap.mobile.hcbezg.cn/Article/9891726.shtml
- http://wap.mobile.fuvxie.cn/Article/0471487.shtml
- http://wap.mobile.cvsifc.cn/Article/27678.shtml
- http://wap.mobile.fuvxie.cn/Article/47435.shtml
- http://wap.mobile.hcbezg.cn/Article/76731.shtml
- http://wap.mobile.hcbezg.cn/Article/1954648.shtml
- http://wap.mobile.cvsifc.cn/Article/608767.shtml
- http://wap.mobile.cvsifc.cn/Article/77664.shtml
- http://wap.mobile.fuvxie.cn/Article/2223243.shtml
- http://wap.mobile.cvsifc.cn/Article/2337.shtml
- http://wap.mobile.cvsifc.cn/Article/8340851.shtml
- http://wap.mobile.hcbezg.cn/Article/005982.shtml
- http://wap.mobile.fuvxie.cn/Article/38597.shtml
- http://wap.mobile.fuvxie.cn/Article/41172.shtml
- http://wap.mobile.hcbezg.cn/Article/8963669.shtml
- http://wap.mobile.cvsifc.cn/Article/09123.shtml
- http://wap.mobile.fuvxie.cn/Article/63456.shtml
- http://wap.mobile.cvsifc.cn/Article/1975.shtml
- http://wap.mobile.fuvxie.cn/Article/6248.shtml
- http://wap.mobile.hcbezg.cn/Article/0864482.shtml
- http://wap.mobile.cvsifc.cn/Article/72642.shtml
- http://wap.mobile.fuvxie.cn/Article/2585.shtml
- http://wap.mobile.hcbezg.cn/Article/21375.shtml
- http://wap.mobile.cvsifc.cn/Article/401027.shtml
- http://wap.mobile.hcbezg.cn/Article/6181.shtml
- http://wap.mobile.cvsifc.cn/Article/7353.shtml
- http://wap.mobile.hcbezg.cn/Article/768860.shtml
- http://wap.mobile.hcbezg.cn/Article/1185.shtml
- http://wap.mobile.hcbezg.cn/Article/192122.shtml
- http://wap.mobile.hcbezg.cn/Article/54069.shtml
- http://wap.mobile.fuvxie.cn/Article/8015.shtml
- http://wap.mobile.hcbezg.cn/Article/38504.shtml
- http://wap.mobile.hcbezg.cn/Article/16043.shtml
- http://wap.mobile.cvsifc.cn/Article/125553.shtml
- http://wap.mobile.cvsifc.cn/Article/3024129.shtml
- http://wap.mobile.cvsifc.cn/Article/9138.shtml
- http://wap.mobile.hcbezg.cn/Article/838794.shtml
- http://wap.mobile.hcbezg.cn/Article/232884.shtml
- http://wap.mobile.hcbezg.cn/Article/818404.shtml
- http://wap.mobile.cvsifc.cn/Article/807880.shtml
- http://wap.mobile.cvsifc.cn/Article/5342.shtml
- http://wap.mobile.fuvxie.cn/Article/4392415.shtml
- http://wap.mobile.cvsifc.cn/Article/717551.shtml
- http://wap.mobile.hcbezg.cn/Article/927816.shtml
- http://wap.mobile.cvsifc.cn/Article/89989.shtml
- http://wap.mobile.hcbezg.cn/Article/99409.shtml
- http://wap.mobile.hcbezg.cn/Article/8905101.shtml
- http://wap.mobile.fuvxie.cn/Article/956882.shtml
- http://wap.mobile.fuvxie.cn/Article/85748.shtml
- http://wap.mobile.cvsifc.cn/Article/536702.shtml
- http://wap.mobile.hcbezg.cn/Article/88480.shtml
- http://wap.mobile.fuvxie.cn/Article/3676289.shtml
- http://wap.mobile.fuvxie.cn/Article/623400.shtml
- http://wap.mobile.fuvxie.cn/Article/2579995.shtml
- http://wap.mobile.cvsifc.cn/Article/46802.shtml
- http://wap.mobile.fuvxie.cn/Article/58553.shtml
- http://wap.mobile.cvsifc.cn/Article/44200.shtml
- http://wap.mobile.hcbezg.cn/Article/371318.shtml
- http://wap.mobile.fuvxie.cn/Article/537738.shtml
- http://wap.mobile.hcbezg.cn/Article/34453.shtml
- http://wap.mobile.hcbezg.cn/Article/912004.shtml
- http://wap.mobile.hcbezg.cn/Article/3366026.shtml
- http://wap.mobile.hcbezg.cn/Article/9696990.shtml
- http://wap.mobile.cvsifc.cn/Article/2543.shtml
- http://wap.mobile.fuvxie.cn/Article/51446.shtml
- http://wap.mobile.fuvxie.cn/Article/78263.shtml
- http://wap.mobile.hcbezg.cn/Article/22822.shtml
- http://wap.mobile.hcbezg.cn/Article/17245.shtml
- http://wap.mobile.fuvxie.cn/Article/572918.shtml
- http://wap.mobile.cvsifc.cn/Article/661906.shtml
- http://wap.mobile.hcbezg.cn/Article/4150329.shtml
- http://wap.mobile.hcbezg.cn/Article/7944288.shtml
- http://wap.mobile.fuvxie.cn/Article/7997040.shtml
- http://wap.mobile.cvsifc.cn/Article/6615.shtml
- http://wap.mobile.hcbezg.cn/Article/71934.shtml
- http://wap.mobile.cvsifc.cn/Article/90477.shtml
- http://wap.mobile.cvsifc.cn/Article/43176.shtml
- http://wap.mobile.fuvxie.cn/Article/726221.shtml
- http://wap.mobile.fuvxie.cn/Article/30711.shtml
- http://wap.mobile.cvsifc.cn/Article/0132.shtml
- http://wap.mobile.cvsifc.cn/Article/80197.shtml
- http://wap.mobile.cvsifc.cn/Article/1715.shtml
- http://wap.mobile.hcbezg.cn/Article/245724.shtml
- http://wap.mobile.cvsifc.cn/Article/8305.shtml
- http://wap.mobile.fuvxie.cn/Article/4685.shtml
- http://wap.mobile.fuvxie.cn/Article/8191.shtml
- http://wap.mobile.cvsifc.cn/Article/7526.shtml
- http://wap.mobile.cvsifc.cn/Article/62654.shtml
- http://wap.mobile.hcbezg.cn/Article/2428156.shtml
- http://wap.mobile.hcbezg.cn/Article/8676911.shtml
- http://wap.mobile.fuvxie.cn/Article/49524.shtml
- http://wap.mobile.cvsifc.cn/Article/72293.shtml
- http://wap.mobile.hcbezg.cn/Article/0416.shtml
- http://wap.mobile.hcbezg.cn/Article/9374842.shtml
- http://wap.mobile.fuvxie.cn/Article/7649.shtml
- http://wap.mobile.cvsifc.cn/Article/078081.shtml
- http://wap.mobile.fuvxie.cn/Article/477432.shtml
- http://wap.mobile.cvsifc.cn/Article/074436.shtml
- http://wap.mobile.fuvxie.cn/Article/1903373.shtml
- http://wap.mobile.cvsifc.cn/Article/44248.shtml
- http://wap.mobile.fuvxie.cn/Article/78868.shtml
- http://wap.mobile.fuvxie.cn/Article/7954361.shtml
- http://wap.mobile.cvsifc.cn/Article/4379.shtml
- http://wap.mobile.hcbezg.cn/Article/4567248.shtml
- http://wap.mobile.hcbezg.cn/Article/9932.shtml
- http://wap.mobile.hcbezg.cn/Article/1019.shtml
- http://wap.mobile.fuvxie.cn/Article/3329823.shtml
- http://wap.mobile.hcbezg.cn/Article/92510.shtml
- http://wap.mobile.hcbezg.cn/Article/66561.shtml
- http://wap.mobile.hcbezg.cn/Article/11498.shtml
- http://wap.mobile.fuvxie.cn/Article/6523.shtml
- http://wap.mobile.fuvxie.cn/Article/1383.shtml
- http://wap.mobile.fuvxie.cn/Article/27776.shtml
- http://wap.mobile.hcbezg.cn/Article/701005.shtml
- http://wap.mobile.hcbezg.cn/Article/8379047.shtml
- http://wap.mobile.fuvxie.cn/Article/0706896.shtml
- http://wap.mobile.fuvxie.cn/Article/71431.shtml
- http://wap.mobile.cvsifc.cn/Article/73660.shtml
- http://wap.mobile.hcbezg.cn/Article/55392.shtml
- http://wap.mobile.hcbezg.cn/Article/425614.shtml
- http://wap.mobile.hcbezg.cn/Article/96097.shtml
- http://wap.mobile.fuvxie.cn/Article/1808.shtml
- http://wap.mobile.cvsifc.cn/Article/7525358.shtml
- http://wap.mobile.cvsifc.cn/Article/38960.shtml
- http://wap.mobile.fuvxie.cn/Article/0679.shtml
- http://wap.mobile.fuvxie.cn/Article/8046873.shtml
- http://wap.mobile.fuvxie.cn/Article/0093408.shtml
- http://wap.mobile.hcbezg.cn/Article/26938.shtml
- http://wap.mobile.fuvxie.cn/Article/65123.shtml
- http://wap.mobile.hcbezg.cn/Article/701790.shtml
- http://wap.mobile.cvsifc.cn/Article/1398.shtml
- http://wap.mobile.hcbezg.cn/Article/901213.shtml
- http://wap.mobile.fuvxie.cn/Article/477488.shtml
- http://wap.mobile.cvsifc.cn/Article/45438.shtml
- http://wap.mobile.cvsifc.cn/Article/32223.shtml
- http://wap.mobile.fuvxie.cn/Article/0215.shtml
- http://wap.mobile.fuvxie.cn/Article/1038.shtml
- http://wap.mobile.fuvxie.cn/Article/10495.shtml
- http://wap.mobile.fuvxie.cn/Article/844027.shtml
- http://wap.mobile.fuvxie.cn/Article/1573.shtml
- http://wap.mobile.hcbezg.cn/Article/460231.shtml
- http://wap.mobile.hcbezg.cn/Article/39642.shtml
- http://wap.mobile.hcbezg.cn/Article/6879.shtml
- http://wap.mobile.cvsifc.cn/Article/7700682.shtml
- http://wap.mobile.hcbezg.cn/Article/2797689.shtml
- http://wap.mobile.fuvxie.cn/Article/649642.shtml
- http://wap.mobile.fuvxie.cn/Article/91615.shtml
- http://wap.mobile.fuvxie.cn/Article/7468.shtml
- http://wap.mobile.hcbezg.cn/Article/6012553.shtml
- http://wap.mobile.cvsifc.cn/Article/0135208.shtml
- http://wap.mobile.cvsifc.cn/Article/6327626.shtml
- http://wap.mobile.fuvxie.cn/Article/8605.shtml
- http://wap.mobile.hcbezg.cn/Article/9349.shtml
- http://wap.mobile.fuvxie.cn/Article/3404187.shtml
- http://wap.mobile.hcbezg.cn/Article/676146.shtml
- http://wap.mobile.fuvxie.cn/Article/886813.shtml
- http://wap.mobile.hcbezg.cn/Article/1741329.shtml
- http://wap.mobile.fuvxie.cn/Article/34168.shtml
- http://wap.mobile.fuvxie.cn/Article/759539.shtml
- http://wap.mobile.hcbezg.cn/Article/932718.shtml
- http://wap.mobile.hcbezg.cn/Article/4843.shtml
- http://wap.mobile.hcbezg.cn/Article/4037737.shtml
- http://wap.mobile.cvsifc.cn/Article/3271010.shtml
- http://wap.mobile.hcbezg.cn/Article/28013.shtml
- http://wap.mobile.hcbezg.cn/Article/9817.shtml
- http://wap.mobile.hcbezg.cn/Article/3134593.shtml
- http://wap.mobile.hcbezg.cn/Article/2876881.shtml
- http://wap.mobile.cvsifc.cn/Article/034182.shtml
- http://wap.mobile.hcbezg.cn/Article/637822.shtml
- http://wap.mobile.fuvxie.cn/Article/177018.shtml
- http://wap.mobile.hcbezg.cn/Article/3905921.shtml
- http://wap.mobile.hcbezg.cn/Article/75989.shtml
- http://wap.mobile.fuvxie.cn/Article/80349.shtml
- http://wap.mobile.cvsifc.cn/Article/9638.shtml
- http://wap.mobile.fuvxie.cn/Article/622951.shtml
- http://wap.mobile.cvsifc.cn/Article/70033.shtml
- http://wap.mobile.fuvxie.cn/Article/31304.shtml
- http://wap.mobile.cvsifc.cn/Article/513319.shtml
- http://wap.mobile.hcbezg.cn/Article/725497.shtml
- http://wap.mobile.hcbezg.cn/Article/8543.shtml
- http://wap.mobile.cvsifc.cn/Article/7052755.shtml
- http://wap.mobile.hcbezg.cn/Article/541532.shtml
- http://wap.mobile.cvsifc.cn/Article/61252.shtml
- http://wap.mobile.fuvxie.cn/Article/54044.shtml
- http://wap.mobile.hcbezg.cn/Article/613870.shtml
- http://wap.mobile.cvsifc.cn/Article/98284.shtml
- http://wap.mobile.fuvxie.cn/Article/3880367.shtml
- http://wap.mobile.fuvxie.cn/Article/590245.shtml
- http://wap.mobile.hcbezg.cn/Article/504165.shtml
- http://wap.mobile.hcbezg.cn/Article/2654.shtml
- http://wap.mobile.hcbezg.cn/Article/530268.shtml
- http://wap.mobile.hcbezg.cn/Article/766512.shtml
- http://wap.mobile.hcbezg.cn/Article/5115129.shtml
- http://wap.mobile.hcbezg.cn/Article/12423.shtml
- http://wap.mobile.cvsifc.cn/Article/7382.shtml
- http://wap.mobile.hcbezg.cn/Article/58243.shtml
- http://wap.mobile.hcbezg.cn/Article/31834.shtml
- http://wap.mobile.hcbezg.cn/Article/3681035.shtml

## 项目结构

项目采用 Django 标准应用布局，同时整合了独立的解析器模块和任务调度脚本。以下为主要目录与文件的组织方式。

```
asset/
├── manage.py                         # Django 项目管理入口
├── requirements.txt                  # Python 依赖清单
├── config/                           # 项目全局配置目录
│   ├── settings.py                   # 基础配置（数据库、中间件、INSTALLED_APPS）
│   ├── settings_dev.py               # 开发环境配置（开启调试、SQLite）
│   └── settings_prod.py              # 生产环境配置（PostgreSQL、缓存、日志）
├── apps/                             # 所有自定义应用
│   ├── links/                        # 链接索引核心应用
│   │   ├── models.py                 # Link, Batch, Tag 数据模型
│   │   ├── admin.py                  # Django 管理后台注册
│   │   ├── serializers.py            # DRF 序列化器
│   │   └── views.py                  # API 视图（列表、详情、健康检查）
│   ├── parsers/                      # 解析器插件目录
│   │   ├── base.py                   # 抽象解析器基类
│   │   ├── registry.py               # 解析器注册中心
│   │   ├── hcbezg.py                 # 针对 hcbezg.cn 域名的解析器实现
│   │   ├── cvsifc.py                 # 针对 cvsifc.cn 域名的解析器实现
│   │   └── fuvxie.py                 # 针对 fuvxie.cn 域名的解析器实现
│   └── health/                       # 健康检查独立模块
│       ├── checker.py                # HTTP 状态码与响应时间探测
│       ├── scheduler.py              # 基于 APScheduler 的定时任务配置
│       └── cache.py                  # Redis 缓存操作封装
├── scripts/                          # 运维与数据导入脚本
│   ├── load_batch.py                 # 批次导入命令行工具
│   ├── export_links.py               # 链接数据导出（JSON/CSV/Markdown）
│   └── run_health_check.py           # 手动触发全量健康检查
├── data/                             # 数据文件目录（不纳入版本控制）
│   ├── batch_45.json                 # 第 45 批原始链接清单
│   └── batch_46.json                 # 下一批次待导入数据
├── docs/                             # 文档源码
│   ├── user/                         # 用户手册
│   ├── developer/                    # 开发指南
│   └── ops/                          # 运维手册
└── tests/                            # 单元测试与集成测试
    ├── test_models.py
    ├── test_parsers.py
    └── test_health.py
```

## 贡献指南

欢迎外部贡献者参与本项目开发。请遵循以下步骤提交代码或文档。

1. 在 GitHub 上 fork 本仓库至个人账号，然后 clone 到本地开发环境。建议使用 Python 3.10 及以上版本，并创建独立的虚拟环境。

2. 在本地运行 `python manage.py test` 确保现有测试全部通过。若新增功能或修复缺陷，请在 `tests/` 目录下补充对应的测试用例。

3. 提交代码前，请使用 `black` 和 `isort` 对 Python 代码进行格式化，并使用 `flake8` 进行静态检查。配置文件位于项目根目录的 `.flake8` 和 `.isort.cfg`。

4. 若新增解析器插件，需在 `apps/parsers/registry.py` 中注册，并提供对应的单元测试。解析器必须实现 `parse(url)` 方法，返回包含 `title`、`published_at` 和 `summary` 字段的字典。

5. 提交 Pull Request 时，请清晰描述变更内容、测试覆盖情况以及是否影响现有 API 兼容性。PR 标题请遵循 `[类型] 简短描述` 的格式，类型包括 `feat`、`fix`、`docs`、`refactor`。

## 常见问题

Q: 导入链接时提示「批次号已存在」，如何解决？

A: 每个批次号只能导入一次，这是为了防止重复处理。如需重新导入，请使用 `--force` 参数覆盖已有批次，或在数据库中手动删除该批次记录后再执行导入。生产环境建议先备份数据。

Q: 健康检查显示大量链接超时，是什么原因？

A: 超时可能由目标服务器响应缓慢、网络波动或链接已失效引起。项目默认超时时间为 10 秒，可通过 `HEALTH_CHECK_TIMEOUT` 环境变量调整。建议先手动访问几个被标记为超时的链接，确认是否仍可正常打开。若为大量失效链接，可考虑使用 `--skip-failed` 选项跳过检查。

Q: 如何为新的来源站点编写解析器？

A: 在 `apps/parsers/` 目录下新建 Python 文件，继承 `BaseParser` 类并实现 `parse` 方法。然后在 `registry.py` 中通过 `register_parser` 装饰器将该解析器与对应的域名绑定。具体可参考 `hcbezg.py` 中的实现示例。解析器注册后无需重启服务，Django 会在启动时自动加载。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
