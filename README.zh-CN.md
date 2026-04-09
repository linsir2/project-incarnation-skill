# project-incarnation

[English](./README.md)

`project-incarnation` 是一个 skill，用来把 repo、框架、SDK、工程方法论或已有 skill 蒸馏成一个高知识密度的 `SKILL.md`。

它的目标很窄也很硬：把一个对象的真实判断压缩进一个自包含文件里，让下游 agent 能直接拿它做推理，而不是只会“像它说话”。

## 快速开始

手动安装到 Codex：

```bash
mkdir -p ~/.codex/skills/project-incarnation
cp /path/to/project-incarnation-skill/SKILL.md \
  ~/.codex/skills/project-incarnation/SKILL.md
```

或者直接从 GitHub 用 Skills CLI 安装：

```bash
npx skills add linsir2/project-incarnation-skill -a codex -g -y
```

显式调用：

```text
$project-incarnation 把这个仓库蒸馏成一个能复现 maintainer judgment 的 skill
```

## 这个 Skill 产出什么

最终产物是一个子 skill：

```text
.codex/skills/<slug>/SKILL.md
```

这个子 skill 应该包含：

- 它在保护什么真相
- 反复出现的判断晶体
- 默认反对项与取舍
- 边界与 abstain 规则
- 证据锚点
- 更新触发器与误判警报

这个 skill **不会**去生成 bundle 或一堆旁路文件，例如：

- `constitution.yaml`
- `sources.jsonl`
- `bundle-spec.json`
- `evals.md`

## 适合什么场景

适合在这些场景里使用：

- 把本地 repo 蒸馏成一个可复用的工程视角
- 把框架或 SDK 压成一个有判断力的 skill
- 把工程方法论压成一个可被调用的 agent skill
- 升级一个“有口吻但没证据”的旧 skill
- 生成一个可用于规划、评审、迁移或设计讨论的技术人格

## 这个 Skill 怎么工作

它遵循一条严格流水线：

1. 先判断输入对象是 repo、技术栈、方法论还是已有 skill。
2. 锁定四个锚点：对象、保护的真相、问题域、不负责什么。
3. 从代码、文档、维护者写作、release 历史和真实摩擦里收集证据。
4. 提炼判断晶体、启发式、默认反对项、内在张力、边界和 watchlist。
5. 先过密度闸门，再渲染。
6. 输出一个单文件、自包含的 `SKILL.md`。

如果产物还需要依赖额外文件来解释它怎么想，那就说明蒸馏失败了。

## 仓库结构

```text
./
├── LICENSE
├── README.md
├── README.zh-CN.md
└── SKILL.md
```

这个仓库是故意压平的。公开发布面只有一个英文版 `SKILL.md`，再加上中英文说明文档。

## 翻译审核

当前英文版 `SKILL.md` 在仓库压平前，已经对照原中文稿做过语义审核。

审核重点包括：

- 范围
- phase 顺序
- 证据要求
- 渲染契约
- 验证清单
- 更新协议
- 禁忌项

也就是说，英文版不是“简化改写”，而是按契约层面保真翻译的版本。

## 安装

### 方式 1：手动安装到 Codex

把根目录的 skill 文件复制到本地 Codex skills 目录：

```bash
mkdir -p ~/.codex/skills/project-incarnation
cp /path/to/project-incarnation-skill/SKILL.md \
  ~/.codex/skills/project-incarnation/SKILL.md
```

安装新 skill 后，重启 Codex 让它重新加载 skills。

### 方式 2：通过 Skills CLI 安装

直接从 GitHub 安装：

```bash
npx skills add linsir2/project-incarnation-skill -a codex -g
```

无交互安装：

```bash
npx skills add linsir2/project-incarnation-skill -a codex -g -y
```

如果只想看这个仓库里有哪些 skill，不真正安装：

```bash
npx skills add linsir2/project-incarnation-skill -a codex -g -l
```

不需要把这个 skill 本体发成 npm 包。`skills` 是安装器，skill 本身是通过 GitHub 仓库分发的。

## 怎么调用这个 Skill

安装后，最稳妥的调用方式是显式按名字调用：

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

## 什么输入最容易出好结果

它在这些输入下效果最好：

- 本地仓库路径
- GitHub 仓库 URL
- 框架、SDK 或技术栈名称
- 现有 `SKILL.md`
- 你关心的问题域的一段简短描述

如果你还能补充这些信息，结果通常会更好：

- 对象的版本或分支
- 未来这个子 skill 主要要回答什么问题
- 它明确不该回答什么
- 关键文档、PR、release notes 或 maintainer essay

## 什么算是好的输出

一个强的生成结果，应该能让下游 agent 回答这些问题：

- 它到底在保护什么？
- 它本能会反对什么？
- 它先看什么证据？
- 它接受什么取舍？
- 它什么时候应该 abstain？
- 什么事件会迫使它更新？

如果生成出来的 skill 只是“听起来聪明”，却不会反对坏方案，那它就还没完成。

## 怎么使用生成出来的子 Skill

`project-incarnation` 生成出来的子 skill，适合拿去做：

- 架构评审
- 规划和设计讨论
- 取舍分析
- 迁移建议
- 带对象判断力的代码审查

典型使用模式是：

1. 先用 `project-incarnation` 蒸馏对象。
2. 安装生成出来的子 skill。
3. 在后续工作里直接调用那个子 skill。

`project-incarnation` 是 authoring skill。生成出来的子 skill 才是可复用的 judgment artifact。

## 怎么更新一个生成出来的子 Skill

更新流程建议是：

1. 先读现有 `SKILL.md`。
2. 除非证据变了，否则保留稳定内核。
3. 刷新版本敏感层、maintainer stance、release 影响和争议变化。
4. 只有在现实发生变化时才改误判警报和 watchlist。
5. 除非原骨架本身错了，否则不要整份重写。

## 发布这个仓库到 GitHub

先创建一个空 GitHub 仓库，然后执行：

```bash
cd /path/to/project-incarnation-skill
git remote add origin git@github.com:<owner>/<repo>.git
git push -u origin main
```

如果你习惯 HTTPS：

```bash
git remote add origin https://github.com/<owner>/<repo>.git
git push -u origin main
```

## skills.sh 和 `npx skills`

当前这条分发路径是：

1. 把 skill 发布到一个 GitHub 仓库。
2. 在根目录暴露一个有效的 `SKILL.md`。
3. 通过 `npx skills add <owner>/<repo> -a codex -g` 安装。
4. 通过安装行为被 skills 生态发现。

所以“支持 skills.sh”，本质上就是“让这个 GitHub 仓库可以被 skills CLI 正常发现和安装”。

## 当前验证状态

这个仓库目前已经验证到这些程度：

- `git push -u origin main` 已成功推送到 `https://github.com/linsir2/project-incarnation-skill.git`
- `npm view skills version` 已成功返回 `1.4.9`
- `npx -y skills --help` 已正常执行
- `npx -y skills add linsir2/project-incarnation-skill -a codex -g -l` 已成功发现 1 个 skill：`project-incarnation`

当前唯一还没有在这台机器上做的是“真正安装进本地 agent 目录”，因为那会直接改动当前环境的 skill 配置。

## License

这个仓库使用 MIT License。见 [LICENSE](./LICENSE)。
