## ⚙️ Node.js Installation Guide

### 🧪 Step 1: Install `fnm` via Winget

Open **PowerShell** and run:

To allow PowerShell to run local scripts, like your profile script (Microsoft.PowerShell_profile.ps1), while still keeping your system reasonably secure. By default running scripts is disabled on system.

```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned -Force

```
Let's start install node by running cmd

```powershell
winget install Schniz.fnm
````

---

### 🛠️ Step 2: Set Up Environment Variables

You **must** add `fnm` to the **User Variables**, not the System Variables.

* Go to:
  `System Properties > Environment Variables > User Variables > Path > New`
* Add a directory similar to the one below (your path may vary):

```plaintext
C:\Users\juwel\AppData\Local\Microsoft\WinGet\Packages\Schniz.fnm_Microsoft.Winget.Source_8wekyb3d8bbwe
```

---

### 📦 Step 3: Install a Node.js Version

In PowerShell, run:

```powershell
fnm install 22
```

---

### 🔁 Step 4: Add the Default Version Path

Also add this directory to the **User Path** in environment variables:

```plaintext
C:\Users\juwel\AppData\Roaming\fnm\aliases\default
```

---

### 🔄 Step 5: Switch Node Version and Configure PowerShell Profile

To switch to a specific Node.js version:

```powershell
fnm use 24.1.0
```

Now create the PowerShell profile file if it doesn’t exist:

```plaintext
C:\Users\username\OneDrive\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
```

Open the file and paste the following:

```powershell
fnm env --use-on-cd --shell powershell | Out-String | Invoke-Expression
```

And if you want to use git bash terminal then open and run this cmd

```git bash cmd
eval "$(fnm env --use-on-cd --shell bash)"
```
