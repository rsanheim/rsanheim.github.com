My homepage. Pretty standard GitHub Pages thing.

## Setup

Ruby is managed with mise. `mise.toml` is the source of truth for the Ruby version,
used locally and by GitHub Actions.

```
mise install
mise exec -- bundle install
mise exec -- bundle exec jekyll serve
```

Run things incrementally like

```
mise exec -- bundle exec jekyll serve --incremental
```
