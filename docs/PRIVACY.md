# Privacy and local data

## What is recorded

For supported races, CM Recorder saves the available course, results, runner
attributes, skills, recorded activation events and decoded replay samples. It
also saves local settings and session information such as timestamps, software
versions and integrity/provenance hashes. This is structured data, not a desktop
video, microphone recording, keyboard logger or recording of unrelated applications.

The capture module reads relevant game responses inside the supported Steam
Global process. It does not operate as a machine-wide traffic proxy. You do not
enter your Steam password into CM Recorder. Technical data needed to decode a
session is handled locally; it is not an account sign-in feature.

## Names and identifiers

Recording starts off. Keeping rival trainer names is an optional setting and is
off by default. Where privacy filtering can identify your trainer name, it removes
it; observed account identifiers are replaced with stable local pseudonyms.
If rival names are enabled, rival trainer/club names can appear in saved summaries
and exports. Stable pseudonyms can still link several races to the same runner/trainer.

**An export is not guaranteed anonymous.** Race times, results, runner builds,
context and user-entered or previously retained names may identify people in
combination. Inspect every export before sharing it. A changed name setting does
not retroactively remove information from old recordings, exports or backups.

## Where data goes

Recordings are stored on your PC. The application has no automatic recording
upload, hosted account or analytics-submission feature. Viewing local portraits
and icons does not require contacting an image server. Choosing **Download ZIP**
downloads data from your local recorder to your browser; you decide whether to
share it. Official website and GitHub links open external sites only when followed,
and those sites have their own privacy policies.

Default locations:

| Data | Windows location |
| --- | --- |
| Race records and available raw replays | `%LOCALAPPDATA%\CMRecorder\steam-global\race-records` |
| Session/provenance files | `%LOCALAPPDATA%\CMRecorder\steam-global\sessions` |
| App settings and local state | `%LOCALAPPDATA%\CMRecorder\steam-global` |
| Capture installation ownership receipts | `%LOCALAPPDATA%\CMRecorder\installations` |

## Local protection and retention

**Recordings and exported ZIPs are not encrypted at rest by this application.**
JSON and gzip/ZIP compression are readable storage formats, not password protection.
Anyone with sufficient access to your Windows account, backup or shared files may
read them. Use your normal device/account protection and manage file sharing carefully.

There is no automatic retention/deletion schedule or cloud backup in this release.
Close the recorder normally before backing up or managing its data. Keep backups
private. Removing game capture files does not delete recordings. Do not delete
ownership receipts to uninstall capture; use the supplied removal control instead.
Do not edit individual state files while the recorder is running.

## Support and your choices

You can leave recording off, select the supported modes, leave rival names off,
view existing recordings offline and choose whether to export/share data.
Never attach a full data directory, private salt, session/control files,
installation receipts, credentials or unreviewed exports to a public issue.

Read [security and permissions](SECURITY.md) for the local-access threat model.
The software license does not give the publisher ownership of your recordings;
sharing game content or another person's information still requires the relevant rights.
