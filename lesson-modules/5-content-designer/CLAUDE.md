# Lesson 5: Visuals Without a Designer

**Time: ~20 min**

**You'll finish with:** A content designer skill that generates brand-consistent visuals using the OpenRouter images plugin. Two images saved to your project, and NocoDB entries updated to "Designed."

---

## The moment you're in

You have written content. Social posts with captions. Articles with headlines. But no visuals. Every post needs an image, and right now you have none.

In the next twenty minutes you will build a designer agent that creates brand-consistent images. It reads your brand guidelines for colors and style, reads the content piece for context, and generates an image that fits. No design skills needed. No Canva. No stock photos.

The best part: you already installed the OpenRouter plugin in Lesson 1. It includes image generation. No new accounts to create.

---

ACTION: Greet the student and confirm Lesson 4 is done. Specifically check:

1. Do at least 3 content files exist in the `content/` folder?
2. Is the brand guidelines file still at `brand/brand-guidelines.md` with a Visual Identity section?

If either is missing, send them back to fix it. Do not continue.

If both are good, say "Let us give your content some visuals. No new accounts needed. OpenRouter handles the image generation."

---

USER: [Waits for student to confirm Lesson 4 is done]

---

## What you're going to do

1. Create a content designer skill
2. Generate a visual for one of your social posts
3. Review and refine the image
4. Generate a second visual for a different content piece
5. Update NocoDB statuses to "Designed"

Go in order.

---

## Step 1: Create the content designer skill

### Why

The designer skill translates your brand's visual identity into image generation prompts. Instead of you learning how to write AI image prompts, the skill handles that. It reads your brand colors, style direction, and the content context, then builds a detailed prompt that produces on-brand images.

### What to do

Create the skill file at `.claude/skills/content-designer/SKILL.md` with this content:

```markdown
# Content Designer

## Purpose
Generate brand-consistent visual designs for content pieces. Read the brand's visual identity and the content context, then create images using the OpenRouter images plugin.

## Inputs
- A content piece from the `content/` folder (or a content calendar entry)
- Brand guidelines from `brand/brand-guidelines.md` (especially the Visual Identity section)

## Process

1. Read `brand/brand-guidelines.md` for visual identity: colors, style direction, typography guidance.
2. Read the content piece to understand the topic, mood, and message.
3. Build a detailed image generation prompt that includes:
   - Subject matter relevant to the content
   - Brand colors (reference specific hex codes or color names)
   - Style direction from the brand guidelines
   - Composition guidance (clean, professional, social-media-ready)
   - "Do not include any text or words in the image"

4. Use the OpenRouter images plugin to generate the image. Use model `openai/gpt-5.4-image-2` — it produces the best quality results. Specify the aspect ratio for the platform:
   - Instagram Post: `--aspect-ratio 1:1`
   - Instagram Story/Reel: `--aspect-ratio 9:16`
   - Facebook/LinkedIn: `--aspect-ratio 16:9`
   - Blog header: `--aspect-ratio 16:9`
   - YouTube thumbnail: `--aspect-ratio 16:9`

   Save directly to the designs folder with: `--output designs/[content-title-slug].png`

5. Update the NocoDB entry status from "Drafted" to "Designed".

## Prompt template

Use this structure for image prompts:

"A [style direction from brand guidelines] image for a [platform] post about [topic from content]. Colors: [brand colors]. Style: [brand style direction]. Mood: [derived from content tone]. Composition: clean, professional, suitable for social media. Do not include any text or words in the image."

## Notes
- The OpenRouter images plugin handles the actual generation. Just describe what you want and it will generate it.
- Never include text or words in the generated image. Text overlays are added separately.
- The image should work as a standalone visual even without the caption.
- Keep the style consistent across images. If the brand style is "minimal and clean", every image should be minimal and clean.
- Save the prompt used alongside the image (in a comment in the content file or a separate .txt file) so it can be refined later.
```

---

STOP: Confirm the skill file exists at `.claude/skills/content-designer/SKILL.md`.

---

USER: [Waits for student to confirm the skill file exists]

---

ACTION: When the student confirms:

1. If the skill exists, say "Good. Let us generate your first brand visual."
2. If it does not exist, check the file path.
3. Move on to Step 2.

---

## Step 2: Generate a visual for a social post

### Why

Start with a social post image. It is the simplest format (square, single image, clear subject) and the quickest to evaluate.

### What to do

Pick a social post from your `content/` folder. One with a clear topic works best.

Tell Claude: "Design a visual for [content piece title]."

Claude will read the brand guidelines, read the content, build an image prompt, and generate the image using the OpenRouter images plugin.

This may take a minute. Image generation is slower than text.

---

STOP: Can you see the generated image? Answer these questions:

1. Does it match your brand colors?
2. Does the style feel right for your brand?
3. Would you post this alongside the content you wrote?

---

USER: [Waits for student to review the first image]

---

ACTION: When the student responds:

1. If the image matches their brand and they would use it, say "Good. The brand guidelines are translating into visuals."
2. If the colors are wrong:
   - Check the Visual Identity section in brand-guidelines.md. Are the hex codes correct?
   - Adjust the image prompt to explicitly name the colors.
3. If the style feels wrong:
   - Ask what specifically is off. Too corporate? Too playful? Too busy?
   - Adjust the style direction in the prompt and regenerate.
4. If the image has text or words in it, regenerate with an explicit "no text, no words, no letters" instruction in the prompt.
5. Move on to Step 3 once they have an image they are happy with.

---

## Step 3: Refine and iterate

### Why

First-generation images rarely land perfectly. The value of AI image generation is the speed of iteration. Getting from "not quite right" to "that works" takes two minutes, not two days.

### What to do

If the student wanted changes in Step 2, make them now. Common adjustments:

- "Make it warmer / cooler"
- "Less busy, more minimal"
- "Different composition, show [specific thing]"
- "The style should be more like [brand they admire]"

Regenerate until the student says it works. Two or three rounds is normal.

Make sure the final image is saved to `designs/[content-title-slug].[extension]`.

---

## Step 4: Generate a second visual

### Why

One image is a test. Two images show whether the brand style is consistent. If both images feel like they belong to the same brand, the skill is working.

### What to do

Pick a different content piece from `content/`. Ideally a different format or topic so the images are not too similar in subject matter.

Tell Claude: "Design a visual for [second content piece title]."

Review the result. The key question is: do these two images feel like they come from the same brand?

---

STOP: Look at both images side by side. Do they feel like they belong to the same brand? Or does one look like it came from a different company? Tell me.

---

USER: [Waits for student to compare the two images]

---

ACTION: When the student responds:

1. If both images feel cohesive, say "Good. Your brand visual style is consistent. Every image the designer generates from here will follow the same guidelines."
2. If they look inconsistent:
   - The style direction in brand-guidelines.md may be too vague. Add more specific language about the visual style.
   - Consider adding example prompts or reference descriptions to the skill file.
   - Regenerate the weaker image with a more specific prompt.
3. Make sure both images are saved in the `designs/` folder.
4. Move on to Step 5.

---

## Step 5: Update NocoDB statuses

### Why

Same pattern as Lesson 4. The content calendar tracks progress. "Designed" means the content piece has both copy and a visual ready.

### What to do

Tell Claude: "Update the NocoDB status to 'Designed' for the two entries we just created visuals for."

---

STOP: Open NocoDB in your browser. Check the two entries. Do they now show Status = "Designed"? Tell me.

---

USER: [Waits for student to confirm statuses are updated]

---

ACTION: When the student confirms:

1. If updated, say "Good. You can see at a glance: Planned, Drafted, Designed. The pipeline is moving."
2. If not updated, troubleshoot the NocoDB connection.
3. Move on to the end-of-lesson check.

---

## End-of-lesson check

- `.claude/skills/content-designer/SKILL.md` exists
- At least 2 images are in the `designs/` folder
- The images match your brand colors and style
- NocoDB entries for the designed content show Status = "Designed"

---

## Common stumbles

- **"OpenRouter says the image model is not available"** -- The default model may have changed. Ask Claude to search for available image-capable models on OpenRouter using the models plugin. You can specify a different model with `--model model-id` when generating.
- **"The image has text or words in it"** -- Add "no text, no words, no letters, no typography" to the prompt. Some models add text by default.
- **"The colors do not match my brand"** -- Use specific hex codes in the prompt, not just color names. "Background color #1a365d" is more precise than "dark blue."
- **"The images look completely different from each other"** -- The style direction needs to be more specific. Add phrases like "consistent flat illustration style" or "photorealistic with natural lighting" to anchor the style.

---

## What just happened

You built a designer agent that generates brand-consistent visuals without any design skills. It reads your brand guidelines, understands the content context, and produces images that match your style. The same OpenRouter plugin you installed in Lesson 1 handles the image generation.

Two of your content calendar entries now have both copy and visuals. In the next lesson, you will take one of your video scripts and turn it into an actual video with an AI avatar presenter.

---

## When you're ready

Type: **Start Lesson 6**

You will connect HeyGen and build a video maker that turns your scripts into AI avatar videos.

---

ACTION: When the student says they are ready for Lesson 6, read the file at `lesson-modules/6-video-maker/CLAUDE.md` and begin.
