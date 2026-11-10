# src/frontend

Web 前端（教务端与教师端）。按业务域组织页面，避免一个大目录平铺。

| 目录 | 职责 |
|---|---|
| `src/api/` | 接口封装，与 `docs/03_api/` 对齐 |
| `src/assets/` | 静态资源 |
| `src/components/` | 通用组件 |
| `src/layouts/` | 页面框架（侧边栏、顶栏） |
| `src/router/` | 路由与权限守卫 |
| `src/stores/` | 状态管理 |
| `src/views/dashboard/` | 首页与数据概览 |
| `src/views/exam/` | 考试管理 |
| `src/views/room/` | 考场管理 |
| `src/views/invigilator/` | 监考教师管理 |
| `src/views/constraint/` | 约束配置 |
| `src/views/scheduling/` | 排考与监考分配（核心页面） |
| `src/views/report/` | 报表导出 |
| `src/utils/` | 工具函数 |

## 约定

- 排考页面的调整操作必须**实时校验约束**，冲突就地提示到具体考试与具体约束。
- 所有时间相关的展示统一时区，避免与后端 UTC 存储混淆。
