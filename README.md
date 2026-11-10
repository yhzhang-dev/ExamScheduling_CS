# ExamScheduling_CS

**基于约束满足的高校考场编排与监考分配系统** —— 本科毕业设计工程仓库。

排考本质是一个多约束组合优化问题：把「考试」安排到「时段 × 教室」，再把「监考教师」匹配到每一场，同时满足学生不冲突、教室容量、教师回避与可用时段、监考均衡等条件。本项目的技术核心是约束建模与分阶段求解，而不是增删改查。

## 技术栈

| 层 | 选型 |
|---|---|
| 后端 | Java 17 + Spring Boot 4.1（Maven，`JdbcTemplate` 直接访问数据库，不引 ORM） |
| 前端 | Vue 3 + TypeScript + Vite |
| 数据库 | MySQL 8.4 |
| 求解 | 自研约束满足求解器：DSatur 着色 → FFD 装箱 → 监考匹配 → 局部搜索 |

## 目录结构

| 目录 | 用途 |
|---|---|
| `docs/` | 设计与开发文档：需求、设计、接口、数据库、部署、手册 |
| `process_materials/` | 学校要求的过程材料：任务书、开题、中期、指导记录、查重、其他 |
| `thesis/` | 论文：模板、章节、图表、文献、草稿与定稿 |
| `src/backend/` | 服务端（Java + Spring Boot，Maven 工程，自带 `mvnw`）：接口、实体、仓储、求解器、导入导出 |
| `src/frontend/` | Web 前端：教务端与教师端 |
| `src/shared/` | 前后端共享常量与类型 |
| `database/` | 建表、种子数据、迁移与备份 |
| `data/` | 测试与实验数据：原始、清洗后、导入模板 |
| `experiments/` | 算法实验：配置、脚本、结果、日志 |
| `deployment/` | 部署：Docker、Nginx、启动脚本 |
| `defense/` | 答辩材料：PPT、讲稿、演示、问答准备 |
| `final_submission/` | 最终提交包 |

## 运行方式

待源码落地后补充。预期的本地流程为：建库 → 导入种子数据 → 启动后端 → 启动前端。

```powershell
cd src/backend
.\mvnw.cmd test              # 运行测试
.\mvnw.cmd spring-boot:run   # 启动服务
```

## 当前进度

- [x] 工程目录结构与说明
- [ ] 需求规格、用例、用户故事
- [ ] 约束清单与排考模型设计
- [ ] 数据库设计与建表脚本
- [ ] 求解器实现与单元测试
- [ ] 接口与前端页面
- [ ] 实验与结果分析

## 约定

- 文档按编号前缀排序（`01_`、`02_` …），同一章节目录内不再分层。
- 数据、实验与代码分离：样本数据进 `data/`，实验结果进 `experiments/results/`，不混在源码里。
- `final_submission/` 只放定稿，不做日常存放。
- 敏感信息（数据库口令、密钥）只放 `.env`，不入库；仓库只提交 `deployment/env.example`。

## 致谢

见 [CONTRIBUTORS.md](CONTRIBUTORS.md)。
