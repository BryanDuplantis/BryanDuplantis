# Bryan Duplantis

I direct the agents; Claude writes the code.

Most of what I build lives in private repos — personal infrastructure I run daily, not portfolio pieces. The contribution graph is the real signal. Here's what's actually running.

It all runs on a Raspberry Pi in my house. brain-mcp, the capture pipeline, the scheduled jobs, the Discord alerting that pings me when something breaks — one ARM board pulling a few watts, running while I sleep. The Mac's just where I sit down to drive.

---

## What I'm building

### [brain-mcp](https://github.com/BryanDuplantis/brain-mcp)
A TypeScript MCP server, and the spine of everything. Notes, decisions, and session history land in a ChromaDB vector store with Voyage AI embeddings; Claude queries it semantically from any surface — iOS, claude.ai, Claude Code in Ghostty — reaching the Pi over Tailscale. I take credit for the idea; Claude takes the rest. Everything else is built on top of it.

### Capture Engine
Capture first, sort it out by machine. I throw a note at it, typed or spoken; Sonnet triages what it is — task, event, stray idea — writes it to a SQLite database on the Pi as the source of truth, then fans out: a Discord ping, a morning digest, an event on my Google Calendar. The piece I touch most after brain-mcp.

### [Concert Bloodhound](https://github.com/BryanDuplantis/concert-bloodhound)
Another TypeScript MCP server. Fetches Ticketmaster, JamBase, and civic event feeds in parallel, dedups by artist and date, returns one clean Zod-typed list — arena tours down to a kid's oboe recital in Marietta. No repeats, no made-up prices, no fake availability.

### Fog of War Room
A daily intelligence-briefing pipeline on the US–Iran war. A chain of subagents — orient, research, draft, finalize — hands off through brain-mcp captures so raw research never clogs the writing context; pulls 170-plus sources, flags confidence, renders to Markdown, and publishes to Substack behind a Cloudflare Access gate. Analyst discipline on the output; agentic pipeline on the build. [Read it here.](https://bryanduplantis.substack.com)

### Movie watchlist semantic search
I dumped nearly 300 films into it and Claude built a semantic search layer on top. I can search "that one where the toys think they're getting thrown out again" and actually land on Toy Story 5. That's the whole point.

### Jukebox Hero
A catalog of my CD collection where every disc gets a real dossier: who played on it, when it was cut, what it was up against. Built for the dossiers — but the way we set it up, it starts drawing lines between records too: a session player who turns up across the stack, a producer two decades apart.

### Surplus Rescue
Early MVP. Coordinates bulk food pickups: drivers, donors, destinations, timing. The one I most want to turn into something real.

### Apex Squad
Not code. A children's book I've been sketching — apex predators who, instead of competing, get along, each in their own way. Claude helped with the character sketches and bios. Underneath it runs a quieter thread: how to be present with what ends, and how to begin again.

---

## How I build

Claude Code, running in Ghostty. I'm the human in the loop — I make the calls and sign off on the architecture, what talks to what and why. Claude does the building. Nothing ships until it's passed a security review, versioned and local alike.

Stack across the active work: TypeScript, Python, MCP servers, ChromaDB, Voyage AI embeddings, Tailscale for the network layer, Discord for alerting.

---

## Before this

20+ years in broadcast television. Started at CNN during the OJ Simpson trial — was in the studio when the verdict was read. Later: NFL Network, the launch of FS1 (Mike Tyson in the control room), the Big Ten Network, teaching video production at Columbia College Chicago.

In March 2015 I changed lanes — Nashville Software School, Cohort 9 — and built a second career in enterprise tech and operations. A decade of it, most recently at Elevance Health.

---

## Find me

- [bryanduplantis.substack.com](https://bryanduplantis.substack.com) — Fog of War Room and whatever comes next
- [linkedin.com/in/bryanduplantis](https://linkedin.com/in/bryanduplantis)

---

*And before you ask: yes, Claude thinks this is a great profile. Claude thinks everything I do is a great idea. We're working on it.*
