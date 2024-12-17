# Treesitter Configuration for Neovim

Created: 2024-09-05 21:34:05 UTC
Updated: 2024-09-07 00:05:14 UTC
UUID: abfd756a-f2b4-4779-931f-3b0728a74bcf
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-09-05 21:34:08 UTC

this is in my treesitter setup for nvim

---

**Assistant** - 2024-09-05 21:34:08 UTC

 I'd be happy to take a look at your Treesitter setup for Neovim. Could you please share the relevant code or configuration snippet you're referring to? Once you provide that, I can review it and offer any insights or assistance you might need.

---

**Human** - 2024-09-05 21:34:22 UTC




Attachments:
- image.png

---

**Assistant** - 2024-09-05 21:34:22 UTC

 The error message you're seeing indicates that there are missing required fields in your Treesitter configuration for Neovim. Specifically, it's saying that the 'TSConfig' type is missing several required fields:

1. 'modules'
2. 'sync_install'
3. 'ignore_install'
4. 'auto_inst' (which appears to be cut off, likely 'auto_install')

To resolve this issue, you'll need to add these missing fields to your Treesitter configuration. Here's an example of how you might structure your configuration to include these required fields:

```lua
require'nvim-treesitter.configs'.setup {
  -- A list of parser names, or "all"
  ensure_installed = { "c", "lua", "vim", "vimdoc", "query" },

  -- Install parsers synchronously (only applied to `ensure_installed`)
  sync_install = false,

  -- Automatically install missing parsers when entering buffer
  auto_install = true,

  -- List of parsers to ignore installing (or "all")
  ignore_install = { "javascript" },

  -- Additional configuration options...
}
```

Make sure to adjust the values of these fields according to your preferences:

- `sync_install`: Set to `true` if you want parsers to be installed synchronously.
- `auto_install`: Set to `true` if you want missing parsers to be automatically installed.
- `ignore_install`: List any parsers you don't want to be installed.

If you're still encountering issues after adding these fields, please share your updated configuration, and I'll be happy to help you further.

---

**Human** - 2024-09-05 21:35:24 UTC

return {
  "nvim-treesitter/nvim-treesitter",
  event = { "BufReadPre", "BufNewFile" },
  build = ":TSUpdate",
  dependencies = {
    "windwp/nvim-ts-autotag",
  },
  config = function()
    -- import nvim-treesitter plugin
    local treesitter = require("nvim-treesitter.configs")
    -- configure treesitter
    treesitter.setup({ -- enable syntax highlighting
      highlight = {
        enable = true,
      },
      -- enable indentation
      indent = { enable = true },
      -- enable autotagging (w/ nvim-ts-autotag plugin)
      autotag = {
        enable = true,
      },
      -- ensure these language parsers are installed
      ensure_installed = {
        "json",
        "javascript",
        "typescript",
        "tsx",
        "yaml",
        "html",
        "css",
        "prisma",
        "markdown",
        "markdown_inline",
        "svelte",
        "graphql",
        "bash",
        "lua",
        "vim",
        "dockerfile",
        "gitignore",
        "query",
        "vimdoc",
        "c",
      },
      incremental_selection = {
        enable = true,
        keymaps = {
          init_selection = "<C-space>",
          node_incremental = "<C-space>",
          scope_incremental = false,
          node_decremental = "<bs>",
        },
      },
    })
  end,
}

---

**Assistant** - 2024-09-05 21:35:24 UTC

 Thank you for sharing your Treesitter configuration. The error message you're seeing is due to some missing required fields in the configuration. Let's modify your setup to include these missing fields and resolve the error.

Here's an updated version of your configuration that includes the missing required fields:

```lua
return {
  "nvim-treesitter/nvim-treesitter",
  event = { "BufReadPre", "BufNewFile" },
  build = ":TSUpdate",
  dependencies = {
    "windwp/nvim-ts-autotag",
  },
  config = function()
    -- import nvim-treesitter plugin
    local treesitter = require("nvim-treesitter.configs")
    -- configure treesitter
    treesitter.setup({
      -- enable syntax highlighting
      highlight = {
        enable = true,
      },
      -- enable indentation
      indent = { enable = true },
      -- enable autotagging (w/ nvim-ts-autotag plugin)
      autotag = {
        enable = true,
      },
      -- ensure these language parsers are installed
      ensure_installed = {
        "json", "javascript", "typescript", "tsx", "yaml", "html", "css",
        "prisma", "markdown", "markdown_inline", "svelte", "graphql", "bash",
        "lua", "vim", "dockerfile", "gitignore", "query", "vimdoc", "c",
      },
      -- Automatically install missing parsers when entering buffer
      auto_install = true,
      -- List of parsers to ignore installing (or "all")
      ignore_install = {},
      -- Install parsers synchronously (only applied to `ensure_installed`)
      sync_install = false,
      incremental_selection = {
        enable = true,
        keymaps = {
          init_selection = "<C-space>",
          node_incremental = "<C-space>",
          scope_incremental = false,
          node_decremental = "<bs>",
        },
      },
    })
  end,
}
```

The main changes I've made to address the error are:

1. Added `auto_install = true`: This enables automatic installation of missing parsers.
2. Added `ignore_install = {}`: This is an empty list, meaning no parsers are ignored for installation.
3. Added `sync_install = false`: This means parsers won't be installed synchronously.

These additions should resolve the "Missing required fields" error you were seeing. The `modules` field mentioned in the error message is not typically required in recent versions of nvim-treesitter, so I've omitted it. If you still encounter issues, you might need to add it as `modules = {}`.

With these changes, your Treesitter configuration should work without errors. The configuration maintains all your original settings while adding the required fields to satisfy the `TSConfig` type requirements.

---

**Human** - 2024-09-05 21:36:59 UTC

i keep getting a tsserver is deprecated error, but i can't figure out which config is calling it.

---

**Assistant** - 2024-09-05 21:36:59 UTC

 The error you're encountering about TSServer being deprecated is likely related to your TypeScript setup in Neovim, rather than directly in your Treesitter configuration. This error typically occurs when using an older language server setup or plugin that's still referencing the deprecated TSServer.

To track down the source of this error, you can try the following steps:

1. Check your LSP configuration:
   Look for any configurations related to TypeScript or JavaScript. You might be using a plugin like `nvim-lspconfig` to set up language servers.

2. Search for 'tsserver' in your Neovim config files:
   Use a command like `grep -R "tsserver" ~/.config/nvim/` (adjust the path if your config is elsewhere) to find any mentions of tsserver in your configuration files.

3. Check your plugin manager setup:
   Look for any TypeScript-related plugins that might be configuring TSServer.

4. Examine your init.lua or init.vim:
   There might be a direct configuration of TSServer there.

5. Use Neovim's :verbose command:
   You can try `:verbose set omnifunc?` in Neovim to see if it gives you information about where TSServer might be configured.

6. Check for outdated plugins:
   Ensure all your Neovim plugins are up to date, especially those related to TypeScript and LSP support.

If you're using a more modern setup, you might want to transition to using `typescript-language-server` instead of the deprecated TSServer. Here's an example of how you might set it up using `nvim-lspconfig`:

```lua
local lspconfig = require('lspconfig')
lspconfig.tsserver.setup{}
```

If you can't find the source of the TSServer configuration, it would be helpful to see more of your Neovim configuration, especially parts related to LSP setup and TypeScript support. With that information, I could provide more specific guidance on resolving the deprecated TSServer issue.

---

**Assistant** - 2024-09-05 21:45:55 UTC

 Thank you for providing that configuration snippet. You're right, and I apologize for the confusion earlier. The issue is indeed in your Mason LSP configuration. Let's address both problems:

1. The deprecated TSServer error
2. The invalid option for `ts_ls`

Here's how we can correct this:

1. Replace `ts_ls` with `tsserver`:
   The correct name for the TypeScript/JavaScript language server in Mason is `tsserver`, not `ts_ls`. This change should resolve both the deprecation warning and the invalid option error.

2. Update your configuration:

```lua
mason_lspconfig.setup({
    ensure_installed = {
        "tsserver",  -- Changed from "ts_ls"
        "html",
        "cssls",
        "tailwindcss",
        "svelte",
        "lua_ls",
        "graphql",
        "emmet_ls",
        "prismals",
        "pyright",
    },
})
```

This change should resolve the immediate issues you're facing. The `tsserver` option will install and use the current, non-deprecated version of the TypeScript language server.

If you're still seeing the deprecation warning after making this change, it's possible that:

1. The configuration hasn't been reloaded. Try restarting Neovim or sourcing your configuration file.
2. There might be another part of your configuration still referencing the old TSServer. You might want to search your entire Neovim configuration for any other mentions of "tsserver" or "ts_ls".

If the problem persists after making these changes, please let me know, and we can investigate further. It would be helpful to see any error messages you're getting after this update.

---

**Human** - 2024-09-05 21:45:55 UTC

mason_lspconfig.setup({ -- list of servers for mason to install
			ensure_installed = {
				"ts_ls",
				"html",
				"cssls",
				"tailwindcss",
				"svelte",
				"lua_ls",
				"graphql",
				"emmet_ls",
				"prismals",
				"pyright",
			},
		})


it was right here.. eventho i was instructed to use ts_ls it's now saying that's not a valid option for that section, AND the initial error persists.

---

**Human** - 2024-09-05 21:47:32 UTC

changed back to tss server as you advised, :wqa and then restarted to the same error: 

                                                                                                                                                                                                        
tsserver is deprecated, use ts_ls instead.                                                                                                                                                              
Feature will be removed in lspconfig 0.2.0                                                                                                                                                              
Press ENTER or type command to continue

---

**Assistant** - 2024-09-05 21:47:32 UTC

 I apologize for the confusion. It seems the information is conflicting, which suggests there might be version mismatches or recent changes in the language server configurations. Let's try to resolve this step by step:

1. First, let's check your nvim-lspconfig version:
   Open Neovim and run `:lua print(require('lspconfig')._version)` 
   This will tell us which version of lspconfig you're using.

2. Based on the error message, it seems that the latest version of lspconfig is suggesting to use `ts_ls` instead of `tsserver`. Let's update your configuration accordingly:

```lua
mason_lspconfig.setup({
    ensure_installed = {
        "ts_ls",  -- Changed back to "ts_ls"
        "html",
        "cssls",
        "tailwindcss",
        "svelte",
        "lua_ls",
        "graphql",
        "emmet_ls",
        "prismals",
        "pyright",
    },
})
```

3. After making this change, also ensure that your lspconfig setup for TypeScript is using `ts_ls`:

```lua
local lspconfig = require('lspconfig')
lspconfig.ts_ls.setup{}  -- Use ts_ls instead of tsserver
```

4. Update your plugins:
   If you're using a plugin manager like Packer or vim-plug, make sure to update all your plugins, especially nvim-lspconfig and mason.nvim.

5. Clear any caches:
   Sometimes, Neovim or your plugins might cache configurations. Try removing any cache directories (usually in `~/.cache/nvim/` or similar) and then restart Neovim.

6. Check Mason installation:
   Run `:Mason` in Neovim and ensure that `ts_ls` is installed correctly.

If you're still encountering issues after these steps, please provide the following information:

1. The output of `:lua print(require('lspconfig')._version)`
2. The output of `:Mason` (look for the TypeScript language server)
3. Any error messages you see when opening a TypeScript file

This information will help us pinpoint the exact cause of the persistent error and find a solution that works with your specific setup.

---

**Human** - 2024-09-05 21:48:59 UTC

worth noting, this is in my mason.lua file.. that was the only mention of tsserver from the previous grep command

---

**Assistant** - 2024-09-05 21:48:59 UTC

 Thank you for that clarification. It's helpful to know that this configuration is in your mason.lua file and that it's the only mention of tsserver from your previous search.

Given this context and the persistent error message, let's try to resolve this issue:

1. Update your mason.lua file:
   Since the error message is specifically recommending to use `ts_ls` instead of `tsserver`, let's make that change in your Mason configuration:

   ```lua
   mason_lspconfig.setup({
       ensure_installed = {
           "ts_ls",  -- Changed from "tsserver" to "ts_ls"
           "html",
           "cssls",
           "tailwindcss",
           "svelte",
           "lua_ls",
           "graphql",
           "emmet_ls",
           "prismals",
           "pyright",
       },
   })
   ```

2. Check your LSP configuration:
   Ensure that you're setting up the TypeScript language server correctly in your LSP configuration. This is typically done in a separate file from mason.lua, often named something like lspconfig.lua. It should look something like this:

   ```lua
   local lspconfig = require('lspconfig')
   lspconfig.tsserver.setup{}  -- This line might need to be changed to ts_ls
   ```

   If you find this line, change it to:

   ```lua
   lspconfig.ts_ls.setup{}
   ```

3. Update your plugins:
   Ensure all your Neovim plugins are up to date, especially nvim-lspconfig and mason.nvim. The method to do this depends on your plugin manager.

4. Clear Mason's cache:
   Sometimes Mason can cache old configurations. Try uninstalling and reinstalling the TypeScript language server:
   
   - Open Neovim and run `:MasonUninstall tsserver`
   - Then run `:MasonInstall ts_ls`

5. Restart Neovim:
   After making these changes, completely quit and restart Neovim.

If you're still seeing the deprecation warning after these steps, it would be helpful to get some more information:

1. What version of nvim-lspconfig are you using? (You can check this with `:lua print(require('lspconfig')._version)` in Neovim)
2. What's the output of `:Mason` in Neovim? (Look for the TypeScript language server in the list)
3. Are there any error messages in `:checkhealth` related to LSP or Mason?

With this additional information, we can further diagnose and resolve the issue.

---

**Human** - 2024-09-05 21:50:18 UTC




Attachments:
- {'file_name': 'paste.txt', 'file_size': 5137, 'file_type': 'txt', 'extracted_content': 'return {\n  "neovim/nvim-lspconfig",\n  event = { "BufReadPre", "BufNewFile" },\n  dependencies = {\n    "hrsh7th/cmp-nvim-lsp",\n    { "antosha417/nvim-lsp-file-operations", config = true },\n    { "folke/neodev.nvim", opts = {} },\n  },\n  config = function()\n    -- import lspconfig plugin\n    local lspconfig = require("lspconfig")\n\n    -- import mason_lspconfig plugin\n    local mason_lspconfig = require("mason-lspconfig")\n\n    -- import cmp-nvim-lsp plugin\n    local cmp_nvim_lsp = require("cmp_nvim_lsp")\n\n    local keymap = vim.keymap -- for conciseness\n\n    vim.api.nvim_create_autocmd("LspAttach", {\n      group = vim.api.nvim_create_augroup("UserLspConfig", {}),\n      callback = function(ev)\n        -- Buffer local mappings.\n        -- See `:help vim.lsp.*` for documentation on any of the below functions\n        local opts = { buffer = ev.buf, silent = true }\n\n        -- set keybinds\n        opts.desc = "Show LSP references"\n        keymap.set("n", "gR", "<cmd>Telescope lsp_references<CR>", opts) -- show definition, references\n\n        opts.desc = "Go to declaration"\n        keymap.set("n", "gD", vim.lsp.buf.declaration, opts) -- go to declaration\n\n        opts.desc = "Show LSP definitions"\n        keymap.set("n", "gd", "<cmd>Telescope lsp_definitions<CR>", opts) -- show lsp definitions\n\n        opts.desc = "Show LSP implementations"\n        keymap.set("n", "gi", "<cmd>Telescope lsp_implementations<CR>", opts) -- show lsp implementations\n\n        opts.desc = "Show LSP type definitions"\n        keymap.set("n", "gt", "<cmd>Telescope lsp_type_definitions<CR>", opts) -- show lsp type definitions\n\n        opts.desc = "See available code actions"\n        keymap.set({ "n", "v" }, "<leader>ca", vim.lsp.buf.code_action, opts) -- see available code actions, in visual mode will apply to selection\n\n        opts.desc = "Smart rename"\n        keymap.set("n", "<leader>rn", vim.lsp.buf.rename, opts) -- smart rename\n\n        opts.desc = "Show buffer diagnostics"\n        keymap.set("n", "<leader>D", "<cmd>Telescope diagnostics bufnr=0<CR>", opts) -- show  diagnostics for file\n\n        opts.desc = "Show line diagnostics"\n        keymap.set("n", "<leader>d", vim.diagnostic.open_float, opts) -- show diagnostics for line\n\n        opts.desc = "Go to previous diagnostic"\n        keymap.set("n", "[d", vim.diagnostic.goto_prev, opts) -- jump to previous diagnostic in buffer\n\n        opts.desc = "Go to next diagnostic"\n        keymap.set("n", "]d", vim.diagnostic.goto_next, opts) -- jump to next diagnostic in buffer\n\n        opts.desc = "Show documentation for what is under cursor"\n        keymap.set("n", "K", vim.lsp.buf.hover, opts) -- show documentation for what is under cursor\n\n        opts.desc = "Restart LSP"\n        keymap.set("n", "<leader>rs", ":LspRestart<CR>", opts) -- mapping to restart lsp if necessary\n      end,\n    })\n\n    -- used to enable autocompletion (assign to every lsp server config)\n    local capabilities = cmp_nvim_lsp.default_capabilities()\n\n    -- Change the Diagnostic symbols in the sign column (gutter)\n    -- (not in youtube nvim video)\n    local signs = { Error = "\uf057 ", Warn = "\uf071 ", Hint = "\U000f0820 ", Info = "\uf05a " }\n    for type, icon in pairs(signs) do\n      local hl = "DiagnosticSign" .. type\n      vim.fn.sign_define(hl, { text = icon, texthl = hl, numhl = "" })\n    end\n\n    mason_lspconfig.setup_handlers({\n      -- default handler for installed servers\n      function(server_name)\n        lspconfig[server_name].setup({\n          capabilities = capabilities,\n        })\n      end,\n      ["svelte"] = function()\n        -- configure svelte server\n        lspconfig["svelte"].setup({\n          capabilities = capabilities,\n          on_attach = function(client, bufnr)\n            vim.api.nvim_create_autocmd("BufWritePost", {\n              pattern = { "*.js", "*.ts" },\n              callback = function(ctx)\n                -- Here use ctx.match instead of ctx.file\n                client.notify("$/onDidChangeTsOrJsFile", { uri = ctx.match })\n              end,\n            })\n          end,\n        })\n      end,\n      ["graphql"] = function()\n        -- configure graphql language server\n        lspconfig["graphql"].setup({\n          capabilities = capabilities,\n          filetypes = { "graphql", "gql", "svelte", "typescriptreact", "javascriptreact" },\n        })\n      end,\n      ["emmet_ls"] = function()\n        -- configure emmet language server\n        lspconfig["emmet_ls"].setup({\n          capabilities = capabilities,\n          filetypes = { "html", "typescriptreact", "javascriptreact", "css", "sass", "scss", "less", "svelte" },\n        })\n      end,\n      ["lua_ls"] = function()\n        -- configure lua server (with special settings)\n        lspconfig["lua_ls"].setup({\n          capabilities = capabilities,\n          settings = {\n            Lua = {\n              -- make the language server recognize "vim" global\n              diagnostics = {\n                globals = { "vim" },\n              },\n              completion = {\n                callSnippet = "Replace",\n              },\n            },\n          },\n        })\n      end,\n    })\n  end,\n}'}
- paste.txt

---

**Assistant** - 2024-09-05 21:50:18 UTC

 Thank you for sharing your LSP configuration. I see that you're using `mason-lspconfig` to set up your language servers. Let's address the TypeScript server issue within this context:

1. First, in your `mason.lua` file (which you mentioned earlier), change `tsserver` to `typescript-language-server`:

   ```lua
   mason_lspconfig.setup({
       ensure_installed = {
           "typescript-language-server",  -- Changed from "tsserver" or "ts_ls"
           "html",
           "cssls",
           "tailwindcss",
           "svelte",
           "lua_ls",
           "graphql",
           "emmet_ls",
           "prismals",
           "pyright",
       },
   })
   ```

2. In your shared configuration, add a specific handler for the TypeScript server. Add this to your `mason_lspconfig.setup_handlers` section:

   ```lua
   mason_lspconfig.setup_handlers({
     -- ... other handlers ...

     ["typescript-language-server"] = function()
       lspconfig["tsserver"].setup({
         capabilities = capabilities,
         -- You can add more specific settings here if needed
       })
     end,

     -- ... rest of your handlers ...
   })
   ```

3. Make sure you have the TypeScript language server installed via Mason. You can do this by running `:MasonInstall typescript-language-server` in Neovim.

4. After making these changes, restart Neovim and try opening a TypeScript file.

These changes should resolve the deprecation warning and ensure that you're using the correct and up-to-date TypeScript language server.

If you're still encountering issues after making these changes, please provide the following information:

1. The output of `:LspInfo` when you have a TypeScript file open.
2. The output of `:Mason` (look for the TypeScript language server in the list).
3. Any error messages you see in the Neovim command line or in `:checkhealth`.

This additional information will help us further diagnose and resolve any persistent issues.

---

**Human** - 2024-09-05 22:05:30 UTC

it's something different.. doing some reading over on the ol' github.. 

	{
		"williamboman/mason.nvim",
		dependencies = {
			"williamboman/mason-lspconfig.nvim",
			"neovim/nvim-lspconfig",
			"hrsh7th/nvim-cmp",
		},
		config = function()
			require("mason").setup()
			require("mason-lspconfig").setup({
				ensure_installed = {
					"lua_ls",
					"pyright",
					"ruff_lsp",
					"tsserver",
					"eslint",
					"tailwindcss",
					"emmet_language_server",
					"jsonls",
				},
			})
			require("mason-lspconfig").setup()
			-- automatically install ensure_installed servers
			require("mason-lspconfig").setup_handlers({
				-- Will be called for each installed server that doesn't have
				-- a dedicated handler.
				--
				function(server_name) -- default handler (optional)
					-- https://github.com/neovim/nvim-lspconfig/pull/3232
					if server_name == "tsserver" then
						server_name = "ts_ls"
					end
					local capabilities = require("cmp_nvim_lsp").default_capabilities()
					require("lspconfig")[server_name].setup({
						capabilities = capabilities,
					})
				end,
			}) 

is one snippet i've found, but also one commenter recommended this which seems much more simple.. 

if server_name == "tsserver" then
    server_name = "ts_ls"
end

but i'm unsure of where to modify, for either.

---

**Assistant** - 2024-09-05 22:05:30 UTC

 Thank you for sharing that information. You're right, the simpler solution seems more appropriate for your case. Let's implement this change in your existing configuration. 

Based on the configuration you shared earlier, you can modify your `mason_lspconfig.setup_handlers` section in your LSP configuration file (which you shared) as follows:

```lua
mason_lspconfig.setup_handlers({
  -- default handler for installed servers
  function(server_name)
    -- Add this condition before setting up the server
    if server_name == "tsserver" then
      server_name = "ts_ls"
    end
    lspconfig[server_name].setup({
      capabilities = capabilities,
    })
  end,
  
  -- ... rest of your specific handlers ...
})
```

This change should be made in the same file where you have your other LSP configurations (the file you shared in your previous message).

Also, update your `mason.lua` file to ensure you're installing the correct server:

```lua
mason_lspconfig.setup({
    ensure_installed = {
        "ts_ls",  -- Changed from "tsserver"
        "html",
        "cssls",
        "tailwindcss",
        "svelte",
        "lua_ls",
        "graphql",
        "emmet_ls",
        "prismals",
        "pyright",
    },
})
```

After making these changes:

1. Save both files.
2. Restart Neovim completely.
3. Run `:MasonInstall ts_ls` to ensure the new server is installed.
4. Open a TypeScript file and check if the error persists.

This solution should resolve the deprecation warning by using the new `ts_ls` server name while maintaining compatibility with configurations that might still reference `tsserver`.

If you're still experiencing issues after these changes, please let me know, and we can investigate further. It might be helpful to see the output of `:LspInfo` when you have a TypeScript file open after making these changes.

---

**Human** - 2024-09-05 22:20:05 UTC

alright. for our next trick. i'm going to hopefully have you help merge a colorscheme into a lualine config file.. attached is a css file, below is the lualine config. 

return {
  "nvim-lualine/lualine.nvim",
  dependencies = { "nvim-tree/nvim-web-devicons" },
  config = function()
    local lualine = require("lualine")
    local lazy_status = require("lazy.status") -- to configure lazy pending updates count
    local colors = {
      blue = "#65D1FF",
      green = "#3EFFDC",
      violet = "#FF61EF",
      yellow = "#FFDA7B",
      red = "#FF4A4A",
      fg = "#c3ccdc",
      bg = "#112638",
      inactive_bg = "#2c3043",
    }
    local my_lualine_theme = {
      normal = {
        a = { bg = colors.blue, fg = colors.bg, gui = "bold" },
        b = { bg = colors.bg, fg = colors.fg },
        c = { bg = colors.bg, fg = colors.fg },
      },
      insert = {
        a = { bg = colors.green, fg = colors.bg, gui = "bold" },
        b = { bg = colors.bg, fg = colors.fg },
        c = { bg = colors.bg, fg = colors.fg },
      },
      visual = {
        a = { bg = colors.violet, fg = colors.bg, gui = "bold" },
        b = { bg = colors.bg, fg = colors.fg },
        c = { bg = colors.bg, fg = colors.fg },
      },
      command = {
        a = { bg = colors.yellow, fg = colors.bg, gui = "bold" },
        b = { bg = colors.bg, fg = colors.fg },
        c = { bg = colors.bg, fg = colors.fg },
      },
      replace = {
        a = { bg = colors.red, fg = colors.bg, gui = "bold" },
        b = { bg = colors.bg, fg = colors.fg },
        c = { bg = colors.bg, fg = colors.fg },
      },
      inactive = {
        a = { bg = colors.inactive_bg, fg = colors.semilightgray, gui = "bold" },
        b = { bg = colors.inactive_bg, fg = colors.semilightgray },
        c = { bg = colors.inactive_bg, fg = colors.semilightgray },
      },
    }
    -- configure lualine with modified theme
    lualine.setup({
      options = {
        theme = my_lualine_theme,
      },
      sections = {
        lualine_x = {
          {
            lazy_status.updates,
            cond = lazy_status.has_updates,
            color = { fg = "#ff9e64" },
          },
          { "encoding" },
          { "fileformat" },
          { "filetype" },
        },
      },
    })
  end,
}


Attachments:
- {'file_name': 'theme.css', 'file_size': 82042, 'file_type': 'text/css', 'extracted_content': '/**=================================================================================\n/** ██████╗░██████╗░██╗░░░██╗░█████╗░███╗░░██╗██╗░██████╗\n/** ██╔══██╗██╔══██╗╚██╗░██╔╝██╔══██╗████╗░██║╚█║██╔════╝\n/** ██████╦╝██████╔╝░╚████╔╝░███████║██╔██╗██║░╚╝╚█████╗░\n/** ██╔══██╗██╔══██╗░░╚██╔╝░░██╔══██║██║╚████║░░░░╚═══██╗\n/** ██████╦╝██║░░██║░░░██║░░░██║░░██║██║░╚███║░░░██████╔╝\n/** ╚═════╝░╚═╝░░╚═╝░░░╚═╝░░░╚═╝░░╚═╝╚═╝░░╚══╝░░░╚═════╝░\n/**\n/** ░█████╗░██████╗░░██████╗██╗██████╗░██╗░█████╗░███╗░░██╗\u2003\u2003░█████╗░░██████╗░██████╗\n/** ██╔══██╗██╔══██╗██╔════╝██║██╔══██╗██║██╔══██╗████╗░██║\u2003\u2003██╔══██╗██╔════╝██╔════╝\n/** ██║░░██║██████╦╝╚█████╗░██║██║░░██║██║███████║██╔██╗██║\u2003\u2003██║░░╚═╝╚█████╗░╚█████╗░\n/** ██║░░██║██╔══██╗░╚═══██╗██║██║░░██║██║██╔══██║██║╚████║\u2003\u2003██║░░██╗░╚═══██╗░╚═══██╗\n/** ╚█████╔╝██████╦╝██████╔╝██║██████╔╝██║██║░░██║██║░╚███║\u2003\u2003╚█████╔╝██████╔╝██████╔╝\n/** ░╚════╝░╚═════╝░╚═════╝░╚═╝╚═════╝░╚═╝╚═╝░░╚═╝╚═╝░░╚══╝\u2003\u2003░╚════╝░╚═════╝░╚═════╝░\n/**==================================================================================*/\n\n/** ----- TABLE OF CONTENTS ----- */\n\n/** 1. Default Theme */\n/** 2. Custom CSS Section */\n/** ____ 2.1 Bullet Points */\n/** ________ 2.1.1 Bullet Point Relationship Lines -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/2 */\n/** ________ 2.1.2 tasklist (preview) indentation lines correction -- https://forum.obsidian.md/t/bullet-lines-in-css-for-checkboxes/6262/3 */\n/** ________ 2.1.3 Better Bullet Points In Edit Mode https://forum.obsidian.md/t/clutter-free-edit-mode/6791/30 */\n/** ________ 2.1.4 Bullet points in preview -- https://discord.com/channels/686053708261228577/702656734631821413/772094128832905226 */\n/** ________ 2.1.5 Bullet List Boxing -- https://discord.com/channels/686053708261228577/702656734631821413/784610806561636413 */\n/** ____ 2.2 File Navigation Pane */\n/** ________ 2.2.1 Relationship lines for the folder levels in file navigation: https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/112 */\n/** ________ 2.2.2 Custom icons differing files and folders -- https://discordapp.com/channels/686053708261228577/702656734631821413/755293685046050896 */\n/** ________ 2.2.3 Top Level Folder Icons -- https://discord.com/channels/686053708261228577/702656734631821413/805318111917113354 */\n/** ________ 2.2.4 Outline Relationship lines -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/357 */\n/** ________ 2.2.5 Image file navigation icon -- https://discord.com/channels/686053708261228577/702656734631821413/866399284437843978 */\n/** ____ 2.3 Clutter Free Mode */\n/** ________ 2.3.1 Make subtler folding gutter arrows -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/10 */\n/** ________ 2.3.2 Hide Block Reference ID\'s -- https://discord.com/channels/686053708261228577/716028884885307432/769267134114037871 */\n/** ________ 2.3.3 Shortened Url Links -- https://forum.obsidian.md/t/hide-or-truncate-urls-in-editor-using-css/359/3 */\n/** ________ 2.3.4 highlight (==) not visible anymore if not active line -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/221 */\n/** ________ 2.3.5 Make code blocks wrap in preview mode too */\n/** ________ 2.3.6 Hide search query title and stop highlighting found element -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/307 */\n/** ________ 2.3.7 vertically centre line numbers in large paragraphs -- https://discord.com/channels/686053708261228577/702656734631821413/822257712825237524 */\n/** ________ 2.3.8 Fix padding of transcluded blocks in lists */\n/** ________ 2.3.9 Custom Highlight Colors based on templater */\n/** ____ 2.4 Font Formatting */\n/** ________ 2.4.1 Make Mathjax Font Larger */\n/** ________ 2.4.2 Hyphenation & Justification -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/25 */\n/** ________ 2.4.3 Stylish Block Quotes -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/39 */\n/** ________ 2.4.4 General Font Formatting */\n/** ________ 2.4.5 Stylish Signatures -- https://discord.com/channels/686053708261228577/702656734631821413/784210155923177552 */\n/** ____ 2.5 Graph Formatting */\n/** ________ 2.5.1 Graph View CSS -- https://discordapp.com/channels/686053708261228577/702656734631821413/760488978691784705 */\n/** ____ 2.6 Image Manipulation */\n/** ________ 2.6.1 Image Hover Grow -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/29 */\n/** ____ 2.7 Check Boxes */\n/** ________ 2.7.1 Nicer Round Checkboxes -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/34 */\n/** ________ 2.7.2 Animated Check Boxes -- https://github.com/TriDiamond/Obsidian-Obsidianite/blob/82207bed4313ee0e6f0bb1fd59b04129408018f5/obsidian.css#L463 */\n/** ________ 2.7.3 Hide Completed Tasks In Preview -- https://forum.obsidian.md/t/hide-checked-todo-s/14043 */\n/** ____ 2.8 Tags */\n/** ________ 2.8.1 Tag Pills -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/72 */\n/** ________ 2.8.2 Tags to the side of the document -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/327 */\n/** ____ 2.9 [[Link]] Modification */\n/** ________ 2.9.1 Bigger Link Hover Popup Preview -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/175 */\n/** ________ 2.9.2 The modal popups from link hovers */\n/** ________ 2.9.3 Input Links -- https://discord.com/channels/686053708261228577/707816848615407697/844751423253905458 */\n/** ____ 2.10 Plugin Specific CSS */\n/** ________ 2.10.1 Calendar Plugin CSS */\n/** ________ 2.10.2 T0DOIST Plugin CSS -- https://github.com/jamiebrynes7/clair-de-lune-obsidian-theme/blob/master/src/modules/extensions/todoist.scss */\n/** ________ 2.10.3 DayPlanner Plugin CSS */\n/** ________ 2.10.4 Folder Note CSS */\n/** ____ 2.11 Heading Formatting */\n/** ________ 2.11.1 Heading Under Gradient Line -- https://github.com/TriDiamond/Obsidian-Obsidianite */\n/** ________ 2.11.2 Emoji Orientation in Andy Mode Headers -- https://discord.com/channels/686053708261228577/702656734631821413/775900471406624768 */\n/** ________ 2.11.3 Heading Horizontal Lines -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/288?u=tallguyjenks */\n/** ____ 2.12 Horizontal Rule Formatting */\n/** ________ 2.12.1 Aesthetic Horizontal Rule -- https://github.com/TriDiamond/Obsidian-Obsidianite */\n/** ____ 2.13 PDF Export Formatting */\n/** ________ 2.13.1 Page Break -- https://gist.github.com/liamcain/81679412643690a7cdd13dff4dc909ce */\n/** ____ 2.14 Tables */\n/** ________ 2.14.1 Banded Table Rows -- https://discord.com/channels/686053708261228577/702656734631821413/777106171948564500 */\n/** ________ 2.14.2 Full Width Tables */\n/** ________ 2.14.3 Numbered Table Rows-- https://discord.com/channels/686053708261228577/707816848615407697/832558496892846080 */\n/** ____ 2.15 Custom HTML Elements */\n/** ________ 2.15.1 aside format -- https://discord.com/channels/686053708261228577/707816848615407697/784964375806083124 */\n/** ________ 2.15.2 Buttons -- https://discord.com/channels/686053708261228577/744933215063638183/784289179328708648 */\n/** ________ 2.15.3 Definition Lists */\n/** ________ 2.15.4 Code Language Fences -- https://discord.com/channels/686053708261228577/702656734631821413/822915125522202654 */\n/** ________ 2.15.5 Rounded Edges of Inline Code blocks https://discord.com/channels/686053708261228577/702656734631821413/822181163639767081 */\n/** ____ 2.16 Quick Switcher */\n/** ________ 2.16.1 Fix the quick switcher highligher after background color change */\n/** __ 3. Grave Yard */\n/** ============================================================================================================================================================ */\n\n@import url(\'https://fonts.googleapis.com/css2?family=Merriweather&family=Open+Sans&family=Fira+Code&display=swap\');\n\n/** 1. Default Theme */\n:root {\n  --dark0-hard: #1d2021;\n  --dark0: #282828;\n  --dark0-soft: #32302f;\n  --dark1: #3c3836;\n  --dark2: #504945;\n  --dark3: #665c54;\n  --dark4: #7c6f64;\n\n  --gray: #928374;\n\n  --light0-hard: #f9f5d7;\n  --light0: #fbf1c7;\n  --light0-soft: #f2e5bc;\n  --light1: #ebdbb2;\n  --light2: #d5c4a1;\n  --light3: #bdae93;\n  --light4: #a89984;\n\n  --bright-red: #fb4934;\n  --bright-green: #b8bb26;\n  --bright-yellow: #fabd2f;\n  --bright-blue: #83a598;\n  --bright-purple: #d3869b;\n  --bright-aqua: #8ec07c;\n  --bright-orange: #fe8019;\n\n  --neutral-red: #cc241d;\n  --neutral-green: #98971a;\n  --neutral-yellow: #d79921;\n  --neutral-blue: #458588;\n  --neutral-purple: #b16286;\n  --neutral-aqua: #689d6a;\n  --neutral-orange: #d65d0e;\n\n  --faded-red: #9d0006;\n  --faded-green: #79740e;\n  --faded-yellow: #b57614;\n  --faded-blue: #076678;\n  --faded-purple: #8f3f71;\n  --faded-aqua: #427b58;\n  --faded-orange: #af3a03;\n\n  /* These are for: */\n  /** outliner bullet lines fade to color in edit mode -- https://discord.com/channels/686053708261228577/702656734631821413/884586663064535141 */\n  --rgb-faded-red: 157, 0, 6;\n  --rgb-faded-green: 121, 116, 14;\n  --rgb-faded-yellow: 181, 118, 20;\n  --rgb-faded-blue: 7, 102, 120;\n  --rgb-faded-purple: 143, 63, 113;\n  --rgb-faded-aqua: 66, 123, 88;\n  --rgb-faded-orange: 175, 58, 3;\n  --alpha-ad: 0.68;\n  --alpha-65: 0.4;\n}\n\n.theme-dark {\n  --font-serif: "Merriweather", Georgia, "Times New Roman", serif;\n  --font-sans-serif: "Inter", "Open Sans", "Helvetica Neue", Arial, sans-serif;\n  --font-monospace: "Fira Code", "Source Code Pro", monospace;\n  --background-primary: var(--dark0);\n  --background-primary-alt: var(--dark0);\n  --background-secondary: var(--dark0-hard);\n  --background-secondary-alt: var(--dark1);\n  --text-normal: var(--light0);\n  --text-faint: var(--light3);\n  --text-title-h1: var(--neutral-red);\n  --text-title-h2: var(--neutral-orange);\n  --text-title-h3: var(--neutral-yellow);\n  --text-title-h4: var(--neutral-green);\n  --text-title-h5: var(--neutral-aqua);\n  --text-title-h6: var(--neutral-purple);\n  --text-link: var(--bright-blue);\n  --text-a: var(--bright-orange);\n  --text-a-hover: var(--bright-blue);\n  --text-mark: var(--neutral-yellow);\n  --pre-code: var(--dark1);\n  --text-highlight-bg: var(--faded-aqua);\n  --interactive-accent: var(--bright-orange);\n  --interactive-before: var(--dark4);\n  --background-modifier-border: var(--dark2);\n  --text-accent: var(--bright-orange);\n  --interactive-accent-rgb: var(--bright-orange);\n  --inline-code: var(--bright-blue);\n  --code-block: var(--bright-blue);\n  --vim-cursor: var(--bright-orange);\n  --text-selection: rgba(168, 153, 132, 0.5); /* light4 */\n}\n\nbody, .markdown-preview-view {\n  font-family: var(--font-sans-serif);\n}\n\nh1, h2, h3, h4, h5, h6,\n.cm-header-1, .cm-header-2, .cm-header-3, .cm-header-4, .cm-header-5, .cm-header-6 {\n  font-family: var(--font-serif);\n}\n\ncode, .cm-inline-code, .CodeMirror {\n  font-family: var(--font-monospace);\n}\n\n.serif { font-family: var(--font-serif); }\n.sans-serif { font-family: var(--font-sans-serif); }\n.monospace { font-family: var(--font-monospace); }\n\n.theme-light {\n  --background-primary: var(--light0);\n  --background-primary-alt: var(--light0);\n  --background-secondary: var(--light0-hard);\n  --background-secondary-alt: var(--light1);\n  --text-normal: var(--dark0);\n  --text-faint: var(--dark3);\n  --text-title-h1: var(--faded-red);\n  --text-title-h2: var(--faded-orange);\n  --text-title-h3: var(--faded-yellow);\n  --text-title-h4: var(--faded-green);\n  --text-title-h5: var(--faded-aqua);\n  --text-link: var(--neutral-blue);\n  --text-a: var(--neutral-orange);\n  --text-a-hover: var(--neutral-blue);\n  --text-mark: var(--neutral-yellow);\n  --pre-code: var(--light1);\n  --text-highlight-bg: var(--bright-aqua);\n  --interactive-accent: var(--neutral-orange);\n  --interactive-before: var(--light4);\n  --background-modifier-border: var(--light2);\n  --text-accent: var(--neutral-orange);\n  --interactive-accent-rgb: var(--neutral-orange);\n  --inline-code: var(--neutral-blue);\n  --vim-cursor: var(--neutral-orange);\n  --text-selection: rgba(189, 174, 147, 0.5); /* light3 */\n}\n\n.theme-dark code[class*="language-"],\n.theme-dark pre[class*="language-"],\n.theme-light code[class*="language-"],\n.theme-light pre[class*="language-"] {\n  text-shadow: none !important;\n  background-color: var(--pre-code) !important;\n}\n\n.graph-view.color-circle,\n.graph-view.color-fill-highlight,\n.graph-view.color-line-highlight {\n  color: var(--interactive-accent-rgb) !important;\n}\n.graph-view.color-text {\n  color: var(--text-a-hover) !important;\n}\n/*\n.graph-view.color-fill\n{\n    color: var(--background-secondary);\n}\n.graph-view.color-line\n{\n  color: var(--background-modifier-border);\n}\n*/\n\nhtml,\nbody {\n  font-size: 16px !important;\n  font-family: var(\n    --font-monospace\n  ); /** Remove this to return body font back to normal */\n\n  /** Norse rune font for hilarity Comes from dafont.com */\n  --custom-font: "TrashHand";\n  /* --custom-font: \'fira code\', \'Hack Nerd Font\', \'Source Code Pro\', monospace; */\n  --custom-H1-font-size: 38px;\n  --custom-H2-font-size: 34px;\n  --custom-H3-font-size: 30px;\n  --custom-H4-font-size: 26px;\n  --custom-H5-font-size: 22px;\n  --custom-H6-font-size: 18px;\n  /* --custom-font: var(--font-monospace); */\n  /* font-family: \'Norse\';\n    font-size: 20px !important; */\n}\n\nstrong {\n  font-weight: 600 !important;\n}\n\na,\n.cm-hmd-internal-link {\n  color: var(--text-a) !important;\n  text-decoration: none !important;\n}\n\na:hover,\n.cm-hmd-internal-link:hover,\n.cm-url {\n  color: var(--text-a-hover) !important;\n  text-decoration: none !important;\n}\n\nmark {\n  background-color: var(--text-mark) !important;\n  color: var(--dark0) !important;\n}\n\n.view-actions a {\n  color: var(--text-normal) !important;\n}\n\n.view-actions a:hover {\n  color: var(--text-a) !important;\n}\n\n.HyperMD-codeblock-bg {\n  background-color: var(--pre-code) !important;\n}\n\n.HyperMD-codeblock {\n  line-height: 1.4em !important;\n  color: var(--code-block) !important;\n}\n\n.HyperMD-codeblock-begin {\n  border-top-left-radius: 4px !important;\n  border-top-right-radius: 4px !important;\n}\n\n.HyperMD-codeblock-end {\n  border-bottom-left-radius: 4px !important;\n  border-bottom-right-radius: 4px !important;\n}\n\nth {\n  font-weight: 600 !important;\n}\n\nthead {\n  border-bottom: 2px solid var(--background-modifier-border) !important;\n}\n\n.HyperMD-table-row {\n  line-height: normal !important;\n  padding-left: 4px !important;\n  padding-right: 4px !important;\n  background-color: var(--pre-code) !important;\n}\n\n/* .HyperMD-table-row-0 { */\n  /* padding-top: 4px !important; */\n/* } */\n\n.CodeMirror-foldgutter-folded,\n.is-collapsed .nav-folder-collapse-indicator {\n  color: var(--text-a) !important;\n}\n\n.nav-file-tag {\n  color: var(--text-a) !important;\n}\n\n.is-active .nav-file-title {\n  color: var(--text-a) !important;\n  background-color: var(--background-primary-alt) !important;\n}\n\n.nav-file-title {\n  border-bottom-left-radius: 0 !important;\n  border-bottom-right-radius: 0 !important;\n  border-top-left-radius: 0 !important;\n  border-top-right-radius: 0 !important;\n}\n\nimg {\n  display: block !important;\n  margin-left: auto !important;\n  margin-right: auto !important;\n}\n\n.HyperMD-list-line {\n  padding-top: 0 !important;\n}\n.CodeMirror-code,\n.CodeMirror-linenumber,\n.cm-formatting {\n  font-family: var(--font-monospace) !important;\n  font-size: 0.9em;\n}\n\n.markdown-preview-section pre code,\n.markdown-preview-section code {\n  font-size: 0.9em !important;\n  background-color: var(--pre-code) !important;\n}\n\n.markdown-preview-section pre code {\n  padding: 4px !important;\n  line-height: 1.4em !important;\n  display: block !important;\n  color: var(--code-block) !important;\n}\n\n.markdown-preview-section code {\n  color: var(--inline-code) !important;\n}\n\n.cm-s-obsidian,\n.cm-inline-code {\n  -webkit-font-smoothing: auto !important;\n}\n\n.cm-inline-code {\n  color: var(--inline-code) !important;\n  background-color: var(--pre-code) !important;\n  padding: 1px !important;\n}\n\n.workspace-leaf-header-title {\n  font-weight: 600 !important;\n}\n\n.side-dock-title {\n  padding-top: 15px !important;\n  font-size: 20px !important;\n}\n\n.side-dock-ribbon-tab:hover,\n.side-dock-ribbon-action:hover,\n.side-dock-ribbon-action.is-active:hover,\n.nav-action-button:hover,\n.side-dock-collapse-btn:hover {\n  color: var(--text-a);\n}\n\n.side-dock {\n  border-right: 0 !important;\n}\n\n.cm-s-obsidian,\n.markdown-preview-view {\n  /* padding-left: 10px !important; */\n  padding-right: 10px !important;\n}\n\n/* vertical resize-handle */\n.workspace-split.mod-vertical > * > .workspace-leaf-resize-handle,\n.workspace-split.mod-left-split > .workspace-leaf-resize-handle,\n.workspace-split.mod-right-split > .workspace-leaf-resize-handle {\n  width: 1px !important;\n  background-color: var(--background-secondary-alt);\n}\n\n/* horizontal resize-handle */\n.workspace-split.mod-horizontal > * > .workspace-leaf-resize-handle {\n  height: 1px !important;\n  background-color: var(--background-secondary-alt);\n}\n\n/* Remove vertical split padding */\n.workspace-split.mod-root .workspace-split.mod-vertical .workspace-leaf-content,\n.workspace-split.mod-vertical > .workspace-split,\n.workspace-split.mod-vertical > .workspace-leaf,\n.workspace-tabs {\n  padding-right: 0px;\n}\n\n.markdown-embed-title {\n  font-weight: 600 !important;\n}\n\n.markdown-embed {\n  padding-left: 10px !important;\n  padding-right: 10px !important;\n  margin-left: 10px !important;\n  margin-right: 10px !important;\n}\n\n.mermaid .note {\n  fill: var(--dark3) !important;\n}\n\n.cm-header-1,\n.markdown-preview-section h1 {\n  font-weight: 500 !important;\n  font-size: var(--custom-H1-font-size) !important;\n  color: var(--text-title-h1) !important;\n  /*     background: -webkit-linear-gradient(var(--bright-red),var(--faded-red));\n    -webkit-background-clip: text;\n    -webkit-text-fill-color: transparent; */\n  font-family: var(--custom-font) !important;\n}\n\n.cm-header-2,\n.markdown-preview-section h2 {\n  font-weight: 500 !important;\n  font-size: var(--custom-H2-font-size) !important;\n  color: var(--text-title-h2) !important;\n  /*     background: -webkit-linear-gradient(var(--bright-orange),var(--faded-orange));\n    -webkit-background-clip: text;\n    -webkit-text-fill-color: transparent; */\n  font-family: var(--custom-font) !important;\n}\n\n.cm-header-3,\n.markdown-preview-section h3 {\n  font-weight: 500 !important;\n  font-size: var(--custom-H3-font-size) !important;\n  color: var(--text-title-h3) !important;\n  /*     background: -webkit-linear-gradient(var(--bright-yellow),var(--faded-yellow));\n    -webkit-background-clip: text;\n    -webkit-text-fill-color: transparent; */\n  font-family: var(--custom-font) !important;\n}\n\n.cm-header-4,\n.markdown-preview-section h4 {\n  font-weight: 500 !important;\n  font-size: var(--custom-H4-font-size) !important;\n  color: var(--text-title-h4) !important;\n  /*     background: -webkit-linear-gradient(var(--bright-green),var(--faded-green));\n    -webkit-background-clip: text;\n    -webkit-text-fill-color: transparent; */\n  font-family: var(--custom-font) !important;\n}\n\n.cm-header-5,\n.markdown-preview-section h5 {\n  font-weight: 500 !important;\n  font-size: var(--custom-H5-font-size) !important;\n  color: var(--text-title-h5) !important;\n  /*   background: -webkit-linear-gradient(var(--bright-aqua),var(--faded-aqua));\n  -webkit-background-clip: text;\n  -webkit-text-fill-color: transparent; */\n  font-family: var(--custom-font) !important;\n}\n\n.cm-header-6,\n.markdown-preview-section h6 {\n  font-weight: 500 !important;\n  font-size: var(--custom-H6-font-size) !important;\n  color: var(--text-title-h6) !important;\n  /*   background: -webkit-linear-gradient(var(--bright-purple),var(--faded-purple));\n  -webkit-background-clip: text;\n  -webkit-text-fill-color: transparent; */\n  font-family: var(--custom-font) !important;\n}\n\n.suggestion-item.is-selected {\n  background-color: var(--background-secondary);\n}\n\n.empty-state-container:hover {\n  background-color: var(--background-secondary-alt);\n  border: 5px solid var(--interactive-accent) !important;\n}\n\n.checkbox-container {\n  background-color: var(--interactive-before);\n}\n\n.checkbox-container:after {\n  background-color: var(--background-secondary-alt);\n}\n\n.mod-cta {\n  color: var(--background-secondary-alt) !important;\n  font-weight: 600 !important;\n}\n\n.mod-cta:hover {\n  background-color: var(--interactive-before) !important;\n  font-weight: 600 !important;\n}\n\n.CodeMirror-cursor {\n  background-color: var(--vim-cursor) !important;\n  opacity: 60% !important;\n}\n\ninput.task-list-item-checkbox {\n  border: 1px solid var(--dark4);\n  appearance: none;\n  -webkit-appearance: none;\n}\n\ninput.task-list-item-checkbox:checked {\n  background-color: var(--dark4);\n  box-shadow: inset 0 0 0 2px var(--background-primary);\n}\n\n::selection {\n  background-color: var(--text-selection) !important;\n}\n\n/** .. 2. Custom CSS Section */\n/** ____ 2.1 Bullet Points */\n/** ______ 2.1.1 Bullet Point Relationship Lines -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/2 */\n.cm-hmd-list-indent .cm-tab,\nul ul {\n  position: relative;\n}\n.cm-hmd-list-indent .cm-tab::before,\nul ul::before {\n  content: "";\n  border-left: 1px solid var(--bright-aqua);\n  position: absolute;\n}\n.cm-hmd-list-indent .cm-tab::before {\n  left: 5px;\n  top: -5px;\n  bottom: -4px;\n}\nul ul::before {\n  left: -16px;\n  top: 0;\n  bottom: 0;\n}\n.cm-hmd-list-indent .cm-tab,\nol ol {\n  position: relative;\n}\n.cm-hmd-list-indent .cm-tab::before,\nol ol::before {\n  content: "";\n  border-left: 1px solid var(--bright-aqua);\n  position: absolute;\n}\n.cm-hmd-list-indent .cm-tab::before {\n  left: 5px;\n  top: -5px;\n  bottom: -4px;\n}\nol ol::before {\n  left: -16px;\n  top: 0;\n  bottom: 0;\n}\n/** ______ 2.1.2 tasklist (preview) indentation lines correction -- https://forum.obsidian.md/t/bullet-lines-in-css-for-checkboxes/6262/3 */\n.contains-task-list::before {\n  left: 10px;\n}\n/** ______ 2.1.3 Better Bullet Points In Edit Mode https://forum.obsidian.md/t/clutter-free-edit-mode/6791/30 */\ndiv:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-formatting-list-ul {\n  color: transparent;\n  position: relative;\n}\ndiv:not(.CodeMirror-activeline)\n  > .CodeMirror-line\n  span.cm-formatting-list-ul:after {\n  content: "•";\n  position: absolute;\n  top: -6px;\n  left: 4px;\n  color: var(--bright-aqua);\n  font-family: sans-serif;\n  font-size: 20px;\n}\n/** ______ 2.1.4 Bullet points in preview -- https://discord.com/channels/686053708261228577/702656734631821413/772094128832905226 */\nul,\nul ul,\nol ul,\nul ul ul,\nol ul ul {\n  list-style: none;\n}\nli > p {\n  display: inline-block;\n  margin-top: 0;\n  margin-bottom: 0;\n}\nul li:not(.task-list-item)::before {\n  content: "•";\n  color: var(--bright-aqua);\n  display: inline-block;\n  width: 1em;\n  margin-left: -1.15em;\n  padding: 0;\n  font-weight: bold;\n  text-shadow: 0 0 0.5em var(--bright-aqua);\n}\nul ul li:not(.task-list-item)::before {\n  content: "•";\n}\nul ul ul li:not(.task-list-item)::before {\n  content: "•";\n}\n/** ______ 2.1.5 Bullet List Boxing -- https://discord.com/channels/686053708261228577/702656734631821413/784610806561636413 */\n/*\n* { list-style: none;}\nul li:not(.task-list-item) {\n  margin-left: 15px;\n  position: relative;\n  padding-left: 5px;\n  padding: 5px;\n  list-style-position: ;\n  border-left: 5px solid var(--faded-aqua);\n  box-shadow: 0 0 0 0.5px var(--bright-aqua);\n  border-radius: 10px;\n}\nol {\n  counter-reset: cupcake;\n  padding-left: 5px;\n}\nol li {\n  counter-increment: cupcake;\n  margin-left: 15px;\n  position: relative;\n  padding-left: 5px;\n  list-style-position: inside;\n  border-left: 5px solid var(--faded-aqua);\n  box-shadow: 0 0 0 0.5px var(--bright-aqua);\n  border-radius: 10px;\n}\nol li:before {\n  content: counters(cupcake, \'.\') \'  \';\n  color: var(--bright-green);\n  font-weight: bold;\n  display: inline-block;\n  white-space: pre;\n}\n.markdown-preview-view .collapse-indicator {\n  margin-left: -46px;\n  padding: 0 18px;\n}\n.markdown-preview-view .heading-collapse-indicator {\n  margin-left: -25px;\n  padding: 0 8px;\n}\ndiv.heading-collapse-indicator.collapse-indicator.collapse-icon:hover{\n  color: var(--text-accent);\n}\n.markdown-preview-section:not(.is-collapsed) svg.right-triangle{\n  color: var(--text-accent);\n}\ndiv.collapsible-item-collapse.collapse-icon{\n  color: var(--text-accent);\n} */\n/** ____ 2.2 File Navigation Pane */\n/** ______ 2.2.1 Relationship lines for the folder levels in file navigation: https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/112 */\n.outline .collapsible-item-children {\n  margin-left: 20px;\n  border-left: 1px solid var(--faded-aqua);\n  border-radius: 4px;\n  transition: all 0.5s ease-in-out;\n}\n.outline .collapsible-item-children:hover {\n  border-left-color: var(--faded-aqua);\n}\n.nav-folder-children .nav-folder-children {\n  margin-left: 20px;\n  padding-left: 0;\n  border-left: 1px solid var(--faded-aqua);\n  border-radius: 4px;\n  transition: all 0.5s ease-in-out;\n}\n.nav-folder-children .nav-folder-children:hover {\n  border-left-color: var(--faded-aqua);\n}\n/** ______ 2.2.2 Custom icons differing files and folders: https://discordapp.com/channels/686053708261228577/702656734631821413/755293685046050896 */\n/* Emoji */\n.nav-file-title-content::before { content: "📝️ "; }\n.nav-folder-title-content::before { content: \'📂 \'; }\n.nav-file-title-content[data-link-data-href="Flows"]::before { content: \'♻️ \'; }\n.nav-file-title-content[data-link-data-href="Tasks"]::before { content: \'✅️ \'; }\n.nav-file-title-content[data-link-data-href="Readwise Items To Review"]::before { content: \'🔁 \'; }\n.nav-file-title-content[data-link-data-href="Timeline"]::before { content: \'🕓️ \'; }\n.nav-file-title-content[data-link-data-href="Research"]::before { content: \'🖥️ \'; }\n.nav-file-title-content[data-link-data-href="ZK Processing"]::before { content: \'🖥️ \'; }\n.nav-file-title-content[data-link-data-href="Top of Mind"]::before { content: \'🧠️ \'; }\n.nav-file-title-content[data-link-data-href="Patrons"]::before { content: \'🧡️ \'; }\n.nav-file-title-content[data-link-data-href="Tools"]::before { content: \'🛠️ \'; }\n.nav-file-title-content[data-link-data-href="Workbench"]::before { content: \'✏️ \'; }\n.nav-file-title-content[data-link-data-href="HOME"]::before { content: \'🌎️ \'; }\n.nav-file-title-content[data-link-data-href="2020 Goals"]::before { content: \'🏆️ \'; }\n.nav-file-title-content[data-link-data-href="2021 Goals"]::before { content: \'🏆️ \'; }\n.nav-file-title-content[data-link-data-href="2023 Goals"]::before { content: \'🏆️ \'; }\n.nav-file-title-content[data-link-data-href="Life Philosophy"]::before { content: \'💭️ \'; }\n.nav-file-title-content[data-link-data-href="Good Feels"]::before { content: \'😊️ \'; }\n.nav-file-title-content[data-link-tags*="#📥️/🐦️"]::before { content: \'🐦️ \'; }\n.nav-file-title-content[data-link-tags*="#📥️/📰️"]::before { content: \'️📰️ \'; }\n.nav-file-title-content[data-link-tags*="#📥️/📚️"]::before { content: \'️📚️ \'; }\n.nav-file-title-content[data-link-tags*="#📝️/👥️"]::before { content: \'️👥️ \'; }\n.nav-file-title-content[data-link-tags*="#📥️/📜️"]::before { content: \'️📜️ \'; }\n.nav-file-title-content[data-link-tags*="#📥️/🎧️"]::before { content: \'️🎧️ \'; }\n.nav-file-title-content[data-link-tags*="#📥️/🎥️"]::before { content: \'️🎥️ \'; }\n.nav-file-title-content[data-link-tags*="#📥️/💭️"]::before { content: \'️💭️ \'; }\n.nav-file-title-content[data-link-tags*="#📥️/🔖️"]::before { content: \'️🔖️ \'; }\n\n/* Flat font */\n/* Requires: https://icomoon.io/#icons-icomoon/liga-font */\n/* .nav-folder-children .nav-file-title-content:first-child::before { content: "\\e924  "; font-family: "IcoMoon-Free"; }\n.nav-folder-children .nav-folder-title-content::before { content: "\\e930  "; font-family: "IcoMoon-Free"; } */\n\n\n/** ________ 2.2.3 Top Level Folder Icons -- https://discord.com/channels/686053708261228577/702656734631821413/805318111917113354 */\n/* .nav-folder-title[data-path="+Medium"] .nav-folder-title-content::before { content: "📜️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="+Newsletter"] .nav-folder-title-content::before { content: "📰️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="+YouTube"] .nav-folder-title-content::before { content: "🔴️ "; font-size: 1.3em; } */\n.nav-folder-title[data-path="Journal"] .nav-folder-title-content::before { content: "📅 "; font-size: 1.3em; }\n.nav-folder-title[data-path="otv"] .nav-folder-title-content::before { content: "💖️ "; font-size: 1.3em; }\n/* .nav-folder-title[data-path="Log"] .nav-folder-title-content::before { content: "📅 "; font-size: 1.3em; } */\n.nav-folder-title[data-path="Media"] .nav-folder-title-content::before { content: "🖼️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="Templates"] .nav-folder-title-content::before { content: "⚙️ "; font-size: 1.3em; }\n/* .nav-folder-title[data-path="Utils"] .nav-folder-title-content::before { content: "⚙️ "; font-size: 1.3em; } */\n.nav-folder-title[data-path="Utility"] .nav-folder-title-content::before { content: "🛠️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="Projects"] .nav-folder-title-content::before { content: "📋 "; font-size: 1.3em; }\n/* .nav-folder-title[data-path="CRM"] .nav-folder-title-content::before { content: "📇️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="Emails"] .nav-folder-title-content::before { content: "📧️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="Timeline"] .nav-folder-title-content::before { content: "⏰️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="Locations"] .nav-folder-title-content::before { content: "📍️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="Names"] .nav-folder-title-content::before { content: "🏷️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="People"] .nav-folder-title-content::before { content: "👥️ "; font-size: 1.3em; } */\n.nav-folder-title[data-path="Inbox"] .nav-folder-title-content::before { content: "📥️ "; font-size: 1.3em; }\n/* .nav-folder-title[data-path="Notes"] .nav-folder-title-content::before { content: "📝️ "; font-size: 1.3em; } */\n/* .nav-folder-title[data-path="Maps Of Content"] .nav-folder-title-content::before { content: "🗺️ "; font-size: 1.3em; } */\n.nav-folder-title[data-path="Sterkere"] .nav-folder-title-content::before { content: "💪🏻️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="DevLog"] .nav-folder-title-content::before { content: "🖥️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="Z"] .nav-folder-title-content::before { content: "🧠️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="Readwise"] .nav-folder-title-content::before { content: "🖋️ "; font-size: 1.3em; }\n/** ________ 2.2.4 Outline Relationship lines -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/357 */\n.outline {\n  font-size: 0.8rem;\n  font-weight: 200;\n}\n\n.outline .tree-item {\n  line-height: 1.3;\n}\n\n.outline .tree-item-self {\n  padding-top: 0.2rem;\n  padding-bottom: 0.1rem;\n  padding-left: 0.5rem;\n  padding-right: 0.3rem;\n}\n\n.outline .tree-item-collapse {\n  left: 0.1rem;\n}\n\n.outline .tree-item-inner {\n  position: relative;\n  padding-top: 0.2rem;\n  /* padding-left: 1rem; */\n  padding-left: 1.7em;\n  text-indent: -0.8em;\n  margin-left: 0.2rem;\n  /* font-size: 0.9em; */\n}\n\n.outline .tree-item-children {\n  margin-left: 0.7rem;\n  padding-left: 0.5rem;\n  margin-top: -0.3rem;\n  padding-top: 0.3rem;\n  border-left: 1px solid var(--neutral-aqua, var(--background-modifier-border));\n  border-radius: 4px;\n  transition: all 0.5s ease-in-out;\n}\n\n.outline .tree-item-children:hover {\n  border-left-color: var(--sidebar-marks-hover, var(--background-secondary));\n}\n\n.outline .collapse-icon + .tree-item-inner {\n  font-weight: 400;\n  padding-left: 0.2rem;\n  /* margin-left: 0rem; */\n  /* font-size: 1em; */\n}\n\n.outline .collapse-icon {\n  margin-top: 0.2rem;\n  margin-left: -0.4rem;\n  margin-right: -0.4rem;\n  width: 2rem;\n}\n/** ________ 2.2.5 Image file navigation icon -- https://discord.com/channels/686053708261228577/702656734631821413/866399284437843978 */\n.nav-file-title[data-path$="jpg"] .nav-file-title-content:before { content: "🌄 "; }\n.nav-file-title[data-path$="pdf"] .nav-file-title-content:before { content: "📜️ "; }\n.nav-file-title[data-path$="docx"] .nav-file-title-content:before { content: "✏️ "; }\n.nav-file-title[data-path$="mp4"] .nav-file-title-content:before { content: "🎥️ "; }\n.nav-file-title[data-path$="webm"] .nav-file-title-content:before { content: "🎥️ "; }\n.nav-file-title[data-path$="mkv"] .nav-file-title-content:before { content: "🎥️ "; }\n.nav-file-title[data-path$="png"] .nav-file-title-content:before { content: "🎨 "; }\n.nav-file-title[data-path$="canvas"] .nav-file-title-content:before { content: "🎨 "; }\n.nav-file-title[data-path$="css"] .nav-file-title-content:before { content: "🎨 "; }\n.nav-file-title[data-path$="sty"] .nav-file-title-content:before { content: "⚙️ "; }\n.nav-file-title[data-path$="csv"] .nav-file-title-content:before { content: "📊️ "; }\n.nav-file-title[data-path$="ico"] .nav-file-title-content:before { content: "ℹ️ "; }\n\n/** ____ 2.3 Clutter Free Mode */\n/** ______ 2.3.1 Make subtler folding gutter arrows -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/10 */\n.CodeMirror-foldgutter-folded:after,\n.CodeMirror-foldgutter-open:after {\n  opacity: 0.5;\n  font-size: 60%;\n  color: var(--bright-aqua);\n}\n.CodeMirror-foldgutter-folded:hover:after,\n.CodeMirror-foldgutter-open:hover:after {\n  opacity: 1;\n}\n.CodeMirror-foldgutter-folded:after {\n  content: "\\25BA";\n}\n.CodeMirror-foldgutter-open:after {\n  content: "\\25BC";\n}\n/** ______ 2.3.2 Hide Block Reference ID\'s -- https://discord.com/channels/686053708261228577/716028884885307432/769267134114037871 */\ndiv:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-blockid {\n  visibility: hidden;\n}\n.cm-blockid::first-letter {\n  visibility: visible;\n  font-weight: 800;\n}\n/** ______ 2.3.3 Shortened Url Links -- https://forum.obsidian.md/t/hide-or-truncate-urls-in-editor-using-css/359/3 */\ndiv:not(.CodeMirror-activeline)\n  > .CodeMirror-line\n  .cm-string.cm-url:not(.cm-formatting) {\n  font-size: 0;\n}\ndiv:not(.CodeMirror-activeline)\n  > .CodeMirror-line\n  .cm-string.cm-url:not(.cm-formatting)::after {\n  content: "🔗";\n  font-size: 1rem;\n}\n/** ______ 2.3.4 highlight (==) not visible anymore if not active line -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/221 */\ndiv:not(.CodeMirror-activeline)\n  > .CodeMirror-line\n  .cm-formatting-highlight.cm-highlight {\n  font-size: 1em;\n  color: transparent;\n}\n/** ______ 2.3.5 Make code blocks wrap in preview mode too */\n.theme-dark code[class*="language-"],\n.theme-dark pre[class*="language-"],\n.theme-light code[class*="language-"],\n.theme-light pre[class*="language-"] {\n  word-wrap: break-word !important;\n  white-space: pre-wrap !important;\n}\n/** ________ 2.3.6 Hide search query title and stop highlighting found element -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/307 */\n.markdown-preview-view .internal-query.is-embed .internal-query-header {\n  display: none;\n}\n\n.search-result-file-matched-text {\n  color: inherit;\n  background-color: inherit;\n}\n/** ________ 2.3.7 vertically centre line numbers in large paragraphs -- https://discord.com/channels/686053708261228577/702656734631821413/822257712825237524 */\n/* .CodeMirror-gutter-wrapper { height:100%; }\n.CodeMirror-gutter-elt { top:0; }\n.cm-s-obsidian .CodeMirror-linenumber{ height: 100%; }\n.cm-s-obsidian .CodeMirror-linenumber::before {\n  content: "";\n  height: calc(50% - 1em);\n  display: block;\n} */\n/** ________ 2.3.8 Fix padding of transcluded blocks in lists */\n.markdown-preview-view .markdown-embed-content > .markdown-preview-view {\n  max-height: 800px;\n  padding-left: 25px;\n}\n/** ________ 2.3.9 Custom Highlight Colors based on templater */\n.hltr-red {\n  background-color: var(--bright-red) !important;\n}\n.hltr-orange {\n  background-color: var(--bright-orange) !important;\n}\n.hltr-yellow {\n  background-color: var(--bright-yellow) !important;\n}\n.hltr-aqua {\n  background-color: var(--bright-aqua) !important;\n}\n.hltr-green {\n  background-color: var(--bright-green) !important;\n}\n.hltr-blue {\n  background-color: var(--bright-blue) !important;\n}\n.hltr-purple {\n  background-color: var(--bright-purple) !important;\n}\n.hltr-magenta {\n  background-color: var(--bright-purple) !important;\n}\n.hltr-grey {\n  background-color: var(--gray) !important;\n}\n/** ____ 2.4 Font Formatting */\n/** ______ 2.4.1 Make Mathjax Font Larger */\n.MJX-TEX {\n  font-size: 180%;\n}\n/** ______ 2.4.2 Hyphenation & Justification     https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/25 */\n.cm-s-obsidian,\n.markdown-preview-view {\n  text-align: justify;\n  hyphens: auto;\n}\n/** ______ 2.4.3 Stylish Block Quotes -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/39 */\nblockquote:before {\n  font: 14px/20px italic Times, serif;\n  content: "“";\n  color: var(--faded-purple);\n  font-size: 3em;\n  line-height: 0.1em;\n  vertical-align: -0.4em;\n}\nblockquote p {\n  display: inline;\n}\n/** ______ 2.4.4 General Font Formatting */\nb,\nstrong,\n.cm-s-obsidian .cm-strong {\n  color: var(--bright-red) !important;\n}\ni,\nem,\nspan.cm-em {\n  color: var(--bright-green) !important;\n}\nu {\n  color: var(--bright-purple) !important;\n}\ndel {\n  color: var(--gray);\n}\nsup,\nsub {\n  color: var(--neutral-yellow);\n}\n/** ______ 2.4.5 Stylish Signatures -- https://discord.com/channels/686053708261228577/702656734631821413/784210155923177552 */\n.signature {\n  font-family: Ananda; /* Font that had to be downloaded from dafont.com */\n  text-align: left;\n  padding-left: 0px;\n  padding-top: 10px;\n  color: var(--bright-purple);\n}\n/** ____ 2.5 Graph Formatting */\n/** ______ 2.5.1 Graph View CSS -- https://discordapp.com/channels/686053708261228577/702656734631821413/760488978691784705 */\n.theme-dark .graph-view.color-arrow {\n  color: var(--bright-aqua);\n}\n.theme-dark .graph-view.color-fill-tag {\n  color: var(--bright-yellow);\n}\n.theme-dark .graph-view.color-fill-attachment {\n  color: var(--neutral-blue);\n}\n.theme-dark .graph-view.color-fill-unresolved {\n  color: var(--bright-red);\n}\n.graph-view.color-fill-focused {\n  color: var(--faded-red);\n}\n.graph-view.color-fill {\n  color: var(--light1);\n}\n/* .graph-view.color-line {\n  color: var(--gray);\n}*/\n/** ____ 2.6 Image Manipulation */\n/** ______ 2.6.1 Image Hover Grow -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/29 */\n.markdown-preview-view img {\n  display: block;\n  margin-left: auto;\n  margin-right: auto;\n  width: 50%;\n  transition: transform 0.25s ease;\n}\n/*   margin-top: 20pt;\n  margin-bottom: 20pt; */\n\n.markdown-preview-view img:hover {\n  -webkit-transform: scale(1.8);\n  transform: scale(2);\n}\n/** ____ 2.7 Check Boxes */\n/** ______ 2.7.1 Nicer Round Checkboxes -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/34 */\n/* input[type="checkbox"],\n.cm-formatting-task {\n  -webkit-appearance: none;\n  appearance: none;\n  border-radius: 50%;\n  border: 1px solid var(--text-faint);\n  padding: 0;\n  vertical-align: top;\n}\n.cm-s-obsidian span.cm-formatting-task {\n  color: transparent;\n  width: 1.25em !important;\n  height: 1.25em;\n  display: inline-block;\n}\ninput[type="checkbox"]:focus {\n  outline: 0;\n}\ninput[type="checkbox"]:checked,\n.cm-formatting-task.cm-property {\n  background-color: var(--text-accent-hover);\n  border: 1px solid var(--text-accent-hover);\n  background-position: center;\n  background-size: 70%;\n  background-repeat: no-repeat;\n  background-image: url(\'data:image/svg+xml; utf8, <svg width="12px" height="10px" viewBox="0 0 12 8" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><g stroke="none" stroke-width="1" fill="none" fill-rule="evenodd"><g transform="translate(-4.000000, -6.000000)" fill="%23ffffff"><path d="M8.1043257,14.0367999 L4.52468714,10.5420499 C4.32525014,10.3497722 4.32525014,10.0368095 4.52468714,9.8424863 L5.24777413,9.1439454 C5.44721114,8.95166768 5.77142411,8.95166768 5.97086112,9.1439454 L8.46638057,11.5903727 L14.0291389,6.1442083 C14.2285759,5.95193057 14.5527889,5.95193057 14.7522259,6.1442083 L15.4753129,6.84377194 C15.6747499,7.03604967 15.6747499,7.35003511 15.4753129,7.54129009 L8.82741268,14.0367999 C8.62797568,14.2290777 8.3037627,14.2290777 8.1043257,14.0367999"></path></g></g></svg>\');\n} */\n/** ______ 2.7.2 Animated Check Boxes -- https://github.com/TriDiamond/Obsidian-Obsidianite/blob/82207bed4313ee0e6f0bb1fd59b04129408018f5/obsidian.css#L463 */\n\n/* .contains-task-list .task-list-item .contains-task-list { padding-inline-start: 0px; }\n.contains-task-list .task-list-item {\n  position: relative;\n  vertical-align: middle;\n  box-sizing: border-box;\n  padding-left: 20px;\n}\n.contains-task-list .task-list-item ul.contains-task-list::before { left: -13px !important; border-width: 2px; }\n.contains-task-list .task-list-item input[type="checkbox"] {\n  position: absolute;\n  top: 4px;\n  left: 0px;\n  width: 15px;\n  height: 15px;\n  margin: 0;\n  opacity: 0;\n  z-index: 10;\n}\n.markdown-preview-view .list-collapse-indicator { margin-left: -35px !important; box-sizing: border-box; }\n.contains-task-list .task-list-item::before {\n  content: "";\n  position: absolute;\n  top: 2px;\n  left: 0px;\n  width: 15px;\n  height: 15px;\n  display: inline-flex;\n  justify-content: center;\n  border: 2px solid var(--neutral-blue);\n  margin-right: 15px;\n  border-radius: 10px;\n  transition: all 0.3s;\n  box-sizing: border-box;\n  z-index: 1;\n}\n.contains-task-list .is-checked.task-list-item::before { border: 10px solid var(--neutral-purple); animation: bounce 300ms; }\n.contains-task-list .is-checked.task-list-item::after {\n  content: "";\n  position: absolute;\n  top: 9px;\n  left: 3px;\n  border-right: 3px solid transparent;\n  border-bottom: 3px solid transparent;\n  transform: rotate(45deg);\n  transform-origin: 0% 100%;\n  animation: checked-box 125ms 250ms forwards;\n  z-index: 5;\n}\n.markdown-preview-view ul > li.task-list-item.is-checked {\n  text-decoration: line-through !important; \n  color: var(--gray) !important; \n}\n.markdown-preview-view ul > li.task-list-item.is-checked ul > li:not(.is-checked) { text-decoration: none !important; color: var(--text-normal) !important; }\n@keyframes checked-box {\n  0% {\n    width: 0;\n    height: 0;\n    border-color: #ffffff;\n    transform: translate(0, 0) rotate(45deg);\n  }\n  33% {\n    width: 4px;\n    height: 0;\n    border-color: #ffffff;\n    transform: translate(0, 0) rotate(45deg);\n  }\n  100% {\n    width: 4px;\n    height: 8px;\n    border-color: #ffffff;\n    transform: translate(0, -8px) rotate(45deg);\n  }\n}\n\n@keyframes bounce {\n  0% { border-width: 2px; }\n  33% { border-width: 4px; }\n  100% { border-width: 10px; } \n}*/\n/** ________ 2.7.3 Hide Completed Tasks In Preview -- https://forum.obsidian.md/t/hide-checked-todo-s/14043 */\n/* .markdown-preview-view ul > li.task-list-item.is-checked { display: none; } */\n/** ____ 2.8 Tags */\n/** ______ 2.8.1 Tag Pills -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/72 */\n/* .tag:not(.token) {\n  background-color: var(--faded-blue);\n  border: none;\n  color: white;\n  font-size: 14px;\n  padding: 0px 8px;\n  text-align: center;\n  text-decoration: none;\n  display: inline-block;\n  margin: 0px 0px;\n  cursor: pointer;\n  border-radius: 14px;\n  font-weight: bold;\n}\n.tag:not(.token):hover {\n  color: var(--bright-red) !important;\n  background-color: var(--bright-red);\n}\n.tag[href^="#📥️"] {\n  background-color: var(--light4);\n  color: var(--light4) !important;\n}\n.tag[href^="#🌱️"] {\n  background-color: var(--faded-aqua);\n  color: var(--faded-aqua) !important;\n}\n.tag[href^="#🌞️"] {\n  background-color: var(--faded-aqua);\n  color: var(--faded-aqua) !important;\n}\n.tag[href^="#🌲️"] {\n  background-color: var(--faded-aqua);\n  color: var(--faded-aqua) !important;\n}\n.tag[href^="#✏"] {\n  background-color: var(--faded-blue);\n  color: var(--faded-blue) !important;\n}\n.tag[href^="#✅️"] {\n  background-color: var(--bright-orange);\n  color: var(--bright-orange) !important;\n}\n.tag[href^="#🗺️"] {\n  background-color: var(--bright-yellow);\n  color: var(--bright-yellow) !important;\n}\n.tag[href^="#⚙️"] {\n  background-color: var(--dark3);\n  color: var(--dark3) !important;\n}\n.tag[href^="#❗️"] {\n  background-color: var(--light1);\n  color: var(--light1) !important;\n} */\n/** ________ 2.8.2 Tags to the side of the document -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/327 */\n/* Requires the core setting "Readable Line Length" to be on */\n/* p > a.tag {\n  font-size: 0;\n  width: 0;\n  padding: 0;\n  margin: 0;\n  background: none;\n  text-decoration: none;\n  border: none;\n}\np > a.tag::before {\n  content: \'Ꚛ\';\n  font-size: 16px;\n  color: var(--bright-purple) ;\n}\n\np > a.tag::after {\n  content: attr(href);\n  float: right;\n  min-width: 3ch;\n  max-width: 25%;\n  margin-right: calc(-25% - 1.5em);\n  margin-left: calc(-25% - 1.5em);\n  position: relative;\n  clear: right;\n  white-space: nowrap;\n  text-overflow: ellipsis;\n  overflow: hidden;\n  font-size: 20px;\n}\n\np > a.tag:hover::after {\n  max-width: fit-content !important;\n}  */\n/** ____ 2.9 [[Link]] Modification */\n/** ______ 2.9.1 Bigger Link Hover Popup Preview -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/175 */\n.popover.hover-popover {\n  transform: scale(0.8); /* makes the content smaller */\n  max-height: 800px;\n  min-height: 50px;\n  width: 700px;\n  overflow: overlay; /* new added */\n}\n.popover.hover-popover .markdown-embed {\n  height: 100%;\n}\n.popover.hover-popover.is-loaded\n  .markdown-embed\n  .markdown-embed-content\n  .markdown-preview-view {\n  padding: 10px 10px 10px 16px; /*16px  two pop magin */\n}\n/** ________ 2.9.2 The modal popups from link hovers */\n.popover {\n  border: 2px solid var(--bright-aqua);\n}\n/** ________ 2.9.3 Input Links -- https://discord.com/channels/686053708261228577/707816848615407697/844751423253905458 */\n/* a.internal-link[data-link-type$="video" i]::before {\n  content: "🎥 " attr(data-link-status) " ";\n}\na.internal-link[data-link-type$="article" i]::before {\n  content: "📰️ " attr(data-link-status) " ";\n}\na.internal-link[data-link-type$="book" i]::before {\n  content: "📚 " attr(data-link-status) " ";\n}\na.internal-link[data-link-type$="paper" i]::before {\n  content: "📜️ " attr(data-link-status) " ";\n}\na.internal-link[data-link-type$="podcast" i]::before {\n  content: "🎧️ " attr(data-link-status) " ";\n}\na.internal-link[data-link-type$="tweet" i]::before {\n  content: "🐦️ " attr(data-link-status) " ";\n}\na.internal-link[data-link-type$="thought" i]::before {\n  content: "💭️ " attr(data-link-status) " ";\n}\na.internal-link[data-link-type$="kindle" i]::before {\n  content: "🔖️ " attr(data-link-status) " ";\n} */\n/* a.internal-link[data-link-status]::after{\n  content: " "attr(data-link-status)\n} */\n/** ______ 2.10.1 Calendar Plugin CSS */\n#calendar-container {\n  --color-background-heading: transparent;\n  --color-background-weeknum: transparent;\n  --color-background-weekend: transparent;\n  --color-background-day: transparent;\n  --color-background-day-empty: var(--background-secondary-alt);\n  --color-background-day-active: var(--interactive-accent);\n  --color-background-day-hover: var(--interactive-hover);\n\n  --color-dot: var(--bright-aqua);\n\n  --color-text-weeknum: var(--bright-aqua);\n  --color-text-title: var(--text-normal);\n  --color-text-heading: var(--text-normal);\n  --color-text-day: var(--text-normal);\n  --color-text-today: var(--text-accent);\n  --color-arrow: var(--bright-aqua);\n  --color-button: var(--text-muted);\n}\n#calendar-container > table > tbody > tr > td {\n  padding: 0px !important;\n}\n#calendar-container .year {\n  color: var(--bright-orange);\n\n}\n#calendar-container [data-emoji-tag]::after {\n  content: attr(data-emoji-tag);\n  position: absolute;\n  top: -4px;\n  right: 4px;\n  height: 8px;\n  width: 8px;\n}\n/** ________ 2.10.2 T0DOIST Plugin CSS -- https://github.com/jamiebrynes7/clair-de-lune-obsidian-theme/blob/master/src/modules/extensions/todoist.scss */\n/* Additional Link -- */\n.todoist-refresh-button {\n  margin-right: 32px;\n}\n.todoist-p1 input {\n  --checkbox-border-color: var(--neutral-red);\n  --checkbox-border-color-hover: var(--bright-red);\n  background-color: var(--faded-red);\n}\n.todoist-p2 input {\n  --checkbox-border-color: var(--neutral-yellow);\n  --checkbox-border-color-hover: var(--bright-yellow);\n  background-color: var(--faded-yellow);\n}\n.todoist-p3 input {\n  --checkbox-border-color: var(--neutral-blue);\n  --checkbox-border-color-hover: var(--bright-blue);\n  background-color: var(--faded-blue);\n}\n.todoist-p4 input {\n  --checkbox-border-color: var(--light4);\n  --checkbox-border-color-hover: var(--light1);\n  background-color: var(--gray);\n}\n.task-metadata {\n  font-size: var(--font-todoist-metadata-size);\n  color: var(--bright-aqua);\n}\n.task-metadata > * {\n  display: inline;\n  margin-right: 30px;\n}\n.task-date.task-overdue {\n  color: var(--bright-red);\n}\n.task-labels-icon {\n  color: var(--bright-green);\n}\n.task-labels {\n  color: var(--bright-purple);\n}\n.task-project-icon {\n  color: var(--bright-blue);\n}\n.task-project {\n  color: var(--bright-blue);\n}\n.todoist-project .todoist-project {\n  margin-left: 20px;\n}\n\n.todoist-section {\n  margin-left: 20px;\n}\n\n.todoist-project .todoist-project-title {\n  font-weight: 700;\n  -webkit-margin-after: 0px;\n  margin-block-end: 0px;\n}\n\n.todoist-section .todoist-section-title {\n  font-size: var(--font-todoist-title-size);\n  font-weight: 700;\n  -webkit-margin-after: 0px;\n  margin-block-end: 0px;\n}\n\n.todoist-error {\n  border: 1px solid var(--bright-red);\n  background-color: rgba(255, 0, 0, 0.05);\n  padding: 1em 1em;\n  margin: 1em 0px;\n}\n\n.todoist-error p {\n  margin: 0 0 1em 0;\n  font-weight: 600;\n}\n\n.todoist-error code {\n  background-color: unset !important;\n  padding: unset !important;\n  margin: unset !important;\n} \n/** ________ 2.10.3 DayPlanner Plugin CSS */\n/* .event_item_color1 {\n  background-color: var(--neutral-aqua) !important;\n}\n\n.event_item_color2 {\n  background-color: var(--neutral-blue) !important;\n}\n\n.event_item_color3 {\n  background-color: var(--neutral-green) !important;\n}\n\n.event_item_color4 {\n  background-color: var(--neutral-orange) !important;\n}\n\n.event_item_color5 {\n  background-color: var(--neutral-purple) !important;\n}\n\n.event_item_color6 {\n  background-color: var(--neutral-red) !important;\n}\n\n.event_item_color7 {\n  background-color: var(--neutral-yellow) !important;\n}\n\n.event_item_color8 {\n  background-color: var(--neutral-aqua) !important;\n}\n\n.event_item_color9 {\n  background-color: var(--neutral-blue) !important;\n}\n\n.event_item_color10 {\n  background-color: var(--neutral-green)!important;\n} */\n/** ________ 2.10.4 Folder Note CSS */\n/* .strip-card-view .thumb-color-folder {\n  background-color: var(--faded-purple) !important;\n  color: var(--light1) !important;\n}\n.strip-card-view .thumb-color-note {\n  background-color: var(--faded-red) !important;\n  color: var(--light1) !important;;\n}\n.strip-card-view span {\n  color: var(--faded-green) !important;\n}\n.strip-card-view p {\n  color: var(--gray) !important;\n} */\n/** ____ 2.11 Heading Formatting */\n/** ______ 2.11.1 Heading Under Gradient Line -- https://github.com/TriDiamond/Obsidian-Obsidianite */\n/* .markdown-preview-view h1,\n.markdown-preview-view h2,\n.markdown-preview-view h3,\n.markdown-preview-view h4,\n.markdown-preview-view h5,\n.markdown-preview-view h6 {\n  position: relative;\n}\n.markdown-preview-view h1:after,\n.markdown-preview-view h2:after,\n.markdown-preview-view h3:after,\n.markdown-preview-view h4:after,\n.markdown-preview-view h5:after,\n.markdown-preview-view h6:after {\n  position: absolute;\n  content: \'\';\n  height: 1px;\n  width: 35%;\n  left: 0;\n  bottom: -0.2rem;\n  background-image: linear-gradient(to right, var(--bright-aqua), var(--background-primary)) ;\n  opacity: 1;\n} */\n/** ______ 2.11.2 Emoji Orientation in Andy Mode Headers -- https://discord.com/channels/686053708261228577/702656734631821413/775900471406624768 */\nbody.plugin-sliding-panes-rotate-header .workspace > .mod-root .view-header {\n  text-orientation: sideways;\n}\n/** ________ 2.11.3 Heading Horizontal Lines -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/288?u=tallguyjenks */\n/* h1,\nh2,\nh3,\nh4,\nh5,\nh6 {\n  display: flex;\n  width: 100%;\n  align-items: center;\n}\nh1:before,\nh1:after,\nh2:before,\nh2:after,\nh3:before,\nh3:after,\nh4:before,\nh4:after,\nh5:before,\nh5:after,\nh6:before,\nh6:after {\n  content: "";\n  background: var(--bright-aqua);\n  height: 0.1em;\n  margin: 0.2em;\n  flex: 1;\n} */\n/** ____ 2.12 Horizontal Rule Formatting */\n/** ______ 2.12.1 Aesthetic Horizontal Rule -- https://github.com/TriDiamond/Obsidian-Obsidianite */\n\n.markdown-preview-view hr {\n  margin-block-start: 4em;\n  margin-block-end: 4em;\n  border: none;\n  height: 1px;\n  background-image: linear-gradient(\n    to right,\n    var(--background-primary),\n    var(--text-accent),\n    var(--background-primary)\n  );\n}\n\n.markdown-preview-view hr::after {\n  /* content: \'§\'; */\n  content: "ᛟ";\n  display: inline-block;\n  position: absolute;\n  left: 50%;\n  /* transform: translate(-50%, -50%) rotate(60deg); */\n  transform: translate(-50%, -50%) rotate(0deg);\n  transform-origin: 50% 50%;\n  padding: 0.5rem;\n  color: var(--bright-aqua);\n  background-color: var(--background-primary);\n}\n/** ______ 2.13.1 Page Break -- https://gist.github.com/liamcain/81679412643690a7cdd13dff4dc909ce */\n@media print {\n  /* pagebreak before all ## headings */\n  h2 {\n    page-break-before: always;\n  }\n\n  h3,\n  h4 {\n    page-break-after: avoid;\n  }\n\n  pre,\n  blockquote {\n    page-break-inside: avoid;\n  }\n\n  /* use double <hr> (\'---\') to indicate a page break */\n  hr + hr {\n    page-break-before: always;\n    visibility: hidden;\n  }\n\n  :not(hr) + hr {\n    visibility: hidden;\n  }\n\n  :not(hr) + hr + :not(hr):not(h2) {\n    border-top: 1px solid black;\n    padding-top: 2em;\n  }\n}\n/** ______ 2.14.1 Banded Table Rows -- https://discord.com/channels/686053708261228577/702656734631821413/777106171948564500 */\ntable {\n  padding: 0;\n  word-break: initial;\n}\n\ntable tr {\n  border-top: 1px solid #cccccc;\n  margin: 0;\n  padding: 0;\n}\n\ntable tr:nth-child(2n) {\n  background-color: var(--dark1);\n}\n\ntable tr th {\n  font-weight: bold;\n  border: 1px solid #cccccc;\n  text-align: left;\n  margin: 0;\n  padding: 6px 13px;\n}\n\ntable tr td {\n  border: 1px solid #cccccc;\n  text-align: left;\n  margin: 0;\n  padding: 6px 13px;\n}\n\ntable tr th:first-child,\ntable tr td:first-child {\n  margin-top: 0;\n}\n\ntable tr th:last-child,\ntable tr td:last-child {\n  margin-bottom: 0;\n}\n/** ________ 2.14.2 Full Width Tables */\n.markdown-preview-view table {\n  width: 100%;\n}\n#sponsors,\n#patrons {\n  width: 50%;\n}\n/** ________ 2.14.3 Numbered Table Rows-- https://discord.com/channels/686053708261228577/707816848615407697/832558496892846080 */\n.table-view-table {\n  counter-reset: section;\n}\n\n.table-view-table > tbody > tr > td:first-child::before {\n  counter-increment: section;\n  content: counter(section) ". ";\n}\n/** ____ 2.15 Custom HTML Elements */\n/** ______ 2.15.1 aside format -- https://discord.com/channels/686053708261228577/707816848615407697/784964375806083124 */\naside {\n  width: 40%;\n  padding-left: 0.5rem;\n  margin-left: 1rem;\n  margin-top: 0.5rem;\n  float: right;\n  box-shadow: inset 5px 0 5px -5px var(--faded-blue);\n  font-style: italic;\n  color: var(--faded-blue);\n}\n\naside > p {\n  margin: 0.5rem;\n}\n/** ______ 2.15.2 Buttons -- https://discord.com/channels/686053708261228577/744933215063638183/784289179328708648 */\n.date_button_today {\n  background-color: var(--neutral-aqua);\n  font-weight: bold;\n  margin-right: 0%;\n}\n.date_button_today:hover {\n  background-color: var(--faded-aqua);\n}\n.date_button {\n  background-color: var(--dark1);\n}\n.date_button:hover {\n  background-color: var(--dark3);\n}\n/** ________ 2.15.3 Definition Lists */\ndt {\n  color: var(--neutral-yellow);\n  font-weight: bold;\n}\ndd {\n  color: var(--faded-yellow);\n  font-style: italic;\n}\ndd::before {\n  content: "├── ";\n  margin-left: -1.5em;\n  color: var(--neutral-orange);\n  font-style: normal;\n}\ndd:last-child::before {\n  content: "└── ";\n  margin-left: -1.5em;\n  color: var(--neutral-orange);\n  font-style: normal;\n}\n/** ________ 2.15.4 Code Language Fences -- https://discord.com/channels/686053708261228577/702656734631821413/822915125522202654 */\n\n/* Informational Code Fences */\n.theme-dark /*replace with dark if needed*/ div pre.language-info {\n  /*replace info with anything you like*/\n  background-color: var(\n    --background-primary\n  ); /*you can replace with any colour you want here*/\n  border-left: 1em solid var(--neutral-blue); /*replace this colour with anything you like*/\n  padding-top: 0;\n}\n\npre.language-info::before {\n  /*replace info with anything you like*/\n  margin-bottom: 0.9em;\n  margin-left: -1em; /*based on default padding of obsidian, you may need to adjust depending on the theme you use*/\n  margin-right: -1em;\n  position: static;\n  display: block;\n  background-color: var(\n    --background-secondary\n  ); /*replace this colour with anything you like*/\n  content: "  ℹ️ Info"; /*replace this content with anything you like*/\n}\n\n/* JavaScript */\n.theme-dark /*replace with dark if needed*/ div pre.language-javascript {\n  /*replace info with anything you like*/\n  background-color: var(\n    --background-primary\n  ); /*you can replace with any colour you want here*/\n  padding-top: 0;\n}\n\npre.language-javascript::before {\n  /*replace info with anything you like*/\n  margin-bottom: 0.9em;\n  margin-left: -1em; /*based on default padding of obsidian, you may need to adjust depending on the theme you use*/\n  margin-right: -1em;\n  position: static;\n  display: block;\n  background-color: var(\n    --neutral-yellow\n  ); /*replace this colour with anything you like*/\n  content: "    JavaScript"; /*replace this content with anything you like*/\n  color: var(--background-secondary);\n  font-weight: bold;\n}\n\n/* HTML */\n.theme-dark /*replace with dark if needed*/ div pre.language-html {\n  /*replace info with anything you like*/\n  background-color: var(\n    --background-primary\n  ); /*you can replace with any colour you want here*/\n  padding-top: 0;\n}\n\npre.language-html::before {\n  /*replace info with anything you like*/\n  margin-bottom: 0.9em;\n  margin-left: -1em; /*based on default padding of obsidian, you may need to adjust depending on the theme you use*/\n  margin-right: -1em;\n  position: static;\n  display: block;\n  background-color: var(\n    --neutral-orange\n  ); /*replace this colour with anything you like*/\n  content: "    HTML"; /*replace this content with anything you like*/\n  color: var(--background-secondary);\n  font-weight: bold;\n}\n\n/* CSS */\n.theme-dark /*replace with dark if needed*/ div pre.language-css {\n  /*replace info with anything you like*/\n  background-color: var(\n    --background-primary\n  ); /*you can replace with any colour you want here*/\n  padding-top: 0;\n}\n\npre.language-css::before {\n  /*replace info with anything you like*/\n  margin-bottom: 0.9em;\n  margin-left: -3em; /*based on default padding of obsidian, you may need to adjust depending on the theme you use*/\n  margin-right: -1em;\n  position: static;\n  display: block;\n  background-color: var(\n    --neutral-blue\n  ); /*replace this colour with anything you like*/\n  content: "    CSS"; /*replace this content with anything you like*/\n  color: var(--background-secondary);\n  font-weight: bold;\n}\n\n/* Git repurposed for pro/con */\n.theme-dark /*replace with dark if needed*/ div pre.language-git {\n  /*replace info with anything you like*/\n  background-color: var(\n    --background-primary\n  ); /*you can replace with any colour you want here*/\n  padding-top: 0;\n}\n\npre.language-git::before {\n  /*replace info with anything you like*/\n  margin-bottom: 0.9em;\n  margin-left: -1em; /*based on default padding of obsidian, you may need to adjust depending on the theme you use*/\n  margin-right: -1em;\n  position: static;\n  display: block;\n  background-color: var(\n    --faded-green\n  ); /*replace this colour with anything you like*/\n  content: "    Pro / Con"; /*replace this content with anything you like*/\n  color: var(--background-secondary);\n  font-weight: bold;\n}\n/** ________ 2.15.5 Rounded Edges of Inline Code blocks https://discord.com/channels/686053708261228577/702656734631821413/822181163639767081 */\n/* set text and colour of codeblock */\n.cm-s-obsidian\n  span.cm-inline-code:not(.cm-formatting):not(.cm-hmd-indented-code):not(.obsidian-search-match-highlight) {\n  color: inherit;\n  background-color: var(--background-secondary);\n  padding: 2px 4px;\n}\n\n/* give rounded left edge to codeblock formatting*/\nspan.cm-formatting.cm-formatting-code.cm-inline-code {\n  border-radius: 4px 0px 0px 4px;\n  background-color: var(--background-secondary);\n  color: inherit;\n  padding: 2px 4px;\n}\n\n/* give rounded right edge to codeblock formatting */\nspan.cm-inline-code + span.cm-formatting.cm-formatting-code.cm-inline-code {\n  border-radius: 0px 4px 4px 0px;\n}\n/** ____ 2.16 Quick Switcher */\n/** ________ 2.16.1 Fix the quick switcher highligher after background color change */\n.suggestion-item.is-selected {\n  background-color: var(--faded-aqua);\n}\n/** .. 3. Grave Yard */\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/* Change color of internal links https://discordapp.com/channels/686053708261228577/702656734631821413/767572809848848385 */\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n\n/* .cm-s-obsidian span.cm-hmd-internal-link, a.internal-link {\n  color: var(--bright-orange) !important;\n} */\n\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/* Whitespace Characters */ /* https://forum.obsidian.md/t/editors-css-to-show-tabs-trailing-whitespace-and-strict-line-breaks/4234 */\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n\n/* .cm-trailing-space-new-line, .cm-trailing-space-a, .cm-trailing-space-b, .cm-tab{\n  font-size: 0;\n}\n.cm-trailing-space-a::before, .cm-trailing-space-b::before, .cm-trailing-space-new-line::before, .cm-tab::before{\n  content:\'·\';\n  color:var(--dark2);\n  font-size: initial;\n}\n.cm-trailing-space-new-line::before {\n  content:\'↵\';\n}\n.cm-tab::before {\n  content:\'⟶\'\n} */\n\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/* Remove blockquote left margin\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/*\nblockquote {\n    margin-inline-start: 0;\n} */\n\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/* Make Tags and Searched pages have expanded columns --- THIS MESSES WITH ANDY MODE */\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/*body > div > div.horizontal-main-container > div > div.workspace-split.mod-horizontal.mod-right-split > div:nth-child(4) > div.workspace-leaf > div > div > div,\nbody > div > div.horizontal-main-container > div > div.workspace-split.mod-horizontal.mod-left-split > div.workspace-tabs > div.workspace-leaf > div > div.search-result-container.mod-global-search > div\n{\n    column-width:200px;\n}*/\n/* Expand List Column for file search (THIS MESSES WITH ANDY MODE): */\n/*.nav-folder-children\n{\n    column-width:200px;\n}*/\n\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/* Lime Light but only for body text */\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/*.cm-s-obsidian,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-link,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-hmd-internal-link,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-url,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-hmd-escape-backslash,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-inline-code,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > pre.CodeMirror-line.HyperMD-codeblock,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-hashtag,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-builtin,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-hr,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-footref,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line pre.HyperMD-footnote span.cm-hmd-footnote,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-formatting-highlight,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-highlight,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-formatting-list,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-formatting-task,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-quote,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-math,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.hmd-fold-math-placeholder {\n  color: var(--dark2);\n}\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-formatting-highlight,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-highlight {\n  background-color: transparent;\n}\n.CodeMirror-activeline {\n  color: var(--light1);\n}*/\n\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/* WYSIWYG Editor Features From: https://discordapp.com/channels/686053708261228577/702656734631821413/749843052385796147 */\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/* inline formatting, link targets and [[ ]] disappears if not active line\ndiv:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-formatting,\ndiv:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-string.cm-url,\ndiv:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-formatting-link\n{ display: none; } */\n/* hide all html tags -- IT IS COMMENTED OUT BY DEFAULT\ndiv:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-tag{ display: none; }*/\n/* optionally header hashes  span.cm-formatting-header,\n/* except list markers  span.cm-formatting-list,\n/* code block backticks span.cm-formatting-code-block.cm-hmd-codeblock\n{\n    display: inline !important;\n}*/\n/* and task checkboxes\nspan.cm-formatting-task { display: inline !important; font-family: monospace; }\n*/\n\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/* replace H1-H6 markup in edit mode: https://discordapp.com/channels/686053708261228577/702656734631821413/753842312882159687\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/* .CodeMirror-sizer {\n  margin-left: 48px !important;\n} */\n/*-- reduce left padding --*/\n/* .CodeMirror {\n  height: 100%;\n  direction: ltr;\n  padding: 0 10px;\n} */\n/*-- header color --*/\n/* .cm-header.cm-header-1 {\n  color: var(--text-accent);\n  left: 0px;\n  position: relative;\n} */\n/* .cm-header.cm-header-2 {\n  color: var(--text-accent2);\n  left: 0px;\n  position: relative;\n} */\n/*-- hide # markup--*/\n/* .cm-formatting.cm-formatting-header.cm-formatting-header-1.cm-header.cm-header-1,\n.cm-formatting.cm-formatting-header.cm-formatting-header-2.cm-header.cm-header-2,\n.cm-formatting.cm-formatting-header.cm-formatting-header-3.cm-header.cm-header-3,\n.cm-formatting.cm-formatting-header.cm-formatting-header-4.cm-header.cm-header-4,\n.cm-formatting.cm-formatting-header.cm-formatting-header-5.cm-header.cm-header-5,\n.cm-formatting.cm-formatting-header.cm-formatting-header-6.cm-header.cm-header-6 {\n  font-size: 0px;\n}\n */\n/*-- display H1-h6 in gutter--*/\n/* .cm-formatting.cm-formatting-header.cm-formatting-header-1.cm-header.cm-header-1:before {\n  content: "H1";\n  font-size: 34px;\n  color: var(--text-accent2);\n  left: -49px;\n  top: -50px;\n  position: absolute;\n}\n.cm-formatting.cm-formatting-header.cm-formatting-header-2.cm-header.cm-header-2:before {\n  content: "H2";\n  font-size: 26px;\n  color: var(--text-accent2);\n  left: -43px;\n  top: -35px;\n  position: absolute;\n}\n.cm-formatting.cm-formatting-header.cm-formatting-header-3.cm-header.cm-header-3:before {\n  content: "H3";\n  font-size: 22px;\n  color: var(--text-accent2);\n  left: -36px;\n  top: -6px;\n  position: absolute;\n}\n.cm-formatting.cm-formatting-header.cm-formatting-header-4.cm-header.cm-header-4:before {\n  content: "H4";\n  font-size: 20px;\n  color: var(--text-accent2);\n  left: -36px;\n  top: -6px;\n  position: absolute;\n}\n.cm-formatting.cm-formatting-header.cm-formatting-header-5.cm-header.cm-header-5:before {\n  content: "H5";\n  font-size: 18px;\n  color: var(--text-accent2);\n  left: -36px;\n  top: -6px;\n  position: absolute;\n}\n.cm-formatting.cm-formatting-header.cm-formatting-header-6.cm-header.cm-header-6:before {\n  content: "H6";\n  font-size: 16px;\n  color: var(--text-accent2);\n  left: -36px;\n  top: -4px;\n  position: absolute;\n} */\n\n/*-- is active line, hide H[1-6] in gutter --*/\n/* .CodeMirror-activeline\n  span.cm-formatting.cm-formatting-header.cm-formatting-header-1.cm-header.cm-header-1:before,\n.CodeMirror-activeline\n  span.cm-formatting.cm-formatting-header.cm-formatting-header-2.cm-header.cm-header-2:before,\n.CodeMirror-activeline\n  span.cm-formatting.cm-formatting-header.cm-formatting-header-3.cm-header.cm-header-3:before,\n.CodeMirror-activeline\n  span.cm-formatting.cm-formatting-header.cm-formatting-header-4.cm-header.cm-header-4:before,\n.CodeMirror-activeline\n  span.cm-formatting.cm-formatting-header.cm-formatting-header-5.cm-header.cm-header-5:before,\n.CodeMirror-activeline\n  span.cm-formatting.cm-formatting-header.cm-formatting-header-6.cm-header.cm-header-6:before {\n  font-size: 0px;\n} */\n/*-- is active line, display # markup --*/\n/* .CodeMirror-activeline\n  > pre\n  > span\n  .cm-formatting.cm-formatting-header.cm-formatting-header-1.cm-header.cm-header-1 {\n  font-size: 32px;\n  display: inline;\n}\n.CodeMirror-activeline\n  > pre\n  > span\n  .cm-formatting.cm-formatting-header.cm-formatting-header-2.cm-header.cm-header-2 {\n  font-size: 24px;\n  display: inline;\n}\n.CodeMirror-activeline\n  > pre\n  > span\n  .cm-formatting.cm-formatting-header.cm-formatting-header-3.cm-header.cm-header-3 {\n  font-size: 19px;\n  display: inline;\n}\n.CodeMirror-activeline\n  > pre\n  > span\n  .cm-formatting.cm-formatting-header.cm-formatting-header-4.cm-header.cm-header-4,\n.CodeMirror-activeline\n  > pre\n  > span\n  .cm-formatting.cm-formatting-header.cm-formatting-header-5.cm-header.cm-header-5,\n.CodeMirror-activeline\n  > pre\n  > span\n  .cm-formatting.cm-formatting-header.cm-formatting-header-6.cm-header.cm-header-6 {\n  font-size: 13px;\n  display: inline;\n} */\n\n/*--------------------------------------------------------------------------------------------------------------------------------------------\nNO HIGHLIGHT OR LINK MARKS WYSIWYG https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/175\n--------------------------------------------------------------------------------------------------------------------------------------------*/\n/* div:not(.CodeMirror-activeline)>.CodeMirror-line span.cm-formatting-link:not(.cm-link),\ndiv:not(.CodeMirror-activeline)>.CodeMirror-line span.cm-formatting-highlight {\n    display: none !important;\n} */\n\n/** Folder colors Source: https://gist.github.com/Larandar/e025313d086b75ec1f9a2e6672836883 */\n.nav-folder-title[data-path^=\'Log\'] {\n  background-color: var(--neutral-red);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'Journal\'] {\n  background-color: var(--neutral-red);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'Sterkere\'] {\n  background-color: var(--neutral-red);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'Templates\'] {\n  background-color: var(--neutral-orange);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'DevLog\'] {\n  background-color: var(--neutral-yellow);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'CRM\'] {\n  background-color: var(--neutral-green);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'Inbox\'] {\n  background-color: var(--neutral-aqua);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'Z\'] {\n  background-color: var(--neutral-aqua);\n  color: var(--background-primary);\n}\n.nav-folder.mod-root\n    > .nav-folder-children\n    > .nav-folder\n    > .nav-folder-title[data-path^=\'People\']\n/* .nav-folder.mod-root\n    > .nav-folder-children\n    > .nav-folder\n    > .nav-folder-title[data-path^=\'readwise\']\n    + .nav-folder-children  */ {\n  background-color: var(--neutral-blue);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'Media\'] {\n  background-color: var(--neutral-blue);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'Notes\'] {\n  background-color: var(--neutral-purple);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'Readwise\'] {\n  background-color: var(--neutral-purple);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'Utility\'] {\n  background-color: var(--gray);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'Projects\'] {\n  background-color: var(--light1);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'otv\'] {\n  background-color: var(--bright-purple);\n  color: var(--background-primary);\n}\n\n/** outliner bullet lines fade to color in edit mode -- https://discord.com/channels/686053708261228577/702656734631821413/884586663064535141 */\n/* .outliner-plugin-bls .cm-hmd-list-indent .cm-tab {\n  position: relative;\n  letter-spacing: 4px;\n}\n\n.HyperMD-list-line-1 .cm-formatting-list::before {\n  color: var(--rgb-faded-aqua) !important;\n}\n.cm-hmd-list-indent > span.cm-tab:nth-child(1)::before {\n  border-color: rgba(var(--rgb-faded-aqua), var(--alpha-ad)) !important;\n  box-shadow: 9px -8px 20px 4px rgba(var(--rgb-faded-aqua), var(--alpha-65));\n}\n\n.HyperMD-list-line-2 .cm-formatting-list::before {\n  color: var(--rgb-faded-blue) !important;\n}\n.cm-hmd-list-indent > span.cm-tab:nth-child(2)::before {\n  border-color: rgba(var(--rgb-faded-blue), var(--alpha-ad)) !important;\n  box-shadow: 9px -8px 20px 4px rgba(var(--rgb-faded-blue), var(--alpha-65));\n}\n\n.HyperMD-list-line-3 .cm-formatting-list::before {\n  color: var(--rgb-faded-purple) !important;\n}\n.cm-hmd-list-indent > span.cm-tab:nth-child(3)::before {\n  border-color: rgba(var(--rgb-faded-purple), var(--alpha-ad)) !important;\n  box-shadow: 9px -8px 20px 4px rgba(var(--rgb-faded-purple), var(--alpha-65));\n}\n\n.HyperMD-list-line-4 .cm-formatting-list::before {\n  color: var(--rgb-faded-red) !important;\n}\n.cm-hmd-list-indent > span.cm-tab:nth-child(4)::before {\n  border-color: rgba(var(--rgb-faded-red), var(--alpha-ad)) !important;\n  box-shadow: 9px -8px 20px 4px rgba(var(--rgb-faded-red), var(--alpha-65));\n}\n\n.HyperMD-list-line-5 .cm-formatting-list::before {\n  color: var(--rgb-faded-orange) !important;\n}\n.cm-hmd-list-indent > span.cm-tab:nth-child(5)::before {\n  border-color: rgba(var(--rgb-faded-orange), var(--alpha-ad)) !important;\n  box-shadow: 9px -8px 20px 4px rgba(var(--rgb-faded-orange), var(--alpha-65));\n}\n.HyperMD-list-line-5 .cm-formatting-list::before {\n  color: var(--rgb-faded-yellow) !important;\n}\n.cm-hmd-list-indent > span.cm-tab:nth-child(6)::before {\n  border-color: rgba(var(--rgb-faded-yellow), var(--alpha-ad)) !important;\n  box-shadow: 9px -8px 20px 4px rgba(var(--rgb-faded-yellow), var(--alpha-65));\n}\n.HyperMD-list-line-5 .cm-formatting-list::before {\n  color: var(--rgb-faded-green) !important;\n}\n.cm-hmd-list-indent > span.cm-tab:nth-child(7)::before {\n  border-color: rgba(var(--rgb-faded-green), var(--alpha-ad)) !important;\n  box-shadow: 9px -8px 20px 4px rgba(var(--rgb-faded-green), var(--alpha-65));\n} */\n\n/** Alternative File Tree Styling */\n\n.oz-folder-toggle > g > path {\n  fill: var(--neutral-aqua);\n}\ndiv.oz-folder-contents {\n  border-left: 1px solid var(--faded-aqua);\n}\n\n/** Block reference counter plugin styling */\n.block-ref-count {\n  /* border: var(--dark2) solid 2px; */\n  border: var(--neutral-aqua) solid 2px;\n  color: var(--neutral-aqua) !important;\n  font-weight: bold;\n  /* color: var(--interactive-accent) !important; */\n  background-color: var(--dark0-hard) !important;\n}\n.block-ref-count:hover {\n  color: var(--interactive-accent) !important;\n}\n/** TODO THIS for code syntax highlighting */\n/* {\n"CodeMirror Options@@cm-background@@dark": "#282a36",\n"CodeMirror Options@@cm-foreground@@dark": "#f8f8f2",\n"CodeMirror Options@@cm-comment@@dark": "#6272a4",\n"CodeMirror Options@@cm-string@@dark": "#f1fa8c",\n"CodeMirror Options@@cm-string-2@@dark": "#f1fa8c",\n"CodeMirror Options@@cm-number@@dark": "#bd93f9",\n"CodeMirror Options@@cm-variable@@dark": "#50fa7b",\n"CodeMirror Options@@cm-variable-2@@dark": "#ffffff",\n"CodeMirror Options@@cm-def@@dark": "#50fa7b",\n"CodeMirror Options@@cm-operator@@dark": "#ff79c6",\n"CodeMirror Options@@cm-keyword@@dark": "#ff79c6",\n"CodeMirror Options@@cm-atom@@dark": "#bd93f9",\n"CodeMirror Options@@cm-meta@@dark": "#f8f8f2",\n"CodeMirror Options@@cm-tag@@dark": "#ff79c6",\n"CodeMirror Options@@cm-attribute@@dark": "#50fa7b",\n"CodeMirror Options@@cm-qualifier@@dark": "#50fa7b",\n"CodeMirror Options@@cm-property@@dark": "#66d9ef",\n"CodeMirror Options@@cm-builtin@@dark": "#50fa7b",\n"CodeMirror Options@@cm-variable-3@@dark": "#ffb86c",\n"CodeMirror Options@@cm-type@@dark": "#ffb86c",\n"CodeMirror Options@@cm-activeline-background@@dark": "#414458",\n"CodeMirror Options@@cm-matchingbracket@@dark": "#ffffff"\n} */\n\n/** Make stars from Prominant Star Plugin Yellow */\n.lucide-bookmark {\n  color: var(--neutral-blue);\n  fill: var(--neutral-blue);\n}\n.lucide-hash {\n  color: var(--neutral-orange);\n}\n.lucide-search, .lucide-git-fork, .lucide-file {\n  color: var(--light1);\n}\n.lucide-folder-closed {\n  color: var(--neutral-yellow);\n}\n.lucide-clock {\n  color: var(--neutral-aqua);\n}\n.lucide-calendar-check {\n  color: var(--bright-red);\n}\n\n.svg-icon.sidebar-left, .svg-icon.sidebar-right  {\n  color: var(--bright-aqua);\n}\n\n/** Forced Dark Mode -- https://discord.com/channels/686053708261228577/694233507500916796/880493122608586782 */\n/* .theme-dark .workspace-leaf-content[data-type="pdf"] iframe {\n\n  filter: invert(0.883);\n}\n\n.theme-dark .pdf-embed iframe {\n  filter: invert(0.883);\n} */\n\n/* .G {\n\n  position: static;\n  display: block;\n  background-color: var(\n    --faded-aqua\n  ); \n  content: "Pro / Con"; \n\n  color: #ebdbb2;\n  font-weight: bold;\n}\n.O {\n  position: static;\n  display: block;\n  background-color: var(\n    --faded-orange\n  ); \n  content: "Pro / Con"; \n\n  color: #ebdbb2;\n  font-weight: bold;\n} */\n\n/* blockquote.G::before{ content: \'emoji\'; } */\n\n\n/** Meta Data Box -- https://discord.com/channels/686053708261228577/771575014382108672/908238393954172930 */\n/* .frontmatter-container {\n  float: right;\n  position: relative;\n  width: 3rem;\n  height: 2.2rem; \n  overflow: hidden;\n  border: none !important;\n  background-color: transparent;\n}\n\n.frontmatter-container::before {\n  content: "ℹ️";\n  color: rgb(17, 124, 119) ;\n  font-size: 40px;\n}\n\n\n.frontmatter-container:hover::before {\n  font-size: 30px !important;\n  float: right;\n  margin-top: -5px; \n}\n\n.frontmatter-container:hover>.frontmatter-container-header {\n  font-size: 20px;\n  text-decoration: underline;\n  padding-bottom: 10px;\n}\n\n.frontmatter-container:hover {\nmargin-left: 20px;\nmargin-bottom: 10px;\nwidth: 300px;\nheight: unset;\nbackground-color: var(--background-primary);\npadding: 0.6em;\npadding-top: 1.5em;\nz-index: 3;\nborder: 2px gray solid !important;\nborder-radius: 1.5em;} */\n\n\n'}
- theme.css

---

**Assistant** - 2024-09-05 22:20:05 UTC

 Certainly! I'll help you merge the color scheme from the CSS file into your Lualine configuration. Based on the CSS file you provided, I'll extract the relevant colors and update your Lualine config. Here's the modified Lualine configuration with the new color scheme:

```lua
return {
  "nvim-lualine/lualine.nvim",
  dependencies = { "nvim-tree/nvim-web-devicons" },
  config = function()
    local lualine = require("lualine")
    local lazy_status = require("lazy.status") -- to configure lazy pending updates count

    -- Colors extracted from the CSS file
    local colors = {
      bright_red = "#fb4934",
      bright_green = "#b8bb26",
      bright_yellow = "#fabd2f",
      bright_blue = "#83a598",
      bright_purple = "#d3869b",
      bright_aqua = "#8ec07c",
      bright_orange = "#fe8019",
      dark0 = "#282828",
      light0 = "#fbf1c7",
      gray = "#928374",
    }

    local my_lualine_theme = {
      normal = {
        a = { bg = colors.bright_blue, fg = colors.dark0, gui = "bold" },
        b = { bg = colors.dark0, fg = colors.light0 },
        c = { bg = colors.dark0, fg = colors.light0 },
      },
      insert = {
        a = { bg = colors.bright_green, fg = colors.dark0, gui = "bold" },
        b = { bg = colors.dark0, fg = colors.light0 },
        c = { bg = colors.dark0, fg = colors.light0 },
      },
      visual = {
        a = { bg = colors.bright_purple, fg = colors.dark0, gui = "bold" },
        b = { bg = colors.dark0, fg = colors.light0 },
        c = { bg = colors.dark0, fg = colors.light0 },
      },
      command = {
        a = { bg = colors.bright_yellow, fg = colors.dark0, gui = "bold" },
        b = { bg = colors.dark0, fg = colors.light0 },
        c = { bg = colors.dark0, fg = colors.light0 },
      },
      replace = {
        a = { bg = colors.bright_red, fg = colors.dark0, gui = "bold" },
        b = { bg = colors.dark0, fg = colors.light0 },
        c = { bg = colors.dark0, fg = colors.light0 },
      },
      inactive = {
        a = { bg = colors.gray, fg = colors.dark0, gui = "bold" },
        b = { bg = colors.gray, fg = colors.dark0 },
        c = { bg = colors.gray, fg = colors.dark0 },
      },
    }

    -- configure lualine with modified theme
    lualine.setup({
      options = {
        theme = my_lualine_theme,
      },
      sections = {
        lualine_x = {
          {
            lazy_status.updates,
            cond = lazy_status.has_updates,
            color = { fg = colors.bright_orange },
          },
          { "encoding" },
          { "fileformat" },
          { "filetype" },
        },
      },
    })
  end,
}
```

In this updated configuration:

1. I've replaced the original color definitions with colors from the CSS file, focusing on the "bright" variants for better visibility.
2. The background color (`bg`) is set to `dark0`, which is a dark gray color from the theme.
3. The foreground color (`fg`) for most sections is set to `light0`, which is a light color from the theme.
4. Each mode (normal, insert, visual, command, replace) uses a different bright color for its indicator.
5. The inactive state uses the gray color from the theme.
6. The lazy status update color is set to the bright orange color.

This configuration should give you a Lualine setup that matches the color scheme from your CSS file. You can further adjust the colors or add more variations if needed.

---

**Human** - 2024-09-05 23:21:48 UTC

when i'm on github and i see neovim plugins with install isntructions like this: i'm using lazy. what do i do? 

Install the theme with your preferred package manager:
vim-plug

```
Plug 'eddyekofo94/gruvbox-flat.nvim'
```

packer

```
use 'eddyekofo94/gruvbox-flat.nvim'
```

lazy.nvim

```
return {
    'eddyekofo94/gruvbox-flat.nvim',
    priority = 1000,
    enabled = true,
    config = function()
        vim.cmd([[colorscheme gruvbox-flat]])
    end,
}

```

---

**Assistant** - 2024-09-05 23:21:48 UTC

 If you're using lazy.nvim as your plugin manager for Neovim, you should follow the lazy.nvim installation instructions. Here's how you would typically add this plugin to your configuration:

1. Open your Neovim configuration file (usually `init.lua` or the file where you define your plugins).

2. In the section where you list your plugins for lazy.nvim, add the following:

```lua
return {
    'eddyekofo94/gruvbox-flat.nvim',
    priority = 1000,
    enabled = true,
    config = function()
        vim.cmd([[colorscheme gruvbox-flat]])
    end,
}
```

3. If you have a separate file for plugin specifications (like `lua/plugins/colorscheme.lua`), you can add it there instead.

4. Save the file and restart Neovim or run `:Lazy sync` to install the plugin.

This configuration does the following:
- Specifies the plugin to be installed ('eddyekofo94/gruvbox-flat.nvim')
- Sets a high priority (1000) to ensure it loads early
- Enables the plugin
- Includes a config function that sets the colorscheme to gruvbox-flat

Remember, the exact placement of this code might depend on how you've structured your Neovim configuration with lazy.nvim. Typically, it would go inside a table that's returned to lazy.nvim for plugin management.

After adding this and restarting Neovim or syncing lazy.nvim, the plugin should be installed and the colorscheme should be applied automatically.

---

**Human** - 2024-09-05 23:22:42 UTC

i've gone ahead and made my setup modular with multiple init.lua files. i'd imagine something like this would go in the main one?

---

**Assistant** - 2024-09-05 23:22:42 UTC

 If you've modularized your Neovim configuration, it's generally a good practice to keep your plugin definitions separate from your main `init.lua` file. Here's a common approach:

1. Create a separate file for your colorscheme plugins, if you haven't already. For example, you might create a file at `~/.config/nvim/lua/plugins/colorscheme.lua`.

2. In this `colorscheme.lua` file, you can add the plugin definition:

```lua
return {
    {
        'eddyekofo94/gruvbox-flat.nvim',
        priority = 1000,
        enabled = true,
        config = function()
            vim.cmd([[colorscheme gruvbox-flat]])
        end,
    }
}
```

3. In your main `init.lua`, you should have a section where you're setting up lazy.nvim. It might look something like this:

```lua
require("lazy").setup({
    spec = {
        -- import any other plugin files here
        { import = "plugins" },
    },
    -- any lazy.nvim options
})
```

This setup tells lazy.nvim to look in the `plugins` directory and import all the Lua files it finds there.

4. If you prefer to explicitly specify each plugin file, you could do something like this in your main `init.lua`:

```lua
require("lazy").setup({
    spec = {
        { import = "plugins.colorscheme" },
        -- import other plugin files...
    },
})
```

This approach keeps your main `init.lua` clean and organized, while allowing you to manage different types of plugins (like colorschemes, LSP configurations, etc.) in separate files.

Remember, the exact structure might vary depending on your preferences and how you've set up your Neovim configuration. The key is to keep things modular and organized in a way that makes sense to you.

---

**Human** - 2024-09-05 23:23:33 UTC

oh. i get it. so this is more true to form as a plugin than say a theme or skin.. or i guess the other way around.. both themes and skins are, in fact, plugins.

---

**Assistant** - 2024-09-05 23:23:33 UTC

 You're absolutely correct! Your realization is spot on. Let me break it down to reinforce your understanding:

1. Plugins in Neovim:
   Plugins are essentially extensions or add-ons that enhance Neovim's functionality. They can range from small utilities to complex features.

2. Themes and Colorschemes as Plugins:
   Themes and colorschemes in Neovim are indeed plugins. They're packages of code that modify Neovim's appearance, but they're installed and managed just like any other plugin.

3. Why They're Plugins:
   - They have their own repository
   - They can be installed using plugin managers
   - They often come with configuration options
   - They can be loaded, enabled, or disabled like other plugins

4. Plugin Managers:
   Whether you're using lazy.nvim, Packer, vim-plug, or any other plugin manager, they all treat themes and colorschemes as plugins.

5. Consistency in Management:
   This approach allows for consistent management of all Neovim extensions, whether they're changing the appearance or adding functionality.

Your realization is an important one for understanding how Neovim's ecosystem works. Themes, colorschemes, and functional plugins are all part of the same category in terms of how they're installed and managed, even if their effects on your Neovim setup are quite different.

This unified approach makes it easier to manage your entire Neovim configuration, including its appearance and functionality, using the same tools and processes.

---

**Human** - 2024-09-05 23:25:32 UTC

i've only got a couple of plugins explicitly called like that in any sort of init. most are their own lua config files. so i guess, would i add this to the init or create its own file?

---

**Assistant** - 2024-09-05 23:25:32 UTC

 Given your current setup, it would be most consistent to create a separate file for this plugin. Here's what I recommend:

1. Create a new file for the gruvbox-flat theme. You could name it something like:
   `~/.config/nvim/lua/plugins/gruvbox-flat.lua`

2. In this new file, add the following content:

   ```lua
   return {
       'eddyekofo94/gruvbox-flat.nvim',
       priority = 1000,
       enabled = true,
       config = function()
           vim.cmd([[colorscheme gruvbox-flat]])
       end,
   }
   ```

3. Make sure your main init.lua or the file where you set up lazy.nvim is configured to load plugin files from the `plugins` directory. It should have something like this:

   ```lua
   require("lazy").setup({
       spec = {
           { import = "plugins" },
           -- other imports if any
       },
       -- other lazy.nvim options
   })
   ```

   This setup tells lazy.nvim to automatically load all Lua files in the `plugins` directory.

4. If you haven't already, you might want to create a `plugins/init.lua` file that explicitly requires all your plugin files. This can help with organization and debugging. For example:

   ```lua
   return {
       require("plugins.gruvbox-flat"),
       -- require other plugin files here
   }
   ```

This approach keeps your configuration modular and consistent with your existing setup. Each plugin gets its own file, making it easy to manage, enable/disable, or modify individual plugins without affecting others.

---

**Human** - 2024-09-05 23:32:43 UTC

yeah, that's interesting. a bunch of these are listed as non loaded..


Attachments:
- image.png

---

**Assistant** - 2024-09-05 23:32:43 UTC

 This situation is quite normal and doesn't necessarily indicate a problem. Let me explain:

1. "Not Loaded" status: 
   Plugins marked as "Not Loaded" are typically lazy-loaded. This means they're installed but not activated until they're needed. This is a performance optimization technique.

2. Lazy loading triggers:
   The items in brackets (like `BufReadPre` and `BufNewFile`) are events that trigger the loading of these plugins. For example, a plugin might load only when you open a new file or start editing an existing one.

3. Performance benefits:
   Lazy loading improves Neovim's startup time by only loading plugins when they're actually needed, rather than all at once when Neovim starts.

4. Already up to date:
   The "already up to date" messages indicate that these plugins are installed and at their latest versions, regardless of whether they're currently loaded.

5. Specific loaded plugins:
   Some plugins like `lazygit.nvim` show multiple triggers, indicating they might load in various scenarios.

This setup is generally good for performance. Plugins load when needed, keeping your initial Neovim startup quick while ensuring functionality is available when required. If you're not experiencing any issues with missing functionality, this lazy-loading approach is working as intended.

---

**Human** - 2024-09-05 23:33:18 UTC

got it. thanks! i think i'm up and running the way i want to be..

---

**Assistant** - 2024-09-05 23:33:18 UTC

 That's great to hear! It sounds like you've successfully set up your Neovim environment with a good understanding of how your plugins are being managed and loaded. This kind of setup, with lazy loading and modular configuration, is excellent for maintaining a fast, efficient, and organized Neovim experience.

A few final tips to keep in mind:

1. Keep track of which plugins are lazy-loaded and how they're triggered. This can help you troubleshoot if you ever find a plugin isn't activating when you expect it to.

2. Regularly update your plugins to ensure you have the latest features and bug fixes.

3. If you add new plugins or modify your configuration, always test to make sure everything still works as expected.

4. Don't hesitate to tweak your setup as you use it more. Your needs might change over time, and Neovim is highly customizable.

5. Keep your configuration files backed up or in version control (like git) so you can easily revert changes if needed.

If you have any questions in the future about your Neovim setup or want to optimize it further, feel free to ask. Enjoy your newly configured Neovim!

---

**Human** - 2024-09-05 23:33:50 UTC

it's a nice variant of gruvbox, huh?

---

**Assistant** - 2024-09-05 23:33:50 UTC

 Yes, the gruvbox-flat theme is indeed a very nice variant of the classic Gruvbox colorscheme. It's known for its clean, flat design that maintains the warmth and readability of the original Gruvbox while offering a more modern look.

Some notable features of gruvbox-flat include:

1. Flatter design: As the name suggests, it reduces some of the shadows and gradients found in the original Gruvbox for a more contemporary appearance.

2. Improved contrast: It often provides better contrast in certain areas, which can enhance readability.

3. Consistency across different file types: It aims to provide a more consistent look across various programming languages and file types.

4. Customization options: Like many modern Neovim themes, it often comes with options to tweak colors and styles to your preference.

5. Good support for plugins: It usually offers good color integration with popular Neovim plugins.

The Gruvbox color palette itself is beloved by many developers for its warm, earthy tones that are easy on the eyes during long coding sessions. The "flat" variant builds on this foundation to create a theme that's both aesthetically pleasing and functional.

If you're enjoying it, that's great! A good color scheme can significantly enhance your coding experience by reducing eye strain and making code more readable. It's a personal choice, but gruvbox-flat is certainly a solid and popular one in the Neovim community.

---

**Human** - 2024-09-07 00:05:14 UTC

i think we might be able to simplify that lualine config a little.. 

To enable the gruvbox theme for Lualine, simply specify it in your lualine settings:
require('lualine').setup {
  options = {
    theme = 'gruvbox-flat'
    -- ... your lualine config
  }
}
To enable the gruvbox-flat colorscheme for Lightline:

---

**Assistant** - 2024-09-07 00:05:14 UTC

 Absolutely! If the gruvbox-flat theme provides a built-in configuration for Lualine, we can indeed simplify the configuration significantly. Let's update your Lualine configuration to use the built-in gruvbox-flat theme:

```lua
return {
  "nvim-lualine/lualine.nvim",
  dependencies = { "nvim-tree/nvim-web-devicons" },
  config = function()
    local lualine = require("lualine")
    local lazy_status = require("lazy.status") -- to configure lazy pending updates count

    lualine.setup({
      options = {
        theme = 'gruvbox-flat',
        -- You can keep any other options you had here
      },
      sections = {
        lualine_x = {
          {
            lazy_status.updates,
            cond = lazy_status.has_updates,
            color = { fg = "#fe8019" }, -- This is the bright_orange from gruvbox
          },
          { "encoding" },
          { "fileformat" },
          { "filetype" },
        },
      },
    })
  end,
}
```

This configuration:

1. Uses the built-in 'gruvbox-flat' theme for Lualine.
2. Keeps the custom section for displaying lazy.nvim update status.
3. Maintains the other sections you had (encoding, fileformat, filetype).

By using the built-in theme, we can remove all the custom color definitions and theme setup we had before. This not only simplifies the configuration but also ensures that the Lualine theme perfectly matches the gruvbox-flat colorscheme you're using for Neovim.

The only custom color we're keeping is for the lazy status updates, which uses the bright orange color from the gruvbox palette.

This approach gives you a more streamlined configuration that's easier to maintain and automatically stays in sync with any updates to the gruvbox-flat theme. If you find that you need to customize any specific aspects of the Lualine appearance, you can always add those customizations back in as needed.

---

