---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Maintaining Audio Output When Monitor Powers Down

Created: 2024-10-13 15:41:20 UTC
Updated: 2024-10-13 16:32:43 UTC
UUID: e6e70434-dedd-4d45-9789-03c75dca6855
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-10-13 15:41:28 UTC

i have a bit of a unique use case on a computer setup that i have and i think i'm running into one of it's limitations. 

i'm utilizing the audio out on one of my monitors in order to have speakers on my desktop (using audio from the motherboard isn't an option as this is technically a proxmox server, but i'm using a vm with the gpu passed through to emulate a desktop environment.)

when spotify is playing, or audio in general, i suppose. the screen going into power saving mode causes audio to stop.. 

how might i work around this?

---

**Assistant** - 2024-10-13 15:41:28 UTC

 This is indeed a unique setup, and the behavior you're experiencing is likely due to the monitor's power-saving mode affecting both the display and audio output. Here are a few potential workarounds you could try:

1. Disable monitor power-saving:
   You could disable the power-saving feature for your monitor in your VM's display settings. This would prevent the screen from turning off, but it might increase power consumption.

2. Use a virtual audio cable:
   Install a virtual audio cable software in your VM. This would create a virtual audio device that doesn't depend on the physical monitor. You could then route your audio through this virtual device to your monitor's speakers.

3. External audio device:
   If possible, consider using a USB audio adapter or a small USB DAC (Digital-to-Analog Converter) connected directly to your VM. This would bypass the monitor's audio system entirely.

4. Adjust EDID settings:
   Some GPUs allow you to modify the EDID (Extended Display Identification Data) of the monitor. You might be able to tell the GPU that the monitor doesn't support power saving, which could prevent this behavior.

5. Custom script:
   Write a script that periodically "wakes up" the monitor or sends a signal to prevent it from entering power-saving mode.

6. Use a different audio output in Proxmox:
   If possible, you could pass through a different audio device from your Proxmox host to the VM, rather than relying on the GPU's audio.

Would you like me to elaborate on any of these options? Also, could you provide more details about your specific hardware (GPU model, monitor model) and the operating system of your VM? This information might help in suggesting more targeted solutions.

---

**Human** - 2024-10-13 15:42:47 UTC

i've seen bits about these virtual cables. i like the sound of that.

---

**Assistant** - 2024-10-13 15:42:47 UTC

 Virtual audio cables are indeed a useful solution for complex audio routing scenarios like yours. They create a virtual audio device that can act as both an output and input, allowing you to route audio between applications or, in your case, potentially bypass the monitor's power-saving audio cutoff.

Here's a basic overview of how you could set this up:

1. Choose a virtual audio cable software:
   - For Windows: VB-Cable or Virtual Audio Cable
   - For Linux: PulseAudio already has this functionality built-in, or you could use JACK
   - For macOS: BlackHole or Loopback

2. Install the software in your VM.

3. Configure your audio output:
   Set your system or application (like Spotify) to output audio to the virtual cable instead of your monitor.

4. Configure your audio input:
   Set your monitor's audio input to listen to the virtual cable.

This setup creates a digital audio "loop" that doesn't depend on your monitor's power state.

Would you like me to walk you through the setup process for a specific operating system? If so, which OS is your VM running?

Also, keep in mind that while this solution should work in theory, there's a small chance that your monitor might still cut off audio input when it goes into power-saving mode. If that happens, we might need to explore other options or combine this with one of the other solutions mentioned earlier.

---

**Assistant** - 2024-10-13 15:59:16 UTC

 Alright, let's walk through setting up a virtual audio cable on your Windows VM. We'll use VB-Cable, which is free and relatively simple to set up.

Here's a step-by-step guide:

1. Download VB-Cable:
   Go to the VB-Audio website (https://vb-audio.com/Cable/) and download the VB-Cable driver.

2. Install VB-Cable:
   - Extract the downloaded zip file.
   - Run the VBCABLE_Setup_x64.exe (for 64-bit systems) or VBCABLE_Setup.exe (for 32-bit systems) as administrator.
   - Follow the installation prompts. You may need to restart your VM after installation.

3. Configure Windows to use VB-Cable:
   - Right-click the speaker icon in your system tray and select "Open Sound settings".
   - Under "Choose your output device", select "CABLE Input (VB-Audio Virtual Cable)".

4. Configure your applications:
   - In Spotify or other audio applications, go to the audio settings and select "CABLE Input (VB-Audio Virtual Cable)" as the output device.

5. Route VB-Cable to your monitor's speakers:
   - In Windows Sound settings, go to "App volume and device preferences".
   - Find "CABLE Output" in the list and set its output to your monitor's speakers.

6. Test the setup:
   Play some audio in Spotify or another application. You should hear it through your monitor's speakers, even when the display goes into power-saving mode.

If you're still experiencing issues after this setup, we might need to look into additional solutions, such as:

1. Using a tool like NirCmd to prevent your monitor from entering power-saving mode.
2. Creating a scheduled task in Windows to periodically "wake" the monitor.
3. Adjusting your GPU's EDID settings to ignore monitor power-saving commands.

Would you like more information on any of these additional steps? Also, please let me know if you encounter any issues during the VB-Cable setup process.

---

**Human** - 2024-10-13 15:59:16 UTC

this is on a windows VM, so...

---

**Assistant** - 2024-10-13 16:24:54 UTC

 You're right, and I apologize for suggesting an overly complex solution. Let's take a step back and consider simpler approaches that are more accessible within a standard Windows environment. Here are some easier options to try:

1. Adjust Power Settings:
   - Right-click on your desktop and select "Display settings"
   - Scroll down and click on "Power & sleep"
   - Under "Screen", set "When plugged in, turn off after" to "Never"

   This will prevent your display from going into sleep mode, which should keep the audio playing.

2. Use Windows' Built-in Focus Assist:
   - Open Settings (Windows key + I)
   - Go to "System" > "Focus assist"
   - Turn on "Alarms only" or "Priority only"
   - This might keep some background processes more active

3. Change Multimedia Settings:
   - Right-click the speaker icon in the taskbar
   - Select "Open Sound settings"
   - Scroll down and click "App volume and device preferences"
   - Ensure your audio apps are set to your preferred output device

4. Run a Small Application:
   You could run a simple application that prevents sleep mode. For example, "Mouse Jiggler" is a tiny program that simulates mouse movement to keep your system active.

5. Windows Power Plan:
   - Right-click the battery icon in the taskbar and select "Power Options"
   - Click "Additional power settings"
   - Select "High performance" or create a custom plan
   - In plan settings, ensure "Turn off the display" is set to "Never"

6. Check Monitor Settings:
   Some monitors have their own power-saving settings. Check your monitor's on-screen display menu to see if there are audio-related sleep settings you can adjust.

Would you like to try one of these approaches? They're much more straightforward and don't require installing additional software or making complex system changes. Let me know which one you'd prefer to start with, and I can provide more detailed steps if needed.

---

**Human** - 2024-10-13 16:24:54 UTC

let's rethink our approach here a little bit.. that all seems VERY granular for what i will and will not have access to in windows.

---

**Assistant** - 2024-10-13 16:27:14 UTC

 I apologize for the confusion earlier. You're right, and I appreciate your clarification. Let's focus on a more realistic and straightforward setup for VB-Cable in Windows. Here's a simplified, step-by-step guide:

1. Download and Install VB-Cable:
   - Go to https://vb-audio.com/Cable/
   - Download the VB-Cable driver
   - Run the installer as administrator
   - Restart your computer if prompted

2. Set VB-Cable as your Default Playback Device:
   - Right-click the speaker icon in your taskbar
   - Select "Open Sound settings"
   - Under "Choose your output device", select "CABLE Input (VB-Audio Virtual Cable)"

3. Set your Monitor's Audio as the Default Recording Device:
   - In the same Sound settings window, click "Sound Control Panel" on the right
   - Go to the "Recording" tab
   - Right-click on "CABLE Output" and select "Properties"
   - Go to the "Listen" tab
   - Check "Listen to this device"
   - In the dropdown under "Playback through this device", select your monitor's audio output
   - Click "Apply" and then "OK"

4. Test the Setup:
   - Play some audio from any source (e.g., YouTube in a web browser)
   - You should hear the audio through your monitor's speakers

This setup creates a virtual audio path:
Your apps -> VB-Cable Input -> VB-Cable Output -> Your monitor's speakers

The key here is that Windows is always "listening" to the VB-Cable output and sending it to your monitor's speakers, regardless of the monitor's power state.

If you're still having issues:
1. Make sure your monitor's audio device is enabled:
   - In Sound settings, under "Output", make sure your monitor's audio device is listed and enabled
2. Check Windows audio levels:
   - Open Volume Mixer (right-click speaker icon > Open Volume Mixer)
   - Ensure levels are up for both system sounds and individual apps

Let me know if this works better for you or if you need any clarification on these steps.

---

**Human** - 2024-10-13 16:27:14 UTC

sorry. let me clarify. 

i like the idea of using VB Cable. but getting it to behave properly isn't seeming to add up. and several of the setting you mentioned dont exist (setting audio outputs inside of apps? not happening. "routing"  audio to my monitor's output? I wish.)

a more detailed and more realistic setup scenario for VB Cable is what i'm after.

---

**Human** - 2024-10-13 16:32:08 UTC

Ah. My brain (and subsequently the setup on my computer) seems to have grasped it that time. thank you! 

I knew it had to be something like this, was just unable to navigate the settings on my own.

---

**Assistant** - 2024-10-13 16:32:08 UTC

 I'm glad to hear that it clicked for you this time! Sometimes it just takes the right explanation to make things fall into place. You're absolutely right that navigating audio settings can be tricky, especially in unique setups like yours.

Now that you have it working, here are a few quick tips:

1. If you ever need to temporarily switch back to direct audio output, you can quickly change the default playback device in the Windows sound settings.

2. Keep an eye on your audio levels. Sometimes using virtual audio devices can affect volume, so you might need to adjust your levels in Windows or on your monitor.

3. If you update Windows or your graphics drivers, you might need to reconfigure these settings, as updates can sometimes reset audio configurations.

Is there anything else you'd like to know about this setup or any other aspects of your audio configuration?

---

**Human** - 2024-10-13 16:32:43 UTC

well, now i've got to wait til the screen turns off and see if it really did the trick. haha

---

**Assistant** - 2024-10-13 16:32:43 UTC

 You're absolutely right! The real test comes when the screen goes into power-saving mode. It's a good idea to verify that the solution actually solves the problem you were experiencing.

Here are a few suggestions to test it thoroughly:

1. Play some continuous audio (like a long YouTube video or a playlist on a music streaming service).

2. Let your screen go into power-saving mode naturally, or you can force it by:
   - Pressing Windows Key + X, selecting "Power Options", then "Choose when to turn off the display", and temporarily setting a short time for testing.

3. Wait a minute or two after the screen goes off to ensure the audio keeps playing.

4. If possible, test this a few times to make sure it's consistently working.

If you find that it doesn't work as expected, don't hesitate to come back and describe what's happening. We can then troubleshoot further or explore other potential solutions.

In the meantime, I hope this setup proves to be the solution you were looking for! Let me know how the test goes when you have a chance to try it out.

---

