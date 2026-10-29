# Roadmap and validation

All milestones are planned. No implementation or test results are claimed.

## M0 — Reproducible transport experiment

Two real Android devices: authenticated LAN/hotspot transfer, direct WebRTC internet transfer, chunk verification, interruption and resume. Publish exact device/OS/network conditions, attempts, successes, failures, time to connect, throughput, data use, and battery measurements. Do not hide failed sessions from percentages.

Initial LAN goal: at least 95% of 100 controlled connection attempts within 10 seconds. Internet success must be reported per network pair; do not promise universal direct connectivity.

Go/no-go: decide whether measured reachability supports the proposed experience. If it does not, retain honest delayed-sharing behavior or revisit infrastructure with the community.

## M1 — Local ownership

Create Android project and reproducible build instructions. Implement identity, local database, import, drafts, export, encrypted backup and tested recovery. Test process death, reboot, low storage, and lost-device recovery. Restoring identity alone must not be presented as restoring media.

## M2 — Social metadata

Profiles, follows, chronological feed, comments/reactions, signed outbox, deduplication, bounded relay queries, relay replacement, and offline reconciliation. Document protocol extensions and interoperability limits.

## M3 — Media distribution

Versioned manifests, resumable transfers, cache, explicit pin/re-serving consent, upload/storage budgets, local thumbnails, and video playback. Accept zero corrupt files as complete.

## M4 — Optional user cloud

Select providers based on verified capabilities and terms. Implement one adapter first: scoped authorization, token protection, private-media encryption, quotas, disconnect, export, and provider migration. Never promise automatic unlimited free storage.

## M5 — Pilot

Pilot with 30–50 consenting users. Test at least six physical devices across manufacturers, including low-memory phones and supported Android versions.

Network matrix: different home Wi-Fi networks, local hotspot without internet, at least two Indonesian mobile carriers, CGNAT, IPv6, blocked UDP, packet loss, and network switching.

Failure matrix: source offline, all peers offline, relay outage, force-stop, process death, reboot, revoked device, missing file, full disk, malformed metadata, replay, corrupt chunks, and request floods.

Load-test metadata separately from media. Measure fan-out, bandwidth, storage, latency, and quota rejection. Set resource-release gates after baseline measurement, not invented battery or scalability claims.
