# Oqe A-11 / A-12 independent audit bundle

This repository contains only the sanitised independent-audit bundle for Oqe
A-11 (bare `--host` policy) and A-12 (packaged server entry loads the loopback
preflight). The Oqe source repository is not published here.

- Artifact: `Oqe-A11-A12-Independent-Audit.zip`
- SHA-256: `2515bace1054db2ba15f6a685a3e9b0ef7bc47ae98a33199555cb272f932bfb3`
- Source commit audited: `4e744558fa48c19e95be9dd7c9d4b5ac719b0ebd` (`main`, private Oqe worktree)
- Prepared: 2026-10-27
- Status: **not independently audited** and **not a V11.1 release**. The
  source project's release remains unpromoted.

## Sanitisation

Local workspace and account path references were replaced with
`[REDACTED_LOCAL_WORKSPACE_PATH]` / `[REDACTED_LOCAL_USER_PATH]` in six files:

- `evidence/bare-host.log`
- `evidence/build.log`
- `evidence/npm-test.log`
- `evidence/provenance-failure.txt`
- `packaged-entry/app/server/_tanstack-start-manifest_v-WYhTG9pN.mjs`
- `records/CHECKPOINT-LOG.md`

65 path references were replaced in total. `MANIFEST-SHA256.txt` was
regenerated and the ZIP was rebuilt from the sanitised tree.

This repository was initialised with a fresh Git history. It does not contain
the earlier unsanitised bundle or inherit its history; that earlier artifact
and its repository remain private.

No credentials, companion tokens, API keys, private keys or `.env` files are
included. Generic documentation examples and RFC1918 test addresses remain
inside the audit evidence as technical material.

## Verify the download

```bash
sha256sum -c Oqe-A11-A12-Independent-Audit.sha256
unzip -t Oqe-A11-A12-Independent-Audit.zip
unzip Oqe-A11-A12-Independent-Audit.zip
cd Oqe-A11-A12-Independent-Audit
node reproduce/verify-manifest.mjs
node reproduce/apply-packaged-guard.mjs
```

`MANIFEST-SHA256.txt` inside the ZIP covers every bundle file except itself.
`AUDIT-EVIDENCE.md` records the commit, changed files, commands, exit codes,
test counts and the limits of the evidence, including that T3/T5 were not
verified and that no clean Windows install was performed.

## Download

https://raw.githubusercontent.com/Clayton119/Oqe-A11-A12-Independent-Audit-Public/main/Oqe-A11-A12-Independent-Audit.zip
