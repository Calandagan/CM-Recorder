# Privacy and local data

CM Recorder observes the supported Steam Global game process and stores recordings
locally. It has no automatic recording upload, cloud account or telemetry submission
feature. Opening the Mihono Studios/GitHub links uses your browser normally.

## Storage

The default root is `%LOCALAPPDATA%\CMRecorder\steam-global`:

- `race-records`: structured races, events and available raw replay records.
- `sessions`: per-session capture/provenance information.
- Product settings, sequence reservation and instance locking files also live here.

Installation ownership receipts are under `%LOCALAPPDATA%\CMRecorder\installations`.
Uninstalling owned game capture files preserves recordings. Automatic retention,
cloud backup and an import/migration feature are not supplied by this release.
Close the recorder normally before making a full local backup.

## Names and sharing

Recording starts off. Retaining rival names is opt-in. Even without plain rival
names, race results, pseudonyms, runner details, timestamps and contextual metadata
can be sensitive or identifying in combination. Exports are not guaranteed anonymous.
Changing a setting does not retroactively clean previously recorded or exported files.

Inspect exports before posting them. Never publish the full local data directory,
installation receipts, privacy salt, session/control files or account credentials.
Only share individual recordings when you are comfortable with their contents and
have the necessary permission. An export is data, not a video.

## Local connections

The panel listens on loopback (`127.0.0.1:8078` by default), with a per-session token
and same-origin checks. The receiver is process-local/loopback, not a machine-wide
traffic proxy. No Windows CA installation is required. Another process using the
same Windows account is outside the protection of this browser-session token.
Do not expose these local ports through a public proxy or router forwarding.

CM Recorder never intentionally kills another capture service or takes over its
occupied port. Close Fukukitaru before connecting the recorder's capture receiver.
