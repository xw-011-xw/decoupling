# Decoupling 小组

本仓库用于 Decoupling（解耦）研究小组的代码、文档与资料共享。

## 内容规划

- 研究笔记与文献整理
- 论文草稿与 LaTeX 源文件
- 数值实验与示例代码
- 组会材料

## 协作方式

### Issues（任务讨论与分工）

Issues 栏目用于小组内的任务协作：

- **任务讨论**：讨论具体研究任务、技术方案
- **提问**：提出疑问、寻求帮助
- **任务分工**：发布任务、分配负责人、跟踪进度

新任务请在 Issues 中创建，并用标签（Label）区分类型（如：文献、写作、代码、组会）。

### Project（工作看板）

仓库已关联「Decoupling 小组工作看板」（Board 视图），按 `Todo → In Progress → Done` 三列跟踪任务状态。Issue 创建后可拖入看板对应列，直观展示整体进度。

### Agents（AI 工具链）

小组的 AI 工具链为：

- **DeepSeek harness**（DeepSeek 模型工作流）
- **Danus / Pharos**（科研控制台）
- **ChatGPT**

不依赖 GitHub 内置 Agents 功能。

## 使用说明

- 拉取仓库：`git clone https://github.com/xw123-pro/decoupling.git`
- 本地更新流程：修改文件后依次执行
  ```
  git add .
  git commit -m "更新说明"
  git push
  ```
- 认证方式：SSH 密钥（免密推送），需先配置 `~/.ssh/id_ed25519` 对应的公钥到 GitHub 账号

## 维护

维护人：xw123-pro
