---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Troubleshooting Starship Prompt Configuration Errors

Created: 2024-10-16 21:04:24 UTC
Updated: 2024-10-20 13:34:06 UTC
UUID: 9b90c0b7-3486-40a6-8597-b82e9597811a
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-10-16 21:04:33 UTC

can you help me figure out what this is trying to tell me? [WARN] - (starship::config): Error in 'Character' at 'use_symbol_for_status': Unknown key
[WARN] - (starship::config): Error in 'Battery' at 'style': Unknown key

---

**Assistant** - 2024-10-16 21:04:33 UTC

 This message appears to be a warning output from the Starship prompt, which is a customizable command-line prompt for various shells. Let's break down the two warnings:

1. `[WARN] - (starship::config): Error in 'Character' at 'use_symbol_for_status': Unknown key`

This warning is indicating that in the Starship configuration, under the 'Character' module, there's a key called 'use_symbol_for_status' that Starship doesn't recognize. This could be due to a typo in your configuration file or using an option that's not available in your current version of Starship.

2. `[WARN] - (starship::config): Error in 'Battery' at 'style': Unknown key`

Similarly, this warning is saying that in the 'Battery' module of your Starship configuration, there's an unknown key called 'style'.

These warnings suggest that there might be some issues in your Starship configuration file (usually located at `~/.config/starship.toml`). It's possible that:

1. You're using configuration options that are outdated or not yet implemented in your version of Starship.
2. There might be typos in your configuration file.
3. You might be using a newer configuration syntax with an older version of Starship.

To resolve these issues, you could:

1. Check your Starship configuration file for any typos.
2. Verify that you're using the correct configuration options as per the Starship documentation for your installed version.
3. Update Starship to the latest version if you're using newer configuration options.

Would you like me to provide more information on how to troubleshoot these Starship configuration issues?

---

**Human** - 2024-10-20 13:34:06 UTC

can you wrap this up to set aliases in .zshrc?
```bash
ld='eza -lD'
lf='eza -lF --color=always | grep -v /'
lh='eza -dl .* --group-directories-first'
ll='eza -al --group-directories-first'
ls='eza -alF --color=always --sort=size | grep -v /'
lt='eza -al --sort=modified'
```
---

**Assistant** - 2024-10-20 13:34:06 UTC

 Certainly. Here's how you can add these aliases to your `.zshrc` file:

<antThinking>This content is a set of shell aliases, which is suitable for an artifact. It's a self-contained piece of configuration that users might want to modify or reuse. I'll create a new artifact for this.</antThinking>

<antArtifact identifier="zsh-eza-aliases" type="application/vnd.ant.code" language="shell" title="Eza aliases for .zshrc">
# Eza aliases
alias ld='eza -lD'
alias lf='eza -lF --color=always | grep -v /'
alias lh='eza -dl .* --group-directories-first'
alias ll='eza -al --group-directories-first'
alias ls='eza -alF --color=always --sort=size | grep -v /'
alias lt='eza -al --sort=modified'
</antArtifact>

To add these aliases to your `.zshrc` file, you can follow these steps:

1. Open your `.zshrc` file in a text editor. It's usually located in your home directory:

   ```
   nano ~/.zshrc
   ```

2. Scroll to the bottom of the file or to a section where you keep your aliases.

3. Paste the aliases from the code block above into your `.zshrc` file.

4. Save the file and exit the text editor. In nano, you can do this by pressing `Ctrl+X`, then `Y`, then `Enter`.

5. To apply the changes, either restart your terminal or run:

   ```
   source ~/.zshrc
   ```

Now you'll be able to use these `eza` aliases in your Zsh shell. These aliases provide various options for listing files and directories using the `eza` command, which is an enhanced alternative to the standard `ls` command.

Would you like me to explain what each of these aliases does?

---

