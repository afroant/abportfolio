# Antony Bridle Design — Portfolio Site

A Jekyll-powered portfolio site built for GitHub Pages. Edit content in Markdown, push to GitHub, and it publishes automatically.

---

## Quick setup

### 1. Install Jekyll (one-time)

You'll need Ruby installed. On a Mac:

```bash
# Install Homebrew if you don't have it
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Ruby via rbenv
brew install rbenv ruby-build
rbenv install 3.2.2
rbenv global 3.2.2

# Install Jekyll
gem install bundler jekyll
```

### 2. Run locally

```bash
cd antonybridle-portfolio
bundle install
bundle exec jekyll serve
```

Then open `http://localhost:4000` in your browser.

### 3. Deploy to GitHub Pages

1. Create a new repository on GitHub named `yourusername.github.io` (for a root domain) or any name (for `yourusername.github.io/repo-name`)
2. Push this folder to that repo
3. In the repo Settings → Pages → set Source to `main` branch
4. Your site will be live at `https://yourusername.github.io`

To use your custom domain (`antonybridle.com`):
- Add a `CNAME` file to the root containing just: `antonybridle.com`
- Point your domain's DNS to GitHub Pages (see GitHub docs)

---

## Updating content

### Edit your bio (About page)

Open `about.md` and edit the text directly. It's plain Markdown.

### Update a project

Each project is a Markdown file in `_projects/`. For example, to update BIG South London, open `_projects/big-south-london.md`.

The top section (between the `---` lines) is the **front matter** — structured data:

```yaml
---
title: "BIG South London"
client: "Recognition Design and Marketing"
tags: ["Brand", "Web Design", "Print"]
thumbnail: /assets/images/projects/big-south-london/thumbnail.jpg
images:
  - /assets/images/projects/big-south-london/01.jpg
  - /assets/images/projects/big-south-london/02.jpg
project_url: https://www.big-knowledge.co.uk
url_label: "Visit big-knowledge.co.uk"
order: 2
---

Your project description goes here in plain Markdown.
```

Below the second `---` is the project description in plain Markdown.

### Add project images

Images live in `assets/images/projects/project-slug/`. For each project create a folder matching its slug (the filename without `.md`):

```
assets/images/projects/big-south-london/
  thumbnail.jpg   ← shown in the work grid (recommend 16:9, ~800×450px)
  01.jpg          ← first image on the project page
  02.jpg
  03.jpg
```

Then reference them in the front matter as shown above.

### Add a new project

1. Create a new file in `_projects/` — e.g. `_projects/my-new-project.md`
2. Copy the front matter structure from an existing project
3. Add your images to `assets/images/projects/my-new-project/`
4. The project will automatically appear in the work grid

### Change the order of projects

Set the `order` number in each project's front matter. Lower numbers appear first.

> **Note:** To sort by order, you'll need to update the `work.html` and `index.html` files to use `{% assign projects = site.projects | sort: "order" %}`.

---

## File structure

```
antonybridle-portfolio/
├── _config.yml          ← Site settings (title, email, etc.)
├── _layouts/
│   ├── default.html     ← Wraps every page (nav + footer)
│   └── project.html     ← Project page template
├── _includes/
│   ├── nav.html         ← Navigation
│   └── footer.html      ← Footer
├── _projects/           ← One .md file per project
│   ├── big-south-london.md
│   └── ...
├── assets/
│   ├── css/main.css     ← All styles
│   ├── js/main.js       ← Mobile nav
│   └── images/
│       ├── logo.png
│       └── projects/    ← Project images go here
├── index.html           ← Home / work grid
├── work.html            ← /work/ page (same grid)
├── about.md             ← About page
└── Gemfile              ← Ruby dependencies
```
