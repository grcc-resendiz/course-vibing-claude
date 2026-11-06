# Course Vibing with Claude: Faculty Setup Guide

This is your copy and paste guide. **Prompts are tucked into lines that start with ▸ Prompt.** Click the line to open it, click the copy icon in the top right corner of the gray box, then paste it into Claude. Every prompt works as is, except the one in Step 9, which has one blank (____) for you to fill in. After each step, "You should see" tells you it worked.

By the end you will have:

- Claude set up with your preferences and a few safety guardrails
- A Claude workspace folder that remembers how you work, from one session to the next
- A **Canvas HQ** workstation and a folder for your own course
- A GitHub Codespace connected to your Canvas course
- A JSON export of your course and a first AI audit of it
- (Homework) A new Canvas page built from a workforce need, posted safely through the Canvas API

## Before We Start

Check these four things first. The labs stall without them.

1. **Claude desktop app** installed, with Cowork available, and signed in.
2. **A GitHub account.** Free is fine. Sign up at github.com.
3. **A Canvas access token.** In Canvas, click Account, then Settings. Scroll to Approved Integrations and click **+ New Access Token**. Type a purpose (for example "Course Vibing"), click Generate Token, and copy the token somewhere safe. You only see it once.
4. **Your course ID.** Open your Canvas course. The number after `/courses/` in the web address is the course ID. Use a template or sandbox shell, not a course students are in.

Never paste your Canvas token into Claude. It only goes into GitHub Codespaces secrets (Step 6).

---

## Part 1: Set Up Claude

### Step 1. Your general Claude preferences

Open a regular Claude chat (not Cowork) and paste this. Claude will interview you and then write your preferences.

<details>
<summary><strong>Prompt: General Claude preferences</strong></summary>

```text
Interview me so you can write my personal preferences for Claude. Ask exactly these four questions, one at a time, and no others:

1. What is your role, where do you work, and what do you teach?
2. How do you like answers: short or detailed, and in paragraphs or bullet points?
3. How much should I explain technical things like code, files, and settings?
4. When something is unclear, should I ask you first or make a reasonable call and tell you what I assumed?

When we're done, write my preferences as one block of text in the first person, under 300 words, with two short sections: "About Me" and "How to Work With Me." I will paste it into Settings → Profile, so give me only the text, ready to paste.
```

</details>

Answer the questions. When Claude gives you the finished text, click its copy button and paste it into **Settings → Profile**, in the personal preferences box. These preferences apply to every chat, not only Cowork.

**You should see:** your preferences saved in Settings → Profile.

### Step 2. Your Cowork settings and guardrails

In the Claude desktop app, go to **Settings → Cowork** and paste these instructions. They stop Claude from touching your files without asking. Loosen them later, once you trust how it behaves.

<details>
<summary><strong>Guardrails for Settings → Cowork</strong></summary>

```text
- Before deleting, overwriting, or renaming any existing file, show me exactly what will change and wait for my confirmation.
- Never modify files outside the folder I'm currently working in unless I explicitly ask you to.
- For any multi-step task, outline a brief plan first and wait for my approval before executing.
- Before sending emails, posting messages, changing calendar events, or taking any other external action, show me the proposed action and wait for confirmation.
- If instructions conflict, required context is missing, or you are unsure which file should be changed, stop and ask instead of guessing.
- Preserve existing file names, folder structure, formatting, and content unless I explicitly ask you to change them.
```

</details>

Then, under **Settings → Capabilities**: turn on both memory features, and set Tool access to **Load tools when needed**.

**You should see:** the six guardrails saved under Settings → Cowork.

---

## Part 2: Build Your Workspace

Here is what you're building. Claude writes every file for you.

```text
Claude Workspace/                        ← the "root" folder: rules here apply to everything
├── CLAUDE.md                            ← how Claude should behave (the rules)
├── MEMORY.md                            ← what Claude should remember (the notepad)
├── 00_Resources/
│   └── voice-principles.md              ← how you write
└── Canvas HQ/                           ← a "workstation": rules for Canvas work only
    ├── CLAUDE.md
    ├── MEMORY.md
    ├── Canvas HQ Resources/
    │   └── canvas_template.py
    └── MN146 - Introduction to Robotics/   ← your course: rules for this course only
        ├── CLAUDE.md
        ├── MEMORY.md
        └── MN146 - Introduction to Robotics Resources/
```

**Heads up:** because of the guardrails from Step 2, Claude will show you a plan or the changes and then wait before doing anything. That's the guardrails working. Read the plan and reply **"Looks good, go ahead."**

### Step 3. Create the root folder

1. In Finder (or File Explorer), create a folder in Documents called **Claude Workspace**. Leave it empty.
2. In the Claude desktop app, start a new Cowork task, choose that folder, and **star it** so Claude opens there every time. Jon will show you where both are.
3. Open the prompt below and paste it into Claude. It creates your three starter files.

<details>
<summary><strong>Prompt: Create your workspace files</strong></summary>

```text
Set up this folder as my Claude workspace. Create these three files with exactly the content shown between the markers, then create a folder called 00_Resources and put voice-principles.md inside it. CLAUDE.md and MEMORY.md stay in the root of this folder. When you're done, show me the folder tree.

=== FILE: CLAUDE.md ===
> Adapted from the Cowork Toolkit by Jeff Su (coworkacademy.ai/toolkit)

# CLAUDE.md

## Memory System

At the start of every session, read MEMORY.md before responding. Use what you find to inform your work. Don't announce what you found, just be informed by it.

When I say "remember this," write the information to MEMORY.md immediately and confirm you've done it.

**Where things go:** Apply two tests when deciding where to save something. Test 1: Does it prescribe behavior? Look for words like "always," "never," "before doing X, do Y." If yes, add it to this file (CLAUDE.md) under the right section. Test 2: Does it describe a fact about the world that could change? Contact details, project status, decisions, things I've told you to remember. If yes, add it to MEMORY.md. When unsure, suggest which file it belongs in and ask me to confirm.

Before working on a task, read the CLAUDE.md and MEMORY.md in every folder between this root folder and the folder the task's files live in, top to bottom.

## Preferences

- Write in a professional but conversational tone. If it sounds like a corporate memo, rewrite it.
- Keep responses concise, under 300 words unless I ask for more detail.
- Use bullet points for lists, but write explanations in natural paragraphs.
- Give me one strong recommendation. Don't give me three options unless I ask for alternatives.

## Rules

- Always ask clarifying questions before starting a complex task.
- If you're not sure about something, say so. Don't guess.
- Before producing any written content on my behalf, read voice-principles.md in the 00_Resources folder.

## Routing Map

*Add a row to this table each time a new workstation is created. At the start of a task, check this table to decide which workstation folder to load.*

| Workstation | Route here when I... |
| :---- | :---- |

## References

*Files in 00_Resources. Load each one only when its trigger applies.*

| Resource | Read when... |
| :---- | :---- |
| voice-principles.md | Writing any content on my behalf |

## Creating New Workstations

When I ask you to create a new workstation, create a subfolder with the workstation name and add these three items inside:

1. **CLAUDE.md** with these sections in this order:
   - **Identity**: One paragraph: who you are in this workstation, what routes here, what doesn't.
   - **Resources**: Table with "Resource" and "Read when..." columns. Start empty.
   - **Workflow**: Numbered steps for the primary task. Start simple; I'll refine over time.
   - **Editorial Rules**: Always opens with: "Follow my voice principles in 00_Resources (voice-principles.md)." Then add domain-specific writing rules that layer on top.
2. **MEMORY.md** with this structure:
   - Header: "[Workstation Name] Memory"
   - Sections: Contacts (people relevant to this area) and Key Decisions (the reasoning behind choices).
   - You fill this in over time as we work. I don't write it by hand.
3. **[Workstation Name] Resources/**: An empty folder for this area's reference files.

After creating the workstation, add a new row to the Routing Map above.
=== END FILE ===

=== FILE: MEMORY.md ===
> Adapted from the Cowork Toolkit by Jeff Su (coworkacademy.ai/toolkit)

# MEMORY.md

*Last updated: (today's date)*

## Active Projects

*What I'm working on right now. I'll say "add this to active projects" when I start something and "this is done" when it's finished.*

- **Course Vibing setup.** Building my Claude workspace and connecting my Canvas course to a GitHub Codespace.

## Core Memory

*Facts Claude has learned about me and my work. I'll say "remember this" to add an entry.*
=== END FILE ===

=== FILE: voice-principles.md ===
> Adapted from the Cowork Toolkit by Jeff Su (coworkacademy.ai/toolkit)

# Voice Principles

*These rules teach Claude how to write in my voice. They start generic. The voice extraction prompt makes them mine.*

## Tone

- Write like a clear, thoughtful colleague talking to a smart friend. Professional but not stiff.
- Be direct. State the key point first, then add supporting context.
- If it sounds like a corporate memo or an AI wrote it, rewrite it.

## Sentence Style

- Vary sentence length so paragraphs flow naturally.
- Use connectors like "so," "because," "for example" instead of stacking short fragments.
- Keep paragraphs to 1 to 3 sentences.

## Words and Phrases to Avoid

- Never use: "dive into," "game-changing," "leverage," "synergize," "circle back," "touch base."
- No em dashes. Use commas, colons, or periods instead.

## Words and Phrases I Use

- (Filled in by the voice extraction prompt.)

## Formatting Defaults

- Bold key points for scannability.
- One idea per paragraph.
- Use bullet points for lists, prose for explanations.
=== END FILE ===
```

</details>

**You should see:** a folder tree with CLAUDE.md, MEMORY.md, and 00_Resources/voice-principles.md.

### Step 4. Make it yours

The starter files are generic. Four quick questions turn them into yours.

<details>
<summary><strong>Prompt: Personalize your workspace</strong></summary>

```text
Interview me to personalize my workspace. Ask exactly these four questions, one at a time, and no others:

1. What college and department are you in, and what is your role?
2. Which courses do you teach, and which one are we working on first?
3. Besides Canvas, where do your course materials live (for example Google Docs, Drive, PowerPoint)?
4. What is one thing I should always do, or never do, when I work on your courses?

Sort each answer using the two tests in the Memory System section of CLAUDE.md: behavior rules go in CLAUDE.md under Preferences or Rules, facts go in MEMORY.md under Core Memory. Keep each entry to one or two sentences. When we're done, show me exactly what you added to each file.
```

</details>

**You should see:** a list of what Claude added to CLAUDE.md and to MEMORY.md, in your own words.

### Step 5. Build your Canvas HQ workstation and your course folder

A workstation is a subfolder for one area of your work, with its own rules that stack on top of the root rules. Canvas HQ is where all your Canvas course work happens. Each course then gets its own folder inside it.

**5a. Canvas HQ:**

<details>
<summary><strong>Prompt: Create Canvas HQ</strong></summary>

```text
Create a workstation called Canvas HQ, following the "Creating New Workstations" instructions in my root CLAUDE.md. Fill in the sections with this content instead of leaving them empty:

Identity: You are my Canvas course editing partner. I bring you a JSON export of a Canvas course. You review it with me, take on whatever lens I assign (subject expert, student, accessibility reviewer), and we edit the content together. Then you write a Python script that applies the approved changes through the Canvas API, which I run in my GitHub Codespace. You never touch grades, rosters, or student information. Each course gets its own folder inside Canvas HQ. Work that isn't Canvas course content doesn't route here.

Resources table, one row: canvas_template.py | Writing any Canvas API script. Reuse its connection pattern instead of rewriting it.

Workflow:
1. Read the course export I saved in that course folder's Resources and summarize the course structure, one item per line.
2. Discuss what should change, using the lens I assign.
3. Draft the edits with me until I approve them.
4. Write one script per round of approved edits, not one script per fix, and save it in the course folder's Resources. The script is a dry run by default: it only prints what it would do. It changes Canvas only when I run it with --confirm. New items are created unpublished. It reads CANVAS_URL, CANVAS_TOKEN, and COURSE_ID from environment variables (my Codespaces secrets) and never asks for a pasted token. It prints "Run started:" with the date and time as its first line, and saves its full terminal output to Run Outputs/<script name>-output.log so I can bring the log back to you.
5. Before I run anything, show me a plain summary of what the script will change, and tell me how to run it: the exact file to drag into my Codespace and the exact terminal commands for the dry run and for --confirm, each ready to copy. Keep script file names short, with no spaces.
6. After I run it with --confirm, I bring back a fresh export, and you confirm that only the approved changes happened.

Editorial Rules, after the standard opening line:
- Every page uses a clear heading order (H2, then H3), descriptive link text, and alt text on every image.
- Check every due date against the term calendar I give you.

Then add a section to Canvas HQ/CLAUDE.md called "Creating New Course Folders": when I start work on a new course, create a subfolder inside Canvas HQ named after the course, containing a CLAUDE.md (sections: Course, a one paragraph description; and Editorial Rules, opening with "Follow Canvas HQ's editorial rules and my voice principles in 00_Resources (voice-principles.md)."), a MEMORY.md (header "[Course Name] Memory", sections Contacts and Key Decisions), and an empty "[Course Name] Resources" folder.

Then add this rule to the Workflow in Canvas HQ/CLAUDE.md: when I say I dropped a file into my workspace, find it in the root folder and move it into the Resources folder where it belongs (a course export or script log goes in that course's Resources folder, canvas_template.py goes in Canvas HQ Resources). Then tell me where you put it.

Finally, add this row to the Routing Map in my root CLAUDE.md: Canvas HQ | ...am working on Canvas course content: reviewing a course export, editing pages, assignments, or modules, or writing a Canvas API script.

Show me the folder tree and each file you wrote.
```

</details>

**You should see:** a Canvas HQ folder with its own CLAUDE.md, MEMORY.md, and Resources folder, and a new Canvas HQ row in your root CLAUDE.md's Routing Map.

**5b. Your course folder:**

<details>
<summary><strong>Prompt: Create your MN146 course folder</strong></summary>

```text
Create a course folder for "MN146 - Introduction to Robotics" inside Canvas HQ, following the "Creating New Course Folders" section in Canvas HQ/CLAUDE.md.

For the Course section, ask me exactly these three questions, one at a time, and no others:

1. What term is this for, and what are its start and end dates?
2. When does class meet, and when is work due each week?
3. Does anything for this course live outside Canvas, such as lab handouts or slides?

Then write the paragraph from my answers and show me both files.
```

</details>

**You should see:** an MN146 folder inside Canvas HQ, with a Course paragraph written from your answers.

---

## Part 3: Connect to Canvas (Lab 1)

### Step 6. Set up your Codespace

1. Open **github.com/grcc-resendiz/canvas-api-template** and click **Use this template → Create a new repository**. Name it after your course (for example `mn146-canvas`), choose **Private**, and click **Create repository**.
2. In your new repo, click the **Settings** tab at the top. In the left menu, click **Secrets and variables → Codespaces**.
3. Add three secrets. For each one, click **New repository secret**, copy the name into the Name box, put the value in the Secret box, and click **Add secret**.

   | Name | Secret |
   | :---- | :---- |
   | `CANVAS_URL` | `https://grcc.instructure.com` |
   | `CANVAS_TOKEN` | the token you copied in Before We Start |
   | `COURSE_ID` | your course ID number |
4. Go back to the **Code** tab of your repo. Click the green **Code** button, then **Codespaces → Create codespace on main**. It opens a code editor in your browser. Wait a minute or two for it to finish building.
5. In the terminal at the bottom, run:

```bash
python canvas_template.py
```

**You should see:** your course name and its modules. That's your first API connection.

6. In the file list on the left, right click **canvas_template.py → Download**. In Finder, drag it from Downloads into your **Claude Workspace** folder (the top level is fine). Then paste this into Claude:

```text
I dropped canvas_template.py into my workspace. Move it into Canvas HQ Resources.
```

Now Claude can base every script on it.

**Added the secrets after opening the Codespace?** Create a new Codespace. One that is already open won't see new secrets.

---

## Part 4: Read Your Course (Lab 2)

### Step 7. Export your course to JSON

1. In the Codespace terminal, run:

```bash
python canvas_course_json_exporter.py
```

This only reads your course. It never changes anything.

**You should see:** a count of your modules, pages, and assignments, and the name of the new .json file.

2. Open the **canvas_exports** folder on the left, right click the new .json file, and choose **Download**.
3. In Finder, drag it from Downloads into your **Claude Workspace** folder.

Claude can only read files that are inside your workspace folder. A file left in Downloads won't work, even if you drag it into the chat.

### Step 8. Have Claude audit your course

<details>
<summary><strong>Prompt: Audit your course</strong></summary>

```text
I dropped a new Canvas course export (.json) into my workspace. Move it into the MN146 - Introduction to Robotics Resources folder, then follow the Canvas HQ workflow: summarize the course structure first, one item per line. Then review it as a student taking this course for the first time. List anything missing, any inconsistent naming, any dates that don't line up, and anything that would confuse a student. End with the one page or assignment that would help students most. Don't write any scripts yet.
```

</details>

**You should see:** your course structure, one item per line, then the audit and one recommendation. Pick one item from the audit. That's what you build in Part 5.

---

## Part 5: Build and Publish (Lab 3, Homework)

### Step 9. Turn a workforce need into Canvas content

Fill in the one blank, then paste.

<details>
<summary><strong>Prompt: Workforce need to Canvas content (fill in one blank)</strong></summary>

```text
For MN146, employers and our advisory board told us graduates need ____________.

Using my latest MN146 course export, create one Canvas page (or assignment, or module) for that need, with a short intro, three learning outcomes, and one hands-on activity. Match the naming and module structure already in my course, and follow this course's CLAUDE.md. Show me the content first.

Once I approve the content, write the script following the Canvas HQ workflow, based on canvas_template.py in Canvas HQ Resources. Create the item unpublished.
```

</details>

### Step 10. Preview, revise, publish

Claude ends Step 9 with the file to drag and the exact commands to run. Use those.

1. Drag the script from your course's Resources folder (in Finder) into the file list on the left of your Codespace.
2. Copy the **dry run** command Claude gave you into the Codespace terminal and press Enter. It looks like `python create_page.py`. Nothing changes in Canvas yet.
3. Read what it says it will do. Want Claude to check it too? Right click the log in the Codespace's **Run Outputs** folder, choose **Download**, drag it into your Claude Workspace folder, and paste:

```text
I dropped the dry run log into my workspace. File it, read it, and tell me if the script will do exactly what we approved.
```

   Not right? Tell Claude what to change, drag the new version into the Codespace, and run the dry run again.
4. When it looks right, copy the **--confirm** command Claude gave you and run it. This is the only step that changes Canvas.
5. Open Canvas and check the new item. It starts unpublished. Publish it yourself when you're ready.

### Step 11. Verify

Run the exporter again (Step 7), download the new export, drag it into your Claude Workspace folder, and paste:

<details>
<summary><strong>Prompt: Verify the changes</strong></summary>

```text
I ran the script with --confirm and dropped a fresh MN146 export into my workspace. File it, then compare it to the previous export and confirm that only the approved changes happened. Then log what we built and why in this course's MEMORY.md under Key Decisions.
```

</details>

---

## Part 6: Keep It Sharp

Use these whenever you have a few minutes. They make the workspace smarter over time.

**Teach it once.** Any time you correct Claude, say "remember this" and it saves the correction.

**Your real voice** (use 5 samples of your own writing, such as emails, announcements, or lab instructions):

<details>
<summary><strong>Prompt: Voice extraction</strong></summary>

```text
I'm going to paste 5 samples of my writing below. Analyze them and extract my writing patterns: tone, sentence cadence, word choices, phrases I repeat, and structural habits that show up no matter what I'm writing. Skip format conventions specific to email, such as greetings, sign-offs, and signature lines. Those are email boilerplate, not voice.

Then read my existing voice-principles.md file in the 00_Resources folder and update it with the patterns you found. Keep the current section structure. Replace the generic defaults with my real patterns, but keep the "Words and Phrases to Avoid" defaults and add any new ones you spot.

After updating the file, show me what changed so I can review it.

---

[Paste your 5 writing samples below this line]
```

</details>

**End of session audit** (run once to create the skill, then say "audit this session" at the end of any session):

<details>
<summary><strong>Prompt: Create the session audit skill</strong></summary>

```text
Create a skill called session-audit. It should run at the end of any session and do exactly two things:

1. Scan the whole conversation for corrections I made to your output, preferences I stated directly (words like "always," "never," "I prefer"), decisions I made, and new facts about me or my work that you didn't already know.
2. For anything not already written in my CLAUDE.md or MEMORY.md, tell me the exact wording to save and which file and section it goes in, then wait for me to approve before writing anything.

If nothing new came up, just say so. Trigger it whenever I say "audit this session," "session audit," or "what did we miss."
```

</details>

**Right file, right place** (run after a few weeks):

<details>
<summary><strong>Prompt: Right file, right place</strong></summary>

```text
Review my root CLAUDE.md and MEMORY.md. In CLAUDE.md, flag any entry whose primary purpose is recording a fact or status rather than prescribing how you should behave. In MEMORY.md, flag any entry whose primary purpose is telling you how to behave rather than recording a fact. Recommend where each flagged entry should move.
```

</details>

---

## If Something Goes Wrong

- **"Unauthorized" or 401 error:** the token is wrong or expired. Make a new token, update the CANVAS_TOKEN secret, and create a new Codespace.
- **Course not found:** check that COURSE_ID is only the number, with no slashes.
- **Codespace can't see your secrets:** create a new Codespace after adding them.
- **"ModuleNotFoundError" when you run a script:** in the terminal, run `pip install canvasapi python-dotenv`, then try again.
- **Claude is waiting and nothing happens:** it's showing you a plan and waiting for approval. Scroll up, read it, and reply "Looks good, go ahead."
- **Claude says it can't find a file:** the file is still in Downloads. Drag it into your Claude Workspace folder and ask again.
- **Claude starts writing a script before you approved the content:** say "Stop. Follow the Canvas HQ workflow." Then say "remember this" so it sticks.

## Go Deeper

The full Course Vibing course in Canvas walks through every step here in more detail, plus importing an old course, shifting dates for a new semester, and bulk updates: **tinyurl.com/course-vibing-canvas**. That course uses ChatGPT in its examples. The same steps work in Claude, and your workspace means you can skip most of the copy and paste.
