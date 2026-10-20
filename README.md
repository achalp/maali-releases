# Maali releases

Firmware binaries and the update manifest for the Maali irrigation
controller. Source lives in a separate (private, for now) repository;
nothing secret ever lands here.

Devices poll `https://updates.getmaali.com/manifest.json` (served from
this repo by GitHub Pages) and follow its `url` to a release asset when a
newer version is offered. Binaries are immutable once published; a bad
release is superseded by a new version, never edited in place.

## /flash — field recovery

`flash/` hosts the browser flasher, served at
`https://updates.getmaali.com/flash/`. It writes Maali onto a fresh
off-the-shelf ESP32-S3 over WebSerial (no install). It lives here, not on the
website, because it is firmware-recovery infrastructure: same-origin with the
images it flashes (no CORS), and published by the same pipeline that
publishes releases. Still nothing secret — a public page, public images.

Two boards, two images, two ESP Web Tools manifests: `manifest-waveshare-8ch.json`
writes `maali-factory-waveshare-8ch.bin`, `manifest-maali-v2.json` writes
`maali-factory-maali-v2.bin`. ESP Web Tools picks by chip family and both
boards are ESP32-S3, so one manifest cannot offer both; the page makes the
owner name the board first, and the manifest's `name` is what the confirmation
window shows (ADR 0013 §7e: a safety control, not a convenience). `manifest.json`
is the Waveshare manifest under its old name, kept for cached copies of the
page; the unnamed `maali-factory.bin` is retired.
