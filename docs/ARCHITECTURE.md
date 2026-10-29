# Architecture proposal

Status: proposed; not implemented or benchmarked.

## Ownership model

Identity is separate from storage. A user can move devices, change cloud providers, export data, and revoke device access without intentionally changing their social identity.

Account creation initializes local identity and storage. It does not silently create a third-party cloud account or promise free capacity.

Storage choices:
- Phone only: local media and direct transfer when a source is reachable.
- Paired personal device: opt-in backup and media availability.
- User-connected cloud: optional backup/distribution using scoped authorization; never collect the provider password.

Private cloud objects should be end-to-end encrypted with user-controlled keys. Public content can be copied by recipients. Revocation prevents future authorized access where enforceable; it cannot erase copies already downloaded.

## Android modules proposed

- app / Compose UI and presentation
- identity / signer integration, recovery, paired-device authorization
- social / signed events, relay subscriptions, local feed, outbox
- storage / local media, manifests, cache, export, cloud adapter interface
- transfer / authenticated transport, chunk verification, resume, quotas
- sync / bounded metadata reconciliation and scheduling

Room, Coroutines/Flow, Media3, WorkManager, Nostr, and WebRTC are candidates pending pinned-version build and license review.

## Data paths

Metadata: local database -> signed outbox -> selected relays -> recipient database.
Device media: source -> authenticated direct P2P session -> recipient cache.
Optional cloud media: user's device -> chosen provider -> authorized recipient.

No raw thumbnails, avatars, videos, photos, or base64 previews belong in shared metadata relays. Large manifests and chunk lists travel with media transports or user storage.

## Transfer requirements

Versioned manifests identify size, format, file hash, and chunk integrity. Authenticate peers and bind signed challenges to session parameters. Verify chunks, persist progress, bound queues, and resume after interruption.

Start with complete downloads for video. Add progressive playback only after integrity and resume semantics work.

For internet direct-only mode, do not configure TURN; record selected ICE candidate types. STUN does not guarantee NAT traversal. LAN/hotspot pairing must work without internet signaling. Bluetooth is outside the initial milestone.

## Offline and lifecycle

Local data remains usable offline. Uncached media waits for an available source. Relay outages can interrupt new internet discovery. Android background restrictions and force-stop can prevent serving; WorkManager is not an always-on peer server.

Explicit opt-in governs re-serving received media. Provide cache limits, upload budgets, metered-network settings, battery controls, and clear availability states.

## Security and unresolved design

Public posts first; private groups require a reviewed key-distribution design. External NIP-55 signers are a candidate. Internal Nostr keys require compatible cryptography and protected storage; do not assume Android Keystore directly supports secp256k1.

Review replay protection, session binding, malicious manifests, oversized decodes, request flooding, storage exhaustion, cloud authorization, backup recovery, key rotation, and metadata leakage.

Direct peers may learn each other's network address. Nostr metadata does not automatically make custom P2P media interoperable with other clients. Device revocation, recovery, and identity rotation need explicit protocol decisions before release.
