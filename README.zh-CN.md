# project-incarnation

[English](./README.md)

`project-incarnation` 是一个 skill，用来把 repo、框架、SDK、方法论或已有 skill 蒸馏成一个高知识密度的 `SKILL.md`。

它是一个 authoring skill。它的目标是把对象的真实判断压缩成一个可复用的子 skill，而不是生成 bundle 或一堆旁路元数据。

## 它产出什么

最终产物是一个子 skill，通常写到：

```text
<repo>/skills/<slug>/SKILL.md
```

一个合格的生成结果通常应该包含：

- 它在保护什么真相
- 反复出现的判断晶体
- 默认反对项与取舍
- 边界与 abstain 规则
- 证据锚点
- 更新触发器与误判警报

像 `.codex/`、`.claude/` 这样的工具私有目录只是 adapter 路径，不再是 canonical 默认输出。

## 安装

手动安装到 Codex：

```bash
mkdir -p ~/.codex/skills/project-incarnation
cp /path/to/project-incarnation-skill/SKILL.md \
  ~/.codex/skills/project-incarnation/SKILL.md
```

通过 Skills CLI 从 GitHub 安装：

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

这个 skill 在下面这些输入下效果最好：

- 本地仓库路径或 GitHub URL
- 框架、SDK、技术栈或方法论名称
- 现有 `SKILL.md`，如果你要做升级
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

如果生成出来的 skill 只是“听起来聪明”，却不会反对坏方案，那它就还没完成。

## License

MIT。见 [LICENSE](./LICENSE)。
