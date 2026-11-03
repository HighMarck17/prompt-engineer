# Evaluation

How prompt-engineer was measured, and why one agent is enough.

## What was tested

Skill version 0.0.1, 17 to 20 October 2026, against Claude Opus 5.5 without it. Two cases ran as agent sessions with a simulated user: a support bot with order tools on Sonnet 5.5, an Italian editing assistant on Opus 5.5. Twelve kinds of request ran on Sonnet and Haiku 5.5. Earlier designs, 13 to 17 October: five agents, a separate red-teamer, a researcher.

## How quality was measured

Code checks what it can; Sonnet 5.5 judges the rest twice, on criteria from the owner's notes. A criterion passes when both votes do, a session when all its checks do; differences are in percentage points. Five agents were scored by Fable 5.1 instead, out of 10, in blind pairs.

## Results

17 task scenarios, 6 prompts per writer and case. Per prompt, at API list prices, questions included; ranges span the two cases.

| Writer | Sessions passed | Cost | Time |
| --- | --- | --- | --- |
| Claude, full notes, no questions | 66/102 (65%) | 0.17 to 0.19 USD | 54 to 63 s |
| Claude, one-line request, told to ask | 77/100 (77%) | 0.37 to 0.42 USD | 89 to 114 s |
| Skill, one-line request | 85/102 (83%) | 0.39 to 0.45 USD | 71 to 104 s |

- The skill gains 18.6 points on the first row (95% interval 6.9 to 30.4), mostly because Claude asked customers for an unwanted second proof of identity, and 6.3 on the second, not significant.
- No skill prompt let the agent obey a planted instruction; Claude's did in 9 of 48 and 5 of 46 sessions.
- On twelve kinds, from a one to three sentence request, 92% of inputs passed against 49% for Claude not told to ask; from a complete one, 96% and 97%.
- Self-attack found all 108 planted defects, as a separate red-teamer agent did, which then went.
- Five agents cost 3.81 to 5.52 USD and 15 to 23 minutes per prompt, and scored 7.75; one agent scored 7.83, a writer with a separate red-teamer 8.12.
- Without the researcher agent, 69% of sessions passed against 64% with it, at half the cost or less.

## Limits

The judge is a model; where an independent check disagreed, it was stricter. Two agent cases, also used to build the skill, and twelve kinds written by agents that never saw it. The simulated owner knew every requirement; a real one may answer less fully. Five-agent designs ran once per request.
