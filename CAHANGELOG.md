# 版本更新

## 0.2.1
- 优化 SLS 查询工具，增加 from_timestamp 和 to_timestamp 参数，确保查询语句的正确性
- 增加 SLS 日志查询的 prompts

## 0.2.0
- 增加 cms_translate_natural_language_to_promql 工具，根据自然语言生成 promql 查询语句

## 0.1.9
- 支持 STS Token 方式登录，可通过环境变量ALIBABA_CLOUD_SECURITY_TOKEN 指定
- 修改 README.md 文档，增加 Cursor，Cline 等集成说明以及 UV 命令等说明

## 0.1.8
- 优化 SLS 列出日志库工具，添加日志库类型验证，确保参数符合规范


## 0.1.7
- 优化错误处理机制，简化错误代码，提高系统稳定性
- 改进 SLS 日志服务相关工具
    - 增强 sls_list_logstores 工具，添加日志库类型验证，确保参数符合规范
    - 完善日志库类型描述，明确区分日志类型(logs)和指标类型(metrics)
    - 优化指标类型日志库筛选逻辑，仅当用户明确需要时才返回指标类型

## 0.1.6
### 工具列表
- 增加 SQL 诊断工具, 当 SLS 查询语句执行失败时，可以调用该工具，根据错误信息，生成诊断结果。诊断结果会包含查询语句的正确性、性能分析、优化建议等信息。


## 0.1.0
本次发布版本为 0.1.0，以新增工具为主，主要包含 SLS 日志服务和 ARMS 应用实时监控服务相关工具。


### 工具列表

- 增加 SLS 日志服务相关工具
    - `sls_describe_logstore`
        - 获取 SLS Logstore 的索引信息
    - `sls_list_projects`
        - 获取 SLS 项目列表
    - `sls_list_logstores`
        - 获取 SLS Logstore 列表
    - `sls_describe_logstore`
        - 获取 SLS Logstore 的索引信息
    - `sls_execute_query`
        - 执行SLS 日志查询
    - `sls_translate_natural_language_to_query`
        - 翻译自然语言为SLS 查询语句

- 增加 ARMS 应用实时监控服务相关工具
    - `arms_search_apps`
        - 搜索 ARMS 应用
    - `arms_generate_trace_query`
        - 根据自然语言生成 trace 查询语句

### 场景举例

- 场景一: 快速查询某个 logstore 相关结构
    - 使用工具:
        - `sls_list_logstores`
        - `sls_describe_logstore`
    ![image](./images/search_log_store.png)


- 场景二: 模糊查询最近一天某个 logstore下面访问量最高的应用是什么
    - 分析:
        - 需要判断 logstore 是否存在
        - 获取 logstore 相关结构
        - 根据要求生成查询语句(对于语句用户可确认修改)
        - 执行查询语句
        - 根据查询结果生成响应
    - 使用工具:
        - `sls_list_logstores`
        - `sls_describe_logstore`
        - `sls_translate_natural_language_to_query`
        - `sls_execute_query`
    ![image](./images/fuzzy_search_and_get_logs.png)

    
- 场景三: 查询 ARMS 某个应用下面响应最慢的几条 Trace
    - 分析:
        - 需要判断应用是否存在
        - 获取应用相关结构
        - 根据要求生成查询语句(对于语句用户可确认修改)
        - 执行查询语句
        - 根据查询结果生成响应
    - 使用工具:
        - `arms_search_apps`
        - `arms_generate_trace_query`
        - `sls_translate_natural_language_to_query`
        - `sls_execute_query`
    ![image](./images/find_slowest_trace.png)

