# How CM Recorder works

CM Recorder saves **structured race data**, not screen recordings. You play the
game normally; the tool records supported races and presents results in a local
browser dashboard. It does not make decisions or press buttons in the game.

## The three parts

1. **Game capture component.** During setup, CM Recorder adds a small set of
   capture/loader files to the Steam Global game folder. The game must be closed.
   When Steam starts the game, these components run inside the game process and
   observe the relevant responses the game already receives. They do not request
   additional races or log in to your account on your behalf.
2. **Local recorder.** A separate program on your PC receives supported race data,
   decodes the available replay, applies privacy filtering and saves structured
   results/events. No recording upload or hosted account is required.
3. **Local dashboard.** Your browser opens `http://127.0.0.1:8078/`. This is your own
   computer, not a public website. The dashboard reads your saved races and displays
   runner details, skills, statistics and export controls.

The capture component runs in the game: it is not a screenshot-only tool or a
server-side integration. Setup does not replace the original game executable,
install a Windows root certificate or configure a system-wide network proxy.
The tool does not provide input automation or animation acceleration.

## Recording a race

Enable **Record races** and the desired modes before entering a race. Recording
is off initially. Supported modes are Room Match, Champions Meeting groups/finals
and Practice on **Steam Global**. JP and DMM are not supported.

The game must actually provide the race data. Starting the tool after the relevant
response has already passed cannot reconstruct missing information. An incomplete
replay, unknown skill or unavailable portrait remains explicitly incomplete/unknown.
Recorded samples and model-derived analysis are not the same kind of evidence.

Reopening the same replay does not intentionally count it as a new independent
race. If later data improves its coverage, the saved record can receive a newer
revision. Statistics use the selected current revision.

## Reading and exporting

**Inspect** opens a runner/skill view; it does not control the game.
**Download ZIP** creates data files that you can save or share yourself. Include
raw replay data if an independent visualizer needs trajectories. Exporting does
not automatically upload anything. These files are not a rendered video or a
prediction of a different race outcome.

**Open Offline.cmd** starts the viewer without connecting the capture receiver
or supervising the game. It can read/export existing local recordings.

## Installation, updates and removal

If setup recognizes an approved compatible capture installation, it reuses it
without replacing or claiming ownership of those files. An unknown or conflicting
installation is blocked for review rather than automatically overwritten.
Only one compatible race-data receiver can use the capture connection at once.
If it is occupied, close the other race-data app yourself and choose **Reconnect capture**.

Install/remove actions require Global to be closed. Removal checks file hashes
and ownership and only removes unchanged files installed by CM Recorder. It
preserves recordings and unrelated files. Updating the portable means extracting
the complete new folder and starting it after closing the previous recorder.
There is no automatic updater in this release.

Read [getting started](GETTING_STARTED.md), [privacy](PRIVACY.md) and
[security and permissions](SECURITY.md) for practical details and limitations.
