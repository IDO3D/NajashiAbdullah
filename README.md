# Najashi Abdullah — Studio Site

A two-practice studio site: graphic design + growth marketing, with a chooser landing page as the entry point.

## Site map

```
najashiabdullah.us/             ← Landing page (chooser, two cards)
najashiabdullah.us/design/      ← Graphic design portfolio
najashiabdullah.us/marketing/   ← Growth marketing site
```

## File structure

```
najashi-site/
├── index.html                  ← The chooser landing page
├── README.md
├── design/
│   ├── index.html              ← Full graphic design portfolio
│   └── images/                 ← 22 portfolio pieces (work-01.jpg through work-22.jpg)
└── marketing/
    └── index.html              ← Growth marketing site (placeholder content — replace as needed)
```

Each subsite has a navigation back to the studio home (logo top-left) and a quick "↔" switcher in the nav to jump between practices.

## Deployment to GitHub + najashiabdullah.us

### 1. Create a single repo

Go to github.com → New repo → name it `najashiabdullah-studio` (or whatever you want) → Public → Create.

Upload everything in this folder (`index.html`, `README.md`, the `design/` folder, the `marketing/` folder) to the repo. Easiest method: drag-and-drop the contents into the GitHub upload box.

### 2. Enable GitHub Pages

Repo → **Settings → Pages** → Source: **Deploy from a branch** → Branch: `main`, folder `/ (root)` → Save.

You'll get a URL like `yourusername.github.io/najashiabdullah-studio` within a minute.

### 3. Connect your custom domain (Namecheap)

In the same Pages settings, under **Custom domain**, type: `najashiabdullah.us` → Save.

Then in Namecheap → Domain List → Manage `najashiabdullah.us` → **Advanced DNS**, add these records:

| Type | Host | Value | TTL |
|---|---|---|---|
| A Record | @ | 185.199.108.153 | Automatic |
| A Record | @ | 185.199.109.153 | Automatic |
| A Record | @ | 185.199.110.153 | Automatic |
| A Record | @ | 185.199.111.153 | Automatic |
| CNAME Record | www | YOUR_USERNAME.github.io | Automatic |

⚠ Replace `YOUR_USERNAME` with your actual GitHub username. The CNAME value ends in `.github.io` only — no repo name, no slashes, no `https://`.

### 4. Enforce HTTPS

Wait 10–60 minutes for DNS to propagate, then go back to GitHub → Settings → Pages and tick **Enforce HTTPS** (it'll be grayed out until DNS propagates and SSL is auto-provisioned).

### Want a subdomain instead?

If you'd rather keep the studio chooser at `portfolio.najashiabdullah.us` and leave `najashiabdullah.us` for something else, use this in Namecheap instead of the A records:

| Type | Host | Value |
|---|---|---|
| CNAME Record | portfolio | YOUR_USERNAME.github.io |

And in GitHub Pages → Custom domain, use `portfolio.najashiabdullah.us`.

---

## Things to update before launching

Open files in any text editor and find-and-replace these strings across all three HTML files:

- `hello@najashi.design` → your real email
- `instagram.com/najashiabdullah` → your real Instagram URL
- `twitter.com/najashiabdullah` → your real X/Twitter URL
- `linkedin.com/in/najashiabdullah` → your real LinkedIn URL
- `behance.net/najashiabdullah` → your real Behance URL
- `Starts at $50` / `Starts at $200` → your actual rates (in `design/index.html`)

## Marketing site — placeholder content

The marketing site (`marketing/index.html`) currently has **placeholder copy** for capabilities and case studies. There's a yellow "Editor's Note" band on the page reminding you to replace the content. To go live with marketing:

1. Replace the three Capability cards with your actual offerings
2. Replace the four Case Study cards with real campaign work — each card supports a title, one-line description, and a "case study #" number
3. Delete the `<!-- PLACEHOLDER NOTICE -->` band when ready
4. Update the contact form's engagement options if needed

If you have an existing growth marketing HTML file you want to drop in instead, just replace the contents of `marketing/index.html` with your file. As long as your file uses the same logo link path (`href="../"`) and a switcher to `../design/`, the studio navigation stays unified.

## Customizing the look

All design tokens live in the `:root` CSS block at the top of every HTML file:

- `--bg` — cream background
- `--ink` — text near-black
- `--accent` — cobalt blue (italic words, hover states)

Change `--accent` to swap the entire site's accent color in one shot. Make sure to change it in all three files.

## Adding new graphic design work

In `design/index.html`, find the `const projects = [` array near the bottom of the script section. Each project is one object — copy the shape, drop a new image into `design/images/`, and the grid + filters update automatically.

```js
{
  id: 23,
  num: 23,
  title: "Project Name",
  subtitle: "Subtitle line · 2026",
  category: "edit",          // edit | campaign | stats | study
  categoryLabel: "Player Edit",
  year: "2026",
  format: "4:5 — Instagram",
  tools: ["Photoshop", "Illustrator"],
  description: "Two or three sentences...",
  img: "images/work-23.jpg"
}
```

---

Two practices, one studio. ✦
