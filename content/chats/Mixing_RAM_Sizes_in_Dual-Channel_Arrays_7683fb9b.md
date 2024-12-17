---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Mixing RAM Sizes in Dual-Channel Arrays

Created: 2024-07-30 01:33:43 UTC
Updated: 2024-07-30 01:44:15 UTC
UUID: 7683fb9b-3924-44c8-af36-7261879f9a97
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Assistant** - 2024-07-30 01:33:47 UTC

 Here's a concise list of pros and cons for running two sizes of RAM in a 2-channel, 4-slot array with paired sizes:

Pros:
1. Increased total memory capacity
2. Cost-effective upgrade path
3. Utilizes all available slots

Cons:
1. Potential performance loss due to dual-channel mode limitations
2. Risk of compatibility issues
3. Increased complexity in system management
4. Possible instability if not configured correctly

Would you like me to elaborate on any of these points or provide more information about RAM configurations?

---

**Human** - 2024-07-30 01:33:47 UTC

pros and cons of running two sizes of ram in a 2 channel, 4 slot array. so long as the sizes are paired.

---

**Assistant** - 2024-07-30 01:41:23 UTC

 Given your current setup and requirements, I can see why you're considering upgrades. Let's break down your options:

1. RAM Upgrade:
   - Adding 2x16GB sticks (replacing two 8GB sticks) would bring you to 48GB total.
   - This is a cost-effective solution and would provide a noticeable improvement for your virtualization needs.
   - Ensure the new RAM matches your current RAM's speed and timings for optimal performance.

2. Case Upgrade:
   - A full tower case would give you more room for expansion and better airflow.
   - This could solve your GPU space issues without needing to change the motherboard.
   - Consider cases with good drive bays for your multiple SSDs and HDDs.

3. Motherboard Upgrade:
   - While an ATX motherboard would offer more slots and potentially better VRM, it's a more complex and expensive upgrade.
   - You'd need to ensure compatibility with your 8th gen Intel CPU.
   - This might be worth considering if you plan to upgrade your CPU in the near future.

4. Riser Cables:
   - These could be a good short-term solution if you just need to utilize more PCIe slots.
   - Ensure they're high quality to avoid performance degradation.

Given your use case (Proxmox with TrueNAS and Windows 11 VM), I'd recommend:

1. Upgrade RAM: Add 2x16GB sticks for a total of 48GB. This will significantly help with virtualization performance.
2. Upgrade Case: A full tower case will give you more flexibility and better cooling.
3. Consider riser cables if you need more PCIe slots immediately.

These upgrades would give you the most immediate benefits without requiring a complete system overhaul. The motherboard upgrade could be considered later if you decide to upgrade your CPU.

Would you like more details on any specific aspect of these upgrades?

---

**Human** - 2024-07-30 01:41:23 UTC

yeah, that was mostly to see if it was worth even looking into further. i've got a tower pc that i'm kind of back and forth with. 

current specs: intel i7-8700k, asus rog strix gaming z370-g wifi motherboard, 32gb trident z ram (i believe 3200 cl16) this is 4x8gb , i've got a 1tb nvme ssd, 3x1tb 2.5" sata ssd and 2x4tb hdd. oh, and a rtx 2070


here's where i keep going back and forth. it's got an interesting use case.. i have proxmox installed on it, where i'm running truenas, and a windows11 installation where i've got the gpu passed through. so basically it's a windows machine with proxmox and truenas hiding underneath (i know it's actually the other way around, but yeah.. )

i would love more ram, i would love an atx form factor motherboard (or at the very least a full tower case and a couple of riser cables to utilize all of the slots even with a large gpu). 

i suppose for all intents and purposes getting some cheap 16gb sticks of ram and a new case probably gets me the furthest the simplest.. i'm just trying to put the whole picture together.. and weigh my options.

---

**Assistant** - 2024-07-30 01:42:49 UTC

 Your approach sounds well-reasoned. Let's break down the stages:

Stage 1: RAM, Case, and Risers

1. RAM:
   - Look for 2x16GB DDR4 sticks matching your current 3200MHz CL16 specs.
   - Brands like Corsair, G.Skill, or Crucial often offer good compatibility.
   - This will bring you to 48GB total (2x16GB + 2x8GB).

2. Case:
   - Full tower cases from brands like Fractal Design, Phanteks, or Corsair are worth considering.
   - Look for cases with good drive bays for your SSDs and HDDs.
   - Ensure good airflow for your virtualization workload.

3. Risers:
   - PCIe 3.0 or 4.0 risers should work fine with your current setup.
   - Brands like EZDIY-FAB or LinkUp are reputable.
   - Consider the length needed based on your new case.

Stage 2: CPU and Motherboard Upgrade

This stage will give you more options, as you won't be limited to 8th gen Intel compatibility. You could consider:

- Latest gen Intel or AMD processors.
- A high-end ATX motherboard with plenty of PCIe lanes and M.2 slots.
- This upgrade will allow you to take full advantage of newer technologies like PCIe 4.0 or even 5.0.

Your plan to carry over the other components is solid. The GPU, storage, and upgraded RAM from Stage 1 will all be compatible with a new CPU/motherboard combo.

Would you like recommendations for specific components or more details on how to plan for Stage 2?

---

**Human** - 2024-07-30 01:42:49 UTC

yeah, i think ram a case and risers is stage 1. stage 2 will then be a cpu and motherboard upgrade, in which case everything will still carryover..

---

**Human** - 2024-07-30 01:43:25 UTC

yeah, the phanteks enthoo pro2 server edition is the one i'm set on.

---

**Assistant** - 2024-07-30 01:43:25 UTC

 The Phanteks Enthoo Pro 2 Server Edition is an excellent choice for your setup. It's well-suited for your needs, especially considering your multi-drive storage setup and virtualization workload. Here's why it's a good fit:

1. Drive capacity: It supports up to 12 HDDs and 11 SSDs, perfect for your current drives with room for expansion.

2. Cooling: Excellent airflow and support for extensive liquid cooling if needed in the future.

3. Expansion: Supports vertical GPU mounting and has multiple expansion slots, addressing your need for better GPU accommodation.

4. Size: At full tower size, it provides ample space for all your components and future upgrades.

5. Server-oriented features: Like hot-swap bays, which could be useful for your TrueNAS setup.

With this case, you'll have plenty of room for your current hardware and future upgrades. It should easily accommodate your planned RAM upgrade and any riser cables you might need.

For the RAM upgrade to complement this case, consider something like:

- 2x16GB G.Skill Trident Z DDR4-3200 CL16
- This matches your current RAM specs and should integrate well with your existing sticks.

For riser cables, look for PCIe 3.0 compatible options (to match your current motherboard) with enough length for this full tower case. A 20cm or longer cable should suffice, but measure to be sure once you have the case.

This combination will set you up well for your planned Stage 2 upgrades later on. Is there anything specific about the case or the other components you'd like to discuss further?

---

**Human** - 2024-07-30 01:44:15 UTC

yeah, the hdd expansion capability here is key too. i'm already closing in on being full.. that's honestly i think the biggest push..

---

**Assistant** - 2024-07-30 01:44:15 UTC

 Absolutely, the storage expansion capability of the Phanteks Enthoo Pro 2 Server Edition is indeed one of its strongest selling points for your situation. Let's break down how this case can help with your storage needs:

1. HDD Capacity:
   - The case supports up to 12 3.5" HDDs, which is a significant upgrade from your current setup.
   - This allows you to add several more 4TB (or larger) HDDs to your array.

2. SSD Support:
   - With space for up to 11 2.5" SSDs, you have room to expand your faster storage as well.
   - This is great for caching or for housing VMs that need faster I/O.

3. Hot-swap capability:
   - Some of the drive bays are hot-swappable, which is excellent for a TrueNAS setup.
   - This allows for easier drive replacement or upgrades without powering down the system.

4. Future-proofing:
   - Even if you don't fill all the bays immediately, you have room to grow over time.
   - This prevents the need for another major case upgrade in the near future.

5. Cooling for drives:
   - With multiple drive bays and good airflow, your drives should stay cool even under heavy load.

Given your current storage situation (2x4TB HDDs, 3x1TB SSDs, 1TB NVMe), you have plenty of room to expand. You could potentially add:

- 2-4 more 4TB HDDs for bulk storage
- Larger capacity HDDs (8TB, 10TB, etc.) for even more storage
- Additional SSDs for faster storage tiers or caching

This expansion capability aligns well with your TrueNAS setup in Proxmox, allowing you to create larger storage pools or implement more complex tiered storage solutions.

Would you like to discuss potential storage expansion strategies or how to best utilize this increased capacity within your TrueNAS/Proxmox environment?

---

