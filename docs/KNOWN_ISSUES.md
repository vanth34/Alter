**English** · [Русский](ru/KNOWN_ISSUES.md)

# Known Issues

This page tracks known limitations and rough edges. If you hit something that
isn't listed, please open a
[bug report](https://github.com/vanth34/Alter/issues/new/choose).

## Current

- _Nothing tracked yet for this release._

## Notes & limitations

- **Storage access:** on Android 11+, patching APKs requires "All files access"
  (`MANAGE_EXTERNAL_STORAGE`). If file selection or saving fails, confirm the
  permission is granted (see [PERMISSIONS.md](PERMISSIONS.md)).
- **Protected / packed targets:** some apps use protections that can interfere
  with dumping or patching. Results vary by target; see the upstream dumper
  projects for details on what they can and cannot handle.
- **Signing:** if a patched APK won't install, make sure **Re-sign APK** was
  enabled and that any previous copy of the app is uninstalled first
  (signature mismatch).
- **Packers are not deterministic:** a rootless DEX dump that finds nothing on
  the first run often succeeds on the second or third.
- **il2cpp static dump:** encrypted `global-metadata.dat`, a packed
  `libil2cpp.so` and metadata v35+ are not supported; use Inject mode.
- **Root dump DEX** works only on `arm64-v8a` devices and restarts the target app.

## Template for reporting

When reporting an issue, please include:

- Alter version (e.g. `2026.11.02`)
- Device model and Android version
- The tool and mode you used (for example *Rootless dump DEX, Sandbox*)
- The log from **Copy log** in the error dialog, if there was one
- Exact steps to reproduce
- What you expected vs. what happened
