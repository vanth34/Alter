**English** · [Русский](ru/RELEASING.md)

# Releasing & Auto-Update

This guide is for the maintainer. It explains how to publish a release so users
get a stable, permanent download link that also powers the in-app updater.

## 1. Naming

Alter uses date-based versions: `YYYY.MM.DD` plus a release name, for example `2026.11.02 Azoth`.

- **Tag:** `v2026.11.02`
- **Release title:** `Alter 2026.11.02 Azoth`
- **APK asset name:** keep it **exactly** `app-release.apk` on every release, since the
  permanent link below depends on this name never changing.

## 2. Publish a release

1. Go to **Releases → Draft a new release**.
2. **Choose a tag** → type the new tag (e.g. `v2026.11.02`) → *Create new tag on
   publish*.
3. Set the **title** and paste your notes (use `.github/RELEASE_TEMPLATE.md`).
4. **Attach** the `app-release.apk` build as a binary asset.
5. Leave **"Set as the latest release"** checked.
6. **Publish release.**

> Binaries live in Releases, not in the repository tree. Do not commit the APK
> into the repo.

## 3. Permanent download link

Because the asset is always named `app-release.apk` and the release is marked latest,
this URL always resolves to the newest APK:

```
https://github.com/vanth34/Alter/releases/latest/download/app-release.apk
```

Use it for the website button, Telegram, and the in-app "Download update" action.

## 4. In-app update check

Alter checks for updates by reading `update.json` from the `main` branch of this
repository:

```
https://raw.githubusercontent.com/vanth34/Alter/main/update.json
```

```json
{
  "versionCode": 2026110216,
  "versionName": "2026.11.02 Azoth",
  "apkUrl": "https://github.com/vanth34/Alter/releases/latest/download/app-release.apk",
  "sha256": "",
  "changelog": ["Each string is one line in the update dialog"]
}
```

- `versionCode`: if it is higher than the installed one, Alter shows the update
  dialog (Download, Later, Skip).
- `versionName` and `changelog`: shown in the dialog.
- `apkUrl`: where the APK is downloaded from.
- `sha256`: lower-case checksum of `app-release.apk`. When filled in, Alter verifies the
  download before installing; when empty, the check is skipped.

Update `update.json` **last**, after the release with `app-release.apk` is published,
otherwise users get a broken download link.

> Get the checksum with `sha256sum app-release.apk` on Linux/macOS or
> `(Get-FileHash app-release.apk).Hash.ToLower()` in PowerShell.
