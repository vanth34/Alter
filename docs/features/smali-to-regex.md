**English** · [Русский](../ru/features/smali-to-regex.md)

# Smali in Regex

Writing a regex for a block of smali by hand is slow and fragile: registers and labels change every time the app is rebuilt. **Smali in Regex** turns a fragment into a pattern that survives those changes.

## How to use

1. Open **Smali in Regex** from the Home tab.
2. Paste a smali fragment with **Paste from clipboard** (or type it in).
3. Tap **Convert to regex**.
4. Tap **Copy result** and save the pattern in the [Regex Manager](regex-manager.md).

## What the converter does

- **Escapes** regex special characters: `[ ] ( ) { } \ $ ^ | + * ? . "`.
- **Registers** such as `v0` or `p1` become `[vp]\d+`.
- **Indentation** of four spaces becomes `\s{4}`.
- **Line breaks** become `\n`, so the whole fragment is one pattern.
- **Labels** such as `:cond_1a` and `:goto_3` become `:cond_[A-Za-z0-9]+` and `:goto_[A-Za-z0-9]+`.

## Example

```smali
    const/4 v0, 0x1
    if-eqz p1, :cond_0
```

becomes

```
\s{4}const/4 [vp]\d+, 0x1\n\s{4}if-eqz [vp]\d+, :cond_[A-Za-z0-9]+
```
