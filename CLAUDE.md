# Finanzleser Newsletter-Generator – Projektkontext

## Projektbeschreibung
Eine interne Web-App (`index.html`) zur Generierung von HTML-Newslettern für CleverReach.
Die App läuft lokal im Browser und nutzt die Anthropic Claude API direkt (kein Backend).

## Betreiberin
Nicole Hahn – Windows-Nutzer, Desktop-App von Claude Code.

## Aktueller Stand
- Single-Page-App (`index.html`) mit eingebettetem CSS und JavaScript
- Nutzer gibt Thema + URL oder Beschreibung ein → Claude generiert fertigem Newsletter-HTML
- API-Key wird lokal im Browser gespeichert (localStorage)
- GitHub Pages Deployment aktiv unter: `https://nicolehahn2890.github.io/Newsletter-Generator/`

## Logo
- Das echte Logo (`finanzleser` mit ">K"-Symbol in Grün #45A117) liegt auf dem Windows-PC der Nutzerin
- Pfad: `C:\Users\Nicole Hahn\Downloads\logo_green.png`
- Aktuell: nur Text-Schriftzug "finanzleser" in Montserrat 900, Farbe #45A117
- **Ziel:** Echtes PNG-Logo einbetten (als Base64 data URI), sobald Datei zugänglich ist
- Die Nutzerin muss die Datei selbst ins Repo hochladen oder per GitHub Web-Interface einfügen

## Geplanter Workflow (noch nicht umgesetzt)

```
[Web-App]
  1. Thema wählen (Kategorie per Radio-Button)
  2. Eingabe: entweder Artikel-URL ODER Live-Websuche zum Thema
  3. Newsletter-HTML wird generiert (festes Layout / Vorlage in der App)
  4. Button "An CleverReach senden"
       ↓
[Make.com Webhook]
  5. Make empfängt das fertige HTML
  6. Make erstellt via CleverReach API eine neue Kampagne als Entwurf
       ↓
[CleverReach]
  7. Entwurf liegt bereit zur manuellen Prüfung und zum Versand
```

## Architekturentscheidung: Vorlage in App, nicht in CleverReach
- Die HTML-Vorlage wird **in der Web-App** gepflegt und generiert
- CleverReach bekommt fertiges HTML per API (Kampagne direkt anlegen)
- Begründung: CleverReach-Vorlagen per Make befüllen ist unzuverlässig und komplex
- CleverReach API erlaubt das direkte Anlegen von Kampagnen mit eigenem HTML → sauberste Lösung

## Noch offene Aufgaben
- [ ] Websuche-Funktion einbauen (live Recherche zu einem Thema als Alternative zur URL-Eingabe)
- [ ] Newsletter-Layout als feste Vorlage definieren (Struktur: Begrüßung, Hauptartikel, Lesetipps, CTA, Footer)
- [ ] Make.com Webhook-Integration: Button "An CleverReach senden" in der App
- [ ] CleverReach API-Verbindung via Make einrichten
- [ ] Logo als echte Bilddatei einbetten

## Wichtige Hinweise für zukünftige Sessions
- Die Nutzerin ist **auf Windows**, der Entwicklungsserver läuft auf Linux → kein direkter Dateizugriff auf lokale Windows-Dateien
- Änderungen müssen auf **allen aktiven Branches** gepusht werden: `main`, `claude/fix-code-response-31ZTB`, `claude/financial-newsletter-studio-oFYU5`
- GitHub Pages deployt von `main`
- Nie nur auf einen Branch pushen und davon ausgehen dass es sichtbar ist
