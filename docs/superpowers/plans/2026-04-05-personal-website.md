# Personal Professional Website Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a minimal personal website with blog for Fatima Mojaddidy, deployed to Netlify via Hugo.

**Architecture:** Static site built with Hugo, hosted on Netlify free tier. Single home page with scrollable sections (hero, journey, what I do, experience, contact). Blog uses Hugo page bundles with markdown posts. Minimal custom templates with clean default CSS, designed to be easily re-themed later.

**Tech Stack:** Hugo (static site generator), Netlify (hosting), Markdown (content), Git/GitHub (source control + deploy trigger)

---

## File Map

| File | Responsibility |
|------|---------------|
| `hugo.toml` | Site config: title, base URL, menus, params |
| `netlify.toml` | Netlify build config: Hugo version, build command, publish dir |
| `layouts/_default/baseof.html` | Base HTML shell: head, nav, footer, CSS link |
| `layouts/index.html` | Home page template: renders scrollable sections |
| `layouts/blog/list.html` | Blog listing: shows all posts with date + description |
| `layouts/blog/single.html` | Single blog post template |
| `layouts/partials/head.html` | HTML head: meta tags, CSS, open graph |
| `layouts/partials/nav.html` | Navigation bar: site title + blog link |
| `layouts/partials/footer.html` | Footer: contact links |
| `assets/css/style.css` | Minimal default stylesheet (easy to re-theme) |
| `content/_index.md` | Home page content: all sections in markdown |
| `content/blog/_index.md` | Blog list page metadata |
| `content/blog/agentic-sdlc-workshop/index.md` | First blog post (placeholder for Fatima to write) |
| `.gitignore` | Ignore public/, resources/, .hugo_build.lock, .superpowers/ |

---

### Task 1: Install Hugo and Initialize Project

**Files:**
- Create: `.gitignore`
- Create: `hugo.toml`

- [ ] **Step 1: Install Hugo via Homebrew**

Run:
```bash
brew install hugo
```
Expected: Hugo installs successfully.

- [ ] **Step 2: Verify Hugo version**

Run:
```bash
hugo version
```
Expected: Output shows Hugo version (v0.140+ expected).

- [ ] **Step 3: Initialize git repo**

Run:
```bash
cd /Users/fatima/git/srely.dev
git init
```
Expected: `Initialized empty Git repository`

- [ ] **Step 4: Create .gitignore**

Create `.gitignore`:
```
public/
resources/
.hugo_build.lock
.superpowers/
.DS_Store
```

- [ ] **Step 5: Create Hugo config**

Create `hugo.toml`:
```toml
baseURL = "https://example.netlify.app/"
languageCode = "en-us"
title = "Fatima Mojaddidy"

[params]
  description = "Senior Site Reliability Engineer. From film school to Pixar to cloud-native infrastructure."
  email = "fatima.mojaddidy@gmail.com"
  linkedin = "https://www.linkedin.com/in/fatimamojaddidy"
  github = "https://github.com/fat0"

[menu]
  [[menu.main]]
    name = "Blog"
    url = "/blog/"
    weight = 1
```

- [ ] **Step 6: Verify Hugo can build (empty site)**

Run:
```bash
hugo
```
Expected: Build succeeds (warnings about no layouts are OK at this stage).

- [ ] **Step 7: Commit**

```bash
git add .gitignore hugo.toml
git commit -m "chore: initialize Hugo project with config"
```

---

### Task 2: Base Layout and CSS

**Files:**
- Create: `layouts/_default/baseof.html`
- Create: `layouts/partials/head.html`
- Create: `layouts/partials/nav.html`
- Create: `layouts/partials/footer.html`
- Create: `assets/css/style.css`

- [ ] **Step 1: Create the head partial**

Create `layouts/partials/head.html`:
```html
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>{{ if .IsHome }}{{ .Site.Title }}{{ else }}{{ .Title }} | {{ .Site.Title }}{{ end }}</title>
<meta name="description" content="{{ with .Description }}{{ . }}{{ else }}{{ .Site.Params.description }}{{ end }}">
{{ $style := resources.Get "css/style.css" | minify }}
<link rel="stylesheet" href="{{ $style.RelPermalink }}">
```

- [ ] **Step 2: Create the nav partial**

Create `layouts/partials/nav.html`:
```html
<nav>
  <a href="/" class="site-title">{{ .Site.Title }}</a>
  <ul>
    {{ range .Site.Menus.main }}
      <li><a href="{{ .URL }}">{{ .Name }}</a></li>
    {{ end }}
  </ul>
</nav>
```

- [ ] **Step 3: Create the footer partial**

Create `layouts/partials/footer.html`:
```html
<footer>
  <p>
    <a href="{{ .Site.Params.linkedin }}">LinkedIn</a> ·
    <a href="{{ .Site.Params.github }}">GitHub</a> ·
    <a href="mailto:{{ .Site.Params.email }}">Email</a>
  </p>
</footer>
```

- [ ] **Step 4: Create the base layout**

Create `layouts/_default/baseof.html`:
```html
<!DOCTYPE html>
<html lang="{{ .Site.LanguageCode }}">
<head>
  {{ partial "head.html" . }}
</head>
<body>
  {{ partial "nav.html" . }}
  <main>
    {{ block "main" . }}{{ end }}
  </main>
  {{ partial "footer.html" . }}
</body>
</html>
```

- [ ] **Step 5: Create minimal default CSS**

Create `assets/css/style.css`:
```css
/* Reset */
*, *::before, *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

/* Base */
body {
  font-family: system-ui, -apple-system, sans-serif;
  line-height: 1.6;
  max-width: 700px;
  margin: 0 auto;
  padding: 2rem 1rem;
  color: #222;
  background: #fff;
}

/* Nav */
nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 3rem;
  padding-bottom: 1rem;
  border-bottom: 1px solid #eee;
}

nav .site-title {
  font-weight: 700;
  text-decoration: none;
  color: #222;
}

nav ul {
  list-style: none;
  display: flex;
  gap: 1.5rem;
}

nav a {
  color: #555;
  text-decoration: none;
}

nav a:hover {
  color: #222;
}

/* Main content */
h1 { font-size: 2rem; margin-bottom: 0.5rem; }
h2 { font-size: 1.4rem; margin-top: 2.5rem; margin-bottom: 0.5rem; }
h3 { font-size: 1.1rem; margin-top: 1.5rem; margin-bottom: 0.5rem; }

p { margin-bottom: 1rem; }

ul, ol {
  margin-bottom: 1rem;
  padding-left: 1.5rem;
}

a { color: #0066cc; }
a:hover { color: #004499; }

/* Sections */
section {
  margin-bottom: 3rem;
}

/* Footer */
footer {
  margin-top: 4rem;
  padding-top: 1rem;
  border-top: 1px solid #eee;
  font-size: 0.9rem;
  color: #777;
}

footer a {
  color: #555;
  text-decoration: none;
}

footer a:hover {
  color: #222;
}

/* Blog list */
.post-list {
  list-style: none;
  padding: 0;
}

.post-list li {
  margin-bottom: 1.5rem;
}

.post-list a {
  font-size: 1.1rem;
  font-weight: 600;
  text-decoration: none;
}

.post-list time {
  display: block;
  font-size: 0.85rem;
  color: #888;
}

.post-list .description {
  font-size: 0.95rem;
  color: #555;
  margin-top: 0.25rem;
}

/* Blog post */
article time {
  display: block;
  font-size: 0.9rem;
  color: #888;
  margin-bottom: 2rem;
}

article img {
  max-width: 100%;
  height: auto;
  border-radius: 4px;
  margin: 1rem 0;
}

/* Code blocks */
pre {
  background: #f5f5f5;
  padding: 1rem;
  border-radius: 4px;
  overflow-x: auto;
  margin-bottom: 1rem;
  font-size: 0.9rem;
}

code {
  font-family: 'SF Mono', Menlo, monospace;
  font-size: 0.9em;
}

p code {
  background: #f5f5f5;
  padding: 0.15rem 0.3rem;
  border-radius: 3px;
}
```

- [ ] **Step 6: Verify Hugo builds with layouts**

Run:
```bash
hugo
```
Expected: Build succeeds with no errors.

- [ ] **Step 7: Commit**

```bash
git add layouts/ assets/
git commit -m "feat: add base layout, partials, and minimal CSS"
```

---

### Task 3: Home Page

**Files:**
- Create: `layouts/index.html`
- Create: `content/_index.md`

- [ ] **Step 1: Create home page template**

Create `layouts/index.html`:
```html
{{ define "main" }}
  <section id="intro">
    <h1>{{ .Title }}</h1>
    {{ with .Params.subtitle }}<p class="subtitle">{{ . }}</p>{{ end }}
  </section>

  {{ .Content }}

  <section id="contact">
    <h2>Get in Touch</h2>
    <p>
      <a href="{{ .Site.Params.linkedin }}">LinkedIn</a> ·
      <a href="{{ .Site.Params.github }}">GitHub</a> ·
      <a href="mailto:{{ .Site.Params.email }}">{{ .Site.Params.email }}</a>
    </p>
  </section>
{{ end }}
```

- [ ] **Step 2: Create home page content**

Create `content/_index.md`:
```markdown
---
title: "Fatima Mojaddidy"
subtitle: "Senior Site Reliability Engineer"
---

## The Journey

I studied film production, then spent years building the infrastructure behind animated films — managing render pipelines and scaling storage from terabytes to petabytes. That path led me from visual effects into cloud infrastructure and eventually into Site Reliability Engineering.

Twenty years later, I'm still doing the same thing at the core: building systems that let people do their best work without worrying about what's underneath.

## What I Do

I build and maintain scalable, resilient infrastructure. My focus areas:

- **Infrastructure as Code & automation** — Terraform, Ansible, eliminating toil
- **Observability & SLOs** — Datadog, Prometheus, Grafana — if you can't see it, you can't fix it
- **Container orchestration & deployment patterns** — designing how code gets to production safely
- **Disaster recovery & platform resiliency** — automated failover, blue/green deployments
- **Cloud-native infrastructure** — AWS, OCI, GCP

## Experience

Over 20 years of building infrastructure — from rendering pipelines for animated films to disaster recovery for cloud platforms. I've scaled storage systems to petabytes, built automated failover across AWS regions, designed blue/green deployment architectures, contributed to cluster lifecycle tooling in Go, and migrated legacy systems to modern automation.

I advocate for eliminating operational toil and making developers' lives easier. The best infrastructure is the kind nobody has to think about.
```

- [ ] **Step 3: Run Hugo dev server and verify**

Run:
```bash
hugo server -D
```
Expected: Server starts at `http://localhost:1313`. Home page renders with all sections: title, subtitle, journey, what I do, experience, and contact links in footer.

- [ ] **Step 4: Stop dev server (Ctrl+C) and commit**

```bash
git add layouts/index.html content/_index.md
git commit -m "feat: add home page with content sections"
```

---

### Task 4: Blog List and Post Templates

**Files:**
- Create: `layouts/blog/list.html`
- Create: `layouts/blog/single.html`
- Create: `content/blog/_index.md`

- [ ] **Step 1: Create blog list template**

Create `layouts/blog/list.html`:
```html
{{ define "main" }}
  <h1>{{ .Title }}</h1>

  <ul class="post-list">
    {{ range .Pages.ByDate.Reverse }}
      <li>
        <a href="{{ .RelPermalink }}">{{ .Title }}</a>
        <time datetime="{{ .Date.Format "2006-01-02" }}">{{ .Date.Format "January 2, 2006" }}</time>
        {{ with .Description }}<p class="description">{{ . }}</p>{{ end }}
      </li>
    {{ end }}
  </ul>
{{ end }}
```

- [ ] **Step 2: Create blog single post template**

Create `layouts/blog/single.html`:
```html
{{ define "main" }}
  <article>
    <h1>{{ .Title }}</h1>
    <time datetime="{{ .Date.Format "2006-01-02" }}">{{ .Date.Format "January 2, 2006" }}</time>
    {{ .Content }}
  </article>
{{ end }}
```

- [ ] **Step 3: Create blog list page content**

Create `content/blog/_index.md`:
```markdown
---
title: "Blog"
description: "Things I'm learning and thinking about."
---
```

- [ ] **Step 4: Verify blog pages render (empty list for now)**

Run:
```bash
hugo server -D
```
Expected: `http://localhost:1313/blog/` shows "Blog" heading with empty list. No errors.

- [ ] **Step 5: Stop dev server and commit**

```bash
git add layouts/blog/ content/blog/_index.md
git commit -m "feat: add blog list and single post templates"
```

---

### Task 5: First Blog Post (Placeholder)

**Files:**
- Create: `content/blog/agentic-sdlc-workshop/index.md`

- [ ] **Step 1: Create first blog post as page bundle**

```bash
mkdir -p content/blog/agentic-sdlc-workshop
```

Create `content/blog/agentic-sdlc-workshop/index.md`:
```markdown
---
title: "What I Learned from the Agentic SDLC Workshop"
date: 2026-04-05
description: "Notes and takeaways from Liz the Developer's Agentic SDLC workshop at Multiverse School."
draft: true
---

*Coming soon — this post is a work in progress.*
```

Note: `draft: true` means this won't appear on the live site until Fatima writes the content and removes the draft flag. It will show in dev server with the `-D` flag.

- [ ] **Step 2: Verify post renders in dev server**

Run:
```bash
hugo server -D
```
Expected: `http://localhost:1313/blog/` shows the post in the list. Clicking it shows the post page with title, date, and placeholder text.

- [ ] **Step 3: Stop dev server and commit**

```bash
git add content/blog/agentic-sdlc-workshop/
git commit -m "feat: add first blog post placeholder (agentic SDLC workshop)"
```

---

### Task 6: Netlify Configuration

**Files:**
- Create: `netlify.toml`

- [ ] **Step 1: Create Netlify config**

Create `netlify.toml`:
```toml
[build]
  command = "hugo"
  publish = "public"

[build.environment]
  HUGO_VERSION = "0.147.0"

[context.production.environment]
  HUGO_ENV = "production"

[[headers]]
  for = "/*"
  [headers.values]
    X-Frame-Options = "DENY"
    X-Content-Type-Options = "nosniff"
    Referrer-Policy = "strict-origin-when-cross-origin"
```

Note: Check the installed Hugo version (`hugo version`) and match `HUGO_VERSION` to it so local and Netlify builds are consistent.

- [ ] **Step 2: Verify Hugo still builds cleanly**

Run:
```bash
hugo
```
Expected: Build succeeds, `public/` directory is created with generated HTML.

- [ ] **Step 3: Commit**

```bash
git add netlify.toml
git commit -m "feat: add Netlify build configuration"
```

---

### Task 7: GitHub Repo and Initial Push

**Files:** None (git operations only)

- [ ] **Step 1: Create GitHub repo**

Run:
```bash
gh repo create srely.dev --public --source=. --push
```
Expected: Repo created at `github.com/fat0/srely.dev` and code pushed.

Note: If Fatima prefers a private repo, use `--private` instead of `--public`. Ask before running.

- [ ] **Step 2: Verify repo exists on GitHub**

Run:
```bash
gh repo view fat0/srely.dev
```
Expected: Shows repo details with all commits.

---

### Task 8: Connect Netlify and Deploy

This task requires manual steps in the Netlify UI.

- [ ] **Step 1: Log into Netlify and connect repo**

1. Go to https://app.netlify.com
2. Click "Add new site" → "Import an existing project"
3. Select GitHub → authorize if needed
4. Select the `srely.dev` repository
5. Build settings should auto-populate from `netlify.toml`:
   - Build command: `hugo`
   - Publish directory: `public`
6. Click "Deploy site"

- [ ] **Step 2: Wait for deploy and verify**

Netlify will assign a random subdomain (e.g., `random-name.netlify.app`). Visit the URL and verify:
- Home page loads with all sections
- Nav shows "Fatima Mojaddidy" and "Blog" link
- Blog page loads (empty — draft post won't show)
- Footer links work (LinkedIn, GitHub, Email)

- [ ] **Step 3: Update Hugo config with actual Netlify URL**

Edit `hugo.toml` and replace the `baseURL`:
```toml
baseURL = "https://YOUR-SITE-NAME.netlify.app/"
```

- [ ] **Step 4: Commit and push**

```bash
git add hugo.toml
git commit -m "chore: update baseURL to actual Netlify domain"
git push
```

Expected: Netlify auto-deploys with the updated config.

---

### Task 9: Final Verification

- [ ] **Step 1: Verify live site**

Visit the Netlify URL and check:
- Home page: hero, journey, what I do, experience, contact sections all render
- Navigation: "Fatima Mojaddidy" links home, "Blog" links to /blog/
- Blog page: loads with heading (no posts visible since draft)
- Footer: LinkedIn, GitHub, and email links are correct and work
- Mobile: site is responsive (check on phone or browser dev tools)

- [ ] **Step 2: Verify blog workflow**

Test that the blog workflow works end-to-end:
1. Edit `content/blog/agentic-sdlc-workshop/index.md` — change `draft: true` to `draft: false`
2. Commit and push
3. Verify the post appears on the live blog page

Then revert back to `draft: true` and push again (Fatima will publish when the content is ready).

- [ ] **Step 3: Done**

The site is live. Next steps for Fatima:
- Write blog post content
- Visual design session (colors, typography, aesthetic)
- Optionally: custom domain, analytics, additional pages
