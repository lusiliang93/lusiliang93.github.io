# Industrial AI Personal Site Bootstrap Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Configure this al-folio site as an English executive research profile and public industrial-AI portfolio for Siliang Lu.

**Architecture:** Keep all personalization in al-folio’s configuration, data, and content collections. The root page supplies the professional narrative and enabled modules; projects are standalone Markdown case studies; configuration and social data control global metadata and contact surfaces. Do not introduce runtime-theme overrides.

**Tech Stack:** Jekyll, al-folio v1.x, YAML front matter/data files, Markdown, Ruby Bundler, npm Prettier.

## Global Constraints

- Keep this site English-language and position Siliang Lu as a Senior Expert at Bosch Corporate Research.
- Present industrial AI across control and optimization, time-series analysis, mobility, and energy.
- Emphasize cross-functional leadership and scalable AI delivering business outcomes or cost reduction.
- Publish only facts, contact details, logos, images, and measurable outcomes explicitly supplied or already verified as public.
- Named Bosch and business-unit case studies are allowed, but private or customer-confidential details must not be published.
- Use `_config.yml`, `_data`, `_pages`, `_projects`, and `_bibliography` before considering a local override.
- Do not create `_layouts`, `_includes`, `_sass`, JavaScript, or runtime-asset overrides.
- Retain a module only when it has genuine public content; hide or remove starter/demo content instead.

---

## File Structure

- Modify: `_config.yml` — public metadata, SEO text, language, global feature switches, and starter-service settings.
- Modify: `_data/socials.yml` — genuine professional links and contact information only.
- Modify: `_pages/about.md` — root-page narrative and module configuration.
- Modify or remove: `_pages/{blog,books,cv,dropdown,news,profiles,repositories,teaching}.md` — navigation and pages that are still starter material.
- Modify or remove: `_news/*.md`, `_posts/*.md`, `_teachings/*.md`, `_projects/*.md` — starter collection content that must not appear as Siliang’s work.
- Create: one Markdown file per approved public industrial-AI case study in `_projects/`, named with its publication date and approved URL slug.
- Modify: `_bibliography/papers.bib` — only to remove non-Siliang demo citations or retain verified public Siliang entries.

### Task 1: Establish accurate global identity and remove placeholder contact surfaces

**Files:**
- Modify: `_config.yml`
- Modify: `_data/socials.yml`

**Interfaces:**
- Consumes: the approved positioning and user-supplied identity/contact information.
- Produces: site-wide title, description, keywords, language, footer, and social-link data consumed by al-folio layouts.

- [ ] **Step 1: Write a failing placeholder scan**

Run:

```bash
rg -n 'A simple, whitespace theme|you@example\.com|1010907|qc6CJjYAAAAJ|Albert Einstein|Custom Social|al-folio' _config.yml _data/socials.yml
```

Expected: matches demonstrate that starter identity, contact, and theme copy remain before configuration.

- [ ] **Step 2: Confirm the public facts required for the edit**

Collect and record the exact public values for:

```text
email address; personal website or LinkedIn URL; Google Scholar ID or public scholar URL;
CV PDF filename/URL; portrait filename; approved short title; approved footer attribution.
```

Expected: no guessed value will be written for any unavailable field; unavailable fields will be omitted or their module disabled.

- [ ] **Step 3: Implement the metadata and social-data update**

In `_config.yml`, set the English description and keywords to describe a Senior Expert at Bosch Corporate Research leading industrial-AI work in control and optimization, time-series analysis, mobility, and energy. Replace generic al-folio description/footer text with concise site-specific copy while retaining accurate Jekyll/GitHub Pages attribution. Disable demo-only external sources, Disqus, and other services not explicitly configured.

In `_data/socials.yml`, delete all example values and add only confirmed social/contact entries. If no CV PDF is supplied, remove `cv_pdf`; if no Google Scholar identifier is supplied, remove `scholar_userid`; remove `custom_social` unless an actual professional destination is supplied.

- [ ] **Step 4: Run the identity scan to verify it passes**

Run:

```bash
rg -n 'you@example\.com|1010907|qc6CJjYAAAAJ|Albert Einstein|Custom Social' _config.yml _data/socials.yml
```

Expected: no output.

- [ ] **Step 5: Commit**

```bash
git add _config.yml _data/socials.yml
git commit -m "feat: personalize site metadata"
```

### Task 2: Build the executive research homepage from real biographical content

**Files:**
- Modify: `_pages/about.md`
- Modify: `_pages/{blog,books,cv,dropdown,news,profiles,repositories,teaching}.md`

**Interfaces:**
- Consumes: Task 1’s global metadata and user-approved biography, portrait, CV, and page availability.
- Produces: the root URL (`/`) with an English professional narrative and a navigation containing only real destinations.

- [ ] **Step 1: Write a failing homepage placeholder scan**

Run:

```bash
rg -n 'Affiliations|555 your office|123 your address|Your City|Write your biography|favorite subreddit|Albert Einstein' _pages/about.md _pages
```

Expected: matches show starter home-page and example-page text before replacement or removal.

- [ ] **Step 2: Implement the root-page front matter and narrative**

Keep `layout: about`, `title: about`, and `permalink: /`. Remove the starter subtitle, address block, biography text, and references to starter assets. Add an English biography containing these verified statements:

```markdown
Siliang Lu is a Senior Expert at Bosch Corporate Research. He leads industrial-AI
projects with business units across domains, with a focus on control and
optimization and time-series analysis for mobility and energy. He leads
cross-functional collaborations that deliver scalable AI solutions for business
goals and cost reduction.
```

Enable selected publications only if the bibliography contains public Siliang Lu entries. Enable announcements, latest posts, and portrait display only if corresponding real content/assets are supplied; otherwise set their relevant front-matter flags to `false` or omit them.

- [ ] **Step 3: Remove starter-only navigation and pages**

For each of `blog`, `books`, `cv`, `dropdown`, `news`, `profiles`, `repositories`, and `teaching`, either replace it with user-supplied public content or set `nav: false`. Do not leave a navigation link pointing to demo posts, a demo CV, a sample people page, or demo repository data.

- [ ] **Step 4: Run homepage and navigation checks**

Run:

```bash
rg -n 'Affiliations|555 your office|123 your address|Your City|Write your biography|favorite subreddit' _pages/about.md
rg -n '^nav: true' _pages
```

Expected: the first command has no output; the second lists only `about`, `projects`, and `publications` until additional real sections are published.

- [ ] **Step 5: Commit**

```bash
git add _pages/about.md _pages
git commit -m "feat: add executive research homepage"
```

### Task 3: Replace demo collections with approved public industrial-AI portfolio content

**Files:**
- Remove or modify: `_projects/1_project.md` through `_projects/9_project.md`
- Create: one date-and-slug-named Markdown file in `_projects/` for each approved case study
- Remove or modify: `_news/*.md`, `_posts/*.md`, `_teachings/*.md`
- Modify: `_bibliography/papers.bib`

**Interfaces:**
- Consumes: the public case-study contract: title, named Bosch/business-unit context, problem, approach, role, measurable outcome, asset/link, and disclosure constraints.
- Produces: public project cards and project pages; an honest publication list; no starter-content collections exposed to visitors.

- [ ] **Step 1: Write a failing demo-content scan**

Run:

```bash
rg -n 'project [1-9]|Introduction to Machine Learning|Data Science Fundamentals|Albert Einstein|medium\.com/@al-folio' _projects _news _posts _teachings _bibliography/papers.bib
```

Expected: matches show starter projects, teaching materials, blog content, and demo identity before cleanup.

- [ ] **Step 2: Gate project publication on supplied facts**

Before creating a project file, obtain all six facts in the case-study contract: title and named context; business problem; AI approach; Siliang’s role; measurable outcome; and asset/link/disclosure constraints. A case study with any missing fact is not publishable and remains absent from `_projects/`.

For every complete case study, create a Markdown project page with front matter containing `layout: page`, the supplied title, a supplied one-sentence outcome as `description`, `importance` as the user-approved display order, and `category: industrial AI`. Include the three Markdown headings `Context`, `Approach`, and `Contribution and impact`, populated solely with the supplied public facts. Include `img` only when a supplied image asset has been added under `assets/img/`.

Remove every starter project file rather than presenting it as Siliang’s work.

- [ ] **Step 3: Remove or hide remaining starter collections**

Remove demo posts, news, and teaching entries, or keep their parent pages out of navigation until real replacements exist. Remove only unverified/demo bibliography records; retain public, verified Siliang Lu records and their existing citation metadata.

- [ ] **Step 4: Run the collection-content checks**

Run:

```bash
rg -n 'project [1-9]|Introduction to Machine Learning|Data Science Fundamentals|Albert Einstein' _projects _news _posts _teachings _bibliography/papers.bib
```

Expected: no output.

- [ ] **Step 5: Commit**

```bash
git add _projects _news _posts _teachings _bibliography/papers.bib
git commit -m "feat: publish industrial AI portfolio content"
```

### Task 4: Validate al-folio wiring and generated public site

**Files:**
- Modify only if validation identifies a configuration/content defect: `_config.yml`, `_data/socials.yml`, `_pages/about.md`, `_pages/*.md`, `_projects/*.md`, `_bibliography/papers.bib`

**Interfaces:**
- Consumes: the configured site from Tasks 1–3.
- Produces: a formatted, buildable site with no unintentional local runtime overrides.

- [ ] **Step 1: Run formatting validation**

Run:

```bash
npm ci
npm run lint:prettier
```

Expected: Prettier exits successfully. If it reports formatting failures, run `npx prettier _config.yml _data/socials.yml _pages _projects _news _posts _teachings _bibliography/papers.bib --write`, then rerun `npm run lint:prettier`.

- [ ] **Step 2: Run ownership and upgrade validation**

Run:

```bash
bundle exec al-folio upgrade audit --no-fail
bundle exec al-folio upgrade overrides audit
```

Expected: audit output is reviewed; no untracked local runtime override is introduced. If the overrides audit creates `.al-folio-overrides.yml`, review it before adding it to the next commit.

- [ ] **Step 3: Build the production site**

Run:

```bash
bundle exec jekyll build --baseurl /al-folio
```

Expected: Jekyll exits successfully and writes `_site` without Liquid, YAML, or missing-asset errors.

- [ ] **Step 4: Commit validation fixes only when needed**

```bash
git status --short
git add _config.yml _data/socials.yml _pages _projects _news _posts _teachings _bibliography/papers.bib
git commit -m "fix: validate public site configuration"
```

Expected: after reviewing `git status --short`, stage only files that validation changed and skip the commit if validation makes no source changes. If the overrides audit creates `.al-folio-overrides.yml`, review it and add it only if it documents an intentional local override.
