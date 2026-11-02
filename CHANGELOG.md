**English** · [Русский](CHANGELOG.ru.md)

# Changelog

All notable changes to Alter are documented here. This project uses date-based
versioning (`YYYY.MM.DD`).

**Alter 2026.11.02 Azoth**

- New tool: Rootless DEX dump — extract DEX from protected apps without root
- Choose a target from installed apps or from an .apk / .apks file
- Deep unpacking with method body recovery, including on Android 12+
- Unpacking options: Hook-dump, Auto-invoke, DEX verification, dual-architecture dump
- Support for 32-bit apps via a 32-bit helper
- New tool: Root DEX dump for rooted devices (arm64)
- God Dump mode for finding hidden and dynamically loaded DEX files
- App list with search and filters for system apps and Xposed modules
- New feature: Smali in Regex
- il2cpp dumper completely rewritten: dump is generated without launching the game, with support for il2cpp metadata versions v24–v31
- Optional saving of scripts for IDA Pro, Ghidra, Binary Ninja, and radare2 alongside dump.cs
- "Inject" mode for creating a patched APK copy with an embedded dumper now automatically extracts files to the Alter folder; Document Provider or Root is no longer required
- "Inject" mode supports split APKs (.apks, .xapk, .apkm) and merges them into a single file
- Redesigned all screens in Material 3 style
- Light, dark, or system theme
- Dynamic colors from the system palette (Android 12+)
- Home / Regex bottom navigation bar: floating or classic
- Liquid glass effect (full effect on Android 13+)
- Glass quality setting with automatic device-based selection
- Smooth transition animations between screens and tabs
- Proper display under system bars and display cutouts
- Welcome onboarding on first launch
- Significantly faster UI performance and app responsiveness
- Fast, smooth scrolling through the regex collection
- Clear error messages during dumping
- Choice of folder for saving results
- Detailed error report with a log-copy button
- Improved stability on Android 8–16
- Built-in update window with a changelog list
- Download and install updates directly from the app
- Option to postpone or skip an update version
- Removed the APK string protection tool (LSParanoid)