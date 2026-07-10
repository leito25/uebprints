---
name: unreal-course-log
description: Use when updating the Unreal Engine Blueprint Scripting 101 course learning log after commits or study sessions, analyzing git changes against ProjectLog.md sessions, adding brief commit notes, and marking course progress checkboxes without inventing unsupported work.
---

# Unreal Blueprint Course Log

Use this skill when the user asks to update, analyze, mark progress, or add comments/details in `ProjectLog.md` after a git commit or coursework session for the Udemy course "Unreal Engine Blueprint Scripting 101":

`https://www.udemy.com/course/unreal-engine-blueprint-scripting-101/`

## Workflow

1. Read `ProjectLog.md`.
   - If it does not exist, create a concise course log skeleton before adding progress.
   - Prefer existing section/session titles in `ProjectLog.md` over the topic hints below.
2. Inspect the target commit, defaulting to `HEAD`:
   - `git show --stat --summary HEAD`
   - `git show --name-status --format=fuller HEAD`
   - Read changed Blueprint-adjacent assets, C++ source, config, maps, docs, or generated notes when the stat is not enough.
3. Match the commit to one learning session using the strongest evidence:
   - Course/project setup, engine version, starter map, repository baseline, `.uproject`, `.gitignore` -> Session 01 or the setup/overview section.
   - Blueprint editor orientation, graph navigation, nodes, execution pins, comments, compile/save workflow -> the Blueprint basics section.
   - Variables, types, object references, arrays, structs, enums, defaults, editable/exposed values -> the variables/data section.
   - Branches, sequences, loops, gates, delays, timers, flow-control nodes -> the flow-control section.
   - Functions, macros, collapsed graphs, pure functions, local variables, reusable logic -> the functions/macros section.
   - Events, input actions, key/mouse/gamepad bindings, player controller, pawn/character input -> the events/input section.
   - Actors, components, construction script, transforms, spawning, destroying, attaching -> the actors/components section.
   - Collision, overlap/hit events, traces, casting/interfaces, object communication -> the interaction/communication section.
   - Timeline, interpolation, movement, animation triggers, materials, audio cues, particle or Niagara triggers -> the feedback/polish section.
   - Widgets, HUD, UMG, buttons, text, progress bars, viewport widget creation -> the UI section.
   - Debugging, print string, breakpoints, watch values, validation, cleanup, naming conventions -> the debugging/cleanup section.
   - Packaging, final review, documentation, course wrap-up -> the final/wrap-up section.
4. Update only the matched session unless the commit clearly spans multiple sessions.
5. Under `Related commits`, add one short bullet:
   - ``- `shortsha` - Brief learning-focused note.``
6. Mark only checklist items directly supported by the commit:
   - Change `- [ ]` to `- [x]`.
   - Do not mark an item complete from filenames alone if the behavior is unclear.
7. Update `Status` conservatively:
   - `Not started` -> `In progress` when any checklist item or related commit is added.
   - `In progress` -> `Completed` only when every checklist item in that session is checked.
8. Add a blocker or follow-up only when the commit or build output shows one.
9. Preserve user notes, existing commit history, and unrelated file changes.

## ProjectLog Skeleton

When `ProjectLog.md` is missing, create a compact skeleton with these sections:

```markdown
# Unreal Engine Blueprint Scripting 101 - Project Log

Course: https://www.udemy.com/course/unreal-engine-blueprint-scripting-101/

## Session 01 - Setup and Overview
Status: Not started

### Checklist
- [ ] Create or open the Unreal project
- [ ] Configure source control ignores
- [ ] Record the course baseline

### Related commits

### Log notes
```

Add later sessions only when the user provides lecture titles, `ProjectLog.md` already contains them, or a commit clearly belongs to a Blueprint topic listed in the workflow.

## Output Rules

- Keep notes brief and factual.
- Prefer course-learning language over raw implementation detail.
- Do not claim tests passed unless they were run.
- If no confident session match exists, add the commit to the closest existing session with a `Follow-up` note explaining what needs human confirmation.
- Do not claim a specific Udemy lecture was completed unless the user explicitly says so or `ProjectLog.md` already records it.

## Helper Commands

Gather context for a commit:

```powershell
git show --stat --summary HEAD
git show --name-status --format=fuller HEAD
git log --oneline -10
```

Add a manual dated note to `ProjectLog.md` under the relevant session's **Log notes** block:

```
- YYYY-MM-DD - Your note here.
```

Do not fabricate log notes. Only write notes grounded in the commit diff or the user's explicit statement.
