# Versioning

This project uses a `VERSION` file as the Single Source of Truth (SSOT) for all release versioning.

## How It Works

```
VERSION (SSOT)
  ├── auto-release.yml  → creates GitHub Release on push to main
  ├── release.yml       → builds & pushes images on release published
  ├── ci.yml            → tags CI builds with version
  └── automation.yml    → reads version for weekly builds
```

## Releasing

### Automatic (recommended)

1. Edit `VERSION` file with the new version
2. Push/merge to `main`
3. GitHub Actions auto-creates a Release → triggers image builds

### Manual

```bash
# Via GitHub CLI
gh workflow run release.yml --ref main

# From a specific tag
gh workflow run release.yml --ref v3.3.2

# Or: GitHub UI → Actions → Release → Run workflow
```

### Direct tag push

```bash
git tag v3.3.2
git push --tags
```

## Version Format

Follows [SemVer](https://semver.org/):

```
MAJOR.MINOR.PATCH[-prerelease]
```

Examples:
- `3.3.2` — stable release
- `3.3.2-rc.1` — release candidate
- `3.3.2-beta.1` — beta

## Image Tags

Each release produces tags per image:

| Image | Tag |
|---|---|
| Ubuntu | `ubuntu-latest-v3.3.2` |
| PHP | `php-latest-v3.3.2` |
| PHP Beta | `php-beta-v3.3.2` |
| Puppeteer | `puppeteer-latest-v3.3.2`, `puppeteer-latest` |
| Redis | `redis-latest-v3.3.2` |

## CI Build Tags

CI runs produce unique tags per run:

```
<image>-<version>-build.<run_number>-<short_sha>
```

Example: `ubuntu-latest-3.3.2-build.42-a1b2c3d`

## Files

| File | Purpose |
|---|---|
| `VERSION` | SSOT — the only place to set the version |
| `package.json` | Version field set to `0.0.0-managed-by-VERSION-file` (not used) |
| `.github/workflows/auto-release.yml` | Detects VERSION change, creates GitHub Release |
| `.github/workflows/release.yml` | Builds and pushes images on release |
