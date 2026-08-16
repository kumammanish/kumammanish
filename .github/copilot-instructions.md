# Copilot Instructions for kumammanish Profile Repository

This is a personal GitHub profile portfolio repository showcasing professional experience, certifications, and projects. The primary content is a comprehensive README.md that serves as the public-facing profile.

## Repository Overview

- **Primary file**: `README.md` - The GitHub profile page (automatically displayed on github.com/kumammanish)
- **Supporting docs**: `docs/resume.md` - Detailed resume in markdown (also renders as `docs/resume.html`)
- **Assets**: Profile images and badge assets in `assets/`
- **Workflows**: GitHub Actions for markdown validation and achievement bot orchestration

## Markdown Content & Conventions

The README follows this structure:
1. **Header section** - Name, title badges, profile view counter
2. **About Me** - Bulleted highlights (FinOps, Automation, IaC expertise)
3. **Tech Stack & Tooling** - Badge-based visual tech display (Azure, Kubernetes, Terraform, etc.)
4. **Featured Projects** - Key achievements with project links
5. **Certifications** - Microsoft certs and achievement badges
6. **GitHub Stats** - Dynamic stats cards from GitHub Actions
7. **Languages** - Spoken languages
8. **Connect** - Social/contact links

When editing README.md:
- Keep the badge-based visual layout for tech stack (HTML img tags with shields.io)
- Maintain consistent heading hierarchy (#, ##, ###)
- Use `<p align="center">` for centered elements and badges
- Update the "Featured Projects" section when new projects emerge
- The resume.md mirrors much of the README content but is more detailed

## Validation & Workflows

### Markdown Linting
The `validate-readme` workflow runs automatically when README.md changes:
```bash
# To validate locally before pushing (requires markdownlint-cli):
npx markdownlint README.md
```

The workflow uses GitHub Super Linter with markdown validation enabled.

### GitHub Achievement Bots (Manual)
The `run-achievement-bots` workflow is manual (`workflow_dispatch`):
- **Purpose**: Run achievement unlocking bots (Pair Shark, Pull Shark) on specified repos
- **Usage**: Requires REPO_TOKEN secret; currently performs dry-run
- **Inputs**:
  - `repo`: Target repository (owner/repo format)
  - `bot`: Which bot to run (pair_shark, pull_shark, all)

## Mermaid Diagrams

When creating, editing, or visualizing diagrams, follow the instructions in `.github/instructions/mermaid.instructions.md`.

Key rules:
- Always validate syntax before presenting diagrams
- Write to `.mmd` files, never return unvalidated Mermaid syntax
- Use `mermaid-diagram-preview` after generating
- Prefer `@mermaid-chart` slash commands for complex diagrams

## Content Edit Tips

- **Resume sync**: Keep `docs/resume.md` aligned with major updates to README.md
- **Links**: Use relative paths for internal links (e.g., `[Resume](./docs/resume.md)`)
- **Badges**: 
  - Local badge images: `assets/badges/{cert-id}.png` (AI-102, AZ-500, AI-900)
  - Dynamic badges: Use shields.io URLs (legacy exams, ITIL, GitHub achievements)
  - Consult `assets/badges/manifest.json` for complete badge metadata
- **Profile image**: Located at `assets/images/profile.png` (used in resume)
- **External links**: Open in new tabs using `target="_blank"` on `<a>` tags

## Badge Management

### Badge Structure
Local Microsoft certification badges are stored in `assets/badges/`:
- **ai-102.png** - Azure AI Engineer Associate (local image, 32KB)
- **az-500.png** - Azure Security Engineer Associate (local image, 49KB)
- **ai-900.png** - Azure AI Fundamentals (local image, 75KB)
- **manifest.json** - Metadata for all badges (cert IDs, Credly URLs, learn.microsoft.com links, download status)

### The Manifest File
`assets/badges/manifest.json` tracks:
- Active certifications (AI-102, AZ-500, AI-900) with local image paths
- Legacy exam badges (533, 534, Azure Infrastructure Solutions) using shields.io dynamic URLs
- Status flags (active/legacy/retired) for easy filtering
- Credly and Microsoft Learn credential URLs for verification

### Adding New Badges
1. Download the badge image (PNG) and save to `assets/badges/{id}.png`
2. Add an entry to the manifest with cert_id, name, status, and local_path
3. Update README.md to reference the badge
4. Ensure badges are NOT in `.gitignore` (PNG files are tracked in Git)

## Analytics & Monitoring

### Profile View Tracking
The README includes a dynamic profile view counter from `komarev.com/ghpvc/`. To monitor trends:
- The badge URL: `https://komarev.com/ghpvc/?username=kumammanish&label=Profile%20Views&color=0e75b6&style=flat-square`
- Track historical views by logging the count over time
- Consider periodic snapshots via GitHub Actions if deeper analytics are needed

### GitHub Stats Cards
The README uses dynamic stats from `github-readme-stats.vercel.app/`:
- **Stats card**: `api?username=kumammanish&show_icons=true&theme=tokyonight`
- **Languages card**: `top-langs/?username=kumammanish&layout=compact&theme=tokyonight`

These auto-update from live GitHub data; no manual maintenance needed.

### Future Analytics Integration
If you need to track profile engagement over time:
- Set up a scheduled GitHub Action to capture view counts
- Use a web scraper MCP to collect periodic snapshots of profile metrics
- Store results in `.github/analytics/` for historical comparison

## No Build/Test Steps

This repository is documentation-only; there are no build, test, or lint commands beyond the markdown validation workflow.
