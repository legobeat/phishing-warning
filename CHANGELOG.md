# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [2.1.0]
### Changed
- "Back to safety" button now triggers a `backToSafetyPhishingWarning` message to be sent on the `phishingSafelistStream` ([#84](https://github.com/MetaMask/phishing-warning/pull/84))

## [2.0.1]
### Fixed
- Restore iframe warning and "open in new tab" link ([#73](https://github.com/MetaMask/phishing-warning/pull/73))

## [2.0.0]
### Changed
- **BREAKING:** Dynamically lookup the source of a block ([#57](https://github.com/MetaMask/phishing-warning/pull/57))
  - The query parameter `newIssueUrl` is no longer accepted. Instead this page will look up the source of a block dynamically.
  - We no longer show on the page which project is responsible for the block. This will be restored in a future version.
- Redesign the phishing warning page ([#52](https://github.com/MetaMask/phishing-warning/pull/52))

## [1.2.2]
### Changed
- Update `ses` version from v0.12.4 to v10.18.1 ([#53](https://github.com/MetaMask/phishing-warning/pull/53))
- Update @metamask/design-tokens from 1.9.0 to 1.11.1 ([#46](https://github.com/MetaMask/phishing-warning/pull/46))
  - This includes minor color updates.

## [1.2.1]
### Fixed
- Fix build script to exclude file imports from `@metamask/post-message-stream` which expect to only run in the context of a Web worker ([#27](https://github.com/MetaMask/phishing-warning/pull/27))

## [1.2.0] [DEPRECATED]
### Added
- Add a check for the protocol of the url being blocked. Remove `continue at your own risk` option if protocol is disallowed ([#16](https://github.com/MetaMask/phishing-warning/pull/16))
- Add optional arg `newIssueUrl` to `getUrl` function so that the correct link to direct disputes can be specified by a hash query param. ([#23](https://github.com/MetaMask/phishing-warning/pull/23))

## [1.1.0]
### Added
- Add service worker for offline caching ([#9](https://github.com/MetaMask/phishing-warning/pull/9))
- Add favicons ([#8](https://github.com/MetaMask/phishing-warning/pull/8))
- Add actions to publish to gh-pages ([#3](https://github.com/MetaMask/phishing-warning/pull/3))
- Add dummy "main" script ([#6](https://github.com/MetaMask/phishing-warning/pull/6))
  - This allows locating the package install directory using `require.resolve`, which is better for compatibility between package managers.
  - The main script throws an error, helping to prevent accidental misuse.
- Skip initialization if the page is being loaded solely to install the service worker ([#11](https://github.com/MetaMask/phishing-warning/pull/11))
  - If the hash `#extensionStartup` is set, skip setup and assume the page is being loaded just for service worker installation. We use this technique to ensure the service worker is installed during the MetaMask extension startup process.
- Add anti-clickjacking measures ([#12](https://github.com/MetaMask/phishing-warning/pull/12))
  - A script was added to the HTML file to detect when the frame is being embedded. If it detects that it is embedded, a separate design is used that prompts the user to open the warning page in a new tab to proceed. This ensures the blocked page cannot be added to the safelist via a clickjacking attack.

## [1.0.0]
### Changed
- Initial implementation of the phishing warning page
  - This should behave identically to the phishing warning page built into the MetaMask extension.

[Unreleased]: https://github.com/MetaMask/phishing-warning/compare/v2.1.0...HEAD
[2.1.0]: https://github.com/MetaMask/phishing-warning/compare/v2.0.1...v2.1.0
[2.0.1]: https://github.com/MetaMask/phishing-warning/compare/v2.0.0...v2.0.1
[2.0.0]: https://github.com/MetaMask/phishing-warning/compare/v1.2.2...v2.0.0
[1.2.2]: https://github.com/MetaMask/phishing-warning/compare/v1.2.1...v1.2.2
[1.2.1]: https://github.com/MetaMask/phishing-warning/compare/v1.2.0...v1.2.1
[1.2.0]: https://github.com/MetaMask/phishing-warning/compare/v1.1.0...v1.2.0
[1.1.0]: https://github.com/MetaMask/phishing-warning/compare/v1.0.0...v1.1.0
[1.0.0]: https://github.com/MetaMask/phishing-warning/releases/tag/v1.0.0
