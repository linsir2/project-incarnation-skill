# project-incarnation

[English README](./README.md)

`project-incarnation` 是一个 skill，用来把 repo、框架、SDK、方法论或已有 skill 蒸馏成一个可复用的技术人格。

它的目标不是生成摘要、角色卡，或者一堆旁路文件。它要产出的是一份高密度 `SKILL.md`，把这个对象真实的判断方式保留下来。

## 为什么要有这个 Skill

大多数生成出来的 skill 会坏在两件事上：

- 只是重写文档，没有提炼判断
- 只学到了语气，没有保留边界、取舍和证据路径

`project-incarnation` 的存在，就是为了避开这两种失败。

它会强制生成结果带上这些东西：

- 这个对象到底在保护什么真相
- 它会本能反对什么
- 它先查什么证据
- 它接受什么取舍
- 它什么时候应该 abstain
- 什么变化会触发更新

## 你会得到什么

最终产物是一个子 skill，通常写到：

```text
<repo>/skills/<slug>/SKILL.md
```

一个强的生成结果通常应该包含：

- 判断晶体
- 决策启发式
- 默认反对项
- 诚实边界
- 证据锚点
- 误判警报
- watchlist 触发器

像 `.codex/`、`.claude/` 这样的工具私有目录只是 adapter 路径，不再是 canonical 默认输出。

## 安装

手动安装到 Codex：

```bash
mkdir -p ~/.codex/skills/project-incarnation
cp /path/to/project-incarnation-skill/SKILL.md \
  ~/.codex/skills/project-incarnation/SKILL.md
```

或者通过 Skills CLI 从 GitHub 安装：

```bash
npx skills add linsir2/project-incarnation-skill -a codex -g -y
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
$project-incarnation 升级这个已有 skill，补上证据锚点、边界和更新触发器
```

## 最佳输入

如果你能提供下面这些信息，结果通常会最好：

- 本地仓库路径或 GitHub URL
- 框架、SDK、技术栈或方法论名称
- 现有 `SKILL.md`，如果你是在做升级
- 你关心的版本或分支
- 未来子 skill 主要要回答的问题类型
- 关键文档、PR、release notes 或 maintainer 写作

## 什么算是好的输出

一个强的生成结果，应该能让下游 agent 回答：

- 它到底在保护什么？
- 它本能会反对什么？
- 它先看什么证据？
- 它接受什么取舍？
- 它什么时候应该 abstain？
- 什么事件会迫使它更新？

如果生成出来的 skill 只是“听起来聪明”，却不会反对坏方案，那它还没有完成。

## License

MIT。见 [LICENSE](./LICENSE)。
