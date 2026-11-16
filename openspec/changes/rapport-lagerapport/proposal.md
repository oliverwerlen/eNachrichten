## Why

Im Rapport werden Lage, Anträge und Aufträge besprochen und entschieden. Heute bereitet der Stab das von Hand auf. Der Lagerapport soll alle wesentlichen Informationen seit dem letzten Rapport grafisch darstellen und den Ablauf führen.

## What Changes

- Rapportmodus mit Lagerapport. Er stellt alle wesentlichen Informationen seit dem letzten Rapport grafisch dar.
- Ablauf (Traktandenliste): Rapportziel (SC), Orientierung (C Lage / SC / alle), Konzepte (Stab), Anträge (SC / Stab), Aufträge (Kontrolle / SC), Fragen (alle), Kommunikation (Information / SC), Nächster Rapport.
- Rapportleitung durch den Adjutanten (Ablauf, Zeit, Weiterschalten). Vortragssicht für den C Lage.
- Das System schlägt vor, was wesentlich ist (Schlüsselnachrichten, Änderungen, Überfälliges). Der C Lage wählt vor Rapportbeginn aus.
- Beschlüsse im Rapport (Aufträge, Anträge, Fragen) werden zu Meldungen und laufen durch den normalen Fluss.
- Der nächste Rapport wird in die Zeitplanung eingetragen. Der Rapportzeitpunkt wird für die nächste Änderungsansicht gespeichert.
- Zugang nur für Chef ND, C Lage, Adjutant und SC.

## Capabilities

### New Capabilities
- `rapport-lagerapport`: Ablauf und grafische Darstellung des Lagerapports mit Rapportleitung und Vortragssicht.

### Modified Capabilities
<!-- keine -->

## Impact

- Abhängigkeiten: `lage-ueberblick`, `lagekarte`, `tafeln-vorgangslisten`, `tafeln-ressourcen`, `tafeln-zaehltafeln`, `zeitplanung`, `meldung-erfassen`.
- Verwandt: `rapport-inforapport`, `rapport-protokoll`.
- Offene Fragen: Bedeutung der zweiten Spalte der Ablaufliste (Annahme: Vortragende in Reihenfolge). "Rapportziel SC": wer legt das Ziel fest (Annahme: SC).
