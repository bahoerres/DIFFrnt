---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Troubleshooting Neovim Setup on Manjaro Sway

Created: 2024-08-07 20:49:51 UTC
Updated: 2024-08-07 21:11:31 UTC
UUID: a15e4bd1-611a-471b-9ba1-c3871eeb2be9
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-08-07 20:50:02 UTC

i feel like, somehow, unsurprisingly, i'm struggling with getting neovim set up and configured.. i'm running a current version of manjaro sway.. 

i've tried getting some theming and dotfiles set up and keep getting this when i try to start: 
Error detected while processing /home/blake/.config/nvim/i
E5113: Error while calling lua chunk: /home/blake/.config/
dule 'lualine' not found:
        no field package.preload['lualine']
        no file './lualine.lua'
        no file '/usr/share/luajit-2.1/lualine.lua'
        no file '/usr/local/share/lua/5.1/lualine.lua'
        no file '/usr/local/share/lua/5.1/lualine/init.lua
        no file '/usr/share/lua/5.1/lualine.lua'
        no file '/usr/share/lua/5.1/lualine/init.lua'
        no file './lualine.so'
        no file '/usr/local/lib/lua/5.1/lualine.so'
        no file '/usr/lib/lua/5.1/lualine.so'
        no file '/usr/local/lib/lua/5.1/loadall.so'
stack traceback:
        [C]: in function 'require'
        /home/blake/.config/nvim/lua/plug/theme.lua:34: in
        [C]: in function 'require'
        /home/blake/.config/nvim/lua/plug/init.lua:31: in 
        [C]: in function 'require'
        /home/blake/.config/nvim/init.lua:1: in main chunk

---

**Assistant** - 2024-08-07 20:50:02 UTC

 It looks like you're encountering an error when trying to start Neovim. The error message suggests that Neovim is unable to find the 'lualine' module. Lualine is a popular statusline plugin for Neovim, and it seems it's not properly installed or configured in your setup.

Here are a few steps you can take to troubleshoot and potentially resolve this issue:

1. Check if you have a plugin manager installed:
   Make sure you have a plugin manager like Packer, vim-plug, or lazy.nvim installed and properly configured in your Neovim setup.

2. Install lualine:
   If you're using a plugin manager, make sure you have lualine listed in your plugins and that you've run the installation command for your plugin manager. For example, if you're using Packer, you might have something like this in your config:

   ```lua
   use 'nvim-lualine/lualine.nvim'
   ```

   Then run `:PackerInstall` or the equivalent command for your plugin manager.

3. Check your Neovim configuration:
   Look at the files mentioned in the error message, particularly:
   - `/home/blake/.config/nvim/lua/plug/theme.lua`
   - `/home/blake/.config/nvim/lua/plug/init.lua`
   - `/home/blake/.config/nvim/init.lua`

   Make sure that lualine is being required correctly and that there are no typos in the plugin name.

4. Update your plugins:
   If you've recently changed your Neovim configuration, make sure all your plugins are up to date. Run the update command for your plugin manager (e.g., `:PackerUpdate` for Packer).

5. Check Lua paths:
   The error message lists several paths where Neovim is looking for the lualine module. Make sure that lualine is installed in one of these locations or that your Neovim configuration is pointing to the correct location.

6. Verify Neovim version:
   Ensure that you're running a recent version of Neovim that's compatible with your plugins. You can check your Neovim version by running `nvim --version` in your terminal.

If you continue to have issues after trying these steps, it might be helpful to share your Neovim configuration files, particularly the ones mentioned in the error message. This would allow for a more detailed analysis of the problem.

Would you like me to explain or elaborate on any of these steps?

---

**Human** - 2024-08-07 20:51:35 UTC

okay, let's work from the beginning. i'm basically uneducated in the ways of vim and will need step by step from the ground up.. id imagine that a simple pamac install vim-plug is going to be my first step?

---

**Assistant** - 2024-08-07 20:51:35 UTC

 Absolutely, let's start from the beginning. You're right that we need to set up a plugin manager first, and vim-plug is a good choice. Here's a step-by-step guide to get you started:

1. Install Neovim:
   Since you're using Manjaro, you probably already have Neovim installed. If not, you can install it with:
   ```
   sudo pacman -S neovim
   ```

2. Install vim-plug:
   Instead of using pamac, for Neovim, it's best to install vim-plug directly. Run this command in your terminal:
   ```
   sh -c 'curl -fLo "${XDG_DATA_HOME:-$HOME/.local/share}"/nvim/site/autoload/plug.vim --create-dirs \
       https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'
   ```

3. Create a Neovim configuration file:
   ```
   mkdir -p ~/.config/nvim
   touch ~/.config/nvim/init.vim
   ```

4. Edit the configuration file:
   Open the file with a text editor. For example:
   ```
   nano ~/.config/nvim/init.vim
   ```

5. Add basic vim-plug configuration:
   Add these lines to your init.vim:
   ```vim
   call plug#begin('~/.local/share/nvim/plugged')

   " Add plugins here
   Plug 'nvim-lualine/lualine.nvim'
   Plug 'kyazdani42/nvim-web-devicons'  " Optional, for file icons

   call plug#end()

   " Basic Neovim settings
   set number
   set expandtab
   set tabstop=2
   set shiftwidth=2

   " Lualine configuration
   lua << END
   require('lualine').setup()
   END
   ```

6. Save and exit the editor (in nano, press Ctrl+X, then Y, then Enter).

7. Open Neovim and install the plugins:
   ```
   nvim
   ```
   Once Neovim opens, type `:PlugInstall` and press Enter. This will install the plugins.

8. Restart Neovim:
   Exit Neovim by typing `:q` and pressing Enter, then open it again.

This should give you a basic Neovim setup with vim-plug and lualine installed. The configuration adds line numbers and sets some basic indentation preferences.

If you encounter any issues or have questions about any of these steps, please let me know. Also, if you want to add more features or plugins, we can discuss that as well.

---

**Human** - 2024-08-07 20:53:04 UTC

in .config/nvim is init.lua different than init.vim?

---

**Assistant** - 2024-08-07 20:53:04 UTC

 Yes, `init.lua` and `init.vim` are different, though they serve similar purposes in Neovim:

1. `init.vim`:
   - This is a Vimscript file.
   - It's the traditional configuration file for Vim and Neovim.
   - It uses Vimscript syntax.

2. `init.lua`:
   - This is a Lua file.
   - It's a newer option for configuring Neovim (since Neovim 0.5).
   - It uses Lua syntax, which many find more intuitive and powerful.

Key points:

- Neovim will use either `init.vim` or `init.lua`, not both. If both exist, `init.lua` takes precedence.
- Using `init.lua` allows you to write your entire configuration in Lua, which is generally more performant and offers more advanced programming capabilities.
- However, `init.vim` is still fully supported and might be easier for those already familiar with Vimscript.

If you prefer to use Lua for your configuration (which is becoming increasingly popular in the Neovim community), you can create an `init.lua` instead of `init.vim`. The equivalent basic setup in `init.lua` would look something like this:

```lua
-- Install packer
local install_path = vim.fn.stdpath 'data' .. '/site/pack/packer/start/packer.nvim'
local is_bootstrap = false
if vim.fn.empty(vim.fn.glob(install_path)) > 0 then
  is_bootstrap = true
  vim.fn.system { 'git', 'clone', '--depth', '1', 'https://github.com/wbthomason/packer.nvim', install_path }
  vim.cmd [[packadd packer.nvim]]
end

require('packer').startup(function(use)
  -- Package manager
  use 'wbthomason/packer.nvim'

  use {
    'nvim-lualine/lualine.nvim',
    requires = { 'kyazdani42/nvim-web-devicons', opt = true }
  }

  if is_bootstrap then
    require('packer').sync()
  end
end)

-- Basic settings
vim.opt.number = true
vim.opt.expandtab = true
vim.opt.tabstop = 2
vim.opt.shiftwidth = 2

-- Lualine setup
require('lualine').setup()
```

This Lua configuration uses Packer as the plugin manager instead of vim-plug, as Packer is written in Lua and integrates well with Neovim's Lua ecosystem.

Would you like to proceed with the Lua-based configuration, or stick with the Vimscript version we discussed earlier?

---

**Human** - 2024-08-07 20:54:53 UTC

let's try the .vim route first.. to be safe, i've saved the .lua you just gave me to init.lua.bak

---

**Assistant** - 2024-08-07 20:54:53 UTC

 That's a good approach. Starting with the `.vim` configuration is often easier for beginners and allows you to gradually transition to Lua if you choose to do so later. Let's proceed with setting up your `init.vim` file.

1. First, make sure you've installed vim-plug as mentioned earlier.

2. Now, let's create and edit your `init.vim` file:

   ```
   mkdir -p ~/.config/nvim
   nvim ~/.config/nvim/init.vim
   ```

3. In the Neovim editor, paste the following configuration:

   ```vim
   " Vim-Plug plugin manager setup
   call plug#begin('~/.local/share/nvim/plugged')

   " Plugins
   Plug 'nvim-lualine/lualine.nvim'
   Plug 'kyazdani42/nvim-web-devicons'  " Optional, for file icons

   " Add any other plugins you want here

   call plug#end()

   " Basic settings
   set number          " Show line numbers
   set expandtab       " Use spaces instead of tabs
   set tabstop=2       " 1 tab = 2 spaces
   set shiftwidth=2    " Indentation amount for < and > commands

   " Lualine setup (using Lua within Vimscript)
   lua << END
   require('lualine').setup()
   END
   ```

4. Save the file and exit Neovim:
   - Press `Esc` to ensure you're in normal mode
   - Type `:wq` and press Enter

5. Now, open Neovim again:

   ```
   nvim
   ```

6. Install the plugins by running:

   ```
   :PlugInstall
   ```

   This will open a split window showing the installation progress.

7. After the installation is complete, you can close the split window by pressing `q`.

8. Restart Neovim for all changes to take effect.

At this point, you should have a basic Neovim setup with line numbers, some indentation settings, and the lualine status bar at the bottom.

If you encounter any errors or if something doesn't look right, please let me know, and we can troubleshoot from there. Also, feel free to ask if you want to customize anything or add more functionality to your setup.

---

**Human** - 2024-08-07 20:57:22 UTC

alright. nvim launches with no errors now.

---

**Assistant** - 2024-08-07 20:57:22 UTC

 That's excellent news! You've successfully set up a basic Neovim configuration with vim-plug and lualine. Here's what you've accomplished:

1. Installed vim-plug as your plugin manager
2. Created an `init.vim` configuration file
3. Added lualine and nvim-web-devicons plugins
4. Set up some basic Neovim settings
5. Successfully launched Neovim without errors

Now that you have a working setup, here are some next steps you might consider:

1. Familiarize yourself with basic Vim/Neovim commands if you haven't already.

2. Explore additional plugins that might be useful for your workflow. Some popular ones include:
   - `nvim-treesitter` for better syntax highlighting
   - `telescope.nvim` for fuzzy finding
   - `nvim-lspconfig` for Language Server Protocol support

3. Customize your color scheme. You can add a color scheme plugin like:
   ```vim
   Plug 'folke/tokyonight.nvim'
   ```
   Then set it in your config:
   ```vim
   colorscheme tokyonight
   ```

4. Set up key mappings for frequently used commands.

5. Configure language-specific settings if you're using Neovim for coding.

Do you have any specific features or improvements you'd like to add to your Neovim setup? Or would you like me to explain any part of the current configuration in more detail?

---

**Human** - 2024-08-07 21:00:36 UTC

step three.. while i understand what the commandsve the are trying to do, i don't have the slightest clue where to enter them, how to use them, etc. 

pretend it's my first day

---

**Assistant** - 2024-08-07 21:00:36 UTC

 You're absolutely right, and I apologize for not being clearer. Let's break this down as if it's your very first day using Neovim. I'll guide you through adding a color scheme step by step.

1. First, open your Neovim configuration file:
   - Open a terminal
   - Type this command and press Enter:
     ```
     nvim ~/.config/nvim/init.vim
     ```

2. Once Neovim opens, you'll see your current configuration. We want to add a new plugin and a command to use it. Here's how:

   - Press `i` to enter Insert mode. You should see "-- INSERT --" at the bottom of the screen.
   
   - Use the arrow keys to navigate to the section where your plugins are listed. It should look something like this:
     ```vim
     call plug#begin('~/.local/share/nvim/plugged')
     Plug 'nvim-lualine/lualine.nvim'
     Plug 'kyazdani42/nvim-web-devicons'
     ```

   - On a new line after the existing `Plug` commands, add:
     ```vim
     Plug 'folke/tokyonight.nvim'
     ```

3. Now, let's add the command to use this color scheme:
   
   - Scroll to the bottom of the file using the arrow keys
   - On a new line at the end of the file, add:
     ```vim
     colorscheme tokyonight
     ```

4. Save the changes and exit:
   - Press `Esc` to exit Insert mode
   - Type `:wq` and press Enter. This saves the file and quits Neovim.

5. Now we need to install the new plugin:
   - Open Neovim again by typing `nvim` in the terminal and pressing Enter
   - Once Neovim opens, type `:PlugInstall` and press Enter
   - You'll see a new split window showing the installation progress
   - When it's done, press `q` to close this window

6. Finally, to see your new color scheme:
   - Quit Neovim by typing `:q` and pressing Enter
   - Open it again by typing `nvim` in the terminal

You should now see Neovim with the new TokyoNight color scheme applied.

Remember:
- `i` enters Insert mode, allowing you to type and edit text
- `Esc` exits Insert mode
- Commands in Neovim start with `:`
- `:w` saves, `:q` quits, `:wq` saves and quits

Let me know if any part of this process is unclear or if you encounter any issues!

---

**Human** - 2024-08-07 21:01:34 UTC

i'd really love to have it run gruvbox as the rest of me theme is oriented around that. i have dotfiles from the theme, but haven't gotten them to work.

---

**Assistant** - 2024-08-07 21:01:34 UTC

 Certainly! Let's set up Gruvbox for your Neovim configuration. Gruvbox is a popular color scheme, and it's easy to implement. Here's how we'll do it:

1. Open your Neovim configuration file:
   ```
   nvim ~/.config/nvim/init.vim
   ```

2. Once in Neovim, press `i` to enter Insert mode.

3. In the plugin section of your `init.vim`, add the Gruvbox plugin. Look for the section that starts with `call plug#begin` and add this line:
   ```vim
   Plug 'morhetz/gruvbox'
   ```

4. Now, let's configure Neovim to use Gruvbox. At the end of your `init.vim` file, add these lines:
   ```vim
   " Gruvbox configuration
   set background=dark  " Use the dark version of Gruvbox
   colorscheme gruvbox  " Set the colorscheme to Gruvbox
   ```

5. Save and exit the file:
   - Press `Esc` to exit Insert mode
   - Type `:wq` and press Enter

6. Now, let's install the new plugin:
   - Open Neovim again by typing `nvim` in the terminal
   - Once Neovim opens, type `:PlugInstall` and press Enter
   - When it's done, press `q` to close the installation window

7. Restart Neovim to see the changes:
   - Type `:q` and press Enter to quit Neovim
   - Open it again by typing `nvim` in the terminal

You should now see Neovim with the Gruvbox color scheme applied.

If you have Gruvbox dotfiles for other applications, they won't directly affect Neovim. Neovim uses its own configuration. However, if you want to fine-tune the Gruvbox theme in Neovim, you can add more configuration options. For example:

```vim
" Add these lines before setting the colorscheme
let g:gruvbox_contrast_dark = 'hard'
let g:gruvbox_italic = 1
```

These options set a harder contrast for the dark theme and enable italics.

If you encounter any issues or if the colors don't look right, please let me know, and we can troubleshoot further. Also, if you want to adjust any specific colors or settings in the Gruvbox theme, feel free to ask!

---

**Assistant** - 2024-08-07 21:04:52 UTC

 This error typically occurs when Git is trying to access a repository but doesn't have the necessary credentials, and it can't prompt for them because it's being run in a non-interactive mode (which is the case when Vim-Plug is installing plugins).

Here's how we can resolve this:

1. First, let's ensure you have Git installed and configured:
   
   Open a terminal and run:
   ```
   git --version
   ```
   If Git isn't installed, you'll need to install it first.

2. Configure your Git username and email if you haven't already:
   ```
   git config --global user.name "Your Name"
   git config --global user.email "your.email@example.com"
   ```

3. For GitHub repositories, it's best to use SSH instead of HTTPS. Let's set up SSH for GitHub:

   a. Generate an SSH key if you don't have one:
      ```
      ssh-keygen -t ed25519 -C "your.email@example.com"
      ```
      Press Enter to accept the default file location and optionally set a passphrase.

   b. Start the SSH agent:
      ```
      eval "$(ssh-agent -s)"
      ```

   c. Add your SSH key to the agent:
      ```
      ssh-add ~/.ssh/id_ed25519
      ```

   d. Copy your public key:
      ```
      cat ~/.ssh/id_ed25519.pub
      ```
      Copy the output.

   e. Go to GitHub in your web browser, go to Settings > SSH and GPG keys > New SSH key, and paste your key there.

4. Now, let's modify your Neovim configuration to use SSH for the Gruvbox plugin:

   Open your init.vim:
   ```
   nvim ~/.config/nvim/init.vim
   ```

   Find the line where you added the Gruvbox plugin and change it to:
   ```vim
   Plug 'git@github.com:morhetz/gruvbox.git'
   ```

5. Save and exit (`:wq`), then try installing the plugin again:
   ```
   nvim +PlugInstall
   ```

This should resolve the authentication issue. If you still encounter problems, please let me know, and we can try alternative solutions.

---

**Human** - 2024-08-07 21:04:52 UTC

fatal: could not read Username for 'https://github.com': terminal prompts disabled

---

**Human** - 2024-08-07 21:11:31 UTC

how about pasting into nvim?

---

**Assistant** - 2024-08-07 21:11:31 UTC

 Certainly! Pasting into Neovim can be done in a few different ways, depending on your terminal and system setup. Let's go through the most common methods:

1. Normal paste in Insert mode:
   - Enter Insert mode by pressing `i`
   - Use your terminal's paste shortcut (usually Ctrl+Shift+V on Linux, or Cmd+V on macOS)

2. Paste in Normal mode:
   - In Normal mode, press `"+p` to paste after the cursor
   - Or press `"+P` to paste before the cursor
   (The `"+` refers to the system clipboard)

3. Using Neovim's paste mode:
   - Enter `:set paste` before pasting to avoid auto-indentation issues
   - Paste your content
   - Then enter `:set nopaste` to turn off paste mode

4. Using the command line:
   - You can paste directly when opening a file with Neovim:
     ```
     nvim <<< "$(xclip -o -selection clipboard)"
     ```
   (Replace `xclip -o -selection clipboard` with `pbpaste` on macOS)

5. Mouse middle-click (if enabled):
   - If you have mouse support enabled, you can use middle-click to paste

To make pasting easier, you can add this to your `init.vim`:

```vim
" Enable clipboard support
set clipboard+=unnamedplus
```

This allows you to use `p` and `P` to paste directly from the system clipboard.

Remember, if you're pasting code, it's often best to use the paste mode (method 3) to avoid unexpected formatting.

Is there a specific pasting scenario you're trying to achieve? Let me know if you need more detailed instructions for a particular use case.

---

