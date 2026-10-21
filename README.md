# Sommerhaus-Liga & Tempto

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

## Tempto: Wettspiel zu Temptation Island VIP, Staffel 7

**Spielen:** https://moritzbauer171-art.github.io/Sommerhaus/temptation/

- Reines Wettspiel für 2 bis 6 Leute, jede*r auf dem eigenen Handy. Wer die Liga erstellt, ist Admin. Alle starten mit 100 Temptationdollar (T$); Einsätze gehen vom Konto ab, Gewinne kommen drauf. Wer nach dem Finale am meisten hat, gewinnt.
- Jede*r bekommt beim Beitreten einen persönlichen Anmeldecode (z. B. `ABCD-EFGH`). Der Server prüft ihn bei jedem Zugriff; nur der Admin darf die Liga ändern und kann verlorene Codes neu ausstellen.
- Oberfläche wie eine Wett-App: Antworten als Quoten-Kacheln, Wettschein-Leiste unten, Kontostand im Kopf. Quoten (Pott ÷ Einsatz auf die Antwort) zeigt der Server erst, wenn mindestens drei Leute auf eine Frage gesetzt haben, damit niemand einzelne Einsätze zurückrechnen kann.
- Wettbüro mit Pott-Prinzip: Alle Einsätze einer Frage landen in einem Pott, die Richtigen teilen ihn sich im Verhältnis ihrer Einsätze, in ganzen T$ mit exakter Restverteilung (größter Rest zuerst). Pötte ohne Gewinner wandern als Jackpot in den Grenz-Pott der nächsten Folge.
  - Wettschein pro Folge (zusammen mit Live-Wetten höchstens 25 T$), nur zu den Vergebenen: „Wie weit geht es heute?“ (Nur Flirten / Kuscheln / Kuss / Gemeinsame Nacht, hier liegt der Jackpot) und „Bei welchem Paar fließen Tränen?“ (Paare oder „Bei keinem“), dazu eigene Fragen des Admins.
  - Treue-Tipp: kostenlos eine*n Vergebene*n wählen, die oder der nicht weiter als Flirten geht (+5 T$), nicht zweimal hintereinander dieselbe Person. Wer pleite ist, kann damit wieder Geld holen.
  - Live-Wetten: startet der Admin während der Folge, sie erscheinen sofort als Pop-up auf allen Handys.
  - Langzeitwetten (bis 30 T$, vor dem Saisonstart): je Paar gemeinsam oder getrennt, ob ein Paar vorzeitig abbricht und bei welchem Paar zuerst die Grenze fällt. Abreisen gibt es nur hier, weil sie in der Sendung selten sind.
- Nach jeder Folge fragt die App den Admin Schritt für Schritt nur die Wetten ab, auf die jemand gesetzt hat, und verteilt dann die Pötte.
- Demomodus: mit drei Bots (Paula, Kenan, Lotte), wahlweise von vorn oder mitten in der Staffel. Läuft komplett auf dem Handy ohne Server, die echte Liga bleibt unberührt.
- Der Admin öffnet jede Folge, schließt die Wetten und startet Live-Wetten. Startguthaben, Höchsteinsätze und Treue-Bonus lassen sich im Adminmodus ändern, ebenso ein vorzeitig abgereistes Paar.
- Gespeichert in Supabase: die Liga als ein Dokument, Wetten pro Person (`league_entries`), Codes nur als Hash (`league_players`). Zugriff ausschließlich über die `tl_*`-Funktionen. Der Server prüft Kontostand und Höchsteinsätze (Startguthaben plus die vom Admin-Gerät eingetragenen Auszahlungen minus alle Einsätze) und liefert fremde Einsätze erst nach Wettschluss aus (Langzeitwetten erst nach dem Finale); vorher gibt es nur die Pott-Summen.
