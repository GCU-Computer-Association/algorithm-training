# 成员提交规范

本仓库用于 GCU 计算机协会算法部的学习与训练。为了避免误改公共资料或其他成员的内容，请所有成员在提交前阅读并遵守本规范。

## 核心原则

1. 每位成员只修改自己的目录：

   ```text
   students/<年份>/<GitHub 用户名>/
   ```

2. 不要修改、移动或删除其他成员的文件。
3. 不要把无关修改、编译产物或临时文件加入提交。
4. 提交前必须检查暂存区中的文件。
5. 禁止对 `main` 使用强制推送。

> GitHub 的普通仓库写权限不能限制成员只能修改某个文件夹。本规范属于团队协作约定，需要每位成员主动遵守。

## 第一次使用

克隆仓库并进入项目目录：

```bash
git clone https://github.com/GCU-Computer-Association/algorithm-training.git
cd algorithm-training
```

在对应年份下创建自己的目录。下面以用户 `xiaoming` 为例，实际使用时请替换成自己的 GitHub 用户名：

```bash
mkdir -p students/2026/xiaoming
cp templates/student-readme.md students/2026/xiaoming/README.md
```

个人目录建议采用以下结构：

```text
students/2026/xiaoming/
├── README.md
├── week-01/
├── week-02/
└── projects/
```

个人 `README.md` 可记录个人介绍、学习进度和练习索引。不要在其中填写手机号、密码、令牌等隐私信息。

## 当前提交方式

仓库目前允许成员直接向 `main` 推送。Git 并不是单独“上传文件夹”，而是将暂存的文件组成一次提交后推送。因此，请通过精确的 `git add` 路径控制提交范围。

### 1. 开始修改前同步仓库

```bash
git switch main
git pull --ff-only origin main
```

如果命令失败，不要使用强制操作，先检查本地状态或联系负责人。

### 2. 完成自己的练习

只在自己的成员目录中添加或修改文件。

### 3. 检查所有变化

```bash
git status
```

确认没有意外修改公共文件或其他成员的目录。

### 4. 只暂存自己的目录

仍以 `xiaoming` 为例：

```bash
git add -- students/2026/xiaoming/
```

不要把下面的命令作为默认操作：

```bash
git add .
```

因为它会把当前目录下的所有修改一起加入暂存区，容易误提交其他成员或公共文件。

### 5. 检查本次准备提交的内容

```bash
git status
git diff --cached --name-only
git diff --cached
```

检查结果中应当只出现自己的目录。发现不属于自己的文件时，必须先移出暂存区。

### 6. 创建提交

提交信息应简短说明“谁完成了什么”，例如：

```bash
git commit -m "2026/xiaoming: 完成 week01 练习"
```

建议格式：

```text
年份/GitHub用户名: 修改内容
```

避免使用 `update`、`修改`、`123` 等无法说明内容的提交信息。

### 7. 推送

```bash
git push origin main
```

推送后到 GitHub 仓库页面确认文件路径和内容是否正确。

## 常见错误与处理

### 误用了 `git add .`

如果还没有提交，可安全地取消全部暂存：

```bash
git restore --staged .
```

这个命令只取消暂存，不会删除本地修改。之后重新只添加自己的目录：

```bash
git add -- students/2026/xiaoming/
```

### 只误暂存了某个文件

```bash
git restore --staged -- 文件路径
```

再次运行 `git status`，确认它已经离开“Changes to be committed”区域。

### 推送被拒绝

通常表示远端出现了新的提交。先执行：

```bash
git pull --rebase origin main
```

如果没有冲突，再执行：

```bash
git push origin main
```

如果发生冲突：

- 冲突只在自己的目录中，可以仔细解决后继续。
- 冲突涉及公共文件或其他成员目录时，立即停止并联系负责人。
- 不要使用 `git push --force` 绕过冲突。

### 已经提交了错误文件

- 尚未推送：不要继续推送，先联系负责人确认如何修改提交。
- 已经推送：立即通知负责人，不要删除历史或强制推送。

### 出现大量自己没有改过的文件

这通常可能由换行符、编辑器设置或错误操作造成。不要执行 `git add .`，也不要批量覆盖文件。先保留现场并联系负责人检查。

### 空文件夹没有出现在 GitHub

Git 不记录真正的空文件夹。如确实需要保留目录，可在其中添加空的 `.gitkeep` 文件。

## 禁止提交的内容

- 编译生成的 `.exe`、`.o`、`.obj` 等文件。
- `Debug/`、`Release/`、`x64/`、`.vs/` 等构建或编辑器缓存目录。
- 日志、缓存、临时文件和无关压缩包。
- 密码、访问令牌、密钥、手机号等敏感信息。
- 来源不明或没有授权的大型资料。

如果发现这些文件，应先检查并完善仓库的 `.gitignore`，不要直接提交。

## 公共内容的修改

如果需要修改 `docs/`、`lessons/`、`exercises/`、`solutions/`、`resources/`、`templates/` 或根目录文件：

1. 先与负责人确认修改范围。
2. 单独创建一次提交，不要和个人练习混在一起。
3. 精确暂存相关文件，并使用 `git diff --cached` 检查。

## 启用 Pull Request 后

仓库将来启用 `main` 分支保护后，成员需要从个人分支提交：

```bash
git switch main
git pull --ff-only origin main
git switch -c student/xiaoming-week01
git add -- students/2026/xiaoming/
git diff --cached --name-only
git commit -m "2026/xiaoming: 完成 week01 练习"
git push -u origin student/xiaoming-week01
```

然后在 GitHub 上创建 Pull Request，等待审核后合并。禁止为了绕过保护规则而强制推送或直接修改 `main`。

## 提交前检查清单

- [ ] 只修改了自己的目录，或已经获得公共内容修改许可。
- [ ] 已执行 `git status`。
- [ ] 已使用明确路径执行 `git add`。
- [ ] 已执行 `git diff --cached --name-only`。
- [ ] 暂存区中没有其他成员的文件。
- [ ] 没有编译产物、缓存、临时文件或敏感信息。
- [ ] 提交信息能够清楚说明修改内容。
- [ ] 推送前已经同步远端最新内容。
