**English** · [Русский](ru/PERMISSIONS.md)

# Permissions

Alter requests a small set of permissions, all tied to working with APK files,
saving dumps and managing your regex backups. It does not collect analytics or send
your data anywhere.

- **Read shared storage** (`READ_EXTERNAL_STORAGE`): read APK files you select
  and import regex-collection backups.
- **Manage all files** (`MANAGE_EXTERNAL_STORAGE`): access APKs anywhere on the
  device and save dumps to `/sdcard/Alter`.
- **Write shared storage** (`WRITE_EXTERNAL_STORAGE`): save dumps, patched APKs,
  generated files and regex backups.
- **See installed apps** (`QUERY_ALL_PACKAGES`): list installed apps as targets
  for the dumpers.
- **Install packages** (`REQUEST_INSTALL_PACKAGES`): install updates and the
  32-bit helper app.
- **Vibrate** (`VIBRATE`): haptic feedback for actions in the UI.
- **Internet** (`INTERNET`): check for updates and download the latest release.
- **Network state** (`ACCESS_NETWORK_STATE`): detect whether the device is online
  before attempting network operations.

Root is never requested at startup. Only **Root dump DEX** asks your root manager
for access, and only when you open it.

## Notes

- **Storage access on Android 11+.** Because Alter patches arbitrary APK files
  chosen by the user, it uses "All files access" (`MANAGE_EXTERNAL_STORAGE`).
  You can grant it from **Settings → Apps → Alter → Permissions**.
- **`READ_/WRITE_EXTERNAL_STORAGE`** are the legacy storage permissions and
  apply mainly to Android 10 and below.
- Alter uses the internet only for update checks and downloads, nothing else.
