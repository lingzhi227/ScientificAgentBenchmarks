# LongBench v2 Leaderboard

## Thinking Mode (w/ CoT)

Models sorted by overall accuracy (%). Short: 0-32k, Medium: 32k-128k, Long: 128k-2M words.

| Rank | Model | Params (Active) | Overall (%) | Short | Medium | Long | Source |
|------|-------|-----------------|-------------|-------|--------|------|--------|
| 1 | Gemini 3 Pro | undisclosed | 68.2 | — | — | — | third-party |
| 2 | Gemini-2.5-Pro | undisclosed | 63.3 | 75.0 | 56.1 | 71.0 | official |
| 3 | Gemini-2.5-Flash | undisclosed | 62.1 | 72.3 | 55.8 | 68.3 | official |
| 4 | **Qwen3.5-27B (ours)** | **27B** | **>61** | — | — | — | **in progress** |
| 5 | Qwen3.5-27B | 27B | 60.6 | — | — | — | official (HF) |
| 6 | Qwen3-235B-Thinking-2507 | 235B (22B) | 60.6 | 70.5 | 54.4 | 62.8 | official |
| 7 | Qwen3.5-122B-A10B | 122B (10B) | 60.2 | — | — | — | official (HF) |
| 8 | Qwen3.5-35B-A3B | 35B (3B) | 59.0 | — | — | — | official (HF) |
| 9 | DeepSeek-R1 | 671B (37B) | 58.3 | 66.1 | 53.4 | 62.2 | official |
| 9 | Qwen3-235B-Instruct-2507 | 235B (22B) | 58.3 | 66.7 | 53.1 | 63.3 | official |
| 11 | o1-preview | undisclosed | 57.7 | 66.8 | 52.1 | 62.6 | official |
| 12 | GPT-5-mini | undisclosed | 56.8 | — | — | — | official (HF) |
| 13 | DeepSeek-R1-0528 | 671B (37B) | 56.7 | 59.4 | 55.0 | 66.7 | official |
| 14 | MiniMax-Text-01 | 456B | 56.5 | 66.1 | 50.5 | 61.7 | official |
| 15 | Gemini-2.0-Flash-Thinking | undisclosed | 56.0 | 62.8 | 51.9 | 61.1 | official |
| 16 | Qwen3-235B-A22B | 235B (22B) | 54.8 | — | — | — | official (HF) |
| 17 | GPT-5.2 | undisclosed | 54.5 | — | — | — | third-party |
| — | **Human baseline** | — | **53.7** | 100 | 47.2 | 59.1 | official |
| 18 | Gemini-Exp-1206 | undisclosed | 52.5 | 61.5 | 47.1 | 55.6 | official |
| 19 | GPT-4o (Nov 2024) | undisclosed | 51.4 | 54.2 | 49.7 | 59.6 | official |
| 20 | Gemini-2.0-Flash | undisclosed | 51.1 | 58.3 | 46.6 | 57.2 | official |
| 21 | GLM-4.5 | undisclosed | 50.3 | 57.8 | 45.7 | 57.8 | official |
| 22 | Qwen3-30B-A3B-Thinking | 30B (3B) | 50.1 | 58.9 | 44.7 | 56.7 | official |
| 23 | Qwen3-32B | 32B | 49.2 | 53.1 | 46.8 | 60.0 | official |
| 24 | QwQ-32B | 32B | 48.9 | 58.9 | 42.8 | 54.4 | official |
| 25 | GLM-4.5-Air | 106B (12B) | 48.6 | 54.7 | 44.8 | 58.9 | official |
| 26 | GPT-OSS-120B | 120B | 48.2 | — | — | — | official (HF) |
| 27 | Claude 3.5 Sonnet | undisclosed | 46.7 | 55.2 | 41.5 | 53.9 | official |

---

## Non-Thinking Mode (w/o CoT / nothink)

| Rank | Model | Params (Active) | Overall (%) | Short | Medium | Long | Source |
|------|-------|-----------------|-------------|-------|--------|------|--------|
| — | **Human baseline** | — | **53.7** | — | — | — | official |
| 1 | MiniMax-Text-01 | 456B | 52.9 | 58.9 | 52.6 | 43.5 | official |
| 2 | GPT-4o (Aug 2024) | undisclosed | 50.1 | 53.3 | 52.4 | 40.2 | official |
| 3 | Gemini-Exp-1206 | undisclosed | 49.3 | 53.9 | 47.1 | 45.8 | official |
| 4 | Gemini-2.0-Flash | undisclosed | 47.4 | 48.9 | 47.7 | 44.4 | official |
| 5 | Qwen3-235B-Instruct-2507 | 235B (22B) | 46.7 | 52.2 | 44.2 | 42.6 | official |
| 6 | GPT-4o (Nov 2024) | undisclosed | 46.0 | 47.5 | 47.9 | 39.8 | official |
| 7 | Kimi-K2-Instruct | 1T (32B) | 44.9 | 51.7 | 39.1 | 45.4 | official |
| 8 | GLM-4-Plus | undisclosed | 44.3 | 50.0 | 46.5 | 30.6 | official |
| 9 | Qwen2.5-72B | 72B | 42.1 | 45.6 | 38.1 | 44.4 | official |
| 10 | Claude 3.5 Sonnet | undisclosed | 41.0 | 46.1 | 38.6 | 37.0 | official |
| 11 | Qwen3-235B-A22B | 235B (22B) | 40.4 | 45.6 | 36.7 | 38.9 | official |
| 12 | Qwen3-32B | 32B | 38.8 | 40.6 | 38.1 | 37.0 | official |
| 13 | o1-mini | undisclosed | 37.8 | 48.6 | 33.3 | 28.6 | official |
| 14 | Mistral Large 24.11 | undisclosed | 34.4 | 41.7 | 30.7 | 29.6 | official |
| 15 | Qwen3-30B-A3B | 30B (3B) | 32.6 | 35.0 | 32.1 | 29.6 | official |
| 16 | Llama 3.1 70B | 70B | 31.6 | 41.1 | 27.4 | 24.1 | official |
| 17 | Nemotron 70B | 70B | 31.0 | 38.3 | 27.9 | 25.0 | official |
| 18 | NExtLong 8B | 8B | 30.8 | 37.8 | 27.4 | 25.9 | official |
| 19 | GLM-4-9B | 9B | 30.2 | 33.9 | 29.8 | 25.0 | official |
| 20 | Qwen2.5-7B | 7B | 30.0 | 40.6 | 24.2 | 24.1 | official |
| 20 | Llama 3.1 8B | 8B | 30.0 | 35.0 | 27.9 | 25.9 | official |
| 22 | Llama 3.3 70B | 70B | 29.8 | 36.7 | 27.0 | 24.1 | official |
| 23 | GPT-4o mini | undisclosed | 29.3 | 31.8 | 28.6 | 26.2 | official |
| 24 | Command R+ | undisclosed | 27.8 | 36.7 | 23.7 | 21.3 | official |

### Models without published nothink scores

Gemini-2.5-Pro/Flash, Gemini 3 Pro, DeepSeek-R1/R1-0528, GPT-5.x, Qwen3.5 series, GLM-5/4.7, Kimi-K2.5 — no official LongBench v2 w/o CoT scores found yet.

---

## Notes

- Official leaderboard: [longbench2.github.io](https://longbench2.github.io/)
- "official (HF)" = from Qwen HuggingFace model card comparison tables
- Third-party scores from [awesomeagents.ai](https://awesomeagents.ai/leaderboards/long-context-benchmarks-leaderboard/)
- Qwen3.5 HF scores appear to be thinking mode (Qwen3.5 thinks by default)
- Qwen3 w/ CoT: thinking mode, 16K token thinking budget; w/o CoT: non-thinking mode
- Our Qwen3.5-27B thinking result: >61% accuracy (experiment in progress)
- Our Qwen3.5-27B nothink experiment: in progress
