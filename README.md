

```markdown
# 🔗 ShortURL Pro — 短链接服务系统 (全栈集成版)

[![Spring Boot](https://img.shields.io/badge/Backend-Spring%20Boot%203.4-brightgreen)](https://spring.io/)
[![Vue](https://img.shields.io/badge/Frontend-Vue%203.5-blue)](https://vuejs.org/)
[![MySQL](https://img.shields.io/badge/Database-MySQL%208.0-orange)](https://www.mysql.com/)
[![Vite](https://img.shields.io/badge/Build-Vite%206.0-646cff)](https://vitejs.dev/)

> **浙江理工大学 - 数字化共享生产实践课程指导文档项目实现**
> 
> 本项目是一个完整的短链接服务系统，包含前端管理后台、功能演示页以及后端核心跳转逻辑。实现了从长链接到唯一短码的映射、302重定向、数据统计及防重复提交等功能。

---

## 📺 功能演示清单

### 1. 功能演示页 (`/demo`)
- [x] **短码生成**：输入长链接 -> 点击生成 -> 获得唯一 8 位短码。
- [x] **防重点击**：点击生成按钮时进入 Loading 状态并锁定，防止连点。
- [x] **一键复制**：集成 Clipboard API，支持生成的短链接一键复制。
- [x] **真实跳转**：生成的短链支持浏览器直接访问并 302 重定向至目标地址。

### 2. 管控后台 (`/admin`)
- [x] **数据列表**：实时展示所有已创建的短链接数据。
- [x] **模糊搜索**：支持按短链接名称进行实时筛选。
- [x] **状态管控**：支持一键切换“启用/禁用”状态（禁用后短链访问失效）。
- [x] **CRUD 操作**：完整支持短链接的新增、删除及操作后的列表自动刷新。

---

## 🛠️ 环境依赖

| 组件 | 版本要求 | 说明 |
| :--- | :--- | :--- |
| **Java JDK** | 17 (LTS) | 后端运行环境 |
| **Node.js** | 18.0.0+ (LTS) | 前端编译环境 |
| **MySQL** | 8.0+ | 数据持久化存储 |
| **Maven** | 3.6+ | 后端依赖管理 |
| **Browser** | Chrome/Edge/Firefox | 建议使用现代浏览器 |

---

## 🚀 快速启动指南

### 第一步：数据库初始化 (MySQL)
1. 创建数据库：
   ```sql
   CREATE DATABASE IF NOT EXISTS short_url_db DEFAULT CHARACTER SET utf8mb4;
   ```
2. 后端启动后会自动根据 JPA 实体类生成 `short_urls` 表结构。

### 第二步：后端启动 (IntelliJ IDEA)
1. 打开 `short-url-service` 文件夹。
2. 修改 `src/main/resources/application.properties` 中的数据库 `password`。
3. 找到 `ShortUrlServiceApplication.java` 点击 **Run**。
4. 后端地址：`http://localhost:8080`

### 第三步：前端启动 (VS Code)
1. 进入目录：`cd shorturl-pro-web`
2. 安装依赖：`npm install`
3. 启动项目：`npm run dev`
4. 访问地址：`http://localhost:5173`

---

## 📂 项目结构说明

```text
ShortURL-Pro/
├── short-url-service/           # 后端 Spring Boot 项目
│   ├── src/main/java/.../
│   │   ├── controller/          # 接口层 (Admin API & Redirect)
│   │   ├── service/             # 业务层 (Base62 算法实现)
│   │   ├── entity/              # 实体层 (JPA 映射)
│   │   └── repository/          # 持久层 (Database Access)
│   └── src/main/resources/      # 配置文件 (application.properties)
│
└── shorturl-pro-web/            # 前端 Vue 3 项目
    ├── src/
    │   ├── api/                 # Axios 请求封装
    │   ├── pages/               # 页面模块 (Admin & Demo)
    │   ├── router/              # 路由配置
    │   └── utils/               # 工具类 (http 拦截器)
    ├── vite.config.ts           # 代理配置 (Proxy to 8080)
    └── package.json             # 依赖管理
```

---

## 💡 开发踩坑记录 (FAQ)

1. **无法运行 npm 脚本？**
   - 以管理员身份运行 PowerShell，执行 `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`。
2. **后端 Access Denied？**
   - 检查 `application.properties` 里的 MySQL 密码是否正确，并确保已手动创建了 `short_url_db` 库。
3. **前端找不到模块？**
   - 确保安装了 `Vue - Official` 扩展，并检查根目录下是否存在 `env.d.ts` 声明文件。
4. **Loading 效果太快？**
   - 前端代码中加入了 `await new Promise(r => setTimeout(r, 600))` 模拟延迟，以确保任务书要求的 Loading 状态肉眼可见。

---

## 👥 团队与致谢
- **课程**: 数字化共享生产实践 (ZSTU)
- **实现**: ShortURL Pro 课题组

---
© 2026 项目组版权所有。
```
