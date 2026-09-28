## Bewertungsmatrix: Konkurrenzanalyse

Bewertungsskala: 0 = nicht erfüllt, 1 = kaum erfüllt, 2 = teilweise erfüllt, 3 = weitgehend erfüllt, 4 = vollständig erfüllt

Nutzwert = Σ (Gewicht × Punkte) / 4

| Kategorie | Nr. | Kriterium | Gewicht | Messmethode | Kleopatra | Picocrypt | age / rage |
|---|---|---|---:|---|:---:|:---:|:---:|
| **Sicherheit** | S1 | Moderne AEAD-Verschlüsselung und Integritätsschutz (Header und Chunks) | 6 | Doku/Spezifikation | | | |
| | S2 | Stärke der Passwort-KDF (Argon2id > scrypt > iteriertes S2K) | 6 | Doku/Quellcode | | | |
| | S3 | Post-Quanten-Resistenz (hybrid, standardisiert, standardmäßig aktiv) | 6 | Doku/Release Notes | | | |
| | S4 | Sichere Defaults, keine unsicheren Optionen wählbar | 6 | Eigener Test | | | |
| | S5 | Öffentliche Spezifikation und unabhängige Audits | 6 | Recherche | | | |
| **Usability** | U1 | Zeit bis zur ersten erfolgreichen Verschlüsselung (Laie) | 8 | Aufgabentest | | | |
| | U2 | Anzahl der Interaktionsschritte pro Standardaufgabe | 6 | Klicks/Befehle zählen | | | |
| | U3 | Verständlichkeit von Fehlermeldungen | 7 | Provozierte Fehler | | | |
| | U4 | Komplexität der Schlüsselverwaltung | 8 | Cognitive Walkthrough | | | |
| | U5 | Schutz vor Fehlbedienung (Passwortbestätigung, Stärkeanzeige, Überschreibschutz) | 6 | Eigener Test | | | |
| **Funktionsumfang** | F1 | Passwort- und Public-Key-Modus | 5 | Doku | | | |
| | F2 | Mehrere Empfänger pro Datei | 3 | Doku | | | |
| | F3 | Große Dateien/Streaming ohne hohen RAM-Verbrauch | 4 | Test mit >4 GB-Datei | | | |
| | F4 | Erweiterbarkeit (Plugins, Hardware-Token) | 3 | Doku | | | |
| **Plattform** | P1 | Betriebssystem-Abdeckung | 4 | Doku | | | |
| | P2 | Installation/Portabilität | 3 | Eigener Test | | | |
| | P3 | Interoperabilität, offenes Dateiformat | 3 | Spezifikation | | | |
| **Wartung** | W1 | Aktive Weiterentwicklung | 5 | Commits/Releases | | | |
| | W2 | Lizenz/Open Source | 2 | Repository | | | |
| | W3 | Dokumentation und Community | 3 | Recherche | | | |
| | | **Summe Gewichte** | **100** | | | | |
| | | **Nutzwert (0–100)** | | | | | |

### Teilergebnisse nach Kategorie

| Kategorie | Max. | Kleopatra | Picocrypt | age / rage |
|---|---:|:---:|:---:|:---:|
| Sicherheit | 30 | | | |
| Usability | 35 | | | |
| Funktionsumfang | 15 | | | |
| Plattform | 10 | | | |
| Wartung | 10 | | | |
| **Gesamt** | **100** | | | |

### Testszenarien für Usability-Kriterien

| Nr. | Aufgabe | Relevante Kriterien |
|---|---|---|
| T1 | 1-GB-Datei mit Passwort verschlüsseln | U1, U2, U5 |
| T2 | Datei für eine andere Person (Public Key) verschlüsseln | U2, U4 |
| T3 | Datei mit falschem Passwort entschlüsseln | U3 |
| T4 | Manipulierte Datei entschlüsseln | U3, S1 |
