## Purpose

Legt fest, wie das System in Ruhezeit und im Einsatz betrieben wird, damit es ohne Nutzung kaum Kosten verursacht und im Einsatz sofort verfügbar ist. Dazu gehört die Kostenkontrolle der KI mit manueller Freigabe ab Schwellen.

## ADDED Requirements

### Requirement: Betriebsmodus Ruhe
Das System SHALL in der Ruhezeit, wenn kein Ereignis aktiv ist, keine laufenden Rechenkosten verursachen und nur Speicherkosten tragen.

#### Scenario: Kein aktives Ereignis
- **WHEN** alle Ereignisse archiviert sind
- **THEN** befindet sich das System im Ruhemodus ohne laufende Rechenkosten

### Requirement: Betriebsmodus Einsatz
Das System SHALL bei aktivem Ereignis dauerhaft und ohne Weckverzögerung verfügbar sein.

#### Scenario: Zugriff im Einsatz
- **WHEN** eine Funktion bei aktivem Ereignis auf das System zugreift
- **THEN** antwortet das System ohne Verzögerung durch ein Wiederanlaufen

### Requirement: Umschalten mit dem Ereignis
Das System SHALL beim Aktivieren eines Ereignisses in den Einsatzbetrieb und beim Archivieren des letzten aktiven Ereignisses in den Ruhemodus wechseln.

#### Scenario: Ereignis aktivieren
- **WHEN** eine berechtigte Funktion ein Ereignis aktiviert
- **THEN** wechselt das System in den Einsatzbetrieb und meldet, wann es bereit ist

#### Scenario: Letztes Ereignis archivieren
- **WHEN** das letzte aktive Ereignis archiviert wird
- **THEN** wechselt das System in den Ruhemodus

### Requirement: Stab aufbieten
Das System SHALL eine Aktion anbieten, die das System vorab in den Einsatzbetrieb bringt, auch wenn noch kein Ereignis angelegt ist.

#### Scenario: Vorab bereit machen
- **WHEN** eine berechtigte Person "Stab aufbieten" auslöst
- **THEN** ist das System nach kurzer Zeit im Einsatzbetrieb und zeigt den Bereitschaftsstatus an

### Requirement: Wiederholung beim Wiederanlaufen
Das System SHALL Anfragen, die während des Wiederanlaufens aus der Ruhe scheitern, selbständig wiederholen und der Person einen Hinweis geben.

#### Scenario: Erste Anfrage nach der Ruhe
- **WHEN** die erste Anfrage während des Wiederanlaufens eintrifft
- **THEN** wird sie wiederholt und die Person sieht den Hinweis "System startet"

### Requirement: Umgebungen
Das System SHALL aus einer produktiven Umgebung und einer Testumgebung bestehen.

#### Scenario: Testumgebung in Ruhe
- **WHEN** in der Testumgebung keine Nutzung stattfindet
- **THEN** entstehen dort keine laufenden Rechenkosten

### Requirement: Zurücksetzbare Testumgebung
Das System SHALL die Testumgebung auf einen definierten Ausgangszustand zurücksetzen können.

#### Scenario: Zurücksetzen vor der Abnahme
- **WHEN** eine berechtigte Person die Testumgebung zurücksetzt
- **THEN** entspricht sie danach dem definierten Ausgangszustand

### Requirement: Aufgaben nur bei aktivem Ereignis
Das System SHALL periodische Aufgaben (Wetterabruf, Fristprüfung) nur bei aktivem Ereignis ausführen.

#### Scenario: Keine Aufgaben in Ruhe
- **WHEN** kein Ereignis aktiv ist
- **THEN** laufen keine periodischen Aufgaben

### Requirement: Kostenprüfung vor jedem KI-Aufruf
Das System SHALL vor jedem KI-Aufruf die Kosten schätzen und mit den Schwellen vergleichen.

#### Scenario: Aufruf unter der Schwelle
- **WHEN** die geschätzten Kosten unter allen Schwellen liegen
- **THEN** wird der Aufruf ausgeführt und der Verbrauch gezählt

### Requirement: Schwellen auf drei Ebenen
Das System SHALL Schwellen pro Aufruf, pro Ereignis und pro Zeitraum führen und konfigurierbar halten.

#### Scenario: Schwelle pro Aufruf
- **WHEN** ein einzelner Aufruf die Schwelle pro Aufruf überschreitet
- **THEN** wird er erst nach manueller Freigabe ausgeführt

#### Scenario: Schwelle pro Ereignis
- **WHEN** der Gesamtverbrauch eines Ereignisses die Schwelle erreicht
- **THEN** braucht jeder weitere KI-Aufruf eine manuelle Freigabe

### Requirement: Vorwarnung
Das System SHALL berechtigten Funktionen vor Erreichen einer Schwelle einen Hinweis mit dem aktuellen Verbrauch anzeigen.

#### Scenario: Vorwarnstufe
- **WHEN** der Verbrauch die Vorwarnstufe erreicht
- **THEN** sehen die berechtigten Funktionen den Hinweis

### Requirement: Manuelle Freigabe
Das System SHALL für Aufrufe über einer Schwelle eine Freigabe durch eine berechtigte Funktion verlangen und dabei Zweck, geschätzte Kosten und bisherigen Verbrauch anzeigen.

#### Scenario: Freigabe erteilen
- **WHEN** eine berechtigte Funktion den Aufruf freigibt
- **THEN** wird er ausgeführt und die Freigabe mit Person und Zeit protokolliert

#### Scenario: Freigabe verweigern
- **WHEN** die Funktion den Aufruf ablehnt
- **THEN** wird er nicht ausgeführt und die Ablehnung protokolliert

### Requirement: Betrieb ohne KI
Das System SHALL alle Abläufe ohne KI weiterführen, solange eine Freigabe aussteht oder die KI nicht verfügbar ist.

#### Scenario: Ausstehende Freigabe
- **WHEN** ein Aufruf auf Freigabe wartet
- **THEN** arbeiten Triage, Tafeln und Karte ohne Einschränkung manuell weiter

### Requirement: Preise aus Konfiguration
Das System SHALL Kosten aus einer konfigurierbaren Preistabelle berechnen, nicht aus festen Werten.

#### Scenario: Preis ändern
- **WHEN** ein Preis in der Konfiguration angepasst wird
- **THEN** verwenden alle weiteren Schätzungen den neuen Preis

### Requirement: Messung von Verbrauch und Kosten
Das System SHALL Verbrauch und Kosten pro Meldung, pro Anwendungsfall (Triage, Korrektur, Tafelzuordnung, Rapport) und pro Ereignis erfassen und anzeigen.

#### Scenario: Kostenübersicht
- **WHEN** eine berechtigte Funktion die Kostenübersicht öffnet
- **THEN** sieht sie Verbrauch und Kosten nach Anwendungsfall und Ereignis

### Requirement: Ausschalter für die KI
Das System SHALL berechtigten Funktionen erlauben, die KI jederzeit auszuschalten und wieder einzuschalten.

#### Scenario: KI ausschalten
- **WHEN** eine berechtigte Funktion die KI ausschaltet
- **THEN** werden keine weiteren KI-Aufrufe ausgelöst und alle Abläufe laufen manuell weiter

### Requirement: Effizienter Einsatz
Das System SHALL nur Meldungen zur KI-Auswertung senden, die dafür nötig sind, und mehrere Auswertungen einer Meldung in einem Aufruf zusammenfassen.

#### Scenario: Systemmeldung
- **WHEN** eine automatisch erzeugte Wettermeldung eingeht
- **THEN** wird sie nicht zur KI-Auswertung gesendet

#### Scenario: Mehrere Auswertungen
- **WHEN** zu einer Meldung Einstufung, Korrektur, Ort und Tafelzuordnung gebraucht werden
- **THEN** erfolgen sie in einem einzigen Aufruf
