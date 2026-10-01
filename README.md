# sota-az — SOTA activation zones for OffARO

Mirror of the SOTA **activation-zone polygons** published by the sotl.as
project in [manuelkasper/sotlas-tiles](https://github.com/manuelkasper/sotlas-tiles)
(`az/*.geojson.gz`), repackaged as GitHub release assets so that
[OffARO](https://offaro.io) users can download an association once and keep
it offline. Release downloads do not count against anyone's Git LFS bandwidth,
which is why the files are mirrored here instead of fetched from the source
repository.

## Contents of a release

* `<assoc>.geojson.gz` — one gzip-compressed GeoJSON `FeatureCollection` per
  SOTA association (lower-case code, e.g. `la.geojson.gz`), unchanged from
  sotlas-tiles. Every feature is one summit's activation zone (`Polygon`,
  `properties.summitCode`, plus the generator's metadata: DEM summit height,
  lower contour, area, source).
* `manifest.json` — `{ version, generatedAt, associations: { LA: { file,
  bytes, sha256, summits, source }, … } }`. OffARO reads
  `releases/latest/download/manifest.json` to learn what is available and
  whether an installed association has a newer file.

Releases are tagged by month (`2026.10`) and built with
`scripts/sota-az-release.sh` in the OffARO source repository.

## Credits and terms

The zones are computed by sotl.as contributors from national high-resolution
elevation models (for Norway: Kartverket's *Nasjonal detaljert høydemodell*,
1 m; see `manifest.json` → `source` for each association). They are provided
on a best-effort basis and are **not endorsed by the SOTA Management Team** —
the activator is always responsible for operating inside the activation zone.

Per the sotlas-tiles README the polygons may be used in applications that are
freely available to users (not for commercial use), with attribution:
**Activation zones © sotl.as contributors**. OffARO's SOTA & POTA feature is
free in every edition of the app, and credits sotl.as and the elevation source
in the settings tab and the help.
