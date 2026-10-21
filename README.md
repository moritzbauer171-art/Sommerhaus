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

- Für 2 bis 6 Leute, jede*r auf dem eigenen Handy. Wer die Liga erstellt, ist Admin.
- Jede*r bekommt beim Beitreten einen persönlichen Anmeldecode (z. B. `ABCD-EFGH`). Der Server prüft ihn bei jedem Zugriff; nur der Admin darf die Liga ändern und kann verlorene Codes neu ausstellen.
- Personen-Draft: jede*r wählt eine vergebene Person und mehrere Verführer*innen.
- Wettbüro mit Pott-Prinzip: Alle Einsätze einer Frage landen in einem Pott, die Richtigen teilen ihn sich im Verhältnis ihrer Einsätze. Ausgezahlte Münzen zählen als Punkte. Pötte ohne Gewinner wandern als Jackpot in den Grenz-Pott der nächsten Folge.
  - Wettschein pro Folge (10 Münzen): Grenze, Tränen, Abreise, Anzahl Küsse, Notfall-Lagerfeuer und eigene Fragen des Admins.
  - Überlebenswette: jede Folge eine*n Verführer*in wählen, die oder der bleibt. Der Gewinn steigt mit der Serie, jede Person nur einmal pro Staffel.
  - Live-Wetten (5 Münzen pro Folge): startet der Admin während der Folge, sie erscheinen sofort als Pop-up auf allen Handys.
  - Langzeitwetten (20 Münzen): welche Paare gemeinsam gehen und wie viele, ausgezahlt nach dem Finale.
- Der Admin öffnet jede Folge, schließt die Wetten, trägt die Ereignisse ein und wertet aus. Die Münzmengen lassen sich im Adminmodus ändern.
- Gespeichert in Supabase: die Liga als ein Dokument, Picks und Wetten pro Person (`league_entries`), Codes nur als Hash (`league_players`). Zugriff ausschließlich über die `tl_*`-Funktionen. Der Server prüft die Münzbudgets und liefert fremde Einsätze erst nach Wettschluss aus (Langzeitwetten erst nach dem Finale); vorher gibt es nur die Pott-Summen.
