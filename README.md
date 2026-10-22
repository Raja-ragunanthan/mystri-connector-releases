# Mystri Connector releases

Installers for **Mystri Connector**, the Windows app that keeps a client's Tally
company in step with [Mystri Audit](https://audit.mystri.ai). This repository
holds only the installers and their signed release notices. The app's source
lives with Mystri Audit.

## Getting the app

Use **Connect Tally** in Mystri Audit. The download button there always points
at the latest version, and the app links itself to your practice from there.
Each version is also attached to its [release](../../releases).

## How updates are checked

`release.json` on this repository's `main` branch describes the latest version:
its number, the installer's address, size and SHA-256, and a signature made with
Mystri's release key. That key is kept offline. Its public half is built into
the app and the portal:

```
kmHt07hIo8jpg5yosw1KU9yB0VHuQM9o+1DbzKOlJjQ=
```

The app installs an update only when the notice verifies against that key and
the downloaded installer matches the size and SHA-256 in the notice. Neither
this repository nor any file host can swap the installer on its own.

The signature covers the line `mystri-connector-release-v1` followed by the
notice's fields in canonical JSON (Ed25519).

## Windows SmartScreen

Installers are not yet code-signed, so Windows shows a SmartScreen warning the
first time one runs. Once Mystri's code-signing certificate arrives, installers
will be signed, and the app will also check the publisher before updating.
