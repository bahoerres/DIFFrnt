---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Removing KDE Icons from Rofi

Created: 2024-11-11 22:49:25 UTC
Updated: 2024-11-11 22:50:03 UTC
UUID: 169f535b-edc4-4f46-8139-c56af54054c6
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-11-11 22:49:32 UTC

help me get these ugly kde icons out of my rofi dmenu

---

**Assistant** - 2024-11-11 22:49:32 UTC

 If KDE icons are showing up in your rofi, they're likely coming from the XDG desktop entries. Let's clean this up with a simple solution.

First, let's check where these .desktop files are coming from:

```bash
find /usr/share/applications ~/.local/share/applications -name "*kde*.desktop"
```

You can either hide them from rofi or remove them if you don't need the KDE applications. To hide them:

1. Create or edit your rofi config:
```bash
mkdir -p ~/.config/rofi
```

2. Add this to `~/.config/rofi/config.rasi`:
```css
configuration {
    show-icons: true;
    drun-match-fields: "name,generic,exec,categories";
    drun-display-format: "{name}";
    drun-categories: "";
    drun-show-actions: false;
}
```

3. For a more aggressive solution, you can move unwanted .desktop files:
```bash
mkdir -p ~/.local/share/applications/hidden
find /usr/share/applications -name "*kde*.desktop" -exec cp {} ~/.local/share/applications/hidden/ \;
for f in ~/.local/share/applications/hidden/*.desktop; do
    basename=$(basename "$f")
    echo -e "[Desktop Entry]\nHidden=true" > ~/.local/share/applications/$basename
done
```

This will create override files that hide the KDE entries. You can test it by restarting rofi. Need any clarification on these steps?

---

**Human** - 2024-11-11 22:50:03 UTC

well, less i usppse that they're kde, more that i want to be able to choose the icon theme for my rofi launcher

---

**Assistant** - 2024-11-11 22:50:03 UTC

 Ah, you want to set a custom icon theme for rofi. This is straightforward with Rofi's icon theme support.

First, check your available icon themes:

```bash
ls /usr/share/icons ~/.local/share/icons
```

Then modify your `~/.config/rofi/config.rasi`:
```css
configuration {
    icon-theme: "Papirus-Dark";  // Replace with your preferred theme
    show-icons: true;
    drun-display-format: "{icon} {name}";
}
```

Common minimal icon themes you might want to try:
- Papirus (clean, modern)
- ePapirus
- Numix
- Breeze
- candy-icons

If you don't have your preferred theme installed:
```bash
paru -S papirus-icon-theme  # Or another theme
```

Test it with:
```bash
rofi -show drun
```

Need the theme names or want to try a specific one?

---

