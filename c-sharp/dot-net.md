
## .NET Architecture
* .NET Architecture is consisted of .NET Framework, .NET Core and Xamarin.
  * .NET Framework has WPF, Window Forms and ASP.NET.
  * .NET Core has UWP, ASP.NET Core.
  * Xamarin supports mobile development for iOS, Android and OS X.
    * It is based on Mono.
    * The Mono framework is an open source implementation of Microsoft’s .NET Framework based on the open standards for the C# language and the Common Language Runtime.
* All component of this architecture use the common .NET stardard library and infrastructure like supported languages, runtime components and build tools.

## .NET Standard
* It is a formal specification of .NET APIs that are intended to be available on all .NET implementations
* [Click](https://docs.microsoft.com/en-us/dotnet/standard/net-standard) to see its content.

Formatting
Advanced/Format Selection

or
Ctrl + K then Ctrl + F

Debug
Visual Studio has breakpoint for debugging it allows the program to run line by line.
There are Autos, Immediate, Locals, and Watch windows for debugging.

Press F9 to add breakpoint.
will see a red dot represents the breakpoint.
run in debug mode can view all values for variables when the code stops at breakpoint in the code editor by hovering over the variable name and click the arrow button.

Debug mode
The Step Into command
Continue to debug by single-stepping through a procedure
The Step Over command
Run procedure without single-stepping, continue single-step after the call
The Step Out command
End single-stepping in procedure, continue single-step after the call

Console App

Every console app contain main method
static void Main(string[] args) { }

Console.ReadLine(); take user input
default in type in C# is 32-bit

Console.WriteLine method displays a line of text in the console window in a new line.
Console.WriteLine(“Hello World”);

Console.Write method displays text in the console window without creating a new line.


Console.ReadLine( ); This method get user input.

Some Console class methods

Console.ForegroundColor=ConsoleColor.Green

Console.Close() method will close and exit the application.

Console.Clear() method of any component will set the console Text to empty.

Console.SetCursorPosition(xPosition, yPosition);

Console.ReadKey(true);	//the program will for user input any key, key will not be shown in the console if the parameter is true.

Console.CursorVisible = false;  //hide cursor

Window Form App
Program.cs –This holds the Main method that will start the program.
From1.cs –Where code is generally added by the programmer. function and event handler can be added here.
Form1.designer.cs –Code is written and inserted here by the Windows designer.

A reference can be added to the current project, so many more objects can be utilized.
to add a reference, right click on the references folder, select add reference. select the desired the reference and click OK.



camel naming convention is mostly used.    submitButton
Properties Window on the right-bottom corner is used to view and modify the property values of a given object.
double-click control item to open the code window in the Form.cs file. A event handler method is generated, it is called when the default event is triggered by the user. the first parameter of the method is the sender object, the second provide additional information about the event. A delegate reference is also auto created in the designer.cs
click the event(lightning) icon in the property panel and double click on a event name can also add the control a specific event handler.

right-click can select lock to lock a control.
Press the Tab key to use IntelliSense for automatic code completion.
access the Visual Studio Documentation by clicking Help on the menu bar
For Context-Sensitive Help, move mouse over any code, click the pop-up hint, then uses F1 Key.
Visual C# has three modes in which it operates:
Design Mode: the mode in which you create the application, also known as design time
Run Mode: executes the application in the Visual Studio environment, also known as run time.
Break Mode: momentarily suspends execution of a running application for testing and debugging purpose

Make a project to be the start-Up Project by right clicking the project name in the solution explorer.
To reference a new project to existing project. Select the References section of the project, right click and select Add Reference.

Anchoring causes controls to remain at a fixed distance from the sides of the container.
Docking attaches a control to a container such that the control stretches across an entire side or fills an entire area.
The Padding property specifies the distance between the docked controls and the edges.

media files can be added to the resources of the project, double clicking the resource node in the solution explorer
resources can be accessed using Properties.Resources.ResourceManager.GetObject(“imageName”)
or
Properties.Resources.resourceName

Font object is used to assign to the Font properties of controls to change theirs fonts.
font style can also be toggled with bitwise operator.
labelName.Font = new Font(currentFont, newStyle);
labelName.Font = new Font(labelName.Font, labeName.Font.Style^FontStyle.Bold);

Image object is the image that can be loaded into the Image property of the controls.
Controls.Image=(Image)(Properties.Resources.ResourceManager.GetObject(“imageName”);

Any object can publish a set of events to which other classes can subscribe.
The publishing class defines a delegate
The subscribing class creates a method that matches the signature of the delegate and then it creates an instance of that delegate type encapsulating that method
When the event is raised, the subscribing class’s methods are invoked through the delegate
A method that handles an event is called an event handle

Event handlers in the .NET Framework always return void and take two parameters
The first is the “source” of the event (publishing object)
The second is an EventArgs object that stores all event data.

Mouse Events can have two type of event argument(the second parameter of the event handlers)
EventArgs - MouseEnter, MouseHover, MouseLeave
MouseEventArgs - MouseDown, MouseUp, MouseMove, MouseWheel

MouseEventArgs

Properties:
Button	//Left, Right, Middle, None
Clicks	//number of clicks.
X	//X coordinates relative to the top-left corner of the clicked control.
Y	//Y coordinates relative to the top-left corner of the clicked control.

Keyboard Event
KeyPress	//response to key that represent ASCII characters. after KeyDown, before KeyUp
Event Argument - KeyPressEventArgs
Property
KeyChar


KeyUp		//sensitive to modifier keys - Alt, Shift, Control and others.
KeyDown	//sensitive to modifier keys - Alt, Shift, Control and others.
Event Argument - KeyEventArgs
Property
Alt		//true. if Alt key is up or down.
Control
Shift
KeyCode	//Key,enum that represent a certain key, modifiers key is not included.
KeyData	//returns key press info, includes key combinations.
KeyValue	//returns an int key code.
Modifiers	//returns Modifers.enum value.

Process class
start method
it can be used to open other app
System.Diagnostics.Process.Start(@“C:\”);	//open C drive
System.Diagnostics.Process.Start(“http://www.google.com”);	//open webpage
System.Diagnostics.Process.Start(“notepad”);	//open notepad

Image Object
get image
Image name = Image.FromFile("filePath");  
draw image
graphicsObjectName.DrawImage(imageObjectName, x1, x2, y1, y2);


Timer object
Create timer
timerName = new Timer();  
Set interval
timerName.Interval = intervalInMs;
Set Tick Event
Occurs when the specified timer interval has elapsed and the timer is enabled.
myTimer.Tick += new EventHandler(TimerEventProcessor);
Start timer:
timerName.Start();
Stop timer:
timerName.Stop();




ColorDialog
If colorDialog component is not created in the form designer.
//declare ColorDialog
ColorDialog newColor = new ColorDialog();     
//open and save selected color    
//     newColor.ShowDialog() open the color picker
if (newColor.ShowDialog() == DialogResult.OK) {
                  userColor = newColor.Color;              
}
If colorDialog component is created in the form designer. and it is called picker.
picker.Color = c;                //Display with the previous colour already chosen  
picker.ShowDialog();             //Display the actual dialog box        
c = picker.Color;                //Save the colour choice the user made




Graphics
Graphics objects need to be create to draw graphics. It can be create inside a using block
using (Graphics g = canvas.CreateGraphics()) {  }
or
in window form app
g = this.CreateGraphics();               //Create a graphics object, this refers to the form class.


SolidBrush object is needed to fill a color.
Brush brushName = new SolidBrush(colorObject);
Pen object is needed to draw lines
penName = new Pen(colorObject);                         

Methods:
g.Clear(initial backgroundcolor);
g.DrawImage(imageObjectName, x1, x2, y1, y2);
g.FillRectangle(brushObject,89,300,1,121);  

A paint event handler can also be added in form constructor.
this.Paint += new PaintEventHandler(paint event handler method);  //Registers the Paint event handler  
paint event handler method has graphics object in the PaintEventArgs
private void PaintHandler(object sender, PaintEventArgs e)      {        
	Graphics g = e.Graphics;                //Get the Graphics object from the PaintEventArgs          
}


—————————————————————————————————
Class Controls

Common Properties
BackColor
BackgroundImage
Enabled	//when false, the control is disabled.
Focused
Font
ForeColor
TabIndex	//the tab order
TabStop 	//if true, the control is focused when tab key is pressed.
Text
Visible

Common Methods
Hide
Select
Show

———————————————————————————————————
Form

Properties
Name	//The name of the form, changed when file name changed in the Solution Explorer.
AcceptButton	//The default button that responses to the enter key.
AutoScroll	//when false(default) scrollbars is disabled.
CancelButton //The default button that response to escape key.
Font
Text 		//form’s title

Method
form method works everywhere in a form cs file.
this.Close();		//this will close the form.
Application.Exit()	//this closes the entire program, it is the preferred method for exit an app.

Hide()
Show()

Common Event
Load		//This is called before the form is displayed.
Activated	//The Activated event occurs when the user switches to the form from another form or application
FormClosing	//The FormClosing event is triggered as the form is being closed, but before it has closed.
FormClosed	//The FormClosed event occurs after a form has closed.


To create an optional event handler, follow these steps:
click the lightning icon to add event handler to certain event.

One project can have one more form, In the menu bar, Project -> Add Windows Form…

To set the start up form.  In Program.cs Main method,
edit Application.Run(new FormName());

Instantiate new form object:
ErrorForm errorForm = new ErrorForm();

//show a model form
errorForm.ShowDialog();
//show a modeless form
errorForm.Show();

model form doesn’t allow the user to switch forms and halt the execution of code after the ShowDialog() method until it is closed. modeless form allow user to switch at anytime.

//close a form
this.Close();

//hide a form
this.Hide();
form can call show() or showDialog() again to show content. hide doesn’t release remove form from memory.


in form cs we can have
customized functions
private void FunctionName() {
}


TabIndex it is used to set the Tab order. the order of focus when user press the tab key.
Access Key is the short key for elements in form to enable add & to the text property of element.
Ex if A button has name E&xit, it can be accessed by using Alt + X(letter after &).

//double click blank area on form to get the method that runs when form is loaded.
private void formName_load(object sender, EventArgs e)
{}


Load Event Handler
Every form has a Load event, Executes when the form is first displayed
Double-click in any empty space on the form to edit it.

Place the code to be executed between the Private Sub and End Sub lines of the event handler
private void Form1_Load(…){
MessageBox.Show("Prepare to see the form!”);
}



———————————————————————————————————
Button
The accept button in the property setting, set the button that reaction to enter key input.
The cancel button reacts with the escape key.
Button can have access shortcuts by place & symbol in front of a desired character from its text.

Properties
Text
FlatStyle	//control the button style, has Flat, Popup, Standard(default), System


Event handler for button click event (enable by double click objects.)
private void Clear_Click(object sender, EventArgs e)
        {
            FunctionName();
        }
———————————————————————————————————
Label
Properties
Font
Text
TextAlign

labelName.Visible = true; //set the label visible.
labelName.Text = “abc”;	//set label text. or set to null for empty text.
labelName.AutoSize = true	//enable autosize when the text content is changed.
reportTitleLabel.TextAlign = ContentAlignment.MiddleCenter;
label.Text		set the label text
greetingLabel.Text = "Hello " + nameTextBox.Text;
messageLabel.BackColor = Color.Black
messageLabel.ForeColor = Color.Yellow
messageLabel.BackColor = SystemColors.Control     //return default color
messageLabel.ForeColor = SystemColors.ControlText	//return default color

———————————————————————————————————
Picture Box
Properties
Image   //set the image to display
Sizemode  //control sizing, Normal(default, top-left), StretchImage, AutoSize(resize picturebox), CenterImage(middle), Zoom(aspect fit)


Event

Click

private void canadaPictureBox_Click(…)	//enable text when pictureBox is clicked
{
messageLabel.Text = "Hello”;   
}

———————————————————————————————————
TextBox
It gets user input

Properties
AcceptsReturn //if true in multiline textbox, hit enter create a new line. if false enter key responses as the default button of the form.

Multiline //default false which means multiline input is not enabled.
textBox.Text = string.Empty;	clear all text inside.
Readonly //if true, preventing user input text.
ScrollBars //works on multiline textbox, has None(default), Horizontal, Vertical or Both.
Text
TextBox.Text.Length;	//returns the text length

TextBox.UseSystemPasswordChar = true; 	//set the textbox to a password textbox.

textBox.Clear();	clear all text inside.
userNameTextBox.Focus();	//Get the cursor.

Common Event
TextChanged
———————————————————————————————————

Radio button
a radio button can be selected among many others, in a certain container like a group box.
Those on a form but not inside a group box are considered members of the same group.

Properties
Checked //bool
Text

Common event
CheckChanged
———————————————————————————————————
Message Box
It displays a pop-up window with customized message.

MessageBox.Show(Message, Caption, Buttons, Icon, DefaultButton);

Message -
It is the only mandatory field, a string that display within the box.
MessageBox.Show(Message); will generates message box will default setting.


Caption - title for the top bar of the box


Buttons - indicates which buttons to display
default is OK buttons
MessageBoxButtons.AbortRetryIgnore 	Displays Abort, Retry, and Ignore buttonsMessageBoxButtons.OK		Displays only an OK buttonMessageBoxButtons.OKCancel	Displays OK and Cancel buttonsMessageBoxButtons.RetryCancel	Displays Retry and Cancel buttonsMessageBoxButtons.YesNo		Displays Yes and No buttonsMessageBoxButtons.YesNoCancel	Displays Yes, No, and Cancel button

Icon - indicates icon to display
MessageBoxIcon.Asterisk
MessageBoxIcon.Information
MessageBoxIcon.Error
MessageBoxIcon.Hand
MessageBoxIcon.Stop
MessageBoxIcon.Exclamation
MessageBoxIcon.Warning
MessageBoxIcon.Questio


DefaultButton - indicates which button corresponds to the Return Key
MessageBoxDefaultButton.Button1	Selects the leftmost button on the message box as the default button
MessageBoxDefaultButton.Button2	Selects the second button from the left edge of the message box as the default button
MessageBoxDefaultButton.Button3	Selects the third button from the left edge of the message box as the default button

MessageBox.Show method returns an enumeration value that indicates which button the user clicked.
DialogResult.Abort
DialogResult.Cancel
DialogResult.Ignore
DialogResult.No
DialogResult.OK
DialogResult.Retry
DialogResult.Yes

———————————————————————————————————
Checkbox
Can select as many check boxes as you like within the same group box.

Properties
ThreeState  //if true checkbox can have three state(checked and indeterminate return trues if checked for Checked properties. This properties ’s default is false(only two state checked and unchecked.)
Appearance   //Normal(default), Button
Checkbox.Checked    //return true when checked, set true for checked state.default false
CheckState	//has checked, unchecked, indeterminate
Text

Common Event
CheckedChanged  //default
———————————————————————————————————

GroupBox
A GroupBox creates a grouping of controls, it has a caption, it doesn’t have scrollbars.
Controls are enclosed in a box with a title
Controls in a GroupBox have their own tab order, it can be assigned separately.
Moving a GroupBox moves its controls with it
Removing a GroupBox also removes all controls within it

Properties
Controls   set of controls it contains
Text
———————————————————————————————————
Panel
similar to Groupbox, but has scrollbars with no caption.

Properties
AutoScroll	//the auto appearance of the scroll. default false
BorderStyle	//has None(default), Fixed3D, FixedSingle
Controls
———————————————————————————————————
ListBox
A ListBox control displays a list of items and also allows the user to select one or more items from the list.

Properties
Items
MultiColumn   If it is set to True, entries can appear side by side horizontally like a table.(false by default)
SelectedIndex
SelectedIndices
SelectedItem
SelectedItems
SelectionMode	//None, One(default), MultiSimple, MultiExtended
Sorted			//if true all items are sorted, default false.

Methods
ClearSelected();   		Clear all selections.
GetSelected(index);	//return true if certain item is selected

Event
SelectedIndexChanged

Listbox.Items
Items property holds all entries of a listbox.
It can be edited using the property panel.
It can be edited in code in runtime using the Items Collection
ListBox has formatString setting in properties.

Items property can be used to access the entries.
customersListBox.Items[2]  // the third entry of the customer listbox.

Properties
Items.Count property returns the number of list box items or zero if the list is empty
Items.SelectedItem returns the text of the selected item.
Items.SelectedIndex property returns an integer with the index of the item selected by the user. If no item is selected, the value is set to -1.
Set Item.SelectedIndex can set the box's default selected value.

Methods
ListBox.Items.Add(value); 		Add item to the listbox at runtime.
ListBox.Items.Insert(Index, Item);	Insert an item at a specific position
ListBox.Items.RemoveAt(Index);	Removes item at the specified Index
ListBox.Items.Remove(Item);		Removes item with value specified by Item
ListBox.Items.Clear();			Removes all items in the Items property
ListBox.Items.Contains(Item);	Returns true if Item is found in the collection
ListBox.Items.IndexOf(Item);		Returns an integer with the index position of the first occurrence of Item in the collection


———————————————————————————————————
Checked List Box
Like a ListBox but user can select multiple entries.

properties
CheckOnClick property enables user to select and check the entry with one click.
SelectionMode //One(default), None

method
GetItemChecked method determines if an item is checked by returning a Boolean value
CheckedListBox.GetItemChecked(Index);	//return  true if it is checked by the user.

Event
ItemCheck	//activated when an item is checked or unchecked.
ItemCheckEventArgs properties
CurrentValue 	//it is either Checked, Unchecked, Indeterminate
Index		//return the index of the item.
NewValue	//specifies the new state of the item.
———————————————————————————————————
Combo Box
like a listBox plus a text field, text can be retrieved in the Text property.
There are Drop-down list combo box and simple combo box that looks similar to list box.

properties
DropDownStyle	//Simple, DropDown, DropDownList
Items
MaxDropDownItems	//a number from 1-100, if more items exists, a scrollbar will appear.
SelectedIndex		//return -1 if none selected.
SelectedItem
Sorted

Event
SelectedIndexChanged
———————————————————————————————————
Tool Tip
it is the short text message you see when holding the mouse over a control.
It is enabled by double-clicking tooltip in the toolbox.
when enabled all controls will have a tool tip property that can be set as a string.
For testing purpose, It can be seen in the component tray at runtime.

Properties
An InitialDelay property that regulates the delay before a tip appears
An AutoPopDelay property that determines how long a tip is displayed
The ReshowDelay property determines the time between the display of different tips as the user moves the mouse from control to control

Event
Draw	//it is called before the tool tip shows on the screen.
———————————————————————————————————
NumericUpDown Control  
Restricting a user’s input choices to a specific range of numeric values can be done with a NumericUpDown control.
A user can type numeric values into this control or click up and down arrows.

Properties
DecimalPlaces
Increment
Maximum
Minimum
UpDownAlign	//controls the direction of the up and down buttons.
Value	//the current value of the control
ReadOnly    //user can only use button to change value, not by typing.

Event
ValueChanged (default)
———————————————————————————————————
MenuStrip
A menuStrip control adds a menu to a form
Double-click on the menuStrip icon in the Menus & Toolbars section of the Toolbox.
The menuStrip control is displayed in the component tray.
Use the menu designer to visually create a custom menu system.
A menuStrip can have many ToolStripMenuItem
To add menu items to the menu, click the Type Here TextBox and type the menu item’s name, hit enter to confirm
Name property is recommended to end with the Menu suffix, to Reflect the Text property and position in the menu hierarchy. Ex fileOpenNewMenu.
To make the File menu item have an Alt key shortcut, type &File.  The letter F is underlined to indicate that it’s a shortcut.
To Add Separator Bars. Right-click menu item, select Insert Separator. A separator bar will be inserted above the menu item. Or type a hyphen (-) as a menu item’s Text propert
Menu items can have shortcut keys by setting the ShortcutKeys property.
You can remove a menu item by selecting it with the mouse and pressing the Delete key.
Menu items can be grouped by separator bars, which are inserted by right clicking and selecting Insert > Separator or by typing “-” for the text of a menu item.  
Before you enter text for a menu item, a drop-down list can be used to select the type of menu item(MenuItem, comboBox, TextBox)
it is a convention to put ellipsis … after any menu items that requires further action by opening new windows.

Properties
RightToLeft	//display text from right to left

ToolStripMenuItem
It is the menu items
Properties
Checked
CheckOnClick
ShortcutKeyDisplayString	//display string instead of key name.
ShortcutKeys		//define  the shortcut key
ShowShortCut-Keys   //default true
Text		text for the menu item

Event
Click
———————————————————————————————————
Context Menus
A context menu, or pop-up menu, is displayed when the user right-clicks a form or control that the context menus is associated with.
———————————————————————————————————
MonthCalendar
The MonthCalendar control (Fig. 15.8) displays a monthly calendar on the Form.
Multiple dates can be selected by clicking dates on the calendar while holding down the Shift key.  
Properties
FirstDayOfWeek	//set the first day of the each weeks in the calendar.
MaxDate		//latest date available for selection
MaxSelectionCount    //the maximum date can be selected at once.
SelectionEnd		//the last of the dates selected by the user.
SelectionRange	//the dates selected by the user.
SelectionStart		//the first date the user select.

Event
DateChaged    	//

———————————————————————————————————
DateTimePicker
The DateTimePicker control displays a calendar when a down arrow is selected.  
CalendarForeColor
CalendarMonthBackground
CustomFormat
Format			//date format(Long, Short)
MaxDate
MinDate
ShowCheckBox	//whether a checkbox is shown beside selected date and time
ShowUpDown		//display up and down button.
Value			//date selected by the user.

Event
ValueChanged //(default)
———————————————————————————————————
LinkLabel
The LinkLabel control displays links to other resources, such as files or web pages
Class LinkLabel inherit all properties from class Label.

Properties
ActiveLinkColor
LinkArea	//specifies the which portion of the text is part of the link.
LinkBehavior
LinkColor	//the original color of the link(default blue)
LinkVisited	//if true the link change its color as visited(default false)
Text		
UseMnemonic	//if true & character can be used to set shortcut key.
VisitedLinkColor

Event
LinkClicked


Visual Inheritance
Visual inheritance enables you to achieve visual consistency.  For example, you could define a base Form that contains a product’s logo and a specific background color.  You then could use the base Form throughout an app for uniformity and branding.
Class VisualInheritanceBaseForm (Fig. 15.45) derives from Form.  We use the public class VisualInheritanceBaseForm.  Use the namespace declaration that was created for us by the IDE.  Right click the project name in the Solution­ Explorer and select Properties, then choose the Application tab.  In the Output type drop-down list, change Windows Application to Class Library.  Building the project produces the .dll.   
To visually inherit from VisualInheritanceBaseForm, create a new Windows Forms app.  In this app, add a reference to the .dll you just created.  Modify the line that defines the class:  public partial class VisualInheritanceTestForm :         VisualInheritanceBase.VisualInheritanceBaseForm   
In Design view, the new app’s Form should now display the controls inherited from the base Form (Fig. 15.46).  Class VisualInheritanceTestForm (Fig. 15.47) is a derived class of VisualInheritanceBaseForm.  
———————————————————————————————————

Visual Basic Library

InputBox
An InputBox is a useful dialog box provided by Visual Basic.
a reference to Microsoft.VisualBasic is required.
using Microsoft.VisualBasic;   //it is also required in the top.

The input box has one input area, one OK button, one Cancel button
OK button returns a string value containing user input
Cancel button returns an empty string.

Interaction.InputBox(Propmt, Title, Default, ,Xpos, Ypos)


Prompt		A string displayed in the input box, normally asks the user for a value
		This is the mandatory parameter.

Title		A string that appears in the title bar, contains project name by default

Default		A string to be initially displayed in the text box, empty by default

Xpos		An integer that specifies the distance (in pixels) of the leftmost edge of the input box from the left edge of the screen, centered horizontally by default

Ypos		An integer that specifies the distance (in pixels) of the topmost edge of the input box from the top of the screen, placed near the top of the screen by defaul

Financial class

Financial.Pmt
The Pmt function returns the periodic payment amount for a loan with a fixed interest rate

Financial.Pmt(periodicInterestRate, numberOfPeriods, –loanAmount);

periodicInterestRate is the rate of interest per period
numberOfPeriods is the total number of months
loanAmount is the amount being borrowed, must be negative

Financial.Ipmt
The IPmt function returns the interest payment for a specific period of a loan with a fixed interest rate and fixed monthly payments

Financial.IPmt(periodicInterestRate, period, numberOfPeriods, –loanAmount);

periodicInterestRate is the rate of interest per period
period is the period for which you would like the payment
numberOfPeriods is the total number of months
loanAmount is the amount being borrowed, must be negative

Financial.PPmt

The PPmt function returns the principal payment for a specific period on a loan with a fixed interest rate and fixed monthly payments
Financial.PPmt(periodicInterestRate, period, numberOfPeriods, –loanAmount);
periodicInterestRate is the rate of interest per period
period is the period for which you would like the payment
numberOfPeriods is the total number of months
loanAmount is the amount being borrowed, must be negative
