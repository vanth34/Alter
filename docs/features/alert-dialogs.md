**English** · [Русский](../ru/features/alert-dialogs.md)

# Alert Dialog Generator

Generate ready-to-use **Smali** code for alert dialogs without writing it by
hand. Pick a style, fill in a short form, preview the result, and copy the
output into your project.

## Styles

Choose a style at the top of the screen. Each one has its own look, and the
preview shows exactly what users of the target app will see.

## Fields

Each dialog is built from a simple form. Typical fields include:

- **Dialog Title**
- **Dialog Message**
- **Negative Button Text**
- **Positive Button Text**
- **Positive Button Link**: opened when the positive button is tapped.
- **Secret cryptKey**: used by the built-in protection logic.

Some styles add their own fields, for example an accent colour or an expiration
date. The form shows them automatically when you pick that style.

Use **Save** to store the dialog and **View** to preview it.

## Output

**Save** writes the result to `/sdcard/Alter/<Style>/`, a separate folder for
each style:

- `classes.dex`: the compiled dialog. Add it to the target APK as the next
  `classesN.dex`.
- `hook.smali`: the line that shows the dialog. Paste it into `onCreate`,
  `onResume` or `onStart` of the activity where the dialog should appear.

## Tamper protection

Generated dialogs include built-in protection logic so they can't be silently
bypassed by editing the host app's `SharedPreferences`. The dialog validates its
own stored state (keyed by the *cryptKey* you provide) before deciding whether it
has already been shown, which prevents trivial "mark as seen" edits from skipping
it.

> Keep your `cryptKey` consistent for a given dialog, it ties the generated code
> to its saved state.
