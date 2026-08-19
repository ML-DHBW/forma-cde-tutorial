# CDE Lernpfad für Autodesk Forma – GitHub Pages

Dieses Paket ist für die Veröffentlichung als statische Website über GitHub Pages vorbereitet. Es benötigt weder Python noch einen lokalen Webserver.

## Funktionsumfang des Prototyps

- Anmeldung bei Autodesk über OAuth 2.0 PKCE
- Auswahl eines berechtigten Forma-Hubs
- Auswahl eines Forma-Data-Management-Projekts
- Einlesen der Projektordner
- Erkennung des Ordners `01_Architektur`
- Erkennung der Datei `ARC_Gebaeude.ifc` im richtigen Ordner
- ausschließlich lesender Zugriff mit `data:read`

Die späteren Module Modellkoordination, Kollisionen, Issues und Freigaben sind in der Oberfläche vorbereitet, aber in dieser Version noch nicht technisch angebunden.

## Dateien

```text
index.html                      eigentliche Tutorial-App
ARC_Gebaeude.ifc                kleine IFC-Testdatei
GITHUB-UPLOAD-ANLEITUNG.md      ausführliche Veröffentlichung
README.md                       diese Übersicht
```

## Veröffentlichung in Kurzform

1. Neues öffentliches oder privates GitHub-Repository anlegen.
2. Alle Dateien dieses Ordners in die oberste Ebene des Repositorys hochladen.
3. Unter **Settings → Pages** die Bereitstellung aus dem Branch `main` und dem Ordner `/root` aktivieren.
4. Die veröffentlichte Adresse aufrufen.
5. Die in der App angezeigte Callback-URL exakt in der APS-Anwendung hinterlegen.
6. Die APS Client-ID in Forma Hub Admin als Custom Integration freigeben.

Die vollständige Anleitung steht in `GITHUB-UPLOAD-ANLEITUNG.md`.

## Sicherheit

- Die Client-ID ist eine öffentliche Kennung und darf im Browser verwendet werden.
- Ein Client Secret wird weder benötigt noch gespeichert.
- Das Zugriffstoken wird nur im `sessionStorage` der jeweiligen Browser-Sitzung abgelegt.
- Der Prototyp verwendet nur `data:read` und verändert keine Forma-Daten.
- Für erste Tests sollte ein separates Übungsprojekt ohne vertrauliche Projektdaten verwendet werden.

