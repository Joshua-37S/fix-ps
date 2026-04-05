# Recovery Mode: Fix Privacy & Security

## Only two commands matter

### Command 1: Mount the Data volume

```
diskutil mount "Macintosh HD - Data"
```

If that fails, run `diskutil list`, find the "Data" volume identifier, then `diskutil mount <identifier>`

### Command 2: Delete the user-level TCC database

```
rm "/Volumes/Macintosh HD - Data/Users/joshua.akparanta/Library/Application Support/com.apple.TCC/TCC.db"
```

Then restart from Apple menu.

---

## Full steps

1. Shut down (Apple menu, Shut Down)
2. Hold power button, "Loading startup options", Options, Continue
3. Menu bar: Utilities, Terminal
4. Run Command 1 above
5. Verify: `ls /Volumes/` should show "Macintosh HD - Data"
6. Run Command 2 above
7. Verify: `ls "/Volumes/Macintosh HD - Data/Users/joshua.akparanta/Library/Application Support/com.apple.TCC/"` should show empty or "No such file"
8. Close Terminal, Apple menu, Restart
9. Open System Settings, Privacy & Security, should work now

## After it works

You will need to re-grant Full Disk Access, Accessibility, etc. to apps (DriveDx, Ghostty, etc.) because the database was rebuilt clean.
