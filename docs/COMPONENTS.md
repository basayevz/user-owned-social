# Preliminary component review

Documentation-level review dated 2026-10-29. Not a full source, dependency, security, or legal audit. No external code has been imported. Pin and re-check the actual revision before adoption.

| Project | License observed | Proposed use / caveat |
| --- | --- | --- |
| [Amethyst](https://github.com/vitorpamplona/amethyst) | MIT | Selective Android social/relay patterns; assess coupling before extracting. |
| [0xchat](https://github.com/0xchat-app/0xchat-app-main) | MIT | Chat/UX reference; Flutter/Dart is not our Kotlin foundation; media hosting differs. |
| [Unfiltered](https://github.com/dmcarrington/unfiltered) | README license placeholder | Photo UX reference only; do not copy without clear permission. Uses Blossom uploads. |
| [Briar](https://briarproject.org/) | GPL family; exact imported file/version must be checked | Strong offline/contact-sync reference; no core integration planned. |
| [Manyverse](https://github.com/staltz/manyverse) | Mostly MPL-2.0, some CC0, per file | Local-first/SSB reference. Official FAQ says Bluetooth is no longer supported; nearby Wi-Fi remains relevant. |
| [Peergos](https://github.com/Peergos/Peergos) | AGPL-3.0 | Encrypted access-control reference; storage-server model differs. |
| [Retroshare](https://github.com/RetroShare/RetroShare) | Mixed AGPL/GPL/LGPL and other file-specific licenses | Friend-to-friend reference; Android integration and license boundaries require deeper review. |
| [libwebrtc](https://webrtc.googlesource.com/src/) | BSD-3-Clause at root, third-party notices also apply | Direct DataChannel transport candidate; Android artifact provenance must be verified. |
| [Media3](https://github.com/androidx/media) | Apache-2.0 at project level | Android playback/transformation candidate; verify selected artifacts. |
| [rust-nostr](https://github.com/rust-nostr/nostr) | MIT | Alternative core, not an additional core; project states alpha/API instability. |

Evidence and protocol references:
- [Amethyst license](https://github.com/vitorpamplona/amethyst/blob/main/LICENSE)
- [Briar copyright](https://briarproject.org/copyright/)
- [Manyverse offline](https://www.manyver.se/faq/off-the-grid/)
- [Manyverse Bluetooth status](https://www.manyver.se/faq/connect-bluetooth/)
- [Retroshare per-component licensing](https://github.com/RetroShare/RetroShare/blob/master/.reuse/dep5)
- [WebRTC license](https://webrtc.googlesource.com/src/+/refs/heads/main/LICENSE)
- [Nostr NIP-01](https://github.com/nostr-protocol/nips/blob/master/01.md)
- [Android signer NIP-55](https://github.com/nostr-protocol/nips/blob/master/55.md)
- [Android background restrictions](https://developer.android.com/develop/background-work/background-tasks/bg-work-restrictions)

For every imported component record source, revision, file list, modifications, SPDX identifiers, dependency inventory, notices, build provenance, and known vulnerabilities. Root licenses alone are insufficient for mixed repositories and binary bundles.
