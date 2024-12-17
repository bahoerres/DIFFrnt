# Customizing Obsidian's Monospace Fonts

Created: 2024-07-15 01:42:39 UTC
Updated: 2024-07-15 05:35:45 UTC
UUID: 7ccf6ce6-af30-4005-b1bd-73cd63f47fd7
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-07-15 01:42:47 UTC

i'm trying my hand at editing a css theme and i would like a bit of help.. my primary interest is changing the fonts.. can you tell me what this will do in relation to the documents in obsidian? 

.theme-dark {
  --font-monospace: "fira code", "Hack Nerd Font", "Source Code Pro", monospace;

---

**Assistant** - 2024-07-15 01:42:47 UTC

 This CSS code snippet will affect the monospace font used in the dark theme of Obsidian. Here's what it does:

1. It targets the dark theme specifically with `.theme-dark`.
2. It sets the `--font-monospace` custom property (CSS variable) to a list of font families.

In Obsidian, this will change the font used for:

1. Code blocks
2. Inline code
3. Any other elements that use monospace fonts in the interface

The browser will try to use these fonts in the following order:

1. "fira code"
2. "Hack Nerd Font"
3. "Source Code Pro"
4. Any default monospace font if none of the above are available

This change will only apply when using the dark theme in Obsidian. The light theme would be unaffected unless you have a similar rule for `.theme-light`.

Would you like more information on how to modify other fonts in Obsidian, or how to apply this to both light and dark themes?

---

**Human** - 2024-07-15 01:45:45 UTC

let's have a go at this together. find me information about fonts and how they display with this theme.


Attachments:
- {'file_name': 'theme.css', 'file_size': 81346, 'file_type': 'text/css', 'extracted_content': '/**=================================================================================\n/** ██████╗░██████╗░██╗░░░██╗░█████╗░███╗░░██╗██╗░██████╗\n/** ██╔══██╗██╔══██╗╚██╗░██╔╝██╔══██╗████╗░██║╚█║██╔════╝\n/** ██████╦╝██████╔╝░╚████╔╝░███████║██╔██╗██║░╚╝╚█████╗░\n/** ██╔══██╗██╔══██╗░░╚██╔╝░░██╔══██║██║╚████║░░░░╚═══██╗\n/** ██████╦╝██║░░██║░░░██║░░░██║░░██║██║░╚███║░░░██████╔╝\n/** ╚═════╝░╚═╝░░╚═╝░░░╚═╝░░░╚═╝░░╚═╝╚═╝░░╚══╝░░░╚═════╝░\n/**\n/** ░█████╗░██████╗░░██████╗██╗██████╗░██╗░█████╗░███╗░░██╗\u2003\u2003░█████╗░░██████╗░██████╗\n/** ██╔══██╗██╔══██╗██╔════╝██║██╔══██╗██║██╔══██╗████╗░██║\u2003\u2003██╔══██╗██╔════╝██╔════╝\n/** ██║░░██║██████╦╝╚█████╗░██║██║░░██║██║███████║██╔██╗██║\u2003\u2003██║░░╚═╝╚█████╗░╚█████╗░\n/** ██║░░██║██╔══██╗░╚═══██╗██║██║░░██║██║██╔══██║██║╚████║\u2003\u2003██║░░██╗░╚═══██╗░╚═══██╗\n/** ╚█████╔╝██████╦╝██████╔╝██║██████╔╝██║██║░░██║██║░╚███║\u2003\u2003╚█████╔╝██████╔╝██████╔╝\n/** ░╚════╝░╚═════╝░╚═════╝░╚═╝╚═════╝░╚═╝╚═╝░░╚═╝╚═╝░░╚══╝\u2003\u2003░╚════╝░╚═════╝░╚═════╝░\n/**==================================================================================*/\n\n/** ----- TABLE OF CONTENTS ----- */\n\n/** 1. Default Theme */\n/** 2. Custom CSS Section */\n/** ____ 2.1 Bullet Points */\n/** ________ 2.1.1 Bullet Point Relationship Lines -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/2 */\n/** ________ 2.1.2 tasklist (preview) indentation lines correction -- https://forum.obsidian.md/t/bullet-lines-in-css-for-checkboxes/6262/3 */\n/** ________ 2.1.3 Better Bullet Points In Edit Mode https://forum.obsidian.md/t/clutter-free-edit-mode/6791/30 */\n/** ________ 2.1.4 Bullet points in preview -- https://discord.com/channels/686053708261228577/702656734631821413/772094128832905226 */\n/** ________ 2.1.5 Bullet List Boxing -- https://discord.com/channels/686053708261228577/702656734631821413/784610806561636413 */\n/** ____ 2.2 File Navigation Pane */\n/** ________ 2.2.1 Relationship lines for the folder levels in file navigation: https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/112 */\n/** ________ 2.2.2 Custom icons differing files and folders -- https://discordapp.com/channels/686053708261228577/702656734631821413/755293685046050896 */\n/** ________ 2.2.3 Top Level Folder Icons -- https://discord.com/channels/686053708261228577/702656734631821413/805318111917113354 */\n/** ________ 2.2.4 Outline Relationship lines -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/357 */\n/** ________ 2.2.5 Image file navigation icon -- https://discord.com/channels/686053708261228577/702656734631821413/866399284437843978 */\n/** ____ 2.3 Clutter Free Mode */\n/** ________ 2.3.1 Make subtler folding gutter arrows -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/10 */\n/** ________ 2.3.2 Hide Block Reference ID\'s -- https://discord.com/channels/686053708261228577/716028884885307432/769267134114037871 */\n/** ________ 2.3.3 Shortened Url Links -- https://forum.obsidian.md/t/hide-or-truncate-urls-in-editor-using-css/359/3 */\n/** ________ 2.3.4 highlight (==) not visible anymore if not active line -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/221 */\n/** ________ 2.3.5 Make code blocks wrap in preview mode too */\n/** ________ 2.3.6 Hide search query title and stop highlighting found element -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/307 */\n/** ________ 2.3.7 vertically centre line numbers in large paragraphs -- https://discord.com/channels/686053708261228577/702656734631821413/822257712825237524 */\n/** ________ 2.3.8 Fix padding of transcluded blocks in lists */\n/** ________ 2.3.9 Custom Highlight Colors based on templater */\n/** ____ 2.4 Font Formatting */\n/** ________ 2.4.1 Make Mathjax Font Larger */\n/** ________ 2.4.2 Hyphenation & Justification -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/25 */\n/** ________ 2.4.3 Stylish Block Quotes -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/39 */\n/** ________ 2.4.4 General Font Formatting */\n/** ________ 2.4.5 Stylish Signatures -- https://discord.com/channels/686053708261228577/702656734631821413/784210155923177552 */\n/** ____ 2.5 Graph Formatting */\n/** ________ 2.5.1 Graph View CSS -- https://discordapp.com/channels/686053708261228577/702656734631821413/760488978691784705 */\n/** ____ 2.6 Image Manipulation */\n/** ________ 2.6.1 Image Hover Grow -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/29 */\n/** ____ 2.7 Check Boxes */\n/** ________ 2.7.1 Nicer Round Checkboxes -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/34 */\n/** ________ 2.7.2 Animated Check Boxes -- https://github.com/TriDiamond/Obsidian-Obsidianite/blob/82207bed4313ee0e6f0bb1fd59b04129408018f5/obsidian.css#L463 */\n/** ________ 2.7.3 Hide Completed Tasks In Preview -- https://forum.obsidian.md/t/hide-checked-todo-s/14043 */\n/** ____ 2.8 Tags */\n/** ________ 2.8.1 Tag Pills -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/72 */\n/** ________ 2.8.2 Tags to the side of the document -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/327 */\n/** ____ 2.9 [[Link]] Modification */\n/** ________ 2.9.1 Bigger Link Hover Popup Preview -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/175 */\n/** ________ 2.9.2 The modal popups from link hovers */\n/** ________ 2.9.3 Input Links -- https://discord.com/channels/686053708261228577/707816848615407697/844751423253905458 */\n/** ____ 2.10 Plugin Specific CSS */\n/** ________ 2.10.1 Calendar Plugin CSS */\n/** ________ 2.10.2 T0DOIST Plugin CSS -- https://github.com/jamiebrynes7/clair-de-lune-obsidian-theme/blob/master/src/modules/extensions/todoist.scss */\n/** ________ 2.10.3 DayPlanner Plugin CSS */\n/** ________ 2.10.4 Folder Note CSS */\n/** ____ 2.11 Heading Formatting */\n/** ________ 2.11.1 Heading Under Gradient Line -- https://github.com/TriDiamond/Obsidian-Obsidianite */\n/** ________ 2.11.2 Emoji Orientation in Andy Mode Headers -- https://discord.com/channels/686053708261228577/702656734631821413/775900471406624768 */\n/** ________ 2.11.3 Heading Horizontal Lines -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/288?u=tallguyjenks */\n/** ____ 2.12 Horizontal Rule Formatting */\n/** ________ 2.12.1 Aesthetic Horizontal Rule -- https://github.com/TriDiamond/Obsidian-Obsidianite */\n/** ____ 2.13 PDF Export Formatting */\n/** ________ 2.13.1 Page Break -- https://gist.github.com/liamcain/81679412643690a7cdd13dff4dc909ce */\n/** ____ 2.14 Tables */\n/** ________ 2.14.1 Banded Table Rows -- https://discord.com/channels/686053708261228577/702656734631821413/777106171948564500 */\n/** ________ 2.14.2 Full Width Tables */\n/** ________ 2.14.3 Numbered Table Rows-- https://discord.com/channels/686053708261228577/707816848615407697/832558496892846080 */\n/** ____ 2.15 Custom HTML Elements */\n/** ________ 2.15.1 aside format -- https://discord.com/channels/686053708261228577/707816848615407697/784964375806083124 */\n/** ________ 2.15.2 Buttons -- https://discord.com/channels/686053708261228577/744933215063638183/784289179328708648 */\n/** ________ 2.15.3 Definition Lists */\n/** ________ 2.15.4 Code Language Fences -- https://discord.com/channels/686053708261228577/702656734631821413/822915125522202654 */\n/** ________ 2.15.5 Rounded Edges of Inline Code blocks https://discord.com/channels/686053708261228577/702656734631821413/822181163639767081 */\n/** ____ 2.16 Quick Switcher */\n/** ________ 2.16.1 Fix the quick switcher highligher after background color change */\n/** __ 3. Grave Yard */\n/** ============================================================================================================================================================ */\n\n/** 1. Default Theme */\n:root {\n  --dark0-hard: #1d2021;\n  --dark0: #282828;\n  --dark0-soft: #32302f;\n  --dark1: #3c3836;\n  --dark2: #504945;\n  --dark3: #665c54;\n  --dark4: #7c6f64;\n\n  --gray: #928374;\n\n  --light0-hard: #f9f5d7;\n  --light0: #fbf1c7;\n  --light0-soft: #f2e5bc;\n  --light1: #ebdbb2;\n  --light2: #d5c4a1;\n  --light3: #bdae93;\n  --light4: #a89984;\n\n  --bright-red: #fb4934;\n  --bright-green: #b8bb26;\n  --bright-yellow: #fabd2f;\n  --bright-blue: #83a598;\n  --bright-purple: #d3869b;\n  --bright-aqua: #8ec07c;\n  --bright-orange: #fe8019;\n\n  --neutral-red: #cc241d;\n  --neutral-green: #98971a;\n  --neutral-yellow: #d79921;\n  --neutral-blue: #458588;\n  --neutral-purple: #b16286;\n  --neutral-aqua: #689d6a;\n  --neutral-orange: #d65d0e;\n\n  --faded-red: #9d0006;\n  --faded-green: #79740e;\n  --faded-yellow: #b57614;\n  --faded-blue: #076678;\n  --faded-purple: #8f3f71;\n  --faded-aqua: #427b58;\n  --faded-orange: #af3a03;\n\n  /* These are for: */\n  /** outliner bullet lines fade to color in edit mode -- https://discord.com/channels/686053708261228577/702656734631821413/884586663064535141 */\n  --rgb-faded-red: 157, 0, 6;\n  --rgb-faded-green: 121, 116, 14;\n  --rgb-faded-yellow: 181, 118, 20;\n  --rgb-faded-blue: 7, 102, 120;\n  --rgb-faded-purple: 143, 63, 113;\n  --rgb-faded-aqua: 66, 123, 88;\n  --rgb-faded-orange: 175, 58, 3;\n  --alpha-ad: 0.68;\n  --alpha-65: 0.4;\n}\n\n.theme-dark {\n  --font-monospace: "fira code", "Hack Nerd Font", "Source Code Pro", monospace;\n  --background-primary: var(--dark0);\n  --background-primary-alt: var(--dark0);\n  --background-secondary: var(--dark0-hard);\n  --background-secondary-alt: var(--dark1);\n  --text-normal: var(--light0);\n  --text-faint: var(--light3);\n  --text-title-h1: var(--neutral-red);\n  --text-title-h2: var(--neutral-orange);\n  --text-title-h3: var(--neutral-yellow);\n  --text-title-h4: var(--neutral-green);\n  --text-title-h5: var(--neutral-aqua);\n  --text-title-h6: var(--neutral-purple);\n  --text-link: var(--bright-blue);\n  --text-a: var(--bright-orange);\n  --text-a-hover: var(--bright-blue);\n  --text-mark: var(--neutral-yellow);\n  --pre-code: var(--dark1);\n  --text-highlight-bg: var(--faded-aqua);\n  --interactive-accent: var(--bright-orange);\n  --interactive-before: var(--dark4);\n  --background-modifier-border: var(--dark2);\n  --text-accent: var(--bright-orange);\n  --interactive-accent-rgb: var(--bright-orange);\n  --inline-code: var(--bright-blue);\n  --code-block: var(--bright-blue);\n  --vim-cursor: var(--bright-orange);\n  --text-selection: rgba(168, 153, 132, 0.5); /* light4 */\n}\n\n.theme-light {\n  --background-primary: var(--light0);\n  --background-primary-alt: var(--light0);\n  --background-secondary: var(--light0-hard);\n  --background-secondary-alt: var(--light1);\n  --text-normal: var(--dark0);\n  --text-faint: var(--dark3);\n  --text-title-h1: var(--faded-red);\n  --text-title-h2: var(--faded-orange);\n  --text-title-h3: var(--faded-yellow);\n  --text-title-h4: var(--faded-green);\n  --text-title-h5: var(--faded-aqua);\n  --text-link: var(--neutral-blue);\n  --text-a: var(--neutral-orange);\n  --text-a-hover: var(--neutral-blue);\n  --text-mark: var(--neutral-yellow);\n  --pre-code: var(--light1);\n  --text-highlight-bg: var(--bright-aqua);\n  --interactive-accent: var(--neutral-orange);\n  --interactive-before: var(--light4);\n  --background-modifier-border: var(--light2);\n  --text-accent: var(--neutral-orange);\n  --interactive-accent-rgb: var(--neutral-orange);\n  --inline-code: var(--neutral-blue);\n  --vim-cursor: var(--neutral-orange);\n  --text-selection: rgba(189, 174, 147, 0.5); /* light3 */\n}\n\n.theme-dark code[class*="language-"],\n.theme-dark pre[class*="language-"],\n.theme-light code[class*="language-"],\n.theme-light pre[class*="language-"] {\n  text-shadow: none !important;\n  background-color: var(--pre-code) !important;\n}\n\n.graph-view.color-circle,\n.graph-view.color-fill-highlight,\n.graph-view.color-line-highlight {\n  color: var(--interactive-accent-rgb) !important;\n}\n.graph-view.color-text {\n  color: var(--text-a-hover) !important;\n}\n/*\n.graph-view.color-fill\n{\n    color: var(--background-secondary);\n}\n.graph-view.color-line\n{\n  color: var(--background-modifier-border);\n}\n*/\n\nhtml,\nbody {\n  font-size: 16px !important;\n  font-family: var(\n    --font-monospace\n  ); /** Remove this to return body font back to normal */\n\n  /** Norse rune font for hilarity Comes from dafont.com */\n  --custom-font: "Norse";\n  /* --custom-font: \'fira code\', \'Hack Nerd Font\', \'Source Code Pro\', monospace; */\n  --custom-H1-font-size: 38px;\n  --custom-H2-font-size: 34px;\n  --custom-H3-font-size: 30px;\n  --custom-H4-font-size: 26px;\n  --custom-H5-font-size: 22px;\n  --custom-H6-font-size: 18px;\n  /* --custom-font: var(--font-monospace); */\n  /* font-family: \'Norse\';\n    font-size: 20px !important; */\n}\n\nstrong {\n  font-weight: 600 !important;\n}\n\na,\n.cm-hmd-internal-link {\n  color: var(--text-a) !important;\n  text-decoration: none !important;\n}\n\na:hover,\n.cm-hmd-internal-link:hover,\n.cm-url {\n  color: var(--text-a-hover) !important;\n  text-decoration: none !important;\n}\n\nmark {\n  background-color: var(--text-mark) !important;\n  color: var(--dark0) !important;\n}\n\n.view-actions a {\n  color: var(--text-normal) !important;\n}\n\n.view-actions a:hover {\n  color: var(--text-a) !important;\n}\n\n.HyperMD-codeblock-bg {\n  background-color: var(--pre-code) !important;\n}\n\n.HyperMD-codeblock {\n  line-height: 1.4em !important;\n  color: var(--code-block) !important;\n}\n\n.HyperMD-codeblock-begin {\n  border-top-left-radius: 4px !important;\n  border-top-right-radius: 4px !important;\n}\n\n.HyperMD-codeblock-end {\n  border-bottom-left-radius: 4px !important;\n  border-bottom-right-radius: 4px !important;\n}\n\nth {\n  font-weight: 600 !important;\n}\n\nthead {\n  border-bottom: 2px solid var(--background-modifier-border) !important;\n}\n\n.HyperMD-table-row {\n  line-height: normal !important;\n  padding-left: 4px !important;\n  padding-right: 4px !important;\n  background-color: var(--pre-code) !important;\n}\n\n/* .HyperMD-table-row-0 { */\n  /* padding-top: 4px !important; */\n/* } */\n\n.CodeMirror-foldgutter-folded,\n.is-collapsed .nav-folder-collapse-indicator {\n  color: var(--text-a) !important;\n}\n\n.nav-file-tag {\n  color: var(--text-a) !important;\n}\n\n.is-active .nav-file-title {\n  color: var(--text-a) !important;\n  background-color: var(--background-primary-alt) !important;\n}\n\n.nav-file-title {\n  border-bottom-left-radius: 0 !important;\n  border-bottom-right-radius: 0 !important;\n  border-top-left-radius: 0 !important;\n  border-top-right-radius: 0 !important;\n}\n\nimg {\n  display: block !important;\n  margin-left: auto !important;\n  margin-right: auto !important;\n}\n\n.HyperMD-list-line {\n  padding-top: 0 !important;\n}\n.CodeMirror-code,\n.CodeMirror-linenumber,\n.cm-formatting {\n  font-family: var(--font-monospace) !important;\n  font-size: 0.9em;\n}\n\n.markdown-preview-section pre code,\n.markdown-preview-section code {\n  font-size: 0.9em !important;\n  background-color: var(--pre-code) !important;\n}\n\n.markdown-preview-section pre code {\n  padding: 4px !important;\n  line-height: 1.4em !important;\n  display: block !important;\n  color: var(--code-block) !important;\n}\n\n.markdown-preview-section code {\n  color: var(--inline-code) !important;\n}\n\n.cm-s-obsidian,\n.cm-inline-code {\n  -webkit-font-smoothing: auto !important;\n}\n\n.cm-inline-code {\n  color: var(--inline-code) !important;\n  background-color: var(--pre-code) !important;\n  padding: 1px !important;\n}\n\n.workspace-leaf-header-title {\n  font-weight: 600 !important;\n}\n\n.side-dock-title {\n  padding-top: 15px !important;\n  font-size: 20px !important;\n}\n\n.side-dock-ribbon-tab:hover,\n.side-dock-ribbon-action:hover,\n.side-dock-ribbon-action.is-active:hover,\n.nav-action-button:hover,\n.side-dock-collapse-btn:hover {\n  color: var(--text-a);\n}\n\n.side-dock {\n  border-right: 0 !important;\n}\n\n.cm-s-obsidian,\n.markdown-preview-view {\n  /* padding-left: 10px !important; */\n  padding-right: 10px !important;\n}\n\n/* vertical resize-handle */\n.workspace-split.mod-vertical > * > .workspace-leaf-resize-handle,\n.workspace-split.mod-left-split > .workspace-leaf-resize-handle,\n.workspace-split.mod-right-split > .workspace-leaf-resize-handle {\n  width: 1px !important;\n  background-color: var(--background-secondary-alt);\n}\n\n/* horizontal resize-handle */\n.workspace-split.mod-horizontal > * > .workspace-leaf-resize-handle {\n  height: 1px !important;\n  background-color: var(--background-secondary-alt);\n}\n\n/* Remove vertical split padding */\n.workspace-split.mod-root .workspace-split.mod-vertical .workspace-leaf-content,\n.workspace-split.mod-vertical > .workspace-split,\n.workspace-split.mod-vertical > .workspace-leaf,\n.workspace-tabs {\n  padding-right: 0px;\n}\n\n.markdown-embed-title {\n  font-weight: 600 !important;\n}\n\n.markdown-embed {\n  padding-left: 10px !important;\n  padding-right: 10px !important;\n  margin-left: 10px !important;\n  margin-right: 10px !important;\n}\n\n.mermaid .note {\n  fill: var(--dark3) !important;\n}\n\n.cm-header-1,\n.markdown-preview-section h1 {\n  font-weight: 500 !important;\n  font-size: var(--custom-H1-font-size) !important;\n  color: var(--text-title-h1) !important;\n  /*     background: -webkit-linear-gradient(var(--bright-red),var(--faded-red));\n    -webkit-background-clip: text;\n    -webkit-text-fill-color: transparent; */\n  font-family: var(--custom-font) !important;\n}\n\n.cm-header-2,\n.markdown-preview-section h2 {\n  font-weight: 500 !important;\n  font-size: var(--custom-H2-font-size) !important;\n  color: var(--text-title-h2) !important;\n  /*     background: -webkit-linear-gradient(var(--bright-orange),var(--faded-orange));\n    -webkit-background-clip: text;\n    -webkit-text-fill-color: transparent; */\n  font-family: var(--custom-font) !important;\n}\n\n.cm-header-3,\n.markdown-preview-section h3 {\n  font-weight: 500 !important;\n  font-size: var(--custom-H3-font-size) !important;\n  color: var(--text-title-h3) !important;\n  /*     background: -webkit-linear-gradient(var(--bright-yellow),var(--faded-yellow));\n    -webkit-background-clip: text;\n    -webkit-text-fill-color: transparent; */\n  font-family: var(--custom-font) !important;\n}\n\n.cm-header-4,\n.markdown-preview-section h4 {\n  font-weight: 500 !important;\n  font-size: var(--custom-H4-font-size) !important;\n  color: var(--text-title-h4) !important;\n  /*     background: -webkit-linear-gradient(var(--bright-green),var(--faded-green));\n    -webkit-background-clip: text;\n    -webkit-text-fill-color: transparent; */\n  font-family: var(--custom-font) !important;\n}\n\n.cm-header-5,\n.markdown-preview-section h5 {\n  font-weight: 500 !important;\n  font-size: var(--custom-H5-font-size) !important;\n  color: var(--text-title-h5) !important;\n  /*   background: -webkit-linear-gradient(var(--bright-aqua),var(--faded-aqua));\n  -webkit-background-clip: text;\n  -webkit-text-fill-color: transparent; */\n  font-family: var(--custom-font) !important;\n}\n\n.cm-header-6,\n.markdown-preview-section h6 {\n  font-weight: 500 !important;\n  font-size: var(--custom-H6-font-size) !important;\n  color: var(--text-title-h6) !important;\n  /*   background: -webkit-linear-gradient(var(--bright-purple),var(--faded-purple));\n  -webkit-background-clip: text;\n  -webkit-text-fill-color: transparent; */\n  font-family: var(--custom-font) !important;\n}\n\n.suggestion-item.is-selected {\n  background-color: var(--background-secondary);\n}\n\n.empty-state-container:hover {\n  background-color: var(--background-secondary-alt);\n  border: 5px solid var(--interactive-accent) !important;\n}\n\n.checkbox-container {\n  background-color: var(--interactive-before);\n}\n\n.checkbox-container:after {\n  background-color: var(--background-secondary-alt);\n}\n\n.mod-cta {\n  color: var(--background-secondary-alt) !important;\n  font-weight: 600 !important;\n}\n\n.mod-cta:hover {\n  background-color: var(--interactive-before) !important;\n  font-weight: 600 !important;\n}\n\n.CodeMirror-cursor {\n  background-color: var(--vim-cursor) !important;\n  opacity: 60% !important;\n}\n\ninput.task-list-item-checkbox {\n  border: 1px solid var(--dark4);\n  appearance: none;\n  -webkit-appearance: none;\n}\n\ninput.task-list-item-checkbox:checked {\n  background-color: var(--dark4);\n  box-shadow: inset 0 0 0 2px var(--background-primary);\n}\n\n::selection {\n  background-color: var(--text-selection) !important;\n}\n\n/** .. 2. Custom CSS Section */\n/** ____ 2.1 Bullet Points */\n/** ______ 2.1.1 Bullet Point Relationship Lines -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/2 */\n.cm-hmd-list-indent .cm-tab,\nul ul {\n  position: relative;\n}\n.cm-hmd-list-indent .cm-tab::before,\nul ul::before {\n  content: "";\n  border-left: 1px solid var(--bright-aqua);\n  position: absolute;\n}\n.cm-hmd-list-indent .cm-tab::before {\n  left: 5px;\n  top: -5px;\n  bottom: -4px;\n}\nul ul::before {\n  left: -16px;\n  top: 0;\n  bottom: 0;\n}\n.cm-hmd-list-indent .cm-tab,\nol ol {\n  position: relative;\n}\n.cm-hmd-list-indent .cm-tab::before,\nol ol::before {\n  content: "";\n  border-left: 1px solid var(--bright-aqua);\n  position: absolute;\n}\n.cm-hmd-list-indent .cm-tab::before {\n  left: 5px;\n  top: -5px;\n  bottom: -4px;\n}\nol ol::before {\n  left: -16px;\n  top: 0;\n  bottom: 0;\n}\n/** ______ 2.1.2 tasklist (preview) indentation lines correction -- https://forum.obsidian.md/t/bullet-lines-in-css-for-checkboxes/6262/3 */\n.contains-task-list::before {\n  left: 10px;\n}\n/** ______ 2.1.3 Better Bullet Points In Edit Mode https://forum.obsidian.md/t/clutter-free-edit-mode/6791/30 */\ndiv:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-formatting-list-ul {\n  color: transparent;\n  position: relative;\n}\ndiv:not(.CodeMirror-activeline)\n  > .CodeMirror-line\n  span.cm-formatting-list-ul:after {\n  content: "•";\n  position: absolute;\n  top: -6px;\n  left: 4px;\n  color: var(--bright-aqua);\n  font-family: sans-serif;\n  font-size: 20px;\n}\n/** ______ 2.1.4 Bullet points in preview -- https://discord.com/channels/686053708261228577/702656734631821413/772094128832905226 */\nul,\nul ul,\nol ul,\nul ul ul,\nol ul ul {\n  list-style: none;\n}\nli > p {\n  display: inline-block;\n  margin-top: 0;\n  margin-bottom: 0;\n}\nul li:not(.task-list-item)::before {\n  content: "•";\n  color: var(--bright-aqua);\n  display: inline-block;\n  width: 1em;\n  margin-left: -1.15em;\n  padding: 0;\n  font-weight: bold;\n  text-shadow: 0 0 0.5em var(--bright-aqua);\n}\nul ul li:not(.task-list-item)::before {\n  content: "•";\n}\nul ul ul li:not(.task-list-item)::before {\n  content: "•";\n}\n/** ______ 2.1.5 Bullet List Boxing -- https://discord.com/channels/686053708261228577/702656734631821413/784610806561636413 */\n/*\n* { list-style: none;}\nul li:not(.task-list-item) {\n  margin-left: 15px;\n  position: relative;\n  padding-left: 5px;\n  padding: 5px;\n  list-style-position: ;\n  border-left: 5px solid var(--faded-aqua);\n  box-shadow: 0 0 0 0.5px var(--bright-aqua);\n  border-radius: 10px;\n}\nol {\n  counter-reset: cupcake;\n  padding-left: 5px;\n}\nol li {\n  counter-increment: cupcake;\n  margin-left: 15px;\n  position: relative;\n  padding-left: 5px;\n  list-style-position: inside;\n  border-left: 5px solid var(--faded-aqua);\n  box-shadow: 0 0 0 0.5px var(--bright-aqua);\n  border-radius: 10px;\n}\nol li:before {\n  content: counters(cupcake, \'.\') \'  \';\n  color: var(--bright-green);\n  font-weight: bold;\n  display: inline-block;\n  white-space: pre;\n}\n.markdown-preview-view .collapse-indicator {\n  margin-left: -46px;\n  padding: 0 18px;\n}\n.markdown-preview-view .heading-collapse-indicator {\n  margin-left: -25px;\n  padding: 0 8px;\n}\ndiv.heading-collapse-indicator.collapse-indicator.collapse-icon:hover{\n  color: var(--text-accent);\n}\n.markdown-preview-section:not(.is-collapsed) svg.right-triangle{\n  color: var(--text-accent);\n}\ndiv.collapsible-item-collapse.collapse-icon{\n  color: var(--text-accent);\n} */\n/** ____ 2.2 File Navigation Pane */\n/** ______ 2.2.1 Relationship lines for the folder levels in file navigation: https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/112 */\n.outline .collapsible-item-children {\n  margin-left: 20px;\n  border-left: 1px solid var(--faded-aqua);\n  border-radius: 4px;\n  transition: all 0.5s ease-in-out;\n}\n.outline .collapsible-item-children:hover {\n  border-left-color: var(--faded-aqua);\n}\n.nav-folder-children .nav-folder-children {\n  margin-left: 20px;\n  padding-left: 0;\n  border-left: 1px solid var(--faded-aqua);\n  border-radius: 4px;\n  transition: all 0.5s ease-in-out;\n}\n.nav-folder-children .nav-folder-children:hover {\n  border-left-color: var(--faded-aqua);\n}\n/** ______ 2.2.2 Custom icons differing files and folders: https://discordapp.com/channels/686053708261228577/702656734631821413/755293685046050896 */\n/* Emoji */\n.nav-file-title-content::before { content: "📝️ "; }\n.nav-folder-title-content::before { content: \'📂 \'; }\n.nav-file-title-content[data-link-data-href="Flows"]::before { content: \'♻️ \'; }\n.nav-file-title-content[data-link-data-href="Tasks"]::before { content: \'✅️ \'; }\n.nav-file-title-content[data-link-data-href="Readwise Items To Review"]::before { content: \'🔁 \'; }\n.nav-file-title-content[data-link-data-href="Timeline"]::before { content: \'🕓️ \'; }\n.nav-file-title-content[data-link-data-href="Research"]::before { content: \'🖥️ \'; }\n.nav-file-title-content[data-link-data-href="ZK Processing"]::before { content: \'🖥️ \'; }\n.nav-file-title-content[data-link-data-href="Top of Mind"]::before { content: \'🧠️ \'; }\n.nav-file-title-content[data-link-data-href="Patrons"]::before { content: \'🧡️ \'; }\n.nav-file-title-content[data-link-data-href="Tools"]::before { content: \'🛠️ \'; }\n.nav-file-title-content[data-link-data-href="Workbench"]::before { content: \'✏️ \'; }\n.nav-file-title-content[data-link-data-href="HOME"]::before { content: \'🌎️ \'; }\n.nav-file-title-content[data-link-data-href="2020 Goals"]::before { content: \'🏆️ \'; }\n.nav-file-title-content[data-link-data-href="2021 Goals"]::before { content: \'🏆️ \'; }\n.nav-file-title-content[data-link-data-href="2023 Goals"]::before { content: \'🏆️ \'; }\n.nav-file-title-content[data-link-data-href="Life Philosophy"]::before { content: \'💭️ \'; }\n.nav-file-title-content[data-link-data-href="Good Feels"]::before { content: \'😊️ \'; }\n.nav-file-title-content[data-link-tags*="#📥️/🐦️"]::before { content: \'🐦️ \'; }\n.nav-file-title-content[data-link-tags*="#📥️/📰️"]::before { content: \'️📰️ \'; }\n.nav-file-title-content[data-link-tags*="#📥️/📚️"]::before { content: \'️📚️ \'; }\n.nav-file-title-content[data-link-tags*="#📝️/👥️"]::before { content: \'️👥️ \'; }\n.nav-file-title-content[data-link-tags*="#📥️/📜️"]::before { content: \'️📜️ \'; }\n.nav-file-title-content[data-link-tags*="#📥️/🎧️"]::before { content: \'️🎧️ \'; }\n.nav-file-title-content[data-link-tags*="#📥️/🎥️"]::before { content: \'️🎥️ \'; }\n.nav-file-title-content[data-link-tags*="#📥️/💭️"]::before { content: \'️💭️ \'; }\n.nav-file-title-content[data-link-tags*="#📥️/🔖️"]::before { content: \'️🔖️ \'; }\n\n/* Flat font */\n/* Requires: https://icomoon.io/#icons-icomoon/liga-font */\n/* .nav-folder-children .nav-file-title-content:first-child::before { content: "\\e924  "; font-family: "IcoMoon-Free"; }\n.nav-folder-children .nav-folder-title-content::before { content: "\\e930  "; font-family: "IcoMoon-Free"; } */\n\n\n/** ________ 2.2.3 Top Level Folder Icons -- https://discord.com/channels/686053708261228577/702656734631821413/805318111917113354 */\n/* .nav-folder-title[data-path="+Medium"] .nav-folder-title-content::before { content: "📜️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="+Newsletter"] .nav-folder-title-content::before { content: "📰️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="+YouTube"] .nav-folder-title-content::before { content: "🔴️ "; font-size: 1.3em; } */\n.nav-folder-title[data-path="Journal"] .nav-folder-title-content::before { content: "📅 "; font-size: 1.3em; }\n.nav-folder-title[data-path="otv"] .nav-folder-title-content::before { content: "💖️ "; font-size: 1.3em; }\n/* .nav-folder-title[data-path="Log"] .nav-folder-title-content::before { content: "📅 "; font-size: 1.3em; } */\n.nav-folder-title[data-path="Media"] .nav-folder-title-content::before { content: "🖼️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="Templates"] .nav-folder-title-content::before { content: "⚙️ "; font-size: 1.3em; }\n/* .nav-folder-title[data-path="Utils"] .nav-folder-title-content::before { content: "⚙️ "; font-size: 1.3em; } */\n.nav-folder-title[data-path="Utility"] .nav-folder-title-content::before { content: "🛠️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="Projects"] .nav-folder-title-content::before { content: "📋 "; font-size: 1.3em; }\n/* .nav-folder-title[data-path="CRM"] .nav-folder-title-content::before { content: "📇️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="Emails"] .nav-folder-title-content::before { content: "📧️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="Timeline"] .nav-folder-title-content::before { content: "⏰️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="Locations"] .nav-folder-title-content::before { content: "📍️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="Names"] .nav-folder-title-content::before { content: "🏷️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="People"] .nav-folder-title-content::before { content: "👥️ "; font-size: 1.3em; } */\n.nav-folder-title[data-path="Inbox"] .nav-folder-title-content::before { content: "📥️ "; font-size: 1.3em; }\n/* .nav-folder-title[data-path="Notes"] .nav-folder-title-content::before { content: "📝️ "; font-size: 1.3em; } */\n/* .nav-folder-title[data-path="Maps Of Content"] .nav-folder-title-content::before { content: "🗺️ "; font-size: 1.3em; } */\n.nav-folder-title[data-path="Sterkere"] .nav-folder-title-content::before { content: "💪🏻️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="DevLog"] .nav-folder-title-content::before { content: "🖥️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="Z"] .nav-folder-title-content::before { content: "🧠️ "; font-size: 1.3em; }\n.nav-folder-title[data-path="Readwise"] .nav-folder-title-content::before { content: "🖋️ "; font-size: 1.3em; }\n/** ________ 2.2.4 Outline Relationship lines -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/357 */\n.outline {\n  font-size: 0.8rem;\n  font-weight: 200;\n}\n\n.outline .tree-item {\n  line-height: 1.3;\n}\n\n.outline .tree-item-self {\n  padding-top: 0.2rem;\n  padding-bottom: 0.1rem;\n  padding-left: 0.5rem;\n  padding-right: 0.3rem;\n}\n\n.outline .tree-item-collapse {\n  left: 0.1rem;\n}\n\n.outline .tree-item-inner {\n  position: relative;\n  padding-top: 0.2rem;\n  /* padding-left: 1rem; */\n  padding-left: 1.7em;\n  text-indent: -0.8em;\n  margin-left: 0.2rem;\n  /* font-size: 0.9em; */\n}\n\n.outline .tree-item-children {\n  margin-left: 0.7rem;\n  padding-left: 0.5rem;\n  margin-top: -0.3rem;\n  padding-top: 0.3rem;\n  border-left: 1px solid var(--neutral-aqua, var(--background-modifier-border));\n  border-radius: 4px;\n  transition: all 0.5s ease-in-out;\n}\n\n.outline .tree-item-children:hover {\n  border-left-color: var(--sidebar-marks-hover, var(--background-secondary));\n}\n\n.outline .collapse-icon + .tree-item-inner {\n  font-weight: 400;\n  padding-left: 0.2rem;\n  /* margin-left: 0rem; */\n  /* font-size: 1em; */\n}\n\n.outline .collapse-icon {\n  margin-top: 0.2rem;\n  margin-left: -0.4rem;\n  margin-right: -0.4rem;\n  width: 2rem;\n}\n/** ________ 2.2.5 Image file navigation icon -- https://discord.com/channels/686053708261228577/702656734631821413/866399284437843978 */\n.nav-file-title[data-path$="jpg"] .nav-file-title-content:before { content: "🌄 "; }\n.nav-file-title[data-path$="pdf"] .nav-file-title-content:before { content: "📜️ "; }\n.nav-file-title[data-path$="docx"] .nav-file-title-content:before { content: "✏️ "; }\n.nav-file-title[data-path$="mp4"] .nav-file-title-content:before { content: "🎥️ "; }\n.nav-file-title[data-path$="webm"] .nav-file-title-content:before { content: "🎥️ "; }\n.nav-file-title[data-path$="mkv"] .nav-file-title-content:before { content: "🎥️ "; }\n.nav-file-title[data-path$="png"] .nav-file-title-content:before { content: "🎨 "; }\n.nav-file-title[data-path$="canvas"] .nav-file-title-content:before { content: "🎨 "; }\n.nav-file-title[data-path$="css"] .nav-file-title-content:before { content: "🎨 "; }\n.nav-file-title[data-path$="sty"] .nav-file-title-content:before { content: "⚙️ "; }\n.nav-file-title[data-path$="csv"] .nav-file-title-content:before { content: "📊️ "; }\n.nav-file-title[data-path$="ico"] .nav-file-title-content:before { content: "ℹ️ "; }\n\n/** ____ 2.3 Clutter Free Mode */\n/** ______ 2.3.1 Make subtler folding gutter arrows -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/10 */\n.CodeMirror-foldgutter-folded:after,\n.CodeMirror-foldgutter-open:after {\n  opacity: 0.5;\n  font-size: 60%;\n  color: var(--bright-aqua);\n}\n.CodeMirror-foldgutter-folded:hover:after,\n.CodeMirror-foldgutter-open:hover:after {\n  opacity: 1;\n}\n.CodeMirror-foldgutter-folded:after {\n  content: "\\25BA";\n}\n.CodeMirror-foldgutter-open:after {\n  content: "\\25BC";\n}\n/** ______ 2.3.2 Hide Block Reference ID\'s -- https://discord.com/channels/686053708261228577/716028884885307432/769267134114037871 */\ndiv:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-blockid {\n  visibility: hidden;\n}\n.cm-blockid::first-letter {\n  visibility: visible;\n  font-weight: 800;\n}\n/** ______ 2.3.3 Shortened Url Links -- https://forum.obsidian.md/t/hide-or-truncate-urls-in-editor-using-css/359/3 */\ndiv:not(.CodeMirror-activeline)\n  > .CodeMirror-line\n  .cm-string.cm-url:not(.cm-formatting) {\n  font-size: 0;\n}\ndiv:not(.CodeMirror-activeline)\n  > .CodeMirror-line\n  .cm-string.cm-url:not(.cm-formatting)::after {\n  content: "🔗";\n  font-size: 1rem;\n}\n/** ______ 2.3.4 highlight (==) not visible anymore if not active line -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/221 */\ndiv:not(.CodeMirror-activeline)\n  > .CodeMirror-line\n  .cm-formatting-highlight.cm-highlight {\n  font-size: 1em;\n  color: transparent;\n}\n/** ______ 2.3.5 Make code blocks wrap in preview mode too */\n.theme-dark code[class*="language-"],\n.theme-dark pre[class*="language-"],\n.theme-light code[class*="language-"],\n.theme-light pre[class*="language-"] {\n  word-wrap: break-word !important;\n  white-space: pre-wrap !important;\n}\n/** ________ 2.3.6 Hide search query title and stop highlighting found element -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/307 */\n.markdown-preview-view .internal-query.is-embed .internal-query-header {\n  display: none;\n}\n\n.search-result-file-matched-text {\n  color: inherit;\n  background-color: inherit;\n}\n/** ________ 2.3.7 vertically centre line numbers in large paragraphs -- https://discord.com/channels/686053708261228577/702656734631821413/822257712825237524 */\n/* .CodeMirror-gutter-wrapper { height:100%; }\n.CodeMirror-gutter-elt { top:0; }\n.cm-s-obsidian .CodeMirror-linenumber{ height: 100%; }\n.cm-s-obsidian .CodeMirror-linenumber::before {\n  content: "";\n  height: calc(50% - 1em);\n  display: block;\n} */\n/** ________ 2.3.8 Fix padding of transcluded blocks in lists */\n.markdown-preview-view .markdown-embed-content > .markdown-preview-view {\n  max-height: 800px;\n  padding-left: 25px;\n}\n/** ________ 2.3.9 Custom Highlight Colors based on templater */\n.hltr-red {\n  background-color: var(--bright-red) !important;\n}\n.hltr-orange {\n  background-color: var(--bright-orange) !important;\n}\n.hltr-yellow {\n  background-color: var(--bright-yellow) !important;\n}\n.hltr-aqua {\n  background-color: var(--bright-aqua) !important;\n}\n.hltr-green {\n  background-color: var(--bright-green) !important;\n}\n.hltr-blue {\n  background-color: var(--bright-blue) !important;\n}\n.hltr-purple {\n  background-color: var(--bright-purple) !important;\n}\n.hltr-magenta {\n  background-color: var(--bright-purple) !important;\n}\n.hltr-grey {\n  background-color: var(--gray) !important;\n}\n/** ____ 2.4 Font Formatting */\n/** ______ 2.4.1 Make Mathjax Font Larger */\n.MJX-TEX {\n  font-size: 180%;\n}\n/** ______ 2.4.2 Hyphenation & Justification     https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/25 */\n.cm-s-obsidian,\n.markdown-preview-view {\n  text-align: justify;\n  hyphens: auto;\n}\n/** ______ 2.4.3 Stylish Block Quotes -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/39 */\nblockquote:before {\n  font: 14px/20px italic Times, serif;\n  content: "“";\n  color: var(--faded-purple);\n  font-size: 3em;\n  line-height: 0.1em;\n  vertical-align: -0.4em;\n}\nblockquote p {\n  display: inline;\n}\n/** ______ 2.4.4 General Font Formatting */\nb,\nstrong,\n.cm-s-obsidian .cm-strong {\n  color: var(--bright-red) !important;\n}\ni,\nem,\nspan.cm-em {\n  color: var(--bright-green) !important;\n}\nu {\n  color: var(--bright-purple) !important;\n}\ndel {\n  color: var(--gray);\n}\nsup,\nsub {\n  color: var(--neutral-yellow);\n}\n/** ______ 2.4.5 Stylish Signatures -- https://discord.com/channels/686053708261228577/702656734631821413/784210155923177552 */\n.signature {\n  font-family: Ananda; /* Font that had to be downloaded from dafont.com */\n  text-align: left;\n  padding-left: 0px;\n  padding-top: 10px;\n  color: var(--bright-purple);\n}\n/** ____ 2.5 Graph Formatting */\n/** ______ 2.5.1 Graph View CSS -- https://discordapp.com/channels/686053708261228577/702656734631821413/760488978691784705 */\n.theme-dark .graph-view.color-arrow {\n  color: var(--bright-aqua);\n}\n.theme-dark .graph-view.color-fill-tag {\n  color: var(--bright-yellow);\n}\n.theme-dark .graph-view.color-fill-attachment {\n  color: var(--neutral-blue);\n}\n.theme-dark .graph-view.color-fill-unresolved {\n  color: var(--bright-red);\n}\n.graph-view.color-fill-focused {\n  color: var(--faded-red);\n}\n.graph-view.color-fill {\n  color: var(--light1);\n}\n/* .graph-view.color-line {\n  color: var(--gray);\n}*/\n/** ____ 2.6 Image Manipulation */\n/** ______ 2.6.1 Image Hover Grow -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/29 */\n.markdown-preview-view img {\n  display: block;\n  margin-left: auto;\n  margin-right: auto;\n  width: 50%;\n  transition: transform 0.25s ease;\n}\n/*   margin-top: 20pt;\n  margin-bottom: 20pt; */\n\n.markdown-preview-view img:hover {\n  -webkit-transform: scale(1.8);\n  transform: scale(2);\n}\n/** ____ 2.7 Check Boxes */\n/** ______ 2.7.1 Nicer Round Checkboxes -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/34 */\n/* input[type="checkbox"],\n.cm-formatting-task {\n  -webkit-appearance: none;\n  appearance: none;\n  border-radius: 50%;\n  border: 1px solid var(--text-faint);\n  padding: 0;\n  vertical-align: top;\n}\n.cm-s-obsidian span.cm-formatting-task {\n  color: transparent;\n  width: 1.25em !important;\n  height: 1.25em;\n  display: inline-block;\n}\ninput[type="checkbox"]:focus {\n  outline: 0;\n}\ninput[type="checkbox"]:checked,\n.cm-formatting-task.cm-property {\n  background-color: var(--text-accent-hover);\n  border: 1px solid var(--text-accent-hover);\n  background-position: center;\n  background-size: 70%;\n  background-repeat: no-repeat;\n  background-image: url(\'data:image/svg+xml; utf8, <svg width="12px" height="10px" viewBox="0 0 12 8" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><g stroke="none" stroke-width="1" fill="none" fill-rule="evenodd"><g transform="translate(-4.000000, -6.000000)" fill="%23ffffff"><path d="M8.1043257,14.0367999 L4.52468714,10.5420499 C4.32525014,10.3497722 4.32525014,10.0368095 4.52468714,9.8424863 L5.24777413,9.1439454 C5.44721114,8.95166768 5.77142411,8.95166768 5.97086112,9.1439454 L8.46638057,11.5903727 L14.0291389,6.1442083 C14.2285759,5.95193057 14.5527889,5.95193057 14.7522259,6.1442083 L15.4753129,6.84377194 C15.6747499,7.03604967 15.6747499,7.35003511 15.4753129,7.54129009 L8.82741268,14.0367999 C8.62797568,14.2290777 8.3037627,14.2290777 8.1043257,14.0367999"></path></g></g></svg>\');\n} */\n/** ______ 2.7.2 Animated Check Boxes -- https://github.com/TriDiamond/Obsidian-Obsidianite/blob/82207bed4313ee0e6f0bb1fd59b04129408018f5/obsidian.css#L463 */\n\n/* .contains-task-list .task-list-item .contains-task-list { padding-inline-start: 0px; }\n.contains-task-list .task-list-item {\n  position: relative;\n  vertical-align: middle;\n  box-sizing: border-box;\n  padding-left: 20px;\n}\n.contains-task-list .task-list-item ul.contains-task-list::before { left: -13px !important; border-width: 2px; }\n.contains-task-list .task-list-item input[type="checkbox"] {\n  position: absolute;\n  top: 4px;\n  left: 0px;\n  width: 15px;\n  height: 15px;\n  margin: 0;\n  opacity: 0;\n  z-index: 10;\n}\n.markdown-preview-view .list-collapse-indicator { margin-left: -35px !important; box-sizing: border-box; }\n.contains-task-list .task-list-item::before {\n  content: "";\n  position: absolute;\n  top: 2px;\n  left: 0px;\n  width: 15px;\n  height: 15px;\n  display: inline-flex;\n  justify-content: center;\n  border: 2px solid var(--neutral-blue);\n  margin-right: 15px;\n  border-radius: 10px;\n  transition: all 0.3s;\n  box-sizing: border-box;\n  z-index: 1;\n}\n.contains-task-list .is-checked.task-list-item::before { border: 10px solid var(--neutral-purple); animation: bounce 300ms; }\n.contains-task-list .is-checked.task-list-item::after {\n  content: "";\n  position: absolute;\n  top: 9px;\n  left: 3px;\n  border-right: 3px solid transparent;\n  border-bottom: 3px solid transparent;\n  transform: rotate(45deg);\n  transform-origin: 0% 100%;\n  animation: checked-box 125ms 250ms forwards;\n  z-index: 5;\n}\n.markdown-preview-view ul > li.task-list-item.is-checked {\n  text-decoration: line-through !important; \n  color: var(--gray) !important; \n}\n.markdown-preview-view ul > li.task-list-item.is-checked ul > li:not(.is-checked) { text-decoration: none !important; color: var(--text-normal) !important; }\n@keyframes checked-box {\n  0% {\n    width: 0;\n    height: 0;\n    border-color: #ffffff;\n    transform: translate(0, 0) rotate(45deg);\n  }\n  33% {\n    width: 4px;\n    height: 0;\n    border-color: #ffffff;\n    transform: translate(0, 0) rotate(45deg);\n  }\n  100% {\n    width: 4px;\n    height: 8px;\n    border-color: #ffffff;\n    transform: translate(0, -8px) rotate(45deg);\n  }\n}\n\n@keyframes bounce {\n  0% { border-width: 2px; }\n  33% { border-width: 4px; }\n  100% { border-width: 10px; } \n}*/\n/** ________ 2.7.3 Hide Completed Tasks In Preview -- https://forum.obsidian.md/t/hide-checked-todo-s/14043 */\n/* .markdown-preview-view ul > li.task-list-item.is-checked { display: none; } */\n/** ____ 2.8 Tags */\n/** ______ 2.8.1 Tag Pills -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/72 */\n/* .tag:not(.token) {\n  background-color: var(--faded-blue);\n  border: none;\n  color: white;\n  font-size: 14px;\n  padding: 0px 8px;\n  text-align: center;\n  text-decoration: none;\n  display: inline-block;\n  margin: 0px 0px;\n  cursor: pointer;\n  border-radius: 14px;\n  font-weight: bold;\n}\n.tag:not(.token):hover {\n  color: var(--bright-red) !important;\n  background-color: var(--bright-red);\n}\n.tag[href^="#📥️"] {\n  background-color: var(--light4);\n  color: var(--light4) !important;\n}\n.tag[href^="#🌱️"] {\n  background-color: var(--faded-aqua);\n  color: var(--faded-aqua) !important;\n}\n.tag[href^="#🌞️"] {\n  background-color: var(--faded-aqua);\n  color: var(--faded-aqua) !important;\n}\n.tag[href^="#🌲️"] {\n  background-color: var(--faded-aqua);\n  color: var(--faded-aqua) !important;\n}\n.tag[href^="#✏"] {\n  background-color: var(--faded-blue);\n  color: var(--faded-blue) !important;\n}\n.tag[href^="#✅️"] {\n  background-color: var(--bright-orange);\n  color: var(--bright-orange) !important;\n}\n.tag[href^="#🗺️"] {\n  background-color: var(--bright-yellow);\n  color: var(--bright-yellow) !important;\n}\n.tag[href^="#⚙️"] {\n  background-color: var(--dark3);\n  color: var(--dark3) !important;\n}\n.tag[href^="#❗️"] {\n  background-color: var(--light1);\n  color: var(--light1) !important;\n} */\n/** ________ 2.8.2 Tags to the side of the document -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/327 */\n/* Requires the core setting "Readable Line Length" to be on */\n/* p > a.tag {\n  font-size: 0;\n  width: 0;\n  padding: 0;\n  margin: 0;\n  background: none;\n  text-decoration: none;\n  border: none;\n}\np > a.tag::before {\n  content: \'Ꚛ\';\n  font-size: 16px;\n  color: var(--bright-purple) ;\n}\n\np > a.tag::after {\n  content: attr(href);\n  float: right;\n  min-width: 3ch;\n  max-width: 25%;\n  margin-right: calc(-25% - 1.5em);\n  margin-left: calc(-25% - 1.5em);\n  position: relative;\n  clear: right;\n  white-space: nowrap;\n  text-overflow: ellipsis;\n  overflow: hidden;\n  font-size: 20px;\n}\n\np > a.tag:hover::after {\n  max-width: fit-content !important;\n}  */\n/** ____ 2.9 [[Link]] Modification */\n/** ______ 2.9.1 Bigger Link Hover Popup Preview -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/175 */\n.popover.hover-popover {\n  transform: scale(0.8); /* makes the content smaller */\n  max-height: 800px;\n  min-height: 50px;\n  width: 700px;\n  overflow: overlay; /* new added */\n}\n.popover.hover-popover .markdown-embed {\n  height: 100%;\n}\n.popover.hover-popover.is-loaded\n  .markdown-embed\n  .markdown-embed-content\n  .markdown-preview-view {\n  padding: 10px 10px 10px 16px; /*16px  two pop magin */\n}\n/** ________ 2.9.2 The modal popups from link hovers */\n.popover {\n  border: 2px solid var(--bright-aqua);\n}\n/** ________ 2.9.3 Input Links -- https://discord.com/channels/686053708261228577/707816848615407697/844751423253905458 */\n/* a.internal-link[data-link-type$="video" i]::before {\n  content: "🎥 " attr(data-link-status) " ";\n}\na.internal-link[data-link-type$="article" i]::before {\n  content: "📰️ " attr(data-link-status) " ";\n}\na.internal-link[data-link-type$="book" i]::before {\n  content: "📚 " attr(data-link-status) " ";\n}\na.internal-link[data-link-type$="paper" i]::before {\n  content: "📜️ " attr(data-link-status) " ";\n}\na.internal-link[data-link-type$="podcast" i]::before {\n  content: "🎧️ " attr(data-link-status) " ";\n}\na.internal-link[data-link-type$="tweet" i]::before {\n  content: "🐦️ " attr(data-link-status) " ";\n}\na.internal-link[data-link-type$="thought" i]::before {\n  content: "💭️ " attr(data-link-status) " ";\n}\na.internal-link[data-link-type$="kindle" i]::before {\n  content: "🔖️ " attr(data-link-status) " ";\n} */\n/* a.internal-link[data-link-status]::after{\n  content: " "attr(data-link-status)\n} */\n/** ______ 2.10.1 Calendar Plugin CSS */\n#calendar-container {\n  --color-background-heading: transparent;\n  --color-background-weeknum: transparent;\n  --color-background-weekend: transparent;\n  --color-background-day: transparent;\n  --color-background-day-empty: var(--background-secondary-alt);\n  --color-background-day-active: var(--interactive-accent);\n  --color-background-day-hover: var(--interactive-hover);\n\n  --color-dot: var(--bright-aqua);\n\n  --color-text-weeknum: var(--bright-aqua);\n  --color-text-title: var(--text-normal);\n  --color-text-heading: var(--text-normal);\n  --color-text-day: var(--text-normal);\n  --color-text-today: var(--text-accent);\n  --color-arrow: var(--bright-aqua);\n  --color-button: var(--text-muted);\n}\n#calendar-container > table > tbody > tr > td {\n  padding: 0px !important;\n}\n#calendar-container .year {\n  color: var(--bright-orange);\n\n}\n#calendar-container [data-emoji-tag]::after {\n  content: attr(data-emoji-tag);\n  position: absolute;\n  top: -4px;\n  right: 4px;\n  height: 8px;\n  width: 8px;\n}\n/** ________ 2.10.2 T0DOIST Plugin CSS -- https://github.com/jamiebrynes7/clair-de-lune-obsidian-theme/blob/master/src/modules/extensions/todoist.scss */\n/* Additional Link -- */\n.todoist-refresh-button {\n  margin-right: 32px;\n}\n.todoist-p1 input {\n  --checkbox-border-color: var(--neutral-red);\n  --checkbox-border-color-hover: var(--bright-red);\n  background-color: var(--faded-red);\n}\n.todoist-p2 input {\n  --checkbox-border-color: var(--neutral-yellow);\n  --checkbox-border-color-hover: var(--bright-yellow);\n  background-color: var(--faded-yellow);\n}\n.todoist-p3 input {\n  --checkbox-border-color: var(--neutral-blue);\n  --checkbox-border-color-hover: var(--bright-blue);\n  background-color: var(--faded-blue);\n}\n.todoist-p4 input {\n  --checkbox-border-color: var(--light4);\n  --checkbox-border-color-hover: var(--light1);\n  background-color: var(--gray);\n}\n.task-metadata {\n  font-size: var(--font-todoist-metadata-size);\n  color: var(--bright-aqua);\n}\n.task-metadata > * {\n  display: inline;\n  margin-right: 30px;\n}\n.task-date.task-overdue {\n  color: var(--bright-red);\n}\n.task-labels-icon {\n  color: var(--bright-green);\n}\n.task-labels {\n  color: var(--bright-purple);\n}\n.task-project-icon {\n  color: var(--bright-blue);\n}\n.task-project {\n  color: var(--bright-blue);\n}\n.todoist-project .todoist-project {\n  margin-left: 20px;\n}\n\n.todoist-section {\n  margin-left: 20px;\n}\n\n.todoist-project .todoist-project-title {\n  font-weight: 700;\n  -webkit-margin-after: 0px;\n  margin-block-end: 0px;\n}\n\n.todoist-section .todoist-section-title {\n  font-size: var(--font-todoist-title-size);\n  font-weight: 700;\n  -webkit-margin-after: 0px;\n  margin-block-end: 0px;\n}\n\n.todoist-error {\n  border: 1px solid var(--bright-red);\n  background-color: rgba(255, 0, 0, 0.05);\n  padding: 1em 1em;\n  margin: 1em 0px;\n}\n\n.todoist-error p {\n  margin: 0 0 1em 0;\n  font-weight: 600;\n}\n\n.todoist-error code {\n  background-color: unset !important;\n  padding: unset !important;\n  margin: unset !important;\n} \n/** ________ 2.10.3 DayPlanner Plugin CSS */\n/* .event_item_color1 {\n  background-color: var(--neutral-aqua) !important;\n}\n\n.event_item_color2 {\n  background-color: var(--neutral-blue) !important;\n}\n\n.event_item_color3 {\n  background-color: var(--neutral-green) !important;\n}\n\n.event_item_color4 {\n  background-color: var(--neutral-orange) !important;\n}\n\n.event_item_color5 {\n  background-color: var(--neutral-purple) !important;\n}\n\n.event_item_color6 {\n  background-color: var(--neutral-red) !important;\n}\n\n.event_item_color7 {\n  background-color: var(--neutral-yellow) !important;\n}\n\n.event_item_color8 {\n  background-color: var(--neutral-aqua) !important;\n}\n\n.event_item_color9 {\n  background-color: var(--neutral-blue) !important;\n}\n\n.event_item_color10 {\n  background-color: var(--neutral-green)!important;\n} */\n/** ________ 2.10.4 Folder Note CSS */\n/* .strip-card-view .thumb-color-folder {\n  background-color: var(--faded-purple) !important;\n  color: var(--light1) !important;\n}\n.strip-card-view .thumb-color-note {\n  background-color: var(--faded-red) !important;\n  color: var(--light1) !important;;\n}\n.strip-card-view span {\n  color: var(--faded-green) !important;\n}\n.strip-card-view p {\n  color: var(--gray) !important;\n} */\n/** ____ 2.11 Heading Formatting */\n/** ______ 2.11.1 Heading Under Gradient Line -- https://github.com/TriDiamond/Obsidian-Obsidianite */\n/* .markdown-preview-view h1,\n.markdown-preview-view h2,\n.markdown-preview-view h3,\n.markdown-preview-view h4,\n.markdown-preview-view h5,\n.markdown-preview-view h6 {\n  position: relative;\n}\n.markdown-preview-view h1:after,\n.markdown-preview-view h2:after,\n.markdown-preview-view h3:after,\n.markdown-preview-view h4:after,\n.markdown-preview-view h5:after,\n.markdown-preview-view h6:after {\n  position: absolute;\n  content: \'\';\n  height: 1px;\n  width: 35%;\n  left: 0;\n  bottom: -0.2rem;\n  background-image: linear-gradient(to right, var(--bright-aqua), var(--background-primary)) ;\n  opacity: 1;\n} */\n/** ______ 2.11.2 Emoji Orientation in Andy Mode Headers -- https://discord.com/channels/686053708261228577/702656734631821413/775900471406624768 */\nbody.plugin-sliding-panes-rotate-header .workspace > .mod-root .view-header {\n  text-orientation: sideways;\n}\n/** ________ 2.11.3 Heading Horizontal Lines -- https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/288?u=tallguyjenks */\n/* h1,\nh2,\nh3,\nh4,\nh5,\nh6 {\n  display: flex;\n  width: 100%;\n  align-items: center;\n}\nh1:before,\nh1:after,\nh2:before,\nh2:after,\nh3:before,\nh3:after,\nh4:before,\nh4:after,\nh5:before,\nh5:after,\nh6:before,\nh6:after {\n  content: "";\n  background: var(--bright-aqua);\n  height: 0.1em;\n  margin: 0.2em;\n  flex: 1;\n} */\n/** ____ 2.12 Horizontal Rule Formatting */\n/** ______ 2.12.1 Aesthetic Horizontal Rule -- https://github.com/TriDiamond/Obsidian-Obsidianite */\n\n.markdown-preview-view hr {\n  margin-block-start: 4em;\n  margin-block-end: 4em;\n  border: none;\n  height: 1px;\n  background-image: linear-gradient(\n    to right,\n    var(--background-primary),\n    var(--text-accent),\n    var(--background-primary)\n  );\n}\n\n.markdown-preview-view hr::after {\n  /* content: \'§\'; */\n  content: "ᛟ";\n  display: inline-block;\n  position: absolute;\n  left: 50%;\n  /* transform: translate(-50%, -50%) rotate(60deg); */\n  transform: translate(-50%, -50%) rotate(0deg);\n  transform-origin: 50% 50%;\n  padding: 0.5rem;\n  color: var(--bright-aqua);\n  background-color: var(--background-primary);\n}\n/** ______ 2.13.1 Page Break -- https://gist.github.com/liamcain/81679412643690a7cdd13dff4dc909ce */\n@media print {\n  /* pagebreak before all ## headings */\n  h2 {\n    page-break-before: always;\n  }\n\n  h3,\n  h4 {\n    page-break-after: avoid;\n  }\n\n  pre,\n  blockquote {\n    page-break-inside: avoid;\n  }\n\n  /* use double <hr> (\'---\') to indicate a page break */\n  hr + hr {\n    page-break-before: always;\n    visibility: hidden;\n  }\n\n  :not(hr) + hr {\n    visibility: hidden;\n  }\n\n  :not(hr) + hr + :not(hr):not(h2) {\n    border-top: 1px solid black;\n    padding-top: 2em;\n  }\n}\n/** ______ 2.14.1 Banded Table Rows -- https://discord.com/channels/686053708261228577/702656734631821413/777106171948564500 */\ntable {\n  padding: 0;\n  word-break: initial;\n}\n\ntable tr {\n  border-top: 1px solid #cccccc;\n  margin: 0;\n  padding: 0;\n}\n\ntable tr:nth-child(2n) {\n  background-color: var(--dark1);\n}\n\ntable tr th {\n  font-weight: bold;\n  border: 1px solid #cccccc;\n  text-align: left;\n  margin: 0;\n  padding: 6px 13px;\n}\n\ntable tr td {\n  border: 1px solid #cccccc;\n  text-align: left;\n  margin: 0;\n  padding: 6px 13px;\n}\n\ntable tr th:first-child,\ntable tr td:first-child {\n  margin-top: 0;\n}\n\ntable tr th:last-child,\ntable tr td:last-child {\n  margin-bottom: 0;\n}\n/** ________ 2.14.2 Full Width Tables */\n.markdown-preview-view table {\n  width: 100%;\n}\n#sponsors,\n#patrons {\n  width: 50%;\n}\n/** ________ 2.14.3 Numbered Table Rows-- https://discord.com/channels/686053708261228577/707816848615407697/832558496892846080 */\n.table-view-table {\n  counter-reset: section;\n}\n\n.table-view-table > tbody > tr > td:first-child::before {\n  counter-increment: section;\n  content: counter(section) ". ";\n}\n/** ____ 2.15 Custom HTML Elements */\n/** ______ 2.15.1 aside format -- https://discord.com/channels/686053708261228577/707816848615407697/784964375806083124 */\naside {\n  width: 40%;\n  padding-left: 0.5rem;\n  margin-left: 1rem;\n  margin-top: 0.5rem;\n  float: right;\n  box-shadow: inset 5px 0 5px -5px var(--faded-blue);\n  font-style: italic;\n  color: var(--faded-blue);\n}\n\naside > p {\n  margin: 0.5rem;\n}\n/** ______ 2.15.2 Buttons -- https://discord.com/channels/686053708261228577/744933215063638183/784289179328708648 */\n.date_button_today {\n  background-color: var(--neutral-aqua);\n  font-weight: bold;\n  margin-right: 0%;\n}\n.date_button_today:hover {\n  background-color: var(--faded-aqua);\n}\n.date_button {\n  background-color: var(--dark1);\n}\n.date_button:hover {\n  background-color: var(--dark3);\n}\n/** ________ 2.15.3 Definition Lists */\ndt {\n  color: var(--neutral-yellow);\n  font-weight: bold;\n}\ndd {\n  color: var(--faded-yellow);\n  font-style: italic;\n}\ndd::before {\n  content: "├── ";\n  margin-left: -1.5em;\n  color: var(--neutral-orange);\n  font-style: normal;\n}\ndd:last-child::before {\n  content: "└── ";\n  margin-left: -1.5em;\n  color: var(--neutral-orange);\n  font-style: normal;\n}\n/** ________ 2.15.4 Code Language Fences -- https://discord.com/channels/686053708261228577/702656734631821413/822915125522202654 */\n\n/* Informational Code Fences */\n.theme-dark /*replace with dark if needed*/ div pre.language-info {\n  /*replace info with anything you like*/\n  background-color: var(\n    --background-primary\n  ); /*you can replace with any colour you want here*/\n  border-left: 1em solid var(--neutral-blue); /*replace this colour with anything you like*/\n  padding-top: 0;\n}\n\npre.language-info::before {\n  /*replace info with anything you like*/\n  margin-bottom: 0.9em;\n  margin-left: -1em; /*based on default padding of obsidian, you may need to adjust depending on the theme you use*/\n  margin-right: -1em;\n  position: static;\n  display: block;\n  background-color: var(\n    --background-secondary\n  ); /*replace this colour with anything you like*/\n  content: "  ℹ️ Info"; /*replace this content with anything you like*/\n}\n\n/* JavaScript */\n.theme-dark /*replace with dark if needed*/ div pre.language-javascript {\n  /*replace info with anything you like*/\n  background-color: var(\n    --background-primary\n  ); /*you can replace with any colour you want here*/\n  padding-top: 0;\n}\n\npre.language-javascript::before {\n  /*replace info with anything you like*/\n  margin-bottom: 0.9em;\n  margin-left: -1em; /*based on default padding of obsidian, you may need to adjust depending on the theme you use*/\n  margin-right: -1em;\n  position: static;\n  display: block;\n  background-color: var(\n    --neutral-yellow\n  ); /*replace this colour with anything you like*/\n  content: "    JavaScript"; /*replace this content with anything you like*/\n  color: var(--background-secondary);\n  font-weight: bold;\n}\n\n/* HTML */\n.theme-dark /*replace with dark if needed*/ div pre.language-html {\n  /*replace info with anything you like*/\n  background-color: var(\n    --background-primary\n  ); /*you can replace with any colour you want here*/\n  padding-top: 0;\n}\n\npre.language-html::before {\n  /*replace info with anything you like*/\n  margin-bottom: 0.9em;\n  margin-left: -1em; /*based on default padding of obsidian, you may need to adjust depending on the theme you use*/\n  margin-right: -1em;\n  position: static;\n  display: block;\n  background-color: var(\n    --neutral-orange\n  ); /*replace this colour with anything you like*/\n  content: "    HTML"; /*replace this content with anything you like*/\n  color: var(--background-secondary);\n  font-weight: bold;\n}\n\n/* CSS */\n.theme-dark /*replace with dark if needed*/ div pre.language-css {\n  /*replace info with anything you like*/\n  background-color: var(\n    --background-primary\n  ); /*you can replace with any colour you want here*/\n  padding-top: 0;\n}\n\npre.language-css::before {\n  /*replace info with anything you like*/\n  margin-bottom: 0.9em;\n  margin-left: -3em; /*based on default padding of obsidian, you may need to adjust depending on the theme you use*/\n  margin-right: -1em;\n  position: static;\n  display: block;\n  background-color: var(\n    --neutral-blue\n  ); /*replace this colour with anything you like*/\n  content: "    CSS"; /*replace this content with anything you like*/\n  color: var(--background-secondary);\n  font-weight: bold;\n}\n\n/* Git repurposed for pro/con */\n.theme-dark /*replace with dark if needed*/ div pre.language-git {\n  /*replace info with anything you like*/\n  background-color: var(\n    --background-primary\n  ); /*you can replace with any colour you want here*/\n  padding-top: 0;\n}\n\npre.language-git::before {\n  /*replace info with anything you like*/\n  margin-bottom: 0.9em;\n  margin-left: -1em; /*based on default padding of obsidian, you may need to adjust depending on the theme you use*/\n  margin-right: -1em;\n  position: static;\n  display: block;\n  background-color: var(\n    --faded-green\n  ); /*replace this colour with anything you like*/\n  content: "    Pro / Con"; /*replace this content with anything you like*/\n  color: var(--background-secondary);\n  font-weight: bold;\n}\n/** ________ 2.15.5 Rounded Edges of Inline Code blocks https://discord.com/channels/686053708261228577/702656734631821413/822181163639767081 */\n/* set text and colour of codeblock */\n.cm-s-obsidian\n  span.cm-inline-code:not(.cm-formatting):not(.cm-hmd-indented-code):not(.obsidian-search-match-highlight) {\n  color: inherit;\n  background-color: var(--background-secondary);\n  padding: 2px 4px;\n}\n\n/* give rounded left edge to codeblock formatting*/\nspan.cm-formatting.cm-formatting-code.cm-inline-code {\n  border-radius: 4px 0px 0px 4px;\n  background-color: var(--background-secondary);\n  color: inherit;\n  padding: 2px 4px;\n}\n\n/* give rounded right edge to codeblock formatting */\nspan.cm-inline-code + span.cm-formatting.cm-formatting-code.cm-inline-code {\n  border-radius: 0px 4px 4px 0px;\n}\n/** ____ 2.16 Quick Switcher */\n/** ________ 2.16.1 Fix the quick switcher highligher after background color change */\n.suggestion-item.is-selected {\n  background-color: var(--faded-aqua);\n}\n/** .. 3. Grave Yard */\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/* Change color of internal links https://discordapp.com/channels/686053708261228577/702656734631821413/767572809848848385 */\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n\n/* .cm-s-obsidian span.cm-hmd-internal-link, a.internal-link {\n  color: var(--bright-orange) !important;\n} */\n\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/* Whitespace Characters */ /* https://forum.obsidian.md/t/editors-css-to-show-tabs-trailing-whitespace-and-strict-line-breaks/4234 */\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n\n/* .cm-trailing-space-new-line, .cm-trailing-space-a, .cm-trailing-space-b, .cm-tab{\n  font-size: 0;\n}\n.cm-trailing-space-a::before, .cm-trailing-space-b::before, .cm-trailing-space-new-line::before, .cm-tab::before{\n  content:\'·\';\n  color:var(--dark2);\n  font-size: initial;\n}\n.cm-trailing-space-new-line::before {\n  content:\'↵\';\n}\n.cm-tab::before {\n  content:\'⟶\'\n} */\n\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/* Remove blockquote left margin\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/*\nblockquote {\n    margin-inline-start: 0;\n} */\n\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/* Make Tags and Searched pages have expanded columns --- THIS MESSES WITH ANDY MODE */\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/*body > div > div.horizontal-main-container > div > div.workspace-split.mod-horizontal.mod-right-split > div:nth-child(4) > div.workspace-leaf > div > div > div,\nbody > div > div.horizontal-main-container > div > div.workspace-split.mod-horizontal.mod-left-split > div.workspace-tabs > div.workspace-leaf > div > div.search-result-container.mod-global-search > div\n{\n    column-width:200px;\n}*/\n/* Expand List Column for file search (THIS MESSES WITH ANDY MODE): */\n/*.nav-folder-children\n{\n    column-width:200px;\n}*/\n\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/* Lime Light but only for body text */\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/*.cm-s-obsidian,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-link,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-hmd-internal-link,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-url,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-hmd-escape-backslash,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-inline-code,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > pre.CodeMirror-line.HyperMD-codeblock,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-hashtag,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-builtin,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-hr,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-footref,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line pre.HyperMD-footnote span.cm-hmd-footnote,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-formatting-highlight,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-highlight,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-formatting-list,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-formatting-task,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-quote,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-math,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.hmd-fold-math-placeholder {\n  color: var(--dark2);\n}\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-formatting-highlight,\n.cm-s-obsidian div:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-highlight {\n  background-color: transparent;\n}\n.CodeMirror-activeline {\n  color: var(--light1);\n}*/\n\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/* WYSIWYG Editor Features From: https://discordapp.com/channels/686053708261228577/702656734631821413/749843052385796147 */\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/* inline formatting, link targets and [[ ]] disappears if not active line\ndiv:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-formatting,\ndiv:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-string.cm-url,\ndiv:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-formatting-link\n{ display: none; } */\n/* hide all html tags -- IT IS COMMENTED OUT BY DEFAULT\ndiv:not(.CodeMirror-activeline) > .CodeMirror-line span.cm-tag{ display: none; }*/\n/* optionally header hashes  span.cm-formatting-header,\n/* except list markers  span.cm-formatting-list,\n/* code block backticks span.cm-formatting-code-block.cm-hmd-codeblock\n{\n    display: inline !important;\n}*/\n/* and task checkboxes\nspan.cm-formatting-task { display: inline !important; font-family: monospace; }\n*/\n\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/* replace H1-H6 markup in edit mode: https://discordapp.com/channels/686053708261228577/702656734631821413/753842312882159687\n/*--------------------------------------------------------------------------------------------------------------------------------------------*/\n/* .CodeMirror-sizer {\n  margin-left: 48px !important;\n} */\n/*-- reduce left padding --*/\n/* .CodeMirror {\n  height: 100%;\n  direction: ltr;\n  padding: 0 10px;\n} */\n/*-- header color --*/\n/* .cm-header.cm-header-1 {\n  color: var(--text-accent);\n  left: 0px;\n  position: relative;\n} */\n/* .cm-header.cm-header-2 {\n  color: var(--text-accent2);\n  left: 0px;\n  position: relative;\n} */\n/*-- hide # markup--*/\n/* .cm-formatting.cm-formatting-header.cm-formatting-header-1.cm-header.cm-header-1,\n.cm-formatting.cm-formatting-header.cm-formatting-header-2.cm-header.cm-header-2,\n.cm-formatting.cm-formatting-header.cm-formatting-header-3.cm-header.cm-header-3,\n.cm-formatting.cm-formatting-header.cm-formatting-header-4.cm-header.cm-header-4,\n.cm-formatting.cm-formatting-header.cm-formatting-header-5.cm-header.cm-header-5,\n.cm-formatting.cm-formatting-header.cm-formatting-header-6.cm-header.cm-header-6 {\n  font-size: 0px;\n}\n */\n/*-- display H1-h6 in gutter--*/\n/* .cm-formatting.cm-formatting-header.cm-formatting-header-1.cm-header.cm-header-1:before {\n  content: "H1";\n  font-size: 34px;\n  color: var(--text-accent2);\n  left: -49px;\n  top: -50px;\n  position: absolute;\n}\n.cm-formatting.cm-formatting-header.cm-formatting-header-2.cm-header.cm-header-2:before {\n  content: "H2";\n  font-size: 26px;\n  color: var(--text-accent2);\n  left: -43px;\n  top: -35px;\n  position: absolute;\n}\n.cm-formatting.cm-formatting-header.cm-formatting-header-3.cm-header.cm-header-3:before {\n  content: "H3";\n  font-size: 22px;\n  color: var(--text-accent2);\n  left: -36px;\n  top: -6px;\n  position: absolute;\n}\n.cm-formatting.cm-formatting-header.cm-formatting-header-4.cm-header.cm-header-4:before {\n  content: "H4";\n  font-size: 20px;\n  color: var(--text-accent2);\n  left: -36px;\n  top: -6px;\n  position: absolute;\n}\n.cm-formatting.cm-formatting-header.cm-formatting-header-5.cm-header.cm-header-5:before {\n  content: "H5";\n  font-size: 18px;\n  color: var(--text-accent2);\n  left: -36px;\n  top: -6px;\n  position: absolute;\n}\n.cm-formatting.cm-formatting-header.cm-formatting-header-6.cm-header.cm-header-6:before {\n  content: "H6";\n  font-size: 16px;\n  color: var(--text-accent2);\n  left: -36px;\n  top: -4px;\n  position: absolute;\n} */\n\n/*-- is active line, hide H[1-6] in gutter --*/\n/* .CodeMirror-activeline\n  span.cm-formatting.cm-formatting-header.cm-formatting-header-1.cm-header.cm-header-1:before,\n.CodeMirror-activeline\n  span.cm-formatting.cm-formatting-header.cm-formatting-header-2.cm-header.cm-header-2:before,\n.CodeMirror-activeline\n  span.cm-formatting.cm-formatting-header.cm-formatting-header-3.cm-header.cm-header-3:before,\n.CodeMirror-activeline\n  span.cm-formatting.cm-formatting-header.cm-formatting-header-4.cm-header.cm-header-4:before,\n.CodeMirror-activeline\n  span.cm-formatting.cm-formatting-header.cm-formatting-header-5.cm-header.cm-header-5:before,\n.CodeMirror-activeline\n  span.cm-formatting.cm-formatting-header.cm-formatting-header-6.cm-header.cm-header-6:before {\n  font-size: 0px;\n} */\n/*-- is active line, display # markup --*/\n/* .CodeMirror-activeline\n  > pre\n  > span\n  .cm-formatting.cm-formatting-header.cm-formatting-header-1.cm-header.cm-header-1 {\n  font-size: 32px;\n  display: inline;\n}\n.CodeMirror-activeline\n  > pre\n  > span\n  .cm-formatting.cm-formatting-header.cm-formatting-header-2.cm-header.cm-header-2 {\n  font-size: 24px;\n  display: inline;\n}\n.CodeMirror-activeline\n  > pre\n  > span\n  .cm-formatting.cm-formatting-header.cm-formatting-header-3.cm-header.cm-header-3 {\n  font-size: 19px;\n  display: inline;\n}\n.CodeMirror-activeline\n  > pre\n  > span\n  .cm-formatting.cm-formatting-header.cm-formatting-header-4.cm-header.cm-header-4,\n.CodeMirror-activeline\n  > pre\n  > span\n  .cm-formatting.cm-formatting-header.cm-formatting-header-5.cm-header.cm-header-5,\n.CodeMirror-activeline\n  > pre\n  > span\n  .cm-formatting.cm-formatting-header.cm-formatting-header-6.cm-header.cm-header-6 {\n  font-size: 13px;\n  display: inline;\n} */\n\n/*--------------------------------------------------------------------------------------------------------------------------------------------\nNO HIGHLIGHT OR LINK MARKS WYSIWYG https://forum.obsidian.md/t/meta-post-common-css-hacks/1978/175\n--------------------------------------------------------------------------------------------------------------------------------------------*/\n/* div:not(.CodeMirror-activeline)>.CodeMirror-line span.cm-formatting-link:not(.cm-link),\ndiv:not(.CodeMirror-activeline)>.CodeMirror-line span.cm-formatting-highlight {\n    display: none !important;\n} */\n\n/** Folder colors Source: https://gist.github.com/Larandar/e025313d086b75ec1f9a2e6672836883 */\n.nav-folder-title[data-path^=\'Log\'] {\n  background-color: var(--neutral-red);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'Journal\'] {\n  background-color: var(--neutral-red);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'Sterkere\'] {\n  background-color: var(--neutral-red);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'Templates\'] {\n  background-color: var(--neutral-orange);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'DevLog\'] {\n  background-color: var(--neutral-yellow);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'CRM\'] {\n  background-color: var(--neutral-green);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'Inbox\'] {\n  background-color: var(--neutral-aqua);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'Z\'] {\n  background-color: var(--neutral-aqua);\n  color: var(--background-primary);\n}\n.nav-folder.mod-root\n    > .nav-folder-children\n    > .nav-folder\n    > .nav-folder-title[data-path^=\'People\']\n/* .nav-folder.mod-root\n    > .nav-folder-children\n    > .nav-folder\n    > .nav-folder-title[data-path^=\'readwise\']\n    + .nav-folder-children  */ {\n  background-color: var(--neutral-blue);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'Media\'] {\n  background-color: var(--neutral-blue);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'Notes\'] {\n  background-color: var(--neutral-purple);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'Readwise\'] {\n  background-color: var(--neutral-purple);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'Utility\'] {\n  background-color: var(--gray);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'Projects\'] {\n  background-color: var(--light1);\n  color: var(--background-primary);\n}\n.nav-folder-title[data-path^=\'otv\'] {\n  background-color: var(--bright-purple);\n  color: var(--background-primary);\n}\n\n/** outliner bullet lines fade to color in edit mode -- https://discord.com/channels/686053708261228577/702656734631821413/884586663064535141 */\n/* .outliner-plugin-bls .cm-hmd-list-indent .cm-tab {\n  position: relative;\n  letter-spacing: 4px;\n}\n\n.HyperMD-list-line-1 .cm-formatting-list::before {\n  color: var(--rgb-faded-aqua) !important;\n}\n.cm-hmd-list-indent > span.cm-tab:nth-child(1)::before {\n  border-color: rgba(var(--rgb-faded-aqua), var(--alpha-ad)) !important;\n  box-shadow: 9px -8px 20px 4px rgba(var(--rgb-faded-aqua), var(--alpha-65));\n}\n\n.HyperMD-list-line-2 .cm-formatting-list::before {\n  color: var(--rgb-faded-blue) !important;\n}\n.cm-hmd-list-indent > span.cm-tab:nth-child(2)::before {\n  border-color: rgba(var(--rgb-faded-blue), var(--alpha-ad)) !important;\n  box-shadow: 9px -8px 20px 4px rgba(var(--rgb-faded-blue), var(--alpha-65));\n}\n\n.HyperMD-list-line-3 .cm-formatting-list::before {\n  color: var(--rgb-faded-purple) !important;\n}\n.cm-hmd-list-indent > span.cm-tab:nth-child(3)::before {\n  border-color: rgba(var(--rgb-faded-purple), var(--alpha-ad)) !important;\n  box-shadow: 9px -8px 20px 4px rgba(var(--rgb-faded-purple), var(--alpha-65));\n}\n\n.HyperMD-list-line-4 .cm-formatting-list::before {\n  color: var(--rgb-faded-red) !important;\n}\n.cm-hmd-list-indent > span.cm-tab:nth-child(4)::before {\n  border-color: rgba(var(--rgb-faded-red), var(--alpha-ad)) !important;\n  box-shadow: 9px -8px 20px 4px rgba(var(--rgb-faded-red), var(--alpha-65));\n}\n\n.HyperMD-list-line-5 .cm-formatting-list::before {\n  color: var(--rgb-faded-orange) !important;\n}\n.cm-hmd-list-indent > span.cm-tab:nth-child(5)::before {\n  border-color: rgba(var(--rgb-faded-orange), var(--alpha-ad)) !important;\n  box-shadow: 9px -8px 20px 4px rgba(var(--rgb-faded-orange), var(--alpha-65));\n}\n.HyperMD-list-line-5 .cm-formatting-list::before {\n  color: var(--rgb-faded-yellow) !important;\n}\n.cm-hmd-list-indent > span.cm-tab:nth-child(6)::before {\n  border-color: rgba(var(--rgb-faded-yellow), var(--alpha-ad)) !important;\n  box-shadow: 9px -8px 20px 4px rgba(var(--rgb-faded-yellow), var(--alpha-65));\n}\n.HyperMD-list-line-5 .cm-formatting-list::before {\n  color: var(--rgb-faded-green) !important;\n}\n.cm-hmd-list-indent > span.cm-tab:nth-child(7)::before {\n  border-color: rgba(var(--rgb-faded-green), var(--alpha-ad)) !important;\n  box-shadow: 9px -8px 20px 4px rgba(var(--rgb-faded-green), var(--alpha-65));\n} */\n\n/** Alternative File Tree Styling */\n\n.oz-folder-toggle > g > path {\n  fill: var(--neutral-aqua);\n}\ndiv.oz-folder-contents {\n  border-left: 1px solid var(--faded-aqua);\n}\n\n/** Block reference counter plugin styling */\n.block-ref-count {\n  /* border: var(--dark2) solid 2px; */\n  border: var(--neutral-aqua) solid 2px;\n  color: var(--neutral-aqua) !important;\n  font-weight: bold;\n  /* color: var(--interactive-accent) !important; */\n  background-color: var(--dark0-hard) !important;\n}\n.block-ref-count:hover {\n  color: var(--interactive-accent) !important;\n}\n/** TODO THIS for code syntax highlighting */\n/* {\n"CodeMirror Options@@cm-background@@dark": "#282a36",\n"CodeMirror Options@@cm-foreground@@dark": "#f8f8f2",\n"CodeMirror Options@@cm-comment@@dark": "#6272a4",\n"CodeMirror Options@@cm-string@@dark": "#f1fa8c",\n"CodeMirror Options@@cm-string-2@@dark": "#f1fa8c",\n"CodeMirror Options@@cm-number@@dark": "#bd93f9",\n"CodeMirror Options@@cm-variable@@dark": "#50fa7b",\n"CodeMirror Options@@cm-variable-2@@dark": "#ffffff",\n"CodeMirror Options@@cm-def@@dark": "#50fa7b",\n"CodeMirror Options@@cm-operator@@dark": "#ff79c6",\n"CodeMirror Options@@cm-keyword@@dark": "#ff79c6",\n"CodeMirror Options@@cm-atom@@dark": "#bd93f9",\n"CodeMirror Options@@cm-meta@@dark": "#f8f8f2",\n"CodeMirror Options@@cm-tag@@dark": "#ff79c6",\n"CodeMirror Options@@cm-attribute@@dark": "#50fa7b",\n"CodeMirror Options@@cm-qualifier@@dark": "#50fa7b",\n"CodeMirror Options@@cm-property@@dark": "#66d9ef",\n"CodeMirror Options@@cm-builtin@@dark": "#50fa7b",\n"CodeMirror Options@@cm-variable-3@@dark": "#ffb86c",\n"CodeMirror Options@@cm-type@@dark": "#ffb86c",\n"CodeMirror Options@@cm-activeline-background@@dark": "#414458",\n"CodeMirror Options@@cm-matchingbracket@@dark": "#ffffff"\n} */\n\n/** Make stars from Prominant Star Plugin Yellow */\n.lucide-bookmark {\n  color: var(--neutral-blue);\n  fill: var(--neutral-blue);\n}\n.lucide-hash {\n  color: var(--neutral-orange);\n}\n.lucide-search, .lucide-git-fork, .lucide-file {\n  color: var(--light1);\n}\n.lucide-folder-closed {\n  color: var(--neutral-yellow);\n}\n.lucide-clock {\n  color: var(--neutral-aqua);\n}\n.lucide-calendar-check {\n  color: var(--bright-red);\n}\n\n.svg-icon.sidebar-left, .svg-icon.sidebar-right  {\n  color: var(--bright-aqua);\n}\n\n/** Forced Dark Mode -- https://discord.com/channels/686053708261228577/694233507500916796/880493122608586782 */\n/* .theme-dark .workspace-leaf-content[data-type="pdf"] iframe {\n\n  filter: invert(0.883);\n}\n\n.theme-dark .pdf-embed iframe {\n  filter: invert(0.883);\n} */\n\n/* .G {\n\n  position: static;\n  display: block;\n  background-color: var(\n    --faded-aqua\n  ); \n  content: "Pro / Con"; \n\n  color: #ebdbb2;\n  font-weight: bold;\n}\n.O {\n  position: static;\n  display: block;\n  background-color: var(\n    --faded-orange\n  ); \n  content: "Pro / Con"; \n\n  color: #ebdbb2;\n  font-weight: bold;\n} */\n\n/* blockquote.G::before{ content: \'emoji\'; } */\n\n\n/** Meta Data Box -- https://discord.com/channels/686053708261228577/771575014382108672/908238393954172930 */\n/* .frontmatter-container {\n  float: right;\n  position: relative;\n  width: 3rem;\n  height: 2.2rem; \n  overflow: hidden;\n  border: none !important;\n  background-color: transparent;\n}\n\n.frontmatter-container::before {\n  content: "ℹ️";\n  color: rgb(17, 124, 119) ;\n  font-size: 40px;\n}\n\n\n.frontmatter-container:hover::before {\n  font-size: 30px !important;\n  float: right;\n  margin-top: -5px; \n}\n\n.frontmatter-container:hover>.frontmatter-container-header {\n  font-size: 20px;\n  text-decoration: underline;\n  padding-bottom: 10px;\n}\n\n.frontmatter-container:hover {\nmargin-left: 20px;\nmargin-bottom: 10px;\nwidth: 300px;\nheight: unset;\nbackground-color: var(--background-primary);\npadding: 0.6em;\npadding-top: 1.5em;\nz-index: 3;\nborder: 2px gray solid !important;\nborder-radius: 1.5em;} */\n\n\n'}
- theme.css

---

**Assistant** - 2024-07-15 01:45:45 UTC

 Certainly! Let's examine the font-related information in this CSS theme. Here are the key points about fonts and how they display:

1. Default font settings:
```css
html, body {
  font-size: 16px !important;
  font-family: var(--font-monospace);
}
```
This sets the base font size to 16px and uses a monospace font defined by the `--font-monospace` variable.

2. Monospace font definition:
```css
.theme-dark {
  --font-monospace: "fira code", "Hack Nerd Font", "Source Code Pro", monospace;
}
```
This defines the monospace font stack for the dark theme. It will try to use Fira Code first, then Hack Nerd Font, then Source Code Pro, and finally any default monospace font.

3. Custom font for headings:
```css
--custom-font: "Norse";
```
There's a custom font called "Norse" defined, which is mentioned to be from dafont.com. This is used for headings.

4. Heading font sizes:
```css
--custom-H1-font-size: 38px;
--custom-H2-font-size: 34px;
--custom-H3-font-size: 30px;
--custom-H4-font-size: 26px;
--custom-H5-font-size: 22px;
--custom-H6-font-size: 18px;
```
These define custom sizes for each heading level.

5. Heading font application:
```css
.cm-header-1, .markdown-preview-section h1 {
  font-weight: 500 !important;
  font-size: var(--custom-H1-font-size) !important;
  color: var(--text-title-h1) !important;
  font-family: var(--custom-font) !important;
}
```
This pattern is repeated for h1 through h6, applying the custom Norse font and the custom sizes to headings.

6. Code block fonts:
```css
.CodeMirror-code, .CodeMirror-linenumber, .cm-formatting {
  font-family: var(--font-monospace) !important;
  font-size: 0.9em;
}
```
This applies the monospace font to code blocks and sets their size to 90% of the base font size.

7. Inline code font:
```css
.markdown-preview-section pre code, .markdown-preview-section code {
  font-size: 0.9em !important;
}
```
This sets inline code to also be 90% of the base font size.

8. Math font sizing:
```css
.MJX-TEX {
  font-size: 180%;
}
```
This makes math equations (rendered by MathJax) 80% larger than the base font size.

These settings create a cohesive typography system with monospace fonts for code and body text, a custom decorative font (Norse) for headings, and consistent sizing across different elements. The theme puts an emphasis on code readability with its choice of monospace fonts and slightly reduced size for code blocks.

Would you like me to explain any of these aspects in more detail?

---

**Human** - 2024-07-15 01:49:05 UTC

1) this effectively makes everything look like code. correct?

---

**Assistant** - 2024-07-15 01:49:05 UTC

 You're absolutely correct. The theme's font choices do indeed make everything look very code-like. Here's why:

1. The base font for the entire document is set to a monospace font:

```css
html, body {
  font-family: var(--font-monospace);
}
```

2. The monospace font stack is defined as:

```css
--font-monospace: "fira code", "Hack Nerd Font", "Source Code Pro", monospace;
```

All of these are monospace fonts commonly used for coding. Fira Code and Hack Nerd Font are particularly popular among programmers.

3. This monospace font is applied not just to code blocks, but to the entire body of text.

This design choice gives the entire document a code-like appearance, which can have several effects:

- It creates a consistent, technical look throughout the document.
- It may improve readability for technical content, especially if there's a lot of inline code mixed with regular text.
- It blurs the visual distinction between code and non-code text, which could be intentional if the content is heavily code-focused.

However, it's worth noting that the headings use a different, custom font ("Norse"), which would provide some visual variety and hierarchy to the document structure.

If you want a more traditional look with proportional fonts for body text and monospace only for code, you would need to modify this theme. Would you like suggestions on how to do that?

---

**Assistant** - 2024-07-15 02:06:15 UTC

 Absolutely! I appreciate your interest in learning about CSS, and I'm happy to help guide you through this process. Your idea of defining multiple fonts for different typographic needs is excellent and very common in web design.

Here's how you could modify the CSS to define three font stacks (serif, sans-serif, and monospace) and use them in Obsidian:

1. First, let's define our font stacks in the `:root` or `.theme-dark` section:

```css
:root {
  --font-serif: "Merriweather", "Georgia", "Times New Roman", serif;
  --font-sans-serif: "Open Sans", "Helvetica Neue", Arial, sans-serif;
  --font-monospace: "Fira Code", "Hack Nerd Font", "Source Code Pro", monospace;
}
```

2. Now, let's apply these fonts to different elements:

```css
/* Apply sans-serif to the body text */
body, .markdown-preview-view {
  font-family: var(--font-sans-serif);
}

/* Apply serif to headings */
h1, h2, h3, h4, h5, h6,
.cm-header-1, .cm-header-2, .cm-header-3, .cm-header-4, .cm-header-5, .cm-header-6 {
  font-family: var(--font-serif);
}

/* Keep monospace for code blocks and inline code */
code, .cm-inline-code, .CodeMirror {
  font-family: var(--font-monospace);
}
```

3. To let Obsidian use these interchangeably, you could create CSS classes:

```css
.serif { font-family: var(--font-serif); }
.sans-serif { font-family: var(--font-sans-serif); }
.monospace { font-family: var(--font-monospace); }
```

Then, in your Obsidian markdown, you could use these classes like this:

```markdown
Normal text

<span class="serif">This text will be serif</span>

<span class="sans-serif">This text will be sans-serif</span>

<span class="monospace">This text will be monospace</span>
```

This setup allows you to use different font styles where needed, while maintaining a consistent overall look. You can adjust the fonts in each stack to your preference.

Remember, for the fonts to work, they need to be installed on your system or loaded via a web font service. The fallback fonts (like Georgia, Arial, etc.) are included in case the preferred fonts aren't available.

Would you like me to explain any part of this in more detail?

---

**Human** - 2024-07-15 02:06:15 UTC

i would. is it possible to define say, 3 fonts each (similar to the example, if i'm understanding this correctly.. this is my first time looking at a css much less trying to decipher what its does. haha), for serif, sans serif and monospace and let obsidian use them interchangeably?

---

**Human** - 2024-07-15 02:09:12 UTC

i've replaced the single line, but copy/paste came in a little crooked. 

is there an easy way to pull that indent from all 3 lines? i'm using vs-code in case it's editor specific


Attachments:
- image.png

---

**Assistant** - 2024-07-15 02:09:12 UTC

 Yes, there's an easy way to adjust the indentation for multiple lines in VS Code:

1. Select all the lines you want to adjust (in this case, lines 150-152).
2. Press Shift + Tab to decrease the indentation for all selected lines at once.

Alternatively, you can:

1. Select the lines you want to adjust.
2. Press Ctrl + [ (or Cmd + [ on Mac) to decrease indentation.

If you need to increase indentation instead, you can use Tab or Ctrl + ] (Cmd + ] on Mac).

These shortcuts allow you to quickly adjust indentation for multiple lines without having to manually edit each line individually. It's a common feature in most code editors, including VS Code.

---

**Assistant** - 2024-07-15 02:10:20 UTC

 Great! I'm glad that helped. Now, for the rest of the CSS snippets I provided earlier, you'll want to add them in appropriate places within your CSS file. Let's go through where to add each part:

1. For the body and markdown preview styles:

Add this after the `.theme-dark` block, perhaps around line 157 or so:

```css
body, .markdown-preview-view {
  font-family: var(--font-sans-serif);
}
```

2. For the heading styles:

Add this after the body styles:

```css
h1, h2, h3, h4, h5, h6,
.cm-header-1, .cm-header-2, .cm-header-3, .cm-header-4, .cm-header-5, .cm-header-6 {
  font-family: var(--font-serif);
}
```

3. For the code block and inline code styles:

Add this after the heading styles:

```css
code, .cm-inline-code, .CodeMirror {
  font-family: var(--font-monospace);
}
```

4. For the utility classes:

You can add these anywhere in the file, but it's often good to group utility classes together. You could add them near the end of the file:

```css
.serif { font-family: var(--font-serif); }
.sans-serif { font-family: var(--font-sans-serif); }
.monospace { font-family: var(--font-monospace); }
```

Remember, the exact placement isn't crucial as long as these rules are not overridden by more specific rules later in the file. CSS follows a cascading order, so later rules can override earlier ones if they have the same or higher specificity.

Also, you might want to review the existing font-related rules in the file and modify or remove them if they conflict with your new font setup. For example, you might want to remove or modify any existing rules that set `font-family` for the entire document to a monospace font.

---

**Human** - 2024-07-15 02:10:20 UTC

that was perfect. thanks. now where do i want to add the rest of these snippets?

---

**Human** - 2024-07-15 02:13:13 UTC

i want these outside of the blocks?

---

**Assistant** - 2024-07-15 02:13:13 UTC

 I apologize for the confusion. You're right to question this. Let me clarify:

1. The font variable definitions (--font-serif, --font-sans-serif, --font-monospace) should indeed be inside the .theme-dark block, as you've already placed them. This is correct because they're defining variables specific to the dark theme.

2. However, for the actual application of these fonts and the utility classes, you have two options:

Option 1: Inside the .theme-dark block
If you want these styles to apply only when the dark theme is active, you can place them inside the .theme-dark block. This would look like:

```css
.theme-dark {
  --font-serif: "Merriweather", "Georgia", "Times New Roman", serif;
  --font-sans-serif: "Open Sans", "Helvetica Neue", Arial, sans-serif;
  --font-monospace: "Fira Code", "Hack Nerd Font", "Source Code Pro", monospace;
  
  /* Other existing dark theme styles... */

  body, .markdown-preview-view {
    font-family: var(--font-sans-serif);
  }

  h1, h2, h3, h4, h5, h6,
  .cm-header-1, .cm-header-2, .cm-header-3, .cm-header-4, .cm-header-5, .cm-header-6 {
    font-family: var(--font-serif);
  }

  code, .cm-inline-code, .CodeMirror {
    font-family: var(--font-monospace);
  }

  .serif { font-family: var(--font-serif); }
  .sans-serif { font-family: var(--font-sans-serif); }
  .monospace { font-family: var(--font-monospace); }
}
```

Option 2: Outside the .theme-dark block
If you want these styles to apply regardless of the theme (which is often the case for font styles), you can place them outside and after the .theme-dark block:

```css
.theme-dark {
  --font-serif: "Merriweather", "Georgia", "Times New Roman", serif;
  --font-sans-serif: "Open Sans", "Helvetica Neue", Arial, sans-serif;
  --font-monospace: "Fira Code", "Hack Nerd Font", "Source Code Pro", monospace;
  
  /* Other existing dark theme styles... */
}

/* Font application styles outside the theme block */
body, .markdown-preview-view {
  font-family: var(--font-sans-serif);
}

h1, h2, h3, h4, h5, h6,
.cm-header-1, .cm-header-2, .cm-header-3, .cm-header-4, .cm-header-5, .cm-header-6 {
  font-family: var(--font-serif);
}

code, .cm-inline-code, .CodeMirror {
  font-family: var(--font-monospace);
}

.serif { font-family: var(--font-serif); }
.sans-serif { font-family: var(--font-sans-serif); }
.monospace { font-family: var(--font-monospace); }
```

Option 2 is generally preferred unless you specifically want different font styles for different themes. It ensures consistent font usage across themes and is typically how font styles are applied in CSS.

---

**Human** - 2024-07-15 02:17:51 UTC

this is what my code ended up like. seems to have worked and changed the fonts when i'm in reading mode.

---

**Assistant** - 2024-07-15 02:17:51 UTC

 I'm glad to hear that the changes are working in reading mode! It looks like you've successfully implemented the font changes. Let's review what you've done:

1. You've defined three font stacks inside the `.theme-dark` block:
   - `--font-serif` for serif fonts
   - `--font-sans-serif` for sans-serif fonts
   - `--font-monospace` for monospace fonts

2. Outside the `.theme-dark` block, you've applied these fonts to different elements:
   - Sans-serif font to the body and markdown preview
   - Serif font to headings
   - Monospace font to code elements

3. You've also added utility classes for serif, sans-serif, and monospace fonts.

This setup allows for flexible use of different font styles throughout your Obsidian documents. The fact that it's working in reading mode is a good sign that the CSS is being applied correctly.

A few things to note:

1. These styles will apply to the dark theme only, as they're using variables defined in the `.theme-dark` block.
2. If you want these styles to apply in light mode as well, you might want to define similar variables in a `.theme-light` block.
3. The utility classes (.serif, .sans-serif, .monospace) allow you to manually apply these fonts to specific elements in your markdown files if needed.

If you're happy with how it looks in reading mode, the next step would be to check how it appears in editing mode and make any necessary adjustments. Is there anything specific you'd like to modify or improve further?

---

**Human** - 2024-07-15 02:18:05 UTC

.theme-dark {
  --font-serif: "Merriweather", "Georgia", "Times New Roman", serif;
  --font-sans-serif: "Open Sans", "Helvetica Neue", Arial, sans-serif;
  --font-monospace: "Fira Code", "Hack Nerd Font", "Source Code Pro", monospace;
  --background-primary: var(--dark0);
  --background-primary-alt: var(--dark0);
  --background-secondary: var(--dark0-hard);
  --background-secondary-alt: var(--dark1);
  --text-normal: var(--light0);
  --text-faint: var(--light3);
  --text-title-h1: var(--neutral-red);
  --text-title-h2: var(--neutral-orange);
  --text-title-h3: var(--neutral-yellow);
  --text-title-h4: var(--neutral-green);
  --text-title-h5: var(--neutral-aqua);
  --text-title-h6: var(--neutral-purple);
  --text-link: var(--bright-blue);
  --text-a: var(--bright-orange);
  --text-a-hover: var(--bright-blue);
  --text-mark: var(--neutral-yellow);
  --pre-code: var(--dark1);
  --text-highlight-bg: var(--faded-aqua);
  --interactive-accent: var(--bright-orange);
  --interactive-before: var(--dark4);
  --background-modifier-border: var(--dark2);
  --text-accent: var(--bright-orange);
  --interactive-accent-rgb: var(--bright-orange);
  --inline-code: var(--bright-blue);
  --code-block: var(--bright-blue);
  --vim-cursor: var(--bright-orange);
  --text-selection: rgba(168, 153, 132, 0.5); /* light4 */
}
body, .markdown-preview-view {
  font-family: var(--font-sans-serif);
}
h1, h2, h3, h4, h5, h6,
.cm-header-1, .cm-header-2, .cm-header-3, .cm-header-4, .cm-header-5, .cm-header-6 {
  font-family: var(--font-serif);
}
code, .cm-inline-code, .CodeMirror {
  font-family: var(--font-monospace);
}
.serif { font-family: var(--font-serif); }
.sans-serif { font-family: var(--font-sans-serif); }
.monospace { font-family: var(--font-monospace); }

---

**Assistant** - 2024-07-15 02:18:05 UTC

 Your code looks good! You've successfully implemented the font changes we discussed. Let's break down what you've done:

1. Inside the `.theme-dark` block:
   - You've defined the three font stacks (serif, sans-serif, and monospace).
   - You've kept all the other theme-specific variables intact.

2. Outside the `.theme-dark` block:
   - You've applied the sans-serif font to the body and markdown preview.
   - You've set serif fonts for all heading levels.
   - You've ensured that code elements use the monospace font.
   - You've added utility classes for easy font switching.

This setup should give you a nice, varied typography in your Obsidian vault:

- Regular text will use your sans-serif font (Open Sans, etc.)
- Headings will use your serif font (Merriweather, etc.)
- Code will use your monospace font (Fira Code, etc.)

A few things to consider:

1. These styles will apply in both reading and editing modes, which is generally what you want for consistency.

2. If you want to use these fonts in light mode as well, you might want to add a similar `.theme-light` block with the same font definitions.

3. You can fine-tune the appearance further by adjusting font sizes, line heights, or weights for different elements if needed.

4. The utility classes (.serif, .sans-serif, .monospace) allow you to manually apply these fonts to specific elements in your markdown if desired.

Your implementation looks correct and should work well. Is there anything specific you'd like to adjust or any other aspects of the typography you want to modify?

---

**Human** - 2024-07-15 02:19:18 UTC

now when someone puts together a full css like this, is there any automation? any fill in the blank? or is this all coded from scratch line by line?  or i suppose, build the framework and then fill in the sections/gaps, huh?

---

**Assistant** - 2024-07-15 02:19:18 UTC

 You've hit upon a key aspect of CSS development! Creating a full CSS theme like this typically involves a combination of approaches:

1. Framework or Starting Point:
   Many developers start with a basic framework or boilerplate CSS. For Obsidian themes, there are often community-shared templates or existing themes that serve as a starting point.

2. CSS Preprocessors:
   Tools like Sass or Less allow developers to use variables, mixins, and functions, making it easier to manage large stylesheets. These can automate repetitive tasks and make the CSS more maintainable.

3. CSS Custom Properties (Variables):
   As you've seen in this theme with `--variable-name`, CSS variables allow for easier theming and reduce repetition.

4. Code Generators:
   Some tools can generate CSS based on input parameters, especially for complex features like gradients or animations.

5. Design Systems:
   Larger projects often use design systems that define reusable components and styles, which can be automatically applied across a theme.

6. Manual Coding:
   Despite these tools, a significant portion is often manually coded to achieve specific, custom looks.

7. Iteration and Refinement:
   Themes are usually built incrementally, starting with basic styles and gradually adding more specific rules.

8. Community Sharing:
   In the Obsidian community, users often share snippets or entire themes, which others can then customize.

For a theme like the one you're working with, it was likely developed through a combination of:
- Starting with a basic Obsidian theme structure
- Using CSS variables for easy customization
- Manually coding specific style rules
- Iterative testing and refinement

While there's no full automation for creating a complete, custom theme, these approaches can significantly streamline the process. The "fill in the blanks" approach you mentioned is quite accurate – developers often create a framework and then fill in specific styles as needed.

---

**Assistant** - 2024-07-15 02:21:11 UTC

 Yes, that's correct. The CSS you've added will override the default font settings within Obsidian. Here's how it works:

1. Obsidian Default Settings: Obsidian has its own default font settings that users can adjust in the app's settings.

2. CSS Override: The CSS you've added is more specific and will take precedence over Obsidian's default styles. This is due to the CSS cascade and specificity rules.

3. What Gets Overridden:
   - The body text will use your sans-serif font stack
   - Headings will use your serif font stack
   - Code elements will use your monospace font stack

4. User Interface vs. Note Content: Your CSS changes will affect the appearance of your notes in both reading and editing modes. However, they might not affect all parts of the Obsidian user interface, depending on how the app is structured.

5. Consistency: This override ensures that your font choices are consistently applied across your notes, regardless of Obsidian's default settings.

6. User Settings: If a user tries to change the font in Obsidian's settings, your CSS will still take precedence unless they use a more specific CSS rule or disable your theme.

7. Flexibility: The utility classes (.serif, .sans-serif, .monospace) you've added allow for manual overrides within specific notes if needed.

It's worth noting that while this CSS will override font families, other font-related settings in Obsidian (like font size) might still apply unless you've specifically overridden those as well.

If you want to allow some user customization while still maintaining your theme's look, you might consider using CSS variables for font families and exposing those through a theme settings plugin, if available.

---

**Human** - 2024-07-15 02:21:11 UTC

now, this will override font settings within obsidian, correct?

---

**Human** - 2024-07-15 02:22:21 UTC

and, say i wanted this to work, even if the fonts weren't installed on someone's system..

---

**Assistant** - 2024-07-15 02:22:21 UTC

 Excellent question! To ensure that your chosen fonts work even if they're not installed on someone's system, you can use web fonts. Here's how you can modify your CSS to include web fonts:

1. Use Google Fonts or another web font service:

For this example, let's use Google Fonts. Add this link in the HTML `<head>` section of your document (if possible in Obsidian):

```html
<link href="https://fonts.googleapis.com/css2?family=Merriweather&family=Open+Sans&family=Fira+Code&display=swap" rel="stylesheet">
```

If you can't add this link (which is likely in Obsidian), you can import the fonts directly in your CSS:

2. Add this to the top of your CSS file:

```css
@import url('https://fonts.googleapis.com/css2?family=Merriweather&family=Open+Sans&family=Fira+Code&display=swap');
```

3. Then, update your font definitions:

```css
.theme-dark {
  --font-serif: "Merriweather", Georgia, "Times New Roman", serif;
  --font-sans-serif: "Open Sans", "Helvetica Neue", Arial, sans-serif;
  --font-monospace: "Fira Code", "Source Code Pro", monospace;
  /* ... rest of your dark theme variables ... */
}
```

This approach ensures that:
- "Merriweather" will be used for serif text
- "Open Sans" for sans-serif text
- "Fira Code" for monospace text

These fonts will be downloaded from Google Fonts if they're not available on the user's system. The fallback fonts you've specified will be used if there's any issue loading the web fonts.

Important notes:
1. Using web fonts may slightly increase load time as the fonts need to be downloaded.
2. Make sure you have the right to use these fonts in your project.
3. Some environments might block external resources, so always have good fallback fonts.
4. In Obsidian, the ability to load external resources might depend on the specific setup and security settings.

If you're developing a theme for public use in Obsidian, you might want to check the Obsidian documentation or community guidelines about including external resources like web fonts. Some theme developers include the font files directly in their theme package to avoid external dependencies.

---

**Human** - 2024-07-15 02:24:15 UTC

adding @import to the very top? outside of root?

---

**Assistant** - 2024-07-15 02:24:15 UTC

 Yes, that's correct! The @import statement should be placed at the very top of your CSS file, outside of any selectors or rule sets. Here's how the beginning of your CSS file should look:

```css
@import url('https://fonts.googleapis.com/css2?family=Merriweather&family=Open+Sans&family=Fira+Code&display=swap');

:root {
  /* Your root variables here */
}

.theme-dark {
  --font-serif: "Merriweather", Georgia, "Times New Roman", serif;
  --font-sans-serif: "Open Sans", "Helvetica Neue", Arial, sans-serif;
  --font-monospace: "Fira Code", "Source Code Pro", monospace;
  /* Rest of your dark theme variables */
}

/* Rest of your CSS rules */
```

Placing the @import at the top ensures that:

1. The fonts are loaded before any other styles are applied.
2. The import directive is recognized and processed correctly by the CSS parser.

This approach allows the web fonts to be available for use throughout your entire stylesheet, regardless of where they're applied. It's a standard practice when using CSS imports for web fonts or other external stylesheets.

Remember, while this method works in many web contexts, its effectiveness in Obsidian might depend on the app's specific implementation and security settings. Always test in your target environment to ensure compatibility.

---

**Assistant** - 2024-07-15 02:45:47 UTC

 I see the issue. You're trying to use a column layout with callouts and Todoist plugin content. The syntax you're using is close, but needs a few adjustments. Here's how you can correct it:

1. For column layouts in Obsidian, you typically use the `cssclass` syntax instead of code blocks.
2. Callouts should be properly nested within the columns.
3. The Todoist plugin syntax looks correct.

Here's the corrected version:

```markdown
<div class="row">
<div class="col-md-6">

>[!todoist]- Overdue
>```todoist
>name: My Tasks
>filter: overdue & !today
>sorting:
>- date
>- priority
>groupby: true
>```

</div>
<div class="col-md-6">

>[!todoist]- Today
>```todoist  
>name: My Tasks
>filter: today
>sorting:
>- date
>- priority
>groupby: true
>```

</div>
</div>
```

This structure should create two columns, each containing a callout with a Todoist list inside.

A few things to note:
1. The `row` and `col-md-6` classes are used for creating a two-column layout. This assumes your CSS theme supports these classes (many do, as they're based on common frameworks like Bootstrap).
2. Each column is wrapped in `<div>` tags.
3. There needs to be a blank line before and after the callout syntax within each column for proper Markdown parsing.

If this doesn't work as expected, it might be because:
1. Your theme doesn't support these specific column classes.
2. The Todoist plugin might not render correctly inside callouts or columns.

In such cases, you might need to add custom CSS to your theme or consult the Todoist plugin documentation for any specific layout requirements.

---

**Human** - 2024-07-15 02:45:47 UTC

ok, my current hiccup.. i'm trying to make side by side callouts with the todoist plugin lists inside of each. i'm missing something.. 

````col
>[!todoist]- Overdue
>```todoist
>name: My Tasks
>filter: overdue & !today
>sorting:
>- date
>- priority
>groupby: true
>``` 
```col-md
>[!todoist]- Today
>```todoist  
>name: My Tasks
>filter: today
>sorting:
>- date
>- priority
>groupby: true
>```
```
`````

---

**Human** - 2024-07-15 02:47:54 UTC

well here's the thing. i get the two columns with the code i sent. it show up correctly in editing mode, actually? but in reading mode, when i try to open the lists, the carat for the callout shifts directions, but doesn't display the list.. 

i'll try your suggestion and report back.

---

**Assistant** - 2024-07-15 02:47:54 UTC

 I appreciate you providing that additional context. It's interesting that the columns appear correctly in editing mode but have issues in reading mode. This suggests there might be a interaction between the column layout, callouts, and the Todoist plugin that's not rendering correctly in reading mode.

Let's try a few things:

1. First, try the suggestion I provided to see if it resolves the issue.

2. If that doesn't work, we could try simplifying the structure. Instead of using callouts, let's try just the columns with the Todoist content:

```markdown
<div class="row">
<div class="col-md-6">

## Overdue

```todoist
name: My Tasks
filter: overdue & !today
sorting:
- date
- priority
groupby: true
```

</div>
<div class="col-md-6">

## Today

```todoist
name: My Tasks
filter: today
sorting:
- date
- priority
groupby: true
```

</div>
</div>
```

3. If the issue persists, it might be related to how the Todoist plugin interacts with Obsidian's reading mode. In this case, you might want to:

   - Check if there are any updates available for the Todoist plugin.
   - See if other users have reported similar issues in the Obsidian community forums or the plugin's GitHub issues.
   - Try using the Todoist lists outside of any special formatting (no columns, no callouts) to see if they work correctly on their own.

4. Another option is to use Obsidian's native callouts without the column layout:

```markdown
> [!note]- Overdue
> ```todoist
> name: My Tasks
> filter: overdue & !today
> sorting:
> - date
> - priority
> groupby: true
> ```

> [!note]- Today
> ```todoist
> name: My Tasks
> filter: today
> sorting:
> - date
> - priority
> groupby: true
> ```
```

Please try these options and let me know which one works best, or if you're still encountering issues. This will help us narrow down whether the problem is with the column layout, the callouts, or the Todoist plugin itself.

---

**Human** - 2024-07-15 02:54:45 UTC

mine still gets me the closest to what i'm looking for... i just need to figure out how to get the lists to populate in reading mode.

---

**Assistant** - 2024-07-15 02:54:45 UTC

 I understand. It sounds like you're very close to your desired result, with the main issue being that the Todoist lists aren't populating in reading mode. This suggests that the problem might be related to how the Todoist plugin interacts with Obsidian's reading mode, especially within the context of callouts and columns.

Here are some steps we can try to troubleshoot and potentially resolve this issue:

1. Plugin Settings:
   Check the Todoist plugin settings in Obsidian. There might be an option to force refresh or render in reading mode.

2. CSS Adjustment:
   The issue might be related to how the plugin's content is being rendered within the callout. Try adding this CSS to your theme:

   ```css
   .callout-content .todoist-query {
     display: block !important;
     visibility: visible !important;
   }
   ```

   This CSS attempts to force the Todoist content to display within callouts.

3. JavaScript Console:
   If you can access the developer console in Obsidian (usually possible in the desktop app), check for any error messages when you try to open the lists in reading mode.

4. Delay Loading:
   Sometimes, dynamic content needs a moment to load. You could try adding a small delay:

   ```markdown
   >[!todoist]- Overdue
   ><div class="todoist-delayed">
   >```todoist
   >name: My Tasks
   >filter: overdue & !today
   >sorting:
   >- date
   >- priority
   >groupby: true
   >```
   ></div>
   ```

   Then add this JavaScript to your Obsidian configuration (if possible):

   ```javascript
   document.addEventListener('DOMContentLoaded', (event) => {
     setTimeout(() => {
       document.querySelectorAll('.todoist-delayed').forEach(el => {
         el.classList.remove('todoist-delayed');
       });
     }, 1000);
   });
   ```

5. Plugin GitHub Issues:
   Check the GitHub repository for the Todoist plugin. There might be known issues or workarounds for this specific problem.

6. Obsidian Forum:
   Post your specific setup in the Obsidian forum. Other users might have encountered and solved this issue.

7. Alternative Approach:
   As a last resort, you could consider using an iframe to embed Todoist directly, if the plugin continues to cause issues.

Remember to test each change individually and in reading mode to see its effect. If none of these solutions work, it might be worth reaching out to the plugin developer with your specific use case.

---

**Human** - 2024-07-15 02:56:12 UTC

i think all of our - and ` might be messing with how code is displayed in the conversation even.. ha

---

**Assistant** - 2024-07-15 02:56:12 UTC

 You're absolutely right, and I apologize for not catching that earlier. The Markdown formatting in our conversation can indeed interfere with how code blocks are displayed, especially when we're discussing Markdown syntax itself. Let's try to clarify the code without using backticks or dashes that might be interpreted as Markdown:

Here's a cleaner representation of your original code:

<div class="row">
<div class="col-md-6">

[!todoist] Overdue
(todoist content here)

</div>
<div class="col-md-6">

[!todoist] Today
(todoist content here)

</div>
</div>

This structure should create two columns, each with a Todoist callout. The fact that this displays correctly in edit mode but not in reading mode suggests there might be an issue with how the Todoist plugin renders its content in different Obsidian view modes.

To troubleshoot this:

1. Try removing the callout syntax ([!todoist]) and see if the Todoist content renders correctly in reading mode within the columns.

2. If that works, the issue might be with how callouts interact with the Todoist plugin in reading mode. You could try using a different callout type, like [!note], to see if it's specific to the Todoist callout.

3. If the problem persists, it could be a plugin-specific issue. In this case, checking the plugin's GitHub issues or Obsidian community forums for similar reports would be a good next step.

4. You might also want to try updating the Todoist plugin if an update is available, as this could potentially fix rendering issues in reading mode.

Let me know how these suggestions work out, and we can continue to refine the approach based on what you observe.

---

**Human** - 2024-07-15 03:07:49 UTC

just isnt going to be easy.. 

something i probably should have lead with, while i dont know anything about using them, i do have obsidian columns and multi column markdown addons installed..

---

**Assistant** - 2024-07-15 03:07:49 UTC

 Ah, that's crucial information! Thank you for sharing that. The Obsidian Columns and Multi-column Markdown plugins provide specific syntax for creating column layouts, which can be different from standard HTML or CSS approaches.

Given that you have these plugins, let's try using their syntax. Here's how you might structure your Todoist lists using the Multi-column Markdown plugin:

```
===+ 2 columns
==- Column 1

> [!todoist]- Overdue
> ```todoist
> name: My Tasks
> filter: overdue & !today
> sorting:
> - date
> - priority
> groupby: true
> ```

==- Column 2

> [!todoist]- Today
> ```todoist
> name: My Tasks
> filter: today
> sorting:
> - date
> - priority
> groupby: true
> ```

===
```

For the Obsidian Columns plugin, the syntax might look like this:

```
:::columns
:::: column
> [!todoist]- Overdue
> ```todoist
> name: My Tasks
> filter: overdue & !today
> sorting:
> - date
> - priority
> groupby: true
> ```
::::

:::: column
> [!todoist]- Today
> ```todoist
> name: My Tasks
> filter: today
> sorting:
> - date
> - priority
> groupby: true
> ```
::::
:::
```

Try both of these formats and see which one works better in both edit and reading modes. The interaction between these column plugins and the Todoist plugin might resolve the issue you were having earlier.

If you're still experiencing problems with the Todoist lists not populating in reading mode, it might be an issue specific to how the Todoist plugin renders its content. In that case, you might need to:

1. Check the Todoist plugin settings for any options related to rendering in different view modes.
2. Look for updates to the Todoist plugin.
3. Reach out to the Todoist plugin developer with your specific use case.

Let me know how these new formats work out, and we can continue to troubleshoot from there.

---

**Human** - 2024-07-15 03:14:46 UTC

neither of those got anywhere close.. one moment.

---

**Assistant** - 2024-07-15 03:14:46 UTC

 I apologize that those suggestions didn't work. It seems the interaction between the Todoist plugin and the column plugins is more complex than anticipated. Let's take a step back and try to understand what's working and what isn't.

You mentioned earlier that your original code was closest to what you're looking for. Could you please provide:

1. The exact code you're using that works in edit mode but not in reading mode.
2. A description of what exactly happens in reading mode (e.g., do you see the columns but not the content, or do you not see the columns at all?)
3. Any error messages you might see in the console (if you can access it).

This information will help me understand the specific behavior you're encountering and provide more targeted suggestions. It's possible that we might need to look into how the Todoist plugin interacts with Obsidian's rendering engine in reading mode, rather than focusing solely on the column layout.

---

**Human** - 2024-07-15 05:35:45 UTC

is there a way to add text to obsidian files in read mode? i seem to remember a plugin that sat in the sidebar to add notes

---

**Assistant** - 2024-07-15 05:35:45 UTC

 Yes, there are a few plugins that allow you to add notes or comments to Obsidian files in read mode. Here are a couple of options:

1. Obsidian Comments:
   This plugin allows you to add comments to your notes that are visible in both edit and read modes. Comments appear in a sidebar and can be associated with specific parts of your text.

2. Marginalia:
   This plugin lets you add notes in the margins of your documents. It works in both edit and read modes, allowing you to add context or thoughts without modifying the main text.

3. Annotator:
   While primarily designed for PDF annotation, this plugin can also be used to add annotations to regular Obsidian notes in read mode.

4. Obsidian Footnotes:
   This plugin allows you to add footnotes to your documents, which can be viewed in both edit and read modes.

5. Obsidian Admonition:
   While not specifically for adding notes, this plugin allows you to create custom callouts that can be used to add additional information or comments to your notes.

To use any of these plugins:

1. Open Obsidian Settings
2. Go to "Community Plugins"
3. Browse or search for the plugin name
4. Install and enable the plugin

After installation, each plugin will have its own settings and usage instructions. The exact method for adding notes will depend on which plugin you choose to use.

Remember to check the specific documentation for the plugin you choose, as the functionality and user interface can vary between plugins.

---

