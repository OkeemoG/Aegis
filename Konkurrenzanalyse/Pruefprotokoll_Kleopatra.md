# Prüfprotokoll Konkurrenzanalyse

## Allgemeine Angaben

| Feld | Eintrag |
|---|---|
| Tool | |
| Version | |
| Betriebssystem und Version | |
| Hardware (CPU, RAM) | |
| Datum | |
| Prüfer | |

## Vorbereitung

| Nr. | Testdatei | Beschreibung | Vorhanden |
|---|---|---|:---:|
| D1 | `test_1gb.bin` | 1 GB Zufallsdaten | [ ] |
| D2 | `test_5gb.bin` | 5 GB Zufallsdaten | [ ] |
| D3 | `manipuliert_mitte` | Verschlüsselte D1, ein Byte in der Dateimitte verändert | [ ] |
| D4 | `manipuliert_header` | Verschlüsselte D1, ein Byte im Header verändert | [ ] |
| D5 | `abgeschnitten` | Verschlüsselte D1, letzte 1000 Byte entfernt | [ ] |

---

## Sicherheit

### S1 Moderne AEAD-Verschlüsselung und Integritätsschutz (Gewicht 6)

| Nr. | Prüffrage | Antwort |
|---|---|---|
| S1.1 | Welcher Verschlüsselungsalgorithmus wird verwendet? | |
| S1.2 | Ist die Verschlüsselung authentifiziert (AEAD oder Encrypt-then-MAC)? | ja / nein |
| S1.3 | Ist der Header authentifiziert? | ja / nein |
| S1.4 | Sind Chunks gegen Vertauschen und Löschen geschützt? | ja / nein |
| S1.5 | Wird ein Abschneiden der Datei erkannt (Test mit D5)? | ja / nein |
| S1.6 | Wird eine Manipulation erkannt (Test mit D3 und D4)? | ja / nein |

| Punkte | Bedingung |
|:---:|---|
| 4 | AEAD, Header authentifiziert, Chunk-Reihenfolge und Dateiende geschützt |
| 3 | AEAD und Header authentifiziert, Abschneiden wird nicht erkannt |
| 2 | Authentifizierung vorhanden, aber veraltete Konstruktion oder nur optional |
| 1 | Integrität nur über separate Signatur möglich |
| 0 | Kein Integritätsschutz |

**Punkte:** ___ **Begründung:**

### S2 Stärke der Passwort-KDF (Gewicht 6)

| Nr. | Prüffrage | Antwort |
|---|---|---|
| S2.1 | Welche KDF wird im Passwortmodus verwendet? | |
| S2.2 | Welche Parameter (Speicher, Iterationen, Parallelität)? | |
| S2.3 | Kann der Nutzer die Parameter abschwächen? | ja / nein |
| S2.4 | Gemessene Dauer der Schlüsselableitung (Sekunden) | |

| Punkte | Bedingung |
|:---:|---|
| 4 | Argon2id mit Parametern mindestens nach RFC 9106 (64 MiB, t = 3), nicht abschwächbar |
| 3 | Argon2id mit schwächeren Parametern oder scrypt mit starken Parametern |
| 2 | scrypt mit schwachen Parametern oder PBKDF2 mit hoher Iterationszahl |
| 1 | Iteriertes S2K oder PBKDF2 mit niedriger Iterationszahl |
| 0 | Kein Passwortmodus oder unsichere Ableitung |

**Punkte:** ___ **Begründung:**

### S3 Post-Quanten-Resistenz (Gewicht 6)

| Nr. | Prüffrage | Antwort |
|---|---|---|
| S3.1 | Wird ein Post-Quanten-Verfahren angeboten? | ja / nein |
| S3.2 | Welches Verfahren (z. B. ML-KEM-768, ML-KEM-1024)? | |
| S3.3 | Wird es hybrid mit einem klassischen Verfahren kombiniert? | ja / nein |
| S3.4 | Ist es standardmäßig aktiv? | ja / nein |
| S3.5 | Ist es in der stabilen Version verfügbar (nicht Beta oder Plugin)? | ja / nein |

| Punkte | Bedingung |
|:---:|---|
| 4 | Hybrides standardisiertes Verfahren, standardmäßig aktiv |
| 3 | Hybrides Verfahren verfügbar, muss manuell gewählt werden |
| 2 | Nur über Plugin oder Beta-Version |
| 1 | Angekündigt, aber nicht verfügbar |
| 0 | Nicht vorhanden |

**Punkte:** ___ **Begründung:**

### S4 Sichere Defaults (Gewicht 6)

| Nr. | Prüffrage | Antwort |
|---|---|---|
| S4.1 | Sind die Standardeinstellungen ohne Änderung sicher? | ja / nein |
| S4.2 | Kann der Nutzer veraltete oder unsichere Algorithmen auswählen? | ja / nein |
| S4.3 | Ist ein leeres Passwort möglich? | ja / nein |
| S4.4 | Wird bei schwachem Passwort gewarnt oder blockiert? | ja / nein |
| S4.5 | Wird unverschlüsselter Klartext unbeabsichtigt zurückgelassen? | ja / nein |

| Punkte | Bedingung |
|:---:|---|
| 4 | Keine unsicheren Optionen wählbar, schwache Passwörter werden abgefangen |
| 3 | Keine unsicheren Optionen, aber keine Passwortprüfung |
| 2 | Unsichere Optionen versteckt in Expertenmenüs wählbar |
| 1 | Unsichere Optionen gleichrangig neben sicheren wählbar |
| 0 | Unsichere Standardeinstellungen |

**Punkte:** ___ **Begründung:**

### S5 Öffentliche Spezifikation und Audits (Gewicht 6)

| Nr. | Prüffrage | Antwort |
|---|---|---|
| S5.1 | Gibt es eine öffentliche Spezifikation des Dateiformats? | ja / nein |
| S5.2 | Ist das Format standardisiert (RFC, C2SP o. Ä.)? | ja / nein |
| S5.3 | Gab es ein unabhängiges Sicherheitsaudit? Wer, wann? | |
| S5.4 | Wurden die Befunde behoben? | ja / nein |
| S5.5 | Gibt es öffentliche Testvektoren? | ja / nein |

| Punkte | Bedingung |
|:---:|---|
| 4 | Standardisierte Spezifikation, aktuelles Audit mit behobenen Befunden, Testvektoren |
| 3 | Öffentliche Spezifikation und Audit vorhanden |
| 2 | Nur Spezifikation oder nur Audit |
| 1 | Nur informelle Beschreibung |
| 0 | Weder Spezifikation noch Audit |

**Punkte:** ___ **Begründung:**

---

## Usability

### Testaufgaben

| Nr. | Aufgabe |
|---|---|
| T1 | D1 mit Passwort verschlüsseln und wieder entschlüsseln |
| T2 | D1 für eine andere Person per Public Key verschlüsseln (inkl. Schlüsselerzeugung und -austausch) |
| T3 | Verschlüsselte D1 mit falschem Passwort entschlüsseln |
| T4 | D3, D4 und D5 entschlüsseln |

### U1 Zeit bis zur ersten erfolgreichen Verschlüsselung (Gewicht 8)

| Nr. | Prüffrage | Antwort |
|---|---|---|
| U1.1 | Zeit vom Programmstart bis zur fertigen verschlüsselten Datei (T1) | ___ min |
| U1.2 | Wurde Dokumentation oder Websuche benötigt? Wie oft? | |
| U1.3 | Gab es Fehlversuche? Welche? | |

| Punkte | Bedingung |
|:---:|---|
| 4 | Unter 1 Minute, ohne Hilfe |
| 3 | 1 bis 3 Minuten, ohne Hilfe |
| 2 | 3 bis 5 Minuten oder einmal Dokumentation nötig |
| 1 | Über 5 Minuten oder mehrfach Dokumentation nötig |
| 0 | Aufgabe nicht gelöst |

**Punkte:** ___ **Begründung:**

### U2 Anzahl der Interaktionsschritte (Gewicht 6)

Gezählt werden Klicks, Tastatureingaben von
