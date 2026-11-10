# 后端

Java + Spring Boot + MySQL，Maven 工程。当前为工程骨架。

业务围绕基础数据、教学任务、排课执行、手动调整和课表查询。求解器采用遗传算法，包含初始化、评价、选择、交叉、变异与冲突修复，与 Web 和数据库解耦；统一校验器供自动排课、人工调整和发布复查共用。

Maven 工程名为 `course-scheduling`，既有包名 `wiki.yuhang.examscheduling` 暂保留，待实际业务代码落地时统一。
