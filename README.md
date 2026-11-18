# Free Cloud Android — compatibility test

This repository contains a **real Android emulator boot test**, not yet an interactive browser cloud phone. It uses GitHub Actions and does not expose Android to the internet.

## Run on iPhone
1. Open **Actions → Test free Android emulator → Run workflow**.
2. Open the job logs. A successful result includes `sys.boot_completed` returning `1` and an Android release version.

## What it does
- Checks KVM on a GitHub-hosted Linux runner.
- Starts an Android 11 (API 30) Google APIs emulator.
- Verifies it boots and lists installed packages.
- Automatically ends after the job. Apps and state are not persistent.

## Limitations
- No Safari-accessible Android display or touch controls yet.
- No persistent phone, Play Store login, or APK installation UI.
- No guarantee specific apps will run, particularly those with emulator detection.
- Public-repository standard GitHub-hosted Actions runners are free within GitHub's policy; this is CI infrastructure, not permanent phone hosting.

## Next stage
After the boot test succeeds, evaluate a browser-streaming frontend and a suitable persistent host. Never expose ADB or emulator streaming ports publicly without authentication, HTTPS and access controls.

Sources:
- https://docs.github.com/en/actions/reference/runners/github-hosted-runners
- https://github.com/ReactiveCircus/android-emulator-runner
- https://docs.cloud.google.com/compute/docs/instances/nested-virtualization/overview
