---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Renaming Ethernet Device on Arch Linux

Created: 2024-09-02 00:42:20 UTC
Updated: 2024-09-02 00:57:01 UTC
UUID: 9f4eee7f-9556-4d2c-8abd-f7cdeefdec83
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-09-02 00:42:26 UTC

i've got an ethernet device that i'd like to rename on archlinux. currently it's enp101s0f4u1u4 (kind of crazy, right?) i'd love it to be something like eth0. 

i know there's a way, but i have no idea where to begin.

---

**Assistant** - 2024-09-02 00:42:26 UTC

 That's a valid request - those auto-generated interface names can indeed get quite unwieldy! Renaming your Ethernet device on Arch Linux is definitely possible. Here's a concise guide to help you rename it to eth0:

1. Create a new udev rule file:
   ```
   sudo nano /etc/udev/rules.d/10-network.rules
   ```

2. Add this line to the file:
   ```
   SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="<MAC_ADDRESS>", NAME="eth0"
   ```
   Replace <MAC_ADDRESS> with your device's actual MAC address.

3. Find your device's MAC address:
   ```
   ip link show enp101s0f4u1u4
   ```

4. Save the file and exit the editor.

5. Reboot your system for the changes to take effect:
   ```
   sudo reboot
   ```

After rebooting, your interface should be renamed to eth0.

Would you like me to explain any part of this process in more detail?

---

**Human** - 2024-09-02 00:56:23 UTC

let's get it to work, first.  then we can talk about it.  

i created the file, the output of ❯ ip link show enp101s0f4u1u4 is:
2: enp101s0f4u1u4: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 80:3f:5d:fb:45:5f brd ff:ff:ff:ff:ff:ff

and i modified your line in step to to be :
SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="80:3F:5D:FB:45:5F", NAME="eth0"

---

**Assistant** - 2024-09-02 00:56:23 UTC

 Great, you've made good progress. Let's continue with the process:

1. The MAC address you've used looks correct. Make sure the file content is exactly as you've written:

   ```
   SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="80:3F:5D:FB:45:5F", NAME="eth0"
   ```

2. Save the file if you haven't already.

3. To apply the changes without rebooting, you can try the following steps:

   a. Reload the udev rules:
      ```
      sudo udevadm control --reload-rules
      ```

   b. Trigger udev to apply the new rule:
      ```
      sudo udevadm trigger --attr-match=subsystem=net
      ```

4. Check if the interface name has changed:
   ```
   ip link show
   ```

   Look for eth0 in the output.

5. If you don't see eth0, you may need to restart the network service or reboot:
   ```
   sudo systemctl restart systemd-networkd
   ```
   
   If that doesn't work, a reboot should do it:
   ```
   sudo reboot
   ```

After these steps, your interface should be renamed to eth0. Let me know the results, and we can troubleshoot further if needed.

---

**Human** - 2024-09-02 00:57:01 UTC

i have rebooted. no change.

---

**Assistant** - 2024-09-02 00:57:01 UTC

 I apologize for the inconvenience. Let's troubleshoot this issue step by step:

1. First, let's verify the contents of the udev rule file:

   ```
   cat /etc/udev/rules.d/10-network.rules
   ```

   Ensure it contains the exact line we created earlier.

2. Let's try a more specific udev rule. Edit the file again:

   ```
   sudo nano /etc/udev/rules.d/10-network.rules
   ```

   Replace the content with:

   ```
   SUBSYSTEM=="net", ACTION=="add", ATTRS{address}=="80:3f:5d:fb:45:5f", NAME="eth0"
   ```

   Note the changes: ATTR{address} became ATTRS{address}, and the MAC address is in lowercase.

3. Save the file and exit the editor.

4. Now, let's check if udev recognizes our rule:

   ```
   sudo udevadm test /sys/class/net/enp101s0f4u1u4
   ```

   Look for any output related to renaming the interface.

5. If the test looks good, reload the rules and trigger udev:

   ```
   sudo udevadm control --reload-rules
   sudo udevadm trigger --attr-match=subsystem=net
   ```

6. Check the interface name again:

   ```
   ip link show
   ```

If you still don't see eth0, there might be other system configurations interfering. Let's check a couple more things:

7. Look for any other network naming rules:

   ```
   ls /etc/udev/rules.d/ | grep net
   ```

8. Check if predictable network interface names are enabled:

   ```
   ls -l /etc/systemd/network/99-default.link
   ```

   If this file exists, it might be enforcing the predictable naming scheme.

If none of these steps work, we might need to consider a different approach. Let me know the results, and we can proceed from there.

---

