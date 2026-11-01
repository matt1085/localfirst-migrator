# User pain research — LocalFirst Migrator

Research date: **31 October 2026**

Method: public web discussions and documentation about Bazzite / Flatpak / desktop migration.
No personal information was scraped. Demand statistics are **not** invented.

## Recurring vocabulary

| Theme | Phrases users actually use |
| --- | --- |
| New hardware | “PC change”, “new laptop”, “new hard drive”, “move my install”, “bring my whole desktop over” |
| Rebuild anxiety | “reinstall”, “don’t want to break Bazzite”, “snapshot”, “restore current state”, “pick up where I left off” |
| Flatpak lists | `flatpak list`, “reinstall Flatpaks”, “apps and settings”, `~/.var/app` |
| Home copy | “copy `/var/home`”, “rsync home”, “home directory”, “clonezilla / Rescuezilla” |
| Scope confusion | Flatpaks vs Brew vs AppImages vs KDE settings vs whole OS image |
| Immutable nuance | “immutable distro”, ostree rollback vs user-data backup |

---

## Pain 1 — New Bazzite PC, want files + apps + settings

**Problem:** Users getting a new laptop/PC ask whether they can bring “files, settings, pictures” and their application setup without starting from zero.

**Current manual workaround:** Fresh Bazzite install, then `rsync`/copy `/home/$USER` (or `/var/home/...`), then hope apps match; sometimes reinstall Flatpaks separately.

**User vocabulary:** “PC change”, “bring my whole desktop over”, “copy home directory”, “rsync”.

**How LocalFirst Migrator addresses it:** Scan → link Desktop/Laptop → review supported Flatpak differences → preview → apply supported Flatpak installs with rollback. Local-first; no cloud account.

**Where it does NOT address it:** Does not migrate KDE settings, Homebrew, Distrobox, secrets, or an entire Linux installation / home tree as a clone.

**Sources:**

- [If I do a PC Change — r/Bazzite](https://www.reddit.com/r/Bazzite/comments/1s95iib/if_i_do_a_pc_change/) (community post; comments discuss home-copy + rsync; observed Apr 2026 thread activity)
- [Directories for Backup — Universal Blue Discourse](https://universal-blue.discourse.group/t/directories-for-backup/3660) (home + `~/.var/app`; brew/containers caveats)

---

## Pain 2 — Back up / restore “apps and settings” on Bazzite

**Problem:** Newer users want a point-in-time restore of applications and settings, beyond ostree rollback.

**Current manual workaround:** `flatpak list --user --app` dump; back up `/home` (especially `.var/`, `.config/`); optional Clonezilla/disk image for full disk clones.

**User vocabulary:** “Bazzite backup”, “applications installed and settings maintained”, “snapshot”, “custom ISO”.

**How LocalFirst Migrator addresses it:** Focused path for **supported Flatpak migration** between two live Bazzite machines with preview and rollback — not a full backup product.

**Where it does NOT address it:** Not a Timeshift/Borg/Clonezilla replacement; not whole-home backup; not OS image creation.

**Sources:**

- [Bazzite backup — r/Bazzite](https://www.reddit.com/r/Bazzite/comments/1kif2zm/bazzite_backup/) (May 2025)
- [Restore Current Bazzite State to Re-installed Bazzite? — Universal Blue](https://universal-blue.discourse.group/t/restore-current-bazzite-state-to-re-installed-bazzite/11500) (home + Flatpak userdata + Brewfile discussion)

---

## Pain 3 — Move install to a new drive / SSD

**Problem:** Users outgrow a slow drive and want the whole Bazzite install moved.

**Current manual workaround:** Clonezilla / Rescuezilla / GParted clone; or fresh install + copy `/var/home`.

**User vocabulary:** “transfer Bazzite install”, “new hard drive”, “clone”, “btrfs cloning the home partition”.

**How LocalFirst Migrator addresses it:** Not a disk-clone tool. After a fresh install on new hardware, it can help recreate **supported Flatpak applications** from another machine without hand-reinstalling each app.

**Where it does NOT address it:** Drive cloning, bootloader, fstab, dual-boot, Windows erase.

**Sources:**

- [How to transfer Bazzite install to new hard drive? — r/Bazzite](https://www.reddit.com/r/Bazzite/comments/1ovql5r/how_to_transfer_bazzite_install_to_new_hard_drive/) (Nov 2025)
- [Move Bazzite install SSD → SSD — Discord via Answer Overflow](https://www.answeroverflow.com/m/1476516949864222791) (Feb 2026; advice: install fresh, copy `/var/home`)

---

## Pain 4 — Flatpak backup/restore is a multi-step shell ritual

**Problem:** Documented Flatpak migration is: export refs + remotes + overrides, copy `~/.var/app`, re-add remotes, loop `flatpak install`.

**Current manual workaround:** Guides such as It’s FOSS “Backup and Restore Your Flatpak Apps & Settings”.

**User vocabulary:** `flatpak list --app --columns=installation,ref`, remotes, overrides, `~/.var/app`.

**How LocalFirst Migrator addresses it:** GUI inventory, plan, dry-run, transactional Flatpak install path, verification, and rollback for supported cases — without requiring users to author shell loops.

**Where it does NOT address it:** Does not claim to migrate every Flatpak userdata edge case as a perfect clone; secrets never sync; non-Flatpak stacks out of v1 scope.

**Sources:**

- [Backup and Restore Your Flatpak Apps & Settings — It’s FOSS](https://itsfoss.com/back-up-restore-flatpak-apps/) (guide; undated in fetch summary; still current public guidance as of research date)
- [Alternative Installation Guide — Bazzite Docs](https://docs.bazzite.gg/General/Installation_Guide/alternate-install-guide/) (default Flatpaks via `ujust`; rebase vs reinstall context)

---

## Pain 5 — Scope confusion: Flatpak vs Brew vs AppImage vs “the whole state”

**Problem:** Users asking to restore “exact state” mix Flatpaks, Homebrew, AppImages, and desktop settings.

**Current manual workaround:** Back up `/var/home`; `brew bundle dump`; reinstall Flatpaks from manifests; re-do DE settings manually.

**User vocabulary:** “exact state”, Brewfile, AppImages, “flatpaks in `~/.var/app`”.

**How LocalFirst Migrator addresses it:** Explicit feature matrix — Flatpak migrate/rollback/manual sync **supported**; KDE / Homebrew / Distrobox **not yet**; secrets **never**.

**Where it does NOT address it:** Brew, Distrobox, KDE write migration, AppImage inventory as a product promise.

**Sources:**

- [Restore Current Bazzite State… — Universal Blue Discourse](https://universal-blue.discourse.group/t/restore-current-bazzite-state-to-re-installed-bazzite/11500)
- [Directories for Backup — Universal Blue Discourse](https://universal-blue.discourse.group/t/directories-for-backup/3660)

---

## Honest positioning takeaway

Community advice converges on **fresh install + home copy + reinstall apps**. That works for experts and fails for people who want a **reviewed, previewable Flatpak move** between two Bazzite PCs without inventing their own scripts.

LocalFirst Migrator sells that narrower job: **supported Flatpak migration with preview and rollback**, local-first, $29 once — not “clone my entire Bazzite life.”
