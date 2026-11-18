## Why

Nur berechtigte Personen dürfen das System nutzen, und jede Aktion muss einer Person und Funktion zugeordnet werden können. Die Anmeldung soll über AGOV erfolgen, damit keine eigenen Passwörter verwaltet werden müssen.

## What Changes

- Anmeldung über AGOV, angebunden über Amazon Cognito als Anmeldedienst der Plattform.
- Eine angemeldete Person erhält erst Zugriff, wenn ihr für das Ereignis mindestens eine Funktion zugewiesen ist.
- Die Funktionen pro Ereignis werden im System geführt (nicht im Anmeldedienst), weil sie sich pro Ereignis und mitten im Einsatz ändern.
- Zuweisung der Funktionen durch eine berechtigte Funktion, mit Protokoll.
- Abmeldung, Sitzungsdauer und Sperre von Personen.
- Anmeldungen und Zugriffsversuche werden protokolliert.
- Externe Organisationen haben keinen Zugang.

## Capabilities

### New Capabilities
- `authentifizierung-agov-cognito`: Anmeldung über AGOV, Zuordnung von Personen zu Funktionen, Sitzungen und Zugriffsprotokoll.

### Modified Capabilities
<!-- keine -->

## Impact

- Abhängigkeiten: `funktionen-und-sichtrechte`, `ereignis-verwaltung`, `meldung-originalarchiv` (Zuordnung der Person zu jeder Aktion).
- Vorgesehene Technik (gehört ins Design): Cognito User Pool mit OIDC-Anbindung an AGOV. Dass Cognito OIDC-Anbieter einbinden kann, ist in der AWS-Dokumentation belegt. Dass AGOV sich so anbinden lässt und wie das Onboarding abläuft, ist nicht geprüft.
- Offene Fragen:
  - Onboarding und Voraussetzungen für die Anbindung an AGOV (wer beantragt, welche Anforderungen).
  - Haben alle Stabsmitglieder ein AGOV-Konto (auch aus Gemeinden oder Partnerorganisationen).
  - Wer weist Funktionen zu (Annahme: Chef Nachrichtendienst oder SC).
  - Notfallzugang, wenn AGOV nicht erreichbar ist (Annahme: nicht Teil des Prototyps, im Design zu klären).
  - Sitzungsdauer im Einsatz (lange Sitzungen für Schichten).
