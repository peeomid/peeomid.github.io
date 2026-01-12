# Repo workflow notes

## GitHub Pages deploy
- This site deploys from GitHub Pages branch builds.
- Keep `_config.yml` using `remote_theme: "mmistakes/minimal-mistakes"` so Pages can fetch the theme.
- The `github-pages` gem in `Gemfile` mirrors the GitHub Pages build environment.

## Local development (no remote theme fetch)
Use a local override so the theme is resolved from the gem instead of GitHub:

```bash
bundle install
bundle exec jekyll serve --config _config.yml,_config_local.yml
```

Local override file:
- `_config_local.yml` sets `theme: minimal-mistakes-jekyll` and disables `remote_theme`.

Ruby version:
- Use Homebrew `ruby@3.1` for local builds to avoid compatibility issues.
- Example:
  `export PATH="/opt/homebrew/opt/ruby@3.1/bin:$PATH"`

Notes:
- If Ruby is 3.0+ and you see a WEBrick error, run:
  `bundle add webrick`
- If `baseurl` is set for GitHub Pages and the site looks wrong locally, use:
  `bundle exec jekyll serve --config _config.yml,_config_local.yml --baseurl=""`
