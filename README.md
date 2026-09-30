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
| `ota`, `api` | OTA und verschlüsselte HA-API |
| `wifi` | WLAN, kein Powersave, 17 dB, Fallback-AP, `reboot_timeout: 0s` |
| `web_server` | v3, lokal, Port 80 |
| `logger` | Level DEBUG |
| `debug` | Reset Reason, Heap Free, Heap Max Block, Loop Time (300 s) |
| `sensor` | WiFi Signal (60 s) |
| `time` | Zeit von Home Assistant |
| `button` | Restart |

## Secrets
Benötigt `wifi_ssid`, `wifi_password`, `fallback_password`, `api_encryption_key` (siehe `secrets.yaml.example`).

## Geräte
- [mpu6050](https://github.com/CzarofAK/mpu6050) – WOMO-Nivelliersensor
- [smartebl](https://github.com/CzarofAK/smartebl) – Smart EBL
