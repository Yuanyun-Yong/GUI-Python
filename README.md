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

"""
Adding a label to the window
Ok, we've got a window, but that's not very exciting by itself! So, let's look at how to add our first widget - a Label.
There are 2 basic steps for adding a widget in tkinter:
my_label = Label(root, text="My Label")
my_label.pack()

First, we create the label, giving it a name. The parameters in the brackets say that root is the parent widget, in other words that this label should go inside the root window, and that the text on the label should be My Label.
The second line uses the pack() function to actually put the widget into the window. We will learn more about ways of doing this later, but for now just know that pack() puts each widget into the window after any that have already been packed.
Under the relevant comment in the editor, create a label called label1, with parent root and text My GUI App!
On the next line, add label1 to the window using pack().
Under the next comment, create a label called label2, with parent root also, but this time make the text a longer sentence--it can say anything.
Pack the label into the window.
"""

from tkinter import *

# Create a window
root = Tk()
root.title("My GUI App")

# Create a label and add it to the window using pack()
my_label = Label(root, text="My GUI App!")
label1 = my_label.pack()
# Create a second label with longer text and add it to the window using pack()
label2 = Label(root, text = "This is my very first time making a GUI")
label2.pack()

# Run the main window loop
root.mainloop()

"""
More on creating a label
In the first lesson we had a look at how to create a window and add a label. In this lesson we are going to take a closer look at labels!
When we create a label, there are a few other parameters we can set in addition to the parent and the text. Let's look at some:
my_label = Label(root, text="Here is a label with a long sentence in it", wraplength=100, justify="center", fg="red", bg="yellow")
wraplength says how wide each line should be. We can use this to make a longer label wrap onto multiple lines. By default this is measured in pixels.
justify lets you set the text to be left, right or center aligned within the label. By default, all text in a label is centered.
fg sets the foreground color or text color for the writing in the label.
bg sets the background color for the space that the label takes up behind the text.
Set the background color for label1 to blue.
Set the foreground color for label1 to yellow.
Set the wraplength for label2 to 100.
Left align the text in label2.
"""

from tkinter import *

# Create a window
root = Tk()
root.title("My GUI App")

# Create a label and add it to the window using pack()
label1 = Label(root, text="My GUI App!", bg = "blue", fg = "yellow")
label1.pack()

# Create a second label with longer text and add it to the window using pack()
label2 = Label(root, text="Whatever you want but make it a longer sentence!", wraplength = 100, justify = "left")
label2.pack()

# Run the main window loop
root.mainloop()

"""
Using a StringVar() to set the text for a label
At the moment, we are hard-coding the text for our labels. This is fine when we know that our label text will never change.
Sometimes, however, we might want the label text to change when the user does something. To do this, we can use a tkinter variable. Tkinter handles variables a bit differently from regular Python code. You have to decide the datatype first, then create the right variable and set the value:
name = StringVar()
name.set("Billy")
my_label = Label(root, textvariable=name)
Then, instead of setting a text parameter, we set a textvariable parameter in our label.
Whatever value is stored in the name variable will be displayed in the label. If the name variable changes at all, the label will automatically be updated which is pretty cool!
In this course we are going to build a banking type app that lets the user deposit and withdraw money from accounts, and track progress towards savings goals such as a holiday, or new video game console. We've put an empty window in the code for you to start with.
Change the title of the window to Goal Tracker.
Under the relevant comment, create a StringVar() called message_text.
On the next line, set() the variable message_text to: Welcome! You can deposit or withdraw money and see your progress towards your goals.
Under the next relevant comment, create a label called message_label with root as the parent, message_text as the textvariable and a wraplength of 250.
Pack the message label into the GUI.
"""

"""
Goal Tracking App

The app we build in this course isn't designed to be an actual banking program, as most people would just use their online banking for that, but rather an app for tracking progress toward some goals.

Although in the course we use accounts and depositing and withdrawing money, the code could easily be adapted for other apps. For example, it could be turned into an app for parents to track their children's saving progress for a new toy or bike with money from their allowance and chores.

It could also be modified to track time spent doing activities like practice or exercise, calories consumed or credits earned from courses. So, once you've completed the course, get creative with the code and let us know what you come up with!
"""
from tkinter import *

# Create a window
root = Tk()
root.title("Goal Tracker")

# Create and set the message text variable
message_text = StringVar()
message_text.set("Welcome! You can deposit or withdraw money and see your progress towards your goals.")

# Create the message label and add it to the window using pack()
message_label = Label(root, textvariable = message_text, wraplength = 250)
message_label.pack()

# Run the main window loop
root.mainloop()
