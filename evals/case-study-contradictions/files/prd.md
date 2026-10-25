# Loop PRD v3 (latest, Oct 2026)

Loop is a habit tracker for people who have quit habit apps before. iOS only in v1; Android is out of scope until 2027.

## Changes since v2
- **AI coach removed.** In the v2 test, 4 of 5 participants found the morning AI coach message "preachy" and 3 turned off notifications. Replaced by habit templates written by the team.
- **Streaks no longer reset on one miss.** A single missed day uses a grace day and pauses the streak; only two misses in a row reset it.
- **Weekly reflection added.** Every Sunday, one screen shows the week as dots and asks one question: "What got in the way?" Answers stay private.

## Screens
1. **Today**: the list of today's habits; tap to check off.
2. **Habit detail**: a 12-week dot calendar; grace days are shown as hollow dots.
3. **Reflection** (Sundays): the week's dots and one question.
4. **Templates**: 20 habit templates by the team, each with a suggested time and a one-line why.

## How Loop handles a day
- Habit done: filled dot, streak +1.
- Habit missed, grace day available: hollow dot, streak paused, a quiet note "Grace day used".
- Habit missed twice in a row: streak resets to 0, and the next morning shows "Start again from today" with no penalty copy.

## Research
See research-notes.md.
