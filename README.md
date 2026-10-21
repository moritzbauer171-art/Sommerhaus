# Sommerhaus-Liga & Temptation-Liga

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

## Temptation-Liga (VIP, Staffel 7)

**Spielen:** https://moritzbauer171-art.github.io/Sommerhaus/temptation/

- Für 2 bis 6 Leute, jede*r auf dem eigenen Handy. Wer die Liga erstellt, ist Admin (mit PIN).
- Personen-Draft: jede*r wählt eine vergebene Person und mehrere Verführer*innen.
- Saisontipps (welche Paare gehen gemeinsam), pro Folge drei Tipps und eine freiwillige Zockerkarte.
- Der Admin öffnet jede Folge, schließt die Tipps, trägt die Ereignisse ein und wertet aus.
- Gespeichert in Supabase: die Liga als ein Dokument, Tipps, Picks und Karten pro Person (Tabelle `league_entries`). Nach Tippschluss nimmt der Server keine Tipps mehr an.
