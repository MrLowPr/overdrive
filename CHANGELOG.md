# Changelog

Changes made in this fork on top of [MyLuxy/overdrive](https://github.com/MyLuxy/overdrive).
Upstream's own history is in its [releases](https://github.com/MyLuxy/overdrive/releases);
this file only records the fork's additions. See [FORK-NOTES.md](FORK-NOTES.md) for what each
change touches.

## Unreleased

Nothing yet.

## mrlowpr.1 — 2026-10-16

First fork build. Starts from upstream `v1.0.5` (`4d3ced0`).

### Added
- **About this build** section in the settings sheet, showing the fork name, the fork build
  tag, the app version and the upstream URL, so a fork build is never mistaken for an
  upstream build.
- `BUILD`, `FORK` and `UPSTREAM` exports in `app/version.js`. `VERSION` deliberately left at
  `1.0.5` so the updater keeps comparing against the upstream feed.
- `about.*` copy for English and Indonesian.

### Changed
- Fork banner and social preview art (`assets/banner.svg`).
- README opens with a fork notice, links to this fork's releases, and keeps upstream's
  install instructions and credits intact.

### Known limitations
- Only the `about.*` keys are translated here; the other 14 catalogs fall back to English,
  which is the upstream behaviour for any missing key.
