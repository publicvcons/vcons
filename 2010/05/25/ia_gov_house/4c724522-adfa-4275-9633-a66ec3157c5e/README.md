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
6. **published** — assembled into this vcon with a `lawful_basis` attachment.

## Lawful basis

`public_task`. The event is a proceeding involving the US House of
Representatives — a US government work in the public domain under
17 USC 105 — and the Internet Archive item is additionally dedicated CC0.
See `lawful_basis.json` (also inlined in `vcon.json`).

## Verifying the lifecycle chain

The `scitt/` directory holds five ed25519-signed lifecycle statements
(`imported → normalized → transcribed → analyzed → published`), each
binding the vcon content hash and the lawful-basis hash.

> Phase 0 note: these statements are signed locally with the project key.
> The public key is at `/.well-known/scitt-pubkey.json` in this repo.
> When the SCITT transparency service at scitt.publicvcons.org is live
> (Phase 1) the same statements will be countersigned by the ledger and
> receipts added here.

To verify:

```
python conserver/pipeline/scitt_sign.py verify --receipts scitt/
```
