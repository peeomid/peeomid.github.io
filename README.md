# osimify.com

Jekyll site for https://osimify.com

## GitHub Pages deploy
- Deploys from branch builds on GitHub Pages.
- `_config.yml` must keep `remote_theme: "mmistakes/minimal-mistakes"`.
- `Gemfile` uses the `github-pages` gem to match the Pages build environment.

## Local development
Use the local override to avoid network fetches for the theme:

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

Troubleshooting:
- Ruby 3.0+ may require WEBrick:
  `bundle add webrick`
- If `baseurl` is set and the site looks wrong locally:
  `bundle exec jekyll serve --config _config.yml,_config_local.yml --baseurl=""`
