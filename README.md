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
`maali-factory.bin` it flashes (no CORS), and published by the same pipeline
that publishes releases. Still nothing secret — a public page, a public image.
