# Fix Privacy & Security (No Recovery Mode)

Use the tempuser account. It has working P&S and admin access.

## Steps

### 1. Switch to tempuser

Apple menu, Log Out. Log into tempuser.

### 2. Grant Full Disk Access to Terminal

Open System Settings, Privacy & Security, Full Disk Access.
Click the + button.
Navigate to /System/Applications/Utilities/ and add Terminal.app.

### 3. Open Terminal.app

Use Terminal (not Ghostty). It is in Applications/Utilities.

### 4. Delete the corrupted TCC database

```
sudo rm "/Users/joshua.akparanta/Library/Application Support/com.apple.TCC/TCC.db"
```

Enter tempuser's password when asked. No output means success.

### 5. Verify

```
ls "/Users/joshua.akparanta/Library/Application Support/com.apple.TCC/TCC.db"
```

Should say "No such file or directory". That means it worked.

### 6. Switch back

Log out of tempuser. Log into joshua.akparanta.
Open System Settings, Privacy & Security. It should load properly.

## After it works

Re-grant Full Disk Access to apps like DriveDx and Ghostty.
The database was rebuilt clean so all previous grants are gone.
