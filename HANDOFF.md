# Studio 1 Live — Präsentation · Übergabe-Notiz

Kurzkontext für eine **frische Session**, damit ohne den alten (bild-lastigen)
Verlauf weitergearbeitet werden kann.

## Was das ist
HTML-Präsentation (Vermarktungs-Folder „Studio 1 Live" von ProSiebenSat.1 Puls 4,
Studiovermietung Wien), erstellt mit dem **frontend-slides**-Skill aus dem
Original-PDF. Marken-treu nachgebaut, Lese-Deck-Dichte.

- **Datei:** `index.html` (self-contained, alles inline)
- **Assets:** `assets/` (Fotos aus PDF + offizielle SVGs) — ~1,4 MB
- **12 Folien**, Fixed 16:9-Stage 1920×1080, gleichmäßig skaliert (`.deck-stage` Transform)
- Öffnen: `open index.html`

## Schrift
Original **Agenda** via Adobe Typekit — im `<head>`:
`<link rel="stylesheet" href="https://use.typekit.net/vit5ssi.css">`
`--font: "agenda", 'Hanken Grotesk', sans-serif;` · nur Gewichte **400/700**
verfügbar (Headlines rendern max. 700). **Braucht Internet** (Typekit).

## Farben (CSS-Variablen in `:root`)
| Rolle | Variable | Wert |
|---|---|---|
| Signalrot | `--red` | `#DC1A31` |
| Rot hell | `--red-bright` | `#F0263D` |
| Navy tief | `--navy` | `#0A1F3B` |
| Navy Panel | `--navy-panel` | `#112540` |
| Verlauf Rot→Blau (alle roten Flächen) | `--panel-grad` | `linear-gradient(180deg,#dc1a31 0%,#8a284f 50%,#14243f 100%)` |
| Weiß | `--white` | `#ffffff` |
| Ink (Headline auf Weiß) | `--ink` | `#14161c` |
| Grau (Fließtext) | `--grey` | `#5b6472` |
| Haarlinie | `--line` | `#e4e7ec` |
| Bühnen-Rand (Letterbox) | `--stage-bg` | `#05070d` |

## Folien (Index 0-11 → „Seite" 1-12)
1 Cover `s-cover` · 2 Willkommen `s-welcome` · 3 Das Studio `s-studio` ·
4 Facts `s-facts` · 5 Vorteile `s-benefits` · 6 Technik-Intro `s-tech` ·
7 Unterschied-Tabelle `s-diff` · 8 Service/Preise `s-service` ·
9 Use Case 1 `s-uc1` · 10 Use Case 2 `s-uc2` · 11 Kontakt `s-contact` ·
12 Closing `s-end`

## Wichtige Konventionen / Fallen
- **Niemals `position` auf dem `.slide`-Element setzen** — muss `absolute`
  bleiben (Fixed-Stage). Absolute Kinder in inneren Wrappern verankern.
- **Grid-Spalten mit ausschließlich absoluten Kindern** brauchen
  `grid-template-rows:1fr`, sonst kollabieren sie auf Höhe 0.
- **Pillen:** Basis `.pill` (rot, `flex-shrink:0`). Weiße Pillen:
  `border-color:#fff; color:#fff` + Fill **Navy 40 %** (`rgba(10,31,59,.4)`)
  über Fotos, bzw. **kein Fill** (`background:none`) auf roten Flächen
  (Seite 5 & 7). Jede Sektions-Pille sitzt **in-flow direkt über ihrer
  Headline** mit **`margin-bottom:30px`** (einheitlicher Abstand per
  Konstruktion). Foto-Pillen liegen im bodenverankerten `.txt`-Block
  (`display:flex; flex-direction:column; align-items:flex-start`).
- **Rote Flächen** nutzen alle `--panel-grad` (Studio-Panel, Facts-Panel rechts,
  Vorteile-BG, Unterschied-BG, Use-Case-1-Karte).
- **Logos/Icons (SVG, weiß/rot angelegt):** `studio1live_logo.svg` (Wortmarke,
  Cover rot/klein, Closing rot), `1.svg` (rote „1"), `Setups.svg` + `Technik.svg`
  (Seite 3), `Studio.svg` (Seite 4, über „Studiofläche").
- Inline-Editing (Taste **E**), Tastatur-Nav (Pfeile/Space), Fortschrittsbalken
  oben. Seitenzahl-Pill wurde entfernt.
- `.frontend-slides/slide-previews/` existiert nicht (keine Style-Discovery,
  markentreuer Nachbau).

## Verifizieren = token-sparsam
Für deterministische Checks (Abstände, Breiten, Farben) **per JS-Messung**
prüfen statt Screenshots (Bilder sind teuer). Reload/Resize/Screenshot nur
**einmal am Ende eines Batches**. Änderungswünsche möglichst **gebündelt**.

## Status / offene Punkte
- Deck ist inhaltlich & gestalterisch fertig und verifiziert.
- **Nicht erledigt (optional, Phase 6):** Deploy auf Live-URL (Vercel) bzw.
  PDF-Export — nur bei Bedarf.
- Kein bekannter Bug offen.
