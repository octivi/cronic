# Changelog

## [v3-octivi-3.1.0] - 2026-02-19

### Added

- Fail fast with a usage message when no wrapped command is provided ([`dda5ba4`](https://github.com/octivi/cronic/commit/dda5ba4)) (Marcin Engelmann)

### Fixed

- Avoid early exits when `xtrace` and `stderr` output are mixed and propagate wrapped command failures as `cronic` exit status ([`1ad4b17`](https://github.com/octivi/cronic/commit/1ad4b17), [`52fada8`](https://github.com/octivi/cronic/commit/52fada8)) (Marcin Engelmann)
- Escape the `PS4` pattern and render traced commands with shell-safe quoting ([`4791174`](https://github.com/octivi/cronic/commit/4791174)) (Marcin Engelmann)

## [v3-octivi-3.0.1] - 2025-12-15

### Changed

- Maintenance-only release with CI/release automation and documentation refresh (no runtime behavior changes) ([`40929bd`](https://github.com/octivi/cronic/commit/40929bd), [`6030dc0`](https://github.com/octivi/cronic/commit/6030dc0), [`adc7df7`](https://github.com/octivi/cronic/commit/adc7df7), [`0da56e1`](https://github.com/octivi/cronic/commit/0da56e1), [`3535b53`](https://github.com/octivi/cronic/commit/3535b53)) (Marcin Engelmann)

## [v3-octivi-3.0.0] - 2022-04-30

### Changed

- Adopt upstream `cronic` v2/v3 script baseline for Octivi packaging ([`740e328`](https://github.com/octivi/cronic/commit/740e328), [`63e1c40`](https://github.com/octivi/cronic/commit/63e1c40)) (Matthew Fallshaw)

### Added

- Add cleanup trap to remove the temporary directory on exit ([`5efd54a`](https://github.com/octivi/cronic/commit/5efd54a)) (Marcin Engelmann)

### Fixed

- Fix script file permissions and shellcheck-reported issues ([`93028f4`](https://github.com/octivi/cronic/commit/93028f4), [`9bf2708`](https://github.com/octivi/cronic/commit/9bf2708)) (Marcin Engelmann)

[v3-octivi-3.1.0]: https://github.com/octivi/cronic/releases/tag/v3-octivi-3.1.0
[v3-octivi-3.0.1]: https://github.com/octivi/cronic/releases/tag/v3-octivi-3.0.1
[v3-octivi-3.0.0]: https://github.com/octivi/cronic/releases/tag/v3-octivi-3.0.0
