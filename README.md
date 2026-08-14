# Algorithm Training

这是 GCU 计算机协会的算法学习与训练仓库，用于集中存放学习文档、课程内容、练习题、参考题解和成员训练记录。

## 仓库内容

- 学习路线和开发环境说明
- 按主题整理的算法课程
- 按难度划分的练习题
- 官方参考题解
- 各届成员的个人训练记录

## 目录结构

```text
algorithm-training/
├── README.md
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── docs/
│   ├── roadmap.md
│   ├── environment-setup.md
│   └── git-guide.md
├── lessons/
│   ├── 01-complexity/
│   │   ├── README.md
│   │   └── examples/
│   └── 02-sorting/
│       ├── README.md
│       └── examples/
├── exercises/
│   ├── beginner/
│   ├── intermediate/
│   └── advanced/
├── solutions/
│   ├── beginner/
│   ├── intermediate/
│   └── advanced/
├── resources/
├── students/
│   ├── 2025/
│   └── 2026/
└── templates/
    ├── student-readme.md
    └── solution-template.md
```

## 文件夹说明

| 文件夹 | 作用 | 内容要求 |
| --- | --- | --- |
| `docs/` | 存放公共学习文档 | 内容应适用于所有成员，标题和步骤要清晰 |
| `lessons/` | 存放正式课程内容 | 按“序号-主题”命名，每课包含说明文档和示例代码 |
| `exercises/` | 存放练习题 | 按难度分类，每道题应写明题目、输入输出和示例 |
| `solutions/` | 存放官方参考题解 | 应与练习题路径对应，并说明思路和复杂度 |
| `resources/` | 存放课件、图片和补充资料 | 文件名应能说明用途，避免上传无关或重复文件 |
| `students/` | 存放各届成员的个人训练记录 | 先按年份分类，再按成员姓名或 GitHub 用户名建目录 |
| `templates/` | 存放可复制的文档模板 | 新建个人介绍或题解时应优先使用这里的模板 |

> `.gitkeep` 只是用于让 Git 保留空文件夹，不需要填写内容。

## Markdown 文件说明

| 文件 | 作用与填写要求 |
| --- | --- |
| `README.md` | 仓库总说明。用于帮助新成员快速了解项目结构和使用方法 |
| `CONTRIBUTING.md` | 协作规范。应说明分支命名、提交信息、Pull Request 和文件命名规则 |
| `CODE_OF_CONDUCT.md` | 社区行为准则。应说明成员交流、协作和内容发布的基本要求 |
| `docs/roadmap.md` | 学习路线。按顺序列出需要学习的知识点和建议进度 |
| `docs/environment-setup.md` | 环境配置指南。说明编译器、编辑器和运行方式 |
| `docs/git-guide.md` | Git 使用指南。说明克隆、分支、提交、推送和 Pull Request 流程 |
| `lessons/*/README.md` | 单节课程讲义。至少包含学习目标、知识点、示例和课后练习 |
| `students/<年份>/README.md` | 该届成员说明。可记录成员名单、训练安排和提交要求 |
| `students/<年份>/<成员>/README.md` | 个人说明。由成员本人维护，可记录个人介绍、学习进度和练习索引 |
| `templates/student-readme.md` | 个人 README 模板，供新成员复制后填写 |
| `templates/solution-template.md` | 题解模板，应包含题目链接、解题思路、复杂度和代码说明 |

## 基本使用方式

1. 在 `exercises/` 中选择合适难度的题目。
2. 将个人代码和记录放入自己的成员目录。
3. 完成后通过独立分支和 Pull Request 提交。
4. 不要修改或覆盖其他成员目录中的内容。

## 文档约定

- Markdown 文件统一使用 UTF-8 编码。
- 每份文档使用一个清晰的一级标题。
- 文件和目录名称应简短、明确，避免使用含义不清的临时名称。
- 引用仓库内文件时优先使用相对路径。
- 提交前确认没有加入编译产物、临时文件或个人隐私信息。
