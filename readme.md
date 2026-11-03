# gen2phen-docs

Documentation website for the Gen2Phen project, built with [Jekyll](https://jekyllrb.com/) and the Minima theme.

All contributions are made through **pull requests**. Please do not push directly to `main`.

## How to contribute

### 1. Clone the repository

```bash
git clone <repo-url>
cd gen2phen-docs
```

### 2. Create a branch

Always branch from an up-to-date `main`:

```bash
git checkout main
git pull origin main
git checkout -b docs/short-description
```

Branch naming suggestions:

| Prefix | Use for |
|---|---|
| `docs/` | Content changes, new pages, text fixes |
| `style/` | CSS or layout changes |
| `fix/` | Broken links, build errors |

### 3. Run the site locally

```bash
bundle install
bundle exec jekyll serve
```

Open http://127.0.0.1:4000/ and confirm your changes look right. The site rebuilds on save, except for `_config.yml` changes, which need a server restart.

> The Sass `lighten()` deprecation warnings come from the Minima theme and can be ignored.

### 4. Make your changes

- **Pages:** create or edit `.md` files in the project root. Give each page front matter with a unique `permalink`:
  ```markdown
  ---
  layout: page
  title: Tutorial
  permalink: /tutorial/
  ---
  ```
- **Navigation:** add new pages to `header_pages` in `_config.yml`.
- **Styles:** add CSS to `assets/main.scss` below `@import "minima";`. Keep the `---` front matter at the top of that file.
- **Footer:** markup is in `_includes/footer.html`.

### 5. Commit and push

```bash
git add .
git commit -m "Add tutorial page"
git push origin docs/short-description
```

### 6. Open a pull request

1. Go to the repository on GitHub and click **Compare & pull request**.
2. Set the base branch to `main`.
3. Describe what changed and why. Attach screenshots for visual changes.
4. Submit the pull request.

### 7. Review and merge

- A maintainer will review your PR and may request changes.
- Push more commits to the same branch to update the PR.
- Once approved, a maintainer will merge it into `main`.

### 8. Clean up

After your PR is merged:

```bash
git checkout main
git pull origin main
git branch -d docs/short-description
```

## Project structure

```
gen2phen-docs/
├── _config.yml        # Site settings
├── _includes/
│   └── footer.html    # Footer markup
├── assets/
│   └── main.scss      # Custom styles
├── index.md           # Home page
├── data.md            # Data page
├── faq.md             # FAQ page
└── README.md
```

## Style guidelines

- Use sentence case for headings.
- One top-level `#` heading per page (the title comes from front matter).
- Use fenced code blocks with a language tag (` ```bash `, ` ```python `).
- Use relative links for internal pages, e.g. `[FAQ]({{ '/faq/' | relative_url }})`.

## Troubleshooting

| Problem | Fix |
|---|---|
| `No repo name found` error | Add `repository: <owner>/<repo>` to `_config.yml` |
| Styles missing entirely | Make sure `assets/main.scss` still starts with the `---` front matter block |
| "Conflict: destination is shared by multiple files" | Give each page a unique `permalink` |
| `_config.yml` changes not showing | Restart the server (`Ctrl+C`, then `bundle exec jekyll serve`) |
| Stale or odd build | `rm -rf _site .jekyll-cache`, then restart the server |

## Questions

Open an issue in this repository.