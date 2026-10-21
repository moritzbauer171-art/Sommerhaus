# Sommerhaus-Liga

Fantasy-Liga für zwei Personen zur 11. Staffel von „Das Sommerhaus der Stars“ (RTL, 2026).

**Spielen:** https://moritzbauer171-art.github.io/Sommerhaus/

**Android-App:** [Sommerhaus-Liga.apk herunterladen](https://github.com/moritzbauer171-art/Sommerhaus/releases/latest/download/Sommerhaus-Liga.apk)

- Geführter Ablauf: Einrichtung, Draft, Saisontipps, und pro Folge Wochentipps, Punkte während der Folge, Auszüge und Abschluss.
- Die Punkte werden in Supabase gespeichert. Jede Liga hat einen eigenen Link (`…#liga=CODE`). Wer den Link hat, sieht und bearbeitet dieselbe Liga.
- Auf Android bietet Chrome „App installieren“ an, auf dem iPhone geht es über Teilen → „Zum Home-Bildschirm“.

## Aufbau

- `index.html`: die komplette Liga als eine Datei (GitHub Pages)
- `manifest.webmanifest`, `icons/`: App-Name und Icons für die Installation
- `app/`: Android-Hülle (Capacitor), die die Live-Seite lädt
- `.github/workflows/android.yml`: baut die APK automatisch, sobald sich etwas in `app/` ändert, und stellt sie unter „Releases“ bereit

## GitHub Pages einschalten

Settings → Pages → „Deploy from a branch“ → Branch `main`, Ordner `/ (root)` → Save.
