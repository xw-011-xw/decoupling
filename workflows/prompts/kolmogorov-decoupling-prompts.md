# AI 辅助 · Kolmogorov 方程 decoupling 函数空间 · 提示词模板

> 用途：让 GPT 与 Danus（DeepSeek harness）推进研究任务——**构造一个适配于 Kolmogorov 方程的 decoupling 函数空间**。
> 与 `science-topic-prompts.md`（选题用）的区别：这里不是找题，而是让 AI 帮我们拆解构造任务、核对结构、补文献。
> 核心原则：AI 必须同时吃透两边——decoupling 的帽分解机制 与 Kolmogorov 方程的各向异性次椭圆几何——再判断接榫点；禁止用"名字像"硬凑。
>
> **判据更新（关键）**：本任务中"decoupling 是否对口"的判断标准不再是"方程是否色散/酉"。
> 而是：**Kolmogorov 方程象征曲面的退化曲率 + 各向异性缩放，能否被 decoupling 的帽分解框架处理。**
> 经典 BD 的"非退化曲率"假设在这里正是要改造的对象（参考退化超曲面 decoupling 的近期工作）。
>
> **现象入口**：若需要先从生活现象/科学问题引出 Kolmogorov 方程（如显微镜下布朗运动的
> 位置-速度观测），见 `phenomenon-to-problem-prompts.md`；本文件假定研究对象已选定，专注构造任务。

## 使用方法

1. **先跑 GPT 版**：让它在"连接梳理 + 构造要素 + 差异对比"三个维度做深度分析。
2. **再跑 Danus 版**：让它按步骤逐项验证（象征曲面 → 缩放 → 帽分解 → 空间性质），输出带信心标注的清单。
3. **对比两边输出**：两边都提到的构造要素 → 可信度高；只有一边提到 → 补查文献。
4. 每次输出回来，与 `docs/topic.md` 的候选 D（退化曲率 decoupling 方向）对照印证。

---

## 共用背景块（两个版本提示词都先粘贴这段）

```text
【研究对象：Kolmogorov 方程】
我们研究 Kolmogorov 型退化抛物算子（Kolmogorov 1934；Hörmander 次椭圆性的标准范例）：
  K = ∂_t + v·∇_x - Δ_v ，作用在 (x, v) ∈ R^d_x × R^d_v 上（位置-速度 / 动理学模型）。
关键结构：
- 次椭圆：一阶场 {∂_t, v·∇_x, ∂_{v_j}} 满足 Hörmander 括号条件
  （[∂_{v_j}, v·∇_x] = ∂_{x_j}），因此解有超正则性，基本解在原点外 C^∞。
- 基本解：各向异性高斯型，约 t^{-2d} exp(-|v|²/t - |x - (t/2)v|²/t³ 型)，不是各向同性热核。
- 各向异性缩放（动理学尺度）：(t, x, v) ↦ (r² t, r³ x, r v)，r > 0。
- 半群性质：L² 耗散（范数衰减），不是酉演化——这与 Schrödinger/色散情形本质不同，
  decoupling 在这里的角色是估计工具（核衰减、Strichartz、限制/迹），不是描述振荡传播。

【我们的任务：构造适配的 decoupling 函数空间】
要构造一个函数空间（含合适的频率分解 / 帽结构 / 范数定义），使得
Bourgain–Demeter 型的 decoupling 不等式在这个空间里成立，并能用于
Kolmogorov 方程解的估计（如核的 L^p 时空估计、次椭圆 Strichartz、迹定理）。

【我们的工具箱】
- Bourgain–Demeter 解耦及其帽分解 / 尺度化机制
- 各向异性伸缩与抛物型 Littlewood–Paley 分解
- Strichartz / 色散估计、振荡积分 / FIO
- 混合范数 L^p 估计与 Besov / Triebel 型函数空间构造
```

---

## GPT 版提示词（深度探索）

```text
我是调和分析方向的研究者，熟悉 Bourgain–Demeter 解耦、各向异性 Littlewood–Paley 分解、
Strichartz 估计、振荡积分与 Besov/Triebel 型函数空间。我粘贴了上面的【背景块】。

请围绕"构造适配 Kolmogorov 方程的 decoupling 函数空间"做四件事，全程区分
"有文献依据"与"你的猜测"：

1. 连接梳理：Kolmogorov 方程 K = ∂_t + v·∇_x - Δ_v 的象征零集是什么几何对象？
   它的曲率在哪些方向退化、退化阶多少？经典 BD decoupling 要求非退化曲率，
   这里哪些部分可以直接用、哪些必须改造（参考退化超曲面 decoupling 的近期工作，
   如 Li–Yang, "Decoupling for degenerate hypersurfaces", arXiv:2507.02134；
   Li–Yang, "Decoupling for surfaces with radial symmetry", arXiv:2504.17100）？

2. 构造要素：为定义"适配的 decoupling 函数空间"，我们需要决定哪些具体要素？
   请逐项给出建议：
   (a) 频率分解：在各向异性缩放 (r²t, r³x, rv) 下，Littlewood–Paley 壳 / 帽应如何
       定义（各向异性宽度 δ、δ^{3/2}、δ² 的关系）？
   (b) 帽结构：decoupling 中的"δ-帽"在这个几何里应取什么形状？
   (c) 范数：空间范数应该包含哪些混合范数 / 加权？和经典 ℓ²(L^p) decoupling 的
       对应关系？
   (d) 不等式形式：你预期 decoupling 常数依赖什么（维数 d、尺度 δ、退化阶）？

3. 差异对比：列一张表——经典 BD（抛物面/球面）vs 我们的 Kolmogorov 设置，
   比较：曲面、曲率、缩放、帽分解、半群类型、decoupling 的用途。

4. 具体子问题：给出 2–3 个可先推进的、规模可控的子问题（例如：先在一维 v、
   固定退化阶下定义空间并证明一个小型 decoupling 不等式；或先证明核估计）。

文献请给真实可查的（arXiv 编号或期刊卷页）；不确定的标注"待核"。
```

---

## Danus 版提示词（结构化验证）

```text
任务：协助构造适配 Kolmogorov 方程的 decoupling 函数空间。背景与工具箱见上方【背景块】。

请严格分步执行，每一步给出"是/否 + 一句话理由"，并标注信心（高/中/低）：

第 1 步：写出 Kolmogorov 算子 K = ∂_t + v·∇_x - Δ_v 的完整象征（对偶变量对应
  (t,x,v)），确定象征零集的维数与退化方向。列出 Hörmander 括号条件如何满足。

第 2 步：在各向异性缩放 (t,x,v) ↦ (r²t, r³x, rv) 下，写出频率空间（对偶变量）的
  各向异性尺度关系：τ、ξ、η 各自随 r 如何缩放？据此定义 Littlewood–Paley 型
  频率壳（宽度 δ 的 η-壳对应多大 ξ-壳、τ-壳）。

第 3 步：基于第 2 步的壳结构，定义 decoupling 的"δ-帽"分解，并写下一个候选的
  decoupling 不等式（含范数定义）。说明它与经典 BD 的异同。

第 4 步：验证候选空间的三个性质（能做多少做多少，明确哪些未验证）：
  (a) 嵌入关系（和 L^p / 各向异性 Sobolev / 抛物型空间的关系）；
  (b) 对偶或插值性质；
  (c) 能否推出 Kolmogorov 基本解的 L^p 时空估计（或次椭圆 Strichartz）。

第 5 步：输出表格：要素 | 定义/建议 | 依据(文献/推断) | 信心 | 待验证点。

注意：不要因为"Kolmogorov 方程是抛物型"就说 decoupling 不适用——我们的问题是
"退化曲率 + 各向异性几何下 decoupling 如何适配"，参考退化超曲面 decoupling
（arXiv:2507.02134、arXiv:2504.17100）的思路。也不要把经典 BD 的结论不加检查地搬过来。
```

---

## 版本记录

- v1（2026-11-03）：初版。为"构造适配 Kolmogorov 方程的 decoupling 函数空间"定制；
  判据从"色散/酉"更新为"退化曲率 + 各向异性几何能否被 decoupling 框架处理"；
  加入 Kolmogorov 背景块（次椭圆性、各向异性缩放 (r²t,r³x,rv)、各向异性高斯基本解、L² 耗散半群）。
