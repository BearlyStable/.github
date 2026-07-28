<div align="center">

# 🐻 BearlyStable

**Small, sharp tools for internal engagements, sysadmin work, and CTFs.**

Built to run with no fuss: standard-library-first, Kali-friendly, and honest in their docs about the trade-offs they make.

</div>

---

## What's here

| Repo | What it does | Stack |
|---|---|---|
| [**scanner**](https://github.com/BearlyStable/scanner) (`tcpsweep`) | Dependency-free, single-file TCP connect sweeper — an `nc -z`-style port sweep with CIDR/range targets, threading, rate limiting, and `nmap`-style output formats. | Python |
| [**smbex**](https://github.com/BearlyStable/smbex) | Ranger-style TUI file explorer for SMB, SSH/SFTP, and FTP/FTPS — built for slow, unreliable links, with listing caches, background downloads, and optional on-box filename translation. | Python |
| [**scribe**](https://github.com/BearlyStable/scribe) | Local-only shell wrapper that documents an interactive remote-shell session as you work it. | Python |
| [**Simple-ADExplorer**](https://github.com/BearlyStable/Simple-ADExplorer) | Lightweight viewer for Sysinternals ADExplorer snapshots and BOFHound output — browse Active Directory data without standing up the full stack. | Python |
| [**GPO-Explorer**](https://github.com/BearlyStable/GPO-Explorer) | Drop in a zip of Group Policy Objects and pull them apart fast — built with CTF-speed triage in mind. | Python |
| [**tiny_helpers**](https://github.com/BearlyStable/tiny_helpers) | Grab-bag of small tools and configs for a more pleasant shell life. | Shell |

## Philosophy

- **Standard library first.** Most tools install with zero or near-zero third-party dependencies, and several run straight from a single file if `pip`/`pipx` isn't an option.
- **Kali-aware.** Where it matters (`smbex`), install paths cover `apt`-only boxes explicitly, not just `pip`.
- **Documented trade-offs, not hidden ones.** Where a tool departs from "reference" protocol behavior (see `smbex`'s design notes on tree-connect churn, host-key trust, and FTP `ABOR` handling), that's written down rather than left for someone to discover the hard way.
- **Data hygiene.** Tools that write scan or session output do so to files scoped for the operator only (owner-readable, `.gitignore`'d by default).

## ⚠️ Authorized use only

Everything here is intended for environments you own, or have explicit written permission to test — internal infrastructure, lab environments, and CTF ranges. Scanning, browsing, or documenting sessions against systems you don't have authorization for is not what these tools are for.

## Getting started

Most repos are `pip`/`pipx`-installable:

```bash
pipx install tcpsweep
pipx install smbex
```

Each repo's own README has full install instructions (including `apt`-only paths for Kali where relevant), usage examples, and — where the tool touches a network protocol — notes on how it behaves compared to the reference client.

`Simple-ADExplorer` and `GPO-Explorer` are local web apps and also ship as container images, published via GitHub Actions on every tagged release:

```bash
docker pull ghcr.io/nm1ss/simple-adexplorer:latest
docker pull ghcr.io/bearlystable/gpo-explorer:latest
```

> Both images are intended for **local/internal use only** — the apps they run can hold sensitive AD data (credentials, security descriptors, GPO contents), so don't expose the container to an untrusted network. Pin to a version tag (e.g. `:1.0.0`) for anything beyond a quick look; each repo's README has the full `docker run` / `docker compose` setup, including persistent-volume and backup/restore instructions.

## License

Repos are individually licensed — mostly **MIT**, with a couple under **GPL-3.0**. Check each repo for specifics.

## A note on the code

A few of these repos note **Claude Sonnet** as an assistant in their development. Human-reviewed, human-shipped.

---

<div align="center">

*Questions, bugs, or ideas — open an issue on the relevant repo.*

</div>
