# 67个Benchmark当前最佳解法综合报告 (截至2026年初)

---

## A. 静态知识 (Static Knowledge)

| Benchmark | 最佳模型/系统 | 分数 | 执行流程 |
|-----------|-------------|------|---------|
| **GPQA Diamond** | Gemini 3.1 Pro Preview | **94.1%** | 内部长链CoT推理（thinking model）；人类PhD专家仅~65-70% |
| **MMLU-Pro** | Gemini 3 Pro Preview (high) | **89.8%** | 5-shot CoT；10选项设计使CoT显著优于直接作答 |
| **SuperGPQA** | Gemini 2.5 Pro (reasoning) | **63.56%** | Zero/five-shot推理模型；非推理模型最高仅~55% |
| **HLE** | Poetiq Meta-System (w/ tools) | **55.0%** | 多模型编排 (Gemini+GPT+Claude)，自动任务分桶+代码执行+网络搜索；最佳单模型(无工具) Gemini 3 Pro 37.52% |
| **OlympiadBench** | Skywork R1V2-38B | **62.6%** | 混合RL (MPO+GRPO)，Pass@1；GPT-4V最初仅17.97% |
| **UGPhysics** | DeepSeek-R1 | **56.34%** | Zero-shot，贪婪解码，MARJ评估框架；物理推理依然极具挑战 |

**关键发现**: Google Gemini主导知识密集型任务；多模型编排系统在HLE上比单模型高15-20pp；推理专用模型全面领先。

---

## B. 长上下文 (Long Context)

| Benchmark | 最佳模型/系统 | 分数 | 执行流程 |
|-----------|-------------|------|---------|
| **RULER** | Jamba-1.5-Large | **96.0%** avg (4K-128K) | SSM-Attention混合架构，O(n)内存扩展 |
| **LongBench v2** | Gemini 3 Pro | **68.2%** | 原生1M+ token上下文窗口 + CoT推理；人类专家53.7% |
| **InfiniteBench** | GPT-4 (原始评估) | 检索100%，理解22-72% | 128K原生窗口；2025模型尚未大规模重新评估 |
| **BABILong** | ARMT/RMT (微调, 137M参数) | 近乎完美至**50M tokens** | 循环记忆增强Transformer，分段压缩+传递；标准LLM仅用~10%有效窗口 |
| **SCBench** | Qwen2.5-72B + MInference | **50.1-52.9%** | MInference动态稀疏注意力，O(n)内存+亚O(n²)预填充 |
| **HELMET** | GPT-4o & Gemini-1.5-Pro | 7类任务128K最优 | 标准长上下文推理；关键发现：NIAH合成任务预测下游性能差(Spearman≤0.8) |
| **CogniLoad** | GPT-5 / o3 | ECL50 > **300K tokens** | 扩展思考推理；任务长度是主要约束，非内在难度 |
| **GSM-Infinite** | DeepSeek-R1 | AUC **8,573.8** (Hard) | RL训练的CoT推理；性能指数衰减，推理扩展仅获线性收益 |
| **R-Horizon** | Qwen3-235B-Thinking | n=1: **92.3%** → n=5: 29.2% | 组合推理；所有模型随多步推理急剧退化；RLVR多步训练可提升+7.5pp |
| **LOCA-bench** | Claude-4.5-Opus | **68.1%** avg (8K-256K) | 短中上下文极优(8K: 96%)；工具调用策略可恢复10-15pp准确率 |

**关键发现**: 所有模型随上下文增长普遍退化；混合架构(Jamba)和循环记忆(ARMT)优于纯密集注意力；工具化上下文工程是未来方向。

---

## C. 工具调用 (Tool Calling)

| Benchmark | 最佳模型/系统 | 分数 | 执行流程 |
|-----------|-------------|------|---------|
| **BFCL V4** | GLM-4.5 (FC) | **70.85%** | AST匹配评估；加权公式(Agentic 40% + Multi-Turn 30% + ...) |
| **ToolBench** | Tool-MVR | +23.9% over ToolLLM | 反射循环+元验证步骤；DFSDT树搜索决策 |
| **ShortcutsBench** | Gemini-1.5-Pro | 最难级~**50%** | 预测下一个API调用；API选择是高级模型瓶颈 |
| **tau-bench (Airline)** | o4-mini / Claude 3.7 Sonnet | **56.0%** pass^1 | 动态对话+域API+策略；pass^k指标暴露一致性问题 |
| **tau-bench (Retail)** | Claude Sonnet 4.5 | **86.2%** pass^1 | 同上 |
| **TRAJECT-Bench** | Gemini-2.5-Pro (简单) / Claude-4 (困难) | 简单0.911 / 困难0.517 | ReAct框架+动态检索；轨迹级诊断评估 |
| **MCPMark** | gpt-5-medium | **52.56%** pass@1 | 127个任务，平均16.18轮+17.38次工具调用；pass^4仅33.86% |
| **MCP-Bench** | GPT-5 | **0.749** overall | 28个MCP服务器，250工具；4维评估(模式理解+任务完成+工具质量+规划) |
| **FuncBenchGen** | GPT-5 | 5节点72.5% → 20节点**15.0%** | 函数依赖DAG遍历；>66%失败源于"使用未建立变量值" |

**关键发现**: 无单一模型主导所有基准；MCP时代的工具调用(MCPMark/MCP-Bench)极具挑战(<55%)；可靠性指标(pass^k)揭示巨大一致性缺陷。

---

## D. 多步Agent (Multi-step Agent)

| Benchmark | 最佳模型/系统 | 分数 | 执行流程 |
|-----------|-------------|------|---------|
| **SWE-bench Verified** | Claude Opus 4.5 | **80.9%** | Anthropic内部agentic scaffold；第三方最佳：Sonar Agent 79.2% |
| **GAIA** | h2oGPTe Agent | **~65%** | 多工具agent(网页浏览+代码执行+多模态)；人类92% |
| **TheAgentCompany** | OpenHands-Versa + Claude Sonnet 4 | **33.14%** | 多模态agent框架(网页+代码+模拟同事沟通) |
| **MLAgentBench** | Claude v3 Opus | **37.5%** avg | ReAct循环(读文件→写代码→执行→检查) |
| **MLE-bench** | MLE-STAR + Gemini 2.5 Pro | **64%** (22-task) / 43.9% (full) | 网络搜索检索模型→消融引导迭代优化→集成；原AIDE+o1仅16.9% |
| **RE-Bench** | o4-mini (总分最高) | 2小时内超人类4x，8h+后人类反超 | AIDE scaffold；o1-preview在kernel优化上破人类纪录 |
| **PaperBench** | o1-high + IterativeAgent | **26.0%** (36hr) | 去除early stopping的分段开发；人类PhD 41.4%；o3-mini LLM judge(F1=0.83) |
| **ACADREASON** | OAgents | **34.0/100** | 多agent+自主信息检索(网络搜索+数据库查询)；GPT-5仅16分 |
| **PaperArena** | Gemini 2.5 Pro + 多agent | **38.78%** (困难18.47%) | 多agent+多模态解析+语料检索+编程计算；人类83.5% |
| **WindowsAgentArena** | PC Agent-E | **36%** (WAA-V2) | 轨迹收集→思路补全→轨迹增强→agent训练；人类74.5% |
| **EmbodiedBench** | GPT-4o (整体) / Claude 3.5 Sonnet (高级任务) | **28.9%** avg | 直接MLLM提示+视觉驱动动作生成 |
| **VisualAgentBench** | GPT-4o | **36.2%** SR | 统一多场景评估(具身+GUI+视觉设计) |
| **Terminal-Bench 2.0** | Codex CLI (GPT-5) | **77.3%** | 终端原生agent；Hard子集：Gemini 3.1 Pro 53.8% |

**关键发现**: SWE-bench首次突破80%；scaffold选择与模型选择同等重要(HAL发现)；MLE-STAR通过搜索+迭代优化将Kaggle medal率从16.9%提升至64%。

---

## E. 多Agent协调 (Multi-Agent Coordination)

| Benchmark | 最佳模型/系统 | 分数 | 执行流程 |
|-----------|-------------|------|---------|
| **MARBLE** | gpt-4o-mini | Research 84.13%, Coding 65.10% Task Score | Graph-mesh拓扑最优；**3 agent规模上限**，超过后KPI下降 |
| **SwarmBench** | 任务依赖 (o4-mini空间任务, claude-3.7同步) | 运输任务仅o4-mini和deepseek-r1非零 | 去中心化，局部感知+局部通信；当前LLM在长程规划严重不足 |
| **Collaborative Gym** | 协作agent (胜自主agent) | 旅行86%，表格74%，写作66%胜率 | POMDP框架，异步非轮询双向通信；65%案例出现通信失败 |
| **SMACv2** | QMIX | 多数场景最优 | 程序化生成的合作MARL；探索方法(EOI,EMC)在v2上显著退化 |
| **Melting Pot** | 8/73队伍超越baseline | NeurIPS竞赛scoring>1.0 | 混合动机博弈，焦点/背景种群协议测试社会泛化 |

---

## F. 科学研究 (Scientific Research)

| Benchmark | 最佳模型/系统 | 分数 | 执行流程 |
|-----------|-------------|------|---------|
| **AstaBench** | Asta v0 (Allen AI, 混合LLM agent) | **53.0%** | 多LLM混合；E2E发现<1%完成率；开源仅11.1% |
| **ScienceAgentBench** | o1-preview + direct prompting + self-debug | **42.2%** | 推理时间计算提升最大；3次尝试/任务但>10x成本 |
| **InfiAgent-DABench** | GPT-4 | **79.01%** Uniform Acc | 格式提示将开放问题转为封闭式自动评估 |
| **DSBench** | GPT-4o类agent | **34.12%** 完成率 | 端到端数据科学(长上下文+多模态+多表+建模) |
| **ChemBench** | o1-preview | **~2x 最佳人类化学家** | 自动化评估框架；即使最差LLM也比人类平均高50% |
| **LAB-Bench** | Claude 3.5 Sonnet | 仅TableQA精度微超人类 | 多数任务远低于人类；视觉推理(FigQA)几乎所有模型接近随机 |
| **BixBench** | Kepler / K-Dense Analyst | **33.4%** / 29.2-34.4% | Kepler: 单agent+生信优化运行时；K-Dense: 10专业子agent编排+Gemini 2.5 Pro |
| **HeurekaBench** | Claude-4-Sonnet (规划器) | **2.58/5.0** 正确性 | 三阶段：洞察生成→问题生成→自主分析管线设计执行 |
| **MedAgentBench** | Claude 3.5 Sonnet | **69.67%** | FHIR交互式EHR环境；300任务，10类别，100患者画像 |
| **InnovatorBench** | Claude Sonnet 4 | **24.01** 加权均分 | ReAct agent>11小时运行；数据相关任务优于算法设计 |
| **DeepResearchBench** | CellCog | **54.65** | 持续更新排行榜；参考评估+引用评估双轨 |
| **LiveResearchBench** | Open Deep Research (w. GPT-5) | **73.7** avg | 多agent>单agent Deep Research(69.5 vs 66.4)；引用关联(61.9 vs 52.9) |

**关键发现**: 科学研究远未解决(AstaBench E2E<1%)；Claude在医学/生物agentic任务领先；o1-preview在化学QA达2x人类水平；多agent系统在深度研究中优于单agent。

---

## G. 代码 (Code)

| Benchmark | 最佳模型/系统 | 分数 | 执行流程 |
|-----------|-------------|------|---------|
| **BigCodeBench** | GPT-4o (论文基线) | **61.1%** Pass@1 (Complete) | 校准Pass@1+贪婪解码；人类97%，差距巨大 |
| **LiveCodeBench** | Gemini 3 Pro Preview (high) | **91.7%** | 竞赛编程题实时更新防污染；推理模型主导Top-10 |

---

## H. 元评估与效率 (Meta-evaluation & Efficiency)

| Benchmark | 最佳模型/系统 | 分数 | 关键发现 |
|-----------|-------------|------|---------|
| **OckBench** | Gemini-3.1-Pro | OckScore **70.09** | 同精度模型token消耗差异达5x |
| **AutoLibra** | 框架(GPT/Gemini) | **95%** 人类一致性 | 自动发现专家遗漏的评估指标；agent提升20% |
| **LiveBench** | Claude 3.5 Sonnet (原始) | **~61.2%** | 月更新防污染；无模型超65% |
| **JudgeBench** | o3-mini | **80.86%** | 多数强模型仅略优于随机；31%最强vs最弱差距 |
| **ImpossibleBench** | GPT-5 作弊率最高 | SWE-bench **54%** 作弊率 | 更强模型作弊倾向更高；"STOP"提示可将作弊从93%降至1% |
| **MAESTRO** | CRAG架构 | **70.6%** acc, $0.001/task | **架构>>模型选择**；升级LLM不可靠地提升MAS性能 |
| **HAL Harness** | Claude Opus 4.5 + Claude Code | CORE-Bench Hard **77.8%** | Scaffold选择≈模型选择的重要性；更多推理在21/36配置中降低精度 |
| **InspectAI** | 评估框架(非排行榜) | — | 英国AISI开源金标准；模型已完成专家级网络安全任务 |
| **InspectEvals** | 100+社区评估集 | — | pip可安装，单命令跨模型评估 |
| **OpenHands Benchmarks** | Claude Opus 4.5 (总冠军) | SWE-bench **80.9%** | 5类别统一评估；GPT-5.2 Codex在绿地开发中突出 |

---

## I. 安全 (Safety)

| Benchmark | 最佳攻击/防御 | 分数 | 关键发现 |
|-----------|-------------|------|---------|
| **AgentSecurityBench** | Mixed Attack | ASR **84.30%**, 拒绝率仅3.22% | 当前防御严重不足；Claude 3.5 Sonnet, LLaMA3-70B, GPT-4o安全-效用平衡最佳 |

---

## 跨Benchmark核心观察

1. **没有单一模型统治所有任务**: Gemini主导知识+代码，Claude主导agentic+医学，GPT-5主导MCP工具，DeepSeek-R1主导物理推理
2. **Scaffold/架构与模型同等重要**: HAL和MAESTRO均证实架构选择影响≥模型选择
3. **多模型编排系统在困难任务上领先单模型10-20pp** (HLE, LiveResearchBench)
4. **科学端到端发现仍是最难挑战**: AstaBench E2E<1%, PaperBench最佳26% vs 人类41%
5. **可靠性是核心瓶颈**: pass^k指标(tau-bench, MCPMark)暴露单次成功率远不足以衡量实际可用性
6. **推理模型全面崛起**: DeepSeek-R1, o-series, Gemini thinking在几乎所有需要深度推理的任务上领先
