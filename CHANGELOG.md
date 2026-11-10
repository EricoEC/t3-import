# 更新日志 (CHANGELOG)

所有对本项目的关键更新与重要修复都将记录于此。

---

## [0.5.0] - 2026-11-10

### 🚀 新增特性与核心适配 (Features & Enhancements)
- **支持 T3 Code 最新 V2 架构与高版本迁移**：
  - 自动识别并默认适配 T3 Code 主数据库 `~/.t3/userdata/statev2.sqlite`（兼容历史旧版 `state.sqlite`）。
  - 移除对 T3 迁移版本 53 的硬编码死锁限制，全面支持 Migration 76+。
  - 解除对已废弃的 `projection_state` 表的强制检查依赖，平滑兼容 T3 V2 的最新架构。
  - 增加 V2 投影层双写支持：导入时自动同步写入 `orchestration_v2_projection_threads` 和 `orchestration_v2_projection_messages`，确保 T3 启动后侧边栏、对话列表和全文检索（FTS）开箱即用，瞬间可见。
- **全界面简体中文汉化 (Localization)**：
  - **TUI 交互终端全汉化**：会话选择列表、多选/单选操作指南、状态提示、确认与替换面板全部中文化。
  - **CLI 命令行帮助全汉化**：`doctor`、`list`、`import`、`sync`、`replace`、`cache` 等子命令及参数说明全部采用清晰易懂的简体中文。
  - 关键安全提示本地化：突出显示“操作前必须关闭 T3 Code”及“数据库快照安全备份已创建”等安心提示。

### 🛡️ 稳定性与体验 (Reliability & UX)
- 优化数据库预演检测（`doctor`）：准确报告当前活动数据库路径、事件总数、迁移版本及源端会话统计。
- 保留完整的数据库自动备份回退机制（VACUUM 快照）。
