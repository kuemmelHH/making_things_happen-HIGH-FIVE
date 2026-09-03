[README.md](https://github.com/user-attachments/files/31773388/README.md)
# Das große Abklatschen

Ein gemeinsamer High-Five-Moment als Abschluss für Remote-Workshops.
Alle öffnen denselben Link, jemand startet den Countdown, bei „JETZT!" klatschen
alle 5 Sekunden lang ab – Konfetti, Sound und Zähler laufen live auf allen
Bildschirmen zusammen.

Die Seite ist eine einzige `index.html` ohne Build-Schritt.

---

## 1. Supabase – ist bereits eingetragen

Die Live-Verbindung läuft über Supabase. Die Zugangsdaten des Projekts
`high-five` stehen schon in `index.html` (ganz unten im `<script>`-Block unter
`HIER EINTRAGEN`). Du musst am Code nichts ändern.

Eine Datenbank, Tabellen oder Login braucht die Seite **nicht** – nur den
Realtime-Kanal, der ohne weitere Konfiguration funktioniert.

**Zu den Keys:** Der publishable Key ist ausdrücklich dafür gemacht, im Browser
sichtbar zu sein – er darf öffentlich im Repo stehen. Verwechsle ihn nicht mit
dem `service_role` bzw. `sb_secret_...` Key: der gehört nie in eine Webseite.

Falls du das Projekt später wechselst, findest du die beiden Werte im
Supabase-Dashboard über den Button **Connect** oder unter
**Settings → API Keys** (die URL dort im Abschnitt *Data API*).

---

## 2. Auf GitHub Pages veröffentlichen

1. Auf GitHub ein neues Repository anlegen, z. B. `high-five`. **Public**, sonst
   funktioniert Pages im kostenlosen Plan nicht.
2. `index.html` hochladen (Button **Add file → Upload files**, Datei
   reinziehen, **Commit changes**).
3. Im Repo auf **Settings → Pages**.
4. Unter *Build and deployment* bei **Source** `Deploy from a branch` wählen,
   Branch `main` und Ordner `/ (root)`, dann **Save**.
5. Nach ein bis zwei Minuten ist die Seite erreichbar unter:
   `https://DEIN-GITHUB-NAME.github.io/high-five/`

Änderst du später etwas an der Datei, ist die Seite ein bis zwei Minuten nach
dem Commit aktualisiert.

---

## 3. Im Workshop benutzen

Link in den Chat der Videokonferenz, alle öffnen ihn.

- Jede Person tippt ihren **Namen** ein – oben rechts siehst du live, wer da ist.
- Wer will, drückt **3 · 2 · 1 starten**. Der Countdown läuft synchron bei allen.
- Bei **JETZT!** hat die Gruppe 5 Sekunden. Klicken, tippen oder Leertaste,
  so oft wie möglich.
- Danach: Gesamtzahl und wer am wildesten war. **Nochmal** setzt alle zurück.

**Ton:** Der Klatschsound braucht in manchen Browsern einen ersten Klick auf der
Seite, bevor er losgeht. Wer nichts hört, klickt einmal irgendwohin.

### Mehrere Gruppen gleichzeitig

Hänge `?raum=` an die URL, dann läuft jede Gruppe in ihrem eigenen Kanal:

```
https://DEIN-NAME.github.io/high-five/?raum=team-nord
https://DEIN-NAME.github.io/high-five/?raum=vertrieb
```

Ohne Angabe landen alle im Raum `finale`. Praktisch, wenn du zwei Workshops
am selben Tag hast – oder um vorher allein zu testen, ohne dass jemand
mitzählt.

---

## Wenn etwas nicht funktioniert

Unten links steht immer der Verbindungsstatus.

| Anzeige | Bedeutung |
|---|---|
| `3 Personen hier` | Alles gut, ihr seid verbunden. |
| `solo – nicht eingerichtet` | `SUPABASE_URL` oder `SUPABASE_KEY` fehlt in der Datei. |
| `solo – Zugangsdaten prüfen` | Die Werte sind da, aber falsch formatiert. |
| `solo – keine Verbindung` | Supabase nicht erreichbar (Firewall, Projekt pausiert). |

Im Solo-Modus funktioniert die Seite weiterhin – Countdown, Konfetti und Sound
laufen, nur eben für jede Person einzeln. Als Notfallplan im Workshop völlig
brauchbar: du zählst per Stimme runter, alle klicken gleichzeitig.

Supabase pausiert Projekte im kostenlosen Plan nach längerer Inaktivität. Wenn
du die Seite ein paar Wochen nicht benutzt hast, kurz vorher einmal öffnen und
prüfen, ob der Status auf „verbunden" springt.

---

## Anpassen

Die wichtigsten Stellschrauben stehen im Skript ganz oben:

- `LIVE_MS` – Länge des Klatschfensters in Millisekunden (Standard 5000)
- `PALETTE` – die Konfettifarben
- Die Farben der Seite selbst stehen im `:root`-Block im `<style>`
