# Prüfprotokoll Konkurrenzanalyse

## Allgemeine Angaben

| Feld | Eintrag |
|---|---|
| Tool | Cryptomator |
| Version | 1.19.3 |
| Betriebssystem und Version | Windows 11 Education 25H2 |
| Hardware (CPU, RAM) | AMD Ryzen AI 9 HX 370, 32GB DDR5-5200 |
| Datum | 07.10.2026 |
| Prüfer | Oliver Decker |

## Abgrenzung

Cryptomator wird nicht vollständig bewertet, da es ein abweichendes Konzept verfolgt:

| Merkmal | Aegis und Hauptkandidaten | Cryptomator |
|---|---|---|
| Einheit der Verschlüsselung | Einzelne Datei | Tresor mit vielen Dateien |
| Bedienung | Datei auswählen, verschlüsseln | Tresor als virtuelles Laufwerk einbinden |
| Weitergabe an Dritte | Verschlüsselte Datei versenden | Tresor über Cloud teilen |
| Public-Key-Modus | Vorhanden oder geplant | Nicht vorhanden |
| Hauptanwendungsfall | Dateiaustausch | Schutz von Cloud-Speicher |

Nicht bewertet werden daher: U4, F1, F2, F4, P2, P3, W2, W3.

## Testaufgaben

| Nr. | Aufgabe |
|---|---|
| C1 | Neuen Tresor anlegen, D1 hineinkopieren, Tresor sperren |
| C2 | Tresor entsperren und D1 wieder herauskopieren |
| C3 | Tresor mit falschem Passwort entsperren |
| C4 | Eine verschlüsselte Datei im Tresorordner manipulieren, dann Tresor entsperren und Datei öffnen |
| C5 | D2 in den Tresor kopieren und wieder herauskopieren |

## Bewertung

Bewertungsskala wie im Hauptprotokoll, sofern unten nichts Abweichendes steht.

| Nr. | Kriterium | Gewicht | Prüfung | Beobachtung | Punkte (0–4) |
|---|---|---:|---|---|:---:|
| S1 | AEAD und Integritätsschutz | 6 | Verfahren für Dateiinhalt und Dateinamen laut Spezifikation, Ergebnis von C4 | | |
| S2 | Passwort-KDF | 6 | Verwendete KDF und Parameter für den Masterkey | | |
| S3 | Post-Quanten-Resistenz | 6 | Verfahren für Tresor und für Cryptomator Hub | | |
| S5 | Spezifikation und Audits | 6 | Öffentliche Spezifikation, Audits (wer, wann) | | |
| U1 | Zeit bis zur ersten Verschlüsselung | 8 | Zeit für C1 inklusive Tresoreinrichtung | | |
| U2 | Interaktionsschritte | 6 | Durchschnitt aus C1 und C2 | | |
| U3 | Fehlermeldungen | 7 | Nur C3 und C4, je vier Prüfpunkte, max. 8 (Skala: 8 = 4, 6–7 = 3, 4–5 = 2, 2–3 = 1, 0–1 = 0) | | |
| U5 | Schutz vor Fehlbedienung | 6 | U5.1, U5.2, U5.5 aus dem Hauptprotokoll, zusätzlich: Warnung beim Schließen mit geöffneten Dateien (max. 4; Skala: 4 = 4, 3 = 3, 2 = 2, 1 = 1, 0 = 0) | | |
| F3 | Große Dateien | 4 | C5 mit RAM-Messung | | |
| P1 | Betriebssystem-Abdeckung | 4 | Wie Hauptprotokoll | | |
| W1 | Aktive Entwicklung | 5 | Wie Hauptprotokoll | | |
| | **Summe bewerteter Gewichte** | **64** | | | |

## Ergebnis

| Wert | Ergebnis |
|---|---|
| Erreichte gewichtete Punkte (Σ Gewicht × Punkte / 4) | ___ von 64 |
| Normierter Teilnutzwert (erreichte Punkte / 64 × 100) | ___ |

Der normierte Teilnutzwert ist nicht direkt mit den Nutzwerten der Hauptkandidaten vergleichbar, da Schlüsselverwaltung, Empfängerfunktionen und Interoperabilität nicht bewertet wurden.

## Erkenntnisse für Aegis

| Nr. | Beobachtung | Übertragbar auf Aegis? | Begründung |
|---|---|---|---|
| 1 | | ja / nein | |
| 2 | | ja / nein | |
| 3 | | ja / nein | |

### Hinweis zur Verwendung von KI-Werkzeugen

| Eingesetztes KI-Werkzeug | Zweck / Art der Nutzung |
|---|---|
| Claude Opus 5.5 | Erste Erstellung der Kriterien für die Nutzwertanalyse, Bereitstellung des Prüfprotokolls als Markdown Code |
| Gemini 3.8 Flash | Unterstützung bei der Beantwortung einzelner Prüffragen und der Durchsuchung von Dokumentation |

### Ergänzende Quellen & Eigene Prüfleistungen (age)

| ID | Typ | Urheber / Projekt | Titel / Ressource | Stand / URL |
|---|---|---|---|---|
| | | | | |
