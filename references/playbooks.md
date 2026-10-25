# Playbooks

Four variants of the loop in SKILL.md. Each one lists the references to collect, the questions the research must answer, the outputs, how to build, and the mistakes that came up in practice.

## Contents

1. Feature or flow redesign
2. Content or asset standard
3. Launch or showcase reel
4. Case study or portfolio page

---

## 1. Feature or flow redesign

**Typical request:** "Turn X into a Y-style community; look at how the common ones are structured, update the PRD and rebuild it." Or: "Rebuild Gallery and Archive per the PRD."

**Clarify first.** Phrases like "Polaroid-style" or "like Instagram" can mean the brand's own program or the genre in general. When the answer changes the research, ask with 2–3 options.

**References to collect** (one research track each):

- the brand's own version of the feature, if it has one, such as an official community, a curated program or an editorial pick;
- enthusiast communities that grew around the medium;
- adjacent apps with the same mechanics;
- failures: similar features that were shut down or that drifted into something else, and why.

**Questions every track must answer:**

- What is the unit of content, and what facts travel with it?
- How is it organized (feed, groups, editions, shelves, profiles), and how does a newcomer find their way?
- What can people do: participation, reactions and the routes back into their own work?
- Who curates, how often and how much?
- What are the moderation and honesty rules?
- What killed or bent similar features?

**Outputs:**

- one report with the adopt / adapt / reject table and its sources;
- the rewritten PRD section: the IA, the content unit, the participation mechanics, the cadence, states and empty states, what is out of scope, and acceptance criteria;
- the rebuilt screens, if the request includes building them, checked in the browser;
- at Large size only, per-track notes in `research_notes/<topic>/`.

**Build notes:**

- Every route in the feature should end at the product's core job. For example, the only public action in a community is "Try on my photo", which opens the main tool on the user's own content.
- Limits are features: a weekly edition, one submission each, no counts. Write them as rules in the PRD so the build can't drift.

**Pitfalls:**

- Treating a weak signal as a mandate. "Some people wanted easier sharing" justified a bounded experiment, not a social network. Gate speculative features behind a test with a pass condition.
- Copying the genre's engagement mechanics (likes, follows, streaks, points) because everyone has them. Check each one against the product's job and against what the research says those mechanics did to communities.

---

## 2. Content or asset standard

**Typical request:** "The photos you picked look too AI or too pretty. Look at how the official site chooses photos and set a standard." Or: "Can you find real ones for me?"

**References to collect:**

- how the brand's official site, campaigns and community picks show content: subject distance, light, composition, what counts as ordinary;
- the brand's own defect or troubleshooting pages, which name the real flaws. Real flaws make honest demo material for any product that fixes or explains them;
- the physical truth of the medium: format, proportions, borders and how the medium renders color and detail.

**The standard:**

- Write 6–10 numbered rules. Each one gets a pass test, concrete examples of what fails, and its source.
- Always include a rule against tells of generation and stock: flawless skin, uncanny symmetry, light with no source, everything pretty at once.
- Then audit every current asset in a pass / close / fail table, giving the failing rule numbers per item.

**Sourcing real replacements:**

- Search sources with license filters, such as Flickr with CC BY, CC BY-SA or public domain, or Wikimedia Commons.
- Read each candidate's metadata page and reject fakes by camera, tags and description. Common fakes are phone-app filters, DSLR shots, a neighboring film format and editing presets.
- Check each candidate against the standard before swapping it in. Drop duplicates and near-duplicate scenes, and anything with clips, stickers or decorative borders the standard excludes.
- Before downloading, ask the user and give the source, the count, the resolution and the destination folder.
- Crop to the content area by hand when automatic cropping fails. Keep the crop boxes so the step can be repeated.
- Record credits (author, title, license, link) in the data file, show them where the product shows the asset, and keep a full list in the README.

**Pitfalls:**

- Demo corrections applied to photos that never had the flaw, such as brightening a photo that was never dark. Each demo asset must visibly have the flaw it demonstrates.
- Mixing in the neighboring brand's medium because it is easier to find.

---

## 3. Launch or showcase reel

**Typical request:** "Look at how other products' launch animations work. Find at least 10 excellent cases, all from big companies, then use what they share to make a feature showcase reel with no extra text. Free mockups only."

**References to collect:**

- At least the requested number of launch films or feature films from large software companies. Strong candidates are WWDC segments, Google I/O and The Android Show, Windows and Surface films, Figma Config, Spotify Wrapped, Airbnb releases and One UI introductions.
- For each one, the source-confirmed traits, usually from studio case pages, design blogs or press. Keep these separate from your reading of the film.

**Patterns that recur** (confirm them against your own cases; don't assume them):

1. The real UI is the hero: press, drag, result. No narration.
2. One continuous route through the product, not a feature list.
3. Shared-element transitions: the thing in this shot becomes the subject of the next.
4. Wide shot to show where you are, then push in on the control that changes.
5. Physicality: springs, weight, material. Sometimes deliberately less smooth.
6. Restraint: motion only where it explains a change, and one visual language throughout.
7. Real content, not stock.
8. End on the logo and hold it.

**Build approach that worked:**

- Write the reel as an HTML page driven by a single timeline function, `seek(t)`, that sets every element's state for time t. Render it frame by frame with headless Chrome over the DevTools protocol, then encode with ffmpeg: 1920×1080, 30 fps, H.264.
- Draw device frames in CSS in the product's own style, or use free mockups with a license you have checked.
- Use the product's real screens and real assets. If the user said no text, the only text on screen is the UI itself and the end logo.

**Verify:**

- Extract frames at key timestamps and look at them.
- Check the duration, resolution and file size.
- Save the reel and its research report together.

---

## 4. Case study or portfolio page

**Typical request:** "Reorganize my case study at <url> to match the latest design. Fix anything that contradicts itself. The decision tree doesn't connect well. Replace weak assets with screenshots. It's responsive, so show both sizes. Make it a mature case study, using the sites you researched as reference."

**Deliverables:** the revised page, plus a short list of the contradictions found and how each was fixed. That list can sit in the final message or in one small file. A case study revision rarely needs its own research notes, decision log or verification file.

**Read before writing:**

- the live page at every breakpoint;
- the latest PRD, the decision log and the README.

List every contradiction between the page and the current design: features, flows, claims, numbers, names and labels. Examples:

- "fixes blur" when the product refuses to fix blur;
- "desktop community" when the feature is cross-platform;
- a competitor's product named wrongly.

**Diagnose weak sections.** A diagram that doesn't connect to the decisions should be replaced with a structure that does. Two kinds work:

- a map from research to decision to feature, showing where each insight ends up in the product;
- a decision tree of how the product itself behaves, for example the three outcomes for a photo, each with a real screenshot.

**Assets:**

- Capture fresh screenshots from the running prototype with a script. Seed the app's state first, then capture desktop and phone sizes at high pixel density. Show desktop and phone side by side for each main screen.
- Keep the user's own videos and mockups when they show the current design.

**Structure borrowed from mature case studies and launch pages:**

- an outcome-first hero;
- the problem with evidence (a number, a real artifact, a quote);
- who was studied;
- what is assumed versus what was designed;
- the research and competitor comparison as a real table, not a screenshot of one;
- each insight leading to a decision with its visual;
- one section on responsive layout;
- the system;
- validation that says honestly what was and wasn't tested;
- reflection;
- credits.

**Apply through the site's own tool.** Draft locally as HTML first, then apply the changes through the site builder's MCP or CLI (for example Framer):

- Reuse the site's text styles and components.
- After rewriting copy on existing nodes, check that their text styles survived, and re-apply them if not.
- Check the order and padding of every breakpoint. New sections often land at the end of tablet and phone layouts, and fixed desktop paddings crush text on a phone.
- Run the publish preview, then ask before publishing.

**Pitfalls:**

- Overwriting the user's wording. Change copy only where it contradicts the design or where the user asked.
- Re-adding what the user removed. Re-read the live page before every batch.
- Claims that aren't backed by the research, such as "fewer than ten packs a year". Cut them or source them.
