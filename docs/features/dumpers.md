**English** · [Русский](../ru/features/dumpers.md)

# Dumpers

Alter's dumpers live on the Home tab, under **Modding Tool's**. Some of them also have an **Inject** mode that patches the APK itself. Pick a tool, choose a target (an installed app or a file), and tap start.

Not sure where to begin? For a regular app, start with the rootless DEX dump. If the app detects the sandbox and you have root, use the ROOT dump. For a Unity game, use the il2cpp dumper. If nothing else works, inject the dumper into the APK.

- [Rootless DEX dump](#rootless-dex-dump)
- [ROOT DEX dump](#root-dex-dump)
- [il2cpp dumper](#il2cpp-dumper)
- [Dumper injection](#dumper-injection)

## Rootless DEX dump

Opens as **Rootless dump DEX**. The target runs inside a [BlackDex](https://github.com/CodingGay/BlackDex) sandbox hosted by Alter, and the DEX it decrypts or loads at runtime is copied out of memory. The installed app itself is never changed, and no root is needed.

### How to use

1. Keep the mode on **Sandbox**.
2. Tap **Choose target**: pick an installed app (best success rate) or an `.apk` / `.apks` file.
3. Check the output folder (default `/storage/emulated/0/Alter/dex`).
4. Tap **Start unpacking**.

### Options

- **Deep unpacking:** restores method bodies that the packer removed back into the DEX. Adapted for Android 12+.
- **Hook dump:** hooks class loading to catch DEX that is loaded later.
- **Auto call methods:** actively loads every class, for shells that decrypt a class only when it is first used.
- **Verify DEX before dump:** checks the DEX magic in memory. Turn it off when a packer wipes the magic.
- **Dual-architecture dump:** dumps both ABIs at once into `arm64/` and `arm32/`.
- **32-bit compatibility:** installs a small helper app so 32-bit-only targets can be unpacked.

> Packers often behave differently from run to run. If the first attempt finds nothing, try again. Every error dialog has a **Copy log** button for bug reports.

## ROOT DEX dump

Opens as **Root dump DEX**. Needs root (Magisk, KernelSU, APatch and similar) and an `arm64-v8a` device. Alter force-stops the real app, starts it again and reads its DEX through a root shell ([libsu](https://github.com/topjohnwu/libsu)). Apps that detect a sandbox are not a problem here.

### How to use

1. Find the app with the search field. The **System apps** and **XP modules** filters show or hide those groups.
2. Choose the dump mode and the output folder (default `/storage/emulated/0/Alter/rootdump`).
3. Tap the start button next to the app and confirm.

### Modes

- **Standard:** collects every DEX the app has loaded.
- **Deep (God Dump):** scans ART memory for `DexFile` objects and rebuilds hidden and dynamically loaded DEX.

## il2cpp dumper

Opens as **il2cpp dumper**. In **Static** mode it reads `libil2cpp.so` and `global-metadata.dat` from the game's files and writes `dump.cs`. The game is never started, so no root, sandbox or patching is needed.

### How to use

1. Keep the mode on **Static**.
2. Tap **Choose target**: an installed game or an `.apk`, `.apks`, `.xapk` or `.apkm` file.
3. Tap **Start dump**.

The result goes to `/storage/emulated/0/Alter/il2cpp/<package>/`:

- `dump.cs`: classes, nested and generic types, fields with offsets, properties, constants and enums, methods with addresses;
- `il2cpp_ida.py`, `il2cpp_ghidra.py`, `il2cpp_binja.py`, `il2cpp_r2.r2`: scripts for IDA Pro, Ghidra, Binary Ninja and radare2. They can be switched off with **Scripts for disassemblers**.

### Limits

- Supported metadata versions are v24–v31 (Unity 2017 to 2023 and early Unity 6).
- Encrypted `global-metadata.dat` or a packed `libil2cpp.so` cannot be dumped statically. Use [Dumper injection](#dumper-injection) instead.

## Dumper injection

The **Inject** mode of **Rootless dump DEX** and **il2cpp dumper**. Alter writes a patched copy of the APK with a native dumper inside. You install it, run it, and the app dumps itself while it runs.

- **il2cpp dumper:** based on [muhammadrizwan87/il2cppdumper](https://github.com/muhammadrizwan87/il2cppdumper) (MIT). Dumps IL2CPP metadata from inside the running game, which also works when the files on disk are encrypted.
- **dex dumper:** based on [muhammadrizwan87/dexdumper](https://github.com/muhammadrizwan87/dexdumper) (MIT). Extracts DEX files from the running app's memory.

### How to use

1. Switch the mode to **Inject** and pick an installed app or a single `.apk` file.
2. Choose whether to **Re-sign APK**.
3. Tap **Inject**. The patched APK is saved next to the source.
4. Install and run the patched app. On first launch it asks once for storage access.
5. The dump is moved to `/sdcard/Alter/<dex|il2cpp>/<package>`. Without storage access it stays in `Android/data/<package>/files/Alter/`.

### What changes in the APK

- If the app is installed as several split APKs, they are merged into one.
- The dumper is added for both `arm64-v8a` and `armeabi-v7a`; other ABIs are removed.
- **Re-sign APK** on: the APK is signed with a test key (v1/v2/v3). Uninstall the original app first, because the signatures differ.
- **Re-sign APK** off: the original signature block is kept. This only installs on firmware that does not verify signatures.

> These libraries operate inside the target app's own sandbox. Use them only on apps you own or are authorized to analyze. Uninstalling the original app erases its data, so back it up first.
