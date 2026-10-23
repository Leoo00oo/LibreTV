# Updating Leo's local LibreTV from upstream

Fork: https://github.com/Leoo00oo/LibreTV  
Upstream: https://github.com/LibreSpark/LibreTV

## Remotes (already configured in this clone)

- `origin` → `https://github.com/Leoo00oo/LibreTV.git` (your fork; push here)
- `upstream` → `https://github.com/LibreSpark/LibreTV.git` (LibreSpark; fetch/merge only; push disabled)

## Pull upstream updates

```bash
cd /Volumes/RESOURCE/workspace/LibreTV
git fetch upstream
git merge upstream/main
# or: git rebase upstream/main
```

Then update the fork on GitHub:

```bash
git push origin main
```

## Local-only files (do not commit)

| File | Why |
|------|-----|
| `.env` | Contains `PASSWORD` and other secrets — already gitignored; local-only |
| `.env.bak*` / `.env.*` | Backups of `.env` — gitignored (`!.env.example` kept) |
| `start.sh` | Local launcher (nvm path, port 8077, password fallback) — gitignored |
| `libretv-sourcelist-*.json` | Local dumps — gitignored |
| `package.json` port `8077` | Uncommitted local edit vs upstream `8080`; keep dirty or re-apply after merge |

Never force-push over upstream. Never commit `.env` or any password.

## Auth note

If `git push origin` fails (SSH `publickey` / HTTPS no credentials), authenticate GitHub on this Mac, or push via Cursor CloudAgent / GitHub web UI.
