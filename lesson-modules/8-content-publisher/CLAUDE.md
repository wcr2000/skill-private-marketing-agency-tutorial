# Lesson 8: Ship It, Then What

**Time: ~15 min**

**You'll finish with:** A content publisher skill, a master `/content-engine` command that chains your agents together, and a clear picture of what you built, what is missing, and what to build next.

---

## The moment you're in

You started this course with Claude Code installed and a brand you wanted to market. About two hours later you have eight connected capabilities: brand guidelines, a research agent, a content calendar in NocoDB, a writer that matches your voice, a designer that matches your style, a video maker with an AI presenter, and a landing page on the internet.

That is a lot. Before you go off and use this system, this lesson does three things: builds the publisher skill, connects everything into one command, and helps you decide what to do next.

---

ACTION: Greet the student and confirm Lesson 7 is done. Specifically check:

1. Do they have a live `*.vercel.app` URL that loads?
2. Does the landing page show their brand?

If yes, acknowledge it briefly (one sentence, no motivational filler) and say "Two more things to build, then we wrap up."

If no, send them back to Lesson 7 to fix it before doing the wrap-up.

---

USER: [Waits for student to confirm Lesson 7 is done]

---

## What you're going to do

1. Create a content publisher skill
2. Create the master `/content-engine` command
3. Run the master command
4. Review what you built
5. Look at three real adaptations
6. Decide what to build next

Go in order.

---

## Step 1: Create the content publisher skill

### Why

You have content written, designed, and ready. But posting to Instagram, Facebook, LinkedIn, or YouTube each has different requirements: different image sizes, different caption lengths, different hashtag rules. The publisher formats your content for each platform so you can copy-paste it directly.

### What to do

Create the skill file at `.claude/skills/content-publisher/SKILL.md` with this content:

```markdown
# Content Publisher

## Purpose
Format content pieces for publishing on specific platforms. Produce copy-paste-ready output for each platform.

## Inputs
- Content files from `content/` folder
- Design files from `designs/` folder
- NocoDB Content Calendar entries with Status = "Designed" or "Drafted"

## Process

1. Read the content piece from `content/`.
2. Read the NocoDB entry for platform and format information.
3. Format the content according to platform requirements:

### Instagram
- Caption: under 2200 characters
- First line is the hook (shows before "more")
- Hashtags: 5-15 relevant hashtags at the end
- Image specs: 1080x1080 (post), 1080x1920 (story/reel)
- Output: caption text ready to paste into Instagram

### Facebook
- Post text: no character limit but 100-250 words performs best
- Can include links (unlike Instagram)
- Minimal hashtags (0-3)
- Image specs: 1200x630
- Output: post text ready to paste into Facebook

### LinkedIn
- Post text: under 3000 characters
- Professional tone (adjusted from brand voice if needed)
- 3-5 hashtags
- Image specs: 1200x627
- Output: post text ready to paste into LinkedIn

### YouTube
- Title: under 100 characters, keyword-rich
- Description: 200-500 words with keywords, timestamps, and links
- Tags: 10-15 relevant tags
- Thumbnail specs: 1280x720
- Output: title, description, and tags ready to paste into YouTube Studio

### Blog
- Full HTML or markdown ready to paste into a CMS
- SEO meta description (155 characters)
- Suggested URL slug
- Output: article with metadata

4. Save the formatted output to `publish/[platform]-[title-slug].md`.
5. Update NocoDB entry status to "Published" (or "Ready to Publish").

## Notes
- Do NOT actually post to platforms (no API calls to social media). This skill formats content for manual posting.
- Each output file should be self-contained: everything needed to post is in the file.
- If a content piece targets multiple platforms, create a separate output file for each platform.
```

---

STOP: Confirm the skill file exists at `.claude/skills/content-publisher/SKILL.md`.

---

USER: [Waits for student to confirm the skill file exists]

---

ACTION: When the student confirms:

1. If the skill exists, say "Good. Now let us connect everything into one command."
2. If it does not exist, check the file path.
3. Move on to Step 2.

---

## Step 2: Create the master /content-engine command

### Why

Right now, running the full pipeline means typing separate commands for each step: research, then calendar, then write, then design. The master command chains them together. One command, the whole pipeline runs.

### What to do

Create a file at `.claude/commands/content-engine.md` with this content:

```markdown
# Content Engine

Run the full marketing content pipeline for a given content pillar.

## Steps

1. **Research**: Run the content-researcher skill on the specified content pillar. Save output to `research/`.

2. **Plan**: Run the content-calendar skill to generate 5 new content entries for this pillar in NocoDB. (Not a full month, just 5 entries for this run.)

3. **Write**: Run the content-writer skill on the first 2 new entries. Save to `content/`.

4. **Design**: Run the content-designer skill on the first written entry. Save to `designs/`.

5. **Format**: Run the content-publisher skill on the first designed entry. Save to `publish/`.

## How to use

Ask the user which content pillar to run the engine on. Show them the list from `brand/brand-guidelines.md`.

Run each step in order. After each step, briefly report what was produced before moving to the next step.

At the end, summarise:
- Research: [number] topics found
- Calendar: [number] entries added to NocoDB
- Written: [number] content pieces
- Designed: [number] visuals
- Formatted: [number] platform-ready pieces

## Notes
- This is a demonstration of the full pipeline. In real use, you would run each step with larger batches.
- If any step fails, report the error and continue with the remaining steps.
```

---

STOP: Type `/content-engine` in the chat. Does Claude ask you which content pillar to run? Tell me what happened.

---

USER: [Waits for student to confirm the slash command works]

---

ACTION: When the student confirms:

1. If the command works and asks for a content pillar, say "Good. Let us run it."
2. If it does not work, check the file path at `.claude/commands/content-engine.md`.
3. Move on to Step 3.

---

## Step 3: Run the master command

### Why

This is the moment everything connects. One command, five agents, one pipeline.

### What to do

Pick a content pillar and run `/content-engine`.

Watch as Claude runs through each step: research, calendar, write, design, format. Each step produces output that feeds the next.

This will take a few minutes. Let it run.

---

STOP: When the pipeline finishes, tell me:

1. Did all five steps complete?
2. How many pieces of content did the pipeline produce end-to-end?
3. If any step failed, which one?

---

USER: [Waits for student to report on the pipeline run]

---

ACTION: When the student responds:

1. If all five steps completed, say "Good. That is your marketing pipeline working end-to-end. One command."
2. If a step failed:
   - If research failed: check web search is working.
   - If calendar failed: check NocoDB connection.
   - If writing failed: check that the calendar entries were created.
   - If design failed: check OpenRouter plugin and credits for image model availability.
   - If formatting failed: check that content files exist.
   - Fix the issue and re-run just that step.
3. Move on to Step 4.

---

## Step 4: What you actually built

Eight capabilities. You used each one for a real reason.

- **CLAUDE.md.** The standing brief Claude reads at the start of every session. You wrote one in Lesson 1 that anchors the whole project.
- **Brand guidelines.** The document every agent reads. Your voice, your colors, your audience. Written in Lesson 1.
- **OpenRouter Plugin.** One account, image generation and model discovery. Installed in Lesson 1, used for visuals in Lesson 5.
- **Skills.** Instructions that teach Claude how YOU want each job done. You wrote five: researcher, calendar, writer, designer, publisher.
- **NocoDB MCP.** Your content calendar database. Connected in Lesson 3. Every agent reads from it and writes to it.
- **HeyGen MCP.** AI avatar video production. Connected in Lesson 6.
- **Vercel MCP.** Deployment to the internet. Connected in Lesson 7.
- **Slash commands.** `/brand`, `/research`, and `/content-engine`. Repeated workflows compressed into one keystroke.

That is more than most people who have been using Claude Code for months.

---

STOP: Quick reality check before we move on. Tell me:

1. Which of those capabilities feels most useful to you right now?
2. Which one will you use first this week?

No wrong answers. I just want to know where your head is at.

---

USER: [Waits for student to share which capabilities they are most drawn to]

---

ACTION: When the student responds:

1. Acknowledge their choice specifically. Connect it to their business: "Right, for [their business], [capability] probably saves you the most time because [specific reason]."
2. Do not lecture. Move on to the three adaptations.

---

## Step 5: Three real ways to extend this

The marketing agency you built is the base pattern. The same structure points at different use cases the moment you change what the agents do.

### 1. Client onboarding system

If you work with clients (freelancer, agency, consultant), the same pipeline works for each client. Swap the brand guidelines file. Each client gets their own research, calendar, content, and visuals without rebuilding anything.

The workflow: client fills out a brand questionnaire. You paste their answers into `/brand`. Claude generates their brand guidelines. From there, `/content-engine` produces a month of content for that client. Your deliverable is a NocoDB table full of planned, written, and designed content.

### 2. Product launch campaign

Same agents, tighter timeline. Instead of a month of general content, the calendar skill generates a launch sequence: teaser posts (week before), announcement day content, follow-up posts (week after), FAQ content.

Edit the content-calendar skill to accept a launch date and generate content around it. The writer produces launch-specific copy. The designer creates a consistent visual series. Everything scheduled to a tight timeline.

### 3. Seasonal campaign automation

Holiday marketing, back-to-school, end-of-year sales. The researcher finds seasonal trends months in advance. The calendar fills with timely content. The writer and designer produce batches you schedule in advance.

Set up a seasonal research run: "Research trending content about [holiday/season] for [your audience]." The calendar skill spreads seasonal content across the weeks leading up to the event.

---

STOP: One question.

Of those three (client onboarding, product launch, seasonal campaigns), which one would actually be useful to your business within the next month?

Pick one. If none of them fit, tell me what your version would look like instead.

---

USER: [Waits for student to pick an adaptation or describe their own]

---

ACTION: When the student responds:

1. **If they pick client onboarding:** Say "The fastest version: duplicate your `marketing-agency` folder for each client. Replace `brand/brand-guidelines.md` with the client's brand details. Run `/content-engine`. Each client gets a separate pipeline."

2. **If they pick product launch:** Say "Edit the content-calendar skill. Add a 'launch date' input. Have it generate content in three phases: teaser (1 week before), launch day, and follow-up (1 week after). The writer and designer handle the rest."

3. **If they pick seasonal campaigns:** Say "Run your researcher on seasonal topics now, months in advance. Feed the research into the calendar with dates spread across the season. Batch the writing and design in one session. You have a month of seasonal content ready before the season starts."

4. **If they describe their own version:** Engage with it. Tell them which skills they would modify and which new skills they might need. Be specific.

5. After whichever path: "You can start building that now. The pattern is the same as what you just used."

---

## Step 6: What's missing

Honest about what is not in here, so you know what you are getting:

- **Automated publishing.** The publisher formats content but does not post it. Connecting to Instagram, Facebook, and YouTube APIs requires OAuth setup that is too complex for this course. You copy-paste from the formatted files.
- **Scheduling.** Content that auto-generates every Monday morning is not set up. You run `/content-engine` manually when you want new content.
- **Analytics.** No tracking of what performs well. You check that in each platform's native analytics.
- **A/B testing.** No way to test which version of content performs better.
- **Multi-user access.** A teammate cannot run the pipeline without access to your API keys.
- **Production reliability.** No error handling, retries, or monitoring for when things break.

The system you built handles the production work: research, planning, writing, design, video, and formatting. You handle the judgement calls: reviewing content, approving designs, deciding what to publish. That is the right split for a first build.

---

## Final check

You are done with the course if:

- You can run `/content-engine` and get content produced end-to-end
- You can name what each agent does and which MCP it uses
- You have a live URL at `*.vercel.app` with your brand on it
- You have one specific idea for what to extend next

That is it.

---

ACTION: Wrap up the course. Do not drag it out. Specifically:

1. Ask the student one final question: "What is one thing you will build with this system in the next two weeks if you had to commit to it right now?"
2. When they answer, validate the idea concretely. If it is feasible, say so. If it is too big for two weeks, suggest a smaller first version.
3. Close with: "That is the course. The pattern is the same for anything you build next: brand context, skills, MCPs, and a slash command to kick it off. You have built one. The next one will take you half the time."

Do NOT use motivational filler ("you crushed it", "amazing work", "you got this"). Just acknowledge what they did, tell them what is next, and let them go.

---

USER: [Waits for student to share their next-build idea]

---

ACTION: When the student shares their idea, follow the wrap-up above. Then end the course cleanly. They are done.

---

## What's not in this lesson

This lesson deliberately does not include:

- A long recap of the course
- Multiple paragraphs of encouragement
- A complicated "next steps" tree

You have built the thing. Anything more here gets in the way.
