---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Setting Up Asus Zenbook 14 with External Monitor and Wireless Keyboard

Created: 2024-10-17 14:02:18 UTC
Updated: 2024-10-17 16:09:28 UTC
UUID: 408413d4-e82d-4c32-8a28-9a91c41730db
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Assistant** - 2024-10-17 14:02:30 UTC

 As your IT technician, I'll guide you through setting up your Asus Zenbook 14 with an external monitor and keyboard on Hyprland/Arch Linux. Here's a step-by-step process:

1. Connect the hardware:
   - Connect your KTC monitor to your laptop using an appropriate cable (likely HDMI or USB-C, depending on your laptop's ports).
   - Plug the wireless keyboard and mouse dongle into a USB port on the monitor.
   - Power on the monitor.

2. Detect the external display:
   - Open a terminal and run:
     ```
     hyprctl monitors
     ```
   This will show you the connected displays and their names.

3. Configure Hyprland:
   - Edit your Hyprland configuration file, usually located at `~/.config/hypr/hyprland.conf`
   - Add a monitor configuration line. For example:
     ```
     monitor=HDMI-A-1,2560x1440@60,0x0,1
     ```
   Replace HDMI-A-1 with the actual name of your monitor from step 2, and adjust the resolution and refresh rate as needed.

4. Set up multi-monitor layout:
   - In the same config file, you can set up your preferred layout. For example, to set the external monitor as your primary display:
     ```
     workspace=HDMI-A-1,1
     ```

5. Configure input devices:
   - Hyprland should automatically detect your new input devices. If not, you may need to add them manually in the config file:
     ```
     input {
         kb_layout = us
         follow_mouse = 1
         sensitivity = 0
     }
     ```

6. Restart Hyprland:
   - Save your configuration file and restart Hyprland to apply changes. You can do this by logging out and back in, or by running:
     ```
     hyprctl reload
     ```

7. Fine-tune display settings:
   - Use `wlr-randr` to adjust display settings if needed:
     ```
     wlr-randr --output HDMI-A-1 --mode 2560x1440 --rate 60
     ```

8. Test your setup:
   - Move your cursor between displays to ensure they're working correctly.
   - Test your wireless keyboard and mouse to ensure they're recognized.

If you encounter any issues or need to make adjustments, let me know, and I'll be happy to help you troubleshoot or fine-tune your setup.

---

**Human** - 2024-10-17 14:02:30 UTC

Acting as my IT technician please help me set up my laptop with an external monitor and keyboard. 

My laptop is an Asus zenbook 14 (I don't recall the exact model, but the processor is an AMD 6800h). It's running hyprland on archlinux. 

My monitor is by ktc, the exact model escapes me but I believe it's m2720 or at least includes those digits. My plan is to have a wireless keyboard and mouse dongle plugged into the monitor.

---

**Human** - 2024-10-17 14:05:26 UTC

My monitors look like this:

eDP-1,2560x1800@90,-2560x0,1.333333

DP-1,2560x1440@144,0x0,1.6

I believe this sets the laptop (eDP-1) on the left?)

---

**Assistant** - 2024-10-17 14:05:26 UTC

 Thank you for providing that information. You're correct in your interpretation. Let's break down what this configuration means:

1. eDP-1 (Your laptop screen):
   - Resolution: 2560x1800
   - Refresh rate: 90Hz
   - Position: -2560x0 (This places it to the left of the origin point)
   - Scale: 1.333333

2. DP-1 (Your external KTC monitor):
   - Resolution: 2560x1440
   - Refresh rate: 144Hz
   - Position: 0x0 (This places it at the origin point, which is to the right of your laptop screen)
   - Scale: 1.6

So yes, this configuration sets your laptop screen (eDP-1) on the left and your external monitor (DP-1) on the right. The negative X-coordinate for the laptop screen (-2560) positions it to the left of the external monitor.

To reflect this in your Hyprland configuration, you could add these lines to your `hyprland.conf` file:

```
monitor=eDP-1,2560x1800@90,-2560x0,1.333333
monitor=DP-1,2560x1440@144,0x0,1.6
```

This setup should give you a dual-monitor configuration with your laptop screen on the left and your external monitor on the right. The external monitor is set as the primary display (at the 0,0 coordinate).

If you want to change this arrangement or make any adjustments, let me know, and I can help you modify the configuration accordingly.

---

**Human** - 2024-10-17 14:06:11 UTC

Now, to confirm, a usb-c cable will suffice for this laptop model?

---

**Assistant** - 2024-10-17 14:06:11 UTC

 For an Asus Zenbook 14 with an AMD 6800H processor, a USB-C cable should indeed suffice for connecting to an external monitor, but there are a few things to consider:

1. USB-C port capabilities: Most modern Asus Zenbook models, especially those with high-end processors like the AMD 6800H, typically come with USB-C ports that support DisplayPort Alternate Mode. This allows video output through the USB-C port.

2. Cable requirements: You'll need a USB-C cable that supports video output. Not all USB-C cables can carry video signals. Look for cables labeled as "USB-C to DisplayPort" or "Thunderbolt 3/4" cables, as these are guaranteed to support video output.

3. Monitor input: Ensure your KTC monitor has a USB-C input that supports DisplayPort Alt Mode. If it doesn't, you might need an adapter (USB-C to HDMI or USB-C to DisplayPort).

4. Power delivery: Some USB-C connections can also provide power to your laptop. If your monitor supports USB-C Power Delivery, you might be able to charge your laptop through the same cable that carries the video signal.

5. Bandwidth: USB-C can support high resolutions and refresh rates, but there are limits. Your setup (2560x1440@144Hz) should be within these limits for most modern USB-C implementations.

To confirm with absolute certainty, you could check the specific model number of your Asus Zenbook 14 and verify the USB-C port specifications in the user manual or on Asus's website.

If you have a USB-C cable available, the easiest way to confirm is simply to try connecting your laptop to the monitor with it. If it works, you'll see your display output on the external monitor.

---

**Human** - 2024-10-17 14:08:12 UTC

I'm fairly certain both usb-c ports are usb4 (not thunderbolt, although it sort of worked well with an egpu I had for a while) 

What steps would I need to take, bios, os, hardware settings to ensure this connection exists and is functioning correctly?

---

**Assistant** - 2024-10-17 14:08:12 UTC

 Given that your Asus Zenbook 14 likely has USB4 ports, which are backward compatible with USB 3.2 and Thunderbolt 3, you should be able to use these for your external monitor connection. Here are the steps to ensure the connection is set up and functioning correctly:

1. Hardware Setup:
   - Connect your USB-C cable from your laptop to the monitor.
   - Ensure the monitor is powered on and set to the correct input.

2. BIOS Settings:
   - Restart your laptop and enter the BIOS (usually by pressing F2 or Del during startup).
   - Look for settings related to Thunderbolt, USB4, or USB-C and ensure they are enabled.
   - If there's an option for "DP Alt Mode" or "DisplayPort over USB-C", make sure it's enabled.
   - Save and exit BIOS.

3. OS (Arch Linux) Settings:
   - Once booted, open a terminal and check if the system detects the monitor:
     ```
     xrandr --listmonitors
     ```
     or for Wayland:
     ```
     wlr-randr
     ```

4. Hyprland Configuration:
   - Ensure your Hyprland config (usually `~/.config/hypr/hyprland.conf`) has the correct monitor settings as we discussed earlier.

5. Graphics Drivers:
   - Ensure your AMD graphics drivers are up to date:
     ```
     sudo pacman -Syu
     ```
   - If you're using the open-source AMD drivers (which is likely), they should be part of the kernel. If not:
     ```
     sudo pacman -S xf86-video-amdgpu
     ```

6. USB4/Thunderbolt Support:
   - Install the Thunderbolt user-space components:
     ```
     sudo pacman -S bolt
     ```
   - Enable and start the bolt service:
     ```
     sudo systemctl enable --now bolt.service
     ```

7. Check USB4 Status:
   - Install the USB utils if not already present:
     ```
     sudo pacman -S usbutils
     ```
   - Check USB device info:
     ```
     lsusb -t
     ```
   - For more detailed info on USB4 ports:
     ```
     sudo lsusb -v | less
     ```
     Look for entries related to USB4 or Thunderbolt.

8. DisplayPort Alt Mode:
   - To check if DisplayPort Alt Mode is active:
     ```
     sudo dmesg | grep -i "dp alt"
     ```

9. Testing the Connection:
   - If everything is set up correctly, your external monitor should be detected automatically.
   - You can test it using the Hyprland command:
     ```
     hyprctl monitors
     ```
   - This should list both your laptop display and the external monitor.

10. Troubleshooting:
    - If the monitor isn't detected, try unplugging and replugging the USB-C cable.
    - Check if the issue persists with a different USB-C cable.
    - Ensure your monitor's firmware is up to date.

If you encounter any specific errors or issues during this process, please let me know, and I'll be happy to help you troubleshoot further.

---

**Human** - 2024-10-17 14:09:09 UTC

Come to think of it. hyprctl monitors found it. That should be proof enough that the connection is established..

---

**Assistant** - 2024-10-17 14:09:09 UTC

 You're absolutely right. If `hyprctl monitors` is detecting your external monitor, that's indeed strong evidence that the connection is established and functioning correctly. Let's break this down:

1. Connection Confirmation: The fact that Hyprland can see the monitor means that:
   - The physical connection (USB-C cable) is working.
   - The operating system (Arch Linux) has recognized the display.
   - The display server (Wayland) is aware of the monitor.
   - Hyprland, your window manager, can interact with the display.

2. Next Steps: Since the connection is established, you can focus on optimizing your setup:
   - Ensure the monitor settings (resolution, refresh rate) are as you desire.
   - Configure your preferred layout in Hyprland.
   - Set up any specific workspaces or window rules you want for the external display.

3. Potential Optimizations: You might want to check:
   - Is the refresh rate set to 144Hz as your monitor supports?
   - Is the scaling factor (1.6 as we saw earlier) comfortable for you?

4. Using the Setup: With the connection confirmed, you can now use Hyprland's commands to manage your displays. For example:
   - To move the focused window to the external monitor: 
     ```
     hyprctl dispatch movetoworkspace <workspace_on_external_monitor>
     ```
   - To switch focus between monitors:
     ```
     hyprctl dispatch focusmonitor <monitor_name>
     ```

5. Performance: If you're satisfied with the image quality and performance, there's no need for further hardware-level troubleshooting.

You're correct in your assessment - the `hyprctl monitors` output is a reliable indicator that your connection is working as intended. Unless you're experiencing any specific issues with display quality, input lag, or other performance metrics, you can consider your setup successful.

Is there anything specific about the monitor setup you'd like to adjust or optimize further?

---

**Human** - 2024-10-17 15:57:00 UTC

can you help me troubleshoot connectivity issues with the wirelss donlgled periferals? they keep cutting out. 

much more than one would expect. steps taken: devices are charged, within range, and function as intended on other devices, even other operating systems on the same setup

---

**Assistant** - 2024-10-17 15:57:00 UTC

 Certainly, I can help you troubleshoot the connectivity issues with your wireless dongled peripherals. Given that you've already confirmed the devices are charged, within range, and working on other devices/operating systems, we'll focus on potential software and system-level issues. Let's go through some steps to diagnose and potentially resolve the problem:

1. Check USB Power Management:
   Linux sometimes aggressively manages USB power, which can cause issues with wireless dongles. Try disabling USB autosuspend:

   ```
   echo '2-1' | sudo tee /sys/bus/usb/devices/*/power/autosuspend >/dev/null
   ```

   Replace '2-1' with the actual USB port number if known. You can find this by running `lsusb -t`.

2. Update the kernel and firmware:
   Ensure your system is fully updated:
   ```
   sudo pacman -Syu
   ```

3. Check for interference:
   - Try different USB ports on your monitor or laptop.
   - Move potential sources of interference (like external hard drives or phones) away from the dongle.

4. Examine kernel logs:
   Look for any USB or wireless peripheral related errors:
   ```
   dmesg | grep -i 'usb\|wireless\|mouse\|keyboard'
   ```

5. Install and run USB utils:
   ```
   sudo pacman -S usbutils
   lsusb
   ```
   This will show you all connected USB devices. Make sure your dongle is consistently listed.

6. Check for conflicting drivers:
   Sometimes, the generic HID driver can conflict with specific device drivers. You can try unloading and reloading the USB HID driver:
   ```
   sudo modprobe -r usbhid
   sudo modprobe usbhid
   ```

7. Increase USB polling rate:
   You can try increasing the USB polling rate, which might help with responsiveness:
   ```
   echo 1 | sudo tee /sys/module/usbhid/parameters/mousepoll
   ```

8. Use a different USB controller:
   If your laptop has multiple USB controllers, try connecting the dongle to a port on a different controller.

9. Check for power saving features:
   Disable any aggressive power saving features in your laptop's BIOS/UEFI settings that might be affecting USB performance.

10. Test with a different dongle:
    If possible, try a different wireless dongle to rule out hardware issues.

11. Monitor USB events:
    Run this command and then use your devices. Watch for any disconnect events:
    ```
    sudo usbmon
    ```

12. Consider using a USB hub:
    Sometimes, using a powered USB hub can provide more stable power to the dongle and improve connectivity.

13. Check for firmware updates:
    Look for any available firmware updates for your wireless peripherals or their dongles.

If none of these steps resolve the issue, we might need to look into more advanced debugging techniques or consider potential hardware issues with the USB ports or the dongle itself. Let me know the results of these steps, and we can proceed from there.

---

**Human** - 2024-10-17 15:58:35 UTC

lsusb output from step 1:

/:  Bus 001.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/4p, 480M
    |__ Port 003: Dev 002, If 0, Class=Vendor Specific Class, Driver=[none], 12M
    |__ Port 004: Dev 003, If 0, Class=Wireless, Driver=btusb, 480M
    |__ Port 004: Dev 003, If 1, Class=Wireless, Driver=btusb, 480M
    |__ Port 004: Dev 003, If 2, Class=Wireless, Driver=btusb, 480M
/:  Bus 002.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/2p, 10000M
/:  Bus 003.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/3p, 480M
/:  Bus 004.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/2p, 10000M
/:  Bus 005.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/1p, 480M
    |__ Port 001: Dev 002, If 0, Class=Video, Driver=uvcvideo, 480M
    |__ Port 001: Dev 002, If 1, Class=Video, Driver=uvcvideo, 480M
    |__ Port 001: Dev 002, If 2, Class=Application Specific Interface, Driver=[none], 480M
/:  Bus 006.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/0p, 5000M
/:  Bus 007.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/1p, 480M
/:  Bus 008.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/1p, 10000M
/:  Bus 009.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/1p, 480M
    |__ Port 001: Dev 002, If 0, Class=Hub, Driver=hub/4p, 480M
        |__ Port 001: Dev 065, If 0, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 001: Dev 065, If 1, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 001: Dev 065, If 2, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 004: Dev 066, If 0, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 004: Dev 066, If 1, Class=Human Interface Device, Driver=usbhid, 12M
/:  Bus 010.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/1p, 10000M

---

**Assistant** - 2024-10-17 15:58:35 UTC

 Thank you for providing the `lsusb` output. This is very helpful. From this information, we can see that your wireless peripherals are connected through a USB hub on Bus 009, Port 001. Let's analyze this and proceed with some targeted troubleshooting:

1. USB Hub:
   Your wireless devices are connected through a USB hub (Dev 002 on Bus 009). This hub is operating at USB 2.0 speeds (480M).

2. Wireless Devices:
   - Device 065: Likely your keyboard or mouse, with three interfaces.
   - Device 066: Probably another peripheral (mouse or keyboard) with two interfaces.

Both devices are operating at low speed (12M), which is typical for many wireless keyboard and mouse setups.

Given this information, let's try some targeted solutions:

1. USB Hub Power:
   The hub might not be providing enough power. Try connecting the hub to a powered USB port on your monitor or use a powered USB hub.

2. Disable USB Autosuspend for the hub and devices:
   ```
   echo -1 | sudo tee /sys/bus/usb/devices/9-1/power/autosuspend_delay_ms
   echo -1 | sudo tee /sys/bus/usb/devices/9-1.1/power/autosuspend_delay_ms
   echo -1 | sudo tee /sys/bus/usb/devices/9-1.4/power/autosuspend_delay_ms
   ```

3. Increase USB polling rate for these specific devices:
   ```
   echo 1 | sudo tee /sys/bus/usb/devices/9-1.1/power/control
   echo 1 | sudo tee /sys/bus/usb/devices/9-1.4/power/control
   ```

4. Check for USB errors:
   Run this command and watch for any errors related to Bus 009:
   ```
   dmesg | grep -i 'usb'
   ```

5. Try different USB ports:
   Connect the hub to a different USB port, preferably one directly on your laptop rather than the monitor.

6. Update usbhid driver:
   Ensure you have the latest usbhid driver:
   ```
   sudo pacman -S linux-headers
   sudo modprobe -r usbhid
   sudo modprobe usbhid
   ```

7. Monitor USB events in real-time:
   Run this command and then use your devices. Watch for any disconnect events:
   ```
   sudo usbmon | grep -E "9-1.1|9-1.4"
   ```

8. Check USB power output:
   You can check the power output of your USB ports:
   ```
   for i in /sys/bus/usb/devices/*/power/autosuspend; do echo $i; cat $i; done
   ```
   Look for any unusually low values.

9. Disable USB 3.0 in BIOS:
   Sometimes, USB 3.0 can cause interference with 2.4 GHz wireless devices. Try disabling USB 3.0 in your BIOS settings temporarily to see if it helps.

10. Update firmware:
    Check if there are any firmware updates available for your USB hub or wireless peripherals.

After trying these steps, please let me know if you notice any improvement or if you encounter any specific error messages. We may need to dive deeper into kernel logs or driver configurations if the issue persists.

---

**Human** - 2024-10-17 16:02:26 UTC

dmesg (required sudo) output:


Attachments:
- {'file_name': 'paste.txt', 'file_size': 10577, 'file_type': 'txt', 'extracted_content': '2.101772] usb 9-1.1: Product: USB Receiver\n[ 8332.101777] usb 9-1.1: Manufacturer: Logitech\n[ 8332.231630] logitech-djreceiver 0003:046D:C52B.00BE: hiddev96,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:65:00.4-1.1/input2\n[ 8332.352549] input: Logitech MX Master 2S as /devices/pci0000:00/0000:00:08.3/0000:65:00.4/usb9/9-1/9-1.1/9-1.1:1.2/0003:046D:C52B.00BE/0003:046D:4069.00BF/input/input198\n[ 8332.467615] usb 9-1.4: new full-speed USB device number 66 using xhci_hcd\n[ 8332.474982] logitech-hidpp-device 0003:046D:4069.00BF: input,hidraw4: USB HID v1.11 Keyboard [Logitech MX Master 2S] on usb-0000:65:00.4-1.1/input2:1\n[ 8332.626703] usb 9-1.4: New USB device found, idVendor=25a7, idProduct=fa70, bcdDevice= 3.00\n[ 8332.626713] usb 9-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0\n[ 8332.626717] usb 9-1.4: Product: 2.4G Wireless Receiver\n[ 8332.626720] usb 9-1.4: Manufacturer: Compx\n[ 8332.724845] input: Compx 2.4G Wireless Receiver as /devices/pci0000:00/0000:00:08.3/0000:65:00.4/usb9/9-1/9-1.4/9-1.4:1.0/0003:25A7:FA70.00C0/input/input199\n[ 8332.877247] hid-generic 0003:25A7:FA70.00C0: input,hidraw5: USB HID v1.10 Keyboard [Compx 2.4G Wireless Receiver] on usb-0000:65:00.4-1.4/input0\n[ 8332.885036] input: Compx 2.4G Wireless Receiver Mouse as /devices/pci0000:00/0000:00:08.3/0000:65:00.4/usb9/9-1/9-1.4/9-1.4:1.1/0003:25A7:FA70.00C1/input/input200\n[ 8332.885264] input: Compx 2.4G Wireless Receiver as /devices/pci0000:00/0000:00:08.3/0000:65:00.4/usb9/9-1/9-1.4/9-1.4:1.1/0003:25A7:FA70.00C1/input/input201\n[ 8332.885396] input: Compx 2.4G Wireless Receiver Keyboard as /devices/pci0000:00/0000:00:08.3/0000:65:00.4/usb9/9-1/9-1.4/9-1.4:1.1/0003:25A7:FA70.00C1/input/input202\n[ 8332.941357] hid-generic 0003:25A7:FA70.00C1: input,hiddev97,hidraw6: USB HID v1.10 Mouse [Compx 2.4G Wireless Receiver] on usb-0000:65:00.4-1.4/input1\n[ 8517.886495] usb 9-1-port1: cannot reset (err = -71)\n[ 8517.886850] usb 9-1-port1: cannot reset (err = -71)\n[ 8517.887349] usb 9-1-port1: cannot reset (err = -71)\n[ 8517.887723] usb 9-1-port1: cannot reset (err = -71)\n[ 8517.888094] usb 9-1-port1: cannot reset (err = -71)\n[ 8517.888095] usb 9-1-port1: Cannot enable. Maybe the USB cable is bad?\n[ 8517.888477] usb 9-1-port1: cannot disable (err = -71)\n[ 8517.888848] usb 9-1-port1: cannot reset (err = -71)\n[ 8517.889218] usb 9-1-port1: cannot reset (err = -71)\n[ 8517.889593] usb 9-1-port1: cannot reset (err = -71)\n[ 8517.889968] usb 9-1-port1: cannot reset (err = -71)\n[ 8517.890354] usb 9-1-port1: cannot reset (err = -71)\n[ 8517.890356] usb 9-1-port1: Cannot enable. Maybe the USB cable is bad?\n[ 8517.890730] usb 9-1-port1: cannot disable (err = -71)\n[ 8517.891096] usb 9-1-port1: cannot reset (err = -71)\n[ 8517.891468] usb 9-1-port1: cannot reset (err = -71)\n[ 8517.891843] usb 9-1-port1: cannot reset (err = -71)\n[ 8517.892218] usb 9-1-port1: cannot reset (err = -71)\n[ 8517.892595] usb 9-1-port1: cannot reset (err = -71)\n[ 8517.892598] usb 9-1-port1: Cannot enable. Maybe the USB cable is bad?\n[ 8517.892970] usb 9-1-port1: cannot disable (err = -71)\n[ 8517.893354] usb 9-1-port1: cannot reset (err = -71)\n[ 8517.893943] usb 9-1-port1: cannot reset (err = -71)\n[ 8517.894230] usb 9-1-port1: cannot reset (err = -71)\n[ 8517.894596] usb 9-1-port1: cannot reset (err = -71)\n[ 8517.894971] usb 9-1-port1: cannot reset (err = -71)\n[ 8517.894973] usb 9-1-port1: Cannot enable. Maybe the USB cable is bad?\n[ 8517.895360] usb 9-1-port1: cannot disable (err = -71)\n[ 8517.895719] usb 9-1-port1: cannot disable (err = -71)\n[ 8517.896096] usb 9-1-port4: cannot reset (err = -71)\n[ 8517.896854] usb 9-1-port4: cannot reset (err = -71)\n[ 8517.897614] usb 9-1-port4: cannot reset (err = -71)\n[ 8517.897973] usb 9-1-port4: cannot reset (err = -71)\n[ 8517.898350] usb 9-1-port4: cannot reset (err = -71)\n[ 8517.898352] usb 9-1-port4: Cannot enable. Maybe the USB cable is bad?\n[ 8517.898716] usb 9-1-port4: cannot disable (err = -71)\n[ 8517.899103] usb 9-1-port4: cannot reset (err = -71)\n[ 8517.899471] usb 9-1-port4: cannot reset (err = -71)\n[ 8517.899834] usb 9-1-port4: cannot reset (err = -71)\n[ 8517.900216] usb 9-1-port4: cannot reset (err = -71)\n[ 8517.900662] usb 9-1-port4: cannot reset (err = -71)\n[ 8517.900665] usb 9-1-port4: Cannot enable. Maybe the USB cable is bad?\n[ 8517.900973] usb 9-1-port4: cannot disable (err = -71)\n[ 8517.901346] usb 9-1-port4: cannot reset (err = -71)\n[ 8517.901729] usb 9-1-port4: cannot reset (err = -71)\n[ 8517.902096] usb 9-1-port4: cannot reset (err = -71)\n[ 8517.902460] usb 9-1-port4: cannot reset (err = -71)\n[ 8517.902840] usb 9-1-port4: cannot reset (err = -71)\n[ 8517.902841] usb 9-1-port4: Cannot enable. Maybe the USB cable is bad?\n[ 8517.903218] usb 9-1-port4: cannot disable (err = -71)\n[ 8517.903604] usb 9-1-port4: cannot reset (err = -71)\n[ 8517.903980] usb 9-1-port4: cannot reset (err = -71)\n[ 8517.904355] usb 9-1-port4: cannot reset (err = -71)\n[ 8517.904718] usb 9-1-port4: cannot reset (err = -71)\n[ 8517.905101] usb 9-1-port4: cannot reset (err = -71)\n[ 8517.905102] usb 9-1-port4: Cannot enable. Maybe the USB cable is bad?\n[ 8517.905468] usb 9-1-port4: cannot disable (err = -71)\n[ 8517.905845] usb 9-1-port4: cannot disable (err = -71)\n[ 8524.302319] usb 9-1.1: USB disconnect, device number 65\n[ 8524.685928] usb 9-1.4: USB disconnect, device number 66\n[ 8525.358138] usb 9-1: reset high-speed USB device number 2 using xhci_hcd\n[ 8526.260771] usb 9-1.1: new full-speed USB device number 67 using xhci_hcd\n[ 8526.427065] usb 9-1.1: New USB device found, idVendor=046d, idProduct=c52b, bcdDevice=12.11\n[ 8526.427082] usb 9-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0\n[ 8526.427089] usb 9-1.1: Product: USB Receiver\n[ 8526.427094] usb 9-1.1: Manufacturer: Logitech\n[ 8526.561927] logitech-djreceiver 0003:046D:C52B.00C4: hiddev96,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:65:00.4-1.1/input2\n[ 8526.685132] input: Logitech MX Master 2S as /devices/pci0000:00/0000:00:08.3/0000:65:00.4/usb9/9-1/9-1.1/9-1.1:1.2/0003:046D:C52B.00C4/0003:046D:4069.00C5/input/input203\n[ 8526.800444] usb 9-1.4: new full-speed USB device number 68 using xhci_hcd\n[ 8526.808106] logitech-hidpp-device 0003:046D:4069.00C5: input,hidraw4: USB HID v1.11 Keyboard [Logitech MX Master 2S] on usb-0000:65:00.4-1.1/input2:1\n[ 8526.965708] usb 9-1.4: New USB device found, idVendor=25a7, idProduct=fa70, bcdDevice= 3.00\n[ 8526.965718] usb 9-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0\n[ 8526.965722] usb 9-1.4: Product: 2.4G Wireless Receiver\n[ 8526.965726] usb 9-1.4: Manufacturer: Compx\n[ 8527.060664] input: Compx 2.4G Wireless Receiver as /devices/pci0000:00/0000:00:08.3/0000:65:00.4/usb9/9-1/9-1.4/9-1.4:1.0/0003:25A7:FA70.00C6/input/input204\n[ 8527.204496] hid-generic 0003:25A7:FA70.00C6: input,hidraw5: USB HID v1.10 Keyboard [Compx 2.4G Wireless Receiver] on usb-0000:65:00.4-1.4/input0\n[ 8527.212888] input: Compx 2.4G Wireless Receiver Mouse as /devices/pci0000:00/0000:00:08.3/0000:65:00.4/usb9/9-1/9-1.4/9-1.4:1.1/0003:25A7:FA70.00C7/input/input205\n[ 8527.213403] input: Compx 2.4G Wireless Receiver as /devices/pci0000:00/0000:00:08.3/0000:65:00.4/usb9/9-1/9-1.4/9-1.4:1.1/0003:25A7:FA70.00C7/input/input206\n[ 8527.213779] input: Compx 2.4G Wireless Receiver Keyboard as /devices/pci0000:00/0000:00:08.3/0000:65:00.4/usb9/9-1/9-1.4/9-1.4:1.1/0003:25A7:FA70.00C7/input/input207\n[ 8527.271084] hid-generic 0003:25A7:FA70.00C7: input,hiddev97,hidraw6: USB HID v1.10 Mouse [Compx 2.4G Wireless Receiver] on usb-0000:65:00.4-1.4/input1\n[ 8529.436361] usb 9-1-port4: cannot reset (err = -71)\n[ 8529.436736] usb 9-1-port4: cannot reset (err = -71)\n[ 8529.437105] usb 9-1-port4: cannot reset (err = -71)\n[ 8529.437460] usb 9-1-port4: cannot reset (err = -71)\n[ 8529.437843] usb 9-1-port4: cannot reset (err = -71)\n[ 8529.437845] usb 9-1-port4: Cannot enable. Maybe the USB cable is bad?\n[ 8529.438218] usb 9-1-port4: cannot disable (err = -71)\n[ 8529.438593] usb 9-1-port4: cannot reset (err = -71)\n[ 8529.438969] usb 9-1-port4: cannot reset (err = -71)\n[ 8529.439347] usb 9-1-port4: cannot reset (err = -71)\n[ 8529.439738] usb 9-1-port4: cannot reset (err = -71)\n[ 8529.440096] usb 9-1-port4: cannot reset (err = -71)\n[ 8529.440099] usb 9-1-port4: Cannot enable. Maybe the USB cable is bad?\n[ 8529.440472] usb 9-1-port4: cannot disable (err = -71)\n[ 8529.440855] usb 9-1-port4: cannot reset (err = -71)\n[ 8529.441230] usb 9-1-port4: cannot reset (err = -71)\n[ 8529.441604] usb 9-1-port4: cannot reset (err = -71)\n[ 8529.441979] usb 9-1-port4: cannot reset (err = -71)\n[ 8529.442346] usb 9-1-port4: cannot reset (err = -71)\n[ 8529.442348] usb 9-1-port4: Cannot enable. Maybe the USB cable is bad?\n[ 8529.442729] usb 9-1-port4: cannot disable (err = -71)\n[ 8529.443113] usb 9-1-port4: cannot reset (err = -71)\n[ 8529.443480] usb 9-1-port4: cannot reset (err = -71)\n[ 8529.443851] usb 9-1-port4: cannot reset (err = -71)\n[ 8529.444229] usb 9-1-port4: cannot reset (err = -71)\n[ 8529.444604] usb 9-1-port4: cannot reset (err = -71)\n[ 8529.444606] usb 9-1-port4: Cannot enable. Maybe the USB cable is bad?\n[ 8529.444971] usb 9-1-port4: cannot disable (err = -71)\n[ 8529.445347] usb 9-1-port4: cannot disable (err = -71)\n[ 8529.445722] usb 9-1-port1: cannot reset (err = -71)\n[ 8529.446470] usb 9-1-port1: cannot reset (err = -71)\n[ 8529.446845] usb 9-1-port1: cannot reset (err = -71)\n[ 8529.447224] usb 9-1-port1: cannot reset (err = -71)\n[ 8529.447599] usb 9-1-port1: cannot reset (err = -71)\n[ 8529.447601] usb 9-1-port1: Cannot enable. Maybe the USB cable is bad?\n[ 8529.447979] usb 9-1-port1: cannot disable (err = -71)\n[ 8529.448346] usb 9-1-port1: cannot reset (err = -71)\n[ 8529.448720] usb 9-1-port1: cannot reset (err = -71)\n[ 8529.449100] usb 9-1-port1: cannot reset (err = -71)\n[ 8529.449471] usb 9-1-port1: cannot reset (err = -71)\n[ 8529.449846] usb 9-1-port1: cannot reset (err = -71)\n[ 8529.449848] usb 9-1-port1: Cannot enable. Maybe the USB cable is bad?\n[ 8529.450218] usb 9-1-port1: cannot disable (err = -71)\n[ 8529.450590] usb 9-1-port1: cannot reset (err = -71)\n[ 8529.450964] usb 9-1-port1: cannot reset (err = -71)\n[ 8529.451347] usb 9-1-port1: cannot reset (err = -71)\n[ 8529.451729] usb 9-1-port1: cannot reset (err = -71)\n[ 8529.452106] usb 9-1-port1: cannot reset (err = -71)\n[ 8529.452109] usb 9-1-port1: Cannot enable. Maybe the USB cable is bad?\n[ 8529.452472] usb 9-1-port1: cannot disable (err = -71)\n[ 8529.452855] usb 9-1-port1: cannot reset (err = -71)\n[ 8529.453221] usb 9-1-port1: cannot reset (err = -71)'}
- paste.txt

---

**Assistant** - 2024-10-17 16:02:26 UTC

 Thank you for providing the detailed dmesg output. This information is very helpful in diagnosing the issue. After analyzing the log, I can see several problems that are likely causing your wireless peripherals to cut out. Let's break down the issues and propose some solutions:

1. USB Port Reset Failures:
   There are numerous errors like:
   ```
   usb 9-1-port1: cannot reset (err = -71)
   usb 9-1-port1: Cannot enable. Maybe the USB cable is bad?
   ```
   This suggests problems with the USB hub or the ports it's connected to.

2. Device Disconnects and Reconnects:
   Your devices are disconnecting and reconnecting:
   ```
   usb 9-1.1: USB disconnect, device number 65
   usb 9-1.4: USB disconnect, device number 66
   ```

3. Power Issues:
   The error -71 often indicates a power-related problem.

Based on these observations, here are some steps to try:

1. Try a Different USB Port:
   Connect your USB hub to a different USB port on your laptop, preferably one that's directly on the motherboard rather than through the monitor.

2. Use a Powered USB Hub:
   If you're not already using one, try a powered USB hub. This can help if the issue is related to power delivery.

3. Update USB Drivers:
   Ensure your USB drivers are up to date:
   ```
   sudo pacman -Syu
   ```

4. Disable USB Autosuspend:
   Create a file `/etc/udev/rules.d/50-usb-autosuspend.rules` with the following content:
   ```
   ACTION=="add", SUBSYSTEM=="usb", TEST=="power/autosuspend", ATTR{power/autosuspend}="-1"
   ```
   Then reload udev rules:
   ```
   sudo udevadm control --reload-rules && sudo udevadm trigger
   ```

5. Check for USB Conflicts:
   Unplug all other USB devices and see if the problem persists with just your keyboard and mouse.

6. Kernel Parameter:
   Add `usbcore.autosuspend=-1` to your kernel parameters in your bootloader configuration.

7. Check USB Cable:
   The error message suggests the USB cable might be bad. Try replacing the USB cable connecting your hub to the computer.

8. BIOS Settings:
   Check your BIOS settings for any USB-related options. Disable USB power saving features if available.

9. Test with a Live USB:
   Boot from a live USB of a different Linux distribution to see if the problem persists. This can help determine if it's a hardware or software issue.

10. Monitor CPU Usage:
    High CPU usage can sometimes cause USB issues. Monitor your system resources to ensure this isn't the case.

11. Update Firmware:
    Check for any available firmware updates for your Logitech and Compx devices.

After trying these steps, if the issue persists, we might need to look into more advanced debugging or consider potential hardware issues with the USB controller on your laptop. Let me know which steps you try and their outcomes, and we can proceed from there.

---

**Human** - 2024-10-17 16:03:10 UTC

modprobe failed with error usbhid in use

---

**Assistant** - 2024-10-17 16:03:10 UTC

 I apologize for the confusion. The error "usbhid in use" indicates that the usbhid module is currently being used by active USB devices, which prevents it from being unloaded. This is actually expected behavior, especially when you're actively using USB input devices. Let's try a different approach to address your USB issues without unloading the usbhid module.

Here are some alternative steps you can try:

1. Reload the USB modules without unloading usbhid:
   ```
   sudo modprobe -r ehci_hcd xhci_hcd
   sudo modprobe ehci_hcd xhci_hcd
   ```
   This will reload the USB host controller drivers, which might help reset the USB subsystem without affecting your input devices.

2. Adjust USB power management settings:
   Instead of modifying the usbhid module directly, let's try adjusting power management for all USB devices:
   ```
   for i in /sys/bus/usb/devices/*/power/control; do echo on | sudo tee $i; done
   ```
   This command will disable power management for all USB devices.

3. Increase USB debug output:
   To get more information about what's happening with your USB devices, you can increase the debug output:
   ```
   echo 3 | sudo tee /sys/module/usbcore/parameters/usbfs_snoop
   ```
   After doing this, try unplugging and replugging your USB devices, then check the kernel log with `dmesg | tail -n 50`.

4. Check for USB bandwidth issues:
   Sometimes, USB bandwidth problems can cause devices to disconnect. You can check the current USB bandwidth usage with:
   ```
   lsusb -t
   ```
   Look for devices that are using a lot of bandwidth or if there are many high-speed devices on the same controller.

5. Adjust USB polling interval:
   You can try adjusting the polling interval for USB devices. Create a file `/etc/modprobe.d/usbhid.conf` with the following content:
   ```
   options usbhid mousepoll=4
   ```
   Then reload the module configuration:
   ```
   sudo update-initramfs -u
   ```
   You'll need to reboot for this change to take effect.

6. Check for USB autosuspend:
   Even if we've disabled it globally, it's worth checking individual devices:
   ```
   for i in /sys/bus/usb/devices/*/power/autosuspend; do echo $i; cat $i; done
   ```
   If any of these show a value other than -1, you can disable autosuspend for that specific device.

7. Monitor USB events in real-time:
   Run this command and then use your devices. Watch for any disconnect events:
   ```
   sudo usbmon
   ```

After trying these steps, please let me know if you notice any improvement or if you encounter any new error messages. We may need to investigate further based on the results of these actions.

---

**Assistant** - 2024-10-17 16:06:15 UTC

 Thank you for providing the `lsusb -t` output. This gives us a clearer picture of your USB device setup. Let's analyze this information and suggest some targeted solutions:

1. USB Hub Configuration:
   Your wireless devices are connected through a USB hub on Bus 009, Port 001. The hub is operating at USB 2.0 speeds (480M).

2. Wireless Devices:
   - Device 079: Likely your Logitech device (probably the MX Master 2S mouse), with three interfaces.
   - Device 080: Probably your Compx device (keyboard), with two interfaces.

Both devices are operating at low speed (12M), which is typical for many wireless keyboard and mouse setups.

Based on this information, here are some targeted recommendations:

1. USB Hub Power:
   The hub might not be providing enough power. Try connecting the hub to a powered USB port on your laptop instead of the monitor, or use a powered USB hub.

2. Reduce USB Load:
   Your wireless devices are on Bus 009, which also has other devices. Try connecting the hub to a less crowded USB bus, like Bus 007 or Bus 008, which appear to be empty.

3. Disable USB Autosuspend for specific devices:
   Run these commands to disable autosuspend for your specific devices:
   ```
   echo -1 | sudo tee /sys/bus/usb/devices/9-1/power/autosuspend_delay_ms
   echo -1 | sudo tee /sys/bus/usb/devices/9-1.1/power/autosuspend_delay_ms
   echo -1 | sudo tee /sys/bus/usb/devices/9-1.4/power/autosuspend_delay_ms
   ```

4. Adjust USB polling rate:
   Create or edit the file `/etc/modprobe.d/usbhid.conf` and add these lines:
   ```
   options usbhid mousepoll=2
   options usbhid kbpoll=2
   ```
   Then run `sudo mkinitcpio -P` and reboot.

5. Check for interference:
   Since both devices are 2.4GHz wireless, they might be experiencing interference. Try moving other 2.4GHz devices (like your phone) away from your computer.

6. Update firmware:
   Check for firmware updates for both your Logitech and Compx devices. Logitech often provides firmware updates through their Logitech Options software.

7. Try different USB ports:
   Connect the hub to different USB ports on your laptop, preferably USB 3.0 ports (usually colored blue).

8. Monitor USB events:
   Run this command and use your devices, watching for disconnect events:
   ```
   sudo usbmon
   ```

9. Check USB power output:
   Run this command to check the power output of your USB ports:
   ```
   for i in /sys/bus/usb/devices/*/power/autosuspend; do echo $i; cat $i; done
   ```
   Look for any unusually low values.

10. Kernel parameter:
    Add `usbcore.autosuspend=-1` to your kernel parameters in your bootloader configuration to globally disable USB autosuspend.

After trying these steps, please let me know if you notice any improvement or if you encounter any new behavior. We may need to investigate further based on the results of these actions.

---

**Human** - 2024-10-17 16:06:15 UTC

❯ lsusb -t
/:  Bus 001.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/4p, 480M
    |__ Port 003: Dev 002, If 0, Class=Vendor Specific Class, Driver=[none], 12M
    |__ Port 004: Dev 003, If 0, Class=Wireless, Driver=btusb, 480M
    |__ Port 004: Dev 003, If 1, Class=Wireless, Driver=btusb, 480M
    |__ Port 004: Dev 003, If 2, Class=Wireless, Driver=btusb, 480M
/:  Bus 002.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/2p, 10000M
/:  Bus 003.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/3p, 480M
/:  Bus 004.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/2p, 10000M
/:  Bus 005.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/1p, 480M
    |__ Port 001: Dev 002, If 0, Class=Video, Driver=uvcvideo, 480M
    |__ Port 001: Dev 002, If 1, Class=Video, Driver=uvcvideo, 480M
    |__ Port 001: Dev 002, If 2, Class=Application Specific Interface, Driver=[none], 480M
/:  Bus 006.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/0p, 5000M
/:  Bus 007.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/1p, 480M
/:  Bus 008.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/1p, 10000M
/:  Bus 009.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/1p, 480M
    |__ Port 001: Dev 002, If 0, Class=Hub, Driver=hub/4p, 480M
        |__ Port 001: Dev 079, If 0, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 001: Dev 079, If 1, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 001: Dev 079, If 2, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 004: Dev 080, If 0, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 004: Dev 080, If 1, Class=Human Interface Device, Driver=usbhid, 12M
/:  Bus 010.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/1p, 10000M

---

**Assistant** - 2024-10-17 16:09:28 UTC

 You're right to ask about this, as it's an important step that requires some care. In many Linux distributions, GRUB (Grand Unified Bootloader) is indeed the default bootloader. However, since you're running Arch Linux with Hyprland, there's a good chance you might be using a different bootloader. Arch is flexible and supports various bootloaders, with systemd-boot being another popular choice.

Let's cover both GRUB and systemd-boot, as these are the most common options:

1. If you're using GRUB:

   a. Edit the GRUB configuration file:
      ```
      sudo nano /etc/default/grub
      ```

   b. Find the line that starts with `GRUB_CMDLINE_LINUX_DEFAULT` and add the parameter to it. It might look something like this:
      ```
      GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1"
      ```

   c. Save the file and exit the editor.

   d. Regenerate the GRUB configuration:
      ```
      sudo grub-mkconfig -o /boot/grub/grub.cfg
      ```

2. If you're using systemd-boot:

   a. Edit or create a new boot entry. Your boot entries are typically located in `/boot/loader/entries/`. You might have a file like `arch.conf` or similar.
      ```
      sudo nano /boot/loader/entries/arch.conf
      ```

   b. Add the kernel parameter to the `options` line. It might look something like this:
      ```
      options root=PARTUUID=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX rw usbcore.autosuspend=-1
      ```

   c. Save the file and exit the editor.

To determine which bootloader you're using:

1. Check if GRUB is installed:
   ```
   pacman -Qs grub
   ```

2. Check if systemd-boot is being used:
   ```
   ls /boot/EFI/systemd
   ```

If you're unsure or using a different bootloader, you can check your current boot parameters:

```
cat /proc/cmdline
```

This will show you your current boot parameters, which can help identify your bootloader and current configuration.

After making these changes, reboot your system for the new parameter to take effect.

Remember, modifying bootloader configurations can potentially make your system unbootable if done incorrectly. It's always a good idea to have a backup or rescue media available before making these changes.

If you're unsure about which bootloader you're using or how to proceed, let me know, and we can investigate further to ensure we're making the correct modifications for your specific setup.

---

**Human** - 2024-10-17 16:09:28 UTC

tell me more about adding the parameter to my bootloader.. i'd imagine that to be grub?

---

