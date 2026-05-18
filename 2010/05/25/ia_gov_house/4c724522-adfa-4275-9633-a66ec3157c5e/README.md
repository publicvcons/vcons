# vcon 4c724522-adfa-4275-9633-a66ec3157c5e

**Subject:** House of Representatives Law.Gov Event (May 25, 2010)
**Source:** Internet Archive item [`gov.house.20100525`](https://archive.org/details/gov.house.20100525) (CC0 1.0, public domain)
**Recording date:** 2010-05-25
**Segment:** 25 minutes beginning at 00:02:00 of the source recording (video begins ~2 min in)

This is the first end-to-end PublicVCons artifact (Phase 0). It validates
the toolchain, the spec interpretation, and the legal posture before any
infrastructure is built.

## How it was produced

All compute ran locally on the Mac mini. No paid APIs.

1. **imported** — source mp4 downloaded from the Internet Archive; SHA-256 in `source_media.sha256`.
2. **normalized** — 25-minute segment extracted to 16 kHz mono WAV with ffmpeg.
3. **transcribed** — whisper.cpp `large-v3`.
4. **diarized + merged** — pyannote.audio 3.1 speaker turns merged onto the transcript (4 anonymous speakers).
5. **analyzed** — `llama3.1:8b-instruct-q4_K_M` via Ollama: summary, topics, entities, neutral editorial summary.
6. **published** — assembled with the upstream `vcon` library
   (vcon-dev), including its reference implementation of the IETF
   lawful-basis extension (`vcon` spec 0.4.0; `extensions:
   ["lawful_basis"]`; structured `purpose_grants`).

## Lawful basis

`public_task`. The event is a proceeding involving the US House of
Representatives — a US government work in the public domain under
17 USC 105 — and the Internet Archive item is additionally dedicated CC0.
See `lawful_basis.json` (also inlined in `vcon.json`).

## Verifying the lifecycle chain

The `scitt/` directory holds, for each lifecycle stage
(`imported → normalized → transcribed → analyzed → published`):

- `NN_stage.scitt.json` — the ed25519-signed lifecycle statement,
  binding the vcon content hash and the lawful-basis hash. Issuer
  public key: `/.well-known/scitt-pubkey.json`.
- `NN_stage.scitt-receipt.json` — the transparency **receipt**: an
  RFC 9162-style Merkle inclusion proof into the SCITT service's
  append-only log, countersigned by the service key. Service public
  key: `/.well-known/scitt-transparency-configuration.json`.

So the integrity chain is: vcon hash → signed statement → logged leaf →
Merkle root → service countersignature. Any tamper to any link fails
verification.

To verify (fully offline — no network, no service needed):

```
python scitt/cli/pvcons_scitt.py verify --receipts scitt/
```

Statement signatures alone (no receipts) can also be checked with
`python conserver/pipeline/scitt_sign.py verify --receipts scitt/`.
