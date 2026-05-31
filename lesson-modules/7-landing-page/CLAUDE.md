# Lesson 7: A Page on the Internet

**Time: ~20 min**

**You'll finish with:** A landing page for your business with your brand colors, content, and a live `*.vercel.app` URL you can share with anyone.

---

## The moment you're in

You have brand guidelines, research, a content calendar, written content, visual designs, and a video. All of it lives on your machine. Nobody else can see it.

In the next twenty minutes, you will build a landing page for your business and deploy it to the internet. When you are done, you will have a live URL you can text to a friend, put in your email signature, or share on social media.

This is the second-to-last lesson. After this, you connect everything into one command and wrap up.

---

ACTION: Greet the student and confirm Lesson 6 is done. Specifically check:

1. Does at least one video exist (generated in Lesson 6)?
2. Do content files exist in `content/`?
3. Do design files exist in `designs/`?

If content or designs are missing, send them back to the relevant lesson.

If the video is missing but content and designs exist, that is acceptable. The landing page does not require the video.

If ready, say "Let us build your landing page and put it on the internet. One new account to set up: Vercel."

---

USER: [Waits for student to confirm Lesson 6 is done]

---

## What you're going to do

1. Create a Vercel account and install the Vercel MCP
2. Create a landing page skill
3. Generate the landing page HTML and CSS
4. Preview it locally
5. Deploy to Vercel
6. Open the live URL

Go in order.

---

## Step 1: Create a Vercel account and install the MCP

### Why

Vercel is a platform that hosts websites for free. You upload your HTML files and get a URL. The Vercel MCP lets Claude deploy directly from your project without you needing to learn the Vercel dashboard.

### What to do

**1a. Create your Vercel account**

1. Open your browser and go to `vercel.com`
2. Click "Sign Up"
3. Sign up with your email, GitHub, or Google account. The free "Hobby" plan is all you need.
4. Once signed in, go to your account settings
5. Find "Tokens" or "API Tokens"
6. Create a new token with a name like "Claude Code"
7. Copy the token

**1b. Install the Vercel MCP**

Vercel has an official remote MCP that uses OAuth — no API token needed.

Run this command in your terminal (outside Claude Code):

```
claude mcp add --transport http vercel https://mcp.vercel.com
```

Then start Claude Code and type `/mcp` to authenticate via browser OAuth. Sign in with your Vercel account.

Alternatively, you can run:

```
npx add-mcp https://mcp.vercel.com
```

This auto-detects your installed AI clients and configures Vercel MCP for all of them at once.

---

STOP: Tell me when Vercel MCP shows as connected in Claude Code.

---

USER: [Waits for student to confirm Vercel MCP is connected]

---

ACTION: When the student responds:

1. If Vercel shows as connected, say "Good. Now let us build the page."
2. If they are stuck:
   - If they cannot find the Vercel token, guide them: "In Vercel, click your avatar top-right, then Settings, then Tokens. Create a new one."
   - If the MCP fails, check the token is correct.
3. Do not move on until Vercel is connected.

---

## Step 2: Create the landing page skill

### Why

The landing page skill tells Claude how to build a page that looks like your brand. It pulls colors from the brand guidelines, content from your written pieces, and structures everything into a professional single-page layout.

### What to do

Create the skill file at `.claude/skills/landing-page/SKILL.md` with this content:

```markdown
# Landing Page Generator

## Purpose
Build a single-page landing page for the brand using Vite + React + Tailwind CSS + shadcn/ui. The page uses the brand's colors, voice, and content. Deploy it to Vercel for a public URL.

## Stack
- **Vite** — build tool
- **React** — component-based UI
- **Tailwind CSS** — utility-first styling
- **shadcn/ui** — professional component library

## Inputs
- Brand guidelines from `brand/brand-guidelines.md`
- Content pieces from `content/` folder
- Design images from `designs/` folder (if available)

## Process

1. Read `brand/brand-guidelines.md` for:
   - Brand name
   - Brand colors (hex codes)
   - Typography guidance
   - Brand voice for copy
   - Target audience

2. Read content pieces from `content/` for:
   - Value proposition or main message
   - Key benefits or features

3. Scaffold the project:
   ```
   npm create vite@latest landing-page -- --template react
   cd landing-page
   npm install
   npm install -D tailwindcss postcss autoprefixer
   npx tailwindcss init -p
   npx shadcn@latest init
   ```

4. Configure Tailwind with brand colors in `tailwind.config.js`:
   - Set primary, secondary, and accent colors from brand guidelines

5. Build the page as a single `src/App.jsx` with these sections using shadcn/ui components:
   - **Hero section**: Brand name, tagline, value proposition, CTA button
   - **About section**: Who you are and what you do
   - **Features/Benefits section**: 3-4 key benefits using shadcn Card components
   - **Content preview section**: Snippets from 2-3 content pieces
   - **Call to action section**: Final CTA
   - **Footer**: Brand name, copyright, social links

6. Run `npm run build` to produce the `dist/` folder for deployment.

## Deployment
Deploy the `landing-page/` folder to Vercel using the Vercel MCP. Vercel auto-detects Vite and runs the build. The live URL will be `*.vercel.app`.

## Notes
- No placeholder text. Every word must be real content about the brand.
- Keep the copy in the brand voice.
- The page must be mobile-responsive.
- Use shadcn/ui components (Button, Card, Badge) for professional look.
```

---

STOP: Confirm the skill file exists at `.claude/skills/landing-page/SKILL.md`.

---

USER: [Waits for student to confirm the skill file exists]

---

ACTION: When the student confirms:

1. If the skill exists, say "Good. Let us generate your landing page."
2. If it does not exist, check the file path.
3. Move on to Step 3.

---

## Step 3: Generate the landing page

### Why

Claude is about to read everything you have built across six lessons (brand guidelines, content, designs) and produce a complete web page. No coding needed.

### What to do

Tell Claude: "Build my landing page."

Claude will read the brand guidelines, content files, and design references, then generate `landing-page/index.html` and `landing-page/styles.css`.

This may take a minute. The page has multiple sections and needs to match your brand precisely.

---

STOP: When Claude finishes, tell me it is done. We will preview it next.

---

USER: [Waits for student to confirm the page is generated]

---

ACTION: When the student confirms:

1. Check that both `landing-page/index.html` and `landing-page/styles.css` exist.
2. If either is missing, have Claude generate it.
3. Move on to Step 4.

---

## Step 4: Preview locally

### Why

Before putting it on the internet, check that it looks right on your machine.

### What to do

Open the landing page in your browser. The easiest way:

- **On Mac:** In Claude Code, run: `open landing-page/index.html`
- **On Windows:** In Claude Code, run: `start landing-page/index.html`
- **Or:** Navigate to the `landing-page` folder in Finder/File Explorer and double-click `index.html`

The page should open in your browser. It will show your brand name, your brand colors, your content, and a clean professional layout.

---

STOP: Look at the landing page in your browser. Answer these questions:

1. Does it show your brand name and colors?
2. Does the layout look professional?
3. What would you change?

---

USER: [Waits for student to review the landing page]

---

ACTION: When the student responds:

1. If they are happy with it, say "Good. Let us put it on the internet."
2. If they want changes:
   - Make the changes immediately. Common requests: different hero text, different color balance, different section order, more or less content.
   - Have them refresh the browser to see the updated version.
   - Repeat until they are happy. Two or three rounds is normal.
3. Move on to Step 5.

---

## Step 5: Deploy to Vercel

### Why

The page is on your machine. Deploying to Vercel puts it on the internet with a URL anyone can access.

### What to do

Tell Claude: "Deploy the landing page to Vercel."

Claude will use the Vercel MCP to:
1. Create a new project on Vercel (or use an existing one)
2. Upload the `landing-page/` folder
3. Deploy it
4. Return the live URL (something like `your-project-name.vercel.app`)

This should take under a minute.

---

STOP: Did Claude give you a Vercel URL? Tell me the URL.

---

USER: [Waits for student to share the Vercel URL]

---

ACTION: When the student shares the URL:

1. Say "Open that URL in your browser. Then open it on your phone if you have one nearby. It should work on any device."
2. Move on to Step 6.

---

## Step 6: Verify the live page

### Why

A URL that only works on your machine is not deployed. Check it on a different device or in an incognito window.

### What to do

Open the URL in your browser. Then try it on a different device if possible:
- Your phone
- An incognito/private browser window
- Text the link to someone and ask them to open it

The page should load with your brand name, colors, and content on any device.

---

STOP: Does the page load on a device that is not your laptop? Tell me what you see.

---

USER: [Waits for student to confirm the page loads on another device]

---

ACTION: When the student confirms:

1. If it works, say "Good. You have a live page on the internet. You can share that URL anywhere: email signature, social media bio, business card."
2. If it does not load:
   - Check the URL is correct (no typos)
   - Ask Claude to check the deployment status through Vercel MCP
   - Try redeploying
3. Move on to the end-of-lesson check.

---

## End-of-lesson check

- Vercel MCP is connected
- `landing-page/index.html` and `landing-page/styles.css` exist
- The page shows your brand name, colors, and content
- The `*.vercel.app` URL loads on any device
- `.claude/skills/landing-page/SKILL.md` exists

---

## Common stumbles

- **"Vercel says the deployment failed"** -- Make sure `npm run build` succeeds locally first. Check that the `landing-page/` folder has a valid `package.json` and Vite config. Vercel auto-detects Vite but needs the build output in `dist/`.
- **"shadcn/ui components not found"** -- Run `npx shadcn@latest add button card badge` to add the components you need.
- **"The page looks wrong on mobile"** -- Tailwind makes responsive easy. Add `sm:`, `md:` prefixes to classes. Ask Claude to fix the specific section.
- **"The colors do not match my brand"** -- Check `tailwind.config.js` — the brand hex codes should be in the `extend.colors` section.
- **"I cannot open the URL on my phone"** -- Make sure you are not on a VPN or corporate network that blocks Vercel. Try a different network or use mobile data.

---

## What just happened

You built a landing page from your brand guidelines and content, then deployed it to the internet in one command. No HTML knowledge needed. No design skills. No hosting setup. Claude read your brand context and content, built the page, and Vercel put it online.

You now have seven of eight agents working. One lesson left: connecting everything into one command and wrapping up.

---

## When you're ready

Type: **Start Lesson 8**

The final lesson. You will build a master command that chains your agents together, then look at where to take this next.

---

ACTION: When the student says they are ready for Lesson 8, read the file at `lesson-modules/8-content-publisher/CLAUDE.md` and begin.
