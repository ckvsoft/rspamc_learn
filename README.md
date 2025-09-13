# rspamc_learn

## Kurzbeschreibung / Short Description

Deutsch: Skript zum Training von rspamc, das die echten Empfänger pro Benutzer lernt, statt nur Delivered-To.

English: Script for training rspamc, learning real recipients per user instead of just Delivered-To.

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

