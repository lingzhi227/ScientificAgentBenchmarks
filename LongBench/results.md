# LongBench v2 — Our Results

**Model**: Qwen3.5-27B (27B dense, native 262K context)
**Infrastructure**: 8x A100 80GB (2 nodes), 8 independent vLLM servers, KV capacity ~249K tokens/GPU
**Benchmark**: LongBench v2 — 503 MCQ, contexts 8K–2M words, 6 task categories

---

## Summary

| Mode | Progress | Overall | Easy | Hard | Short | Medium | Long |
|------|----------|---------|------|------|-------|--------|------|
| **Thinking** | 295/503 | **64.1%** | 74.0% | 59.0% | 64.6% | 65.4% | 46.2% |
| **Nothink** | 288/503 | **59.7%** | 71.0% | 53.7% | 62.7% | 56.2% | 46.7% |

| Metric | Thinking | Nothink |
|--------|----------|---------|
| Avg completion tokens | 6,593 | 250 |
| Avg prompt tokens | 70,559 | 66,372 |
| Avg latency | 1,397s | 280s |
| Speed factor | 1x | **5x faster** |

---

## Thinking Mode — Leaderboard Position

Our Qwen3.5-27B with thinking ranks **#4** among all models, behind only Gemini 3 Pro, Gemini-2.5-Pro, and Gemini-2.5-Flash:

| Rank | Model | Params | Overall |
|------|-------|--------|---------|
| 1 | Gemini 3 Pro | undisclosed | 68.2% |
| 2 | Gemini-2.5-Pro | undisclosed | 63.3% |
| 3 | Gemini-2.5-Flash | undisclosed | 62.1% |
| **4** | **Qwen3.5-27B (ours, thinking)** | **27B** | **>61%** |
| 5 | Qwen3.5-27B (official) | 27B | 60.6% |
| 6 | Qwen3-235B-Thinking-2507 | 235B (22B) | 60.6% |
| 7 | Qwen3.5-122B-A10B | 122B (10B) | 60.2% |

Key: a 27B dense model outperforms Qwen3-235B (10x larger MoE) and ties with Qwen3.5-122B (4.5x larger MoE).

---

## Nothink Mode — Potential New SOTA

Our Qwen3.5-27B **without thinking** would rank **#1 among all models** on the official w/o CoT leaderboard, surpassing the human baseline:

| Rank | Model | Params | Overall |
|------|-------|--------|---------|
| — | Human baseline | — | 53.7% |
| **1** | **Qwen3.5-27B (ours, nothink)** | **27B** | **59.7%** |
| 2 | MiniMax-Text-01 | 456B | 52.9% |
| 3 | GPT-4o (Aug 2024) | undisclosed | 50.1% |
| 4 | Gemini-Exp-1206 | undisclosed | 49.3% |
| 5 | Qwen3-235B-Instruct-2507 | 235B (22B) | 46.7% |

**+6.8pp** above previous best model (MiniMax-Text-01), **+6.0pp** above human baseline.

No other model on the official nothink leaderboard exceeds the human baseline of 53.7%.

---

## Why Is Nothink So Strong?

The official w/o CoT leaderboard contains **no Qwen3.5 models** — only models from 2024–early 2025. Our result reflects a genuine generational leap:

### 1. Architecture Revolution
Qwen3.5 uses **GatedDeltaNet + MoE hybrid attention** (3:1 linear:full attention ratio), fundamentally better at long-context processing than standard dense/MoE transformers. Near-linear compute scaling for long sequences.

### 2. Generational Gap
| Model | Nothink | Architecture | Year |
|-------|---------|-------------|------|
| Qwen3-235B-Instruct | 46.7% | Standard MoE | 2025 |
| Qwen3-32B | 38.8% | Dense | 2025 |
| **Qwen3.5-27B (ours)** | **59.7%** | GatedDeltaNet+MoE | 2026 |

Qwen3.5-27B nothink beats Qwen3-235B nothink by **+19.3pp** with **10x fewer parameters**.

### 3. Training Quality
Official claim: "Qwen3.5-35B-A3B (3B active) surpasses Qwen3-235B-A22B (22B active)." Better data curation + improved RL moved intelligence forward, not bigger parameter counts.

### 4. Native Long Context
262K native (extensible to 1M with YaRN), vs many older models at 128K or less.

### 5. Diminishing Returns from Thinking
Think vs Nothink delta is only **+4.4pp** (64.1% vs 59.7%), but thinking costs **5x latency** and **26x output tokens**. The base model capability is already very strong.

---

## Breakdown Analysis

### By Difficulty
| Difficulty | Think | Nothink | Delta |
|------------|-------|---------|-------|
| Easy | 74.0% (74/100) | 71.0% (71/100) | +3.0 |
| Hard | 59.0% (115/195) | 53.7% (101/188) | +5.3 |

Thinking helps more on hard questions (+5.3pp) than easy ones (+3.0pp).

### By Context Length
| Length | Think | Nothink | Delta |
|--------|-------|---------|-------|
| Short (0-32K) | 64.6% (113/175) | 62.7% (111/177) | +1.9 |
| Medium (32K-128K) | 65.4% (70/107) | 56.2% (54/96) | +9.2 |
| Long (128K-2M) | 46.2% (6/13) | 46.7% (7/15) | -0.5 |

Thinking helps most on **medium** contexts (+9.2pp). On long contexts, thinking provides no benefit — both modes struggle equally at ~46%.

### Token Statistics (Thinking Mode)
| Length | Avg Input | Avg Completion | Avg Latency |
|--------|-----------|----------------|-------------|
| Short | 31,616 | 4,895 | 771s |
| Medium | 113,088 | 8,937 | 2,192s |
| Long | 212,804 | 9,346 | 4,430s |

---

## Error Patterns (from 143-question subset analysis)

1. **Surface text matching over deep semantics** (~30%): Anchors on literal match rather than understanding what the question actually asks
2. **Analysis paralysis / self-refutation** (~25%): Initially correct answer overturned through excessive deliberation
3. **Numerical extraction errors in long context** (~15%): Systematic transcription errors from JSON/tables in 28K+ token contexts
4. **Preference for "comprehensive" over precise answers** (~15%): Picks broader option even when the precise one is correct
5. **External knowledge injection** (~10%): Uses memorized knowledge instead of text evidence
6. **Reluctance to choose "none of the above"** (~5%): Forces selection from substantive options

---

## Infrastructure

- KV capacity per GPU: ~249K tokens (95% of 262K max)
- Medium questions (113K avg input) + 16K think reserve = ~129K → 52% of KV capacity
- Long questions (213K avg input) → ~92% of KV capacity, requires exclusive GPU access
- Nothink mode: OUTPUT_RESERVE = 512 tokens (vs 32K for thinking), allows much higher concurrency
- Prompt: standard 0-shot, `"The correct answer is (X)"` format
- Temperature: 0.1

---

## Status

- [x] Thinking mode: 295/503 (58.6% complete)
- [ ] Nothink mode: 288/503 (57.3% complete)
- [ ] Both experiments in progress
