# LinkHub CMS

LinkHub CMS 是一个面向技术内容聚合与外部链接管理的开源发布系统，专为需要批量维护、分类展示和快速检索大量外链资源的团队设计。系统定位于中小型技术门户、个人知识库站长的日常运维工具，解决人工维护外链列表时存在的重复劳动、格式混乱与可追溯性缺失问题。本项目提供从原始链接导入、自动分类标记、多维度筛选到前端展示的完整链路方案，支持十万级链接数据的稳定管理。目标用户包括开源社区文档维护者、技术博客运营人员、企业内部知识库管理员以及需要进行大规模外链审计的安全研究人员。

## 功能概览

批量链接导入与自动清洗：支持从文本文件、CSV 表格及数据库导出结果中批量拉取 URL，自动识别协议头与域名主体，剔除无效空白与重复条目，并生成导入日志供后续审计。

多级标签分类系统：允许管理员自定义分类标签树，可为每条链接标记所属技术领域、内容类型、来源站点、时效性等级等维度，支持标签继承与批量打标。

链接状态健康检查：内置定时巡检任务，通过 HTTP 请求检测目标资源可达性，记录响应码、响应时间与内容哈希变化，对失效或重定向链接发出告警。

全文检索与高级筛选：基于倒排索引提供对 URL、标题、摘要、标签、来源域名的快速检索，支持多条件组合筛选，结果可按更新时间、访问热度或自定义权重排序。

前端响应式展示模板：提供两套默认主题（文档风格与门户风格），自适应桌面与移动设备，支持暗色模式，列表视图与卡片视图一键切换。

数据导入导出标准接口：支持 JSON、YAML、Markdown 表格、CSV 四种格式的导入导出，便于与其他系统（如静态站点生成器、CMS、监控平台）对接。

操作审计与版本回溯：记录所有增删改操作的管理员身份与时间戳，支持回滚至任意历史版本，确保链接库变更可追溯。

## 应用场景

技术文档站点的外部参考资料管理：开源项目文档中常需引用大量第三方规范、教程、工具站与 API 参考，LinkHub CMS 可作为独立子服务运行，文档维护者通过后台批量更新链接状态，前端通过 iframe 或 JSONP 嵌入文档页，避免频繁修改文档源文件。

安全研究团队的威胁情报源聚合：安全团队每日需跟进数十个漏洞公告、威胁博客与补丁发布站点，利用本系统的健康检查与标签分类功能，可快速筛选出近期活跃的威胁情报源，并通过导出接口将链接列表同步至 SIEM 或威胁情报平台。

企业知识库的外部资源引用规范管理：大型企业知识库中常散落大量外部链接，存在过期或指向竞品的问题。LinkHub CMS 可定期扫描知识库导出的链接清单，生成失效报告并自动标记风险等级，辅助知识库管理员进行合规审查。

个人技术博客的友情链接与阅读清单维护：独立博主可使用该系统管理博客侧边栏的友情链接、每月技术阅读清单及工具推荐列表，通过前端 API 动态渲染，无需每次修改博客主题模板。

批量资源迁移前的链接审计：当站点迁移或域名更换时，需批量检查所有外部链接是否仍有效、是否需要替换为新的镜像地址。本系统提供链接批量替换与重定向检测功能，辅助迁移决策。

## 快速开始

以下步骤指导您在 Linux 服务器或本地开发环境中完成 LinkHub CMS 的部署与启动。

```bash
# 克隆代码仓库
git clone https://github.com/linkhub/linkhub-cms.git
cd linkhub-cms

# 安装项目依赖（使用 pip 与 npm）
pip install -r requirements.txt
npm install --prefix frontend

# 初始化数据库与默认配置
python manage.py db init
python manage.py db migrate
python manage.py db upgrade
python manage.py init_data --sample-links=100

# 启动后端服务（开发模式）
python manage.py runserver --host=0.0.0.0 --port=8000

# 另开终端启动前端开发服务器
npm run dev --prefix frontend
```

生产环境部署请参考 `docs/deployment.md` 中的 uWSGI + Nginx 配置示例。

## 安装要求

系统运行所需依赖及环境要求如下表所列，请确保部署前全部满足。

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.9 ~ 3.11 | 后端运行环境，推荐使用 pyenv 或 conda 管理版本 |
| Node.js | 18.x LTS | 前端构建与开发服务器依赖，需包含 npm 或 yarn |
| PostgreSQL | 14.x 及以上 | 主数据库，存储链接元数据、标签、审计日志，需启用 pg_trgm 扩展以支持中文模糊检索 |
| Redis | 6.x 及以上 | 缓存与任务队列后端，用于健康检查任务的分布式锁与结果缓存 |
| Nginx | 1.20 及以上 | 生产环境推荐反向代理服务器，用于静态文件服务与负载均衡 |
| 系统内存 | >= 2GB（推荐 4GB） | 保证 Python 进程与前端构建工具同时运行时的稳定性 |
| 磁盘空间 | >= 10GB | 用于存储导入的原始数据文件、日志及 SQLite 备份（若使用 SQLite 替代 PostgreSQL） |

## 文档导航

项目文档按用户角色与使用层面划分，下表列出各模块入口及其覆盖的问题范围。

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 管理员部署 | `docs/deployment.md` | 如何配置生产环境数据库连接、设置 Nginx 反向代理、启用 HTTPS、调整 uWSGI 进程数 |
| 后台操作指南 | `docs/admin/operations.md` | 如何批量导入链接、如何创建标签树、如何配置健康检查策略、如何导出审计报告 |
| API 开发参考 | `docs/api/endpoints.md` | 所有 RESTful API 的请求参数与响应结构说明，包括认证方式、分页格式、错误码定义 |
| 前端组件文档 | `docs/frontend/components.md` | 列表组件、筛选面板、图表卡片的使用方法，以及如何自定义主题样式 |

## 资源列表

- http://www.mobile.hcbezg.cn/Article/397632.shtml
- http://www.mobile.cvsifc.cn/Article/5574172.shtml
- http://www.mobile.cvsifc.cn/Article/1862.shtml
- http://www.mobile.cvsifc.cn/Article/069021.shtml
- http://www.mobile.fuvxie.cn/Article/15587.shtml
- http://www.mobile.cvsifc.cn/Article/002716.shtml
- http://www.mobile.hcbezg.cn/Article/542631.shtml
- http://www.mobile.hcbezg.cn/Article/808134.shtml
- http://www.mobile.fuvxie.cn/Article/027831.shtml
- http://www.mobile.cvsifc.cn/Article/1277370.shtml
- http://www.mobile.fuvxie.cn/Article/6299.shtml
- http://www.mobile.cvsifc.cn/Article/617721.shtml
- http://www.mobile.hcbezg.cn/Article/6404.shtml
- http://www.mobile.cvsifc.cn/Article/52736.shtml
- http://www.mobile.hcbezg.cn/Article/7505.shtml
- http://www.mobile.fuvxie.cn/Article/7659.shtml
- http://www.mobile.fuvxie.cn/Article/6126.shtml
- http://www.mobile.cvsifc.cn/Article/6384.shtml
- http://www.mobile.cvsifc.cn/Article/8191488.shtml
- http://www.mobile.fuvxie.cn/Article/3448.shtml
- http://www.mobile.hcbezg.cn/Article/911483.shtml
- http://www.mobile.hcbezg.cn/Article/1133.shtml
- http://www.mobile.fuvxie.cn/Article/471889.shtml
- http://www.mobile.cvsifc.cn/Article/210261.shtml
- http://www.mobile.hcbezg.cn/Article/177630.shtml
- http://www.mobile.hcbezg.cn/Article/8071.shtml
- http://www.mobile.fuvxie.cn/Article/684321.shtml
- http://www.mobile.fuvxie.cn/Article/303014.shtml
- http://www.mobile.cvsifc.cn/Article/0601137.shtml
- http://www.mobile.cvsifc.cn/Article/7266588.shtml
- http://www.mobile.cvsifc.cn/Article/4656712.shtml
- http://www.mobile.fuvxie.cn/Article/8982.shtml
- http://www.mobile.fuvxie.cn/Article/643097.shtml
- http://www.mobile.cvsifc.cn/Article/0957474.shtml
- http://www.mobile.hcbezg.cn/Article/39094.shtml
- http://www.mobile.fuvxie.cn/Article/542285.shtml
- http://www.mobile.hcbezg.cn/Article/5912039.shtml
- http://www.mobile.hcbezg.cn/Article/4773.shtml
- http://www.mobile.fuvxie.cn/Article/288166.shtml
- http://www.mobile.cvsifc.cn/Article/60361.shtml
- http://www.mobile.hcbezg.cn/Article/82829.shtml
- http://www.mobile.hcbezg.cn/Article/0672.shtml
- http://www.mobile.cvsifc.cn/Article/816150.shtml
- http://www.mobile.cvsifc.cn/Article/9166.shtml
- http://www.mobile.hcbezg.cn/Article/16699.shtml
- http://www.mobile.hcbezg.cn/Article/8699.shtml
- http://www.mobile.cvsifc.cn/Article/1437595.shtml
- http://www.mobile.cvsifc.cn/Article/7782.shtml
- http://www.mobile.cvsifc.cn/Article/263152.shtml
- http://www.mobile.cvsifc.cn/Article/0667.shtml
- http://www.mobile.fuvxie.cn/Article/461516.shtml
- http://www.mobile.cvsifc.cn/Article/05937.shtml
- http://www.mobile.fuvxie.cn/Article/9908235.shtml
- http://www.mobile.hcbezg.cn/Article/53800.shtml
- http://www.mobile.hcbezg.cn/Article/91474.shtml
- http://www.mobile.cvsifc.cn/Article/83972.shtml
- http://www.mobile.cvsifc.cn/Article/8947417.shtml
- http://www.mobile.fuvxie.cn/Article/9702482.shtml
- http://www.mobile.cvsifc.cn/Article/8509.shtml
- http://www.mobile.fuvxie.cn/Article/0454.shtml
- http://www.mobile.cvsifc.cn/Article/5013.shtml
- http://www.mobile.cvsifc.cn/Article/29427.shtml
- http://www.mobile.fuvxie.cn/Article/8946.shtml
- http://www.mobile.fuvxie.cn/Article/33673.shtml
- http://www.mobile.hcbezg.cn/Article/4291232.shtml
- http://www.mobile.fuvxie.cn/Article/132265.shtml
- http://www.mobile.fuvxie.cn/Article/9621.shtml
- http://www.mobile.hcbezg.cn/Article/960785.shtml
- http://www.mobile.hcbezg.cn/Article/679924.shtml
- http://www.mobile.fuvxie.cn/Article/10408.shtml
- http://www.mobile.fuvxie.cn/Article/474654.shtml
- http://www.mobile.fuvxie.cn/Article/7837.shtml
- http://www.mobile.fuvxie.cn/Article/5235144.shtml
- http://www.mobile.hcbezg.cn/Article/84713.shtml
- http://www.mobile.hcbezg.cn/Article/176384.shtml
- http://www.mobile.hcbezg.cn/Article/14851.shtml
- http://www.mobile.hcbezg.cn/Article/9832.shtml
- http://www.mobile.cvsifc.cn/Article/3783.shtml
- http://www.mobile.hcbezg.cn/Article/9136.shtml
- http://www.mobile.fuvxie.cn/Article/105590.shtml
- http://www.mobile.cvsifc.cn/Article/861125.shtml
- http://www.mobile.cvsifc.cn/Article/6468.shtml
- http://www.mobile.fuvxie.cn/Article/9735531.shtml
- http://www.mobile.cvsifc.cn/Article/94870.shtml
- http://www.mobile.hcbezg.cn/Article/22017.shtml
- http://www.mobile.cvsifc.cn/Article/06789.shtml
- http://www.mobile.cvsifc.cn/Article/098568.shtml
- http://www.mobile.cvsifc.cn/Article/251230.shtml
- http://www.mobile.cvsifc.cn/Article/44166.shtml
- http://www.mobile.fuvxie.cn/Article/261512.shtml
- http://www.mobile.cvsifc.cn/Article/83362.shtml
- http://www.mobile.cvsifc.cn/Article/1420618.shtml
- http://www.mobile.fuvxie.cn/Article/412198.shtml
- http://www.mobile.fuvxie.cn/Article/62453.shtml
- http://www.mobile.hcbezg.cn/Article/7871354.shtml
- http://www.mobile.cvsifc.cn/Article/0361112.shtml
- http://www.mobile.cvsifc.cn/Article/0939.shtml
- http://www.mobile.hcbezg.cn/Article/2004942.shtml
- http://www.mobile.cvsifc.cn/Article/9946639.shtml
- http://www.mobile.cvsifc.cn/Article/62430.shtml
- http://www.mobile.hcbezg.cn/Article/0971093.shtml
- http://www.mobile.cvsifc.cn/Article/41776.shtml
- http://www.mobile.hcbezg.cn/Article/1235.shtml
- http://www.mobile.hcbezg.cn/Article/4509.shtml
- http://www.mobile.fuvxie.cn/Article/7287495.shtml
- http://www.mobile.cvsifc.cn/Article/6964966.shtml
- http://www.mobile.fuvxie.cn/Article/58488.shtml
- http://www.mobile.fuvxie.cn/Article/6817210.shtml
- http://www.mobile.cvsifc.cn/Article/76490.shtml
- http://www.mobile.hcbezg.cn/Article/74677.shtml
- http://www.mobile.fuvxie.cn/Article/2732.shtml
- http://www.mobile.hcbezg.cn/Article/92019.shtml
- http://www.mobile.cvsifc.cn/Article/0180.shtml
- http://www.mobile.fuvxie.cn/Article/368634.shtml
- http://www.mobile.fuvxie.cn/Article/05714.shtml
- http://www.mobile.fuvxie.cn/Article/825542.shtml
- http://www.mobile.fuvxie.cn/Article/1373.shtml
- http://www.mobile.fuvxie.cn/Article/1167.shtml
- http://www.mobile.cvsifc.cn/Article/977876.shtml
- http://www.mobile.cvsifc.cn/Article/7816.shtml
- http://www.mobile.cvsifc.cn/Article/8831633.shtml
- http://www.mobile.hcbezg.cn/Article/17925.shtml
- http://www.mobile.fuvxie.cn/Article/198762.shtml
- http://www.mobile.fuvxie.cn/Article/8744447.shtml
- http://www.mobile.hcbezg.cn/Article/997415.shtml
- http://www.mobile.cvsifc.cn/Article/943982.shtml
- http://www.mobile.fuvxie.cn/Article/21444.shtml
- http://www.mobile.hcbezg.cn/Article/728966.shtml
- http://www.mobile.cvsifc.cn/Article/6311.shtml
- http://www.mobile.cvsifc.cn/Article/38495.shtml
- http://www.mobile.cvsifc.cn/Article/5732.shtml
- http://www.mobile.fuvxie.cn/Article/7983.shtml
- http://www.mobile.hcbezg.cn/Article/82002.shtml
- http://www.mobile.cvsifc.cn/Article/25212.shtml
- http://www.mobile.hcbezg.cn/Article/25277.shtml
- http://www.mobile.fuvxie.cn/Article/623399.shtml
- http://www.mobile.cvsifc.cn/Article/272460.shtml
- http://www.mobile.cvsifc.cn/Article/7236392.shtml
- http://www.mobile.hcbezg.cn/Article/867569.shtml
- http://www.mobile.cvsifc.cn/Article/078860.shtml
- http://www.mobile.hcbezg.cn/Article/654235.shtml
- http://www.mobile.fuvxie.cn/Article/024121.shtml
- http://www.mobile.fuvxie.cn/Article/31789.shtml
- http://www.mobile.fuvxie.cn/Article/9485834.shtml
- http://www.mobile.hcbezg.cn/Article/1015181.shtml
- http://www.mobile.cvsifc.cn/Article/3721171.shtml
- http://www.mobile.hcbezg.cn/Article/9148.shtml
- http://www.mobile.hcbezg.cn/Article/82308.shtml
- http://www.mobile.cvsifc.cn/Article/6587010.shtml
- http://www.mobile.cvsifc.cn/Article/79098.shtml
- http://www.mobile.fuvxie.cn/Article/61206.shtml
- http://www.mobile.cvsifc.cn/Article/6744.shtml
- http://www.mobile.cvsifc.cn/Article/3010974.shtml
- http://www.mobile.fuvxie.cn/Article/53968.shtml
- http://www.mobile.cvsifc.cn/Article/835066.shtml
- http://www.mobile.hcbezg.cn/Article/1829707.shtml
- http://www.mobile.cvsifc.cn/Article/22937.shtml
- http://www.mobile.fuvxie.cn/Article/7331.shtml
- http://www.mobile.fuvxie.cn/Article/90704.shtml
- http://www.mobile.cvsifc.cn/Article/5607.shtml
- http://www.mobile.fuvxie.cn/Article/97835.shtml
- http://www.mobile.fuvxie.cn/Article/1033757.shtml
- http://www.mobile.cvsifc.cn/Article/4168.shtml
- http://www.mobile.hcbezg.cn/Article/9615567.shtml
- http://www.mobile.fuvxie.cn/Article/3118338.shtml
- http://www.mobile.fuvxie.cn/Article/519486.shtml
- http://www.mobile.hcbezg.cn/Article/2178939.shtml
- http://www.mobile.fuvxie.cn/Article/6304567.shtml
- http://www.mobile.cvsifc.cn/Article/3591025.shtml
- http://www.mobile.hcbezg.cn/Article/12769.shtml
- http://www.mobile.cvsifc.cn/Article/2997387.shtml
- http://www.mobile.cvsifc.cn/Article/683346.shtml
- http://www.mobile.hcbezg.cn/Article/821657.shtml
- http://www.mobile.cvsifc.cn/Article/218640.shtml
- http://www.mobile.hcbezg.cn/Article/3190.shtml
- http://www.mobile.hcbezg.cn/Article/010414.shtml
- http://www.mobile.fuvxie.cn/Article/1153028.shtml
- http://www.mobile.cvsifc.cn/Article/28480.shtml
- http://www.mobile.hcbezg.cn/Article/2296040.shtml
- http://www.mobile.cvsifc.cn/Article/6625034.shtml
- http://www.mobile.hcbezg.cn/Article/798627.shtml
- http://www.mobile.fuvxie.cn/Article/3889.shtml
- http://www.mobile.hcbezg.cn/Article/080678.shtml
- http://www.mobile.hcbezg.cn/Article/7059.shtml
- http://www.mobile.hcbezg.cn/Article/3102953.shtml
- http://www.mobile.hcbezg.cn/Article/999325.shtml
- http://www.mobile.fuvxie.cn/Article/897944.shtml
- http://www.mobile.fuvxie.cn/Article/313787.shtml
- http://www.mobile.fuvxie.cn/Article/845359.shtml
- http://www.mobile.fuvxie.cn/Article/312251.shtml
- http://www.mobile.fuvxie.cn/Article/73744.shtml
- http://www.mobile.hcbezg.cn/Article/4067.shtml
- http://www.mobile.fuvxie.cn/Article/1684.shtml
- http://www.mobile.fuvxie.cn/Article/5940.shtml
- http://www.mobile.hcbezg.cn/Article/8641.shtml
- http://www.mobile.cvsifc.cn/Article/8360429.shtml
- http://www.mobile.cvsifc.cn/Article/91700.shtml
- http://www.mobile.fuvxie.cn/Article/284542.shtml
- http://www.mobile.hcbezg.cn/Article/9718.shtml
- http://www.mobile.hcbezg.cn/Article/305306.shtml
- http://www.mobile.fuvxie.cn/Article/0225.shtml
- http://www.mobile.hcbezg.cn/Article/53012.shtml
- http://www.mobile.hcbezg.cn/Article/1463.shtml
- http://www.mobile.fuvxie.cn/Article/18186.shtml
- http://www.mobile.hcbezg.cn/Article/1671736.shtml
- http://www.mobile.fuvxie.cn/Article/07983.shtml
- http://www.mobile.hcbezg.cn/Article/5663679.shtml
- http://www.mobile.fuvxie.cn/Article/1686.shtml
- http://www.mobile.cvsifc.cn/Article/241345.shtml
- http://www.mobile.fuvxie.cn/Article/82744.shtml
- http://www.mobile.fuvxie.cn/Article/5286.shtml
- http://www.mobile.fuvxie.cn/Article/162532.shtml
- http://www.mobile.cvsifc.cn/Article/905311.shtml
- http://www.mobile.fuvxie.cn/Article/6772415.shtml
- http://www.mobile.hcbezg.cn/Article/230058.shtml
- http://www.mobile.hcbezg.cn/Article/5123741.shtml
- http://www.mobile.fuvxie.cn/Article/51452.shtml
- http://www.mobile.fuvxie.cn/Article/505019.shtml
- http://www.mobile.fuvxie.cn/Article/582291.shtml
- http://www.mobile.hcbezg.cn/Article/5189098.shtml
- http://www.mobile.hcbezg.cn/Article/60244.shtml
- http://www.mobile.cvsifc.cn/Article/011909.shtml
- http://www.mobile.fuvxie.cn/Article/9920.shtml
- http://www.mobile.hcbezg.cn/Article/78252.shtml
- http://www.mobile.cvsifc.cn/Article/02777.shtml
- http://www.mobile.cvsifc.cn/Article/7681.shtml
- http://www.mobile.cvsifc.cn/Article/494791.shtml
- http://www.mobile.cvsifc.cn/Article/1388.shtml
- http://www.mobile.fuvxie.cn/Article/704216.shtml
- http://www.mobile.fuvxie.cn/Article/049377.shtml
- http://www.mobile.fuvxie.cn/Article/5504746.shtml
- http://www.mobile.fuvxie.cn/Article/114958.shtml
- http://www.mobile.fuvxie.cn/Article/1007119.shtml
- http://www.mobile.cvsifc.cn/Article/14583.shtml
- http://www.mobile.hcbezg.cn/Article/695082.shtml
- http://www.mobile.hcbezg.cn/Article/240838.shtml
- http://www.mobile.cvsifc.cn/Article/306303.shtml
- http://www.mobile.hcbezg.cn/Article/8698.shtml
- http://www.mobile.hcbezg.cn/Article/9694.shtml
- http://www.mobile.fuvxie.cn/Article/9581365.shtml
- http://www.mobile.hcbezg.cn/Article/45001.shtml
- http://www.mobile.hcbezg.cn/Article/2479836.shtml
- http://www.mobile.cvsifc.cn/Article/3800.shtml
- http://www.mobile.hcbezg.cn/Article/1877219.shtml
- http://www.mobile.fuvxie.cn/Article/94134.shtml
- http://www.mobile.cvsifc.cn/Article/88475.shtml
- http://www.mobile.fuvxie.cn/Article/5543118.shtml
- http://www.mobile.hcbezg.cn/Article/0155.shtml
- http://www.mobile.cvsifc.cn/Article/6712.shtml
- http://www.mobile.hcbezg.cn/Article/6753720.shtml

## 项目结构

项目采用前后端分离架构，后端基于 Flask 与 SQLAlchemy，前端基于 Vue 3 + Vite。以下为关键目录与文件说明。

```
linkhub-cms/
├── backend/                          # 后端 Python 包根目录
│   ├── api/                          # RESTful 路由与视图函数
│   │   ├── v1/                       # API 版本 v1 实现
│   │   │   ├── links.py              # 链接资源的 CRUD 端点
│   │   │   ├── tags.py               # 标签管理端点
│   │   │   ├── health.py             # 健康检查任务触发与结果查询
│   │   │   └── audit.py              # 审计日志查询端点
│   │   └── __init__.py               # 蓝图注册与版本路由前缀配置
│   ├── core/                         # 核心业务逻辑层
│   │   ├── link_processor.py         # 链接清洗、去重、格式规范化
│   │   ├── tag_engine.py             # 标签继承、合并与冲突解决
│   │   ├── health_checker.py         # 并发 HTTP 巡检与结果持久化
│   │   └── importer.py               # 批量导入解析器（支持 CSV/JSON/YAML）
│   ├── models/                       # 数据库模型定义（SQLAlchemy ORM）
│   │   ├── link.py                   # 链接主表模型（含 URL、标题、摘要、状态）
│   │   ├── tag.py                    # 标签表及关联表模型
│   │   ├── health_log.py             # 健康检查历史记录
│   │   └── audit_log.py              # 操作审计日志
│   ├── tasks/                        # 异步任务定义（Celery / RQ）
│   │   ├── periodic_health.py        # 定时巡检任务调度
│   │   └── batch_import.py           # 后台导入任务
│   ├── utils/                        # 通用工具函数
│   │   ├── http_client.py            # 带超时与重试的 HTTP 请求封装
│   │   ├── validators.py             # URL 格式校验与域名黑名单检查
│   │   └── logger.py                 # 结构化日志配置（JSON 格式）
│   └── config/                       # 环境配置管理
│       ├── development.py            # 开发环境配置（SQLite / 调试模式）
│       ├── production.py             # 生产环境配置（PostgreSQL / Redis）
│       └── testing.py                # 单元测试环境配置
├── frontend/                         # 前端 Vue 3 项目
│   ├── src/
│   │   ├── views/                    # 页面级组件
│   │   │   ├── LinkList.vue          # 链接列表与筛选主视图
│   │   │   ├── Dashboard.vue         # 概览统计面板
│   │   │   └── Settings.vue          # 系统配置与标签管理界面
│   │   ├── components/               # 可复用 UI 组件
│   │   │   ├── FilterPanel.vue       # 多条件筛选器组件
│   │   │   ├── HealthBadge.vue       # 链接状态指示器
│   │   │   └── TagSelector.vue       # 标签下拉选择与创建组件
│   │   ├── stores/                   # Pinia 状态管理
│   │   │   ├── linkStore.js          # 链接数据与筛选状态
│   │   │   └── tagStore.js           # 标签树与选中标签状态
│   │   └── api/                      # 与后端通信的 API 封装
│   │       └── client.js             # Axios 实例与请求拦截器
│   ├── public/                       # 静态资源入口
│   └── vite.config.js                # Vite 构建配置（代理与别名）
├── docs/                             # 项目文档目录（详见文档导航）
│   ├── deployment.md
│   ├── admin/
│   ├── api/
│   └── frontend/
├── scripts/                          # 运维与辅助脚本
│   ├── backup_db.sh                  # 数据库定时备份脚本
│   ├── import_batch.sh               # 批量导入命令行工具
│   └── migrate_legacy.py             # 旧数据迁移脚本
├── tests/                            # 单元测试与集成测试
│   ├── unit/                         # 核心函数与模型测试
│   └── integration/                  # API 端点与数据库交互测试
├── requirements.txt                  # Python 生产依赖列表
├── requirements-dev.txt              # Python 开发与测试依赖
├── package.json                      # Node.js 前端依赖与脚本定义
└── README.md                         # 本文件
```

## 贡献指南

欢迎社区开发者提交代码、文档或问题报告。请遵循以下步骤参与项目贡献。

第一步：阅读项目行为准则与贡献者协议。所有贡献者需签署 CLA（贡献者许可协议），确保代码可被合并至主分支。协议模板位于项目根目录的 `CLA.md` 文件中。

第二步：从 GitHub Issues 中挑选未被分配的任务，或提交新 Issue 描述您希望修复的缺陷或新增的功能。建议先通过 Issue 与维护者沟通设计思路，避免不必要的实现返工。

第三步：Fork 本仓库至个人账户，基于 `develop` 分支创建功能分支，分支命名格式为 `feature/功能简述` 或 `fix/问题编号`。本地开发时请确保通过全部现有单元测试，并为新增代码补充对应测试用例。

第四步：完成代码修改后，提交 Pull Request 至 `develop` 分支。PR 描述需包含变更摘要、测试覆盖情况以及关联 Issue 编号。维护者将在 7 个工作日内进行代码审查，必要时会提出修改意见。

第五步：文档更新与国际化贡献。若您修改了 API 行为或新增配置项，请同步更新 `docs/` 目录下对应的中文文档。欢迎将文档翻译为英文或其他语言，翻译贡献将单独列入贡献者名单。

## 常见问题

Q：系统是否支持 MySQL 作为主数据库？  
A：当前官方支持 PostgreSQL 14+ 和 SQLite 3.35+ 两种数据库后端。MySQL / MariaDB 未经过完整兼容性测试，但理论上可通过修改 SQLAlchemy 连接字符串尝试使用。若需在生产环境使用 MySQL，建议自行进行充分测试并调整索引策略，同时注意 JSON 字段与全文索引的语法差异。

Q：健康检查任务是否会因为目标站点响应缓慢而阻塞系统？  
A：健康检查任务基于异步队列（Redis + RQ）执行，每个目标请求均设置了连接超时（5 秒）和读取超时（10 秒），且采用小批量并发（默认并发数 20）的方式运行。即使部分站点响应极慢，也不会影响主 Web 服务的请求处理。检查结果会异步写入数据库，用户可通过 API 查询最新状态。

Q：导入 250 条链接需要多长时间？系统是否有导入数量限制？  
A：单次导入 250 条链接通常在 3 至 8 秒内完成（取决于网络环境与数据清洗复杂度）。系统未对单次导入数量设置硬性上限，但建议单批次不超过 5000 条，以避免内存占用过高。若需导入更大规模数据，可使用后台任务模式分批提交，或通过命令行脚本 `import_batch.sh` 执行分块导入。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
