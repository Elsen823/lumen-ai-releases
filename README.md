# Lumen AI

Android and iPhone builds of Lumen AI. The source is private; this repository publishes its
releases.

## Install

Download from the [latest release](https://github.com/Elsen823/lumen-ai-releases/releases/latest).
Each file comes with its SHA-256.

- **Android** 7 or later, arm64: install the `.apk`. Newer versions install over it and keep your
  data, and 设置 → 关于 → 检查更新 finds and installs them.
- **iPhone** with iOS 16.4 or later: the `.ipa` is unsigned. [SideStore](https://sidestore.io)
  signs it with your own Apple ID and refreshes it every 7 days on the phone; 设置 → 关于 →
  检查更新 then hands new releases to SideStore. [Sideloadly](https://sideloadly.io) works too,
  from a computer.

Nightlies are pre-releases that preview the next version. A stable install is offered stable
releases only; a nightly install is offered whichever is newer.

## How releases get here

The source repository's CI builds and signs the APK, then pushes it with the notes and the plan
to a branch `incoming/<tag>` here. [The release workflow](.github/workflows/release.yml) builds
the IPA from the same source commit, publishes the release and deletes the branch. It reads the
source through a read-only deploy key, the `SOURCE_DEPLOY_KEY` secret; the source repository
pushes with a deploy key of this one.
