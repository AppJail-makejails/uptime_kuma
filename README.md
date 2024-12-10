# Uptime Kuma

Uptime Kuma is an easy-to-use self-hosted monitoring tool.

uptime.kuma.pet

<img src="https://uptime.kuma.pet/img/icon.svg" alt="uptime-kuma logo" width="30%" height="auto">

## How to use this Makejail

```sh
mkdir -p .volumes/data
appjail makejail \
    -j uptime_kuma \
    -f gh+AppJail-makejails/uptime_kuma \
    -o virtualnet=":<random> default" \
    -o nat \
    -o expose=3001 \
    -o fstab="$PWD/.volumes/data uptimekuma-data <volumefs>"
appjail start uptime_kuma
```

### Arguments (stage: build):

* `uptime_kuma_tag` (default: `13.4`): see [#tags](#tags).

### Check current status

The custom stage `uptime_kuma_status` can be used to run `top(1)` to check the status of Uptime Kuma.

```sh
appjail run -s uptime_kuma_status uptime_kuma
```

### Log

To view the log generated by the web application, run the custom stage `uptime_kuma_log`.

```sh
appjail run -s uptime_kuma_log uptime_kuma
```

### Volumes

| Name              | Owner | Group | Perm | Type | Mountpoint      |
| ----------------- | ----- | ----- | ---- | ---- | --------------- |
| uptimekuma-data   | 1001  | 1001  |  -   |  -   | /app/src/data   |
| uptimekuma-server | 1001  | 1001  |  -   |  -   | /app/src/server |
| uptimekuma-db     | 1001  | 1001  |  -   |  -   | /app/src/db     |

## Tags

| Tag    | Arch    | Version        | Type   |
| ------ | ------- | -------------- | ------ |
| `13.4` | `amd64` | `13.4-RELEASE` | `thin` |
| `14.2` | `amd64` | `14.2-RELEASE` | `thin` |
