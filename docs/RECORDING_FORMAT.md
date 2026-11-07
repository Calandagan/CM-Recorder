# Recording and export format (Global)

This is a public data-interoperability overview. The program license does not
prohibit independent readers/visualizers merely because they support this format.
It does not grant a license to copy proprietary program code or game artwork.

## Export ZIP, not the program ZIP

Choose **Export recordings → Download ZIP**, with raw replay data enabled if
you need trajectories. A data export can contain:

```text
export.json
README.md
races.jsonl
events.jsonl
race_fixes.json             optional
raw/<race_key>.json.gz      requested and verified raw records only
```

JSONL is UTF-8, one JSON object per line. Raw files are gzip-compressed JSON, not
videos. `races.jsonl` is a summary; **trajectories are in `replay.frames` inside raw**.
Artwork, portraits and skill icons are not bundled inside recording exports.

## Schemas and identity

| Layer | Schema/client |
| --- | --- |
| Export manifest | Versioned export schema in `export.json` |
| Race record | Versioned race schema in each JSONL object |
| Event record | Versioned event schema in each JSONL object |
| Raw record | Versioned raw schema in the decompressed JSON |
| Application client | `steam-global` |
| Record/raw outer client | `steam` |
| Decoded replay client | `global` |

Read the exact schema identifier and version from the exported file; do not
rename them or infer them from the application name.

Respect `race_key` and `revision`; do not join runners or revisions by display name.
The export selects one race revision and regenerates its events. Raw is included
only if its schema, key, revision and client match. Read the revision from its
JSON content, not the exported filename. Honor `raw_missing`, `events_unavailable`,
`filter.raw` and `raw_policy` in `export.json`; absent raw must not be silently
replaced by another revision's trajectory.

The core recorder version in export metadata differs from the CM Recorder app
version. Preserve unknown fields/enums and reject unsupported versions explicitly.
Use result/runner indices consistently: a horse index is not finishing place,
gate number or frame-array index inferred from a sorted UI table.

## Decoded raw replay

The outer raw JSON has context plus `replay`, `moments` and joined runner metadata.
`replay` can be null; check this before rendering. Available replay fields include
`version`, `client`, `horse_count`, `frame_count`, `frames`, `results`, `events` and `warnings`.
Known Global binary version: `100000002`; do not assume unknown versions share its layout.

Each frame has a time `t` (seconds) and a `horses` array. Each runner's six values:

| Index | Meaning | Unit/handling |
| --- | --- | --- |
| 0 | distance | meters traveled |
| 1 | lateral lane value | raw game units, not a world XY position or integer lane |
| 2 | speed | m/s; already scaled by the parser |
| 3 | HP | raw replay HP, not percent |
| 4 | temptation/rushed mode | discrete signed enum; preserve unknown values |
| 5 | blocked-front horse | `-1` none; `0` is a valid horse index |

Use every frame's timestamp; sampling is not assumed constant. Smooth rendering
interpolates observations but does not increase measurement precision. Interpolate
continuous values only with an explicit rule; hold discrete states instead of
inventing fractional runner indices or enum values.

## Timing and results

Use one common replay clock for frames and replay events. `finish_time_raw` belongs
to that clock; `finish_time` is the displayed final result and may differ. Do not
scale each runner's timeline separately to its displayed finish time, or add start
delay again to trajectories that already contain it. Use recorded results for
placing rather than estimating placing from average speed.

Recorded samples, enriched labels and model-derived analysis are different kinds
of evidence. A viewer should mark missing/estimated data and parser warnings.
There is no complete world-space track mesh or official 3D camera path in this export.
Replaying observations is distinct from simulating an alternative build or race outcome.

## Safe web imports

Validate schemas, file paths, sizes, gzip expansion limits, finite numbers, frame
timestamps, runner counts/indices and key/revision consistency. Treat imported
names as untrusted text; never render them as HTML. Unknown/missing data should
produce an explicit unsupported/incomplete state. Review [privacy](PRIVACY.md)
before sharing exports; they are not guaranteed anonymous.
