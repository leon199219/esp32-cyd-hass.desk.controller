# Security

## Never publish

- A `secrets.yaml` with a Wi-Fi password, API encryption key or OTA password
- A screenshot or log that shows those values, or the fallback access-point password

Other people copy [`secrets.yaml.example`](secrets.yaml.example) to `secrets.yaml` (next to the ESPHome configs, or in Home Assistant at `/config/esphome/secrets.yaml` or `/config/secrets.yaml`) and fill in their own values.

`secrets.yaml` is listed in [`.gitignore`](.gitignore). Before you push, check it is not in the commit.

## Fallback access point

The YAML sets `ap_password` to `changeme`. Change this before you flash. Anyone who can join the fallback network (`CYD-35 Fallback` or `CYD-28 Fallback`) can use the captive portal.

`ap_password` is a substitution in the YAML, not a secret in `secrets.yaml`. Do not leave the default in place on a device that is already on your network.

## API encryption and OTA

The API encryption key and the OTA password are passwords. Generate a new API key with `openssl rand -base64 32`. Do not share either value in issues or screenshots.

If you already have a device named `cyd-35` or `cyd-28`, keep the existing encryption key or Home Assistant will refuse the API connection.

## Wi-Fi

Wi-Fi credentials belong in `secrets.yaml` on your machine, not in this repo.
