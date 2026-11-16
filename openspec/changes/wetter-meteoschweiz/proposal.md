## Why

Wetter und Prognosen beeinflussen Lage, Einsätze und Zeitplanung im Lötschental unmittelbar. Der Führungsstab soll genaue Prognosen je Standort sehen, ohne sie von Hand zusammenzusuchen. Die Daten kommen von MeteoSchweiz und müssen nachvollziehbar (Quelle, Abrufzeit, Gültigkeit) im System erscheinen.

## What Changes

- Anbindung an MeteoSchweiz für Prognosen je Standort. Standorte sind vorhandene Orte des Systems (Einsatzorte, Unterkünfte, Sektoren, Kartenobjekte, Gemeinden des Tals) und frei gewählte Punkte auf der Karte.
- Prognose als Datenansicht: Verlauf und Werte je Standort, mit Quelle ("Quelle: MeteoSchweiz"), Abrufzeit und Gültigkeitszeitraum.
- Anzeige als Ebene auf der Lagekarte, im Lage-Überblick, in der Orientierung des Lagerapports, im Inforapport und im Planungskontext der Zeitplanung.
- Warnungen und wesentliche Wetterumschwünge werden als automatisch erzeugte Meldung (Eingang, Absender MeteoSchweiz) der Triage zugeführt. Sie durchlaufen den normalen Fluss.
- Ausfall der Verbindung: Anzeige der letzten Prognose mit deutlichem Hinweis auf ihr Alter.
- Für den Prototyp werden simulierte Daten verwendet, mit klar getrenntem Anschluss für Live-Daten.

## Capabilities

### New Capabilities
- `wetter-meteoschweiz`: Prognosen je Standort von MeteoSchweiz, Anzeige in Karte, Überblick und Rapport, Warnungen als Meldungen.

### Modified Capabilities
<!-- keine, da die betroffenen Specs (meldung-erfassen, meldung-triage-verteilung, gegenstellen-adressbuch, lagekarte) noch als offene Changes bestehen. Die Auswirkungen sind in dieser Spec als eigene Anforderungen beschrieben. -->

## Impact

- Abhängigkeiten: `meldung-erfassen`, `meldung-triage-verteilung`, `gegenstellen-adressbuch` (MeteoSchweiz als Gegenstelle), `lagekarte`, `lage-ueberblick`, `rapport-lagerapport`, `rapport-inforapport`, `zeitplanung`.
- Externe Abhängigkeit: Open Data von MeteoSchweiz (seit Mai 2025 frei nutzbar, Quellenangabe erforderlich). Ob punktgenaue lokale Prognosen in geeignetem Format abrufbar sind, ist vor dem Design zu prüfen.
- Offene Fragen: Welche Werte werden benötigt (Annahme: Niederschlag, Wind, Temperatur, Nullgradgrenze, Neuschnee, Gewitter, Sicht). Erzeugen Warnungen automatisch Meldungen (Annahme: ja, zu bestätigen). Ab welcher Stufe gilt eine Änderung als wesentlich. Spätere Anbindung der Lawinenwarnung (SLF) als eigener Change.
