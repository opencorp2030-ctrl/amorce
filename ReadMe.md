# Amorce — open firmware for Flipper Zero / Firmware libre pour Flipper Zero

🇬🇧 [English](#english) · 🇫🇷 [Français](#français)

---

## English

**Amorce** is a free, developer-oriented firmware for the Flipper Zero, built on [RogueMaster](https://github.com/RogueMaster/flipperzero-firmware-wPlugins), which itself builds on
[Unleashed](https://github.com/DarkFlippers/unleashed-firmware) and the official
[flipperzero-firmware](https://github.com/flipperdevices/flipperzero-firmware) (all GPLv3).
Part of the [Cartouche](https://github.com/opencorp2030-ctrl) ecosystem. No account, no telemetry.

### Status
Work in progress. Done: RogueMaster base, animated Amorce star logo among the desktop animations (slow spin, stop, repeat). Next: boot splash, Amorce Center, custom menu/icons, dev apps, TPE Test.

### Goals
- Maximum freedom: GPLv3 core, MIT/Apache app SDK, no signed-app requirement, no telemetry.
- Developer tooling first: payment-terminal testing, protocol analyzers, embedded debugging.
- Ideas borrowed from other OSes: Unix shell + `/proc`, Android-style app permissions,
  apt-style package manager, NixOS-style declarative config.
- Bilingual (EN/FR) UI and docs.

### Apps (planned)
| Area | Apps |
|---|---|
| Payment / NFC (test) | **TPE Test** (simulated terminal, never charges), APDU console, TLV/EMV decoder, response-latency tester |
| Embedded | Logic analyzer, UART/SPI/I²C/1-Wire terminal, I²C scanner, SWD programmer, CAN bridge, scope, signal generator |
| Network | HTTP/MQTT client, ping, DNS, file server, SSH (Wi-Fi module) |
| Tools | Text/hex editor, JSON viewer, hash/CRC/base64/UUID, TOTP, local encrypted password manager, QR generator |
| System | Package manager (`flip install`), OTA via BLE, scripting (Lua/MicroPython), `config.toml` |

### TPE Test — scope and limits
Acts as a **test** contactless terminal to check that *your own* payment solution
(e.g. Apple Pay integration) answers correctly: PPSE/AID selection, GPO, record reads,
TLV display, **simulated** approved/declined result.
- It never contacts an acquirer, never sends an authorization, never debits anything.
- It never stores PANs or tokens.
- It does **not** clone or emulate real bank cards. Use it only on devices you own.
- It is not a certified reader: it cannot validate a real transaction cryptogram.

### Build
```bash
git clone --recursive https://github.com/opencorp2030-ctrl/amorce
cd amorce
./fbt            # build firmware
./fbt fap_dist   # build external apps
```
Flashing can brick a badly built image; DFU mode always lets you return to official firmware.

### License
GPLv3 (inherited from upstream). See `LICENSE`.

---

## Français

**Amorce** est un firmware libre pour Flipper Zero, orienté développeurs, basé sur [RogueMaster](https://github.com/RogueMaster/flipperzero-firmware-wPlugins), lui-même basé sur
[Unleashed](https://github.com/DarkFlippers/unleashed-firmware) et le
[firmware officiel](https://github.com/flipperdevices/flipperzero-firmware) (tous GPLv3).
Il fait partie de l'écosystème [Cartouche](https://github.com/opencorp2030-ctrl). Sans compte, sans télémétrie.

### État
En cours. Fait : base RogueMaster, logo Amorce animé (étoile qui tourne doucement, s'arrête, recommence) dans les fonds d'écran. Prochain : écran de démarrage, Amorce Center, menu et icônes sur mesure, apps dev, TPE Test.

### Objectifs
- Liberté maximale : noyau GPLv3, SDK d'apps MIT/Apache, aucune signature d'app obligatoire, aucune télémétrie.
- Outils de développement d'abord : test de terminaux de paiement, analyseurs de protocoles, debug embarqué.
- Idées d'autres OS : shell Unix + `/proc`, permissions d'apps façon Android,
  gestionnaire de paquets façon apt, configuration déclarative façon NixOS.
- Interface et documentation bilingues (FR/EN).

### Apps (prévues)
| Domaine | Apps |
|---|---|
| Paiement / NFC (test) | **TPE Test** (terminal simulé, ne débite jamais), console APDU, décodeur TLV/EMV, testeur de latence |
| Embarqué | Analyseur logique, terminal UART/SPI/I²C/1-Wire, scanner I²C, programmeur SWD, pont CAN, oscilloscope, générateur de signaux |
| Réseau | Client HTTP/MQTT, ping, DNS, serveur de fichiers, SSH (module Wi-Fi) |
| Outils | Éditeur texte/hex, visionneuse JSON, hash/CRC/base64/UUID, TOTP, gestionnaire de mots de passe chiffré local, générateur QR |
| Système | Gestionnaire de paquets (`flip install`), OTA par BLE, scripts (Lua/MicroPython), `config.toml` |

### TPE Test — périmètre et limites
Joue le rôle d'un terminal sans contact **de test** pour vérifier que *ta propre* solution de paiement
(par ex. une intégration Apple Pay) répond correctement : sélection PPSE/AID, GPO, lecture des
enregistrements, affichage TLV, résultat approuvé/refusé **simulé**.
- Il ne contacte jamais d'acquéreur, n'envoie aucune autorisation, ne débite rien.
- Il ne stocke aucun PAN ni token.
- Il ne **clone pas** et n'émule pas de vraies cartes bancaires. À utiliser uniquement sur tes propres appareils.
- Ce n'est pas un lecteur certifié : il ne peut pas valider le cryptogramme d'une vraie transaction.

### Compiler
```bash
git clone --recursive https://github.com/opencorp2030-ctrl/amorce
cd amorce
./fbt            # compile le firmware
./fbt fap_dist   # compile les apps externes
```
Un flash raté peut bloquer l'appareil ; le mode DFU permet toujours de revenir au firmware officiel.

### Licence
GPLv3 (héritée de l'amont). Voir `LICENSE`.
