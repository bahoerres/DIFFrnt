---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Meaning of Regular Expression Patterns in Hyprland Config

Created: 2024-09-07 22:15:24 UTC
Updated: 2024-09-07 22:18:05 UTC
UUID: fcfe7516-03be-4bdc-8572-f8a1cab119bf
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-09-07 22:15:31 UTC

in my hyprland config files, when a windowrule is defined and there's something like ^(kitty)$ what do the brackets and accents mean?

---

**Assistant** - 2024-09-07 22:15:31 UTC

 The `^(kitty)$` pattern in your Hyprland config file is a regular expression (regex) used for matching window titles or classes. Let's break down what each part means:

1. `^`: This symbol represents the start of the line or string.
2. `(`: Opening parenthesis for grouping.
3. `kitty`: The actual text to match (in this case, the application name "kitty").
4. `)`: Closing parenthesis for grouping.
5. `$`: This symbol represents the end of the line or string.

So, `^(kitty)$` means:
- Match a line that starts with "kitty" and ends with "kitty", with nothing before or after it.

The parentheses `()` are used for grouping, which can be useful for more complex patterns or for capturing parts of the match.

This pattern ensures that the rule applies only to windows with the exact title or class "kitty", without any additional characters before or after. It prevents partial matches like "my-kitty-config" or "kitty-terminal".

Would you like me to explain more about regular expressions or how they're used in Hyprland configs?

---

**Human** - 2024-09-07 22:18:05 UTC

for example, 

windowrule = move 100 100, kitty

while producing similar results, is not as precise as 

windowrule = move 100 100, ^(kitty)$

---

**Assistant** - 2024-09-07 22:18:05 UTC

 You're absolutely correct. Let's compare these two windowrule examples to understand why the second one is more precise:

1. `windowrule = move 100 100, kitty`
2. `windowrule = move 100 100, ^(kitty)$`

The first rule:
- Will match any window title or class that contains "kitty" anywhere in its name.
- This could potentially match unintended windows like "my-kitty-config", "kitty-terminal", or even "minikitty".

The second rule with `^(kitty)$`:
- Will only match windows where the title or class is exactly "kitty", nothing more and nothing less.
- It won't match "my-kitty-config", "kitty-terminal", or any other variation.

The increased precision of the second rule helps in several ways:

1. Avoiding conflicts: It prevents the rule from accidentally applying to similarly named applications or windows.

2. Performance: More precise rules can be processed faster, as they reduce the number of potential matches.

3. Predictability: You can be more certain about which windows the rule will affect, leading to a more consistent user experience.

4. Flexibility: If you later add similar applications (e.g., "kitty-alt"), you won't need to modify this rule, as it won't interfere with the new application.

In general, using regular expressions like `^(kitty)$` in your Hyprland config allows for more fine-grained control over your window management rules. It's a good practice to be as specific as possible with your windowrules to avoid unexpected behavior.

---

