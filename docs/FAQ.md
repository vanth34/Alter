**English** · [Русский](ru/FAQ.md)

# FAQ

### What is Alter?
An all-in-one Android modding and reverse-engineering toolkit: a regex manager,
a Smali in Regex converter, a Smali alert-dialog generator, DEX dumping with and
without root, an il2cpp dumper, and one-tap injection of the il2cpp and dex
dumper libraries.

### Does it require root?
No. Everything works on non-rooted devices except **Root dump DEX**, which needs
root and an `arm64-v8a` device.

### What Android versions are supported?
Android 8.0 (API 26) and newer, on ARM devices (`arm64-v8a` or `armeabi-v7a`).

### Is Alter open source?
No. The application is proprietary (see [../LICENSE](../LICENSE)). It bundles a
few open-source components, credited in [CREDITS.md](CREDITS.md).

### Can I use files that Alter generates in my own projects?
Yes. Generated content (for example, generated Smali dialogs) is covered by the
permissive [Alter Generated Content License](../LICENSE-GENERATED-CONTENT.txt).
You can use it in personal and commercial projects; attribution is required only
when you redistribute generated content as part of a library or template pack.

### In what format are regex backups saved?
A `.zip` archive with an index file (`folders_meta.json`) and one `JSON` file per
folder. Import merges the backup into your collection and never deletes anything. Full details are in
[features/regex-manager.md](features/regex-manager.md).

### What does the "Secret cryptKey" field in the dialog builder do?
It powers the dialog's tamper-protection logic, which prevents the dialog from
being bypassed by editing the host app's `SharedPreferences`. See
[features/alert-dialogs.md](features/alert-dialogs.md).

### Which DEX dumper should I use?
Start with **Rootless dump DEX** in Sandbox mode. If the result is empty, enable
*Deep unpacking*, *Hook dump* and *Auto call* and try a couple more times. If the
app detects the sandbox, switch to **Inject** mode. With root, **Root dump DEX**
in God Dump mode also catches DEX that only exists in memory. See
[features/dumpers.md](features/dumpers.md).

### The il2cpp dumper says the metadata is encrypted. What now?
A static dump is impossible for that game. Switch the il2cpp dumper to **Inject**
mode: the patched game dumps itself after it decrypts the metadata at runtime.

### What is the "32-bit compatibility" option?
It installs a small helper app so the rootless DEX dumper can run 32-bit-only
apps. Inject mode needs no such option: it always adds both ARM architectures.

### What does "Re-sign APK" do?
It signs the patched APK with a test key so Android will install it. Uninstall
the original app first, because the signatures differ. With the option off, the
original signature is kept, which only installs on firmware without signature
checks.

### How do I get updates?
Use the in-app update check, download the latest build from the
[Releases](https://github.com/vanth34/Alter/releases/latest) page, or grab
it from the project's Telegram channel
[t.me/AlterProject](https://t.me/AlterProject), where releases are also posted.

### Where can I report a bug or ask for a feature?
Open an issue on GitHub, or reach the project on Telegram:
[t.me/AlterProject](https://t.me/AlterProject).
