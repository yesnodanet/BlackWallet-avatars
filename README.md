# BlackWallet Avatars Storage

Public repository for user avatar files used by BlackWallet.

## Purpose
- Store only non-sensitive profile avatar images.
- Serve avatars via jsDelivr CDN.
- Keep backend metadata in app database (`avatar_key`, `avatar_updated_at`).

## File Path Convention
Backend writes files using the following key format:

`avatars/<login-segment>/avatar.<ext>`

Where:
- `<login-segment>` is sanitized login (lowercase, `[a-z0-9_.-]`).
- `<ext>` is one of: `png`, `jpg`, `webp`.

Examples:
- `avatars/alice/avatar.png`
- `avatars/admin/avatar.jpg`

## CDN URL Pattern

`https://cdn.jsdelivr.net/gh/yesnodanet/BlackWallet-avatars@main/<avatar_key>?v=<timestamp>`

`<timestamp>` is cache buster derived from `avatar_updated_at`.

## Rules
- Do not store any private or financial documents.
- Allowed image formats: PNG, JPEG, WEBP.
- Recommended max size per file: 1 MB.

## Maintenance
- Old avatar files can be removed when user changes format/path.
- This repository is intentionally public for CDN delivery.
