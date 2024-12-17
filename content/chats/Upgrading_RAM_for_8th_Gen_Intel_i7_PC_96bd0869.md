---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Upgrading RAM for 8th Gen Intel i7 PC

Created: 2024-10-16 06:22:17 UTC
Updated: 2024-11-13 17:24:56 UTC
UUID: 96bd0869-d331-45dc-918c-fa6f752d936f
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-10-16 06:22:31 UTC

I'm looking to add additional ram to an agint PC. While still in great working order, it is an 8th gen Intel i7. 

I'm looking at a 64gb 4 stick kit (or 2x32 I suppose?) as that's the listed cap for my motherboard. 

I don't imagine that going bonkers on speeds will do me many favors except for emptying my wallet faster. 

My thoughts would be a modest 3200mhz cl16 or something of that nature? 

Help me out.

---

**Assistant** - 2024-10-16 06:22:31 UTC

 Your approach to upgrading the RAM on your 8th gen Intel i7 system is sensible. Let's break down your considerations and provide some recommendations:

1. Capacity:
   - 64GB is a good choice, especially if that's the maximum your motherboard supports.
   - Both 4x16GB and 2x32GB configurations can work, but there are some factors to consider:
     - 4x16GB might offer slightly better performance due to quad-channel support (if your motherboard supports it).
     - 2x32GB leaves room for future expansion and might be easier to cool.

2. Speed:
   Your thinking on speed is correct. 3200MHz CL16 is a good balance of performance and cost for an 8th gen Intel system. Here's why:
   - 8th gen Intel CPUs officially support up to 2666MHz RAM.
   - While faster RAM can still provide benefits, the performance gains beyond 3200MHz are often minimal for this generation of CPUs.
   - CL16 latency at 3200MHz offers a good balance of speed and responsiveness.

3. Compatibility:
   - Ensure the RAM you choose is compatible with your specific motherboard model.
   - Check your motherboard's QVL (Qualified Vendor List) if available.

4. Brand and Quality:
   - Stick to reputable brands like Corsair, G.Skill, Crucial, or Kingston.
   - Look for kits specifically sold as matched sets to ensure compatibility and optimal performance.

5. Cost-effectiveness:
   - As you noted, extremely high-speed kits (e.g., 4000MHz+) would likely not provide significant benefits for your system and would be more expensive.

Given your requirements, a 64GB (4x16GB or 2x32GB) kit of 3200MHz CL16 RAM from a reputable brand would be an excellent choice for your 8th gen Intel i7 system. This configuration offers a good balance of capacity, speed, and cost-effectiveness without overspending on marginal performance gains.

---

**Human** - 2024-10-16 06:23:41 UTC

Explain let latency grading scale to me in simple layperson terms.

---

**Assistant** - 2024-10-16 06:23:41 UTC

 Certainly, I'd be happy to explain the latency grading scale (often referred to as CL or CAS Latency) in simple terms.

Think of RAM (memory) as a big library, and the latency as the time it takes for the librarian to find and retrieve a book you've requested.

The CL (CAS Latency) number represents how many clock cycles it takes for the RAM to respond to a request. Lower numbers are faster, just like a quicker librarian would be better.

Here's a simplified breakdown:

1. CL14: Very fast (like a super-efficient librarian)
2. CL16: Fast (a good, speedy librarian)
3. CL18: Average (a decent librarian)
4. CL20 and above: Slower (the librarian might be taking their time)

However, this isn't the whole story. The overall speed of RAM depends on both its frequency (MHz) and its latency (CL). It's like considering both how quickly the librarian moves (frequency) and how long it takes them to find a book once they reach the right shelf (latency).

For example:
- 3200MHz CL16 might be roughly equivalent in real-world performance to 3600MHz CL18

This is because while the 3600MHz RAM has a higher frequency (librarian moves faster), it also has a higher latency (takes longer to find the book once at the shelf).

In general, for most users, anything in the CL14 to CL16 range at common speeds (2666MHz to 3600MHz) will provide good performance. The differences often become noticeable only in very specific, high-performance scenarios or benchmarks.

---

**Human** - 2024-10-16 06:27:24 UTC

What about the full string? 

CL 16-18-18-40?

---

**Assistant** - 2024-10-16 06:27:24 UTC

 Great question. The full string of numbers you're referring to represents different timing parameters for the RAM. Let's break down what CL 16-18-18-40 means in simple terms:

1. CL (CAS Latency): 16
   - This is the first number we discussed earlier, representing how quickly the RAM responds to a request.

2. tRCD (RAS to CAS Delay): 18
   - Think of this as the time it takes to open the correct row of data in memory.

3. tRP (RAS Precharge): 18
   - This is the time needed to close one row of memory and open another.

4. tRAS (Active to Precharge Delay): 40
   - This represents the minimum number of cycles a row must remain open for to ensure all data is read or written correctly.

To use our library analogy:

1. CL (16): How long it takes the librarian to start grabbing a book once they're at the right shelf.
2. tRCD (18): The time it takes to locate the correct shelf.
3. tRP (18): The time needed to move from one shelf to another.
4. tRAS (40): The minimum time the librarian needs to keep a shelf "open" to ensure they've grabbed all the necessary information.

In general, lower numbers are faster, but they all work together to determine overall performance. The first number (CL) is often the most quoted as it has the most noticeable impact in many scenarios.

For most users, the differences between similar timing sets (like 16-18-18-38 vs. 16-18-18-40) are minimal and often not noticeable in everyday use. These timings become more important for enthusiasts, overclockers, or in very specific high-performance computing scenarios.

---

**Human** - 2024-10-16 06:28:31 UTC

Is there any sort of magic combo here? Or am I really splitting hairs considering it's an almost 10 year old processor?

---

**Assistant** - 2024-10-16 06:28:31 UTC

 You're on the right track - for an 8th generation Intel processor (which is actually about 5-6 years old, not 10), you're definitely at the point of diminishing returns when it comes to fine-tuning RAM timings.

There's no real "magic combo" here that will give you dramatically better performance. You're absolutely correct that you'd be splitting hairs trying to optimize these numbers too much. Here's why:

1. Age of the processor: 8th gen Intel CPUs have a memory controller that isn't as sensitive to RAM timings as newer generations. The official support is up to 2666 MHz, so anything above that is already an overclock.

2. Minimal real-world impact: The difference between, say, 16-18-18-38 and 16-18-18-40 would be virtually imperceptible in real-world usage on your system.

3. Cost vs. Benefit: Tighter timings or higher frequencies often come with a price premium that isn't justified by the minimal performance gain on your platform.

4. System balance: Your CPU is more likely to be the limiting factor in most scenarios rather than RAM timings.

For your system, focusing on these aspects would be more beneficial:

1. Capacity: Ensuring you have enough RAM (which you're doing with the 64GB upgrade) is far more important than minor timing differences.

2. Reliability: Choose a reputable brand with a good warranty.

3. Compatibility: Ensure the RAM is compatible with your specific motherboard model.

4. Cost-effectiveness: A reasonably priced 3200 MHz CL16 kit would be a great choice, offering a good balance of performance and value.

In summary, for your 8th gen Intel system, you're better off choosing a reliable, compatible RAM kit with good overall specs (like 3200 MHz CL16) rather than obsessing over minor timing differences. The real-world performance difference will be negligible, and your upgrade focus is well-placed on increasing capacity to 64GB.

---

**Human** - 2024-10-16 06:29:03 UTC

2018-2024 feels like 10 years. 😅

---

**Assistant** - 2024-10-16 06:29:03 UTC

 I completely understand that feeling! You're right, the last few years have certainly felt longer than usual for many people. 

2018 to 2024 is indeed about 5-6 years in calendar time, but I can certainly empathize with why it might feel like a decade. A lot has happened in that period:

1. The global pandemic and its aftermath
2. Rapid technological advancements
3. Significant political and social events worldwide
4. Changes in work and lifestyle patterns

In the tech world specifically, we've seen several generations of hardware released, making older components feel more dated than they might be in absolute terms.

Your perception isn't unusual - many people have experienced a sense of time dilation, especially due to the disruptions and changes we've all faced. It's a common psychological phenomenon, particularly during periods of stress or significant change.

As for your PC, while it might feel older, an 8th gen Intel processor is still quite capable for many tasks. The fact that you're upgrading the RAM rather than replacing the whole system speaks to its continued utility. This upgrade should give your system a nice boost and extend its useful life, which is a smart and cost-effective approach.

---

**Human** - 2024-10-16 06:30:37 UTC

Is there anything between 2666 and 3200?

---

**Assistant** - 2024-10-16 06:30:37 UTC

 Yes, there are RAM speeds between 2666 MHz and 3200 MHz. The most common ones you might encounter are:

1. 2800 MHz
2. 2933 MHz
3. 3000 MHz

Here's some context on these speeds:

1. 2800 MHz: This is less common but does exist. It's a modest step up from 2666 MHz.

2. 2933 MHz: This is a popular speed, often used in systems that don't quite need 3200 MHz. It's the official maximum supported speed for some 9th gen Intel CPUs.

3. 3000 MHz: This is another common speed, offering a balance between 2666 MHz and 3200 MHz. It's popular in mid-range builds.

For your 8th gen Intel system:

1. 2666 MHz is the officially supported maximum speed for most 8th gen Intel CPUs.

2. Any speed above 2666 MHz is technically an overclock, even if it's stable and common.

3. The performance difference between these intermediate speeds (2800, 2933, 3000) and 3200 MHz is usually small, especially on an 8th gen platform.

4. Availability and pricing often drive the choice between these speeds. Sometimes, 3200 MHz kits are priced very close to 3000 MHz kits, making them a better value.

If you find a good deal on a 2933 MHz or 3000 MHz kit, it could be a solid choice for your system. However, given that 3200 MHz is widely available and often competitively priced, it's usually the go-to choice for a balance of performance and value, even if your system can't fully utilize its maximum speed.

Remember to check your motherboard's specifications and QVL (Qualified Vendor List) to ensure compatibility with whatever speed you choose.

---

**Human** - 2024-10-16 06:39:04 UTC

What sort of generational improvement is a ryzen 5 5600x from my 17-8700k?

---

**Assistant** - 2024-10-16 06:39:04 UTC

 The Ryzen 5 5600X and the Intel i7-8700K represent different generations and architectures, so let's compare them to give you an idea of the generational improvement:

1. Release dates:
   - i7-8700K: October 2017
   - Ryzen 5 5600X: November 2020

2. Core/Thread count:
   - i7-8700K: 6 cores, 12 threads
   - Ryzen 5 5600X: 6 cores, 12 threads

3. Base/Boost Clock:
   - i7-8700K: 3.7 GHz base, 4.7 GHz boost
   - Ryzen 5 5600X: 3.7 GHz base, 4.6 GHz boost

4. Manufacturing process:
   - i7-8700K: 14nm
   - Ryzen 5 5600X: 7nm (smaller is generally better for efficiency)

5. IPC (Instructions Per Clock):
   - The Ryzen 5 5600X has significantly improved IPC over the i7-8700K

6. Performance improvement:
   - In single-threaded tasks: The 5600X is about 15-20% faster on average
   - In multi-threaded tasks: The 5600X can be 20-30% faster, sometimes more

7. Power efficiency:
   - The 5600X is generally more power-efficient due to its newer architecture and manufacturing process

8. Features:
   - The 5600X supports PCIe 4.0, while the 8700K is limited to PCIe 3.0
   - The 5600X has larger and faster caches

9. Gaming performance:
   - The 5600X typically offers better gaming performance, especially at 1080p where CPU differences are more noticeable

Overall, the Ryzen 5 5600X represents a significant generational improvement over the i7-8700K. While both are 6-core/12-thread CPUs, the architectural advancements, improved IPC, and better power efficiency of the 5600X result in noticeably better performance across most tasks.

However, whether this upgrade would be worthwhile depends on your specific use case and whether your current system is meeting your needs. For many users, the i7-8700K is still a capable processor for a wide range of tasks.

---

**Human** - 2024-10-16 06:40:49 UTC

Is there anything in the same amd era with higher core counts before we move into their server offerings?

---

**Assistant** - 2024-10-16 06:40:49 UTC

 Certainly! AMD's Ryzen lineup from the same era as the 5600X (Zen 3 architecture) includes several processors with higher core counts. Here are some options, moving up in core count:

1. Ryzen 7 5800X
   - 8 cores, 16 threads
   - Great for gaming and content creation

2. Ryzen 9 5900X
   - 12 cores, 24 threads
   - Excellent for heavy multitasking and content creation

3. Ryzen 9 5950X
   - 16 cores, 32 threads
   - Top-of-the-line consumer CPU, great for demanding workloads

4. Ryzen 9 5945WX / 5955WX (part of the Threadripper Pro series)
   - 12 cores / 16 cores respectively
   - Workstation-class CPUs with additional features

5. Ryzen 9 5965WX / 5975WX / 5995WX (Threadripper Pro)
   - 24 cores / 32 cores / 64 cores respectively
   - High-end workstation/HEDT (High-End Desktop) CPUs

These are all from the same generation as the 5600X, using the Zen 3 architecture. The Threadripper Pro series, while not server CPUs, are designed for high-end workstations and fall between consumer and server offerings.

For most users, the 5800X, 5900X, or 5950X would be the logical next steps up from the 5600X in terms of core count, depending on your needs and budget. These offer significant multi-threaded performance improvements while maintaining high single-core performance for tasks like gaming.

The Threadripper Pro series, while extremely powerful, requires specialized motherboards and is typically overkill for most consumer or prosumer applications unless you have very specific high-performance computing needs.

---

**Human** - 2024-10-16 06:49:08 UTC

I'm really loving the creative names of some of these knockoff brands on Amazon. "GigaStone" and "TeamGroup" ha. 

The motherboard I have it the Asus rog strix gaming wifi. I believe it's the z370 chip set. Matx form factor. 

It has 4 slots. Does that mean it's 4 channel? Or is that debateable?

---

**Assistant** - 2024-10-16 06:49:08 UTC

 I understand your amusement at some of the brand names! While "GigaStone" does sound like a knockoff brand, it's worth noting that TeamGroup is actually a legitimate and reasonably well-known Taiwanese memory manufacturer. They've been around since 1997 and produce a range of memory products.

Now, regarding your motherboard and RAM configuration:

1. Motherboard: 
   ASUS ROG Strix Gaming WiFi with Z370 chipset in mATX form factor is indeed a real and solid motherboard.

2. RAM slots and channels:
   Having 4 RAM slots doesn't necessarily mean it's a quad-channel memory configuration. In fact, for your system, it's not quad-channel. Here's why:

   - The Z370 chipset and 8th gen Intel CPUs (like your i7-8700K) support dual-channel memory configurations.
   - The four slots are actually two pairs of dual-channel slots.

3. Memory configuration:
   - Your motherboard uses a dual-channel memory configuration.
   - The four slots allow you to have two DIMMs (sticks of RAM) per channel.
   - This is often referred to as "2DPC" (2 DIMMs Per Channel).

4. Optimal configuration:
   - For best performance, you'd ideally want to populate either 2 or 4 of these slots.
   - If using 2 sticks, they should be in matched slots (usually color-coded or labeled as A1 and B1) to enable dual-channel operation.
   - If using 4 sticks, you'll still be in dual-channel mode, but with all slots filled.

5. Quad-channel vs. Dual-channel:
   - Quad-channel configurations are typically found on high-end desktop (HEDT) platforms like Intel's X-series or AMD's Threadripper.
   - Your platform (mainstream Intel) uses dual-channel, which is plenty for most applications including gaming.

So, to directly answer your question: No, it's not debatable - your motherboard definitively supports dual-channel memory, not quad-channel, despite having 4 slots. The extra slots are for capacity expansion while maintaining dual-channel operation.

---

**Human** - 2024-10-16 06:50:57 UTC

Great. Aside fromayne some slight price differences, a 2 vs 4 slot kit will be a negligible difference?

---

**Assistant** - 2024-10-16 06:50:57 UTC

 You're on the right track. The difference between a 2-slot kit and a 4-slot kit for your system will indeed be minimal in most cases. Here's a breakdown:

1. Performance:
   - In a dual-channel configuration like yours, 2x32GB and 4x16GB will perform very similarly.
   - There might be a slight theoretical advantage to 4 sticks in some scenarios due to rank interleaving, but this is often negligible in real-world usage.

2. Stability:
   - 2 sticks might offer slightly better stability, as it puts less stress on the memory controller.
   - However, with modern systems, 4 sticks are generally quite stable as well.

3. Upgradability:
   - 2x32GB leaves you room to add more RAM later if needed.
   - 4x16GB fills all your slots but gives you the full 64GB immediately.

4. Cooling:
   - 2 sticks might allow for slightly better airflow around the RAM.
   - This is a minor consideration for most users unless you're doing heavy overclocking.

5. Price:
   - As you mentioned, there might be some price differences, but they're often small.
   - Sometimes 4x16GB kits are slightly cheaper than 2x32GB kits.

6. Aesthetics:
   - If your case has a window, you might prefer the look of all 4 slots filled.

For your i7-8700K system, the performance difference between 2x32GB and 4x16GB will be negligible in most real-world scenarios. Your choice can come down to:

- Price: Choose whichever is more cost-effective.
- Future plans: If you think you might want to upgrade to 128GB someday, go with 2x32GB.
- Aesthetics: If you prefer the look of all slots filled, go with 4x16GB.

Either way, you'll get the full benefit of dual-channel operation and the performance boost of upgrading to 64GB. The difference between the two configurations is small enough that other factors like price and personal preference can be your main deciding factors.

---

**Human** - 2024-10-16 06:52:47 UTC

Are you able to see if there have been reports of people successfully running >32gb (LISTED Max, I know sometimes there's wiggle room there) on this mobo?

---

**Assistant** - 2024-10-16 06:52:47 UTC

 I apologize, but I don't have access to real-time data or the ability to search for current user reports. However, I can provide some general insights about memory support on motherboards:

1. Listed Max vs. Actual Support:
   You're correct that there's often some wiggle room with maximum RAM support. Motherboard manufacturers sometimes list conservative estimates, and BIOS updates can expand support.

2. Z370 Chipset:
   The Z370 chipset theoretically supports up to 128GB of RAM. However, this is often limited by the motherboard's design and BIOS.

3. ASUS ROG Strix Gaming WiFi (Z370):
   While I can't confirm specific user reports, it's not uncommon for high-end motherboards like this to support more RAM than officially listed, especially after BIOS updates.

4. Factors affecting support:
   - BIOS version: Newer BIOS versions might add support for higher capacities.
   - RAM module technology: Newer, higher-density modules might work even if they weren't available when the motherboard was released.

5. Testing higher capacities:
   Some users do successfully run higher-than-listed RAM capacities, but it's not guaranteed and may depend on specific RAM modules and BIOS versions.

To get definitive information about running >32GB on your specific motherboard model, I would recommend:

1. Check the ASUS support forums or ROG forums for user reports.
2. Look for any notes in recent BIOS update changelogs about memory support.
3. Consider reaching out to ASUS support directly for the most up-to-date information.

Remember, even if others have succeeded, there's always a risk when exceeding officially listed specifications. If you decide to try it, make sure you have a fallback plan in case it doesn't work as expected.

---

**Human** - 2024-11-13 17:24:56 UTC

What were some of the dell and hp skus that you mentioned?

---

**Assistant** - 2024-11-13 17:24:56 UTC

 I haven't actually mentioned any Dell or HP SKUs in our conversation - we've been discussing your ASUS motherboard, RAM configurations, and the AMD Ryzen lineup. 

Would you like me to provide information about comparable Dell or HP systems from that era (around the 8th gen Intel timeframe)? Or were you perhaps thinking of a different conversation? Let me know what specific information you're looking for about Dell or HP systems, and I'll be happy to help.

---

