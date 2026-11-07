# Troubleshooting

## Panel does not open

Open `http://127.0.0.1:8078/` after starting **Start CM Recorder.cmd**. Keep the entire
extracted portable folder together. Do not run just the EXE moved out of that folder.
Reload the page after restarting the recorder; the browser-session token changes.
The development preview port 18078 is not the portable's default address.

## Port busy or no capture connection

Close other race-data recording apps using the capture connection. Select **Reconnect capture**.
Do not delete another service's configuration or installation receipt. The app will
not terminate other services. **Open Offline.cmd** does not connect to the game.

## Capture setup is missing

Check **Capture settings → Global capture setup**. Close Global before installing
the supplied capture profile. If game-folder permissions require elevation, run
**Install Capture.cmd** as administrator, then run the recorder normally.
Do not replace foreign DLLs manually. An approved compatible capture installation is reused
without replacing its loader, input bridge or acceleration modules.

## Global folder is not detected

From PowerShell in the extracted portable directory:

```powershell
& '.\CMRecorder.exe' --game-dir 'C:\Program Files (x86)\Steam\steamapps\common\UmamusumePrettyDerby'
```

Use the actual **Steam Global** directory. JP and DMM are not supported.

## A race did not appear

Enable **Record races** and the relevant mode before entering the race. Wait for
**Global capture connected**. Report whether the race was Room Match, Practice,
CM group or CM final, and include the setup/receiver status messages.
A successful receiver connection alone does not prove the game supplied a complete replay.

## Skills or portraits are missing

Unknown IDs and unavailable catalog artwork have placeholders. The bundled Global
snapshot has 117 portraits/outfits and 61 of 63 referenced skill icons. Missing
master data can also limit enrichment without making the recorded replay unusable.
No recorded activation is not proof of a failed roll; see [skill consistency](SKILL_CONSISTENCY.md).

## Update or remove

Close the previous recorder normally; extract the new complete portable to a new
folder and start it. The default recording data directory is reused. Do not copy
individual EXE/DLL files between versions. Updating this UI does not itself require
replacing a verified existing game capture installation.

For a fresh CM Recorder-owned capture installation, close Global and use
**Remove CM Recorder Capture.cmd** or the removal control. Ownership/hash checks
preserve foreign or changed files. Removing game capture components keeps recordings.

## Offline diagnostics

```powershell
& '.\CMRecorder.exe' --check-capture
& '.\CMRecorder.exe' --self-test
```

The self-test uses synthetic data, not a real race. Do not substitute it for a
live compatibility or clean-PC test. See [SUPPORT.md](../SUPPORT.md) before sharing diagnostics.
