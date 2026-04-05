# Recovery Mode: Fix Privacy & Security

## Only two commands matter

### Command 1: Mount the Data volume

```
diskutil mount disk3s4
```

If unsure of the identifier, run `diskutil list` and look for the line showing "Data" with ~393 GB.

### Command 2: Delete the user-level TCC database

```
rm "/Volumes/Macintosh HD - Data/Users/joshua.akparanta/Library/Application Support/com.apple.TCC/TCC.db"
```

IMPORTANT: The quotes around the path are critical. Do not remove them.

Then restart from Apple menu.

---

## Full steps

1. Shut down (Apple menu, Shut Down)
2. Hold power button, "Loading startup options", Options, Continue
3. Menu bar: Utilities, Terminal
4. Run Command 1: `diskutil mount disk3s4`
5. Verify: `ls /Volumes/` should now show "Macintosh HD - Data"
6. Run Command 2 exactly as written above (with the quotes)
7. Verify: `ls "/Volumes/Macintosh HD - Data/Users/joshua.akparanta/Library/Application Support/com.apple.TCC/"` should show empty or "No such file"
8. Close Terminal, Apple menu, Restart
9. Open System Settings, Privacy & Security, should work now

## Common mistakes

- Missing quotes: every path with spaces MUST be in double quotes "like this"
- Wrong volume: use `disk3s4` not a name with spaces
- Wrong TCC.db: the path must go through /Users/joshua.akparanta/ (user-level, not system-level)

## After it works

Re-grant Full Disk Access, Accessibility, etc. to apps (DriveDx, Ghostty, etc.) because the database was rebuilt clean.
