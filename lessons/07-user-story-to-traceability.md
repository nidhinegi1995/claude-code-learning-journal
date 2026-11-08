# From User Story to Traceability with Agent Teams

In old flow we used an agent that was performing all tasks
but

In new flow we are using diff agents for each task which behaves like teammates for efficient results.

Claude Agents:

**Agent Teams: summary**

**What they are:** Agent teams let several Claude Code sessions work on one task together. Your main session becomes the **team lead**. It spawns **teammates**, hands out work and combines their results at the end. Each teammate is a full Claude Code session with its own context window. Teammates can message each other directly, and you can also talk to any teammate yourself.

⚠️ **This is experimental and turned off by default.** To turn it on, add this to settings.json:

{ "env": { "CLAUDE\_CODE\_EXPERIMENTAL\_AGENT\_TEAMS": "1" } }

Teams only work in interactive sessions. They don't work with -p (headless mode) or the Agent SDK.

**Agent teams vs. subagents**

|  |
**Subagents**

 |

**Agent teams**

 |
| --- | --- | --- |
|

Communication

 |

Send their result back to the main agent

 |

Teammates message each other directly

 |
|

Coordination

 |

The main agent manages all the work

 |

Teammates share a task list and pick up work themselves

 |
|

Best for

 |

Focused jobs where you only need the result

 |

Complex work that needs discussion and debate

 |
|

Token cost

 |

Lower

 |

Much higher (each teammate is a separate Claude)

 |

**Good uses:** parallel research or review, building separate modules, debugging by testing several theories at once, and changes that span frontend, backend and tests.
**Poor uses:** step-by-step work, several people editing the same file, or work where each piece depends on another.

**How to use them**

-   **Start a team** by asking in plain language, e.g. _"Spawn three teammates: one on UX, one on architecture, one playing devil's advocate."_ You can name the number of teammates, their models (_"use Sonnet for each"_) and their names.
-   **Agent panel** (below the prompt box): use ↑/↓ to pick a teammate, Enter to open it and message it, x to stop it, Ctrl+T to show the task list, and Esc to interrupt it.
-   **Display modes:**
    -   in-process (default) works in any terminal.
    -   Split panes need tmux or iTerm2. Set this with teammateMode in settings or the --teammate-mode flag.
    -   **Split panes don't work in VS Code's terminal or Windows Terminal**, so you'll be using in-process mode.
-   **Shared task list:** each task is pending, in progress or completed, and a task can depend on others. The lead can assign tasks, or teammates can claim the next one that isn't blocked.
-   **Plan first:** if you put the lead in plan mode and then spawn a teammate, the teammate plans before it writes any code.
-   **Reusing roles:** if you've defined subagents (e.g. security-reviewer), you can spawn teammates from those definitions.
-   **Hooks for quality checks:** TeammateIdle, TaskCreated and TaskCompleted. Exiting with code 2 blocks the action and sends feedback.
-   **Shutting down:** _"Ask the researcher teammate to shut down."_ Cleanup happens automatically.

**Permissions and context**

-   Teammates start with the lead's permission mode. You can't give each one a different mode when you spawn it.
-   Teammates' permission prompts show up in the lead's session.
-   Teammates load CLAUDE.md, MCP servers and skills, but **not** the lead's conversation history. Put all the context they need in the spawn prompt.
-   A teammate can't approve actions on your behalf.

**Best practices**

-   Start with **3–5 teammates** and about **5–6 tasks per teammate**.
-   Give each teammate its own files so they don't overwrite each other.
-   If you're new to teams, start with research or review tasks rather than code changes.
-   Check in on progress. If the lead starts doing the work itself, tell it: _"Wait for your teammates to finish."_

**Limitations**

-   /resume and /rewind don't bring back in-process teammates.
-   Task status can lag behind and block tasks that depend on it.
-   Shutdown can be slow.
-   Each session gets one team. Teammates can't create their own teams, and the lead can't be changed.
-   Teams use a lot of tokens, and the cost grows with each teammate.

**Rule of thumb:** use subagents when you only need results back, and agent teams when the workers need to talk to and challenge each other.

To enable agent Teams:

User Story:

**US-BILLPAY-01**

**User Story:** As a ParaBank customer, I want to pay a bill from my account by entering payee details and an amount, so that I can settle payments without visiting a branch.

**Acceptance Criteria:**

-   User can enter payee information: Payee Name, Address, City, State, Zip Code, Phone #
-   User can enter Account # and Verify Account # for the payee
-   User enters Amount and selects the From account # from a dropdown
-   On clicking **Send Payment**, the system processes the payment and shows a confirmation

Now our first team agent is story analyst – which will analyse the story as it doesn’t include negative cases etc. So it will analyse and reduce gap like actual tester.

Now we will create a new skill – excel-test-management.md

In short: **strict ownership per workbook, fixed schemas for consistency, enforced role-based updates, and ID-based linking for automation traceability.**

Now we will create a new agent – story-analyst-agent.md

In essence: it’s a **gap‑finder and clarifier** that ensures user stories are precise, assumptions are documented with sources, and downstream teams don’t have to guess.

Next agent we will create – test-author-agent.md

It take the output file from previous agent as input.

Automation engineer agent we already have from previous lessons.

Now agent we will create – execution-sync-agent.md

It **runs tests, syncs results into Excel, and ensures every failure is tracked as a defect**.

Now last agent we will create = traceability-agent.md

👉 In short: the Traceability Agent **consolidates all upstream QA data into a clear matrix, showing coverage and risk for each user story.**

Now install exceljs

Create a utility of excel.helper.ts

👉 In short: this utils script is a **bridge between Playwright test execution and Excel-based test management**, ensuring that test authors, automation engineers, and QA leads can collaborate seamlessly in one workbook.

Now check the output excel for the result
