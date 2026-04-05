# Recovery Mode: Fix Privacy & Security

## THE ONE COMMAND (does everything)

```
diskutil mount disk3s4 && find /Volumes -path "*/joshua.akparanta/Library/Application Support/com.apple.TCC/TCC.db" -exec rm {} \; && echo "DELETED SUCCESSFULLY"
```

If you see DELETED SUCCESSFULLY at the end, it worked. Restart.

If you see nothing after the mount message, the file was not found. Run this to check what volumes exist and search manually:

```
ls /Volumes/
```

Then for each volume name you see, try:

```
ls "/Volumes/VOLUMENAME/Users/joshua.akparanta/Library/Application Support/com.apple.TCC/"
```

Replace VOLUMENAME with each name from the list until you find one that shows TCC.db.

---

## How to get here

1. Shut down (Apple menu, Shut Down)
2. Hold power button until "Loading startup options"
3. Click Options, Continue
4. Menu bar: Utilities, Terminal
5. Paste the one command above
6. If it says DELETED SUCCESSFULLY, close Terminal, Apple menu, Restart
7. Open System Settings, Privacy & Security

## After it works

Re-grant Full Disk Access, Accessibility, etc. to apps (DriveDx, Ghostty, etc.)
