# Changelog

Tutte le modifiche rilevanti a questo modulo sono documentate in questo file.

Il formato è basato su [Keep a Changelog](https://keepachangelog.com/it/1.0.0/)
e il progetto aderisce al [Versionamento Semantico](https://semver.org/lang/it/).

## [1.1.0] - 2026-06-19

### Added
- Il consenso privacy viene ora salvato nella colonna `privacy` di `newsletter_subscriber` al momento dell'iscrizione.
- Schema dichiarativo (`etc/db_schema.xml` + `etc/db_schema_whitelist.json`) per la gestione della colonna `privacy`.
- ViewModel `PrivacyConfig` per esporre la configurazione privacy al template.

### Changed
- Migrazione da `Setup/InstallSchema.php` (deprecato) allo schema dichiarativo.
- Template footer: sostituito `$this->helper()` (deprecato) con il ViewModel `PrivacyConfig`.
- Costruttore del controller `NewAction`: parametri resi esplicitamente nullable (deprecazione PHP 8.4).
- Rimosso l'attributo deprecato `setup_version` da `module.xml`.

### Fixed
- Allineato il namespace a `Threecommerce` in tutto il modulo (il mismatch PSR-4 nel `composer.json` impediva l'autoload di Helper e Controller).
- `etc/module.xml`: corretto il tag `<sequenze>` in `<sequence>` (dipendenza di load-order da `Magento_Newsletter` ora applicata).
- `etc/config.xml`: corretti i path dei valori di default su `newsletter_privacy/general/active` e `newsletter_privacy/general/text_privacy` (il testo privacy di default ora viene applicato).
- Rimossa la dipendenza fissa e inutilizzata da `Smartwave\Porto\Helper\Data` nel template (causa di fatal error in assenza del tema Porto).
- L'iscrizione alla newsletter non fallisce più silenziosamente quando la privacy è disattivata; con privacy attiva e consenso mancante viene mostrato un messaggio di errore esplicito.

## [1.0.1]

- Versione iniziale tracciata.