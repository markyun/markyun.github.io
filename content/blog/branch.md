---
title: Git 仓库的分支 (Branch) 规范
date: 2018-11-27 19:31:30
tags: ["Git", "代码管理", "规范"]
series: ["Specification"]
category: ["blog"]
featured: true

---

## 分支 (Branch) 规范

分支主要分为**master, develop(development), feature, release, hotfix** 这几类，另外还有一个仅日常/预发部署时有效的**sprint**分支，并在其基础上做了扩展，最终是 git-flow + CR 的组合方式。

**Tag (标签 | 里程碑）：**
便于开发成员识别项目的每个**标记**版本。

**master（master branch）：**
主干分之是已生产环境当前运行的代码，即可安全运行的稳定分支，处于 (production-ready) 状态，hotfix 需求从此分支拉取。禁止直接代码提交，避免被污染，仅用于代码合并和归集，在这个分支上的代码应该永远是可用、稳定的。当需要拉一个新开发分支时，应该基于 master。

**开发分支（develop || development branch）：**
该分支上会包含所有已开发、联调、测试完毕，进入可发布状态的功能，每个开发人员都在这个分支上保持线性的持续小步迭代，开发新功能的分支从此分支拉取。正常的 CodeReview WorkFlow 和开发级的自动 CI 也在这里进行。当开发完一个迭代 (Sprint)，开发团队完成后转测试时，就将代码合并到 release 分支，并要求打一个 alpha 级的 Tag(如 1.1.0-alpha)。

**功能分支（feature branch）：**
开发人员对某个功能完成后，会提交到这个分支，feature 拆分的粒度依据功能的独立性来判断。原则上一个 feature 分支仅且必须包含一个可独立发布的完整功能。该分支上的内容处于 WIP（Work in progress）可能功能还未完成、未进行联调等，当开发完毕并且通过了日常、预发环境联调测试，前后端代码都已准备就绪，进入可发布阶段时，feature 会被合并到 develop 上并删除 feature。

**预发分支（release branch）：**
用于发布过程的分支，包括开发转测 (实际上我们认为这里的测试集成测试)、测试和 BugFix 以及发布上线的过程。release 分支的基点一定为某一时刻的 develop 分支，release 分支原则上不允许进行功能性提交，仅可进行上线前验证出的问题的修复。当生产发布完成后，release 分支会被同时合并到 master 与 develop 分支上，并删除 release 分支

**补丁分支（hotfix branch）：**
修复线上问题专用，当出现线上 Bug 需要 hotfix 时，等不及 release 版本了！必须马上修复上线，我们需要在上次上线的 master 版本拉一个临时的分支（hotfix 热修复分支\*\* \*\*），fix bug 后该分支会被同时合并到 master 与 develop 分支上，并删除 hotfix 分支。

**聚合分支（sprint）**
sprint 分支为部署日常/预发环境使用的临时聚合分支（在 aone 适用），目的是实现在同一套日常/预发环境上，部署多个 feature 分支功能，实现多个 feature 并行联调&测试的能力，sprint 分支仅发布责任人需要关注，
sprint 分支从 develop 分支开始，合并入需要联调的 feature 分支代码，部署到日常 CDN 环境

## Git-flow 模型

Git Flow 是构建在 Git 之上的一个组织软件开发活动的模型，是在 Git 之上构建的一项软件开发最佳实践。Git Flow 是一套使用 Git 进行源代码管理时的一套行为规范。

个人分支结合了 CR 后产生的，开发人员在参与 feature 分支、hotfix 分支的开发过程中，不直接提交代码到分支上，而是“每次”从“最新”的 feature/hotfix 分支上拉取新的个人分支，完成一个小功能点的开发后，通过 gitlab 提交 MR，在完成了 CR 后，由代码审核人通过 MR 并合并入对应的 feature/hotfix 分支。以小步前进的方式，最终让 feature/hotfix 分支完成完整功能的迭代。

**Git Flow 代码分支管理模型**

![](https://cdn.nlark.com/yuque/0/2018/png/203859/1544518039819-350d0617-17d2-4486-8b48-bbb17127507d.png#averageHue=%23f1f1f1&height=990&id=QuF7I&originHeight=1524&originWidth=1150&originalType=binary&ratio=1&rotation=0&showTitle=false&status=done&style=none&title=&width=747)
团队定制模型参考
![](https://cdn.nlark.com/yuque/0/2018/png/203859/1544509718208-5aa10e94-aa08-4780-9c9c-cc027c6c2821.png#averageHue=%23f7f7f7&height=373&id=IBQBK&originHeight=1102&originWidth=2206&originalType=binary&ratio=1&rotation=0&showTitle=false&status=done&style=none&title=&width=747)

参考资料：
[https://nvie.com/posts/a-successful-git-branching-model/](https://nvie.com/posts/a-successful-git-branching-model/)
[http://www.ituring.com.cn/article/56870](http://www.ituring.com.cn/article/56870)
