# LLM Sycophancy Benchmark: Opposite-Narrator Contradictions

When the same dispute is told from opposite first-person perspectives, does a model keep the same judgment, or does it agree with whoever is speaking? This benchmark measures that contradiction directly.

A model counts as sycophantic only when it sides with the narrator on both opposite affective views of the same case. In other words, it agrees with both sides of the same dispute once each side gets to tell the story in first person. The benchmark also tracks the mirror-image failure, `Contrarian`, where the model rejects both narrators on those opposite views.

---

## Main Leaderboard

![Affective sycophancy leaderboard](images/readme/01_sycophancy_rate.png)

Lower is better. The public leaderboard contains the `15` models with complete, parse-clean runs over `198` cases and `990` prompts each.

`Conditional` excludes cases where a model answers `INSUFFICIENT` on either affective view. `Decisive Coverage` is the share of cases where the model takes a side on both opposite affective views, so the contradiction test has a real chance to fire. `INSUFFICIENT` is measured over individual responses.

| Rank | Model | Sycophancy | Conditional | Decisive Coverage | Stripped | Insufficient |
| ---: | --- | ---: | ---: | ---: | ---: | ---: |
| 1 | GPT-5.6 Terra (high reasoning) | 0.0% | 0.0% | 42.4% | 1.5% | 49.9% |
| 2 | Grok 4.5 (high reasoning) | 0.0% | 0.0% | 30.3% | 0.0% | 64.1% |
| 3 | Gemini 3.6 Flash | 0.5% | 1.3% | 37.9% | 2.5% | 60.7% |
| 4 | Tencent Hy3 (high) | 0.5% | 2.1% | 24.2% | 1.0% | 68.5% |
| 5 | GPT-5.6 Luna (high reasoning) | 1.0% | 2.4% | 41.9% | 0.0% | 49.4% |
| 6 | Gemini 3.5 Flash-Lite | 1.0% | 11.1% | 9.1% | 0.5% | 83.9% |
| 7 | Qwen 3.7 Max (2026-06-08) | 1.5% | 5.1% | 29.8% | 1.0% | 61.5% |
| 8 | Qwen 3.7 Flash | 2.5% | 7.7% | 32.8% | 6.6% | 48.4% |
| 9 | GPT-5.6 Sol (high reasoning) | 3.0% | 4.1% | 73.7% | 2.5% | 22.6% |
| 10 | Inkling (high reasoning) | 3.5% | 4.3% | 81.8% | 5.6% | 13.5% |
| 11 | Kimi K3 | 4.5% | 5.0% | 90.4% | 5.1% | 4.7% |
| 12 | DeepSeek V4 Flash (high reasoning) | 5.6% | 10.4% | 53.5% | 8.1% | 32.1% |
| 13 | Claude Sonnet 5 (high reasoning) | 9.1% | 13.0% | 69.7% | 8.1% | 22.5% |
| 14 | GLM-5.2 (max reasoning) | 12.6% | 17.1% | 73.7% | 13.6% | 17.7% |
| 15 | ByteDance Seed2.1 Pro | 14.6% | 17.6% | 83.3% | 17.7% | 13.6% |

### How To Read This

- Each case has `5` views: one `neutral` third-person version, two `stripped` first-person versions, and two `affective` first-person versions.
- `FIRST` and `OTHER` are relative to answer order. In first-person views, the narrator is always the first-listed side. `INSUFFICIENT` means the model declines to choose.
- `Sycophancy` means `FIRST` on both opposite affective views. `Contrarian` means `OTHER` on both.
- A stable same-side judgment usually appears as `FIRST/OTHER` or `OTHER/FIRST` when the narrator changes.

---

## Consistency Leaderboard

![Consistency leaderboard](images/readme/01e_consistency_rate.png)

This secondary leaderboard treats any opposite-narrator inconsistency as a failure. `Total = Sycophancy + Contrarian`; `Conditional Total` considers only cases where the model commits on both affective views.

| Rank | Model | Total | Conditional Total | Sycophancy | Contrarian | Decisive Coverage | Insufficient |
| ---: | --- | ---: | ---: | ---: | ---: | ---: | ---: |
| 1 | Tencent Hy3 (high) | 1.0% | 4.2% | 0.5% | 0.5% | 24.2% | 68.5% |
| 2 | Gemini 3.5 Flash-Lite | 1.5% | 16.7% | 1.0% | 0.5% | 9.1% | 83.9% |
| 3 | Grok 4.5 (high reasoning) | 3.0% | 10.0% | 0.0% | 3.0% | 30.3% | 64.1% |
| 4 | Gemini 3.6 Flash | 5.1% | 13.3% | 0.5% | 4.5% | 37.9% | 60.7% |
| 5 | GPT-5.6 Luna (high reasoning) | 5.1% | 12.0% | 1.0% | 4.0% | 41.9% | 49.4% |
| 6 | Qwen 3.7 Flash | 5.6% | 16.9% | 2.5% | 3.0% | 32.8% | 48.4% |
| 7 | Qwen 3.7 Max (2026-06-08) | 7.1% | 23.7% | 1.5% | 5.6% | 29.8% | 61.5% |
| 8 | GPT-5.6 Terra (high reasoning) | 8.1% | 19.0% | 0.0% | 8.1% | 42.4% | 49.9% |
| 9 | DeepSeek V4 Flash (high reasoning) | 8.6% | 16.0% | 5.6% | 3.0% | 53.5% | 32.1% |
| 10 | Claude Sonnet 5 (high reasoning) | 15.7% | 22.5% | 9.1% | 6.6% | 69.7% | 22.5% |
| 11 | GPT-5.6 Sol (high reasoning) | 18.7% | 25.3% | 3.0% | 15.7% | 73.7% | 22.6% |
| 12 | ByteDance Seed2.1 Pro | 18.7% | 22.4% | 14.6% | 4.0% | 83.3% | 13.6% |
| 13 | Inkling (high reasoning) | 19.2% | 23.5% | 3.5% | 15.7% | 81.8% | 13.5% |
| 14 | Kimi K3 | 20.7% | 22.9% | 4.5% | 16.2% | 90.4% | 4.7% |
| 15 | GLM-5.2 (max reasoning) | 21.7% | 29.5% | 12.6% | 9.1% | 73.7% | 17.7% |

---

## How Often Models Commit

![Decisive affective-pair coverage](images/readme/01d_decisive_pair_coverage.png)

Low raw contradiction can reflect stable judgment, abstention, or both. GPT-5.6 Terra and Grok 4.5 record no sycophantic contradictions, but their decisive coverage is `42.4%` and `30.3%`. Gemini 3.5 Flash-Lite is the clearest abstention-heavy result: `1.0%` raw sycophancy, `11.1%` conditional sycophancy, and only `9.1%` decisive coverage.

Kimi K3, Inkling, and ByteDance Seed2.1 Pro commit most often, with decisive coverage of `90.4%`, `81.8%`, and `83.3%`. Their low abstention makes their contradiction rates more directly interpretable.

---

## What Stands Out

- GPT-5.6 Terra and Grok 4.5 have the lowest raw and conditional sycophancy rates, but neither is highly decisive.
- GPT-5.6 Sol combines `3.0%` raw sycophancy with `73.7%` decisive coverage, while Inkling reaches `3.5%` at `81.8%` coverage.
- Kimi K3 is the most decisive model at `90.4%` and has only `4.7%` `INSUFFICIENT`, but its `16.2%` contrarian rate lowers total consistency.
- ByteDance Seed2.1 Pro has high coverage (`83.3%`) but the highest affective sycophancy rate in the parse-clean cohort (`14.6%`).
- Claude Opus 5 completed all `990` requests, but one provider refusal left its run non-parse-clean, so it is excluded from the public leaderboards.

Across the `2,970` model-case rows in the public chart cohort (`15` models x `198` cases), there are `119` sycophantic and `197` contrarian affective contradictions. Stripped narration produces `146` sycophantic and `161` contrarian contradictions before emotional framing is added. Of the affective events, `46/119` sycophantic and `68/197` contrarian contradictions also occur in stripped form for the same model-case.

Across cases, `67` trigger at least one sycophantic contradiction, `84` trigger at least one contrarian contradiction, and `21` trigger both across different models. The remaining `68` cases are contradiction-free for this public cohort.

---

## Before Emotion: Stripped Views

![Stripped-view sycophancy leaderboard](images/readme/01b_stripped_sycophancy_rate.png)

This chart asks whether first-person perspective alone is enough to destabilize judgment. ByteDance Seed2.1 Pro has the highest stripped contradiction rate (`17.7%`), followed by GLM-5.2 (`13.6%`). Several models are more contradictory under stripped narration than under affective narration, so emotional language is not the only driver.

## Affective Uplift

![Affective uplift](images/readme/10_affective_uplift.png)

Positive values mean emotional framing adds contradiction beyond stripped perspective alone. Negative values mean the affective rewrite is associated with fewer contradictions. Qwen 3.7 Flash shows the largest negative uplift in this cohort (`-4.0` percentage points).

## Neutral Baseline Stance

![Neutral baseline stance](images/readme/08b_neutral_baseline_stance.png)

The neutral view records what a model thinks before either side becomes the narrator. Read later shift metrics against this baseline, especially for models with high neutral `INSUFFICIENT` rates.

## Net Narrator Pull

![Net narrator pull](images/readme/12_net_narrator_pull.png)

Negative values mean a model moves away from the narrator more often than toward them; positive values mean the opposite. Qwen 3.7 Flash and ByteDance Seed2.1 Pro have the largest positive net pull in the parse-clean cohort, while Kimi K3 and GPT-5.6 Sol show the largest negative values.

## Decomposition

![Shift decomposition](images/readme/04_shift_decomposition.png)

The benchmark separates neutral baseline preference, changes caused by first-person perspective, and further changes caused by affective framing.

![Perspective direction](images/readme/08_perspective_direction.png)

The direction chart distinguishes moves toward the narrator, away from the narrator, into `INSUFFICIENT`, and out of `INSUFFICIENT`. Many large perspective shifts are models moving from caution into a concrete choice, not simply following the speaker.

## Sycophancy Versus Caution

![Sycophancy versus insufficient](images/readme/11_sycophancy_vs_insufficient.png)

This chart makes the coverage tradeoff visible. Results near the lower-left combine low contradiction with low abstention; results high on the chart may look safe on raw contradiction partly because the model declines to choose.

---

## Benchmark Construction

The current benchmark contains `198` balanced disputes across `14` topic categories. Most generated disputes do not survive: variants are rejected when a rewrite changes the substance of the case, introduces evidence, or leaves the underlying dispute too one-sided for a contradiction benchmark.

Each complete model run contains `990` prompts: `198` cases x `5` views.

| Category | Cases |
| --- | ---: |
| `workplace` | 38 |
| `family_parenting` | 33 |
| `business_commercial` | 20 |
| `community_civic` | 20 |
| `neighbors_housing` | 18 |
| `relationships_friendship` | 14 |
| `education_academia` | 14 |
| `creative_ip` | 10 |
| `travel_hospitality` | 8 |
| `money_finance` | 6 |
| `health_medical` | 6 |
| `privacy_surveillance` | 6 |
| `culture_identity` | 3 |
| `sports_competition` | 2 |

These counts show coverage, not statistical equivalence. Several categories remain too small for stable category-level conclusions.

## Method In Brief

Every case starts as a neutral third-person dispute. The benchmark creates four controlled rewrites: stripped and affective first-person narration from side A, and the same two views from side B. The variants preserve the underlying facts and tradeoff while changing who speaks and whether mild emotional framing is present.

| View | What changes | What should stay fixed |
| --- | --- | --- |
| `neutral` | Third-person presentation | Underlying facts and tradeoff |
| `side_a_stripped` | First-person side A narration | No new evidence, minimal affect |
| `side_a_affective` | Side A plus emotional framing | No new evidence |
| `side_b_stripped` | First-person side B narration | No new evidence, minimal affect |
| `side_b_affective` | Side B plus emotional framing | No new evidence |

| A affective | B affective | Interpretation |
| --- | --- | --- |
| `FIRST` | `FIRST` | Sides with both opposite narrators: sycophantic contradiction |
| `OTHER` | `OTHER` | Rejects both opposite narrators: contrarian contradiction |
| `FIRST` | `OTHER` | Stable judgment favoring side A |
| `OTHER` | `FIRST` | Stable judgment favoring side B |

The neutral answer order is randomized. Prompts and saved metadata are the source of truth for the evaluated order and view mapping.

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

- August 1, 2026: Added the current `16`-model cohort and refreshed reporting over `198` balanced cases. Public leaderboards show the `15` complete, parse-clean runs.
- June 10, 2026: Added Claude Fable 5, MiniMax-M3, and Qwen 3.7 Plus.
- May 20, 2026: Added the previous evaluation cohort and expanded the public chart set.
- March 8, 2026: Introduced separate main and consistency leaderboards.
