# Image Release Notes

Per-image version history and available tags.

---

## Ubuntu

**Registry:** `ghcr.io/lehungio/docker-images`

| Version | Tag | Base | Status |
|---|---|---|---|
| v3.3.2 | `ubuntu-latest-v3.3.2` | `ubuntu:latest` | Current |
| v3.3.1 | `ubuntu-latest-v3.3.1` | `ubuntu:latest` | Stable |
| v3.3.0 | `ubuntu-latest-v3.3.0` | `ubuntu:latest` | — |
| v3.2.0 | `ubuntu-latest-v3.2.0` | `ubuntu:latest` | — |

**Included tools:** Node.js, npm, yarn, Java 11 (Amazon Corretto), sbt, AWS CLI v2, Docker, Docker Compose, Playwright, Python 3, trcli, Gource 0.55, Chromium, PostgreSQL client, git, curl, vim

**Variants:**
- `ubuntu-qa` — QA-specific image (`./ubuntu/qa.Dockerfile`)
- `ubuntu-noble` — Ubuntu Noble base (`./ubuntu/noble.Dockerfile`)

---

## PHP

**Registry:** `ghcr.io/lehungio/docker-images`

### php-latest

| Version | Tag | Base | PHP | Status |
|---|---|---|---|---|
| v3.3.2 | `php-latest-v3.3.2` | `php:8.3.7-fpm` | 8.3.7 | Current |
| v3.3.1 | `php-latest-v3.3.1` | `php:8.3.7-fpm` | 8.3.7 | Stable |
| v3.3.0 | `php-latest-v3.3.0` | `php:8.3.7-fpm` | 8.3.7 | — |

**Included tools:** Composer, Node.js LTS (nvm), yarn, jest, MySQL client, Python 3.11, PHP extensions (bcmath, exif, gd, gmp, igbinary, imagick, imap, intl, mysqli, oci8, opcache, pcntl, pdo_mysql, pdo_oci, pdo_pgsql, pdo_sqlsrv, redis, sockets, tidy, xdebug, xsl, zip)

### php-beta

| Version | Tag | Base | PHP | Status |
|---|---|---|---|---|
| v3.3.2 | `php-beta-v3.3.2` | `php:8.4-fpm` | 8.4 | Current |
| v3.3.1 | `php-beta-v3.3.1` | `php:8.4-fpm` | 8.4 | Stable |

**Included tools:** Same as php-latest, targeting PHP 8.4 with Debian Trixie base

---

## Puppeteer

**Registry:** `ghcr.io/lehungio/docker-images`

| Version | Tag | Base | Node | Chrome | Status |
|---|---|---|---|---|---|
| v3.3.2 | `puppeteer-latest-v3.3.2` | `node:23.8.0` | 23.8.0 | google-chrome-stable | Current |
| v3.3.1 | `puppeteer-latest-v3.3.1` | `node:23.8.0` | 23.8.0 | google-chrome-stable | Stable |
| v3.3.0 | `puppeteer-latest-v3.3.0` | `node:23.8.0` | 23.8.0 | google-chrome-stable | — |

**Rolling tag:** `puppeteer-latest` (always points to latest release)

**Included tools:** Google Chrome stable, Puppeteer, Java (default-jre/jdk), sbt 1.10.7, AWS CLI, Python 3, trcli, PostgreSQL client, yarn, CJK fonts, screen

**User:** Runs as non-root `qa` user

---

## Redis

**Registry:** `ghcr.io/lehungio/docker-images`

| Version | Tag | Base | Status |
|---|---|---|---|
| v3.3.2 | `redis-latest-v3.3.2` | `redis:latest` | Current |
| v3.3.1 | `redis-latest-v3.3.1` | `redis:latest` | Stable |

**Included tools:** Redis server/CLI, locale (en_US.UTF-8), git, curl, vim, iputils-ping, telnet

**Port:** 6379

---

## Jenkins

**Registry:** `ghcr.io/lehungio/docker-images`

| Version | Tag | Base | Status |
|---|---|---|---|
| v3.3.2 | `jenkins-latest-v3.3.2` | `jenkins/jenkins:latest` | Current |

**Ports:** 8080 (web), 50000 (agent)

**Note:** Jenkins image is build-only in CI (not pushed via automation). Available in release workflow.

---

## Scala (CI build-only)

Not pushed to registry. Used for CI testing.

| Image | Dockerfile | Base | Java | sbt | Node | Playwright |
|---|---|---|---|---|---|---|
| scala-latest | `./scala/build/latest.Dockerfile` | `ubuntu:24.10` | 11 | 1.10.2 | 22.9.0 | 1.47.2 |
| scala-bionic | `./scala/build/bionic.Dockerfile` | `ubuntu:bionic` | 8 | 1.2.8 | 16.20.2 | 1.30.0 |
| scala-maintenance | `./scala/build/maintenance.Dockerfile` | `ubuntu:24.04` | 11 | 1.10.2 | 20.x | 1.47.2 |

---

## Tag Format

| Pattern | Example | Description |
|---|---|---|
| `<image>-v<version>` | `ubuntu-latest-v3.3.2` | Release tag (stable) |
| `<image>-sha-<short>` | `ubuntu-latest-sha-a1b2c3d` | Commit SHA tag |
| `<image>` | `puppeteer-latest` | Rolling latest (puppeteer only) |
| `<image>-build` | `ubuntu-latest-build` | CI build tag (overwritten each run) |

## Pull Examples

```bash
docker pull ghcr.io/lehungio/docker-images:ubuntu-latest-v3.3.2
docker pull ghcr.io/lehungio/docker-images:php-latest-v3.3.2
docker pull ghcr.io/lehungio/docker-images:php-beta-v3.3.2
docker pull ghcr.io/lehungio/docker-images:puppeteer-latest-v3.3.2
docker pull ghcr.io/lehungio/docker-images:redis-latest-v3.3.2
docker pull ghcr.io/lehungio/docker-images:puppeteer-latest
```
