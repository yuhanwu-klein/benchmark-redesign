# benchmark-redesign

A skill for Claude Code. It redesigns part of a software product by first studying how well-made software solves the same job. It distills what those products share into a standard, writes the standard into the PRD, and only then rebuilds and verifies.

I built it from my own design process. While redesigning **PoPo**, a companion app for a concept Polaroid camera, I kept running the same loop:

- reworking the inspiration feature into a curated community;
- setting a photo standard from Polaroid's own site;
- making a launch reel modeled on twelve big-company launch films;
- bringing the case study in line with the final design.

This skill packages that loop so an agent can run it on any product.

## What it does

1. **Reads the request before searching.** It works out the target, the user's reference brief ("at least 10 cases", "big companies only", "free mockups only"), the product's brand, and the rules the user set earlier.
2. **Sizes the work.**
   - A small request gets an answer with inline sources.
   - A medium one (the default) gets one report plus the changed file.
   - Only a large one gets per-track research notes.
3. **Chooses references that can teach something.** It draws on the brand's own official material, direct competitors, adjacent leaders and platform guidelines (Apple HIG, Material 3). Lookalikes and AI-generated examples are left out.
4. **Researches with sources.** Every finding is tagged as read directly, from a search summary, or unverified, and facts are kept apart from inference.
5. **Distills.** It writes up the shared patterns, then an adopt / adapt / reject table with reasons. For quality judgments such as "these photos look too AI", it writes a numbered standard and audits the current assets against it.
6. **Writes it into the spec, then builds.** It updates the PRD, prefers real and licensed content, and adds no decoration that carries no information.
7. **Verifies like a reviewer.** It checks desktop and phone widths, sweeps for contradictions and cuts unsupported claims. It asks before publishing, and it never overwrites what the user changed by hand.

`references/playbooks.md` covers four variants:

- feature or flow redesign;
- content or asset standard;
- launch or showcase reel;
- case study or portfolio page.

`references/templates.md` has the document shapes.

## Install

Claude Code (personal skills):

```bash
git clone https://github.com/yuhanwu-klein/benchmark-redesign ~/.claude/skills/benchmark-redesign
```

For claude.ai, download `benchmark-redesign.skill` from the [latest release](https://github.com/yuhanwu-klein/benchmark-redesign/releases) and upload it in your Skills settings.

The skill triggers on requests like "look at how other apps do budgets, find at least 6 cases and update the PRD", "set a photo standard from the brand's official site", or 参考 / 借鉴 / 对标 别的软件.

## Evaluation

The `evals/` folder holds three test tasks written for this skill. None of them is the product it came from:

| Task | What it tests |
| --- | --- |
| `budget-feature-benchmark` | Research at least 6 budgeting and banking apps, then rewrite a PRD section within the PRD's own design rules |
| `case-study-contradictions` | Fix 7 planted contradictions in a case study and replace an unrelated "decision tree" |
| `photo-standard-official-site` | Write a sample-photo standard from Lomography's site, audit 12 photos, plan licensed replacements |

How the runs were set up:

- Each task ran once with the skill and once without it, on the same model (Claude Opus).
- Each run was graded against 8 written checks per task.
- Round 2 used the revised skill.

| | Round 1 with skill | Round 2 with skill | Without skill (round 2) |
| --- | --- | --- | --- |
| Checks passed | 24 / 24 | 24 / 24 | 23 / 24 |
| New files written (per task) | 4 / 6 / 6 | 1 / 2 / 1 | 1 / 1 / 3 |
| Mean run time | 766 s | 562 s | 426 s |
| Mean tokens | 168k | 151k | 124k |

What the numbers show:

- **The one check that separates the two.** In both rounds, only the runs with the skill wrote a quality standard whose rules each cite a source.
- **The rest is a tie.** The model without the skill researched well and fixed every planted contradiction. The checks don't capture the rest of the difference: the skill's runs separate facts from inference, keep an explicit adopt / adapt / reject record, and add acceptance criteria with "ships only if" gates.
- **What revision 2 changed.** It cut the skill's run time by 27% and its written output by about a third, and still passed every check.

These are small samples: three tasks, one run each, graded by the same model family. Treat the results as direction, not proof.

To rerun the tests with Claude Code (these are real, billed model runs):

```bash
cd ~/.claude/skills/benchmark-redesign
claude plugin eval . --allow-tools Write,Edit,Bash,WebSearch,WebFetch --scaffold
```

## 中文简介

这是一个 Claude Code skill，用来按"先看做得好的软件怎么做，再改自己的产品"的思路修改软件。流程是：
1. 确认要改什么、参考要求和品牌；
2. 挑选值得学的参考对象；
3. 带出处调研，事实和推断分开写；
4. 归纳共通做法，列出"采用 / 改造 / 不采用"；如果是"太 AI"这类主观问题，就先定一套可检查的标准；
5. 先写进 PRD，再动手改；
6. 像评审一样验收。

它来自我做 PoPo（一个概念 Polaroid 相机的配套 app）时反复用的方法。

## License

MIT
