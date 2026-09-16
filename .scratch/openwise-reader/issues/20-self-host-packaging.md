# 20: Self-Host Packaging (Docker Compose, Backup, Restore)

**What to build:** `docker compose up -d` brings up the whole product (server, Postgres, object-storage adapter). Backup and restore commands cover database, uploaded files, content snapshots, annotations, and configuration. Documentation covers ports, volumes, SMTP, AI providers, backup, restore, and upgrade.

**Blocked by:** 18, 19

**Status:** ready-for-agent

- [ ] `docker compose up -d` brings up a working self-hosted instance
- [ ] SMTP configuration documented and tested (env-driven)
- [ ] AI provider configuration documented and tested (env-driven)
- [ ] Backup command produces a complete bundle (DB, files, snapshots, config, excluding secrets by default)
- [ ] Restore command rebuilds from a bundle with no data loss
- [ ] Upgrade path documented (in-place migration, with a "previous-version" rollback plan)
- [ ] Self-host docs cover ports, volumes, network, security hardening, single-user mode
- [ ] Health and readiness endpoints are exposed
- [ ] One-command backup, one-command restore, one-command upgrade
