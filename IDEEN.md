# Ideen

Wohin das läuft. Die Herauslösung ist der Umzug, nicht das Ziel — am
Ende soll ein eigenes Planungswerkzeug stehen und nicht eine Kopie von
dem, was in einem Projekt entstanden ist.

Die Reihenfolge ist Absicht: **erst der Umzug, dann der Ausbau.** Wer
umgekehrt anfängt, baut die neuen Fähigkeiten in einen Motor, der noch
an seinem Herkunftsprojekt klebt — und baut sie zweimal.

---

## 1 · Verbindungen in der Oberfläche anlegen

**Heute.** Die Verknüpfung zwischen einer Zeile und ihrem Unterschirm
steht als Funktionsaufruf im HTML der Schirmdatei. Wer eine Verbindung
anlegt, öffnet die Datei und tippt die Schirm-ID ab. Ein Tippfehler
fällt erst in der Prüfung auf — und nur, wenn jemand hinsieht.

**Soll.** Element anklicken, Zielschirm aus einer Liste wählen, fertig.

**Die Schwierigkeit** ist nicht das Anklicken, sondern das Ergebnis
zurück in die Datei zu bekommen: Das Board läuft im Browser, die Datei
liegt auf der Platte. Der erste Schritt ist deshalb ein Codeschnipsel
zum Kopieren — billig, braucht kein Schreibrecht und ist sofort
nützlich. Echtes Zurückschreiben über den mitgelieferten Server später,
wenn sich zeigt, dass das Kopieren nervt.

**Fertig, wenn** eine neue Verbindung entsteht, ohne eine Schirmdatei
von Hand zu öffnen.

---

## 2 · Symbole: Herkunft klären

**Heute.** Der Herkunfts-Satz besteht aus 37 von Hand gezeichneten
SVG-Pfaden. Ihre Namen sind die von Apples SF Symbols, die Pfade sind
eigene Nachzeichnungen.

**Der Befund.** Es wird keine Apple-Datei mitverteilt — nur Namen und
eigene Pfade. Das ist deutlich sicherer als mitgelieferte SF Symbols.
Trotzdem offen: Apples Lizenz untersagt das Ableiten der Symbole. Eine
Glocke oder ein Haken ist kaum schützbar, aber eine Datei, die sich
selbst als Nachzeichnung eines lizenzierten Satzes beschreibt, trägt in
einem öffentlichen Repo ein Risiko, das sie nicht tragen muss. Dazu ist
der Satz fachlich schief für ein allgemeines Werkzeug — er enthält
Hantel, Besteck und Stethoskop.

**Drei Wege.**

| | Heißt |
|---|---|
| **a** | Eigener kleiner Satz, eigene Namen, selbst gezeichnet |
| **b** | Ein freier Satz als Grundlage — Lucide oder Feather, beide ISC/MIT |
| **c** | Nur die rund fünf Symbole, die der Rahmen braucht; alles weitere legt das Projekt nach |

Der Entwurf sieht **c** als Mechanik vor. Offen bleibt, was in diesen
fünf steckt und woher sie stammen; **b** und **c** schließen einander
nicht aus.

**Muss vor der ersten Veröffentlichung von Code beantwortet sein.**

---

## 3 · Export: aus dem Board herausschreiben

**Heute.** Genau ein Export, fest auf ein Projekt zugeschnitten: die
Palette als Quelltext einer bestimmten Sprache.

**Soll.** Ein Ausgabeformat ist ein Eintrag in der Config — eine
Funktion, die aus dem Boardzustand Text macht, plus eine Beschriftung
für den Knopf. Fehlt der Eintrag, fehlt der Knopf.

Vier Kandidaten, nach Nutzen sortiert:

1. **Ein Schirm als Spec-Text für einen Agenten.** Abschnitte,
   Beschriftungen, Zustände, welche Zeile wohin führt. Das schließt die
   Lücke zwischen Entwurf und dem, woraus tatsächlich gebaut wird — die
   beiden driften sonst, weil der Bauende eine Spec liest und nicht das
   Board.
2. **Farben** als CSS-Variablen, SCSS-Variablen oder Konstanten einer
   Sprache.
3. **Die Zustandsliste eines Schirms** als Checkliste — die
   Leerzustände, die zum Feature gehören.
4. **Das CSS eines Schirms** als Startpunkt für die Umsetzung.

Der erste ist der wertvollste und zugleich der gefährlichste: Ein
erzeugter Spec-Text, der aussieht wie eine geschriebene Spec und
weniger weiß, ist schlechter als keiner. Er muss erkennbar erzeugt sein
und sagen, woraus.

---

## 4 · Schirme mit ihrer gebauten Fassung verlinken

**Heute.** Ein Schirm trägt einen Dateipfad als bloße Zeichenkette.
Daraus wird kein Link, und es steht nicht da, welcher Stand gemeint ist.

**Soll.** Ein anklickbarer Link auf **einen Commit oder Tag**, nicht auf
den Hauptzweig. Ein Link auf den Hauptzweig zeigt in einem Jahr etwas
anderes als das, was der Entwurf meinte — und sagt es nicht.

**Zu klären: woher die Angabe kommt.** Von Hand gepflegt veraltet sie am
Tag nach dem Eintragen. Besser beim Bündeln aus Git ermitteln: der
letzte Commit, der die genannte Datei angefasst hat.

Dazu die Gegenrichtung: Ein Schirm ohne Quellangabe ist Entwurf und
noch nicht gebaut. Das soll man sehen, nicht erraten.

---

## Schon im Entwurf enthalten

Zwei naheliegende Wünsche brauchen keine eigene Karte, weil sie Teil der
Herauslösung sind:

- **Farben frei konfigurierbar.** Der Motor kennt nur sieben neutrale
  Farbrollen; die Palette des Projekts bildet darauf ab. Heute verlangen
  die Rahmen-Regeln die Farbnamen ihres Herkunftsprojekts — ein Projekt
  mit eigener Palette bekäme gar keinen Geräterahmen gezeichnet.
- **Schriften konfigurierbar.** Heute lädt das Gerüst zwei bestimmte
  Schriften fest.

## Bewusst nicht vorgesehen

- **Andere Gerätetypen als das Telefon.** Der Rahmen liegt in einer
  eigenen Datei, damit ein Web- oder Uhr-Rahmen nachrüstbar bleibt.
  Gebaut wird er nicht, bis ihn jemand braucht.
- **Ein Build-Schritt, npm oder TypeScript.** ES-Module, ein Server,
  ein Node-Skript. Was ohne Werkzeugkette läuft, läuft auch in zwei
  Jahren noch.
- **Mehr als zwei Themen in v1.** Hell und Dunkel reichen. Die
  Themenliste ist trotzdem von Anfang an eine Liste und kein Paar —
  dann kostet ein drittes Thema später keine MAJOR-Version.
