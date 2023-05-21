# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

## [44.0.0] - 2022-12-05

### Added
- Allow more variables for the PhpStan analyse script [PR #789](https://github.com/markshust/docker-magento/pull/789).
- New bin/docker-compose script to abstract away calls to docker-compose [PR #787](https://github.com/markshust/docker-magento/pull/787).
- Support for Docker Compose V2 ("docker compose" and backwards-compatibility for "docker-compose") [PR #787](https://github.com/markshust/docker-magento/pull/787).
- New Docker Compose healthcheck [PR #384](https://github.com/markshust/docker-magento/pull/384).
- MageOS support [4591b68c](https://github.com/markshust/docker-magento/commit/4591b68c46667d4015e728392b813ec42939ae67).
- Documentation to recover from failed install [#816](https://github.com/markshust/docker-magento/issues/816).
- OpenSearch support [PR #680](https://github.com/markshust/docker-magento/pull/680).
- New build for Elasticsearch 7.17 [c45f05c3](https://github.com/markshust/docker-magento/commit/c45f05c370fe1347afa35117511794f736710f71).

### Updated
- Rename docker-compose.yml to compose.yaml (preferred) [PR #799](https://github.com/markshust/docker-magento/pull/799).
- Readme file with new info on configuring Xdebug in WSL2 environments [PR #810](https://github.com/markshust/docker-magento/pull/810).

### Fixed
- Lowered RAM check on setup [#720](https://github.com/markshust/docker-magento/issues/720).

### Removed
- Deprecated PHP 7.4 due to all versions < Magento 2.4.4 reaching EOL [3a64324e](https://github.com/markshust/docker-magento/commit/3a64324e08f3d15e3c3ce86b5c0f5e7ebb635a75).

## [43.2.0] - 2022-09-13

### Added
- Added phpmyadmin to docker-compose.dev.yml file [PR #772](https://github.com/markshust/docker-magento/pull/772).

## [43.1.0] - 2022-09-13

### Added
- Support for Grunt + LiveReload [#430](https://github.com/markshust/docker-magento/issues/430).

## [43.0.0] - 2022-05-26

### Added
- Fall back to PHP 7.4 for Magento versions older than 2.4.4 [PR #685](https://github.com/markshust/docker-magento/pull/685) [PR #710](https://github.com/markshust/docker-magento/pull/710).
- Checksum flag to rsync in `bin/update` [PR #707](https://github.com/markshust/docker-magento/pull/707).
- New `bin/analyse` command to statically analyse code with PHPStan [8601c2f7](https://github.com/markshust/docker-magento/commit/8601c2f73cc6f1d2534f017c8f31eec49b0e00fc).
- `node` & `npm` to PHP images [#694](https://github.com/markshust/docker-magento/issues/694).

### Updated
- Magento download to default to 2.4.4 [151dc09a](https://github.com/markshust/docker-magento/commit/151dc09ae95a5cff75598c366f3d77efa58098d5)
- Prevent domain duplication in `/etc/hosts` [PR #693](https://github.com/markshust/docker-magento/pull/693).
- Replace buster images with bullseye to properly fix Apple M1 5-sec delay [#636](https://github.com/markshust/docker-magento/issues/636).

## [42.0.0] - 2022-04-14

This release brings streamlined PHP Docker images (saving 300MB on previous images), a brand new PHP 8.1 image with full support for Magento 2.4.4, a proper Elasticsearch health check during setup, and ability to detect memory assigned to Docker on startup (which will prevent failed installations). Elasticsearch, Redis & RabbitMQ Docker images have also all been updated to their recently supported Magento versions.

### Added
- New Docker image for PHP 8.1 [903f9867](https://github.com/markshust/docker-magento/commit/903f9867aa130100267290feaa03b1b48b157337).
- New Docker image for Elasticsearch 7.16 [f70a1565](https://github.com/markshust/docker-magento/commit/f70a1565bddd56a3abe8df52d4122dbcdc85d98a).
- New Docker image for RabbitMQ 3.9 [7711365c](https://github.com/markshust/docker-magento/commit/7711365cb73aab685859e3e34fc23774937a4e2a).
- Elasticsearch health check timeout when installing Magento [#675](https://github.com/markshust/docker-magento/pull/675).
- Ability to detect if memory usage is too low [#527](https://github.com/markshust/docker-magento/issues/527).

### Updated
- PHP 7.4 Docker image for parity with PHP 8.1 image [481097b3](https://github.com/markshust/docker-magento/commit/481097b3f9184d19deb102b901b43af906ebb256).

### Removed
- ionCube support from PHP 7 image in order to retain Docker image parity between versions, to slim down image size, and because I no longer want to support encrypted or obfuscated code in my open source projects. Feel free to pull, fork or modify if you still need ionCube in your projects.

## [41.1.0] - 2022-03-28

### Fixed
- Increased RabbitMQ sleep timeout to prevent errors on startup [#426](https://github.com/markshust/docker-magento/issues/426).
- RabbitMQ connection issues on Windows/WSL2 [#426](https://github.com/markshust/docker-magento/issues/426).
- Problem with elasticsearch & unexpected character [#597](https://github.com/markshust/docker-magento/issues/597).
- Issue with extra_hosts host.docker.internal for Xdebug on Linux [#595](https://github.com/markshust/docker-magento/issues/595).
- Reverted Xdebug/magerun code refactor which caused issues [#595](https://github.com/markshust/docker-magento/pull/545).
- Composer auth.json auth required message shows after authenticating [#587](https://github.com/markshust/docker-magento/issues/587).
- Failing shellchecks [08206e6d](https://github.com/markshust/docker-magento/commit/08206e6d6a48fdb3c1c3adc8f52b146609ba771c), [53d9b858](https://github.com/markshust/docker-magento/commit/53d9b8585733f8f78a5dcaedce53a83863a1b634).
- Firefox SSL cert fails on first-time install [2695fe2e](https://github.com/markshust/docker-magento/commit/2695fe2e508098906103dd442767d50e9f6011c0).
- Some commands including bin/xdebug not working on Windows + Docker Desktop 4.4.3 [#619](https://github.com/markshust/docker-magento/issues/619).

### Updated
- Redis 5.0 to 6.0 [6653d787](https://github.com/markshust/docker-magento/commit/6653d78722fb8d1d76cc2433a89227456e48514f).
- `bin/setup` script so it can run completely automated [PR #633](https://github.com/markshust/docker-magento/pull/633).
- PHP 8 image to 8.1.4, last version before tagging final release [86093b70](https://github.com/markshust/docker-magento/commit/86093b70c9ee7f0ed3c62e84460b7e53926d033c).

### Added
- `bin/stopall` script to stop all running containers [#599](https://github.com/markshust/docker-magento/pull/599).
- New PHP image to enable WebP support in GD [PR #651](https://github.com/markshust/docker-magento/pull/651).
- Ability to configure custom user/group ID in Nginx image [PR #658](https://github.com/markshust/docker-magento/pull/658).

### Removed
- PHP 7.3 images have been deprecated due to 7.3's EOL.
- EXPOSE statement from PHP image (unneeded) [790e2fe0](https://github.com/markshust/docker-magento/commit/790e2fe0293feb12455d7f9ed2593aa97ad6df99).

## [41.0.2] - 2021-12-09

### Fixed
- Disable "Composer is slower because of Xdebug" message [1990d84](https://github.com/markshust/docker-magento/commit/1990d84).
- Updated verbiage in setup on how to start cron [c3ba47d](https://github.com/markshust/docker-magento/commit/1990d84).
- Fixed "The input device is not a TTY" error during setup [8aada97](https://github.com/markshust/docker-magento/commit/8aada97).
- Expose port 9003 on PHP Docker image for Xdebug [263e40d](https://github.com/markshust/docker-magento/commit/263e40d).
- Disable Xdebug by default for PHP 7.3 [263e40d](https://github.com/markshust/docker-magento/commit/263e40d).

### Updated
- Updated PHP 8.1 image to use official GA version [263e40d](https://github.com/markshust/docker-magento/commit/263e40d).

## [41.0.1] - 2021-11-09

### Fixed
- Fixed additional issue of waiting for Elasticsearch/RabbitMQ connection on Mac [#442](https://github.com/markshust/docker-magento/issues/442).

## [41.0.0] - 2021-11-08

There has been an ongoing issue with Docker for Mac + M1 chips (Apple Silicon) which causes a 5-second delay in network requests (see [#5626](https://github.com/docker/for-mac/issues/5626)). A fix has been implemented in this release that works around this issue, adding `extra_hosts` directives in the `docker-compose.yml` file. This update should be backwards-compatible, but will break existing setups that use custom Docker networks (this is an uncommon scenario). See notes at the top of `docker-compose.yml` for how to configure this project for custom Docker networks.

### Added
- Added Imagick PHP extension [#530](https://github.com/markshust/docker-magento/issues/530).

### Fixed
- Fixed issue with onelinesetup script failing on download [92b803c](https://github.com/markshust/docker-magento/commit/92b803c) [67c76b4](https://github.com/markshust/docker-magento/commit/67c76b4).
- Fix Shellcheck failures for bin/setup-ssl-ca [#558](https://github.com/markshust/docker-magento/issues/558).
- Fix wrong `sendmail_path` in php.ini [#556](https://github.com/markshust/docker-magento/issues/556).
- Ensure .composer directory isn't created by root [#562](https://github.com/markshust/docker-magento/issues/562).
- Fixed `bin/devconsole` command not working [646f617](https://github.com/markshust/docker-magento/commit/646f617).
- Fixed `bin/setup-composer-auth` does not persist auth creds [#567](https://github.com/markshust/docker-magento/issues/567).
- Fixed documentation around Xdebug port on Linux [90af7fa](https://github.com/markshust/docker-magento/commit/90af7fa).
- Fixed waiting for Elasticsearch/RabbitMQ connection on Mac [#442](https://github.com/markshust/docker-magento/issues/442).

### Updated
- Updated info about MySQL backups and existing projects in README [86faa70](https://github.com/markshust/docker-magento/commit/86faa70).
- Updated README for Xdebug + PhpStorm [b1fe812](https://github.com/markshust/docker-magento/commit/b1fe812).

## [40.1.0] - 2021-10-29

### Fixed
- Fixed issues with onelinesetup script [#564](https://github.com/markshust/docker-magento/issues/564).
- Fixed Shellcheck failures for bin/setup-ssl-ca [#558](https://github.com/markshust/docker-magento/issues/558).
- Fixed php.ini possible wrong smtp-addr [#556](https://github.com/markshust/docker-magento/issues/556).
- Ensure files are created so Docker doesn't create them as root [#562](https://github.com/markshust/docker-magento/issues/562).
- Added additional time for Elasticsearch container to get initialized during setup.

## [40.0.2] - 2021-10-20

### Fixed
- Fixed Selenium configuration for MFTF [PR #554](https://github.com/markshust/docker-magento/pull/554).

## [40.0.1] - 2021-10-20

### Fixed
- Fixed PHP image `8.0-fpm-develop` for Magento 2.4.4 support (note: still has `-develop` tag).

### Updated
- Moved `~/.ssh` volume mount references to `docker-compose.yml` to ease maintenance.

## [40.0.0] - 2021-10-15

This is one of the biggest releases of docker-magento 💥! This major update includes support for Apple Silicon (M1/M1X) chips, as well as SSH support for fully native filesystem speed.

All the images are now multi-arch builds, meaning they can install on both AMD & ARM chipsets. Additionally, by setting up your IDE to connect to Docker over SSH/SFTP to avoid selective filesystem syncing.

The docker-compose configuration files have also been streamlined & simplified, with dedicated files for both SSH and Linux setups. Read more about these updates at https://github.com/markshust/docker-magento#ssh and https://github.com/markshust/docker-magento#linux respectively.

Many issues have been resolved, and long-standing pull requests have been merged. A special thanks to [@drpayyne](https://github.com/drpayyne) for multi-arch support, [@rangerz](https://github.com/rangerz) for their massive contributions, as well as many others for their continued work & pull requests submitted to this project.

### Updated
- Updated `onelinesetup` script to use version `2.4.3-p1` by default.
- Updated `bin/cache-clean` with improved logic [PR #400](https://github.com/markshust/docker-magento/pull/400).
- Simplified `docker-compose.dev.yml` file to only contain volume mounting information.

### Added
- Added new `mailcatcher` image to replace `mailhog` for multi-arch support [#511](https://github.com/markshust/docker-magento/issues/511).
- Added `docker-compose.dev-ssh.xml` to streamline SSH setup.
- Added `docker-compose.dev-linux.xml` to streamline Linux setup.
- Added GitHub workflows for multi-arch build support [#396](https://github.com/markshust/docker-magento/issues/396).
- Added multi-arch support for Nginx [PR #515](https://github.com/markshust/docker-magento/pull/515).
- Added multi-arch support for PHP [PR #516](https://github.com/markshust/docker-magento/pull/516).
- Added new `bin/setup-domain` script [PR #429](https://github.com/markshust/docker-magento/pull/429).
- Added Basic MFTP Setup information [PR #269](https://github.com/markshust/docker-magento/pull/269).
- Make uid & gid of app user configurable [#520](https://github.com/markshust/docker-magento/pull/520).
- Added Makefile with list of available commands [#399](https://github.com/markshust/docker-magento/pull/399).
- Xdebug 3 support for `bin/n98-magerun2` [#545](https://github.com/markshust/docker-magento/pull/545).

### Fixed
- Fixed SSL setup failing on Linux [#222](https://github.com/markshust/docker-magento/issues/222).
- Fixed locale code for `bin/setup-grunt` [#484](https://github.com/markshust/docker-magento/pull/484).
- Fixed cron not working [#540](https://github.com/markshust/docker-magento/issues/540).

## [39.1.0] - 2021-09-21

### Updated
- Replace MailHog with Mailcatcher for multi-arch compatibility [#511](https://github.com/markshust/docker-magento/issues/511).

## [39.0.2] - 2021-09-21

### Fixed
- Fixed placement of enabling developer mode within bin/setup.

## [39.0.1] - 2021-09-21

### Fixed
- Connection to Redis fails without php-redis extension [#474](https://github.com/markshust/docker-magento/issues/474).

## [39.0.0] - 2021-09-21

### Added
- New Elasticsearch Docker images `7.9`, `7.9.3-0` [#488](https://github.com/markshust/docker-magento/issues/488).

### Updated
- Replace Percona DB with MariaDB 10.4 [#514](https://github.com/markshust/docker-magento/issues/514).
- Updated RabbitMQ image to 3.8.

### Fixed
- Resolve cron install script not in bin/setup [#420](https://github.com/markshust/docker-magento/issues/420).
- Update Elasticsearch settings to fix catalog search index error [#488](https://github.com/markshust/docker-magento/issues/488).

## [38.0.0] - 2021-07-27

### Added
- Composer 2 support [#409](https://github.com/markshust/docker-magento/issues/409).

### Fixed
- Composer `auth.json` not properly set after installation [#42](https://github.com/markshust/docker-magento/issues/42).
- `bin/remove` not removing containers in newer versions of Docker Compose.
- Invalid template error with Docker 3.5.1 [#486](https://github.com/markshust/docker-magento/issues/486).

## [37.0.2] - 2021-02-17

### Added
- New `bin/setup-composer-auth` file to setup Composer auth creds.

## [37.0.1] - 2021-02-15

### Fixed
- Fix onelinesetup script bug.

## [37.0.0] - 2021-02-14

### Added
- Official support for Xdebug 3 [#390](https://github.com/markshust/docker-magento/issues/390). The new PHP images are `7.3-fpm-12` & `7.4-fpm-5`.
- If you need to still use Xdebug 2, update your docker-compose.yml files to instead look at PHP image `7.3-fpm-11` or `7.4-fpm-4`. These images are exactly the same other than being pegged to Xdebug 2.

## [36.0.2] - 2021-02-14

### Updated
- Reverted Xdebug to version 2 for backwards-compatible support [#390](https://github.com/markshust/docker-magento/issues/390).

## [36.0.1] - 2021-02-04

### Updated
- Reverted DB image back to `percona:5.7` until issues with MySQL 8.0 image are resolved.

## [36.0.0] - 2021-02-04

### Added
- New Elasticsearch Docker images `7.7`, `7.7.1-0` [#392](https://github.com/markshust/docker-magento/issues/392).
- SpellCheck GitHub Action for continuous integration checks of shell scripts [#387](https://github.com/markshust/docker-magento/pull/387), [#388](https://github.com/markshust/docker-magento/pull/388).

### Fixed
- Support filesystem paths with spaces [e5f22e56](https://github.com/markshust/docker-magento/commit/e5f22e56fcd382b8339d5804a9d236dd6b238a3d).
- Added missing `bin/cache-clean` file [f0e57202](https://github.com/markshust/docker-magento/commit/f0e5720281cd9f536f163bd5bdfe5bd66a956dc6).

### Updated
- Updated PHP images to NodeJS version 14 LTS [4a81f2b8](https://github.com/markshust/docker-magento/commit/4a81f2b8c61674b261ee7b42752e21fc8d5e945d).
- Changed `db` service to use MySQL 8.0 Docker image.

## [35.0.0] - 2021-01-29

### Added
- Automatically purge caches for a better dev experience [#380](https://github.com/markshust/docker-magento/issues/380).
- Stop script execution on error [#363](https://github.com/markshust/docker-magento/pull/363/).
- Make xdebug command understand partials [#371](https://github.com/markshust/docker-magento/pull/371).
- Extended functionality for `bin/xdebug`, including new `status` and `toggle` commands [#332](https://github.com/markshust/docker-magento/pull/332).
- Check Elasticsearch connection before setup:install [#326](https://github.com/markshust/docker-magento/pull/326).

### Updated
- The onelinesetup now accepts a `community` or `enterprise` param to pick version to install [b2399ff1](https://github.com/markshust/docker-magento/commit/ad573f6f3c8d2f7066034cbde936a86eb2399ff1).
- Fix bin/start for macOS Big Sur [#355](https://github.com/markshust/docker-magento/pull/355/).

## [34.2.0] - 2020-10-15

### Updated
- Updated Composer to version `1.10.15` to avoid nag update messages in new PHP Docker images `7.3-fpm-9`, `7.4-fpm-2`.

## [34.1.0] - 2020-10-15

### Added
- HTTP/2 added to Nginx image `1.18-4`

### Updated
- `bin/download` falls back to using Composer if archive download fails or is not found.

## [34.0.0] - 2020-10-11

### Added
- New `bin/setup-integration-tests` script to setup integration tests [3c021ff](https://github.com/markshust/docker-magento/commit/3c021ff6c92e49fad669deed0805cceae26bdccf).
- Added `MYSQL_HOST` environment variable to `env/db.env` file.
- New Nginx `1.18-3` Docker images uses Alpine as base image [PR #306](https://github.com/markshust/docker-magento/pull/306).

### Updated
- Prevent containers from starting if volume mapping doesn't exist, validate volumes to avoid empty folder creation [PR #256](https://github.com/markshust/docker-magento/pull/256).
- Setup script uses MySQL `env/db.env` file for database connection credentials [PR #302](https://github.com/markshust/docker-magento/pull/302).
- Increased MySQL's `max_allowed_packet` to `64M` in `docker-compose.yml` file [PR #303](https://github.com/markshust/docker-magento/pull/303).
- `docker-compose.yml` now uses Alpine images for Redis and RabbitMQ [#305](https://github.com/markshust/docker-magento/pull/305).
- `docker-compose.yml` file now uses new Alpine images for Redis, RabbitMQ & Nginx.
- `bin/setup` script updated to use Redis for cache and session directly in installer script [PR #304](https://github.com/markshust/docker-magento/pull/304).
- `bin/setup` script sets Admin URL to `/admin` [PR #304](https://github.com/markshust/docker-magento/pull/304).
- Enabling/disabling Xdebug now only restarts `phpfpm` container rather than all containers [PR #314](https://github.com/markshust/docker-magento/pull/314).
- `bin/setup` script moves `.vscode` directory to `src` after install [846d02c](https://github.com/markshust/docker-magento/commit/846d02c12c5af8005fe0cbb0b167b97f501db0c9).

### Fixed
- Exception while running integration tests [#292](https://github.com/markshust/docker-magento/pull/292).
- Nested files not copying in copytocontainer script [#295](https://github.com/markshust/docker-magento/pull/295) [#296](https://github.com/markshust/docker-magento/pull/295).
- Ubuntu unable to start because of missing volumes [#309](https://github.com/markshust/docker-magento/issues/309).

## [33.0.0] - 2020-07-30

### Added
- The `php:7.4-fpm` Docker image has been setup with full support for Magento 2.4 (see [images/php/7.4](https://github.com/markshust/docker-magento/tree/master/images/php/7.4)).
- Added easy way to mount an SSH key to the container (see [#89](https://github.com/markshust/docker-magento/issues/89)).
- The `bin/download` script now falls back to Hypernode's Magento Download mirror in the event the archive doesn't exist or fails to download from Nexcess.

### Updated
- All Docker volumes now use `:cached` rather than `:delegated`. The `delegated` volume functionality is changing in a future version of Docker for Mac to use Mutagen volumes, and the implementation is very buggy & awkward. Using the `cached` flag retains the current functionality we've been using in `delegated` without any changes (confirmed in [docker/for-mac#1592](https://github.com/docker/for-mac/issues/1592#issuecomment-662504816)).
- Updated `bin/setup-ssl-ca` so SSL generation works on Linux ([#222](https://github.com/markshust/docker-magento/issues/222))
- Updated `php` Docker images to use most recent version of Composer (1.10.9).
- The `bin/setup` script now runs `composer update` rather than `composer install`. There was an error happening with `composer install`, and with the start of the project it's best to just get the most recent Composer packages anyway.
- The `bin/setup` script now sets Elasticsearch 7 as the default catalog search engine directly when executing `bin/magento setup:install`.

### Removed
- All `latest` tags have been removed on all Docker images. It is bad practice to not use a specific version. The `latest` tag will no longer be recompiled when new images are released.
- The `php:7.2` Docker images have been deprecated, as that version is no longer supported in Magento.
- The `elasticsearch:6` Docker images have been deprecated, as those versions are no longer supported in Magento.
- Removed invalid checksum hack fix in `bin/setup` for `google-shopping-api` package, as that is only applicable to older versions of Magento.

## [32.0.1] - 2020-05-12

### Fixed
- Backed out last Elasticsearch update with elasticsearch.yml, caused issues with startup.

## [32.0.0] - 2020-05-11

### Fixed
- Updated `bin/dev-urn-catalog-generate` to account for new versions of PHPStorm (simplified).
- Indexing error with possible ElasticSearch modules ([#262](https://github.com/markshust/docker-magento/issues/262)).

### Updated
- Updated ElasticSearch 6 to version 6.8.

## [31.0.2] - 2020-04-30

### Fixed
- Fixed typo in last build image, new version is `magento-nginx:1.18-2`.

## [31.0.1] - 2020-04-30

### Fixed
- Reverted old SSL cert, it needs to exist as default cert until new certs are generated.

## [31.0.0] - 2020-04-30

### Added
- New `magento-nginx:1.18` Docker image.
- New `magento-elasticsearch:7.6` Docker image.
- Documentation to install Magento directly with sample data (using `with-samples-` prefix (thanks Nexcess!).

### Updated
- The `bin/setup` helper script to enable Elasticsearch 7 and automatically reindex during installation.
- The `docker-compose.yml` file now references the `magento-nginx:1.18-0` and `magento-elasticsearch:7.6.2-0` Docker images.
- The `docker-compose.yml` adds the new environment variable `"discovery.type=single-node"` for compatibility with Elasticsearch 7.
- The new `nginx:1.18` Docker image sets `fastcgi_buffer_size 64k;` and `fastcgi_buffers 8 128k;` directives for Magento 2.3.5 compatibility.

### Removed
- Old SSL cert being generated directly on Nginx image (deprecated).
- References to Nginx 1.13 images (deprecated).

## [30.0.3] - 2020-04-25

### Updated
- Reverted disabling Temando_Shipping module in bin/magento for sample data installation. <a href="https://github.com/markshust/docker-magento/issues/250">#250</a>

## [30.0.2] - 2020-04-17

### Fixed
- The `Temando_Shipping` module conflicts with sample data installation. Added fix to `bin/magento` helper script to disable this module, install sample data, then re-enable it.

### Added
- Added a `--remove-orphans` flag to `bin/start` script to remove orphaned containers (applicable to cron service).

## [30.0.1] - 2020-03-18

### Updated
- Increased php.ini `memory_limit` to `4G` to get PHPUnit tests to pass
- Increased php.ini `upload_max_filesize` and `post_max_size` to `100M` just to prevent issues from being filed in the future

### Added
- New PHP image tags `7.2-fpm-9`, `7.3-fpm-6`

## [30.0.0] - 2020-03-09

### Added
- Added new CLI to connect to MySQL

### Updated
- Updated readme with new bin/mysql documentation
- n98-magerun2 to install on exec of `bin/n98-magerun2` instead of `bin/setup` script
- Increased `max_input_vars` to `10000` to prevent Invalid Form Post submission errors

### Fixed
- Fixed PHP ioncube module missing ioncube.so file
- Disable TTY on `bin/setup-ssl-ca script`
- Fixed `bin/copytocontainer` script not copying files to proper directory

## [29.0.0] - 2020-01-31

### Fixed
- Fixed implementation of grunt. The grunt-cli is now installed globally on the image and doesn't depend on contents of the `vendor` directory.

## [28.0.0] - 2020-01-31

### Updated
- Upgraded NodeJS to 10.x, as 8.x was failing to install npm due to source repository updates <a href="https://github.com/markshust/docker-magento/issues/210">#210</a>

### Removed
- Removed PHP 7.1 image from filesystem as it has been deprecated. If you need to reference the last version of these images, they are available at <a href="https://github.com/markshust/docker-magento/tree/27.2.0/images/php/7.1">https://github.com/markshust/docker-magento/tree/27.2.0/images/php/7.1</a>

## [27.2.0] - 2020-01-22

### Added
- Support for RabbitMQ <a href="https://github.com/markshust/docker-magento/pull/212">PR #212</a>

## [27.1.0] - 2020-01-20

### Added
- New `bin/setup-ssl` script to generate valid SSL certificates <a href="https://github.com/markshust/docker-magento/issues/211">#211</a>
- New `markoshust/magento-nginx:1.13-8` image containing mkcert script

### Updated
- Updated `bin/setup` to use new `bin/setup-ssl` script

## [27.0.0] - 2020-01-01

Happy new year! 🎉

### Updated
- Updated the PHP base images from Debian Stretch to Buster
- Updated PHP libsodium package to `1.0.17` to support `HASH_VERSION_ARGON2ID13` <a href="https://github.com/markshust/docker-magento/issues/193">#193</a>

### Added
- Built-in support for Blackfire.io
- New PHP image tags `7.2-fpm-5`, `7.3-fpm-2`

## [26.0.0] - 2019-12-30

### Added
- Ability for `src` directory to be a symlink

### Fixed
- Fixed Magento2 setup script with n98-magerun2.phar
- Fixed dev-urn-catalog-generate script

### Removed
- All Windows-specific setup and helper scripts. This involved changing directory structure of `compose` folder, there is no longer specific `magento-2` and `magento-2-windows` specific folders. Windows support works on Docker with WSL.
- Support for PHP 7.1 (EOL)

## [25.0.0] - 2019-10-22

### Added
- Full parity with [Magento Cloud PHP extensions](https://devdocs.magento.com/guides/v2.3/cloud/project/project-conf-files_magento-app.html#php-extensions)

### Updated
- Optimized Dockerfile install order and layer usage for all PHP images (7.1, 7.2 & 7.3)
- Updated few lib dependencies in Dockerfiles with new versions
- Pegged Composer to version 1.9.0 for predictability, moved to lower layer so updating version doesn't require full rebuild of all layers

## [24.2.0] - 2019-10-18

### Fixed
- Fixed logic of `bin/copyfromcontainer` and `bin/copytocontainer` so subdirectories are now properly copied from and to the container

### Added
- The `bin/fixowns` script now includes the ability to fix ownerships at the subdirectory level
- The `bin/copyfromcontainer` and `bin/copytocontainer` scripts now fixes permissions and ownerships of just the subdirectories that are copied

## [24.1.2] - 2019-10-15

### Fixed
- Fixed `bin/copyfromcontainer` and `bin/copytocontainer` referencing incorrect destination file locations

## [24.1.1] - 2019-10-11

### Fixed
- Added missing `bin/pwa-studio` and `bin/setup-pwa-studio` bash scripts

## [24.1.0] - 2019-10-10

### Added
- Documented in README how to retrieve `bin/update` file for previous versions that did not include it
- Added `hirak/prestissimo` composer package to `bin/setup` helper script for much faster composer installs
- Downloaded archive installs are now cached on the user's machine, so subsequent installs of Magento will no longer re-download the archive if previously downloaded. Downloaded archives are stored in the `~/.docker-magento` folder.

### Fixed
- There is an invalid checksum reference in the Nexcess archive of 2.3.3, replaced checksum reference in `bin/setup` to resolve the error

### Removed
- The previous CHANGELOG for `24.0.0` referenced `vertex/module-tax` being removed but for some reason it was not removed, now it is

## [24.0.0] - 2019-10-09

### Added
- New PHP docker image version `7.3-fpm-0` for Magento 2.3.3 support
- New Elasticsearch docker image `markoshust/magento-elasticsearch:6.5.4-0` which comes bundled with icu and phonetic plugins. The initial `6.5` version is for parity with Magento Cloud.
- New `bin/update` helper script that updates your docker-magento setup to the latest version
- Added `.gitignore` file to project root to ignore `src` directory. It is recommended to keep your root docker config files in one repository, and your Magento code setup in another. This ensures the Magento base path lives at the top of one specific repository, which makes automated build pipelines and deployments easy to manage, and maintains compatibility with projects such as Magento Cloud.
- Install n98-magerun2 when setup is executed, and added related `bin/n98-magerun` and `bin/devconsole` helper scripts.
- Added `bin/setup-pwa-studio` (BETA) helper script to easily install PWA Studio, usage accepts a single parameter being the site URL you wish PWA Studio to connect to (ex. `bin/setup-pwa-studio magento2.test`)
- Added `bin/pwa-studio` (BETA) helper script to easily run the PWA Studio NodeJS web server

### Fixed
- The `bin/dev-urn-catalog-generate` helper script has been updated for compatibility with more recent versions of PHPStorm

### Removed
- The `vertex/module-tax` Composer package installs correctly as of 2.3.0, so the line within the `bin/setup` script which prevented it from being installed was removed. If one is having issues installing an older version of Magento 2, add the following line to your `composer.json` file to prevent this package from being installed:

  `{"replace": { "vertex/module-tax": "*" }}`

## [23.2.3] - 2019-07-20

### Fixed
- The `php` base Docker image changed from Debian Stretch to Buster and broke a lot of packages, which caused a failed build for `7.1-fpm-12` & `7.2-fpm-3` tags. This update pegs the `php` Docker image to Debian Stretch.

## [23.2.2] - 2019-07-17

### Fixed
- Xdebug breakpoints not triggering

### Added
- New PHP docker image versions `7.1-fpm-12`, `7.2-fpm-3`

## [23.2.1] - 2019-07-11

### Fixed
- Mailhog container doesn't stop when running bin/stop

## [23.2.0] - 2019-07-07

### Added
- View emails sent locally through Mailhog by visiting [http://{yourdomain}:8025](http://{yourdomain}:8025)

## [23.1.1] - 2019-07-01

### Updated
- Make Dockerfile consistent between versions
- Move Docker layers to bottom for smaller downloads, useful for those using previous versions
- Same Docker version tag, so just remove Docker image locally and re-pull to use

## [23.1.0] - 2019-06-27

### Added
- `libsodium-dev` package and `sodium` PHP extension for Magento 2.3.2 support.
- New PHP docker versions `7.1-fpm-10`, `7.2-fpm-1`

## [23.0.0] - 2019-04-02

### Added
- Allow setup without SSH credentials.
- Documentation for connecting to MySQL.
- `bin/status` to check container status.

### Updated
- Readme for existing installs.
- `bin/dev-urn-catalog-generate` to look at `src` folder as project root.

### Fixed
- Readme usage of pasting command into non-standard terminal.

## [22.0.0] - 2019-02-14

### Added
- Host bind mount `var/log` folder in `docker-compose.dev.yml` for debugging purposes.
- Redis is now the default storage engine for cache and session. Massively improved performance for local dev! 🚀
- Added commented-out line in `docker-compose.dev.yml` file to easily mount `auth.json` file, with updated usage in README

### Fixed
- Cron not working correctly

## [21.1.2] - 2019-02-04

### Fixed
- Helper script `bin/fixowns` now fixes permissions on `/var/www` instead of `/var/www/html` folder.
- Removed superfluous mounting of `~/.composer` directory in `docker-compose.dev.yml` file.

## [21.1.1] - 2018-12-27

### Fixed
- Helper script `bin/copytocontainer` now calls `bin/fixowns` afterwards to ensure correct file ownerships are set.

## [21.1.0] - 2018-12-26

### Added
- Helper script `bin/removevolumes` to remove docker volumes easily.
- Added removal of `vendor` folder and force of composer install to `bin/setup` script. When installed from zip, it's possible Magento isn't installing all deps properly and assigning wrong permissions in Docker. Forcing a reinstall fixes this issue.
- Force deploy of static content when running `bin/setup` to speed up initial requests.

### Fixed
- Fixed helper script `bin/dev-urn-catalog-generate` to copy file to host.

## [21.0.0] - 2018-12-24

🎅 Santa Shust wishes you a very Merry Christmas!

### Changed
- 💯 performance improvements (14 second load times now take 7 seconds!)
  - The `bin/start` helper script no longer copies docker volumes introduced in version 18.0.0. The `docker-compose.yml` setup has been updated to only reference native Docker volumes. A new `docker-compose.dev.yml` file has been added to reference development-specific settings, including host bind mounts. Only `.composer`, `app/code`, `app/design`, `app/etc`, `composer.json`, `composer.lock`, and `nginx.conf` filesystem locations are host bind mounted. Being very specific in which files and folders are being mounted leads to drastically faster response times. The main culprit in performance penalties before was mounting `generated` and `var` folders as host bind mounts. These directories are considered "caching" folders and should never be host bind mounted.
  - If you need access to specific files that are created within the container and are not host bind mounted, you can use `bin/cli` or `bin/bash` commands to go into the container to access the files. You can also use the new `bin/copyfromcontainer` and `bin/copytocontainer` bin helper scripts to copy files & folders from or to containers.
  - If you need to host bind mount files or folders, feel free to do so within the `docker-compose.dev.yml` file! Just be aware there is a performance penalty for doing so.
- Updated `nginx` Docker image to look for `nginx.conf` file instead of `nginx.conf.sample` file. This will now require copying the `nginx.conf.sample` file to `nginx.conf`, or using a host bind mount. This location allows overrides that aren't overridden when you upgrade Magento, and allow customizations for projects. Tagged new image as `markoshust/magento-nginx:1.13-7`.
- The `bin/setup` helper script uses only the `docker-compose.yml` file, with only native docker volume mounts.
- The `bin/start` helper script uses both `docker-compose.yml` and `docker-compose.dev.yml` files. Development-only specifications should now be placed within `docker-compose.dev.yml`, such as host bind volume mounts.
- The `docker-compose.yml` file now uses a `sockdata` volume mount to mount the `/sock` directory. You may need to delete the `appdata` volume mount (`docker volume rm NAME`) and rebuild it with `bin/copytocontainer --all`.
- Removed call to `bin/fixperms` within `bin/setup` to speed up initial installation.

### Added
- Added `bin/copyfromcontainer` and `bin/copytocontainer` helper scripts to copy folders or files from or to containers. Specify the `--all` option to copy entire web directory structure.
- Added `bin/rootnotty` to run root commands with no TTY (needed for unassisted one-line setup with new volume setup).
- Added `bin/fixowns` to fix filesystem ownerships within the Docker container.
- Added `docker-compose.dev.yml` file for development-only specifications.

### Removed
- The Magento 1 version of this development environment has been deprecated and is no longer supported. PHP 5 was used as it's base, and that version has reached end-of-life. If you still wish to use this setup, please reference [compose/magento-1 on tag 20.1.1](https://github.com/markshust/docker-magento/tree/master/compose/magento-1), but please be aware these images are no longer maintained.
- The PHP 5.6 and 7.0 images have been deprecated, as both of these versions have reached end-of-life. These versions have been removed from the README and are no longer maintained. If you still wish to use these images, please reference the [README on tag 20.1.1](https://github.com/markshust/docker-magento/blob/master/README.md), but please be aware these images are no longer maintained.
- Removed `bin/copydir` and `bin/copydirall` helper scripts.

## [20.1.1] - 2018-12-10

### Fixed
- Fixed typo in docker-compose.yml for linux

## [20.1.0] - 2018-12-03

### Added
- Official support for Elasticsearch. Go to Admin > Stores > Configuration > Catalog > Catalog > Catalog Search, and select "Elasticsarch 5.0+" from the list of options. Keep all defaults the same, but set Elasticsearch Server Hostname to `elasticsearch`. Save, clear the cache, and run `bin/magento indexer:reindex` to enable.

## [20.0.0] - 2018-11-27

### Added
- Official support for Magento 2.3 & PHP 7.2. Officially tagging `7.2-fpm-0` php image.

### Updated
- Various updates to README, including references now being made to Magento 2.3.
- Added comments to docker-compose for fixes needed on Linux machines (volume mounts and host.docker.internal fix).

### Fixed
- Volume mount issues on linux. Updated `bin/start` to ignore call to `bin/copydirall` when ran on Linux.

## [19.0.0] - 2018-10-08

### Added
- Added SSL support and made it enabled by default in the nginx config. All http requests will also be forwarded to https.

## [18.1.1] - 2018-10-08

### Updated
- Magento 2 nginx configuration now includes `nginx.conf.sample` file from root installation directory for configuration, instead of having standalone configuration.

## [18.0.1] - 2018-10-08

### Fixed
- Reverted old `bin/cli` usage and created `bin/clinotty` for non-tty sessions. Updated calls in `bin/setup` and other scripts where appropriate to `bin/clinotty`.

## [18.0.0] - 2018-10-06

### Changed
- Changed the way bind mounts work with Docker compose and Magento 2.
    - Note that `bin/start` now includes a call to `bin/copydirall` after the containers start. This helper script runs a `docker cp` command of all Magento directories from the container to the host. There is still a bind mount setup to `./src` root directory.
    - There is a condition/bug within Docker that when named volumes overlap with bind mounts, the named volumes automatically sync back to the host once a `docker cp` command runs, while retaining their named volume status within the Docker container.
    - We're tapping into this very odd bug and taking advantage of this as long as we can. Since data is still fetched from within the Docker container as a named volume, this should also allow not-so-performant computers to now run this Docker setup, as it provides near or truly native filesystem performance, since requests to these directories are still fetched through the named volume as far as Docker is concerned.
- `bin/start` now runs in daemon mode, as we also need to run `bin/copydirall` immediately after starting containers so data syncs back to the host (and vice versa). This also eliminates the need to to have a terminal window open all the time for keeping containers running.

### Added
- Added back support for Magento 1 and PHP 5.6 containers. Magento 1 EOL will not be until 2020, so we should support these images and Docker Compose setup indefinitely for the time being.
- Added new `bin/restart` helper script to stop and start all containers.
- Added new `bin/remove` helper script to remove all containers.
- Added new `bin/copydir` which copies whichever folder you wish from the container to the host.
- Added new `bin/copydirall` which copies all Magento folders from the container to the host.
- Added `lib/template` and `lib/onelinesetup` for much easier installation methods.
- Added automatic Xdebug support for VS Code - no setup needed!

### Removed
- Removed `bin/initloopback` along with any references to `10.254.254.254` ip address. This may break existing Xdebug setups. Note that this ip address has been replaced with `host.docker.internal`, which should automatically resolve back to the host machine.

## [17.0.1] - 2018-10-06

### Removed
- Removed bind mount of vendor folder introduced in 16.2.0 due to inconsistency issues. Update coming soon that will implement new method of bind mounting.

## [17.0.0] - 2018-09-06

### Removed
- Removed idekey setting from php.ini config.

### Changed
- Simplified Xdebug configuration for PHPStorm. This will require configuration updates for all users using Xdebug within PHPStorm.

### Added
- Added support for Xdebug and VS Code.

## [16.2.0] - 2018-08-29

### Changed
- Updated docker-compose.yml file to volume mount vendor folder for 50% performance increase

## [16.1.0] - 2018-08-23

### Added
- Added php ssh2 extension

### Deprecated
- The PHP 5.6 release will no longer be maintained, the last released version is 16.0.0

## [16.0.0] - 2018-08-22

### Changed
- Moved `dev/auth.json` to `dev/composer/auth.json`
- Added `client_max_body_size 20M` to nginx.conf
- Added `upload_max_filesize = 20M` and `post_max_size = 20M` to php.ini

## [15.0.1] - 2018-08-03

### Fixed
- Bugs with npm permissions.

## [15.0.0] - 2018-08-03

### Added
- NodeJS 8 and npm 5 added to the PHP images!
- New PHP 7.2 image. Be aware that this hasn't yet been fully tested.
- New helper scripts bin/grunt, bin/node, bin/npm and bin/stop.

### Changed
- All bin helper script calls from ./bin/name to bin/name.
- Updated bin scripts for Windows, possible breaking updates.

## [14.0.1] - 2018-07-28

### Fixed
- Magento 2.2.5 requires username and password to be different values. Updated to dummy "John Smith" user persona with username `john.smith` and password `password123`.

## [14.0.0] - 2018-07-21

### Added
- New `dev/auth.json` file used instead of `~/.composer/auth.json` file, so each project can have different auth credentials.

### Changed
- The `cron` service is now disabled by default. This services uses higher CPU and should probably only be enabled when working on cron-related tasks (or on production).
