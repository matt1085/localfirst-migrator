# 60–90 second demo plan

Target length: **~90 seconds**. Record on a sanitized demo pair labeled **Desktop** / **Laptop**.

## Beat sheet

| Time | Beat | On screen |
| --- | --- | --- |
| 0–8s | Problem | “New Bazzite PC — I do not want to reinstall every Flatpak by hand.” |
| 8–20s | Scan / link | Open app → scan Desktop → Link computers → Laptop trusted |
| 20–35s | Detected Flatpaks | Inventory / review list with clear statuses |
| 35–50s | Preview | Dry-run → banner **NO CHANGES WERE MADE** |
| 50–62s | Apply | Supported Flatpak migrate phases → Completed |
| 62–72s | Verify | App present / success summary |
| 72–80s | Rollback / manual sync glimpse | History rollback affordance **or** Manual sync conflict choice |
| 80–90s | Offer | “$29 one-time · matt1085.github.io/localfirst-migrator” |

## Spoken script (approx.)

“When I move between Bazzite machines I usually dump `flatpak list` and reinstall by hand. LocalFirst Migrator scans this PC, links Laptop, shows what would install, runs a preview with zero changes, then applies a supported Flatpak migration. Rollback stays available while the transaction is valid. Manual sync is opt-in — never automatic. I’m the developer. It’s $29 once. Limits are honest: no KDE, Homebrew, or Distrobox writes in v1, and secrets never sync.”

## Capture capability on this operator machine (31 Oct 2026)

| Asset | Feasible? | Notes |
| --- | --- | --- |
| Static screenshots | **Yes** | Sanitized illustrative UI shipped under `assets/screenshots/` (Desktop/Laptop labels). Live GUI capture is possible (`linux-migrator` installed; Wayland/X11 available) but risks leaking hostname/paths — prefer demo profiles. |
| Animated GIF / WebM | **Yes with care** | `ffmpeg` is installed. Record only after demo hosts/labels are sanitized. |
| Full screen capture | **Yes with care** | Use a clean demo user or redact in post. Do not show real usernames, LAN/VPN hostnames or IPs, SSH fingerprints, emails, or tokens. |

## Recording checklist

- [ ] Hostnames: Desktop / Laptop only
- [ ] Fake/demo Flatpak set (or redact personal app lists if needed)
- [ ] No payment UI, session IDs, or private repo names
- [ ] Non-affiliation line in description, not necessarily spoken
- [ ] End card: URL + $29 once

## Existing still assets

- `assets/screenshots/01-scan-inventory.jpg` … `07-manual-sync-conflict.jpg`
- `assets/og-card.jpg` (1200×630)
- `assets/screenshots/hero-montage.jpg`

Live video was **not** auto-recorded in this pass (privacy gate). Operator can record when a safe demo state is ready.
