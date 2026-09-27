# dsh-upstream-first-debug · 上游优先排障

**DSH 专用 Skill 安装包。** 第三方工具报错时，先确认实际运行版本、核对上游修复是否已发布，再决定本地修复，并通过用户实际入口验证结果。

作者 **Tzhen** · **MIT** · **v0.1.1** · 中文指令 · 独立维护，无官方背书。

## 下载并安装

**[下载 dsh-upstream-first-debug-0.1.1.zip](https://github.com/Tzhen-X/dsh-upstream-first-debug/releases/download/v0.1.1/dsh-upstream-first-debug-0.1.1.zip)**

1. 解压，把其中的 `dsh-upstream-first-debug` 文件夹放到 `~/.dsh/skills/` 下。
2. 最终路径应为 `~/.dsh/skills/dsh-upstream-first-debug/SKILL.md`，不能多嵌套一层仓库目录。`~` 是当前用户主目录；设置了 DSH_HOME 时，用该目录下的 skills。
3. 在 DSH 用户消息中输入 `/dsh-upstream-first-debug` 显式加载，或按完整名称要求 Agent 使用本技能，确认正文被读取后继续。

本包是纯 Skill，不使用 `dsh plugin add`，无需更改 profile 或安装 Node 依赖。宿主需已有文件读取、命令执行及联网能力。项目内安装可用项目根 `.dsh/skills/` 或 `.agents/skills/`；项目根为最近含 `.git` 的祖先，没有 `.git` 时使用 cwd。同名项目副本优先于用户副本。更新前备份旧技能文件夹；撤销时只移除自己安装的本技能文件夹。

## 它会检查什么

- 实际调用的是哪个可执行文件、模块或容器版本，而不只看安装记录。
- 上游修复是否已经进入正在使用的发布包，而不只看 PR 已合并。
- 相似问题的环境、关闭原因、发布状态与复验结果。
- 修复是否通过用户实际入口验证，而不只看旁路调用成功。

适用于 DSH 中使用的第三方工具与依赖，不限于 DSH 本体。自研业务代码的一般调试不触发；不会自动升级、发帖或提交 PR。模型遵守情况不由本文件强制保证。

## 验证与同源关系

最新 **DSH 0.1.7-rc.2** 官方组件已通过 v0.1.1 ZIP 的用户根、两种项目根发现、完整正文加载、工具输出及显式调用。旧基线 0.1.6-alpha.1 的用户根发现和加载也通过；详见 [VALIDATION.md](VALIDATION.md)，其中同时记录了同源通用版的验证。尚未进行独立模型效果评测，6 个合成场景仅作规则走查。

本仓库提供以 `dsh-` 命名的独立发现和下载入口，核心正文维护源为 [upstream-first-debug](https://github.com/Tzhen-X/upstream-first-debug)。两个仓库的 v0.1.1 DSH ZIP 完全一致；通用版与 DSH 版通常选择一种安装即可。

[DSH 社区约定](DSH-COMPATIBILITY.md) · [来源](SOURCES.md) · [示例](examples.md) · [MIT 许可证](LICENSE)
