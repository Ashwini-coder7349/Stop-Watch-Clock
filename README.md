COMANY: MICRO IIT

NAME: ASHWINI NAIK

DOMAIN: PYTHON PROGRAMMING

DURATION:1 MONTH

MENTOR:MR. VIJAY KUMAR

# Stop-Watch-Clock
Here's a detailed explanation of a stopwatch/clock application, along with a Python program to implement it:

# Stopwatch/Clock Application
A stopwatch/clock application is a digital tool that combines the functions of a stopwatch and a clock. It allows users to measure elapsed time with start, stop, and reset features, while also displaying the current time.

# Key Features:
1. Stopwatch functionality: Measure elapsed time with start, stop, and reset features.
2. Clock display: Show current time in hours, minutes, and seconds.
3. Versatile tool: Allow users to time activities and check the current time simultaneously.

# Interface:
- Display hours, minutes, and seconds
- Start, stop, and reset buttons for stopwatch functionality

# Python Program:
Here's a simple implementation of a stopwatch/clock application using Python's Tkinter library:


import tkinter as tk
from threading import Thread
import time

class StopWatch(tk.Frame):
    def __init__(self, master=None):
super().__init__(master)
        self.master = master
        self.pack()
        self.running = False
        self.seconds = 0
        self.display_seconds = "00:00:00"
        self.create_widgets()
        self.update_timer()

    def create_widgets(self):
        self.time_label = tk.Label(self, text=self.display_seconds, font=("Helvetica", 24))
        self.time_label.pack()

        self.start_button = tk.Button(self, text="Start", command=self.start_timer)
        self.start_button.pack(side="left")

        self.stop_button = tk.Button(self, text="Stop", command=self.stop_timer, state="disabled")
        self.stop_button.pack(side="left")

        self.reset_button = tk.Button(self, text="Reset", command=self.reset_timer)
        self.reset_button.pack(side="left")

    def start_timer(self):
        self.running = True
        self.start_button.config(state="disabled")
        self.stop_button.config(state="normal")

    def stop_timer(self):
        self.running = False
        self.start_button.config(state="normal")
        self.stop_button.config(state="disabled")

    def reset_timer(self):
        self.running = False
self.seconds = 0
        self.display_seconds = "00:00:00"
        self.time_label.config(text=self.display_seconds)
        self.start_button.config(state="normal")
        self.stop_button.config(state="disabled")

    def update_timer(self):
        if self.running:
            hours, remainder = divmod(self.seconds, 3600)
            minutes, seconds = divmod(remainder, 60)
            self.display_seconds = "{:02}:{:02}:{:02}".format(int(hours), int(minutes), int(seconds))
            self.time_label.config(text=self.display_seconds)
            self.seconds += 1
        self.master.after(1000, self.update_timer)

def show_time():
    current_time = time.strftime("%H:%M:%S")
    time_label.config(text=current_time)
    root.after(1000, show_time)

root = tk.Tk()
root.title("Stopwatch/Clock")

time_label = tk.Label(root, font=("Helvetica", 24))
time_label.pack()

show_time()

stopwatch = StopWatch(master=root)
stopwatch.mainloop()


# How the Program Works:
1. The program creates a window with a stopwatch display and buttons to start, stop, and reset the stopwatch.
2. The StopWatch class handles the stopwatch functionality, including updating the display and handling button clicks.
3. The show_time function updates the current time display every second.
4. The program uses the after method to schedule the update_timer and show_time functions to run at regular intervals.

# Example Use Cases:
- Run the program and click the "Start" button to begin the stopwatch.
- Click the "Stop" button to pause the stopwatch.
- Click the "Reset" button to reset the stopwatch to zero.
- Observe the current time display at the top of the window.

#OUTPUT:
A window with the title "Stopwatch/Clock" will appear, displaying:

- A digital clock showing the current time in hours, minutes, and seconds.
- A stopwatch display showing "00:00:00".
- Three buttons: "Start", "Stop", and "Reset".

When you click the "Start" button:

- The stopwatch will begin counting up from "00:00:00".
- The "Start" button will become disabled.
- The "Stop" button will become enabled.

When you click the "Stop" button:

- The stopwatch will pause.
- The "Stop" button will become disabled.
- The "Start" button will become enabled.

When you click the "Reset" button:

- The stopwatch will reset to "00:00:00".
- The "Start" button will become enabled.
- The "Stop" button will become disabled.

The digital clock will continue to update every second, showing the current time.

