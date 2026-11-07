# CM Recorder 0.3.0 · Steam Global test package

Developed by **Mihono Studios for the Umamusume community**.
Official website: https://mihonostudios.com.
Free to download and use under **LICENSE.txt**; the source code remains private.
See **ABOUT.txt** and the separate third-party notices supplied with the package.

This folder includes the compiled recorder, local panel and capture-only
installation payload. Python, Node, Fukukitaru and Hachimi are not required.
Keep the whole folder together. This test build has not yet passed a live-game
or clean-PC acceptance test; do not treat it as a public production release.

## Start here

1. Extract the complete ZIP to a writable folder outside the game directory.
2. Close Fukukitaru and leave the Rulership bot stopped. They use the same
   capture receiver port. CM Recorder never closes them automatically.
3. Open **Start CM Recorder.cmd** or **CMRecorder.exe**.
4. Open **Capture settings → Global capture setup**:
   - **Verified existing Rulership capture** means no installation is needed.
     Your loader, input, acceleration and other files remain unchanged.
   - If capture is missing, close Global and click **Install capture**. Only
     the included capture profile is installed. Foreign DLLs are never replaced.
   - If folder access is denied, close the recorder and Global, right-click
     **Install Capture.cmd** and select **Run as administrator**. Then start
     CM Recorder normally.
5. If the receiver says the port is busy, close the other capture service and
   click **Reconnect capture**. CM Recorder will not take over an occupied port.
6. Enable **Record races** before opening Global or entering Room Match/CM.
   Leave rival names off unless you want them in your local records and exports.
7. Open Global through Steam. Wait for **Global capture connected** in the panel.
8. Play a Room Match or CM race you already intended to play. No career is needed.
   Check the new row, your finishing positions, course and runner count.
9. Open **Export recordings → Download ZIP**, with raw replay data enabled, to inspect/export the
   same structured records and replay data as Rulership's recorder.

The panel address is **http://127.0.0.1:8078/**. If the browser did not open,
enter that address manually. The first recording is off by default.

You do not need a new race just to confirm installation. First verify the
setup state, receiver state and bridge connection, then use a planned race.

## Inspect runners and skills

Click **Inspect** on a recorded race, then choose a runner in finishing order.
Portraits identify known Global outfits; unavailable identities remain unknown.
Filter skills by Acceleration, Speed, Green passive, Recovery, Debuff or Other.
Mixed effects appear in more than one filter. Search supports skill names or IDs.
Each card shows its original icon when available, recorded activation times and
an expandable description. **No activation recorded** is not a failure verdict.
Activations with missing ownership data are labeled explicitly.

The Global catalog has 117 portraits/outfits and 61 of 63 skill icons.
Missing icons have a text placeholder. Unknown IDs may need a later catalog
refresh. Artwork is local; viewing it does not contact external services.
Course statistics also show skill icons and your runners' portraits.

When updating from 0.2.0, close the old recorder normally and start this complete
portable folder. The same data folder is reused. This UI update does not require
a game DLL replacement or a game restart.

## Your existing Rulership installation

A recognized installation is reused read-only. **Remove CM Recorder Capture**
will not delete it. No existing Rulership configuration or recordings are
imported, overwritten or deleted. The capture-only payload for a fresh game
does not include the input bridge or animation/skip modules.

## Removing a fresh CM Recorder capture installation

Close Global, then use **Remove CM Recorder Capture** in the panel or run
**Remove CM Recorder Capture.cmd**. Elevate that command only if folder
permissions require it. Only this product's four capture files are removed,
after their hashes and ownership receipt are checked. Modified or foreign
files are preserved and removal is blocked. Recordings are always kept.

An interrupted installation can be removed through the same control, then
installed again. Do not manually delete the installation receipt.

## Data and troubleshooting

- Recordings: `%LOCALAPPDATA%\CMRecorder\steam-global\race-records`.
- Session information: `%LOCALAPPDATA%\CMRecorder\steam-global\sessions`.
- Installation receipts: `%LOCALAPPDATA%\CMRecorder\installations`.
- **Open Offline.cmd** views/exports data without connecting to the game.
- Close through **Close recorder** or Ctrl+C; force-closing may lose queued data.
- No CA, Windows proxy, antivirus exclusions, account login or uploads are used.
- Global only. JP and DMM are not supported by this package.

If Steam Global is not detected, start from PowerShell with its folder:

```powershell
& ".\CMRecorder.exe" --game-dir "C:\Program Files (x86)\Steam\steamapps\common\UmamusumePrettyDerby"
```

Optional read-only check: `CMRecorder.exe --check-capture`.
Self-test with synthetic data and no game connection: `CMRecorder.exe --self-test`.

When reporting a problem, include the setup/receiver messages, whether the
race was Room Match/CM group/final, and whether the record row appeared.
Exports can include rival names if enabled; inspect them before sharing.
