# Watchtower – Veröffentlichungen

Dieses Repository enthält **nur die Installer und die signierten Update-Beschreibungen** von Watchtower, einer lokalen Verwaltung für 3D-Druckerfarmen
(Klipper/Moonraker, Bambu Lab, OctoPrint, PrusaLink), ohne Cloud. Es gibt hier keinen Quellcode.

## Installation (Windows)

1. Unter [Releases](../../releases/latest) die Datei `Watchtower-Setup-<Version>-win-x64.exe` herunterladen.
2. Ausführen. Der Installer ist nicht code-signiert, Windows SmartScreen kann warnen („Weitere Informationen“ → „Trotzdem ausführen“).
3. Es sind keine Administratorrechte nötig, die Installation gilt nur für deinen Benutzer.

## Automatische Updates

Das installierte Programm prüft diese Adresse selbst (nach dem Start und alle 6 Stunden) und fragt, bevor es eine neue Version installiert:

```
https://github.com/jpdoering02-stack/watchtower-releases/releases/latest/download
```

Es werden nur zwei Dateien abgerufen: `watchtower-update.json` und der Installer. Die Beschreibung ist mit einem Ed25519-Schlüssel signiert, der Installer wird
gegen die darin stehende SHA-256-Prüfsumme geprüft; eine untergeschobene Datei wird vom Programm abgelehnt. Das Abschalten geht im Programm unter
*Programm-Updates* → „Automatisch nach Updates suchen“.

## Prüfsumme prüfen (optional)

`watchtower-update.json` enthält `sha256` und `size` des Installers:

```powershell
(Get-FileHash .\Watchtower-Setup-<Version>-win-x64.exe -Algorithm SHA256).Hash.ToLower()
```
