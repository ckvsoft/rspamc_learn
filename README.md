# rspamc_learn

## Kurzbeschreibung / Short Description

Deutsch: Skript zum Training von rspamc, das die echten Empfänger pro Benutzer lernt, statt nur Delivered-To.

English: Script for training rspamc, learning real recipients per user instead of just Delivered-To.

Hinweis / Note:
Deutsch: Ich habe absichtlich die Endung .py weggelassen, da das Skript bei mir im cron.hourly ausgeführt wird.
English: The .py extension is intentionally omitted because the script is executed in cron.hourly on my system.

---

## Beschreibung / Description

Deutsch: Dieses Skript dient dazu, rspamc effizienter zu trainieren. Im Gegensatz zum Standardtraining, das sich nur an der Delivered-To-Adresse orientiert, lernt dieses Skript die tatsächlichen Empfänger pro Benutzer (per_user). Dies ermöglicht eine genauere Spam-Erkennung und verbessert die Anpassung an individuelle Postfächer.

Funktionen:
- Analysiert E-Mails und erkennt echte Empfänger pro Benutzer
- Trainiert rspamc basierend auf den echten Empfängern
- Vermeidet Fehlklassifikationen, die durch Delivered-To entstehen

English: This script is designed to train rspamc more accurately. Unlike the standard training, which only considers the Delivered-To address, this script learns the actual recipients per user (per_user). This allows for more precise spam detection and better adaptation to individual mailboxes.

Features:
- Analyzes emails and identifies real recipients per user
- Trains rspamc based on real recipients
- Avoids misclassifications caused by relying solely on Delivered-To

---

## Konfiguration / Configuration

Deutsch:
- **VERSION**: Versionsnummer des Skripts, z.B. "v0.2-20250901.3"
- **MAILROOT**: Basisverzeichnis für Mailkonten, z.B. "/vhome/vmail"
- **TIMESTAMP_FILE**: Datei, in der der letzte Trainingszeitpunkt gespeichert wird, z.B. "/var/lib/rspamd/learn_timestamp"
- **RSPAMD_LOG**: Pfad zur rspamd-Logdatei, z.B. "/var/log/rspamd/rspamd.log"
- **FACTOR**: Multiplikator für Lernfaktor, standardmäßig 6 (kann über Umgebungsvariable FACTOR angepasst werden)
- **DEBUG**: Debug-Modus, 0 = aus, 1 = an (kann über Umgebungsvariable DEBUG angepasst werden)
- **TEST**: Testmodus, True/False
- **ALIASES**: Dictionary zur Definition von Alias-Adressen. Der Schlüssel ist die Hauptadresse eines bestehenden Postfachs, die Werte sind Aliases oder Forwards an diese Hauptadresse. Wenn die Mail im rspamd ankommt, fehlt normalerweise Delivered-To, wodurch rspamd zu wenige Bayes-Daten zum Prüfen hat. Gleichzeitig wird beim Lernen normalerweise nur für den Hauptuser gelernt. Dieses Skript ermöglicht es, den Alias aus der Mail zu erkennen und auch für diesen Benutzer zu lernen. Es ist möglich, dass ein Hauptbenutzer keine zusätzlichen Aliase hat; das Lernen für den Hauptbenutzer funktioniert trotzdem.
  - Beispiel:
    - "chris@ckvsoft.at" lernt auch für info@ckvsoft.at, press@ckvsoft.at, root@ckvsoft.at und office@kvasny.at
    - "office@schmidlmoto.at" hat keine zusätzlichen Aliase, was möglich, aber nicht erforderlich ist.
- **EXCLUDE_DIRS**: Verzeichnisse, die beim Training ausgeschlossen werden, z.B. {'sieve', 'pgp'}

English:
- **VERSION**: Script version, e.g., "v0.2-20250901.3"
- **MAILROOT**: Base directory for mail accounts, e.g., "/vhome/vmail"
- **TIMESTAMP_FILE**: File storing the last training timestamp, e.g., "/var/lib/rspamd/learn_timestamp"
- **RSPAMD_LOG**: Path to rspamd log file, e.g., "/var/log/rspamd/rspamd.log"
- **FACTOR**: Multiplier for learning factor, default 6 (can be set via environment variable FACTOR)
- **DEBUG**: Debug mode, 0 = off, 1 = on (can be set via environment variable DEBUG)
- **TEST**: Test mode, True/False
- **ALIASES**: Dictionary defining alias addresses. Key is the main address of an existing mailbox, values are aliases or forwards to the main address. When mail arrives in rspamd, Delivered-To is usually missing, resulting in too few Bayes data to check. Normally rspamc only learns for the main user. This script allows reading the alias from the mail and training rspamc for it as well. It is possible for a main user to have no additional aliases; learning for the main user works regardless.
  - Example:
    - "chris@ckvsoft.at" also learns for info@ckvsoft.at, press@ckvsoft.at, root@ckvsoft.at, and office@kvasny.at
    - "office@schmidlmoto.at" has no additional aliases, which is possible but not required.
- **EXCLUDE_DIRS**: Directories excluded from training, e.g., {'sieve', 'pgp'}

---

## Usage / Verwendung

Deutsch: ./rspamc_learn <mailfile>

English: ./rspamc_learn <mailfile>

---

## Installation

Deutsch:
- Stelle sicher, dass rspamc installiert ist
- Lade das Skript herunter und mache es ausführbar: chmod +x rspamc_learn

English:
- Make sure rspamc is installed
- Download the script and make it executable: chmod +x rspamc_learn

