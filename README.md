# Bryan Duplantis

I direct the agents; Claude writes the code.

Most of what I build lives in private repos. Personal infrastructure I run daily, not portfolio pieces. The contribution graph is the real signal. Here's what's actually running.

It all runs on a Raspberry Pi in my house. brain-mcp, the capture pipeline, the cron jobs, the Discord alerts that tell me when something broke. One little ARM board pulling a few watts, running while I sleep. The Mac is just where I sit down to drive.

---

## What I'm building

### [brain-mcp](https://github.com/BryanDuplantis/brain-mcp)
A TypeScript MCP server. It holds my notes, decisions, and session history in a ChromaDB vector store, embedded with Voyage AI, so Claude searches them by meaning instead of keyword. I can reach it from anywhere I work: the iOS app, claude.ai, Claude Code in Ghostty, all talking back to the Pi over a private network, never the open internet. I take credit for the idea; Claude takes the rest. Everything else is built on top of it.

### Glossary of terms
A running glossary of the terms Claude and I land on while we build: names for the failure modes that keep recurring, the concepts worth a shorthand, the lessons that earned a label. When something burns us once, it goes in here so it can't do it quietly again. It's the teaching and the learning written down, mine and the model's both.

### Capture Engine
The thing I touch most after brain-mcp. I throw a note at it, typed or spoken, and Sonnet works out what it is (a task, an event, a stray idea) and files it. SQLite on the Pi holds the real copy. From there it handles the rest: a Discord ping, a line in the morning digest, an event on my calendar. I never have to stop and decide where it goes.

### [Concert Bloodhound](https://github.com/BryanDuplantis/concert-bloodhound)
Another MCP server, in TypeScript. I couldn't find one place that listed everything from arena tours down to a kid's oboe recital in Marietta, so I built it. It pulls Ticketmaster, JamBase, and civic feeds at the same time, drops the duplicates, and hands back one clean typed list. No repeats, no made-up prices, no fake availability.

### Fog of War Room
A daily intelligence briefing on the war between the US and Iran. It runs as a chain of subagents (orient, research, draft, finalize) that hand off through brain-mcp captures, so the raw research never crowds out the writing. It pulls from 170-plus sources, flags how sure it is on each, renders to Markdown, and publishes to Substack behind an access gate. Analyst-grade discipline on the output; agentic pipeline on the build. [Read it here.](https://bryanduplantis.substack.com)

### Movie watchlist semantic search
I dumped nearly 300 films into it and Claude built a semantic search layer on top. I can search "that one where the toys think they're getting thrown out again" and actually land on Toy Story 5. That's the whole point.

### Jukebox Hero
A catalog of my CD collection where every disc gets a real dossier: who played on it, when it was cut, what it was up against. I built it for the dossiers, but the way it's set up it started drawing lines between records on its own. A session player who keeps turning up across the stack, a producer who shows up two decades apart.

### Surplus Rescue
Early MVP. Coordinates bulk food pickups: drivers, donors, destinations, timing. The one I most want to turn into something real.

### Apex Squad
Not code. A children's book I've been sketching. Apex predators who get along instead of competing, each in their own way. Claude helped with the character sketches and bios. Underneath it runs a quieter thread: how to be present with what ends, and how to begin again.

---

## How I build

Claude Code, running in Ghostty. I'm the human in the loop. I make the calls and sign off on the architecture, what talks to what and why. Claude does the building.

Stack across the active work: TypeScript, Python, MCP servers, ChromaDB, Voyage AI embeddings, Discord for alerting.

---

## Security

Nothing ships until it passes a security review, scoped to whatever that change can actually reach. A few rules that don't bend:

- Secrets never touch the chat, the command line, or git history. They go from my clipboard to a vault on the Pi over stdin, so the model never sees the value.
- Least privilege by default: read-only scopes unless a write is genuinely needed, and the agent's shell is allowlisted to specific commands, not handed the keys.
- Anything that goes on the web sits behind an access gate, and I check the lock is on before I call it done.

---

## Before this

20+ years in broadcast television. Started at CNN during the OJ Simpson trial, in the studio when the verdict was read. Later: NFL Network, the launch of FS1 (Mike Tyson in the control room), the Big Ten Network, teaching video production at Columbia College Chicago.

In March 2015 I changed lanes. Nashville Software School, Cohort 9, and a second career in enterprise tech and operations. A decade of it, most recently at Elevance Health.

---

## Find me

- [bryanduplantis.substack.com](https://bryanduplantis.substack.com): Fog of War Room and whatever comes next
- [linkedin.com/in/bryanduplantis](https://linkedin.com/in/bryanduplantis)

---

*And before you ask: yes, Claude thinks this is a great profile. Claude thinks everything I do is a great idea. We're working on it.*
