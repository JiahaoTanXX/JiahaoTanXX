<div align="center">


### Agentic RL Data · Coding Agents · Reproducible Research

Understanding how agent trajectories become reliable training data.

MSc student in Data Science at **City University of Hong Kong**

[Trace2Batch](https://github.com/JiahaoTanXX/Trace2Batch) &nbsp;·&nbsp; [SkillLoop](https://github.com/JiahaoTanXX/SkillLoop) &nbsp;·&nbsp; [Merged contribution](https://github.com/microsoft/agent-lightning/pull/587) &nbsp;·&nbsp; [Contact](mailto:t.jiahao@outlook.com)

</div>

---

I work on the data and tooling behind multi-turn agents: **trajectory aggregation, token-level consistency, and training-sample construction**. I also build systems for **agent safety evaluation and regression testing**. Across both, I focus on observable behavior, reproducible experiments, and evidence that can be inspected.


## Selected projects

### [Trace2Batch](https://github.com/JiahaoTanXX/Trace2Batch)

**A diagnostic toolkit and empirical study of multi-turn trajectory data for agentic RL.**

Merging agent turns into a training sample requires the next prompt to preserve the previous token context. Trace2Batch investigates how chat templates, tool-call parsing, and re-tokenization can silently break that assumption.

| Study | Evidence |
| :--- | :--- |
| **Chat-template consistency** | 900 public trajectories, 5 tokenizers across 4 model families, and 107,848 merge attempts in an offline collection-path simulation |
| **Real sampling** | Follow-up experiments with model sampling and a live vLLM server separate template rewrites, parser formatting, and tokenization mismatches |
| **Length-budget allocation** | On SWE-smith at a 16,384-token row limit, dynamic prompt/response allocation raised policy-token retention from **26.3% to 54.6%** |

**What I built**

- A dependency-free sample builder and mismatch classifier for trajectory aggregation, policy masks, rewards, and truncation.
- Prefix-stable template patches and a token-in-token-out reference implementation.
- Reproducible experiments with pinned data/model revisions, fixed sampling seeds, offline and tokenizer tests, and CI.

**Selected finding:** in canonical-output experiments, template patches restored merging from **0% to 100%** for the tested Qwen3 non-thinking and gpt-oss configurations. Real sampling exposed additional parser and tokenization failures, motivating token-preserving collection.

These are data-pipeline findings; merge rates and token retention do not establish downstream model-quality gains.

[Code](https://github.com/JiahaoTanXX/Trace2Batch/tree/main/trace2batch) · [Prefix study](https://github.com/JiahaoTanXX/Trace2Batch/blob/main/experiments/template_prefix/REPORT.md) · [Template patches](https://github.com/JiahaoTanXX/Trace2Batch/blob/main/experiments/template_patch/REPORT.md) · [GPU sampling](https://github.com/JiahaoTanXX/Trace2Batch/blob/main/experiments/vllm_sampling/REPORT.md) · [Budget study](https://github.com/JiahaoTanXX/Trace2Batch/blob/main/experiments/truncation/REPORT.md)

### [SkillLoop](https://github.com/JiahaoTanXX/SkillLoop)

**A safety evaluation and CI platform prototype for agent skills.**

SkillLoop tests whether a skill completes its task correctly and whether adversarial inputs cause observable unauthorized effects. It connects semantic scanning, adversarial testing, controlled tool execution, independent outcome checks, and patch regression.

- **Evidence-based evaluation:** checks task artifacts and tool-proxy events, with separate judgments for business success, safety violations, and evidence completeness.
- **Controlled execution:** validates structured tool requests through a runtime and proxy, with SQLite-backed task state and auditable call records.
- **Repair and regression:** tests candidate patches against the original case, attack variants, and normal tasks.
- **Interactive demo:** an order-processing workbench for inspecting findings, comparing candidates, and exporting redacted reports; additional profiles cover refunds and Markdown indexing.

[Repository](https://github.com/JiahaoTanXX/SkillLoop) · [Demo guide](https://github.com/JiahaoTanXX/SkillLoop/blob/main/demo/README.md) · [Architecture](https://github.com/JiahaoTanXX/SkillLoop/blob/main/docs/system-design-v2.2.zh-CN.md)

## Open-source contributions

**Microsoft Agent Lightning**

- **[PR #587 — Merged](https://github.com/microsoft/agent-lightning/pull/587)**  
  Fixed LLM Gateway handling of valid JSON with a non-object top-level value. Added input validation and parameterized regression tests so strings, arrays, numbers, and `null` receive a clear **HTTP 400** response instead of a server error.

- **[Issue #645 — Proposal](https://github.com/microsoft/agent-lightning/issues/645)**  
  Reported missing cause attribution in trajectory-merge diagnostics, backed by experiments on **900 public agent trajectories**. Proposed separating template mismatches from re-tokenization failures, with a standalone reference implementation.

## Background

**City University of Hong Kong** — MSc in Data Science, 2026–2028 (expected)  
**South China Agricultural University** — Bachelor's in Software Engineering, 2021–2025 · GPA: 90/100 · Outstanding Graduate

---

Interested in reliable agent training data or coding-agent systems?  
**[t.jiahao@outlook.com] / [tanjiahaoxx@163.com]**
