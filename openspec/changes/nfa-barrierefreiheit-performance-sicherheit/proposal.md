## Why

Der Lieferprozess verlangt nichtfunktionale Anforderungen als Teil der Spezifikation und prüft sie in der Pipeline bei jedem Commit: Tests, Barrierefreiheit, Performance und Sicherheit. In den bisherigen Changes fehlen sie. Im Einsatz muss die Anwendung ausserdem unter Zeitdruck und auf verschiedenen Geräten gut bedienbar sein.

## What Changes

- Barrierefreiheit nach WCAG 2.1 Stufe AA.
- Performance nach Core Web Vitals (Ladegeschwindigkeit, Reaktionsfähigkeit, visuelle Stabilität).
- Sicherheit: Verschlüsselung bei Übertragung und Speicherung, minimale Berechtigungen, Schutz der Personendaten, Protokollierung, Prüfung auf bekannte Schwachstellen.
- Bedienbarkeit im Einsatz: Erfassung einer Meldung mit wenigen Schritten, Tastaturbedienung, verständliche Fehlermeldungen.
- Sprache: Deutsch.
- Ausfallbetrieb: Papier-Fallback für Netz- oder Stromausfall, mit späterer Nacherfassung.
- Automatisch prüfbar in der Pipeline, soweit möglich.

## Capabilities

### New Capabilities
- `nfa-barrierefreiheit-performance-sicherheit`: Nichtfunktionale Anforderungen an Zugänglichkeit, Geschwindigkeit, Sicherheit und Ausfallbetrieb.

### Modified Capabilities
<!-- keine -->

## Impact

- Gilt für alle übrigen Changes. Verweist auf `authentifizierung-agov-cognito`, `meldung-originalarchiv` und `plattform-betrieb-kosten`.
- Die Anforderungen stammen aus dem Prozessbild der Unterlagen (WCAG 2.1 AA, Core Web Vitals, Sicherheit). Die Werte der Core Web Vitals sind die üblichen "gut"-Schwellen und noch mit der FGI abzustimmen.
- Offene Fragen:
  - Konkrete Schwellenwerte und Messgeräte für Performance (Annahme: übliche "gut"-Schwellen).
  - Verfügbarkeitsziel im Einsatz (nicht vorgegeben).
  - Unterstützte Browser und Geräte (Annahme: aktuelle Browser auf Desktop, Tablet).
  - Datenstandort Schweiz, Datenschutzvorgaben und Löschpflichten.
  - Umfang des Papier-Fallbacks (Ausdruck des Meldezettels, Nacherfassung).
