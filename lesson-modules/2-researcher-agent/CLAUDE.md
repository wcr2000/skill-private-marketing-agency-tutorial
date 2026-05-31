# Lesson 2: Your Research Team

**Time: ~20 min**

**You'll finish with:** A content researcher skill that uses web search to find trending topics, competitor angles, and audience questions for any content pillar. Plus a research output saved to your project and a `/research` slash command.

---

## The moment you're in

Right now you have a project with brand guidelines. But you do not have any content ideas. You know your content pillars (the themes you post about), but you do not know what is trending, what your competitors are talking about, or what questions your audience is asking right now.

In the next twenty minutes you will build a research agent that answers all of that. Pick a content pillar, run the researcher, and get back a structured report with topics you can actually use.

---

ACTION: Greet the student and confirm Lesson 1 is done. Specifically check:

1. Does `brand/brand-guidelines.md` exist with content pillars?

If it is missing, send them back to Lesson 1 to fix it. Do not continue.

If both are good, say "Let us build your research agent. First, pick one of your content pillars from the brand guidelines. Which one do you want to research first?"

Wait for their answer before moving on.

---

USER: [Waits for student to confirm Lesson 1 is done and pick a content pillar]

---

## What you're going to do

1. Create a content researcher skill
2. Run the researcher on one of your content pillars
3. Review and validate the research output
4. Save the output to the research folder
5. Create a `/research` slash command

Go in order.

---

## Step 1: Create the content researcher skill

### Why

A skill is a file that teaches Claude exactly how YOU want a job done. Without a skill, you would have to explain the research process every time. With a skill, Claude knows the format, the depth, and where to save the output.

### What to do

Create the skill file at `.claude/skills/content-researcher/SKILL.md` with this content:

```markdown
# Content Researcher

## Purpose
Research a specific content pillar to find trending topics, competitor content, and audience questions. Use this research to inform the content calendar.

## Inputs
- A content pillar name from `brand/brand-guidelines.md`

## Process

1. Read `brand/brand-guidelines.md` to understand the brand, audience, and the specific content pillar being researched.

2. Use web search to research the following for this content pillar and the brand's niche:

   a. **Trending topics** (last 30 days) related to this content pillar and the brand's niche. Find 5-8 specific topics that are getting attention right now.

   b. **Competitor content** -- What are competitors or similar brands posting about? What formats are they using (reels, carousels, articles, videos)? What is getting engagement?

   c. **Audience questions** -- What questions is the target audience asking online? Check forums, social media, and Q&A sites. Find 5-8 real questions.

   d. **Seasonal and timely hooks** -- Any upcoming events, holidays, or industry dates that connect to this pillar in the next 30 days?

3. Compile the findings into a structured markdown report.

## Output format

Save the report to `research/[pillar-name-slug].md` using this structure:

```
# Research: [Content Pillar Name]
**Date:** [today's date]
**Pillar:** [pillar name from brand guidelines]

## Trending Topics
1. [Topic] -- [one sentence on why it is trending]
2. [Topic] -- [one sentence]
...

## Competitor Content
- [What competitors are posting and in what format]
- [What is getting engagement and why]
...

## Audience Questions
1. [Question people are actually asking]
2. [Question]
...

## Timely Hooks
- [Upcoming event or date and how to connect it to content]
...

## Suggested Content Ideas
Based on the above research, here are 5 content ideas:
1. [Idea with suggested format: post/reel/article/video]
2. [Idea]
...
```

## Notes
- Focus on the brand's specific niche and audience, not generic industry trends.
- Prioritise topics the brand can credibly speak about given their positioning.
- Each suggested content idea should map to a realistic piece of content the brand could produce.
```

---

STOP: Confirm the skill file exists at `.claude/skills/content-researcher/SKILL.md`. Ask Claude "What skills do you have?" or check the file tree. Tell me if it is there.

---

USER: [Waits for student to confirm the skill file exists]

---

ACTION: When the student confirms:

1. If the skill exists, say "Good. Now let us run it."
2. If it does not exist, check the file path. The `.claude` folder must be at the root of `marketing-agency`. The path must be exactly `.claude/skills/content-researcher/SKILL.md`.
3. Move on to Step 2.

---

## Step 2: Run the researcher on your content pillar

### Why

The skill file teaches Claude the process. Now you run it on a real content pillar to get real research.

### What to do

Tell Claude:

"Research my content pillar: [the pillar name the student chose earlier]"

Claude will read the skill, use web search to research current information, and generate a report.

This may take a minute or two. Claude is searching the internet for current information.

---

STOP: When the research is done, tell me:

1. Which content pillar did you research?
2. Name 3 trending topics it found.
3. Do the topics feel relevant to your business, or do they feel generic?

---

USER: [Waits for student to share the research results and whether they feel relevant]

---

ACTION: When the student responds:

1. If the topics feel relevant, say "Good. This is what your research agent will produce every time you run it. Real topics your audience cares about."
2. If the topics feel generic or off-target:
   - Check if the brand guidelines have enough detail about the audience and niche. Generic guidelines produce generic research.
   - Try re-running with a more specific prompt: "Research trending topics about [specific niche detail] for [specific audience] in the context of [pillar name]."
   - If the research returned no results, try a more specific search query with the audience and niche details.
3. Move on to Step 3.

---

## Step 3: Review and save the research

### Why

Research is only useful if you can find it later. Every research output goes into the `research/` folder so the content calendar skill (Lesson 3) and the content writer skill (Lesson 4) can reference it.

### What to do

Check that the research output was saved to `research/[pillar-name].md`. If it was not saved automatically, tell Claude to save it there now.

Open the file and skim it. Make sure:
- The trending topics are specific, not vague
- The audience questions are questions real people would ask
- The suggested content ideas are things your brand could actually produce

If anything needs improvement, tell Claude what to fix.

---

STOP: Confirm you have a research file in the `research/` folder. Tell me the file name.

---

USER: [Waits for student to confirm the research file is saved]

---

ACTION: When the student confirms:

1. If the file exists, say "Good. The content calendar skill in Lesson 3 will read these research files to generate content ideas."
2. If the file does not exist, have Claude create the `research/` folder and save the output there.
3. Move on to Step 4.

---

## Step 4: Create the /research slash command

### Why

Right now you had to type out "Research my content pillar: [name]." A slash command makes this a one-keystroke operation. Type `/research`, pick a pillar, and the agent runs.

### What to do

Create a file at `.claude/commands/research.md` with this content:

```markdown
# Research a Content Pillar

Read the content pillars from `brand/brand-guidelines.md`.

Ask the user which pillar they want to research. Show them the list of pillars and let them pick one.

Then run the content-researcher skill on that pillar. Save the output to `research/[pillar-name-slug].md`.

When done, summarise the top 3 trending topics and top 3 audience questions.
```

---

STOP: Type `/research` in the chat. Does Claude ask you which content pillar to research? Tell me what happened.

---

USER: [Waits for student to confirm the slash command works]

---

ACTION: When the student confirms:

1. If the slash command works, say "Good. You now have a research agent you can run anytime. Pick a pillar, run /research, and get back a report in under two minutes."
2. If it did not work, check that the file is at `.claude/commands/research.md` exactly.
3. Move on to the end-of-lesson check.

---

## End-of-lesson check

- `.claude/skills/content-researcher/SKILL.md` exists
- You ran the researcher on at least one content pillar
- A research file is saved in the `research/` folder
- The `/research` slash command works

---

## Common stumbles

- **"The web search did not return useful results"** -- Try more specific search terms. Include your niche, audience type, and the current month/year. For example: "trending fitness topics for small business owners June 2026" is better than "fitness trends."
- **"The research feels outdated or generic"** -- Research models sometimes return cached results. Try adding "in [current month and year]" to the research prompt. Also check that your brand guidelines are specific enough about your niche.
- **"Claude did not use the skill"** -- Make sure the skill file is at the exact path `.claude/skills/content-researcher/SKILL.md`. The folder name `content-researcher` and the file name `SKILL.md` (all caps) both matter.

---

## What just happened

You built a research agent that takes a content pillar and returns a structured report with trending topics, competitor insights, and audience questions. This is the input for everything that comes next. The content calendar (Lesson 3) uses this research to plan what to post. The writer (Lesson 4) uses it to know what topics are resonating.

You also learned what a skill is: a file that teaches Claude exactly how you want a job done. You will create more skills for writing, design, video, and publishing.

---

## When you're ready

Type: **Start Lesson 3**

You will connect NocoDB and build a content calendar with a full month of planned content.

---

ACTION: When the student says they are ready for Lesson 3, read the file at `lesson-modules/3-content-calendar/CLAUDE.md` and begin.
