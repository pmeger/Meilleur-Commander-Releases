# Meilleur Releases

Public distribution-only repository for immutable Meilleur Commander release artifacts.

## Scope

This repository may contain finished, signed release artifacts for:
- Meilleur Commander Gateway
- Windows native client
- macOS native client
- Linux native/headless client
- public checksums/signature metadata required to verify those artifacts

It must **not** contain:
- Meilleur Commander product source code
- release private/signing keys
- customer, tenant, entitlement or billing data
- enrollment/device secrets
- private deployment configuration

## Update authority

This repository is storage/CDN only. It is never update authority.

Clients must not query GitHub Releases, tags, repository contents or a global `latest` endpoint to choose an update.

The authoritative update path remains:
- Owner/Internal: assigned autonomous Gateway
- Standard/Hosted: assigned Meilleur Hosted/CTRL update authority
- Professional/Private: assigned customer Gateway after the server-side entitlement contract

The assigned authority serves the signed compatibility manifest and decides whether the state is `current`, `update_available`, `gateway_update_required` or `incompatible`.

After that decision, the authority's bounded package endpoint may redirect the binary download to an exact immutable GitHub Release asset in this repository. GitHub supplies bytes; it does not select the release.

## Verification

Every downloaded artifact remains bound to the signed release contract and must be verified before mutation, including product version, immutable build identity, source commit, platform/architecture, compatibility ranges and SHA-256/signature.

HTTPS redirects must never downgrade to HTTP. A successful download does not bypass signature/hash verification.

## Immutability

Published release assets are immutable.

Do not replace an existing asset with different bytes. New bytes require a new immutable build/release identity and version-specific asset path. Clients must never rely on GitHub `latest`.

Public availability of a binary does not grant a license or entitlement. Product capabilities remain server-authoritative.

Release signing private keys remain outside this repository.
