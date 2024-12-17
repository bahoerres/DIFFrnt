---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Creating a System Monitor like btop/bpytop from Scratch

Created: 2024-10-29 00:11:31 UTC
Updated: 2024-10-29 00:14:07 UTC
UUID: 8626201e-334a-459c-afeb-2b7d431a338b
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-10-29 00:12:00 UTC

I've seen the Linux terminal package btop and possibly even bpytop(or something of the like) 

What code would be required to reproduce one of these from scratch? The the one including py actually written using python?

---

**Assistant** - 2024-10-29 00:12:00 UTC

 Let me help you explore creating a system monitor similar to btop/bpytop. You're correct - bpytop (now renamed to btop++) was originally written in Python before being rewritten in C++.

Let's create a simplified version of a system monitor that shows CPU, memory, and process information using Python. This will demonstrate the core concepts while being easier to understand.

<antThinking>This is a good candidate for an artifact as it's a substantial piece of functional code that creates a complete application. It will likely be reused or modified and includes multiple components working together.</antThinking>

```python
<antArtifact identifier="system-monitor" type="application/vnd.ant.code" language="python" title="Simple System Monitor in Python">
import curses
import psutil
import time
from datetime import datetime
import os

class SystemMonitor:
    def __init__(self):
        self.screen = curses.initscr()
        curses.start_color()
        curses.use_default_colors()
        curses.init_pair(1, curses.COLOR_GREEN, -1)
        curses.init_pair(2, curses.COLOR_RED, -1)
        curses.init_pair(3, curses.COLOR_CYAN, -1)
        curses.curs_set(0)
        self.screen.nodelay(1)

    def draw_gauge(self, win, percent, width=50, y=0, x=0):
        filled = int(width * percent / 100)
        win.addstr(y, x, "[")
        win.addstr(y, x + 1, "=" * filled, curses.color_pair(1))
        win.addstr(y, x + filled + 1, " " * (width - filled))
        win.addstr(y, x + width + 1, "]")
        win.addstr(f" {percent:5.1f}%")

    def get_cpu_info(self):
        cpu_percent = psutil.cpu_percent(interval=0.1, percpu=True)
        return cpu_percent

    def get_memory_info(self):
        memory = psutil.virtual_memory()
        swap = psutil.swap_memory()
        return memory, swap

    def get_process_list(self):
        processes = []
        for proc in psutil.process_iter(['pid', 'name', 'cpu_percent', 'memory_percent']):
            try:
                processes.append(proc.info)
            except (psutil.NoSuchProcess, psutil.AccessDenied):
                pass
        return sorted(processes, key=lambda x: x['cpu_percent'], reverse=True)

    def draw_header(self, y, x):
        time_str = datetime.now().strftime("%H:%M:%S")
        uptime = datetime.fromtimestamp(time.time() - psutil.boot_time()).strftime("%H:%M:%S")
        header = f"System Monitor (Time: {time_str} | Uptime: {uptime})"
        self.screen.addstr(y, x, header, curses.color_pair(3) | curses.A_BOLD)

    def run(self):
        try:
            while True:
                self.screen.clear()
                max_y, max_x = self.screen.getmaxyx()

                # Draw header
                self.draw_header(0, 2)

                # Draw CPU usage
                self.screen.addstr(2, 2, "CPU Usage:", curses.A_BOLD)
                cpu_percentages = self.get_cpu_info()
                for i, cpu in enumerate(cpu_percentages):
                    self.screen.addstr(3 + i, 4, f"CPU {i}: ")
                    self.draw_gauge(self.screen, cpu, 40, 3 + i, 12)

                # Draw Memory usage
                memory, swap = self.get_memory_info()
                mem_y = 4 + len(cpu_percentages)
                self.screen.addstr(mem_y, 2, "Memory Usage:", curses.A_BOLD)
                self.screen.addstr(mem_y + 1, 4, "RAM: ")
                self.draw_gauge(self.screen, memory.percent, 40, mem_y + 1, 12)
                self.screen.addstr(mem_y + 2, 4, "Swap: ")
                self.draw_gauge(self.screen, swap.percent, 40, mem_y + 2, 12)

                # Draw Process list
                proc_y = mem_y + 4
                self.screen.addstr(proc_y, 2, "Top Processes:", curses.A_BOLD)
                self.screen.addstr(proc_y + 1, 4, "PID    CPU%    MEM%    Name")
                
                processes = self.get_process_list()[:5]  # Show top 5 processes
                for i, proc in enumerate(processes):
                    self.screen.addstr(proc_y + 2 + i, 4, 
                        f"{proc['pid']:<6} {proc['cpu_percent']:6.1f} {proc['memory_percent']:7.1f}  {proc['name']}")

                self.screen.addstr(max_y-1, 2, "Press 'q' to quit", curses.A_DIM)
                self.screen.refresh()

                # Check for quit
                ch = self.screen.getch()
                if ch == ord('q'):
                    break

                time.sleep(1)

        finally:
            curses.endwin()

if __name__ == "__main__":
    monitor = SystemMonitor()
    monitor.run()
</antArtifact> 
```

This code creates a basic system monitor that includes:
1. CPU usage bars for each core
2. Memory (RAM and Swap) usage bars
3. Top processes sorted by CPU usage
4. System uptime and current time
5. A clean terminal UI using the curses library

To run this code, you'll need to install the required packages:
```bash
pip install psutil
```

Key differences from btop/bpytop:
1. This is much simpler - btop++ includes many more features like:
   - Network monitoring
   - Detailed disk I/O
   - More process information and sorting options
   - Themes and configuration
2. The real btop++ (formerly bpytop) was rewritten in C++ for better performance
3. This version updates every second, while btop++ has more sophisticated update timing

Would you like me to explain any particular part of the code in more detail or add any specific features?

---

**Human** - 2024-10-29 00:14:07 UTC

And btop is written in rust?

---

**Assistant** - 2024-10-29 00:14:07 UTC

 Actually, btop is written in C++, not Rust. The history goes:

1. First there was `bpytop` - written in Python
2. The same developer (Anders Bergh) later rewrote it completely in C++ and renamed it to `btop++`
3. This C++ version is what you typically find now when you install `btop`

You might be thinking of `bottom` (often called `btm` when installed), which is a similar system monitor that IS written in Rust. It's a different project but serves a similar purpose.

The timeline was roughly:
- 2020: `bpytop` released (Python)
- 2021: Rewritten as `btop++` (C++)
- Current: `btop++` is commonly just called `btop`

The switch from Python to C++ was made primarily for performance reasons - while Python is great for prototyping and smaller applications, system monitors benefit significantly from the lower-level control and better performance that C++ provides, especially when dealing with constant system calls and UI updates.

Would you like to see the differences between these tools, or would you be interested in seeing how you might implement a similar tool in Rust?

---

