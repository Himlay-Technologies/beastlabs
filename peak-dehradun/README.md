# Peak Dehradun — Climbing + Boxing Landing Page

A single-page Next.js site for the two activities, with a dark "liquid
glass" look (frosted, tilting glass cards), a sandstone-amber accent for
climbing and an impact-red accent for boxing, and a hand-drawn "crack"
line that visually ties the two disciplines together.

Both CTA buttons ("Book a Climbing Slot" / "Book a Boxing Slot") open a
**separate Google Form in a new tab** — Forms handle signup traffic fine,
so the free Vercel tier only ever has to serve the static landing page,
never process form submissions.

## 1. Add your real Google Forms

Open `app/page.tsx` and edit the four constants at the top of the file:

```ts
const CLIMB_FORM_URL = "https://forms.gle/REPLACE_WITH_CLIMBING_FORM_ID";
const BOX_FORM_URL = "https://forms.gle/REPLACE_WITH_BOXING_FORM_ID";
const CLIMB_INSTAGRAM = "https://www.instagram.com/gripdt/";
const BOX_INSTAGRAM = "https://www.instagram.com/peak_boxing_promotion/";
```

To get a `forms.gle` short link: open your Google Form → **Send** → the
link icon → check **Shorten URL**.

## 2. About the visuals

I can't reach Instagram from this environment, so I couldn't pull your
actual photos/reels — instead the two panels use original SVG line-art
(chalk holds for climbing, gloves + ropes for boxing) inside the glass
cards, so there's nothing here that reproduces someone else's copyrighted
photography.

To swap in your own photos once you have them:

1. Drop images into `public/images/` (e.g. `climbing.jpg`, `boxing.jpg`).
2. In `app/page.tsx`, replace `<ClimbHoldsArt />` or `<GloveRopesArt />`
   with an `<img src="/images/climbing.jpg" className="w-full h-full
   object-cover rounded-2xl" />` (or use `next/image` for optimization).

Short vertical clips work well too — swap the `<img>` for a muted,
autoplaying `<video>` tag pointed at a file in `public/videos/`.

## 3. Run it locally

```bash
npm install
npm run dev
```

Visit `http://localhost:3000`.

## 4. Deploy to Vercel (free tier)

```bash
npm install -g vercel
vercel
```

Or connect the GitHub repo directly at vercel.com → **New Project**. No
environment variables are needed — everything is a static page plus two
external links to your Google Forms.

## Structure

```
app/
  layout.tsx      fonts (Bebas Neue / Inter / JetBrains Mono) + metadata
  page.tsx         the whole landing page (hero, climbing, boxing, footer)
  globals.css      liquid-glass, grain, tilt, and crack-line styles
public/images/     drop your real photos here (optional)
```
