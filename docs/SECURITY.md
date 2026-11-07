# Security, permissions and limits

This page describes the current design and checks. It is **not a guarantee of
zero vulnerabilities, uninterrupted game compatibility or approval by the game publisher**.
This is an unofficial community tool.

## What runs on your PC

CM Recorder has a local recorder process, a browser dashboard and capture components
loaded inside the supported Steam Global game process. The capture components are
native executable code, not ordinary documents. They observe relevant responses
received by the game. Download the complete portable from the official release page.

A fresh setup writes a small set of product-owned capture/loader files in the
game directory. It does not patch or replace the original game executable, install
a kernel driver, change Windows certificate trust, or configure a system-wide proxy.
It does not provide game-input automation or change system mouse settings.

## Permissions and installation safeguards

Run the recorder as a normal Windows user. Writing/removing files in a protected
game folder may require running the supplied install/remove command as administrator;
this is separate from ordinary recording. Close the game before either operation.

Setup verifies the included capture payload, checks approved existing files and
records installation ownership. It refuses unknown conflicts rather than blindly
replacing files. Removal checks ownership and integrity, preserves changed/foreign
files and keeps recordings. These checks reduce accidental replacement; they do
not make malicious local software trustworthy or eliminate all installation failures.

## Local dashboard and connections

The dashboard listens on `127.0.0.1:8078` by default: a loopback address on your PC,
not a public web service. The recorder's game-data receiver also uses loopback.
You do not need to open router ports or expose it to your local network/Internet.

The dashboard checks the expected host and web origin, rejects cross-site API
access and requires a random session token for API requests. The token changes
when the app restarts. Security headers restrict scripts/images to local resources,
prevent framing and tell the browser not to cache responses.

These browser protections do **not** protect against another program with access
to the same Windows account. The game-data transport is not an authenticated
boundary against malicious software already running locally. A local attacker
with sufficient access could inspect memory/files, connect to ports or tamper with
data. Process/path verification is an additional compatibility check, not strong
isolation from a compromised device. Do not publicly proxy or forward these ports.

## Downloads, checksums and signatures

Compare the downloaded ZIP's SHA-256 with the checksum published for that exact
release. A match verifies the downloaded bytes against the published value;
it is not malware detection or independent proof of who produced the program.

**The current 0.3.0 executable is not digitally code-signed.** Its checksum does
not replace a code-signing certificate. Windows can therefore show an unknown
publisher/reputation prompt. Verify the source and file integrity before deciding
whether to run it. Do not disable antivirus or add broad security exclusions as
part of normal setup; investigate any security alert rather than automatically bypassing it.

## Data and compatibility limits

Local recordings/exports are not application-encrypted. Name filtering and
pseudonyms do not guarantee anonymity. See [privacy](PRIVACY.md).
Game updates can break capture compatibility. Automated/offline tests do not prove
compatibility with every current game build or PC. No promise is made about game
publisher policy, account outcomes or antivirus acceptance.

The release notes distinguish automated checks from real-game and clean-PC
acceptance. Independent security certification or a full penetration test is not
claimed. If you suspect a vulnerability, start with a non-sensitive description
via the [support process](../SUPPORT.md), without exposing credentials, private
recordings or another user's information.
