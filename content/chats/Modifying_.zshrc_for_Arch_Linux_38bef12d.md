---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Modifying .zshrc for Arch Linux

Created: 2024-10-20 11:47:37 UTC
Updated: 2024-10-20 11:49:24 UTC
UUID: 38bef12d-7638-4ca4-949d-3d6dd4e5ea6c
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-10-20 11:47:42 UTC

can you help me modify my .zshrc? 

i'm using a config from someone who runs macOS and obviously my Arch installation doesnt like this line:

---

**Assistant** - 2024-10-20 11:47:42 UTC

 Certainly, I'd be happy to help you modify your .zshrc file. Could you please share the specific line from the .zshrc file that's causing issues on your Arch Linux installation? Once you provide that line, I can suggest how to modify it to work with your Arch system.

Also, it would be helpful to know:

1. What specific error or problem are you encountering?
2. Are there any particular features or functionalities you want to maintain from the macOS configuration?

With this information, I can provide more tailored advice for your Arch Linux setup.

---

**Human** - 2024-10-20 11:49:24 UTC

source $(brew --prefix)/share/zsh-autosuggestions/zsh-autosuggestions.zsh

and these are the errors it throws: 

/home/blake/.config/zshrc/custom/bh-zen:11: command not found: brew
/home/blake/.config/zshrc/custom/bh-zen:source:11: no such file or directory: /share/zsh-autosuggestions/zsh-autosuggestions.zsh

---

**Assistant** - 2024-10-20 11:49:24 UTC

 I see the issue. The configuration is trying to use Homebrew (`brew`), which is a package manager for macOS. Arch Linux doesn't use Homebrew, so we need to adjust this line for your system. Let's modify it to work with Arch Linux:

1. First, we need to install zsh-autosuggestions if you haven't already. On Arch Linux, you can do this using pacman:

   ```
   sudo pacman -S zsh-autosuggestions
   ```

2. After installation, the zsh-autosuggestions script is typically located at `/usr/share/zsh/plugins/zsh-autosuggestions/zsh-autosuggestions.zsh` on Arch Linux.

3. Now, let's modify your .zshrc file. Replace the line:

   ```
   source $(brew --prefix)/share/zsh-autosuggestions/zsh-autosuggestions.zsh
   ```

   with:

   ```
   source /usr/share/zsh/plugins/zsh-autosuggestions/zsh-autosuggestions.zsh
   ```

4. Save the file and restart your terminal or run `source ~/.zshrc` to apply the changes.

This modification should resolve the errors you're seeing. The new line directly sources the zsh-autosuggestions script from the location where it's installed on Arch Linux systems.

If you encounter any other macOS-specific configurations in your .zshrc, feel free to ask, and I'll help you adapt them for Arch Linux.

---

