# Lesson 1: Your Brand, In Claude's Head

**Time: ~20 min**

**You'll finish with:** A project folder open in Claude Code, a working `CLAUDE.md`, OpenRouter plugin installed, a `brand/brand-guidelines.md` document that defines your brand, and a `/brand` slash command.

---

## The moment you're in

You are here to build a Private Marketing Agency, an AI-powered system that does your marketing work for you. Research, planning, writing, design, video, landing pages, publishing. All connected.

In the next twenty minutes you will lay the foundation. You will create the project, set up the AI gateway that powers every agent in this course, and teach Claude who your brand is. Everything you build in the next seven lessons reads from what you create here.

Get this right and the rest of the course feels easy.

---

ACTION: Greet the student briefly. Do NOT recap the whole course or re-explain the marketing agency concept (the README covered that). Just confirm you are about to start Lesson 1, tell them the lesson takes about twenty minutes, and ask if they have the Claude Code desktop app open and ready.

If they say yes, continue to Step 1.

If they say no, walk them through opening the desktop app, then continue. Do not move on until they confirm Claude Code is open.

---

USER: [Waits for student to confirm Claude Code is open and ready]

---

## What you're going to do

1. Create a project folder called `marketing-agency`
2. Open that folder in Claude Code
3. Add a `CLAUDE.md` file with project context
4. Sign up for OpenRouter and install the OpenRouter plugin
5. Describe your brand to Claude
6. Generate your brand guidelines document
7. Create a `/brand` slash command

Go in order. Do not skip.

---

## Step 1: Create a project folder

On your machine, create a new folder somewhere you will remember. Documents is fine. Desktop is fine.

Name the folder exactly: `marketing-agency`

Lowercase. Hyphen, not space. You can do this in Finder or File Explorer. Right-click, New Folder, name it.

---

STOP: Tell me when you have created the `marketing-agency` folder and where you put it (Documents, Desktop, etc).

---

USER: [Waits for student to confirm folder created and tells you the location]

---

ACTION: When the student confirms:

1. If they used a different name (e.g. "Marketing Agency" with a space, "MarketingAgency", etc), ask them to rename it to `marketing-agency` exactly. Lowercase, hyphenated. Wait for them to rename before continuing.
2. If the folder name is correct, say "Good. Now let us open it in Claude Code."
3. Move on to Step 2.

---

## Step 2: Open the folder in Claude Code

In the Claude Code desktop app, choose "Open Folder" (the label may vary slightly by version).

Navigate to your `marketing-agency` folder. Select it.

You should now see Claude Code with the folder open. The left sidebar shows the folder name and an empty file tree. The chat input is at the bottom.

If a small notice appears asking whether to trust the folder, trust it. You created it.

---

STOP: Tell me when you have the `marketing-agency` folder open in Claude Code.

---

USER: [Waits for student to confirm folder is open in Claude Code]

---

ACTION: When the student confirms:

1. If they are having trouble opening the folder, troubleshoot: ask them what they see on screen and guide them through the "Open Folder" flow.
2. If the folder is open, say "Good. Now we will create the project's standing brief."
3. Move on to Step 3.

---

## Step 3: Create the project CLAUDE.md

### Why

Every Claude Code project has a file called `CLAUDE.md` at the root. Claude reads it at the start of every session. It is the standing brief that tells Claude what this project is, what it does, and how to work in it.

Without it, Claude starts every session with no context. With it, Claude knows what is going on immediately.

### What to do

Tell Claude to create a file called `CLAUDE.md` at the root of your project with this content:

```markdown
# Marketing Agency

This is a Private Marketing Agency project. It contains AI agents that handle marketing tasks for a brand.

## What this project does

This project uses Claude Code skills and MCP integrations to:
- Research trending content topics in the brand's niche
- Plan a monthly content calendar
- Write content (social posts, articles, video scripts) in the brand's voice
- Generate brand-consistent visual designs
- Produce AI avatar videos
- Build and deploy landing pages
- Format content for publishing across platforms

## Key files

- `brand/brand-guidelines.md` contains the brand voice, visual identity, audience, and content pillars. Every skill reads this file.
- `research/` contains research outputs from the content researcher.
- `content/` contains written content pieces.
- `designs/` contains generated visual designs.
- `landing-page/` contains the landing page HTML and CSS.

## Integrations

- **OpenRouter Plugin** for accessing AI models (image generation, model discovery)
- **NocoDB MCP** for the content calendar database
- **HeyGen MCP** for AI avatar video production
- **Vercel MCP** for deploying the landing page
```

---

STOP: Ask Claude "What is this project about?" If it answers with something about a marketing agency and AI agents, the CLAUDE.md is working. Tell me what Claude said.

---

USER: [Waits for student to confirm Claude reads the CLAUDE.md correctly]

---

ACTION: When the student confirms:

1. If Claude gave a correct summary about a marketing agency project, say "Good. Claude now knows what this project is every time you open it."
2. If Claude seemed confused or did not mention the marketing agency, check that CLAUDE.md is at the root of the folder (not inside a subfolder). Have them verify the file exists and is named exactly `CLAUDE.md` (capital C, capital L, capital A, capital U, capital D, capital E).
3. Move on to Step 4.

---

## Step 4: Set up OpenRouter Plugin

### Why

Throughout this course, you will use AI models for different jobs: image generation models to create visuals, and model discovery to find the right AI for each task. Instead of signing up for each AI service separately, OpenRouter gives you one account that accesses hundreds of models. Think of it as a single key that opens many doors.

OpenRouter is installed as a **plugin** (a set of skills that auto-load in Claude Code), not an MCP server.

### What to do

**4a. Create your OpenRouter account**

1. Open your browser and go to `openrouter.ai`
2. Click "Sign Up" or "Get Started"
3. Create an account with your email or Google account
4. Once signed in, go to `openrouter.ai/keys`
5. Click "Create Key"
6. Give it a name like "Marketing Agency"
7. Copy the key. You will only see it once. Paste it somewhere safe temporarily (a note, a text file, anywhere you can grab it in a moment).

**4b. Add credits to OpenRouter**

Go to `openrouter.ai/credits` in your browser. Add a small amount of credits ($5 is plenty for this entire course). This pays for the AI model calls you will make in Lesson 5 (image generation).

**4c. Install the OpenRouter plugin in Claude Code**

In the Claude Code chat, type this command:

```
claude skill install --github OpenRouterTeam/skills
```

This installs the OpenRouter skills plugin which gives Claude access to:
- **Image generation** (creating visuals from text prompts)
- **Model discovery** (finding and comparing AI models)
- **Video generation** (creating AI videos from prompts)

**4d. Set the API key**

Claude Code needs your OpenRouter API key as an environment variable. Set it by adding it to your shell profile or project configuration.

Ask Claude to help you set the environment variable:

"Set the OPENROUTER_API_KEY environment variable to [paste your key]"

Claude will guide you through adding it to the right place based on your operating system.

---

STOP: Test if OpenRouter is working. Ask Claude: "Generate a simple test image of a blue circle on a white background using OpenRouter." If an image file is created, the plugin is working. Tell me what happened.

---

USER: [Waits for student to confirm OpenRouter plugin is working]

---

ACTION: When the student responds:

1. If an image was generated successfully, say "Good. OpenRouter is working. You now have access to image generation and model discovery. We will use image generation in Lesson 5 to create brand visuals."
2. If they get an error:
   - If it says "OPENROUTER_API_KEY not set", help them set the environment variable. On Mac: `export OPENROUTER_API_KEY=their-key`. On Windows: set it in System Environment Variables.
   - If it says "insufficient credits", go to openrouter.ai/credits and add credits.
   - If the plugin did not install, make sure Claude Code CLI is available. Try running `claude skill install --github OpenRouterTeam/skills` directly in your terminal.
   - If they get a "npm install" or "node" error, they need Node.js installed. Walk them through installing Node.js from nodejs.org.
3. Do not move on until OpenRouter is working.

---

## Step 5: Describe your brand

### Why

Everything you build in this course references your brand. The research agent looks for topics in your niche. The writer uses your voice. The designer uses your colors. If Claude does not know your brand, every output will be generic.

### What to do

Tell Claude about your brand. Answer these questions in the chat:

1. **What is your business name?**
2. **What do you sell or offer?** (Products, services, or both. Be specific.)
3. **Who is your ideal customer?** (Age range, interests, what problem you solve for them.)
4. **Describe your brand personality in 3 adjectives.** (Example: "professional, warm, straightforward" or "bold, playful, edgy")
5. **What colors does your brand use?** (If you are not sure, name colors you like or brands whose look you admire.)
6. **Name 1-2 brands whose style you admire.** (Not competitors necessarily. Brands whose marketing you think "that is the vibe I want.")

Take your time. This is the most important input in the whole course. Everything else builds on it.

---

STOP: Share your brand details with me now. Answer the six questions above. There are no wrong answers. This is about YOUR brand.

---

USER: [Waits for student to share their brand details]

---

ACTION: When the student shares their brand details:

1. Acknowledge what they shared. Repeat back the key points briefly: "So [business name] sells [what they sell] to [their audience], with a [their adjectives] personality. [Colors]. Inspired by [brands they admire]."
2. If any answers are vague (e.g. "everyone" for audience), ask one follow-up question to make it more specific.
3. Once you have enough detail, say "Good. Let me turn this into your brand guidelines."
4. Move on to Step 6.

---

## Step 6: Generate brand guidelines

### Why

The brand guidelines document is the single most important file in this project. Every skill you build reads it. The researcher uses the content pillars to know what topics to look for. The writer uses the voice section to match your tone. The designer uses the visual identity for colors and style. If this document is wrong, everything downstream is wrong.

### What to do

Create a folder called `brand/` at the root of the project. Inside it, create a file called `brand-guidelines.md`.

Generate the brand guidelines based on everything the student just told you. The file should have these sections:

```markdown
# Brand Guidelines: [Business Name]

## Brand Voice

### Tone
[2-3 sentences describing how the brand sounds. Example: "Conversational and direct. We speak like a knowledgeable friend, not a corporate brochure. We use simple language and avoid jargon unless our audience uses it naturally."]

### Vocabulary
[Words and phrases the brand uses. Words and phrases the brand avoids.]

### What to avoid
[Specific things the brand should never sound like. Example: "Never use pushy sales language. Never use corporate buzzwords like 'synergy' or 'leverage'."]

## Visual Identity

### Colors
- Primary: [color with hex code]
- Secondary: [color with hex code]
- Accent: [color with hex code]
- Background: [color]
- Text: [color]

### Style direction
[2-3 sentences. Example: "Clean and modern. Lots of white space. Photography style: natural lighting, real people, not stock photos. Graphics: simple, geometric, flat design."]

### Typography guidance
[Font style preferences. Example: "Sans-serif for headings, clean and bold. Body text should be highly readable."]

## Target Audience

### Demographics
[Age, location, profession, income level if relevant]

### Pain points
[3-5 specific problems they face that the brand solves]

### What they care about
[3-5 things they value, follow, or spend time on]

## Content Pillars

[3-5 themes the brand should consistently create content about. Each pillar gets a name and a one-sentence description.]

1. **[Pillar Name]** - [Description]
2. **[Pillar Name]** - [Description]
3. **[Pillar Name]** - [Description]
```

Fill this in using the student's brand details. Make it specific to their business, not generic. If you need to make educated guesses about hex codes or audience details, make them based on the brands they admire and the personality they described.

---

STOP: I just generated your brand guidelines. Read back the **Brand Voice** section. Does it sound like YOUR brand? If something feels off, tell me what to change.

---

USER: [Waits for student to review the brand voice section]

---

ACTION: When the student reviews:

1. If they say it sounds right, say "Good. Let us check the content pillars next."
2. If they want changes, make the adjustments immediately. Ask them to read the updated version. Repeat until they are happy with it.
3. Move on to checking the content pillars.

---

STOP: Now read the **Content Pillars** section. Are these topics you would actually post about? If one feels wrong or something is missing, tell me.

---

USER: [Waits for student to review the content pillars]

---

ACTION: When the student reviews:

1. If they are happy with the pillars, say "Good. These pillars will drive everything: what we research, what we plan, what we write."
2. If they want changes, adjust the pillars. The content pillars are important because the researcher agent in Lesson 2 will use them to find topics.
3. Move on to Step 7.

---

## Step 7: Create the /brand slash command

### Why

Right now, if you want to update your brand guidelines, you have to explain the whole process to Claude again. A slash command lets you type `/brand` and Claude knows exactly what to do: ask you the brand questions, then regenerate or update the guidelines file.

### What to do

Create a folder at `.claude/commands/` (if it does not already exist). Inside it, create a file called `brand.md` with this content:

```markdown
# Update Brand Guidelines

Read the current brand guidelines at `brand/brand-guidelines.md`.

Ask the user what they want to change about their brand. This could be:
- Updated brand voice or tone
- New or changed colors
- Updated audience description
- New content pillars or changed existing ones
- Any other brand detail

After they tell you what to change, update `brand/brand-guidelines.md` with the changes. Keep everything else the same.

Read back the changed sections so the user can confirm.
```

Note: the `.claude` folder starts with a dot, which means it is a hidden folder on your computer. You will not see it in Finder or File Explorer by default, but Claude Code can see it and create files in it.

---

STOP: Type `/brand` in the chat. Does Claude respond by asking what you want to change about your brand? Tell me what happened.

---

USER: [Waits for student to confirm the slash command works]

---

ACTION: When the student confirms:

1. If the slash command works and Claude asks about brand changes, say "Good. You can use this anytime your brand evolves. The guidelines file stays up to date and every agent reads the latest version."
2. If it did not work:
   - Check that the file is at `.claude/commands/brand.md` exactly.
   - Check that the `.claude` folder is at the root of `marketing-agency`, not inside another folder.
   - The slash command should appear when they type `/` in the chat input.
3. Do not move on until the slash command works.

---

## End-of-lesson check

- Your `marketing-agency` folder is open in Claude Code
- `CLAUDE.md` exists at the root and Claude can describe the project
- OpenRouter plugin is installed and working
- `brand/brand-guidelines.md` exists with your brand's voice, visual identity, audience, and content pillars
- The `/brand` slash command works

---

## Common stumbles

- **"The OpenRouter plugin did not install"** -- Open a terminal and run `claude skill install --github OpenRouterTeam/skills` directly. Make sure Claude Code CLI is installed and you are logged in.
- **"OpenRouter says invalid API key"** -- Go back to openrouter.ai/keys and create a new key. Make sure you copy the full key including the `sk-or-` prefix.
- **"OPENROUTER_API_KEY not found"** -- The environment variable needs to be set. On Mac, add `export OPENROUTER_API_KEY=your-key` to your `~/.zshrc` file. On Windows, add it to System Environment Variables. After setting it, restart Claude Code.
- **"I do not know what hex codes to use for my colors"** -- That is fine. Describe the colors in words ("dark navy blue", "warm orange") and Claude will pick appropriate hex codes.
- **"My brand guidelines sound too generic"** -- Be more specific in your brand description. Instead of "professional", say "professional like a trusted financial advisor, not professional like a law firm." The more specific your input, the more specific the output.

---

## What just happened

You created the foundation that every other lesson builds on. The `CLAUDE.md` gives Claude project context. The OpenRouter plugin gives Claude access to image generation and model discovery. The brand guidelines tell every agent who your brand is and how to create content that sounds and looks like you.

In the next lesson, you will use that foundation to build a research agent that finds trending topics and competitor content in your niche.

---

## When you're ready

Type: **Start Lesson 2**

You will build a research agent that uses web search to find what your audience is talking about right now.

---

ACTION: When the student says they are ready for Lesson 2, read the file at `lesson-modules/2-researcher-agent/CLAUDE.md` and begin.
