# Jekyll-Scholar Setup with GitHub Actions

This repository uses **jekyll-scholar** for academic citations, which requires custom GitHub Actions deployment since it's not in GitHub Pages' default plugin allowlist.

## How It Works

1. **Local Development**: Standard Jekyll workflow with `bundle exec jekyll serve`
2. **Deployment**: GitHub Actions builds site with custom plugins, then deploys to GitHub Pages
3. **No Extra Steps**: Just push to `main` branch as usual

## File Changes Made

### 1. Gemfile
- Removed `github-pages` gem (limited plugins)
- Added `jekyll ~> 4.3` directly
- Added `jekyll-scholar` to plugins group

### 2. _config.yml
- Added `jekyll-scholar` to plugins list
- Added scholar configuration:
  - Style: APA
  - Bibliography source: `_bibliography/references.bib`
  - Other settings for bibliography rendering

### 3. .github/workflows/deploy.yml (NEW)
- GitHub Actions workflow that:
  - Checks out code
  - Sets up Ruby environment
  - Installs dependencies (including jekyll-scholar)
  - Builds site with `bundle exec jekyll build`
  - Deploys to GitHub Pages

### 4. _bibliography/references.bib (NEW)
- BibTeX file for academic references
- Sample entries included

## Usage in Posts

### In-text citations:
```markdown
Research shows collusion emerges {% cite douglas2024algorithmic %}.

Multiple studies {% cite varoufakis2023technofeudalism allouah2025agentic %}.
```

### Bibliography section:
```markdown
## References

{% bibliography --cited %}
```

### Adding new references:
1. Add BibTeX entry to `_bibliography/references.bib`
2. Use citation key in post: `{% cite key %}`
3. Add `{% bibliography --cited %}` at end of post

## GitHub Pages Settings

**Important**: In your repository settings, you need to configure GitHub Pages to use GitHub Actions:

1. Go to **Settings → Pages**
2. Under **Build and deployment**
3. Set **Source** to **GitHub Actions** (not "Deploy from a branch")

## Local Testing

```bash
# Install dependencies
bundle install

# Serve locally
bundle exec jekyll serve

# Build site
bundle exec jekyll build
```

## Why This Approach?

GitHub Pages default build only supports a limited set of plugins. jekyll-scholar is not on that list. By using GitHub Actions, we can:
- Use any Jekyll plugins we want
- Control Ruby version
- Customize build process
- Still deploy automatically to GitHub Pages

## References

- [jekyll-scholar documentation](https://github.com/inukshuk/jekyll-scholar)
- [GitHub Actions for Jekyll](https://jekyllrb.com/docs/continuous-integration/github-actions/)
- [Deploying Jekyll to GitHub Pages with Actions](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages#static-site-generators)
