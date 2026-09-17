# Bryan Duplantis

I direct the agents. Claude writes the code.

Most of what I build lives in private repos, because it's infrastructure I actually run rather than portfolio work. It all sits on a Raspberry Pi in my house: 16 services, 15 cron jobs, and the Discord alerts that tell me when one of them broke. The Mac is just where I sit down to drive.

Atlanta, GA. [LinkedIn](https://linkedin.com/in/bryanduplantis) · [duplantis@gmail.com](mailto:duplantis@gmail.com)

## Start here

[**Claude Code Starter Kit**](https://github.com/BryanDuplantis/claude-code-starter-kit) is the only thing on this page you can pick up and use today. Public, MIT, aimed at people who aren't developers, because every other kit I found assumes you already know what a terminal is.

It's deliberately not an installer. Claude Code's own setup takes ten minutes and doing it by hand is the first real lesson. What the kit adds is the part nobody teaches: house rules Claude reads every session, a running log of what tripped you up, the handful of security rules that matter on day one, and a practice project to break before you point it at anything you care about. Setup was never the hard part. The habits are.

## What's running

**brain-mcp** is a TypeScript MCP server and the floor everything else stands on. Notes, decisions, and session history go into a ChromaDB vector store embedded with Voyage AI, so Claude searches them by meaning instead of keyword, about 1,100 captures so far. I reach it from the iOS app, claude.ai, and Claude Code in the terminal, all talking back to the Pi over a private network and never the open internet. The repo is private, so there's nothing to click here.

**Capture Engine** is what I touch most after that. I throw a note at it, typed or spoken, Sonnet works out whether it's a task, an event, or a stray idea, and a Pydantic schema validates the answer before anything downstream trusts it. SQLite on the Pi holds the real copy. From there: a Discord ping, a line in the morning digest, an event on my calendar.

[**Concert Bloodhound**](https://github.com/BryanDuplantis/concert-bloodhound) is another MCP server, public this time. Nothing out there listed everything from arena tours down to a kid's oboe recital in Marietta, so this pulls Ticketmaster, JamBase, and civic feeds at once, drops the duplicates, and hands back one typed list. No repeats, no invented prices.

**Fog of War Room** is a day-by-day brief on the US and Iran war, 191 days of it, written from my own outlines and source pile. The part worth talking about is the build: a chain of subagents (orient, research, draft, publish) that hand off through brain-mcp instead of one long conversation, so the raw research never crowds out the writing. Renders to HTML and publishes behind a Cloudflare Access gate.

**Underneath all of it** sit 53 skills and 15 scoped subagents in my Claude Code config, which is where most of this year's work actually went. A subagent's tool list is its security boundary, not a paragraph of instructions, so the agents that read the open web hold no shell and can't write anywhere.

Also in the mix: a Discord command router with a persisted circuit breaker that trips on billing-wall signals, so a runaway loop can't bill twice. Live match desks for the US Open, F1 race weekends, and Champions League nights, rendering to a Pi kiosk and my screensaver. College football briefs. A semantic search layer over 300 films, so "that one where the toys think they're getting thrown out again" lands on the right movie.

## How I verify

Exit code 0 means nothing. Almost every failure I've hit was silent: a cron job exits clean and does nothing, a config file is present and readable and points at a webhook that was deleted last month, a deploy reports success and writes to the wrong path.

So most of my work now is designing the signal that proves something happened. My deploy script restarts the service, then POSTs an authenticated request and greps the response body for a known field, because a GET returns 401 and proves nothing.

- Ask the running process what it believes, not the file on disk. They disagree more often than you'd think.
- A missing error is not a result. If a check can't fail interestingly, it isn't a check.
- Control test the thing that should fail. A guard whose failure path has never run is the same as no guard.
- Write down the falsifier, not just the symptom. A diagnosis ages faster than the bug it explains.

That last one covers the model too. Confident and wrong is the failure mode that walks past every safety net keyed to uncertainty. I keep a written registry of these, 81 entries and counting, each one something that fooled me exactly once.

## Security

- Secrets never touch the chat, the command line, or git history. They go from my clipboard to a vault on the Pi over stdin, so the model never sees the value.
- Least privilege by default. Read-only scopes unless a write is actually needed, and the agent's shell is allowlisted to named commands rather than handed the keys.
- Anything on the web sits behind an access gate, and I check the lock from a signed-out session, because my own logged-in view is the one guaranteed not to match a visitor's.

## Before this

Nearly ten years in healthcare systems. I was lead production support engineer for an AWS-hosted palliative care EMR across its full lifecycle, from rollout through nine years of multi-state clinical operations to its 2025 retirement and data migration to Epic, and I led that platform's support function off a standalone tool onto Elevance's enterprise ServiceNow instance. Later, backend systems and data platforms at Carelon. All of it under HIPAA controls. Before that, multi-client EHR implementations on NextGen and PrimeSUITE.

Before *that*, twenty years in broadcast television operations and real-time graphics engineering. Started at CNN during the OJ Simpson trial, in the studio when the verdict was read. Later the FS1 launch team (Mike Tyson in the control room), NFL Network, Big Ten Network, and Fox 32 Chicago. I also taught video for internet and mobile TV at Columbia College Chicago for seven years.

In March 2015 I changed lanes: Nashville Software School, Cohort 9.

## Find me

[linkedin.com/in/bryanduplantis](https://linkedin.com/in/bryanduplantis) · [duplantis@gmail.com](mailto:duplantis@gmail.com)

---

*And before you ask: yes, Claude thinks this is a great profile. Claude thinks everything I do is a great idea. We're working on it.*
