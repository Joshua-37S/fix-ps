# Recovery Mode: Fix Privacy & Security

## Only two commands matter

### Command 1: Mount the Data volume

```
diskutil mount disk3s4
```

### Command 2: Delete the user-level TCC database

```
rm "/Volumes/Data/Users/joshua.akparanta/Library/Application Support/com.apple.TCC/TCC.db"
```

NOTE: The volume is called "Data" in Tahoe, NOT "Macintosh HD - Data".

The quotes around the path are critical. Do not remove them.

Then restart from Apple menu.

---

## Full steps

1. Shut down (Apple menu, Shut Down)
2. Hold power button, "Loading startup options", Options, Continue
3. Menu bar: Utilities, Terminal
4. Run: `diskutil mount disk3s4`
5. Check the mount name: `ls /Volumes/` and note whether it says "Data" or "Macintosh HD - Data"
6. Run the rm command using the correct volume name from step 5:
   `rm "/Volumes/Data/Users/joshua.akparanta/Library/Application Support/com.apple.TCC/TCC.db"`
7. Verify it is gone:
   `ls "/Volumes/Data/Users/joshua.akparanta/Library/Application Support/com.apple.TCC/"`
   Should show empty or "No such file". That means success.
8. Close Terminal, Apple menu, Restart
9. Open System Settings, Privacy & Security, should work now

## After it works

Re-grant Full Disk Access, Accessibility, etc. to apps (DriveDx, Ghostty, etc.) because the database was rebuilt clean.
