---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Optimizing Terminal Setup for System Administration

Created: 2024-11-08 16:59:18 UTC
Updated: 2024-11-08 16:59:35 UTC
UUID: 839b2a91-fb3f-4601-8bcc-5be8a7fe2248
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-11-08 16:59:33 UTC

I've got what i think is a pretty interesting idea.. I've been back on some of my servers and vms (mostly command line. debain/ubuntu/alpine). proxmox. docker stuff, nothing crazy but still enough to keep me interested. 

as i also do a bit in coding and have obviously found all of the crazy that people get into with their terminals as it pertains to meshing with a gui, git states, baterry states and whatever other ungodly icons people want to cram into their prompts. 

what would be a good, clean, comprehensive and intuitive setup geared more towards system and server administration, while still retaining a little bit of stlyle, if not from a bit more of a minimal/brutal styling perspective.

---

**Assistant** - 2024-11-08 16:59:33 UTC

 I understand you're looking for a pragmatic yet visually informative terminal setup that prioritizes system administration functionality over pure aesthetics. Let's build this up in layers, focusing on practical utilities first.

1. First, let's set up a minimal but functional prompt using starship, which is lightweight and works across shells:

```bash
paru -S starship
```

Let's create a focused starship config:



<antArtifact identifier="starship-config" type="application/vnd.ant.code" language="toml" title="~/.config/starship.toml">
# ~/.config/starship.toml
format = """
$username\
$hostname\
$directory\
$git_branch\
$cmd_duration\
$status\
$line_break\
$character"""

[username]
format = "[$user]($style)@"
show_always = true

[hostname]
format = "[$hostname]($style) "
ssh_only = false

[directory]
truncation_length = 3
truncate_to_repo = false
format = "[$path]($style) "

[git_branch]
format = "[$branch]($style) "
style = "bright-black"

[cmd_duration]
min_time = 2000
format = "took [$duration]($style) "

[status]
disabled = false
format = "[$status]($style) "

[character]
success_symbol = "[>](green)"
error_symbol = "[>](red)"
</antArtifact>

2. Essential utilities for system administration:

```bash
paru -S \
    btop \         # Modern system monitor
    duf \          # Better df
    dog \          # Modern dig
    ripgrep \      # Better grep
    fd \           # Better find
    delta \        # Better git diff
    bat \          # Better cat
    eza \          # Better ls
    dua-cli        # Better du
```

3. Add these aliases to your shell config:

```bash
# System monitoring
alias df='duf'
alias top='btop'
alias du='dua i'
alias ls='eza --group-directories-first'
alias ll='eza -l --group-directories-first'
alias la='eza -la --group-directories-first'
alias cat='bat --style=plain'
alias grep='rg'
alias find='fd'

# Quick system checks
alias ports='ss -tulanp'
alias mem='free -h'
alias cpu='grep "^cpu" /proc/stat | awk "{usage=($2+$4)*100/($2+$4+$5)} END {print usage}"%'
```

4. For those server connections, add this to your `~/.ssh/config`:

```bash
Host *
    ServerAliveInterval 60
    ServerAliveCountMax 2
    ControlMaster auto
    ControlPath ~/.ssh/control/%r@%h:%p
    ControlPersist 10m
```

Create the control directory:
```bash
mkdir -p ~/.ssh/control
```

This gives you:
- A clean, informative prompt showing essential info
- Modern replacements for core utils that maintain simplicity
- Smart SSH connection handling
- Quick system monitoring capabilities

The setup maintains Unix philosophy while providing modern conveniences. Want me to focus on any particular aspect or add specific functionality?

---

