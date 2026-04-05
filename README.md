# Personal Jekyll Blog

A clean, fast personal blog built with Jekyll for GitHub Pages.  
4 pages · weekly post feature · SEO-ready · no CMS needed.

---

## 🚀 One-Time Setup

### 1. Install Jekyll locally (for previewing)
```bash
gem install bundler jekyll
bundle install
bundle exec jekyll serve
# → open http://localhost:4000
```

### 2. Create your GitHub repo
- Go to github.com → **New repository**
- Name it exactly: `yourusername.github.io`
- Set to **Public** → **Create repository**

### 3. Push your site
```bash
git init
git add .
git commit -m "Launch site"
git branch -M main
git remote add origin https://github.com/yourusername/yourusername.github.io.git
git push -u origin main
```

### 4. Enable GitHub Pages
- Go to your repo → **Settings** → **Pages**
- Under **Source**, choose **GitHub Actions**
- That's it — the workflow in `.github/workflows/deploy.yml` handles everything

Your site goes live at `https://yourusername.github.io` within ~2 minutes of every push.

---

## ✍️ How to Add a Weekly Post

Create one file in `_posts/` named with this exact format:

```
_posts/YYYY-MM-DD-your-post-title.md
```

Paste this front matter at the top, then write your post in Markdown below:

```markdown
---
layout: post
title: "Your Post Title"
date: 2025-05-05
tag: Essay
read_time: "5 min read"
excerpt: "One or two sentence summary shown on the blog listing page."
---

Your post content here in regular Markdown.

## A subheading

More paragraphs...

> A blockquote looks like this.

A **bold** word or an *italic* word.
```

**Available tags:** `Essay`, `Books`, `Travel`, `Reflection` — or invent your own.  
The tag filter on the Chronicles page updates automatically.

**That's it.** Commit and push. GitHub Actions builds and deploys automatically.

---

## 📁 File Structure

```
/
├── _config.yml              ← Site settings (name, URL, social links)
├── Gemfile                  ← Ruby dependencies
├── index.md                 ← Home page (static — no posts shown here)
├── about.md                 ← About page
├── chronicles.md            ← Blog listing page (auto-populated)
├── contact.md               ← Contact page
│
├── _layouts/
│   ├── default.html         ← Base HTML wrapper (nav + footer)
│   ├── home.html            ← Home layout
│   ├── page.html            ← About / Contact layout
│   ├── chronicles.html      ← Blog listing with pagination + tag filter
│   └── post.html            ← Single post reader
│
├── _includes/
│   ├── nav.html             ← Navigation bar
│   ├── footer.html          ← Footer
│   └── post-card.html       ← Reusable post card component
│
├── _posts/                  ← ⭐ YOUR WEEKLY POSTS GO HERE
│   ├── 2025-04-07-first-thoughts.md
│   ├── 2025-04-14-reading-on-trains.md
│   └── 2025-04-21-reading-england.md
│
├── assets/
│   ├── css/main.scss        ← All styles (compiled by Jekyll)
│   └── js/main.js           ← Nav, scroll effects
│
└── .github/workflows/
    └── deploy.yml           ← Auto-deploy on every git push
```

---

## 🔧 Personalisation

### Change your name, tagline, email
Edit `_config.yml` — these values flow into every page automatically:
```yaml
title: "Your Name"
tagline: "Your tagline here"
email: "you@example.com"
twitter_username: yourhandle
```

### Add your photo (About page)
1. Drop `photo.jpg` into `assets/img/`
2. Open `about.md` and replace the `portrait-placeholder` div with:
```html
<img src="/assets/img/photo.jpg" alt="Your name" class="portrait-img">
```

### Set up the contact form
1. Sign up free at [formspree.io](https://formspree.io)
2. Create a form — copy the form ID (looks like `xpwzabcd`)
3. Open `contact.md` and replace `YOUR_FORM_ID`:
```html
action="https://formspree.io/f/xpwzabcd"
```

### Update canonical URLs
In `_config.yml`, set your actual GitHub Pages URL:
```yaml
url: "https://yourusername.github.io"
```

---

## 🔗 SEO & Backlinks

- Post URLs are **stable and permanent**: `/chronicles/YYYY/MM/DD/post-title/`
- The `jekyll-seo-tag` plugin auto-generates meta tags, Open Graph, and Twitter Cards
- The `jekyll-sitemap` plugin auto-generates `/sitemap.xml`
- The `jekyll-feed` plugin auto-generates `/feed.xml` (RSS)
- Never rename a published post file — the URL is the filename

---

## 💾 Backup Before Changes

```bash
git checkout -b backup-before-redesign
git push origin backup-before-redesign
```

Your backup lives as a branch in GitHub forever. To restore:
```bash
git checkout backup-before-redesign
```
