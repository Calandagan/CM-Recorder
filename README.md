# CM Recorder · Mihono Studios

**A free tool developed by [Mihono Studios](https://mihonostudios.com) for the Umamusume community.**

Record and inspect **Umamusume Pretty Derby — Steam Global** races: Room Match,
Champions Meeting groups/finals and Practice. Browse results and runner details,
inspect recorded skill activations, and export race data for independent analysis.

[Español](README.es.md) · [Download ZIP](https://github.com/Calandagan/CM-Recorder/releases/download/v0.3.0-beta.1/CMRecorder-0.3.0-Global-Test-20261107-173013-092.zip) · [Release notes](https://github.com/Calandagan/CM-Recorder/releases/tag/v0.3.0-beta.1) · [Report a problem](https://github.com/Calandagan/CM-Recorder/issues/new/choose)

## Download

**Current version: 0.3.0 — preliminary Windows x64 portable.**
Download the complete ZIP from [Releases](https://github.com/Calandagan/CM-Recorder/releases), extract it to a writable
folder outside the game directory, and keep the whole folder together.
No development tools or separate capture application are required.

The current build passed automated tests and compiled offline checks. A clean-PC
acceptance test and an end-to-end live-game acceptance test for this exact package
are not yet documented. This is a pre-release, not a production certification.

## Start recording

1. Close any other race-data recording app that may already be using the capture connection.
2. Open **Start CM Recorder.cmd** (or **CMRecorder.exe**).
3. In **Capture settings → Global capture setup**, inspect the installation status.
   An approved compatible capture installation is reused without changing it. If capture
   is missing, close Global and choose **Install capture**.
4. Enable **Record races**, then open Global through Steam. Wait for
   **Global capture connected** before entering the supported race mode.
5. After a race, choose **Inspect** or **Export recordings → Download ZIP**.

The local panel is **http://127.0.0.1:8078/**. Recording is off initially.
For viewing existing recordings without connecting to the game, open **Open Offline.cmd**.

[Full setup, update and removal guide](docs/GETTING_STARTED.md) · [Troubleshooting](docs/TROUBLESHOOTING.md)

## What you can inspect

- Race results and runner statistics, with available character portraits.
- Skill icons, descriptions and categories: acceleration, speed, green passive,
  recovery, debuff and other. Mixed effects can belong to more than one category.
- Recorded activation times and available replay data, including distance, speed,
  HP and race events. Missing or derived information must not be treated as directly observed data.
- Course statistics and **Skill activation consistency**: lowest observed activation
  frequency first, sample-size filters and conservative explanations of catalog mismatches.
- Local exports for independent analysis or race replay tools.

Not every missing activation has a provable cause. **No activation recorded** does
not by itself mean a failed activation roll. See [skill-analysis limits](docs/SKILL_CONSISTENCY.md).

## How it works, privacy and security

**Steam Global only** (appid `3224770`); JP and DMM are not supported.
This product records data; it does not send game inputs, run a bot or accelerate animations.
Fresh capture setup installs product-owned capture components in the game folder
with the game closed. It does not patch the original game executable, configure
a Windows-wide proxy or install a trusted certificate.

A capture component runs inside the game process and sends relevant race data to
the local recorder. The browser dashboard is served by your own PC; it is not an
online account or screen-recording service.

Recordings remain on your PC. The app does not automatically upload them.
Rival names are opt-in; review exports before sharing.
Local recordings and exports are not encrypted by the app. The current executable
is not digitally signed. The local web API has session/origin checks, but these
do not defend against malicious software running as your Windows user.
Local recording files are not included in the official download.

[How it works](docs/HOW_IT_WORKS.md) · [Privacy and local data](docs/PRIVACY.md) · [Security and permissions](docs/SECURITY.md) · [Recording/export format](docs/RECORDING_FORMAT.md)

## License and credits

CM Recorder is **free to download and use, with proprietary source code**.
This public repository contains documentation, issue reporting and official releases.
It does not grant general permission to redistribute modified/repackaged original
components or reuse their code. You may share the official project link.
Read [LICENSE.txt](LICENSE.txt); mandatory legal rights and separate third-party licenses remain unaffected.

Developed and published by **Mihono Studios** for the community: **https://mihonostudios.com**.
See [ABOUT.txt](ABOUT.txt), [third-party notices](THIRD-PARTY-NOTICES.txt),
[dependency notices](dependency-notices.json), [licenses](licenses/) and [artwork notices](ARTWORK-NOTICES.txt).
This is an unofficial community project, not affiliated with or endorsed by Cygames.
Umamusume Pretty Derby, characters and artwork belong to their respective rights holders.

## File integrity

Use the `.zip.sha256` asset accompanying the release. For this exact package:

```text
187cd86005794811599fb06926d6fae8e5caee172ad4d51c84a0222d0636beb2  CMRecorder-0.3.0-Global-Test-20261107-173013-092.zip
```

PowerShell: `Get-FileHash -Algorithm SHA256 -LiteralPath '.\CMRecorder-0.3.0-Global-Test-20261107-173013-092.zip'`.
The checksum detects a changed file; it is not a code-signing certificate.

## Support

Use [GitHub Issues](https://github.com/Calandagan/CM-Recorder/issues/new/choose), including the version, race mode,
setup/receiver messages and steps to reproduce. Do not attach private data folders,
tokens, account credentials or unreviewed exports. See [the support guide](SUPPORT.md).
