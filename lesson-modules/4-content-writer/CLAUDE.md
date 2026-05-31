# Lesson 4: Words That Sound Like You

**Time: ~15 min**

**You'll finish with:** A content writer skill that picks entries from your calendar and writes content in your brand voice. Three content pieces saved to your project (a social post, an article, and a video script), and NocoDB entries updated to "Drafted."

---

## The moment you're in

You have a content calendar full of ideas. Titles, platforms, formats, dates. But no actual content. The calendar says "post about [topic] on Instagram on Thursday" but nobody has written the post yet.

In the next fifteen minutes, you will build a writer agent that does that. Pick an entry from the calendar, and the writer produces the full content piece in your brand voice. Social posts get captions and hashtags. Articles get full long-form text. Video scripts get a shot-by-shot breakdown.

---

ACTION: Greet the student and confirm Lesson 3 is done. Specifically check:

1. Is NocoDB MCP connected?
2. Does the Content Calendar table have at least 20 entries?

If either is missing, send them back to Lesson 3 to fix it. Do not continue.

If both are good, say "Time to turn those calendar entries into actual content. Let us build your writer."

---

USER: [Waits for student to confirm Lesson 3 is done]

---

## What you're going to do

1. Create a content writer skill
2. Write a social post from a calendar entry
3. Write an article from a calendar entry
4. Write a video script from a calendar entry
5. Update NocoDB statuses to "Drafted"

Go in order.

---

## Step 1: Create the content writer skill

### Why

The content writer skill teaches Claude how to turn a calendar entry into a finished piece of content. It reads the brand guidelines for voice and tone, then writes content appropriate for the platform and format.

### What to do

Create the skill file at `.claude/skills/content-writer/SKILL.md` with this content:

```markdown
# Content Writer

## Purpose
Take a content calendar entry and write the full content piece in the brand's voice. Save the output to the `content/` folder and update the entry status in NocoDB.

## Inputs
- A content calendar entry (by title or by selecting from the NocoDB table)
- Brand guidelines from `brand/brand-guidelines.md`

## Process

1. Read `brand/brand-guidelines.md` for brand voice, tone, vocabulary, and what to avoid.
2. Read the specified content calendar entry from NocoDB to get the title, platform, format, content pillar, and notes.
3. Write the content piece following the platform and format rules below.
4. Save the content to `content/[title-slug].md`.
5. Update the NocoDB entry status from "Planned" to "Drafted".

## Platform and format rules

### Instagram Post
- Caption: 100-200 words, conversational, matches brand voice
- Include a hook in the first line (this shows before "more")
- Include a call to action at the end
- Add 5-10 relevant hashtags
- Note the ideal image description for the designer

### Instagram Reel / Story
- Script: 30-60 seconds of spoken content
- Include visual directions (what should be on screen)
- Hook in the first 3 seconds
- Call to action at the end

### Facebook Post
- Slightly longer than Instagram (200-300 words is fine)
- Can be more informational
- Include a question to encourage comments
- No hashtags (or max 2-3)

### LinkedIn Post
- Professional but still matches brand voice
- 150-300 words
- Lead with insight or data
- End with a question or call to action
- 3-5 hashtags

### Blog Article
- 800-1500 words
- Include H2 and H3 subheadings
- Opening paragraph hooks the reader
- Include practical takeaways
- End with a call to action

### YouTube Video Script
- Full script with timestamps or sections
- Include intro hook (first 30 seconds)
- Include B-roll suggestions
- Include outro with call to action and subscribe prompt
- Note any on-screen text or graphics needed

## Notes
- Every piece must sound like the brand, not like generic AI writing
- Reference specific details from the brand guidelines
- If the calendar entry has notes, use them as creative direction
- Keep the brand's "what to avoid" list in mind throughout
```

---

STOP: Confirm the skill file exists at `.claude/skills/content-writer/SKILL.md`.

---

USER: [Waits for student to confirm the skill file exists]

---

ACTION: When the student confirms:

1. If the skill exists, say "Good. Let us test it with three different types of content."
2. If it does not exist, check the file path.
3. Move on to Step 2.

---

## Step 2: Write a social post

### Why

Social posts are the quickest test. Short, specific, and easy to judge whether it sounds like your brand.

### What to do

Look at your content calendar in NocoDB (or ask Claude to list entries). Pick an entry that has Format = "Post" and Platform = "Instagram" or "LinkedIn" or "Facebook."

Tell Claude: "Write the content for [entry title]."

Claude will read the brand guidelines, read the calendar entry, and produce the content piece.

---

STOP: Read the social post Claude wrote. Answer these two questions:

1. Does it sound like YOUR brand, or does it sound like generic marketing AI?
2. What would you change about it?

---

USER: [Waits for student to review the post and share feedback]

---

ACTION: When the student responds:

1. If they say it sounds like their brand, say "Good. The brand guidelines are doing their job."
2. If it sounds generic or off-brand:
   - Ask what specifically feels wrong. Is it the tone? The vocabulary? The structure?
   - Make the adjustments right now. Rewrite the post with their feedback.
   - If the brand guidelines need updating (e.g. the voice section is too vague), note that they can run `/brand` to update them later.
3. Make sure the content file is saved to `content/[title-slug].md`.
4. Move on to Step 3.

---

## Step 3: Write an article

### Why

Long-form content tests whether the brand voice holds over 800+ words, not just a short caption.

### What to do

Pick an entry with Format = "Article" or "Blog" from the calendar. If there are none, pick any entry and tell Claude to write it as a blog article.

Tell Claude: "Write the article for [entry title]."

Review the output. It should have headings, a clear structure, and still sound like your brand throughout.

Save to `content/[title-slug].md`.

---

STOP: Skim the article. Does the brand voice hold throughout, or does it drift into generic writing in the middle? Tell me.

---

USER: [Waits for student to review the article]

---

ACTION: When the student responds:

1. If the voice holds, say "Good. Now one more: a video script."
2. If it drifts, adjust the voice section in the content writer skill or in the brand guidelines. The most common issue is the "what to avoid" section being too vague.
3. Move on to Step 4.

---

## Step 4: Write a video script

### Why

The video script you write here will be used in Lesson 6 when you create an AI avatar video. The video maker agent reads scripts from the `content/` folder. If you do not have a video script, Lesson 6 has nothing to work with.

### What to do

Pick an entry with Format = "Video" from the calendar. If there are none, pick a topic and tell Claude to write it as a YouTube or Instagram Reel script.

Tell Claude: "Write the video script for [entry title]."

The output should include spoken script, visual directions, and timing guidance.

Save to `content/[title-slug].md`.

---

STOP: Read the video script. Does it sound natural enough that a person (or AI avatar) could speak it out loud? Tell me.

---

USER: [Waits for student to review the video script]

---

ACTION: When the student responds:

1. If the script sounds natural and speakable, say "Good. This is the script we will use to create an AI avatar video in Lesson 6."
2. If it sounds too formal or unnatural for spoken delivery, have Claude rewrite it in a more conversational tone. Spoken scripts should sound like talking, not like writing.
3. Move on to Step 5.

---

## Step 5: Update NocoDB statuses

### Why

The content calendar is your dashboard. When content is written, the status should change from "Planned" to "Drafted" so you know what has been done and what still needs work.

### What to do

Tell Claude: "Update the NocoDB status to 'Drafted' for the three entries we just wrote."

Claude will use the NocoDB MCP to update each entry.

---

STOP: Open NocoDB in your browser. Check the three entries you wrote content for. Do they now show Status = "Drafted"? Tell me.

---

USER: [Waits for student to confirm the statuses are updated]

---

ACTION: When the student confirms:

1. If the statuses are updated, say "Good. You can see at a glance what is drafted and what still needs writing. Every time the writer runs, it updates the calendar."
2. If the statuses are not updated, check that Claude has write access to NocoDB. Try updating one manually through Claude.
3. Move on to the end-of-lesson check.

---

## End-of-lesson check

- `.claude/skills/content-writer/SKILL.md` exists
- At least 3 content files are in the `content/` folder (post, article, video script)
- The content sounds like YOUR brand, not generic AI
- NocoDB entries for the written content show Status = "Drafted"

---

## Common stumbles

- **"The content sounds generic"** -- The brand guidelines voice section needs more specificity. Instead of "professional and friendly," write "professional like a trusted advisor explaining something complex in simple terms." The more specific the guidelines, the more distinct the writing.
- **"Claude did not update NocoDB"** -- Check that the NocoDB MCP is still connected. If the session has been long, the connection may need refreshing.
- **"I do not have a video entry in the calendar"** -- No problem. Pick any topic from your content pillars and tell Claude "Write a 60-second Instagram Reel script about [topic]." Save it to `content/`. The calendar skill should have created at least 2 video entries, but if it did not, you can add one manually.

---

## What just happened

You built a writer agent that turns calendar entries into actual content. Not generic content. Content that sounds like your brand. It reads the brand guidelines, follows platform-specific rules, and saves everything to a folder the designer and video maker can access.

The content folder now has real pieces your business could publish. The NocoDB calendar shows what has been drafted and what still needs work.

---

## When you're ready

Type: **Start Lesson 5**

You will build a content designer that generates brand-consistent visuals using the OpenRouter images plugin.

---

ACTION: When the student says they are ready for Lesson 5, read the file at `lesson-modules/5-content-designer/CLAUDE.md` and begin.
