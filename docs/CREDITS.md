**English** · [Русский](ru/CREDITS.md)

# Credits

Alter stands on the work of several open-source projects. Huge thanks to their
authors and maintainers. Each component remains the property of its respective
author and is used under its own license. Full license texts are collected in
[THIRD_PARTY_LICENSES.md](THIRD_PARTY_LICENSES.md).

## People

- **RevEx**: author and developer ([t.me/revexlab](https://t.me/revexlab)).
- **☭return-void☭**: chief beta tester and the steady hand behind building the code.
- **slavrom21**: designer of the Monet app icon.

## Bundled components

### il2cppdumper
- **Author:** MuhammadRizwan ([@muhammadrizwan87](https://github.com/muhammadrizwan87))
- **Repository:** https://github.com/muhammadrizwan87/il2cppdumper
- **License:** MIT
- **Role in Alter:** native runtime library injected by the *il2cpp dumper* in
  Inject mode to dump IL2CPP classes, methods and fields from a running Unity app.
  Its script templates are used for the IDA, Ghidra, Binary Ninja and radare2
  scripts saved next to `dump.cs`.
- Built on the foundation of [Zygisk-Il2CppDumper](https://github.com/Perfare/Zygisk-Il2CppDumper) by Perfare.

### dexdumper
- **Author:** MuhammadRizwan ([@muhammadrizwan87](https://github.com/muhammadrizwan87))
- **Repository:** https://github.com/muhammadrizwan87/dexdumper
- **License:** MIT
- **Role in Alter:** native runtime library injected by *Rootless dump DEX* in Inject mode to
  extract DEX files from a running app's memory.

### BlackDex
- **Author:** CodingGay
- **Repository:** https://github.com/CodingGay/BlackDex
- **License:** Apache License 2.0
- **Role in Alter:** sandbox that runs the target and dumps its DEX from memory; the core of *Rootless dump DEX*.

### Dobby
- **Author:** jmpews
- **Repository:** https://github.com/jmpews/Dobby
- **License:** Apache License 2.0
- **Role in Alter:** inline hooks on ART class loading inside the sandbox.

### xHook
- **Author:** iQIYI
- **Repository:** https://github.com/iqiyi/xHook
- **License:** MIT
- **Role in Alter:** PLT/GOT hooks that stop the target app from killing itself.

### FreeReflection
- **Author:** tiann
- **Repository:** https://github.com/tiann/FreeReflection
- **License:** MIT
- **Role in Alter:** hidden API access for the sandbox on Android 9+.

### libsu
- **Author:** topjohnwu
- **Repository:** https://github.com/topjohnwu/libsu
- **License:** Apache License 2.0
- **Role in Alter:** root shell for *Root dump DEX*.

### ARSCLib
- **Author:** REAndroid
- **Repository:** https://github.com/REAndroid/ARSCLib
- **License:** Apache License 2.0
- **Role in Alter:** reading and writing APKs, manifest edits and split merging in inject mode.

### apksig
- **Author:** The Android Open Source Project
- **Repository:** https://android.googlesource.com/platform/tools/apksig
- **License:** Apache License 2.0
- **Role in Alter:** signing patched APKs (v1/v2/v3).

### smali / dexlib2
- **Author:** Google, Ben Gruver (JesusFreke)
- **Repository:** https://github.com/google/smali
- **License:** BSD 3-Clause
- **Role in Alter:** assembling the `classes.dex` of generated dialogs.

### liquidglass
- **Author:** pandadog (QWEA0)
- **Repository:** https://github.com/QWEA0/liquidglass
- **License:** MIT
- **Role in Alter:** the Liquid Glass bar and surfaces.

## Thank you

If you maintain one of the projects above and would like an attribution
adjusted, please reach out via [t.me/revexlab](https://t.me/revexlab).
