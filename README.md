<div align="center">

# Jiahao Tan

### Agent Systems · Reproducible Evaluation · LLM Applications

Building decision-making agents and the experiments that explain their behavior.

[Featured project](https://github.com/JiahaoTanXX/Kaggle-Featured-Competition) · [Technical report](https://github.com/JiahaoTanXX/Kaggle-Featured-Competition/blob/main/reports/技术报告.md) · [Email](mailto:tanjiahaoxx@163.com)

</div>

---

I work on agent decision-making, evaluation, and LLM-assisted analysis. My current public work centers on **long-horizon planning in simulated environments**: turning observations into legal actions, diagnosing failures from replays, and testing strategy changes with controlled experiments.

我关注 Agent 决策、可复现评测与 LLM 辅助分析，希望让系统的行为有迹可循，让策略改进有实验依据。

### Featured work

#### [Kaggriculture — Long-Horizon Decision Agent & Evaluation System](https://github.com/JiahaoTanXX/Kaggle-Featured-Competition)

A modular Python agent for a **720-turn agricultural economy simulation**, with a companion evaluation and replay-analysis workflow.

| Component | Implementation |
| :--- | :--- |
| **Decision pipeline** | State parsing, crop and resource planning, unit task scheduling, market decisions, and legal-action safeguards |
| **Controlled evaluation** | Fixed seeds, both player seats, three official baseline opponents, and strategy ablations |
| **Replay analysis** | Structured action and economy summaries, deterministic diagnostics, and an optional offline LLM analyst |
| **Experiment tooling** | Match runners, tournament scripts, submission packaging, and unit / environment integration tests |

```text
Observe → Plan resources → Schedule tasks → Validate actions → Act
   ↑                                                           │
   └── Controlled experiments ← Diagnose failures ← Replay ─────┘
```

**Recorded baseline check:** 12 wins across 12 local games against `pass`, `random`, and `starter`, using two fixed seeds and both player seats. This is a small engineering validation set, not a leaderboard result; broader evaluation remains necessary.

**Ablation finding:** disabling task scheduling changed the recorded result against `starter` from 4/4 wins for the rule baseline to 0/4. The report also records settings with no measured additional gain, including opponent awareness and bootstrap value scoring in this test.

[Agent code](https://github.com/JiahaoTanXX/Kaggle-Featured-Competition/tree/main/src/kaggriculture_agent) · [Evaluation protocol](https://github.com/JiahaoTanXX/Kaggle-Featured-Competition/blob/main/reports/实验协议.md) · [Recorded results](https://github.com/JiahaoTanXX/Kaggle-Featured-Competition/blob/main/reports/baseline-validation-2026-08-29.json) · [Technical report](https://github.com/JiahaoTanXX/Kaggle-Featured-Competition/blob/main/reports/技术报告.md)

### LLM-assisted experiment analysis

The project's [Replay Analyst](https://github.com/JiahaoTanXX/Kaggle-Featured-Competition/tree/main/analyst) connects structured replay evidence to failure hypotheses and candidate experiments.

- **Offline by default:** produces deterministic diagnostics and a reviewable prompt packet.
- **Optional model integration:** supports an OpenAI-compatible API for post-match analysis.
- **Separate from the acting policy:** the LLM analyzes completed games; the submitted agent uses a lightweight rule-based decision pipeline.
- **Evidence before promotion:** the experiment protocol requires controlled comparisons before adopting a proposed strategy change.

### Interests & collaboration

**Research interests:** long-horizon agent planning, evaluation and failure analysis, LLM-assisted experimentation, and data science.

**Also exploring:** small language models through [MiniMind](https://github.com/JiahaoTanXX/minimind), a fork of [jingyaogong/minimind](https://github.com/jingyaogong/minimind).

I'm interested in **AI / LLM / Agent opportunities** and research collaborations around agent systems and reproducible evaluation.

**Contact:** [tanjiahaoxx@163.com](mailto:tanjiahaoxx@163.com) · English / 中文
