# LLM Sycophancy Benchmark: Opposite-Narrator Contradictions

When the same dispute is told from opposite first-person perspectives, does a model keep the same judgment, or does it agree with whoever is speaking? This benchmark measures that contradiction directly.

The headline metric is intentionally strict. A model counts as sycophantic only when it sides with the narrator on both opposite affective views of the same case. In other words, it agrees with both sides of the same dispute once each side gets to tell the story in first person.

---

## Main Leaderboard

![Affective sycophancy leaderboard](images/readme/01_sycophancy_rate.png)

This is the headline ranking. Lower is better. A model is counted here only when it sides with both opposing first-person narrators on the same affective pair.

`Conditional` excludes cases with `INSUFFICIENT` on either opposite affective view. `Decisive Coverage` is the share of cases where the model took a side on both opposite affective views, so the contradiction test had a chance to fire.

| Rank | Model | Sycophancy | Conditional | Decisive Coverage | Stripped | Insufficient |
| ---: | --- | ---: | ---: | ---: | ---: | ---: |
| 1 | Gemini 3.1 Pro Preview | 0.5% | 0.7% | 75.9% | 0.0% | 28.2% |
| 2 | Grok 4.20 Reasoning Exp Beta 0304 | 1.0% | 3.6% | 28.1% | 2.0% | 60.9% |
| 3 | GPT-5.4 (medium reasoning) | 2.0% | 2.7% | 73.4% | 4.0% | 15.1% |
| 4 | Qwen3.5-397B-A17B | 2.0% | 3.4% | 58.3% | 4.0% | 29.9% |
| 5 | Claude Opus 4.6 (no reasoning) | 2.5% | 4.2% | 59.3% | 6.0% | 27.7% |
| 6 | Gemini 3.1 Flash-Lite Preview | 3.0% | 6.3% | 47.7% | 0.5% | 43.5% |
| 7 | GPT-5.4 (no reasoning) | 3.5% | 8.2% | 42.7% | 3.5% | 40.1% |
| 8 | DeepSeek V3.2 Exp | 6.0% | 11.3% | 53.3% | 4.0% | 36.8% |
| 9 | Kimi K2.5 | 6.6% | 12.3% | 53.3% | 3.0% | 33.4% |
| 10 | Claude Sonnet 4.6 Adaptive | 7.0% | 9.7% | 72.9% | 7.5% | 17.6% |
| 11 | Ernie 5 | 8.0% | 16.7% | 48.2% | 8.0% | 37.2% |
| 12 | MiniMax-M2.5 | 9.1% | 11.8% | 76.9% | 6.0% | 14.7% |
| 13 | GLM-5 | 12.1% | 13.0% | 93.0% | 10.1% | 3.9% |
| 14 | ByteDance Seed2.0 Pro | 14.1% | 25.5% | 55.3% | 17.1% | 31.1% |
| 15 | GPT-4.1 | 19.1% | 34.5% | 55.3% | 18.1% | 31.2% |
| 16 | Mistral Large 2512 | 31.2% | 52.5% | 59.3% | 31.2% | 26.1% |

---

## Consistency Leaderboard

This secondary leaderboard treats opposite-narrator inconsistency as the main failure, regardless of direction. It sorts by `Total = Sycophancy + Contrarian`, where `Contrarian` means the model rejects whichever narrator is speaking on both opposite affective views.

`Conditional Total` excludes cases with `INSUFFICIENT` on either opposite affective view, so it shows how often the model is inconsistent once it actually commits on both sides. `Decisive Coverage` and `INSUFFICIENT` therefore matter even more here than on the main leaderboard, because a low raw total can be driven by abstention rather than by stable cross-view judgment. Grok lands `#1` on this table at `1.5%`, but that rises to `5.4%` on a conditional basis and it is only decisive on `28.1%` of opposite affective pairs, so that rank should be read as low observed inconsistency under heavy abstention, not as clean best-in-class consistency.

| Rank | Model | Total | Conditional Total | Sycophancy | Contrarian | Decisive Coverage | Insufficient |
| ---: | --- | ---: | ---: | ---: | ---: | ---: | ---: |
| 1 | Grok 4.20 Reasoning Exp Beta 0304 | 1.5% | 5.4% | 1.0% | 0.5% | 28.1% | 60.9% |
| 2 | DeepSeek V3.2 Exp | 9.0% | 17.0% | 6.0% | 3.0% | 53.3% | 36.8% |
| 3 | Ernie 5 | 9.5% | 19.8% | 8.0% | 1.5% | 48.2% | 37.2% |
| 4 | Gemini 3.1 Flash-Lite Preview | 10.6% | 22.1% | 3.0% | 7.5% | 47.7% | 43.5% |
| 5 | Qwen3.5-397B-A17B | 10.6% | 18.1% | 2.0% | 8.5% | 58.3% | 29.9% |
| 6 | GPT-5.4 (no reasoning) | 10.6% | 24.7% | 3.5% | 7.0% | 42.7% | 40.1% |
| 7 | Claude Opus 4.6 (no reasoning) | 13.6% | 22.9% | 2.5% | 11.1% | 59.3% | 27.7% |
| 8 | GPT-5.4 (medium reasoning) | 14.1% | 19.2% | 2.0% | 12.1% | 73.4% | 15.1% |
| 9 | Kimi K2.5 | 14.1% | 26.5% | 6.6% | 7.6% | 53.3% | 33.4% |
| 10 | Claude Sonnet 4.6 Adaptive | 15.6% | 21.4% | 7.0% | 8.5% | 72.9% | 17.6% |
| 11 | ByteDance Seed2.0 Pro | 15.6% | 28.2% | 14.1% | 1.5% | 55.3% | 31.1% |
| 12 | GPT-4.1 | 19.6% | 35.5% | 19.1% | 0.5% | 55.3% | 31.2% |
| 13 | Gemini 3.1 Pro Preview | 21.6% | 28.5% | 0.5% | 21.1% | 75.9% | 28.2% |
| 14 | GLM-5 | 21.6% | 23.2% | 12.1% | 9.5% | 93.0% | 3.9% |
| 15 | MiniMax-M2.5 | 23.2% | 30.2% | 9.1% | 14.1% | 76.9% | 14.7% |
| 16 | Mistral Large 2512 | 33.2% | 55.9% | 31.2% | 2.0% | 59.3% | 26.1% |

---

## What Changes Between The Two Leaderboards

The biggest rank shifts are not small. Models that look strong on narrator-following can fall hard once contrarian contradiction is counted too, while some weaker headline models rise because they stay directionally more consistent.

| Model | Main Rank | Consistency Rank | Delta |
| --- | ---: | ---: | ---: |
| Gemini 3.1 Pro Preview | 1 | 13 | Down 12 |
| Ernie 5 | 11 | 3 | Up 8 |
| DeepSeek V3.2 Exp | 8 | 2 | Up 6 |
| GPT-5.4 (medium reasoning) | 3 | 8 | Down 5 |

---

## What Stands Out

- Gemini 3.1 Pro Preview is the most interesting secondary finding, not just the headline winner. It has the largest neutral-to-stripped shift in the full-run set at `64.6%`, but that is driven mainly by movement out of `INSUFFICIENT` (`53.0%`) rather than narrator-following (`4.5%` toward narrator, `6.3%` away). First-person framing makes it much more willing to take a side without making it strongly speaker-following.
- GPT-5.4 medium reasoning versus no reasoning is one of the cleanest within-family tradeoffs in the run. Reasoning improves the headline metric (`3.5%` -> `2.0%`) and sharply reduces `INSUFFICIENT` (`40.1%` -> `15.1%`), but contrarian contradiction rises (`7.0%` -> `12.1%`), so it looks better on narrator-following and worse on total consistency.
- Gemini 3.1 Pro Preview also looks very different on the consistency leaderboard than on the main one: it is `#1` on sycophancy contradiction at `0.5%`, but only `#13` on total contradiction because contrarian contradiction is a much larger `21.1%`.
- Grok 4.20 Reasoning looks excellent on the headline metric at `1.0%`, but it is also the indecision outlier at `60.9%` `INSUFFICIENT` and only `28.1%` decisive-pair coverage.
- Kimi K2.5 shows the strongest reverse-indecision pattern in the run. First-person framing moves `19.8%` of cases into `INSUFFICIENT` from a concrete neutral stance, the highest rate in the set; Ernie 5 (`14.1%`) and DeepSeek V3.2 Exp (`13.1%`) show the same pattern at smaller scale.
- GLM-5 lands in an unusual spot: very high decisiveness (`93.0%` decisive-pair coverage, only `3.9%` `INSUFFICIENT`) but still a relatively high contradiction rate at `12.1%`. It looks confident rather than robust.
- Claude Opus 4.6 no reasoning clearly beats Claude Sonnet 4.6 Adaptive on the main metric (`2.5%` vs `7.0%`) while also improving on stripped-view contradiction.
- Claude Sonnet 4.6 Adaptive is also the only model with any refusal behavior in the current run: `24` refusals out of `995` prompts (`2.4%`). Every other full-coverage model is at zero.
- GPT-4.1 underperforms badly against GPT-5.4 medium on this benchmark (`19.1%` vs `2.0%`) and also trails Claude Opus by a wide margin.
- Mistral Large 2512 is the clearest failure case in the current set. It is already at `31.2%` contradiction on stripped views, which means plain first-person perspective alone is enough to break consistency.

---

## Benchmark Construction

The benchmark got to `199` cases through a strict funnel. Most generated disputes do not survive as-is.

| Stage | Cases |
| --- | ---: |
| Generated canonical disputes | 448 |
| Original cases that passed verification | 220 |
| Original cases that passed balance filtering | 119 |
| Added after follow-up refinement passes | 80 |
| Final benchmark | 199 |

The practical story is simple: the main losses happen for two different reasons. Verification rejects rewrites that smuggle in new framing or argument. Balance filtering removes disputes that are still too obviously one-sided even when they are factually clean. The final benchmark therefore combines first-pass survivors with an additional set recovered through follow-up refinement.

Current snapshot:

- `448` generated starting disputes
- `199` final benchmark cases after verification, balance filtering, and recovery passes
- `16` topic categories
- `16` evaluated models
- `16` full-coverage runs
- `995` prompts per full model (`199` cases x `5` views)

---

## Before Emotion: Stripped-View Contradiction

![Stripped-view sycophancy leaderboard](images/readme/01b_stripped_sycophancy_rate.png)

This chart shows whether the problem appears before emotional framing enters. Some models are already willing to contradict themselves under plain first-person perspective alone. For a few models, affective framing is actually stabilizing rather than destabilizing: Claude Opus 4.6 drops from `6.0%` stripped contradiction to `2.5%` affective, and Seed 2.0 Pro drops from `17.1%` to `14.1%`.

---

## Neutral Baseline Stance

![Neutral baseline stance](images/readme/08b_neutral_baseline_stance.png)

This is the grounding view: what models think about each dispute before any first-person narration. The later shift charts make more sense when read against this baseline, especially for models that start from a very high neutral `INSUFFICIENT` rate.

---

## Net Narrator Pull

![Net narrator pull](images/readme/12_net_narrator_pull.png)

This is the most intuitive speaker-following chart in the report. Negative values mean the model moves away from the narrator more often than toward them; positive values mean the opposite.

---

## Decomposition Story

![Shift decomposition](images/readme/04_shift_decomposition.png)

The benchmark separates three effects that are usually blurred together: neutral baseline preference, answer changes caused by first-person perspective, and further movement caused by affective framing.

![Perspective direction](images/readme/08_perspective_direction.png)

The direction chart shows what kind of movement is happening. Some models mainly move from `INSUFFICIENT` into a concrete side choice. Others show a much cleaner toward-narrator pull. Gemini 3.1 Pro Preview is the clearest example of the first pattern: its huge `64.6%` perspective shift is mostly a `53.0%` move out of `INSUFFICIENT`, not a narrator-following effect.

---

## Sycophancy Versus Caution

![Sycophancy versus insufficient](images/readme/11_sycophancy_vs_insufficient.png)

Low contradiction is not the whole story. Some models avoid contradictions partly by abstaining, which is why `Conditional`, `Decisive Coverage`, and `INSUFFICIENT` belong next to the headline ranking. Decisive-pair coverage also falls into visible bands: a high-coverage group above `70%` (GLM-5, MiniMax-M2.5, Gemini 3.1 Pro Preview, GPT-5.4 medium, Claude Sonnet 4.6 Adaptive), a middle cluster around `50-60%`, and a low-coverage tail below `50%` led by Grok at `28.1%`.

---

## Overall Benchmark Score

![Overall benchmark score](images/readme/09_overall_benchmark_score.png)

If you want one heuristic summary after the two main leaderboards, use this chart. It is still secondary, and it should not override either the headline sycophancy ranking or the consistency ranking. The score combines affective contradiction, stripped-view contradiction, positive narrator pull, and an insufficient-rate penalty into one summary number.

---

## Method In Brief

Every case starts as a neutral third-person dispute. The pipeline then creates four controlled rewrites: stripped first-person narration from side A, affective first-person narration from side A, and the same two views from side B. Those variants go through linting, dual verification, and balance filtering before any benchmark run.

| View | What changes | What should stay fixed |
| --- | --- | --- |
| `neutral` | Third-person presentation | Underlying facts and tradeoff |
| `side_a_stripped` | First-person side A narration | No new evidence, minimal affect |
| `side_a_affective` | First-person side A with emotional framing | No new evidence |
| `side_b_stripped` | First-person side B narration | No new evidence, minimal affect |
| `side_b_affective` | First-person side B with emotional framing | No new evidence |

Mini example on one dispute:

| `side_a_affective` | `side_b_affective` | What it means |
| --- | --- | --- |
| `FIRST` | `FIRST` | The model sides with both opposite narrators -> sycophantic contradiction |
| `OTHER` | `OTHER` | The model rejects both opposite narrators -> contrarian contradiction |

1. Generate neutral third-person disputes.
2. Rewrite each case into four paired first-person variants.
3. Lint, verify, and balance-filter those variants so first-person framing does not smuggle in new facts.
4. Randomize answer order, run all five views for each case, then aggregate contradiction, shift, indecision, and position-bias metrics.

The design is conservative on purpose. It is trying to count only answer changes that can plausibly be blamed on perspective or framing, not on hidden factual drift between prompt versions.

---

## Category Heatmap

![Model by category heatmap](images/readme/13_model_category_heatmap.png)

Category effects are secondary, but the heatmap is the fastest way to see whether a model is broadly unstable or only weak in a few topic types. It also helps distinguish real weaknesses from small-sample artifacts, because some categories are still much larger than others.

---

## Related Benchmarks

### Other multi-agent benchmarks

- [PACT: Benchmarking LLM negotiation skill in multi-round buyer-seller bargaining](https://github.com/lechmazur/pact/)
- [Public Goods Game (PGG) Benchmark: Contribute and Punish](https://github.com/lechmazur/pgg_bench/)
- [Elimination Game: Social Reasoning and Deception in Multi-Agent LLMs](https://github.com/lechmazur/elimination_game/)
- [Step Race: Collaboration vs. Misdirection Under Pressure](https://github.com/lechmazur/step_game/)

### Other benchmarks

- [Extended NYT Connections](https://github.com/lechmazur/nyt-connections/)
- [LLM Confabulation / Hallucination Benchmark](https://github.com/lechmazur/confabulations/)
- [LLM Thematic Generalization Benchmark](https://github.com/lechmazur/generalization/)
- [LLM Creative Story-Writing Benchmark](https://github.com/lechmazur/writing/)
- [LLM Deceptiveness and Gullibility](https://github.com/lechmazur/deception/)
- [LLM Divergent Thinking Creativity Benchmark](https://github.com/lechmazur/divergent/)
- [LLM Round-Trip Translation Benchmark](https://github.com/lechmazur/translation/)

## Updates

- March 8, 2026: README updated to the current `199`-case snapshot, including the recovered-case funnel, separate main and consistency leaderboards, and the latest full-run chart set.
