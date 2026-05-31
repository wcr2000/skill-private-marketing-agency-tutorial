# Lesson 6: Your AI Video Team

**Time: ~20 min**

**You'll finish with:** HeyGen connected to Claude Code, a video maker skill installed, and at least one completed AI avatar video where a virtual presenter speaks your script.

---

## The moment you're in

You have written content and visual designs. But your content calendar has video entries too, and right now those are just scripts in a text file. Nobody is on camera.

In the next twenty minutes, you will fix that. You will connect Claude to HeyGen, pick an AI avatar and voice that fit your brand, and turn one of your video scripts into a real video. The avatar moves, speaks, and presents your content.

This is the last new MCP you will set up. After this, you have the full creative pipeline: research, planning, writing, design, and video.

---

ACTION: Greet the student and confirm Lesson 5 is done. Specifically check:

1. Do at least 2 images exist in the `designs/` folder?
2. Does a video script exist in the `content/` folder?

If the images are missing, send them back to Lesson 5.

If there is no video script, help them create one quickly: pick a topic from their content calendar and write a 30-60 second script. Save it to `content/` before continuing. This is necessary because the video maker needs a script to work with.

If both are good, say "Time to turn one of your scripts into a video. We need to connect HeyGen first."

---

USER: [Waits for student to confirm Lesson 5 is done]

---

## What you're going to do

1. Create a HeyGen account and get your API key
2. Install the HeyGen MCP in Claude Code
3. Browse available avatars and voices
4. Pick an avatar and voice for your brand
5. Create a video maker skill
6. Generate a video from your script
7. Watch the completed video

Go in order.

---

## Step 1: Create a HeyGen account

### Why

HeyGen is a service that creates videos with AI avatars. The avatars are realistic-looking people who speak your script with lip sync. You need an account to access their API.

### What to do

1. Open your browser and go to `heygen.com`
2. Click "Sign Up" or "Get Started Free"
3. Create an account with your email or Google account
4. The free plan gives you limited credits. That is enough for this lesson.

Once signed in, find your API key:

1. Go to your account settings or developer settings
2. Look for "API Key" or "API Access"
3. Copy the API key

---

STOP: Tell me when you have a HeyGen account and have copied the API key.

---

USER: [Waits for student to confirm HeyGen account is ready]

---

ACTION: When the student confirms:

1. If they have the API key, say "Good. Let us connect it to Claude Code."
2. If they cannot find the API key, guide them: "In HeyGen, click your profile icon in the top right, then look for 'Settings' or 'API'. The key usually starts with a long string of letters and numbers."
3. Move on to Step 2.

---

## Step 2: Install the HeyGen MCP

### Why

Just like NocoDB in Lesson 3, Claude needs an MCP connection to talk to HeyGen. Without it, Claude cannot list avatars, create videos, or check their status.

### What to do

HeyGen has an official remote MCP that uses OAuth — no API key needed.

Run this command in your terminal (outside Claude Code):

```
claude mcp add --transport http heygen https://mcp.heygen.com/mcp/v1/
```

To make it available across all projects, add `-s user`:

```
claude mcp add --transport http -s user heygen https://mcp.heygen.com/mcp/v1/
```

Then start Claude Code and type `/mcp` to authenticate via browser OAuth. Sign in with your HeyGen account. No API key required — it uses your existing HeyGen plan and credits.

---

STOP: Tell me when HeyGen MCP shows as connected. Ask Claude "What MCP servers are connected?" if you are not sure.

---

USER: [Waits for student to confirm HeyGen MCP is connected]

---

ACTION: When the student responds:

1. If HeyGen shows as connected, say "Good. Let us see what avatars are available."
2. If they are stuck:
   - If the MCP fails to connect, check the API key is correct.
   - If they get a "command not found" error, they need Node.js installed.
   - If HeyGen MCP is pre-installed but needs a key, guide them to the right settings field.
3. Do not move on until HeyGen is connected.

---

## Step 3: Browse available avatars and voices

### Why

HeyGen has dozens of avatars (different people with different looks) and dozens of voices (different accents, tones, speeds). You want to pick ones that fit your brand. A tech startup might pick a young, casual presenter. A law firm might pick someone more formal.

### What to do

Ask Claude to:

1. "List the available HeyGen avatars." Claude will use the HeyGen MCP to show you the options. Each avatar has a name and a preview.

2. "List the available HeyGen voices." Each voice has a name, language, and a description of the tone.

Take a moment to look through the options. You are picking the face and voice of your brand's video content.

---

STOP: Tell me:

1. Which avatar catches your eye? (Name or describe it.)
2. Which voice sounds right for your brand? (Name or describe it.)

---

USER: [Waits for student to pick an avatar and voice]

---

ACTION: When the student picks:

1. Acknowledge their choice. Connect it to their brand: "That fits the [brand personality adjectives] vibe you described in Lesson 1."
2. Note the avatar ID and voice ID. You will need these for the video maker skill.
3. If they are unsure, help them narrow down: "Your brand is [their adjectives]. For that, I would suggest [avatar] with [voice] because [reason]."
4. Move on to Step 4.

---

## Step 4: Create the video maker skill

### Why

The video maker skill automates the process of turning a script into a video. It reads the script, calls HeyGen with the right avatar and voice, and monitors until the video is ready.

### What to do

Create the skill file at `.claude/skills/video-maker/SKILL.md` with this content:

```markdown
# Video Maker

## Purpose
Turn a video script from the `content/` folder into a produced video using HeyGen's AI avatar.

## Inputs
- A video script file from `content/` (must contain spoken script text)
- Avatar and voice preferences

## Configuration
- **Default Avatar:** [avatar ID the student chose]
- **Default Voice:** [voice ID the student chose]

## Process

1. Read the video script file from `content/`.
2. Extract the spoken script text (remove stage directions, visual notes, etc. -- only the words the avatar will speak).
3. Use the HeyGen MCP to create a video:
   - Use `create_video_from_avatar` with the configured avatar and voice
   - Pass the spoken script as the text input
   - Set video dimensions appropriate for the platform:
     - YouTube: 1920x1080 (landscape)
     - Instagram Reel: 1080x1920 (portrait)
     - General: 1920x1080 (landscape)
4. Monitor the video generation progress. HeyGen takes 2-5 minutes to render a video.
5. When the video is complete, provide the video URL or download link to the student.
6. Update the NocoDB entry status if applicable.

## Notes
- Keep scripts under 2 minutes for the free tier. Shorter scripts render faster and use fewer credits.
- If the script has multiple sections or scenes, consider generating each as a separate clip.
- The avatar will lip-sync to the text. Make sure the script is written for speaking, not reading.
- Notify the student that rendering takes a few minutes. This is normal.
```

Fill in the avatar ID and voice ID that the student chose in Step 3.

---

STOP: Confirm the skill file exists at `.claude/skills/video-maker/SKILL.md` and has the correct avatar and voice IDs.

---

USER: [Waits for student to confirm the skill file exists]

---

ACTION: When the student confirms:

1. If the skill exists with the right IDs, say "Good. Let us make your first video."
2. If the IDs are wrong or missing, update them.
3. Move on to Step 5.

---

## Step 5: Generate a video

### Why

This is the payoff. Your script becomes a video with a virtual presenter.

### What to do

Tell Claude: "Create a video from my video script [script title from content/]."

Claude will:
1. Read the script
2. Extract the spoken text
3. Call HeyGen through the MCP
4. Start monitoring the render

The video will take 2-5 minutes to render. This is normal. Claude will check the status periodically and tell you when it is done.

While you wait, this is a good time to stretch or grab a drink. You have built five agents in five lessons.

---

STOP: Has the video finished generating? When it is ready, watch it. Tell me:

1. Does the avatar speak your script correctly?
2. Does the voice sound natural?
3. Would you share this video on your social media?

---

USER: [Waits for student to watch the video and share their reaction]

---

ACTION: When the student responds:

1. If the video looks and sounds good, say "Good. You now have a video pipeline. Script goes in, video comes out. No camera, no editing software, no video skills."
2. If the avatar mispronounces something:
   - This sometimes happens with brand names or technical terms. You can adjust the script to spell words phonetically.
3. If the voice sounds unnatural:
   - Try a different voice and regenerate. Some voices handle certain types of content better than others.
4. If they would not share it:
   - Ask what specifically is wrong. If it is the avatar choice, they can pick a different one. If it is the script, adjust the script first.
5. Move on to the end-of-lesson check.

---

## End-of-lesson check

- HeyGen MCP is connected
- `.claude/skills/video-maker/SKILL.md` exists with correct avatar and voice IDs
- At least one video has been generated
- The video is watchable and the avatar speaks the script

---

## Common stumbles

- **"HeyGen says insufficient credits"** -- The free tier has limited credits. Short scripts (under 60 seconds) use fewer credits. If you run out, you can upgrade or create a new account.
- **"The video is taking a long time"** -- HeyGen videos typically take 2-5 minutes. If it has been more than 10 minutes, check the status through Claude. Sometimes renders get stuck and need to be resubmitted.
- **"The avatar looks weird or glitchy"** -- Try a different avatar. Some avatars handle certain script lengths or topics better than others.
- **"I cannot find the video"** -- Ask Claude to check the video status and provide the URL. HeyGen videos are hosted on HeyGen's servers. You can download them or link to them.

---

## What just happened

You connected the last creative tool in your pipeline. You now have six connected capabilities: brand context, research, content calendar, writing, design, and video. Each one reads from the ones before it. The brand guidelines inform everything. The research drives the calendar. The calendar feeds the writer. The writer feeds the designer and video maker.

One more lesson builds the landing page and deploys it. Then the final lesson connects everything into one command.

---

## When you're ready

Type: **Start Lesson 7**

You will build a landing page for your business and deploy it to a live URL on the internet.

---

ACTION: When the student says they are ready for Lesson 7, read the file at `lesson-modules/7-landing-page/CLAUDE.md` and begin.
