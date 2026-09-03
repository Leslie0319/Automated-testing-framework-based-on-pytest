# Pytest 接口自动化测试实践

这是一个**基于开源项目进行学习与实践**的接口自动化测试仓库，主要用于理解 Python + Pytest 接口自动化框架的工程结构、运行流程和常见问题排查。

>原始框架设计和部分代码来自开源项目；我的工作主要集中在环境搭建、依赖适配、运行调试、Mock 联调、兼容性问题处理以及对框架结构的学习整理。

## 实践内容

- 在 Windows 环境完成项目部署与虚拟环境配置
- 补齐和适配项目运行依赖
- 处理 Pytest 版本兼容问题
- 启动 Flask Mock 服务并完成接口联调
- 跑通测试收集、执行、结果查看和失败分析流程
- 学习 YAML 数据驱动、参数化、Fixture、统一请求封装和断言机制
- 梳理测试用例层、公共工具层、基础封装层、配置层、数据层、报告层和 Mock 层的职责

## 技术栈

`Python` · `Pytest` · `Requests` · `PyYAML` · `Allure` · `Flask` · `SQLAlchemy`

项目中还涉及 Redis、PyMySQL、PyMongo、Paramiko 等依赖，主要用于理解较完整测试框架中的外部服务与工具集成方式。

## 本地运行

### 1. 创建虚拟环境

```bash
python -m venv .venv
```

Windows：

```bash
.venv\Scripts\activate
```

### 2. 安装主要依赖

```bash
pip install -U pip
pip install pytest==8.3.5 requests pyyaml allure-pytest jsonpath pandas pymysql redis pymongo sqlalchemy paramiko colorlog clickhouse-sqlalchemy flask flask-jwt-extended flask-cors
```

### 3. 启动 Mock 服务

```bash
cd mock_server\api_server
python base\flask_service.py
```

### 4. 执行测试

```bash
pytest
```

也可以执行指定测试文件：

```bash
pytest "testcase\Single interface\test_debug_api.py"
```

## 学习重点

通过这个仓库主要练习和理解：

1. Pytest 工程化使用与测试执行流程
2. YAML 数据驱动和参数化测试
3. 请求封装、动态参数处理与统一断言
4. Mock 服务在接口测试中的作用
5. Python 项目的依赖、版本兼容和环境问题排查

## 说明

这是一个学习实践仓库，保留它主要是为了记录自动化测试框架的实际运行、调试和排障过程。

GitHub: https://github.com/Leslie0319
