---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Laptop RAM Speed Discrepancy

Created: 2024-07-17 04:45:00 UTC
Updated: 2024-07-17 04:47:19 UTC
UUID: 1af06158-2973-41cb-a2e7-1744755e34e9
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-07-17 04:45:08 UTC

Is there any reason that both cpuz and hwinfo are showing my ram running at around 800 mhz and task manager in windows shows 6400mhz? I also find it strange showing up as 4 channel, as it's a laptop.

---

**Assistant** - 2024-07-17 04:45:08 UTC

 There are a few things to unpack here:

1. RAM speed discrepancy:
The difference between 800 MHz and 6400 MHz is likely due to how the data rate is reported:

- 800 MHz is probably the actual clock speed of your RAM.
- 6400 MHz (or more accurately, 6400 MT/s - megatransfers per second) is likely the effective speed.

Modern DDR (Double Data Rate) RAM performs transfers on both the rising and falling edges of the clock cycle, effectively doubling the data rate. Additionally, some newer RAM types like DDR5 can perform multiple operations per clock cycle.

For DDR4, the relationship is typically:
Effective speed = Clock speed * 2
For DDR5, it's:
Effective speed = Clock speed * 4

So if you have DDR5 RAM, 800 MHz clock speed would indeed result in 6400 MT/s effective speed.

2. 4-channel memory in a laptop:
It is unusual for a laptop to have true 4-channel memory, as this is typically found in high-end desktop or server systems. There are a few possibilities:

a) Your laptop might have a high-end mobile processor that supports quad-channel memory.
b) The software might be misreporting dual-channel memory as quad-channel.
c) If you have DDR5 RAM, it might be interpreting the two 32-bit subchannels per DIMM as separate channels.

To get a clearer picture, you could:
1. Check your laptop's specifications to confirm the RAM type and configuration.
2. Use a tool like CPU-Z to look at the SPD (Serial Presence Detect) tab for more detailed memory information.
3. Verify the exact model of your processor to see if it supports quad-channel memory.

Would you like me to explain any part of this in more detail?

---

**Assistant** - 2024-07-17 04:47:19 UTC

 Based on that information, let's break this down further:

1. RAM Speed:
Your Ryzen 6800H is compatible with DDR5 memory. This explains the speed discrepancy you're seeing:

- 800 MHz is the base clock speed
- 6400 MT/s (reported as MHz in Task Manager) is the effective speed

This aligns with DDR5 operation where: Effective speed = Base clock * 4

2. Channel Configuration:
The Ryzen 6800H officially supports dual-channel memory, not quad-channel. The "4 channel" report is likely a misinterpretation. Here's why:

- DDR5 introduces a feature called "dual 32-bit subchannels" per module.
- Each DDR5 stick essentially operates as two separate channels internally.
- Some software might interpret this as 4 channels total (2 physical channels * 2 subchannels each).

3. CPU-Z SPD Tab:
When you check the SPD tab in CPU-Z, look for:
- Number of physical slots used
- Memory type (should be DDR5)
- Max bandwidth (should match your effective speed)

This should give you a clearer picture of your actual memory configuration.

Your setup is most likely:
- Two DDR5 RAM sticks (dual-channel)
- Each stick operating at 800 MHz base clock
- Resulting in 6400 MT/s effective speed

The "4 channel" report is almost certainly a misinterpretation of DDR5's subchannel feature rather than true quad-channel memory.

Let me know what you find in the CPU-Z SPD tab, or if you have any other questions about your system's memory configuration.

---

**Human** - 2024-07-17 04:47:19 UTC

It's a 2 year old Lenovo laptop. Ryzen 6800h I believe. Going to have a look at the cpuz tab you mentioned.

---

