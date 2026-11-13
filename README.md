# iOS apps

Two personal iPhone apps (SwiftUI, iOS 17+), built automatically and distributed through TestFlight.
No subscriptions and no central service: all keys are entered in the apps on the device, none of them is in the code.

| App | Folder | What it does |
|---|---|---|
| 💪 **Vital** | `vital/` | training with an AI coach, nutrition, weight, medication reminders |
| 💰 **Saldo** | `saldo/` | finances: Apple Pay capture, bank import, budgets, crypto |

The travel app **Awaymate** (formerly Skylog) lives in its own project:
[Nobody430/awaymate](https://github.com/Nobody430/awaymate).

## What is where

| Where | What |
|---|---|
| `vital/`, `saldo/` | the apps (one XcodeGen project each, `project.yml`) |
| `.github/workflows/testflight.yml` | builds both apps and uploads them to TestFlight |
| `.github/workflows/ios.yml` | unsigned test build, manual only |
| `.github/scripts/` | sets up bundle IDs, certificate and profiles through the App Store Connect API |

## Build

- Every push that touches an app builds both apps and uploads them to TestFlight.
- Required repository secrets: `ASC_KEY_ID`, `ASC_ISSUER_ID`, `ASC_KEY_P8`, `APPLE_TEAM_ID`
  (App Store Connect API key with the Admin role).
- Bundle IDs, capabilities, certificate and profiles are set up automatically through the API.
- The build number is `300 + run number` of the workflow.
- If you fork the project and want to distribute it yourself, you need your own Apple Developer account, your own
  bundle IDs (in the `project.yml` files) and your own app records in App Store Connect.

## Security

- No keys, tokens or passwords in the repository; everything is in GitHub secrets or on the device.
- If you find a security-related bug, please report it through a private GitHub advisory instead of publicly.
