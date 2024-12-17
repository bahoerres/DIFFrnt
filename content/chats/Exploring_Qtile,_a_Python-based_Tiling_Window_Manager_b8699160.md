---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Exploring Qtile, a Python-based Tiling Window Manager

Created: 2024-11-03 19:35:17 UTC
Updated: 2024-11-03 21:21:12 UTC
UUID: b8699160-902c-4049-bb2c-5e4f7ae73ae9
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-11-03 19:35:23 UTC

i've seen a lot of mentions in configs (as i'm incessantly ricing multiple computers) of qtile. can you tell me about it a little bit?

---

**Assistant** - 2024-11-03 19:35:23 UTC

 Qtile is a tiling window manager written and configured in Python. It's particularly popular among users who enjoy programming-based configuration and want fine-grained control over their desktop environment.

Key features of Qtile:
- Full window management through Python scripts
- Dynamic tiling layouts (like MonadTall, Matrix, Max, etc.)
- Support for floating windows when needed
- Built-in widget system for status bars
- Multiple screen support
- Extensible through Python
- Wayland support (though X11 is still more commonly used)

What makes Qtile stand out is that your entire configuration is a Python script, which means you can use all of Python's features to customize your environment. For example, you can write functions to manipulate windows, create custom layouts, or even integrate with external Python libraries.

Would you like me to show you what a basic Qtile configuration looks like? Since you mentioned you're into ricing, I could demonstrate some customization examples.

---

**Human** - 2024-11-03 19:36:43 UTC

well, i'm using hyprland. and very happy with how far it's come. 

i have a feeling that there's a lot of these remnants for people that use other DEs as a backup. like, Gnome in case of emergency.

---

**Assistant** - 2024-11-03 19:36:43 UTC

 Ah yes, Hyprland is fantastic - it's really shown how smooth and capable Wayland compositors can be, especially with its animations and dynamic tiling. It's become quite popular in the ricing community, particularly for those who've moved to Wayland.

You make an interesting observation about keeping backup DEs. It's actually a pretty common practice, especially among users who like to experiment. There are several reasons for this:

1. Troubleshooting: If something breaks in your main setup (like a bad config), having GNOME or KDE as a fallback lets you still get work done
2. Updates can sometimes break things: Especially true with bleeding-edge setups like Hyprland
3. Display manager compatibility: Some users keep a traditional DE for better login manager integration
4. Certain apps: Some applications still work better under traditional DEs or X11

But you're right - as Wayland compositors like Hyprland mature, the need for these "safety nets" is decreasing. Many users who previously kept GNOME or KDE as a backup are finding they don't need them anymore, especially if they're comfortable with terminal-based recovery methods.

Are you running pure Hyprland, or do you keep any backup environments installed?

---

**Assistant** - 2024-11-03 19:38:20 UTC

 That makes sense. Using KDE and Budgie as safety nets while primarily living in Hyprland is a pretty solid approach. Both are relatively lightweight for what they offer as backups - Budgie especially is quite minimal compared to full GNOME or KDE.

I find it interesting you're running Hyprland in a VM - that's actually pretty impressive given how some compositors can be finicky about virtualization. I'm guessing you've got decent GPU passthrough set up? 

The emergency use case scenario is exactly why these DEs persist on many systems. It's kind of like keeping a basic toolset around - you might not need it often, but when you do (like after a bad update breaks your Hyprland config, or a new version has incompatibilities), you really need it. Though with Hyprland's stability improving, these occasions are becoming rarer.

Budgie's an interesting choice for a backup - what led you to pick it over something like XFCE, which is often used as a fallback?

---

**Human** - 2024-11-03 19:38:20 UTC

i've got KDE in the background on my desktop (well, it's a VM, but that's another discussion) and budgie on my laptop. i don't particularly care for either of them. just have them as emergency use cases.

---

**Human** - 2024-11-03 19:41:20 UTC

proxmox as the base, arch in a vm on it with an nvidia gpu (the more headaches, the merrier i guess!) passed through. 

as was formerly a gaming rig, and is showing it's age and small form factor limitations, it's definitely done plenty of bellyaching about it's shortcomings. but it works well, and i enjoy it. 

upgrading to a larger form factor and being able to have more than 6c/12t and a cap of 64gb ram would be nice.

---

**Assistant** - 2024-11-03 19:41:20 UTC

 Ah, the classic "let's make it as challenging as possible" setup with Proxmox + Arch + Hyprland + Nvidia GPU passthrough! That's actually pretty impressive that you've got it all working smoothly. The Nvidia passthrough especially can be finicky - their drivers have historically been... let's say "less than cooperative" with virtualization.

A SFF (Small Form Factor) build hitting those limits is definitely relatable. When you're dealing with 6c/12t and 64GB RAM cap, you really start to feel it when running VMs, especially if you're doing any kind of development work or running multiple environments. The CPU constraints probably become pretty apparent when you're doing any heavy compilation or running multiple resource-intensive VMs.

If you're planning an upgrade, are you thinking of going with something like a tower build? The current gen AMD and Intel offerings would give you a pretty significant boost in both core count and memory capacity. Though I suppose with Proxmox as your base, you'd need to carefully consider the CPU's virtualization features and IOMMU grouping for that GPU passthrough.

Are you finding the current setup impacts your Hyprland performance much, or does the GPU passthrough keep things pretty smooth?

---

**Human** - 2024-11-03 19:42:15 UTC

well, i suppose it was more of a "this is what i've got, these are the things i want to play with. let's figure it out!" 

if you're gonna be broke, you've gotta be creative in order to have "nice things"

---

**Assistant** - 2024-11-03 19:42:15 UTC

 That's honestly the best kind of learning experience - working with what you've got and finding creative solutions! It's the "necessity is the mother of invention" approach to tech setup. Sometimes having constraints forces you to learn the ins and outs of systems in ways you might not if you just threw money at the latest hardware.

Your setup is a great example of maximizing existing hardware - taking what was a gaming rig and transforming it into a virtualization platform that can still handle modern workflows and a pretty sophisticated desktop environment. The fact that you've got Hyprland running smoothly through GPU passthrough on older hardware is testament to both the efficiency of modern Linux systems and some clever configuration work.

It's kind of satisfying when you can take hardware that might be considered "aging" by some standards and make it do things that even some newer systems might struggle with. The whole "broke but clever" approach often results in much deeper system knowledge than just buying the latest stuff.

Plus, there's something to be said for really knowing your system's limits and how to work within them, rather than just throwing more resources at problems.

---

**Human** - 2024-11-03 19:45:28 UTC

the system is still rather capable. intel i7-8700k, 32gb of 3200mhz ram, and an rtx 2070. while not true SFF, even the atx motherboard has given me plenty of issues/limitations (another vm on the machine is truenas scale, i have a sata controller card passed through to it, although i've only got 2x4tb HDDs and 2x 1tb SDDs (also due to limitations) 

i'm short on cores, ram capacity,  pcie slots, iommu segmentation, and just generally lacking space inside of this enthoo matx case

---

**Assistant** - 2024-11-03 19:45:28 UTC

 That's actually still a pretty solid setup - the 8700K and 2070 are far from obsolete. You're just pushing them to their absolute limits with virtualization! The IOMMU grouping on that generation can definitely be a pain point though, especially with a mATX board where you're already tight on PCIe lanes.

The storage setup is particularly interesting - dealing with SATA controller passthrough on limited PCIe slots while also managing GPU passthrough must have required some creative IOMMU handling. The fact that you've got TrueNAS Scale and an Arch desktop VM running simultaneously speaks to good resource management, even with the constraints.

Your description of the limitations is spot-on for mATX builds trying to do serious virtualization:
- PCIe slots become precious real estate when you need them for both storage and GPU
- IOMMU groupings can be frustratingly inflexible
- Physical space becomes a tetris game with drives, cards, and cooling
- The 8700K's 6c/12t, while capable, definitely starts to feel the pinch when you're running multiple VMs

It's kind of like trying to fit a datacenter's worth of functionality into a shoebox - you can do it, but you'll hit every possible constraint along the way. Sounds like when you do upgrade, a full ATX or even E-ATX build would give you some much-needed breathing room.

---

**Human** - 2024-11-03 19:46:38 UTC

while i have 4 slots (2x16or x8 and 2x1) i can only use one 16 and 1 single because of the size of things.

---

**Assistant** - 2024-11-03 19:46:38 UTC

 Ah yeah, that physical clearance issue is real - when you've got a chunky GPU taking up 2-3 slots worth of space, it basically renders nearby PCIe slots unusable. Those theoretical PCIe lanes look great on the motherboard specs until you actually try to populate them with real hardware!

It's especially painful when you've got multiple full-size cards like:
- GPU (probably taking 2.5-3 slots of physical space)
- SATA controller 
And then you're basically out of usable space, even if you technically have more slots available.

The physical layout limitations often end up being more restrictive than the actual PCIe lane limitations. You could have all the lanes in the world, but if you can't physically fit the cards due to cooler clearance or card thickness, those lanes might as well not exist.

This is one of those things that makes planning virtualization builds tricky - you need to consider not just the electrical lanes and IOMMU groupings, but also the physical spacing and clearance of all the components you want to pass through. It's like playing 3D chess with computer parts!

---

**Human** - 2024-11-03 19:47:40 UTC

so i have a 6 port sata card and the gpu.. 

the host os is on an nvme hard drive and i have one of the sata ports on the motherboard with an additional terabyte for LVM storage

---

**Assistant** - 2024-11-03 19:47:40 UTC

 That makes sense - you're really maximizing every available connection point there. The NVME for Proxmox is a smart choice since it doesn't compete for SATA ports or PCIe lanes needed for passthrough devices.

So your layout is basically:
- NVME: Proxmox host
- Motherboard SATA: 1TB for LVM
- 6-port SATA card: Passed to TrueNAS Scale (handling your 2x4TB HDDs and 2x1TB SSDs)
- GPU: Passed to Arch VM

And all of this in a case where you're probably having to get creative with cable management and airflow given the space constraints. I'm guessing any maintenance or drive swaps requires some careful planning and probably removal of other components just to get access.

It's kind of amazing how quickly you can max out even modern hardware when you're trying to run a proper homelab setup with storage and VMs. Each component makes sense in isolation, but stack them all together in a mATX case and suddenly you're playing hardware Tetris!

---

**Human** - 2024-11-03 20:19:41 UTC

With all that said, and just having a little look, the ryzen 9 5900x seems like a good upgrade without breaking the bank. 

I have also been perusing the used/decommissioned enterprise market and previous gen hardware doesn't seem too bad. 

Ideally I think I want 24-32 cores, with at least some hyper threaded for at least as many vcores 128 or 256gb of ram and lots of pcie slots is really my only motherboard stipulation. Ha.

---

**Assistant** - 2024-11-03 20:19:41 UTC

 The 5900X would definitely be a nice jump - going from 6c/12t to 12c/24t would give your VMs a lot more breathing room, and they can be found at pretty reasonable prices now that the 7000 series is out.

But yeah, the enterprise/decommissioned market can offer some incredible value, especially if you're willing to deal with slightly higher power consumption and maybe a bit more noise. Something like a dual socket Xeon setup could get you those core counts and memory capacity for surprisingly reasonable money. Plus, server/workstation boards tend to be much more generous with PCIe lanes and expansion options.

Your wishlist is pretty reasonable for a virtualization host:
- 24-32 cores (48-64 threads) gives you plenty to distribute
- 128/256GB RAM would let you actually allocate meaningful amounts to each VM
- Abundant PCIe slots means no more playing hardware Tetris

The main tradeoffs with enterprise gear tend to be:
- Power consumption (especially with older Xeons)
- Cooling requirements (hello, server fans!)
- Physical size (say goodbye to mATX constraints!)
- Sometimes quirky with consumer GPUs for passthrough

Have you looked at any specific enterprise platforms? The Dell R7xx series or HP Z workstations can sometimes pop up at good prices.

---

**Assistant** - 2024-11-03 20:21:40 UTC

 The proprietary aspects of Dell and HP enterprise gear can be a mixed bag. Dell's generally a bit more standard than HP, especially in their PowerEdge line. The main proprietary gotchas tend to be:

- Cooling solutions that throw fits if you don't use their specific fans (HP is notorious for this)
- Power supplies with custom pinouts (especially HP)
- BIOS/UEFI that might be picky about non-certified components
- Some models require their specific drive caddies

But there are some advantages too:
- Usually rock-solid IOMMU implementation
- Better remote management (iDRAC for Dell, iLO for HP)
- Built for 24/7 operation
- Often more PCIe slots than you'd get in consumer boards

If you want to avoid some of the proprietary headaches while still getting enterprise-grade hardware, you might want to look at:
- Supermicro boards/systems (generally more standard)
- Standalone server/workstation motherboards
- Previous-gen Threadripper platforms (though these can still be pricey)

The R720/R730 series from Dell tends to be a sweet spot for price/performance/compatibility if you go that route. They're old enough to be affordable but new enough to handle modern workloads.

---

**Human** - 2024-11-03 20:21:40 UTC

That's good information. I hadn't really refined my search that much. The dell and hp offerings are likely going to have some proprietary restrictions right? But for a reasonably priced work horse I guess those things are probably worth sacrificing.

---

**Human** - 2024-11-03 20:22:18 UTC

Yeah, PSU and other mobo pinouts are what mainly hear about.

---

**Assistant** - 2024-11-03 20:22:18 UTC

 Yeah, those proprietary pinouts can be a real pain - especially if you ever need to replace or upgrade components. HP is particularly infamous for their PSU situation where you can't just swap in a standard ATX power supply.

The thing about server gear is you're often better off getting complete systems rather than trying to piece things together. When you buy a full R730 for instance, you're getting everything matched and known-working, rather than trying to source compatible parts individually. This is almost the opposite of regular PC building where piece-by-piece often makes more sense.

That said, if you're open to a kind of middle ground, workstation-class hardware like the older Threadrippers or even first-gen EPYC can be interesting. They give you:
- Standard ATX power connections
- Regular memory slots (though ECC capable)
- Plenty of PCIe lanes
- Good core counts
- Better compatibility with consumer parts

They tend to cost more than older enterprise gear initially, but you avoid some of the headaches of dealing with proprietary enterprise stuff. Plus, they usually run cooler and quieter than dual Xeon setups.

What's your tolerance for fan noise? That's often a deciding factor between workstation and server hardware.

---

**Assistant** - 2024-11-03 20:23:43 UTC

 The Enthoo Pro 2 is actually a really solid choice for this kind of build! It's like having server capacity without looking like a server. It's got some nice features that would work well for your use case:

- Those vertical HDD mounting options (up to 12 drives)
- Multiple radiator mounting points if you need serious cooling
- Full E-ATX support with good clearance
- Decent airflow without sounding like a jet engine
- Much better access for maintenance than your current setup

You could basically build a "home server that doesn't look like a server" setup. You'd get:
- All the PCIe slots you need for GPU and SATA controller(s)
- Room for future storage expansion
- Proper cooling without enterprise noise levels
- Easy access for maintenance

This approach would give you most of the benefits of enterprise hardware (capacity, expandability) while avoiding the proprietary headaches and noise issues. Plus, it's a lot easier to live with than a rack server if this is going in a home environment.

Is your plan to still run Proxmox as the hypervisor in the new build? The extra cores and RAM would really let it stretch its legs.

---

**Human** - 2024-11-03 20:23:43 UTC

What I was sort of spit balling was a full or even eatx, the core and ram capacities we discussed and housing it all in an enthoo pro 2 server case

---

**Human** - 2024-11-03 20:25:11 UTC

And with Linux and windows vms that I like to use as the "desktop" experience, that's right there in the middle too. 

Hmm maybe a second GPU to be able to run both vms concurrently.

---

**Assistant** - 2024-11-03 20:25:11 UTC

 Ah yes, having dual GPUs for simultaneous desktop VMs would be super nice! That's the kind of setup that really benefits from a larger case and proper E-ATX board - you'd actually have the physical space and PCIe lanes to support it properly.

In the Enthoo Pro 2, you could run:
- Two full-size GPUs with proper spacing for cooling
- Your SATA controller(s)
- Maybe even a dedicated NIC for TrueNAS
All without playing tetris with the components or worrying about clearance.

For desktop VMs, you could have:
- Linux VM with Hyprland (passed GPU 1)
- Windows VM for gaming/specific apps (passed GPU 2)
- Both running simultaneously with proper hardware acceleration
- Enough CPU cores and RAM to give each VM dedicated resources

That's actually a really elegant solution - you get the benefits of separate systems (isolation, dedicated resources) with the convenience of a single physical machine. And with the extra cores/threads we were discussing, you could still have plenty of headroom for TrueNAS and other services.

Just need to make sure the motherboard you choose has good IOMMU grouping for clean GPU passthrough. Some of the higher-end AMD boards tend to be pretty good about this.

---

**Human** - 2024-11-03 20:26:19 UTC

Will all of the extra room in the case, I had even looked at using riser cables in the case that a GPU other other card obscures the motherboard slot, but would still allow for it to be mounted in the case.

---

**Assistant** - 2024-11-03 20:26:19 UTC

 That's a really smart approach! Riser cables would give you a ton of flexibility in component placement, especially with the Enthoo Pro 2's design. You could:

- Mount GPUs vertically to avoid slot blocking
- Position cards for optimal airflow
- Access otherwise obscured PCIe slots
- Better distribute the weight of heavy GPUs

The Pro 2 is particularly good for this because it has:
- Multiple mounting points for vertical cards
- Good cable management channels
- Enough depth to accommodate risers
- Space to route the cables cleanly

Modern PCIe risers are pretty reliable now too - they've come a long way from the early days where signal integrity could be iffy. Just need to make sure to get PCIe 4.0 capable risers if you're using newer cards.

This kind of setup would give you a lot of flexibility for future changes too. If you later wanted to add another card or rearrange things for better cooling, you wouldn't be locked into specific slot arrangements by physical constraints.

The only real gotcha is making sure the risers are high quality - with GPU passthrough, you really don't want any signal integrity issues causing VM instability.

---

**Human** - 2024-11-03 20:27:41 UTC

I think in a situation like this, so long as I can find an appropriate motherboard, the 5900x may be a better option, if only for being a bit more future proof.

---

**Assistant** - 2024-11-03 20:27:41 UTC

 The 5900X does make a lot of sense here - it's a more modern platform with better features and efficiency than older enterprise gear. Some key advantages:

- PCIe 4.0 support for newer GPUs and NVMe drives
- Better single-thread performance (important for desktop VMs)
- Lower power draw than comparable core-count Xeons
- AM4 motherboards generally have good IOMMU support
- Still plenty of cores (12c/24t) for virtualization
- Modern instruction sets and security features
- Better memory latency than older enterprise platforms

Plus, suitable AM4 motherboards are readily available and use standard components. You could look at boards like:
- MSI Creation
- ASUS Pro WS
- Some of the higher-end X570 boards

These would give you:
- Multiple full-size PCIe slots
- Good spacing for dual GPUs
- Solid VRM design for sustained workloads
- Standard ATX/E-ATX form factors
- No proprietary nonsense to deal with

You'd be getting a more balanced system - enough cores for virtualization while maintaining good single-thread performance for your desktop VMs, and modern features without the quirks of enterprise hardware.

---

**Human** - 2024-11-03 20:28:38 UTC

Yeah, I had been looking at a few of the ASRock rack boards. 

While expensive, they sure do open a lot of doors.

---

**Assistant** - 2024-11-03 20:28:38 UTC

 ASRock Rack boards are really interesting - they're like the perfect middle ground between enterprise and consumer hardware. They give you server-grade features without all the proprietary lockdowns:

- Tons of PCIe lanes properly segmented
- IPMI for remote management
- ECC memory support
- Better IOMMU groupings
- Rock-solid power delivery
- Standard form factors and connections

They're expensive, but you're getting:
- Enterprise reliability
- Consumer compatibility 
- None of the Dell/HP proprietary headaches
- Actually designed with virtualization in mind
- Good documentation and support for Linux

The X570D4U series in particular seems popular for builds like what you're planning. While pricey, they're basically purpose-built for advanced virtualization setups with multiple PCIe passthrough devices.

It's one of those "buy once, cry once" situations - the board is expensive, but you're not going to run into limitations or compatibility issues down the road. Plus, with the 5900X, you'd have a really solid foundation for future upgrades.

You're clearly thinking long-term with this build plan!

---

**Human** - 2024-11-03 20:32:01 UTC

Let's make a shopping list then, I suppose. Haha. 

I'll likely scavenge things from the current desktop, but still leaving a core to build back up for a later project. Maybe a home theatre pc. The drives, the sata controller, the GPU (the 8700k has onboard video, and while less than ideal, will work in a pinch). 

And I also understand your limitations and knowledge
 I'm just looking to put together a parts list. I can deal with pricing on my own.

---

**Assistant** - 2024-11-03 20:32:01 UTC

 Perfect! Let's draft a build list, assuming we're scavenging some parts from your current build but leaving it functional. Starting with the core components:

Core Build:
1. CPU: AMD Ryzen 9 5900X
2. Motherboard: ASRock Rack X570D4U (or similar server-grade AM4)
3. Case: Phanteks Enthoo Pro 2
4. RAM: Looking at your virtualization needs, probably 128GB (4x32GB) DDR4 ECC
5. Power Supply: Need something beefy for dual GPUs and all drives - 1000W+ 80+ Gold minimum
6. CPU Cooling: High-end air cooler or 360mm AIO (given the case space)
7. Additional case fans
8. Second GPU for dual VM setup

Parts you mentioned scavenging from current build:
- RTX 2070
- SATA controller card
- Storage drives (2x4TB HDDs, 2x1TB SSDs)

New storage needs:
- NVME drive for Proxmox host OS
- Maybe additional NVME drives for VM storage

Would you like me to break down any of these categories further or focus on specific components? The motherboard choice particularly influences a lot of other decisions.

---

**Human** - 2024-11-03 20:36:33 UTC

Fans, I'm a sucker for those beige and tans. Haha. CPU cooler as well. 

Second GPU will likely take a back seat and come at a later date, favoring more storage. I'd also like a dual 2.5g nic that I can dedicate to truenas.

---

**Assistant** - 2024-11-03 20:36:33 UTC

 Ah, a person of culture with the beige/tan fans! Noctua's classic color scheme is instantly recognizable:

Cooling:
- CPU Cooler: Noctua NH-D15 (that classic beige/brown look, and performs amazingly)
- Case Fans: Noctua NF-A14 (140mm) or NF-A12x25 (120mm) in that signature brown/beige
  - The Enthoo Pro 2 can fit quite a few of these

For the networking:
- A dual-port 2.5GbE card for TrueNAS like the Intel X550-T2 would be solid
  - Could also look at something like a Mellanox ConnectX-3/4 if you want to explore 10GbE later

Storage expansion priorities:
1. NVME for Proxmox host
2. Maybe a separate NVME for VM storage
3. Additional mechanical drives for TrueNAS pool

Going with storage over immediate second GPU makes sense - you can always add the GPU later when prices/availability are better, but having solid storage from the start is crucial for a virtualization host.

Want to dig into any specific component choices or configurations? The Noctua cooling setup in particular would give you plenty of headroom for the 5900X.

---

**Human** - 2024-11-03 20:40:08 UTC

Do you know the fan capacity and arrangement of the pro 2 server? 

I think I have a 140mm that I originally got for my current enthoo case (I forget the model, but it's one of their matx offerings). If that could be worked into an arrangement accounting for appreciate negative pressure inside the case.  I think that one's of their gray/black offerings.

---

**Assistant** - 2024-11-03 20:40:08 UTC

 The Enthoo Pro 2 has pretty extensive fan mounting options:

Front:
- 3x 140mm or 4x 120mm
- Includes 1x 140mm fan

Top:
- 3x 140mm or 4x 120mm

Bottom:
- 3x 140mm or 4x 120mm

Rear:
- 1x 140mm or 120mm
- Includes 1x 140mm fan

Side:
- 3x 140mm or 4x 120mm

For negative pressure (which helps with dust control), you could do something like:

Intake:
- Front: 2-3x 140mm Noctua
- Bottom: 2x 140mm Noctua (good for GPU cooling)

Exhaust:
- Top: 3x 140mm (could use your existing gray/black one here)
- Rear: 1x 140mm Noctua

This would give you slightly more exhaust than intake for that negative pressure, while maintaining good airflow through the whole case. The bottom-to-top path is particularly good for GPU cooling.

The side panel fans are optional - they can be useful if you end up with multiple GPUs later, but aren't necessary for initial setup.

---

**Human** - 2024-11-03 21:04:44 UTC

I wonder. Could I dedicate say, a usb card to a VM and have my own kvm switch essentially?

---

**Assistant** - 2024-11-03 21:04:44 UTC

 Absolutely! That's actually a really clever KVM alternative. You could pass through a dedicated USB PCIe card to a VM and connect your peripherals to it. When you want to switch VMs, you'd just move your peripherals to the USB ports assigned to that VM.

You could set it up like:
- PCIe USB card passed to Windows VM
- Motherboard USB ports for Linux VM
- Or vice versa, depending on your preference

Benefits of this approach:
- Much cheaper than a hardware KVM
- No input lag or compatibility issues
- Clean separation of devices between VMs
- Can hot-plug devices between VMs
- Potentially better compatibility with gaming peripherals

You'd just need:
- A basic PCIe USB card (even USB 3.0 cards are pretty cheap)
- Make sure it has its own IOMMU group
- Enough ports for your peripherals

This is especially nice because you wouldn't have to deal with the quirks of USB-over-IP or similar software solutions. It's just direct hardware passthrough, so it behaves exactly like native USB ports.

---

**Human** - 2024-11-03 21:07:22 UTC

Another twist: the two monitors on that machine have a number of ports and the good ol usb b to a cable to connect to the computer.

I guess what I really would like is some sort of solution to be able to bring my laptop to the desk, and use the keyboard and mouse there, without having to move all of the cables.

---

**Assistant** - 2024-11-03 21:07:22 UTC

 Ah, now I see where you're going! You're basically looking for a modern KVM setup that can handle:
- Desktop VM(s) from the main machine
- Laptop when you bring it to the desk
- Monitors with USB hubs built in
- Single cable switching if possible

There are a few ways you could approach this:

1. USB-C Dock approach:
- Get a good USB-C/Thunderbolt dock
- Connect monitors, keyboard, mouse to dock
- Single cable connect/disconnect for laptop
- Pass the dock connection through to VM when needed

2. Monitor-as-hub approach:
- Use the monitors' built-in USB hubs
- Connect one monitor's USB-B to each VM/system
- Switch monitor inputs and USB connection simultaneously
- Works especially well if monitors have KVM features built in

3. Hybrid approach:
- Use monitor KVM features for video
- Separate USB switch for peripherals
- Could still integrate with VM passthrough

Some modern monitors (especially Dell and LG) have pretty sophisticated KVM features built right in. If your current monitors don't have this, it might be worth considering for future upgrades.

Want to explore any of these approaches in more detail? Knowing your monitor models might help suggest the most elegant solution.

---

**Assistant** - 2024-11-03 21:09:17 UTC

 For software KVM solutions that could handle switching between your desktop VMs and laptop, there are a few options:

1. Barrier (fork of Synergy):
- Open source
- Share mouse/keyboard across machines
- Works across networks
- Clipboard sharing
- But doesn't handle video switching

2. Input-Leap (another Synergy fork):
- Similar features to Barrier
- More active development
- Better security features

3. Looking Glass (for VM switching):
- Low latency VM display capturing
- But only works between VMs, not physical machines

The challenge is that pure software solutions usually can't handle video switching - they're mainly for keyboard/mouse sharing. This is why hardware KVM switches are still popular for full peripheral+display switching.

For your use case, you might want:
1. Hardware KVM switch for complete switching (video, USB, audio)
2. Software KVM (like Barrier) for quick mouse/keyboard sharing when you don't need full switching

Or, as mentioned earlier, some modern monitors have this KVM functionality built in, which might be worth considering for future upgrades since you're already planning a system overhaul.

Want to explore any of these options in more detail?

---

**Human** - 2024-11-03 21:09:17 UTC

Yeah, I'm leaning towards a switch. One desktop and one laptop connection. I just wasn't sure if there were self hosted or hardware androgenous switch software options

---

**Human** - 2024-11-03 21:12:03 UTC

The way I do it right now, I connect one monitor by usb-c (amd laptop so usb4) and then the second port on the laptop I use a usb-c dongle with the wireless mouse and keyboard dongles and a secondary monitor cable for the other monitor. I unplug the dongle and second monitor cable when I switch back to the desktop, which is connected directly to both monitors from the GPU.

---

**Assistant** - 2024-11-03 21:12:03 UTC

 Ah, so currently you're doing the manual shuffle with the dongle and second monitor cable. That's functional but definitely not ideal for frequent switching. Given your current setup:

For a cleaner solution, you could look at:

1. USB-C KVM approach:
- KVM that supports USB-C passthrough for your laptop
- Regular DisplayPort/HDMI for desktop GPU
- Would handle both monitors and peripherals
- Single cable to laptop (utilizing your USB4 port)

2. Modern Display-focused solution:
- Monitor with built-in KVM (like Dell's newer models)
- USB-C connection handles one monitor + peripherals
- Second monitor on regular DisplayPort/HDMI
- Still just one cable to move for laptop

Your current USB4/USB-C setup is actually pretty good - it's just the second monitor and peripheral switching that's cumbersome. The ideal solution would maintain that single USB-C convenience for the laptop while making the desktop switch smoother.

Do you need to maintain USB4 speeds when connected to the laptop, or would USB 3.2 be sufficient? That might affect which KVM options would work best.

---

**Human** - 2024-11-03 21:13:19 UTC

The switch I was looking at had usb-c in for the laptop, and then video in for theonitors from the desktop, and the keyboard and mouse dongles/fobs would be plugged into it.

---

**Assistant** - 2024-11-03 21:13:19 UTC

 That sounds like a solid solution - keeps your USB-C single cable convenience for the laptop while giving you clean switching for everything. If I'm understanding correctly:

Desktop side:
- Direct GPU to monitor connections stay as is
- USB from desktop to switch for peripherals

Laptop side:
- Single USB-C to switch handles everything
- Uses your laptop's USB4 capabilities

Switch handles:
- Keyboard/mouse dongles
- Switching between sources
- No video conversion needed for desktop (which can introduce latency)
- Clean cable management

This is actually pretty elegant because it:
- Maintains direct GPU connection for desktop (best performance)
- Keeps your current laptop USB-C convenience
- Only switches what needs to be switched (peripherals)
- No unnecessary video conversion or potential quality loss
- Simple operation - just hit the switch

Do you have a specific switch model in mind? Some have better features for handling wireless dongles than others.

---

**Human** - 2024-11-03 21:13:57 UTC

Desktop side would go computer >> switch >> monitor

---

**Assistant** - 2024-11-03 21:13:57 UTC

 Ah, I see - so the switch would handle all routing, both video and peripherals:

Desktop:
- Video out to switch
- USB to switch for peripherals

Laptop:
- Single USB-C to switch

Switch then manages:
- Video out to both monitors
- Keyboard/mouse dongles
- Switching between laptop/desktop
- Monitor USB hub connections

This is actually more comprehensive than my previous understanding. The benefit here is:
- Single point of control
- Everything switches together
- No manual cable management
- Clean desk setup
- No direct cable swapping needed

The only potential watch-out might be making sure the switch supports the resolution/refresh rate of your monitors when passing through from the desktop GPU. Some switches can bottleneck high refresh or high resolution displays.

Would you be running the monitors at high refresh rates or above 1440p? That might influence which switches would work best.

---

**Human** - 2024-11-03 21:16:32 UTC

No, I have a KTC(?? I always forget the brand) 27" 1440p and an lg dualup, so it's big and I guess hi res, but only 60hz. The 1440p can run as high as 165, but I mostly do RPG and fantasy style gaming, so I don't need FPS FPS rates. Haha

---

**Assistant** - 2024-11-03 21:16:32 UTC

 The LG DualUp is that interesting 16:18 aspect ratio one right? Something like 2560x2880? It's such a unique monitor choice - great for productivity and document work.

For your setup then:
- KTC 1440p (2560x1440 @ 165Hz potential)
- LG DualUp (2560x2880 @ 60Hz)
- Gaming needs aren't super demanding refresh-rate wise

That's actually pretty friendly for KVM switch compatibility since you're not pushing bleeding edge refresh rates or doing competitive FPS gaming where every millisecond matters. Most decent KVM switches should handle:
- 1440p/60Hz easily
- 1440p/165Hz for when you do want higher refresh
- The DualUp's unusual resolution

The non-standard resolution of the DualUp is probably the most important spec to verify switch compatibility for, but since it's 60Hz, most modern switches should handle it fine.

Your use case (RPGs, productivity) means you won't be as sensitive to any minor input lag a switch might introduce compared to someone playing competitive shooters.

---

**Human** - 2024-11-03 21:17:17 UTC

Yeah, the dualup is a weird one, but I really enjoy it.

---

**Assistant** - 2024-11-03 21:17:17 UTC

 The DualUp is one of those "weird but brilliant" designs. It's like having a pair of stacked 16:9 monitors but without the bezel in the middle. Really nice for:
- Code editing
- Document work
- Web browsing
- Monitoring dashboards
- Having Discord/chat above your game

That 16:18 aspect ratio makes a lot of sense when you think about how much vertical content we deal with these days. Plus, it's easier on the neck than constantly looking left and right with traditional dual monitor setups.

For your KVM setup, its unusual resolution actually works in your favor since you're running it at 60Hz - it's basically just pushing the same bandwidth as a standard 4K@30Hz or 1440p@60Hz signal, which most modern KVMs can handle easily.

Do you run the DualUp in portrait or landscape with your current setup? I've seen some interesting workspace arrangements where people use it alongside a traditional monitor like your KTC.

---

**Human** - 2024-11-03 21:19:54 UTC

I tend to keep whatever my main focus is on the main screen in front of me and the dualup typically splits between (tiling windows ftw) obsidian for notes and task tracking, a timer, a standard clock face, and I'll usually keep a chat or a media player up in the top left. So the top half is one big and two little windows with the smalls vertical split on the right hand side, and then the bottom is sort of daily dashboard as a full size obsidian window.

---

**Assistant** - 2024-11-03 21:19:54 UTC

 That's a really well thought out workspace layout - taking full advantage of Hyprland's tiling and the DualUp's unique form factor. It's like you've created a natural "mission control" setup on the DualUp:

Top section:
- Chat/media (small)
- Time/timer (small)
- Notes/tasks (larger)

Bottom section:
- Full Obsidian dashboard

Then your KTC monitor stays focused on your main task, whether that's:
- Gaming
- Development
- Main workspace

The tiling window management really shines with unusual aspect ratios like the DualUp - you can create these precise layouts that would be awkward to maintain with floating windows. The fact that you can keep persistent workspace tools (timer, notes, chat) visible while maintaining a clean main workspace is pretty elegant.

This kind of setup really shows why good window management (like Hyprland) and thoughtful monitor choices matter more than just raw specs. You've basically created a custom productivity dashboard that's always accessible but not intrusive.

---

**Human** - 2024-11-03 21:21:12 UTC

Swapping workspaces between monitors, etc. so fluid and effortless. 

I'm now beginning to also wrap my brain around tmux and tiling/window/session management in terminal.

---

**Assistant** - 2024-11-03 21:21:12 UTC

 Ah yes, tmux is another layer of tiling goodness! It's especially powerful when you combine it with your existing Hyprland setup. You get:

Terminal management:
- Persistent sessions (detach/reattach)
- Multiple windows within one terminal
- Split panes for different tasks
- Session management across SSH connections

It pairs really well with tiling WMs because:
- You can have dedicated workspaces for different tmux sessions
- Nested tiling (Hyprland managing the windows, tmux managing terminal splits)
- Consistent key bindings once you customize them
- Great for remote work since sessions persist

The DualUp would be perfect for something like:
- Top: tmux session with multiple panes for monitoring/logs
- Bottom: another session for development work
  - Editor in main pane
  - Shell for commands
  - Test output window

Once you get comfortable with tmux, you might find yourself creating different session layouts for different types of work. Like having a dedicated monitoring session, development session, server management session, etc.

Want to dive into any specific tmux configurations or use cases?

---

