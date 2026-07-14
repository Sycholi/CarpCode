# CarpCode

`carpcode` 是用于通用软件工程任务的 Codex 技能。它要求先明确改动范围，再进行小范围实现，并按风险完成测试和检查。

## 安装

在 Codex 中输入：

```text
使用 skill-installer 从 Sycholi/CarpCode 仓库根目录安装 carpcode 技能。
```

也可以在终端运行 Codex 自带的安装脚本：

```bash
python "${CODEX_HOME:-$HOME/.codex}/skills/.system/skill-installer/scripts/install-skill-from-github.py" \
  --repo Sycholi/CarpCode \
  --path . \
  --name carpcode
```

安装完成后，在下一轮 Codex 对话中使用该技能。若本地已存在同名技能，安装程序会停止，避免覆盖原文件。

## 适用任务

- 功能实现、缺陷修复和代码重构
- 代码审查、测试编写和构建修复
- 需要控制改动范围并保护现有行为的软件工程任务
- 生物医学软件包、分析流程和工具仓库的工程开发

一次性的生物医学 R 或 Python 数据分析应使用 `biocarp`。只有涉及软件包、程序库、流程软件或仓库工程时，才同时使用 `carpcode`。

## 使用方法

在 Codex 中直接说明任务，例如：

```text
使用 carpcode 修复这个仓库中的测试失败，保留现有公开接口，并运行相关测试。
```

```text
使用 carpcode 审查当前分支的改动，重点检查行为变化、边界条件和测试缺口。
```

## 工作原则

- 修改前检查仓库说明、现有行为、测试和工作区状态
- 只实现满足当前需求所需的改动
- 保留既有结构、命名、接口和用户的无关修改
- 根据任务风险运行测试、构建、静态检查或直接验证
- 明确报告修改文件、原因、验证结果和未解决问题
