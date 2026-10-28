# Decoupling 小组

本仓库用于 Decoupling（解耦）研究小组的代码、文档与资料共享。

## 目录结构

- `docs/`：文献目录（literature.md）、科学选题（topic.md）
- `workflows/`：工作流说明与改动记录（changes-log.md）
- `experiments/`：GPT 对比差距定位（gpt-comparison.md）、独立验证（verification.md）
- `reports/`：组会与汇报材料（presentation.md）

## 当前任务（AI4Math 第四次实践课）

- **主线**：迭代工作流（拆解问题、多模型对比、强化验证、人机配合），在数学上理解结果，提出更合理的问题
- **副线**：科学问题初步选题（解耦组方向：大规模粒子随机游动；先确认与频率解耦的连接）
- **红线**：可以魔改工作流，但坚决不能抛弃现有工作流；每处改动写清「改了什么、为什么、效果」
- **协作**：正式任务与材料入 GitHub / Overleaf；每位成员都有可查的贡献（提交 / 编辑 / 整理 / 数据等）

## 协作方式

### Issues（任务讨论与分工）

Issues 栏目用于小组内的任务协作：

- **任务讨论**：讨论具体研究任务、技术方案
- **提问**：提出疑问、寻求帮助
- **任务分工**：发布任务、分配负责人、跟踪进度

新任务请在 Issues 中创建，并用标签（Label）区分类型（如：文献、写作、代码、组会）。

### Project（工作看板）

仓库已关联「Decoupling 小组工作看板」（Board 视图），按 `待办 → 进行中 → 已完成` 三列跟踪任务状态。Issue 创建后可拖入看板对应列，直观展示整体进度。

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
