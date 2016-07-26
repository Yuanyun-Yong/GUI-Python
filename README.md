# GUI-Python
# Demo GUI
"""Introduction to GUIs
Up until now, all of our Python code has been run in the console or shell. It has been text-based, and run by the user inputting text into the program.
A graphical user interface (GUI), on the other hand, is when your program has a window where the user can interact with it. This window contains widgets such as text fields, buttons, drop-down menus and more for the user to click and type in.
We're going to learn how to build a GUI using a module called tkinter, but first let's have a look at one. In the editor is a LOT of code - don't worry, you don't need to understand it all just yet!
Click Run to see the GUI in action.
Read through the comments in the code to see how it is put together.
Find line 15, and change the window title to My Python GUI Demo.
On line 18, change the Labelframe text to say Greeting Program.
On line 49, change the button text to say Greet me!
"""

from tkinter import *
from tkinter import ttk
from tkinter import scrolledtext

# ------------------- FUNCTION CODE ---------------------#

# Greet me function, run when button is clicked and says greeting with name e.g. Hello Bob!
def greet_me():
    greeting_message.set("{} {}".format(greeting.get(), name.get()))


# -------------------- USER INTERFACE CODE --------------#
# Create the main window with title
root = Tk()
root.title("My Python GUI Demo")

# Create an outer label frame - puts a labeled border around its child widgets, can help to organise UI
container = ttk.LabelFrame(root, text="Greeting Program")
container.grid(column=0, row=0)

# ---------------------- GREETING CHOICES --------------#
# Adding a combo box - dropdown with text entry, can disable free text entry (read only)
greeting_box_label = ttk.Label(container, text="Choose/enter a greeting:").grid(column=0, row=0)
greeting = StringVar()

greeting_box = ttk.Combobox(container, textvariable=greeting)
greeting_box['values'] = ["Hello", "Goodbye", "Good Morning", "Good Afternoon", "Good Night"]
greeting_box.grid(column=0, row=1)
greeting_box.current(0)

# -----------------------NAME ENTRY --------------------#
#Adding a Label - Text labels that can go anywhere
name_label = ttk.Label(container, text="Enter a name: ")
name_label.grid(column=1, row=0)

#Adding a textbox entry widget - just a basic 1 line input you can set the width of
#Can assign it a textvariable which it will automatically change to if that variable is changed
name = StringVar()
name_entered = ttk.Entry(container, textvariable=name)
name_entered.grid(column=1, row=1)
name_entered.focus()

# ------------------- GREETING OUTPUT AND BUTTON --------#
# Label to put text into
greeting_message = StringVar()
greeting_label = ttk.Label(container, textvariable=greeting_message).grid(column=2, row=0)

#Adding a Button - just a button, with text, can run a function when clicked
action_button = ttk.Button(container, text="Greet Me!", command=greet_me)
action_button.grid(column=2, row=1)

# Adding checkboxes in different states
use_name = IntVar()
check_box = Checkbutton(container, text="Use my name", variable=use_name, state='disabled')
check_box.select()
check_box.grid(column=0, row=2, sticky=W)

# ------------------- STYLES/PADDING --------------------#
container.grid_configure(padx=10, pady=10)

for child in container.winfo_children():
    child.grid_configure(padx=10, pady=10, sticky=W)

# Up to page 41 with tabbed widgets up next
root.mainloop()

"""
Creating a tkinter window
Ok, so let's start at the beginning now. The first thing we need to do to use tkinter to create a GUI is import the module:
from tkinter import *
This is slightly different to our usual import syntax--click here for an explanation.
We can then use it to create a window by doing the following:
root = Tk()
The variable root can be any name, but root is used most often. To give the window a title, we use the following line:
root.title("Here is a window!")
And to get the window to run we use the mainloop() function, which goes at the end after all of your GUI code:
root.mainloop()
"""
First import tkinter using the new syntax.
Under the relevant comment create a window called root.
Set the title for the window to My GUI App on the next line.
Under the next comment, run the mainloop() function so that your window will appear.
"""
Note about: Importing Modules

So far, when we import modules, we have done it like this: 
import random 

When we do it this way, we then have to use dot notation, or write the name of the module in front, to use the functions from the module, for example: 
number = random.randint(1, 10) 

Because we will use a lot of functions to write our GUI code, we're going to use a slightly different import syntax to make it easier. It looks like this: 
from random import *

The import * means import all and it means we don't need to write random. before the functions and can generate a random number using: 
number = randint(1,10)
"""
from tkinter import *

# Create a window
root = Tk()
root.title("My GUI App")

# Run the main window loop
root.mainloop()

#Note that a blank GUI will pop up
