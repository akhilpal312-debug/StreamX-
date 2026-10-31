# Publish StreamX source on GitHub

## Before publishing
1. Review `LICENSE`, `UPSTREAM-README.md`, `STREAMX-ASSET-NOTICES.md`,
   and the notices in bundled plugin/provider files. Keep all notices.
2. Do not commit `.env` files containing real values, API keys, cookies,
   account data, signing keys, `local.properties`, or build output.
3. The included APK is in `release-artifacts/` for convenience. Prefer
   attaching it to a GitHub Release instead of committing it to the source
   history. The SHA-256 checksum is in that folder.
4. This source is a development candidate. Read `qa/R4-DEVICE-RETEST.md`
   and complete the physical-device acceptance tests before calling it a
   production release.

## Create and push your repository

Create an empty repository on GitHub, then run these commands from the
extracted `StreamX/` folder (replace the URL with your own repository URL):

```bash
git init
git branch -M main
git add .
git status --short
git diff --cached --stat
git commit -m "Prepare StreamX R4 source"
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
git push -u origin main
```

If you choose the recommended release workflow, remove
`release-artifacts/StreamX-R4.apk` from the Git commit and upload it to
GitHub Releases as a binary asset. Keep `release-artifacts/README.md` and
`SHA256SUMS.txt` if useful.

## Build notes
Follow the exact Android and server build instructions in `README.md`.
No GitHub repository was created, and no push or deployment was performed
by packaging this ZIP.
