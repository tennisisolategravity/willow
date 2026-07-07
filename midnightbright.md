# WebIndex Gateway

WebIndex Gateway 是一个面向技术团队与内容运营者的轻量级外链资源聚合与导航系统。该项目定位于解决多源、多批次、大规模外链数据在采集、清洗、分类、检索与可视化呈现过程中的工程化问题。目标用户包括运维工程师、数据采集工程师、内容管理专员以及需要批量维护外部引用关系的开发者。WebIndex Gateway 不提供爬虫功能，而是以结构化索引为核心，对外链资源进行标准化封装，支持静态站点生成、动态接口查询与分类目录导出等多种使用模式，可作为企业级知识库或技术文档站点的外链中台。

## 功能概览

批量外链导入与去重 系统提供统一的导入接口，支持从文本文件、CSV 或直接粘贴的 URL 列表中批量导入外链，并基于 URL 完整路径与来源批次号进行自动去重，避免重复记录污染索引库。

多级分类标签管理 每条外链可绑定多个自定义标签，支持建立层级化的分类体系（如 技术文档 / 移动端 / 行业资讯），便于后续按分类目录生成导航页面或 API 过滤条件。

资源状态健康检查 内置定时检查任务，可对已收录的外链发起 HTTP 头部探测，标记不可达、重定向或响应超时的链接，并将异常状态输出至监控报表，辅助运维人员及时清理失效资源。

静态站点生成器 支持将索引数据渲染为纯 HTML 静态导航站点，内置响应式布局模板，适合部署至 Nginx、CDN 或对象存储服务，无需依赖后端运行环境。

JSON / XML 数据导出 提供标准的数据导出接口，可将当前索引库完整导出为 JSON 或 XML 格式，方便下游系统（如企业内部搜索、第三方文档平台）进行二次加工或迁移。

访问统计与热度排序 记录每条外链的点击次数与最近访问时间，支持按热度、添加时间或字母顺序对资源列表进行排序，提升高频资源的曝光效率。

权限与批次管理 支持多用户角色划分，每批导入的资源自动归属至对应批次（如 第32/60批），便于追踪资源来源、审计变更记录以及按批次执行批量下线或更新操作。

## 应用场景

技术文档站点的外链附录管理 技术团队在撰写产品文档或 API 参考手册时，需要引用大量外部规范、标准或第三方库主页。WebIndex Gateway 可作为文档站点的后端外链仓库，编辑人员通过标签将外链与具体文档版本关联，生成统一的引用附录页面，避免文档中散落裸链接导致维护困难。

数据采集项目的资源清单维护 数据采集工程师在实施定向采集任务前，需整理目标网站清单。使用 WebIndex Gateway 可分批导入数百个起始 URL，并通过健康检查功能提前筛除无法访问的站点，提高采集任务的成功率与稳定性。

企业知识库的外部参考整合 企业内部的 Confluence、Notion 或自建知识库中常包含大量外部参考链接。WebIndex Gateway 可定期接收来自知识库的 URL 导出文件，自动归并并生成企业级外链地图，供新员工培训或技术调研时快速检索。

静态导航站点快速搭建 个人开发者或小型团队无需开发后端，可直接使用 WebIndex Gateway 的静态生成功能，将一批收藏的行业资源、博客或工具站点生成为干净、可搜索的导航页面，部署至 GitHub Pages 或 Cloudflare Pages 即可对外服务。

## 快速开始

以下指令适用于 Linux / macOS 环境，Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/webindex/gateway.git
cd gateway

# 安装依赖（项目使用 Python 3.9+ 与 pipenv 管理）
pip install pipenv
pipenv install --dev

# 复制示例配置文件并修改数据库连接与批次信息
cp .env.example .env
# 编辑 .env 文件，设置 BATCH_ID=32 与 BATCH_TOTAL=60

# 运行初始化数据库迁移
pipenv run alembic upgrade head

# 导入示例数据（包含本批次 250 条资源占位记录）
pipenv run webindex import --batch 32 --file ./data/batch_32.txt

# 启动开发服务器
pipenv run python manage.py runserver
```

访问 http://127.0.0.1:8000 即可查看资源索引首页。若要生成静态站点，执行 `pipenv run webindex build --output ./dist`。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 至 3.11 | 核心运行环境，3.12 暂未完成兼容性测试 |
| Pipenv | 2023.x 或更新 | 用于依赖隔离与锁定，推荐使用 pip 安装 |
| PostgreSQL | 13 至 15 | 生产环境推荐，支持 JSONB 字段与全文检索；开发环境可使用 SQLite 替代 |
| Redis | 6.2 或更新 | 用于缓存健康检查结果与访问计数，非必需但强烈建议启用 |
| Node.js | 18 LTS | 仅当启用前端资产编译时必需（静态生成器主题开发） |
| Nginx | 1.20 或更新 | 生产环境静态站点部署建议，非运行强依赖 |
| Supervisor | 4.x | 用于管理后台健康检查守护进程，生产环境推荐 |
| Alembic | 1.9 或更新 | 数据库迁移管理，项目初始化时自动安装 |
| pytest | 7.x | 仅在运行单元测试时使用，开发依赖 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user/quickstart.md | 如何快速导入第一批外链、如何生成静态站点、如何配置分类标签 |
| 运维指南 | /docs/ops/deployment.md | 生产环境如何部署至 Linux 服务器、如何配置 Nginx 反向代理、如何设置定时健康检查 |
| 开发参考 | /docs/dev/api.md | 数据导入接口、标签管理接口、导出接口的请求与响应格式，以及扩展自定义分类器的步骤 |
| 设计说明 | /docs/design/schema.md | 索引库的 ER 图、批次与资源的关系模型、健康检查状态机的设计决策 |

## 资源列表

- http://www.mobile.cvsifc.cn/Article/43291.shtml
- http://www.mobile.fuvxie.cn/Article/2945884.shtml
- http://www.mobile.fuvxie.cn/Article/4802.shtml
- http://www.mobile.cvsifc.cn/Article/679983.shtml
- http://www.mobile.hcbezg.cn/Article/363727.shtml
- http://www.mobile.cvsifc.cn/Article/2997.shtml
- http://www.mobile.cvsifc.cn/Article/2352.shtml
- http://www.mobile.fuvxie.cn/Article/9543807.shtml
- http://www.mobile.cvsifc.cn/Article/181075.shtml
- http://www.mobile.cvsifc.cn/Article/33401.shtml
- http://www.mobile.cvsifc.cn/Article/46609.shtml
- http://www.mobile.cvsifc.cn/Article/5296853.shtml
- http://www.mobile.cvsifc.cn/Article/7852853.shtml
- http://www.mobile.hcbezg.cn/Article/7696.shtml
- http://www.mobile.hcbezg.cn/Article/124009.shtml
- http://www.mobile.fuvxie.cn/Article/6491.shtml
- http://www.mobile.cvsifc.cn/Article/3021351.shtml
- http://www.mobile.fuvxie.cn/Article/3047.shtml
- http://www.mobile.cvsifc.cn/Article/190930.shtml
- http://www.mobile.fuvxie.cn/Article/74385.shtml
- http://www.mobile.hcbezg.cn/Article/343942.shtml
- http://www.mobile.hcbezg.cn/Article/6856441.shtml
- http://www.mobile.cvsifc.cn/Article/1335.shtml
- http://www.mobile.hcbezg.cn/Article/8659961.shtml
- http://www.mobile.hcbezg.cn/Article/3422.shtml
- http://www.mobile.hcbezg.cn/Article/4762.shtml
- http://www.mobile.hcbezg.cn/Article/2995.shtml
- http://www.mobile.hcbezg.cn/Article/6929.shtml
- http://www.mobile.fuvxie.cn/Article/306547.shtml
- http://www.mobile.hcbezg.cn/Article/2636210.shtml
- http://www.mobile.cvsifc.cn/Article/2620.shtml
- http://www.mobile.hcbezg.cn/Article/38042.shtml
- http://www.mobile.fuvxie.cn/Article/5572594.shtml
- http://www.mobile.cvsifc.cn/Article/0858.shtml
- http://www.mobile.fuvxie.cn/Article/74932.shtml
- http://www.mobile.fuvxie.cn/Article/354961.shtml
- http://www.mobile.fuvxie.cn/Article/9995637.shtml
- http://www.mobile.cvsifc.cn/Article/15722.shtml
- http://www.mobile.cvsifc.cn/Article/079391.shtml
- http://www.mobile.cvsifc.cn/Article/5771.shtml
- http://www.mobile.hcbezg.cn/Article/4315.shtml
- http://www.mobile.hcbezg.cn/Article/6398621.shtml
- http://www.mobile.cvsifc.cn/Article/39493.shtml
- http://www.mobile.hcbezg.cn/Article/361414.shtml
- http://www.mobile.hcbezg.cn/Article/534438.shtml
- http://www.mobile.cvsifc.cn/Article/47463.shtml
- http://www.mobile.hcbezg.cn/Article/725984.shtml
- http://www.mobile.fuvxie.cn/Article/3684.shtml
- http://www.mobile.hcbezg.cn/Article/4077.shtml
- http://www.mobile.cvsifc.cn/Article/884073.shtml
- http://www.mobile.hcbezg.cn/Article/3748.shtml
- http://www.mobile.cvsifc.cn/Article/067791.shtml
- http://www.mobile.fuvxie.cn/Article/87843.shtml
- http://www.mobile.fuvxie.cn/Article/7047.shtml
- http://www.mobile.cvsifc.cn/Article/42392.shtml
- http://www.mobile.cvsifc.cn/Article/3311.shtml
- http://www.mobile.hcbezg.cn/Article/8856.shtml
- http://www.mobile.fuvxie.cn/Article/15044.shtml
- http://www.mobile.cvsifc.cn/Article/5365812.shtml
- http://www.mobile.fuvxie.cn/Article/1472.shtml
- http://www.mobile.fuvxie.cn/Article/7461.shtml
- http://www.mobile.hcbezg.cn/Article/8569.shtml
- http://www.mobile.hcbezg.cn/Article/077179.shtml
- http://www.mobile.fuvxie.cn/Article/1720165.shtml
- http://www.mobile.cvsifc.cn/Article/8252.shtml
- http://www.mobile.hcbezg.cn/Article/802832.shtml
- http://www.mobile.cvsifc.cn/Article/7801.shtml
- http://www.mobile.hcbezg.cn/Article/01916.shtml
- http://www.mobile.hcbezg.cn/Article/3602457.shtml
- http://www.mobile.fuvxie.cn/Article/165494.shtml
- http://www.mobile.fuvxie.cn/Article/237798.shtml
- http://www.mobile.fuvxie.cn/Article/7748111.shtml
- http://www.mobile.cvsifc.cn/Article/3714440.shtml
- http://www.mobile.hcbezg.cn/Article/8769.shtml
- http://www.mobile.hcbezg.cn/Article/404598.shtml
- http://www.mobile.fuvxie.cn/Article/3407618.shtml
- http://www.mobile.fuvxie.cn/Article/8255228.shtml
- http://www.mobile.cvsifc.cn/Article/82953.shtml
- http://www.mobile.cvsifc.cn/Article/905355.shtml
- http://www.mobile.fuvxie.cn/Article/2872.shtml
- http://www.mobile.cvsifc.cn/Article/89012.shtml
- http://www.mobile.fuvxie.cn/Article/174111.shtml
- http://www.mobile.hcbezg.cn/Article/76988.shtml
- http://www.mobile.fuvxie.cn/Article/10673.shtml
- http://www.mobile.fuvxie.cn/Article/120939.shtml
- http://www.mobile.cvsifc.cn/Article/714331.shtml
- http://www.mobile.fuvxie.cn/Article/5266480.shtml
- http://www.mobile.hcbezg.cn/Article/2784687.shtml
- http://www.mobile.fuvxie.cn/Article/3284.shtml
- http://www.mobile.hcbezg.cn/Article/4277676.shtml
- http://www.mobile.hcbezg.cn/Article/00216.shtml
- http://www.mobile.fuvxie.cn/Article/63927.shtml
- http://www.mobile.hcbezg.cn/Article/83950.shtml
- http://www.mobile.fuvxie.cn/Article/7064.shtml
- http://www.mobile.cvsifc.cn/Article/6415926.shtml
- http://www.mobile.cvsifc.cn/Article/959555.shtml
- http://www.mobile.fuvxie.cn/Article/04520.shtml
- http://www.mobile.fuvxie.cn/Article/132506.shtml
- http://www.mobile.cvsifc.cn/Article/058744.shtml
- http://www.mobile.fuvxie.cn/Article/9561.shtml
- http://www.mobile.fuvxie.cn/Article/2696.shtml
- http://www.mobile.hcbezg.cn/Article/11819.shtml
- http://www.mobile.hcbezg.cn/Article/850110.shtml
- http://www.mobile.fuvxie.cn/Article/7609.shtml
- http://www.mobile.hcbezg.cn/Article/00923.shtml
- http://www.mobile.cvsifc.cn/Article/0195.shtml
- http://www.mobile.fuvxie.cn/Article/1707.shtml
- http://www.mobile.hcbezg.cn/Article/76057.shtml
- http://www.mobile.hcbezg.cn/Article/200930.shtml
- http://www.mobile.fuvxie.cn/Article/087421.shtml
- http://www.mobile.cvsifc.cn/Article/2771367.shtml
- http://www.mobile.fuvxie.cn/Article/43308.shtml
- http://www.mobile.fuvxie.cn/Article/7044404.shtml
- http://www.mobile.hcbezg.cn/Article/025583.shtml
- http://www.mobile.cvsifc.cn/Article/7078.shtml
- http://www.mobile.hcbezg.cn/Article/5890.shtml
- http://www.mobile.hcbezg.cn/Article/317169.shtml
- http://www.mobile.hcbezg.cn/Article/713096.shtml
- http://www.mobile.fuvxie.cn/Article/715613.shtml
- http://www.mobile.cvsifc.cn/Article/0392303.shtml
- http://www.mobile.fuvxie.cn/Article/24270.shtml
- http://www.mobile.hcbezg.cn/Article/8439.shtml
- http://www.mobile.fuvxie.cn/Article/16055.shtml
- http://www.mobile.fuvxie.cn/Article/236688.shtml
- http://www.mobile.cvsifc.cn/Article/34103.shtml
- http://www.mobile.hcbezg.cn/Article/3990032.shtml
- http://www.mobile.fuvxie.cn/Article/7703.shtml
- http://www.mobile.fuvxie.cn/Article/863048.shtml
- http://www.mobile.cvsifc.cn/Article/7312406.shtml
- http://www.mobile.hcbezg.cn/Article/6589886.shtml
- http://www.mobile.cvsifc.cn/Article/6235.shtml
- http://www.mobile.cvsifc.cn/Article/3055.shtml
- http://www.mobile.cvsifc.cn/Article/851954.shtml
- http://www.mobile.fuvxie.cn/Article/3167323.shtml
- http://www.mobile.hcbezg.cn/Article/5139094.shtml
- http://www.mobile.hcbezg.cn/Article/4196.shtml
- http://www.mobile.fuvxie.cn/Article/1155.shtml
- http://www.mobile.hcbezg.cn/Article/760983.shtml
- http://www.mobile.cvsifc.cn/Article/3153.shtml
- http://www.mobile.cvsifc.cn/Article/496263.shtml
- http://www.mobile.fuvxie.cn/Article/87349.shtml
- http://www.mobile.fuvxie.cn/Article/05013.shtml
- http://www.mobile.fuvxie.cn/Article/15601.shtml
- http://www.mobile.cvsifc.cn/Article/36794.shtml
- http://www.mobile.cvsifc.cn/Article/2623844.shtml
- http://www.mobile.fuvxie.cn/Article/4083.shtml
- http://www.mobile.hcbezg.cn/Article/9094548.shtml
- http://www.mobile.cvsifc.cn/Article/8677559.shtml
- http://www.mobile.hcbezg.cn/Article/38155.shtml
- http://www.mobile.fuvxie.cn/Article/4979.shtml
- http://www.mobile.cvsifc.cn/Article/7186.shtml
- http://www.mobile.cvsifc.cn/Article/7054988.shtml
- http://www.mobile.cvsifc.cn/Article/85828.shtml
- http://www.mobile.hcbezg.cn/Article/327697.shtml
- http://www.mobile.cvsifc.cn/Article/05762.shtml
- http://www.mobile.fuvxie.cn/Article/90286.shtml
- http://www.mobile.hcbezg.cn/Article/4496.shtml
- http://www.mobile.hcbezg.cn/Article/0221.shtml
- http://www.mobile.hcbezg.cn/Article/8832481.shtml
- http://www.mobile.fuvxie.cn/Article/75345.shtml
- http://www.mobile.fuvxie.cn/Article/319090.shtml
- http://www.mobile.cvsifc.cn/Article/371670.shtml
- http://www.mobile.fuvxie.cn/Article/759401.shtml
- http://www.mobile.hcbezg.cn/Article/8975697.shtml
- http://www.mobile.hcbezg.cn/Article/096606.shtml
- http://www.mobile.cvsifc.cn/Article/595305.shtml
- http://www.mobile.hcbezg.cn/Article/04404.shtml
- http://www.mobile.fuvxie.cn/Article/631326.shtml
- http://www.mobile.hcbezg.cn/Article/5632636.shtml
- http://www.mobile.cvsifc.cn/Article/98986.shtml
- http://www.mobile.fuvxie.cn/Article/974578.shtml
- http://www.mobile.cvsifc.cn/Article/498612.shtml
- http://www.mobile.fuvxie.cn/Article/1211.shtml
- http://www.mobile.cvsifc.cn/Article/893700.shtml
- http://www.mobile.fuvxie.cn/Article/9102.shtml
- http://www.mobile.fuvxie.cn/Article/568583.shtml
- http://www.mobile.cvsifc.cn/Article/7372321.shtml
- http://www.mobile.cvsifc.cn/Article/971748.shtml
- http://www.mobile.hcbezg.cn/Article/031438.shtml
- http://www.mobile.cvsifc.cn/Article/4380.shtml
- http://www.mobile.cvsifc.cn/Article/811345.shtml
- http://www.mobile.hcbezg.cn/Article/6057148.shtml
- http://www.mobile.fuvxie.cn/Article/88656.shtml
- http://www.mobile.cvsifc.cn/Article/9906380.shtml
- http://www.mobile.fuvxie.cn/Article/64063.shtml
- http://www.mobile.fuvxie.cn/Article/71245.shtml
- http://www.mobile.hcbezg.cn/Article/49364.shtml
- http://www.mobile.hcbezg.cn/Article/8881.shtml
- http://www.mobile.fuvxie.cn/Article/2860.shtml
- http://www.mobile.hcbezg.cn/Article/6283.shtml
- http://www.mobile.fuvxie.cn/Article/928787.shtml
- http://www.mobile.hcbezg.cn/Article/39759.shtml
- http://www.mobile.fuvxie.cn/Article/38356.shtml
- http://www.mobile.fuvxie.cn/Article/0580378.shtml
- http://www.mobile.fuvxie.cn/Article/8826.shtml
- http://www.mobile.fuvxie.cn/Article/69265.shtml
- http://www.mobile.cvsifc.cn/Article/73690.shtml
- http://www.mobile.cvsifc.cn/Article/24583.shtml
- http://www.mobile.fuvxie.cn/Article/3401.shtml
- http://www.mobile.hcbezg.cn/Article/076783.shtml
- http://www.mobile.fuvxie.cn/Article/22998.shtml
- http://www.mobile.hcbezg.cn/Article/450857.shtml
- http://www.mobile.fuvxie.cn/Article/0807720.shtml
- http://www.mobile.hcbezg.cn/Article/9471.shtml
- http://www.mobile.cvsifc.cn/Article/785010.shtml
- http://www.mobile.fuvxie.cn/Article/83842.shtml
- http://www.mobile.fuvxie.cn/Article/985863.shtml
- http://www.mobile.hcbezg.cn/Article/721896.shtml
- http://www.mobile.cvsifc.cn/Article/121916.shtml
- http://www.mobile.cvsifc.cn/Article/581837.shtml
- http://www.mobile.fuvxie.cn/Article/468805.shtml
- http://www.mobile.hcbezg.cn/Article/7967.shtml
- http://www.mobile.hcbezg.cn/Article/615095.shtml
- http://www.mobile.cvsifc.cn/Article/124577.shtml
- http://www.mobile.hcbezg.cn/Article/6226.shtml
- http://www.mobile.fuvxie.cn/Article/51705.shtml
- http://www.mobile.cvsifc.cn/Article/66320.shtml
- http://www.mobile.fuvxie.cn/Article/001555.shtml
- http://www.mobile.fuvxie.cn/Article/947108.shtml
- http://www.mobile.cvsifc.cn/Article/0873.shtml
- http://www.mobile.hcbezg.cn/Article/398120.shtml
- http://www.mobile.fuvxie.cn/Article/2508432.shtml
- http://www.mobile.hcbezg.cn/Article/37322.shtml
- http://www.mobile.fuvxie.cn/Article/7428889.shtml
- http://www.mobile.cvsifc.cn/Article/97159.shtml
- http://www.mobile.fuvxie.cn/Article/281794.shtml
- http://www.mobile.cvsifc.cn/Article/628978.shtml
- http://www.mobile.cvsifc.cn/Article/0984.shtml
- http://www.mobile.cvsifc.cn/Article/333569.shtml
- http://www.mobile.hcbezg.cn/Article/7525364.shtml
- http://www.mobile.fuvxie.cn/Article/35604.shtml
- http://www.mobile.hcbezg.cn/Article/710917.shtml
- http://www.mobile.hcbezg.cn/Article/4157133.shtml
- http://www.mobile.fuvxie.cn/Article/19420.shtml
- http://www.mobile.fuvxie.cn/Article/97531.shtml
- http://www.mobile.hcbezg.cn/Article/353124.shtml
- http://www.mobile.cvsifc.cn/Article/00996.shtml
- http://www.mobile.hcbezg.cn/Article/5637.shtml
- http://www.mobile.fuvxie.cn/Article/2147.shtml
- http://www.mobile.hcbezg.cn/Article/3961.shtml
- http://www.mobile.hcbezg.cn/Article/4791.shtml
- http://www.mobile.fuvxie.cn/Article/78570.shtml
- http://www.mobile.fuvxie.cn/Article/90985.shtml
- http://www.mobile.cvsifc.cn/Article/0988081.shtml
- http://www.mobile.fuvxie.cn/Article/89485.shtml
- http://www.mobile.cvsifc.cn/Article/385971.shtml
- http://www.mobile.fuvxie.cn/Article/7614824.shtml
- http://www.mobile.hcbezg.cn/Article/9986386.shtml
- http://www.mobile.hcbezg.cn/Article/0741358.shtml
- http://www.mobile.cvsifc.cn/Article/9264256.shtml

## 项目结构

```
gateway/
├── .env.example                      # 环境变量模板，包含数据库连接串与批次元数据
├── .gitignore                        # Git 忽略规则，排除本地配置与临时文件
├── Dockerfile                        # 多阶段构建文件，用于生成生产镜像
├── Makefile                          # 常用命令封装（install, test, build, clean）
├── README.md                         # 项目说明文档（当前文件）
├── docker-compose.yml                # 本地开发环境编排（PostgreSQL + Redis + 应用）
├── manage.py                         # Django 管理入口（实际使用 Flask CLI 风格，此处为兼容命名）
├── pyproject.toml                    # Pipenv 依赖清单与项目元数据
├── requirements.txt                  # 传统 pip 依赖导出（供 CI 使用）
├── webindex/                         # 核心应用模块
│   ├── __init__.py
│   ├── app.py                        # Flask 应用工厂与路由注册
│   ├── cli.py                        # 命令行接口（导入、检查、构建、导出）
│   ├── config.py                     # 配置类（开发、测试、生产）
│   ├── models/                       # 数据模型层
│   │   ├── __init__.py
│   │   ├── resource.py               # Resource 表定义（URL、标题、状态、点击量）
│   │   ├── batch.py                  # Batch 表定义（批次编号、总量、导入时间）
│   │   ├── tag.py                    # Tag 表定义与多对多关联表
│   │   └── health_log.py             # 健康检查历史记录表
│   ├── services/                     # 业务逻辑层
│   │   ├── __init__.py
│   │   ├── importer.py               # 批量导入解析器（支持 txt/csv 与直接粘贴）
│   │   ├── deduplicator.py           # 去重算法（基于 URL 哈希与批次 ID）
│   │   ├── health_checker.py         # 异步 HTTP 探活与状态更新
│   │   ├── static_generator.py       # 静态站点渲染引擎（Jinja2 + 响应式模板）
│   │   └── exporter.py               # JSON/XML 导出序列化器
│   ├── templates/                    # 静态生成器所使用的 HTML 模板
│   │   ├── base.html
│   │   ├── index.html                # 首页资源列表（分页 + 标签过滤）
│   │   ├── detail.html               # 单条资源详情页
│   │   └── error.html
│   ├── static/                       # 静态资源（CSS、JS、字体）
│   │   ├── css/
│   │   ├── js/
│   │   └── images/
│   ├── utils/                        # 通用工具函数
│   │   ├── __init__.py
│   │   ├── http_client.py            # 带超时与重试的 requests 封装
│   │   ├── logger.py                 # 统一日志格式与分级输出
│   │   └── validators.py             # URL 格式校验与规范化
│   └── migrations/                   # Alembic 数据库迁移脚本
│       ├── versions/
│       └── alembic.ini
├── tests/                            # 单元测试与集成测试
│   ├── test_importer.py
│   ├── test_deduplicator.py
│   ├── test_health_checker.py
│   └── conftest.py                   # pytest 共享夹具
├── data/                             # 示例数据与批次导入文件存放目录
│   └── batch_32.txt                  # 第 32 批原始 URL 列表（纯文本，每行一条）
└── docs/                             # 详细文档（用户手册、运维指南、API 参考）
    ├── user/
    ├── ops/
    ├── dev/
    └── design/
```

## 贡献指南

1. 阅读设计文档与代码风格规范  
   在提交任何代码或文档之前，请先查阅 /docs/design/schema.md 了解数据模型设计决策，并参考 /docs/dev/coding_style.md 中的 PEP 8 与命名约定。所有 Python 代码必须通过 flake8 与 black 格式化检查。

2. 选择或创建 Issue 并获取讨论  
   推荐先在 GitHub Issues 中搜索已有话题，若无相关议题则新建一个 Issue 描述你希望解决的问题或新增的功能。核心维护者会在 48 小时内给出初步反馈，并标记 "ready-to-work" 或 "needs-discussion" 标签。

3. 派生项目并创建功能分支  
   将主仓库 Fork 至个人账户，然后克隆派生仓库到本地。创建分支时请使用 `feature/描述` 或 `fix/描述` 格式，例如 `feature/support-json-import`。保持分支聚焦于单一问题或功能点。

4. 编写测试用例并确保全部通过  
   新增或修改功能必须同步编写对应的 pytest 用例，放置于 /tests 目录下对应文件中。运行 `make test` 执行全部测试套件，确保覆盖率达到 80% 以上且无回归错误。

5. 提交 Pull Request 并等待 Code Review  
   推送分支后，向主仓库的 `main` 分支发起 Pull Request。请填写 PR 模板中的检查清单，包括是否更新文档、是否添加变更日志条目。至少需要一位核心维护者 Approve 后方可合并。

## 常见问题

Q: 导入大量 URL 时出现超时或内存不足如何处理？  
A: 默认导入接口采用流式读取与分批提交策略，单次建议不超过 2000 条。若需导入超过 10000 条记录，请使用命令行工具 `webindex import --chunk-size 500` 指定更小的分块，并确保 PostgreSQL 的 work_mem 参数已调优。此外，可通过增加 `--no-health-check` 选项推迟健康检查至导入完成后再统一执行。

Q: 静态生成器输出的页面不包含搜索功能，如何实现站点内搜索？  
A: 静态生成器默认输出纯静态 HTML，不包含服务端搜索接口。如需搜索能力，推荐两种方案：一是将导出 JSON 数据与开源全文搜索库（如 Lunr.js 或 FlexSearch）集成，在前端实现本地搜索；二是在生成阶段调用外部搜索引擎 API（如 Algolia 或 Meilisearch），将索引数据推送至第三方服务。

Q: 健康检查标记为 "不可达" 的链接会自动重试吗？  
A: 系统在首次检查失败后会进入指数退避重试队列，最多重试 3 次（间隔分别为 60 秒、300 秒、900 秒）。若三次全部失败，状态将被固定为 "异常" 并记录最终错误码。用户可通过管理后台或 CLI 命令 `webindex check --retry-failed` 手动触发重新检查。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-08 01:10:02
