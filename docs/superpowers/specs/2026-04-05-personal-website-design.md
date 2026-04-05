# Personal Professional Website — Design Spec

**Author:** Fatima Mojaddidy
**Date:** 2026-04-05
**Status:** Draft

## Overview

A minimal personal professional website with a blog. The site serves as a professional home base, showcases Fatima's unique career path (film school → VFX pipeline infrastructure → cloud-native SRE), and provides a platform for sharing technical knowledge. Hosted on Netlify free tier.

The tone is personal and unconventional — not a polished corporate template. The site should feel like Fatima, with her personality and unique perspective coming through. Let the work speak for itself.

## Goals

1. Establish a professional online presence
2. Tell the story of an unconventional career path into SRE
3. Share technical learnings and perspectives via blog
4. Be discoverable by recruiters and peers
5. Keep it minimal — easy to maintain, easy to extend later

## Site Structure

### Single Home Page (/)

One scrollable page with these sections:

1. **Hero/Intro** — Name, title ("Senior Site Reliability Engineer"), a one-liner that captures personality and vibe.

2. **The Journey** — Short narrative of the career arc: Film Production (BFA, Florida State) → VFX/animation pipeline infrastructure → cloud infrastructure → Site Reliability Engineering. This is the differentiator — an unconventional path told in an authentic voice.

3. **What I Do** — Brief overview of expertise areas:
   - Infrastructure as Code & automation
   - Observability & SLOs
   - Container orchestration & deployment patterns
   - Disaster recovery & platform resiliency
   - Cloud-native infrastructure (AWS, OCI, GCP)

4. **Experience** — Focus on *what was built and accomplished*, not company names. Describe the work: building DR automation, designing blue/green deployments, scaling storage from terabytes to petabytes, building cluster lifecycle tooling, eliminating toil through automation. No logo walls, no name-dropping. The work speaks for itself.

5. **Contact** — LinkedIn link, GitHub (github.com/fat0), and email address (fatima.mojaddidy@gmail.com)

### Blog (/blog/)

- **List page** — Posts listed chronologically, newest first. Each entry shows title, date, and a short description.
- **Post pages** — Clean, readable typography. No comments system. No categories or tags to start.
- **Post format** — Markdown files using Hugo page bundles (each post is a folder containing `index.md` and any images).

#### Planned Blog Posts

**Post 1: Agentic SDLC Workshop**
What Fatima learned from Liz the Developer's Agentic SDLC workshop at Multiverse School (taken twice). Especially relevant since this very website is being built using that workflow.

**Post 2: You Don't Need Kubernetes Experience — You Need Orchestration Principles**
A perspective piece arguing that the industry over-indexes on Kubernetes production experience in SRE job requirements. The underlying concepts matter more than the specific tool:
- Container orchestration
- Control plane vs data plane scaling
- Deployment design (getting developer images deployed reliably)
- Autoscaling
- Resiliency and reliability

The post will draw on Fatima's deep experience with the HashiCorp stack (Nomad, Consul, Vault, Terraform) to demonstrate how these same problems are solved without Kubernetes. The core argument: tools change constantly (especially now with AI accelerating everything), but principles are durable. What matters is understanding the concepts, not which tool implements them.

## Tech Stack

- **Hugo** — Static site generator (Go-based, aligns with Fatima's Go expertise)
- **Netlify** — Hosting, free tier, auto-deploys from GitHub on push to `main`
- **Markdown** — Blog post authoring
- **Git/GitHub** — Source control and deployment trigger

### Why Hugo

- Go-based — familiar language for customization
- Blazing fast builds
- Native markdown blog support with page bundles
- First-class Netlify support (zero-config deploy)
- No Node.js, no npm, no build toolchain — single binary
- Mature theme ecosystem for starting points

## Project Structure

```
srely.dev/
├── hugo.toml                # Hugo config (site title, menus, params)
├── content/
│   ├── _index.md            # Home page content
│   └── blog/
│       ├── _index.md        # Blog list page
│       └── agentic-sdlc-workshop/
│           ├── index.md     # First blog post
│           └── (images)     # Co-located post images
├── layouts/                 # Custom Hugo templates
│   ├── index.html           # Home page template
│   ├── _default/
│   │   ├── baseof.html      # Base layout (head, nav, footer)
│   │   └── single.html      # Single page/post template
│   └── blog/
│       └── list.html        # Blog listing template
├── static/                  # Static assets (favicon, etc.)
├── assets/                  # CSS (theme TBD — separate design session)
└── netlify.toml             # Netlify build configuration
```

## Deployment

- **Repository:** `srely.dev` on GitHub
- **Netlify config:** Connect GitHub repo, build command `hugo`, publish directory `public/`
- **Workflow:** Write markdown → push to `main` → Netlify auto-deploys

## Visual Design

**Deferred to a separate session.** The implementation will use a minimal custom layout with clean defaults that are easy to theme later. The visual design session will cover:

- Color palette
- Typography
- Dark/light mode preference
- Overall aesthetic and feel

For now, the layout templates will be built with semantic HTML and minimal CSS that's straightforward to restyle.

## What's Intentionally Excluded

- No phone number on site
- No full resume (LinkedIn for that)
- No projects page (can add later)
- No comment system on blog
- No analytics (can add later)
- No categories/tags on blog (can add later)
- No contact form
- No JavaScript framework
