# pmgHealth Roadmap

Proxmox Mail Gateway health plugin. Feature parity with monokit1 `pmgHealth/`.

## Scaffolding

- [X] Plugin skeleton from pluginTemplate (go.mod, justfile, Containerfile, test harness)
- [X] Shared example config `config/mail.yml` (pmg section)
- [ ] Config struct + `mail.yml` case wired into monokit_lib
- [ ] Podman integration tests

## Features

- [ ] PMG systemd services check (per-service alarms)
- [ ] PostgreSQL status check
- [ ] Queued messages check (`mailq` count vs queue-limit)
- [ ] Mail-volume anomaly detection (email-monitoring)
  - [ ] 24h sent+received vs previous period × daily threshold factor (alarm + Redmine issue)
  - [ ] Hourly stats vs hourly threshold factor
- [ ] Daily `pmgcm sync` run/verify
- [ ] IP blacklist monitoring (blacklist-check)
  - [ ] External IP auto-detection (or configured IP)
  - [ ] MXToolbox scrape (temp auth key + JSON API, HTML fallback parser, regex fallback)
  - [ ] Ignore list
  - [ ] Result caching in DB with check throttling
  - [ ] blacklist / blacklist-not-ignored alarms
- [ ] PMG version reporting (`pmgversion`; monokit2: osHealth vlib `proxmox.go`)
