## Why

Meldungen nennen Orte oft nur umgangssprachlich: Flurnamen, Alpen, Weiler, "oberhalb der Brücke". Heute werden sie von Hand auf der Karte gesucht und eingezeichnet. Eine KI soll Orte erkennen, auflösen und als Kartenvorschlag bereitstellen, damit die Karte schneller und vollständiger nachgeführt wird.

## What Changes

- Die KI erkennt Ortsangaben im Meldungstext (Gemeinden, Weiler, Flurnamen, Alpen, Brücken, Strassen, Koordinaten, relative Angaben).
- Sie löst Orte zu einer Position auf der swisstopo-Karte auf. Bei Mehrdeutigkeit bietet sie Kandidaten zur Auswahl an. Bei Unsicherheit zeigt sie diese an.
- Sie schlägt ein Kartenobjekt mit Symbol, Ort und Zeit vor, vorausgefüllt und anpassbar. Der Chef Nachrichtendienst bestätigt oder ändert.
- Der Vorschlag verweist auf die Meldung, und jeder Ort im Text ist mit der Kartenposition verknüpft.
- Der aufgelöste Ort steht auch als Standort für Wetter und Tafeln (Ort/Sektor) zur Verfügung.

## Capabilities

### New Capabilities
- `ki-ortsaufloesung`: Erkennen und Auflösen von Ortsangaben aus Meldungen und Vorschlag von Kartenobjekten.

### Modified Capabilities
<!-- keine, siehe Hinweis in Impact -->

## Impact

- Abhängigkeiten: `meldung-erfassen`, `meldung-triage-verteilung`, `lagekarte`, `automatisierungsvorschlaege`.
- Ergänzt `lagekarte` (Kartenvorschlag aus Meldung) und `automatisierungsvorschlaege`, ohne diese Specs zu ändern, weil sie noch offene Changes sind.
- Externe Abhängigkeit: Ortsnamenverzeichnis und Geodienste von swisstopo. Ob die Dienste für Flurnamen und Alpen im Lötschental ausreichen, ist vor dem Design zu prüfen.
- Offene Fragen: Wo läuft die KI und wohin gehen die Daten (sensible Meldungen, zu klären). Wie genau muss die Position sein (Annahme: Punkt oder Fläche, mit Angabe der Genauigkeit). Was geschieht bei Orten, die nicht auflösbar sind (Annahme: Hinweis, manuelles Setzen auf der Karte).
