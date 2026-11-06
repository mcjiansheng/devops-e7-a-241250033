# E7 A：谢浩天 241250033

A09 组，BuildChecker 依赖检测、故障验证、CI 与合并门禁。

实验主机：`DevOps` / `60.204.240.40`，Ubuntu 云服务器。个人工作目录：`/root/241250033/e7-a`。GitHub Actions 使用同一主机上的 `devops-241250033` self-hosted runner。

- [个人贡献](CONTRIBUTIONS.md)
- [环境适配](STATE.md)
- [个人实验报告](REPORT-241250033.md)
- [验收记录](E7验收记录-241250033.csv)
- [关键证据](evidence/241250033-20261106/)

## 在服务器复跑

在独立的新结果目录执行，镜像使用个人标签：

```bash
python3 scripts/lab_cloud.py doctor
python3 -m unittest discover -s tests/e7 -v
python3 scripts/lab_cloud.py build --image e7-buildchecker:241250033 --out work/build-repeat --build-timeout 1200
python3 scripts/lab_cloud.py gate --image e7-buildchecker:241250033 --out work/gate-repeat
```

E5、E6 的原始结果保留在 `/root/241250033/buildchecker/e5/reference-a/work/`，本项目沿用 E6 个人新增的依赖一致性测试。

门禁共八项：服务测试、原始检测三次、修复复检、构建失败、多输出任务和超时。全部场景符合各自预期后，整体退出 0。完整 `work/` 单独打包，仓库保存报告和关键证据索引。

2026-11-06 已完成：服务器 oracle 8 项、服务 17 项、门禁 8 项通过；CI 正常、失败、拒绝合并、恢复与同一 PR 合并全部有记录。
