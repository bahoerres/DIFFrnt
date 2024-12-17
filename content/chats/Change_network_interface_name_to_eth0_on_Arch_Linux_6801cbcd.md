---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Change network interface name to eth0 on Arch Linux

Created: 2024-12-07 18:30:17 UTC
Updated: 2024-12-07 18:38:43 UTC
UUID: 6801cbcd-964f-41cc-8ad4-ead149e2b13c
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-12-07 18:30:24 UTC

how do i change the device alias for my network adapter? arch linux. it's currently enp6s18 i would like it to be eth0

---

**Assistant** - 2024-12-07 18:30:24 UTC

 I can help you change your network interface name back to the traditional `eth0` naming scheme on Arch Linux. This requires modifying the kernel parameters to disable predictable network interface names.

Here are the steps:

1. Edit `/etc/default/grub` and add `net.ifnames=0 biosdevname=0` to the `GRUB_CMDLINE_LINUX` line:

```bash
sudo nano /etc/default/grub
```

Find the line that looks like:
```
GRUB_CMDLINE_LINUX=""
```

Change it to:
```
GRUB_CMDLINE_LINUX="net.ifnames=0 biosdevname=0"
```

2. Regenerate the GRUB configuration:
```bash
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

3. Reboot your system:
```bash
sudo reboot
```

After reboot, your network interface should be renamed to `eth0`. You can verify this with:
```bash
ip link show
```

Note that this will affect all network interfaces on your system, reverting them to the traditional naming scheme (eth0, eth1, wlan0, etc.).

---

**Human** - 2024-12-07 18:30:48 UTC

i feel like the last time i did this there was a much easier way.

---

**Assistant** - 2024-12-07 18:30:48 UTC

 Ah yes, there is a simpler way if you just want to rename a specific interface! You can use systemd's network interface naming rules.

1. Create a rule file in `/etc/systemd/network/`:
```bash
sudo nano /etc/systemd/network/10-eth0.link
```

2. Add these lines:
```
[Match]
OriginalName=enp6s18

[Link]
Name=eth0
```

3. Reboot:
```bash
sudo reboot
```

This method is more targeted since it only renames the specific interface you want, rather than changing the naming scheme system-wide. Is this more like what you remembered?

---

**Human** - 2024-12-07 18:38:24 UTC

any other ways? ifconfig maybe? the link doesnt seem to be behaving the way i'd like

---

**Assistant** - 2024-12-07 18:38:24 UTC

 You can use `ip link` to rename the interface temporarily (until next reboot):

```bash
sudo ip link set enp6s18 down
sudo ip link set enp6s18 name eth0
sudo ip link set eth0 up
```

If that's what you want, you could put it in a startup script to make it persistent.

The older `ifconfig` method still works too if you have net-tools installed:
```bash
sudo ifconfig enp6s18 down
sudo ip link set enp6s18 name eth0
sudo ifconfig eth0 up
```

Would you like me to explain any other methods? There are a few other approaches we could try if these don't work for your needs.

---

**Human** - 2024-12-07 18:38:43 UTC

that's exactly what it was! thanks!

---

**Assistant** - 2024-12-07 18:38:43 UTC

 You're welcome! Yes, the `ip link` method is nice and straightforward when you just need a quick interface rename. Glad I could help you track down the command you were thinking of!

---

