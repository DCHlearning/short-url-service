ShortURL Pro — 短链接服务系统（后端）
本专案为 浙江理工大学-数字化共享生产实践课程 的后端实现部分。采用 Spring Boot 框架开发，为前端提供短链接的生成、管理 API，并实现核心的 302 重定向功能。
1. 环境要求
在运行本专案之前，请确保你的本地环境已安装以下工具：
Java SDK: JDK 17 (LTS 版本)
构建工具: Apache Maven 3.6.0 或更高版本
数据库: MySQL 8.0 或更高版本
IDE: IntelliJ IDEA (推荐使用)
2. 数据库配置
创建数据库：
在 MySQL 中执行以下 SQL 语句创建数据库：
code
SQL
CREATE DATABASE IF NOT EXISTS short_url_db DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
修改配置：
打开 src/main/resources/application.properties，修改数据库连接信息：
code
Properties
spring.datasource.username=你的用户名 (通常是 root)
spring.datasource.password=你的密码
3. 启动说明
导入项目：使用 IntelliJ IDEA 打开项目，等待 Maven 依赖自动下载完成（若下载缓慢，请参考文档配置阿里云镜像）。
运行项目：找到 org.example.shorturlservice.ShortUrlServiceApplication 类，右键点击 Run 启动。
服务端口：后端服务默认运行在 http://localhost:8080。
4. 核心功能实现
302 重定向：访问 http://localhost:8080/{shortCode} 将自动跳转至原始长链接。
RESTful APIs：
GET /api/shortlinks：获取短链接列表（支持按名称搜索）。
POST /api/shortlinks/generate：输入长链接和名称，生成唯一短码。
PATCH /api/shortlinks/{id}/status：启用或禁用指定的短链接。
DELETE /api/shortlinks/{id}：删除短链接。
JPA 自动建表：程序启动后会自动在 short_url_db 中创建 short_urls 表，无需手动执行 DDL 脚本。
5. 项目结构
code
Text
src/main/java/org/example/shorturlservice/
├── controller/    # 控制层：处理 REST 请求及 302 跳转
├── service/       # 业务层：实现 Base62 短码生成算法及点击计数逻辑
├── entity/        # 实体层：对应数据库 short_urls 表
├── repository/    # 持久层：JPA 数据库操作接口
└── ShortUrlServiceApplication.java # 项目启动类
6. 联调说明（与前端配合）
前端入口：演示页 /demo，管控后台 /admin。
跨域处理：前端 Vite 已配置 Proxy 代理，所有 /api 开头的请求将自动转发至本后端。
防重复提交：后端接口配合前端 loading 状态，确保生成短码操作的唯一性与稳定性。
7. 注意事项
若访问接口时弹出登录窗口，请在 ShortUrlServiceApplication.java 中确认已配置 exclude = { SecurityAutoConfiguration.class }。
短码生成采用 Base62 算法，生成 8 位长度的随机字符串，理论支持百亿级数据不重复。
