# src/backend

服务端（Java 17 + Spring Boot 4.1，Maven 工程，自带 `mvnw` wrapper）。

分层原则：**求解器与 Web、数据库解耦**——给定输入数据结构即可独立求解与测试，不读数据库、不依赖 Spring 上下文。

## 目录职责

| 目录 | 职责 |
|---|---|
| `src/main/java/.../api/v1/` | 接口层：认证、用户、考试、考场、监考教师、约束配置、排考、报表 |
| `src/main/java/.../core/` | 横切能力：安全、统一异常、请求日志 |
| `src/main/java/.../entity/` | 数据库实体 |
| `src/main/java/.../dto/` | 请求/响应模型 |
| `src/main/java/.../repository/` | 数据访问（`JdbcTemplate`，不引 ORM） |
| `src/main/java/.../service/scheduling/` | **求解器**：变量、值域、约束、求解、目标、校验、结果 |
| `src/main/java/.../service/invigilation/` | 监考分配与工作量均衡 |
| `src/main/java/.../service/export/` | 报表导出（Excel / PDF） |
| `src/main/java/.../util/` | 工具 |
| `src/main/resources/` | `application.yml` 等配置 |
| `src/test/java/...` | 单元测试；`api/` 下放接口集成测试 |
| `src/test/resources/fixtures/` | 测试夹具（小规模实例数据） |

> 与原目录规划的对应：`app/api/v1` → `api/v1`，`app/models` → `entity`，`app/schemas` → `dto`，`app/db` → `repository`，`app/utils` → `util`；`tests/unit`、`tests/integration` 合并为镜像主结构的测试包。

## 求解器约定

- 输入为纯数据结构（考试、时段、教室、教师、约束参数），与数据库无关。
- 输出为分配方案 + 指标（硬冲突数、软约束代价、耗时）。
- 每个阶段单独可测；任一步失败都要能定位到「哪一场、哪条约束」。

## 命令

```powershell
cd src/backend
.\mvnw.cmd test            # 跑测试
.\mvnw.cmd spring-boot:run # 启动服务（端口见 application.yml）
```
