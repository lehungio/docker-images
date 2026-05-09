# Release Notes

All notable changes to Docker images in this repository.

Version is managed via the `VERSION` file (SSOT). Bumping `VERSION` on `main` triggers auto-release.

---

## v3.3.2

### Ubuntu (`ubuntu-latest`)

| Base | Key Packages |
|---|---|
| `ubuntu:latest` | Node.js (stable via n), Java 11 (Amazon Corretto), sbt, AWS CLI v2, Docker, Playwright, Gource 0.55 |

- Add OCI labels for GHCR repo linking
- Add Gource 0.55 (built from source)
- Add Playwright with browser dependencies
- Add trcli via Python venv
- Add Docker and Docker Compose

### PHP (`php-latest`)

| Base | PHP | Node |
|---|---|---|
| `php:8.3.7-fpm` | 8.3.7 | LTS (via nvm) |

- Replace stale pinned extension commits with `install-php-extensions` 2.11.0
- Add Oracle Instant Client packing to reduce image size
- Add OCI labels
- Extensions: bcmath, exif, gd, gmp, igbinary, imagick, imap, intl, mysqli, oci8, opcache, pcntl, pdo_mysql, pdo_oci, pdo_pgsql, pdo_sqlsrv, redis, sockets, tidy, xdebug, xsl, zip

### PHP (`php-beta`)

| Base | PHP | Node |
|---|---|---|
| `php:8.4-fpm` | 8.4 | LTS (via nvm) |

- Fix Debian Trixie compatibility (replace `python3.11` with `python3`, remove `software-properties-common`)
- Remove duplicate extension installs
- Fix apt install failure (exit code 100)
- Split Oracle packing from extension install with dynamic paths
- Fix ENV format for Docker best practices

### Puppeteer (`puppeteer-latest`)

| Base | Node | Chrome | sbt |
|---|---|---|---|
| `node:23.8.0` | 23.8.0 | google-chrome-stable (latest) | 1.10.7 |

- Replace dead Google font URL
- Fix legacy ENV format
- Add Scala 3 build support
- Add trcli, AWS CLI, PostgreSQL client
- Add CJK font support (fonts-noto-cjk)

### Redis (`redis-latest`)

| Base | Extras |
|---|---|
| `redis:latest` | locale (en_US.UTF-8), git, curl, vim |

- Add OCI labels
- Add locale configuration (en_US.UTF-8)
- Add basic utilities (git, curl, iputils-ping, telnet, vim)

### Jenkins (`jenkins-latest`)

| Base |
|---|
| `jenkins/jenkins:latest` |

- Add OCI labels
- Custom dependencies via `dependencies.sh`

### CI/CD

- Add `VERSION` file as SSOT for package versioning
- Add auto-release workflow (VERSION change on main → GitHub Release → image builds)
- Add `filter` job to CI for unique version per run
- Add `workflow_dispatch` and tag push triggers to release workflow

---

## v3.3.1

### All Images

- Migrate repository from `lecaoquochung` to `lehungio`
- Update release tags and registry references

---

## v3.3.0

### Puppeteer (`puppeteer-latest`)

| Base | Node | sbt |
|---|---|---|
| `node:23.8.0` | 23.8.0 | 1.10.7 |

- Upgrade Node.js base image to 23.8.0
- Add Scala 3 build support in Puppeteer image
- Version bump for puppeteer dependencies

---

## v3.2.0

### All Images

- CI workflow improvements (tags, packages)
- Test reporting enhancements
- Build automation refinements

---

## v3.1.1

### All Images

- Bug fixes and CI tweaks

---

## v3.1.0

### All Images

- Redis image introduced
- CI test jobs for Redis connection verification
- Newman/Postman API test integration

---

## v3.0.0

### Breaking Changes

- Major CI/CD restructure
- Separate manual and automation build jobs
- GitHub Container Registry (`ghcr.io`) as primary registry
- Artifact attestation for all automation builds

### Ubuntu (`ubuntu-latest`)

- Full rebuild with comprehensive tooling

### PHP (`php-latest`)

- Automation build and push pipeline

### Puppeteer (`puppeteer-latest`)

- Automation build and push pipeline
- Container verification steps

---

## v2.1.1

- Maintenance release

## v2.1.0

- Scala image improvements

## v2.0.0

### Breaking Changes

- Scala build images restructured
- Coding workflow introduced

---

## v1.4.0

- Scala latest/bionic/maintenance images added

## v1.3.0

- Redash Docker Compose setup
- Windows and macOS runner support in CI
- OS build-in dependency checks

## v1.2.0

- Postman/Newman API testing integration
- CircleCI configuration updates

## v1.1.0

- Puppeteer image introduced
- Selenium test support
- Package management (package.json)

## v1.0.0

- Initial release
- Jenkins image
- Ubuntu base image
- CircleCI pipeline
