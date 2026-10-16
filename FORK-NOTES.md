# Fork notes

This repository is a fork of **[MyLuxy/overdrive](https://github.com/MyLuxy/overdrive)** — the
original project, which decompiled the PS5 store, recovered its source and rebuilt it. All
original credit goes to [MyLuxy](https://github.com/MyLuxy) and the upstream contributors.

Upstream stays the source of truth for how the store works. This fork exists so that a few
local changes can live somewhere without blocking on upstream. Everything below is what this
fork adds; everything else is upstream code.

## What this fork changes

| Area | Change | Where |
| --- | --- | --- |
| Build identity | `BUILD`, `FORK` and `UPSTREAM` exports next to the untouched `VERSION` | `app/version.js` |
| Settings sheet | New read-only **About this build** section: fork name, fork build tag, app version, upstream URL | `app/ui/LanguageSheet.jsx` |
| Copy (EN) | `about.title`, `about.detail`, `about.build`, `about.version`, `about.upstream` | `app/i18n/locales/en.json` |
| Copy (ID) | The same five keys, in Indonesian | `app/i18n/locales/id.json` |
| Branding | Fork banner and social preview (`assets/banner.svg`) | `assets/banner.svg` |
| Docs | Fork notice at the top of the README, this file, and `CHANGELOG.md` | `README.md` |

## Why `VERSION` is not bumped

`VERSION` is what the app compares against the upstream update feed. Changing it would make a
fork build claim a version the upstream feed has never published, and the updater would start
offering an update that does not exist. The fork therefore carries its own `BUILD` tag
(`mrlowpr.N`) instead, and `VERSION` stays `1.0.5` until upstream moves.

## Staying in sync with upstream

```bash
git remote -v                    # origin = this fork, upstream = MyLuxy/overdrive
git fetch upstream
git merge upstream/main          # or rebase, your choice
```

Two conflicts are expected and both are mechanical:

- `app/version.js` — upstream may move `VERSION`; keep the fork's `BUILD`/`FORK`/`UPSTREAM`
  exports when merging.
- `app/i18n/locales/en.json` and `id.json` — the `about.*` keys are appended at the end of
  each catalog, so an upstream append lands next to them.

If a change here is worth having upstream, open a pull request against
[MyLuxy/overdrive](https://github.com/MyLuxy/overdrive) rather than letting it drift.

## Conventions

Upstream marks every deliberate deviation with a `// MODIFIED:` comment in the file header.
Fork-only changes continue that convention with an explicit `// MODIFIED (fork):` marker, so
the two sets of changes stay distinguishable in the diff.
