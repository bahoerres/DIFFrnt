---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Troubleshooting Rofi screenshot script error

Created: 2024-09-01 00:19:45 UTC
Updated: 2024-09-01 00:19:55 UTC
UUID: 0d6b2246-4777-4438-9303-6d7bd97f9713
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-09-01 00:19:54 UTC

~/.c/r/a/bin ➜ ./screenshot.sh
(process:1746): Helper-WARNING **: 19:12:19.538: Failed to set lock on pidfile: Rofi already running?
(process:1746): Helper-WARNING **: 19:12:19.538: Got error: -1 Socket operation on non-socket

hoping you might be able to help me troubleshoot this.. attached is the script it's calling.


Attachments:
- {'file_name': 'screenshot.sh', 'file_size': 4135, 'file_type': 'application/x-shellscript', 'extracted_content': '#!/usr/bin/env bash\n\n## Author  : Aditya Shakya (adi1090x)\n## Github  : @adi1090x\n#\n## Applets : Screenshot\n\n# Import Current Theme\nsource "$HOME"/.config/rofi/applets/shared/theme.bash\ntheme="$type/$style"\nslurp_select_area="slurp -d -b \'#ebdbb244\' -c \'#323232FF\' -B \'#323232FF\' -F \'JetBrains Mono Nerd Font\' -w \'1\'"\n# Theme Elements\nprompt=\'Screenshot\'\nmesg="DIR: $(xdg-user-dir PICTURES)/Screenshots"\nbackground_image=$(cat "$HOME/.cache/swww/HDMI-A-1")\n\nif [[ "$theme" == *\'type-1\'* ]]; then\n\tlist_col=\'1\'\n\tlist_row=\'5\'\n\twin_width=\'400px\'\nelif [[ "$theme" == *\'type-3\'* ]]; then\n\tlist_col=\'1\'\n\tlist_row=\'5\'\n\twin_width=\'120px\'\nelif [[ "$theme" == *\'type-5\'* ]]; then\n\tlist_col=\'1\'\n\tlist_row=\'5\'\n\twin_width=\'520px\'\nelif [[ ( "$theme" == *\'type-2\'* ) || ( "$theme" == *\'type-4\'* ) ]]; then\n\tlist_col=\'5\'\n\tlist_row=\'1\'\n\twin_width=\'670px\'\nfi\n\n# Options\nlayout=$(echo "${theme}" | grep \'USE_ICON\' | cut -d\'=\' -f2)\nif [[ "$layout" == \'NO\' ]]; then\n\toption_1="\ue9a2 Capture Desktop"\n\toption_2="\ue952 Capture Area"\n\toption_3="\ue988 Capture Window"\n\toption_4="\uea0d Capture in 5s"\n\toption_5="\ue939 Capture in 10s"\nelse\n\toption_1="\ue9a2"\n\toption_2="\ue952"\n\toption_3="\ue988"\n\toption_4="\uea0d"\n\toption_5="\ue939"\nfi\n\n# Rofi CMD\nrofi_cmd() {\n\trofi -theme-str "window {width: $win_width;}" \\\n\t\t-theme-str "listview {columns: $list_col; lines: $list_row;}" \\\n\t\t-theme-str \'textbox-prompt-colon {str: "\uf03e ";}\' \\\n\t\t-theme-str \'inputbar {background-image: url("\'$background_image\'", width);}\' \\\n\t\t-dmenu \\\n\t\t-p "$prompt" \\\n\t\t-mesg "$mesg" \\\n\t\t-markup-rows \\\n\t\t-theme "${theme}"\n}\n\n# Pass variables to rofi dmenu\nrun_rofi() {\n\techo -e "$option_1\\n$option_2\\n$option_3\\n$option_4\\n$option_5" | rofi_cmd\n}\n\n\ndir="$(xdg-user-dir PICTURES)/Screenshots"\nbefore=$(ls "$dir" -1q | wc -l)\nif [[ ! -d "$dir" ]]; then\n\tmkdir -p "$dir"\nfi\n\n# notify and view screenshot\nnotify_view() {\n\tlocal before="$1"\n\tafter=$(ls "$dir" -1q | wc -l)\n\techo "$after"\n\tnotify_cmd_shot=\'dunstify -u low -i gnome-screenshot Rofishot --replace=699\'\n\tif [ "$after" -gt "$before" ]; then\n    ${notify_cmd_shot} "Screenshot Saved."\n\telse\n    ${notify_cmd_shot} "Screenshot Not Saved."\n\tfi\n\t\n}\n\n# Grab window wayland \n\nfunction grab_window() {\n    local monitors=`hyprctl -j monitors`\n    local clients=`hyprctl -j clients | jq -r \'[.[] | select(.workspace.id | contains(\'$(echo $monitors | jq -r \'map(.activeWorkspace.id) | join(",")\')\'))]\'`\n    # Generate boxes for each visible window and send that to slurp\n    # through stdin\n    local boxes="$(echo $clients | jq -r \'.[] | "\\(.at[0]),\\(.at[1]) \\(.size[0])x\\(.size[1]) \\(.title)"\')"\n    slurp -r <<< "$boxes"\n}\n\n# countdown\ncountdown () {\n\tfor sec in $(seq "$1" -1 1); do\n\t\tdunstify -t 1000 --replace=699 "Taking shot in : $sec"\n\t\tsleep 1\n\tdone\n}\n\n# take shots\nshotnow () {\n\tgrim -g "$(slurp -o)" - | swappy -f - && notify_view "$1"\n\t\n}\n\nshot5 () {\n\tcountdown \'5\'\n\tsleep 0.2 && grim -g "$(slurp -d -b \'#ebdbb244\' -c \'#323232FF\' -B \'#323232FF\' -F \'JetBrains Mono Nerd Font\' -w \'1\')" - | convert - -trim +repage - | swappy -f -\n\tnotify_view "$1"\n}\n\nshot10 () {\n\tcountdown \'10\'\n\tsleep 1 && grim -g "$(slurp -d -b \'#ebdbb244\' -c \'#323232FF\' -B \'#323232FF\' -F \'JetBrains Mono Nerd Font\' -w \'1\')" - | convert - -trim +repage - | swappy -f -\n\tnotify_view "$1"\n}\n\nshotwin () {\n\tsleep 0.3 && grim -g "$(grab_window)" - | convert - -trim +repage - | swappy -f -\n\tnotify_view "$1"\n}\n\nshotarea () {\n\tsleep 0.2 && grim -g "$(slurp -d -b \'#ebdbb244\' -c \'#323232FF\' -B \'#323232FF\' -F \'JetBrains Mono Nerd Font\' -w \'1\')" - | convert - -trim +repage - | swappy -f - \n\tnotify_view "$1"\n}\n\n# Execute Command\nrun_cmd() {\n\tif [[ "$1" == \'--opt1\' ]]; then\n\t\tshotnow "$before" \n\telif [[ "$1" == \'--opt2\' ]]; then\n\t\tshotarea "$before"\n\telif [[ "$1" == \'--opt3\' ]]; then\n\t\tshotwin "$before"\n\telif [[ "$1" == \'--opt4\' ]]; then\n\t\tshot5 "$before"\n\telif [[ "$1" == \'--opt5\' ]]; then\n\t\tshot10 "$before"\n\tfi\n}\n\n# Actions\nchosen="$(run_rofi)"\ncase ${chosen} in\n    $option_1)\n\t\trun_cmd --opt1\n        ;;\n    $option_2)\n\t\trun_cmd --opt2\n        ;;\n    $option_3)\n\t\trun_cmd --opt3\n        ;;\n    $option_4)\n\t\trun_cmd --opt4\n        ;;\n    $option_5)\n\t\trun_cmd --opt5\n        ;;\nesac\n\n\n'}
- screenshot.sh

---

**Assistant** - 2024-09-01 00:19:54 UTC

 I'd be happy to help you troubleshoot this issue. Let's analyze the error message and the script to identify potential causes and solutions.

The error message you're seeing suggests that there might be an issue with Rofi already running or a problem with socket operations. Here are a few things we can check and try:

1. Check if Rofi is already running:
   The error message suggests that Rofi might already be running. You can try killing any existing Rofi processes before running the script again.

   Try running this command:
   ```
   pkill rofi
   ```
   Then attempt to run your script again.

2. Check Rofi configuration:
   Make sure your Rofi configuration is correct and doesn't have any syntax errors. The script is using a custom theme and configuration. Verify that the theme file exists and is properly formatted.

3. Verify environment variables:
   The script relies on some environment variables like $HOME and uses xdg-user-dir. Ensure these are set correctly in your environment.

4. Check permissions:
   Ensure that the script has the correct permissions to execute and access the necessary files and directories.

5. Debug the Rofi command:
   You could try running the Rofi command directly to see if it produces the same error. Extract the Rofi command from the script and run it manually.

6. Use strace:
   If the above steps don't help, you can use strace to get more detailed information about what's happening when the script runs:

   ```
   strace -f ./screenshot.sh
   ```

   This will show you system calls and signals, which might provide more insight into where the error is occurring.

7. Check for conflicting processes:
   Make sure there are no other processes interfering with Rofi or the screenshot functionality.

If you've tried these steps and are still experiencing issues, please let me know the results, and we can dig deeper into the problem. It would also be helpful to know your operating system, desktop environment, and Rofi version.

---

