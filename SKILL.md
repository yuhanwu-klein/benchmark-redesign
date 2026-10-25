---
name: benchmark-redesign
description: Revise or redesign part of a software product (a feature, flow, screen, visual system, asset set, demo or launch video, or a portfolio case study) by first studying how well-made software solves the same job. That means big-company apps, direct competitors, platform guidelines and the brand's own official site. Distill what they share into a standard, write it into the PRD, then rebuild and verify. Use this whenever the user asks to 参考 / 借鉴 / 对标 other software or do 竞品调研 before changing something, says "look at how X does it", asks for N excellent cases or competitors and wants the common patterns applied, wants a standard taken from an official site, wants a feature reworked "like other products do", wants a showcase reel modeled on launch videos, or wants a case study brought in line with the latest design. It applies even when they never say "benchmark" or "redesign".
---

# Benchmark-driven redesign

Change a product by learning from software that already does the same job well, then rebuild it on that evidence. The goal is not to copy a look. It is to find out what the strongest products agree on, decide what this product should adopt, adapt or reject, write that decision down, and only then change the build.

This loop came out of a long redesign of a camera companion app. It ran the same way each time, whether the target was a community feature, a photo standard, a launch reel or a case study page. The playbooks in `references/playbooks.md` cover those four variants. The templates in `references/templates.md` give the shape of every document the loop produces.

## Before searching anything

Read the request for four things.

1. **The target and the deliverable.** Name the part that changes: a feature, a flow, a screen, the visual system, an asset set, a video or a case study. Name what you will hand back: code, a live site page, a PRD section, an MP4 or a report. If either is truly ambiguous, ask one question with options. Otherwise pick the obvious reading and say which one you picked.
2. **The reference brief.** Users often give hard constraints in passing:
   - a count ("at least 10 cases");
   - a source type ("must be big companies", "look at the official site");
   - a cost limit ("mockups must be free");
   - an exclusion ("no extra text").
   Repeat these in your plan and meet them. If you can't meet one, say so plainly. Don't quietly lower the bar.
3. **The product's truth.** State the one job the product does, the brand it belongs to, and what must stay true. Get the brand exactly right. A Polaroid product is not a Fujifilm product, even though both make instant cameras. Material from the neighboring brand can only ever serve as contrast.
4. **Standing rules.** Read the existing PRD, design docs, README and memory for rules the user set earlier. Typical examples:
   - no decorative small text, shadows or gradients;
   - square photos;
   - follow Apple HIG and Material 3.
   These rules hold for every new loop, even when the new request doesn't repeat them.

Then tell the user the plan in a few lines: which references you will collect, what you will produce, and which part of the product will change. Start right away. Wait for an answer only when something is genuinely the user's call.

## Size the work to the request

The value of this loop is traceable decisions, not volume. Extra files cost the user reading time and cost you time and tokens. Pick the smallest size that keeps every decision traceable to a source.

| Size | Typical request | What you produce |
| --- | --- | --- |
| **Small** | "How do other apps handle X?", one screen or one copy change, a quick check against a few references | No new files. Answer in the message, or make the one change. Cite sources inline and list adopt / adapt / reject in a few lines. |
| **Medium** (the default) | Rework one feature, write one standard, revise one case study or PRD section | **One report file** holding the cases, the patterns, the adopt / adapt / reject table and every source with its quality tag. Then the changed artifact itself. |
| **Large** | Several research tracks, a new product area, or more than about 15 sources; also when the user asks for full research notes | Per-track notes in `research_notes/<topic>/`, plus the report, the spec changes and the build. |

Two rules hold at every size:

- **Write into documents the project already has.** Append to the existing PRD and decision log, and put verification results where the project already keeps them. Don't start a new decision log, verification file or notes folder just because the loop mentions one. If the project has none, a short "Decisions" and "Checked" section at the end of the report is enough.
- **Put the verification summary in your final message** when the deliverable is a document rather than running software.

## The loop

### 1. Choose references that can teach something

Start from the job, not the look. "How do products let people compare an edit against the original?" finds better references than "apps with a nice editor".

Draw from four kinds of source, and say which kind each case is:

- **The brand's own official material.** This means product pages, help and troubleshooting pages, editorial picks and community programs. It is the ground truth for what this brand considers right. For example, a photo standard for a Polaroid app should come from how Polaroid's own site shows photos and from the flaws its troubleshooting page names.
- **Direct competitors** doing the same job for the same users.
- **Adjacent leaders** that solved the same pattern at scale, such as Apple, Google, Microsoft, Figma, Spotify or Airbnb. Use these especially when the user asks for big companies.
- **Platform guidelines**, Apple HIG and Material 3. Use them to check that your conclusions fit the platform the product ships on.

Meet the requested count with real cases you can check. Leave out anything that only looks like the category:

- a phone filter imitating instant film;
- a print from a different film format;
- a concept shot;
- an AI-generated example presented as real.

If you cannot reach the count with good cases, report the shortfall instead of padding the list.

### 2. Research with sources, keeping facts and inferences apart

- Keep the research proportional:
  - Aim for the requested number of cases plus one or two spares.
  - Stop adding cases once new ones only repeat patterns you already have.
  - Prefer official help pages and product pages; they state behavior more precisely than reviews.
  - If a page is blocked by a bot check or returns 403, don't fight it. Use the search summary, tag it, and move on.
  - Read each page once and take what you need from it.
- At Large size, split the work into 3–6 tracks, one notes file per track under `research_notes/<topic>/`. At Medium size, keep the cited findings in the report itself. Run tracks in parallel with subagents only when the user has asked for that or allowed it; otherwise work through them yourself.
- Every finding gets a claim, a link and a source-quality tag:
  - no tag: you read the page directly;
  - "(search summary)": the claim came from a search snippet;
  - "[unverified]": you could not confirm it.
  Date the research.
- Write what a source confirms separately from what you infer from it. Launch films, for example, are rarely described frame by frame. The report should say "source confirms: physics-based springs" and then, separately, "my reading: one continuous route instead of a feature list".
- Quote sparingly and paraphrase the rest.

### 3. Distill: shared patterns, then adopt, adapt or reject

Write the report (`reports/<topic>.md`, or wherever the project keeps research) and lead with the conclusion. Include:

- a cases table: case, what the source confirms, source link;
- the common patterns, numbered, each citing the cases that show it. Patterns backed by only one case are anecdotes; label them as such;
- a section on what this means for the product, built around an **adopt / adapt / reject** table. Its columns are: the source structure, where it came from, what this product does with it, and why, tied to the product's one job. Write down rejections and their reasons too. "Rejected: open user galleries need moderation forever and get shut down when priorities change" is the kind of line that stops the next iteration from re-adding the feature.

When the problem is a quality judgment, turn the patterns into a numbered **standard**. Typical complaints are "these photos look too AI", "too pretty" or "the motion feels cheap". Each rule in the standard needs:

- a pass test;
- examples of what fails;
- the source it traces to.

A rule's source is the research, the brand's official material or the project's own rules. This skill is never a source. If a rule comes from general practice rather than from what you found, label it "general practice".

Then **audit** the current state against the standard in a pass / close / fail table, with the failing rule numbers for each item. A vague complaint becomes a list of fixes.

### 4. Write it into the spec before building

- Update the PRD: the affected sections, the acceptance criteria and the out-of-scope list. Keep the PRD's existing structure and voice; rewrite only what the research changes.
- If the project has a decision log, append rows with these columns: Problem, Decision, Why, Source, Verified by. If it has none, don't create one for a Medium request; the report's adopt / adapt / reject table already records the decisions.
- Mark scope honestly in the spec and in anything the user will show others:
  - assumed versus designed;
  - simulated versus real;
  - "ships only if a test shows X" for speculative features. A participant asking for easier sharing is not evidence that they want a social network.
- If the change makes a README, case study or design doc wrong, list those contradictions now so they get fixed in the same pass.

### 5. Build from the spec

- Change the real artifact, and reuse the existing system first: tokens, components, text styles and layout patterns. New styles are a last resort.
- Treat every design choice as a decision that needs a reason. Before adding an element, name the problem it solves and the evidence for it. If you can't, leave it out. Decoration that carries no information makes a UI look generated. That includes meaningless small labels, drop shadows, gradients, sparkles and badges. Real hierarchy comes from type, space and order.
- Prefer real content to generated content:
  - your own screenshots of the running product;
  - real, licensed works with credits (Creative Commons, with author, title, license and link);
  - the user's own material.
  Use generated stand-ins only when nothing real exists, and check them against the same standard.
- Ask before downloading in bulk, and say the source, the count and the size. Record credits wherever the product or page shows the asset.

### 6. Verify like a reviewer

- Match the check to the deliverable:
  - **Running software or a live page:** run it and check desktop and phone widths, plus tablet if the target has a tablet layout. Take screenshots as proof, and keep them only if the user will want them.
  - **A document** (PRD, report, standard): reread it against the brief and the standing rules. Summarize the check in your final message.
- For running software, walk through each scenario and record Scenario, Expected and Status. Use the project's verification file if it has one; otherwise put this in the final message. Say what the check does not cover, for example no real users, no hardware, or a video that can't be seen in a static screenshot.
- Sweep for consistency. Check every claim in the copy against the PRD and the research, and every number against its source. Remove a claim you can't support; don't soften it.
- Re-run the standard on any new assets before calling them done.

### 7. Hand back

- Give a short report covering:
  - what changed;
  - what rests on evidence and what is your inference;
  - what is still unverified;
  - the one decision that is the user's to make next.
- Ask before publishing, committing, deleting, or replacing anything the user made.
- On shared canvases such as Framer, Figma or a live CMS, the user may be editing while you work:
  - re-read the live state before each batch of changes, and never revert their edits;
  - if something you built has disappeared, ask whether that was on purpose before restoring it. Users often prune deliberately.

## Variants

Read the matching section of `references/playbooks.md` once the target is clear:

- **Feature or flow redesign**: rework a feature the way strong products structure it. Example: turning an inspiration tab into a brand-style community.
- **Content or asset standard**: derive a standard from official sources, audit the current assets, and source real replacements.
- **Launch or showcase reel**: research big-company launch films, extract the shared techniques, and build a feature reel from the real UI.
- **Case study or portfolio page**: bring a case study in line with the latest design, fix contradictions, replace weak diagrams and assets, show responsive pairs, and apply the changes through the site's own tool.

## Templates

`references/templates.md` has the shapes for:

- a research note;
- a report;
- an adopt / adapt / reject table;
- a standard with its audit;
- a decision log;
- a verification table;
- a credits list;
- the final hand-back.

Use only the ones the request's size calls for. At Medium size that is one report file.
