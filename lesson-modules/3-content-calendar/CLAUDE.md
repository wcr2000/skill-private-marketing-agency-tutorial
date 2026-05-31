# Lesson 3: A Month of Content, Planned

**Time: ~20 min**

**You'll finish with:** NocoDB connected to Claude Code, a Content Calendar table with the right fields, a content calendar skill installed, and at least 20 content entries planned for the next month.

---

## The moment you're in

You have brand guidelines and research on at least one content pillar. You know who your brand is, who your audience is, and what topics are trending. But you do not have a plan. No calendar. No schedule. No idea what to post next Tuesday.

In the next twenty minutes you will fix that. You will connect Claude to a database, create a content calendar table, and fill it with a full month of planned content. Every entry will have a title, a platform, a format, and a date.

After this lesson, you will never again stare at a blank screen wondering "what should I post today?"

---

ACTION: Greet the student and confirm Lesson 2 is done. Specifically check:

1. Does at least one research file exist in the `research/` folder?
2. Does the content researcher skill exist?

If either is missing, send them back to Lesson 2 to fix it. Do not continue.

If both are good, say "Now we need somewhere to store your content plan. We are going to use NocoDB, a free database you can view in your browser like a spreadsheet."

Ask: "Do you already have a NocoDB account, or do we need to create one?"

Wait for their answer before moving on.

---

USER: [Waits for student to confirm Lesson 2 is done and tell you their NocoDB account status]

---

ACTION: When the student responds:

1. If they have a NocoDB account, say "Good. Keep that browser tab handy."
2. If they do not, walk them through it: "Open your browser and go to `app.nocodb.com`. Click 'Sign Up'. Use your email or Google account. The free plan works. Tell me when you are signed in."
3. Wait for them to confirm NocoDB is ready before moving to Step 1.

---

## What you're going to do

1. Install the NocoDB MCP in Claude Code
2. Create a Content Calendar table in NocoDB
3. Confirm Claude can see the table
4. Create a content calendar skill
5. Run the skill to fill the calendar with a month of content
6. Review the calendar in your browser

Go in order.

---

## Step 1: Install the NocoDB MCP

### Why

An MCP (Model Context Protocol) is how Claude connects to systems outside your project folder. Without the NocoDB MCP, Claude cannot read or write to your database. With it, Claude can create tables, add rows, update statuses, and read your content plan.

### What to do

**1a. Create a new Base in NocoDB**

1. Go to `app.nocodb.com`
2. In the left sidebar, create a new Base. Name it "Marketing Agency" or your brand name.

**1b. Get the MCP config from NocoDB**

NocoDB has a built-in MCP endpoint for each base. To find it:

1. Inside your new base, look for **Settings** in the left sidebar
2. Click on **Model Context Protocol** (MCP)
3. Click **"New MCP Endpoint"**
4. NocoDB will show you a JSON config that looks like this:

```json
{
  "mcpServers": {
    "NocoDB Base - your-base-name": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://app.nocodb.com/mcp/your-base-id",
        "--header",
        "xc-mcp-token: your-token-here"
      ]
    }
  }
}
```

5. Copy this config. You will only see the token once.

**1c. Add the config to Claude Code**

Ask Claude to add this MCP config to your project. Paste the JSON config you copied from NocoDB.

After Claude adds it, restart Claude Code to load the new MCP connection.

---

STOP: Tell me when NocoDB MCP shows as connected in Claude Code. If you are not sure, ask Claude "What MCP servers are connected?" and check if NocoDB appears in the list.

---

USER: [Waits for student to confirm NocoDB MCP is connected]

---

ACTION: When the student responds:

1. If NocoDB shows as connected, say "Good. Now let us create the content calendar table."
2. If they are stuck:
   - If they cannot find the API token in NocoDB, guide them through the NocoDB interface. The location varies by version but it is usually under Account Settings or Team Settings.
   - If the MCP connection fails, check the base URL. If they are self-hosting NocoDB, the URL will be different from `app.nocodb.com`.
   - If they get a "command not found" error for npx, they need Node.js installed (same fix as Lesson 1).
3. Do not move on until NocoDB is connected.

---

## Step 2: Create the Content Calendar table

### Why

The content calendar is the backbone of your marketing system. Every agent reads from it or writes to it. The writer picks entries to write. The designer picks entries to design. The publisher picks entries to publish. The table needs the right fields so each agent knows what to do.

### Important limitation

The NocoDB MCP can only read and write records (rows). It cannot create tables or add fields (columns). You must create the table and fields manually in the NocoDB browser interface. Once the table exists, Claude will fill it with content via MCP.

### What to do

Go to `app.nocodb.com`, open your base, and create the table manually:

1. Click **+** to add a new table. Name it exactly: **Content Calendar**
2. Add these fields one by one using the **+** button on the right side of the column headers:

| Field Name | Type |
| --- | --- |
| Title | Single line text |
| Content Pillar | Single line text |
| Platform | Single line text |
| Format | Single line text |
| Status | Single line text |
| Scheduled Date | Date |
| Notes | Long text |

Once all fields are created, come back to Claude Code.

---

STOP: Ask Claude to list the fields in the Content Calendar table. Does it show all seven fields? Tell me what Claude reports.

---

USER: [Waits for student to confirm the table has the correct fields]

---

ACTION: When the student responds:

1. If all seven fields are there, say "Good. The table is ready. Now let us fill it."
2. If fields are missing, have Claude add them. Double-check the field types.
3. If Claude cannot see the table at all, check that the NocoDB MCP is connected and that Claude has access to the right base/workspace.
4. Move on to Step 3.

---

## Step 3: Verify Claude can read and write to NocoDB

### Why

Before we automate content planning, we need to confirm the connection works both ways: Claude can read the table structure AND write rows to it.

### What to do

Ask Claude to add one test row to the Content Calendar:

"Add a test row to the Content Calendar with Title 'Test Entry', Content Pillar 'Test', Platform 'Instagram', Format 'Post', Status 'Planned', Scheduled Date tomorrow."

Then check: open NocoDB in your browser and look at the Content Calendar table. You should see the test row.

---

STOP: Open NocoDB in your browser. Can you see the test row in the Content Calendar? Tell me what you see.

---

USER: [Waits for student to confirm they can see the test row in NocoDB]

---

ACTION: When the student responds:

1. If they can see the test row, say "Good. Claude can read and write to your database. Delete the test row if you want, or leave it. Now let us create the skill that fills the calendar."
2. If the row is not there:
   - Ask Claude if the write was successful. Check for error messages.
   - Verify the MCP token has write permissions.
   - Try having Claude list the tables it can see to confirm it is connected to the right base.
3. Move on to Step 4.

---

## Step 4: Create the content calendar skill

### Why

The content calendar skill automates the entire planning process. It reads your brand guidelines, reads your research, and generates a full month of content ideas with the right mix of platforms, formats, and content pillars.

### What to do

Create the skill file at `.claude/skills/content-calendar/SKILL.md` with this content:

```markdown
# Content Calendar Generator

## Purpose
Generate a month of content ideas and push them to the NocoDB Content Calendar table.

## Inputs
- Brand guidelines from `brand/brand-guidelines.md`
- Research files from `research/` folder
- Optional: specific month and year (defaults to the upcoming month)

## Process

1. Read `brand/brand-guidelines.md` for content pillars, audience, and brand voice.
2. Read all research files in `research/` for trending topics, audience questions, and timely hooks.
3. Generate 20-30 content entries for the next 4 weeks. Each entry needs:
   - **Title**: Specific, descriptive title for the content piece
   - **Content Pillar**: Which pillar this maps to
   - **Platform**: Target platform (Instagram, Facebook, LinkedIn, YouTube, Blog)
   - **Format**: Content format (Post, Reel, Story, Carousel, Article, Video)
   - **Status**: "Planned"
   - **Scheduled Date**: A date within the next 4 weeks
   - **Notes**: Brief description of the angle or hook

4. Ensure variety:
   - Spread content across all content pillars (not just one)
   - Mix platforms (do not put everything on Instagram)
   - Mix formats (posts, reels, articles, videos)
   - Space out dates (roughly 1-2 pieces per day, more on high-traffic days)
   - Include at least 2 video scripts (for the video maker in Lesson 6)

5. Push all entries to the NocoDB Content Calendar table using the NocoDB MCP.

## Output
- All entries added to NocoDB
- Summary printed in chat: total entries, breakdown by platform, breakdown by pillar
```

---

STOP: Confirm the skill file exists at `.claude/skills/content-calendar/SKILL.md`.

---

USER: [Waits for student to confirm the skill file exists]

---

ACTION: When the student confirms:

1. If the skill exists, say "Good. Now let us run it and fill your calendar."
2. If it does not exist, check the file path.
3. Move on to Step 5.

---

## Step 5: Fill the calendar

### Why

This is the payoff. One command and your content calendar fills with a month of planned content.

### What to do

Tell Claude: "Generate my content calendar for the next month."

Claude will read the brand guidelines, read the research, generate 20-30 entries, and push them to NocoDB one by one.

This may take a few minutes. You will see Claude adding rows in the chat. Let it finish.

---

STOP: When it is done, tell me:

1. How many entries did Claude add to the calendar?
2. Name 3 titles you like.
3. Is there a good mix of platforms and formats, or is it all the same?

---

USER: [Waits for student to share the results]

---

ACTION: When the student responds:

1. If there are 20+ entries with good variety, say "Good. You now have a month of content planned."
2. If there are fewer entries, ask Claude to add more. The skill should generate at least 20.
3. If the mix is too heavy on one platform or format, ask Claude to adjust: "Add more [platform/format] entries and fewer [over-represented type]."
4. Move on to Step 6.

---

## Step 6: Review in your browser

### Why

NocoDB has a browser interface that looks like a spreadsheet. This is your home base for the rest of the course. The writer will update statuses to "Drafted." The designer will update to "Designed." You will use this view to see the state of your marketing pipeline at a glance.

### What to do

Open NocoDB in your browser. Navigate to the Content Calendar table. You should see all the entries Claude just created, with titles, platforms, formats, dates, and statuses.

Take a minute to look through them. This is your content plan for the next month.

---

STOP: Open NocoDB in your browser. Can you see the Content Calendar with all the entries? Does it look like a real content plan you would use? Tell me.

---

USER: [Waits for student to confirm they can see the calendar in the browser]

---

ACTION: When the student confirms:

1. If they can see the calendar and it looks useful, say "Good. This is your marketing dashboard from now on. Every lesson from here reads from this calendar and updates it."
2. If they cannot see it, troubleshoot the NocoDB browser interface. Make sure they are looking at the right base and table.
3. Move on to the end-of-lesson check.

---

## End-of-lesson check

- NocoDB MCP is connected
- Content Calendar table has all seven fields
- At least 20 entries are in the calendar
- Entries cover multiple platforms, formats, and content pillars
- You can see the calendar in your browser

---

## NocoDB MCP limits (confirmed)

These are real limits discovered in practice:

**What the MCP can do:**
- Add, read, update, and delete records (rows)
- Maximum 10 records per create request (Claude will batch automatically)

**What the MCP cannot do:**
- Create tables
- Add, edit, or delete fields (columns)
- Rename tables
- Manage views, permissions, or base settings

**Connection notes:**
- Use the `mcp-remote` config from NocoDB app (Base > Settings > Model Context Protocol > New MCP Endpoint)
- The token is tied to one specific base, not the whole workspace
- For multiple bases, create separate MCP endpoints
- Config goes in `~/Library/Application Support/Code/User/mcp.json` (VS Code) or `.mcp.json` in the project root. Reload Claude Code after every config change.

## Common stumbles

- **"NocoDB MCP cannot connect"** -- Get the MCP config directly from NocoDB: open your base, go to Settings > Model Context Protocol, click "New MCP Endpoint". Copy the JSON config and add it to Claude Code. The token is shown only once.
- **"Claude says it cannot find the table"** -- The table name must match exactly. Ask Claude to list all tables it can see.
- **"Only 5-10 entries were created"** -- The MCP limit is 10 records per request. Claude should batch multiple requests automatically. If it stopped early, tell it to continue adding entries until there are at least 20.
- **"All entries are for Instagram"** -- Ask Claude to add variety. Explicitly request entries for TikTok, Facebook, YouTube, and Blog posts.

---

## What just happened

You connected Claude to a database through an MCP, built a content calendar skill, and filled it with a month of planned content. This is the backbone of your marketing system. Every lesson from here reads from this calendar: the writer picks entries to draft, the designer picks entries to design, and the publisher picks entries to publish.

You also learned how MCPs work: they give Claude access to systems outside your project folder. NocoDB is the first. You will add HeyGen (video) and Vercel (deployment) in later lessons.

---

## When you're ready

Type: **Start Lesson 4**

You will build a content writer that picks entries from the calendar and writes them in your brand voice.

---

ACTION: When the student says they are ready for Lesson 4, read the file at `lesson-modules/4-content-writer/CLAUDE.md` and begin.
