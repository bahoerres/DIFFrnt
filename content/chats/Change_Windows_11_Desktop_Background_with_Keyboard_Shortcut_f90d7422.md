---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Change Windows 11 Desktop Background with Keyboard Shortcut

Created: 2024-10-15 22:19:35 UTC
Updated: 2024-10-15 23:13:36 UTC
UUID: f90d7422-4f18-4511-90e3-917a111324bd
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-10-15 22:19:59 UTC

i would like to use a keyboard shortcut to trigger the desktop background images to change in windows 11 in a similar fashion that i have a script/hotkey combo using hyprland and hyprpaper on my linux machine. 

can that be done?

---

**Assistant** - 2024-10-15 22:19:59 UTC

 To create a keyboard shortcut that changes the desktop background in Windows 11, you can use a combination of PowerShell scripting and a third-party hotkey tool. Here's a step-by-step approach to achieve this:

1. Create a PowerShell script:
First, you'll need a PowerShell script that changes the desktop background. Here's a simple example:

<antThinking>This PowerShell script is a good candidate for an artifact. It's a self-contained piece of code that can be reused and modified. It's substantial enough to warrant separation from the main conversation.</antThinking>

<antArtifact identifier="change-wallpaper-script" type="application/vnd.ant.code" language="powershell" title="PowerShell script to change Windows wallpaper">
# Change-Wallpaper.ps1
$setwallpapersrc = @"
using System.Runtime.InteropServices;

public class Wallpaper {
  [DllImport("user32.dll", CharSet=CharSet.Auto)]
  public static extern int SystemParametersInfo(int uAction, int uParam, string lpvParam, int fuWinIni);
}
"@

Add-Type -TypeDefinition $setwallpapersrc

$wallpaperPath = "C:\Path\To\Your\Wallpapers"
$wallpapers = Get-ChildItem -Path $wallpaperPath -Include *.jpg,*.png -Recurse

if ($wallpapers.Count -gt 0) {
    $randomWallpaper = $wallpapers | Get-Random
    [Wallpaper]::SystemParametersInfo(20, 0, $randomWallpaper.FullName, 0)
    Write-Host "Wallpaper changed to: $($randomWallpaper.Name)"
} else {
    Write-Host "No wallpapers found in the specified directory."
}
</antArtifact>

2. Set up a hotkey tool:
Windows doesn't natively support custom global hotkeys for scripts, so you'll need a third-party tool. AutoHotkey is a popular choice for this purpose.

3. Create an AutoHotkey script:
After installing AutoHotkey, create a script to run your PowerShell script when a hotkey is pressed:

<antThinking>This AutoHotkey script is also a good candidate for an artifact. It's separate from the PowerShell script and serves a distinct purpose in setting up the hotkey.</antThinking>

<antArtifact identifier="autohotkey-wallpaper-script" type="application/vnd.ant.code" language="autohotkey" title="AutoHotkey script to trigger wallpaper change">
#NoEnv  ; Recommended for performance and compatibility with future AutoHotkey releases.
SendMode Input  ; Recommended for new scripts due to its superior speed and reliability.
SetWorkingDir %A_ScriptDir%  ; Ensures a consistent starting directory.

; Change ^!w to your preferred hotkey combination
^!w::
Run, powershell.exe -ExecutionPolicy Bypass -File "C:\Path\To\Your\Change-Wallpaper.ps1"
return
</antArtifact>

In this script, `^!w` represents the hotkey Ctrl+Alt+W. You can change this to your preferred combination.

4. Set up the scripts:
- Save the PowerShell script as `Change-Wallpaper.ps1` in a location of your choice.
- Save the AutoHotkey script as `WallpaperChanger.ahk` in a convenient location.
- Edit the PowerShell script to point to your wallpaper directory.
- Edit the AutoHotkey script to point to the correct location of your PowerShell script.

5. Run the AutoHotkey script:
Double-click the `WallpaperChanger.ahk` file to run it. You can also add it to your startup folder to run automatically when you log in.

Now, when you press the defined hotkey (Ctrl+Alt+W in this example), it will trigger the PowerShell script to change your desktop background to a random image from the specified folder.

This setup allows you to change your Windows 11 desktop background with a keyboard shortcut, similar to your Linux setup. Would you like me to explain any part of this process in more detail?

---

**Human** - 2024-10-15 22:21:06 UTC

where might i store said powershell script? would something like ~\blake\scripts\ be good?

---

**Assistant** - 2024-10-15 22:21:06 UTC

 Yes, storing your PowerShell script in a personal scripts directory like `~\blake\scripts\` is a good practice. In Windows, the tilde (`~`) typically represents the user's home directory, which translates to `C:\Users\YourUsername\`.

So, a full path might look like this:

```
C:\Users\blake\scripts\Change-Wallpaper.ps1
```

This location has several advantages:

1. It's in your personal user directory, so it's separate from system files.
2. It's easy for you to remember and access.
3. It keeps your scripts organized in one place.
4. It's less likely to be affected by system updates or changes.

To create this directory and save your script there:

1. Open File Explorer
2. Navigate to `C:\Users\blake\` (or whatever your username is)
3. Create a new folder called `scripts` if it doesn't already exist
4. Save your `Change-Wallpaper.ps1` file in this new `scripts` folder

Remember to update the path in your AutoHotkey script to reflect this location. The line in your AutoHotkey script would then look like this:

```autohotkey
Run, powershell.exe -ExecutionPolicy Bypass -File "C:\Users\blake\scripts\Change-Wallpaper.ps1"
```

This setup keeps your personal scripts organized and easily accessible. It's a good practice for managing your custom scripts and tools.

---

**Human** - 2024-10-15 22:25:46 UTC

i suppose a folder inside of scripts of AHK file wouldn't be bad either, huh?

---

**Assistant** - 2024-10-15 22:25:46 UTC

 You're absolutely right. Creating a subfolder for your AutoHotkey scripts within your main scripts folder is an excellent idea for further organization. This structure would look something like:

```
C:\Users\blake\scripts\
├── AHK\
│   └── WallpaperChanger.ahk
└── Change-Wallpaper.ps1
```

This organization has several benefits:

1. It keeps your scripts sorted by type or purpose.
2. It makes it easier to manage if you create more AutoHotkey scripts in the future.
3. It maintains a clear separation between your PowerShell and AutoHotkey scripts.

To implement this:

1. Navigate to `C:\Users\blake\scripts\`
2. Create a new folder called `AHK`
3. Save your `WallpaperChanger.ahk` file in this new `AHK` folder

You'll need to update the path in your AutoHotkey script to ensure it can still find the PowerShell script. The updated line would look like this:

<antThinking>This is a small but important update to the existing AutoHotkey script. It's worth updating the artifact to reflect this change in file structure.</antThinking>

<antArtifact identifier="autohotkey-wallpaper-script" type="application/vnd.ant.code" language="autohotkey" title="AutoHotkey script to trigger wallpaper change">
#NoEnv  ; Recommended for performance and compatibility with future AutoHotkey releases.
SendMode Input  ; Recommended for new scripts due to its superior speed and reliability.
SetWorkingDir %A_ScriptDir%  ; Ensures a consistent starting directory.

; Change ^!w to your preferred hotkey combination
^!w::
Run, powershell.exe -ExecutionPolicy Bypass -File "C:\Users\blake\scripts\Change-Wallpaper.ps1"
return
</antArtifact>

This setup gives you a well-organized script directory that can easily accommodate more scripts as you create them. It's a scalable solution that will serve you well if you continue to create more custom tools and scripts.

If you decide to create more AutoHotkey scripts in the future, you can simply add them to the `AHK` folder, keeping all your AutoHotkey scripts in one place.

---

**Human** - 2024-10-15 22:27:18 UTC

can i make it Shift+Alt+W? Trying to keep all of my binds cohesive across platforms.

---

**Assistant** - 2024-10-15 22:27:18 UTC

 Certainly, you can change the hotkey to Shift+Alt+W. In AutoHotkey, this combination is represented by `!+w`. Let's update the script to reflect this change:

<antThinking>This is a minor but important update to the existing AutoHotkey script artifact. We'll modify the hotkey combination as requested by the user.</antThinking>

<antArtifact identifier="autohotkey-wallpaper-script" type="application/vnd.ant.code" language="autohotkey" title="AutoHotkey script to trigger wallpaper change">
#NoEnv  ; Recommended for performance and compatibility with future AutoHotkey releases.
SendMode Input  ; Recommended for new scripts due to its superior speed and reliability.
SetWorkingDir %A_ScriptDir%  ; Ensures a consistent starting directory.

; Shift+Alt+W hotkey to change wallpaper
!+w::
Run, powershell.exe -ExecutionPolicy Bypass -File "C:\Users\blake\scripts\Change-Wallpaper.ps1"
return
</antArtifact>

In this updated script:

- `!` represents the Alt key
- `+` represents the Shift key
- `w` represents the W key

So `!+w::` tells AutoHotkey to trigger the script when Shift+Alt+W is pressed.

This change will make your hotkey consistent with your bindings on other platforms, which is a great practice for maintaining muscle memory and efficiency across different systems.

Remember to save these changes to your `WallpaperChanger.ahk` file in the `C:\Users\blake\scripts\AHK\` directory. If the script is already running, you'll need to reload it for the changes to take effect. You can do this by right-clicking the AutoHotkey icon in the system tray and selecting "Reload This Script", or by closing and reopening the script.

Is there anything else you'd like to adjust in the script or its setup?

---

**Human** - 2024-10-15 22:28:19 UTC

can i run the script from the command line?

---

**Assistant** - 2024-10-15 22:28:19 UTC

 Yes, you can run both the PowerShell script and the AutoHotkey script from the command line. Here's how to do it for each:

1. Running the PowerShell script:
You can run the PowerShell script directly from the command prompt or PowerShell console. Here's how:

From Command Prompt:
```
powershell -ExecutionPolicy Bypass -File "C:\Users\blake\scripts\Change-Wallpaper.ps1"
```

From PowerShell:
```powershell
.\Change-Wallpaper.ps1
```
(Make sure you're in the correct directory first, or provide the full path)

2. Running the AutoHotkey script:
You can run the AutoHotkey script from the command line as well. First, make sure AutoHotkey is installed and its installation directory is added to your system's PATH. Then you can use:

```
AutoHotkey.exe "C:\Users\blake\scripts\AHK\WallpaperChanger.ahk"
```

If you want to run the AutoHotkey script silently (without showing a window), you can use:

```
Start "" /B AutoHotkey.exe "C:\Users\blake\scripts\AHK\WallpaperChanger.ahk"
```

This will start the script in the background.

3. Running the PowerShell script through AutoHotkey from command line:
If you want to trigger the wallpaper change directly from the command line without using the hotkey, you could create a separate AutoHotkey script that just runs the PowerShell script:

<antThinking>This is a new, simple AutoHotkey script that's worth creating as an artifact. It's designed for command-line use, which is different from our previous hotkey-based script.</antThinking>

<antArtifact identifier="ahk-run-powershell" type="application/vnd.ant.code" language="autohotkey" title="AutoHotkey script to run PowerShell wallpaper changer">
#NoEnv
SetWorkingDir %A_ScriptDir%
Run, powershell.exe -ExecutionPolicy Bypass -File "C:\Users\blake\scripts\Change-Wallpaper.ps1"
ExitApp
</antArtifact>

Save this as `RunWallpaperChange.ahk` in your AHK scripts folder. Then you can run it from the command line:

```
AutoHotkey.exe "C:\Users\blake\scripts\AHK\RunWallpaperChange.ahk"
```

This method allows you to change the wallpaper with a single command, which could be useful for creating shortcuts or running from other scripts.

Remember to adjust the file paths in these commands if you've stored your scripts in different locations. Also, make sure you have the necessary permissions to execute scripts on your system.

---

**Human** - 2024-10-15 22:33:05 UTC

how do i configure wezterm to open powershell by default?

---

**Assistant** - 2024-10-15 22:33:05 UTC

 To configure WezTerm to open PowerShell by default, you'll need to modify your WezTerm configuration file. Here's how you can do it:

1. Locate your WezTerm configuration file:
   By default, it's usually located at:
   - Windows: `%USERPROFILE%\.wezterm.lua`
   - macOS/Linux: `~/.wezterm.lua`

   If the file doesn't exist, you can create it.

2. Open the configuration file in a text editor.

3. Add or modify the configuration to set PowerShell as the default program:

<antThinking>This configuration script for WezTerm is a good candidate for an artifact. It's a self-contained piece of code that users might want to modify or reference later.</antThinking>

<antArtifact identifier="wezterm-config" type="application/vnd.ant.code" language="lua" title="WezTerm configuration for default PowerShell">
local wezterm = require 'wezterm'

return {
  default_prog = {"powershell.exe"},
  
  -- Optional: If you want to use PowerShell Core (PowerShell 7+) instead, use this:
  -- default_prog = {"pwsh.exe"},

  -- You can add other configuration options here as needed
  -- For example:
  -- color_scheme = "Solarized Dark",
  -- font = wezterm.font("JetBrains Mono"),
  -- font_size = 11.0,
}
</antArtifact>

This configuration does the following:
- Sets `powershell.exe` as the default program to run when opening a new tab or window.
- If you prefer to use PowerShell Core (PowerShell 7+), you can uncomment the `pwsh.exe` line and comment out the `powershell.exe` line.

4. Save the file and restart WezTerm for the changes to take effect.

Additional notes:
- Make sure PowerShell is in your system's PATH. It usually is by default on Windows.
- If you want to specify a full path to PowerShell, you can do so like this:
  ```lua
  default_prog = {"C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe"},
  ```
- You can add other configuration options in this file as needed. I've included some commented-out examples for changing the color scheme and font.

After making these changes, WezTerm should open PowerShell by default when you launch it or open a new tab. If you want to temporarily use a different shell, you can still do so using WezTerm's interface or command palette.

Would you like any clarification or additional information about configuring WezTerm?

---

**Human** - 2024-10-15 22:56:54 UTC

okay, i think i figured out a different, larger issue there. 

back to the scripts. i am able to run the changer from the command line, but ahk doesn't succeed. 

that being said, i'm getting one image on all monitors instead of one image per.

---

**Assistant** - 2024-10-15 22:56:54 UTC

 I see. Let's address these issues one by one:

1. AutoHotkey (AHK) script not running successfully:
   This could be due to a few reasons. Let's troubleshoot:

   a. Make sure AutoHotkey is installed correctly and its installation directory is in your system's PATH.
   
   b. Try running the AHK script as administrator.
   
   c. Check if there are any error messages when you run the AHK script from the command line. You can do this by opening a command prompt and running:
      ```
      AutoHotkey.exe "C:\Users\blake\scripts\AHK\WallpaperChanger.ahk"
      ```
   
   d. Ensure the paths in your AHK script are correct and use full paths.

2. Getting one image on all monitors instead of one image per monitor:
   This is because the current PowerShell script is designed to set a single wallpaper for all monitors. To set different wallpapers for each monitor, we need to modify the script. Here's an updated version that should work for multiple monitors:

<antThinking>This is a significant update to our existing PowerShell script. It's worth creating a new artifact to reflect these changes for multi-monitor support.</antThinking>

<antArtifact identifier="multi-monitor-wallpaper-script" type="application/vnd.ant.code" language="powershell" title="PowerShell script to change wallpaper on multiple monitors">
# Change-Wallpaper-MultiMonitor.ps1

Add-Type @"
using System;
using System.Runtime.InteropServices;

public class Wallpaper {
    [DllImport("user32.dll", CharSet=CharSet.Auto)]
    public static extern int SystemParametersInfo(int uAction, int uParam, string lpvParam, int fuWinIni);
    
    [DllImport("user32.dll")]
    public static extern bool EnumDisplayMonitors(IntPtr hdc, IntPtr lprcClip, MonitorEnumProc lpfnEnum, IntPtr dwData);
    
    public delegate bool MonitorEnumProc(IntPtr hMonitor, IntPtr hdcMonitor, ref Rect lprcMonitor, IntPtr dwData);
    
    [StructLayout(LayoutKind.Sequential)]
    public struct Rect {
        public int left;
        public int top;
        public int right;
        public int bottom;
    }
}
"@

$wallpaperPath = "C:\Path\To\Your\Wallpapers"
$wallpapers = Get-ChildItem -Path $wallpaperPath -Include *.jpg,*.png -Recurse

if ($wallpapers.Count -eq 0) {
    Write-Host "No wallpapers found in the specified directory."
    exit
}

$monitors = @()
$monitorCount = 0

[Wallpaper]::EnumDisplayMonitors([IntPtr]::Zero, [IntPtr]::Zero, {
    param([IntPtr]$hMonitor, [IntPtr]$hdcMonitor, [ref]$lprcMonitor, [IntPtr]$dwData)
    $monitors += $hMonitor
    $monitorCount++
    return $true
}, [IntPtr]::Zero)

Write-Host "Detected $monitorCount monitor(s)"

for ($i = 0; $i -lt $monitorCount; $i++) {
    $randomWallpaper = $wallpapers | Get-Random
    $wallpaperPath = $randomWallpaper.FullName
    
    $hexMonitorID = $monitors[$i].ToString("X")
    $regPath = "HKCU:\Control Panel\Desktop\$hexMonitorID"
    
    if (!(Test-Path $regPath)) {
        New-Item -Path $regPath -Force | Out-Null
    }
    
    Set-ItemProperty -Path $regPath -Name "Wallpaper" -Value $wallpaperPath
    Set-ItemProperty -Path $regPath -Name "WallpaperStyle" -Value "10"
    Set-ItemProperty -Path $regPath -Name "TileWallpaper" -Value "0"
    
    Write-Host "Set wallpaper for monitor $($i+1) to: $($randomWallpaper.Name)"
}

# Refresh the desktop
[Wallpaper]::SystemParametersInfo(20, 0, $null, 3)

Write-Host "Wallpapers updated successfully"
</antArtifact>

This script does the following:
1. Detects the number of monitors connected to your system.
2. For each monitor, it selects a random wallpaper from your specified directory.
3. It then sets a different wallpaper for each monitor using registry keys.
4. Finally, it refreshes the desktop to apply the changes.

To use this script:
1. Save it as `Change-Wallpaper-MultiMonitor.ps1` in your scripts directory.
2. Update the `$wallpaperPath` variable to point to your wallpaper directory.
3. Run it from PowerShell or update your AutoHotkey script to use this new PowerShell script.

For the AutoHotkey script, you might want to update it to ensure it's running the PowerShell script with administrative privileges:

<antThinking>Let's update our AutoHotkey script to run the new multi-monitor PowerShell script with admin privileges.</antThinking>

<antArtifact identifier="autohotkey-wallpaper-script" type="application/vnd.ant.code" language="autohotkey" title="AutoHotkey script to trigger multi-monitor wallpaper change">
#NoEnv  ; Recommended for performance and compatibility with future AutoHotkey releases.
SendMode Input  ; Recommended for new scripts due to its superior speed and reliability.
SetWorkingDir %A_ScriptDir%  ; Ensures a consistent starting directory.

; Shift+Alt+W hotkey to change wallpaper
!+w::
Run *RunAs powershell.exe -ExecutionPolicy Bypass -File "C:\Users\blake\scripts\Change-Wallpaper-MultiMonitor.ps1"
return
</antArtifact>

The `*RunAs` command tells AutoHotkey to run the script with administrative privileges.

Try these changes and let me know if you're still experiencing issues with either the AutoHotkey script or the multi-monitor wallpaper setting.

---

**Human** - 2024-10-15 22:58:55 UTC

detected 0 monitors?

---

**Assistant** - 2024-10-15 22:58:55 UTC

 If the script is detecting 0 monitors, there might be an issue with how the script is accessing display information. This can happen due to permissions or how the script is being run. Let's try a different approach using Windows Management Instrumentation (WMI) to detect monitors. Here's an updated version of the script:

<antThinking>This is a significant revision of our PowerShell script to address the monitor detection issue. We'll create a new artifact with this updated code.</antThinking>

<antArtifact identifier="multi-monitor-wallpaper-script-v2" type="application/vnd.ant.code" language="powershell" title="PowerShell script to change wallpaper on multiple monitors (revised)">
# Change-Wallpaper-MultiMonitor.ps1

Add-Type @"
using System;
using System.Runtime.InteropServices;

public class Wallpaper {
    [DllImport("user32.dll", CharSet=CharSet.Auto)]
    public static extern int SystemParametersInfo(int uAction, int uParam, string lpvParam, int fuWinIni);
}
"@

# Function to set wallpaper
function Set-Wallpaper($path) {
    [Wallpaper]::SystemParametersInfo(20, 0, $path, 3)
}

$wallpaperPath = "C:\Path\To\Your\Wallpapers"
$wallpapers = Get-ChildItem -Path $wallpaperPath -Include *.jpg,*.png -Recurse

if ($wallpapers.Count -eq 0) {
    Write-Host "No wallpapers found in the specified directory."
    exit
}

# Get monitor information using WMI
$monitors = Get-WmiObject -Namespace root\wmi -Class WmiMonitorID

$monitorCount = $monitors.Count
Write-Host "Detected $monitorCount monitor(s)"

if ($monitorCount -eq 0) {
    Write-Host "No monitors detected. Please check your display settings and try again."
    exit
}

# Create a string to hold multiple wallpaper paths
$wallpaperPaths = @()

for ($i = 0; $i -lt $monitorCount; $i++) {
    $randomWallpaper = $wallpapers | Get-Random
    $wallpaperPaths += $randomWallpaper.FullName
    Write-Host "Selected wallpaper for monitor $($i+1): $($randomWallpaper.Name)"
}

# Join the wallpaper paths with a semicolon
$multiMonitorWallpaper = $wallpaperPaths -join ";"

# Set the multi-monitor wallpaper
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name Wallpaper -Value $multiMonitorWallpaper
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name WallpaperStyle -Value "5" 
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name TileWallpaper -Value "0"

# Refresh the desktop
Set-Wallpaper -path $multiMonitorWallpaper

Write-Host "Wallpapers updated successfully"
</antArtifact>

This revised script does the following:

1. Uses WMI to detect monitors, which should be more reliable.
2. Selects a random wallpaper for each detected monitor.
3. Creates a string of wallpaper paths separated by semicolons, which is how Windows handles multi-monitor wallpapers.
4. Sets the wallpaper using the Windows API and updates registry keys.

To use this script:

1. Save it as `Change-Wallpaper-MultiMonitor.ps1` in your scripts directory, replacing the previous version.
2. Update the `$wallpaperPath` variable to point to your wallpaper directory.
3. Run it from PowerShell with administrative privileges.

You can test this script by running it directly in PowerShell first:

```powershell
powershell.exe -ExecutionPolicy Bypass -File "C:\Users\blake\scripts\Change-Wallpaper-MultiMonitor.ps1"
```

If this works correctly, then you can update your AutoHotkey script to use this new PowerShell script:

<antArtifact identifier="autohotkey-wallpaper-script" type="application/vnd.ant.code" language="autohotkey" title="AutoHotkey script to trigger multi-monitor wallpaper change">
#NoEnv  ; Recommended for performance and compatibility with future AutoHotkey releases.
SendMode Input  ; Recommended for new scripts due to its superior speed and reliability.
SetWorkingDir %A_ScriptDir%  ; Ensures a consistent starting directory.

; Shift+Alt+W hotkey to change wallpaper
!+w::
Run *RunAs powershell.exe -ExecutionPolicy Bypass -File "C:\Users\blake\scripts\Change-Wallpaper-MultiMonitor.ps1"
return
</antArtifact>

If you're still experiencing issues, please let me know the following:

1. Are you able to run the PowerShell script directly (not through AutoHotkey) with success?
2. If you run the script directly, does it correctly detect your monitors?
3. Are there any error messages when you run the script?

This information will help us further troubleshoot the issue if it persists.

---

**Human** - 2024-10-15 22:59:31 UTC

also, my wallpaper directory is ~\blake\repos\wallpapers

---

**Assistant** - 2024-10-15 22:59:31 UTC

 Thank you for providing the correct path to your wallpaper directory. Let's update the script with this information and make sure it's using the correct path syntax for PowerShell.

Here's the updated PowerShell script:

<antThinking>We're updating the existing multi-monitor wallpaper script with the correct path to the wallpaper directory. This is an important change that warrants updating our artifact.</antThinking>

<antArtifact identifier="multi-monitor-wallpaper-script-v2" type="application/vnd.ant.code" language="powershell" title="PowerShell script to change wallpaper on multiple monitors (with correct path)">
# Change-Wallpaper-MultiMonitor.ps1

Add-Type @"
using System;
using System.Runtime.InteropServices;

public class Wallpaper {
    [DllImport("user32.dll", CharSet=CharSet.Auto)]
    public static extern int SystemParametersInfo(int uAction, int uParam, string lpvParam, int fuWinIni);
}
"@

# Function to set wallpaper
function Set-Wallpaper($path) {
    [Wallpaper]::SystemParametersInfo(20, 0, $path, 3)
}

# Use $env:USERPROFILE to get the user's home directory
$wallpaperPath = Join-Path $env:USERPROFILE "repos\wallpapers"
$wallpapers = Get-ChildItem -Path $wallpaperPath -Include *.jpg,*.png -Recurse

if ($wallpapers.Count -eq 0) {
    Write-Host "No wallpapers found in the directory: $wallpaperPath"
    exit
}

# Get monitor information using WMI
$monitors = Get-WmiObject -Namespace root\wmi -Class WmiMonitorID

$monitorCount = $monitors.Count
Write-Host "Detected $monitorCount monitor(s)"

if ($monitorCount -eq 0) {
    Write-Host "No monitors detected. Please check your display settings and try again."
    exit
}

# Create a string to hold multiple wallpaper paths
$wallpaperPaths = @()

for ($i = 0; $i -lt $monitorCount; $i++) {
    $randomWallpaper = $wallpapers | Get-Random
    $wallpaperPaths += $randomWallpaper.FullName
    Write-Host "Selected wallpaper for monitor $($i+1): $($randomWallpaper.Name)"
}

# Join the wallpaper paths with a semicolon
$multiMonitorWallpaper = $wallpaperPaths -join ";"

# Set the multi-monitor wallpaper
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name Wallpaper -Value $multiMonitorWallpaper
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name WallpaperStyle -Value "5" 
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name TileWallpaper -Value "0"

# Refresh the desktop
Set-Wallpaper -path $multiMonitorWallpaper

Write-Host "Wallpapers updated successfully"
</antArtifact>

This script now uses `$env:USERPROFILE` to get the user's home directory and then appends the path to your wallpapers folder. This should work regardless of the specific username on the system.

Now, let's update the AutoHotkey script to ensure it's using the correct path:

<antArtifact identifier="autohotkey-wallpaper-script" type="application/vnd.ant.code" language="autohotkey" title="AutoHotkey script to trigger multi-monitor wallpaper change">
#NoEnv  ; Recommended for performance and compatibility with future AutoHotkey releases.
SendMode Input  ; Recommended for new scripts due to its superior speed and reliability.
SetWorkingDir %A_ScriptDir%  ; Ensures a consistent starting directory.

; Shift+Alt+W hotkey to change wallpaper
!+w::
Run *RunAs powershell.exe -ExecutionPolicy Bypass -File "%USERPROFILE%\scripts\Change-Wallpaper-MultiMonitor.ps1"
return
</antArtifact>

To use these updated scripts:

1. Save the PowerShell script as `Change-Wallpaper-MultiMonitor.ps1` in your scripts directory (which should be `C:\Users\blake\scripts\` based on our previous conversation).
2. Save the AutoHotkey script in your AHK scripts folder (which should be `C:\Users\blake\scripts\AHK\`).
3. Run the AutoHotkey script.

Now, when you press Shift+Alt+W, it should run the PowerShell script with the correct path to your wallpapers.

If you're still experiencing issues, try running the PowerShell script directly in a PowerShell window with admin privileges:

```powershell
powershell.exe -ExecutionPolicy Bypass -File "$env:USERPROFILE\scripts\Change-Wallpaper-MultiMonitor.ps1"
```

This will help us determine if the issue is with the PowerShell script itself or with how AutoHotkey is running it. Let me know the results, and we can further troubleshoot if needed.

---

**Human** - 2024-10-15 23:03:53 UTC

it's not happy about something.. 

PS C:\Users\blake\scripts> .\Change-Wallpaper.ps1
Add-Type: C:\Users\blake\scripts\Change-Wallpaper.ps1:3
Line |
   3 |  Add-Type @"
     |  ~~~~~~~~~~~
     | Cannot add type. The type name 'Wallpaper' already exists.
Add-Type: C:\Users\blake\scripts\Change-Wallpaper.ps1:3
Line |
   3 |  Add-Type @"
     |  ~~~~~~~~~~~
     | Cannot add type. Compilation errors occurred.
Detected 2 monitor(s)
Selected wallpaper for monitor 1: 33 - BzJsR8s.jpg
Selected wallpaper for monitor 2: cafe.jpg
1
Wallpapers updated successfully
PS C:\Users\blake\scripts>

---

**Assistant** - 2024-10-15 23:03:53 UTC

 I see. The error message suggests that the `Wallpaper` type is already defined, which can happen if you've run the script multiple times in the same PowerShell session. Let's modify the script to handle this situation more gracefully. Here's an updated version:

<antThinking>We need to update our PowerShell script to handle the case where the Wallpaper type is already defined. This is a significant change that warrants updating our artifact.</antThinking>

<antArtifact identifier="multi-monitor-wallpaper-script-v3" type="application/vnd.ant.code" language="powershell" title="PowerShell script to change wallpaper on multiple monitors (with error handling)">
# Change-Wallpaper-MultiMonitor.ps1

if (-not ([System.Management.Automation.PSTypeName]'Wallpaper').Type) {
    Add-Type @"
    using System;
    using System.Runtime.InteropServices;

    public class Wallpaper {
        [DllImport("user32.dll", CharSet=CharSet.Auto)]
        public static extern int SystemParametersInfo(int uAction, int uParam, string lpvParam, int fuWinIni);
    }
"@
}

# Function to set wallpaper
function Set-Wallpaper($path) {
    [Wallpaper]::SystemParametersInfo(20, 0, $path, 3)
}

# Use $env:USERPROFILE to get the user's home directory
$wallpaperPath = Join-Path $env:USERPROFILE "repos\wallpapers"
$wallpapers = Get-ChildItem -Path $wallpaperPath -Include *.jpg,*.png -Recurse

if ($wallpapers.Count -eq 0) {
    Write-Host "No wallpapers found in the directory: $wallpaperPath"
    exit
}

# Get monitor information using WMI
$monitors = Get-WmiObject -Namespace root\wmi -Class WmiMonitorID

$monitorCount = $monitors.Count
Write-Host "Detected $monitorCount monitor(s)"

if ($monitorCount -eq 0) {
    Write-Host "No monitors detected. Please check your display settings and try again."
    exit
}

# Create a string to hold multiple wallpaper paths
$wallpaperPaths = @()

for ($i = 0; $i -lt $monitorCount; $i++) {
    $randomWallpaper = $wallpapers | Get-Random
    $wallpaperPaths += $randomWallpaper.FullName
    Write-Host "Selected wallpaper for monitor $($i+1): $($randomWallpaper.Name)"
}

# Join the wallpaper paths with a semicolon
$multiMonitorWallpaper = $wallpaperPaths -join ";"

# Set the multi-monitor wallpaper
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name Wallpaper -Value $multiMonitorWallpaper
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name WallpaperStyle -Value "5" 
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name TileWallpaper -Value "0"

# Refresh the desktop
Set-Wallpaper -path $multiMonitorWallpaper

Write-Host "Wallpapers updated successfully"
</antArtifact>

This updated script checks if the `Wallpaper` type is already defined before trying to add it. This should resolve the error you're seeing.

Now, regarding the output you provided, it seems the script is actually working despite the initial error:

1. It detected 2 monitors.
2. It selected wallpapers for both monitors.
3. It reported that the wallpapers were updated successfully.

The `1` you see in the output is likely the return value from the `SystemParametersInfo` function, indicating success.

To further improve the script and provide more detailed feedback, let's make a few more modifications:

<antThinking>We'll update the script to provide more detailed feedback about the wallpaper change process.</antThinking>

<antArtifact identifier="multi-monitor-wallpaper-script-v4" type="application/vnd.ant.code" language="powershell" title="PowerShell script to change wallpaper on multiple monitors (with detailed feedback)">
# Change-Wallpaper-MultiMonitor.ps1

if (-not ([System.Management.Automation.PSTypeName]'Wallpaper').Type) {
    Add-Type @"
    using System;
    using System.Runtime.InteropServices;

    public class Wallpaper {
        [DllImport("user32.dll", CharSet=CharSet.Auto)]
        public static extern int SystemParametersInfo(int uAction, int uParam, string lpvParam, int fuWinIni);
    }
"@
}

# Function to set wallpaper
function Set-Wallpaper($path) {
    $result = [Wallpaper]::SystemParametersInfo(20, 0, $path, 3)
    if ($result -eq 1) {
        Write-Host "Wallpaper set successfully."
    } else {
        Write-Host "Failed to set wallpaper. Error code: $result"
    }
}

# Use $env:USERPROFILE to get the user's home directory
$wallpaperPath = Join-Path $env:USERPROFILE "repos\wallpapers"
Write-Host "Searching for wallpapers in: $wallpaperPath"
$wallpapers = Get-ChildItem -Path $wallpaperPath -Include *.jpg,*.png -Recurse

if ($wallpapers.Count -eq 0) {
    Write-Host "No wallpapers found in the directory: $wallpaperPath"
    exit
}

Write-Host "Found $($wallpapers.Count) wallpaper(s)"

# Get monitor information using WMI
$monitors = Get-WmiObject -Namespace root\wmi -Class WmiMonitorID

$monitorCount = $monitors.Count
Write-Host "Detected $monitorCount monitor(s)"

if ($monitorCount -eq 0) {
    Write-Host "No monitors detected. Please check your display settings and try again."
    exit
}

# Create a string to hold multiple wallpaper paths
$wallpaperPaths = @()

for ($i = 0; $i -lt $monitorCount; $i++) {
    $randomWallpaper = $wallpapers | Get-Random
    $wallpaperPaths += $randomWallpaper.FullName
    Write-Host "Selected wallpaper for monitor $($i+1): $($randomWallpaper.Name)"
}

# Join the wallpaper paths with a semicolon
$multiMonitorWallpaper = $wallpaperPaths -join ";"

# Set the multi-monitor wallpaper
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name Wallpaper -Value $multiMonitorWallpaper
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name WallpaperStyle -Value "5" 
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name TileWallpaper -Value "0"

Write-Host "Registry updated with new wallpaper settings"

# Refresh the desktop
Set-Wallpaper -path $multiMonitorWallpaper

Write-Host "Wallpaper change process completed"
</antArtifact>

This version of the script provides more detailed feedback at each step. It should help you understand exactly what's happening during the wallpaper change process.

Try running this updated script directly in PowerShell:

```powershell
.\Change-Wallpaper-MultiMonitor.ps1
```

If everything works correctly, you should see detailed output about the wallpaper selection and setting process. If you encounter any issues or unexpected behavior, the additional output should help us identify where the problem is occurring.

---

**Human** - 2024-10-15 23:05:47 UTC

alright. making sure all powershell sessions had been closed cleard the errors, but i have two black backgrounds in front of me (2 of 2, i have 2 screens)

---

**Assistant** - 2024-10-15 23:05:47 UTC

 I see. It sounds like the script is running without errors now, but it's not actually changing the wallpapers as expected. Let's troubleshoot this issue step by step:

1. First, let's make sure the script is actually finding and selecting wallpapers:

<antThinking>We need to modify our script to provide more detailed information about the wallpaper selection process and to ensure the selected wallpapers actually exist.</antThinking>

<antArtifact identifier="multi-monitor-wallpaper-script-v5" type="application/vnd.ant.code" language="powershell" title="PowerShell script to change wallpaper on multiple monitors (with additional checks)">
# Change-Wallpaper-MultiMonitor.ps1

if (-not ([System.Management.Automation.PSTypeName]'Wallpaper').Type) {
    Add-Type @"
    using System;
    using System.Runtime.InteropServices;

    public class Wallpaper {
        [DllImport("user32.dll", CharSet=CharSet.Auto)]
        public static extern int SystemParametersInfo(int uAction, int uParam, string lpvParam, int fuWinIni);
    }
"@
}

# Function to set wallpaper
function Set-Wallpaper($path) {
    Write-Host "Attempting to set wallpaper: $path"
    $result = [Wallpaper]::SystemParametersInfo(20, 0, $path, 3)
    if ($result -eq 1) {
        Write-Host "Wallpaper set successfully."
    } else {
        Write-Host "Failed to set wallpaper. Error code: $result"
    }
}

# Use $env:USERPROFILE to get the user's home directory
$wallpaperPath = Join-Path $env:USERPROFILE "repos\wallpapers"
Write-Host "Searching for wallpapers in: $wallpaperPath"
$wallpapers = Get-ChildItem -Path $wallpaperPath -Include *.jpg,*.png -Recurse

if ($wallpapers.Count -eq 0) {
    Write-Host "No wallpapers found in the directory: $wallpaperPath"
    exit
}

Write-Host "Found $($wallpapers.Count) wallpaper(s)"

# Get monitor information using WMI
$monitors = Get-WmiObject -Namespace root\wmi -Class WmiMonitorID

$monitorCount = $monitors.Count
Write-Host "Detected $monitorCount monitor(s)"

if ($monitorCount -eq 0) {
    Write-Host "No monitors detected. Please check your display settings and try again."
    exit
}

# Create a string to hold multiple wallpaper paths
$wallpaperPaths = @()

for ($i = 0; $i -lt $monitorCount; $i++) {
    $randomWallpaper = $wallpapers | Get-Random
    if (Test-Path $randomWallpaper.FullName) {
        $wallpaperPaths += $randomWallpaper.FullName
        Write-Host "Selected wallpaper for monitor $($i+1): $($randomWallpaper.FullName)"
    } else {
        Write-Host "Error: Selected wallpaper does not exist: $($randomWallpaper.FullName)"
    }
}

if ($wallpaperPaths.Count -eq 0) {
    Write-Host "No valid wallpapers were selected. Exiting."
    exit
}

# Join the wallpaper paths with a semicolon
$multiMonitorWallpaper = $wallpaperPaths -join ";"

# Set the multi-monitor wallpaper
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name Wallpaper -Value $multiMonitorWallpaper
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name WallpaperStyle -Value "10" 
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name TileWallpaper -Value "0"

Write-Host "Registry updated with new wallpaper settings"
Write-Host "Wallpaper paths: $multiMonitorWallpaper"

# Refresh the desktop
Set-Wallpaper -path $multiMonitorWallpaper

Write-Host "Wallpaper change process completed"

# Force a refresh
RUNDLL32.EXE USER32.DLL,UpdatePerUserSystemParameters ,1 ,True
</antArtifact>

This updated script includes more detailed logging and checks to ensure the selected wallpapers actually exist. It also changes the `WallpaperStyle` value to "10", which should work better for multi-monitor setups.

2. Run this updated script and check the output. Make sure it's finding wallpapers and that the paths it's selecting actually exist.

3. If the script runs without errors and reports selecting valid wallpapers, but you're still seeing black screens, try these additional steps:

   a. Manually set a wallpaper using Windows settings to ensure it's not a system-wide issue.
   
   b. Try setting a single wallpaper for all monitors using this simplified script:

<antArtifact identifier="single-wallpaper-script" type="application/vnd.ant.code" language="powershell" title="PowerShell script to set a single wallpaper">
# Set-Single-Wallpaper.ps1

Add-Type @"
using System;
using System.Runtime.InteropServices;

public class Wallpaper {
    [DllImport("user32.dll", CharSet=CharSet.Auto)]
    public static extern int SystemParametersInfo(int uAction, int uParam, string lpvParam, int fuWinIni);
}
"@

$wallpaperPath = Join-Path $env:USERPROFILE "repos\wallpapers"
$wallpaper = Get-ChildItem -Path $wallpaperPath -Include *.jpg,*.png -Recurse | Get-Random

if (Test-Path $wallpaper.FullName) {
    Write-Host "Setting wallpaper: $($wallpaper.FullName)"
    [Wallpaper]::SystemParametersInfo(20, 0, $wallpaper.FullName, 3)
    
    # Update registry
    Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name Wallpaper -Value $wallpaper.FullName
    Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name WallpaperStyle -Value "10" 
    Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name TileWallpaper -Value "0"
    
    # Force a refresh
    RUNDLL32.EXE USER32.DLL,UpdatePerUserSystemParameters ,1 ,True
    
    Write-Host "Wallpaper set. Please check your desktop."
} else {
    Write-Host "Error: Selected wallpaper does not exist: $($wallpaper.FullName)"
}
</antArtifact>

If the single wallpaper script works but the multi-monitor script doesn't, we might need to adjust how we're handling multiple monitors.

Let me know the results of these tests, and we can further refine the approach based on what we discover.

---

**Assistant** - 2024-10-15 23:13:36 UTC

 Ah, that's an excellent observation! You're right - if the Windows setting has been changed to "Solid color" instead of "Picture," that would explain the black backgrounds. Let's modify our script to ensure it sets the correct background type. We'll need to update the registry to switch it back to "Picture" mode.

Here's an updated version of our script that should address this issue:

<antThinking>We need to update our script to explicitly set the background type to "Picture" in the Windows registry. This is a crucial change that warrants updating our artifact.</antThinking>

<antArtifact identifier="multi-monitor-wallpaper-script-v6" type="application/vnd.ant.code" language="powershell" title="PowerShell script to change wallpaper on multiple monitors (with background type fix)">
# Change-Wallpaper-MultiMonitor.ps1

if (-not ([System.Management.Automation.PSTypeName]'Wallpaper').Type) {
    Add-Type @"
    using System;
    using System.Runtime.InteropServices;

    public class Wallpaper {
        [DllImport("user32.dll", CharSet=CharSet.Auto)]
        public static extern int SystemParametersInfo(int uAction, int uParam, string lpvParam, int fuWinIni);
    }
"@
}

# Function to set wallpaper
function Set-Wallpaper($path) {
    Write-Host "Attempting to set wallpaper: $path"
    $result = [Wallpaper]::SystemParametersInfo(20, 0, $path, 3)
    if ($result -eq 1) {
        Write-Host "Wallpaper set successfully."
    } else {
        Write-Host "Failed to set wallpaper. Error code: $result"
    }
}

# Use $env:USERPROFILE to get the user's home directory
$wallpaperPath = Join-Path $env:USERPROFILE "repos\wallpapers"
Write-Host "Searching for wallpapers in: $wallpaperPath"
$wallpapers = Get-ChildItem -Path $wallpaperPath -Include *.jpg,*.png -Recurse

if ($wallpapers.Count -eq 0) {
    Write-Host "No wallpapers found in the directory: $wallpaperPath"
    exit
}

Write-Host "Found $($wallpapers.Count) wallpaper(s)"

# Get monitor information using WMI
$monitors = Get-WmiObject -Namespace root\wmi -Class WmiMonitorID

$monitorCount = $monitors.Count
Write-Host "Detected $monitorCount monitor(s)"

if ($monitorCount -eq 0) {
    Write-Host "No monitors detected. Please check your display settings and try again."
    exit
}

# Create a string to hold multiple wallpaper paths
$wallpaperPaths = @()

for ($i = 0; $i -lt $monitorCount; $i++) {
    $randomWallpaper = $wallpapers | Get-Random
    if (Test-Path $randomWallpaper.FullName) {
        $wallpaperPaths += $randomWallpaper.FullName
        Write-Host "Selected wallpaper for monitor $($i+1): $($randomWallpaper.FullName)"
    } else {
        Write-Host "Error: Selected wallpaper does not exist: $($randomWallpaper.FullName)"
    }
}

if ($wallpaperPaths.Count -eq 0) {
    Write-Host "No valid wallpapers were selected. Exiting."
    exit
}

# Join the wallpaper paths with a semicolon
$multiMonitorWallpaper = $wallpaperPaths -join ";"

# Set the background type to Picture
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name WallpaperStyle -Value 10
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name TileWallpaper -Value 0

# Ensure the PersonalizationCSP key exists
$PersonalizationCSP = "HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion\PersonalizationCSP"
if (!(Test-Path $PersonalizationCSP)) {
    New-Item -Path $PersonalizationCSP -Force | Out-Null
}

# Set the wallpaper using PersonalizationCSP
Set-ItemProperty -Path $PersonalizationCSP -Name DesktopImagePath -Value $multiMonitorWallpaper
Set-ItemProperty -Path $PersonalizationCSP -Name DesktopImageUrl -Value $multiMonitorWallpaper
Set-ItemProperty -Path $PersonalizationCSP -Name LockScreenImagePath -Value $multiMonitorWallpaper
Set-ItemProperty -Path $PersonalizationCSP -Name LockScreenImageUrl -Value $multiMonitorWallpaper

# Set the wallpaper using the traditional method as well
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name Wallpaper -Value $multiMonitorWallpaper

Write-Host "Registry updated with new wallpaper settings"
Write-Host "Wallpaper paths: $multiMonitorWallpaper"

# Refresh the desktop
Set-Wallpaper -path $multiMonitorWallpaper

Write-Host "Wallpaper change process completed"

# Force a refresh
RUNDLL32.EXE USER32.DLL,UpdatePerUserSystemParameters ,1 ,True
</antArtifact>

This updated script does the following:

1. It explicitly sets the `WallpaperStyle` to 10 and `TileWallpaper` to 0, which should ensure the background type is set to "Picture."
2. It uses both the traditional method of setting the wallpaper (through the "Control Panel\Desktop" registry key) and the newer PersonalizationCSP method, which is more reliable in some versions of Windows 10 and 11.
3. It forces a refresh of the desktop settings at the end.

To use this updated script:

1. Save it as `Change-Wallpaper-MultiMonitor.ps1` in your scripts directory.
2. Run it in PowerShell with administrator privileges:

```powershell
powershell.exe -ExecutionPolicy Bypass -File "C:\Users\blake\scripts\Change-Wallpaper-MultiMonitor.ps1"
```

If you're using this with AutoHotkey, make sure your AutoHotkey script is also running with administrator privileges.

This should resolve the issue with the background type being set to "Solid color." Let me know if this works or if you encounter any other issues.

---

**Human** - 2024-10-15 23:13:36 UTC

i think i might be onto something.. the reason my backgrounds are black is we managed to flip the windows setting from "picture" to "solid color" for background image

---

