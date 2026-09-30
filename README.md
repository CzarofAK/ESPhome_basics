# ESPhome_basics

Gemeinsames Package für alle eigenen ESPHome-Geräte (`.basics.yaml`).

## Einbindung
Datei nach `/config/esphome/.basics.yaml` legen, im Gerät:

```yaml
substitutions:
  name: mein-geraet

packages:
  basics: !include .basics.yaml
```

`${name}` wird für den Fallback-AP verwendet.

## Inhalt
| Block | Zweck |
|---|---|
| `ota`, `api` | Verschlüsselte HA-API; OTA mit leerem `encryption:` = verschlüsselt und Pflicht, nutzt den API-Key (ab ESPHome 2026.9) |
| `wifi` | WLAN, kein Powersave, 17 dB, Fallback-AP, `reboot_timeout: 0s` |
| `web_server` | v3, lokal, Port 80 |
| `logger` | Level DEBUG |
| `debug` | Reset Reason, Heap Free, Heap Max Block, Loop Time (300 s) |
| `sensor` | WiFi Signal (60 s) |
| `time` | Zeit von Home Assistant |
| `button` | Restart |

## Voraussetzung
ESPHome **2026.9 oder neuer** (wegen `ota: encryption:`). Ältere Versionen melden
`[encryption] is an invalid option for [ota.esphome]`.

## Secrets
Benötigt `wifi_ssid`, `wifi_password`, `fallback_password`, `api_encryption_key` (siehe `secrets.yaml.example`).

## Geräte
- [mpu6050](https://github.com/CzarofAK/mpu6050) – WOMO-Nivelliersensor
- [smartebl](https://github.com/CzarofAK/smartebl) – Smart EBL
