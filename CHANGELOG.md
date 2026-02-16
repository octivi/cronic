# Changelog

## [Unreleased]

### Changed

- Improve documentation clarity for installation, exit-code behavior, and
  security reporting guidance
  ([`ca30660`](https://github.com/octivi/cronic/commit/ca30660),
  [`8c0ad07`](https://github.com/octivi/cronic/commit/8c0ad07),
  [`2ae8a5c`](https://github.com/octivi/cronic/commit/2ae8a5c))
- Improve maintenance automation around yearly header updates and workflow
  consistency
  ([`ded33cc`](https://github.com/octivi/cronic/commit/ded33cc),
  [`6b06360`](https://github.com/octivi/cronic/commit/6b06360),
  [`d599e80`](https://github.com/octivi/cronic/commit/d599e80))

### Added

- Add fail-fast usage validation when no wrapped command is provided
  ([`dda5ba4`](https://github.com/octivi/cronic/commit/dda5ba4))
- Add and expand project badges and repository metadata in documentation
  ([`3208b31`](https://github.com/octivi/cronic/commit/3208b31),
  [`30e62be`](https://github.com/octivi/cronic/commit/30e62be))
- Add a dedicated security policy file
  ([`146b92d`](https://github.com/octivi/cronic/commit/146b92d))

### Removed

- No user-facing removals.

### Fixed

- Preserve wrapped command failure as `cronic` exit status
  ([`52fada8`](https://github.com/octivi/cronic/commit/52fada8))
- Prevent early exit when xtrace output is mixed with command stderr
  ([`1ad4b17`](https://github.com/octivi/cronic/commit/1ad4b17))
- Escape `PS4` pattern and render command with shell-safe quoting
  ([`4791174`](https://github.com/octivi/cronic/commit/4791174))
- Fix CI edge cases in release and test workflows
  ([`cae7f5a`](https://github.com/octivi/cronic/commit/cae7f5a),
  [`f98c5c3`](https://github.com/octivi/cronic/commit/f98c5c3),
  [`80f1542`](https://github.com/octivi/cronic/commit/80f1542),
  [`82db850`](https://github.com/octivi/cronic/commit/82db850))

## [3.0.1] - 2025-12-15

### Changed

- Refresh CI dependencies and repository automation for release maintenance
  ([`6030dc0`](https://github.com/octivi/cronic/commit/6030dc0),
  [`8b6ac0d`](https://github.com/octivi/cronic/commit/8b6ac0d))
- Improve project documentation and release workflow ergonomics
  ([`0da56e1`](https://github.com/octivi/cronic/commit/0da56e1),
  [`2849300`](https://github.com/octivi/cronic/commit/2849300),
  [`a3867c9`](https://github.com/octivi/cronic/commit/a3867c9))

### Added

- Add GitHub release workflow for tagged versions
  ([`adc7df7`](https://github.com/octivi/cronic/commit/adc7df7))
- Add automated yearly copyright-header update workflow
  ([`8b6ac0d`](https://github.com/octivi/cronic/commit/8b6ac0d))

### Removed

- No user-facing removals.

### Fixed

- Fix CI and test triggering behavior for pull requests
  ([`42587bd`](https://github.com/octivi/cronic/commit/42587bd))

## [3.0.0] - 2022-04-30

_This release establishes the v3 baseline for the Octivi-maintained fork._

### Changed

- Modernize shell style and readability with consistent variable expansion and
  formatting
  ([`a22fd02`](https://github.com/octivi/cronic/commit/a22fd02),
  [`f6c41bc`](https://github.com/octivi/cronic/commit/f6c41bc),
  [`d5cdaa9`](https://github.com/octivi/cronic/commit/d5cdaa9))
- Expand in-file documentation and clean up repository links
  ([`d7cafa6`](https://github.com/octivi/cronic/commit/d7cafa6),
  [`a615974`](https://github.com/octivi/cronic/commit/a615974))

### Added

- Add cleanup trap for temporary files created during execution
  ([`5efd54a`](https://github.com/octivi/cronic/commit/5efd54a))
- Add ShellCheck GitHub Actions workflow for automated linting
  ([`cbe3ffe`](https://github.com/octivi/cronic/commit/cbe3ffe))

### Removed

- No user-facing removals.

### Fixed

- Fix executable file permissions
  ([`93028f4`](https://github.com/octivi/cronic/commit/93028f4))
- Resolve ShellCheck-reported issues in the script
  ([`9bf2708`](https://github.com/octivi/cronic/commit/9bf2708))

<!-- Reference links (recommended) -->

[Unreleased]: https://github.com/octivi/cronic/compare/v3-octivi-3.0.1...HEAD
[3.0.1]: https://github.com/octivi/cronic/releases/tag/v3-octivi-3.0.1
[3.0.0]: https://github.com/octivi/cronic/releases/tag/v3-octivi-3.0.0
