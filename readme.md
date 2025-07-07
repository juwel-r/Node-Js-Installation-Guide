# ⚙️ Node.js Installation with `fnm` (Fast Node Manager) on Windows

---

## Step 1: Enable PowerShell Script Execution

PowerShell blocks running scripts by default. To allow local scripts like your profile to run, open PowerShell **as your user** (no admin needed) and run:

```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned -Force
```

---

## Step 2: Install `fnm` (Fast Node Manager)

### Option A: Using Winget (Windows Package Manager)

```powershell
winget install Schniz.fnm
```

> **If you get:**
> `'winget' is not recognized`
> → Install **App Installer** from Microsoft Store: [https://aka.ms/GetWinget](https://aka.ms/GetWinget)
> Then restart PowerShell and try again.

---

## Step 3: Add `fnm` to Your User PATH (if not added automatically)

1. Open **System Properties** > **Environment Variables**
2. Under **User Variables** > **Path** > **Edit** > **New**
3. Add the directory (adjust if your username is different):

```
%LOCALAPPDATA%\Microsoft\WinGet\Packages\Schniz.fnm_Microsoft.Winget.Source_8wekyb3d8bbwe
```

Example full path:

```plaintext
C:\Users\juwel\AppData\Local\Microsoft\WinGet\Packages\Schniz.fnm_Microsoft.Winget.Source_8wekyb3d8bbwe
```

4. Also add:

```
%APPDATA%\fnm\aliases\default
```

Example:

```plaintext
C:\Users\juwel\AppData\Roaming\fnm\aliases\default
```

---

## Step 4: Verify `fnm` Installation

Restart PowerShell and run:

```powershell
fnm --version
```

You should see the installed `fnm` version number.

---

## Step 5: Install Node.js Versions

To install a Node.js version (e.g., 22):

```powershell
fnm install 22
```

You can also install the latest Node.js version:

```powershell
fnm install --latest
```

---

## Step 6: Switch Between Node Versions

To use a specific version:

```powershell
fnm use 22
```

To set a default version:

```powershell
fnm default 22
```

Check your current Node version:

```powershell
node -v
```

---

## Step 7: Configure PowerShell to Load `fnm` Automatically

Create or open your PowerShell profile script at:

```plaintext
%USERPROFILE%\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
```

If the file doesn’t exist, create it:

```powershell
if (!(Test-Path -Path $PROFILE)) {
    New-Item -ItemType File -Path $PROFILE -Force
}
```

Open the profile in Notepad:

```powershell
notepad $PROFILE
```

Add this line inside the file:

```powershell
fnm env --use-on-cd | Out-String | Invoke-Expression
```

Save and close.

Reload the profile:

```powershell
. $PROFILE
```

---

## Bonus: Setup for Git Bash or Other Bash Terminals

In Git Bash or any Bash shell, run:

```bash
eval "$(fnm env --use-on-cd --shell bash)"
```

To make it permanent, add that line to your `~/.bashrc` or `~/.zshrc`.

---

## Troubleshooting & Tips

| Problem                             | Solution                                                                                                         |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| `winget` not recognized             | Install App Installer from Microsoft Store, then restart terminal                                                |
| `fnm` command not found             | Check PATH includes `%LOCALAPPDATA%\Microsoft\WinGet\Packages\Schniz.fnm...` and `%APPDATA%\fnm\aliases\default` |
| `running scripts is disabled` error | Run `Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned -Force`                                |
| Profile file missing                | Create PowerShell profile with `New-Item -ItemType File -Path $PROFILE -Force`                                   |
| Changes not applied                 | Restart PowerShell or reboot system                                                                              |

---

This setup ensures **smooth management of Node.js versions** on Windows with `fnm` using PowerShell and optionally Git Bash.

---

If you want, I can help you make a **script that automates all these steps** or create a condensed cheat sheet!
