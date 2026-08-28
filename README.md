<div align="center">
  <h1>Awesome RSI</h1>
  <br>
  <a href="https://awesome.re">
    <img src="https://awesome.re/badge-flat2.svg" alt="Awesome">
  </a>
  <p>A curated list of literature, open-source projects, and products on<br>self-evolving agents &amp; recursive self-improvement.</p>
  <p><b>English</b> · <a href="README_cn.md">中文</a></p>
</div>

---

The body is organized by **object of evolution** in six layers, each annotated with its characteristic failure mode. The remaining sections (algorithmic foundations, self-evaluation, safety, benchmarks) cut across layers.

## Contents

- [Surveys](#surveys)
- [L1 Artifact Level](#l1-artifact-level)
- [L2 Model Level](#l2-model-level)
- [L3 Context & Memory Level](#l3-context--memory-level)
- [L4 Harness & Self-Modification Level](#l4-harness--self-modification-level)
- [L5 Meta-Improvement Level](#l5-meta-improvement-level)
- [L6 Criterion Level](#l6-criterion-level)
- [Algorithmic Foundations: Open-Endedness & Quality-Diversity](#algorithmic-foundations-open-endedness--quality-diversity)
- [Self-Evaluation & Introspection](#self-evaluation--introspection)
- [Safety & Goal Preservation](#safety--goal-preservation)
- [Benchmarks](#benchmarks)
- [Open-Source Frameworks & Tools](#open-source-frameworks--tools)
- [Products & Companies](#products--companies)
- [Historical & Theoretical Foundations](#historical--theoretical-foundations)

---

## Surveys

- [Recursive Self-Improvement in AI: From Bounded Self-Refinement to Autonomous Research Loops](https://arxiv.org/abs/2607.07663) - Survey of 1,250 papers organized along two axes — object of improvement × loop closure — with a verification hierarchy (formal verifiers > execution feedback > learned judges > intrinsic self-assessment). (arXiv 2026)
- [A Comprehensive Survey of Self-Evolving AI Agents: Bridging Foundation Models and Lifelong Agentic Systems](https://arxiv.org/abs/2508.07407) - Organizes agent-evolution literature around feedback loops, update targets, application domains, evaluation, and safety. (arXiv 2025)
- [A Survey on Self-Evolution of Large Language Models](https://arxiv.org/abs/2404.14387) - Proposes a four-phase self-evolution framework: experience acquisition, refinement, update, evaluation. (arXiv 2024)
- [A Systematic Survey of Self-Evolving Agents: From Model-Centric to Environment-Driven Co-Evolution](https://doi.org/10.36227/techrxiv.177203250.05832634/v2) - Taxonomy spanning model-centric to environment-driven co-evolution. (TechRxiv 2026)

## L1 Artifact Level

The object of evolution is the system's output — from single responses to persistent artifacts. Characteristic failure mode: **self-confirmation** — iteration without an external signal is rewriting, not progress.

### Within-Task Self-Refinement (No Persistence)

- [Self-Consistency Improves Chain of Thought Reasoning](https://arxiv.org/abs/2203.11171) - Samples multiple reasoning paths and takes the most consistent answer. (ICLR 2023)
- [Self-Refine: Iterative Refinement with Self-Feedback](https://arxiv.org/abs/2303.17651) - One model acts as generator, critic, and refiner over multiple iterations. (NeurIPS 2023)
- [CRITIC: Large Language Models Can Self-Correct with Tool-Interactive Critiquing](https://arxiv.org/abs/2305.11738) - Uses external tools to verify outputs and turn evidence into iterative corrections. (ICLR 2024)
- [Chain-of-Verification Reduces Hallucination in Large Language Models](https://arxiv.org/abs/2309.11495) - Plans and answers independent verification questions before producing a revised response. (ACL 2024 Findings)
- [Improving Factuality and Reasoning in Language Models through Multiagent Debate](https://arxiv.org/abs/2305.14325) - Multiple model instances converge on more accurate answers through iterated proposals and critique. (ICML 2024)
- [Large Language Models Cannot Self-Correct Reasoning Yet](https://arxiv.org/abs/2310.01798) - Intrinsic self-correction without external feedback degrades reasoning; the negative-result baseline for this level. (ICLR 2024)

### Cross-Generational Artifact Evolution (Persistent Artifacts)

Artifacts evolve under evaluator pressure across generations while the system itself stays fixed.

- [Mathematical Discoveries from Program Search with Large Language Models (FunSearch)](https://www.nature.com/articles/s41586-023-06924-6) - Pairs a frozen coding LLM with an executable evaluator for evolutionary program search, yielding new mathematical results. (Nature 2024) [[code]](https://github.com/google-deepmind/funsearch)
- [AlphaEvolve: A Coding Agent for Scientific and Algorithmic Discovery](https://arxiv.org/abs/2506.13131) - Combines LLM-ensemble sampling, automated evaluation, and evolutionary search for algorithm discovery and infrastructure optimization. (DeepMind 2025) [[problems]](https://github.com/google-deepmind/alphaevolve_repository_of_problems)
- [ShinkaEvolve: Towards Open-Ended and Sample-Efficient Program Evolution](https://arxiv.org/abs/2509.19349) - Sample-efficiency-focused program evolution framework reaching comparable results under small evaluation budgets. (ICLR 2026) [[code]](https://github.com/SakanaAI/ShinkaEvolve)
- [Vesper: Effective Harness Engineering for Algorithm Discovery with Coding Agents](https://arxiv.org/abs/2605.15221) - Harness-engineering study for algorithm discovery with coding agents. (arXiv 2026)
- [AutoML-Zero: Evolving Machine Learning Algorithms From Scratch](https://arxiv.org/abs/2003.03384) - Evolves complete learning algorithms from basic mathematical operations, minimizing human design bias. (ICML 2020)
- [Evolutionary Optimization of Model Merging Recipes](https://arxiv.org/abs/2403.13187) - Evolves combinations of open-source models in parameter space and data-flow space. (Sakana, arXiv 2024)
- [The AI Scientist: Towards Fully Automated Open-Ended Scientific Discovery](https://arxiv.org/abs/2408.06292) - The artifact is the research itself: automated idea generation, experiments, paper writing, and reviewing in a full loop. (Sakana, arXiv 2024) [[code]](https://github.com/SakanaAI/AI-Scientist)

## L2 Model Level

The object of evolution is the model's own parameters: weights updated with self-generated data, rewards, or reasoning traces. Characteristic failure mode: **model collapse** — iterated training on self-generated data drains diversity.

### Self-Training & Self-Rewarding

- [Self-Instruct: Aligning Language Models with Self-Generated Instructions](https://arxiv.org/abs/2212.10560) - Bootstraps instruction data from the model itself, filtered, then fine-tunes. (ACL 2023)
- [Large Language Models Can Self-Improve](https://arxiv.org/abs/2210.11610) - Uses high-confidence self-generated answers as pseudo-labels to iteratively fine-tune reasoning tasks. (EMNLP 2023)
- [Self-Alignment with Instruction Backtranslation](https://arxiv.org/abs/2308.06259) - Back-translates instructions from unlabeled model-generated documents to build synthetic pairs for fine-tuning. (ICLR 2024)
- [Self-Rewarding Language Models](https://arxiv.org/abs/2401.10020) - The model generates and judges its own instruction-following data across alignment iterations (its judging ability improves too, crossing into L6). (ICML 2024)
- [Self-Play Fine-Tuning Converts Weak Language Models to Strong Language Models](https://arxiv.org/abs/2401.01335) - Iteratively improves a single model via self-play preference learning without extra human labels. (ICML 2024)
- [RLAIF vs. RLHF: Scaling RL from Human Feedback with AI Feedback](https://arxiv.org/abs/2309.00267) - Replaces direct human feedback with AI-generated preferences for reinforcement learning. (ICML 2024)
- [Self-Adapting Language Models (SEAL)](https://arxiv.org/abs/2506.10943) - Models self-generate update data and fine-tuning directives to adapt their weights to new tasks. (NeurIPS 2025)
- [Agentic ESOpt: Fine-Tuning Long-Horizon LLM Agents with Minimal GPU Requirements](https://arxiv.org/abs/2608.17310) - Full-parameter, gradient-free agent fine-tuning via evolution strategies: sample weight perturbations, score whole trajectories with environment rewards, apply reward-weighted updates. (arXiv 2026) [[code]](https://github.com/zz1358m/Agentic-ESOpt)

### Self-Taught Reasoning

- [STaR: Bootstrapping Reasoning With Reasoning](https://arxiv.org/abs/2203.14465) - Alternates rationale generation, answer filtering, and fine-tuning to bootstrap reasoning. (NeurIPS 2022)
- [Quiet-STaR: Language Models Can Teach Themselves to Think Before Speaking](https://arxiv.org/abs/2403.09629) - Trains models to generate internal reasoning within arbitrary text, not just QA tasks. (COLM 2024)
- [rStar-Math: Small LLMs Can Master Math Reasoning with Self-Evolved Deep Thinking](https://arxiv.org/abs/2501.04519) - MCTS + self-evolved training data + process preference model for math reasoning. (ICML 2025)

## L3 Context & Memory Level

Weights untouched; evolution happens in steadily growing experience, skills, and context: append, retrieve, consolidate, forget. Characteristic failure mode: **context collapse & memory poisoning** — accumulation that degrades rather than improves.

- [Reflexion: Language Agents with Verbal Reinforcement Learning](https://arxiv.org/abs/2303.11366) - Stores natural-language reflections derived from task feedback to improve across trials. (NeurIPS 2023)
- [ExpeL: LLM Agents Are Experiential Learners](https://arxiv.org/abs/2308.10144) - Extracts transferable lessons from successful and failed trajectories without weight updates. (AAAI 2024)
- [MemoryBank: Enhancing Large Language Models with Long-Term Memory](https://arxiv.org/abs/2305.10250) - Long-term interaction memory with selective forgetting, adapting responses over time. (AAAI 2024)
- [Voyager: An Open-Ended Embodied Agent with Large Language Models](https://arxiv.org/abs/2305.16291) - Minecraft lifelong-learning agent: automatic curriculum + a steadily growing library of reusable skills. (TMLR 2024) [[code]](https://github.com/MineDojo/Voyager)
- [Recursive Introspection: Teaching Language Model Agents How to Self-Improve](https://arxiv.org/abs/2407.18219) - Trains models to inspect failed prior attempts and recursively improve on subsequent turns. (NeurIPS 2024)
- [A-MEM: Agentic Memory for LLM Agents](https://arxiv.org/abs/2502.12110) - Dynamically linked note networks whose organization evolves as experience accumulates. (NeurIPS 2025)
- [Agentic Context Engineering (ACE)](https://arxiv.org/abs/2510.04618) - Treats context as a structured playbook that evolves via incremental updates, avoiding context collapse. (ICLR 2026)

## L4 Harness & Self-Modification Level

The object of evolution is the agent's prompts, tools, workflows, and own code: modify, version, roll back. Characteristic failure mode: **scaffold overfitting** — structural changes tuned to the evaluation environment.

### Self-Modifying Agents

- [Darwin Gödel Machine: Open-Ended Evolution of Self-Improving Agents](https://arxiv.org/abs/2505.22954) - Agents modify their own code; benchmark-validated improvements enter an open-ended archive forming a growing tree; SWE-bench 20% → 50%. (ICLR 2026) [[code]](https://github.com/jennyzzt/dgm)
- [SICA: A Self-Improving Coding Agent](https://arxiv.org/abs/2504.15228) - An agent that edits its own implementation and maintains a versioned lineage, empirically improving on SWE-bench Verified. (ICLR 2025 SSI-FM Workshop)
- [Gödel Agent: A Self-Referential Agent Framework for Recursive Self-Improvement](https://arxiv.org/abs/2410.04444) - Self-referential agent framework that can inspect and rewrite its own logic without fixed hand-crafted optimization routines. (ACL 2025)

### Prompt & Program Optimization

- [DSPy: Compiling Declarative Language Model Calls into Self-Improving Pipelines](https://arxiv.org/abs/2310.03714) - Automatically optimizes prompts and demonstrations against user-defined metrics, compiling declarative LM programs. (arXiv 2023) [[code]](https://github.com/stanfordnlp/dspy)
- [Large Language Models as Optimizers (OPRO)](https://arxiv.org/abs/2309.03409) - Iteratively proposes natural-language solutions and prompts from scored history. (ICLR 2024)
- [Language Agent Tree Search (LATS)](https://arxiv.org/abs/2310.04406) - Unifies MCTS, value estimation, environment feedback, and self-reflection without weight updates. (ICML 2024)
- [Automated Design of Agentic Systems (ADAS)](https://arxiv.org/abs/2408.08435) - Uses a meta-agent to invent and iteratively improve agent architectures expressed as executable code. (ICLR 2025) [[code]](https://github.com/ShengranHu/ADAS)
- [TextGrad: Automatic "Differentiation" via Text](https://arxiv.org/abs/2406.07496) - "Backpropagates" textual feedback through compound AI systems to optimize prompts and code. (Nature 2025) [[code]](https://github.com/zou-group/textgrad)
- [GEPA: Reflective Prompt Evolution Can Outperform Reinforcement Learning](https://arxiv.org/abs/2507.19457) - Genetic-Pareto prompt evolution: maintains a pool of prompts on a Pareto frontier and mutates them via natural-language reflection over full trajectories; beats GRPO by up to 20% with 35x fewer rollouts. (ICLR 2026 Oral) [[code]](https://github.com/gepa-ai/gepa)

## L5 Meta-Improvement Level

The object of evolution is the mechanism responsible for improvement itself. Characteristic failure mode: **metric capture** — the improver learns to optimize the measure rather than the capability.

- [Promptbreeder: Self-Referential Self-Improvement via Prompt Evolution](https://arxiv.org/abs/2309.16797) - Evolves both task prompts and the mutation prompts that generate future prompts — the improver improving the improver. (ICML 2024)
- [Self-Taught Optimizer (STOP): Recursively Self-Improving Code Generation](https://arxiv.org/abs/2310.02304) - An LLM-written scaffolding program improves the very program responsible for further improvements. (COLM 2024)
- [Huxley-Gödel Machine](https://arxiv.org/abs/2510.21614) - Successor to DGM: learns an "expected value of self-improvement" estimate to guide the choice of modification targets — evolving the search policy of self-improvement. (arXiv 2025)
- [EvoX](https://arxiv.org/abs/2602.23413) - A meta-evolution framework where the evolutionary strategy is itself an object of evolution. (arXiv 2026)

## L6 Criterion Level

The object of evolution is the judge: evaluators, verifiers, scoring rubrics. Characteristic failure mode: **criterion drift** — the judge gets pulled off course by the judged during co-evolution.

- [Meta-Rewarding Language Models: Self-Improving Alignment with LLM-as-a-Meta-Judge](https://arxiv.org/abs/2407.19594) - The model judges its own judgments, iteratively improving both evaluation ability and instruction following. (EMNLP 2025)
- [CoEvoSkills: Self-Evolving Agent Skills via Co-Evolutionary Verification](https://arxiv.org/abs/2604.01687) - Skill generator and information-isolated proxy verifier co-evolve; the verifier cannot see the generator's reasoning process. (arXiv 2026)

## Algorithmic Foundations: Open-Endedness & Quality-Diversity

The shared source of search algorithms used across all layers above.

- [MAP-Elites: Illuminating Search Spaces by Mapping Elites](https://arxiv.org/abs/1504.04909) - Foundational quality-diversity search: maintains an archive of elites partitioned by behavioral characteristics. (arXiv 2015)
- [POET: Paired Open-Ended Trailblazer](https://arxiv.org/abs/1901.01753) - Co-evolves environments and solvers, continually generating learning environments of increasing difficulty and their solutions. (GECCO 2019)
- [AI-GAs: AI-Generating Algorithms](https://arxiv.org/abs/1905.10985) - Argues for an open-ended paradigm that automatically learns environments, architectures, and learning algorithms together. (arXiv 2019)

## Self-Evaluation & Introspection

How models measure their own competence and behavior — the metrology of "is the improvement real" for every layer.

- [Let's Verify Step by Step](https://arxiv.org/abs/2305.20050) - Trains process reward models to score intermediate reasoning steps, guiding more reliable solution selection. (ICLR 2024)
- [Language Models (Mostly) Know What They Know](https://arxiv.org/abs/2207.05221) - Studies models' calibration in assessing the correctness of their own answers. (Anthropic, arXiv 2022)
- [Looking Inward: Language Models Can Learn About Themselves by Introspection](https://arxiv.org/abs/2410.13787) - Models hold privileged predictive access to their own behavior, beating other models' predictions. (ICLR 2025)

## Safety & Goal Preservation

- [Concrete Problems in AI Safety](https://arxiv.org/abs/1606.06565) - Framing paper for practical safety problems: reward hacking, scalable oversight, safe exploration, robustness to distributional shift. (arXiv 2016)
- [Scalable Agent Alignment via Reward Modeling](https://arxiv.org/abs/1811.07871) - Recursive reward modeling: supervising agents beyond direct human evaluation ability. (arXiv 2018)
- [Risks from Learned Optimization in Advanced Machine Learning Systems](https://arxiv.org/abs/1906.01820) - The mesa-optimizer analysis: learned internal objectives may diverge from training objectives. (arXiv 2019)
- [Reward Tampering Problems and Solutions in Reinforcement Learning](https://arxiv.org/abs/1908.04734) - Uses causal influence diagrams to characterize incentives for tampering with the reward process, with design principles. (Synthese 2021)
- [Optimal Policies Tend to Seek Power](https://arxiv.org/abs/1912.01683) - Proves that optimal agents have incentives to preserve options and seek environmental control under certain conditions. (NeurIPS 2021)
- [Constitutional AI: Harmlessness from AI Feedback](https://arxiv.org/abs/2212.08073) - Scales oversight with written principles and model-generated critiques while retaining explicit behavioral constraints. (Anthropic, arXiv 2022)
- [Model Evaluation for Extreme Risks](https://arxiv.org/abs/2305.15324) - Capability and alignment evaluation framework for dangerous emergent capabilities, including autonomous replication and adaptation. (arXiv 2023)
- [Sleeper Agents: Training Deceptive LLMs that Persist Through Safety Training](https://arxiv.org/abs/2401.05566) - Deceptive policies can remain hidden through standard safety training. (Anthropic, arXiv 2024)
- [Safely Interruptible Agents](https://intelligence.org/files/Interruptibility.pdf) - Designing RL agents that do not acquire incentives to resist human intervention. (UAI 2016)
- [Evaluating Goal Drift in Language Model Agents](https://arxiv.org/abs/2505.02709) - Measures goal drift in long-horizon agents under environmental pressure. (arXiv 2025)
- [Your Agent May Misevolve: Emergent Risks in Self-evolving LLM Agents](https://arxiv.org/abs/2509.26354) - Coins "misevolution" and systematically studies harmful drift across four evolutionary pathways: model, memory, tools, workflow. (ICLR 2026)
- [SAHOO: Safeguarded Alignment for High-Order Optimization Objectives in RSI](https://arxiv.org/abs/2603.06333) - Alignment-drift monitoring in recursive self-improvement: goal-drift detection, constraint-preservation checks, regression-risk analysis. (ICLR 2026 RSI Workshop)

## Benchmarks

- [SWE-bench](https://arxiv.org/abs/2310.06770) - Benchmark of generating patches that resolve real-world GitHub issues, verified by repository test suites; the standard evaluation for self-modifying systems like DGM. (ICLR 2024)
- [MLAgentBench](https://arxiv.org/abs/2310.03302) - Evaluates whether language agents can autonomously execute and improve ML experiments from research instructions. (ICML 2024)
- [MLE-bench](https://arxiv.org/abs/2410.07095) - End-to-end ML engineering evaluation across 75 Kaggle competitions. (OpenAI, ICLR 2025)
- [RE-Bench](https://arxiv.org/abs/2411.15114) - Open-ended ML R&D tasks comparing AI agents against human experts under fixed time budgets. (ICML 2025)

## Open-Source Frameworks & Tools

- [OpenEvolve](https://github.com/algorithmicsuperintelligence/openevolve) - Open-source reproduction of AlphaEvolve; community-maintained evolutionary coding agent.
- [DGM](https://github.com/jennyzzt/dgm) - Official implementation of the Darwin Gödel Machine.
- [FunSearch](https://github.com/google-deepmind/funsearch) - Official FunSearch reference implementation and evaluators.
- [ShinkaEvolve](https://github.com/SakanaAI/ShinkaEvolve) - Official implementation of sample-efficient program evolution.
- [Agentic-ESOpt](https://github.com/zz1358m/Agentic-ESOpt) - Official implementation of gradient-free evolution-strategy fine-tuning for long-horizon LLM agents; checkpoints on Hugging Face.
- [Voyager](https://github.com/MineDojo/Voyager) - Official implementation of the skill-library lifelong-learning agent.
- [AI-Scientist](https://github.com/SakanaAI/AI-Scientist) - Open-source automated research loop.
- [AI-Scientist-v2](https://github.com/SakanaAI/AI-Scientist-v2) - Second generation: template-free agentic tree search covering hypothesis, experiments, analysis, and writing.
- [DSPy](https://github.com/stanfordnlp/dspy) - Self-optimizing framework for declarative LM programs.
- [ADAS](https://github.com/ShengranHu/ADAS) - Official implementation of meta-agent search over executable agent designs.
- [TextGrad](https://github.com/zou-group/textgrad) - Textual-"gradient" optimization framework.
- [GEPA](https://github.com/gepa-ai/gepa) - Genetic-Pareto prompt evolution with reflective feedback; also integrated into DSPy as an optimizer.
- [Agent Zero](https://github.com/agent0ai/agent-zero) - Open agent framework where prompts, tools, skills, and plugins are all inspectable and replaceable.
- [Letta](https://github.com/letta-ai/letta) - Memory-first agent framework; long-running agents rewrite their own context and learn skills.

## Products & Companies

- [Sakana AI](https://sakana.ai) - The company behind The AI Scientist series; automated-research product line.
- [Apodex](https://platform.apodex.ai) - In-house models + open-source agent runtime ([FrontierAgent](https://github.com/ApodexAI/FrontierAgent)); verification-centric research agent teams.
- [Letta](https://www.letta.com) - Commercial platform for stateful, memory-driven agents; open-source framework listed above.
- [Agent Zero](https://github.com/agent0ai/agent-zero) - Open-source agent product distributed as a personal assistant.

## Historical & Theoretical Foundations

- [Gödel Machines: Self-Referential Universal Problem Solvers](https://people.idsia.ch/~juergen/goedelmachine.html) - Fully self-referential machines that rewrite themselves after proving the modification improves expected utility. The theoretical prototype of RSI. (Schmidhuber, 2006)
- [POWERPLAY: Training an Increasingly General Problem Solver](https://arxiv.org/abs/1112.5309) - Alternates inventing new tasks and modifying the solver, steadily growing a verified capability set. (arXiv 2011)
- [Learning to Learn by Gradient Descent by Gradient Descent](https://arxiv.org/abs/1606.04474) - Meta-learns a recurrent update rule that can replace hand-designed optimization algorithms. (NeurIPS 2016)

## License

[CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/)
