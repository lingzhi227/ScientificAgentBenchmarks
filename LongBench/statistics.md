# LongBench v2 Statistics — Qwen3.5-27B

Progress: **273 / 503** (54.3% complete) | Accuracy: **63.4%** (173/273)

## Input Tokens by Length

| Length | Count | Min | Avg | Median | Max |
|--------|-------|---------|---------|---------|---------|
| short | 173 | 10,314 | 31,616 | 27,470 | 100,097 |
| medium | 92 | 41,997 | 113,088 | 106,251 | 218,436 |
| long | 8 | 193,810 | 212,804 | 215,933 | 220,617 |

## Completion Tokens (Thinking + Answer) by Length

| Length | Min | Avg | Median | Max |
|--------|-----|-------|--------|---------|
| short | 657 | 4,895 | 4,420 | 15,373 |
| medium | 551 | 8,937 | 4,462 | 158,999 |
| long | 1,294 | 9,346 | 4,870 | 45,699 |

## Latency (seconds) by Length

| Length | Min | Avg | Median | Max |
|--------|-------|---------|---------|----------|
| short | 111.7 | 770.7 | 622.9 | 4,083.6 |
| medium | 175.6 | 2,192.1 | 1,119.6 | 12,527.5 |
| long | 523.2 | 4,430.2 | 5,157.2 | 9,442.0 |

## Accuracy by Difficulty

| Difficulty | Correct | Total | Accuracy |
|------------|---------|-------|----------|
| easy | 68 | 93 | 73.1% |
| hard | 105 | 180 | 58.3% |

## Accuracy by Length

| Length | Correct | Total | Accuracy |
|--------|---------|-------|----------|
| short | 112 | 173 | 64.7% |
| medium | 59 | 92 | 64.1% |
| long | 2 | 8 | 25.0% |

## KV Cache Impact

- Medium question avg input (113K) + 16K think reserve = **129K** → 52% of per-GPU KV capacity (249K)
- Max 1 medium + 1 short per GPU concurrently; 2 medium cannot fit
- Long questions (213K avg) occupy **92%** of KV capacity → exclusive GPU access

## Infrastructure

- 8x A100 80GB GPUs across 2 nodes (nid200352 + nid200332)
- 8 independent vLLM servers (1 GPU each, 262K max context)
- KV capacity per GPU: ~249K tokens (95% of 262K)
