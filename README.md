![架构图](/.image/common/yudao-cloud-architecture.png)

* Java 后端：JDK 17/21 + Spring Boot 3.2
* 管理后台的电脑端：Vue3 
* 管理后台的移动端：采用 [uni-app](https://github.com/dcloudio/uni-app) 方案，一份代码多终端适配，同时支持 APP、小程序、H5！
* 后端采用 Spring Cloud Alibaba 微服务架构，注册中心 + 配置中心 Nacos，定时任务 XXL-Job，服务保障 Sentinel，服务网关 Gateway，分布式事务 Seata
* 数据库可使用 MySQL、Oracle、PostgreSQL、SQL Server、MariaDB、国产达梦 DM、TiDB 等，基于 MyBatis Plus、Redis + Redisson 操作
* 消息队列可使用 Event、Redis、RabbitMQ、Kafka、RocketMQ 等
* 权限认证使用 Spring Security & Token & Redis，支持多终端、多种用户的认证系统，支持 SSO 单点登录
* 支持加载动态权限菜单，按钮级别权限控制，Redis 缓存提升性能
* 支持 SaaS 多租户，可自定义每个租户的权限，提供透明化的多租户底层封装
* 工作流使用 Flowable，支持动态表单、在线设计流程、会签 / 或签、多种任务分配方式
* 高效率开发，使用代码生成器可以一键生成 Java、Vue 前后端代码、SQL 脚本、接口文档，支持单表、树表、主子表
* 实时通信，采用 Spring WebSocket 实现，内置 Token 身份校验，支持 WebSocket 集群
* 集成微信小程序、微信公众号、企业微信、钉钉等三方登陆，集成支付宝、微信等支付与退款
* 集成阿里云、腾讯云等短信渠道，集成 MinIO、阿里云、腾讯云、七牛云等云存储服务
* 集成报表设计器、大屏设计器，通过拖拽即可生成酷炫的报表与大屏

## 🐼 内置功能

系统内置多种多种业务功能：

![功能分层](/.image/common/ruoyi-vue-pro-biz.png)

* 通用模块（必选）：系统功能、基础设施
* 通用模块（可选）：工作流程、支付系统、数据报表、会员中心
* 业务系统（按需）：ERP 系统、CRM 系统、商城系统、微信公众号、AI 大模型

🙂 所有功能，都通过 **单元测试** 保证高质量。

### 基础设施

|     | 功能        | 描述                                           |
|-----|-----------|----------------------------------------------|
| 🚀  | 代码生成      | 前后端代码的生成（Java、Vue、SQL、单元测试），支持 CRUD 下载       |
| 🚀  | 系统接口      | 基于 Swagger 自动生成相关的 RESTful API 接口文档          |
| 🚀  | 数据库文档     | 基于 Screw 自动生成数据库文档，支持导出 Word、HTML、MD 格式      |
|     | 表单构建      | 拖动表单元素生成相应的 HTML 代码，支持导出 JSON、Vue 文件         |
| 🚀  | 配置管理      | 对系统动态配置常用参数，支持 SpringBoot 加载                 |
| ⭐️  | 定时任务      | 在线（添加、修改、删除)任务调度包含执行结果日志                     |
| 🚀  | 文件服务      | 支持将文件存储到 S3（MinIO、阿里云、腾讯云、七牛云）、本地、FTP、数据库等   | 
| 🚀  | WebSocket | 提供 WebSocket 接入示例，支持一对一、一对多发送方式              | 
| 🚀  | API 日志    | 包括 RESTful API 访问日志、异常日志两部分，方便排查 API 相关的问题   |
|     | MySQL 监控  | 监视当前系统数据库连接池状态，可进行分析SQL找出系统性能瓶颈              |
|     | Redis 监控  | 监控 Redis 数据库的使用情况，使用的 Redis Key 管理           |
| 🚀  | 消息队列      | 基于 Redis 实现消息队列，Stream 提供集群消费，Pub/Sub 提供广播消费 |
| 🚀  | Java 监控   | 基于 Spring Boot Admin 实现 Java 应用的监控           |
| 🚀  | 链路追踪      | 接入 SkyWalking 组件，实现链路追踪                      |
| 🚀  | 日志中心      | 接入 SkyWalking 组件，实现日志中心                      |
| 🚀  | 服务保障      | 基于 Redis 实现分布式锁、幂等、限流功能，满足高并发场景              |
| 🚀  | 日志服务      | 轻量级日志中心，查看远程服务器的日志                           |
| 🚀  | 单元测试      | 基于 JUnit + Mockito 实现单元测试，保证功能的正确性、代码的质量等    |

![功能图](/.image/common/infra-feature.png)

### ERP 系统

演示地址：<https://cloud.iocoder.cn/erp-preview/>

![功能图](/.image/common/erp-feature.png)

## 🐨 技术栈

### 微服务

| 项目              | 说明                 |
|-----------------|--------------------|
| `dependencies`  | Maven 依赖版本管理       |
| `framework`     | Java 框架拓展          |
| `server`        | 管理后台 + 用户 APP 的服务端 |
| `module-system` | 系统功能的 Module 模块    |
| `module-infra`  | 基础设施的 Module 模块    |
| `module-erp`    | ERP 系统的 Module 模块  |

### 框架

| 框架                                                                                          | 说明               | 版本         | 学习指南                                                                |
|---------------------------------------------------------------------------------------------|------------------|------------|---------------------------------------------------------------------|
| [Spring Cloud Alibaba](https://github.com/alibaba/spring-cloud-alibaba)                     | 微服务框架            | 2023.0.1   | [文档](https://github.com/YunaiV/SpringBoot-Labs)                     |
| [Nacos](https://github.com/alibaba/nacos)                                                   | 配置中心 & 注册中心      | 2.3.2      | [文档](https://www.iocoder.cn/categories/Nacos/?yudao)                |
| [RocketMQ](https://github.com/apache/rocketmq)                                              | 消息队列             | 5.2.0      | [文档](https://www.iocoder.cn/categories/RocketMQ/?yudao)             |
| [Sentinel](https://github.com/alibaba/sentinel)                                             | 服务保障             | 1.8.6      | [文档](https://www.iocoder.cn/categories/Sentinel/?yudao)             |
| [XXL Job](https://github.com/xuxueli/xxl-job)                                               | 定时任务             | 2.4.0      | [文档](https://www.iocoder.cn/XXL-JOB/good-collection/?yudao)         |
| [Spring Cloud Gateway](https://github.com/spring-cloud/spring-cloud-gateway)                | 服务网关             | 4.1.0      | [文档](https://www.iocoder.cn/categories/Spring-Cloud-Gateway/?yudao) |
| [Seata](https://github.com/seata/seata)                                                     | 分布式事务            | 1.6.1      | [文档](https://www.iocoder.cn/categories/Seata/?yudao)                |
| [MySQL](https://www.mysql.com/cn/)                                                          | 数据库服务器           | 5.7 / 8.0+ |                                                                     |
| [Druid](https://github.com/alibaba/druid)                                                   | JDBC 连接池、监控组件    | 1.2.23     | [文档](http://www.iocoder.cn/Spring-Boot/datasource-pool/?yudao)      |
| [MyBatis Plus](https://mp.baomidou.com/)                                                    | MyBatis 增强工具包    | 3.5.7      | [文档](http://www.iocoder.cn/Spring-Boot/MyBatis/?yudao)              |
| [Dynamic Datasource](https://dynamic-datasource.com/)                                       | 动态数据源            | 4.3.1      | [文档](http://www.iocoder.cn/Spring-Boot/datasource-pool/?yudao)      |
| [Redis](https://redis.io/)                                                                  | key-value 数据库    | 5.0 / 6.0  |                                                                     |
| [Redisson](https://github.com/redisson/redisson)                                            | Redis 客户端        | 3.32.0     | [文档](http://www.iocoder.cn/Spring-Boot/Redis/?yudao)                |
| [Spring MVC](https://github.com/spring-projects/spring-framework/tree/master/spring-webmvc) | MVC 框架           | 6.1.10     | [文档](http://www.iocoder.cn/SpringMVC/MVC/?yudao)                    |
| [Spring Security](https://github.com/spring-projects/spring-security)                       | Spring 安全框架      | 6.3.1      | [文档](http://www.iocoder.cn/Spring-Boot/Spring-Security/?yudao)      |
| [Hibernate Validator](https://github.com/hibernate/hibernate-validator)                     | 参数校验组件           | 8.0.1      | [文档](http://www.iocoder.cn/Spring-Boot/Validation/?yudao)           |
| [Flowable](https://github.com/flowable/flowable-engine)                                     | 工作流引擎            | 7.0.0      | [文档](https://doc.iocoder.cn/bpm/)                                   |
| [Knife4j](https://gitee.com/xiaoym/knife4j)                                                 | Swagger 增强 UI 实现 | 4.5.0      | [文档](http://www.iocoder.cn/Spring-Boot/Swagger/?yudao)              |
| [SkyWalking](https://skywalking.apache.org/)                                                | 分布式应用追踪系统        | 9.0.0      | [文档](http://www.iocoder.cn/Spring-Boot/SkyWalking/?yudao)           |
| [Spring Boot Admin](https://github.com/codecentric/spring-boot-admin)                       | Spring Boot 监控平台 | 3.6.1      | [文档](http://www.iocoder.cn/Spring-Boot/Admin/?yudao)                |
| [Jackson](https://github.com/FasterXML/jackson)                                             | JSON 工具库         | 2.17.1     |                                                                     |
| [MapStruct](https://mapstruct.org/)                                                         | Java Bean 转换     | 1.6.3      | [文档](http://www.iocoder.cn/Spring-Boot/MapStruct/?yudao)            |
| [Lombok](https://projectlombok.org/)                                                        | 消除冗长的 Java 代码    | 1.18.34    | [文档](http://www.iocoder.cn/Spring-Boot/Lombok/?yudao)               |
| [JUnit](https://junit.org/junit5/)                                                          | Java 单元测试框架      | 5.10.1     | -                                                                   |
| [Mockito](https://github.com/mockito/mockito)                                               | Java Mock 框架     | 5.7.0      | -                                                                   |
