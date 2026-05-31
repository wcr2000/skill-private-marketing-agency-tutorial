# Private Marketing Agency Blueprint - Course Plan

**Target Audience:** SME owners and solopreneurs who do their own marketing, have Claude Code installed, and want to build a real AI-powered marketing system in one focused session.

---

## Course Overview

**Mission:** In about 2.5 hours, take a student from "I do all my marketing by hand" to "I have 8 connected AI agents that research, plan, write, design, produce video, build a landing page, and format content for publishing, all running from my Claude Code."

**Core Philosophy:**

- One real marketing system, end to end. Not toy examples.
- Every agent does one real job and connects to the next.
- The student finishes with proof, not knowledge. Real content for THEIR brand, in THEIR calendar, with THEIR visuals, on a live URL.
- No coding experience required. Claude Code does the heavy lifting.
- The scenario is the student's own business. Every output is immediately useful.

**Deliverables:**

- Working `marketing-agency` project folder
- `CLAUDE.md` and brand guidelines document
- OpenRouter plugin connected (unified AI gateway)
- Content researcher skill via web search
- NocoDB content calendar with a month of planned content
- Content writer skill producing brand-voice copy
- Content designer skill generating brand-consistent visuals via OpenRouter plugin
- HeyGen video with AI avatar presenter
- Landing page deployed to Vercel
- Master `/content-engine` slash command

---

## The Scenario

The scenario is the student themselves. Each lesson opens by putting the student in the moment of building their marketing system. The framing is "you are about to build X" and "in a minute you will see Y appear."

This works because:

1. SME owners are motivated by solving their own marketing problem. Building for a fictional company wastes that energy.
2. Every output (brand guidelines, content calendar, written posts, visuals) is immediately useful for their real business.
3. They can show the results to a business partner or team member and say "look what I built for us."

---

## Lesson Structure

### Lesson 1: Your Brand, In Claude's Head (~20 min)

**What they build:**

- `marketing-agency` project folder open in Claude Code
- `CLAUDE.md` at the project root
- OpenRouter account and plugin installed
- `brand/brand-guidelines.md` with voice, visual identity, audience, content pillars
- `.claude/commands/brand.md` slash command

**What they learn:**

- How a Claude Code project is structured
- Why CLAUDE.md is the standing brief Claude reads every session
- How OpenRouter plugin gives Claude access to image generation and model discovery through one account
- How brand context shapes every output from every agent

**End-of-lesson check:**

1. CLAUDE.md exists and Claude can describe the project
2. OpenRouter plugin is installed and working
3. Brand guidelines document reads like their actual brand

---

### Lesson 2: Your Research Team (~20 min)

**What they build:**

- `.claude/skills/content-researcher/SKILL.md`
- Research output for one content pillar saved to `research/`
- `.claude/commands/research.md` slash command

**What they learn:**

- What a skill is and how it teaches Claude how YOU want a job done
- How web search finds trending topics and audience insights
- How research agents find trends, competitor angles, and audience questions

**End-of-lesson check:**

- Research file exists with relevant trending topics for their niche

---

### Lesson 3: A Month of Content, Planned (~20 min)

**What they build:**

- NocoDB account and MCP connected
- Content Calendar table with the right fields
- `.claude/skills/content-calendar/SKILL.md`
- 20+ content entries in NocoDB

**What they learn:**

- What an MCP is and how it gives Claude access to systems outside the file tree
- How to structure a content calendar for multi-platform marketing
- How AI turns research into a planned content strategy

**End-of-lesson check:**

- NocoDB table visible in browser with 20+ entries, covering multiple platforms and formats

---

### Lesson 4: Words That Sound Like You (~15 min)

**What they build:**

- `.claude/skills/content-writer/SKILL.md`
- Three content pieces in `content/` (social post, article, video script)
- NocoDB entries updated to "drafted"

**What they learn:**

- How brand guidelines make AI writing sound like YOUR brand, not generic marketing
- How different content formats (social, long-form, video) need different approaches
- How skills and MCPs work together (skill writes, MCP updates the calendar)

**End-of-lesson check:**

- Three content files that sound like the student's brand, not generic AI output

---

### Lesson 5: Visuals Without a Designer (~20 min)

**What they build:**

- `.claude/skills/content-designer/SKILL.md`
- Two brand-consistent images in `designs/`
- NocoDB entries updated to "designed"

**What they learn:**

- How to generate images that match a brand's visual identity
- How the same OpenRouter plugin (from Lesson 1) accesses image generation models
- How detailed prompts with brand constraints produce consistent visuals

**End-of-lesson check:**

- Two images that match the brand colors and style

---

### Lesson 6: Your AI Video Team (~20 min)

**What they build:**

- HeyGen account and MCP connected
- `.claude/skills/video-maker/SKILL.md`
- One completed video with an AI avatar

**What they learn:**

- How HeyGen MCP gives Claude access to video production
- How a video script from the writer becomes a produced video
- The pattern of connecting a new MCP (avatar selection, voice selection, rendering)

**End-of-lesson check:**

- A video exists, the avatar speaks the script, and the student can watch it

---

### Lesson 7: A Page on the Internet (~20 min)

**What they build:**

- Vercel account and MCP connected
- `landing-page/index.html` and `styles.css`
- Live `*.vercel.app` URL

**What they learn:**

- That Claude Code can build a full web page from brand context and content
- The deploy loop (build, preview, deploy, get URL)
- That live URL on the internet feeling

**End-of-lesson check:**

- The URL opens on a device that is not their laptop and shows their brand

---

### Lesson 8: Ship It, Then What (~15 min)

**What they build:**

- `.claude/skills/content-publisher/SKILL.md`
- Master `.claude/commands/content-engine.md` slash command
- Platform-formatted content ready to post

**What it covers:**

- The full chain running end to end in one command
- Three real adaptations (client onboarding, product launch, seasonal campaigns)
- Honest list of what is missing
- One specific idea for what to build next

**Deliverable:**

- Confidence that they can operate and extend the system, plus three concrete ideas for what to build next.

---

## Teaching Methodology

**Interactive, conversational.**

- No videos. No passive watching.
- Student opens the project folder in Claude Code and types "Start Lesson 1"
- Claude reads the lesson CLAUDE.md and becomes the live instructor
- STOP / USER / ACTION blocks pace the conversation
- Student does the work themselves at every step

**Each lesson includes:**

- A grounded scenario opener ("you are about to build X")
- Numbered build steps with clear instructions
- STOP blocks at every meaningful checkpoint
- USER blocks showing the expected response shape
- ACTION blocks with conditional branches based on student input
- Common-stumble guidance for predictable issues
- Clean handoff to the next lesson

---

## Technical Requirements

**Required:**

- Claude Code desktop app installed and signed in
- A brand or business to market
- About 2.5 hours (can be split across sessions)

**Set up during the course:**

- OpenRouter account and plugin (Lesson 1, covers image generation for Lesson 5)
- NocoDB account and MCP (Lesson 3)
- HeyGen account and MCP (Lesson 6)
- Vercel account and MCP (Lesson 7)

**Not required:**

- Coding experience
- Design or video production experience
- Git, npm, or terminal knowledge
- A paid Claude plan
- A domain or hosting setup

---

## Student Deliverables

### By the end of Lesson 1:

- [ ] `marketing-agency` folder open in Claude Code
- [ ] `CLAUDE.md` at project root
- [ ] OpenRouter plugin installed and working
- [ ] `brand/brand-guidelines.md` with voice, visuals, audience, pillars
- [ ] `.claude/commands/brand.md` slash command

### By the end of Lesson 2:

- [ ] `.claude/skills/content-researcher/SKILL.md`
- [ ] Research output in `research/` folder
- [ ] `.claude/commands/research.md` slash command

### By the end of Lesson 3:

- [ ] NocoDB MCP connected
- [ ] Content Calendar table with correct fields
- [ ] 20+ content entries in NocoDB

### By the end of Lesson 4:

- [ ] `.claude/skills/content-writer/SKILL.md`
- [ ] Three content files in `content/`
- [ ] NocoDB entries updated to "drafted"

### By the end of Lesson 5:

- [ ] `.claude/skills/content-designer/SKILL.md`
- [ ] Two images in `designs/`
- [ ] NocoDB entries updated to "designed"

### By the end of Lesson 6:

- [ ] HeyGen MCP connected
- [ ] One completed video
- [ ] `.claude/skills/video-maker/SKILL.md`

### By the end of Lesson 7:

- [ ] Vercel MCP connected
- [ ] `landing-page/index.html` and `styles.css`
- [ ] Live `*.vercel.app` URL

### By the end of Lesson 8:

- [ ] `.claude/skills/content-publisher/SKILL.md`
- [ ] Master `.claude/commands/content-engine.md`
- [ ] Three concrete ideas for what to build next

---

## Key Concepts Taught

**Claude Code core concepts:**

- CLAUDE.md as standing project context
- Slash commands for repeated prompts
- Skills for "how I want this job done"
- MCPs for accessing systems outside the file tree (NocoDB, HeyGen, Vercel)
- Plugins for AI model access (OpenRouter for image generation and model discovery)

**Marketing automation concepts:**

- Brand guidelines as AI context
- Research-driven content strategy
- Multi-platform content planning
- Brand-voice AI writing
- Brand-consistent AI image generation
- AI video production
- Code-free web development
- Content formatting for publishing

---

## Notes for Maintenance

- OpenRouter's available models change. The skills should use the OpenRouter models plugin to discover current image-capable models rather than hardcoding specific model IDs.
- NocoDB's UI changes occasionally. The MCP handles the API layer, so UI changes rarely affect the lesson.
- HeyGen avatar and voice availability changes. The lesson has students pick from whatever is currently available rather than hardcoding specific options.
- Vercel's deployment UI changes between versions. The MCP path is more stable than the web UI path.
