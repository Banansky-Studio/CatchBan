# CatchBan Release Workflow

This repo now automates GitHub Release page creation only.  
App build, DMG packaging, and the readme/PDF inside the DMG remain local (manual).

## 1) Local release build (manual)

1. Validate runtime architecture coverage before archive:

```bash
scripts/validate_release_architectures.sh
```

2. Run explicit dual-architecture compile checks (arm64 + x86_64):

```bash
scripts/verify_dual_arch_build.sh
```

This step now enforces architecture isolation automatically via:

```bash
scripts/enforce_runtime_arch_isolation.sh
```

3. Build and verify the new version in Xcode.

4. (Recommended) Validate the built `.app` again before DMG packaging:

```bash
scripts/validate_release_architectures.sh --bundle "/path/to/CatchBan.app"
```

5. Package your final `.dmg` locally (including your readme/PDF).

## 2) Prepare release metadata in repo

Create versioned release files before tagging:

- `.github/releases/<tag>.env`
- `.github/releases/<tag>.md`

Example for `v2.0.0-beta.1`:

```bash
cat .github/releases/v2.0.0-beta.1.env
cat .github/releases/v2.0.0-beta.1.md
```

The `.env` file controls release metadata:

```bash
RELEASE_NAME="CatchBan V2.0 Beta"
PRERELEASE="false"
MAKE_LATEST="true"
```

Supported keys:

- `RELEASE_NAME`: Human-facing release title.
- `PRERELEASE`: `true` or `false`.
- `MAKE_LATEST`: `true`, `false`, or `legacy`.

If `.github/releases/<tag>.md` exists, the workflow uses that bilingual Markdown as the release body.  
If it does not exist, the workflow falls back to GitHub-generated release notes.

## 3) Create Release page automatically

### Option A: Tag-driven (recommended)

```bash
git tag -a v2.0.0-beta.1 -m "CatchBan V2.0 Beta"
git push origin v2.0.0-beta.1
```

What automation does:

- Creates or updates `releases/tag/v2.0.0-beta.1`
- Uses `.github/releases/v2.0.0-beta.1.env` for release title and publish flags
- Uses `.github/releases/v2.0.0-beta.1.md` for the final release body
- Falls back to GitHub-generated notes if no versioned Markdown body exists
- Does not upload any assets

### Option B: Manual trigger (Actions UI)

Actions -> `Create Release Page` -> `Run workflow` -> input tag (for example `v2.0.0-beta.1`)

## 4) Upload DMG manually

After the release page exists, upload your local `.dmg` by either:

- GitHub web UI (Release page -> `Attach binaries`)
- CLI:

```bash
gh release upload v2.0.0-beta.1 /path/to/CatchBan.dmg --clobber
```

Optional checksum upload:

```bash
shasum -a 256 /path/to/CatchBan.dmg > /path/to/CatchBan.dmg.sha256
gh release upload v2.0.0-beta.1 /path/to/CatchBan.dmg.sha256 --clobber
```

## 5) Fallback behavior

- The release workflow prefers versioned `.github/releases/<tag>.md` files when present.
- If no versioned Markdown body exists, the workflow falls back to GitHub-generated release notes.
- This keeps release pages brand-safe and bilingual while preserving a fallback path for technical releases.
