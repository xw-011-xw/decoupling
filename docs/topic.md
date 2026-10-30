# 科学问题初步选题

> 任务来源：AI4Math 第四次实践课 · 任务二（副线）
> 解耦组对应科学方向：**大规模粒子随机游动**（如格点 / 图上的扩散、密度与涨落；先确认与频率解耦的连接）
> 注意：候选不是结论。名称相同、方程形式相似不足以证明两者有联系；本轮只做初步选题，不做完整论证。
>
> **参考依据**：本文件结合了两份 AI 辅助选题报告——
> - `experiments/GPT-topic_selection-report.pdf`（5 方向聚焦，含文献入口）
> - `experiments/Danus-topic_selection-report.pdf`（14 候选穷举，含具体衰减指数；全部结论 status=unverified，具体定理/文献需自行核对后引用）

## 核心思路

**从我们自己的数学工具箱出发，不从物理名词出发。**

我们手里的工具是：Bourgain–Demeter 解耦、Schrödinger 方程的 Strichartz 估计、FIO / 振荡积分估计、二进频率壳与球面帽分解、混合范数 L^p 估计。这些工具擅长处理的是**色散方程解在时空上的 L^p 估计**——核心特征是**振荡**。

**硬判据**：看演化算子的 Fourier 乘子——
- 纯相位 e^{itω(ξ)}（酉演化，色散型）→ 对口，有超曲面、有曲率、有帽分解
- 实阻尼 e^{-tΩ(ξ)}（正半群，抛物型）→ 不对口，无相位振荡，解耦使不上劲

同一 Laplacian，酉演化 e^{itΔ} 和热演化 e^{tΔ} 的分析机制完全不同。下面列候选并标注联系强度。

---

## 候选 A · 扩散极限与热核的 L^p 估计（降级方向）

**对象 / 现象**：Z^d 上的简单随机游走，长时间（t → ∞）下概率密度收敛到高斯热核。

**判断**：**降级**。热型演化 ∂_t u = Δ_d u 的 Fourier 乘子是 e^{-tΩ(ξ)} 实阻尼，机制是高频平滑、热核衰减（Nash 不等式、Davies–Gaffney），无相消、无振荡、L^2 不守恒——解耦工具用不上劲。

**修正**：之前想当然认为"Lévy / 分数阶"会对口，实际上分数阶**热方程** ∂_t u = -(-Δ)^{α/2} u 的乘子 e^{-t|ξ|^α} 仍是正 Markov 半群，只是把高斯尾换成多项式尾，没有相位振荡——仍然降级。真正对口的是分数阶 **Schrödinger**（见候选 E）。

**入门资料**：
- Lawler & Limic, *Random Walk: A Modern Introduction*（扩散极限章节，了解背景即可）

---

## 候选 B · 图 / 格点上的随机游走（拆分：热流降级 / Schrödinger 升级）

**关键拆分**：同一个图上，两种演化机制完全不同——

- **热流演化** e^{-tL_G}（抛物型）：降级。对称 Markov 跳生成元的 m(ξ) = Σ a(z)(cos(z·ξ)-1) ∈ [-2Λ, 0]，短时行为与酉演化首项同阶（t^{dE(x,y)}），Wick 旋转不带来振荡增益。
- **Schrödinger 演化** e^{-itL_G}（色散型）：升级。图 / 格点上 Laplacian 的谱分析是离散限制问题，连续谱上的衰减、带边稳相、谱密度估计——和我们的频率分解工具对口。

**联系强度**：**有依据（仅 Schrödinger 侧）**。

**入门资料**：
- Woess, *Random Walks on Infinite Graphs and Groups*（图上随机游走背景）
- arXiv:2003.12031 Thm 6；arXiv:1509.01993 Thm 2.2（图上热流 vs 酉演化短时对比，编号待核）

---

## 候选 C · 多粒子密度涨落 / SPDE（明确降级）

**对象 / 现象**：SSEP 等多粒子系统的密度涨落场，流体力学极限下收敛到 Edwards–Wilkinson / KPZ 类 SPDE。

**判断**：**降级**。三条独立判据一致给抛物：
1. 极限律由正热核构成的高斯场，时空谱密度是 Lorentzian（τ 方向全支撑，无超曲面）
2. KPZ 经 Cole–Hopf 变换保正
3. **关键陷阱**：KPZ 里的 Airy 来自可解模型 Fredholm 行列式的最速下降，不是色散超曲面的稳相；KPZ 无乘子 μ_t、无 ω、无酉群，σ（曲率退化参数）根本无定义——不得据"出现 Airy"升级

**入门资料**：暂不展开，列作远期排除方向。

---

## 候选 D · 量子随机游走与格点 Schrödinger（★ 首选方向）

**对象 / 现象**：
- **格点 Schrödinger / CTQW**：Z^d 上 i∂_t u = -Δ_d u，离散 Fourier 相位 Ω(ξ) = 4Σsin²(ξ_j/2)
- **DTQW（带硬币量子游走）**：ψ_{n+1} = S(C⊗I)ψ_n，多支带结构 + 弹道波前焦散
- **随机介质中的波**：i∂_t ψ = -Δψ + λV_ω(x)ψ

**为什么是首选**：
- 酉演化的乘子是纯相位 e^{-itΩ(ξ)}，支撑在超曲面 {τ = Ω(ξ)} 上，L^p_{t,x} 估计 = restriction/decoupling 问题，完全对口。
- **具体题目**：格点 Schrödinger 传播子在退化集 D = {∏ cos k_j = 0} 上曲率退化，衰减率从连续情形的 t^{-d/2} 变成 t^{-d/3}（Bessel 函数 Airy 一致渐近）。需要"适配 D 的帽分解 + 退化水平集 ℓ^2 decoupling"——**arXiv:1904.09640 Rmk 1.4 已明确把这条路线标注为 "leave for future study"，是文献里写好的开放问题**。
- 随机介质中的波：弱无序（d ≥ 3）下自由色散估计在相干窗口 t ≲ (λ²G_d)^{-1} 内成立；强无序 / Anderson 局域化区色散被定理级否定——要分区域做。

**联系强度**：**有依据，首选**。

**入门资料**（GPT 报告给的具体文献，组内分头读）：
- Maeda, Sasaki, Segawa, Suzuki & Suzuki (2022), *Dispersive estimates for quantum walks on 1D lattice*, J. Math. Soc. Jpn. 74(1), 217–246 —— **起点文献，先读这篇**
- Hong & Yang (2019), *Uniform Strichartz estimates on the lattice*, DCDS 39(6), 3239–3264
- Hu & Li (2014), *Discrete Fourier restriction associated with Schrödinger equations*, Rev. Mat. Iberoam. 30(4), 1281–1300
- Bi, Cheng & Hua, *The Wave Equation on Lattices and Oscillatory Integrals*, arXiv:2312.04130
- Bal, Komorowski & Ryzhik (2010), *Kinetic limits for waves in a random medium*, KRM 3(4), 529–644 —— 随机介质波综述
- Bourgain–Demeter, Ann. Math. 182 (2015) 351–389（我们自己的解耦原文）

---

## 候选 E · 分数阶 Schrödinger 与退相干量子游走（备选方向）

**对象 / 现象**：
- **分数阶 Schrödinger**：i∂_t u = (-Δ)^{α/2} u（α > 0, α ≠ 2），色散关系 τ = |ξ|^α，曲率 ~ |ξ|^{α-2} 在 α≠2 时退化
- **退相干 / 被监测量子游走**：游走 + 速率 t^β 的位置测量，β = 1 得弹道（色散），β = 0 得高斯扩散，0 < β < 1 得方差缩减的高斯律——参数 β 横跨色散↔抛物两类

**可能的联系**：
- 分数阶 Schrödinger 的 α-admissible Strichartz（2/q + d/(αr) = d/2）和退化 / 锥面 decoupling 是直接推广；同时长程格点相互作用 DNLS 的连续极限恰是它。
- 退相干量子游走是"色散↔抛物"的插值模型，β 参数中间区域的极限律形状未定，是个有意思的过渡问题。

**联系强度**：**有依据（分数阶 Schrödinger）/ 中（退相干，交叉指数未定）**。

**入门资料**：
- Kirkpatrick–Lenzmann–Staffilani, CMP 317 (2013) 563–591（分数阶 NLS / Schrödinger）
- Shikano–Chisaki–Segawa, arXiv:1001.3989（退相干量子游走，编号待核）

---

## 下一步分工建议（待讨论）

1. **主线明确**：**首选候选 D（格点 Schrödinger 曲率退化 + CTQW）**——两份 AI 报告独立收敛到这个方向，且是文献里写好的开放问题（arXiv:1904.09640 Rmk 1.4 "leave for future study"）。
2. **入门顺序**：先读 Maeda et al. (2022) 一维量子游走色散估计（GPT 推荐的起点），建立基本认识；再读 Hong-Yang (2019) 格点 Strichartz。
3. **分头任务**：
   - 一人读概率侧（量子游走、随机介质波综述 Bal-Komorowski-Ryzhik 2010）
   - 一人读我们自己侧（Schrödinger Strichartz、Bourgain-Demeter 解耦原文）
   - 碰头时对照候选 D 的具体题目：格点 Schrödinger 在 D={∏cos k_j=0} 上的 t^{-d/3} 衰减
4. **排除方向不用花时间**：A（热核）、C（KPZ/SPDE）、血流 CFD / Navier-Stokes 已明确降级，不用再投入。
5. **下次汇报口径**：讲清首选 D 的具体题目和开放问题定位；E 作为备选；A/B/C 说明为什么降级。
