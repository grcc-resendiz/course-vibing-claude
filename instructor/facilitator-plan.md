# Course Vibing with Claude: Facilitator Plan

**Session:** John Doneth, Friday, November 6, 2026, 10:00 to 11:00 AM
**Goal:** John leaves with a working Claude workspace, a Canvas HQ workstation, an MN146 course folder, a connected Codespace, and a first audit of his MN146 template shell. Lab 3 is homework.
**His material:** the faculty guide (2026-11-06-course-vibing-with-claude-faculty-guide.md). You demo, he copies and pastes from the guide.

## Run of Show

| Time | Guide step | You show | He has when done |
| :---- | :---- | :---- | :---- |
| 10:00 | Before We Start | Check the app, GitHub, token, course ID | All four ready, or a fallback chosen |
| 10:05 | Steps 1 and 2 | Settings → Profile, Settings → Cowork, Capabilities | Preferences saved, guardrails pasted |
| 10:12 | Step 3 | Create and star the folder, paste the setup prompt | Root CLAUDE.md, MEMORY.md, 00_Resources |
| 10:17 | Step 4 | The interview prompt | His own rules and facts in both files |
| 10:24 | Steps 5a and 5b | Workstation prompt, then course folder prompt | Canvas HQ and the MN146 folder, Routing Map row |
| 10:32 | Step 6 (Lab 1) | Template repo, three secrets, Codespace, connection test | His course name prints in the terminal |
| 10:45 | Steps 7 and 8 (Lab 2) | Exporter, download, move into the course Resources folder, audit prompt | His first course audit |
| 10:55 | Part 5 and Part 6 | Walk through what's left to do on his own | Lab 3 and voice profile as homework |

## Talking Points (one line each)

- **Two files run everything.** CLAUDE.md is the rules, MEMORY.md is the notepad. Both are plain text that Claude writes for you.
- **Rules stack.** Root rules apply everywhere, and Canvas HQ rules only apply to Canvas work. The course folder adds his course's own rules on top.
- **The token never goes into Claude.** Only into Codespaces secrets.
- **Dry run first, every time.** Nothing changes in Canvas until he types --confirm, and new items start unpublished.
- **Teach it once.** Every correction plus "remember this" makes the next session better.

## Checkpoints (don't move on until he has it)

1. After Step 3: the folder tree shows CLAUDE.md, MEMORY.md, and 00_Resources/voice-principles.md.
2. After Step 5: the root CLAUDE.md Routing Map has a Canvas HQ row.
3. After Step 6: the terminal prints his course name.
4. After Step 7: the export is inside his course's Resources folder, not in Downloads.

## Fallbacks

- **No Canvas token:** finish Parts 1 and 2 (Steps 1 to 5), then show Labs 1 and 2 on your screen. He does Lab 1 once his token works.
- **Running behind at 10:32:** skip Step 4 in the session. It's the easiest step for him to finish alone.
- **Secrets added after the Codespace was open:** create a new Codespace instead of troubleshooting.
- **Claude can't see the export:** the file is still in Downloads. Move it into the course Resources folder.

## After the Session

- Push the guide to GitHub so he can use it from the repo.
- Follow up next week on Lab 3: one page built from a workforce need, run as a dry run first, then confirmed and checked with a fresh export.
