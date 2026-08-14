# TechEtics

Source for [omnaphade.github.io](https://omnaphade.github.io) — my personal tech blog, "Exploring spectrum of technology." Built on the [Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy) Jekyll theme and deployed via GitHub Pages/Actions.

## Posts

- [JAVA — from basics to advanced](_posts/2024-11-29-JAVA-from-basics-to-advanced.md)
- [State management mistakes I made in my first full-stack app](<_posts/2025-02-02-state-mnagement-mistakes-I-made-in-my-first-full-stack-app.md>)
- [Docker — from basics to real understanding](_posts/2025-07-10-docker-from-basics-to-real-understanding.md)
- [When localhost broke my entire Docker setup](_posts/2026-02-20-when-localhost-broke-my-entire-docker-setup.md)
- [Postgres/JVM timezone issue](_posts/2026-03-23-postgres-jvm-timezone-issue.md)

## Running locally

```bash
bundle install
bundle exec jekyll serve
```

Site config lives in `_config.yml`; posts go in `_posts/`, static pages/tabs in `_tabs/`.

## Deployment

Pushes to `main` trigger `.github/workflows/pages-deploy.yml`, which builds the Jekyll site and publishes it to GitHub Pages.

## Credits

Built on the [Chirpy Starter][chirpy] theme, published under the [MIT License][mit].

[chirpy]: https://github.com/cotes2020/jekyll-theme-chirpy/
[mit]: https://github.com/cotes2020/chirpy-starter/blob/master/LICENSE
