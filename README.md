# Aegis
User-friendly file encryption application with extensibility for end-to-end encrypted communication

# Projektplan

## Phase 1: Vorbereitung, Analyse & Anforderungsdefinition
* **Konkurrenzanalyse durchführen:**
  * Kleopatra, Picocrypt und age / rage vergleichen
  * Typische UX-Schwachstellen dokumentieren
* **Anforderungen ausarbeiten:**
  * Randbedingungen festlegen
  * Funktionale Anforderungen definieren
  * Nicht-funktionale Anforderungen festlegen
* **Technologie-Stack & Rollenverteilung:**
  * Krypto-Crates festlegen
  * Rollen aufteilen

## Phase 2: Spezifikation des Dateiformats & Bedrohungsmodell
* **Dateicontainer-Spezifikation (RFC-Style) schreiben:**
  * Header-Aufbau exakt definieren
  * Chunking-Modell festlegen
* **Threat Model & Security Goals aufstellen:**
  * Angreifermodell definieren
  * Sicherheitsgrenzen dokumentieren

## Phase 3: Entwicklung des Krypto-Backends
* **Schlüsselableitung & KEM implementieren:**
  * Modul für Argon2id (Passwort-Modus) mit festen, sicheren Parametern aufsetzen.
  * Modul für Hybrid-KEM (X25519 + ML-KEM-768 kombiniert via HKDF-SHA256) implementieren.
* **Streaming-Pipeline implementieren:**
  * Reader/Writer für dateibasiertes Chunk-Verschlüsseln und -Entschlüsseln schreiben.
  * `zeroize` auf allen Puffern und Schlüsseln im Speicher verankern.
* **Unit- & Integrationstests schreiben:**
  * Testvektoren für Korrektheit prüfen.
  * Negativtests ausarbeiten

## Phase 4: Entwicklung des Frontends
* Flutter, Tauri und Iced vergleichen und auswählen
* **Zustandsautomat (State Machine) definieren:**
  * Zustände modellieren
* **UI-Komponenten bauen:**
  * Drag-and-Drop-Dropzone implementieren.
  * Eingabemasken
  * Animierte `ProgressBar` für Dateifortschritt

## Phase 5: Testing, Benchmarks & Sicherheitsaudit
* **Performance-Benchmarks erstellen:**
  * Durchsatz messen (MB/s bzw. GB/min) im Vergleich zu VeraCrypt, Kleopatra und Picocrypt mit `criterion`
  * RAM-Verbrauch messen
* **Usability-Testing (Mini-Studie für die Arbeit):**
  * 3–5 Kommilitonen unvorbereitet eine Datei ver- und entschlüsseln lassen.
  * Zeit bis zum Abschluss und Klick-Anzahl messen; Feedback für das Fazit der Arbeit nutzen.
* **Code-Audit & Tooling:**
  * `cargo audit` (Sicherheitslücken in Crates prüfen).
  * `cargo clippy` & Formatierung.
  * Speicheranalyse zur Verifikation von `zeroize`.

## Phase 6: Schriftliche Ausarbeitung (DHBW-Studienarbeit)
* **Einleitung & Motivation:** Problemstellung schlechter Krypto-UIs („Why Johnny Can’t Encrypt“), Quantenbedrohung (*Harvest Now, Decrypt Later*).
* **Stand der Technik & Verwandte Arbeiten:** Detaillierte Konkurrenzanalyse.
* **Konzeption & Bedrohungsmodell:** Mathematische Grundlagen (FIPS 203, STREAM-Konstruktion, Argon2id) und Container-Spezifikation.
* **Implementierung:** Rust-Architektur, Concurrency-Modell in Iced, Memory-Safety-Garantien.
* **Evaluation:** Benchmarks, Usability-Testergebnisse, Sicherheitsanalyse.
* **Fazit & Ausblick:** Zusammenfassung und künftige Erweiterungen (z. B. Hardware-Tokens/YubiKey-Support).
