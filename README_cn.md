<div align="center">
  <h1>Awesome RSI</h1>
  <br>
  <a href="https://awesome.re">
    <img src="https://awesome.re/badge-flat2.svg" alt="Awesome">
  </a>
  <a href="https://creativecommons.org/publicdomain/zero/1.0/">
    <img src="https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg" alt="License: CC0 1.0">
  </a>
  <p>自进化 Agent / 递归自我改进（RSI）领域的<br>文献、开源项目与产品精选列表。</p>
  <p><a href="README.md">English</a> · <b>中文</b></p>
</div>

---

本列表收录通过迭代来改进 AI 系统某一部分的相关研究与工程实现——从单次响应的自我批评，到改写自身代码的 Agent。主体按**进化对象**分六层，每层标注该层的特征失败模式；其余分区（算法基础、自我评估、安全、基准）为横切面，其后依次是开源框架、产品与历史源流。

## 目录

- [综述](#综述)
- [L1 产物层](#l1-产物层)
- [L2 模型层](#l2-模型层)
- [L3 上下文与记忆层](#l3-上下文与记忆层)
- [L4 脚手架与自修改层](#l4-脚手架与自修改层)
- [L5 元改进层](#l5-元改进层)
- [L6 准则层](#l6-准则层)
- [算法基础：开放式进化与质量多样性](#算法基础开放式进化与质量多样性)
- [自我评估与内省](#自我评估与内省)
- [安全与目标保持](#安全与目标保持)
- [评测基准](#评测基准)
- [开源框架与工具](#开源框架与工具)
- [产品与公司](#产品与公司)
- [历史源流与理论基础](#历史源流与理论基础)

---

## 综述

自进化 Agent 与递归自我改进的跨层综述。

- [Recursive Self-Improvement in AI: From Bounded Self-Refinement to Autonomous Research Loops](https://arxiv.org/abs/2607.07663) - 基于 1,250 篇文献的综述，按「改进对象 × 回路闭合程度」双轴分类，提出验证层级（形式验证器 > 执行反馈 > 学习型裁判 > 内在自评）。(arXiv 2026)
- [A Comprehensive Survey of Self-Evolving AI Agents: Bridging Foundation Models and Lifelong Agentic Systems](https://arxiv.org/abs/2508.07407) - 围绕反馈回路、更新目标、领域应用、评估与安全组织 Agent 进化文献。(arXiv 2025)
- [A Survey on Self-Evolution of Large Language Models](https://arxiv.org/abs/2404.14387) - 提出经验获取、精炼、更新、评估的四阶段自进化框架。(arXiv 2024)
- [A Systematic Survey of Self-Evolving Agents: From Model-Centric to Environment-Driven Co-Evolution](https://doi.org/10.36227/techrxiv.177203250.05832634/v2) - 从模型中心到环境驱动共进化的分类框架。(TechRxiv 2026)

## L1 产物层

进化的对象是系统的输出——从单次响应到可持久留存的产物。特征失败模式：**自证循环**——没有外部信号的迭代只是改写，不是进步。

### 任务内自我精炼（无持久化）

任务内回路：模型在单次会话内自我批评并改写输出，不留存任何状态。

- [Self-Consistency Improves Chain of Thought Reasoning](https://arxiv.org/abs/2203.11171) - 采样多条推理路径并取一致性最高的答案。(ICLR 2023)
- [Self-Refine: Iterative Refinement with Self-Feedback](https://arxiv.org/abs/2303.17651) - 同一模型兼任生成者、批评者与改进者，经多轮迭代改进输出。(NeurIPS 2023)
- [CRITIC: Large Language Models Can Self-Correct with Tool-Interactive Critiquing](https://arxiv.org/abs/2305.11738) - 用外部工具验证输出，将证据转化为迭代修正。(ICLR 2024)
- [Chain-of-Verification Reduces Hallucination in Large Language Models](https://arxiv.org/abs/2309.11495) - 先规划并回答独立验证问题，再产出修正响应。(ACL 2024 Findings)
- [Improving Factuality and Reasoning in Language Models through Multiagent Debate](https://arxiv.org/abs/2305.14325) - 多个模型实例经迭代提案与互评收敛到更准确的答案。(ICML 2024)
- [Large Language Models Cannot Self-Correct Reasoning Yet](https://arxiv.org/abs/2310.01798) - 无外部反馈的内在自我纠错会降低推理表现；本层的负结果基线。(ICLR 2024)

### 跨代产物进化（持久产物）

产物在评估器压力下跨代演化，系统本身不变。

- [Mathematical Discoveries from Program Search with Large Language Models (FunSearch)](https://www.nature.com/articles/s41586-023-06924-6) - 冻结代码 LLM 与可执行评估器配对做进化式程序搜索，产出新数学结果。(Nature 2024) [[code]](https://github.com/google-deepmind/funsearch)
- [AlphaEvolve: A Coding Agent for Scientific and Algorithmic Discovery](https://arxiv.org/abs/2506.13131) - 来自 Google DeepMind：结合 LLM 集成采样、自动化评估与进化搜索，应用于算法发现与基础设施优化。(arXiv 2025) [[problems]](https://github.com/google-deepmind/alphaevolve_repository_of_problems)
- [ShinkaEvolve: Towards Open-Ended and Sample-Efficient Program Evolution](https://arxiv.org/abs/2509.19349) - 以样本效率为重点的程序进化框架，在极小评估预算下取得相当的效果。(ICLR 2026) [[code]](https://github.com/SakanaAI/ShinkaEvolve)
- [Vesper: Effective Harness Engineering for Algorithm Discovery with Coding Agents](https://arxiv.org/abs/2605.15221) - 面向算法发现的编码 Agent 脚手架工程研究。(arXiv 2026)
- [AutoML-Zero: Evolving Machine Learning Algorithms From Scratch](https://arxiv.org/abs/2003.03384) - 从基本数学运算出发进化完整学习算法，最小化人工设计偏置。(ICML 2020)
- [Evolutionary Optimization of Model Merging Recipes](https://arxiv.org/abs/2403.13187) - 来自 Sakana AI：在参数空间与数据流空间中进化开源模型的组合方式。(arXiv 2024)
- [The AI Scientist: Towards Fully Automated Open-Ended Scientific Discovery](https://arxiv.org/abs/2408.06292) - 来自 Sakana AI：产物为研究成果本身——自动化想法生成、实验、论文写作与评审的完整循环。(arXiv 2024) [[code]](https://github.com/SakanaAI/AI-Scientist)

## L2 模型层

进化的对象是模型自身参数：用自生成的数据、奖励或推理轨迹更新权重。特征失败模式：**模型坍塌**——在自生成数据上迭代训练导致多样性流失。

### 自训练与自奖励

模型自行生成训练信号——数据、偏好或奖励——并用其更新自身权重。

- [Self-Instruct: Aligning Language Models with Self-Generated Instructions](https://arxiv.org/abs/2212.10560) - 从模型自身生成指令数据，过滤后用于微调。(ACL 2023)
- [Large Language Models Can Self-Improve](https://arxiv.org/abs/2210.11610) - 用高置信度的模型自生成答案作为伪标签，在推理任务上迭代微调。(EMNLP 2023)
- [Self-Alignment with Instruction Backtranslation](https://arxiv.org/abs/2308.06259) - 从模型生成的无标注文档中反推指令，构造合成指令对用于微调。(ICLR 2024)
- [Self-Rewarding Language Models](https://arxiv.org/abs/2401.10020) - 模型生成并评判自己的指令跟随数据，多轮对齐迭代（评判能力本身也随训练提升，兼跨 L6）。(ICML 2024)
- [Self-Play Fine-Tuning Converts Weak Language Models to Strong Language Models](https://arxiv.org/abs/2401.01335) - 通过自博弈偏好学习迭代提升单一模型，无需额外人工标注。(ICML 2024)
- [RLAIF vs. RLHF: Scaling RL from Human Feedback with AI Feedback](https://arxiv.org/abs/2309.00267) - 用 AI 生成的偏好替代直接人工反馈做强化学习。(ICML 2024)
- [Self-Adapting Language Models (SEAL)](https://arxiv.org/abs/2506.10943) - 模型自生成更新数据与微调指令，使权重适配新任务。(NeurIPS 2025)
- [Agentic ESOpt: Fine-Tuning Long-Horizon LLM Agents with Minimal GPU Requirements](https://arxiv.org/abs/2608.17310) - 用进化策略做无梯度的全参数 Agent 微调：采样权重扰动，用环境奖励为完整轨迹评分，做奖励加权更新。(arXiv 2026) [[code]](https://github.com/zz1358m/Agentic-ESOpt)

### 自学推理

推理能力从模型自身的推理链中自举，而非依赖人工示范。

- [STaR: Bootstrapping Reasoning With Reasoning](https://arxiv.org/abs/2203.14465) - 交替进行推理链生成、答案过滤与微调，自举推理能力。(NeurIPS 2022)
- [Quiet-STaR: Language Models Can Teach Themselves to Think Before Speaking](https://arxiv.org/abs/2403.09629) - 训练模型在任意文本中生成内部推理，而非仅问答任务。(COLM 2024)
- [rStar-Math: Small LLMs Can Master Math Reasoning with Self-Evolved Deep Thinking](https://arxiv.org/abs/2501.04519) - 蒙特卡洛树搜索 + 自进化训练数据 + 过程偏好模型提升数学推理。(ICML 2025)

## L3 上下文与记忆层

进化的对象不是权重，而是 Agent 不断积累的经验、技能与上下文：追加、检索、巩固、遗忘。特征失败模式：**上下文坍塌与记忆污染**——积累越多反而越退化。

- [Reflexion: Language Agents with Verbal Reinforcement Learning](https://arxiv.org/abs/2303.11366) - 将任务反馈衍生的自然语言反思存入记忆，跨试验改进。(NeurIPS 2023)
- [ExpeL: LLM Agents Are Experiential Learners](https://arxiv.org/abs/2308.10144) - 从成功与失败轨迹中提取可迁移经验，无权重更新。(AAAI 2024)
- [MemoryBank: Enhancing Large Language Models with Long-Term Memory](https://arxiv.org/abs/2305.10250) - 带选择性遗忘的长期交互记忆，使响应随时间适配。(AAAI 2024)
- [Voyager: An Open-Ended Embodied Agent with Large Language Models](https://arxiv.org/abs/2305.16291) - Minecraft 终身学习 Agent：自动课程 + 持续扩展的可复用技能库。(TMLR 2024) [[code]](https://github.com/MineDojo/Voyager)
- [Recursive Introspection: Teaching Language Model Agents How to Self-Improve](https://arxiv.org/abs/2407.18219) - 训练模型检查先前失败的尝试，并在后续轮次递归改进。(NeurIPS 2024)
- [A-MEM: Agentic Memory for LLM Agents](https://arxiv.org/abs/2502.12110) - 动态链接的笔记网络，组织方式随经验积累而演化。(NeurIPS 2025)
- [Agentic Context Engineering (ACE)](https://arxiv.org/abs/2510.04618) - 将上下文视为结构化 playbook（行动手册），通过增量更新使其进化，避免上下文坍塌。(ICLR 2026)

## L4 脚手架与自修改层

进化的对象是 Agent 自身的提示、工具、工作流与代码：修改、版本化、回滚。特征失败模式：**脚手架过拟合**——对评估环境过拟合的结构性修改。

### 自我修改 Agent

Agent 编辑自身源代码，并保留经检验的版本谱系。

- [Darwin Gödel Machine: Open-Ended Evolution of Self-Improving Agents](https://arxiv.org/abs/2505.22954) - Agent 修改自身代码，改进经基准验证后进入开放式档案库，形成不断扩展的谱系树；SWE-bench 20% → 50%。(ICLR 2026) [[code]](https://github.com/jennyzzt/dgm)
- [SICA: A Self-Improving Coding Agent](https://arxiv.org/abs/2504.15228) - Agent 编辑自身实现并维护版本谱系，在 SWE-bench Verified 上实证提升。(ICLR 2025 SSI-FM Workshop)
- [Gödel Agent: A Self-Referential Agent Framework for Recursive Self-Improvement](https://arxiv.org/abs/2410.04444) - 自指 Agent 框架，可检查并改写自身逻辑，不依赖固定手工优化例程。(ACL 2025)

### 提示与程序优化

对提示、工作流与以可执行代码表示的 Agent 架构做自动化搜索。

- [DSPy: Compiling Declarative Language Model Calls into Self-Improving Pipelines](https://arxiv.org/abs/2310.03714) - 按用户定义指标自动优化提示与示例，编译声明式 LM 程序。(arXiv 2023) [[code]](https://github.com/stanfordnlp/dspy)
- [Large Language Models as Optimizers (OPRO)](https://arxiv.org/abs/2309.03409) - 从带分数的历史尝试中迭代提出自然语言解法与提示。(ICLR 2024)
- [Language Agent Tree Search (LATS)](https://arxiv.org/abs/2310.04406) - 统一蒙特卡洛树搜索、价值估计、环境反馈与自我反思，不更新权重。(ICML 2024)
- [Automated Design of Agentic Systems (ADAS)](https://arxiv.org/abs/2408.08435) - 用元 Agent 发明并迭代改进以可执行代码表示的 Agent 架构。(ICLR 2025) [[code]](https://github.com/ShengranHu/ADAS)
- [TextGrad: Automatic "Differentiation" via Text](https://arxiv.org/abs/2406.07496) - 通过文本反馈在复合 AI 系统中「反向传播」，优化提示与代码。(Nature 2025) [[code]](https://github.com/zou-group/textgrad)
- [GEPA: Reflective Prompt Evolution Can Outperform Reinforcement Learning](https://arxiv.org/abs/2507.19457) - 遗传-Pareto 提示进化：在 Pareto 前沿维护提示池，通过对完整轨迹的自然语言反思提出变异；比 GRPO 最高提升 20%，rollout 用量仅为 1/35。(ICLR 2026 Oral) [[code]](https://github.com/gepa-ai/gepa)

## L5 元改进层

进化的对象是「负责改进的机制」本身。特征失败模式：**指标捕获**——改进者学会优化度量而非能力。

- [Promptbreeder: Self-Referential Self-Improvement via Prompt Evolution](https://arxiv.org/abs/2309.16797) - 同时进化任务提示与「生成未来提示的变异提示」——改进者改进改进者。(ICML 2024)
- [Self-Taught Optimizer (STOP): Recursively Self-Improving Code Generation](https://arxiv.org/abs/2310.02304) - LLM 编写的脚手架程序改进「负责进一步改进的程序」自身。(COLM 2024)
- [Huxley-Gödel Machine](https://arxiv.org/abs/2510.21614) - DGM 的后继：学习「预期自我改进收益」估计来指导修改目标的选择，即进化自我改进的搜索策略。(arXiv 2025)
- [EvoX](https://arxiv.org/abs/2602.23413) - 进化策略本身也作为进化对象的元进化框架。(arXiv 2026)

## L6 准则层

进化的对象是裁判：评估器、验证器、评分准则。特征失败模式：**准则漂移**——裁判在共进化中被其评估的对象带偏。

- [Meta-Rewarding Language Models: Self-Improving Alignment with LLM-as-a-Meta-Judge](https://arxiv.org/abs/2407.19594) - 模型评判自己的评判，迭代改进评估能力与指令跟随能力。(EMNLP 2025)
- [CoEvoSkills: Self-Evolving Agent Skills via Co-Evolutionary Verification](https://arxiv.org/abs/2604.01687) - 技能生成器与信息隔离的代理验证器共进化；验证器看不到生成者的推理过程。(arXiv 2026)

## 算法基础：开放式进化与质量多样性

上述各层共用的搜索算法源头。

- [MAP-Elites: Illuminating Search Spaces by Mapping Elites](https://arxiv.org/abs/1504.04909) - 质量-多样性搜索的开创性工作：维护按行为特征分格的精英档案库。(arXiv 2015)
- [POET: Paired Open-Ended Trailblazer](https://arxiv.org/abs/1901.01753) - 环境与求解器共进化，持续生成难度递增的学习环境及其解。(GECCO 2019)
- [AI-GAs: AI-Generating Algorithms](https://arxiv.org/abs/1905.10985) - 主张同时自动学习环境、架构与学习算法的开放式范式。(arXiv 2019)

## 自我评估与内省

模型对自身能力与行为的度量——为各层提供「改进是否真实」的测量学基础。

- [Let's Verify Step by Step](https://arxiv.org/abs/2305.20050) - 训练过程奖励模型评分中间推理步骤，引导更可靠地选择解答。(ICLR 2024)
- [Language Models (Mostly) Know What They Know](https://arxiv.org/abs/2207.05221) - Anthropic 的研究：模型评估自身答案正确性的校准能力。(arXiv 2022)
- [Looking Inward: Language Models Can Learn About Themselves by Introspection](https://arxiv.org/abs/2410.13787) - 模型对自身行为拥有特权信息通道，预测优于其他模型。(ICLR 2025)

## 安全与目标保持

系统自我修改时可能出什么问题：奖励篡改、目标漂移、欺骗性对齐与监督难题。

- [Concrete Problems in AI Safety](https://arxiv.org/abs/1606.06565) - 系统提出奖励篡改、可扩展监督、安全探索、分布偏移鲁棒性等实际安全问题框架的论文。(arXiv 2016)
- [Scalable Agent Alignment via Reward Modeling](https://arxiv.org/abs/1811.07871) - 递归奖励建模：监督超出人类直接评估能力的 Agent。(arXiv 2018)
- [Risks from Learned Optimization in Advanced Machine Learning Systems](https://arxiv.org/abs/1906.01820) - mesa-optimizer 分析：学习到的内部目标可能与训练目标偏离。(arXiv 2019)
- [Reward Tampering Problems and Solutions in Reinforcement Learning](https://arxiv.org/abs/1908.04734) - 用因果影响图刻画篡改奖励过程的激励并给出设计原则。(Synthese 2021)
- [Optimal Policies Tend to Seek Power](https://arxiv.org/abs/1912.01683) - 证明最优 Agent 在特定条件下有保留选择权、寻求环境控制权的激励。(NeurIPS 2021)
- [Constitutional AI: Harmlessness from AI Feedback](https://arxiv.org/abs/2212.08073) - Anthropic 的方案：用书面原则与模型生成的批评扩大监督规模，保留显式行为约束。(arXiv 2022)
- [Model Evaluation for Extreme Risks](https://arxiv.org/abs/2305.15324) - 针对危险涌现能力（含自主复制与适应）的能力与对齐评估框架。(arXiv 2023)
- [Sleeper Agents: Training Deceptive LLMs that Persist Through Safety Training](https://arxiv.org/abs/2401.05566) - 来自 Anthropic：欺骗性策略可在标准安全训练中保持隐蔽。(arXiv 2024)
- [Safely Interruptible Agents](https://intelligence.org/files/Interruptibility.pdf) - 设计不产生抵抗人为干预激励的强化学习 Agent。(UAI 2016)
- [Evaluating Goal Drift in Language Model Agents](https://arxiv.org/abs/2505.02709) - 度量长时程 Agent 在环境压力下的目标漂移。(arXiv 2025)
- [Your Agent May Misevolve: Emergent Risks in Self-evolving LLM Agents](https://arxiv.org/abs/2509.26354) - 提出 misevolution 概念，系统研究模型、记忆、工具、工作流四条进化路径上的有害漂移。(ICLR 2026)
- [SAHOO: Safeguarded Alignment for High-Order Optimization Objectives in RSI](https://arxiv.org/abs/2603.06333) - 递归自我改进中的对齐漂移监控：目标漂移检测、约束保持检查、回归风险分析。(ICLR 2026 RSI Workshop)

## 评测基准

检验「自我改进」的说法是否成立的任务套件。

- [SWE-bench](https://arxiv.org/abs/2310.06770) - 真实 GitHub issue 解决基准（生成补丁并通过仓库测试验证），DGM 等自我修改系统的常用评估。(ICLR 2024)
- [MLAgentBench](https://arxiv.org/abs/2310.03302) - 评估语言 Agent 能否从研究指令自主执行并改进 ML 实验。(ICML 2024)
- [MLE-bench](https://arxiv.org/abs/2410.07095) - OpenAI 的端到端 ML 工程评估，覆盖 75 个 Kaggle 竞赛。(ICLR 2025)
- [RE-Bench](https://arxiv.org/abs/2411.15114) - 固定时间预算下 AI Agent 与人类专家的开放式 ML 研发任务对比。(ICML 2025)

## 开源框架与工具

可运行的实现：从进化式编码 Agent 到自优化 LM 流水线。

- [OpenEvolve](https://github.com/algorithmicsuperintelligence/openevolve) - AlphaEvolve 的开源复现，社区维护的进化式编码 Agent。
- [DGM](https://github.com/jennyzzt/dgm) - Darwin Gödel Machine 官方实现。
- [FunSearch](https://github.com/google-deepmind/funsearch) - FunSearch 官方参考实现与评估器。
- [ShinkaEvolve](https://github.com/SakanaAI/ShinkaEvolve) - 样本高效程序进化的官方实现。
- [Agentic-ESOpt](https://github.com/zz1358m/Agentic-ESOpt) - 无梯度进化策略微调长时程 Agent 的官方实现，Hugging Face 提供 checkpoints。
- [Voyager](https://github.com/MineDojo/Voyager) - 技能库式终身学习 Agent 官方实现。
- [AI-Scientist](https://github.com/SakanaAI/AI-Scientist) - 自动化研究循环的开源实现。
- [AI-Scientist-v2](https://github.com/SakanaAI/AI-Scientist-v2) - 第二代：无模板 Agent 化树搜索覆盖假设、实验、分析与写作。
- [DSPy](https://github.com/stanfordnlp/dspy) - 声明式 LM 程序的自优化框架。
- [ADAS](https://github.com/ShengranHu/ADAS) - 元 Agent 搜索可执行 Agent 设计的官方实现。
- [TextGrad](https://github.com/zou-group/textgrad) - 文本「梯度」优化框架。
- [GEPA](https://github.com/gepa-ai/gepa) - 遗传-Pareto 提示进化官方实现，并作为优化器集成到 DSPy 中。
- [Agent Zero](https://github.com/agent0ai/agent-zero) - 提示、工具、技能、插件均可检视、替换的开放 Agent 框架。
- [Letta](https://github.com/letta-ai/letta) - 记忆优先的 Agent 框架，长期运行的 Agent 可重写上下文并学习技能。

## 产品与公司

围绕自进化 Agent 技术的商业实践。

- [Sakana AI](https://sakana.ai) - The AI Scientist 系列背后的公司，自动化研究产品线。
- [Apodex](https://platform.apodex.ai) - 自研模型 + 开源 Agent 运行时（[FrontierAgent](https://github.com/ApodexAI/FrontierAgent)），主打以验证为核心的研究型 Agent 团队。
- [Letta](https://www.letta.com) - 状态化/记忆驱动 Agent 的商业平台，开源框架见上文。
- [Agent Zero](https://github.com/agent0ai/agent-zero) - 以个人助手形态发布的开源 Agent 产品。
- [Agent QA](https://github.com/vostride/agent-qa) - 以自然语言执行 Web 和移动端测试，将执行观察整理为持久记忆，并在后续测试步骤中检索复用，是上下文与记忆适应机制的应用。采用 FSL-1.1-ALv2 源码可用许可。

## 历史源流与理论基础

早于 LLM 时代、预示了递归自我改进的思想。

- [Gödel Machines: Self-Referential Universal Problem Solvers](https://people.idsia.ch/~juergen/goedelmachine.html) - 完全自指机器：在证明修改能提升期望效用后改写自身。RSI 的理论原型。(Schmidhuber, 2006)
- [POWERPLAY: Training an Increasingly General Problem Solver](https://arxiv.org/abs/1112.5309) - 交替发明新任务与修改求解器，持续扩展已验证的能力集。(arXiv 2011)
- [Learning to Learn by Gradient Descent by Gradient Descent](https://arxiv.org/abs/1606.04474) - 元学习一个可替代手工优化算法的循环更新规则。(NeurIPS 2016)

## Contributing

欢迎补充。条目需附简要说明与有效来源链接。

## License

[CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/)
