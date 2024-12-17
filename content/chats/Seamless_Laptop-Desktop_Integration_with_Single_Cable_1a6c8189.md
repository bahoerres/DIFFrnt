---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Seamless Laptop-Desktop Integration with Single Cable

Created: 2024-10-19 23:53:47 UTC
Updated: 2024-10-20 00:00:37 UTC
UUID: 1a6c8189-70a6-4554-b5f6-d163eacb310f
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-10-19 23:54:05 UTC

i'd like to be able to come and go from my desk freely with my laptop and be able to connect it to my peripherals easily and seemlessly, ideally with a single cable. my laptop is an asus un5401a running arch linux with hyperland as the winowmanager on wayland. i have a desktop pc with two monitors that i would like to share with the laptop along with the keyboard and mouse. 

i'd appreciate you laying out some options for me

---

**Assistant** - 2024-10-19 23:54:05 UTC

 I understand you're looking for a seamless way to connect your laptop to your desktop peripherals, ideally with a single cable. Given your setup, here are some options to consider:

1. USB-C Docking Station:
   - This is likely the most straightforward solution if your Asus UN5401A has a USB-C port with DisplayPort Alt Mode support.
   - A docking station would allow you to connect all your peripherals (monitors, keyboard, mouse) to it, and then connect to your laptop with a single USB-C cable.
   - Ensure the dock supports dual monitors and check if it's compatible with Linux and Wayland.

2. KVM (Keyboard, Video, Mouse) Switch:
   - A KVM switch allows you to share peripherals between multiple computers.
   - You'd connect your desktop PC and laptop to the KVM, and then connect your monitors, keyboard, and mouse to the KVM.
   - Look for a KVM that supports dual monitors and USB for peripherals.
   - This option might require more cables than a docking station.

3. Software-based solution:
   - You could use software like Synergy or Barrier to share your keyboard and mouse between your desktop and laptop.
   - For display sharing, you could use VNC or RDP to access your desktop from your laptop.
   - This option doesn't require additional hardware but may not be as seamless as a hardware solution.

4. HDMI/DisplayPort switch + USB switch:
   - Use an HDMI or DisplayPort switch for your monitors.
   - Pair this with a USB switch for your keyboard and mouse.
   - This solution requires multiple cables but can be more cost-effective than a full KVM switch.

5. Thunderbolt Dock:
   - If your laptop supports Thunderbolt, a Thunderbolt dock could offer high performance and compatibility.
   - Check Linux compatibility before purchasing.

Given your specific setup with Arch Linux, Hyprland, and Wayland, I'd recommend the following:

1. Verify if your Asus UN5401A supports USB-C with DisplayPort Alt Mode.
2. If it does, look for a USB-C docking station with good Linux compatibility.
3. If USB-C isn't an option, consider a KVM switch that's known to work well with Linux.

Before making a purchase, I'd suggest researching Linux compatibility for any hardware solution you're considering, as support can vary. You might also want to check the Arch Linux forums or Hyprland community for specific recommendations from users with similar setups.

Would you like me to elaborate on any of these options or provide more information about a specific solution?

---

**Human** - 2024-10-20 00:00:37 UTC

ah, that's a point that i forgot to mention, and one that i'm glad you touched on. 

i think a kvm is going to be my only viable option. the desktop does have a usb-c port on the graphics card (Msi GeForce RTX 2070 Gaming Z) although i don't really know what/if any purpose that will serve in this scenario when hardware is involved.

---

**Assistant** - 2024-10-20 00:00:37 UTC

 Thank you for providing that additional information. Given that a KVM switch seems to be your most viable option, let's focus on that solution and how you might incorporate the USB-C port on your desktop's graphics card.

Here's a more detailed look at setting up a KVM switch for your scenario:

1. KVM Switch Selection:
   - Look for a KVM switch that supports dual monitors, USB for peripherals, and ideally has a USB-C input.
   - Ensure it's compatible with the resolutions and refresh rates of your monitors.
   - Check for Linux compatibility, especially with Wayland.

2. Connections:
   - Desktop PC:
     - Connect the video outputs from your MSI GeForce RTX 2070 to the KVM switch.
     - The USB-C port on your graphics card might support DisplayPort Alt Mode. If so, you could potentially use a single USB-C cable for both video and data to the KVM, simplifying your setup.
   - Laptop:
     - Connect your Asus UN5401A to the KVM switch. Depending on its ports, you might use HDMI/DisplayPort for video and USB for data, or a single USB-C if supported.
   - Peripherals:
     - Connect your monitors, keyboard, and mouse to the KVM switch's output ports.

3. USB-C Considerations:
   - The USB-C port on your RTX 2070 could be useful. NVIDIA calls this VirtualLink, originally intended for VR headsets.
   - In some cases, it can function as a standard DisplayPort output and may even carry USB data.
   - If your KVM switch has a USB-C input, you might be able to use this for both video and peripheral data from your desktop PC.

4. Potential KVM Options:
   - Look for KVMs from reputable brands like ATEN, TESmart, or Level1Techs (known for good Linux support).
   - Ensure it supports the number of video outputs you need (likely two for your setup).
   - USB 3.0 support would be beneficial for faster peripheral response and data transfer.

5. Software Considerations:
   - Some KVMs come with software for advanced features. Check if this software is Linux-compatible.
   - You might need to configure Hyprland to recognize the displays correctly when switching inputs.

6. Audio:
   - If you need audio switching, ensure the KVM supports audio or consider a separate audio switch.

Remember to check the specifications of any KVM switch you're considering to ensure it meets all your requirements, especially in terms of video resolution, refresh rate, and Linux compatibility.

Would you like me to provide more specific KVM switch recommendations or elaborate on any part of this setup process?

---

