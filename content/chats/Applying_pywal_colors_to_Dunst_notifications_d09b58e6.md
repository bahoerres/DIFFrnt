---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Applying pywal colors to Dunst notifications

Created: 2024-09-11 21:46:28 UTC
Updated: 2024-09-11 21:46:48 UTC
UUID: d09b58e6-6a57-44dc-9528-c51ff07d7a8e
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-09-11 21:46:45 UTC

i'd like to include dunst to the objects that get colors applied to them with this config. other dunst formatting is also provided in a file.


Attachments:
- {'file_name': 'wallpaper.sh', 'file_size': 5595, 'file_type': 'application/x-shellscript', 'extracted_content': '#!/bin/bash\n#                _ _                              \n# __      ____ _| | |_ __   __ _ _ __   ___ _ __  \n# \\ \\ /\\ / / _` | | | \'_ \\ / _` | \'_ \\ / _ \\ \'__| \n#  \\ V  V / (_| | | | |_) | (_| | |_) |  __/ |    \n#   \\_/\\_/ \\__,_|_|_| .__/ \\__,_| .__/ \\___|_|    \n#                   |_|         |_|               \n#  \n# ----------------------------------------------------- \n# Check to use wallpaper cache\n# ----------------------------------------------------- \n\nuse_cache=0\nif [ -f ~/.config/ml4w/settings/wallpaper_cache ] ;then\n    use_cache=1\nfi\n\nif [ "$use_cache" == "1" ] ;then\n    echo ":: Using Wallpaper Cache"\nelse\n    echo ":: Wallpaper Cache disabled"\nfi\n\n# ----------------------------------------------------- \n# Set defaults\n# ----------------------------------------------------- \n\nforce_generate=0\ngenerated_versions="$HOME/.config/ml4w/cache/wallpaper-generated"\ncache_file="$HOME/.config/ml4w/cache/current_wallpaper"\nblurred_wallpaper="$HOME/.config/ml4w/cache/blurred_wallpaper.png"\nsquare_wallpaper="$HOME/.config/ml4w/cache/square_wallpaper.png"\nrasi_file="$HOME/.config/ml4w/cache/current_wallpaper.rasi"\nblur_file="$HOME/.config/ml4w/settings/blur.sh"\ndefault_wallpaper="$HOME/wallpaper/default.jpg"\nwallpaper_effect="$HOME/.config/ml4w/settings/wallpaper-effect.sh"\nblur="50x30"\nblur=$(cat $blur_file)\n\n# Create folder with generated versions of wallpaper if not exists\nif [ ! -d $generated_versions ] ;then\n    mkdir $generated_versions\nfi\n\n# ----------------------------------------------------- \n# Get selected wallpaper\n# ----------------------------------------------------- \n\nif [ -z $1 ] ;then\n    if [ -f $cache_file ] ;then\n        wallpaper=$(cat $cache_file)\n    else\n        wallpaper=$default_wallpaper\n    fi\nelse\n    wallpaper=$1\nfi\nused_wallpaper=$wallpaper\necho ":: Setting wallpaper with original image $wallpaper"\ntmp_wallpaper=$wallpaper\n\n# ----------------------------------------------------- \n# Copy path of current wallpaper to cache file\n# ----------------------------------------------------- \n\nif [ ! -f $cache_file ] ;then\n    touch $cache_file\nfi\necho "$wallpaper" > $cache_file\necho ":: Path of current wallpaper copied to $cache_file"\n\n# ----------------------------------------------------- \n# Get wallpaper filename\n# ----------------------------------------------------- \nwallpaper_filename=$(basename $wallpaper)\necho ":: Wallpaper Filename: $wallpaper_filename"\n\n# ----------------------------------------------------- \n# Wallpaper Effects\n# -----------------------------------------------------\n\nif [ -f $wallpaper_effect ] ;then\n    effect=$(cat $wallpaper_effect)\n    if [ ! "$effect" == "off" ] ;then\n        used_wallpaper=$generated_versions/$effect-$wallpaper_filename\n        if [ -f $generated_versions/$effect-$wallpaper_filename ] && [ "$force_generate" == "0" ] && [ "$use_cache" == "1" ] ;then\n            echo ":: Use cached wallpaper $effect-$wallpaper_filename"\n        else\n            echo ":: Generate new cached wallpaper $effect-$wallpaper_filename with effect $effect"\n            dunstify "Using wallpaper effect $effect..." "with image $wallpaper_filename" -h int:value:10 -h string:x-dunst-stack-tag:wallpaper\n            source $HOME/.config/hypr/effects/wallpaper/$effect\n        fi\n        echo ":: Loading wallpaper $generated_versions/$effect-$wallpaper_filename with effect $effect"\n    else\n        echo ":: Wallpaper effect is set to off"\n    fi\nfi\n\n# ----------------------------------------------------- \n# Execute pywal\n# ----------------------------------------------------- \n\necho ":: Execute pywal with $used_wallpaper"\nwal -q -i $used_wallpaper\nsource "$HOME/.cache/wal/colors.sh"\n\n# ----------------------------------------------------- \n# Write hyprpaper.conf\n# -----------------------------------------------------\n\necho ":: Setting wallpaper with $used_wallpaper"\nkillall -e hyprpaper & \nsleep 1; \nwal_tpl=$(cat $HOME/.config/ml4w/settings/hyprpaper.tpl)\noutput=${wal_tpl//WALLPAPER/$used_wallpaper}\necho "$output" > $HOME/.config/hypr/hyprpaper.conf\nhyprpaper & > /dev/null 2>&1\n\n# ----------------------------------------------------- \n# Reload Waybar\n# -----------------------------------------------------\n~/.config/waybar/launch.sh\n\n# ----------------------------------------------------- \n# Reload AGS\n# -----------------------------------------------------\nkillall ags\nags &\n\n# ----------------------------------------------------- \n# Created blurred wallpaper\n# -----------------------------------------------------\n\necho ":: Generate new cached wallpaper blur-$blur-$wallpaper_filename with blur $blur"\nmagick $used_wallpaper -resize 75% $blurred_wallpaper\necho ":: Resized to 75%"\nif [ ! "$blur" == "0x0" ] ;then\n    magick $blurred_wallpaper -blur $blur $blurred_wallpaper\n    cp $blurred_wallpaper $generated_versions/blur-$blur-$wallpaper_filename.png\n    echo ":: Blurred"\nfi\ncp $generated_versions/blur-$blur-$wallpaper_filename.png $blurred_wallpaper\n\n# ----------------------------------------------------- \n# Create rasi file\n# ----------------------------------------------------- \n\nif [ ! -f $rasi_file ] ;then\n    touch $rasi_file\nfi\necho "* { current-image: url(\\"$blurred_wallpaper\\", height); }" > "$rasi_file"\n\n# ----------------------------------------------------- \n# Created square wallpaper\n# -----------------------------------------------------\n\necho ":: Generate new cached wallpaper square-$wallpaper_filename"\nmagick $tmp_wallpaper -gravity Center -extent 1:1 $square_wallpaper\ncp $square_wallpaper $generated_versions/square-$wallpaper_filename.png\n'}
- {'file_name': 'dunstrc', 'file_size': 2102, 'file_type': '', 'extracted_content': '[global]\nbackground = "{background}"\nforeground = "{foreground}"\nframe_color = "{color7}"\nhighlight = "{color2}"\n\nmonitor = 0\nfollow = mouse\nwidth = (0,600)\nheight = 350\nprogress_bar = true\nprogress_bar_height = 25\nprogress_bar_frame_width = 3\nprogress_bar_min_width = 460\nprogress_bar_max_width = 480\nindicate_hidden = true\nshrink = true\ntransparency = 5\nseparator_height = 5\npadding = 10\nhorizontal_padding = 10\nframe_width = 0\nsort = true\nidle_threshold = 0\nfont = JetBrains Mono Nerd Font 13\nline_height = 2\nmarkup = full\norigin = "top-right"\noffset = "10x10"\nformat = "<b>%s</b>\\n%b"\nalignment = left\nshow_age_threshold = 60\nword_wrap = true\nignore_newline = true\nstack_duplicates = true\nhide_duplicate_count = false\nshow_indicators = true\nicon_position = left\nmax_icon_size = 86\nmin_icon_size = 32\nicon_theme = "Papirus"\nenable_recursive_icon_lookup = true\nsticky_history = true\nhistory_length = 20\nbrowser = firefox\nalways_run_script = true\ntitle = Dunst\nclass = Dunst\ncorner_radius = 10\nicon_corner_radius = 5\nnotification_limit = 5\nmouse_left_click = close_current\nmouse_middle_click = do_action\nmouse_right_click = context_all\nignore_dbusclose = true\nellipsize = middle\n\n[urgency_low]\ntimeout = 2\nbackground = "{background}"\nframe_color = "{color8}"\nforeground = "{foreground}"\n\n[urgency_normal]\ntimeout = 6\nbackground = "{background}"\nframe_color = "{color8}"\nforeground = "{foreground}"\n\n[urgency_critical]\ntimeout = 30\nbackground = "{background}"\nframe_color = "{color8}"\nforeground = "{color1}"\n\n[fullscreen_show_critical]\nmsg_urgency = critical\nfullscreen = pushback\n\n[mpd]\nappname = "mpd"\nsummary = "*"\nset_stack_tag = "mpd"\nformat = "<span size=\'x-large\' font_desc=\'Cooper Hewitt 12\' weight=\'bold\' foreground=\'{color5}\'>%s</span>\\n%b"\n\n[firefox]\nappname = firefox\nnew_icon = firefox-default\n\n[network]\nappname = network\nnew_icon = network\nsummary = "*"\nformat = "<span size=\'x-large\' weight=\'bold\'>%s</span>\\n<span font_desc=\'Cooper Hewitt,Iosevka Nerd Font 12\'>%b</span>"\n\n[NetworkManager Applet]\nappname = "NetworkManager Applet"\nnew_icon = "network-wireless"\n\n# vim:filetype=dosini\n'}
- wallpaper.sh
- dunstrc

---

**Assistant** - 2024-09-11 21:46:45 UTC

 Certainly! To incorporate Dunst into the objects that have colors applied to them, we'll need to modify the `wallpaper.sh` script to update the Dunst configuration with the new colors generated by `pywal`. We'll use the existing Dunst configuration as a template and replace the color values with the ones from `pywal`.

Here's how we can modify the `wallpaper.sh` script to achieve this:

<antThinking>This task involves updating an existing script to include Dunst configuration. It's substantial, self-contained, and likely to be modified or reused. We'll update the existing "wallpaper-script" artifact with the new changes.</antThinking>

<antArtifact identifier="wallpaper-script" type="application/vnd.ant.code" language="bash" title="Updated wallpaper.sh script with Dunst integration">
#!/bin/bash
# ... (previous content remains the same)

# ----------------------------------------------------- 
# Execute pywal
# ----------------------------------------------------- 

echo ":: Execute pywal with $used_wallpaper"
wal -q -i $used_wallpaper
source "$HOME/.cache/wal/colors.sh"

# ----------------------------------------------------- 
# Update Dunst configuration
# -----------------------------------------------------

echo ":: Updating Dunst configuration with new colors"
dunst_config="$HOME/.config/dunst/dunstrc"
dunst_config_template="$HOME/.config/dunst/dunstrc.template"

# Create a copy of the original dunstrc if it doesn't exist
if [ ! -f "$dunst_config_template" ]; then
    cp "$dunst_config" "$dunst_config_template"
fi

# Update colors in Dunst configuration
sed -e "s/{background}/$background/g" \
    -e "s/{foreground}/$foreground/g" \
    -e "s/{color1}/$color1/g" \
    -e "s/{color2}/$color2/g" \
    -e "s/{color5}/$color5/g" \
    -e "s/{color7}/$color7/g" \
    -e "s/{color8}/$color8/g" \
    "$dunst_config_template" > "$dunst_config"

# Restart Dunst to apply new configuration
killall dunst
dunst &

# ----------------------------------------------------- 
# Write hyprpaper.conf
# -----------------------------------------------------

# ... (rest of the script remains the same)
</antArtifact>

Here's a breakdown of the changes made to the `wallpaper.sh` script:

1. We've added a new section called "Update Dunst configuration" after the pywal execution.
2. We define the paths for the Dunst configuration file and a template file.
3. If the template file doesn't exist, we create it by copying the original configuration file. This step ensures we always have a clean template to work from.
4. We use `sed` to replace the color placeholders in the template with the actual colors generated by pywal.
5. The updated configuration is then written to the main Dunst configuration file.
6. Finally, we restart Dunst to apply the new configuration.

To make this work, you'll need to update your Dunst configuration file (`~/.config/dunst/dunstrc`) to use color placeholders. Here's how you can modify it:

<antThinking>The Dunst configuration file is a good candidate for an artifact. It's substantial, self-contained, and likely to be reused or modified. We'll create a new artifact for the updated Dunst configuration.</antThinking>

<antArtifact identifier="dunst-config" type="application/vnd.ant.code" language="ini" title="Updated Dunst configuration with color placeholders">
[global]
background = "{background}"
foreground = "{foreground}"
frame_color = "{color7}"
highlight = "{color2}"

# ... (rest of the global settings remain the same)

[urgency_low]
timeout = 2
background = "{background}"
frame_color = "{color8}"
foreground = "{foreground}"

[urgency_normal]
timeout = 6
background = "{background}"
frame_color = "{color8}"
foreground = "{foreground}"

[urgency_critical]
timeout = 30
background = "{background}"
frame_color = "{color8}"
foreground = "{color1}"

# ... (rest of the configuration remains the same)
</antArtifact>

With these changes, Dunst will now use the colors generated by pywal, ensuring it matches the overall theme of your desktop environment. The script will automatically update the Dunst configuration and restart the Dunst service whenever you change your wallpaper.

To implement this solution:

1. Update your `wallpaper.sh` script with the new content provided in the first artifact.
2. Modify your Dunst configuration file (`~/.config/dunst/dunstrc`) to use the color placeholders as shown in the second artifact.

After making these changes, your Dunst notifications will automatically adapt to the color scheme generated by pywal when you change your wallpaper.

---

