# Maali releases

Firmware binaries and the update manifest for the Maali irrigation
controller. Source lives in a separate (private, for now) repository;
nothing secret ever lands here.

Devices poll `https://updates.getmaali.com/manifest.json` (served from
this repo by GitHub Pages) and follow its `url` to a release asset when a
newer version is offered. Binaries are immutable once published; a bad
release is superseded by a new version, never edited in place.
