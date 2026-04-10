# project-incarnation

[English README](./README.md)

`project-incarnation` 用来把 repo、框架、SDK、方法论或已有 skill 蒸馏成一个可复用的技术人格。

它产出的不是摘要，也不是 bundle。它要生成的是一份高密度 `SKILL.md`，把这个对象真实的判断方式保留下来：它保护什么、反对什么、先查什么证据、什么时候应该闭嘴，以及在什么变化发生时必须重查。

## 这个 Skill 会做什么

`project-incarnation` 激活后，核心工作是：

- 判断当前要蒸馏的对象类型：项目、技术栈、方法论，还是已有 skill
- 从文档、代码、测试、release、maintainer 写作和真实摩擦中收集证据
- 提炼判断晶体、决策启发式、默认反对项、边界、内在张力和 watchlist 触发器
- 渲染一个单文件、自包含的子 `SKILL.md`
- 直接把这个子 skill 安装到 runtime 可发现的 skill root
- 避免重新回到 bundle 式输出和工具私有脚手架

## 什么时候用

适合这些场景：

- 把代码库蒸馏成一个可复用的工程视角
- 把框架或 SDK 压成一个有判断力的 skill
- 把方法论压成一个能参与规划和评审的 skill
- 升级一个“有口吻但证据、边界、预测力很弱”的旧 skill

## 产出与安装行为

最终产物是一个子 skill，默认行为是蒸馏完成后立即安装。

推荐的 runtime skill root：

```text
<project-root>/.agents/skills/<slug>/SKILL.md
<project-root>/.codex/skills/<slug>/SKILL.md
$CODEX_HOME/skills/<slug>/SKILL.md
~/.codex/skills/<slug>/SKILL.md
```

默认优先级：

1. 如果项目里已经有 `.agents/skills/`，优先安装到这里。
2. 否则如果项目里已经有 `.codex/skills/`，安装到这里。
3. 否则如果当前处于明确项目根内，默认创建并安装到 `.agents/skills/`。
4. 如果当前不在明确项目根内，则回退到 `$CODEX_HOME/skills/`，再回退到 `~/.codex/skills/`。

普通 `./skills/` 目录不再是 canonical 默认落点。只有在用户明确要求“只导出、不安装”时才使用它。

一个强的生成结果通常应该包含：

- 它在保护什么真相
- 判断晶体
- 决策启发式
- 默认反对项
- 诚实边界
- 证据锚点
- 误判警报
- watchlist 触发器

## 安装这个 Skill

手动安装到首选 runtime root：

```bash
mkdir -p ~/.agents/skills/project-incarnation
cp /path/to/project-incarnation-skill/SKILL.md \
  ~/.agents/skills/project-incarnation/SKILL.md
```

如果你要兼容 Codex 专用 runtime root，也可以安装到：

```bash
mkdir -p ~/.codex/skills/project-incarnation
cp /path/to/project-incarnation-skill/SKILL.md \
  ~/.codex/skills/project-incarnation/SKILL.md
```

通过 Skills CLI 从 GitHub 安装：

```bash
npx skills add linsir2/project-incarnation-skill
```

## 怎么使用

显式调用：

```text
$project-incarnation <你的请求>
```

例子：

```text
$project-incarnation 把这个仓库蒸馏成一个能捕捉 maintainer judgment 的 skill
```

```text
$project-incarnation 把 FastAPI 蒸馏成一个聚焦 API 契约设计和生产边界的高知识密度 skill
```

```text
$project-incarnation 升级这个已有 skill，补强证据、边界和更新触发器
```

## 最佳输入

如果你能提供下面这些信息，结果通常会最好：

- 本地仓库路径或 GitHub URL
- 框架、SDK、技术栈或方法论名称
- 现有 `SKILL.md`，如果你是在做升级
- 你关心的版本或分支
- 未来子 skill 主要要回答的问题类型
- 关键文档、PR、release notes 或 maintainer 写作

## 仓库内容

这个仓库故意保持最小化：

- [`SKILL.md`](./SKILL.md)：skill 本体
- [`README.md`](./README.md)：英文说明
- [`README.zh-CN.md`](./README.zh-CN.md)：中文说明

## License

MIT。见 [LICENSE](./LICENSE)。
