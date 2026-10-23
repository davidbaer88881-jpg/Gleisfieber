# Update-Dateien

Ab Version 0.8.0 schaut Gleisfieber beim Start hier nach (`version.json`).
Ist dort eine neuere Version eingetragen, lädt das Spiel das passende
Paket (`.pck`) im Hintergrund herunter und benutzt es nach dem nächsten Start.
Erstellt werden die Dateien mit `tools/make_update.sh <version> "<Notiz>"`.
