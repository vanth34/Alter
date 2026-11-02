[English](../CREDITS.md) · **Русский**

# Благодарности

Alter опирается на работу нескольких open-source проектов. Огромная благодарность
их авторам и мейнтейнерам. Каждый компонент остаётся собственностью своего автора
и используется по его лицензии. Полные тексты лицензий собраны в
[THIRD_PARTY_LICENSES.md](THIRD_PARTY_LICENSES.md).

## Люди

- **RevEx**: автор и разработчик ([t.me/revexlab](https://t.me/revexlab)).
- **☭return-void☭**: главный бета-тестер и помощь со сборкой кода.
- **slavrom21**: дизайнер Monet-иконки приложения.

## Встроенные компоненты

### il2cppdumper
- **Автор:** MuhammadRizwan ([@muhammadrizwan87](https://github.com/muhammadrizwan87))
- **Репозиторий:** https://github.com/muhammadrizwan87/il2cppdumper
- **Лицензия:** MIT
- **Роль в Alter:** нативная библиотека, которую *il2cpp dumper* внедряет в
  инжект-режиме для дампа классов, методов и полей IL2CPP из запущенного
  Unity-приложения. Её шаблоны используются для скриптов IDA, Ghidra, Binary Ninja
  и radare2, которые сохраняются рядом с `dump.cs`.
- Построено на основе [Zygisk-Il2CppDumper](https://github.com/Perfare/Zygisk-Il2CppDumper) от Perfare.

### dexdumper
- **Автор:** MuhammadRizwan ([@muhammadrizwan87](https://github.com/muhammadrizwan87))
- **Репозиторий:** https://github.com/muhammadrizwan87/dexdumper
- **Лицензия:** MIT
- **Роль в Alter:** нативная библиотека, которую *Rootless dump DEX* внедряет в инжект-режиме для
  извлечения DEX-файлов из памяти запущенного приложения.

### BlackDex
- **Автор:** CodingGay
- **Репозиторий:** https://github.com/CodingGay/BlackDex
- **Лицензия:** Apache License 2.0
- **Роль в Alter:** песочница, которая запускает цель и дампит её DEX из памяти; основа *Rootless dump DEX*.

### Dobby
- **Автор:** jmpews
- **Репозиторий:** https://github.com/jmpews/Dobby
- **Лицензия:** Apache License 2.0
- **Роль в Alter:** inline-хуки загрузки классов ART внутри песочницы.

### xHook
- **Автор:** iQIYI
- **Репозиторий:** https://github.com/iqiyi/xHook
- **Лицензия:** MIT
- **Роль в Alter:** PLT/GOT-хуки, которые не дают целевому приложению завершить себя.

### FreeReflection
- **Автор:** tiann
- **Репозиторий:** https://github.com/tiann/FreeReflection
- **Лицензия:** MIT
- **Роль в Alter:** доступ к скрытому API для песочницы на Android 9+.

### libsu
- **Автор:** topjohnwu
- **Репозиторий:** https://github.com/topjohnwu/libsu
- **Лицензия:** Apache License 2.0
- **Роль в Alter:** root-оболочка для *Root dump DEX*.

### ARSCLib
- **Автор:** REAndroid
- **Репозиторий:** https://github.com/REAndroid/ARSCLib
- **Лицензия:** Apache License 2.0
- **Роль в Alter:** чтение и запись APK, правка манифеста и слияние сплитов в инжект-режиме.

### apksig
- **Автор:** The Android Open Source Project
- **Репозиторий:** https://android.googlesource.com/platform/tools/apksig
- **Лицензия:** Apache License 2.0
- **Роль в Alter:** подпись пропатченных APK (v1/v2/v3).

### smali / dexlib2
- **Автор:** Google, Ben Gruver (JesusFreke)
- **Репозиторий:** https://github.com/google/smali
- **Лицензия:** BSD 3-Clause
- **Роль в Alter:** сборка `classes.dex` сгенерированных диалогов.

### liquidglass
- **Автор:** pandadog (QWEA0)
- **Репозиторий:** https://github.com/QWEA0/liquidglass
- **Лицензия:** MIT
- **Роль в Alter:** панель и поверхности Liquid Glass.

## Спасибо

Если вы поддерживаете один из проектов выше и хотите скорректировать атрибуцию,
напишите в [t.me/revexlab](https://t.me/revexlab).
