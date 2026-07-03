# Codex Video Skills

面向 AI 视频创作流程的 3 个 Codex skill 仓库，覆盖：

- `screenwriter`：剧本、剧情节拍、场景结构
- `shotlist-builder`：分镜、机位、调度、镜头组织
- `ai-video-prompt-optimizer`：多模型提示词整理、优化与双语输出

这套 skill 的目标不是单纯“一键生成”，而是更接近一个可协作的导演操作台：

- 单独调用某一个 skill 时，它可以独立工作
- 多个 skill 串联调用时，它们会尽量保持强关联的上下游关系
- 在创作过程中主动检查缺失信息，允许用户补充、确认，或选择跳过

## 中文说明

这个仓库只保留可复用的 skill 正式文件，不包含测试样例、审阅 HTML、生成图片、压缩包或临时输出。

适合的使用场景：

- 从一个想法开始，先写剧本，再拆分镜，再生成视频提示词
- 已经有剧本，只需要做 shotlist
- 已经有分镜，只需要做某个模型的 prompt package
- 需要中文交互，但最终输出希望中英双语并存

## Included Skills

### `screenwriter`

用于前期故事开发与剧本整理，强调：

- 剧情目标、角色关系、视觉事件链
- 场景节拍与时长意识
- 为下游 `shotlist-builder` 提供清晰的故事输入

位置：
[skills/screenwriter](skills/screenwriter)

### `shotlist-builder`

用于把剧本或故事事件拆成镜头执行方案，强调：

- 镜头编号与镜头功能
- 景别、机位、运动、节奏
- 人物反应、动作递进、视觉重点
- 为下游 `ai-video-prompt-optimizer` 提供 prompt-ready 结构

位置：
[skills/shotlist-builder](skills/shotlist-builder)

### `ai-video-prompt-optimizer`

用于把镜头信息整理成可投喂不同模型的提示词包，当前重点支持：

- Seedance 2.x / Seedance-fast 风格路由
- 中英双语输出
- 有参考图/参考视频时输出带 `@image` 或类似资源占位的版本
- 无资源依赖时输出 plain-text 版本

位置：
[skills/ai-video-prompt-optimizer](skills/ai-video-prompt-optimizer)

## Repository Structure

```text
skills/
  ai-video-prompt-optimizer/
    agents/
    references/
    SKILL.md
  screenwriter/
    agents/
    templates/
    tools/
    SKILL.md
  shotlist-builder/
    agents/
    reference/
    templates/
    SKILL.md
```

## Installation

### 方法 1：直接复制到 Codex skills 目录

把这 3 个目录复制到你的本地 Codex skills 目录，例如：

```text
~/.codex/skills/
  screenwriter/
  shotlist-builder/
  ai-video-prompt-optimizer/
```

Windows 常见位置示例：

```text
C:\Users\<YourName>\.codex\skills\
```

### 方法 2：克隆仓库后手动同步

```bash
git clone https://github.com/zwj870987952-maker/codex-video-skills.git
```

然后把 `skills/` 下面的三个 skill 目录复制到你的 Codex 本地 skills 目录。

## Usage Examples

### 示例 1：只调用剧本 skill

适合“我只有一个故事概念，还没成型”的情况。

示例提示：

```text
Use $screenwriter to help me write a 10-15 second hard sci-fi silent short.
请用中文和我确认缺失信息。
主角是女研究员，男研究员作为旁观者。
结尾要有震惊和发现感。
```

### 示例 2：只调用分镜 skill

适合“我已经有故事内容，只需要拆镜头”的情况。

示例提示：

```text
Use $shotlist-builder to break this story into a cinematic shotlist.
请用中文确认缺失信息，并允许我跳过不确定项。
最终我要 16:9，写实电影感，突出人物反应、道具融合过程和最后的 key reveal。
```

### 示例 3：只调用提示词 skill

适合“我已经有分镜，需要面向模型整理提示词”的情况。

示例提示：

```text
Use $ai-video-prompt-optimizer to convert my shot plan into a bilingual prompt package.
请全程中文提示我补齐信息，输出默认中英文都要。
如果有参考图，请输出带 @image 标记的版本和纯文本版本。
```

### 示例 4：串联完整流程

适合“先剧本，再分镜，再提示词”的完整创作流程。

推荐顺序：

1. `screenwriter`
2. `shotlist-builder`
3. `ai-video-prompt-optimizer`

示例流程提示：

```text
先用 $screenwriter 和我完成剧本。
剧本确认后，再调用 $shotlist-builder 基于剧本生成强关联分镜。
分镜确认后，再调用 $ai-video-prompt-optimizer 生成最终提示词包。
整个过程请用中文和我交互，持续检查缺失信息，并允许我参与关键决策。
最终输出默认中英文双语。
```

## Workflow Design

这套仓库支持两种工作方式：

### 1. 独立工作模式

当你只调用一个 skill 时，它应该能够独立完成自己的任务，不强依赖上游模块。

例如：

- 只写剧本
- 只拆分镜
- 只做提示词

### 2. 联动工作模式

当你一次创作中连续调用多个 skill 时，推荐保持如下链路：

```text
screenwriter -> shotlist-builder -> ai-video-prompt-optimizer
```

此时的要求是：

- 下游尽量继承上游已经确认的信息
- 避免重复询问已经明确的内容
- 遇到真正缺失的信息时再提示补充
- 允许用户跳过非关键项

## What Is Not Included

这个仓库有意不上传以下内容：

- 测试生成的剧本
- 测试生成的分镜
- 测试生成的 prompt package
- 审阅用 HTML 页面
- 生成的图片素材
- 本地压缩包和临时文件
- `outputs/` 目录下的过程产物

## Notes

- 当前仓库更偏向本地 Codex skill 使用场景
- `screenwriter` 与 `shotlist-builder` 以尽量保留原 skill 核心能力为原则做了规范化整理
- `ai-video-prompt-optimizer` 目前强调中文交互与默认中英双语输出

如果你希望继续扩展，下一步很适合补：

- `CONTRIBUTING.md`
- 示例项目输入/输出规范
- 更明确的模型适配说明
- 单独的 `seedance2.0` 文档或 skill 变体
