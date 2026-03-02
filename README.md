# 🔗 ShortURL Pro — 短链接服务系统 (后端)

[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.4.3-brightgreen)](https://spring.io/projects/spring-boot)
[![Java](https://img.shields.io/badge/Java-17-orange)](https://www.oracle.com/java/)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-blue)](https://www.mysql.com/)

> **浙江理工大学 - 数字化共享生产实践课程指导文档项目实现**
> 
> 本项目是 ShortURL Pro 短链接服务系统的后端部分，负责提供短链接生成的核心算法、RESTful 管理接口以及高效的 302 重定向服务。

---

## 🛠️ 技术栈

- **框架**: Spring Boot 3.4.3 (Java 17)
- **持久层**: Spring Data JPA (Hibernate)
- **数据库**: MySQL 8.0+
- **工具**: Lombok, Maven
- **核心算法**: 自定义 Base62 随机 8 位短码生成逻辑

---

## 🚀 快速开始

### 1. 环境准备
确保你的本地环境已配置：
- JDK 17+
- Maven 3.6+
- MySQL 8.0+

### 2. 数据库初始化
在 MySQL 中运行以下脚本创建数据库：
```sql
CREATE DATABASE IF NOT EXISTS short_url_db 
DEFAULT CHARACTER SET utf8mb4 
COLLATE utf8mb4_general_ci;

### 3. 修改配置文件
找到 src/main/resources/application.properties，填入你的数据库账号密码：
