# GitHub-Pages-Veröffentlichung – Schritt für Schritt

## 1. Repository erstellen

1. Bei `https://github.com` anmelden.
2. Oben rechts auf das Pluszeichen klicken.
3. **New repository** auswählen.
4. Als Namen beispielsweise `forma-cde-tutorial` eintragen.
5. Für einen einfachen Test **Public** auswählen. GitHub Pages für private Repositorys hängt vom verwendeten GitHub-Tarif ab.
6. Keine zusätzliche README, `.gitignore` oder Lizenz erzeugen lassen, da die benötigten Dateien bereits im Paket liegen.
7. **Create repository** anklicken.

## 2. Dateien hochladen

1. Im leeren Repository **uploading an existing file** auswählen oder **Add file → Upload files** öffnen.
2. Diese vier Dateien aus dem entpackten Paket in den Uploadbereich ziehen:

   - `index.html`
   - `ARC_Gebaeude.ifc`
   - `README.md`
   - `GITHUB-UPLOAD-ANLEITUNG.md`

3. Unter **Commit changes** beispielsweise `Erster CDE-Tutorial-Prototyp` eintragen.
4. **Commit changes** bestätigen.

Wichtig: Die Dateien müssen direkt in der obersten Ebene des Repositorys liegen. `index.html` darf nicht noch in einem zusätzlichen Unterordner liegen.

## 3. GitHub Pages aktivieren

1. Im Repository **Settings** öffnen.
2. Links unter **Code and automation** den Punkt **Pages** auswählen.
3. Unter **Build and deployment** bei **Source** die Option **Deploy from a branch** wählen.
4. Als Branch `main` auswählen.
5. Als Ordner `/ (root)` auswählen.
6. **Save** anklicken.

Die Veröffentlichung kann einige Minuten dauern. Danach zeigt GitHub unter **Settings → Pages** die Adresse an. Sie sieht typischerweise so aus:

```text
https://BENUTZERNAME.github.io/forma-cde-tutorial/
```

Die Tutorial-App verwendet als feste Callback-Adresse:

```text
https://BENUTZERNAME.github.io/forma-cde-tutorial/index.html
```

## 4. Callback-URL ablesen

1. Die veröffentlichte GitHub-Pages-Adresse öffnen.
2. Im Feld **Callback-URL** wird die exakte Adresse angezeigt.
3. Diese Adresse vollständig kopieren.

Verwende die angezeigte Adresse und tippe sie möglichst nicht von Hand ab. Groß-/Kleinschreibung, Repositoryname, `https` und `/index.html` müssen exakt stimmen.

## 5. APS-Anwendung erstellen oder anpassen

1. `https://aps.autodesk.com/` öffnen und anmelden.
2. Den richtigen APS Developer Hub öffnen.
3. Unter **Applications** eine Anwendung erstellen oder die vorhandene Anwendung bearbeiten.
4. Als Typ **Desktop, Mobile, Single-Page App** verwenden.
5. Mindestens die **Data Management API** aktivieren.
6. Die zuvor kopierte GitHub-Pages-Adresse als Callback-URL eintragen.
7. Änderungen speichern.
8. Die APS Client-ID kopieren.

Ein Client Secret wird für diesen PKCE-Prototyp nicht benötigt und darf nicht in `index.html` eingetragen werden.

## 6. Anwendung im Forma-Hub freigeben

Dieser Schritt muss von einem Forma-Hub-Administrator durchgeführt werden:

1. Den gewünschten Forma-Hub öffnen.
2. **Hub Admin** öffnen.
3. Zu **Apps / Custom Integrations** wechseln.
4. **Add custom integration** auswählen.
5. Die APS Client-ID eintragen.
6. Als Namen beispielsweise `DHBW CDE Lernpfad` verwenden.
7. Zugriff auf **Forma Data Management** erlauben.
8. Integration speichern.

Der APS Developer Hub und der Forma-Hub sind zwei unterschiedliche Bereiche: Im APS Developer Hub wird die Anwendung verwaltet; im Forma-Hub wird ihr Zugriff auf die Projektdaten freigegeben.

## 7. Funktionstest

1. GitHub-Pages-Adresse öffnen.
2. APS Client-ID in das vorgesehene Feld einfügen.
3. **Mit Autodesk anmelden** anklicken.
4. Autodesk-Zugriff bestätigen.
5. Forma-Hub und Übungsprojekt auswählen.
6. Im Projekt einen Ordner mit dem exakten Namen `01_Architektur` verwenden.
7. Die beiliegende Datei `ARC_Gebaeude.ifc` manuell in diesen Ordner hochladen.
8. In der Tutorial-App die Schritte **Ordner finden** und **Datei prüfen** ausführen.

## Fehlerbehebung

| Problem | Wahrscheinliche Ursache | Lösung |
|---|---|---|
| `Invalid redirect URI` | Callback-Adresse stimmt nicht exakt | URL aus dem Feld der veröffentlichten App kopieren und in APS ersetzen |
| Kein Hub sichtbar | Client-ID nicht freigegeben | Custom Integration im richtigen Forma-Hub hinzufügen |
| Hub sichtbar, Projekt fehlt | Benutzer besitzt keinen Dateizugriff | Projektmitgliedschaft und Data-Management-Berechtigung kontrollieren |
| Datei wird nicht erkannt | falscher Name oder Ablageort | `ARC_Gebaeude.ifc` direkt in `01_Architektur` ablegen |
| GitHub-Seite zeigt 404 | Pages noch nicht fertig oder falscher Branch | Bereitstellung abwarten und Branch `main`, Ordner `/root` prüfen |
| APS-Anwendung ungültig | Anwendung keinem aktiven Developer Hub zugeordnet | Anwendung in den APS Developer Hub verschieben |

## Aktualisierungen veröffentlichen

Für spätere Versionen genügt es, die geänderte `index.html` im Repository zu ersetzen und den Commit zu bestätigen. Die GitHub-Pages-Adresse und die APS Callback-URL bleiben gleich, solange Benutzername und Repositoryname nicht geändert werden.

