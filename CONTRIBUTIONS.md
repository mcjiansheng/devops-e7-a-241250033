# 个人贡献

学生：谢浩天，学号 241250033，A09 组，E7 A。

## 参考实现来源

本项目基于用户提供的课程参考包 `DevOps_E7_Student_Cloud.zip`（整理日期 2026-11-05）。参考包中的 buildchecker 核心算法、容器运行方式、E7 gate 脚本及原有测试继续沿用。检测核心算法未改。

## E6 个人工作沿用

从本人 E6 提交 `8ba60482da7f2140026c40660b55c7b39b974c0c` 迁入 `services/buildchecker/tests/test_fullcheck.py` 中的 `test_matching_dependencies_have_no_findings_and_preserve_graphs_and_job`。该用例检查声明依赖与实际读取一致时 findings 为空，同时保留声明图、实际图、证据 PID 和进程 job 归属。参考包的其他测试保留。

E6 完整最终提交为 `Lee-bx-06/devops-2026` 的 `2f776cd13b62ea22d960046e5ccc4e83b7934e52`。

## E7 本次新增

- `scripts/doctor.py`：将本组最低内存改为 1.5 GiB，适配教师分配的 2 GiB 主机（系统实际报告约 1.7 GiB），保留真实资源报告和建议阈值。
- `tests/e7/test_e7_a_gate.py`：新增“多一条 finding 拒绝”和“缺失 evidence 拒绝”两个行为测试。E7 oracle 用例由 6 条增至 8 条，gate 实现未改。
- `STATE.md`：记录资源阈值适配原因和恢复条件。

## 协作与执行记录

Codex 协助编写代码、执行命令及整理材料。个人新增与参考实现按上文区分。

本次实验与测试统一在 `60.204.240.40` 的 `/root/241250033/e7-a` 执行。本次修改尚待服务器运行验证，测试结果、运行时间和产物以服务器后续生成的日志为准。

构建网络适配：移除未使用扩展语法的外部 Dockerfile frontend 指令；基础镜像使用服务器已有的 DaoCloud 地址，固定 SHA-256 不变。首次 Docker Hub 解析超时日志保留在 work/build-20261106-01。
