这是一个基于开源项目进行学习与实践的 接口自动化测试框架练习仓库，主要围绕 Python + Pytest 接口自动化测试 的核心链路展开，包括本地环境搭建、YAML 数据驱动、Mock 服务联调、测试执行、结果分析与问题排查。

本仓库的重点不在于“从零原创一个框架”，而在于通过真实的项目运行与排障过程，系统理解接口自动化测试框架在工程实践中的落地方式，并沉淀测试开发岗位所需的核心能力。

项目简介

本项目基于开源 Pytest 自动化测试框架进行学习和实践，结合 Windows 本地环境完成了项目部署、依赖适配、Mock 服务启动、测试执行与问题分析，并对测试框架的目录分层、执行流程与工程化设计思路进行了整理与总结。

在实践过程中，我重点关注了以下内容：

自动化测试项目的本地搭建与环境初始化

Git / Python 依赖 / Pytest 版本兼容等常见问题排查

基于 Pytest 的测试执行机制与参数化能力

基于 YAML 的数据驱动测试思路

Mock 服务在接口自动化测试中的联调方式

请求封装、动态参数替换、结果提取、统一断言与报告生成的完整执行链路

技术栈

Python / Pytest / Requests / PyYAML / Allure / Flask / Mock Server / SQLAlchemy / Redis / PyMySQL / PyMongo / Paramiko

我的实践内容

在该项目中，我主要完成了以下实践工作：

在 Windows 本地完成项目克隆、虚拟环境创建与依赖安装

解决 Git HTTPS 证书校验问题，完成仓库本地拉取

识别项目属于“源码目录直接运行”的测试框架工程，而非标准单包发布项目

补齐项目运行依赖，解决 clickhouse_sqlalchemy、flask_jwt_extended 等模块缺失问题

处理 Pytest 版本兼容问题，解决 conftest.py 中测试汇总逻辑与新版本不兼容的问题

启动本地 Flask Mock 服务，完成接口自动化测试运行环境搭建

跑通自动化测试执行链路，完成用例收集、执行、结果查看与失败分析

结合项目源码梳理框架分层设计，理解用例层、公共层、基础封装层、配置层、数据层、报告层与 Mock 层的职责划分

框架结构理解

本项目采用较为典型的接口自动化测试框架分层设计，主要模块如下：

testcase

存放测试用例，包含单接口测试、商品管理测试以及业务场景测试。

common

存放公共工具方法，例如断言封装、配置读取、日志处理、数据提取等。

base

存放请求封装与基础能力模块，负责统一处理接口调用流程。

conf

存放配置文件，用于实现测试逻辑与环境参数分离。

data

存放测试数据与 YAML 用例文件，支撑参数化执行和数据驱动测试。

report

存放测试执行结果与测试报告相关内容。

mock_server

存放本地 Mock 服务，用于在无真实后端依赖时完成接口联调与测试执行。

关键学习点

通过本项目，我重点学习并实践了以下测试开发相关内容：

1. 接口自动化测试框架分层设计

理解测试框架中用例层、公共能力层、请求封装层、配置层、数据层和报告层的职责划分，以及如何通过分层设计提升可维护性和可扩展性。

2. Pytest 工程化使用

学习并实践了 pytest.main()、pytest.ini、conftest.py、fixture、mark、参数化执行、失败重跑、分组执行等机制在自动化测试中的应用。

3. YAML 数据驱动测试

通过 pytest.mark.parametrize 结合 YAML 文件实现测试数据与测试逻辑分离，理解 baseInfo / testCase 拆分、动态变量替换和测试场景扩展方式。

4. 请求封装与统一断言

理解接口请求统一封装、响应结果处理、字段提取、断言抽象等实现思路，提升用例复用性与可维护性。

5. Mock 服务联调

掌握本地 Flask Mock 服务的启动与联调方式，理解在自动化测试中隔离真实后端依赖、构造可控测试环境的价值。

6. 环境搭建与问题排查

在项目实践中处理了 Git SSL、依赖缺失、Pytest 版本兼容、Mock 服务启动异常等问题，提升了测试环境搭建与排障能力。

项目运行流程
1. 克隆项目
git clone https://github.com/你的用户名/你的仓库名.git
cd 你的仓库名
2. 创建并激活虚拟环境

Windows：

python -m venv .venv
.venv\Scripts\activate
3. 安装依赖
pip install -U pip
pip install pytest==8.3.5 requests pyyaml allure-pytest jsonpath pandas pymysql redis pymongo sqlalchemy paramiko colorlog clickhouse-sqlalchemy flask flask-jwt-extended flask-cors
4. 启动 Mock 服务
cd mock_server\api_server
python base\flask_service.py
5. 执行测试

重新打开一个终端，在项目根目录激活虚拟环境后执行：

pytest

也可以单独执行指定测试文件：

pytest "testcase\Single interface\test_debug_api.py"
项目收获

这个仓库帮助我把“会使用测试工具”进一步推进到“理解自动化测试框架如何落地”。
相比单纯编写接口测试脚本，我更系统地学习了以下能力：

自动化测试框架的结构化组织方式

接口自动化项目的本地部署与环境适配

测试数据驱动与参数化执行机制

Mock 服务联调与测试环境隔离思路

自动化测试执行结果分析与失败根因定位

面向测试开发岗位的工程化意识与排障能力

项目说明

本仓库基于开源项目进行学习与实践，原始框架设计思路与部分代码实现来源于原作者开源仓库。
本人主要完成了环境搭建、依赖适配、运行调试、Mock 联调、问题排查、框架理解与个人实践总结等工作。

该仓库主要用于 测试开发岗位求职展示与自动化测试学习沉淀。

联系方式

GitHub：你的 GitHub 地址

Email：你的邮箱

欢迎交流接口自动化测试、Pytest 框架实践与测试开发相关问题。
