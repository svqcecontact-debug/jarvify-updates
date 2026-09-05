# Jarvify updates

This repository exists so the app can find new versions of itself. It is read by
`src-tauri/src/update.rs`, which asks for exactly one address:

    https://raw.githubusercontent.com/svqcecontact-debug/jarvify-updates/main/latest.json

Two files, and nothing else belongs here.

- **`latest.json`** is the manifest. Version, download address, and a sha256 the
  app checks before it runs anything it downloaded.
- **`jarvify-<version>-setup.exe`** is the installer that manifest points at.

Both are produced by `python tools/pack.py` in the Jarvify project, which prints
these two addresses at the end of every build.

## Publishing a new version

Copy both files out of `Jarvify/updates/` into here, then:

    git add -A
    git commit -m "Publish 1.2.0"
    git push

The app checks only when somebody presses Check now in Settings. It never phones
home on its own.

## A note on size

Each installer is about 28 MB and git keeps every version forever, so this
repository grows by that much per release. That is fine for a school year. If it
ever gets uncomfortable, the fix is to attach the installer to a GitHub Release
instead and point `url` in `latest.json` at the release asset: the app only
requires https and a matching sha256, so it does not care where the file lives.
