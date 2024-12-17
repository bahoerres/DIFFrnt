---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Authenticating LinkedIn on Linux without Phone

Created: 2024-12-08 16:00:31 UTC
Updated: 2024-12-08 16:05:33 UTC
UUID: afb15846-c4b7-4317-a2a3-4dbc0b76598f
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-12-08 16:00:39 UTC

okay, i understand this is a little silly.. i'm trying to log into linkendin from my laptop. i need to register the device and my phone is in the other room so i can't open the app. 

there is an authenticator option that i see, but i don't have anything set up on my laptop (arch, hyprland, fish terminal) in order to use it. i use the google authenticator app on my phone. 

let's get these working together.

---

**Assistant** - 2024-12-08 16:00:39 UTC

 Ah, I understand - you want to set up an authenticator on your Linux machine to work with your existing Google Authenticator. This is actually not silly at all - it's a common situation!

For Arch Linux, I'd recommend installing `oath-toolkit` which can generate TOTP codes compatible with Google Authenticator. Here's how we can set it up:

1. First, install oath-toolkit:
```bash
sudo pacman -s oath-toolkit
```

2. However, to make this work with your existing Google Authenticator setup, you'll need the original secret key that was used when you first set up Google Authenticator with LinkedIn. Unfortunately, if you only scanned the QR code initially without saving the secret key, you'll need to:
   - Either go to LinkedIn's 2FA settings and set up a new authenticator (which will give you a new secret key/QR code)
   - Or look at your Google Authenticator app settings to see if you can export the secret key

Would you like me to proceed with the next steps once you have access to a secret key? We can then set up the TOTP generation on your laptop.

Alternatively, if this is a one-time need, would it be simpler to just walk to the other room to get your phone? I want to make sure we're not overcomplicating a temporary situation!

---

**Human** - 2024-12-08 16:00:55 UTC

the silly part is that i don't want to take the 20 steps to just go get my phone.. haha

---

**Assistant** - 2024-12-08 16:00:55 UTC

 Haha, I totally get it - sometimes those 20 steps feel like 20 miles! I've definitely been there, trying to solve a problem "the hard way" just to avoid getting up.

Want to stick with the tech solution instead of the walking solution? Just let me know and I'll continue with the OATH setup instructions. Though I have to say, by now we've probably spent more time than those 20 steps would have taken... 😄

---

**Human** - 2024-12-08 16:02:10 UTC

well, i figure it'll be nice to have it set up like this anyway. i'm trying to be less reliant/zoned in on my phone (adhd, and just general input decluttering). so while yes, this started out of laziness.. it will absolutely provide benefits in the future

---

**Assistant** - 2024-12-08 16:02:10 UTC

 That's actually a really thoughtful perspective - turning a moment of laziness into an opportunity for better digital hygiene and workflow optimization. Using your desktop for 2FA instead of constantly reaching for your phone can definitely help maintain focus and reduce context switching.

Let's set this up properly then. The tricky part is going to be getting that initial secret key. Since you're wanting to reduce phone dependence, we could:

1. Set up a fresh 2FA configuration in LinkedIn (this would temporarily require your phone to remove the old one)
2. When you get the new QR code/secret key, we can configure it both on your phone (as backup) and on your laptop as the primary

Would you like to proceed with this approach? You'll need to do the phone thing one last time, but then you'll be set up for a more phone-independent workflow going forward.

Also, since you're using fish shell, we could even create a convenient fish function to make generating codes super quick once we're set up.

---

**Human** - 2024-12-08 16:05:33 UTC

if i have to get up in order to do this, that's fine.. i was hoping i could avoid it, but seeing the benefit in the process, i'll do what it takes. haha

so the oauth toolkit to start? i'd also seen things like freeotp and gauth authenticator.

---

**Assistant** - 2024-12-08 16:05:33 UTC

 Yes, let's start with `oath-toolkit` - it's lightweight and works well from the command line, which fits nicely with your Hyprland setup. The other options you mentioned are good too:
- FreeOTP is more of a GUI app
- GAuth is a Chrome/Chromium extension

Since you're running Arch with a terminal-focused workflow, I think `oath-toolkit` makes the most sense. Plus, we can script it easily with fish.

```bash
sudo pacman -S oath-toolkit
```

Once you grab your phone (when you're ready!), we'll need to:
1. Set up a new authenticator config in LinkedIn
2. Save the secret key
3. Set up the TOTP generation on your laptop
4. Create a fish function to make it easy to use

Would you like me to start outlining the fish function while you work up the motivation for those 20 steps? 😄

---

