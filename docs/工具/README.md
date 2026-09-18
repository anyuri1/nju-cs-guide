# 工具

工具的价值不在“专业”，而在少打断。命令行、版本控制、调试器和文档写作越早变成习惯，后面的课程、科研和实习越省力。

## 终端、Git、编辑器

- [The Missing Semester of Your CS Education](https://missing.csail.mit.edu/)（[中文](https://missing-semester-cn.github.io/)）：Shell、编辑器、Git、调试、自动化。挑眼下要用的一讲，不必顺序看完。
- [Pro Git](https://git-scm.com/book/zh/v2)：Git 官方免费书；至少读“起步”“基础”“分支”。
- [Learn Git Branching](https://learngitbranching.js.org/?locale=zh_CN)：可视化练分支、合并和 rebase。
- [GitHub Skills](https://skills.github.com/)：在真实仓库里练 Issue、Pull Request 和 Actions。
- [VS Code 文档](https://code.visualstudio.com/docs) 与 [Remote SSH](https://code.visualstudio.com/docs/remote/ssh)：先保持配置简单，缺什么再装什么。

先做到：会从终端运行程序；会读 `git status`；每个可工作的改动单独 commit；知道怎样回到一个旧版本。花哨的终端主题可以以后再说。

## 调试、编译与构建

- [GDB 文档](https://sourceware.org/gdb/current/onlinedocs/gdb.html)：断点、单步、调用栈和内存检查的权威说明。
- [100 个 GDB 小技巧](https://github.com/hellogcc/100-gdb-tips)：中文短例子，适合按问题查。
- [Compiler Explorer](https://godbolt.org/)：对照源码和汇编，理解优化与代码生成。
- [GNU Make Manual](https://www.gnu.org/software/make/manual/) 与 [跟我一起写 Makefile](https://seisman.github.io/how-to-write-makefile/)：先理解依赖图，再背语法。
- [CMake Tutorial](https://cmake.org/cmake/help/latest/guide/tutorial/)：需要跨平台或多目标项目时再学。
- [ShellCheck](https://www.shellcheck.net/)：给 Shell 脚本做静态检查。
- [tldr pages](https://tldr.sh/)：先看常用例子；需要精确语义时回到 `man`。

调试的基本顺序是：稳定复现，缩小范围，观察状态，提出假设，再改代码。一次改十处然后祈祷，不叫调试。

## 写东西

- [Markdown Guide](https://www.markdownguide.org/)：README、实验报告和项目文档的最低成本格式。
- [Mermaid](https://mermaid.js.org/intro/)：用文本画流程图和时序图，适合跟代码一起版本控制。
- [Overleaf Learn](https://www.overleaf.com/learn)：LaTeX 和 BibTeX 的实用手册。
- [Zotero](https://www.zotero.org/)：论文收藏、标注和引用管理。从第一篇论文开始用，不要等到写毕业论文再整理文件名。

## AI 编程工具

[GitHub Copilot](https://docs.github.com/zh/copilot)、[Claude Code](https://code.claude.com/docs/en/overview)、[OpenAI Codex CLI](https://learn.chatgpt.com/docs/codex/cli)、[Cursor](https://cursor.com/docs)、[Pi](https://pi.dev/)、[OpenCode](https://opencode.ai/) 等。挑一个能在现有工作流里使用的即可，不要把时间花在反复迁移配置上。

适合交给它们的工作：解释陌生代码、生成样板、补测试、列排查路径、审阅 diff。不能外包的工作：确认需求、判断结果是否正确、遵守课程规定、保护密钥和私人数据。

任何由工具生成但你无法解释的代码，暂时都不属于你。

### 两个实验，和它们说明的事

- Anthropic 的随机对照实验（52 名工程师学一个没用过的新库）：用 AI 的那组，事后理解力测验平均 50%，纯手写组 67%；**调试题的差距最大**，而速度优势并不显著。得分高的用法是问概念、要解释；得分低的是直接让它写、把它当调试拐棍。（[研究页](https://www.anthropic.com/research/AI-assistance-coding-skills)）
- METR 2025 年 7 月的实验：资深开源开发者用 AI 后实测慢了 19%，自己却感觉快了 20%。**但 METR 在 [2026 年 2 月的更新](https://metr.org/blog/2026-02-24-uplift-update/)里说，后续数据因选择偏差已不可靠，重新估计反而是提速**——这条更适合当作“研究也有发布日期”的例子。

结论不是别用，而是**用在你已经会一点的地方**：它是加速器，不是老师。学新东西时先自己写一遍，再看 AI 的。

## 从零上手一条 AI 编程路线

工具清单容易看花眼。这里给一条零成本、国内网络可达的路径：

1. 装 [Node.js](https://nodejs.org/) LTS 版（pi 需要 Node 22 以上）；
2. `npm install -g @earendil-works/pi-coding-agent`；
3. 到 [platform.deepseek.com](https://platform.deepseek.com/) 创建 API key；
4. 写进 `~/.zshrc`：`export DEEPSEEK_API_KEY=sk-xxxx`。

然后在项目目录敲 `pi`，让它读代码、改一个文件、跑一次命令，最后 `git commit` 留下记录。

**四步跑通，比读完十篇评测有用。** 其他方案（Copilot、Claude Code、Codex）见上方工具清单。

## GitHub：两条安全线

- **提交前**：`git status` 确认没混进 token、密码、私钥；`.env` 和密钥文件写进 `.gitignore`。
- **一旦泄露**：立刻撤销并轮换密钥。**光删掉提交没用**——它还在历史里，别人可能已经拉走了。

顺带值得知道的：[GitHub 学生包](https://education.github.com/pack)（含 Copilot 等权益，以官网为准）、[GitHub Pages](https://pages.github.com/)（免费主页）、[first-contributions](https://github.com/firstcontributions/first-contributions)（专门给新手练第一个 PR）、[goodfirstissue.dev](https://goodfirstissue.dev/)（筛“适合新手”的任务）。
