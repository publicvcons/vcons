# vcon 4b18caac-433c-41a2-8203-e4d892566db2

**Subject:** Iran-Contra Hearings (July 8, 1987)
**Source:** National Archives, via Internet Archive item
[`gov.archives.arc.11161`](https://archive.org/details/gov.archives.arc.11161)
(NARA ARC 11161; CC0 / public domain, FedFlix)
**Recording date:** 1987-07-08
**Segment:** first 25 minutes of the ~64-minute source

Second corpus artifact and the first from the historical priority
backlog (PROTOTYPE_PLAN.md §3.5, item p5). Produced unattended by
`conserver/backlog/run_backlog.py` → `orchestrate.py` on the offline
Mac mini; no paid APIs.

## How it was produced

`imported → normalized → transcribed → analyzed → published`, the same
pipeline as the first artifact, via the `nara_federal` source profile:

1. **imported** — mp4 fetched from the Internet Archive; SHA-256 in `source_media.sha256`.
2. **normalized** — 25-min segment → 16 kHz mono WAV (ffmpeg).
3. **transcribed** — whisper.cpp `large-v3` (793 segments).
4. **diarized + merged** — pyannote.audio 3.1 (3 anonymous speakers).
5. **analyzed** — `llama3.1:8b-instruct-q4_K_M` via Ollama.
6. **published** — assembled with the upstream `vcon` library
   (spec 0.4.0; IETF lawful-basis extension).

## Lawful basis

`public_task`. The hearing is a proceeding of the US federal
government, a US government work in the public domain under 17 USC 105;
the NARA item is additionally CC0. The NARA ARC identifier
(`gov.archives.arc.11161`) is cited in
`lawful_basis.json → metadata.source`.

## Verifying the lifecycle chain

`scitt/` holds, per stage, the ed25519 signed statement
(`NN_stage.scitt.json`) and the transparency **receipt**
(`NN_stage.scitt-receipt.json`) — an RFC 9162-style Merkle inclusion
proof into the SCITT service's append-only log, countersigned by the
service key. Verify offline (no network):

```
python scitt/cli/pvcons_scitt.py verify --receipts scitt/
```

Service public key: `/.well-known/scitt-transparency-configuration.json`.
Issuer public key: `/.well-known/scitt-pubkey.json`.
