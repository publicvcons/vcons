# publicvcons/vcons

Public corpus of IETF vcons for US federal government conversations, with SCITT receipts.

Part of the PublicVCons project. See https://publicvcons.org and the project plan in the workspace root for the larger picture.

## What is here

`YYYY/MM/DD/source/uuid/` directories holding:

- `vcon.json`: the canonical vcon document
- `scitt/`: SCITT statements and receipts for each lifecycle stage
- `lawful_basis.json`: the lawful basis attachment (also inlined in the vcon)

Media blobs are not stored here. They live in Digital Ocean Spaces behind `media.publicvcons.org` and are referenced from the vcon by URL plus SHA-256.

## Conventions

- Daily commit cadence, one commit per ingest batch
- Monthly tagged releases
- ISO 8601 timestamps in UTC
- SHA-256 hashes, hex encoded
- Speaker IDs stable within a vcon, anonymous unless identified

## License

CC0 1.0 Universal. The underlying material is overwhelmingly US federal works in the public domain. This dedication mirrors that posture.
