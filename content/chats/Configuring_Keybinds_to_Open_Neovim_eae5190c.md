---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Configuring Keybinds to Open Neovim

Created: 2024-11-22 14:16:49 UTC
Updated: 2024-11-22 15:07:14 UTC
UUID: eae5190c-264c-4654-92b6-f2228d34b33a
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-11-22 14:17:10 UTC

Alright, i need a little help with some keybind configs.. 

i would like to use $mainMod + N to open neovim. i think i have to probably do something like kitty -e neovim  as the exec paramater for the keybind?

---

**Assistant** - 2024-11-22 14:17:10 UTC

 For Hyprland, you'll want to add this to your `~/.config/hypr/hyprland.conf`:

```bash
bind = $mainMod, N, exec, kitty -e nvim
```

This assumes:
- `kitty` is your terminal (adjust if using another)
- `nvim` is in your PATH
- `$mainMod` is already defined (typically SUPER/Windows key)

If you want to open to a specific directory:
```bash
bind = $mainMod, N, exec, kitty -e nvim /home/blake
```

---

**Human** - 2024-11-22 14:18:15 UTC

what about using classes? like: --class=editor or whatever the syntax is. how would that work, and what are some things that i could do with that sort of tagging?

---

**Assistant** - 2024-11-22 14:18:15 UTC

 Here's how to use class tagging in Hyprland:

```bash
# In hyprland.conf
bind = $mainMod, N, exec, kitty --class editor -e nvim
windowrule = float, ^(editor)$
windowrule = size 80% 80%, ^(editor)$
windowrule = center, ^(editor)$
```

Common use cases for window classes:
- Floating specific applications
- Custom sizes/positions
- Workspace assignments
- Different borders/opacity
- Special animations

To check a window's class:
```bash
hyprctl clients | grep class
```

Want to see some more specific windowrule examples?

---

**Assistant** - 2024-11-22 14:20:49 UTC

 Here's the config for your workspace 3 setup:

```bash
# Workspace 3 layout rules
windowrule = workspace 3, ^(obsidian)$
windowrule = workspace 3, ^(morgen)$
windowrule = workspace 3, ^(todoist)$

# Zero gaps for Obsidian and Morgen
windowrulev2 = bordersize 0, class:^(obsidian)$
windowrulev2 = bordersize 0, class:^(morgen)$
windowrulev2 = gaps in 0, class:^(obsidian)$
windowrulev2 = gaps in 0, class:^(morgen)$
windowrulev2 = gaps out 0, class:^(obsidian)$
windowrulev2 = gaps out 0, class:^(morgen)$

# Floating Todoist
windowrule = float, ^(todoist)$
windowrule = size 40% 50%, ^(todoist)$
windowrule = center, ^(todoist)$
```

---

**Human** - 2024-11-22 14:20:49 UTC

oh, i like that a lot.. brb. adding now. 

i may do something like that with todoist.. 

my workspace 3 is my "productivity" workspace for lack of a better way of putting it. obsidian, morgen calendar, and todoist. i like having both obsidian and morgen tiled, no gaps in or out, and then totoist floating, probably 40% width and 50% height

---

**Human** - 2024-11-22 14:41:11 UTC

now something that might be slightly more complex: how can i get my neovim dashboard to open centered?


Attachments:
- image.png

---

**Assistant** - 2024-11-22 14:41:11 UTC

 For Hyprland, add this windowrule to center Neovim when launched:

```bash
windowrule = center, ^(neovim)$
# If using kitty with class
windowrule = center, ^(editor)$
```

To get the exact window class being used:
```bash
hyprctl clients | grep class
```

Run this while your Neovim window is open to confirm the correct class name.

---

**Human** - 2024-11-22 14:42:53 UTC

sorry. i should have clarified. the window when it opens is fine.. i think we need to edit some of my nvim config. probably something in alpha.lua for the graphic, and i'm honestly not sure which of the plugins is handling the filesystem options.

---

**Assistant** - 2024-11-22 14:42:53 UTC

 For Neovim dashboard centering, you'll need to configure both alpha.nvim and the window layout. Add this to your alpha.nvim config (likely in `alpha.lua`):

```lua
local padding = vim.fn.max { 2, vim.fn.floor(vim.fn.winheight(0) * 0.2) }

require('alpha').setup({
    layout = {
        { type = "padding", val = padding },
        -- your existing sections here
    },
})
```

If you're using dashboard-nvim instead, adjust the `custom_center` option:

```lua
require('dashboard').setup({
    config = {
        header_pad = math.floor(vim.fn.winheight(0) * 0.2),
    }
})
```

Which dashboard plugin are you using? That'll help me provide more specific configuration.

---

**Human** - 2024-11-22 14:43:30 UTC

this is my current: return {
  "goolord/alpha-nvim",
  dependencies = {
    "nvim-tree/nvim-web-devicons",
  },
  config = function()
    local alpha = require("alpha")
    local dashboard = require("alpha.themes.startify")
    dashboard.section.header.val = {
      [[                                                                       ]],
      [[                                                                       ]],
      [[                                                                       ]],
      [[                                                                       ]],
      [[                                                                     ]],
      [[       ████ ██████           █████      ██                     ]],
      [[      ███████████             █████                             ]],
      [[      █████████ ███████████████████ ███   ███████████   ]],
      [[     █████████  ███    █████████████ █████ ██████████████   ]],
      [[    █████████ ██████████ █████████ █████ █████ ████ █████   ]],
      [[  ███████████ ███    ███ █████████ █████ █████ ████ █████  ]],
      [[ ██████  █████████████████████ ████ █████ █████ ████ ██████ ]],
      [[                                                                       ]],
      [[                                                                       ]],
      [[                                                                       ]],
    }
    alpha.setup(dashboard.opts)
  end,
}

---

**Assistant** - 2024-11-22 14:43:30 UTC

 Since you're using alpha.nvim with the startify theme, you'll want to modify the spacing and config. Here's the adjusted config:

```lua
return {
  "goolord/alpha-nvim",
  dependencies = {
    "nvim-tree/nvim-web-devicons",
  },
  config = function()
    local alpha = require("alpha")
    local dashboard = require("alpha.themes.startify")
    
    -- Calculate padding based on window height
    local header_padding = vim.fn.max { 2, vim.fn.floor(vim.fn.winheight(0) * 0.25) }
    
    dashboard.section.header.val = {
      -- Your existing ASCII art
    }
    
    dashboard.section.header.opts.position = "center"
    dashboard.opts.layout = {
      { type = "padding", val = header_padding },
      dashboard.section.header,
      { type = "padding", val = 2 },
      dashboard.section.top_buttons,
      dashboard.section.mru,
      dashboard.section.mru_cwd,
      dashboard.section.bottom_buttons,
    }
    
    alpha.setup(dashboard.opts)
  end,
}
```

This should center your Neovim logo vertically with proportional padding.

---

**Assistant** - 2024-11-22 14:48:31 UTC

 Looking at your config in the previous message, you're using `alpha.themes.startify` which is providing the dashboard layout. The file sections and buttons come from startify's built-in components.

To see these components and their configuration options:

```lua
:lua =require('alpha.themes.startify')
```

Want me to show you how to customize the buttons and MRU file list sections?

---

**Human** - 2024-11-22 14:48:31 UTC

centered the art, now i'm trying to figure out which plugin is responsible for the dashboard.

---

**Human** - 2024-11-22 14:49:23 UTC

well, startify is still left aligned. that's the only issue.

---

**Assistant** - 2024-11-22 14:49:23 UTC

 To center the Startify sections, modify the config to override their position:

```lua
dashboard.section.header.opts.position = "center"
dashboard.section.top_buttons.opts.position = "center"
dashboard.section.mru.opts.position = "center"
dashboard.section.mru_cwd.opts.position = "center"
dashboard.section.bottom_buttons.opts.position = "center"
```

Add this before the `alpha.setup(dashboard.opts)` line.

---

**Human** - 2024-11-22 14:50:20 UTC

below the curly brace above it?

---

**Assistant** - 2024-11-22 14:50:20 UTC

 Yes, add those position settings right after your header definition but before the final `alpha.setup(dashboard.opts)`. Like this:

```lua
    dashboard.section.header.val = {
      -- Your ASCII art
    }
    
    dashboard.section.header.opts.position = "center"
    dashboard.section.top_buttons.opts.position = "center"
    dashboard.section.mru.opts.position = "center"
    dashboard.section.mru_cwd.opts.position = "center"
    dashboard.section.bottom_buttons.opts.position = "center"
    
    alpha.setup(dashboard.opts)
```

---

**Human** - 2024-11-22 14:51:34 UTC

the previous config you gave me looks like this: 

*ascii art*

dashboard.section.header.opts.position = "center" dashboard.opts.layout = { { type = "padding", val = header_padding }, dashboard.section.header, { type = "padding", val = 2 }, dashboard.section.top_buttons, dashboard.section.mru, dashboard.section.mru_cwd, dashboard.section.bottom_buttons, } alpha.setup(dashboard.opts) end,

---

**Assistant** - 2024-11-22 14:51:34 UTC

 Let me show you the complete config structure with both the padding and centering:

```lua
return {
  "goolord/alpha-nvim",
  dependencies = {
    "nvim-tree/nvim-web-devicons",
  },
  config = function()
    local alpha = require("alpha")
    local dashboard = require("alpha.themes.startify")
    
    local header_padding = vim.fn.max { 2, vim.fn.floor(vim.fn.winheight(0) * 0.25) }
    
    dashboard.section.header.val = {
      -- Your ASCII art here
    }
    
    dashboard.section.header.opts.position = "center"
    dashboard.section.top_buttons.opts.position = "center"
    dashboard.section.mru.opts.position = "center"
    dashboard.section.mru_cwd.opts.position = "center"
    dashboard.section.bottom_buttons.opts.position = "center"
    
    dashboard.opts.layout = {
      { type = "padding", val = header_padding },
      dashboard.section.header,
      { type = "padding", val = 2 },
      dashboard.section.top_buttons,
      dashboard.section.mru,
      dashboard.section.mru_cwd,
      dashboard.section.bottom_buttons,
    }
    
    alpha.setup(dashboard.opts)
  end,
}
```

---

**Human** - 2024-11-22 14:52:50 UTC

Failed to run `config` for alpha-nvim                                                                                                                                                                     
                                                                                                                                                                                                          
/home/blake/.config/nvim/lua/plugins/alpha.lua:31: attempt to index field 'opts' (a nil value)                                                                                                            
                                                                                                                                                                                                          
# stacktrace:                                                                                                                                                                                             
  - .config/nvim/lua/plugins/alpha.lua:31 *in* **config**                                                                                                                                                 
  - .config/nvim/init.lua:15

---

**Assistant** - 2024-11-22 14:52:50 UTC

 Let's fix the error. The startify theme needs its sections initialized before setting options. Here's the corrected config:

```lua
return {
  "goolord/alpha-nvim",
  dependencies = {
    "nvim-tree/nvim-web-devicons",
  },
  config = function()
    local alpha = require("alpha")
    local dashboard = require("alpha.themes.startify")
    
    -- Initialize dashboard with default settings first
    local config = dashboard.config
    
    config.layout[1] = { type = "padding", val = 8 }
    config.opts = {
      position = "center",
    }
    
    dashboard.section.header.val = {
      -- Your ASCII art here
    }
    
    alpha.setup(config)
  end,
}
```

---

**Assistant** - 2024-11-22 14:56:37 UTC

 Yes, with this approach you can remove the `dashboard.section` settings. The centering is handled by `config.opts.position = "center"`. The other positioning directives aren't needed since we're modifying the base config directly.

---

**Human** - 2024-11-22 14:56:37 UTC

so i can scrap all of the dashboard.section stuff?

---

**Human** - 2024-11-22 14:59:23 UTC

now we're back to everything on the left.

---

**Assistant** - 2024-11-22 14:59:23 UTC

 Let's try another approach to get everything centered:

```lua
return {
  "goolord/alpha-nvim",
  dependencies = {
    "nvim-tree/nvim-web-devicons",
  },
  config = function()
    local alpha = require("alpha")
    local dashboard = require("alpha.themes.startify")
    
    dashboard.section.header.val = {
      -- Your ASCII art
    }
    
    dashboard.section.header.opts = {
      position = "center",
      hl = "Type",
    }
    
    for _, section in pairs(dashboard.section) do
      if section.opts then
        section.opts.position = "center"
      else
        section.opts = { position = "center" }
      end
    end
    
    alpha.setup(dashboard.opts)
  end,
}
```

This iterates through all sections and ensures they're centered.

---

**Assistant** - 2024-11-22 15:07:14 UTC

 I see - you're actually using the dashboard theme instead of startify. To add vertical padding, modify the layout:

```lua
local header_padding = math.max(2, vim.fn.floor(vim.fn.winheight(0) * 0.2))
dashboard.opts = {
  layout = {
    {type = "padding", val = header_padding},
    dashboard.section.header,
    {type = "padding", val = 2},
    dashboard.section.buttons,
    {type = "padding", val = 2},
  }
}
```

Add this before the `alpha.setup(dashboard.opts)` line.

---

**Human** - 2024-11-22 15:07:14 UTC

while i'm unsure of the specific differences, this config has everything centered.. although to be fair, it's all at the very top, which looks a little silly.. 

return {
  "goolord/alpha-nvim",
  event = "VimEnter",
  config = function()
    local alpha = require("alpha")
    local dashboard = require("alpha.themes.dashboard")
    -- Set header
    dashboard.section.header.val = {
      "                                                     ",
      "  ███╗   ██╗███████╗ ██████╗ ██╗   ██╗██╗███╗   ███╗ ",
      "  ████╗  ██║██╔════╝██╔═══██╗██║   ██║██║████╗ ████║ ",
      "  ██╔██╗ ██║█████╗  ██║   ██║██║   ██║██║██╔████╔██║ ",
      "  ██║╚██╗██║██╔══╝  ██║   ██║╚██╗ ██╔╝██║██║╚██╔╝██║ ",
      "  ██║ ╚████║███████╗╚██████╔╝ ╚████╔╝ ██║██║ ╚═╝ ██║ ",
      "  ╚═╝  ╚═══╝╚══════╝ ╚═════╝   ╚═══╝  ╚═╝╚═╝     ╚═╝ ",
      "                                                     ",
    }
    -- Set menu
    dashboard.section.buttons.val = {
      dashboard.button("e", "  > New File", "<cmd>ene<CR>"),
      dashboard.button("SPC ee", "  > Toggle file explorer", "<cmd>NvimTreeToggle<CR>"),
      dashboard.button("SPC ff", "󰱼  > Find File", "<cmd>Telescope find_files<CR>"),
      dashboard.button("SPC fs", "  > Find Word", "<cmd>Telescope live_grep<CR>"),
      dashboard.button("SPC wr", "󰁯  > Restore Session For Current Directory", "<cmd>SessionRestore<CR>"),
      dashboard.button("q", "  > Quit NVIM", "<cmd>qa<CR>"),
    }
    -- Send config to alpha
    alpha.setup(dashboard.opts)
    -- Disable folding on alpha buffer
    vim.cmd([[autocmd FileType alpha setlocal nofoldenable]])
  end,
}

---

