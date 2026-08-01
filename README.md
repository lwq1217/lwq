# 后端部署与配置说明（Railway）

此后端为 Node.js + Express 最小示例，使用 PostgreSQL 作为用户存储，JWT 做简易鉴权。

快速在 Railway 上部署：
1. 前往 https://railway.app 并登录（支持 GitHub 账户）。
2. New Project -> Deploy from GitHub repo，选择本仓库（lwq1217/lwq）。
3. 在 Configure 阶段，确保服务根目录为仓库根并保留默认启动命令：`npm install && npm start`。
4. 添加 PostgreSQL 插件（Railway 会提供 DATABASE_URL）。
5. 在 Railway -> Settings -> Variables 添加：
   - DATABASE_URL
   - JWT_SECRET（生成一个强随机字符串）
   - ALLOWED_ORIGIN（例如 https://lwq1217.github.io）
6. 部署完成后，Railway 会给出后端 URL（例如 https://your-backend.up.railway.app）。
7. 在 Railway 的数据库控制台运行 sql/init.sql 创建 users 表，或通过 psql 运行该 SQL 文件。
8. 在前端仓库（lwq1217.github.io）的 index.html 中将 `window.API_BASE_URL` 替换为上述后端 URL。

注意：该示例在生产中需改进 token 存储（用 HttpOnly cookie）、添加刷新 token、邮件验证和速率限制等安全措施。
