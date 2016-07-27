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

"""
Putting an image in a label
We can also put images in labels! This is a handy way of getting any images you need into a GUI app.
To add an image, we do it in a similar way to how we used a variable. First we have to create a PhotoImage() variable with the name or path to the image stored in it:
happy_image =  PhotoImage(file="/images/python/happy.png")
Then, we set an image parameter on the label to the variable the image is stored in, and pack it into the GUI:
my_label = Label(root, image=happy_image)
my_label.pack()
Under the relevant comment create a PhotoImage() variable called neutral_image storing the image /images/python/neutral.png.
Under the next comment, create a new label called image_label and set the image to our neutral image.
Pack the label into the GUI.
"""
from tkinter import *

root = Tk()
root.title("Goal Tracker")

# Create and set the message text variable
message_text = StringVar()
message_text.set("Welcome! You can deposit or withdraw money and see your progress towards your goals.")

# Create the message label and add it to the window using pack()
message_label = Label(root, textvariable=message_text, wraplength=250)
message_label.pack()

#Create a PhotoImage()
neutral_image = PhotoImage(file = "/images/python/neutral.png")

#Create a new Label using the PhotoImage and pack it into the GUI
image_label = Label(root, image = neutral_image)
image_label.pack()

# Run the main window loop
root.mainloop()

"""
Adding a multiline label using \n
We now have a welcome message label and an image label, but this part of the GUI will need one more label to show us our account balances. So let's get one more bit of practice adding a label with a textvariable.
This time, instead of using wraplength we're going to split the label onto 2 lines using \n, which is the newline character.
Under the relevant comment, create a StringVar() called account_details.
Set account_details to: Savings: $500 - 25% of $2000 goal \nTotal balance: $500
Create a label called details_label and set the textvariable to account_details.
Pack the details label into the GUI.
"""
from tkinter import *

root = Tk()
root.title("Goal Tracker")

# Create and set the message text variable
message_text = StringVar()
message_text.set("Welcome! You can deposit or withdraw money and see your progress towards your goals.")

# Create the message label and add it to the window using pack()
message_label = Label(root, textvariable=message_text, wraplength=250)
message_label.pack()

#Create a PhotoImage()
neutral_image = PhotoImage(file="/images/python/neutral.png")

#Create a new Label using the PhotoImage and pack it into the GUI
image_label = Label(root, image=neutral_image)
image_label.pack()


# Create and set the account details variable
account_details = StringVar()
account_details.set("Savings:$500 - 25% of $2000 goal \nTotal balance:$500")

# Create the details label and pack it into the GUI
details_label = Label(root, textvariable=account_details)
details_label.pack()

# Run the mainloop
root.mainloop()

"""
Getting to know the Entry widget.
A widget that is commonly needed in a GUI app is an Entry widget. This is a basic text input field that the user can type into. Let's see how it works:
name_entry = Entry(root, textvariable=name, width=30)
Usually, we would have it linked to a variable because we most likely want to do something with the value. The width for an entry is measured in characters by default.
Under the relevant comment, create a StringVar() called words, we don't need to set a value this time.
Under the next comment, create an Entry called words_entry with root as parent, and set the textvariable to words.
Pack the entry into the GUI.
"""

from tkinter import *

# Create a window
root = Tk()
root.title("My GUI App")

# Create a label and add it to the window using pack()
label1 = Label(root, text="My GUI App!")
label1.pack()

#Create a StringVar() to store text
words = StringVar()

# Create a text entry field
words_entry = Entry(root, textvariable=words)
words_entry.pack()

# Create a second label with longer text and add it to the window using pack()
label2 = Label(root, text="Another label", wraplength=150)
label2.pack()

# Run the main window loop
root.mainloop()

"""
Linking an Entry with a Label using a textvariable
Whenever the user types something into the Entry field, that value will be stored in the textvariable we have assigned to it.
We can link another widget to the same textvariable to see this in action. This is an easy way to use the value, and we will look at other ways later on.
Replace the ??? to set the textvariable for label2 to words as well.
You may like to try changing the wraplength on label2 to some different numbers to see what happens to the label and the window when you enter more text in the entry field. What happens if you remove wraplength altogether?
"""

from tkinter import *

# Create a window
root = Tk()
root.title("My GUI App")

# Create a label and add it to the window using pack()
label1 = Label(root, text="My GUI App!")
label1.pack()

#Create a StringVar() to store text
words = StringVar()

# Create a text entry field
words_entry = Entry(root, textvariable=words)
words_entry.pack()

# Create a second label with longer text and add it to the window using pack()
label2 = Label(root, textvariable = words, wraplength=150)
label2.pack()

# Run the main window loop
root.mainloop()

"""
Customizing an Entry widget
We have seen that we can change the width of an Entry widget. Like a label, there are many other things that can be customized too. Again, just because you can change the colors of things, it doesn't mean you should, but here are a couple of examples:
colorful_entry = Entry(root, bg="blue", fg="yellow", selectbackground="limegreen", selectforeground="black")
bg and fg set the background color of the entry box and the color of the text in the entry box respectively.
selectbackground sets the highlight color of selected text in the entry and selectforeground sets the color of text itself when it is selected.
Set the background color of the words_entry widget to a color of your choice e.g. yellow.
Set the foreground color of the words_entry widget to another color of your choice.
Set the background color for selected text to another color of your choice.
Set the text color for selected text to another color of your choice.
"""

from tkinter import *

# Create a window
root = Tk()
root.title("My GUI App")

# Create a label and add it to the window using pack()
label1 = Label(root, text="My GUI App!")
label1.pack()

#Create a StringVar() to store text
words = StringVar()

# Create a text entry field
words_entry = Entry(root, textvariable=words, bg = "blue", fg = "yellow", selectbackground = "purple", selectforeground = "red")
words_entry.pack()

# Create a second label with longer text and add it to the window using pack()
label2 = Label(root, textvariable=words, wraplength=150)
label2.pack()

# Run the main window loop
root.mainloop()

"""
Adding an amount input to our goal tracking app
Let's return to our goal tracking app. We've got an area set up where our helpful goal tracking character welcomes us and tells us how much money we currently have.
We want our users to be able to deposit and withdraw money, so we're going to need an Entry widget where they can type in the amount. We're also going to need to label it so they know what to type into it.
Let's start with the label.
Under the relevant comment, create a Label called amount_label with root as parent and the text Amount: This text won't change so we can hard-code it in rather than using a variable.
Pack the label into the GUI.
"""
from tkinter import *

root = Tk()
root.title("Goal Tracker")

# Create and set the message text variable
message_text = StringVar()
message_text.set("Welcome! You can deposit or withdraw money and see your progress towards your goals.")

# Create and pack the message label
message_label = Label(root, textvariable=message_text, wraplength=250)
message_label.pack()

# Create the PhotoImage and label to hold it
neutral_image = PhotoImage(file="/images/python/neutral.png")
image_label = Label(root, image=neutral_image)
image_label.pack()

# Create and set the account details variable
account_details = StringVar()
account_details.set("Savings: $500 - 25% of $2000 goal \nTotal balance: $500")

# Create the details label and pack it into the GUI
details_label = Label(root, textvariable=account_details)
details_label.pack()

# Create a label for the amount field and pack it into the GUI
amount_label = Label(root, text = "Amount: ")
amount_label.pack()

# Run the mainloop
root.mainloop()

"""
Adding the amount entry field
Ok, now we need to create a variable so that we can store the value the user types in, and create the Entry field itself.
Users might want to enter an amount like $65.50 so we'll need to use a DoubleVar() which will let us store float values. When we do this, it puts the value 0.0 into the field. It will be annoying if the user has to delete this before they start typing, so we're going to set() the variable to an empty string "" to start off with so that the field will be empty.
Create a DoubleVar() called amount under the relevant comment.
Set amount to an empty string by putting "" inside the brackets of the set() function.
Under the next comment, create an Entry called amount_entry with root as parent and amount as the textvariable.
Pack amount_entry into the GUI.
"""

from tkinter import *

root = Tk()
root.title("Goal Tracker")

# Create and set the message text variable
message_text = StringVar()
message_text.set("Welcome! You can deposit or withdraw money and see your progress towards your goals.")

# Create and pack the message label
message_label = Label(root, textvariable=message_text, wraplength=250)
message_label.pack()

# Create the PhotoImage and label to hold it
neutral_image = PhotoImage(file="/images/python/neutral.png")
image_label = Label(root, image=neutral_image)
image_label.pack()

# Create and set the account details variable
account_details = StringVar()
account_details.set("Savings: $500 - 25% of $2000 goal \nTotal balance: $500")

# Create the details label and pack it into the GUI
details_label = Label(root, textvariable=account_details)
details_label.pack()

# Create a label for the amount field and pack it into the GUI
amount_label = ttk.Label(root, text="Amount:")
amount_label.pack()

# Create a variable to store the amount
amount = DoubleVar()
amount.set("")

# Create an entry to type in amount
amount_entry = Entry(root, textvariable = amount)
amount_entry.pack()

# Run the mainloop
root.mainloop()

"""
Creating a Button widget
Now that we’ve learned how to put labels, images, and text entry fields into a window, we need to learn to create buttons. Later, we will learn how to make things happen when a user clicks on one of our buttons but for right now, here’s the code to create a button that says, “Click Me!”:
my_button = Button(root, text="Click Me!")
We simply give it a name, use the Button widget class and put some text on it.
Let's add a Submit button to our goal tracking app so that we can do something with the amount the user enters.
Underneath the comment, create a Button called submit_button with root as the parent.
Set the text for the button to Submit.
Pack the button into the GUI.
"""

from tkinter import *

root = Tk()
root.title("Goal Tracker")

# Create and set the message text variable
message_text = StringVar()
message_text.set("Welcome! You can deposit or withdraw money and see your progress towards your goals.")

# Create and pack the message label
message_label = Label(root, textvariable=message_text, wraplength=250)
message_label.pack()

# Create the PhotoImage and label to hold it
neutral_image = PhotoImage(file="/images/python/neutral.png")
image_label = Label(root, image=neutral_image)
image_label.pack()

# Create and set the account details variable
account_details = StringVar()
account_details.set("Savings: $0 \nTotal balance: $0")

# Create the details label and pack it into the GUI
details_label = Label(root, textvariable=account_details)
details_label.pack()

# Create a label for the amount field and pack it into the GUI
amount_label = Label(root, text="Amount:")
amount_label.pack()

# Create a variable to store the amount
amount = DoubleVar()
amount.set("") 

# Create an entry to type in amount
amount_entry = Entry(root, textvariable=amount)
amount_entry.pack()

# Create a submit button
submit_button = Button(root, text = "Submit")
submit_button.pack()

# Run the mainloop
root.mainloop()

"""
Customizing a Button widget
Let's have a look at some of the things we can customize on a Button widget. We have bg and fg as usual, and here are a few others:
my_button = Button(root, text="Click Me!", bg="red", fg="yellow", width=30, height=3, bd=1, state="normal", activebackground="green")
width is measured in characters.
height is measured in rows or lines of text.
bd sets the border width for the button in pixels, the default is 2px.
state lets you disable a button using state="disabled", the default is "normal".
activebackground and activeforeground set the colors for the button and text when the user is pressing down on the button.
Set the width of the submit button to 16.
Set the background color to red.
Set the text color to yellow.
Set the active background color to lawngreen.
"""

from tkinter import *

root = Tk()
root.title("Goal Tracker")

# Create and set the message text variable
message_text = StringVar()
message_text.set("Welcome! You can deposit or withdraw money and see your progress towards your goals.")

# Create and pack the message label
message_label = Label(root, textvariable=message_text, wraplength=250)
message_label.pack()

# Create the PhotoImage and label to hold it
neutral_image = PhotoImage(file="/images/python/neutral.png")
image_label = Label(root, image=neutral_image)
image_label.pack()

# Create and set the account details variable
account_details = StringVar()
account_details.set("Savings: $0 \nTotal balance: $0")

# Create the details label and pack it into the GUI
details_label = Label(root, textvariable=account_details)
details_label.pack()

# Create a label for the amount field and pack it into the GUI
amount_label = Label(root, text="Amount:")
amount_label.pack()

# Create a variable to store the amount
amount = DoubleVar()
amount.set("") 

# Create an entry to type in amount
amount_entry = Entry(root, textvariable=amount)
amount_entry.pack()

# Create a submit button
submit_button = Button(root, text="Submit", width = 16, bg = "red", fg = "yellow", activebackground = "lawngreen")
submit_button.pack()

# Run the mainloop
root.mainloop()

"""
Themed tkinter widgets or ttk
If you put tkinter code into a Python editor on your computer such as IDLE or PyCharm and run it, you might be disappointed with how plain the GUI looks. This might make you want to brighten it up with some colors and things like we did with our submit button. However, as we've mentioned, users generally want a GUI to look nice, but also consistent with the operating system they are using.
Luckily, tkinter has a collection of themed widgets, called ttk that can be imported if you want a simple way to make your GUI look nicer. These widgets are designed to look more native, so if you're on Windows they will be styled like the normal Windows programs, if you're on Mac, they'll be styled to look like Mac programs:
https://www.codeavengers.com/images/python/gui/all-os.png
To use ttk widgets, you just import them and then use ttk. in front of your widgets:
from tkinter import ttk
my_button = ttk.Button(root, text="Hello")
Note that you can't set parameters like bg and fg on these. There are a few other differences between tk and ttk widgets.
We've prefixed the Labels for you–they don't really look much different as ttk widgets, but it's good to be consistent.
Import ttk from tkinter of our goal tracking app code.
Put the ttk. prefix in front of the amount_entry widget.
Then put the ttk. prefix in front of the submit_button widget.
"""

from tkinter import *
from tkinter import ttk

root = Tk()
root.title("Goal Tracker")

# Create and set the message text variable
message_text = StringVar()
message_text.set("Welcome! You can deposit or withdraw money and see your progress towards your goals.")

# Create and pack the message label
message_label = ttk.Label(root, textvariable=message_text, wraplength=250)
message_label.pack()

# Create the PhotoImage and label to hold it
neutral_image = PhotoImage(file="/images/python/neutral.png")
image_label = ttk.Label(root, image=neutral_image)
image_label.pack()

# Create and set the account details variable
account_details = StringVar()
account_details.set("Savings: $0 \nTotal balance: $0")

# Create the details label and pack it into the GUI
details_label = ttk.Label(root, textvariable=account_details)
details_label.pack()

# Create a label for the amount field and pack it into the GUI
amount_label = ttk.Label(root, text="Amount:")
amount_label.pack()

# Create a variable to store the amount
amount = DoubleVar()
amount.set("")

# Create an entry to type in amount
amount_entry = ttk.Entry(root, textvariable=amount)
amount_entry.pack()

# Create a submit button
submit_button = ttk.Button(root, text="Submit")
submit_button.pack()

# Run the mainloop
root.mainloop()

"""
Making a button call a function
At the start of this lesson we talked about making something happen when a user clicks a button. This is commonly called handling an event in programming.
In a Button widget, we can set a command argument that will call a function when the button is clicked:
def say_hello():
    label_text.set("Hello!")
    
label_text = StringVar()
my_label = ttk.Label(root, textvariable=label_text)
my_button = ttk.Button(root, text="Click Me!", command=say_hello)
In this code, we have created a function called say_hello() that changes the label text to Hello. When the button is clicked, this function is called.
If you need to get the value of a variable, for example from an Entry, you can use the .get() function e.g. a_value = a_variable.get()
Let's add a function and a call to it in our goal tracking app. We want the user to enter an amount, click "submit" and have that amount added to their savings account balance.
First, we'll need a variable to store the account balance. On line 5 create a regular python variable called savings_balance and set it to 0.
Next, create a function called update_balance that takes no parameters.
Inside the function, add the line global savings_balance - this lets us access the savings balance variable inside the function, without having to pass it in.
Then use the .get() function to get the value in the amount entry, and store it as deposit_amount.
Add the deposit amount to the current savings balance, and store in  savings_balance.
Add a command to the submit_button to run the update_balance() function when clicked.
"""

from tkinter import *
from tkinter import ttk

# Create a variable to store the account balance
savings_balance = 0


# Create a function that will update the balance.
def update_balance():
  global savings_balance
  deposit_amount = amount.get()
  savings_balance = savings_balance + deposit_amount

# GUI Code
root = Tk()
root.title("Goal Tracker")

# Create and set the message text variable
message_text = StringVar()
message_text.set("Welcome! You can deposit or withdraw money and see your progress towards your goals.")

# Create and pack the message label
message_label = ttk.Label(root, textvariable=message_text, wraplength=250)
message_label.pack()

# Create the PhotoImage and label to hold it
neutral_image = PhotoImage(file="/images/python/neutral.png")
image_label = ttk.Label(root, image=neutral_image)
image_label.pack()

# Create and set the account details variable
account_details = StringVar()
account_details.set("Savings: $0 \nTotal balance: $0")

# Create the details label and pack it into the GUI
details_label = ttk.Label(root, textvariable=account_details)
details_label.pack()

# Create a label for the amount field and pack it into the GUI
amount_label = ttk.Label(root, text="Amount:")
amount_label.pack()

# Create a variable to store the amount
amount = DoubleVar()
amount.set("")

# Create an entry to type in amount
amount_entry = ttk.Entry(root, textvariable=amount)
amount_entry.pack()

# Create a submit button
submit_button = ttk.Button(root, text="Submit", command = update_balance)
submit_button.pack()

# Run the mainloop
root.mainloop()

"""
Updating the GUI from the function
Lastly, we need to make it so that our label gets updated with the new account balance. This is just a simplified version of what our finished app will do, but it is enough to learn how buttons work for now.
Since our details_label has our savings balance and total balance, we'll need to set a variable for that. This part will make more sense once we add the ability to have more than one account/goal, but for now let's future-proof it.
Inside the update_balance() function, create a variable called total_balance and set it equal to savings_balance since we only have one account for now.
Use the .set() function to set the account_details variable to the following string: Savings: ${}\nTotal Balance: ${}.
Use .format() to insert the values savings_balance and total_balance into the string.
Set the amount variable back to an empty string "" so that the field clears when the user hits submit.
Format the output so that the balances in the label display to 2dp.
"""

from tkinter import *
from tkinter import ttk

# Create a variable to store the account balance
savings_balance = 0

# Create a function that will update the balance.
def update_balance():
    global savings_balance
    deposit_amount = amount.get()
    savings_balance += deposit_amount
    total_balance = savings_balance
    account_details.set("Savings: ${}\nTotal Balance: ${}".format(savings_balance, total_balance))


root = Tk()
root.title("Goal Tracker")

# Create and set the message text variable
message_text = StringVar()
message_text.set("Welcome! You can deposit or withdraw money and see your progress towards your goals.")

# Create and pack the message label
message_label = ttk.Label(root, textvariable=message_text, wraplength=250)
message_label.pack()

# Create the PhotoImage and label to hold it
neutral_image = PhotoImage(file="/images/python/neutral.png")
image_label = ttk.Label(root, image=neutral_image)
image_label.pack()

# Create and set the account details variable
account_details = StringVar()
account_details.set("Savings: $0 \nTotal balance: $0")

# Create the details label and pack it into the GUI
details_label = ttk.Label(root, textvariable=account_details)
details_label.pack()

# Create a label for the amount field and pack it into the GUI
amount_label = ttk.Label(root, text="Amount:")
amount_label.pack()

# Create a variable to store the amount
amount = DoubleVar()
amount.set("")

# Create an entry to type in amount
amount_entry = ttk.Entry(root, textvariable=amount)
amount_entry.pack()

# Create a submit button
submit_button = ttk.Button(root, text="Submit", command=update_balance)
submit_button.pack()

# Run the mainloop
root.mainloop()

"""
Introduction to the .grid() layout system
Our GUI for our goal tracking app is starting to get a bit more complex now that we have added so many widgets. It would be nice if we could have some more control over how they are placed in the window.
We have been using .pack() to place the widgets in the window, but tkinter also has another geometry manager called .grid().
With .grid() you set which row and column you want the widget to appear in, and it goes there:
my_button = ttk.Button(root, test="Click Me!")
my_button.grid(row=0, column=0)
(0, 0) is the top left corner of the window. Nice and easy, as long as you plan your grid well and use it for all of your widgets.
In the editor is a window with 9 buttons. Each button is labeled with the row and column it should be in, but .pack() has been used.
Change .pack() to .grid() and put each button in the correct row and column.
"""
from tkinter import *
from tkinter import ttk

root = Tk()
root.title("Grid Test")

button1 = ttk.Button(root, text="Row 0, Col 0")
button1.grid(row=0, column=0)

button2 = ttk.Button(root, text="Row 1, Col 2")
button2.grid(row=1, column=2)

button3 = ttk.Button(root, text="Row 2, Col 2")
button3.grid(row=2, column=2)

button4 = ttk.Button(root, text="Row 1, Col 0")
button4.grid(row=1, column=0)

button5 = ttk.Button(root, text="Row 0, Col 1")
button5.grid(row=0, column=1)

button6 = ttk.Button(root, text="Row 0, Col 2")
button6.grid(row=0, column=2)

button7 = ttk.Button(root, text="Row 1, Col 1")
button7.grid(row=1, column=1)

button8 = ttk.Button(root, text="Row 2, Col 1")
button8.grid(row=2, column=1)

button9 = ttk.Button(root, text="Row 2, Col 0")
button9.grid(row=2, column=0)

root.mainloop()

"""
Using rowspan and columnspan
Sometimes when we're using a grid layout system, we might want a widget to span over more than one row or column like so:
https://www.codeavengers.com/images/python/colspan.png
To do this, we can specify a columnspan or rowspan inside the .grid() function. A columnspan of 3 means that widget should take up 3 columns.
Another parameter we can set for widgets using the grid function is sticky. This makes the widget stick to specified edges of its container. To set sticky you pass in any combination of the letters N, S, W, E (compass directions) as either a string: sticky="NS" or a tuple: sticky=(N, NW)
Using sticky="WE" will make a widget the full width it can be, and sticky="NS" will make it full height.  "NSWE" will make it fill all the space available to it.
We've modified the code slightly so that you can explore columnspan and rowspan.
Edit the code to make button4 span 3 columns.
Make button5 span 2 rows.
Make button8 span 2 columns.
button4 should fill the width of the window, add a sticky parameter to make it do that.
Do the same for button8.
Lastly, button5 should fill the height of the space it is in, add a sticky parameter to do that.
"""
from tkinter import *
from tkinter import ttk

root = Tk()
root.title("Grid Test")

button1 = ttk.Button(root, text="Row 0, Col 0")
button1.grid(row=0, column=0)

button2 = ttk.Button(root, text="Row 0, Col 1")
button2.grid(row=0, column=1)

button3 = ttk.Button(root, text="Row 0, Col 2")
button3.grid(row=0, column=2)

button4 = ttk.Button(root, text="Row 1, Col 0")
button4.grid(row=1, column=0, columnspan=3, sticky="WE")

button5 = ttk.Button(root, text="Row 2, Col 0")
button5.grid(row=2, column=0, rowspan=2, sticky="NS")

button6 = ttk.Button(root, text="Row 2, Col 1")
button6.grid(row=2, column=1)

button7 = ttk.Button(root, text="Row 2, Col 2")
button7.grid(row=2, column=2)

button8 = ttk.Button(root, text="Row 3, Col 1")
button8.grid(row=3, column=1, columnspan=2, sticky="WE")

root.mainloop()

"""
Laying out our goal tracking GUI with .grid()
Ok, let's use .grid() to improve the layout of our app GUI!
It would be nice if we could sit the Amount:  label and its entry box next to each other on one line, as later we will need to add some other widgets to choose an account and so on.
In that row, we will have 2 columns, so we will need to set the columnspan of all of the other widgets to 2.
Here are the positions each widget should be in:
message_label: row 0, column 0
image_label: row 1, column 0
details_label: row 2, column 0
amount_label: row 3, column 0
amount_entry: row 3, column 1
submit_button: row 4, column 0
Position each widget in the positions listed above using .grid() instead of .pack().
Set the columnspan for all widgets except amount_label and amount_entry to 2.
"""
from tkinter import *
from tkinter import ttk

# Create a variable to store the account balance
savings_balance = 0

# Create a function that will update the balance.
def update_balance():
    global savings_balance
    deposit_amount = amount.get()
    savings_balance += deposit_amount
    total_balance = savings_balance
    account_details.set("Savings: ${:.2f}\nTotal Balance: ${:.2f}".format(savings_balance, total_balance))
    amount.set("")

root = Tk()
root.title("Goal Tracker")

# Create and set the message text variable
message_text = StringVar()
message_text.set("Welcome! You can deposit or withdraw money and see your progress towards your goals.")

# Create and pack the message label
message_label = ttk.Label(root, textvariable=message_text, wraplength=250)
message_label.grid(row=0, column=0, columnspan=2)

# Create the PhotoImage and label to hold it
neutral_image = PhotoImage(file="/images/python/neutral.png")
image_label = ttk.Label(root, image=neutral_image)
image_label.grid(row=1, column=0, columnspan=2)

# Create and set the account details variable
account_details = StringVar()
account_details.set("Savings: $0 \nTotal balance: $0")

# Create the details label and pack it into the GUI
details_label = ttk.Label(root, textvariable=account_details)
details_label.grid(row=2, column=0, columnspan=2)

# Create a label for the amount field and pack it into the GUI
amount_label = ttk.Label(root, text="Amount:")
amount_label.grid(row=3, column=0)

# Create a variable to store the amount
amount = DoubleVar()
amount.set("")

# Create an entry to type in amount
amount_entry = ttk.Entry(root, textvariable=amount)
amount_entry.grid(row=3, column=1)

# Create a submit button
submit_button = ttk.Button(root, text="Submit", command=update_balance)
submit_button.grid(row=4, column=0, columnspan=2)

# Run the mainloop
root.mainloop()

"""
Adding padding to space out widgets
We can add padding to widgets in order to space them out and make them look less cluttered. We use padx (pads the sides) and pady (pads the top and bottom) which are both in pixels:
my_label = Label(root, text="Hello")
my_label.grid(row=0, column=0, padx=10, pady=10)
Let's improve our goal tracking app GUI with these.
Add 10px of padding on all 4 sides of the message_label.
Add 10px of padding on all 4 sides of the image_label.
Add 10px of padding on all 4 sides of the details_label.
Add 3px padding to the top and bottom of the amount_label and 10px to the sides.
Add 3px padding to the top and bottom of the amount_entry and 10px to the sides.
Add 10px padding to all sides of the submit_button.
"""

from tkinter import *
from tkinter import ttk

# Create a variable to store the account balance
savings_balance = 0

# Create a function that will update the balance.
def update_balance():
    global savings_balance
    deposit_amount = amount.get()
    savings_balance += deposit_amount
    total_balance = savings_balance
    account_details.set("Savings: ${:.2f}\nTotal Balance: ${:.2f}".format(savings_balance, total_balance))
    amount.set("")

root = Tk()
root.title("Goal Tracker")

# Create and set the message text variable
message_text = StringVar()
message_text.set("Welcome! You can deposit or withdraw money and see your progress towards your goals.")

# Create and pack the message label
message_label = ttk.Label(root, textvariable=message_text, wraplength=250)
message_label.grid(row=0, column=0, columnspan=2, padx=10, pady=10)

# Create the PhotoImage and label to hold it
neutral_image = PhotoImage(file="/images/python/neutral.png")
image_label = ttk.Label(root, image=neutral_image)
image_label.grid(row=1, column=0, columnspan=2, padx=10, pady=10)

# Create and set the account details variable
account_details = StringVar()
account_details.set("Savings: $0 \nTotal balance: $0")

# Create the details label and pack it into the GUI
details_label = ttk.Label(root, textvariable=account_details)
details_label.grid(row=2, column=0, columnspan=2, padx=10, pady=10)

# Create a label for the amount field and pack it into the GUI
amount_label = ttk.Label(root, text="Amount:")
amount_label.grid(row=3, column=0, padx=10, pady=3)

# Create a variable to store the amount
amount = DoubleVar()
amount.set("")

# Create an entry to type in amount
amount_entry = ttk.Entry(root, textvariable=amount)
amount_entry.grid(row=3, column=1, padx=10, pady=3)

# Create a submit button
submit_button = ttk.Button(root, text="Submit", command=update_balance)
submit_button.grid(row=4, column=0, columnspan=2, padx=10, pady=10)

# Run the mainloop
root.mainloop()

"""

"""
