# Backup-Skript

Ein kleines Python-Skript, das einen Ordner als ZIP-Datei sichert. Jedes Backup bekommt Datum und Uhrzeit in den Namen, und alte Backups werden automatisch gelöscht, damit der Speicher nicht vollläuft.

## Funktionen

- Packt einen beliebigen Ordner als ZIP-Datei
- Zeitstempel im Dateinamen (z. B. `Dokumente_2026-11-19_17-42-55.zip`), dadurch ist jedes Backup eindeutig und sortierbar
- Behält nur die neuesten Backups (Standard: 5) und löscht ältere
- Prüft die Eingaben, bevor etwas passiert:
  - Existiert der Quellordner?
  - Liegt der Zielordner nicht im Quellordner? (sonst würde sich das Backup selbst mitsichern)

## Voraussetzungen

- Python 3.9 oder neuer
- Keine zusätzlichen Pakete nötig, nur die Standardbibliothek

## Verwendung

```bash
python backup.py QUELLORDNER ZIELORDNER
```

Anzahl der aufbewahrten Backups selbst festlegen:

```bash
python backup.py QUELLORDNER ZIELORDNER --behalten 3
```

### Beispiel

```bash
python backup.py ~/Dokumente ~/Backups --behalten 3
```

Ausgabe:

```
Backup erstellt: Dokumente_2026-11-19_17-42-56.zip (12.34 MB)
Altes Backup gelöscht: Dokumente_2026-11-16_09-10-00.zip
```

## Was ich dabei gelernt habe

- Mit Dateien und Ordnern in Python arbeiten (`pathlib`, `shutil`)
- Kommandozeilen-Argumente mit `argparse` verarbeiten
- Eingaben prüfen und verständliche Fehlermeldungen ausgeben
- Wie man Dateinamen so gestaltet, dass alphabetische Sortierung gleich zeitliche Sortierung ist
