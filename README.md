# iOS-Apps

Zwei eigene iPhone-Apps (SwiftUI, iOS 17+), automatisch gebaut und über TestFlight verteilt.
Keine Abos, kein zentraler Dienst: Alle Keys werden in den Apps auf dem Gerät eingegeben, nichts davon steht im Code.

| App | Ordner | Inhalt |
|---|---|---|
| 💪 **Vital** | `vital/` | Training mit KI-Coach, Ernährung, Gewicht, Medikamenten-Erinnerung |
| 💰 **Saldo** | `saldo/` | Finanzen: Apple-Pay-Erfassung, Bankimport, Budgets, Krypto |

Die Reise-App **Awaymate** (früher Skylog) liegt in einem eigenen Projekt:
[Nobody430/awaymate](https://github.com/Nobody430/awaymate).

## Was liegt wo

| Ort | Inhalt |
|---|---|
| `vital/`, `saldo/` | die Apps (je ein XcodeGen-Projekt, `project.yml`) |
| `.github/workflows/testflight.yml` | baut beide Apps und lädt sie zu TestFlight hoch |
| `.github/workflows/ios.yml` | unsignierter Test-Build, nur von Hand |
| `.github/scripts/` | Einrichtung von Bundle-IDs, Zertifikat und Profilen über die App-Store-Connect-API |

## Build

- Jeder Push, der eine App betrifft, baut beide Apps und lädt sie zu TestFlight hoch.
- Benötigte Repository-Secrets: `ASC_KEY_ID`, `ASC_ISSUER_ID`, `ASC_KEY_P8`, `APPLE_TEAM_ID`
  (App-Store-Connect-API-Key mit Rolle Admin).
- Bundle-IDs, Capabilities, Zertifikat und Profile werden über die API automatisch eingerichtet.
- Die Build-Nummer ist `300 + Laufnummer` des Workflows.
- Wer das Projekt forkt und selbst verteilen will, braucht ein eigenes Apple-Developer-Konto, eigene Bundle-IDs
  (in den `project.yml`) und eigene App-Einträge in App Store Connect.

## Sicherheit

- Keine Keys, Tokens oder Passwörter im Repository; alles liegt in GitHub-Secrets oder auf dem Gerät.
- Wer einen Fehler mit Sicherheitsbezug findet, meldet ihn bitte über ein privates GitHub-Advisory statt öffentlich.
