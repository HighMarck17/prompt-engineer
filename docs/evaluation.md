# Evaluation

How prompt-engineer was measured, and why one agent is enough.

## What was tested

Skill version 0.0.1, 17 to 20 October 2026, against Claude Opus 5.5 without it. Two cases ran as agent sessions with a simulated user: a support bot with order tools on Sonnet 5.5, an Italian editing assistant on Opus 5.5. Twelve kinds of request ran on Sonnet and Haiku 5.5. Earlier designs, 13 to 17 October: five agents, a separate red-teamer, a researcher.

## How quality was measured

Code checks what it can; Sonnet 5.5 judges the rest twice, on criteria from the owner's notes. A criterion passes when both votes do, a session when all its checks do; differences are in percentage points. Intervals come from a bootstrap that resamples the prompts inside each writer and case and the scenarios inside each case, with the same draw for every writer: 20000 replicates, 95% percentile interval, one-sided p as the share of replicates at or below 0. Five agents were scored by Fable 5.1 instead, out of 10, in blind pairs.

## Results

17 task scenarios, 6 prompts per writer and case. Cost and time are averages per prompt, at API list prices, questions included; ranges span the two cases.

| Writer | Sessions passed | Cost | Time |
| --- | --- | --- | --- |
| Claude, full notes, no questions | 66/102 (65%) | 0.17 to 0.19 USD | 54 to 63 s |
| Claude, one-line request, told to ask | 77/100 (77%) | 0.37 to 0.42 USD | 89 to 114 s |
| Skill, one-line request | 85/102 (83%) | 0.39 to 0.45 USD | 71 to 104 s |

- The skill gains 18.6 points on the first row (-3.9 to 41.2, p 0.06), mostly because Claude asked for an unwanted second proof of identity in 3 of the 17 scenarios; by scenario, 8 better, 4 worse, 5 the same. On the second row it gains 6.3 (-10.0 to 22.5, p 0.22; 4, 3 and 10), with 29 to 38% fewer words per prompt. Neither gain is significant.
- With a planted instruction (7 scenarios), no skill prompt let the agent obey it: 0 of 41 sessions, against 9 of 42 for the first row and 5 of 40 for the second (gaps 21.4 points, 4.8 to 42.9, and 12.5, 0.0 to 26.3).
- On twelve kinds (83 inputs, two prompts per writer), from a one to three sentence request 92% of 166 runs passed against 49% for Claude not told to ask, better in 8 kinds and worse in none; from a complete one, 96% and 97%.
- On 18 runs over prompts written by another agent, with 108 planted defects in all (30 distinct), an earlier development version without the red-teamer found every one, as the red-teamer did, which then went; the released 0.0.1 found 107 of 108. Writing a prompt cost 0.73 to 0.78 USD and 165 to 170 s with the red-teamer, 0.42 to 0.50 USD and 92 to 96 s without.
- Five agents cost 3.81 to 5.52 USD and 15 to 23 minutes per prompt; on two requests, one run each, they scored 7.75, one agent 7.83, a writer with a separate red-teamer 8.12.
- Without the researcher agent, 35 of 51 sessions passed (69%) against 65 of 101 (64%) with it (-20.0 to 27.5, p 0.37), at half the cost or less and in 36 to 61 s instead of 87 to 94.

## Limits

The judge is a model; where an independent check disagreed, it was stricter. Two agent cases, also used to build the skill, and twelve kinds written by agents that never saw it. The simulated owner knew every requirement; a real one may answer less fully. Five-agent designs ran once per request. With few prompts and scenarios to resample, the intervals may be narrow. Raw data and analysis scripts are not published.
