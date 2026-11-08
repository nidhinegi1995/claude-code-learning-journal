# Agentic AI & Multi-Agent Workflows: Build Apps with One Prompt

**Agentic AI refers to autonomous AI systems that don’t just generate outputs like text or images, but actively _take actions_ toward achieving goals with minimal human supervision. Unlike generative AI, which focuses on content creation, agentic AI is designed to plan, decide, and execute tasks in the digital or physical world.**

**⚙️ How Agentic AI Works**

**Agentic AI typically combines several components:**

-   **Large Language Models (LLMs): Provide reasoning, planning, and natural language interaction.**
-   **Tools & APIs: Allow agents to interact with external systems (e.g., search engines, calculators, databases).**
-   **Memory & Feedback Loops: Enable learning from past actions and adjusting strategies.**
-   **Orchestration: Coordinates multiple agents (sometimes hierarchical, sometimes decentralized) to complete complex workflows.**

In short, **agentic AI is the next evolution beyond generative AI**—moving from “thinking and speaking” to “thinking and doing.” It’s about AI systems that can autonomously plan, act, and adapt in pursuit of real-world goals.

Create a new Project Folder. Open it in Vscode.

In **Claude**, the term _context_ refers to the information the model has available when generating a response. Think of it as the "working memory" Claude uses to understand your request and produce relevant output.

**🧠 What Context Means in Claude**

-   **Conversation history**: Claude looks at the messages exchanged so far in the chat.
-   **Uploaded files or documents**: If you provide text, PDFs, or other content, Claude can use that as part of its context.
-   **Prompt length**: Claude has a maximum _context window_ (the number of tokens it can process at once). For example, Claude 3.5 Sonnet supports up to **200,000 tokens**, which is huge compared to most other models. This means it can handle entire books, long codebases, or detailed project files in one go.

**⚙️ How Claude Uses Context**

-   **Understanding intent**: It interprets your question based on prior turns.
-   **Referencing details**: It can recall facts or instructions from earlier in the conversation.
-   **Maintaining coherence**: Context helps Claude stay consistent across long dialogues.
-   **Grounding answers**: If you upload a document, Claude uses that document’s text as context to answer questions about it.

**📊 Example**

If you ask Claude:

1.  _"Summarize this 50-page research paper"_ → The paper becomes part of the context.
2.  _"Now compare it with the one I uploaded earlier"_ → Claude uses both documents in its context window to generate a comparison.

**⚠️ Limitations**

-   **Context window size**: If the conversation or files exceed the maximum token limit, Claude will only consider the most recent or most relevant parts.
-   **No permanent memory**: Context is temporary; once the chat ends, Claude doesn’t retain it unless paired with external memory systems.

👉 In short, _context in Claude is the immediate information the model can "see" and reason over while responding_. Its massive context window is one of its standout features, making it especially powerful for analyzing long documents or extended conversations.

If you want to resume a context then do/resume conversation and select the options from the contexts. Then that context will be resumed.

Yes—you can absolutely **summarize a context and reuse it later in a new context**. This is a common technique in prompt engineering and agentic AI workflows. Here’s how it works:

**🧠 Why Summarize Context**

-   **Compression**: Long conversations or documents may exceed the model’s context window. Summarizing reduces size while keeping the essence.
-   **Reusability**: A summary can be stored and reintroduced whenever you want to “remind” the AI of past information.
-   **Clarity**: Summaries strip away noise and highlight the most relevant details for future tasks.

**⚙️ How to Do It**

1.  **Create a summary** of your current context (conversation, document, or notes).
    -   Example: Instead of pasting a 20-page report, summarize it into key bullet points.
2.  **Save the summary** externally (in your notes, a file, or memory if the AI supports it).
3.  **Inject the summary into a new prompt** when you want to reuse it.
    -   Example:
        -   _Summary_: “Project X is a Java-based web app using Maven and Tomcat. Goal: automate testing with Playwright.”
        -   _New Context_: “Using the summary above, suggest next steps for scaling Project X.”

Claude Code Modes:

**Rule of thumb:** Use Plan to think things through, Accept edits once you trust the direction, and Default when shell commands could do damage. Allow and deny rules in your settings sit on top of whichever mode you choose.

**Use Case 1 — AI Content System**

With one prompt:

-   Generate viral LinkedIn post
-   Create Twitter content
-   Build reusable **brand voice system**

In Plan mode, enter this prompt:
**Research the latest Claude code tool and write a viral LinkedIn Post** **Output the draft document**

Yes. In plan mode, Claude Code saves each plan as a Markdown (.md) file on your computer. Here’s what to know for your notes:

**Where it’s saved**

-   By default, plans go to ~/.claude/plans/ in your home folder. This one folder is shared by every project, and file names are random and generated, like dreamy-orbiting-quokka.md. Plans persist across sessions, so closing and reopening Claude Code won’t delete them.
-   To keep plans next to your code, add this to the project’s .claude/settings.json:

json

"plansDirectory": "./plans"

The plan is then saved in your repo’s plans/ folder, where you can find it next session, @-mention it, and commit it with the PR. The path has to stay inside the project. If it points outside, Claude Code ignores it and falls back to ~/.claude/plans/.

**What’s in the file**

-   The full plan: context, the changes file by file, and how to verify them. It’s plain Markdown, so you can open it in any editor, add notes, and ask Claude to revise the plan from your annotations.

**Useful to know**

-   The file is the plan itself, not a summary. Claude reads it back after context compaction, so the plan survives long sessions.
-   Approving the plan exits plan mode and starts the edits, so the .md file is the record of what was agreed.

I've saved your brand voice as a personal skill and rewritten both drafts in that voice.

**The skill:** `~/.claude/skills/brand-voice/SKILL.md`

It's stored in your user folder, so it works in every project, not just Lesson03. Claude should load it on its own whenever you ask for a post, tweet, bio or newsletter, without you having to mention it. It records your answers:

-   **Who you are:** a QA/test engineer learning AI in public, sharing your own journey.
-   **Audience:** testers, developers, beginners and hiring managers. Jargon gets a short plain explanation.
-   **Tone:** friendly and practical. Posts open with what you tried, then the news.
-   **Format:** moderate emoji, 150–250 words on LinkedIn, and every post ends on one key takeaway line.
-   **Hashtags:** 3–5 per post, from a core set (#SoftwareTesting #AIinTesting #QA #LearningInPublic) plus 1–2 for the topic.
-   **Never:** fear-based hooks, engagement bait or hype without a real example. The skill ends with a short checklist I go through before handing you a draft.

**One thing to add later:** the skill has an empty "Sample posts" section. Pasting 2–5 posts you've actually written is the best way to make future drafts sound like you, and where your real posts differ from the written rules, the skill follows your posts.

**Skills in Claude**

A **skill** is a packaged set of instructions, plus optional scripts and reference files, that teaches Claude how to do one kind of task well. You can think of it as a playbook Claude picks up when the task calls for it.

**What a skill contains**

A skill is a folder with a SKILL.md file at its root:

my-skill/

├── SKILL.md ← required: name, description, instructions

├── scripts/ ← optional: helper code Claude can run

└── references/ ← optional: docs, templates, examples

SKILL.md starts with a short header:

\---

name: weekly-report

description: Build the team's weekly status report. Use when the user asks for a weekly update or status report.

\---

\# Instructions

1\. Pull last week's items from...

2\. Format them as...

**How it works**

1.  **Discovery:** Claude only sees each skill's name and one-line description up front, so having many skills installed costs very little context.
2.  **Triggering:** When your request matches a description, Claude loads the full instructions. This can happen without you naming the skill (for example, "write a LinkedIn post" can trigger a brand-voice skill). You can also call one directly by typing /skill-name.
3.  **Progressive loading:** Scripts and reference files load only when they're needed, which keeps skills cheap until they're used.

**Why use them**

-   **Consistency:** The same process every time, like your house style, a review checklist, or a reporting format.
-   **Domain knowledge:** Rules and context Claude wouldn't otherwise know, like your team's conventions or your trading framework.
-   **Reusability:** You write it once and it applies in every session, without re-explaining.
-   **Tools bundled in:** Skills can include working code, like the PDF, Excel and PowerPoint skills that create real files.

**Examples already in your setup**

|
**Skill**

 |

**What it does**

 |
| --- | --- |
|

brand-voice

 |

Writes social posts in a set personal style

 |
|

nifty-trend-range

 |

Weekly Nifty regime and range framework, logged to a spreadsheet

 |
|

weekly-positioning-check

 |

Checks F&O leverage and positioning across three brokerage accounts

 |
|

pdf, xlsx, docx, pptx

 |

Read and create those file types

 |
|

skill-creator

 |

Helps you build and test new skills

 |

**Skills vs. other features**

-   **Skills vs. prompts:** A prompt applies once. A skill is saved and loads automatically whenever it's relevant.
-   **Skills vs. MCP connectors:** Connectors give Claude _access_ to systems like Gmail, Drive or Groww. Skills give Claude _know-how_: how to use that access for your task.
-   **Skills vs. memory:** Memory stores facts about you. Skills store procedures.

**Making your own**

The easiest way is to ask: _"Create a skill that…"_. That uses the skill-creator skill, which drafts the SKILL.md, tunes the description so it triggers at the right times, and can test it. You can also write the folder by hand and put it in ~/.claude/skills/ (personal) or .claude/skills/ inside a project (shared with that project).

Prompt:

Hi there, I would like to create and develop a To Do List Web Application that uses a Kanban board to track the progress of the To Do’s. By default, there will be three columns in this Kanban board:

1\. To Do

2\. In Progress

3\. Completed

To Do items should have all of the basic details like:

\- The title

\- A description

\- A priority

\- Tags

I've built the Kanban to-do app in [kanban-todo/](vscode-webview://19flu0jgjftbi3qnutn9gcejh7ohfgmsk2c7cnjc7ttmlj3bftpk/kanban-todo/). To use it, double-click [index.html](vscode-webview://19flu0jgjftbi3qnutn9gcejh7ohfgmsk2c7cnjc7ttmlj3bftpk/kanban-todo/index.html) to open it in your browser. There's no install or server.

I checked the JavaScript for syntax errors and it passed, but I haven't opened the app in a browser or tested the features. Please click through them once, especially drag-and-drop.

**What it does:**

-   **Three columns** (To Do, In Progress, Completed), each showing how many tasks it holds.
-   **Each task has** a title (required), a description, a priority (High, Medium or Low), tags (comma-separated) and a status.
-   **Adding tasks:** use the "+ New task" button, the "+" on a column header, or press N anywhere outside a text box.
-   **Editing and deleting:** click ✎ or double-click a card. The Delete button is in the edit window and asks you to confirm.
-   **Moving tasks:** drag cards between columns or reorder them within a column. The ← → buttons on each card do the same thing and also work on phones, where dragging doesn't.
-   **Search and filter:** the search box covers titles, descriptions and tags. You can also filter by priority, or click a tag on any card to show only tasks with that tag.
-   **Saving:** tasks stay in your browser between visits. The board starts with three example tasks so it isn't empty.
-   **Look:** cards have a coloured left edge for priority, completed tasks are struck through, there's a dark mode, and on a phone the columns stack vertically.

**Files:**

-   [index.html](vscode-webview://19flu0jgjftbi3qnutn9gcejh7ohfgmsk2c7cnjc7ttmlj3bftpk/kanban-todo/index.html): the page and the add/edit window.
-   [styles.css](vscode-webview://19flu0jgjftbi3qnutn9gcejh7ohfgmsk2c7cnjc7ttmlj3bftpk/kanban-todo/styles.css): the layout, colours and dark mode.
-   [app.js](vscode-webview://19flu0jgjftbi3qnutn9gcejh7ohfgmsk2c7cnjc7ttmlj3bftpk/kanban-todo/app.js): the tasks, saving, drag-and-drop and filters.

**Limits:**

-   Tasks are saved only in the browser you use. They won't appear on another device or browser, and they're lost if you clear your browser data.
-   I chose plain HTML, CSS and JavaScript so it opens without any setup. If you'd rather have React, a backend database or user accounts, tell me which and I'll plan that version.

The React version of your Kanban to-do app is running on your computer at [**http://localhost:5173**](http://localhost:5173/). Open that address in your browser to use it.

I confirmed the production build finishes without errors and the server returns the page and the compiled app code. I haven't clicked through it in a browser, so please try adding, editing, dragging, filtering and deleting a task once.

**What it does:**

-   **Three columns:** To Do, In Progress and Completed, each with a task count.
-   **Tasks** have a title, description, priority (High, Medium or Low), tags and a status.
-   **Adding:** the "+ New task" button, the "+" on any column, or the N key.
-   **Editing:** the ✎ button, a double-click, or Enter on a selected card. You can delete a task from the edit window, and it asks you to confirm first.
-   **Moving:** drag a card to another column or to a new spot in the same column, or use the ← → buttons, which also work on phones.
-   **Search and filters:** a search box, a priority filter, and clicking any tag shows only tasks with that tag.
-   **Saving:** tasks stay saved in your browser after a refresh. There's also a dark mode and a layout that works on phones.

**Where things are:** the app is in [kanban-react/](vscode-webview://19flu0jgjftbi3qnutn9gcejh7ohfgmsk2c7cnjc7ttmlj3bftpk/). [README.md](vscode-webview://19flu0jgjftbi3qnutn9gcejh7ohfgmsk2c7cnjc7ttmlj3bftpk/README.md) has the run steps and a map of the files. The task logic (add, edit, delete, move and saving) is all in [useTodos.js](vscode-webview://19flu0jgjftbi3qnutn9gcejh7ohfgmsk2c7cnjc7ttmlj3bftpk/src/hooks/useTodos.js), and each part of the screen has its own file under [src/components/](vscode-webview://19flu0jgjftbi3qnutn9gcejh7ohfgmsk2c7cnjc7ttmlj3bftpk/src/components/).

**To start it yourself later**, open a terminal in kanban-react and run:

npm run dev

The server I started stays on for this session. Stop it with Ctrl+C in its terminal, or ask me to stop it.

**Two things to know:**

-   Tasks are saved only in the browser you use. Moving them across devices would need a backend database, which I can add.
-   The plain HTML version in [../kanban-todo/](vscode-webview://19flu0jgjftbi3qnutn9gcejh7ohfgmsk2c7cnjc7ttmlj3bftpk/kanban-todo/) is still there. Delete it if you only want the React app.

Prompt:
I would like to change the color theme, Please consider the color theme of application from most trending web applications and styles. Please update the web application accordingly

While that is running open another chat and prompt:
Hey! Please can you use three deep dive agents to review your implementation? Please ensure that it is actually complete and that there aren’t any bugs or massive gaps in the solution.

And that’s how we can save time in reviewing it manually.

I had three review agents look at the kanban-react app, and the verdict is that it's complete but has a few real bugs. Every feature in the README is there. The production build succeeds with no warnings. None of the bugs is critical except one: bad saved data can break the app until storage is cleared. I didn't change any files.

Some files were edited by something outside this session at 21:40, while the reviews were running. I've rechecked the findings below against the current code. A "theme button does nothing" bug they reported is already fixed in those edits, so it's left out.

**Worth fixing (major)**

1.  **One bad saved task blanks the app on every load.** Two reviewers found this separately. [useTodos.js:19](vscode-webview://19flu0jgjftbi3qnutn9gcejh7ohfgmsk2c7cnjc7ttmlj3bftpk/src/hooks/useTodos.js#L19) accepts any saved list without checking the tasks in it.
    -   A task without tags makes [TaskCard.jsx:64](vscode-webview://19flu0jgjftbi3qnutn9gcejh7ohfgmsk2c7cnjc7ttmlj3bftpk/src/components/TaskCard.jsx#L64) crash. The bad data is then saved straight back, so it crashes again on every reload until you clear localStorage by hand.
    -   Two other cases: a task with an unknown column is saved but never shown, and duplicate ids lose tasks when you move them.
    -   Fix: check and repair each task as it loads.
2.  **The edit window can close and lose your changes.** The backdrop-click check at [TaskDialog.jsx:54-59](vscode-webview://19flu0jgjftbi3qnutn9gcejh7ohfgmsk2c7cnjc7ttmlj3bftpk/src/components/TaskDialog.jsx#L54-L59) causes this in two ways:
    -   Selecting text in the Title box and letting go outside the window closes it.
    -   Double-clicking ✎ opens the window and the second click closes it straight away.
    -   Fix: close only when both the mouse press and the release happen on the backdrop.
3.  **Keyboard users lose their place after Save, Cancel or Delete.** The window is removed from the page ([App.jsx:89](vscode-webview://19flu0jgjftbi3qnutn9gcejh7ohfgmsk2c7cnjc7ttmlj3bftpk/src/App.jsx#L89)) rather than closed, so the browser doesn't return focus to the card. The same happens after moving a card with ← →.
4.  **The priority labels are hard to read in light mode.** The colours are at [index.css:26-31](vscode-webview://19flu0jgjftbi3qnutn9gcejh7ohfgmsk2c7cnjc7ttmlj3bftpk/src/index.css#L26-L31). Medium (orange) has a contrast of 3.07:1, High 4.28 and Low 3.58, against the 4.5:1 standard for small text. Darker shades of the same colours would pass. Dark mode is fine.

**Minor**

-   **Title made of spaces:** it's rejected with no message, while the older kanban-todo version showed one. This is the only feature lost in the move to React.
-   **Double-clicking a tag:** it applies the tag filter and also opens the edit window ([TaskCard.jsx:23](vscode-webview://19flu0jgjftbi3qnutn9gcejh7ohfgmsk2c7cnjc7ttmlj3bftpk/src/components/TaskCard.jsx#L23)).
-   **Dropping on a column:** only the card area accepts drops ([Column.jsx:69-71](vscode-webview://19flu0jgjftbi3qnutn9gcejh7ohfgmsk2c7cnjc7ttmlj3bftpk/src/components/Column.jsx#L69-L71)), so a card dropped on a column's title snaps back.
-   **N shortcut:** e.key.toLowerCase() at [App.jsx:26](vscode-webview://19flu0jgjftbi3qnutn9gcejh7ohfgmsk2c7cnjc7ttmlj3bftpk/src/App.jsx#L26) can crash on browser autofill events.
-   **Searching for a tag:** searching #bug finds nothing, because tags are stored without the #.
-   **Saving:** a failed save isn't shown to the user, and two open tabs overwrite each other's changes.
-   **Vite:** version 5.4.11 has two security advisories that affect only the dev server. Updating to 5.4.21 or later fixes them.
-   **README:** it doesn't mention the new theme toggle or useTheme.js.

**Checked and found correct**

-   Drag-and-drop reordering is correct, including while a filter is on.
-   The ← → buttons are disabled at the first and last columns.
-   The N shortcut is ignored while typing and with Ctrl, Alt or Cmd held.
-   Add and edit don't leak values into each other.
-   No unsafe HTML: React escapes all user text.
-   Dark mode is complete, and the layout works at phone width.

Should I fix the four major items? They're small changes, about an hour together.

Prompt:
Can you please spin up 2 agents to fix all these issues identified. One agent should take care of critical, high issues. Another Agent should take care of medium, low issues
