# iOS Development

## Design Concepts

- the prototype is necessary before making any app.
- universal app: the app that fits all screen sizes.
- point: it is the fixed unit for screen resolution regardless the screen quality(pixel is depends on screen quality)
- Safe area is all the free space in the current UI, the entire scene excluding navigation bar, status bar etc.
- arranged views are like the views embedded in a stack view
- usually `@3X` image is for 6/7/8 plus iPhone X, `@2X` image is for SE/6/7/8, without `@` is for non-Retina.
- adaptive layout change the constrain according to the device. iOS system has for size classes. regular and - compact for both height and width. Variation can be added by click the plus sign in front of its constant property. or other size property.
- Clip to bounds means the view which is trimmed by its boundary.
- leading is the left side, trailing is the right side.
- `iPhone X`’s full screen is extended to Superview. bottom instead of Safe Area.bottom.

## Playground

- Playground is the Immediate-mode for Swift, it provide real-time result for codes. It has a `.playground` file extension.
- `shift+command+enter` is used to execute codes.
- hold option key and click variables to see its details.

## Workspace Environment

### Project Navigator

- Left Panal is project navigator.
- `Command + 0` to hide and show the project navigator.
- `Command + 1 - 9` is used to select 9 tabs on the top of the project navigator.
- shows file like ViewController.swift and Main.storybord.
- show `Asset.xcassets` folder contain set list where you drag image and icon file for importing. And every files will be shown in the set viewer at the centre. file version will be handle automatically. double click can open file. Xcode accept raster and vector image.
- right click folder can create new group. group name Model(data model) View(custom class) Controller(view controllers) and StoryBoard are recommended to group swift controller files.
- right click can create new files into the folder. cocoa template is often used for custom class.
  when create custom new class, the class type should be set accordingly.
- custom view class has the following function.
- making connection between object in storyboard and class Object, setting object upon declaration and appearance of the object.
- view controller class has the following function.
- Controller class is responsible for objects connection and setting, passing data, user interaction and the appearance of the controller’s view.

### Editor Area

- The center part is the editor area. its where you edit the file open from project navigator.

### Utility Area

- right pane is the utility area, it sets the properties of the file selected.
- hide/show `command + option + 0`
- `command + option + (1-6)` select tabs
- Identity inspector: shows associated swift file for each View Controller and object.
  It has User defined runtime attribute editor can insert the code in didSet method here and set its value.
- attributes inspector: stuff like change objects color. "+" button can be used to set properties(or hide by checking the Hidden checkbox) for specific screen size. preserve vector option can be used in the attributes inspector when select the image in the assets folds, in order to make vector image has the best quality. initial view controller is the first view to load, can be change in attributes inspector, shown a big arrow on the left, It also has clip to bounds option. change object’s title,
  hide navigation bar on swipe(once for all) , change controller size, large navi bar etc.
- connection inspector: show all the connection between actions and function calls
- size inspector: shows constrains, change view size, object size.

### Debug Area

- The bottom is the debug area.
- There is a console to display program output.

### Tool Bar

- Top area is the tool bar.
- from play button to device select: build the app(including compile codes and package files.) and run in the simulator indicated which device to run.
- `Command + B` can build the app. or click run.(command+r) and command+q to quit
- Clean the project is a good way to avoid errors.
- assistant editor can open swift files on the top of the editor area
- can be used to option+ drag(object code to UI objects) make connections.

### Simulator

- `command + 1` scale down the simulator size. `command + w` to close, `command + left` and `command + right` rotate screen
- `Command + k` open keyboard
- drag and move cursor up and down to scroll in the simulator.
- drag images to the simulator can add image to its photo library.
- `command + shift + h` back to home screen

### Interface builder

- `Main.storyboard` bring the editing area into a visual editor for storyboard called Interface builder.
  -It has a object library `Shift+Command+L`
- `shift + right` click show all options for an accurate selection to find an item.
- objects can be dragged directly in to the view.
- `Command + =` for auto resize objects.
- top left is the assist pop-up menu, hold option click preview in related item button or other files on the top bar.. its content opens the assistant editor.
- scene dock is on the top of the scene, it has exit icon for unwind segue connection, can drag additional view to this dock for editing, and IBAction connection.
- right click empty space can zoom out to have an overview of the storyboards.
- Controllers in one storyboard can be refactored to a new storyboard. As a result, the controller are moved from the old to the new storyboard. The reference of these storyboard for the controllers will be shown as the storyboard reference. It is done by selecting the controllers and clicking the Refactor to Storyboard editor menu, then renaming the new storyboard.(double-clicking the reference will show the corresponding storyboard.)
- Changes made on LaunchScreen StoryBoard will only be effective after reinstallation of the App.
  LaunchScreen.storyboard is the launch screen for your app. It can not have a controller file for customization, it can be frozen for certain time using Thread.sleep method in AppDelegate file.

### Document Outline

- an outline sits between interface builder and project navigator
- It has a scene which refer to on-screen content(controller)
- It has segue is used for transition between scene(show and present)
- storyboard references are used to break a large storyboard into small storyboards.
- when there is any issue yellow arrow is shown on the right.
- It has a controller for each screen of the app
- show constrains/stack viewer etc, click and editing in the attributes inspector
- This place can also be control-dragged, after right click, so connect can be made.
- right-click can show its property
- Objects in the outline should be renamed properly for readability.
- configuration bar
  - preview setting
  - open by clicking View as
  - located in the bottom bar
  - choose live preview device
- show current size class
- Auto layout bar
  - can be done by control-drag between two objects, drag to the constrain you aim at. can be done in doc outline panel.
  - constrain to margin means safe area excluding the status bar
  - located at right side of the config bar
  - default object hard-coded its position relate to the top left corner.
  - constrains can be double clicked and edited.
  - objects’ width and height can be set as constrain.
  - option+drag to itself in the document outlines can set the aspect ratio constrain.
- Align: add new constrains
- update frame: reset positions according to the constrains.
- Embed in: create stack view for selected items, can be nested, can also be found in object library.

### Top menu

- Embed tab bar and navi bar.
- Project Setting:
  - disable landscape view.

### Code Editing View

- hold control key and drag object to View Control Icon on top and select connection.
- hold option and click the class name see details. It has reference link at the bottom.
- in the code comment `//MARK: -` something is used to separate code into blocks and can be seen by clicking jump bar where shows the files address on the top.
- `Control+Command+?` and click anything to get info
- grey circle can show connection properties.
- `@IBAction` is for method exposure, `@IBOutlet` is for object exposure.
- `@IBOutlets` can be included in an array of objects, so the array variable can connect many outlets. This is called outlet collection. the index for objects is based on the connection order.
- use `command + f` to find keyword in the document windows.
- `command + \` turn a block of code into a comment.
- the document has up-to-date articles and detail of all methods. three finger click on the touch pad when the cursor is over any code in code editing mode, it will show the document about it.
- the IDE can give you all available input at each point.
- When copy paste code into the editor be aware of the extra `{` error. it is solved by restart Xcode.

### New Project Creation

- organization name : personal user use your own name. and the identifier is a reversed domain
- bundle identifier is used during app submission
- Single View has a ViewController class in the swift file and it is associated with a default View Controller Scene. more view can be added by drawing the view controller object. and create new swift file and associate them.

### Project File Structure

#### Controlller Files

- one controller per class.
- `willsomething` method is about to, did is already for methods.
- objects from the library are optional type.
- There is a traitCollection value to describe the current device properties.
- CGPoint:
  - This is the Coordinate of for the storyboard in point unit.
- viewDidLoad
  - This is the method that runs when controller completes to load the view.
  - This method is only called once when the view is first loaded.
  - all the initial value can be set here.
- viewWillAppear
  - This method is called when the view is about to display.
  - It is called every time the view is about to display.
  - can be called in other function like viewWillAppear(true), the bool value enables the animation effect.
- viewDidAppear
  - This method is called when the view is presented on screen.
  - It is called every time the view is presented.
- `NSException` might means `IBOutlet` is not properly connected.
- didSet block
  - didSet block can contain setting for objects right after the declaration.

```swift
@IBOutlet var newObject: UIType! {
    didSet {
    //make changes here.
    }
}
```

#### AppDelegate

- AppDelegate class
  - It set the appearance for the entire app.
  - It save data for the entire app.
  - It overrides all setting in controller class.
- objectDelegate class
  - whenever extend the controller class to an UIDelegate object’s delegate is required to connect to the controller.
  - It change the behaviour of certain object for the entire app, this controller class are required to inherit this delegate class, some method can be the implemented in the controller class. in the didSet method objectName.delegate = self are required

#### Fonts

- It can be placed in a Font folder under Resources folder.
- Drag the font files in the new folder. make sure the target membership is correct and select the "copy item is needed" option
- The T button is used to set font style. Font set to T can auto adjust the size according to the system setting.
- set font style will enable Dynamic type(user can change the font size through setting)
- enable the Automatically Adjusts Font option in attributes inspector for dynamic type to take effect immediately.
- use `command + =` to make change to the new font size immediately.

```swift
if let newFont = UIFont(name: "Font name", size: 123.0) { //declare custom font
…//make change here
}
```

#### `Info.plist` file

- the configuration file of the Xcode project using XML
- move the cursor on any entry and click the + button, type the key name and set its value.
- Or right-click and choose add row.

## UI Kit Framework

- `UIKit` is the framework for iOS mobile app development
- All of it classes have UI prefix.
- for Mac desktop development, referring to AppKit(has NS prefix)
- It has the following predefined classes

### UIView

- All objects is from a subclass of UIView, including table cell collection cells
- The first UIView of any storyboard is the overall background of the app.
- It has the following properties.
  - `object.bounds.width`, return the width
- View objects has a size value
  - `object.frame.size`
  - the size value has .width and .height attributes.
- `String(describing: className.self)`, it returns the identifier of the class
- most object can have a tag
- `.superview`, this can refer to the object’s parent.
  - `var cell: UITableViewCell = sender.superview.superview as UITableViewCell`
- In ViewDidLoad

```swift
view.backgroundColor = UIcolor.black
//this set the background to black.
backgroundImageView.image = UIImage(named: "abc") //set background image
anyView.contentInsetAdjustmentBehavior = .never //the safe area move up to status bar.
let x = UIBlurEffect(style: .dark) //.dark, .light, .extraLight
let y = UIVIsuallEffectView(effect: x)
y.frame = view.bounds
backgroundImageView.addSubview(y) //add blur effect to the background.
```

- In the didSet

```swift
newObject.layer.cornerRadius = newObject.bounds.width / 2
newObject.clipsToBounds = true
textFieldName.tag = 1 //all objects can have a tag value.
```

- Extension for take snapshot:

```swift
import UIKit

extension UIView {
var snapshot: UIImage? {
var image: UIImage? = nil
UIGraphicsBeginImageContext(bounds.size)
if let context - UIGraphicsGetCurrentContext( ) {
    self.layer.render(in: context)
    image = UIGraphicsGetImageFromCurrentImageContext( )
    }
    UIGraphicsEndImageContext( )

        return image
}

//This enable All the .snapshot property of all its subclasses. It take snap of any objects by using object.snapshot.
Additional view can be added to a view controller as subview or input view(like keyboard)
view.addSubView(subViewName)
//set subview layout
//Bring subview to front
tableView.bringSubviewToFront(buttonView)
```

- or drag the object to lower in the navigator.????What is it called again?

### Button

- It can be connected to a `@IBAction` function in the view controller and act like the sender. Code inside this function will be executed.
- control drag button to the controller in the scene dock
- `@IBAction func funcName(sender: UIButton) {…}`
- in the function:
  - `sender.titleLabel?.text` is the label name of the button.
- can be activated if mouse over, mouse release ,clicking(default)
- There can be found and set up in the connections inspector.
- It has `button.style.StyleName` to set its style.

### Switch

- `switchName.setOn(true, animated: false)`
  - set the switch on or off according to the boolean parameter.
- `switchName.isON`, it return the boolean value about its on/off state.

### Label

- `label.text = "abe"`, set label’s text
- has auto shirk property to fit small screen with large font size.
- set line number to 0 to enable multiline label.
- in didSet:
  - `labelName.numberOfLInes = 0` //to enable multi-line for label.
  - `labelName.adjustsFontForContentSizeCategory = true`, make dynamic type to be effective immiatediatly after setting

### UIColor

- it can be used to set color `let coelorx = UIColor(red: 123.0/255.0, green: 123.0/255.0, blue: 123.0/255.0, alpha: 1.0)` or use `Color.bule`

### UIImage

- used to display image.
- all the image file should be drag into the assets folder first.
- set the image file to display in its attribute inspector.
- control drag is used to set aspect ratio.
- drag view underneath and set it color to black with some low alpha value can make the image has a dim effect.
- `var newImage = UIImage(named: "abc")` set image use the file name.
- `UIImage()`, set image to transparent(blank)
- `UIImage(data: newImage as Data)`, load image saved as Data
- `newMO.image = newImage.pngData()`, save image in png format
- in didSet, `imageName.image = UIImage(named:"abc")?. withRenderingMode(.alwaysTemplate)`, load image abc as a template image
- `heartImageView.tintColor = .white`, change the image color to white.

### ActivityViewController

- it is used to share content.
- `let controllerName = UIActivityViewController(activityItems: ["array of text and image here"], applicationActivities: nil)`
- `self.present(activityController, animated: true, completion: nil)`

### AlertController

- It create a pop-up in the app as an alert window.
- `let controllerName = UIAlertController(title: "The title on top", message: "Message in the center.", preferredStyle: .alert)`, alert style is a pop-up window in the middle.
- `actionSheet` style is displayed at the bottom.
- AlertAction class defines the buttons of the alert window.
- `controllerName.addAction(UIAlertAction(title: "OK", style: .default, handler: nil))`
  - default, cancel and destruction styles are available.
  - handler is a function defined earlier to be executed when this action is activated.
- alert controller works with present method to present.
  - `present(controllerName, animated: true, completion: nil)`
- when working with iPad, a popoverPresentationController is required before presenting.

```swift
if let popoverController = alertControllerName.popoverPresentationController {
    if let cell = tableView.cellForRow(at: indexPath) {
        popoverController.sourceView = cell
        popoverController.sourceRect = cell.bounds
        //.sourceRect set the location of the popover window.
    }
}
```

### Tableview

- It can be drag into any controller.
- `indexPath.row`, return the index number in integer
- It has basic setting like the number of prototype cells, style(basic, custom), and cell identifier.
- It can contain header and footer, if objects are dragged as the first or last item in the table.
- its controller class need to inherit two protocols: UITableViewDataSource, UITableViewDelegate. the tableview object also need to connect to the two protocols.

```swift
class ViewControllerName: UIViewController, UITableViewDataSource, UITableViewDelegate{
    //
}
```

- tableview has section header and table header.
- It require two methods defined in the controller class:

```swift
func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int
{
//set the number of rows in the section here. (the default number of section is one.)
}

func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
let cell = tableView.dequeueReusableCell(withIdentifier: "cellIdentifier", for:indexPath)
//dequeueReusableCell is a function that load and relocate new cells when swipe.
//Configure the cell here…
cell.textLabel?.text = dataArray[indexPath.row]
 cell.imageView?.image = UIImage(named: "imageNameInAssets")
//textLabel and imageView? are optional in the default TabelViewCell class.
    return cell
}
```

- In ViewDidLoad

```swift
tableview.backgroundView = imageName
tableView.backgroundView?.isHidden = true
//the background image’s constrains are set as usual.
//set and hide temperate empty table background.
//unhide can be set in the numberOfSection method (it is called when the table is configured) using if statement, along with the separator style setting.
self.tableView.rowHeight //set the rowHeight of the tableView Controller.
tableView.cellLayoutMarginsFollowReadableWidth = true
//set a readable width on iPad.
tableView.separatorStyle = .none //it removes the separator between cells.
tableView.delegate = self //it means to use delegate implemented here in this controller.
tableView.dataSource = self //set the association for mandatory protocols for tableview class.
```

- `enum` can be used to track cells state if certain cell needed to be changed. or the cell reuse will cause bug. action method and cellforRow need to have the updates for the tracking value.

```swift
//set the height for all section headers
override func tableView(_ tableView: UITableView, heightForHeaderInSection section: Int) -> CGFloat {
return 50
}
//set style for all section headers
override func tableView(_ tableView: UITableView, willDisplayHeaderView view: UIView, forSection section: Int) {
let headerView = view as! UITableViewHeaderFooterView
headerView.backgroundView?.backgroundColor = UI Color(red: 236.0/255.0, green: 236.0/255.0, blue: 236.0/255.0, alpha: 1.0)
    headerView.textLabel?.font = UIFont(name: "Avenir", size: 25.0)

}
```

#### TableViewController

- It can auto focus on the textfield when keyboard shows up. (not working with viewWillAppear method)
- It has two protocols inherited and connected, all constrains are set for the table content.
- It has static table.
- the number of section method needs to be changed to at least 1.

```swift
override func numberOfSections(in tableview: UITableView) -> Int {
return 1
} //remove this method will set the number of section to default value as 1.
```

- willselect for click cell that is about to open.
- didselect for clicked cell
- For default style it has UIOutlet as follows, no connection is required:
  - `cell.textLabel?.text`
  - `cell.detailTextLabel?.text`
  - `cell.imageView?.image`
- For selected cell the contain of the following method will be called.

```swift
override func tableView(\_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
    //a certain cell can be found and assigned using
    let cell = tableView.cellForRow(at: indexPath)
    //indexPath records the row number of the selected cell
    tableView.deselectRow(at: indexPath, animated: false)
    //this method is used to deselect the row after the selection process is done, otherwise
    //the cell will keep a darker background.
}
```

- To enable left swipe to delete, use the following method.

```swift
override func tableView(_ tableView: UITableView, commit editingStyle: UITableViewCell.EditingStyle, forRowAt indexPath: IndexPath) {
    if editingStyle == .delete {
        cellData.remove(at: indexPath.row)  //remove selected cell data
    }
    tableView.reloadData() //reload the tableView.
    //or
    tableView.deleteRows(at: [indexPath], with: .fade)
    //delete the row from the current view.
}
```

- For more customized swiping experience use

```swift
override func tableView(\_ table View: UITableView, leadingSwipeActionConfigurationForRowAt indexPath: IndexPath) -> UISwipeActionsConfigurations? {
//right swipe
}
override func tableView(\_ table View: UITableView, trailingSwipeActionConfigurationForRowAt indexPath: IndexPath) -> UISwipeActionsConfigurations? {
//left swipe
    let actionName = UIContextualAction(style: .destruction, title: "Delete") {(action, sourceView,completionHandler) in
//.destruction presents red color, style can be .normal. it is gray.
self.cellData.remove(at: indexPath.row)
    self.tableView.deleteRows(at: [indexPath], with: .fade)
    completionHandler(true)
    //ContextualAction object is used for "swipe to delete".

}
    actionName.backgroudColor = UIColor()   //set its color.
    actionName.image = UIImage(named: "abc")  //set its icon.
    let configurationName = UISwipeActionConfiguration(actions: [actionName1,actionName2,…])
    return configurationName
}
```

- The following example code shows how to return a custom height for the first row of each section and use the default height for all other rows.

```swift
override func tableView(_ tableView: UITableView,
heightForRowAt indexPath: IndexPath) -> CGFloat {
    // Make the first row larger to accommodate a custom cell.
    if indexPath.row == 0 {
        return 80
    }
    // Use the default size for all other rows.
        return UITableView.automaticDimension
    }
```

- TableView Scroll position, `tableV.contentOffset.y`
- in tableView(titleForHeaderInSection) `return sectionTitles[section]`, set section title
- in ViewDidLoad: `tableView.tableFooterView = UIView()`, remove extra separator in a table view.
- when changing certain table cell in the `didselect` or other action methods:

```swift
tableView.beginUpdates()
//make change here
tableView.endUpdates() //the code in between will take effect immediately.
```

#### TableViewCell

- customized cell in a table required the creation of a new class file as a subclass of UITableViewCell.
  In the controller, the dequeueReusableCell class return type need to specify as the new cell class type, using `as!`.
- self sizing cell is enabled after defining its layout constrains.
- to enable self sizing, in the `ViewDidLoad` method add:
  - `tableView.estimatedRowHeight = 100.0`
  - `tableView.rowHeight = UITableView.automaticDimension`, this is the default row height.
- in attributes inspector, selection option can be set for reaction style after cell selection.
- cell need to have identifier and is required in the cellForRowAt’s dequeue method.
- In the customized cell, connection and basic setup are needed for all the objects within the cell.
  - `@IBOutlet var labelX: UILabel!`
  - `@IBOutlet var ImageX: UIImageView!`
- cell object has properties as following.
  - `cell?.accessoryType = .checkmark`
- There are four types of built-in accessory views, disclosure indicator, detail disclosure button, checkmark and detail. when setup this change, an array of boolean is required to track the change or the dequeueReusableCell method will keep the change on certain cell location and cause bug.
- In order to set multi cell, In cellForRowAt:

```swift
switch indexPath.row {
    case 0: //switch and case statement are usually used in the current controller
    default:
        fatalError("error message")
```

### Collection View

- It displays a collection of data like Apple’s default image app.
- For `UICollectionView`, its controller class needs to be extended from datasource and delegate protocol classes.
- `class CuppingViewController: UIViewController, UICollectionViewDataSource, UICollectionViewDelegate {}`
- The collection view should be associated with these protocols in the storyboard or using code in ViewDidLoad method as following.
  - `collectionView.delegate = self`
  - `collectionView.dataSource = self`
- Collection view controller contains all the protocols by default.
- Datasource protocol contain methods that control numberOfSections, numberOfItemsInSections, and cell configuration(with dequeue method).
- Delegate protocol contains methods including didSelectItemAt, didDeselectItemAt
- In action handler method. set `collectionView?.allowsMultipleSelection = true` to enable multi-select.
- There is an `UICollectionViewDelegateFlowLayout` protocol to format the layout.
  - It has an optional method `UICollectionViewLayout` to specifying the cell size as following.

```swift
//in the controller class from the FlowLayout protocol.
extension SampleCollectionViewController: UICollectionViewDelegateFlowLayout {
func collectionView(_ collectionView: UICollectionView, layout collectionViewLayout: UICollectionViewLayout, sizeForItemAt indexPath: IndexPath) -> CGSize {
    let sideSize = (traitCollection.horizontalSizeClass == .compact && traitCollection.verticalSizeClass == .regular) ? 80.0 : 128.0
    return CGSize (width:sideSize, height: sideSize)

}
//for specific header and footer size
func collectionView(_ collectionView: UICollectionView, layout collectionViewLayout: UICollectionViewLayout, referenceSizeForFooterInSection section: Int) -> CGSize
```

- To respond the size class change immediately, implement the following method in the controller class:

```swift
override func viewWillTransition(to size: CGSize, with coordinator: UIViewControllerTransitionCoordinator) {
collectionView.reloadData( )
}
```

#### Header and Footer View

- In controller class use the following method:

```swift
func collectionView(_ collectionView: UICollectionView, viewForSupplementaryElementOfKind kind: String, at indexPath: IndexPath) -> UICollectionReusableView {
        if kind == UICollectionView.elementKindSectionHeader{
            let supplementaryView = collectionView.dequeueReusableSupplementaryView(ofKind: kind, withReuseIdentifier: "headerView", for: indexPath) as! CuppingHeaderView
            supplementaryView.sampleName.text = "abc"
            return supplementaryView
        }
}
```

- view height:

```swift
func collectionView(\_ collectionView: UICollectionView, layout collectionViewLayout: UICollectionViewLayout, referenceSizeForFooterInSection section: Int) -> CGSize {
    let width = view.bounds.width
    return CGSize(width: width, height: 100)
}
```

#### Collection View Cell

- It has `.backgroundView` and `.selectedBackgroundView` property.

### NSDate and NSCalendar and DateFormatter

- Get Date and Time `let x = Date( )`, get current date and time using a 64-bit floating point number and the reference date
- `let hour = calendarX.component(.hour, from: dateX)`
- `let minutes = calendarX.component(.minute, from: dateX)`
- `x.timeIntervalSinceReferenceDate`, return the number of sec from the reference date on Jan 1st, 2001 in UTC
- `let x = Calendar.current`, get the current calendar
- Get the current date and time in integer

```swift
let date = Date()
let calendar = Calendar.current
let hour = calendar.component(.hour, from: date)
let minutes = calendar.component(.minute, from: date)
let seconds = calendar.component(.second, from: date)
print("hours = \(hour):\(minutes):\(seconds)")
//using components
let requestedComponents: Set<Calendar.Component> = [ .year,.month,.day,.hour,.minute,.second]
let dateTimeComponents = userCalendar.dateComponents(requestedComponents, from: currentDateTime)
dateTimeComponents.year // 2016
dateTimeComponents.month // 10
dateTimeComponents.day // 8
dateTimeComponents.hour // 22
dateTimeComponents.minute // 42
dateTimeComponents.second // 17
//Using Date Formatter
let currentDateTime = Date()

let formatter = DateFormatter() // initialize and set the style
formatter.timeStyle = .medium
formatter.dateStyle = .long

// get the date time String from the date object
formatter.string(from: currentDateTime) // October 8, 2016 at 10:48:53 PM
Here is a continuation of the above code that shows more formatting options:

// "10/8/16, 10:52 PM"
formatter.timeStyle = .short
formatter.dateStyle = .short
formatter.string(from: currentDateTime)

// "Oct 8, 2016, 10:52:30 PM"
formatter.timeStyle = .medium
formatter.dateStyle = .medium
formatter.string(from: currentDateTime)

// "October 8, 2016 at 10:52:30 PM GMT+8"
formatter.timeStyle = .long
formatter.dateStyle = .long
formatter.string(from: currentDateTime)

// "October 8, 2016"
formatter.timeStyle = .none
formatter.dateStyle = .long
formatter.string(from: currentDateTime)

// "10:52:30 PM"
formatter.timeStyle = .medium
formatter.dateStyle = .none
formatter.string(from: currentDateTime)

Set Date and Time

let y = Date(timeIntervalSinceReferenceDate: -1,000,000,000)
//return a Date 1billion sec before the reference date.

let z = DateComponents( )
z.year //return the current year
z.month
z.day
z.timeZone = TimeZone(abbreviation: "BJT")
//set current time zone, set abbr. blank for user time zone
z.hour
z.minute

var x = Calendar.current
var dateZ = x.date(from: z) //create date from components z

set date using format
let formatter = DateFormatter()
formatter.dateFormat = "yyyy/MM/dd HH:mm"
let someDateTime = formatter.date(from: "2016/10/08 22:31")
```

### Stepper

- It can return the value in double using the following code
- `x = Int(stepperName.value)`
- can be activated if mouse over, clicking, and value change(default)
- There can be found and set up in the connections inspector.
- When value changed, by default it will send action to IBAction function without connecting to the action.

### SegmentControl

- In action method, get the selected segment using the following code
- `if defectSegment.selectedSegmentIndex == 0`

### Animation

### UIImagePickerController

```swift
let cameraAction = UIAlertAction(title: "Camera", style: .default, handler: { (action) in
if UIImagePickerController.isSourceTypeAvailable(.camera){
    let imagePicker = UIImagePickerController()
    imagePicker.allowsEditing = false
    imagePicker.sourceType = .camera
    self.present(imagePicker, animated: true, completion: nil)
    }
})
let photoLibraryAction = UIAlertAction(title: "Photo library", style: .default, handler: { (action) in
if UIImagePickerController.isSourceTypeAvailable(.photoLibrary) {
    let imagePicker = UIImagePickerController()
    imagePicker.allowsEditing = false
    imagePicker.sourceType = .photoLibrary
    self.present(imagePicker, animated:true, completion: nil)
    }
})//need popover control for iPad
```

- In `Info.plist` file
  - `NSPhotoLibraryUsageDescription` and `NSCameraUsageDescription` are required:
  - key name: `Privacy - Photo Library Usage Description`
  - value: The reason
  - key name: `Privacy - Camera Usage Description`
  - value: The reason
- UIImagePickerControllerDelegate and UINavigationControllerDelegate are required to be adopted by the controller class, in order to interact with the image picker interface.
- the the `imagePickerController(_didFinishPicking)` is called after user picks an image.
- an outlet is required to connect to the file for the image to display.
- In the controller file:

```swift
func imagePickerController(_ picker: UIImagePickerController, didFinishPickingMediaWithInfo info: [UIImagePickerController.Infokey :Any]) {
    if let selectedImage = info[UIImagePickerController.Infokey.originalImage] as? UIImage {
        photoImageView.image = selectedImage
        photoImageView.contentMode = .scaleAspectFill
        photoImageView.clipsToBounds = true
    }
    dismiss(animated: true, completion: nil)
}
//imagePicker.delegate = self is required in the didSelect method.
```

### Extensions

- extensions are custom class use to simplify or customize classes from the framework, to make the coding easier.
- It is recommended to create an Extension group to hold the file.
- The name of the extensions can be ClassName+Ext.swift
- it uses swift template file.

```swift
import UIKit
extension UIColor {
    convenience init(x:Int, y:Int){
        //your new initializer goes here
        self.init(x: Double, y:Double, z:Double) //the original initializer goes here
    }
}
```

## NS Objects

### NSLayoutConstraint

- User input objects
- It can work with a static cells table for user input.
- static table is a style of the table view controller.
- textfield: accept single line input
- text view: accept multi-line input
- customized text field
- `self.view.endEditing(true)` //close the keyboard.

```swift
class RoundedTextField: UITextField {
    let padding = UIEdgeInsets(top: 0, left: 10, bottom: 0, right: 10);
    override func textRect(forBounds bounds: CGRect) -> CGRect {
        return bounds.inset(by: padding) //text input area
    }
    override func placeholderRect(forBounds bounds: CGRect) -> CGRect {
        return bounds.inset(by:padding) //placeholder text area
    }
    override func editingRect(forBounds bounds: CGRect) -> CGRect {
        return bound.inset(by: padding) //text display area
    }
    over func layoutSubviews() { //this method is called every time when the text field is displayed
        super.layoutSubviews()
        self.layer.cornerRadius = 5.0
        self.layer.masksToBounds = true
    }
}
```

- when adapt UITextFieldDelgate, the following method can be used to enable auto selection after pressing the return key.
- this method is called when pressing return key in a textfield.

```swift
func textFieldShouldReturn(\_ textField: UITextField) -> Bool {
    if let nextTextField = view.viewWithTag(textField.tag + 1) {
        textField.resignFirstResponder()
        nextTextField.becomeFirstResponder()
    }
    return true
}
```

- In didSet:

```swift
textFieldName.becomeFirstResponder()
//only the first object need to specify the first responder
textFieldName.delegate = self
//these codes enable auto selection for textfield object
```

- TextField can detect actions like `didEndEdit` for `@IBAction` func to act or method like `didEndEdit` can also be found in the `TextFieldDelegate`(it will be called when certain action is performed)

### NSString

- return all value contained in the beginning of the string.
- `.doubleValue` return double values.
- `.intValue return` integer values.

### Localization

- wrap all strings in the code using NSLocalizedString
- "abc" -> NSLocalizedString("abc", comment: "abc")
- select the project in the project navigator
- open the left panel, select the app under project section.
- add new languages in the localizations section for storyboard files.
- select the project in the project navigator, Editor -> export for localization
- all text from storyboard and wrapped strings in code is shown in source tag, in XLIFF files.
- translate everything in the target tag in the XLIFF files. //For strings from code, add target tag for them.
- select the project in the project navigator, Editor -> import for localization
- the base file is the for the default language that is used for development.

## Data Source

### Core Data

- Core data is enabled when click the Core Data option during the project creation. As a result, related code will be generated in the AppDelegate.Swift with import CoreData in its first line.
- The `persistentContainer` name is the same as the project name.
- The data modal file(.xcdatamodeld) will also be created.
- click add entity button to create and name the data model by clicking the entity name.
- click + under the attributes section to create new attributes with corresponding data type.
- parent relationship can make the current entity have the attributes from the parent entity.
- Integer 16: a 16-bit signed integer attribute.
- Integer 32: a 32-bit signed integer attribute.
- Integer 64: a 64-bit signed integer attribute.
- attributes name "description" is reserved.
- image file is usually save as Binary data type.
- set the information as required by unchecking the optional checkbox in the data modal inspector.
- managed objects are what associate with the core data database, its class can be automatically generated by building the project after setting up the data model.
- class name and code options(usually class defination) are set in the data model inspector.
- when error occurs during rebuilding the project, go to Product->Clean to clean the project first.
- When the managed object class is created, an array of this objects can be declared in all controller classes and the class object is optional type.

```swift
if let newImage = MOarray[indexPath.row].image {
cell.image = UIImage(data: newImage as Data)
} //binary image data access
```

#### Save Data

```swift
import CoreData //import CoreData
var newMO: MO! //declare new variable
```

- In the save method

```swift
//get the AppDelegate object
if let appDelegate = (UIApplication.shared.delegate as? AppDelegate) {
newMO = RestaurantMO(context: appDelegate.persistentContainer.viewContext)
//create new MO with the view context of the persistent container, This is the only way to create new MO object.
newMO.xText = "x"
newMO.yText = "y"
if let newImage = object.image {
newMO.image = newImage.pngData() //save image in png format
}
//call saveContext()
appDelegate.saveContext()
```

- the save process can also work as an update process.

#### Fetching Data

```swift
if let appDelegate = (UIApplication.shared.delegate as? AppDelegate) {
    let request: NSFetchRequest<RestaurantMO> = RestaurantMO.fetchRequest()
    let context = appDelegate.persistentContainer.viewContext
    do {
        restaurants = try context.fetch(request)
    } catch {
        print(error)
    }
}
```

- In order to monitor the changes of the managed objects, NSFetchedResultsControllerDelegate is used.
  1. import CoreData
  2. add the NSFetchedResultControllerDelegate Protocol to the Controller class.
  3. declare a new fetchResultsController in the controller class `var fetchResultController: NSFetchedResultsController<restaurantMO>!`
  4. add following code in the `viewDidLoad`

```swift
//fetch data
let fetchRequest: NSFetchRequest<RestaurantMO> = RestaurantMO.fetchRequest( )
let sortDescriptor = NSSortDescriptor(key: "name", ascending: true)
//key name is the attribute name for sorting
fetchRequest.sortDescriptors = [sortDescriptor]
if let appDelegate = (UIApplication.shared.delegate as? AppDelegate) {
    let context = appDelegate.persistentContainer.viewContext
    fetchResultController = NSFetchResultsController(fetchRequest: fetchRequest, managedObjectContext: context, sectionNameKeyPath: nil, cacheName: nil)
    fetchResultController.delegate = self
    do {
        try fetchResultController.performFetch( )
        if let fetchedObjects = fetchResultController.fetchedObjects {
            restaurants = fetchedObjects
        }
    }catch {
        print(error)
    }
}
```

#### Change Data

```swift
//When there are changes made for the Managed objects, the following methods in the controller class are called.
func controllerWillChangeContent(_ controller: NSFetchedResultsController<NSFetchRequestResult>) {
tableView.beginUpdates()
}
func controller(_ controller: NSFetchedResultsController<NSFetchRequestResult>, didChange anObject: Any, at indexPath: IndexPath?, for type: NSFetchedResultsChangeType, newIndexPath: IndexPath?) {

    switch type {
    case .inset:
        if let newIndexPath = newIndexPath {
            tableView.insertRows(at: [newIndexPath], with: .fade)
        }
    case .delete:
        if let indexPath = indexPath {
            tableView.deleteRows(at: [indexPath], with: .fade)
        }
    case .update:
        if let indexPath = indexPath {
            tableView.reloadRows(at: [indexPath], with: .fade)
        }
    default:
        tableView.reloadData( )
    }
    if let fetchedObjects = controller.fetchedObjects {
        restaurants = fetchedObjects as! [RestaurantMO]
    }
}

func controllerDidChangeContent(\_ controller: NSFetchedResultsController<NSFetchRequestResult>) {
    tableView.endUpdates( )
}
```

#### Delete Data

- In the deletion action method:

```swift
if let appDelegate = (UIApplication.shared.delegate as? AppDelegate) { //get the delegate
let context = appDelegate.persistenContainer.viewContext //get the context
let objectToDelete = self.fetchResultController.object(at: indexPath) //get the object
context.delete(objectToDelete)//delete the object, and call controller .delete type action
appDelegate.saveContext() //save the context
}
```

#### Relationship

- It helps the definition of delete rules
- A delete rule defines what happens when the record that owns the relationship is deleted.
  - Nullify - nullify the relationships upon deletion
  - Cascade - delete the other objects upon deletion
  - No Action - take no action upon deletion
  - Deny - protect the other objects upon deletion
- Relationship needs be set and created on each side with to many or to one properties.
- choose the first entity and add relationship, set the destination to the second entity with corresponding property.
- choose the second entity and add relationship, set the destination to the first entity with corresponding property.
- In the style view(see style button in the bottom right corner)
- one arrow means to one relationship, double arrow means to many relationship.
- Once setup properly the objects can contain other objects as an attributes.
- The objects can be accessed by using the following code.
- `parentObject.childObjects?.allObjects as! [childObjectType]`
- Or sort the array `parentObject.childObject?.sortedArray(using: [NSSortDescriptor(key: "anyChildObjectAttribute", ascending: true)]) as! [childObjectType]`
- Many relationship enable the `addToEntity` method.
- `many to many` relationship enable `addToEntity` to add multiple objects.
- `addToEntity` method can be used to add the object to the other as an attribute.
- `removeFromEntity` is used to remove.

### Custom Data Model

- if core data is not used, an array of custom objects is recommended to store formatted app data, and it is accessed by `object[index].attributes`. it requires a model class file(initializer should be implemented.). more detail in data mode section

```swift
import Foundation

class Restaurant {
var name: String
var type: String
var location: String
var phone: String
var description: String
var image: String
var isVisited: Bool
var rating: String

    init(name: String, type: String, location: String, phone: String, description: String, image: String, isVisited: Bool, rating: String = "") {
        self.name = name
        self.type = type
        self.location = location
        self.phone = phone
        self.description = description
        self.image = image
        self.isVisited = isVisited
        self.rating = rating
    }
    convenience init() {
        self.init(name: "", type: "", location: "", phone: "", description: "", image: "", isVisited: false)
    }
}
```

## App Navigation

### Tab Bar

- It is a row of buttons at the bottom of the screen.
- It manage multiple view controllers that have no relation to on another.
- To create tab bar select a controller which designated to embed in a tab bar and click Editor>Embed in>Tab Bar Controller
- A navigation controller is usually used to embed the tab bar. In order to connect more controllers with the tab bar, control + drag the tab bar to the new navigation controller and select root view controllers. the tab bar can have up to 5 controller embedded inside.
- In the Attributes inspector for each tab item the image(set System Item Option to custom) and title can be changed.
- No layout constrains are required for the tab bars.
- To hide tab bar in the specific view, enable the Hide Bottom Bar on Push option in the Attribute inspector.
- to hide tab bar using code, in the prepare(for: ) for segue `destinationController.hidesBottomBarWhenPushed = true`
- For customization of the tab bar for the entire tab bar, in application(didFinishLauch) method in AppDelegate class.
- Change the icon color, `UITabBar.appearance().tintColor = UIColor(red: 231.0/255.0, green: 76.0/255.0, blue: 60.0/255.0, alpha: 1.0)`
- Change the background color, `UITabBar.appearance().barTintColor = UIColor.black UITabBar.appearance().backgroundImage = UIImage(named: "imageName")`
- `.selectedIndex`, This method can be used to set the tab on push.

### Status Bar

- Navigation controller is set as default controller for status bar style, to change its style in different controllers in one app, an extension for UINavigationController class is required.
- add the following extension

```swift
import UIKit
extension UINavigationController {
    open override var childForStatusBarStyle: UIViewController? {
        return topViewController
    }
} //make the status bar refers to the top controller class’s setting
```

- so then make setting in the controller class

```swift
override var preferredStatusBarStyle: UIStatusBarStyle {
    return .lightContent
}
```

- to hide staue bar

```swift
override var prefersStatusBarHidden: Bool {
    return true
}
```

- To make change globally, make change in the AppDelegate file.
  - in the application(didFinish) method in the AppDelegate
  - `UIApplication.shared.statusBarStyle = .lightContent(deprecated)`
  - Then, Opt out the View navigation controller-based status bar appearance in the `Info.plist` file
    Key name: `View controller-based status bar appearance`, Value `NO`. This disable the control for status bar in each view controller.
- Hide status bar on launch screen
  in plist file add `Status bar is initially hidden - Yes`

### Navigation Controller

- It is the page title and back buttons on the top part of the app
- Navigation Item is an object that used to customize navigation bar for certain controller.
- Navigation Item can have bar item and titles for this controller.
  without navigation item all navigation bars are control by the common parent navigation controller.
- In order to embed any controller into navigation controller: Edit->Embed in->Navigation controller.
- `control + drag` for a root view controller relationship is the same as the embed in relationship.
- Any view controller can have its own navigation controller with different design by embedding its own navigation controller.
- It can have a bar button item on the side, no constrains needed.
- It navigate hierarchical content by managing a stack of view controllers.
- All the hierarchical content share one common navigation bar.
- The same title of certain navigation controller will be displayed on all its controllers(the controllers the navigation bar associated with). Different navigation controller has different title.
- When create a new Navigation controller, it will associate with a default tableView controller.
- In view will appear method

```swift
navigationController?.hidesBarsOnSwipe = true
 //enable hide on swipe feature for specific navigation bar.
navigationController?.setNavigationBarHidden(false, animated: true)
//unhide the navigation bar.
navigationController?.setNavigationBarHidden(true, animated: true)
//hide the navigation bar.
navigationItem.hidesBackButton = true
//hide back button
```

- For global change in application(didFinishLaunch) method in AppDelegate file:

```swift
//change the back bottom of the navigation bar
UINavigationBar.appearance( ).backIndicatorImage = someImage
UINavigationBar.appearance( ).backIndicatorTransitionMaskImage = someImage
UINavigationBar.appearance().backgroundColor = UIColor()
//NavigationBar color
UINavigationBar.appearance().barTintColor = UIColor()
//NavigationBar text color
UINavigationBar.appearance().titleTextAttributes = [NSAttributedString.Key.foregroundColor:UIColor.white]
//NavigationBar item color
UIBarButtonItem.appearance().tintColor = UIColor.yellow
//Navigation back button color
UINavigationBar.appearance().tintColor = UIColor.white
```

- InViewDidLoad

```swift
//Use will Appear for individual child view settings.
//this enable the large navigation bar, when scroll it become smaller.
navigationController?.navigationBar.prefersLargeTitles = true

navigationItem.largeTitleDisplayMode = .never
//disable large navigation bar in specific controller.
//.automatic inherits setting from previous controller.
//.always turn on the large navigation bar.

//set navigation background and shadow to be transparent
navigationController?.navigationBar.setBackgroundImage(UIImage(), for: .default)
navigationController?.navigationBar.shadowImage = UIImage()

//set navigation font text color and font
navigationController?.navigationBar.largeTitleTextAttributes = [ NSAttributedString.Key.foregroundColor: .black, NSAttributedString.Key.font: newFont ]

//change the color of items in the navigation
navigationController?.navigationBar.tintColor = .white
```

- It also works with `contentInsetAdjustmentBehavior` to have an overlap effect. `viewType.contentInsetAdjustmentBehavior = .never`

### Segue

- segue is the transition between scenes.
- control drag form an object in one scene to another scene will establish segue(segue control the transit setup between views.).(doc outline mode will also do). then add segue an identifier. segue will copy the navigation bar from previous page.
- `prepare()` this method is called before segue in triggered. It can be used to pass data between two scene.
  in the first controller implement prepare method as following:

```swift
override func prepare(for segue: UIStoryboardSegue, sender: Any?) {
    //Any? it can be downcast to the actual object(like UIButton) which actually initiated the segue.
    //set data transition for the following segue
    if segue.identifier == "abc" {
        //get the indexPath for selected row
        if let indexPath = tableView.indexPathForSelectedRow {
            //get the destination controller object.
            let destinationController = segue.destination as! DestiControllerName
            destinationController.dataName = dataNameArray[indexPath.row]
        }
    }
}

performSegue(withIdentifier: "abc", sender: sender)
//This function works in the IBAction func to performSegue.
```

- unwind segue is used to go back to previous view. (or any other parent with unwind func)
  to enable unwind segue, in the previous view controller add:

```swift
@IBAction func methodName(segue: UIStoryboardSegue) {

            //data manipulation goes here, using information from segue.identifier or segue.source

    dismiss(animated: true, completion: nil) //(optional) further dismiss the current view with animation

}
```

- then, `option + drag` the close button to the Exit icon of the scene dock on the top of the view and select the method above.
- Show segue will add the current navigation controller to the destination view controller.
- To pass data through a navigation controller for a new look of the navigation bar on the next page:

```swift
let destinationController = segue.destination as! UINavigationController
let finalDestinationController = destinationController.topViewController as! FinalViewController
finalDestinationController.attribute = currentAttribute
```

- IndexPath
  - It can be set using
  - `IndexPath(row: 0, section: sourceController.sampleNumber)]`

## Testing

- testing at runtime
  - click the app icon beside run button and choose edit scheme…
  - run->option->set application language
  - then run the app
- testing in preview
  - open preview and select language at the lower right corner.
- To localize storyboard manually, select the storyboard and in file inspector, enable localization. Then XLIFF file will be generated.
- Test App on real device
  - make bundle ID unique
  - connect the device to the Mac
  - enable automatically manage signing option
  - find and select the device in the simulator list
  - add an account in team option using apple ID
  - assign the account in the team option
  - Unlock the device and Run the simulator in Xcode
  - Trust the developer in Settings->General->Device Management
- Enable wi-fi deployment
  - Connect the device to the Mac
  - In Xcode menu, Windows -> Devices and Simulators
  - enable connect via network for the device
  - make sure the device and the Mac are connected to the same network
  - when a globe icon is shown in device list, wi-fi deployment is now available

## Testflight

1. Enroll in the iOS Developer Program
2. Go on Apple Store Connect website
3. Select my App and click `+` to add a new app
4. Provide required information(name <= 30 char, SKU can be anything, like "appName-slogan"), add a unique bundle ID.
5. Provide additional information including subtitle, privacy policy page, availability & price. (The information can be provided in different language.)
6. provide submission information like screenshots, promotion text, descriptions, keywords, website URL etc.
7. Update version and build number in Xcode, version number is like major version + minor version + reversion(separated by "."), build number is the number of build for the software or major version + minor version in alphabet + number of builds for this minor version.(Eg. 6B358)
8. Edit scheme -> Run -> Set Build Config to Release
9. Select the device as generic device or your personal device. In Xcode menu, `Product -> Archive`
10. Update the Bundle ID, set it the same as the bundle entered in Apple Connect console.
11. In `Window -> Organizer`, click Validate App.
12. After click Validation, click distribute, select App Store Distribution -> Upload, click choose automatically manage signing.
13. In the Organizer, find the archive click Distribute App, select iOS App Store, click Upload.
14. In Apple Connect Website, select Testflight(It will be shown few minutes after uploading).
15. In Test Information, fill in all fields. Internal tester can be added directly, External tester can be added after app review.

## Submission

- In Apple Connect - My App, click prepare for submission. In the build section, click `+` to add your build. Fill in all required info. then, click submit for review.
