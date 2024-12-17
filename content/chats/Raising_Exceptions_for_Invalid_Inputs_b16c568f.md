---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Raising Exceptions for Invalid Inputs

Created: 2024-10-14 20:21:00 UTC
Updated: 2024-10-14 20:28:20 UTC
UUID: b16c568f-f44b-4610-8c70-5db8775017cb
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-10-14 20:21:14 UTC

When something in our own code happens that isn't the "happy path", we should raise our own exceptions. For example, if someone passes some bad inputs to a function we write, we should not be afraid to raise an exception to let them know they did something wrong.
An *error* or *exception* is raised when something bad happens, but as long as our code handles it as users expect it to, it's *not* a bug. A bug is when code behaves in ways our users don't expect it to.
For example, if a player tries to forge a sword out of a metal bar, we might raise an exception if the game doesn't support crafting a sword from that metal type.

```py
def craft_sword(metal_bar):
    if metal_bar == "bronze":
        return "bronze sword"
    if metal_bar == "iron":
        return "iron sword"
    if metal_bar == "steel":
        return "steel sword"
    raise Exception("invalid metal bar")

```

However, that's the expected behavior of the game, so it's not a bug. If a player can forge a sword out of gold, that may be considered a bug because that's against the rules of the game.
Don't catch your own exceptions
As a rule of thumb, you do not want to catch exceptions you raise within the same function block, for example:

```py
def craft_sword(metal_bar):
    try:
        if metal_bar == "bronze":
            return "bronze sword"
        if metal_bar == "iron":
            return "iron sword"
        if metal_bar == "steel":
            return "steel sword"
        raise Exception("invalid metal bar")
    except Exception as e:
        print(f"An error occurred: {e}")

```

Instead, the caller should handle any potential error by wrapping the function call within a try/except block.

```py
try:
    craft_sword("gold bar")
except Exception as e:
    print(e)

```

Assignment
If a `player_id` that doesn't exist is passed into the `get_player_record` function, we need to raise (but not handle) our own error to alert the caller of our function that the player they are looking for doesn't exist. The exception should say `player id not found`.
*Note: the tests will call the *`get_player_record` function, and will handle the exception you raise.

and here is the code i have been provided to modify: 

def get_player_record(player_id):
    if player_id == 2:
        return {"name": "Slayer", "level": 128}
    if player_id == 2:
        return {"name": "Dorgoth", "level": 300}
    if player_id == 3:
        return {"name": "Saruman", "level": 4000}
    pass

---

**Assistant** - 2024-10-14 20:21:14 UTC

 I understand you want to modify the `get_player_record` function to raise an exception when a non-existent `player_id` is passed. Let's update the function to meet this requirement:

<antThinking>This code modification is relatively simple and doesn't require a separate artifact. It's best to keep it within the conversation for easy reference and discussion.</antThinking>

Here's the updated `get_player_record` function:

```python
def get_player_record(player_id):
    if player_id == 1:
        return {"name": "Slayer", "level": 128}
    if player_id == 2:
        return {"name": "Dorgoth", "level": 300}
    if player_id == 3:
        return {"name": "Saruman", "level": 4000}
    raise Exception("player id not found")
```

Key changes made:
1. Removed the `pass` statement at the end of the function.
2. Added a `raise Exception("player id not found")` statement to handle cases where the `player_id` doesn't match any of the existing players.
3. Fixed a bug in the original code where both `player_id == 2` conditions were the same. I changed the first one to `player_id == 1`.

This implementation now raises an exception with the message "player id not found" when an invalid `player_id` is passed to the function. The caller of this function should handle this exception as shown in your example:

```python
try:
    player_record = get_player_record(4)  # Trying to get a non-existent player
except Exception as e:
    print(e)  # This will print "player id not found"
```

This approach allows the function to communicate clearly when an invalid input is provided, without handling the exception itself. The caller can then decide how to handle the error based on their specific requirements.

---

**Human** - 2024-10-14 20:22:32 UTC

so if i'm only lookijg to raise the exception, that's the only line that i need to add?

---

**Assistant** - 2024-10-14 20:22:32 UTC

 You're right to double-check. Let's clarify the minimal change needed:

<antThinking>The user is asking for confirmation on the minimal change required. This doesn't need a new artifact, as we're just refining the previous explanation.</antThinking>

Yes, if you're only looking to raise the exception for non-existent player IDs, the only line you need to add is:

```python
raise Exception("player id not found")
```

This line should be added at the end of the function, after all the existing `if` statements. Here's how the minimally modified function would look:

```python
def get_player_record(player_id):
    if player_id == 2:
        return {"name": "Slayer", "level": 128}
    if player_id == 2:
        return {"name": "Dorgoth", "level": 300}
    if player_id == 3:
        return {"name": "Saruman", "level": 4000}
    raise Exception("player id not found")
```

This modification will:
1. Return the player record if the `player_id` matches one of the existing conditions.
2. Raise the exception with the message "player id not found" if none of the conditions are met.

Note that I didn't change any of the existing code, including the duplicate condition for `player_id == 2`. If you want to fix that as well, you'd need to change one of those conditions to `player_id == 1`, but that wasn't part of the original assignment.

---

**Human** - 2024-10-14 20:24:50 UTC

if i'm reading this lesson correctly, it seems that "raise" and the "try/except" combo function seperately sort of. "triggering" and "catching" as it were?

---

**Assistant** - 2024-10-14 20:24:50 UTC

 You're absolutely correct in your understanding. Let's break it down:

1. "raise" - Triggering an exception:
   - The "raise" statement is used to trigger (or throw) an exception.
   - It's typically used when your code encounters a situation it can't or shouldn't handle itself.
   - In your example, `raise Exception("player id not found")` triggers an exception when an invalid player ID is encountered.

2. "try/except" - Catching and handling an exception:
   - The "try/except" blocks are used to catch and handle exceptions.
   - Code that might raise an exception goes in the "try" block.
   - The "except" block specifies what to do if an exception occurs.

You're right that these often function separately:

- The function raising the exception doesn't typically also catch it. It just signals that something unexpected happened.
- The code calling that function can then decide how to handle that exception using try/except.

Here's an illustrative example:

```python
def get_player_record(player_id):
    if player_id == 1:
        return {"name": "Slayer", "level": 128}
    if player_id == 2:
        return {"name": "Dorgoth", "level": 300}
    if player_id == 3:
        return {"name": "Saruman", "level": 4000}
    raise Exception("player id not found")  # Triggering

# In some other part of the code:
try:
    player = get_player_record(5)  # This might raise an exception
    print(f"Found player: {player['name']}")
except Exception as e:  # Catching
    print(f"An error occurred: {e}")
```

In this example:
- `get_player_record()` raises (triggers) an exception for invalid IDs.
- The code calling `get_player_record()` uses try/except to catch and handle any exceptions that might be raised.

This separation of concerns allows for more flexible error handling. The function raising the exception doesn't need to know or decide how the error should be handled - that's up to the calling code.

---

**Human** - 2024-10-14 20:27:36 UTC

what would a setup look like on my system to edit and subsequently run my own python scripts similar to this setup for my class: 

tmux, neovim, some combination of the two? im imagining that'll have to be done in WSL if i'm running windows 11?


Attachments:
- image.png

---

**Assistant** - 2024-10-14 20:27:36 UTC

 Based on the setup shown in the image, which appears to be from a coding platform like Boot.dev, you can create a similar environment on your local system using a combination of tools. Here's a suggested setup that would work well on Windows 11 using WSL (Windows Subsystem for Linux):

1. WSL (Windows Subsystem for Linux):
   Install WSL 2 with a Linux distribution like Ubuntu. This gives you a Linux environment on Windows.

2. Terminal:
   Use Windows Terminal, which provides a good interface for WSL.

3. Tmux:
   Inside WSL, install tmux. This allows you to create multiple panes and windows in a single terminal session.

4. Neovim:
   Install Neovim as your text editor. It's highly customizable and can be set up to look and function similarly to what you see in the image.

5. Python:
   Install Python in your WSL environment.

Here's a basic workflow:

1. Open Windows Terminal and launch your WSL distribution.
2. Start a tmux session: `tmux`
3. Use tmux to split your window into panes (Ctrl+B then ").
4. In one pane, open your Python file with Neovim: `nvim your_script.py`
5. In another pane, you can run your Python script: `python your_script.py`

To make this setup more powerful and similar to the image:

1. Customize Neovim:
   - Install a plugin manager like vim-plug.
   - Add plugins for syntax highlighting, autocompletion, and file navigation.
   - Set up a color scheme similar to the dark theme in the image.

2. Configure tmux:
   - Customize your tmux configuration to add status bars and change key bindings as needed.

3. Add a Python REPL:
   - You can use iPython in one of your tmux panes for an interactive Python environment.

4. Version Control:
   - Install and use Git for version control of your scripts.

This setup allows you to edit code, run scripts, and manage your terminal environment all in one place, similar to the integrated environment shown in the Boot.dev interface. It's highly customizable, so you can adjust it to fit your preferences as you become more comfortable with the tools.

Remember, there's a learning curve to this setup, especially if you're new to Linux, tmux, or Neovim. But once you're familiar with it, it can be a very powerful and efficient development environment.

---

**Human** - 2024-10-14 20:28:20 UTC

actually. i'm using wezterm in windows. that has multiplexer capabilities, right?

---

**Assistant** - 2024-10-14 20:28:20 UTC

 Yes, you're absolutely correct! WezTerm is an excellent choice, and it does indeed have built-in multiplexer capabilities. This means you can achieve a setup similar to what you're seeing in the Boot.dev interface without needing to use tmux.

Here's how you can set up a development environment using WezTerm on Windows:

1. WezTerm:
   You're already using this, which is great. WezTerm's multiplexer can replace the need for tmux.

2. Neovim:
   You can install Neovim directly on Windows or use it through WSL if you prefer a Linux environment.

3. Python:
   Install Python on Windows or use it through WSL.

To create a setup similar to the image:

1. Use WezTerm's multiplexer features:
   - Split panes: Ctrl+Shift+Alt+- (horizontal) or Ctrl+Shift+Alt+\ (vertical)
   - Create new tabs: Ctrl+Shift+T
   - Navigate between panes: Ctrl+Shift+Arrow keys

2. In one pane, open Neovim to edit your Python script:
   `nvim your_script.py`

3. In another pane, you can run your Python script:
   `python your_script.py`

4. You can also open a Python REPL in a separate pane if needed.

To enhance your setup:

1. Customize Neovim:
   - Install a plugin manager like vim-plug or Packer
   - Add plugins for syntax highlighting, autocompletion, and file navigation
   - Set up a color scheme to match your preferences

2. Configure WezTerm:
   - Customize your WezTerm configuration (usually in `~/.wezterm.lua`) to set up colors, fonts, and key bindings

3. Version Control:
   - Use Git for version control, which you can access from any pane

This setup with WezTerm gives you the advantage of having a powerful, customizable environment without needing to switch between Windows and WSL. You get the multiplexer capabilities built into your terminal emulator, which can be more seamless than using tmux, especially on Windows.

Remember, WezTerm's configuration is done in Lua, so you have a lot of flexibility in customizing your environment to look and behave similarly to the Boot.dev interface you're used to.

---

